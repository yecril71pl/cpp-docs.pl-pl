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
ms.openlocfilehash: 729e9f65fd1054b8381f45b81e5276846145ebc1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87198726"
---
# <a name="type-qualifiers"></a>Kwalifikatory typów

Kwalifikatory typu dają jedną z dwóch właściwości do identyfikatora. **`const`** Kwalifikator typu deklaruje obiekt jako niemodyfikowalny. **`volatile`** Kwalifikator typu deklaruje element, którego wartość może być słusznie zmieniona przez coś poza formantem programu, w którym występuje, na przykład współbieżnie wykonywany wątek.

Dwa Kwalifikatory typu **`const`** i **`volatile`** , mogą występować tylko raz w deklaracji. Kwalifikatory typu mogą występować z dowolnym specyfikatorem typu; nie mogą jednak występować po pierwszym przecinku w deklaracji wielu elementów. Na przykład następujące deklaracje są dozwolone:

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

Poniżej przedstawiono prawne **`const`** i **`volatile`** deklaracje:

```
int const *p_ci;       /* Pointer to constant int */
int const (*p_ci);     /* Pointer to constant int */
int *const cp_i;       /* Constant pointer to int */
int (*const cp_i);     /* Constant pointer to int */
int volatile vint;     /* Volatile integer        */
```

Jeśli specyfikacja typu tablicy zawiera kwalifikatory typu, element jest kwalifikowany, a nie typ tablicy. Jeśli specyfikacja typu funkcji zawiera kwalifikatory, zachowanie jest niezdefiniowane. Ani **`volatile`** nie **`const`** ma wpływu na zakres wartości lub właściwości arytmetyczne obiektu.

Ta lista zawiera opis sposobu korzystania z programu **`const`** i **`volatile`** .

- **`const`** Słowo kluczowe może służyć do modyfikowania dowolnego typu podstawowego lub agregacji lub wskaźnika do obiektu dowolnego typu lub **`typedef`** . Jeśli element jest zadeklarowany tylko przy użyciu **`const`** kwalifikatora typu, jego typ jest traktowany jako **const int**. **`const`** Zmienna może być inicjowana lub może zostać umieszczona w regionie magazynu tylko do odczytu. **`const`** Słowo kluczowe jest przydatne do deklarowania wskaźników do **`const`** , ponieważ wymaga, aby funkcja nie zmieniła wskaźnika w jakikolwiek sposób.

- Kompilator zakłada, że w dowolnym momencie w programie **`volatile`** zmienna może być dostępna przez nieznany proces, który używa lub modyfikuje jego wartość. Z tego względu, niezależnie od optymalizacji określonych w wierszu polecenia, należy wygenerować kod dla każdego przypisania lub odwołania do zmiennej, **`volatile`** nawet jeśli wydaje się, że nie ma żadnego wpływu.

   Jeśli **`volatile`** jest używany samodzielnie, **`int`** przyjmowana jest wartość. **`volatile`** Specyfikatora typu można użyć, aby zapewnić niezawodny dostęp do specjalnych lokalizacji pamięci. Używany **`volatile`** z obiektami danych, które mogą być dostępne lub modyfikowane przez programy obsługi sygnałów przez współbieżnie wykonywane programy lub przez specjalny sprzęt, taki jak rejestry kontroli we/wy mapowane na pamięć. Możesz zadeklarować zmienną jako **`volatile`** dla swojego okresu istnienia lub można rzutować pojedyncze odwołanie na nie **`volatile`** .

- Element może być zarówno **`const`** , jak i **`volatile`** , w takim przypadku element nie mógł zostać słusznie zmodyfikowany przez swój własny program, ale może być zmodyfikowany przez proces asynchroniczny.

## <a name="see-also"></a>Zobacz także

[Deklaracje i typy](../c-language/declarations-and-types.md)
