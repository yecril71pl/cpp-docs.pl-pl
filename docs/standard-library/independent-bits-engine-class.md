---
title: independent_bits_engine — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: a90e4be4ff6e92734f6b2e6804f8059be78e66b9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456344"
---
# <a name="independentbitsengine-class"></a>independent_bits_engine — Klasa

Generuje losową sekwencję liczb z określoną liczbą bitów przez przepakowywanie bitów z wartości zwracanych przez aparat podstawowy.

## <a name="syntax"></a>Składnia

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Parametry

*Wyszukiwarce*\
Typ aparatu podstawowego.

*K*\
**Rozmiar wyrazu**. Rozmiar w bitach dla każdej wygenerowanej liczby. **Warunek wstępny**:`0 < W ≤ numeric_limits<UIntType>::digits`

*UInttype*\
Typ wyniku bez znaku liczby całkowitej. W przypadku możliwych typów zobacz [ \<losowe >](../standard-library/random.md).

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

Aby uzyskać więcej informacji na temat elementów członkowskich silnika, zobacz [ \<Random >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Ta klasa szablonu opisuje *adapter aparatu* , który tworzy wartości poprzez przepakowywanie bitów z wartości zwracanych przez aparat podstawowy, co spowodowało wartości w bitach .

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[\<random>](../standard-library/random.md)
