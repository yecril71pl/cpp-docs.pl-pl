---
title: Wyliczenie endian
description: Wyliczenie używane do określania wartości endian typów skalarnych
ms.date: 08/27/2020
f1_keywords:
- bit/std::endian
helpviewer_keywords:
- std::endian
ms.openlocfilehash: 78df181e20d0e5d72508bd0fc86118528a312d6b
ms.sourcegitcommit: 3628707bc17c99aac7aac27eb126cc2eaa4d07b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2020
ms.locfileid: "89194560"
---
# <a name="endian-enum"></a>Wyliczenie endian

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

`/std:c++latest` jest wymagana

## <a name="see-also"></a>Zobacz też

[\<bit>](../standard-library/bit.md)  
