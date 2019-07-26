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
ms.openlocfilehash: 17091e33c504df60c0b6b8e346d2a6fd3893679c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447418"
---
# <a name="subtractwithcarryengine-class"></a>subtract_with_carry_engine — Klasa

Generuje losową sekwencję przy użyciu algorytmu odejmowania z przenoszonej (Fibonacci).

## <a name="syntax"></a>Składnia

```cpp
template <class UIntType, size_t W, size_t S, size_t R>
class subtract_with_carry_engine;
```

### <a name="parameters"></a>Parametry

*UInttype*\
Typ wyniku bez znaku liczby całkowitej. W przypadku możliwych typów zobacz [ \<losowe >](../standard-library/random.md).

*K*\
**Rozmiar wyrazu**. Rozmiar każdego wyrazu, w bitach, sekwencji stanu. **Warunek wstępny**:`0 < W ≤ numeric_limits<UIntType>::digits`

*WOLUMIN*\
**Krótkie opóźnienie**. Liczba wartości całkowitych. **Warunek wstępny**:`0 < S < R`

*R*\
**Długi czas opóźnienia**. Określa cykl w wygenerowanych seriach.

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|
|`default_seed`jest stałą składową, zdefiniowaną `19780503u`jako domyślną `subtract_with_carry_engine::seed` wartością parametru i konstruktorem pojedynczej wartości.|||

Aby uzyskać więcej informacji na temat elementów członkowskich silnika, zobacz [ \<Random >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Klasa szablonu jest ulepszeniem w linear_congruential_engine. [](../standard-library/linear-congruential-engine-class.md) `substract_with_carry_engine` Żadna z tych aparatów nie jest tak szybka, jak i z wysoką jakością jako [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md).

Ten aparat tworzy wartości określonego przez użytkownika niepodpisanego typu całkowitego przy użyciu relacji powtarzania (kropka `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`) `cy(i)` , gdzie ma `1` wartość `x(i - S) - x(i - R) - cy(i - 1) < 0`, jeśli `0`, w `M` przeciwnym razie, i ma wartość `2` <sup>w</sup>. Stanem aparatu jest wskaźnik przenoszenia Plus wartości *R* . Te wartości składają się z ostatnich wartości *R* zwróconych `operator()` , jeśli został wywołany co najmniej `N` *r* razy, w przeciwnym razie wartości, które zostały zwrócone `R - N` , a ostatnią wartością inicjatora.

Argument `UIntType` szablonu musi być wystarczająco duży, aby można było przechowywać wartości `M - 1`do.

Chociaż można skonstruować Generator z tego aparatu bezpośrednio, można również użyć jednego z tych wstępnie zdefiniowanych typów typedef:

`ranlux24_base`: Używany jako podstawa dla `ranlux24`.
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

`ranlux48_base`: Używany jako podstawa dla `ranlux48`.
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

Aby uzyskać szczegółowe informacje na temat subract z algorytmem aparatu przenoszenia, zobacz artykuł witryny Wikipedia z [opóźnionym generatorem Fibonacci](https://en.wikipedia.org/wiki/Lagged_Fibonacci_generator).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[\<random>](../standard-library/random.md)
