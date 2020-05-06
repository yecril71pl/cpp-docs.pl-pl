---
title: Kwalifikatory typów
ms.date: 11/04/2016
helpviewer_keywords:
- volatile keyword [C], type qualifier
- type qualifiers
- volatile keyword [C]
- qualifiers for types
- const keyword [C]
- memory, access using volatile
- volatile keyword [C], type specifier
ms.assetid: bb4c6744-1dd7-40a8-b4eb-f5585be30908
ms.openlocfilehash: a5cb7ab3de8938b77dc95be3ee442f71d3b18b42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344801"
---
# <a name="type-qualifiers"></a>Kwalifikatory typów

Kwalifikatory typu dają jedną z dwóch właściwości do identyfikatora. Kwalifikator typu **const** deklaruje obiekt jako niemodyfikowalny. Kwalifikator `volatile` typu deklaruje element, którego wartość może być słusznie zmieniona przez coś poza formantem programu, w którym występuje, na przykład współbieżnie wykonywany wątek.

Dwa Kwalifikatory typu, **const** i `volatile`, mogą występować tylko raz w deklaracji. Kwalifikatory typu mogą występować z dowolnym specyfikatorem typu; nie mogą jednak występować po pierwszym przecinku w deklaracji wielu elementów. Na przykład następujące deklaracje są dozwolone:

```
typedef volatile int VI;
const int ci;
```

Te deklaracje nie są dozwolone:

```
typedef int *i, volatile *vi;
float f, const cf;
```

Kwalifikatory typu są istotne tylko podczas uzyskiwania dostępu do identyfikatorów jako wartości l w wyrażeniach. Aby uzyskać informacje na temat wartości l i wyrażeń, zobacz [wyrażenia wartości l i R](../c-language/l-value-and-r-value-expressions.md) .

## <a name="syntax"></a>Składnia

*kwalifikator typu*: **constvolatile**

Poniżej przedstawiono prawne elementy **stałe** i `volatile` deklaracje:

```
int const *p_ci;       /* Pointer to constant int */
int const (*p_ci);     /* Pointer to constant int */
int *const cp_i;       /* Constant pointer to int */
int (*const cp_i);     /* Constant pointer to int */
int volatile vint;     /* Volatile integer        */
```

Jeśli specyfikacja typu tablicy zawiera kwalifikatory typu, element jest kwalifikowany, a nie typ tablicy. Jeśli specyfikacja typu funkcji zawiera kwalifikatory, zachowanie jest niezdefiniowane. Żadna `volatile` lub **stała** nie ma wpływu na zakres wartości lub właściwości arytmetyczne obiektu.

Ta lista zawiera opis sposobu używania **const** i `volatile`.

- Słowo kluczowe **const** może służyć do modyfikowania dowolnego typu podstawowego lub agregacji lub wskaźnika do obiektu dowolnego typu lub `typedef`. Jeśli element jest zadeklarowany tylko jako kwalifikator typu **const** , jego typ jest traktowany jako **const int**. Zmienną **const** można zainicjować lub można ją umieścić w regionie magazynu tylko do odczytu. Słowo kluczowe **const** jest przydatne do deklarowania wskaźników do **const** , ponieważ wymaga, aby funkcja nie zmieniła wskaźnika w jakikolwiek sposób.

- Kompilator zakłada, że w dowolnym momencie w programie `volatile` zmienna może być dostępna przez nieznany proces, który używa lub modyfikuje jego wartość. Z tego względu, niezależnie od optymalizacji określonych w wierszu polecenia, należy wygenerować kod dla każdego przypisania lub odwołania do `volatile` zmiennej, nawet jeśli wydaje się, że nie ma żadnego wpływu.

   Jeśli `volatile` jest używany samodzielnie, `int` przyjmowana jest wartość. Specyfikatora typu można użyć, `volatile` aby zapewnić niezawodny dostęp do specjalnych lokalizacji pamięci. Używany `volatile` z obiektami danych, które mogą być dostępne lub modyfikowane przez programy obsługi sygnałów przez współbieżnie wykonywane programy lub przez specjalny sprzęt, taki jak rejestry kontroli we/wy mapowane na pamięć. Możesz zadeklarować zmienną jako `volatile` dla swojego okresu istnienia lub można rzutować pojedyncze odwołanie na nie. `volatile`

- Element może **być zarówno stały,** jak `volatile`i, w tym przypadku element nie może być słusznie zmodyfikowany przez swój własny program, ale może być modyfikowany przez jakiś proces asynchroniczny.

## <a name="see-also"></a>Zobacz też

[Deklaracje i typy](../c-language/declarations-and-types.md)
