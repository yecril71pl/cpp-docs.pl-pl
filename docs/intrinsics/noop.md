---
title: __noop
ms.date: 11/04/2016
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 074ab4c6ea51c8b3a2543d9b43248a8da37567cf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613017"
---
# <a name="noop"></a>__noop

**Microsoft Specific**

`__noop` Wewnętrzne określa, że funkcja mają być ignorowane i przeanalizowania listy argumentów, ale nie można wygenerować kodu dla argumentów. Jest ona przeznaczona do użytku w funkcje globalne debugowania, które przyjmują zmienną liczbę argumentów.

Kompilator konwertuje `__noop` wewnętrzne na 0 w czasie kompilacji.

## <a name="example"></a>Przykład

Poniższy kod przedstawia sposób użycia `__noop`.

```
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

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)