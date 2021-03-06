---
title: 模板内容元素（可视化工作室模板） |微软文档
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 577ce71d3900947cde1de9a1e913124ab778a1ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699236"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent 元素（Visual Studio 模板）

指定模板的内容。

元素层次结构：

```xml
<VSTemplate>
  <TemplateContent>
```

## <a name="syntax"></a>语法

```xml
<TemplateContent>
    ...
</TemplateContent>
```

## <a name="attributes-and-elements"></a>特性和元素
 下列各节描述了特性、子元素和父元素。

### <a name="attributes"></a>特性

|特性|描述|
|---------------|-----------------|
|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|指定是否从模板创建项目时生成解决方案。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定多项目模板的组织和内容。|
|[Project](../extensibility/project-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定要添加到项目的文件或目录。|
|[参考](../extensibility/references-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定项目模板所需的程序集引用。|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|可选元素。<br /><br /> 指定模板中包含的文件。|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定从模板创建项目或项目时要使用的任何自定义参数。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必需元素。<br /><br /> 包含项目模板、项目模板或初学者工具包的所有元数据。|

## <a name="remarks"></a>备注
 `TemplateContent`是必需的元素。

## <a name="example"></a>示例
 下面的示例显示了[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]应用程序的项目模板的元数据。

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs</ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>请参阅

- [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)
- [创建项目和项目模板](../ide/creating-project-and-item-templates.md)
