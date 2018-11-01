---
title: Błąd kompilatora C2217
ms.date: 11/04/2016
f1_keywords:
- C2217
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
ms.openlocfilehash: f178f969afa189910c9d23d70226ecc6c15876a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507552"
---
# <a name="compiler-error-c2217"></a>Błąd kompilatora C2217

"attribute1" wymaga "attribute2"

Pierwszy atrybut funkcja wymaga drugiego atrybutu.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Przerwań (`__interrupt`) funkcja zadeklarowana jako `near`. Przerwania funkcji musi być `far`.

1. Przerwanie funkcja zadeklarowana ze `__stdcall`, lub `__fastcall`. Przerwań funkcje muszą używają Konwencje wywoływania.

## <a name="example"></a>Przykład

C2217 może również wystąpić, jeśli użytkownik podejmie próbę powiązać delegata funkcji CLR, która przyjmuje zmienną liczbę argumentów. Jeśli funkcja ma również e param tablicy przeciążenia, który zamiast tego użyj. Poniższy przykład spowoduje wygenerowanie C2217.

```
// C2217.cpp
// compile with: /clr
using namespace System;
delegate void MyDel(String^, Object^, Object^, ...);   // C2217
delegate void MyDel2(String ^, array<Object ^> ^);   // OK

int main() {
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);
   array<Object ^ > ^ x = gcnew array<Object ^>(2);
   x[0] = safe_cast<Object^>(0);
   x[1] = safe_cast<Object^>(1);

   // wl("{0}, {1}", 0, 1);
   wl("{0}, {1}", x);
}
```