---
title: Błąd kompilatora C2923
ms.date: 11/04/2016
f1_keywords:
- C2923
helpviewer_keywords:
- C2923
ms.assetid: 6b92933b-13ef-4124-99d9-b89f9fdae030
ms.openlocfilehash: 885a3a09d43d8c3c479d11e22342487d1a1958d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593625"
---
# <a name="compiler-error-c2923"></a>Błąd kompilatora C2923

'type': 'Identyfikator' nie jest prawidłowym szablonem typ argumentu dla parametru "param"

Lista argumentów brakuje typu potrzebne do utworzenia wystąpienia szablonu lub typ ogólny. Sprawdź szablon lub deklaracji ogólnej.

Poniższy przykład spowoduje wygenerowanie C2923:

```
// C2923.cpp
template <class T> struct TC {};
int x;
int main() {
   TC<x>* tc2;   // C2923
   TC<int>* tc2;   // OK
}
```

C2923 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C2923b.cpp
// compile with: /clr /c
generic <class T> ref struct GC {};

int x;

int main() {
   GC<x>^ gc2;   // C2923
   GC<int>^ gc2;   // OK
}
```