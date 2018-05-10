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
ms.openlocfilehash: 805045e4ea63f153e9a35b0d4b068bd69874b93f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="moneybase-class"></a>money_base — Klasa

Klasa opisuje, wyliczenia i struktury wspólne dla wszystkich specjalizacji szablonu klasy [moneypunct —](../standard-library/moneypunct-class.md).

## <a name="syntax"></a>Składnia

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>Uwagi

Wyliczenie **części** opisano możliwe wartości w elementach pola tablicy we wzorcu struktury. Wartości **części** są:

- **Brak** odpowiada zero lub więcej spacji lub wygenerowanie nothing.

- **znak** zgodny lub wygenerowanie znak dodatnią lub ujemną.

- **miejsce** odpowiada zero lub więcej spacji lub wygenerowanie spacją.

- **symbol** zgodny lub wygenerowanie symbol waluty.

- **wartość** zgodny lub wygenerowanie wartość pieniężną.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
