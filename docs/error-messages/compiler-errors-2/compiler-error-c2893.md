---
title: Błąd kompilatora C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: ca603eb94d5d528a7fed15e0320e1f5d88bf0629
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760879"
---
# <a name="compiler-error-c2893"></a>Błąd kompilatora C2893

Nie powiodła się specjalizacja szablonu funkcji "Nazwa szablonu"

Kompilator nie może przeprowadzić specjalizacji szablonu funkcji. Może istnieć wiele przyczyn tego błędu.

Ogólnie rzecz biorąc, metoda rozwiązywania błędu C2893 polega na przejrzeniu podpisu funkcji i upewnieniu się, że można utworzyć wystąpienie każdego typu.

## <a name="example"></a>Przykład

C2893 występuje, ponieważ `T` parametru szablonu `f`jest `std::map<int,int>`, ale `std::map<int,int>` nie ma elementu członkowskiego `data_type` (`T::data_type` nie można utworzyć wystąpienia z `T = std::map<int,int>`.). Poniższy przykład generuje C2893.

```cpp
// C2893.cpp
// compile with: /c /EHsc
#include<map>
using namespace std;
class MyClass {};

template<class T>
inline typename T::data_type
// try the following line instead
// inline typename  T::mapped_type
f(T const& p1, MyClass const& p2);

template<class T>
void bar(T const& p1) {
    MyClass r;
    f(p1,r);   // C2893
}

int main() {
   map<int,int> m;
   bar(m);
}
```
