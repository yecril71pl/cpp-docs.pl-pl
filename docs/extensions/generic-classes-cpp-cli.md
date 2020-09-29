---
title: Klasy ogólne [C++/CLI]
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], generic
- generic classes [C++], about generic classes
- data types [C++], generic
- generic classes
- generics [C++], declaring generic classes
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
ms.openlocfilehash: fd287d8e9fe08ccd42436569eafee3f6935700e2
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414129"
---
# <a name="generic-classes-ccli"></a>Klasy ogólne [C++/CLI]

Klasa generyczna jest zadeklarowana przy użyciu następującej postaci:

## <a name="syntax"></a>Składnia

```cpp
[attributes]
generic <class-key type-parameter-identifier(s)>
[constraint-clauses]
[accessibility-modifiers] ref class identifier  [modifiers]
[: base-list]
{
class-body
} [declarators] [;]
```

## <a name="remarks"></a>Uwagi

W powyższej składni są używane następujące terminy:

*Attributes*<br/>
Obowiązkowe Dodatkowe informacje deklaratywne. Aby uzyskać więcej informacji na temat atrybutów i klas atrybutów, zobacz atrybuty.

*klucz klasy*<br/>
Albo **`class`****`typename`**

identyfikatory *parametrów typu*, rozdzielana przecinkami lista identyfikatorów określających nazwy parametrów typu.

*Klauzula CONSTRAINT — klauzule*<br/>
Lista (nie rozdzielona przecinkami) klauzul **WHERE** , które określają ograniczenia dotyczące parametrów typu. Przyjmuje formę:

> **gdzie** *Typ-parametru-Identifier* **:** *Constraint-list*  **...**

*Lista ograniczeń*<br/>
*Klasa lub interfejs*[ `,` *...*]

*ułatwienia dostępu — Modyfikatory*<br/>
Modyfikatory dostępności dla klasy generycznej. Dla środowisko wykonawcze systemu Windows jedynym dozwolonym modyfikatorem jest **`private`** . Dla środowiska uruchomieniowego języka wspólnego dozwolone Modyfikatory to **`private`** i **`public`** .

*identyfikatora*<br/>
Nazwa klasy generycznej, dowolny prawidłowy identyfikator C++.

*Modyfikatory*<br/>
Obowiązkowe Dozwolone Modyfikatory to **Sealed** i **abstract**.

*Lista podstawowa*<br/>
Lista zawierająca jedną klasę bazową i wszystkie zaimplementowane interfejsy, które są rozdzielone przecinkami.

*Treść klasy*<br/>
Treść klasy, zawierająca pola, funkcje członkowskie itd.

*Deklaratory*<br/>
Deklaracje wszelkich zmiennych tego typu. Na przykład: `^` *Identyfikator*[ `,` ...]

Można zadeklarować klasy ogólne, takie jak te (należy zauważyć, że słowo kluczowe **`class`** może być używane zamiast **`typename`** ). W tym przykładzie, `ItemType` `KeyType` i `ValueType` są nieznane typy, które są określone w punkcie, w którym typ. `HashTable<int, int>` jest typem konstruowanym typu ogólnego `HashTable<KeyType, ValueType>` . Wiele różnych skonstruowanych typów można utworzyć z jednego typu ogólnego. Skonstruowane typy zbudowane z klas ogólnych są traktowane jak każdy inny typ klasy referencyjnej.

```cpp
// generic_classes_1.cpp
// compile with: /clr
using namespace System;
generic <typename ItemType>
ref struct Stack {
   // ItemType may be used as a type here
   void Add(ItemType item) {}
};

generic <typename KeyType, typename ValueType>
ref class HashTable {};

// The keyword class may be used instead of typename:
generic <class ListItem>
ref class List {};

int main() {
   HashTable<int, Decimal>^ g1 = gcnew HashTable<int, Decimal>();
}
```

Oba typy wartości (wbudowane typy, takie jak **`int`** lub **`double`** , lub typy wartości zdefiniowane przez użytkownika) i typy referencyjne mogą być używane jako argument typu ogólnego. Składnia w definicji ogólnej jest taka sama niezależnie od. Syntaktycznie nieznany typ jest traktowany tak, jakby był typem referencyjnym. Jednak środowisko uruchomieniowe jest w stanie określić, że jeśli typ rzeczywiście używany jest typem wartości i zastępuje odpowiedni wygenerowany kod dla bezpośredniego dostępu do elementów członkowskich. Typy wartości używane jako argumenty typu generycznego nie są opakowane i dlatego nie pogorszenia wydajności związanej z opakowaniem. Składnia użyta w treści generycznej powinna być `T^` i `->` zamiast `.` . Wszelkie użycie [ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md) dla parametru typu będzie odpowiednio interpretowane przez środowisko uruchomieniowe jako proste tworzenie typu wartości, jeśli argument typu jest typem wartości.

Można również zadeklarować klasę generyczną z [ograniczeniami dotyczącymi parametrów typu ogólnego (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md) dla typów, które mogą być używane dla parametru typu. W poniższym przykładzie dowolny typ używany dla `ItemType` musi implementować `IItem` interfejs. Próba użycia **`int`** , na przykład, który nie implementuje programu `IItem` , spowoduje błąd czasu kompilacji, ponieważ argument typu nie spełnia ograniczenia.

```cpp
// generic_classes_2.cpp
// compile with: /clr /c
interface class IItem {};
generic <class ItemType>
where ItemType : IItem
ref class Stack {};
```

Klasy generyczne w tej samej przestrzeni nazw nie mogą być przeciążone przez zmianę liczby lub typów parametrów typu. Jeśli jednak każda klasa znajduje się w innej przestrzeni nazw, mogą one być przeciążone. Rozważmy na przykład następujące dwie klasy, `MyClass` a `MyClass<ItemType>` w przestrzeniach nazw `A` i `B` . Dwie klasy mogą następnie być przeciążone w trzecim obszarze nazw C:

```cpp
// generic_classes_3.cpp
// compile with: /clr /c
namespace A {
   ref class MyClass {};
}

namespace B {
   generic <typename ItemType>
   ref class MyClass2 { };
}

namespace C {
   using namespace A;
   using namespace B;

   ref class Test {
      static void F() {
         MyClass^ m1 = gcnew MyClass();   // OK
         MyClass2<int>^ m2 = gcnew MyClass2<int>();   // OK
      }
   };
}
```

Klasa bazowa i interfejsy podstawowe nie mogą być parametrami typu. Jednak Klasa bazowa może dotyczyć parametru typu jako argumentu, jak w następujących przypadkach:

```cpp
// generic_classes_4.cpp
// compile with: /clr /c
generic <typename ItemType>
interface class IInterface {};

generic <typename ItemType>
ref class MyClass : IInterface<ItemType> {};
```

Konstruktory i destruktory są wykonywane raz dla każdego wystąpienia obiektu (jak zwykle); Konstruktory statyczne są wykonywane raz dla każdego skompilowanego typu.

## <a name="fields-in-generic-classes"></a>Pola w klasach ogólnych

W tej sekcji pokazano, jak używać wystąpień i pól statycznych w klasach ogólnych.

### <a name="instance-variables"></a>Zmienne wystąpienia

Zmienne wystąpień klasy generycznej mogą mieć typy i inicjatory zmiennych, które zawierają parametry typu z otaczającej klasy.

## <a name="example-different-generic-classes"></a>Przykład: różne klasy ogólne

W poniższym przykładzie trzy różne wystąpienia klasy generycznej, MyClass \<ItemType> , są tworzone przy użyciu odpowiednich argumentów typu ( **`int`** , **`double`** i **String**).

```cpp
// generics_instance_fields1.cpp
// compile with: /clr
// Instance fields on generic classes
using namespace System;

generic <typename ItemType>
ref class MyClass {
// Field of the type ItemType:
public :
   ItemType field1;
   // Constructor using a parameter of the type ItemType:
   MyClass(ItemType p) {
   field1 = p;
   }
};

int main() {
   // Instantiate an instance with an integer field:
   MyClass<int>^ myObj1 = gcnew MyClass<int>(123);
   Console::WriteLine("Integer field = {0}", myObj1->field1);

   // Instantiate an instance with a double field:
   MyClass<double>^ myObj2 = gcnew MyClass<double>(1.23);
   Console::WriteLine("Double field = {0}", myObj2->field1);

   // Instantiate an instance with a String field:
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>("ABC");
   Console::WriteLine("String field = {0}", myObj3->field1);
   }
```

```Output
Integer field = 123
Double field = 1.23
String field = ABC
```

## <a name="static-variables"></a>Zmienne statyczne

W przypadku tworzenia nowego typu ogólnego tworzone są nowe wystąpienia wszelkich zmiennych statycznych, a każdy Konstruktor statyczny dla tego typu jest wykonywany.

Zmienne statyczne mogą używać wszelkich parametrów typu z klasy otaczającej.

## <a name="example-use-static-variables"></a>Przykład: Użyj zmiennych statycznych

Poniższy przykład demonstruje użycie pól statycznych i konstruktora statycznego w obrębie klasy generycznej.

```cpp
// generics_static2.cpp
// compile with: /clr
using namespace System;

interface class ILog {
   void Write(String^ s);
};

ref class DateTimeLog : ILog {
public:
   virtual void Write(String^ s) {
      Console::WriteLine( "{0}\t{1}", DateTime::Now, s);
   }
};

ref class PlainLog : ILog {
public:
   virtual void Write(String^ s) { Console::WriteLine(s); }
};

generic <typename LogType>
where LogType : ILog
ref class G {
   static LogType s_log;

public:
   G(){}
   void SetLog(LogType log) { s_log = log; }
   void F() { s_log->Write("Test1"); }
   static G() { Console::WriteLine("Static constructor called."); }
};

int main() {
   G<PlainLog^>^ g1 = gcnew G<PlainLog^>();
   g1->SetLog(gcnew PlainLog());
   g1->F();

   G<DateTimeLog^>^ g2 = gcnew G<DateTimeLog^>();
   g2->SetLog(gcnew DateTimeLog());

   // prints date
   // g2->F();
}
```

```Output
Static constructor called.
Static constructor called.
Static constructor called.
Test1
```

## <a name="methods-in-generic-classes"></a>Metody w klasach ogólnych

Metody w klasach ogólnych mogą być same ogólnymi; Metody inne niż ogólne będą niejawnie sparametryzowane przez parametr typu klasy.

Poniższe reguły specjalne dotyczą metod w klasach ogólnych:

- Metody w klasach ogólnych mogą używać parametrów typu jako parametrów, typów zwracanych lub zmiennych lokalnych.

- Metody w klasach generycznych mogą używać typów skonstruowanych lub zamkniętych, jako parametrów, typów zwracanych lub zmiennych lokalnych.

### <a name="non-generic-methods-in-generic-classes"></a>Metody nieogólne w klasach generycznych

Metody klasy generycznej, które nie mają dodatkowych parametrów typu, są zwykle określane jako nieogólne, chociaż są niejawnie sparametryzowane przez otaczającą klasę generyczną.

Sygnatura metody niegenerycznej może zawierać jeden lub więcej parametrów typu otaczającej klasy, bezpośrednio lub w otwartym typie skonstruowanym. Na przykład:

`void MyMethod(MyClass<ItemType> x) {}`

Treść tych metod może również używać tych parametrów typu.

## <a name="example-declare-non-generic-method"></a>Przykład: deklarowanie metody niegenerycznej

Poniższy przykład deklaruje metodę nierodzajową, `ProtectData` wewnątrz klasy generycznej `MyClass<ItemType>` . Metoda używa parametru typu klasy `ItemType` w jego podpisie w otwartym typie skonstruowanym.

```cpp
// generics_non_generic_methods1.cpp
// compile with: /clr
// Non-generic methods within a generic class.
using namespace System;

generic <typename ItemType>
ref class MyClass {
public:
   String^ name;
   ItemType data;

   MyClass(ItemType x) {
      data = x;
   }

   // Non-generic method using the type parameter:
   virtual void ProtectData(MyClass<ItemType>^ x) {
      data = x->data;
   }
};

// ItemType defined as String^
ref class MyMainClass: MyClass<String^> {
public:
   // Passing "123.00" to the constructor:
   MyMainClass(): MyClass<String^>("123.00") {
      name = "Jeff Smith";
   }

   virtual void ProtectData(MyClass<String^>^ x) override {
      x->data = String::Format("${0}**", x->data);
   }

   static void Main() {
      MyMainClass^ x1 = gcnew MyMainClass();

      x1->ProtectData(x1);
      Console::WriteLine("Name: {0}", x1->name);
      Console::WriteLine("Amount: {0}", x1->data);
   }
};

int main() {
   MyMainClass::Main();
}
```

```Output
Name: Jeff Smith
Amount: $123.00**
```

## <a name="generic-methods-in-generic-classes"></a>Metody ogólne w klasach ogólnych

Można zadeklarować metody generyczne zarówno w klasach ogólnych, jak i nierodzajowych. Na przykład:

## <a name="example-declare-generic-and-non-generic-methods"></a>Przykład: Zadeklaruj metody generyczne i inne niż ogólne

```cpp
// generics_method2.cpp
// compile with: /clr /c
generic <typename Type1>
ref class G {
public:
   // Generic method having a type parameter
   // from the class, Type1, and its own type
   // parameter, Type2
   generic <typename Type2>
   void Method1(Type1 t1, Type2 t2) { F(t1, t2); }

   // Non-generic method:
   // Can use the class type param, Type1, but not Type2.
   void Method2(Type1 t1) { F(t1, t1); }

   void F(Object^ o1, Object^ o2) {}
};
```

Metoda niegeneryczna nadal jest ogólna w sensie, że jest sparametryzowane przez parametr typu klasy, ale nie ma żadnych dodatkowych parametrów typu.

Wszystkie typy metod w klasach generycznych mogą być ogólne, w tym statyczne, wystąpienia i metody wirtualne.

## <a name="example-declare-and-use-generic-methods"></a>Przykład: deklarowanie metod ogólnych i korzystanie z nich

Poniższy przykład demonstruje deklarowanie i używanie metod ogólnych w klasach ogólnych:

```cpp
// generics_generic_method2.cpp
// compile with: /clr
using namespace System;
generic <class ItemType>
ref class MyClass {
public:
   // Declare a generic method member.
   generic <class Type1>
   String^ MyMethod(ItemType item, Type1 t) {
      return String::Concat(item->ToString(), t->ToString());
   }
};

int main() {
   // Create instances using different types.
   MyClass<int>^ myObj1 = gcnew MyClass<int>();
   MyClass<String^>^ myObj2 = gcnew MyClass<String^>();
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>();

   // Calling MyMethod using two integers.
   Console::WriteLine("MyMethod returned: {0}",
            myObj1->MyMethod<int>(1, 2));

   // Calling MyMethod using an integer and a string.
   Console::WriteLine("MyMethod returned: {0}",
            myObj2->MyMethod<int>("Hello #", 1));

   // Calling MyMethod using two strings.
   Console::WriteLine("MyMethod returned: {0}",
       myObj3->MyMethod<String^>("Hello ", "World!"));

   // generic methods can be called without specifying type arguments
   myObj1->MyMethod<int>(1, 2);
   myObj2->MyMethod<int>("Hello #", 1);
   myObj3->MyMethod<String^>("Hello ", "World!");
}
```

```Output
MyMethod returned: 12
MyMethod returned: Hello #1
MyMethod returned: Hello World!
```

## <a name="using-nested-types-in-generic-classes"></a>Używanie zagnieżdżonych typów w klasach ogólnych

Podobnie jak w przypadku zwykłych klas, można zadeklarować inne typy wewnątrz klasy generycznej. Deklaracja klasy zagnieżdżonej jest niejawnie sparametryzowana przez parametry typu deklaracji klasy zewnętrznej. W tym celu dla każdego skonstruowanego typu zewnętrznego jest definiowana odrębna Klasa zagnieżdżona. Na przykład, w deklaracji,

```cpp
// generic_classes_5.cpp
// compile with: /clr /c
generic <typename ItemType>
ref struct Outer {
   ref class Inner {};
};
```

Typ `Outer<int>::Inner` nie jest taki sam jak typ `Outer<double>::Inner` .

Podobnie jak w przypadku metod rodzajowych w klasach ogólnych, można zdefiniować dodatkowe parametry typu dla typu zagnieżdżonego. Jeśli używasz tych samych nazw parametrów typu w klasie wewnętrznej i zewnętrznej, parametr typu wewnętrznego spowoduje ukrycie zewnętrznego parametru typu.

```cpp
// generic_classes_6.cpp
// compile with: /clr /c
generic <typename ItemType>
ref class Outer {
   ItemType outer_item;   // refers to outer ItemType

   generic <typename ItemType>
   ref class Inner {
      ItemType inner_item;   // refers to Inner ItemType
   };
};
```

Ponieważ nie ma sposobu odwoływania się do parametru typu zewnętrznego, kompilator generuje ostrzeżenie w tej sytuacji.

W przypadku konstruowania zagnieżdżonych typów ogólnych, parametr typu dla typu zewnętrznego nie jest uwzględniony na liście parametrów typu dla typu wewnętrznego, chociaż typ wewnętrzny jest niejawnie sparametryzowane przez parametr typu zewnętrznego. W powyższym przypadku jest to nazwa konstruowanego typu `Outer<int>::Inner<string>` .

## <a name="example-build-and-read-linked-list"></a>Przykład: kompilowanie i odczytywanie połączonej listy

Poniższy przykład ilustruje Kompilowanie i odczytywanie połączonej listy przy użyciu zagnieżdżonych typów w klasach generycznych.

```cpp
// generics_linked_list.cpp
// compile with: /clr
using namespace System;
generic <class ItemType>
ref class LinkedList {
// The node class:
public:
   ref class Node {
   // The link field:
   public:
      Node^ next;
      // The data field:
      ItemType item;
   } ^first, ^current;
};

ref class ListBuilder {
public:
   void BuildIt(LinkedList<double>^ list) {
      /* Build the list */
      double m[5] = {0.1, 0.2, 0.3, 0.4, 0.5};
      Console::WriteLine("Building the list:");

      for (int n=0; n<=4; n++) {
         // Create a new node:
         list->current = gcnew LinkedList<double>::Node();

         // Assign a value to the data field:
         list->current->item = m[n];

         // Set the link field "next" to be the same as
         // the "first" field:
         list->current->next = list->first;

         // Redirect "first" to the new node:
         list->first = list->current;

         // Display node's data as it builds:
         Console::WriteLine(list->current->item);
      }
   }

   void ReadIt(LinkedList<double>^ list) {
      // Read the list
      // Make "first" the "current" link field:
      list->current = list->first;
      Console::WriteLine("Reading nodes:");

      // Read nodes until current == null:
      while (list->current != nullptr) {
         // Display the node's data field:
         Console::WriteLine(list->current->item);

         // Move to the next node:
         list->current = list->current->next;
      }
   }
};

int main() {
   // Create a list:
   LinkedList<double>^ aList = gcnew LinkedList<double>();

   // Initialize first node:
   aList->first = nullptr;

   // Instantiate the class, build, and read the list:
   ListBuilder^ myListBuilder = gcnew ListBuilder();
   myListBuilder->BuildIt(aList);
   myListBuilder->ReadIt(aList);
}
```

```Output
Building the list:
0.1
0.2
0.3
0.4
0.5
Reading nodes:
0.5
0.4
0.3
0.2
0.1
```

## <a name="properties-events-indexers-and-operators-in-generic-classes"></a>Właściwości, zdarzenia, indeksatory i operatory w klasach ogólnych

- Właściwości, zdarzenia, indeksatory i operatory mogą używać parametrów typu otaczającej klasy generycznej jako wartości zwracanych, parametrów lub zmiennych lokalnych, takich jak kiedy `ItemType` jest parametrem typu klasy:

    ```cpp
    public ItemType MyProperty {}
    ```

- Właściwości, zdarzenia, indeksatory i operatory nie mogą być sparametryzowane.

## <a name="example-declare-instance-property"></a>Przykład: Zadeklaruj Właściwość wystąpienia

Ten przykład przedstawia deklaracje właściwości instance w klasie generycznej.

```cpp
// generics_generic_properties1.cpp
// compile with: /clr
using namespace System;

generic <typename ItemType>
ref class MyClass {
private:
   property ItemType myField;

public:
   property ItemType MyProperty {
      ItemType get() {
         return myField;
      }
      void set(ItemType value) {
         myField = value;
      }
   }
};

int main() {
   MyClass<String^>^ c = gcnew MyClass<String^>();
   MyClass<int>^ c1 = gcnew MyClass<int>();

   c->MyProperty = "John";
   c1->MyProperty = 234;

   Console::Write("{0}, {1}", c->MyProperty, c1->MyProperty);
}
```

```Output
John, 234
```

## <a name="example-generic-class-with-event"></a>Przykład: Klasa ogólna ze zdarzeniem

W następnym przykładzie pokazano klasę generyczną ze zdarzeniem.

```cpp
// generics_generic_with_event.cpp
// compile with: /clr
// Declare a generic class with an event and
// invoke events.
using namespace System;

// declare delegates
generic <typename ItemType>
delegate void ClickEventHandler(ItemType);

// generic class that defines events
generic <typename ItemType>
ref class EventSource {
public:
   // declare the event OnClick
   event ClickEventHandler<ItemType>^ OnClick;
   void FireEvents(ItemType item) {
      // raises events
      OnClick(item);
   }
};

// generic class that defines methods that will called when
// event occurs
generic <typename ItemType>
ref class EventReceiver {
public:
   void OnMyClick(ItemType item) {
   Console::WriteLine("OnClick: {0}", item);
   }
};

int main() {
   EventSource<String^>^ MyEventSourceString =
                   gcnew EventSource<String^>();
   EventSource<int>^ MyEventSourceInt = gcnew EventSource<int>();
   EventReceiver<String^>^ MyEventReceiverString =
                   gcnew EventReceiver<String^>();
   EventReceiver<int>^ MyEventReceiverInt = gcnew EventReceiver<int>();

   // hook handler to event
   MyEventSourceString->OnClick += gcnew ClickEventHandler<String^>(
       MyEventReceiverString, &EventReceiver<String^>::OnMyClick);
   MyEventSourceInt->OnClick += gcnew ClickEventHandler<int>(
             MyEventReceiverInt, &EventReceiver<int>::OnMyClick);

   // invoke events
   MyEventSourceString->FireEvents("Hello");
   MyEventSourceInt->FireEvents(112);

   // unhook handler to event
   MyEventSourceString->OnClick -= gcnew ClickEventHandler<String^>(
        MyEventReceiverString, &EventReceiver<String^>::OnMyClick);
   MyEventSourceInt->OnClick -= gcnew ClickEventHandler<int>(
        MyEventReceiverInt, &EventReceiver<int>::OnMyClick);
}
```

## <a name="generic-structs"></a>Struktury generyczne

Reguły deklarowania i używania struktur generycznych są takie same jak dla klas ogólnych, z wyjątkiem różnic zanotowanych w dokumentacji języka Visual C++.

## <a name="example-declare-generic-struct"></a>Przykład: Zadeklaruj strukturę generyczną

Poniższy przykład deklaruje generyczną strukturę, `MyGenStruct` , z jednym polem, `myField` i przypisuje wartości różnych typów ( **`int`** , **`double`** , `String^` ) do tego pola.

```cpp
// generics_generic_struct1.cpp
// compile with: /clr
using namespace System;

generic <typename ItemType>
ref struct MyGenStruct {
public:
   ItemType myField;

   ItemType AssignValue(ItemType item) {
      myField = item;
      return myField;
   }
};

int main() {
   int myInt = 123;
   MyGenStruct<int>^ myIntObj = gcnew MyGenStruct<int>();
   myIntObj->AssignValue(myInt);
   Console::WriteLine("The field is assigned the integer value: {0}",
            myIntObj->myField);

   double myDouble = 0.123;
   MyGenStruct<double>^ myDoubleObj = gcnew MyGenStruct<double>();
   myDoubleObj->AssignValue(myDouble);
   Console::WriteLine("The field is assigned the double value: {0}",
            myDoubleObj->myField);

   String^ myString = "Hello Generics!";
   MyGenStruct<String^>^ myStringObj = gcnew MyGenStruct<String^>();
   myStringObj->AssignValue(myString);
   Console::WriteLine("The field is assigned the string: {0}",
            myStringObj->myField);
}
```

```Output
The field is assigned the integer value: 123
The field is assigned the double value: 0.123
The field is assigned the string: Hello Generics!
```

## <a name="see-also"></a>Zobacz także

[Typy ogólne](generics-cpp-component-extensions.md)
