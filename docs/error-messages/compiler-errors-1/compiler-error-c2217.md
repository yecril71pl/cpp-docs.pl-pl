---
title: Błąd kompilatora C2217 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2217
dev_langs:
- C++
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4eb8b9fcaffa30f3a5ced5362a0f9d54a45f07e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050622"
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