---
title: money_base — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/std::money_base
dev_langs:
- C++
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3195d2c988abcfb2d62acb4ece957c8c5156bbd7
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965691"
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
