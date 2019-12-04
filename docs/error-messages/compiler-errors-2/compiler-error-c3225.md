---
title: Błąd kompilatora C3225
ms.date: 11/04/2016
f1_keywords:
- C3225
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
ms.openlocfilehash: 1caa1e7ce787ffc14e615c946b5d670c75e0332a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757621"
---
# <a name="compiler-error-c3225"></a>Błąd kompilatora C3225

argument typu generycznego dla elementu "ARG" nie może być typem "Type", musi być typem wartościowym lub typem dojścia

Nieprawidłowy typ argumentu typu ogólnego.

Aby uzyskać więcej informacji, zobacz [Ogólne](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Nie można utworzyć wystąpienia typu ogólnego z typem natywnym. Poniższy przykład generuje C3225.

```cpp
// C3225.cpp
// compile with: /clr
class A {};

ref class B {};

generic <class T>
ref class C {};

int main() {
   C<A>^ c = gcnew C<A>;   // C3225
   C<B^>^ c2 = gcnew C<B^>;   // OK
}
```

## <a name="example"></a>Przykład

Poniższy przykład tworzy składnik przy użyciu C#. Należy zauważyć, że ograniczenie określa, że typ ogólny można utworzyć tylko przy użyciu typu wartości.

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

## <a name="example"></a>Przykład

Ten przykład zużywa składnik C#--------------Author i narusza ograniczenia, które można utworzyć tylko przy użyciu typu wartości innego niż <xref:System.Nullable>. Poniższy przykład generuje C3225.

```cpp
// C3225_c.cpp
// compile with: /clr
#using "C3225_b.dll"
ref class A {};
value class B {};
int main() {
   MyList<A> x;   // C3225
   MyList<B> y;   // OK
}
```
