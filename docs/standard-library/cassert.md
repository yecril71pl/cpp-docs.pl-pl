---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: b28f4554610d37b881494748f75499f46cd9e8d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230236"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

Zawiera nagłówek standardowej biblioteki C \<assert.h> i dodaje skojarzone nazwy do `std` przestrzeni nazw. Dołączenie tego nagłówka zapewnia, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku standardowej biblioteki C są deklarowane w `std` przestrzeni nazw.

> [!NOTE]
> \<assert.h>nie definiuje **`static_assert`** makra.

## <a name="syntax"></a>Składnia

```cpp
#include <cassert>
```

## <a name="macros"></a>Makra

```cpp
#define assert(E)
```

### <a name="remarks"></a>Uwagi

`assert(E)`jest tylko stałą, jeśli NDEBUG jest zdefiniowany, gdzie jest zdefiniowana jako `assert` Ostatnia zdefiniowana lub ponownie zdefiniowana, lub wartość *E* konwertowana na bool jest równa **`true`** .

## <a name="see-also"></a>Zobacz także

[potwierdzj makro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)\
[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Omówienie standardowej biblioteki języka C++](../standard-library/cpp-standard-library-overview.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
