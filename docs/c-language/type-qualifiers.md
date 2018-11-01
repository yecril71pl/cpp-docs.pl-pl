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
ms.openlocfilehash: 31cfa4d0d443cc6bb854e8010f1e1535cd39b51b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507688"
---
# <a name="type-qualifiers"></a>Kwalifikatory typów

Kwalifikatory typów oferowanie jednej z dwóch właściwości identyfikatora. **Const** kwalifikator typu deklaruje niemodyfikowalnymi obiektu. `volatile` Kwalifikator typu deklaruje element, którego wartość może rzeczywiście zmienić coś poza kontrolą programu, w której występuje, takich jak współbieżnie wykonywanego wątku.

Kwalifikatory, należy wpisać dwa **const** i `volatile`, może wystąpić tylko raz w deklaracji. Kwalifikatory typów mogą być wyświetlane ze specyfikatorem dowolnego typu; jednak nie może występować po pierwszej przecinkami w wielu deklaracji elementu. Na przykład następujące deklaracje są dopuszczalne:

```
typedef volatile int VI;
const int ci;
```

Deklaracje te są niedozwolone:

```
typedef int *i, volatile *vi;
float f, const cf;
```

Kwalifikatory typów mają zastosowanie tylko wtedy, gdy dostęp do identyfikatorów jako l wartości w wyrażeniach. Zobacz [wyrażenia wartości L i r](../c-language/l-value-and-r-value-expressions.md) informacji dotyczących l wartości i wyrażeń.

## <a name="syntax"></a>Składnia

*Kwalifikator typu*: **constvolatile**

Poniżej przedstawiono prawne **const** i `volatile` deklaracje:

```
int const *p_ci;       /* Pointer to constant int */
int const (*p_ci);     /* Pointer to constant int */
int *const cp_i;       /* Constant pointer to int */
int (*const cp_i);     /* Constant pointer to int */
int volatile vint;     /* Volatile integer        */
```

Jeśli specyfikacja typu tablicowego zawiera kwalifikatory typów, element jest kwalifikowana, nie typu tablicy. Jeśli specyfikacja typu funkcji zawiera kwalifikatorów, zachowanie jest niezdefiniowane. Ani `volatile` ani **const** ma wpływ na zakres wartości lub arytmetyczne właściwości obiektu.

Poniższa lista opisuje sposób używania **const** i `volatile`.

- **Const** — słowo kluczowe może służyć do modyfikowania dowolnego typu podstawowe lub agregacji lub wskaźnik do obiektu dowolnego typu lub `typedef`. Jeśli element jest zadeklarowana za pomocą tylko **const** kwalifikator typu jego typ przyjmuje się **const int**. A **const** zmiennej może być inicjowany lub można umieścić w regionie magazynu tylko do odczytu. **Const** — słowo kluczowe jest przydatne do deklarowania wskaźników do **const** ponieważ wymaga to funkcja, nie należy zmieniać wskaźnika w dowolny sposób.

- Kompilator zakłada, że w dowolnym momencie w programie `volatile` zmiennej może zostać oceniony przez nieznany proces, który używa lub modyfikuje jego wartość. W związku z tym, niezależnie od optymalizacji określone w poleceniu wiersza kodu dla każdego przypisania do lub odwołaj się do elementu `volatile` zmienna musi zostać wygenerowany, nawet jeśli wydaje się mieć żadnego wpływu.

   Jeśli `volatile` jest używana samodzielnie, `int` zakłada, że. `volatile` Specyfikator typu może służyć do zapewnienia niezawodny dostęp do lokalizacji pamięci specjalne. Użyj `volatile` z obiektami danych, które mogą być dostępne lub zmieniane przez procedurach obsługi sygnału, jednocześnie wykonywania programów lub specjalnego sprzętu, takich jak mapowane w pamięci operacji We/Wy rejestry sterowania. Można zadeklarować zmienną jako `volatile` dla jego okres istnienia, lub można rzutować jedno odwołanie do być `volatile`.

- Element może być zarówno **const** i `volatile`, w którym to przypadku nie można zmodyfikować rzeczywiście swój własny program element, ale może być modyfikowane przez niektóre procesu asynchronicznego.

## <a name="see-also"></a>Zobacz też

[Deklaracje i typy](../c-language/declarations-and-types.md)