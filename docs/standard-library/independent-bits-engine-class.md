---
title: independent_bits_engine — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: 28c9301d270ef516a1acc59f6ab06f0e61a1c9c5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687928"
---
# <a name="independent_bits_engine-class"></a>independent_bits_engine — Klasa

Generuje losową sekwencję liczb z określoną liczbą bitów przez przepakowywanie bitów z wartości zwracanych przez aparat podstawowy.

## <a name="syntax"></a>Składnia

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Parametry

@No__t_1 *silnika*
Typ aparatu podstawowego.

*W* \
**Rozmiar wyrazu**. Rozmiar w bitach dla każdej wygenerowanej liczby. **Warunek wstępny**: `0 < W ≤ numeric_limits<UIntType>::digits`

@No__t_1 *UIntType*
Typ wyniku bez znaku liczby całkowitej. W przypadku możliwych typów zobacz [\<random >](../standard-library/random.md).

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

Aby uzyskać więcej informacji na temat elementów członkowskich silnika, zobacz [\<random >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Ten szablon klasy zawiera opis *adaptera* , który tworzy wartości poprzez przepakowywanie bitów z wartości zwracanych przez aparat podstawowy, co spowodowało *wartości w bitach*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<random >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[\<random >](../standard-library/random.md)
