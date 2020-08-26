---
title: stack — Klasa
ms.date: 11/04/2016
f1_keywords:
- stack/std::stack::container_type
- stack/std::stack::size_type
- stack/std::stack::value_type
- stack/std::stack::empty
- stack/std::stack::pop
- stack/std::stack::push
- stack/std::stack::size
- stack/std::stack::top
helpviewer_keywords:
- std::stack [C++], container_type
- std::stack [C++], size_type
- std::stack [C++], value_type
- std::stack [C++], empty
- std::stack [C++], pop
- std::stack [C++], push
- std::stack [C++], size
- std::stack [C++], top
ms.assetid: 02151c1e-eab0-41b8-be94-a839ead78ecf
ms.openlocfilehash: f1d44a4242542ac6856fd7208fe423c43ae79997
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844304"
---
# <a name="stack-class"></a>stack — Klasa

Klasa adaptera kontenerów szablonu, która zapewnia ograniczenie funkcjonalności ograniczającej dostęp do elementu, który ostatnio został dodany do pewnego bazowego typu kontenera. Klasa stosu jest używana, gdy ma być jasne, że tylko operacje stosu są wykonywane na kontenerze.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Container= deque <Type>>
class stack
```

### <a name="parameters"></a>Parametry

*Wprowadź*\
Typ danych elementu, który ma być przechowywany w stosie.

*Wbudowane*\
Typ źródłowego kontenera używany do implementowania stosu. Wartość domyślna to Klasa `deque` *\<Type>* .

## <a name="remarks"></a>Uwagi

Elementy klasy `Type` ustalone w pierwszym parametrze szablonu obiektu stosu są synonimem [value_type](#value_type) i muszą być zgodne z typem elementu w klasie bazowego kontenera `Container` określonym przez drugi parametr szablonu. `Type`Należy je przypisać, aby można było kopiować obiekty tego typu i przypisywać wartości do zmiennych tego typu.

Odpowiednie źródłowe klasy kontenerów dla stosu obejmują [deque](../standard-library/deque-class.md), [klasy list](../standard-library/list-class.md)i [klasy Vector](../standard-library/vector-class.md)albo dowolnego kontenera sekwencji obsługującego operacje `back` , `push_back` i `pop_back` . Bazowa Klasa kontenera jest hermetyzowana w ramach adaptera kontenerów, która uwidacznia tylko ograniczony zestaw funkcji Członkowskich kontenera sekwencji jako interfejs publiczny.

Obiekty stosu są równe porównywalnie, jeśli i tylko wtedy, gdy elementy klasy `Type` są porównywalne, i są mniejsze niż porównywalne, jeśli elementy klasy `Type` są mniejsze niż porównywalne.

- Klasa stosu obsługuje strukturę danych Last-in, First-Out (LIFO). Dobrym sposobem na zachowywać się to stos płyt. Elementy (płytki) mogą być wstawiane, badane lub usuwane tylko z góry stosu, który jest ostatnim elementem na końcu kontenera podstawowego. Ograniczenie dostępu do elementu Top jest przyczyną użycia klasy stosu.

- [Klasa Queue](../standard-library/queue-class.md) obsługuje strukturę danych First-In, First-Out (FIFO). Dobrym analogem na to, aby mieć na uwadze, osoby tworzące informację o poinformowaniu banku. Elementy (ludzie) mogą zostać dodane z tyłu wiersza i są usuwane z przodu wiersza. Można sprawdzić zarówno przód, jak i tyłu wiersza. Ograniczenie do uzyskiwania dostępu tylko do elementów przednich i z tyłu w ten sposób jest przyczyną użycia klasy Queue.

- [Klasa priority_queue](../standard-library/priority-queue-class.md) porządkuje swoje elementy, aby największy element zawsze znajduje się na górze. Obsługuje wstawianie elementu i inspekcję oraz usuwanie elementu Top. Dobrym analogicznym sposobem jest pogrupowanie osób, które są ułożone według wieku, wysokości lub innego kryterium.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|Nazwa|Opis|
|-|-|
|[stosu](#stack)|Tworzy element a `stack` , który jest pusty lub jest kopią podstawowego obiektu kontenera.|

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|-|-|
|[container_type](#container_type)|Typ, który dostarcza kontener podstawowy, który ma zostać dostosowany przez `stack` .|
|[size_type](#size_type)|Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w `stack` .|
|[value_type](#value_type)|Typ, który reprezentuje typ obiektu przechowywanego jako element w `stack` .|

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[puste](#empty)|Testuje, czy `stack` jest pusty.|
|[skakując](#pop)|Usuwa element z góry `stack` .|
|[push](#push)|Dodaje element w górnej części `stack` .|
|[zmienia](#size)|Zwraca liczbę elementów w `stack` .|
|[top (pierwsze)](#top)|Zwraca odwołanie do elementu w górnej części `stack` .|

## <a name="container_type"></a><a name="container_type"></a> container_type

Typ, który dostarcza kontener bazowy, który ma zostać dostosowany.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Container` . Wszystkie trzy klasy kontenerów sekwencji standardowej biblioteki C++ — Klasa Vector, Klasa list i Klasa domyślna deque — spełniają wymagania, które mają być używane jako kontener podstawowy dla obiektu stosu. Typy zdefiniowane przez użytkownika spełniające te wymagania mogą być również używane.

Aby uzyskać więcej informacji na temat `Container` , zobacz sekcję Uwagi w temacie [klasy stosu](../standard-library/stack-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [stosu:: Stack](#stack) na przykład sposobu deklarowania i używania `container_type` .

## <a name="empty"></a><a name="empty"></a> ciągiem

Testuje, czy stos jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli stos jest pusty; **`false`** Jeśli stos nie jest pusty.

### <a name="example"></a>Przykład

```cpp
// stack_empty.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   // Declares stacks with default deque base container
   stack <int> s1, s2;

   s1.push( 1 );

   if ( s1.empty( ) )
      cout << "The stack s1 is empty." << endl;
   else
      cout << "The stack s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The stack s2 is empty." << endl;
   else
      cout << "The stack s2 is not empty." << endl;
}
```

```Output
The stack s1 is not empty.
The stack s2 is empty.
```

## <a name="pop"></a><a name="pop"></a> skakując

Usuwa element z góry stosu.

```cpp
void pop();
```

### <a name="remarks"></a>Uwagi

Stos nie może być pusty, aby można było zastosować funkcję członkowską. Górna część stosu jest pozycją zajmowaną przez ostatnio dodany element i jest ostatnim elementem na końcu kontenera.

### <a name="example"></a>Przykład

```cpp
// stack_pop.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1, s2;

   s1.push( 10 );
   s1.push( 20 );
   s1.push( 30 );

   stack <int>::size_type i;
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   i = s1.top( );
   cout << "The element at the top of the stack is "
        << i << "." << endl;

   s1.pop( );

   i = s1.size( );
   cout << "After a pop, the stack length is "
        << i << "." << endl;

   i = s1.top( );
   cout << "After a pop, the element at the top of the stack is "
        << i << "." << endl;
}
```

```Output
The stack length is 3.
The element at the top of the stack is 30.
After a pop, the stack length is 2.
After a pop, the element at the top of the stack is 20.
```

## <a name="push"></a><a name="push"></a> wydajności

Dodaje element na górze stosu.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

*użyte*\
Element dodany na górze stosu.

### <a name="remarks"></a>Uwagi

Górna część stosu jest pozycją zajmowaną przez ostatnio dodany element i jest ostatnim elementem na końcu kontenera.

### <a name="example"></a>Przykład

```cpp
// stack_push.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1;

   s1.push( 10 );
   s1.push( 20 );
   s1.push( 30 );

   stack <int>::size_type i;
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   i = s1.top( );
   cout << "The element at the top of the stack is "
        << i << "." << endl;
}
```

```Output
The stack length is 3.
The element at the top of the stack is 30.
```

## <a name="size"></a><a name="size"></a> zmienia

Zwraca liczbę elementów w stosie.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość stosu.

### <a name="example"></a>Przykład

```cpp
// stack_size.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1, s2;
   stack <int>::size_type i;

   s1.push( 1 );
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   s1.push( 2 );
   i = s1.size( );
   cout << "The stack length is now " << i << "." << endl;
}
```

```Output
The stack length is 1.
The stack length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w stosie.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `size_type` kontenera podstawowego dostosowany przez stos.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dotyczącym [rozmiaru](#size) , aby zapoznać się z przykładem sposobu deklarowania i używania `size_type` .

## <a name="stack"></a><a name="stack"></a> stosu

Konstruuje stos, który jest pusty lub jest kopią bazowej klasy kontenera.

```cpp
stack();

explicit stack(const container_type& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Kontener, w którym skonstruowany stos ma być kopią.

### <a name="example"></a>Przykład

```cpp
// stack_stack.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stack with default deque base container
   stack <char> dsc1;

   //Explicitly declares a stack with deque base container
   stack <char, deque<char> > dsc2;

   // Declares a stack with vector base containers
   stack <int, vector<int> > vsi1;

   // Declares a stack with list base container
   stack <int, list<int> > lsi;

   // The second member function copies elements from a container
   vector<int> v1;
   v1.push_back( 1 );
   stack <int, vector<int> > vsi2( v1 );
   cout << "The element at the top of stack vsi2 is "
        << vsi2.top( ) << "." << endl;
}
```

```Output
The element at the top of stack vsi2 is 1.
```

## <a name="top"></a><a name="top"></a> Do góry

Zwraca odwołanie do elementu w górnej części stosu.

```cpp
reference top();

const_reference top() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do ostatniego elementu w kontenerze w górnej części stosu.

### <a name="remarks"></a>Uwagi

Stos nie może być pusty, aby można było zastosować funkcję członkowską. Górna część stosu jest pozycją zajmowaną przez ostatnio dodany element i jest ostatnim elementem na końcu kontenera.

Jeśli wartość zwracana `top` jest przypisana do `const_reference` , obiekt stosu nie może być modyfikowany. Jeśli wartość zwracana `top` jest przypisana do `reference` , obiekt stosu może być modyfikowany.

### <a name="example"></a>Przykład

```cpp
// stack_top.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1;

   s1.push( 1 );
   s1.push( 2 );

   int& i = s1.top( );
   const int& ii = s1.top( );

   cout << "The top integer of the stack s1 is "
        << i << "." << endl;
   i--;
   cout << "The next integer down is "<< ii << "." << endl;
}
```

```Output
The top integer of the stack s1 is 2.
The next integer down is 1.
```

## <a name="value_type"></a><a name="value_type"></a> value_type

Typ, który reprezentuje typ obiektu przechowywanego jako element w stosie.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `value_type` kontenera podstawowego dostosowany przez stos.

### <a name="example"></a>Przykład

```cpp
// stack_value_type.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   // Declares stacks with default deque base container
   stack<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   stack<int> s1;
   s1.push( AnInt );
   cout << "The element at the top of the stack is "
        << s1.top( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the top of the stack is 69.
```

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
