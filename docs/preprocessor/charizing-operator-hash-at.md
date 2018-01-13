---
title: Operator konwersji na znaki (#@) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#@'
dev_langs: C++
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 933e97732462b61919d9e5a1e73f2a72d26ea01b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="charizing-operator-"></a>Operator konwersji na znaki (#@)
**Dotyczące firmy Microsoft**  
  
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