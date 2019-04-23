---
title: 'Instrukcje: Poprawianie wydajności za pomocą typów ogólnych (C++sposób niezamierzony)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- performance, C++
- C++, performance
- C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
ms.openlocfilehash: 958da08716022bedaa8d0fe217814fa2bd86c065
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038782"
---
# <a name="how-to-improve-performance-with-generics-ccli"></a>Instrukcje: Poprawianie wydajności za pomocą typów ogólnych (C++sposób niezamierzony)

Za pomocą typów ogólnych można utworzyć na podstawie parametru typu kodu wielokrotnego użytku. Rzeczywisty typ parametru typu jest odroczone do czasu wywołania przez kod klienta. Aby uzyskać więcej informacji na temat typów ogólnych, zobacz [ogólne](generics-cpp-component-extensions.md).

W tym artykule przedstawimy, jak ogólne może pomóc zwiększyć wydajność aplikacji korzystającej z kolekcji.

## <a name="example"></a>Przykład

.NET Framework, który jest dostarczany z wielu klas kolekcji przestrzeni <xref:System.Collections?displayProperty=fullName> przestrzeni nazw. Większość tych kolekcji działają na obiektach typu <xref:System.Object?displayProperty=fullName>. Dzięki temu kolekcji do przechowywania dowolnego typu, ponieważ wszystkie typy w .NET Framework, nawet typy wartości pochodzą z <xref:System.Object?displayProperty=fullName>. Istnieją dwie wady tego podejścia.

Po pierwsze, jeśli kolekcja jest przechowywania typów wartości, takich jak liczb całkowitych, wartość musi być opakowany przed dodaniem do kolekcji i rozpakowywany, gdy wartość jest pobierana z kolekcji. Są to kosztownych operacji.

Po drugie nie ma możliwości kontrolować, które typy mogą być dodawane do kolekcji. Jest idealnie legalne, aby dodać liczbę całkowitą i ciąg do tej samej kolekcji, nawet jeśli jest to, co prawdopodobnie nie był przeznaczony. W związku z tym aby swój kod jest bezpiecznym typem, należy sprawdzić, czy typ pobierane z kolekcji naprawdę oczekiwanym.

Poniższy przykład kodu pokazuje dwa główne minusy kolekcji .NET Framework przed typów ogólnych.

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

## <a name="example"></a>Przykład

Nowy <xref:System.Collections.Generic?displayProperty=fullName> przestrzeń nazw zawiera wiele można znaleźć w kolekcji ten sam <xref:System.Collections?displayProperty=fullName> przestrzeni nazw, ale zostały zmodyfikowane w celu akceptowania parametrów typu genetycznego. Eliminuje to dwie wady innych niż ogólne kolekcje: pakowania i rozpakowywania typów wartości i z brakiem, aby określić typy, które mają być przechowywane w kolekcjach. Operacje na dwie kolekcje są identyczne; różnią się tylko po to, w jaki sposób są tworzone.

Porównaj przykład powyżej napisanych przy użyciu następującego przykładu, który korzysta z ogólnego <xref:System.Collections.Generic.Stack%601> kolekcji. W dużych kolekcjach, które są często używane wydajności, w tym przykładzie będzie znacznie większa niż poprzedniego przykładu.

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