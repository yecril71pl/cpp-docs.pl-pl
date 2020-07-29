---
title: Interfejsy ogólne (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generic interfaces
- interfaces, generic [C++}
ms.assetid: f3da788a-ba83-4db7-9dcf-9b95a8fb9d1a
ms.openlocfilehash: f5a74eaafa7ff348079ec367a7c2318f86081f15
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218029"
---
# <a name="generic-interfaces-ccli"></a>Interfejsy ogólne (C++/CLI)

Ograniczenia, które są stosowane do parametrów typu dla klas są takie same jak te, które są stosowane do parametrów typu w interfejsach (zobacz [klasy ogólne (C++/CLI)](generic-classes-cpp-cli.md)).

Reguły, które kontrolują przeciążanie funkcji są takie same dla funkcji w klasach ogólnych lub ogólnych interfejsach.

Jawne implementacje elementu członkowskiego interfejsu działają z skonstruowanymi typami interfejsów w taki sam sposób jak w przypadku prostych typów interfejsów (Zobacz poniższe przykłady).

Aby uzyskać więcej informacji na temat interfejsów, zobacz [Klasa interfejsu](interface-class-cpp-component-extensions.md).

## <a name="syntax"></a>Składnia

```cpp
[attributes] generic <class-key type-parameter-identifier[, ...]>
[type-parameter-constraints-clauses][accesibility-modifiers] interface class identifier [: base-list] {   interface-body} [declarators] ;
```

## <a name="remarks"></a>Uwagi

*Attributes*<br/>
Obowiązkowe Dodatkowe informacje deklaratywne. Aby uzyskać więcej informacji na temat atrybutów i klas atrybutów, zobacz **atrybuty**.

*klucz klasy*<br/>
**`class`** oraz**`typename`**

*identyfikatory parametrów typu*<br/>
Lista identyfikatorów rozdzielonych przecinkami.

*ograniczenia parametrów typu-Parameter-klauzule*<br/>
Przyjmuje formularz określony w [ograniczeniach dla parametrów typu ogólnego (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)

*ułatwienia dostępu — Modyfikatory*<br/>
Obowiązkowe Modyfikatory dostępności (np. **publiczne, prywatne**).

*identyfikatora*<br/>
Nazwa interfejsu.

*Lista podstawowa*<br/>
Obowiązkowe Lista zawierająca jeden lub więcej jawnych interfejsów podstawowych oddzielonych przecinkami.

*Interfejs — treść*<br/>
Deklaracje elementów członkowskich interfejsu.

*Deklaratory*<br/>
Obowiązkowe Deklaracje zmiennych na podstawie tego typu.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób deklarowania i tworzenia wystąpienia interfejsu ogólnego. W tym przykładzie ogólny interfejs `IList<ItemType>` jest zadeklarowany. Są one następnie zaimplementowane przez dwie klasy ogólne `List1<ItemType>` i `List2<ItemType>` , z różnymi implementacjami.

```cpp
// generic_interface.cpp
// compile with: /clr
using namespace System;

// An exception to be thrown by the List when
// attempting to access elements beyond the
// end of the list.
ref class ElementNotFoundException : Exception {};

// A generic List interface
generic <typename ItemType>
public interface class IList {
   ItemType MoveFirst();
   bool Add(ItemType item);
   bool AtEnd();
   ItemType Current();
   void MoveNext();
};

// A linked list implementation of IList
generic <typename ItemType>
public ref class List1 : public IList<ItemType> {
   ref class Node {
      ItemType m_item;

   public:
      ItemType get_Item() { return m_item; };
      void set_Item(ItemType value) { m_item = value; };

      Node^ next;

      Node(ItemType item) {
         m_item = item;
         next = nullptr;
      }
   };

   Node^ first;
   Node^ last;
   Node^ current;

   public:
   List1() {
      first = nullptr;
      last = first;
      current = first;
   }

   virtual ItemType MoveFirst() {
      current = first;
      if (first != nullptr)
        return first->get_Item();
      else
         return ItemType();
   }

   virtual bool Add(ItemType item) {
      if (last != nullptr) {
         last->next = gcnew Node(item);
         last = last->next;
      }
      else {
         first = gcnew Node(item);
         last = first;
         current = first;
      }
      return true;
   }

   virtual bool AtEnd() {
      if (current == nullptr )
        return true;
      else
        return false;
   }

   virtual ItemType Current() {
       if (current != nullptr)
         return current->get_Item();
       else
         throw gcnew ElementNotFoundException();
   }

   virtual void MoveNext() {
      if (current != nullptr)
       current = current->next;
      else
        throw gcnew ElementNotFoundException();
   }
};

// An array implementation of IList
generic <typename ItemType>
ref class List2 : public IList<ItemType> {
   array<ItemType>^ item_array;
   int count;
   int current;

   public:

   List2() {
      // not yet possible to declare an
      // array of a generic type parameter
      item_array = gcnew array<ItemType>(256);
      count = current = 0;
   }

   virtual ItemType MoveFirst() {
      current = 0;
      return item_array[0];
   }

   virtual bool Add(ItemType item) {
      if (count < 256)
         item_array[count++] = item;
      else
        return false;
      return true;
   }

   virtual bool AtEnd() {
      if (current >= count)
        return true;
      else
        return false;
   }

   virtual ItemType Current() {
      if (current < count)
        return item_array[current];
      else
        throw gcnew ElementNotFoundException();
   }

   virtual void MoveNext() {
      if (current < count)
         ++current;
      else
         throw gcnew ElementNotFoundException();
   }
};

// Add elements to the list and display them.
generic <typename ItemType>
void AddStringsAndDisplay(IList<ItemType>^ list, ItemType item1, ItemType item2) {
   list->Add(item1);
   list->Add(item2);
   for (list->MoveFirst(); ! list->AtEnd(); list->MoveNext())
   Console::WriteLine(list->Current());
}

int main() {
   // Instantiate both types of list.

   List1<String^>^ list1 = gcnew List1<String^>();
   List2<String^>^ list2 = gcnew List2<String^>();

   // Use the linked list implementation of IList.
   AddStringsAndDisplay<String^>(list1, "Linked List", "List1");

   // Use the array implementation of the IList.
   AddStringsAndDisplay<String^>(list2, "Array List", "List2");
}
```

```Output
Linked List
List1
Array List
List2
```

## <a name="example"></a>Przykład

Ten przykład deklaruje ogólny interfejs, `IMyGenIface` i dwa interfejsy inne niż ogólne, `IMySpecializedInt` i `ImySpecializedString` , które są specjalizacją `IMyGenIface` . Dwa wyspecjalizowane interfejsy są następnie implementowane przez dwie klasy `MyIntClass` i `MyStringClass` . W przykładzie przedstawiono sposób specjalizacji interfejsów ogólnych, tworzenia wystąpienia ogólnych i nieogólnych interfejsów oraz wywoływania jawnie zaimplementowanych elementów członkowskich w interfejsach.

```cpp
// generic_interface2.cpp
// compile with: /clr
// Specializing and implementing generic interfaces.
using namespace System;

generic <class ItemType>
public interface class IMyGenIface {
   void Initialize(ItemType f);
};

public interface class IMySpecializedInt: public IMyGenIface<int> {
   void Display();
};

public interface class IMySpecializedString: public IMyGenIface<String^> {
   void Display();
};

public ref class MyIntClass: public IMySpecializedInt {
   int myField;

public:
   virtual void Initialize(int f) {
      myField = f;
   }

   virtual void Display() {
      Console::WriteLine("The integer field contains: {0}", myField);
   }
};

public ref struct MyStringClass: IMySpecializedString {
   String^ myField;

public:
   virtual void Initialize(String^ f) {
      myField = f;
    }

   virtual void Display() {
      Console::WriteLine("The String field contains: {0}", myField);
   }
};

int main() {
   // Instantiate the generic interface.
   IMyGenIface<int>^ myIntObj = gcnew MyIntClass();

   // Instantiate the specialized interface "IMySpecializedInt."
   IMySpecializedInt^ mySpIntObj = (IMySpecializedInt^) myIntObj;

   // Instantiate the generic interface.
   IMyGenIface<String^>^ myStringObj = gcnew MyStringClass();

   // Instantiate the specialized interface "IMySpecializedString."
   IMySpecializedString^ mySpStringObj =
            (IMySpecializedString^) myStringObj;

   // Call the explicitly implemented interface members.
   myIntObj->Initialize(1234);
   mySpIntObj->Display();

   myStringObj->Initialize("My string");
   mySpStringObj->Display();
}
```

```Output
The integer field contains: 1234
The String field contains: My string
```

## <a name="see-also"></a>Zobacz także

[Typy ogólne](generics-cpp-component-extensions.md)
