---
title: 如何： 测试和调试可视化工具 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9972951b1c5064fcc0582909976a234158ea096
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47482980"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>如何：测试和调试可视化工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[如何： 测试和调试可视化工具](https://docs.microsoft.com/visualstudio/debugger/how-to-test-and-debug-a-visualizer)。  
  
编写完可视化工具后，需要对其进行调试和测试。  
  
 测试可视化工具的一种方法是将它安装在 Visual Studio 中并从调试器窗口进行调用。 (请参阅[如何： 安装可视化工具](../debugger/how-to-install-a-visualizer.md)。)如果采用这种方法，则需要使用另一个 Visual Studio 实例附加和调试正在第一个调试器实例中运行的可视化工具。  
  
 一种更简单的调试可视化工具的方法，是从测试驱动程序运行可视化工具。 可视化工具 Api 轻松地创建此类驱动程序，称为*可视化工具开发宿主*。  
  
### <a name="to-create-a-visualizer-development-host"></a>创建可视化工具开发宿主  
  
1.  在调试器端类中，包含一个创建 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> 对象并调用其 show 方法的静态方法：  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     用于构造宿主的参数是数据对象（将显示在可视化工具 (`objectToVisualize`) 中）和调试器端类的类型。  
  
2.  添加下面的语句以调用 `TestShowVisualizer`。 如果可视化工具是在类库中创建的，则需要创建调用该类库的可执行文件，并将此语句放置到可执行文件中：  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     有关更完整的示例，请参阅[演练： 用 C# 编写可视化工具](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)。  
  
## <a name="see-also"></a>请参阅  
 [演练： 用 C# 编写可视化工具](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [如何： 安装可视化工具](../debugger/how-to-install-a-visualizer.md)   
 [创建自定义可视化工具](../debugger/create-custom-visualizers-of-data.md)


