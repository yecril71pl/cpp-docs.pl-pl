---
title: Błąd kompilatora C2678
ms.date: 11/04/2016
f1_keywords:
- C2678
helpviewer_keywords:
- C2678
ms.assetid: 1f0a4e26-b429-44f5-9f94-cb66441220c8
ms.openlocfilehash: 9055210401e14eeb9fdb88266870ac8fe5cbd496
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580989"
---
# <a name="compiler-error-c2678"></a>Błąd kompilatora C2678

plik binarny 'operator': nie operator zdefiniowany, który przyjmuje lewostronny operand typu "type" (lub nie jest dopuszczalne konwersja)

Użycie operatora, możesz go przeciążenia dla określonego typu lub zdefiniuj konwersji na typ, dla którego zdefiniowano operator.

## <a name="example"></a>Przykład

C2678 może wystąpić, gdy lewostronny operand jest kwalifikowanego, ale zdefiniowano operator zostały w nim argumentu wartości innej niż stała.

Poniższy przykład generuje C2678 i pokazuje, jak go naprawić:

```
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

## <a name="example"></a>Przykład

C2678 może również wystąpić, jeśli natywnych elementu członkowskiego nie należy umieszczać przed wywołaniem funkcji członkowskiej w nim.

Poniższy przykład generuje C2678 i pokazuje, jak go naprawić.

```
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
