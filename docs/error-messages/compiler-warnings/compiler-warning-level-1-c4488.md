---
title: Kompilator ostrzeżenie (poziom 1) C4488
ms.date: 11/04/2016
f1_keywords:
- C4488
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
ms.openlocfilehash: c816c1b3f5481ccff19fd2a2377c5fc98f950fee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577830"
---
# <a name="compiler-warning-level-1-c4488"></a>Kompilator ostrzeżenie (poziom 1) C4488

'Funkcja': wymaga słowa kluczowego "— słowo kluczowe" zaimplementować metodę interfejsu "interface_method"

Klasa musi implementować interfejs, po którym bezpośrednio dziedziczy wszystkich członków. Element członkowski zaimplementowano musi mieć dostęp publiczny i musi być oznaczona jako wirtualna.

## <a name="example"></a>Przykład

C4488 może wystąpić, jeśli zaimplementowano elementu członkowskiego nie jest publiczna. Poniższy przykład spowoduje wygenerowanie C4488.

```
// C4488.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

// implemented member not public
ref class B : MyI { virtual void f1() {} };  // C4488

// OK
ref class C : MyI {
public:
   virtual void f1() {}
};
```

## <a name="example"></a>Przykład

C4488 może wystąpić, jeśli zaimplementowano elementu członkowskiego nie jest oznaczona jako wirtualny. Poniższy przykład spowoduje wygenerowanie C4488.

```
// C4488_b.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

ref struct B : MyI { void f1() {} };   // C4488
ref struct C : MyI { virtual void f1() {} };   // OK
```