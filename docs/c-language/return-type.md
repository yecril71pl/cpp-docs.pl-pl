---
title: Zwracany typ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08c81333d599411b180ebf5f0a00e1ab61536903
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076856"
---
# <a name="return-type"></a>Zwracany typ

Zwracany typ funkcji ustanawia rozmiar i typ wartości zwracanej przez funkcję i odpowiada specyfikatorowi typu w poniższej składni:

## <a name="syntax"></a>Składnia

*Definicja funkcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub> *atrybutu seq*<sub>zoptymalizowany pod kątem</sub> *deklaratora* *lista deklaracji*  <sub>zoptymalizowany pod kątem</sub> *compound-statement*

/\* *Atrybut seq* jest Specific dla Microsoft \*/

*Specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub>

*Specyfikator typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Krótka**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int8**  / \* specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int16**  / \* specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int32**  / \* specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int64**  / \* specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**długi**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Podwójne**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Podpisany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Bez znaku**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator struktury lub Unii*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu wyliczeniowego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Nazwa TypeDef*

*Specyfikator typu* można określić wszelkie podstawowego, struktury lub Unii. Jeśli nie dołączysz *Specyfikator typu*, zwracany typ `int` zakłada, że.

Zwracany typ podany w definicji funkcji musi odpowiadać zwracanej w deklaracjach funkcji w programie. Funkcja zwraca wartość po `return` zostaje wykonana instrukcja zawiera wyrażenie. Wyrażenie jest obliczane konwertowane na typ zwracanej wartości, jeśli niezbędne i zwrócony do punktu, w którym funkcja została wywołana. Jeśli funkcja jest zadeklarowana z typem zwracanym `void`wyrażenie nie jest obliczane i instrukcję return, która zawiera wyrażenie generuje ostrzeżenie.

Poniższe przykłady ilustrują wartości zwracane przez funkcję.

```C
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

Ten przykład definiuje `STUDENT` to typ `typedef` deklaracji i definiuje funkcję `sortstu` mieć `STUDENT` typ zwracany. Funkcja wybiera i zwraca jedną z jej argumentów dwie struktury. W kolejnych wywołaniach funkcji, kompilator sprawdza typy argumentów są `STUDENT`.

> [!NOTE]
> Wydajność można rozszerzyć za przekazywanie wskaźników do struktury, a nie całą strukturę.

```C
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

W tym przykładzie definiuje funkcji zwracającej wskaźnik do tablicy znaków. Funkcja przyjmuje dwie tablice znaków (parametry) jako argumenty i zwraca wskaźnik do krótszego dwóch ciągów. Wskaźnik do tablicy wskazuje na pierwszy elementów tablicy, a jego typ; ma w związku z tym, zwracany typ funkcji jest wskaźnikiem do typu `char`.

Nie należy deklarować funkcji z `int` zwracany typ przed wywołaniem, mimo że prototypy są zalecane, tak aby był włączony poprawny typ sprawdzania argumentów i zwracanych wartości.

## <a name="see-also"></a>Zobacz też

[Definicje funkcji języka C](../c-language/c-function-definitions.md)