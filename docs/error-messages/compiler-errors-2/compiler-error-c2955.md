---
title: Błąd kompilatora C2955
ms.date: 03/28/2017
f1_keywords:
- C2955
helpviewer_keywords:
- C2955
ms.assetid: 77709fb6-d69b-46fd-a62f-e8564563d01b
ms.openlocfilehash: 8afdeaf43c0c9789753b9165f1e8a8287aaac76d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742876"
---
# <a name="compiler-error-c2955"></a>Błąd kompilatora C2955

"Identyfikator": użycie szablonu klasy lub aliasu generycznego wymaga szablonu lub listy argumentów ogólnych

Nie można użyć szablonu klasy ani klasy generycznej jako identyfikatora bez szablonu lub listy argumentów ogólnych.

Aby uzyskać więcej informacji, zobacz [Szablony klas](../../cpp/class-templates.md).

Poniższy przykład generuje C2955 i pokazuje, jak to naprawić:

```cpp
// C2955.cpp
// compile with: /c
template<class T>
class X {};

X x1;   // C2955
X<int> x2;   // OK - this is how to fix it.
```

C2955 może również wystąpić przy próbie zdefiniowania poza wierszem funkcji zadeklarowanej w szablonie klasy:

```cpp
// C2955_b.cpp
// compile with: /c
template <class T>
class CT {
public:
   void CTFunc();
   void CTFunc2();
};

void CT::CTFunc() {}   // C2955

// OK - this is how to fix it
template <class T>
void CT<T>::CTFunc2() {}
```

C2955 może również wystąpić przy użyciu typów ogólnych:

```cpp
// C2955_c.cpp
// compile with: /clr
generic <class T>
ref struct GC {
   T t;
};

int main() {
   GC^ g;   // C2955
   GC <int>^ g;
}
```

## <a name="example"></a>Przykład

**Program Visual Studio 2017 lub nowszy:** Kompilator prawidłowo diagnozuje brakujące listy argumentów szablonu, gdy szablon pojawia się na liście parametrów szablonu (na przykład jako część argumentu szablonu domyślnego lub parametru szablonu bez typu). Poniższy kod kompiluje się w programie Visual Studio 2015, ale powoduje wystąpienie błędu w programie Visual Studio 2017.

```
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```
