---
title: Błąd kompilatora C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: 1c58c2d5da0049ec670e11c930b397caec3cbbee
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751524"
---
# <a name="compiler-error-c2990"></a>Błąd kompilatora C2990

"Class": typ inny niż Klasa jako zadeklarowany jako typ klasy

Klasa niegeneryczna lub szablonu ponownie definiuje klasę generyczną lub szablonową. Sprawdź pliki nagłówkowe pod kątem konfliktów.

Poniższy przykład generuje C2990:

```cpp
// C2990.cpp
// compile with: /c
template <class T>
class C{};
class C{};   // C2990
```

C2990 może również wystąpić przy użyciu typów ogólnych:

```cpp
// C2990b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC;

ref struct GC {};   // C2990
```

C2990 może również wystąpić ze względu na nieprzerwaną zmianę C++ w kompilatorze Microsoft dla programu Visual Studio 2005; kompilator wymaga teraz, aby wiele deklaracji tego samego typu były identyczne z uwzględnieniem specyfikacji szablonu.

Poniższy przykład generuje C2990:

```cpp
// C2990c.cpp
// compile with: /c
template<class T>
class A;

template<class T>
struct A2 {
   friend class A;   // C2990
};

// OK
template<class T>
struct B {
   template<class T>
   friend class A;
};
```
