---
title: Typ zwracany
ms.date: 11/04/2016
helpviewer_keywords:
- function return types
- return values [C++], function procedures
- function return types, syntax
- return values [C++]
- data types [C++], function return types
- return keyword [C++], function return types
- functions [C++], return types
ms.assetid: 3e5b8a97-b341-48c5-8be8-8986980ef586
ms.openlocfilehash: 1d905e02be02784b562b9d1a8f72a9bfa4057b9b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226330"
---
# <a name="return-type"></a>Typ zwracany

Zwracany typ funkcji ustala rozmiar i typ wartości zwracanej przez funkcję i odpowiada specyfikatorowi typu w składni poniżej:

## <a name="syntax"></a>Składnia

*definicja funkcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja-specyfikators*<sub>opt</sub> *Attribute-SEQ*<sub>opt</sub> *deklarator* *deklaracji-list*<sub>opt</sub> *złożone-instrukcja*

/\**atrybut-seq* jest specyficzny dla firmy Microsoft\*/

*specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja* *specyfikatora klasy magazynu* —<sub>wybór</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;Deklaracja *specyfikatora typu* *— wybór specyfikatorów*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;Deklaracja *kwalifikatora typu* *— wybór specyfikatorów*<sub>opt</sub>

*specyfikator typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`void`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`char`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`short`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`int`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__int8`** /\*Specyficzne dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__int16`** /\*Specyficzne dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__int32`** /\*Specyficzne dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__int64`** /\*Specyficzne dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`long`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`float`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`double`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`signed`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`unsigned`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-lub-Union-specyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum — specyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef — nazwa*

*Specyfikator typu* może określać dowolny typ podstawowy, struktura lub związek. Jeśli nie dołączysz *specyfikatora typu*, przyjmuje się typ zwracany **`int`** .

Zwracany typ określony w definicji funkcji musi być zgodny z typem zwracanym w deklaracjach funkcji w innym miejscu programu. Funkcja zwraca wartość, gdy **`return`** zostanie wykonana instrukcja zawierająca wyrażenie. Wyrażenie jest oceniane, konwertowane na typ wartości zwracanej w razie potrzeby i zwracane do punktu, w którym funkcja została wywołana. Jeśli funkcja jest zadeklarowana z typem zwracanym **`void`** , instrukcja return zawierająca wyrażenie generuje ostrzeżenie i wyrażenie nie jest oceniane.

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

Ten przykład definiuje `STUDENT` Typ z **`typedef`** deklaracją i definiuje funkcję, `sortstu` która ma być `STUDENT` typem zwracanym. Funkcja wybiera i zwraca jeden z dwóch argumentów struktury. W kolejnych wywołaniach funkcji kompilator sprawdza, czy typy argumentów są `STUDENT` .

> [!NOTE]
> Wydajność zostałaby ulepszona poprzez przekazanie wskaźników do struktury, a nie całej struktury.

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

Ten przykład definiuje funkcję zwracającą wskaźnik do tablicy znaków. Funkcja przyjmuje dwie tablice znakowe (ciągi) jako argumenty i zwraca wskaźnik do krótszych dwóch ciągów. Wskaźnik do tablicy wskazuje pierwszy element tablicy i ma jego typ; w ten sposób zwracany typ funkcji jest wskaźnikiem do typu **`char`** .

Nie musisz deklarować funkcji z **`int`** typem zwracanym przed wywołaniem ich, chociaż prototypy są zalecane, aby sprawdzać poprawność typu dla argumentów i zwracanych wartości.

## <a name="see-also"></a>Zobacz także

[Definicje funkcji języka C](../c-language/c-function-definitions.md)
