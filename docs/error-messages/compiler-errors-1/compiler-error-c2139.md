---
title: Błąd kompilatora C2139
ms.date: 11/04/2016
f1_keywords:
- C2139
helpviewer_keywords:
- C2139
ms.assetid: 31e047c0-5bf9-46c2-b6de-b627ea6a5768
ms.openlocfilehash: 15813216399c0f00fea036cd95443235e7acf4c3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769085"
---
# <a name="compiler-error-c2139"></a>Błąd kompilatora C2139

"type": Niezdefiniowana klasa nie jest dozwolona jako argument typu wewnętrznej cechy kompilatora "cechy"

Do cechy typu przekazano nieprawidłowy argument.

Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../../extensions/compiler-support-for-type-traits-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2139.

```
// C2139.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T>
struct is_polymorphic {
   static const bool value = __is_polymorphic(T);
};

class C;
class D {};

class E {
public:
   virtual void Test() {}
};

int main() {
   cout << is_polymorphic<C>::value << endl;   // C2139
   cout << is_polymorphic<D>::value << endl;   // OK
   cout << is_polymorphic<E>::value << endl;   // OK
}
```