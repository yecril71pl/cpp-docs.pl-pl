---
title: Błąd kompilatora C2681
ms.date: 11/04/2016
f1_keywords:
- C2681
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
ms.openlocfilehash: d7cf39e89f70f27471fb3a251aac12793f1fb33b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760299"
---
# <a name="compiler-error-c2681"></a>Błąd kompilatora C2681

"Type": nieprawidłowy typ wyrażenia dla nazwy

Operator rzutowania próbował wykonać konwersję z nieprawidłowego typu. Na przykład jeśli używasz operatora [dynamic_cast](../../cpp/dynamic-cast-operator.md) , aby skonwertować wyrażenie na typ wskaźnika, wyrażenie źródłowe musi być wskaźnikiem.

Poniższy przykład generuje C2681:

```cpp
// C2681.cpp
class A { virtual void f(); };

void g(int i) {
    A* pa;
    pa = dynamic_cast<A*>(i);  // C2681
}
```
