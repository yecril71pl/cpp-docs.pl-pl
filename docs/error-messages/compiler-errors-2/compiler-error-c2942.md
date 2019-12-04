---
title: Błąd kompilatora C2942
ms.date: 11/04/2016
f1_keywords:
- C2942
helpviewer_keywords:
- C2942
ms.assetid: 13abf744-8fa1-450d-886d-e5717c04956e
ms.openlocfilehash: 98bb0d9945068042e00c7c48c0304314e281fa8f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758362"
---
# <a name="compiler-error-c2942"></a>Błąd kompilatora C2942

"Class": Identyfikator klasy typu jest ponownie zdefiniowany jako formalny argument funkcji

Nie można użyć klasy generycznej ani szablonu jako argumentu formalnego. Nie można przekazać argumentu bezpośrednio do konstruktora klasy generycznej lub szablonu.

Poniższy przykład generuje C2942:

```

// C2942.cpp
// compile with: /c
template<class T>
struct TC {};
void f(int TC<int>) {}   // C2942

// OK
struct TC2 {};
void f(TC2 i) {}
```

C2942 może również wystąpić przy użyciu typów ogólnych:

```cpp
// C2942b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
void f(int GC<int>) {}   // C2942
ref struct GC2 { };
void f(int GC2) {}
```
