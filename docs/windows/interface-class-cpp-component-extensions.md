---
title: Interfejs klasy (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: interface_CPP
dev_langs: C++
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: abe4173dabd20442b96c8e5536b040483df4f150
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="interface-class--c-component-extensions"></a>interface class (C++ Component Extensions)
Deklaruje interfejsu.  Informacji dla natywnych interfejsów, temacie [__interface](../cpp/interface.md).  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 **Składnia**  
  
```  
  
interface_access  
interface class  
 name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};  
```  
  
 **Parametry**  
  
 *interface_access*  
 Ułatwienia dostępu interfejsu poza zestaw.  Możliwe wartości to **publicznego** i `private`.  `private`jest ustawieniem domyślnym.  Zagnieżdżone interfejsów nie mogą mieć *interface_access* specyfikator.  
  
 *Nazwa*  
 Nazwa interfejsu.  
  
 *inherit_access*  
 Dostępność *base_interface*.  Tylko dozwolone ułatwień dostępu dla interfejs podstawowy jest `public` (ustawienie domyślne).  
  
 *base_interface* (opcjonalnie)  
 Podstawowy interfejs dla interfejsu *nazwa*.  
  
 **Uwagi**  
  
 **Interface struct** jest odpowiednikiem **interfejsu klasy**.  
  
 Interfejs może zawierać deklaracje funkcji, zdarzeń i właściwości.  Wszystkie elementy członkowskie interfejsu mają powszechnej dostępności. Interfejs może również zawierać statyczne elementy członkowskie danych, funkcji, zdarzeń i właściwości i te statyczne elementy członkowskie muszą być zdefiniowane w interfejsie.  
  
 Interfejs definiuje, jak można zaimplementować klasy. Interfejs nie jest klasą i klasy tylko mogą implementować interfejsów. Po klasie definiuje funkcję zadeklarowany w interfejsie, funkcja jest zaimplementowana nie zastąpiona. W związku z tym wyszukiwanie nazw nie ma członków interfejsu.  
  
 Klasy lub struktury, która jest pochodną interfejsu musi implementować wszystkich członków interfejsu. Podczas implementowania interfejsu *nazwa* musi także implementować interfejsów w `base_interface` listy.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Statyczny Konstruktor interfejsu](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)  
  
-   [Interfejsy ogólne (Visual C++)](../windows/generic-interfaces-visual-cpp.md)  
  
 Aby uzyskać informacje na inne typy CLR, zobacz [klas i struktur](../windows/classes-and-structs-cpp-component-extensions.md).  
  
 Można wykrywać w czasie kompilacji, jeśli typ interfejsu o `__is_interface_class(type)`. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 Środowisko projektowe pozwala na uzyskanie pomocy F1 w następujących słów kluczowych przez wyróżnianie słowo kluczowe (`interface class`, na przykład) i naciskając klawisz F1.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 **Uwagi**  
  
 (Brak żadnych uwag dla tej funkcji języka, które są stosowane do środowiska uruchomieniowego systemu Windows.)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 **Uwagi**  
  
 (Istnieją nie uwagi dla tej funkcji języka, które dotyczą tylko środowiska CLR.)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 W poniższym przykładzie kodu pokazano, jak interfejs można określić zachowanie funkcji zegara.  
  
```  
// mcppv2_interface_class.cpp  
// compile with: /clr  
using namespace System;  
  
public delegate void ClickEventHandler(int, double);  
  
// define interface with nested interface  
public interface class Interface_A {  
   void Function_1();  
  
   interface class Interface_Nested_A {  
      void Function_2();  
   };  
};  
  
// interface with a base interface  
public interface class Interface_B : Interface_A {  
   property int Property_Block;  
   event ClickEventHandler^ OnClick;     
   static void Function_3() { Console::WriteLine("in Function_3"); }  
};  
  
// implement nested interface  
public ref class MyClass : public Interface_A::Interface_Nested_A {  
public:  
   virtual void Function_2() { Console::WriteLine("in Function_2"); }  
};  
  
// implement interface and base interface  
public ref class MyClass2 : public Interface_B {  
private:  
   int MyInt;  
  
public:  
   // implement non-static function  
   virtual void Function_1() { Console::WriteLine("in Function_1"); }  
  
   // implement property  
   property int Property_Block {  
      virtual int get() { return MyInt; }  
      virtual void set(int value) { MyInt = value; }  
   }  
   // implement event  
   virtual event ClickEventHandler^ OnClick;  
  
   void FireEvents() {  
      OnClick(7, 3.14159);  
   }  
};  
  
// class that defines method called when event occurs  
ref class EventReceiver {  
public:  
   void OnMyClick(int i, double d) {  
      Console::WriteLine("OnClick: {0}, {1}", i, d);  
   }  
};  
  
int main() {  
   // call static function in an interface  
   Interface_B::Function_3();  
  
   // instantiate class that implements nested interface  
   MyClass ^ x = gcnew MyClass;  
   x->Function_2();  
  
   // instantiate class that implements interface with base interface  
   MyClass2 ^ y = gcnew MyClass2;  
   y->Function_1();  
   y->Property_Block = 8;  
   Console::WriteLine(y->Property_Block);  
  
   EventReceiver^ MyEventReceiver = gcnew EventReceiver();  
  
   // hook handler to event  
   y->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);  
  
   // invoke events  
   y->FireEvents();  
  
   // unhook handler to event  
   y->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);  
  
   // call implemented function via interface handle  
   Interface_A^ hi = gcnew MyClass2();  
   hi->Function_1();  
}  
```  
  
 **Output**  
  
```Output  
in Function_3  
  
in Function_2  
  
in Function_1  
  
8  
  
OnClick: 7, 3.14159  
  
in Function_1  
```  
  
 **Przykład**  
  
 Poniższy przykładowy kod przedstawia dwa sposoby implementacji funkcji o tej samej sygnaturze zadeklarowany w wielu interfejsach i gdzie te interfejsy są używane przez klasę.  
  
```  
// mcppv2_interface_class_2.cpp  
// compile with: /clr /c  
interface class I {  
   void Test();  
   void Test2();  
};  
  
interface class J : I {  
   void Test();  
   void Test2();  
};  
  
ref struct R : I, J {  
   // satisfies the requirement to implement Test in both interfaces  
   virtual void Test() {}  
  
   // implement both interface functions with explicit overrides  
   virtual void A() = I::Test2 {}  
   virtual void B() = J::Test2 {}  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)