---
title: endian, wyliczenie
description: Wyliczenie używane do określania wartości endian typów skalarnych
ms.date: 08/27/2020
f1_keywords:
- bit/std::endian
helpviewer_keywords:
- std::endian
ms.openlocfilehash: b535bc009fbdc0b047444a6bc2ca36eed7a6d1cb
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040083"
---
# <a name="endian-enum"></a>endian, wyliczenie

Wskazuje liczbę bajtów wszystkich typów skalarnych.

## <a name="syntax"></a>Składnia

```cpp
enum class endian {
    little = 0,
    big = 1,
    native = little
 };
```

### <a name="members"></a>Elementy członkowskie

|Element|Opis|
|-|-|
| `little` | Wskazuje, że typy skalarne to little-endian. Oznacza to, że najmniej znaczący bajt jest przechowywany na najmniejszym adresie. Na przykład `0x1234` jest przechowywany `0x34` `0x12` .  |
| `big` | Wskazuje, że typy skalarne są big-endian, to oznacza, że najbardziej znaczący bajt jest przechowywany w najmniejszym adresie. Na przykład `0x1234` jest przechowywany `0x12` `0x34` .  |

## <a name="remarks"></a>Uwagi

Wszystkie natywne typy skalarne to little-endian dla platform, które Microsoft Visual C++ obiektami docelowymi (x86, x64, ARM, ARM64).

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<bit>

**Przestrzeń nazw:** std

[/std: wymagany jest język c + +](../build/reference/std-specify-language-standard-version.md) .

## <a name="see-also"></a>Zobacz także

[\<bit>](../standard-library/bit.md)  
