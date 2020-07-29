---
title: klasa interfejsu  (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- interface_CPP
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
ms.openlocfilehash: e7847f71502354189e874d505414b4a45b74ab45
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228703"
---
# <a name="interface-class--ccli-and-ccx"></a>klasa interfejsu  (C++/CLI i C++/CX)

Deklaruje interfejs.  Aby uzyskać informacje na temat natywnych interfejsów, zobacz [__interface](../cpp/interface.md).

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="syntax"></a>Składnia

```cpp
interface_access
interface class
name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};
```

### <a name="parameters"></a>Parametry

*interface_access*<br/>
Dostępność interfejsu poza zestawem.  Możliwe wartości to **`public`** i **`private`** .  **`private`** jest wartością domyślną. Interfejsy zagnieżdżone nie mogą mieć specyfikatora *interface_access* .

*Nazwij*<br/>
Nazwa interfejsu.

*inherit_access*<br/>
Dostępność *base_interface*.  Jedyna dozwolona dostępność dla interfejsu podstawowego to **`public`** (domyślnie).

*base_interface*<br/>
Obowiązkowe Interfejs podstawowy dla *nazwy*interfejsu.

### <a name="remarks"></a>Uwagi

**Struktura interfejsu** jest równoważna z **klasą interfejsu**.

Interfejs może zawierać deklaracje dla funkcji, zdarzeń i właściwości.  Wszyscy członkowie interfejsu mają publiczny dostęp. Interfejs może również zawierać statyczne elementy członkowskie danych, funkcje, zdarzenia i właściwości, a te statyczne elementy członkowskie muszą być zdefiniowane w interfejsie.

Interfejs definiuje, jak można zaimplementować klasę. Interfejs nie jest klasą, a klasy mogą implementować tylko interfejsy. Gdy klasa definiuje funkcję zadeklarowaną w interfejsie, funkcja jest zaimplementowana, a nie przesłonięta. W związku z tym wyszukiwanie nazw nie zawiera elementów członkowskich interfejsu.

Klasa lub struktura, która dziedziczy z interfejsu, musi implementować wszystkie elementy członkowskie interfejsu. Podczas implementowania *nazwy* interfejsu należy również zaimplementować interfejsy na `base_interface` liście.

Aby uzyskać więcej informacji, zobacz:

- [Statyczny Konstruktor interfejsu](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)

- [Interfejsy ogólne (C++/CLI)](generic-interfaces-visual-cpp.md)

Aby uzyskać informacje na temat innych typów CLR, zobacz [klasy i struktury](classes-and-structs-cpp-component-extensions.md).

Możesz wykryć w czasie kompilacji, jeśli typ jest interfejsem z `__is_interface_class(type)` . Aby uzyskać więcej informacji, zobacz [Obsługa kompilatora dla cech typu](compiler-support-for-type-traits-cpp-component-extensions.md).

W środowisku programistycznym możesz uzyskać pomoc dotyczącą F1 dla tych słów kluczowych, zaznaczając słowo kluczowe ( **`interface class`** na przykład) i naciskając klawisz F1.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="remarks"></a>Uwagi

(Nie ma żadnych uwag dla tej funkcji języka, które mają zastosowanie tylko do środowisko wykonawcze systemu Windows).

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="remarks"></a>Uwagi

(Nie ma żadnych uwag dla tej funkcji języka, które mają zastosowanie tylko do środowiska uruchomieniowego języka wspólnego).

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład kodu demonstruje, jak interfejs może definiować zachowanie funkcji zegara.

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

Poniższy przykład kodu przedstawia dwa sposoby implementowania funkcji z tym samym podpisem zadeklarowanym w wielu interfejsach i miejsce, w którym te interfejsy są używane przez klasę.

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

[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)
