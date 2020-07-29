---
title: Błąd kompilatora C2676
ms.date: 11/04/2016
f1_keywords:
- C2676
helpviewer_keywords:
- C2676
ms.assetid: 838a5e34-c92f-4f65-a597-e150bf8cf737
ms.openlocfilehash: 1b999875aa1c7ef34065c0a36046c634308075f5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218198"
---
# <a name="compiler-error-c2676"></a>Błąd kompilatora C2676

element binarny "operator": "Type" nie definiuje tego operatora lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora

Aby użyć operatora, należy przeciążyć go dla określonego typu lub zdefiniować konwersję do typu, dla którego zdefiniowano operator.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2676.

```cpp
// C2676.cpp
// C2676 expected
struct C {
   C();
} c;

struct D {
   D();
   D operator >>( C& ){return * new D;}
   D operator <<( C& ){return * new D;}
} d;

struct E {
   // operator int();
};

int main() {
   d >> c;
   d << c;
   E e1, e2;
   e1 == e2;   // uncomment operator int in class E, then
               // it is OK even though neither E::operator==(E) nor
               // operator==(E, E) defined. Uses the conversion to int
               // and then the builtin-operator==(int, int)
}
```

## <a name="example"></a>Przykład

C2676 może również wystąpić, jeśli spróbujesz przeprowadzić arytmetyczne wskaźnika na **`this`** wskaźniku typu odwołania.

**`this`** Wskaźnik jest typu dojścia w typie referencyjnym. Aby uzyskać więcej informacji, zobacz [semantyka tego wskaźnika](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).

Poniższy przykład generuje C2676.

```cpp
// C2676_a.cpp
// compile with: /clr
using namespace System;

ref struct A {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }

   A() {
      Console::WriteLine("{0}", this + 3.3);   // C2676
      Console::WriteLine("{0}", this[3.3]);   // OK
   }
};

int main() {
   A ^ mya = gcnew A();
}
```
