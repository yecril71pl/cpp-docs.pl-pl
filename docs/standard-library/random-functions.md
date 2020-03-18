---
title: '&lt;funkcje&gt; losowych'
ms.date: 09/04/2019
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 3d94f607fc6b7bdf22d7f573f590b451dbaa718d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419645"
---
# <a name="ltrandomgt-functions"></a>&lt;funkcje&gt; losowych

## <a name="generate_canonical"></a>generate_canonical

Zwraca wartość zmiennoprzecinkową z sekwencji losowej.

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Parametry

\ *rzeczywistości*
Typ całkowity zmiennoprzecinkowy. W przypadku możliwych typów zobacz [\<> losowe](../standard-library/random.md).

\ *BITS*
Liczba bitów losowości do użycia.

*Generator*\
Klasa generatora liczb losowych.

\ *Gen*
Odwołanie do wystąpienia generatora liczb losowych *generatora*typów.

### <a name="remarks"></a>Uwagi

Funkcja szablonu wywołuje *`operator()` cyklicznie* i pakuje zwrócone wartości do wartości zmiennoprzecinkowej `x` typu *RealType* do momentu zebrania określonej liczby mantysy bitów w `x`. Określona liczba jest mniejszą liczbą *bitów* (która musi być różna od zera) i pełną liczbą mantysy bitów w *rzeczywistości*. Pierwsze wywołanie dostarcza najniższej kolejności bitów. Funkcja zwraca `x`.
