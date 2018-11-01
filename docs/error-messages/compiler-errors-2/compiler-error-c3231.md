---
title: Błąd kompilatora C3231
ms.date: 11/04/2016
f1_keywords:
- C3231
helpviewer_keywords:
- C3231
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
ms.openlocfilehash: 653f0b18737f937483f5d3e79cb99c9a55160c19
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571967"
---
# <a name="compiler-error-c3231"></a>Błąd kompilatora C3231

"argument": argument typu szablonu nie można użyć parametru typu ogólnego

Szablony są tworzone w czasie kompilacji, ale typy ogólne są tworzone w czasie wykonywania. W związku z tym nie jest możliwe wygenerować kod ogólny, który można wywołać tego szablonu, ponieważ nie można utworzyć wystąpienia szablonu w czasie wykonywania, gdy na koniec jest znany typ ogólny.

Poniższy przykład spowoduje wygenerowanie C3231:

```
// C3231.cpp
// compile with: /clr /LD
template <class T> class A;

generic <class T>
ref class C {
   void f() {
      A<T> a;   // C3231
   }
};
```