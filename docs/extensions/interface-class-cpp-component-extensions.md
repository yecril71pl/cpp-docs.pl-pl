---
title: Klasa interfejsu (C + +/ CLI i C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- interface_CPP
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
ms.openlocfilehash: 60e8965e3ef2538554d8c664b35bd0849bd5e69e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035857"
---
# <a name="interface-class--ccli-and-ccx"></a>Klasa interfejsu (C + +/ CLI i C + +/ CX)

Deklaruje interfejsu.  Informacje na temat interfejsy macierzyste można zobaczyć [__interface](../cpp/interface.md).

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="syntax"></a>Składnia

```cpp
interface_access
interface class
name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};
```

### <a name="parameters"></a>Parametry

*interface_access*<br/>
Dostępność interfejs spoza zestawu.  Możliwe wartości to **publicznych** i **prywatnej**.  **prywatne** jest ustawieniem domyślnym. Zagnieżdżone interfejsy nie mogą mieć *interface_access* specyfikator.

*nazwa*<br/>
Nazwa interfejsu.

*inherit_access*<br/>
Dostępność *base_interface*.  Jedyna dozwolona w ułatwienia dostępu przypadku interfejs podstawowy **publicznych** (ustawienie domyślne).

*base_interface*<br/>
(Opcjonalnie) Podstawowy interfejs dla interfejsu *nazwa*.

### <a name="remarks"></a>Uwagi

**Struktura interfejsu** jest odpowiednikiem **interfejsu klasy**.

Interfejs może zawierać deklaracje funkcji, właściwości i zdarzenia.  Wszyscy członkowie interfejsu mają powszechnej dostępności. Interfejs może również zawierać statycznych składowych danych, funkcje, zdarzenia i właściwości, a te statyczne elementy członkowskie muszą być zdefiniowane w interfejsie.

Interfejs definiuje, jak można zaimplementować klasę. Interfejs nie jest klasą i klasy może zawierać implementację tylko interfejsów. Gdy klasa definiuje funkcja zadeklarowana w interfejsie, że funkcja jest zaimplementowana, nie zostanie zastąpiona. W związku z tym wyszukiwanie nazw nie ma składowych interfejsu.

Klasa lub struktura, która pochodzi z interfejsu muszą implementować wszystkie elementy członkowskie interfejsu. Podczas implementowania interfejsu *nazwa* musi także implementować interfejsy w `base_interface` listy.

Aby uzyskać więcej informacji, zobacz:

- [Statyczny Konstruktor interfejsu](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)

- [Interfejsy ogólne (C + +/ CLI)](generic-interfaces-visual-cpp.md)

Aby uzyskać informacji o innych typach CLR, zobacz [klas i struktur](classes-and-structs-cpp-component-extensions.md).

Można wykrywać w czasie kompilacji, jeśli typ jest interfejsem z `__is_interface_class(type)`. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](compiler-support-for-type-traits-cpp-component-extensions.md).

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

## <a name="see-also"></a>Zobacz także

[Component Extensions dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)