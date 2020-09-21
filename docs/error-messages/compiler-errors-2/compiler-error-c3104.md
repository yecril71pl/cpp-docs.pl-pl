---
title: Błąd kompilatora C3104
ms.date: 11/04/2016
f1_keywords:
- C3104
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
ms.openlocfilehash: 5f72af3d7149db7362df9fa23ac5ad6c058c552b
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743467"
---
# <a name="compiler-error-c3104"></a>Błąd kompilatora C3104

niedozwolony argument atrybutu

Określono nieprawidłowy argument dla atrybutu.

Aby uzyskać więcej informacji, zobacz [typy parametrów atrybutów](../../extensions/attribute-parameter-types-cpp-component-extensions.md) .

Ten błąd może zostać wygenerowany w wyniku działania kompilatora, który został wykonany dla programu Visual Studio 2005: podczas przekazywania tablic zarządzanych do atrybutów niestandardowych typ tablicy nie jest już określany na podstawie listy inicjalizacji agregacji. Kompilator wymaga teraz, aby określić typ tablicy oraz listę inicjatorów.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C3104.

```cpp
// C3104a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104
// try the following line instead
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

Poniższy przykład generuje C3104.

```cpp
// C3104b.cpp
// compile with: /clr /c
// C3104 expected
using namespace System;

int func() {
   return 0;
}

[attribute(All)]
ref class A {
public:
   A(int) {}
};

// Delete the following 2 lines to resolve.
[A(func())]
ref class B {};

// OK
[A(0)]
ref class B {};
```
