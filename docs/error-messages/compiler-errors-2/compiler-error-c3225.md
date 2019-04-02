---
title: Błąd kompilatora C3225
ms.date: 11/04/2016
f1_keywords:
- C3225
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
ms.openlocfilehash: cae0572002c849fb5aed771993d3a89ed82c726a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58778315"
---
# <a name="compiler-error-c3225"></a>Błąd kompilatora C3225

argument Typ generycznego dla "arg" nie może być "type", musi on być typem wartościowym lub typem uchwytu

Argument typu ogólnego nie jest poprawnego typu.

Aby uzyskać więcej informacji, zobacz [ogólne](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Nie można utworzyć wystąpienia typu ogólnego z typu natywnego. Poniższy przykład spowoduje wygenerowanie C3225.

```
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

Poniższy przykład tworzy składnik przy użyciu języka C#. Należy zauważyć, że ograniczenia Określa typ ogólny tylko mogą być utworzone z typem wartości.

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

## <a name="example"></a>Przykład

W tym przykładzie używa języka C# — utworzone składnika i narusza ograniczenie, które mogą być tylko MyList utworzone za pomocą typu wartości innych niż <xref:System.Nullable>. Poniższy przykład spowoduje wygenerowanie C3225.

```
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