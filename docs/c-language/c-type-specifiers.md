---
title: Specyfikatory typu C
ms.date: 01/29/2018
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
ms.openlocfilehash: 652388fdf345cab7878bbd8c054b769377b322a9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217158"
---
# <a name="c-type-specifiers"></a>Specyfikatory typu C

Specyfikatory typu w deklaracjach definiują typ deklaracji zmiennej lub funkcji.

## <a name="syntax"></a>Składnia

*specyfikator typu*: &nbsp; &nbsp; &nbsp; &nbsp; **`void`** &nbsp; &nbsp; &nbsp; &nbsp; **`char`** &nbsp; &nbsp; &nbsp; &nbsp; **`short`** &nbsp; &nbsp; &nbsp; &nbsp; **`int`** &nbsp; &nbsp; &nbsp; &nbsp; **`long`** &nbsp; &nbsp; &nbsp; &nbsp; **`float`** &nbsp; &nbsp; &nbsp; &nbsp; **`double`** &nbsp; &nbsp; &nbsp; &nbsp; **`signed`** &nbsp; &nbsp; &nbsp; &nbsp; **`unsigned`** &nbsp; &nbsp; &nbsp; &nbsp; element *struct-or-Union-specyfikatortype* &nbsp; &nbsp; &nbsp; &nbsp; *enum* - &nbsp; &nbsp; &nbsp; &nbsp; *name*

**`signed char`**, **`signed int`** , **`signed short int`** , I **podpisane długie int** , wraz z ich **`unsigned`** odpowiednikami i **`enum`** , są nazywane typami *całkowitymi* . **`float`** **`double`** Specyfikatory, i **`long double`** typu są określane jako typy *zmiennoprzecinkowe* lub *zmiennoprzecinkowe* . Można użyć dowolnego specyfikatora typu całkowitego lub zmiennoprzecinkowego w deklaracji zmiennej lub funkcji. Jeśli *specyfikator typu* nie jest podany w deklaracji, jest on traktowany jako **`int`** .

Opcjonalne słowa kluczowe **`signed`** i **`unsigned`** mogą poprzedzać lub korzystać z dowolnego typu całkowitego, z wyjątkiem **`enum`** i mogą być również używane jako Specyfikatory typu, w tym przypadku są one zrozumiałe **`signed int`** odpowiednio i **`unsigned int`** . W przypadku użycia samego słowa kluczowego przyjmuje się wartość **`int`** **`signed`** . W przypadku użycia samego słowa kluczowego **`long`** i **`short`** rozumie się jako **long int** i **`short int`** .

Typy wyliczeniowe są uznawane za typy podstawowe. Specyfikatory typów dla typów wyliczenia są omówione w [deklaracji wyliczenia](../c-language/c-enumeration-declarations.md).

Słowo kluczowe **`void`** ma trzy zastosowania: aby określić typ zwracany funkcji, aby określić listę typu argumentu dla funkcji, która nie przyjmuje argumentów, i określić wskaźnik do nieokreślonego typu. Możesz użyć typu, **`void`** Aby zadeklarować funkcje, które nie zwracają wartości ani zadeklarować wskaźnika dla nieokreślonego typu. Zobacz [argumenty](../c-language/arguments.md) , aby uzyskać informacje o tym **`void`** , kiedy pojawiają się one w nawiasach po nazwie funkcji.

**Specyficzne dla firmy Microsoft**

Sprawdzanie typu jest teraz zgodne ze standardem ANSI, co oznacza, że typ **`short`** i typ **`int`** są różnymi typami. Na przykład jest to zmiana definicji w kompilatorze języka Microsoft C, która została zaakceptowana przez poprzednie wersje kompilatora.

```C
int   myfunc();
short myfunc();
```

Ten następny przykład generuje również ostrzeżenie dotyczące pośrednika do różnych typów:

```C
int *pi;
short *ps;

ps = pi;  /* Now generates warning */
```

Kompilator języka Microsoft C generuje również ostrzeżenia o różnicach w znakach. Na przykład:

```C
signed int *pi;
unsigned int *pu

pi = pu;  /* Now generates warning */
```

**`void`** Wyrażenia typu są oceniane pod kątem efektów ubocznych. Nie można użyć (nieistniejącej) wartości wyrażenia, które ma typ **`void`** w dowolny sposób, ani nie można przekonwertować **`void`** wyrażenia (poprzez niejawną lub jawną konwersję) do dowolnego typu z wyjątkiem **`void`** . Jeśli używasz wyrażenia dowolnego innego typu w kontekście, w którym **`void`** wyrażenie jest wymagane, jego wartość zostanie odrzucona.

Aby zapewnić zgodność ze specyfikacją ANSI, wartość <strong>void \* \* </strong> nie może być używana jako <strong>int \* \* </strong>. **`void`** <strong>\*</strong> Można go użyć tylko jako wskaźnika do nieokreślonego typu.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Można utworzyć dodatkowe Specyfikatory typu z **`typedef`** deklaracjami, zgodnie z opisem w [deklaracji typedef](../c-language/typedef-declarations.md). Zobacz [Magazyn typów podstawowych](../c-language/storage-of-basic-types.md) , aby uzyskać informacje o rozmiarze poszczególnych typów.

## <a name="see-also"></a>Zobacz także

[Deklaracje i typy](../c-language/declarations-and-types.md)
