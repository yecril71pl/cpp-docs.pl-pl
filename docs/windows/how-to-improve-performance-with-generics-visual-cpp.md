---
title: 'Porady: poprawianie wydajności z typów ogólnych (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- performance, C++
- Visual C++, performance
- Visual C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c16dccd78abfc4a90dc0faea534c999a52b7b79
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-improve-performance-with-generics-visual-c"></a>Porady: poprawianie wydajności za pomocą typów ogólnych (Visual C++)
Z ogólnymi można utworzyć do ponownego użycia kodu na podstawie parametru typu. Rzeczywisty typ parametru typu została odroczona, dopóki wywoływany przez kod klienta. Aby uzyskać więcej informacji dotyczących typów ogólnych, zobacz [ogólne](../windows/generics-cpp-component-extensions.md).  
  
 W tym artykule przedstawimy, jak ogólne może pomóc zwiększyć wydajność aplikacji, która korzysta z kolekcji.  
  
## <a name="example"></a>Przykład  
 .NET Framework jest dostarczany z wielu klas kolekcji w <xref:System.Collections?displayProperty=fullName> przestrzeni nazw. Większość tych kolekcji działanie na obiektach typu <xref:System.Object?displayProperty=fullName>. Dzięki temu kolekcje do przechowywania dowolnego typu, ponieważ wszystkie typy w programie .NET Framework, nawet typy wartości, pochodzi z <xref:System.Object?displayProperty=fullName>. Istnieją dwie wady tej metody.  
  
 Najpierw Jeśli kolekcja jest przechowywana typy wartości, takich jak liczby całkowite, wartość musi być opakowany przed dodaniem go do kolekcji i rozpakowany, gdy wartość jest pobierana z kolekcji. Są to kosztowne operacje.  
  
 Po drugie nie istnieje sposób kontrolować typy, które można dodać do kolekcji. Jest doskonale prawnych, aby dodać do tej samej kolekcji liczba całkowita i ciąg, nawet jeśli jest to prawdopodobnie nie został przeznaczenie. W związku z tym aby kodu do typu bezpieczne, należy sprawdzić, czy typ pobrane z kolekcji jest naprawdę oczekiwanym.  
  
 Poniższy przykładowy kod przedstawia dwa główne wady kolekcji .NET Framework, przed typów ogólnych.  
  
```  
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
 Nowy <xref:System.Collections.Generic?displayProperty=fullName> przestrzeń nazw zawiera wiele kolekcji tego samego odnaleźć w <xref:System.Collections?displayProperty=fullName> przestrzeni nazw, ale został zmodyfikowany w celu akceptowania parametry typu ogólnego. Eliminuje to dwie wady kolekcja nierodzajową: opakowywanie i rozpakowywanie typów wartości i niemożność Określ typy, które mają być przechowywane w kolekcji. Operacje na dwie kolekcje są identyczne; różnią się tylko w sposób ich wystąpienia.  
  
 Porównanie przykład podano powyżej z tego przykładu, która korzysta z ogólnego <xref:System.Collections.Generic.Stack%601> kolekcji. W dużych kolekcjach, które są często używane wydajność w tym przykładzie będzie znacznie większą niż w poprzednim przykładzie.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](../windows/generics-cpp-component-extensions.md)