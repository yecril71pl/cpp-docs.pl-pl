---
title: '&lt;limity&gt; wyliczenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 356c98ce5c93d1e05a583fc30c4758c5d15d7529
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltlimitsgt-enums"></a>&lt;limity&gt; wyliczenia

|||
|-|-|
|[float_denorm_style](#float_denorm_style)|[float_round_style](#float_round_style)|

## <a name="float_denorm_style"></a>  float_denorm_style — wyliczenie

Wyliczenie zawiera opis różnych metod, które można wybrać implementację reprezentujący nieznormalizowany wartość zmiennoprzecinkowa — jeden za mały, aby reprezentować znormalizowaną wartość:

```cpp
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wyliczenie:

- **denorm_indeterminate** Jeśli obecności lub braku nieznormalizowany formularzy nie można określić podczas tłumaczenia.

- **denorm_absent** Jeśli nieznormalizowany formularze są nieobecne.

- **denorm_present** Jeśli nieznormalizowany formularze są obecne.

### <a name="example"></a>Przykład

Zobacz [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm) na przykład, w którym mogą być używane wartości tego wyliczenia.

## <a name="float_round_style"></a>  float_round_style — wyliczenie

Wyliczenie zawiera opis różnych metod, które można wybrać implementację zaokrąglania wartości zmiennoprzecinkowej na wartość całkowitą.

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

- **round_indeterminate** , jeśli nie można określić metody zaokrąglania.

- **round_toward_zero** Jeśli round w kierunku zera.

- **round_to_nearest** Jeśli zaokrąglona do najbliższej liczby całkowitej.

- **round_toward_infinity** Jeśli round w kierunku od zera.

- **round_toward_neg_infinity** Jeśli zaokrąglona do bardziej ujemnej liczby całkowitej.

### <a name="example"></a>Przykład

Zobacz [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style) na przykład, w którym mogą być używane wartości tego wyliczenia.

## <a name="see-also"></a>Zobacz także

[\<limits>](../standard-library/limits.md)<br/>
