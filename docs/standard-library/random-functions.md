---
title: '&lt;funkcje&gt; losowe'
ms.date: 09/04/2019
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 3d94f607fc6b7bdf22d7f573f590b451dbaa718d
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273826"
---
# <a name="ltrandomgt-functions"></a>&lt;funkcje&gt; losowe

## <a name="generate_canonical"></a>generate_canonical

Zwraca wartość zmiennoprzecinkową z sekwencji losowej.

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Parametry

*Liczba rzeczywista*\
Typ całkowity zmiennoprzecinkowy. W przypadku możliwych typów zobacz [ \<losowe >](../standard-library/random.md).

*Bitów*\
Liczba bitów losowości do użycia.

*Is*\
Klasa generatora liczb losowych.

*Zbieranie*\
Odwołanie do wystąpienia generatora liczb losowych *generatora*typów.

### <a name="remarks"></a>Uwagi

Funkcja szablonu wielokrotnie wywołuje `operator()` metodę *generacji* i pakuje zwrócone wartości do wartości `x` zmiennoprzecinkowej typu *RealType* do momentu zebrania określonej liczby bitów mantysy w. `x` Określona liczba jest mniejszą liczbą *bitów* (która musi być różna od zera) i pełną liczbą mantysy bitów w *rzeczywistości*. Pierwsze wywołanie dostarcza najniższej kolejności bitów. Funkcja zwraca wartość `x`.
