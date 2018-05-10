---
title: independent_bits_engine — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::independent_bits_engine
dev_langs:
- C++
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f89e6e0fc83a83ece82793050441fec9a1e7978b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="independentbitsengine-class"></a>independent_bits_engine — Klasa

Generuje sekwencję losowych liczb z określoną liczbę bitów za pomocą liczby bitów przepakowania spośród wartości zwróconych przez silnik podstawowej.

## <a name="syntax"></a>Składnia

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Parametry

`Engine` Typ podstawowy aparatu.

`W` **Word rozmiar**. Rozmiar w bitach każdą liczbę wygenerowany. **Warunek wstępny**: `0 < W ≤ numeric_limits<UIntType>::digits`

`UIntType` Typ wyniku liczbę całkowitą bez znaku. Dla typów możliwych [ \<losowe >](../standard-library/random.md).

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

Aby uzyskać więcej informacji na temat aparatu członków zobacz [ \<losowe >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Ta klasa szablonu opisuje *karty aparatu* daje wartości przez przepakowaniu bitów spośród wartości zwróconych przez silnik podstawowej, co powoduje `W`-bit wartości.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[\<losowe >](../standard-library/random.md)<br/>
