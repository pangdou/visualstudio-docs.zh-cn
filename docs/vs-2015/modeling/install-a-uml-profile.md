---
title: 安装 UML 配置文件 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, profiles
ms.assetid: 586f9ba5-4d01-4a1d-b001-32e2efaa4f24
caps.latest.revision: 13
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 47346af32cf1b86ddf2f526e271127e4bde2da95
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47483591"
---
# <a name="install-a-uml-profile"></a>安装 UML 配置文件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[安装 UML 配置文件](https://docs.microsoft.com/visualstudio/modeling/install-a-uml-profile)。  
  
你可以使用 UML 配置文件来扩展 Visual Studio。 使用配置文件可以向在 UML 模型中创建的元素添加构造型及其他属性。 若要查看支持此功能的 Visual Studio 的版本，请参阅 [体系结构和建模工具的版本支持](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
 收到使用配置文件创建的 UML 模型时，除非你安装相同配置文件，否则将不会显示某些属性。  
  
 在 Visual Studio 扩展内部分发配置文件。 扩展还可能包含其他功能，如菜单命令。 有关详细信息，请参阅[管理 Visual Studio 扩展](http://go.microsoft.com/fwlink/?LinkId=160728)。  
  
### <a name="to-install-a-uml-profile-on-your-computer"></a>在计算机上安装 UML 配置文件  
  
1.  应以 Visual Studio 扩展 (`.vsix`) 文件的形式向你提供了该配置文件。 同一文件中可能有其他功能。  
  
     将 `.vsix` 文件移到计算机上方便的位置。  
  
2.  在 Windows 资源管理器（或文件资源管理器）中双击 `.vsix` 文件，或在 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 中打开它。  
  
3.  单击**安装**中出现的对话框。  
  
4.  若要卸载或临时禁用该扩展，打开**扩展管理器**从**工具**菜单。  
  
### <a name="to-uninstall-or-disable-a-profile-extension"></a>卸载或禁用配置文件扩展  
  
1.  在 Visual Studio**工具**菜单上，单击**扩展管理器**。  
  
2.  单击你想要删除，然后依次扩展**禁用**或**卸载**。  
  
## <a name="see-also"></a>请参阅  
 [自定义模型使用配置文件和构造型](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [定义用于扩展 UML 的配置文件](../modeling/define-a-profile-to-extend-uml.md)


