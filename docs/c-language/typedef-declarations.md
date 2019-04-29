---
title: Deklaracje typedef
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, typedef
- typedef declarations
- types [C], declarations
ms.assetid: e92a3b82-9269-4bc6-834a-6f431ccac83e
ms.openlocfilehash: b4bf7bc82cdf792e5a23f6d5533cc4d800fe4252
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346109"
---
# <a name="typedef-declarations"></a>Deklaracje typedef

Deklaracji typedef jest deklaracją przy użyciu elementu typedef jako klasa magazynu. Deklarator staje się nowym typem. Deklaracje typedef służy do konstruowania krótszy bardziej znaczących nazw typów już zdefiniowanych przez C lub typy, które zostały zadeklarowane. Nazwy zdefiniowane przez typedef pozwalają na hermetyzację szczegółów implementacji, które mogą się zmieniać.

Deklaracji typedef jest interpretowany w taki sam sposób, jak zmienna lub deklaracji funkcji, ale identyfikator, a nie typu określonego przez deklarację, zakładając, że staje się synonimem typu.

## <a name="syntax"></a>Składnia

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji init-declarator-list*<sub>zoptymalizowany pod kątem</sub> **;**

*Specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji Storage-class-specifier*<sub>zoptymalizowany pod kątem</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji Specyfikator typu*<sub>zoptymalizowany pod kątem</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji kwalifikator typu*<sub>zoptymalizowany pod kątem</sub>

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Element TypeDef**

*Specyfikator typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**długi**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Podpisany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Bez znaku**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu wyliczeniowego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*Nazwa TypeDef*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

Należy pamiętać, że deklaracji typedef nie tworzy typy. Tworzy synonimy dla istniejących typów lub nazwy dla typów, które można określić w inny sposób. Gdy nazwa typedef jest używana jako specyfikatora typu, można ją połączyć z niektórych specyfikatory typu, ale innych nie. Modyfikatory dopuszczalne obejmują **const** i `volatile`.

Nazwy elementów TypeDef udostępnianie przestrzeń nazw ze zwykłymi identyfikatorami (zobacz [przestrzenie nazw](../c-language/name-spaces.md) Aby uzyskać więcej informacji). Program może mieć więc nazwę typedef i identyfikator o zakresie lokalnym o tej samej nazwie. Na przykład:

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

Podczas deklarowania identyfikatora o zakresie lokalnym o tej samej nazwie co element typedef lub podczas deklarowania elementu struktury lub unii w tym samym zakresie lub w zakresie wewnętrznym, należy określić specyfikator typu. Ten przykład ilustruje tego ograniczenia:

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

Nazwy elementów TypeDef można zwiększyć czytelność kodu. Wszystkie trzy następujące deklaracje `signal` Określ dokładnie tego samego typu, najpierw bez wprowadzania Użyj dowolnej nazwy elementów typedef.

```C
typedef void fv( int ), (*pfv)( int );  /* typedef declarations */

void ( *signal( int, void (*) (int)) ) ( int );
fv *signal( int, fv * );   /* Uses typedef type */
pfv signal( int, pfv );    /* Uses typedef type */
```

## <a name="examples"></a>Przykłady

W poniższych przykładach pokazano deklaracje typedef:

```C
typedef int WHOLE; /* Declares WHOLE to be a synonym for int */
```

Należy pamiętać, że `WHOLE` można teraz używać w deklaracji zmiennej takich jak `WHOLE i;` lub `const WHOLE i;`. Jednak deklaracji `long WHOLE i;` będzie niedozwolone.

```C
typedef struct club
{
    char name[30];
    int size, year;
} GROUP;
```

Ta instrukcja deklaruje `GROUP` jako typ struktury z trzema elementami członkowskimi. Ponieważ tag struktury `club`, również jest określony, nazwa typedef (`GROUP`) lub tag struktury mogą być używane w deklaracjach. Należy użyć struct, słowo kluczowe z tagu, a nazwa typedef nie można używać struct, słowo kluczowe.

```C
typedef GROUP *PG; /* Uses the previous typedef name
                      to declare a pointer            */
```

Typ `PG` jest zadeklarowany jako wskaźnik do `GROUP` typ, który z kolei jest zdefiniowana jako typ struktury.

```C
typedef void DRAWF( int, int );
```

W poniższym przykładzie przedstawiono typ `DRAWF` dla funkcji niezwracającej wartości i biorąc dwa argumenty typu int. Oznacza to, na przykład, że deklaracja

```C
DRAWF box;
```

jest równoważna z deklaracją

```C
void box( int, int );
```

## <a name="see-also"></a>Zobacz także

[Deklaracje i typy](../c-language/declarations-and-types.md)
