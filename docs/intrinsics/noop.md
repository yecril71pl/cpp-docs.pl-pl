---
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: aec4df98413bf34ac1e2966d012bb905edd4775e
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857934"
---
# <a name="__noop"></a>__noop

**Microsoft Specific**

Wewnętrzna `__noop` określa, że funkcja powinna być ignorowana. Lista argumentów jest analizowana, ale dla argumentów nie jest generowany żaden kod. Jest ona przeznaczona do użycia w globalnych funkcjach debugowania, które przyjmują zmienną liczbę argumentów.

Kompilator konwertuje `__noop` wewnętrznie na 0 w czasie kompilacji.

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak można użyć `__noop`.

```cpp
// compiler_intrinsics__noop.cpp
// compile with or without /DDEBUG
#include <stdio.h>

#if DEBUG
   #define PRINT   printf_s
#else
   #define PRINT   __noop
#endif

int main() {
   PRINT("\nhello\n");
}
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

\ [Wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
[Słowa kluczowe](../cpp/keywords-cpp.md)
