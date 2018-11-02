---
title: '&lt;losowe&gt; funkcji'
ms.date: 11/04/2016
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 80bdb1ca83be5fb390035d7f3b005793a2f03715
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520617"
---
# <a name="ltrandomgt-functions"></a>&lt;losowe&gt; funkcji

## <a name="generate_canonical"></a>  generate_canonical

Zwraca wartość zmiennoprzecinkową z sekwencji losowej.

> [!NOTE]
> Standardu ISO C++ stwierdzający, że ta funkcja powinna zwrócić wartości z zakresu [ `0`, `1`). Program Visual Studio nie jest jeszcze zgodne z tym ograniczeniem. Jako obejście do generowania wartości w tym zakresie, należy użyć [uniform_real_distribution —](../standard-library/uniform-real-distribution-class.md).

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Parametry

*RealType*<br/>
Zmiennoprzecinkowy typu całkowitego. Aby możliwych typów, zobacz [ \<losowy >](../standard-library/random.md).

*Usługa BITS*<br/>
Generator liczb losowych.

*Gen*<br/>
Generator liczb losowych.

### <a name="remarks"></a>Uwagi

Wywołania funkcji szablonu `operator()` z *ogólnego* wielokrotnie pakiety wartości zwracane wartości zmiennoprzecinkowe i `x` typu *RealType* aż zebrane określoną liczbę mantysy bitów w `x`. Określony numer jest mniejszy od *bitów* (może być różna od zera) i Pełna liczba bitów mantysy *RealType*. Pierwsze wywołanie dostarcza bitów najniższego rzędu. Funkcja zwraca `x`.

## <a name="see-also"></a>Zobacz także

[\<losowy >](../standard-library/random.md)<br/>
