---
title: '&lt;cassert —&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: a1d554eedef368fe10a9f13b0b654078675e8348
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559019"
---
# <a name="ltcassertgt"></a>&lt;cassert —&gt;

Dołącza nagłówek biblioteki standardowej C \<assert.h > i dodaje skojarzone nazwy `std` przestrzeni nazw.

## <a name="syntax"></a>Składnia

```cpp
#include <cassert>

```

## <a name="remarks"></a>Uwagi

Dołączenie tego pliku nagłówkowego gwarantuje również, że nazwy zadeklarowane przez zewnętrzne powiązanie w nagłówku standardowej biblioteki C są deklarowane w `std` przestrzeni nazw.

## <a name="see-also"></a>Zobacz także

[assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
