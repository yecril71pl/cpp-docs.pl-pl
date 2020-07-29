---
title: Błąd kompilatora C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 9b6b7bb54d5dce48dc6fce517eb0c909b0284da2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233447"
---
# <a name="compiler-error-c2885"></a>Błąd kompilatora C2885

"Class:: identifier": nie jest prawidłową deklaracją Using w zakresie nieklasowym

Użyto nieprawidłowej deklaracji [using](../../cpp/using-declaration.md) .

## <a name="example"></a>Przykład

Ten błąd może zostać wygenerowany w wyniku pracy zgodnej z kompilatorem, który został wykonany dla programu Visual Studio 2005: nie jest już prawidłowa **`using`** Deklaracja do typu zagnieżdżonego; należy jawnie zakwalifikować każde odwołanie do typu zagnieżdżonego, umieścić typ w przestrzeni nazw lub utworzyć element typedef.

Poniższy przykład generuje C2885.

```cpp
// C2885.cpp
namespace MyNamespace {
   class X1 {};
}

struct MyStruct {
   struct X1 {
      int i;
   };
};

int main () {
   using MyStruct::X1;   // C2885

   // OK
   using MyNamespace::X1;
   X1 myX1;

   MyStruct::X1 X12;

   typedef MyStruct::X1 abc;
   abc X13;
   X13.i = 9;
}
```

## <a name="example"></a>Przykład

Jeśli używasz **`using`** słowa kluczowego z składową klasy, C++ wymaga zdefiniowania tego elementu członkowskiego wewnątrz innej klasy (klasy pochodnej).

Poniższy przykład generuje C2885.

```cpp
// C2885_b.cpp
// compile with: /c
class A {
public:
   int i;
};

void z() {
   using A::i;   // C2885 not in a class
}

class B : public A {
public:
   using A::i;
};
```
