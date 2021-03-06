---
title: Błąd kompilatora C2678
ms.date: 11/04/2016
f1_keywords:
- C2678
helpviewer_keywords:
- C2678
ms.assetid: 1f0a4e26-b429-44f5-9f94-cb66441220c8
ms.openlocfilehash: c8f5b06e6c2f9966d714f4a360525617dbff400f
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743181"
---
# <a name="compiler-error-c2678"></a>Błąd kompilatora C2678

Binary "operator": nie zdefiniowano operatora, który pobiera operand z lewej strony typu "Type" (lub nie istnieje akceptowalna konwersja)

Aby użyć operatora, należy przeciążyć go dla określonego typu lub zdefiniować konwersję do typu, dla którego zdefiniowano operator.

C2678 może wystąpić, gdy argument operacji po lewej stronie jest kwalifikowany z kwalifikatorem, ale operator jest zdefiniowany, aby przyjmować argument inny niż const.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C2678 i pokazuje, jak to naprawić:

```cpp
// C2678a.cpp
// Compile by using: cl /EHsc /W4 C2678a.cpp
struct Combo {
   int number;
   char letter;
};

inline Combo& operator+=(Combo& lhs, int rhs) {
   lhs.number += rhs;
   return lhs;
}

int main() {
   Combo const combo1{ 42, 'X' };
   Combo combo2{ 13, 'Z' };

   combo1 += 6; // C2678
   combo2 += 9; // OK - operator+= matches non-const Combo
}
```

C2678 może również wystąpić, jeśli nie przypinasz natywnego elementu członkowskiego przed wywołaniem funkcji składowej.

Poniższy przykład generuje C2678 i pokazuje, jak rozwiązać ten problem.

```cpp
// C2678.cpp
// compile with: /clr /c
struct S { int _a; };

ref class C {
public:
   void M( S param ) {
      test = param;   // C2678

      // OK
      pin_ptr<S> ptest = &test;
      *ptest = param;
   }
   S test;
};
```
