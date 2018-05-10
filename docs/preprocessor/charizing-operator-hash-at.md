---
title: Operator konwersji na znaki (#@) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9e0c0d140d937b7359ff3abf9c0eae145a89210
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="charizing-operator-"></a>Operator konwersji na znaki (#@)
**Microsoft Specific**  
  
 Operatora charizing można używać tylko z argumentami makr. Jeśli **#@** poprzedza parametrów formalnych w definicji makra, rzeczywisty argument jest ujęta w znaki apostrofu i traktowany jako znak po rozwinięciu makra. Na przykład:  
  
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