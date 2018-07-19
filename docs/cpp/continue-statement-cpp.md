---
title: Continue — instrukcja (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- continue_cpp
dev_langs:
- C++
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97422a09f890686c4d414eea13da7db891494cc4
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947954"
---
# <a name="continue-statement-c"></a>continue — instrukcja (C++)
Wymusza transfer kontroli do kontrolowania wyrażenia najmniejszy otaczający [czy](../cpp/do-while-statement-cpp.md), [dla](../cpp/for-statement-cpp.md), lub [podczas](../cpp/while-statement-cpp.md) pętli.  
  
## <a name="syntax"></a>Składnia  
  
```  
continue;  
```  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie pozostałe instrukcje w bieżącej iteracji nie zostaną wykonane. Następnej iteracji pętli jest określane w następujący sposób:  
  
-   W **czy** lub **podczas** pętli, następnej iteracji należy zacząć od reevaluating kontrolowanie wyrażenia **czy** lub **podczas** instrukcji.  
  
-   W **dla** pętli (przy użyciu składni `for`(`init-expr`; `cond-expr`; `loop-expr`)), `loop-expr` klauzula jest wykonywany. A następnie `cond-expr` klauzula jest ponownie oceniane i, w zależności od wyniku pętli albo kończy się lub występuje innej iteracji.  
  
 W poniższym przykładzie pokazano sposób, w jaki **nadal** instrukcja może być używana do obejścia sekcje kodu i rozpocząć kolejnej iteracji pętli.  
  
## <a name="example"></a>Przykład  
  
```cpp 
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