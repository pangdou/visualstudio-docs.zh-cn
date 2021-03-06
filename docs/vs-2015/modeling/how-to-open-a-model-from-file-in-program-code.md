---
title: 如何：在程序代码中从文件打开模型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: d7d68697-5418-4263-bdb2-48401924ea71
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c98bec69631b852521f682a24dd1b5ce6ddf0424
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662576"
---
# <a name="how-to-open-a-model-from-file-in-program-code"></a>如果：在程序代码中从文件打开模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

可以在任何应用程序中打开 DSL 模型。

 通过 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 扩展，可以使用 ModelBus 来实现此目的。 ModelBus 提供了用于引用模型或模型中的元素的标准机制，并用于查找模型（如果该模型已移动）。 有关详细信息，请参阅[使用 Visual Studio 集成模型 Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)。

## <a name="target-framework"></a>目标 Framework
 将应用程序项目的**目标框架**设置为 **.NET Framework 4**。

#### <a name="to-set-the-target-framework"></a>设置目标框架

1. 打开要在其中读取 DSL 模型的应用程序的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 项目。

2. 在**解决方案资源管理器**中，右键单击项目，然后单击 "**属性**"。

3. 在项目的 "属性" 窗口的 "**应用程序**" 选项卡上，将 "**目标框架**" 字段设置为 **.NET Framework 4**。

> [!NOTE]
> 即使在 "项目创建" 对话框中选择了 " **.NET Framework 4** "，也可能需要执行此操作。 目标框架不 **.NET Framework 4 客户端配置文件**。

## <a name="references"></a>reference
 必须将这些引用添加到 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 应用程序项目中：

- `Microsoft.VisualStudio.Modeling.Sdk.11.0`

  - 如果在 "**添加引用**" 对话框中的 " **.net** " 选项卡下看不到此，请单击 "**浏览**" 选项卡，然后导航到 `%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Common\Assemblies\`。

- DSL 程序集，你将在 DSL 项目的 bin 文件夹下找到该程序集。 其名称的格式通常为： *YourCompany*。*项目*`.Dsl.dll`。

## <a name="important-classes-in-the-dsl"></a>DSL 中的重要类
 在编写用于读取 DSL 的代码之前，你应该知道 DSL 生成的某些类的名称。 在 DSL 解决方案中，打开**dsl**项目，并在**GeneratedCode**文件夹中查找。 或者，在项目**引用**中双击 dsl 程序集，并在**对象浏览器**中打开 dsl 命名空间。

 这些是你应该识别的类：

- *YourDslRootClass* -这是 `DslDefinition.dsl` 中的根类的名称。

- *E* `SerializationHelper`-此类是在 DSL 项目 `SerializationHelper.cs` 中定义的。

- *E* `DomainModel`-此类是在 DSL 项目 `DomainModel.cs` 中定义的。

## <a name="reading-from-a-file"></a>从文件读取
 下面的示例旨在读取一个 DSL，其中重要的类如下所示：

- FamilyTreeModel

- FamilyTreeSerializationHelper

- FamilyTreeDomainModel

  此 DSL 中的其他域类为 Person。

```
using System;
using Microsoft.VisualStudio.Modeling;
using Company.FamilyTree; // Your DSL namespace

namespace StandaloneReadDslConsole
{ class Program
  { static void Main(string[] args)
    {
      // The path of a DSL model file:
      string dslModel = @"C:\FamilyTrees\Tudor.ftree";
      // Set up the Store to read your type of model:
      Store store = new Store(
        typeof(Company.FamilyTree.FamilyTreeDomainModel));
      // The Model type generated by the DSL:
      FamilyTreeModel familyTree;
      // All Store changes must be in a Transaction:
      using (Transaction t =
        store.TransactionManager.BeginTransaction("Load model"))
      {
        familyTree =
           FamilyTreeSerializationHelper.Instance.
              LoadModel(store, dslModel, null, null, null);
        t.Commit(); // Don't forget this!
      }
      // Now we can read the model:
      foreach (Person p in familyTree.People)
      {
        Console.WriteLine(p.Name);
        foreach (Person child in p.Children)
        {
          Console.WriteLine("    " + child.Name);
        }
} } } }
```

## <a name="saving-to-a-file"></a>保存到文件
 下面添加前面的代码会对模型进行更改，然后将其保存到文件中。

```
using (Transaction t =
  store.TransactionManager.BeginTransaction("update model"))
{
  // Create a new model element:
  Person p = new Person(store);
  // Set its embedding relationship:
  p.FamilyTreeModel = familyTree;
  // - same as: familyTree.People.Add(p);
  // Set its properties:
  p.Name = "Edward VI";
  t.Commit(); // Don't forget this!
}
// Save the model:
try
{
  SerializationResult result = new SerializationResult();
  FamilyTreeSerializationHelper.Instance
    .SaveModel(result, familyTree, @"C:\FamilyTrees\Tudor-upd.ftree");
  // Report any error:
  if (result.Failed)
  {
    foreach (SerializationMessage message in result)
    {
      Console.WriteLine(message);
    }
  }
}
catch (System.IO.IOException ex)
{ ... }
```
