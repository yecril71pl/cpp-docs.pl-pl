---
title: Błąd kompilatora C2942
ms.date: 11/04/2016
f1_keywords:
- C2942
helpviewer_keywords:
- C2942
ms.assetid: 13abf744-8fa1-450d-886d-e5717c04956e
ms.openlocfilehash: 8a594b9d1d8374caa972f6bfdafe5d691e634a9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366644"
---
# <a name="compiler-error-c2942"></a>Błąd kompilatora C2942

"class": typ klasy identyfikator ponownie definiowana jako argument formalny funkcji

Generyczny lub szablonu klasy nie można użyć jako argumentu formalnego. Nie można przekazać argument bezpośrednio do konstruktora ogólnego lub klasą szablonu.

Poniższy przykład spowoduje wygenerowanie C2942:

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

C2942 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C2942b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
void f(int GC<int>) {}   // C2942
ref struct GC2 { };
void f(int GC2) {}
```