---
title: Delegaty ogólne (Visual C++) | Dokumentacja firmy Microsoft
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
- generic delegates
- delegates, generic [C++]
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f5e1635afb2c11dbb7835244eae776fabdaea9c0
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="generic-delegates-visual-c"></a>Delegaty ogólne (Visual C++)
Z obiektów delegowanych można używać parametrów typu ogólnego. Aby uzyskać więcej informacji na delegatów, zobacz [delegata (C++ Component Extensions)](../windows/delegate-cpp-component-extensions.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
[attributes]   
generic < [class | typename] type-parameter-identifiers>  
[type-parameter-constraints-clauses]  
[accessibility-modifiers] delegate result-type identifier   
([formal-parameters]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `attributes` (Opcjonalnie)  
 Dodatkowe informacje deklaratywne. Aby uzyskać więcej informacji na atrybuty i klasy atrybutów Zobacz atrybutów.  
  
 *Typ — parametr-identyfikatory*  
 Rozdzielana przecinkami lista identyfikatorów dla parametrów typu.  
  
 `type-parameter-constraints-clauses`  
 Ma postać określone w [ograniczenia dotyczące parametrów typu ogólnego (C + +/ CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)  
  
 *modyfikatory dostępności* (opcjonalnie)  
 Modyfikatory dostępności (np. **publicznego**, `private`).  
  
 *result-type*  
 Typ zwracany delegata.  
  
 *identifier*  
 Nazwa obiektu delegowanego.  
  
 *parametrów formalnych* (opcjonalnie)  
 Lista parametrów delegata.  
  
## <a name="example"></a>Przykład  
 Określono parametry typu delegata w momencie, gdy tworzony jest obiekt delegowany. Zarówno delegata, jak i metody skojarzonych z nim musi mieć taką samą sygnaturę. Oto przykład deklaracja Delegat ogólny.  
  
```  
// generics_generic_delegate1.cpp  
// compile with: /clr /c  
generic <class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, że  
  
-   Nie można używać tego samego obiektu delegowanego różne typy utworzone. Tworzenie delegata różnych obiektów dla różnych typów.  
  
-   Delegat ogólny może być skojarzony z metody rodzajowej.  
  
-   Po wywołaniu metody rodzajowej bez określania argumentów typu, kompilator próbuje wywnioskować argumentów typu dla wywołania.  
  
```  
// generics_generic_delegate2.cpp  
// compile with: /clr  
generic <class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
  
generic <class ItemType>  
ref struct MyGenClass {  
   ItemType MyMethod(ItemType i, ItemType % j) {  
      return ItemType();  
   }  
};  
  
ref struct MyClass {  
   generic <class ItemType>  
   static ItemType MyStaticMethod(ItemType i, ItemType % j) {  
      return ItemType();  
   }  
};  
  
int main() {  
   MyGenClass<int> ^ myObj1 = gcnew MyGenClass<int>();  
   MyGenClass<double> ^ myObj2 = gcnew MyGenClass<double>();  
   GenDelegate<int>^ myDelegate1 =  
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);  
  
   GenDelegate<double>^ myDelegate2 =   
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);  
  
   GenDelegate<int>^ myDelegate =  
      gcnew GenDelegate<int>(&MyClass::MyStaticMethod<int>);  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje Delegat ogólny `GenDelegate<ItemType>`i tworzy on przez skojarzenie jej z metodą `MyMethod` używającą parametr typu `ItemType`. Dwa wystąpienia delegata (całkowitą i wartość o podwójnej precyzji) są tworzone i wywoływane.  
  
```  
// generics_generic_delegate.cpp  
// compile with: /clr  
using namespace System;  
  
// declare generic delegate  
generic <typename ItemType>  
delegate ItemType GenDelegate (ItemType p1, ItemType% p2);  
  
// Declare a generic class:  
generic <typename ItemType>  
ref class MyGenClass {  
public:  
   ItemType MyMethod(ItemType p1, ItemType% p2) {  
      p2 = p1;  
      return p1;  
    }  
};  
  
int main() {  
   int i = 0, j = 0;   
   double m = 0.0, n = 0.0;  
  
   MyGenClass<int>^ myObj1 = gcnew MyGenClass<int>();  
   MyGenClass<double>^ myObj2 = gcnew MyGenClass<double>();   
  
   // Instantiate a delegate using int.  
   GenDelegate<int>^ MyDelegate1 =   
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);  
  
   // Invoke the integer delegate using MyMethod.  
   i = MyDelegate1(123, j);  
  
   Console::WriteLine(  
      "Invoking the integer delegate: i = {0}, j = {1}", i, j);  
  
   // Instantiate a delegate using double.  
   GenDelegate<double>^ MyDelegate2 =   
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);  
  
   // Invoke the integer delegate using MyMethod.  
   m = MyDelegate2(0.123, n);  
  
   Console::WriteLine(  
      "Invoking the double delegate: m = {0}, n = {1}", m, n);  
}  
```  
  
```Output  
Invoking the integer delegate: i = 123, j = 123  
Invoking the double delegate: m = 0.123, n = 0.123  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](../windows/generics-cpp-component-extensions.md)