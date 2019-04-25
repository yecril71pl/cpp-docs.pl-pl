---
title: independent_bits_engine — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: 8f420ca054d20cd222b8eda9a4a35a383a8e535a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159226"
---
# <a name="independentbitsengine-class"></a>independent_bits_engine — Klasa

Generuje losową sekwencję liczb z określoną liczbą bitów za pomocą liczby bitów przepakowanie na podstawie wartości zwracanych przez silnik podstawowy.

## <a name="syntax"></a>Składnia

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Parametry

*Aparat*<br/>
Typ podstawowy aparat.

*W*<br/>
**Word rozmiar**. Rozmiar w bitach poszczególnych liczb wygenerowany. **Warunek wstępny**: `0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType*<br/>
Typ wyniku liczby całkowitej bez znaku. Aby możliwych typów, zobacz [ \<losowy >](../standard-library/random.md).

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

Aby uzyskać więcej informacji na temat elementów członkowskich aparatu zobacz [ \<losowy >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Ta klasa szablonu opisuje *łącznik aparatu* która wytwarza wartości przez przepakowaniu bitów z wartości zwracanych przez silnik podstawowy skutkuje *W*— wartości bitowe.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowy >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[\<random>](../standard-library/random.md)<br/>
