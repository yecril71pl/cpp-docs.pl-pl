---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: 14dda03e835ec411013b2d827bd1ccaa77f8982e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245020"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

Dołącza nagłówek biblioteki standardowe C \<assert.h > i dodaje skojarzone nazwy `std` przestrzeni nazw. Dołączenie tego pliku nagłówkowego gwarantuje również, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku biblioteki standardowe C są deklarowane w `std` przestrzeni nazw.

> [!NOTE]
> \<Assert.h > nedefinuje `static_assert` makra.

## <a name="syntax"></a>Składnia

```cpp
#include <cassert>
```

## <a name="macros"></a>Makra

```cpp
#define assert(E)
```

### <a name="remarks"></a>Uwagi

`assert(E)` tylko jest wartością stałą, jeśli nie zdefiniowano NDEBUG gdzie `assert` ostatniego zdefiniowane lub przedefiniowana, lub *E* przekonwertowane na bool daje w wyniku **true**.

## <a name="see-also"></a>Zobacz także

[assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
