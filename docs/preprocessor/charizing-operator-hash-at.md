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
ms.openlocfilehash: 1920d8183607140ebe38aaf56a447bc9cd3010f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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