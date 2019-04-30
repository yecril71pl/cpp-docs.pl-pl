---
title: alignment_of — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: 2633749a72ceeea197579dca4300b58250f60d73
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411087"
---
# <a name="alignmentof-class"></a>alignment_of — Klasa

Pobiera wyrównanie określonego typu. Ta struktura jest zaimplementowana w [alignof](../cpp/alignof-and-alignas-cpp.md). Użyj `alignof` bezpośrednio po prostu konieczność wartość wyrównania zapytania. Alignment_of — należy używać wtedy, gdy konieczne stałą całkowitą, na przykład podczas wysyłania tagu.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Zapytanie typu przechowuje wartość wyrównanie typu *Ty*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[aligned_storage, klasa](../standard-library/aligned-storage-class.md)<br/>
