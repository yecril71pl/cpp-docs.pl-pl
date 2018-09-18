---
title: Deklaracje złożeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- unions
- union keyword [C], declarations
- variant records
ms.assetid: 978c6165-e0ae-4196-afa7-6d94e24f62f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b63ed026cf3dd90563bdd412107debfa6d516229
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110123"
---
# <a name="union-declarations"></a>Deklaracje złożeń

"Deklaracją złożenia" Określa zestaw wartości zmiennych i, opcjonalnie, tag nazewnictwa Unii. Wartości zmiennych są nazywane "Członkowie" Unii i mogą mieć różne typy. Unie są podobne do "rekordy wariantów" w innych językach.

## <a name="syntax"></a>Składnia

*struct-or-union-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struktury lub Unii* *identyfikator*<sub>zoptymalizowany pod kątem</sub> **{** *struktury deklaracji listy* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struktury lub Unii* *identyfikator*

*struct-or-union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**— Struktura**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Unia**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja — struktura*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura deklaracji listy* *deklaracji struktury*

Złożenia zawartości jest definiowany jako

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator kwalifikator listy* *struktury declarator-list***;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *specyfikator kwalifikator listy*<sub>zoptymalizowany pod kątem</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu* *specyfikator kwalifikator listy*<sub>zoptymalizowany pod kątem</sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator — struktura*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura declarator-list***,***deklaratora — struktura*

Zmienna o **Unii** typ przechowuje jedną z wartości zdefiniowanych przez tego typu. Te same zasady określają deklaracje struktur i związków. Unie może również mieć pól bitowych.

Elementy członkowskie związków nie może mieć typu niekompletnego typu `void`, lub typu funkcji. W związku z tym członkowie nie może być wystąpieniem elementu Unii, ale może być wskaźniki do typu złożenia, został zadeklarowany.

Deklaracja typu Unii jest tylko szablon. Pamięć nie jest zarezerwowana, dopóki ta zmienna została zgłoszona.

> [!NOTE]
> Jeśli zadeklarowano sumę dwóch typów jednej wartości są przechowywane, ale Unii odbywa się przy użyciu innego typu, wyniki są nieprzewidywalne. Na przykład sumę **float** i `int` jest zadeklarowana. A **float** wartości są przechowywane, ale program później dostęp do wartości jako `int`. W takiej sytuacji wartość będzie zależeć od pamięci wewnętrznej **float** wartości. Wartość całkowitą nie być wiarygodne.

## <a name="examples"></a>Przykłady

Poniżej przedstawiono przykłady Unii:

```C
union sign   /* A definition and a declaration */
{
    int svar;
    unsigned uvar;
} number;
```

Ten przykład definiuje zmienną typu Unia z `sign` wpisz i deklaruje zmienną o nazwie `number` zawierający dwa elementy członkowskie: `svar`, liczbą całkowitą ze znakiem i `uvar`, liczbą całkowitą bez znaku. Ta deklaracja umożliwia bieżącą wartość `number` mają być przechowywane jako znakiem czy bez znaku. Tag skojarzone z tego typu Unii jest `sign`.

```C
union               /* Defines a two-dimensional */
{                   /*  array named screen */
    struct
    {
      unsigned int icon : 8;
      unsigned color : 4;
    } window1;
    int screenval;
} screen[25][80];
```

`screen` Tablica zawiera elementy 2000. Każdy element tablicy jest poszczególnych Unii, z dwoma elementami członkowskimi: `window1` i `screenval`. `window1` Elementu członkowskiego jest strukturą za pomocą dwóch członków pola bitowego, `icon` i `color`. `screenval` Element członkowski jest `int`. W dowolnym momencie każdy element złożenia przechowuje albo `int` reprezentowany przez `screenval` lub struktury, reprezentowane przez `window1`.

**Microsoft Specific**

Zagnieżdżone Unii mogą być deklarowane anonimowo, gdy należą innej struktury lub Unii. Jest to przykład pustego Unii:

```C
struct str
{
    int a, b;
    union            / * Unnamed union */
    {
      char c[4];
      long l;
      float f;
   };
   char c_array[10];
} my_str;
.
.
.
my_str.l == 0L;  /* A reference to a field in the my_str union */
```

Unie często są zagnieżdżone w obrębie struktury, która zawiera pole, dzięki czemu typu danych zawartych w Unii w danym momencie. Jest to przykład deklaracji dla takich Unii:

```C
struct x
{
    int type_tag;
    union
    {
      int x;
      float y;
    }
}
```

Zobacz [składowe struktury i złożenia](../c-language/structure-and-union-members.md) uzyskać informacji na temat odwołujące się do Unii.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)