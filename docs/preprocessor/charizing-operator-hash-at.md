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
ms.openlocfilehash: c6aa18936497f0415da331697aceb26f26345500
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42464530"
---
# <a name="charizing-operator-"></a>Operator konwersji na znaki (#@)
**Microsoft Specific**  
  
Charizing operatora można używać tylko w przypadku argumentów makra. Jeśli `#@` poprzedza parametrów formalnych w definicji makra, rzeczywisty argument jest ujęty w znaki pojedynczego cudzysłowu i traktowany jako znak, po rozwinięciu makra. Na przykład:  
  
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
  
Znak pojedynczego cudzysłowu nie można użyć z operatorem charizing.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 
[Operatory preprocesora](../preprocessor/preprocessor-operators.md)