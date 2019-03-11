---
title: 'Instrukcje: Jawne żądanie konwersji Boxing'
ms.date: 11/04/2016
helpviewer_keywords:
- boxing, explicitly requesting
ms.assetid: 1359e6e5-162d-4f5d-9b6a-1690d93df3ee
ms.openlocfilehash: 1e720923c89a79f75350b6e7d0781ad6fc5759ed
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748752"
---
# <a name="how-to-explicitly-request-boxing"></a>Instrukcje: Jawne żądanie konwersji Boxing

Możesz jawne żądanie konwersji boxing, przypisując zmienną do zmiennej typu `Object`.

## <a name="example"></a>Przykład

```
// vcmcppv2_explicit_boxing3.cpp
// compile with: /clr
using namespace System;

void f(int i) {
   Console::WriteLine("f(int i)");
}

void f(Object ^o) {
   Console::WriteLine("f(Object^ o)");
}

int main() {
   int i = 5;
   Object ^ O = i;   // forces i to be boxed
   f(i);
   f(O);
   f( (Object^)i );  // boxes i
}
```

```Output
f(int i)
f(Object^ o)
f(Object^ o)
```

## <a name="see-also"></a>Zobacz także

[Konwersja boxing](../windows/boxing-cpp-component-extensions.md)
