---
title: Błąd kompilatora C2893 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2893
dev_langs:
- C++
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73d4f838f030db3667b08295006c2ea1df94c87b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026182"
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