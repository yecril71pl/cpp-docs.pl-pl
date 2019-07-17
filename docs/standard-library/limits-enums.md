---
title: '&lt;limity&gt; Typy wyliczeniowe'
ms.date: 11/04/2016
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 567e0538f59c40d57f85d652a8919be6e034cf0b
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245357"
---
# <a name="ltlimitsgt-enums"></a>&lt;limity&gt; Typy wyliczeniowe

## <a name="float_denorm_style"></a> float_denorm_style

Wyliczenia w tym artykule opisano różne metody, które można wybrać implementacji reprezentujący wartość zmiennoprzecinkowa nieznormalizowany — jeden zbyt mała, aby przedstawić jako wartość znormalizowaną:

```cpp
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wyliczenie:

- `denorm_indeterminate` Jeżeli nie można ustalić obecności lub braku nieznormalizowany formularzy w czasie tłumaczenia.

- `denorm_absent` Jeśli nieznormalizowany formularzy nie są spełnione.

- `denorm_present` Jeśli istnieją formularze nieznormalizowany.

### <a name="example"></a>Przykład

Zobacz [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm) na przykład, w którym mogą być dostępne wartości to wyliczenie.

## <a name="float_round_style"></a> float_round_style

Wyliczenia w tym artykule opisano różne metody wdrażania można wybrać podczas zaokrąglania wartość zmiennoprzecinkowa wartość będącą liczbą całkowitą.

```cpp
enum float_round_style {
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wyliczenie:

- `round_indeterminate` Jeśli nie można określić metodę zaokrąglania.

- `round_toward_zero` Jeśli działanie w kierunku zera.

- `round_to_nearest` Jeśli zaokrąglić do najbliższej liczby całkowitej.

- `round_toward_infinity` Jeśli działanie w kierunku od zera.

- `round_toward_neg_infinity` Jeśli zaokrąglić do bardziej ujemną liczbę całkowitą.

### <a name="example"></a>Przykład

Zobacz [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style) na przykład, w którym mogą być dostępne wartości to wyliczenie.
