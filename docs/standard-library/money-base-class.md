---
title: money_base — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: 5b19635cf4d2cce58ec50226c463a075cfac5b0f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455566"
---
# <a name="moneybase-class"></a>money_base — Klasa

Klasa opisuje Wyliczenie i strukturę wspólną dla wszystkich specjalizacji klasy szablonu [moneypunct](../standard-library/moneypunct-class.md).

## <a name="syntax"></a>Składnia

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>Uwagi

Wyliczenie `part` opisuje możliwe wartości w elementach pola tablicy we wzorcu struktury. Wartości `part` są:

- `none`Aby dopasować zero lub więcej spacji lub wygenerować Nothing.

- `sign`Aby dopasować lub wygenerować znak dodatni lub ujemny.

- `space`Aby dopasować zero lub więcej spacji lub wygenerować spację.

- `symbol`Aby dopasować lub wygenerować symbol waluty.

- `value`Aby dopasować lub wygenerować wartość pieniężną.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
