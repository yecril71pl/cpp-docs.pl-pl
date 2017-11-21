---
title: "Kontynuuj — instrukcja (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: continue_cpp
dev_langs: C++
helpviewer_keywords: continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7ae5093f26cb46b30cf01d453a51df2585bee534
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="continue-statement-c"></a>continue — instrukcja (C++)
Wymusza przekazanie sterowania do kontrolowania wyrażenia najmniejszą otaczającej [czy](../cpp/do-while-statement-cpp.md), [dla](../cpp/for-statement-cpp.md), lub [podczas](../cpp/while-statement-cpp.md) pętli.  
  
## <a name="syntax"></a>Składnia  
  
```  
continue;  
```  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie pozostałe instrukcje w bieżącej iteracji nie są wykonywane. Następnej iteracji pętli jest określane w następujący sposób:  
  
-   W `do` lub `while` pętli następnej iteracji rozpoczyna się od wyrażenia kontrolowanie reevaluating `do` lub `while` instrukcji.  
  
-   W `for` pętli (przy użyciu składni `for`(`init-expr`; `cond-expr`; `loop-expr`)), `loop-expr` klauzuli jest wykonywana. Następnie przy użyciu `cond-expr` klauzuli jest ponownie oceniane i, w zależności od wyniku pętli albo kończy się lub innego iteracji.  
  
 W poniższym przykładzie przedstawiono sposób `continue` instrukcji można użyć do obejścia fragmentów kodu i rozpocząć następnej iteracji pętli.  
  
## <a name="example"></a>Przykład  
  
```  
// continue_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        i++;  
        printf_s("before the continue\n");  
        continue;  
        printf("after the continue, should never print\n");  
     } while (i < 3);  
  
     printf_s("after the do loop\n");  
}  
```  
  
```Output  
before the continue  
before the continue  
before the continue  
after the do loop  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje skoku](../cpp/jump-statements-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)