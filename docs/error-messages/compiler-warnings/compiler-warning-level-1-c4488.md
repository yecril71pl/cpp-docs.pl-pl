---
title: Kompilator ostrzeżenie (poziom 1) C4488 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4488
dev_langs:
- C++
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d2cccedada47519ada55353cb44faab0e34cf03
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118274"
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