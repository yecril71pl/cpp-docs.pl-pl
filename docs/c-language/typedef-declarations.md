---
title: Deklaracje typedef
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, typedef
- typedef declarations
- types [C], declarations
ms.assetid: e92a3b82-9269-4bc6-834a-6f431ccac83e
ms.openlocfilehash: 3d477e33def7168d01f9c5f8a64579fed0b497eb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87190068"
---
# <a name="typedef-declarations"></a>Deklaracje typedef

Deklaracja typedef jest deklaracją z elementem TypeDef jako klasą magazynu. Deklarator zostanie nowym typem. Za pomocą deklaracji typedef można tworzyć krótsze lub bardziej zrozumiałe nazwy dla typów już zdefiniowanych przez C lub dla zadeklarowanych typów. Nazwy zdefiniowane przez typedef pozwalają na hermetyzację szczegółów implementacji, które mogą się zmieniać.

Deklaracja typedef jest interpretowana w taki sam sposób jak zmienna lub funkcja deklaracji, ale identyfikator, zamiast założeniu, że typ określony przez deklarację, będzie synonimem typu.

## <a name="syntax"></a>Składnia

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracje-specyfikatory init-deklarator-list*<sub>opt</sub> **;**

*specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja specyfikatora klasy magazynu*—<sub>wybór</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja specyfikatora typu — wybór specyfikatorów*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja kwalifikatora typu — wybór specyfikatorów*<sub>opt</sub>

*specyfikator klasy magazynu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`typedef`**

*specyfikator typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`void`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`char`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`short`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`int`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`long`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`float`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`double`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`signed`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`unsigned`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-lub-Union-specyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum — specyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef — nazwa*

*typedef-Name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikatora*

Należy zauważyć, że deklaracja typedef nie tworzy typów. Tworzy synonimy dla istniejących typów lub nazwy typów, które można określić w inny sposób. Gdy nazwa typedef jest używana jako specyfikator typu, można ją połączyć z pewnymi specyfikatorami typu, ale nie z innymi. Dopuszczalne Modyfikatory obejmują **`const`** i **`volatile`** .

Nazwy typedef współdzielą przestrzeń nazw z identyfikatorami zwykłymi (zobacz [spacje nazw](../c-language/name-spaces.md) , aby uzyskać więcej informacji). Program może mieć więc nazwę typedef i identyfikator o zakresie lokalnym o tej samej nazwie. Na przykład:

```C
typedef char FlagType;

int main()
{
}

int myproc( int )
{
    int FlagType;
}
```

Podczas deklarowania identyfikatora o zakresie lokalnym o tej samej nazwie co element typedef lub podczas deklarowania elementu struktury lub unii w tym samym zakresie lub w zakresie wewnętrznym, należy określić specyfikator typu. Ten przykład ilustruje to ograniczenie:

```C
typedef char FlagType;
const FlagType x;
```

Aby ponownie użyć nazwy `FlagType` dla identyfikatora, elementu struktury lub unii musi zostać dostarczony typ:

```C
const int FlagType;  /* Type specifier required */
```

Nie wystarczy powiedzieć

```C
const FlagType;      /* Incomplete specification */
```

ponieważ `FlagType` uważa się za część typu, a nie identyfikatora, który jest ponownie deklarowany. Taką deklarację uważa się za niedozwoloną, tak jak

```C
int;  /* Illegal declaration */
```

Można zadeklarować dowolny typ z typedef, w tym wskaźnik, funkcję i typy tablic. Można zadeklarować nazwę typedef wskaźnika na strukturę lub unię przed zdefiniowaniem struktury lub unii, tak długo jak definicja ma taką samą widoczność jak deklaracja.

Nazwy typedef mogą służyć do poprawienia czytelności kodu. Wszystkie trzy z poniższych deklaracji `signal` określają dokładnie ten sam typ, a pierwszy bez używania nazw typedef.

```C
typedef void fv( int ), (*pfv)( int );  /* typedef declarations */

void ( *signal( int, void (*) (int)) ) ( int );
fv *signal( int, fv * );   /* Uses typedef type */
pfv signal( int, pfv );    /* Uses typedef type */
```

## <a name="examples"></a>Przykłady

Poniższe przykłady ilustrują deklaracje typedef:

```C
typedef int WHOLE; /* Declares WHOLE to be a synonym for int */
```

Należy pamiętać, że `WHOLE` można teraz użyć w deklaracji zmiennej, takiej jak `WHOLE i;` lub `const WHOLE i;` . Jednakże deklaracja `long WHOLE i;` jest niedozwolona.

```C
typedef struct club
{
    char name[30];
    int size, year;
} GROUP;
```

Ta instrukcja deklaruje `GROUP` jako typ struktury z trzema składowymi. Ponieważ tag struktury, `club` ,,,, jest również określony, `GROUP` w deklaracjach może być używany element typedef Name () lub tag Structure. Musisz użyć słowa kluczowego struct ze znacznikiem i nie można użyć słowa kluczowego struct z nazwą typedef.

```C
typedef GROUP *PG; /* Uses the previous typedef name
                      to declare a pointer            */
```

Typ `PG` jest zadeklarowany jako wskaźnik do `GROUP` typu, który z kolei jest zdefiniowany jako typ struktury.

```C
typedef void DRAWF( int, int );
```

Ten przykład zawiera typ `DRAWF` dla funkcji zwracającej brak wartości i pobierającej dwa argumenty int. Oznacza to na przykład, że deklaracja

```C
DRAWF box;
```

jest odpowiednikiem deklaracji

```C
void box( int, int );
```

## <a name="see-also"></a>Zobacz także

[Deklaracje i typy](../c-language/declarations-and-types.md)
