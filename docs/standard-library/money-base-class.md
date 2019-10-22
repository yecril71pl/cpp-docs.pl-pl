---
title: money_base — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: c614832b0cbb1cc23e42ecb3a939ccf1334a5cea
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689324"
---
# <a name="money_base-class"></a>money_base — Klasa

Klasa opisuje Wyliczenie i strukturę wspólną dla wszystkich specjalizacji szablonu klasy [moneypunct](../standard-library/moneypunct-class.md).

## <a name="syntax"></a>Składnia

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>Uwagi

Wyliczenie `part` opisuje możliwe wartości w elementach pola tablicy we wzorcu struktury. Wartości `part` są następujące:

- `none`, aby dopasować zero lub więcej spacji lub wygenerować Nothing.

- `sign` dopasować lub wygenerować znaku dodatniego lub ujemnego.

- `space`, aby dopasować zero lub więcej spacji lub wygenerować spację.

- `symbol` dopasować lub wygenerować symbol waluty.

- `value` dopasować lub wygenerować wartości pieniężnej.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<locale >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
