---
title: Błąd kompilatora C2939
ms.date: 11/04/2016
f1_keywords:
- C2939
helpviewer_keywords:
- C2939
ms.assetid: 455b050b-f2dc-4b5b-bd6a-e1f81d3d1644
ms.openlocfilehash: 59b2f63ba12a644f13b3586fbf6eec4d5bfa8be5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604194"
---
# <a name="compiler-error-c2939"></a>Błąd kompilatora C2939

"class": typ klasy identyfikator ponownie definiowana jako zmienna danych lokalnych

Nie można użyć klasy generyczny lub szablonu jako zmienna danych lokalnych.

Ten błąd może być spowodowany nawiasy klamrowe są nieprawidłowo dopasowywane.

Poniższy przykład spowoduje wygenerowanie C2939:

```
// C2939.cpp
template<class T>
struct TC { };
int main() {
   int TC<int>;   // C2939
   int TC;   // OK
}
```

C2939 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C2939b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };

int main() {
   int GC<int>;   // C2939
   int GC;   // OK
}
```