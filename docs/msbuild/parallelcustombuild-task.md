---
title: ParallelCustomBuild 任务 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 0d8a171d393f629d0b6ab3a7fc61ad37862b0da1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279264"
---
# <a name="parallelcustombuild-task"></a>ParallelCustomBuild 任务

运行 [CustomBuild 任务](../msbuild/custombuild-task.md)的并行实例。

## <a name="parameters"></a>参数

下表介绍了 ParallelCustomBuild  任务的参数。

|参数|说明|
|---------------|-----------------|
|**BreakOnFirstFailure**|可选的 bool  参数。|
|**MaxItemsInBatch**|可选 **int** 参数。|
|**MaxProcesses**|可选 **int** 参数。|
|**Sources**|必需的 **ITaskItem[]** 参数。|

## <a name="see-also"></a>另请参阅

[任务参考](../msbuild/msbuild-task-reference.md)