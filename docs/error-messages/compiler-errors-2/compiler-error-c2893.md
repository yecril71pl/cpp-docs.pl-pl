---
title: Błąd kompilatora C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: f1fad1ad18af54945ef32dadaac50a6de4dbd62f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366384"
---
# <a name="compiler-error-c2893"></a>Błąd kompilatora C2893

Nie powiodła się specjalizacja szablonu funkcji "Nazwa szablonu"

Kompilator nie powiodła się specjalizacja szablonu funkcji. Może istnieć wiele przyczyn tego błędu.

Ogólnie rzecz biorąc sposób, aby rozwiązać błąd C2893 jest Przejrzyj podpisu funkcji i upewnij się, że można utworzyć wystąpienie każdego typu.

## <a name="example"></a>Przykład

C2893 występuje, ponieważ `f`firmy parametru szablonu `T` jest wywnioskowano `std::map<int,int>`, ale `std::map<int,int>` nie ma składowej `data_type` (`T::data_type` nie może zostać utworzona za pomocą `T = std::map<int,int>`.). Poniższy przykład spowoduje wygenerowanie C2893.

```
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