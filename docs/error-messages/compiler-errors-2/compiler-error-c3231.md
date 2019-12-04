---
title: Błąd kompilatora C3231
ms.date: 11/04/2016
f1_keywords:
- C3231
helpviewer_keywords:
- C3231
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
ms.openlocfilehash: 3bc8293f0cbed7c2093cfe9dd0513b690b8c76f0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750341"
---
# <a name="compiler-error-c3231"></a>Błąd kompilatora C3231

"ARG": argument typu szablonu nie może użyć parametru typu ogólnego

Szablony są tworzone w czasie kompilacji, ale typy ogólne są tworzone w czasie wykonywania. W związku z tym nie jest możliwe generowanie kodu generycznego, który może wywołać szablon, ponieważ nie można utworzyć wystąpienia szablonu w czasie wykonywania, gdy typ ogólny jest znany.

Poniższy przykład generuje C3231:

```cpp
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
