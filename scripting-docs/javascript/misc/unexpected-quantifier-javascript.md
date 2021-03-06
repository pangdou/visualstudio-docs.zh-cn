---
title: 意外的限定符（JavaScript） |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da4ff08ae667b868670364c7ad6b9a6b69ae6ad3
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815326"
---
# <a name="unexpected-quantifier-javascript"></a>意外的限定符 (JavaScript)
编写正则表达式搜索模式时，创建的模式元素具有非法的重复因子。 例如，模式  
  
```js
/^+/  
```  
  
 是非法的，因为元素 ^ （输入的开头）不能具有重复因子。 下表列出了不能有重复因素的元素。  
  
|元素|描述|  
|-------------|-----------------|  
|^|输入的开头|  
|$|输入结束|  
|\b|字边界|  
|\B|非单词边界|  
|*|零次或多次重复|  
|+|一个或多个重复项|  
|?|零次或一次重复|  
|北|n 重复|  
|{n，}|n 次或多次重复|  
|{n，m}|从 n 到 m 次重复，包含|  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
- 请确保搜索模式元素仅包含法律重复因素。  
  
## <a name="see-also"></a>请参阅  
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [正则表达式语法（JavaScript）](https://msdn.microsoft.com/library/1400241x)