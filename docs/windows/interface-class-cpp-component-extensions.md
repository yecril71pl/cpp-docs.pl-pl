---
title: Interface class (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- interface_CPP
dev_langs:
- C++
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 775fbe39edc9478b1fce3afb39ee2bf1f6d5ed36
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714314"
---
# <a name="interface-class--c-component-extensions"></a>interface class (C++ Component Extensions)

Deklaruje interfejsu.  Informacje na temat interfejsy macierzyste można zobaczyć [__interface](../cpp/interface.md).

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="syntax"></a>Składnia

```cpp
interface_access
interface class
 name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};
```

### <a name="parameters"></a>Parametry

*interface_access*  
Dostępność interfejs spoza zestawu.  Możliwe wartości to **publicznych** i **prywatnej**.  **prywatne** jest ustawieniem domyślnym. Zagnieżdżone interfejsy nie mogą mieć *interface_access* specyfikator.

*Nazwa*  
Nazwa interfejsu.

*inherit_access*  
Dostępność *base_interface*.  Jedyna dozwolona w ułatwienia dostępu przypadku interfejs podstawowy **publicznych** (ustawienie domyślne).

*base_interface*  
(Opcjonalnie) Podstawowy interfejs dla interfejsu *nazwa*.

### <a name="remarks"></a>Uwagi

**Struktura interfejsu** jest odpowiednikiem **interfejsu klasy**.

Interfejs może zawierać deklaracje funkcji, właściwości i zdarzenia.  Wszyscy członkowie interfejsu mają powszechnej dostępności. Interfejs może również zawierać statycznych składowych danych, funkcje, zdarzenia i właściwości, a te statyczne elementy członkowskie muszą być zdefiniowane w interfejsie.

Interfejs definiuje, jak można zaimplementować klasę. Interfejs nie jest klasą i klasy może zawierać implementację tylko interfejsów. Gdy klasa definiuje funkcja zadeklarowana w interfejsie, że funkcja jest zaimplementowana, nie zostanie zastąpiona. W związku z tym wyszukiwanie nazw nie ma składowych interfejsu.

Klasa lub struktura, która pochodzi z interfejsu muszą implementować wszystkie elementy członkowskie interfejsu. Podczas implementowania interfejsu *nazwa* musi także implementować interfejsy w `base_interface` listy.

Aby uzyskać więcej informacji, zobacz:

- [Statyczny Konstruktor interfejsu](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)

- [Interfejsy ogólne (Visual C++)](../windows/generic-interfaces-visual-cpp.md)

Aby uzyskać informacji o innych typach CLR, zobacz [klas i struktur](../windows/classes-and-structs-cpp-component-extensions.md).

Można wykrywać w czasie kompilacji, jeśli typ jest interfejsem z `__is_interface_class(type)`. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

W środowisku deweloperskim, możesz uzyskać Pomoc F1 na tych słów kluczowych, wyróżniając słowo kluczowe (`interface class`, na przykład) i naciskając klawisz F1.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="remarks"></a>Uwagi

(Nie ma żadnych uwag dla tej funkcji języka, które dotyczą tylko środowiska uruchomieniowego Windows).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="remarks"></a>Uwagi

(Nie ma żadnych uwag dla tej funkcji języka, które dotyczą tylko środowiska uruchomieniowego języka wspólnego).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład kodu pokazuje, jak zdefiniować interfejs zachowanie funkcji zegara.

```cpp
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

```Output
in Function_3

in Function_2

in Function_1

8

OnClick: 7, 3.14159

in Function_1
```

Poniższy przykładowy kod przedstawia dwa sposoby implementacji funkcji o tej samej sygnaturze, zadeklarowany w wielu interfejsach i której te interfejsy są używane przez klasę.

```cpp
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