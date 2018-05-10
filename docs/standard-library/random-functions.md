---
title: '&lt;losowe&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: c8ee20759e66c7beb295de96b8311df46555ac6b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltrandomgt-functions"></a>&lt;losowe&gt; funkcji

## <a name="generate_canonical"></a>  generate_canonical

Zwraca wartość zmiennoprzecinkową z sekwencję losowych.

> [!NOTE]
> Stany standardowi ISO C++, ta funkcja powinna zwrócić wartości z zakresu [ `0`, `1`). Program Visual Studio nie jest jeszcze zgodne z tym ograniczeniem. Jako rozwiązanie alternatywne do generowania wartości w tym zakresie, użyj [uniform_real_distribution —](../standard-library/uniform-real-distribution-class.md).

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Parametry

`RealType` Zmiennoprzecinkowy typ całkowity. Dla typów możliwych [ \<losowe >](../standard-library/random.md).

`Bits` Generator liczb losowych.

`Gen` Generator liczb losowych.

### <a name="remarks"></a>Uwagi

Wywołania funkcji szablonu `operator()` z `Gen` wielokrotnie pakiety zwracanych wartości do wartości zmiennoprzecinkowych i `x` typu `RealType` dopóki zebrane określoną liczbę bitów mantysa `x`. Określona liczba jest mniejsza od `Bits` (który musi być różna od zera) i pełne liczba bitów mantysa `RealType`. Pierwsze wywołanie dostarcza najniższy znaczących bitów. Funkcja zwraca `x`.

## <a name="see-also"></a>Zobacz także

[\<losowe >](../standard-library/random.md)<br/>
