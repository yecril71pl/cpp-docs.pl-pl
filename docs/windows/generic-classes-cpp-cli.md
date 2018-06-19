---
title: Klasy ogólne (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], generic
- generic classes [C++], about generic classes
- data types [C++], generic
- generic classes
- generics [C++], declaring generic classes
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 07a5cb6abaca56901af26895b1304a9b7079ced9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881403"
---
# <a name="generic-classes-ccli"></a>Klasy ogólne [C++/CLI]
Klasy generycznej jest deklarowany przy użyciu następującej postaci:  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 W powyższej składni używane są następujące warunki:  
  
 `attributes` (opcjonalnie)  
 Dodatkowe informacje deklaratywne. Aby uzyskać więcej informacji na atrybuty i klasy atrybutów Zobacz atrybutów.  
  
 *klucz klasy*  
 Albo `class` lub `typename`  
  
 *Typ — parametr-identyfikatory*,  
 Rozdzielana przecinkami lista identyfikatorów określenie nazwy parametrów typu.  
  
 *klauzule ograniczenia*  
 Lista (nie przecinkami) **gdzie** klauzule określenie ograniczenia dla parametrów typu. Ma postać:  
  
 `where`  *Typ parametru identyfikatorów*`:`*listy ograniczenie*   `...`  
  
 *Lista ograniczeń*  
 *klasy lub interfejsu*[`,` *...* ]  
  
 *modyfikatory dostępności*  
 Modyfikatory dostępności dla klasy ogólnej. Dla środowiska uruchomieniowego systemu Windows jest dozwolony tylko modyfikator `private`. Dla środowiska CLR są dozwolone Modyfikatory `private` i `public`.  
  
 *Identyfikator*  
 Nazwa klasy generycznej dowolnego prawidłowego identyfikatora C++.  
  
 *Modyfikatory* (opcjonalnie)  
 Może zawierać Modyfikatory `sealed` i **abstrakcyjny**.  
  
 *Lista podstawowego*  
 Lista zawierająca jedną klasę podstawową i wszystkie zaimplementowane interfejsy, wszystkie rozdzielonych przecinkami.  
  
 *Treść klasy*  
 Treść klasy zawierające pola, funkcji Członkowskich itp.  
  
 *Deklaratory*  
 Deklaracje zmiennych tego typu. Na przykład: `^` *identyfikator*[`,` ...]  
  
 Klasy ogólne, takie jak te można zadeklarować (należy pamiętać, że słowo kluczowe **klasy** może być używana zamiast **typename**). W tym przykładzie `ItemType`, `KeyType` i `ValueType` są nieznane typy, które są określone w punkcie gdzie typu. `HashTable<int, int>` Typ skonstruowanego typu ogólnego `HashTable<KeyType, ValueType>`. Liczba różne typy utworzone mogą zostać utworzone na podstawie pojedynczego typu ogólnego. Typy utworzone utworzone na podstawie klasy ogólne są traktowane jak innego typu klasy referencyjnej.  
  
```  
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
  
 Oba typy wartości (takie jak typy albo wbudowane `int` lub `double`, lub typów wartości zdefiniowanej przez użytkownika) i typy referencyjne może być używany jako argumentu typu ogólnego. Składnia w ramach definicji ogólnego jest taka sama niezależnie od tego. Składnia nieznany typ jest traktowana tak, jakby to był typem referencyjnym. Środowisko uruchomieniowe jest jednak która sprawdza, czy typ faktycznie używany jest typ wartości i zastępuje odpowiednie wygenerowany kod dla bezpośredni dostęp do elementów członkowskich. Typy wartości używane jako argumenty typu ogólnego nie jest opakowany i tak problem występuje w przypadku spadek wydajności skojarzonego z boxing. Składnia wykorzystywana w treści ogólnych powinny być **T ^** i "**->**"zamiast elementu"**.**". Jakimkolwiek użyciem [ref new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md) dla typu parametru będzie odpowiednio interpretowany przez środowisko uruchomieniowe jako proste tworzenie typu wartości, jeśli argument Typ jest typem wartości.  
  
 Można również zadeklarować klasy ogólnej z [ograniczenia dotyczące parametrów typu ogólnego (C + +/ CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md) na typy, które mogą być używane dla parametru typu. W poniższym przykładzie dowolnego typu używany dla `ItemType` musi implementować `IItem` interfejsu. Podjęto próbę użycia `int`, na przykład, który nie implementuje `IItem`, zwróci błąd w czasie kompilacji, ponieważ argument typu nie spełnia warunków ograniczenia.  
  
```  
// generic_classes_2.cpp  
// compile with: /clr /c  
interface class IItem {};  
generic <class ItemType>  
where ItemType : IItem  
ref class Stack {};  
```  
  
 Klasy ogólne w tej samej przestrzeni nazw nie może zostać przeciążony przez zmianę tylko liczbę i typy parametrów typu. Jednak jeśli każda klasa znajduje się w innej przestrzeni nazw, ich może być przeciążony. Na przykład, należy wziąć pod uwagę następujące dwie klasy `MyClass` i `MyClass<ItemType>`, w przestrzeni nazw `A` i `B`. Następnie można przeciążać dwóch klas w przestrzeni nazw trzeci C:  
  
```  
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
  
 Klasa podstawowa i interfejsach podstawowych nie mogą mieć parametrów typu. Jednak klasy podstawowej może wymagać parametru typu jako argumentu, tak jak w przypadku następujących:  
  
```  
// generic_classes_4.cpp  
// compile with: /clr /c  
generic <typename ItemType>  
interface class IInterface {};  
  
generic <typename ItemType>  
ref class MyClass : IInterface<ItemType> {};  
```  
  
 Konstruktory i destruktory są wykonywane raz dla każdego wystąpienia obiektu (w zwykły sposób); Konstruktory statyczne są wykonywane raz dla każdego typu skonstruowane.  
  
## <a name="fields-in-generic-classes"></a>Pola klasy ogólne  
 W tej sekcji przedstawiono użycie wystąpienia oraz pól statycznych w klasach ogólnych.  
  
### <a name="instance-variables"></a>Zmienne wystąpienia  
 Zmienne wystąpienia klasy generycznej może mieć typów i inicjatory zmiennych, które obejmują wszystkie parametry typu klasy otaczającej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie trzy różne wystąpienia klasy generycznej MyClass\<ItemType >, są tworzone za pomocą odpowiedniego typu argumentów (`int`, **podwójne**, i **ciąg**).  
  
```  
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
 Przy tworzeniu nowego typu ogólnego są tworzone nowe wystąpienia wszystkie zmienne statyczne i wszelkie Konstruktor statyczny dla tego typu jest wykonywana.  
  
 Zmienne statyczne można używać parametrów typu klasy otaczającej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, za pomocą pola statyczne i konstruktora statycznego w klasie ogólnej.  
  
```  
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
  
## <a name="methods-in-generic-classes"></a>Metod w klasach ogólnych  
 Metod w klasach ogólnych może być rodzajowy. metody ogólne nie zostanie niejawnie sparametryzowanych przez parametr typu klasy.  
  
 Mają zastosowanie następujące reguły specjalne metod w klasach ogólnych:  
  
-   Metod w klasach ogólnych można używać parametrów typu jako parametry, zwracane typy lub zmiennych lokalnych.  
  
-   Metod w klasach ogólnych służy open lub closed typy utworzone jako parametry, zwracane typy lub zmiennych lokalnych.  
  
### <a name="non-generic-methods-in-generic-classes"></a>Nieogólnego metod w klasach ogólnych  
 Metod w klasach ogólnych, które nie mają typu dodatkowych parametrów są zwykle nazywane nierodzajową chociaż są one niejawnie parametry funkcjom otaczającej klasy ogólnej.  
  
 Podpis metody nieogólnego może zawierać co najmniej jeden parametr typu klasy otaczającej, bezpośrednio lub skonstruowanego typu otwartego. Na przykład:  
  
 `void MyMethod(MyClass<ItemType> x) {}`  
  
 Treść tych metod można także użyć tych parametrów typu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje metodę nierodzajową `ProtectData`, wewnątrz klasy ogólnej `MyClass<ItemType>`. Metoda używa parametru typu klasy `ItemType` w jego sygnatura w skonstruowanego typu otwartego.  
  
```  
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
  
## <a name="generic-methods-in-generic-classes"></a>Metody rodzajowe w klasach ogólnych  
 Można zadeklarować metody rodzajowe w klasach ogólnych i nierodzajową. Na przykład:  
  
## <a name="example"></a>Przykład  
  
```  
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
  
 Metoda nieogólnego jest nadal rodzajowa w tym sensie, że jest ona sparametryzowana przez parametr typu klasy, ale go nie ma typu dodatkowych parametrów.  
  
 Wszystkie typy metod w klasach ogólnych mogą być ogólne, takie jak statyczne, wystąpienia i metodach wirtualnych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano deklarowanie i przy użyciu metody rodzajowe w klasach ogólnych:  
  
```  
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
  
## <a name="using-nested-types-in-generic-classes"></a>Przy użyciu typów zagnieżdżonych klas ogólnych  
 Podobnie jak w przypadku zwykłej klas mogą zadeklarować innych typów wewnątrz klasy ogólnej. Deklaracja zagnieżdżonej klasy jest niejawnie parametry funkcjom parametrów typu w deklaracji klasy zewnętrzne. W związku z tym różne zagnieżdżona klasa jest zdefiniowana dla każdego skonstruowanego typu zewnętrznego. Na przykład w deklaracji  
  
```  
// generic_classes_5.cpp  
// compile with: /clr /c  
generic <typename ItemType>  
ref struct Outer {  
   ref class Inner {};  
};  
```  
  
 Typ zewnętrzne\<int >:: wewnętrzny nie jest taka sama, jak typ zewnętrzne\<podwójne >:: wewnętrzny.  
  
 Podobnie jak w przypadku metody rodzajowe w klasach ogólnych, typ dodatkowe parametry mogą być definiowane dla typu zagnieżdżonego. Jeśli używasz tej samej nazwy parametrów typu w klasie wewnętrznych i zewnętrznych, parametru typu wewnętrzny spowoduje ukrycie parametr typu zewnętrznego.  
  
```  
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
  
 Ponieważ nie można odwoływać się do parametru typu zewnętrznego, kompilator powoduje wygenerowanie ostrzeżenia w takiej sytuacji.  
  
 Podczas skonstruowane zagnieżdżone typy ogólne są nazywane, parametr typu dla typu zewnętrznego nie jest uwzględniony na liście parametrów typu dla typu wewnętrznej, mimo że wewnętrzny typu jest niejawnie sparametryzowana przez parametr typu zewnętrznego. W przypadku powyższych nazwę typu skonstruowane byłoby zewnętrzne\<int >:: wewnętrzny\<ciągu >.  
  
 W poniższym przykładzie pokazano tworzenie i odczytywanie listy połączonej przy użyciu typów zagnieżdżonych klas ogólnych.  
  
## <a name="example"></a>Przykład  
  
```  
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
  
## <a name="properties-events-indexers-and-operators-in-generic-classes"></a>Właściwości, zdarzenia, indeksatorów i operatory w klasach ogólnych  
  
-   Właściwości, zdarzenia, indeksatorów i operatory można używać parametrów typu klasy otaczającej ogólnego jako wartości zwracane, parametry lub zmienne lokalne, takie jak czas `ItemType` jest parametrem typu klasy:  
  
    ```  
    public ItemType MyProperty {}  
    ```  
  
-   Właściwości, zdarzenia, indeksatorów i operatory nie może się być sparametryzowana.  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia deklaracje właściwości wystąpienia w klasie ogólnej.  
  
```  
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
  
## <a name="example"></a>Przykład  
 W kolejnym przykładzie pokazano klasy ogólnej ze zdarzeniem.  
  
```  
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
  
## <a name="generic-structs"></a>Struktury ogólne  
 Reguły deklarowania i używanie struktur ogólne są takie same jak dla klas ogólny, z wyjątkiem różnice zanotowanym w w dokumentacja języka Visual C++.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje to struktura generyczna `MyGenStruct`, z jednym polem `myField`i przypisuje wartości różnych typów (`int`, **podwójne**, **String ^**) do tego pola.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](../windows/generics-cpp-component-extensions.md)