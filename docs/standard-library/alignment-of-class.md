---
title: alignment_of — Klasa
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: d241848edf57fe4876c35e22f1762abf5d6888fa
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302318"
---
# <a name="alignment_of-class"></a>alignment_of — Klasa

Pobiera wyrównanie określonego typu. Ta struktura jest zaimplementowana w odniesieniu do [alignof](../cpp/alignment-cpp-declarations.md). Używaj **alignof** bezpośrednio, gdy musisz po prostu wykonać zapytanie względem wartości wyrównania. Użyj alignment_of, gdy potrzebujesz stałej całkowitej, na przykład podczas wysyłania tagów.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Zapytanie typu przechowuje wartość wyrównania typu *ty*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[aligned_storage, klasa](../standard-library/aligned-storage-class.md)
