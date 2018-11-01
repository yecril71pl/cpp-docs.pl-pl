---
title: Błąd kompilatora C2955
ms.date: 03/28/2017
f1_keywords:
- C2955
helpviewer_keywords:
- C2955
ms.assetid: 77709fb6-d69b-46fd-a62f-e8564563d01b
ms.openlocfilehash: 841dd6ea2258438bf14cbe5338ba8007dee9bb26
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473024"
---
# <a name="compiler-error-c2955"></a>Błąd kompilatora C2955

'Identyfikator': użycie szablonu klasy lub alias ogólny wymaga szablon lub listy argumentów ogólnych

Nie można użyć szablonu klasy lub klas ogólnych jako identyfikator bez szablon lub listy argumentów ogólnych.

Aby uzyskać więcej informacji, zobacz [szablony klas](../../cpp/class-templates.md).

Poniższy przykład generuje C2955 i pokazuje, jak go naprawić:

```
// C2955.cpp
// compile with: /c
template<class T>
class X {};

X x1;   // C2955
X<int> x2;   // OK - this is how to fix it.
```

C2955 może również wystąpić podczas próby definicji poza wierszem funkcja zadeklarowana w szablonie klasy:

```
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

C2955 może również wystąpić, gdy za pomocą typów ogólnych:

```
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

**Visual Studio 2017 i nowszym:** kompilator poprawnie diagnozuje brakuje listy argumentów szablonu, gdy szablon jest wyświetlany na liście parametrów szablonu (na przykład jako część domyślnego argumentu szablonu lub parametru szablonu bez typu). Poniższy kod kompilowany w programie Visual Studio 2015, ale generuje błąd w programie Visual Studio 2017.

```
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```
