---
title: Błąd kompilatora C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: e60f3fff2ef61f4d6374072c05a2ad3e64a57031
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760931"
---
# <a name="compiler-error-c2885"></a>Błąd kompilatora C2885

"Class:: identifier": nie jest prawidłową deklaracją Using w zakresie nieklasowym

Użyto nieprawidłowej deklaracji [using](../../cpp/using-declaration.md) .

## <a name="example"></a>Przykład

Ten błąd może być wygenerowany jako wynik zgodności kompilatora, który został wykonany dla programu Visual Studio 2005: nie jest już prawidłowym elementem deklaracji `using` dla typu zagnieżdżonego; należy jawnie zakwalifikować każde odwołanie do typu zagnieżdżonego, umieścić typ w przestrzeni nazw lub utworzyć typedef.

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

Użycie słowa kluczowego `using` z elementem członkowskim klasy C++ wymaga zdefiniowania tego elementu członkowskiego wewnątrz innej klasy (klasy pochodnej).

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
