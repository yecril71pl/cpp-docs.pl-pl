---
title: '&lt;losowe&gt; funkcji'
ms.date: 11/04/2016
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 87b640d4f3aa3fbfa23ad5603d84102301e71ea4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240389"
---
# <a name="ltrandomgt-functions"></a>&lt;losowe&gt; funkcji

## <a name="generate_canonical"></a> generate_canonical

Zwraca wartość zmiennoprzecinkową z sekwencji losowej.

> [!NOTE]
> Obraz ISO C++ Standard stwierdza, że ta funkcja powinna zwrócić wartości z zakresu [ `0`, `1`). Program Visual Studio nie jest jeszcze zgodne z tym ograniczeniem. Jako obejście do generowania wartości w tym zakresie, należy użyć [uniform_real_distribution —](../standard-library/uniform-real-distribution-class.md).

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Parametry

*RealType*\
Zmiennoprzecinkowy typu całkowitego. Aby możliwych typów, zobacz [ \<losowy >](../standard-library/random.md).

*Usługa BITS*\
Generator liczb losowych.

*Gen*\
Generator liczb losowych.

### <a name="remarks"></a>Uwagi

Wywołania funkcji szablonu `operator()` z *ogólnego* wielokrotnie pakiety wartości zwracane wartości zmiennoprzecinkowe i `x` typu *RealType* aż zebrane określoną liczbę mantysy bitów w `x`. Określony numer jest mniejszy od *bitów* (może być różna od zera) i Pełna liczba bitów mantysy *RealType*. Pierwsze wywołanie dostarcza bitów najniższego rzędu. Funkcja zwraca `x`.
