---
title: alignment_of — Klasa
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: c2af00ac32b3013820a3109783c4bf7eb42ec445
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623730"
---
# <a name="alignment_of-class"></a>alignment_of — Klasa

Pobiera wyrównanie określonego typu. Ta struktura jest zaimplementowana w odniesieniu do [alignof](../cpp/alignment-cpp-declarations.md). Używaj **alignof** bezpośrednio, gdy musisz po prostu wykonać zapytanie względem wartości wyrównania. Użyj alignment_of, gdy potrzebujesz stałej całkowitej, na przykład podczas wysyłania tagów.

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

## <a name="see-also"></a>Zobacz też

[<type_traits>](type-traits.md)\
[Klasa aligned_storage](aligned-storage-class.md)
