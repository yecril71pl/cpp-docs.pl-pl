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
ms.openlocfilehash: 76981df1f4a642cca1a57a9619f20aa4cebd63bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412194"
---
# <a name="subtractwithcarryengine-class"></a>subtract_with_carry_engine — Klasa

Generuje losową sekwencję przez algorytm odejmowania z przeniesienia (opóźnioną kopię Fibonacci).

## <a name="syntax"></a>Składnia

```cpp
template <class UIntType, size_t W, size_t S, size_t R>
class subtract_with_carry_engine;
```

### <a name="parameters"></a>Parametry

*UIntType*<br/>
Typ wyniku liczby całkowitej bez znaku. Aby możliwych typów, zobacz [ \<losowy >](../standard-library/random.md).

*W*<br/>
**Word rozmiar**. Rozmiar każdego wyrazu w bitach sekwencji stanu. **Warunek wstępny**: `0 < W ≤ numeric_limits<UIntType>::digits`

*S*<br/>
**Krótkie opóźnienie**. Liczba wartości całkowitych. **Warunek wstępny**: `0 < S < R`

*R*<br/>
**Opóźnione w długo**. Określa cyklu w serii wygenerowany.

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|
|`default_seed` jest elementem członkowskim stałą, definiowany jako `19780503u`, który jest używany jako wartość domyślna parametru `subtract_with_carry_engine::seed` i konstruktora pojedynczej wartości.|||

Aby uzyskać więcej informacji na temat elementów członkowskich aparatu zobacz [ \<losowy >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

`substract_with_carry_engine` Klasy szablonu jest ulepszeniem [linear_congruential_engine —](../standard-library/linear-congruential-engine-class.md). Żadna tych aparatów jest tak szybko, lub jako wysokiej jakości wyniki w postaci [mersenne_twister_engine —](../standard-library/mersenne-twister-engine-class.md).

Ten aparat tworzy wartości określonych przez użytkownika typ bez znaku typu całkowitego przy użyciu relacji cyklu ( *okres*) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`, gdzie `cy(i)` ma wartość `1` Jeśli `x(i - S) - x(i - R) - cy(i - 1) < 0`, w przeciwnym razie `0`, i `M` ma wartość `2` <sup>W</sup>. Stan aparatu to przeniesienie wskaźnika plus *R* wartości. Wartości te składają się z ostatnich *R* wartości zwracane, gdy `operator()` została wywołana co najmniej *R* czas, w przeciwnym razie `N` wartości, które zostały zwrócone, a ostatni `R - N` wartości inicjatora.

Argument szablonu `UIntType` musi być wystarczająco duży, aby przechowywać wartości do `M - 1`.

Chociaż można utworzyć generatora z tego aparatu bezpośrednio, umożliwia także jeden z tych wstępnie zdefiniowanych definicje typów:

`ranlux24_base`: Używane jako podstawa `ranlux24`.
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

`ranlux48_base`: Używane jako podstawa `ranlux48`.
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

Aby uzyskać szczegółowe informacje na temat subract z algorytmem aparatem przeniesienia, zobacz artykułu w Wikipedii [generator opóźnioną kopię Fibonacci](https://en.wikipedia.org/wiki/Lagged_Fibonacci_generator).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowy >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[\<random>](../standard-library/random.md)<br/>
