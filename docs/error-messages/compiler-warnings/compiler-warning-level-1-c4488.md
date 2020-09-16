---
title: Ostrzeżenie kompilatora (poziom 1) C4488
ms.date: 11/04/2016
f1_keywords:
- C4488
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
ms.openlocfilehash: 6db814e405c0b13cdf40fc81a1f23c6d59fd5f00
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684667"
---
# <a name="compiler-warning-level-1-c4488"></a>Ostrzeżenie kompilatora (poziom 1) C4488

"Function": wymaga słowa kluczowego "Keyword", aby zaimplementować metodę interfejsu "interface_method"

Klasa musi implementować wszystkie elementy członkowskie interfejsu, z których dziedziczy bezpośredni. Zaimplementowana składowa musi mieć publiczną dostępność i musi być oznaczona jako wirtualna.

## <a name="examples"></a>Przykłady

C4488 może wystąpić, jeśli zaimplementowany element członkowski nie jest publiczny. Poniższy przykład generuje C4488.

```cpp
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

C4488 może wystąpić, jeśli zaimplementowany element członkowski nie jest oznaczony jako wirtualny. Poniższy przykład generuje C4488.

```cpp
// C4488_b.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

ref struct B : MyI { void f1() {} };   // C4488
ref struct C : MyI { virtual void f1() {} };   // OK
```
