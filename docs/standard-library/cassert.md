---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: 58ebd91fb4fa32cf31d2c49429d0445b92fe0c82
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449908"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

Zawiera nagłówek \<standardowej biblioteki C Assert. h > i dodaje skojarzone nazwy `std` do przestrzeni nazw. Dołączenie tego nagłówka zapewnia, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku standardowej biblioteki C są `std` deklarowane w przestrzeni nazw.

> [!NOTE]
> \<Assert. h > nie definiuje `static_assert` makra.

## <a name="syntax"></a>Składnia

```cpp
#include <cassert>
```

## <a name="macros"></a>Makra

```cpp
#define assert(E)
```

### <a name="remarks"></a>Uwagi

`assert(E)`jest tylko stałą, jeśli NDEBUG jest zdefiniowany, `assert` gdzie jest zdefiniowana jako Ostatnia zdefiniowana lub ponownie zdefiniowana, lub wartość *E* konwertowana na typ bool jest równa **true**.

## <a name="see-also"></a>Zobacz także

[assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)\
[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[C++Omówienie biblioteki standardowej](../standard-library/cpp-standard-library-overview.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
