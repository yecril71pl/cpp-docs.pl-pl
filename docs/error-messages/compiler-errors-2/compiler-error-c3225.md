---
title: Błąd kompilatora C3225
ms.date: 11/04/2016
f1_keywords:
- C3225
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
ms.openlocfilehash: ed645535300e0a7c4d27f8bed43d3143bae7e97a
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742869"
---
# <a name="compiler-error-c3225"></a>Błąd kompilatora C3225

argument typu generycznego dla elementu "ARG" nie może być typem "Type", musi być typem wartościowym lub typem dojścia

Nieprawidłowy typ argumentu typu ogólnego.

Aby uzyskać więcej informacji, zobacz [Ogólne](../../extensions/generics-cpp-component-extensions.md).

## <a name="examples"></a>Przykłady

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

Poniższy przykład tworzy składnik przy użyciu języka C#. Należy zauważyć, że ograniczenie określa, że typ ogólny można utworzyć tylko przy użyciu typu wartości.

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

Ten przykład korzysta ze składnika napisanego w języku C# i narusza ograniczenia, które można utworzyć tylko na liście z typem wartości innym niż <xref:System.Nullable> . Poniższy przykład generuje C3225.

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
