---
title: Anonimowe typy klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e4200548100804d1e64c16311875e85ffcdd717
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="anonymous-class-types"></a>Anonimowe typy klas
Klasy mogą być anonimowy — czyli może być zadeklarowana bez *identyfikator*. Jest to przydatne, gdy musisz zastąpić nazwę klasy o `typedef` nazwę, co przedstawiono poniżej:  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
> [!NOTE]
>  Korzystanie z klasy anonimowy w poprzednim przykładzie jest przydatne w celu zachowania zgodności z istniejącego kodu C. W niektórych kodu C, użycie `typedef` w połączeniu z struktury anonimowe jest powszechnie znane.  
  
 Anonimowe klasy także są przydatne w przypadku, gdy ma odwołanie do elementu członkowskiego klasy wrażenie, że nie zostały zawarte w osobnej klasy, tak jak poniżej:  
  
```  
struct PTValue  
{  
    POINT ptLoc;  
    union  
    {  
        int  iValue;  
        long lValue;  
    };  
};  
  
PTValue ptv;  
```  
  
 W powyższym kodzie `iValue` jest możliwy przy użyciu operatora wyboru elementu członkowskiego obiektu (**.**) w następujący sposób:  
  
```  
int i = ptv.iValue;  
```  
  
 Anonimowe klasy obowiązują pewne ograniczenia. (Aby uzyskać więcej informacji na temat związki anonimowe, zobacz [unie](../cpp/unions.md).) Anonimowe klasy:  
  
-   Nie może mieć konstruktora lub destruktora.  
  
-   Nie można przekazać jako argumenty do funkcji (chyba, że kontrola typów jest bezcelowe, przy użyciu elipsy).  
  
-   Nie można zwrócić wartości jako zwracane z funkcji.  
  
## <a name="anonymous-structs"></a>Struktury anonimowe  
  
### <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Rozszerzenia Microsoft C można zadeklarować zmiennej struktury w inną strukturę bez nadanie mu nazwy. Te struktury zagnieżdżone są nazywane struktury anonimowe. Struktury anonimowe są niedozwolone w C++.  
  
 Tak, jakby były członkami w strukturze zawierającego można uzyskać dostępu do elementów członkowskich struktury anonimowe.  
  
```  
// anonymous_structures.c  
#include <stdio.h>  
  
struct phone  
{  
    int  areacode;  
    long number;  
};  
  
struct person  
{  
    char   name[30];  
    char   gender;  
    int    age;  
    int    weight;  
    struct phone;    // Anonymous structure; no name needed  
} Jim;  
  
int main()  
{  
    Jim.number = 1234567;  
    printf_s("%d\n", Jim.number);     
}  
//Output: 1234567  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
