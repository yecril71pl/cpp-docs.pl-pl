---
title: Operator konwersji na znaki (#@) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#@'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6521322e7a71d8e76b657fb8580157c036e881b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="charizing-operator-"></a>Operator konwersji na znaki (#@)
**Microsoft Specific**  
  
 Operatora charizing można używać tylko z argumentami makr. Jeśli  **#@**  poprzedza parametrów formalnych w definicji makra, rzeczywisty argument jest ujęta w znaki apostrofu i traktowany jako znak po rozwinięciu makra. Na przykład:  
  
```  
#define makechar(x)  #@x  
```  
  
 powoduje, że instrukcja  
  
```  
a = makechar(b);  
```  
  
 Aby rozszerzyć, aby  
  
```  
a = 'b';  
```  
  
 Znak pojedynczego cudzysłowu nie można używać z operatorem charizing.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory preprocesora](../preprocessor/preprocessor-operators.md)