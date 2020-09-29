---
title: 'Instrukcje: poprawianie wydajności za pomocą typów ogólnych (C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- performance, C++
- C++, performance
- C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
ms.openlocfilehash: 039c5b069351249e51d961d9d1757ed6b09ef99c
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414168"
---
# <a name="how-to-improve-performance-with-generics-ccli"></a>Instrukcje: poprawianie wydajności za pomocą typów ogólnych (C++/CLI)

W przypadku typów ogólnych można utworzyć kod wielokrotnego użytku oparty na parametrze typu. Rzeczywisty typ parametru typu jest odroczony do momentu wywołania przez kod klienta. Aby uzyskać więcej informacji na temat typów ogólnych, zobacz [typy ogólne](generics-cpp-component-extensions.md).

W tym artykule omówiono sposób, w jaki typy ogólne mogą pomóc zwiększyć wydajność aplikacji korzystającej z kolekcji.

## <a name="example-two-main-drawbacks-of-net-framework-collections"></a>Przykład: dwa główne wady kolekcji .NET Framework

.NET Framework zawiera wiele klas kolekcji w <xref:System.Collections?displayProperty=fullName> przestrzeni nazw. Większość z tych kolekcji działa na obiektach typu <xref:System.Object?displayProperty=fullName> . Dzięki temu kolekcje mogą przechowywać dowolny typ, ponieważ wszystkie typy w .NET Framework typy wartości parzystych pochodne od <xref:System.Object?displayProperty=fullName> . Istnieją jednak dwie wady tego podejścia.

Po pierwsze, jeśli kolekcja przechowuje typy wartości, takie jak liczby całkowite, wartość musi być opakowana przed dodaniem do kolekcji i nieopakowany, gdy wartość jest pobierana z kolekcji. Są to kosztowne operacje.

Po drugie nie istnieje sposób sterowania tym, które typy można dodać do kolekcji. Dobrze jest dodać liczbę całkowitą i ciąg do tej samej kolekcji, nawet jeśli jest to prawdopodobnie nieoczekiwane. W związku z tym, aby kod był bezpieczny, należy sprawdzić, czy typ pobrany z kolekcji rzeczywiście jest oczekiwany.

Poniższy przykład kodu przedstawia dwa główne wady kolekcji .NET Framework przed ogólnymi.

```cpp
// perf_pre_generics.cpp
// compile with: /clr

using namespace System;
using namespace System::Collections;

int main()
{
    // This Stack can contain any type.
    Stack ^s = gcnew Stack();

    // Push an integer to the Stack.
    // A boxing operation is performed here.
    s->Push(7);

    // Push a String to the same Stack.
    // The Stack now contains two different data types.
    s->Push("Seven");

    // Pop the items off the Stack.
    // The item is returned as an Object, so a cast is
    // necessary to convert it to its proper type.
    while (s->Count> 0)
    {
        Object ^o = s->Pop();
        if (o->GetType() == Type::GetType("System.String"))
        {
            Console::WriteLine("Popped a String: {0}", (String ^)o);
        }
        else if (o->GetType() == Type::GetType("System.Int32"))
        {
            Console::WriteLine("Popped an int: {0}", (int)o);
        }
        else
        {
            Console::WriteLine("Popped an unknown type!");
        }
    }
}
```

```Output
Popped a String: Seven
Popped an int: 7
```

## <a name="example-benefit-of-using-generic-collection"></a>Przykład: korzyści wynikające z używania kolekcji ogólnej

Nowa <xref:System.Collections.Generic?displayProperty=fullName> przestrzeń nazw zawiera wiele z tych samych kolekcji znalezionych w <xref:System.Collections?displayProperty=fullName> przestrzeni nazw, ale zostały zmodyfikowane w celu akceptowania parametrów typu ogólnego. Eliminuje to dwie wady nieogólnych kolekcji: opakowanie i rozpakowywanie typów wartości i niemożność określenia typów, które mają być przechowywane w kolekcjach. Operacje w dwóch kolekcjach są identyczne. różnią się one tylko sposobem tworzenia wystąpienia.

Porównaj przykład zapisany powyżej z tym przykładem, który używa <xref:System.Collections.Generic.Stack%601> kolekcji ogólnej. W przypadku dużych kolekcji, które są często używane, wydajność tego przykładu będzie znacznie większa niż w poprzednim przykładzie.

```cpp
// perf_post_generics.cpp
// compile with: /clr

#using <System.dll>

using namespace System;
using namespace System::Collections::Generic;

int main()
{
    // This Stack can only contain integers.
    Stack<int> ^s = gcnew Stack<int>();

    // Push an integer to the Stack.
    // A boxing operation is performed here.
    s->Push(7);
    s->Push(14);

    // You can no longer push a String to the same Stack.
    // This will result in compile time error C2664.
    //s->Push("Seven");

    // Pop an item off the Stack.
    // The item is returned as the type of the collection, so no
    // casting is necessary and no unboxing is performed for
    // value types.
    int i = s->Pop();
    Console::WriteLine(i);

    // You can no longer retrieve a String from the Stack.
    // This will result in compile time error C2440.
    //String ^str = s->Pop();
}
```

```Output
14
```

## <a name="see-also"></a>Zobacz także

[Typy ogólne](generics-cpp-component-extensions.md)
