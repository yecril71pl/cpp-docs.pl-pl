---
title: '&lt;csetjmp&gt;'
ms.date: 11/04/2016
f1_keywords:
- <csetjmp>
helpviewer_keywords:
- csetjmp header
ms.assetid: 8f21fddd-5e9b-4219-a848-581cdd3569d9
ms.openlocfilehash: 3eba0b4521c0abf414de1416f02039a67c896644
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244514"
---
# <a name="ltcsetjmpgt"></a>&lt;csetjmp&gt;

Dołącza nagłówek biblioteki standardowej C \<setjmp.h > i dodaje skojarzone nazwy `std` przestrzeni nazw.

## <a name="syntax"></a>Składnia

```cpp
#include <csetjmp>

using jmp_buf = see below;
```

## <a name="functions"></a>Funkcje

```cpp
[[noreturn]] void longjmp(jmp_buf env, int val);
```

## <a name="macros"></a>Makra

```cpp
#define setjmp(env)
```

## <a name="remarks"></a>Uwagi

Dołączenie tego pliku nagłówkowego gwarantuje również, że nazwy zadeklarowane przez zewnętrzne powiązanie w nagłówku standardowej biblioteki C są deklarowane w `std` przestrzeni nazw.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
