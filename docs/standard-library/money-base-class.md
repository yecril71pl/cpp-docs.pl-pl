---
title: money_base — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: b0c77b523dbe31bc5b07ae3d736441880fe04546
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610454"
---
# <a name="moneybase-class"></a>money_base — Klasa

Klasa opisuje, wyliczenia i struktury, które są wspólne dla wszystkich specjalizacje szablonu klasy [moneypunct](../standard-library/moneypunct-class.md).

## <a name="syntax"></a>Składnia

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>Uwagi

Wyliczanie `part` opisano możliwe wartości w elementach pola tablicy we wzorcu struktury. Wartości `part` są:

- `none` Aby dopasować zero lub więcej spacji lub generowanie nothing.

- `sign` Aby dopasować lub generowanie znaku dodatniego lub ujemnego.

- `space` Aby dopasować zero lub więcej spacji lub generowanie spację.

- `symbol` Aby dopasować lub wygenerowania symbolu waluty.

- `value` Aby dopasować lub wygenerować wartość pieniężną.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
