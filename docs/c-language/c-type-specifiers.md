---
title: Specyfikatory typu C
ms.date: 01/29/2018
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
ms.openlocfilehash: 1191cf4d2912cda535547f465fe4bfbedebe8fa2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313197"
---
# <a name="c-type-specifiers"></a>Specyfikatory typu C

Specyfikatory typu w deklaracjach definiują typ deklaracji zmiennej lub funkcji.

## <a name="syntax"></a>Składnia

*specyfikator typu* &nbsp; &nbsp; &nbsp;: &nbsp; **void** *typedef-name* **signed** *enum-specifier* **char** &nbsp; **short** &nbsp; **long** **int** **float** **double** **unsigned** *struct-or-union-specifier* char short int Long zmiennoprzecinkow podwójnie &nbsp;signed &nbsp;struct-or-Union-specyfikator &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;

**Znaki**ze znakiem signd, **int**, signed **short int**, i signed **Long** int, w połączeniu ze swoimi **niepodpisanymi** odpowiednikami i **wyliczeniem**, są nazywane typami *całkowitymi* . Specyfikatory typu **float**, **Double**i **Long Double** są określane jako typy *zmiennoprzecinkowe* lub *zmiennoprzecinkowe* . Można użyć dowolnego specyfikatora typu całkowitego lub zmiennoprzecinkowego w deklaracji zmiennej lub funkcji. Jeśli *specyfikator typu* nie jest podany w deklaracji, jest on traktowany jako **int**.

Opcjonalne słowa kluczowe **podpisane** i **niepodpisane** mogą poprzedzać lub korzystać z dowolnego typu całkowitego, z wyjątkiem **wyliczenia**, i mogą być używane osobno jako Specyfikatory typu, w tym przypadku są one rozumiane jako **niepodpisane int** i **unsigned int**. W przypadku użycia samego słowa kluczowego **int** jest założono, że jest **podpisana**. Jeśli są używane samodzielnie, słowa kluczowe o **długości długiej** i **krótkiej** są interpretowane jako **long int** i **short int**.

Typy wyliczeniowe są uznawane za typy podstawowe. Specyfikatory typów dla typów wyliczenia są omówione w [deklaracji wyliczenia](../c-language/c-enumeration-declarations.md).

Słowo kluczowe **void** ma trzy zastosowania: aby określić typ zwracany funkcji, aby określić listę typu argumentu dla funkcji, która nie przyjmuje argumentów, i określić wskaźnik do nieokreślonego typu. Można użyć typu **void** do zadeklarowania funkcji, które nie zwracają wartości ani do deklarowania wskaźnika do nieokreślonego typu. Zobacz [argumenty](../c-language/arguments.md) , aby uzyskać informacje na temat **void** , gdy pojawia się on w nawiasach po nazwie funkcji.

**Specyficzne dla firmy Microsoft**

Sprawdzanie typu jest teraz zgodne ze standardem ANSI, co oznacza, że typ **Short** i Type **int** są różnymi typami. Na przykład jest to zmiana definicji w kompilatorze języka Microsoft C, która została zaakceptowana przez poprzednie wersje kompilatora.

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

Kompilator języka Microsoft C generuje również ostrzeżenia o różnicach w znakach. Przykład:

```C
signed int *pi;
unsigned int *pu

pi = pu;  /* Now generates warning */
```

Wyrażenia typu **void** są oceniane pod kątem efektów ubocznych. Nie można użyć (nieistniejącej) wartości wyrażenia, które ma typ **void** w dowolny sposób, ani nie można przekonwertować wyrażenia **void** (poprzez niejawną lub jawną konwersję) do dowolnego typu z wyjątkiem **void**. Jeśli używasz wyrażenia dowolnego innego typu w kontekście, w którym jest wymagane wyrażenie **void** , jego wartość zostanie odrzucona.

Aby zapewnić zgodność ze specyfikacją ANSI, wartość <strong>void\* </strong> nie może być używana jako <strong>int\*</strong>. Tylko **void** <strong>\*</strong> może być używany jako wskaźnik do nieokreślonego typu.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Można utworzyć dodatkowe Specyfikatory typu z deklaracjami **typedef** , zgodnie z opisem w [deklaracji typedef](../c-language/typedef-declarations.md). Zobacz [Magazyn typów podstawowych](../c-language/storage-of-basic-types.md) , aby uzyskać informacje o rozmiarze poszczególnych typów.

## <a name="see-also"></a>Zobacz też

[Deklaracje i typy](../c-language/declarations-and-types.md)
