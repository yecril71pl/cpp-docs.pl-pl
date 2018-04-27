---
title: subtract_with_carry_engine — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
dev_langs:
- C++
helpviewer_keywords:
- std::subtract_with_carry_engine [C++]
- std::subtract_with_carry_engine [C++], default_seed
- std::subtract_with_carry_engine [C++], discard
- std::subtract_with_carry_engine [C++], min
- std::subtract_with_carry_engine [C++], max
- std::subtract_with_carry_engine [C++], seed
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f60be83bb3b1298c9f1ccf5dfaf4f367deb65f74
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="subtractwithcarryengine-class"></a>subtract_with_carry_engine — Klasa

Generuje losowe sekwencji przez algorytm subtract z przenoszące (połączenie z otuliną Fibonacci).

## <a name="syntax"></a>Składnia

```cpp
template <class UIntType, size_t W, size_t S, size_t R>
class subtract_with_carry_engine;
```

### <a name="parameters"></a>Parametry

`UIntType` Typ wyniku liczbę całkowitą bez znaku. Dla typów możliwych [ \<losowe >](../standard-library/random.md).

`W` **Word rozmiar**. Rozmiar każdego wyrazu w bitach sekwencji stanu. **Warunek wstępny**: `0 < W ≤ numeric_limits<UIntType>::digits`

`S` **Krótkie opóźnienie**. Liczba wartości będące liczbami całkowitymi. **Warunek wstępny**: `0 < S < R`

`R` **Long lag**. Określa cyklu w serii wygenerowany.

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|
|`default_seed` jest elementem członkowskim stałej, zdefiniowanej jako `19780503u`, używana jako domyślna wartość parametru `subtract_with_carry_engine::seed` i Konstruktor pojedynczej wartości.|||

Aby uzyskać więcej informacji na temat aparatu członków zobacz [ \<losowe >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

`substract_with_carry_engine` Klasy szablonu jest ulepszeniem [linear_congruential_engine —](../standard-library/linear-congruential-engine-class.md). Nie te aparatów będzie tak szybko, lub za pomocą jako wysokiej jakości wyniki w postaci [mersenne_twister_engine —](../standard-library/mersenne-twister-engine-class.md).

Ten aparat tworzy wartości określonych przez użytkownika bez znaku typu całkowitego przy użyciu relacji cyklu ( *okres*) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`, gdzie `cy(i)` ma wartość `1` Jeśli `x(i - S) - x(i - R) - cy(i - 1) < 0`, w przeciwnym razie `0`, i `M` ma wartość `2` <sup>W</sup>. Stan aparatu jest przeniesienie wskaźnik plus `R` wartości. Te wartości składają się z ostatniego `R` wartości zwracane w przypadku `operator()` została wywołana w co najmniej `R` czas, w przeciwnym razie `N` wartości, które zostały zwrócone oraz za ostatni `R - N` wartości inicjatora.

Argument szablonu `UIntType` musi być wystarczająco duży, aby pomieścić wartości do `M - 1`.

Mimo że można bezpośrednio utworzyć generator z tym aparatem, można także można użyć jednego z tych wstępnie zdefiniowanych definicje typów:

`ranlux24_base`: Użyty jako podstawa dla `ranlux24`.
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

`ranlux48_base`: Użyty jako podstawa dla `ranlux48`.
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

Aby uzyskać szczegółowe informacje na temat subract z algorytmem aparat przenoszące, zobacz artykuł Wikipedia [generator połączenie z otuliną Fibonacci](http://go.microsoft.com/fwlink/p/?linkid=402445).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[\<losowe >](../standard-library/random.md)<br/>
