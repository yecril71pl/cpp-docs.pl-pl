---
title: alignment_of — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: 5222e70965db69d33ec62039bf9013a52d145705
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456451"
---
# <a name="alignmentof-class"></a>alignment_of — Klasa

Pobiera wyrównanie określonego typu. Ta struktura jest zaimplementowana w odniesieniu do [alignof](../cpp/alignof-and-alignas-cpp.md). Użyj `alignof` bezpośrednio, gdy musisz po prostu wykonać zapytanie względem wartości wyrównania. Użyj alignment_of, gdy potrzebujesz stałej całkowitej, na przykład podczas wysyłania tagów.

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

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[aligned_storage, klasa](../standard-library/aligned-storage-class.md)
