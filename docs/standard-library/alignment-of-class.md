---
title: alignment_of — Klasa
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: 5a90f481c33431d92f0f28405e6226863d2b3913
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205018"
---
# <a name="alignment_of-class"></a>alignment_of — Klasa

Pobiera wyrównanie określonego typu. Ta struktura jest zaimplementowana w zakresie [`alignof`](../cpp/alignment-cpp-declarations.md) . Użyj **`alignof`** bezpośrednio, gdy musisz po prostu wykonać zapytanie względem wartości wyrównania. Użyj `alignment_of` , gdy potrzebna jest stała całkowita, na przykład podczas wysyłania tagów.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Zapytanie typu przechowuje wartość wyrównania typu *ty*.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[`<type_traits>`](type-traits.md)\
[`aligned_storage`Określonej](aligned-storage-class.md)
