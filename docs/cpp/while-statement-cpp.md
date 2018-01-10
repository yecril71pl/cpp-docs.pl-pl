---
title: "while — instrukcja (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: while_cpp
dev_langs: C++
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e93d31457beb3c1546b55d303fd71566176a9367
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="while-statement-c"></a>while — instrukcja (C++)
Wykonuje *instrukcji* wielokrotnie do *wyrażenie* oblicza od zera.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      while ( expression )  
   statement  
```  
  
## <a name="remarks"></a>Uwagi  
 Badania *wyrażenie* ma miejsce przed każdym wykonywania pętli; w związku z tym `while` pętla jest wykonywana zero lub więcej razy. *wyrażenie* musi być typem całkowitym, typem wskaźnika lub typ klasy jednoznaczne konwersji na typy całkowite lub typu wskaźnika.  
  
 A `while` pętli można również przerwanie podczas [podziału](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), lub [zwracać](../cpp/return-statement-cpp.md) w instrukcji treści jest wykonywana. Użyj [kontynuować](../cpp/continue-statement-cpp.md) zakończyć bez zamykania bieżącej iteracji `while` pętli. **kontynuować** przekazuje formantu do następnej iteracji `while` pętli.  
  
 Poniższy kod używa `while` pętli, aby przyciąć, końcowy znak podkreślenia z ciągu:  
  
```  
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
  
 Warunek zakończenia jest obliczane w górnej części pętli. Jeśli nie ma żadnych końcowe znaki podkreślenia, pętli nigdy nie wykonuje.  
  
## <a name="see-also"></a>Zobacz też  
 [Iteracja — instrukcje](../cpp/iteration-statements-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [czy-while — instrukcja (C++)](../cpp/do-while-statement-cpp.md)   
 [for — instrukcja (C++)](../cpp/for-statement-cpp.md)   
 [Range-based for, instrukcja (C++)](../cpp/range-based-for-statement-cpp.md)