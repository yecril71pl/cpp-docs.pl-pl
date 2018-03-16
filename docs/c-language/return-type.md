---
title: Zwracany typ | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- function return types
- return values [C++], function procedures
- function return types, syntax
- return values [C++]
- data types [C++], function return types
- return keyword [C++], function return types
- functions [C++], return types
ms.assetid: 3e5b8a97-b341-48c5-8be8-8986980ef586
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9768baa53e39f1b3243aba24385d592010c3d81a
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="return-type"></a>Zwracany typ
Zwracany typ funkcji określa rozmiar i typ wartości zwracanej przez funkcję i odpowiada specyfikatora typu z poniższą składnią:  
  
## <a name="syntax"></a>Składnia  
 *Definicja funkcji*:  
 *Specyfikatory deklaracji* opt*seq atrybutu* opt*lista deklaracji deklarator* opt*złożonej instrukcji*  
  
 /\* *Atrybut seq* jest Specific Microsoft * /  
  
 *Specyfikatory deklaracji*:  
 *Specyfikatory deklaracji Specyfikator klasy magazynu* opcjonalnych  
  
 *Specyfikatory deklaracji specyfikatora typu* opcjonalnych  
  
 *Specyfikatory deklaracji kwalifikator typu* opcjonalnych  
  
 *Specyfikator typu*:  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **Podpisany**  
  
 **Bez znaku**  
  
 *struct-or-union-specifier*  
  
 *enum-specifier*  
  
 *Nazwa typu TypeDef*  
  
 *Specyfikatora typu* można określić żadnych podstawowe, struktury lub Unii. Jeśli nie zostanie uwzględniony *specyfikatora typu*, zwracany typ `int` zakłada, że.  
  
 Zwracany typ podane w definicji funkcji musi pasuje do zwracanego typu w deklaracjach funkcji w programie. Funkcja zwraca wartość po `return` instrukcji zawierającej wyrażenie jest wykonywana. Wyrażenie jest obliczane konwertowane na typ zwracanej wartości, jeśli to konieczne i zwrócony do punktu, w którym została wywołana funkcja. Funkcja zadeklarowana ze zwracanego typu `void`, instrukcja return zawiera wyrażenie generuje ostrzeżenie i nie jest obliczane wyrażenie.  
  
 Poniższe przykłady przedstawiają wartości zwracane przez funkcję.  
  
```  
typedef struct    
{  
    char name[20];  
    int id;  
    long class;  
} STUDENT;  
  
/* Return type is STUDENT: */  
  
STUDENT sortstu( STUDENT a, STUDENT b )  
{  
    return ( (a.id < b.id) ? a : b );  
}  
```  
  
 W tym przykładzie definiuje `STUDENT` to typ `typedef` deklaracji i definiuje funkcję `sortstu` ma `STUDENT` typ zwracany. Funkcja wybiera i zwraca jedną z jego struktury dwóch argumentów. W kolejnych wywołaniach funkcji kompilator sprawdza typy argumentu są `STUDENT`.  
  
> [!NOTE]
>  Wydajność można rozszerzyć za przekazywanie wskaźników do struktury, a nie całą strukturę.  
  
```  
char *smallstr( char s1[], char s2[] )  
{  
    int i;  
  
    i = 0;  
    while ( s1[i] != '\0' && s2[i] != '\0' )  
        i++;  
    if ( s1[i] == '\0' )  
        return ( s1 );  
    else  
        return ( s2 );  
}  
```  
  
 W tym przykładzie definiuje funkcji zwracającej wskaźnik do tablicy znaków. Funkcja przyjmuje dwie tablice znaków (ciągi) jako argumenty i zwraca wskaźnik do krótszego z dwóch ciągów. Wskazuje wskaźnika do tablicy pierwszy elementów tablicy i typ; w związku z tym zwracany typ funkcji jest wskaźnik do typu `char`.  
  
 Nie należy deklarować funkcje z `int` typ zwracany przed wywołaniem, mimo że prototypy są zalecane, tak aby był włączony poprawnego typu sprawdzanie argumentów i zwracanych wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Definicje funkcji języka C](../c-language/c-function-definitions.md)