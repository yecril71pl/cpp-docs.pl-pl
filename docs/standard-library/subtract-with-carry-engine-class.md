---
title: subtract_with_carry_engine — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
helpviewer_keywords:
- std::subtract_with_carry_engine [C++]
- std::subtract_with_carry_engine [C++], default_seed
- std::subtract_with_carry_engine [C++], discard
- std::subtract_with_carry_engine [C++], min
- std::subtract_with_carry_engine [C++], max
- std::subtract_with_carry_engine [C++], seed
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
ms.openlocfilehash: 63cbbb3a1a508b41c1e0632eda3eeabe4fda6696
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685816"
---
# <a name="subtract_with_carry_engine-class"></a>subtract_with_carry_engine — Klasa

Generuje losową sekwencję przy użyciu algorytmu odejmowania z przenoszonej (Fibonacci).

## <a name="syntax"></a>Składnia

```cpp
template <class UIntType, size_t W, size_t S, size_t R>
class subtract_with_carry_engine;
```

### <a name="parameters"></a>Parametry

@No__t_1 *UIntType*
Typ wyniku bez znaku liczby całkowitej. W przypadku możliwych typów zobacz [\<random >](../standard-library/random.md).

*W* \
**Rozmiar wyrazu**. Rozmiar każdego wyrazu, w bitach, sekwencji stanu. **Warunek wstępny**: `0 < W ≤ numeric_limits<UIntType>::digits`

@No__t_1 *S*
**Krótkie opóźnienie**. Liczba wartości całkowitych. **Warunek wstępny**: `0 < S < R`

@No__t_1 *R*
**Długi czas opóźnienia**. Określa cykl w wygenerowanych seriach.

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|
|`default_seed` jest stałą członkowską, zdefiniowaną jako `19780503u`, używaną jako domyślna wartość parametru `subtract_with_carry_engine::seed` i konstruktora pojedynczego wartości.|||

Aby uzyskać więcej informacji na temat elementów członkowskich silnika, zobacz [\<random >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Szablon klasy `substract_with_carry_engine` jest ulepszeniem w [linear_congruential_engine](../standard-library/linear-congruential-engine-class.md). Żadna z tych aparatów nie jest tak szybka, jak i z wysoką jakością jako [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md).

Ten aparat tworzy wartości określonego przez użytkownika niepodpisanego typu całkowitego przy użyciu relacji cyklu ( *kropka*) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`, gdzie `cy(i)` ma wartość `1` Jeśli `x(i - S) - x(i - R) - cy(i - 1) < 0`, w przeciwnym razie `0`, a `M` ma wartość `2`<sup>w</sup>. Stanem aparatu jest wskaźnik przenoszenia Plus wartości *R* . Te wartości składają się z ostatnich wartości *R* zwróconych, jeśli `operator()` zostało wywołane co najmniej *R* razy, w przeciwnym razie zwrócone wartości `N` i ostatnie `R - N` wartości inicjatora.

@No__t_0 argumentu szablonu musi być wystarczająco duży, aby pomieścić wartości do `M - 1`.

Chociaż można skonstruować Generator z tego aparatu bezpośrednio, można również użyć jednego z tych wstępnie zdefiniowanych typów typedef:

`ranlux24_base`: używany jako podstawa dla `ranlux24`.
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

`ranlux48_base`: używany jako podstawa dla `ranlux48`.
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

Aby uzyskać szczegółowe informacje na temat subract z algorytmem aparatu przenoszenia, zobacz artykuł witryny Wikipedia z [opóźnionym generatorem Fibonacci](https://en.wikipedia.org/wiki/Lagged_Fibonacci_generator).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<random >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[\<random >](../standard-library/random.md)
