---
title: while — instrukcja (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- while_cpp
dev_langs:
- C++
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc826b588f133abb93c9942e7907dd8b0fce9574
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947778"
---
# <a name="while-statement-c"></a>while — instrukcja (C++)
Wykonuje *instrukcji* wielokrotnie do momentu *wyrażenie* osiągnie wartość zero.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
while ( expression )  
   statement  
```  
  
## <a name="remarks"></a>Uwagi  
 Test *wyrażenie* ma miejsce przed każdym wykonaniu pętli, dlatego **podczas** pętla jest wykonywana zero lub więcej razy. *wyrażenie* musi być typem całkowitym, typem wskaźnika lub typu klasy za pomocą jednoznaczną konwersję na całkowite lub typu wskaźnika.  
  
 A **podczas** pętli można także zakończyć, gdy [podziału](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), lub [zwracają](../cpp/return-statement-cpp.md) w ramach instrukcja zostaje wykonana. Użyj [nadal](../cpp/continue-statement-cpp.md) zakończenie bieżącej iteracji bez zamykania **podczas** pętli. **Kontynuuj** przekazuje kontrolę do następnej iteracji **podczas** pętli.  
  
 Poniższy kod używa **podczas** pętli można przycięcia końcowe podkreślenia z ciągu:  
  
```cpp 
// while_statement.cpp  
  
#include <string.h>  
#include <stdio.h>  
char *trim( char *szSource )  
{  
    char *pszEOS = 0;  
  
    //  Set pointer to character before terminating NULL  
    pszEOS = szSource + strlen( szSource ) - 1;  
  
    //  iterate backwards until non '_' is found   
    while( (pszEOS >= szSource) && (*pszEOS == '_') )  
        *pszEOS-- = '\0';  
  
    return szSource;  
}  
int main()  
{  
    char szbuf[] = "12345_____";  
  
    printf_s("\nBefore trim: %s", szbuf);  
    printf_s("\nAfter trim: %s\n", trim(szbuf));  
}  
```  
  
 Warunku zakończenia jest oceniany u góry pętli. Jeśli nie ma żadnych końcowe znaki podkreślenia, pętla nigdy nie jest wykonywany.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje iteracji](../cpp/iteration-statements-cpp.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [czy-while — instrukcja (C++)](../cpp/do-while-statement-cpp.md)   
 [for — instrukcja (C++)](../cpp/for-statement-cpp.md)   
 [Range-based for, instrukcja (C++)](../cpp/range-based-for-statement-cpp.md)