---
title: Stack — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- stack/std::stack::container_type
- stack/std::stack::size_type
- stack/std::stack::value_type
- stack/std::stack::empty
- stack/std::stack::pop
- stack/std::stack::push
- stack/std::stack::size
- stack/std::stack::top
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b933029f7180292e1c9e392bf2ab09e8dbcb204
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963228"
---
# <a name="stack-class"></a>stack — Klasa

Szablon kontenera adaptera Klasa udostępniająca ograniczenia funkcjonalność ograniczania dostępu do elementu ostatnio dodane do niektórych podstawowych typ kontenera. Klasa stosu jest używana, gdy jest się jasne, że tylko stosu operacje są wykonywane w kontenerze.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Container= deque <Type>>
class stack
```

### <a name="parameters"></a>Parametry

*Typ* typ danych elementu mają być przechowywane w stosie.

*Kontener* typu bazowego kontenera, używaną do zaimplementowania stosu. Wartość domyślna to klasa `deque`  *\<typ >*.

## <a name="remarks"></a>Uwagi

Elementy klasy `Type` określone w szablonie pierwszy parametr obiektu stack jest równoznaczny z [value_type](#value_type) i musi odpowiadać typowi elementu w klasie podstawowej kontenera `Container` określonymi przez drugi parametr szablonu. `Type` Musi być możliwy do przypisania, więc jest możliwe, aby skopiować obiekty tego typu, a także do przypisywania wartości do zmiennych tego typu.

Dołączyć odpowiednie podstawowej klasy kontenera stosu [deque](../standard-library/deque-class.md), [list, klasa](../standard-library/list-class.md), i [vector, klasa](../standard-library/vector-class.md), lub innego kontenera sekwencji, która obsługuje operacje `back`, `push_back`, i `pop_back`. Podstawowej klasy kontenera są hermetyzowane w obrębie adaptera kontenera, który uwidacznia tylko ograniczony zestaw funkcji elementów członkowskich kontenerów sekwencji jako interfejs publiczny.

Stosu obiektów są wtedy porównywanie równości i tylko wtedy, gdy elementy klasy `Type` są porównywanie równości i mniej-niż porównywalne wtedy i tylko wtedy, gdy elementy klasy `Type` są mniejsze-niż porównywalne.

- Klasa stosu obsługuje ostatni na wejściu, first-out (LIFO) strukturę danych. Dobre analogowy na uwadze byłoby były stosem talerzy. Elementy (talerzy) może wstawiania, inspekcji lub usunąć tylko z góry stosu, w którym jest ostatnim elementem na końcu podstawowym kontenerem. Ograniczenie do uzyskiwania dostępu do górnego elementu jest przyczyna przy użyciu klasy stosu.

- [Kolejkowania klasy](../standard-library/queue-class.md) obsługuje pierwszy in, first-out (FIFO) strukturę danych. Dobre analogowy na uwadze byłoby osób wyrównywania dla dla kasjerów bankowych. Elementy (osób) mogą być dodawane do końca wiersza i są usuwane z początku wiersza. Mogą być kontrolowane zarówno do przodu, jak i do tyłu wiersza. Ograniczenie do uzyskiwania dostępu do tylko przód i Wstecz elementy w ten sposób jest futerkowych Przyczyna przy użyciu klasy kolejki.

- [Priority_queue — klasa](../standard-library/priority-queue-class.md) porządkuje jego elementy, dzięki czemu największy element jest zawsze u góry. Obsługuje ona Wstawianie elementu i inspekcji i usuwania górnego elementu. Dobre analogowy na uwadze byłoby osób wyrównywanie gdzie one są uporządkowane według wiek, wysokości lub innego kryterium.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[stack](#stack)|Konstruuje `stack` pusty lub jest kopię obiektu podstawowego kontenera.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który zapewnia podstawowy kontener, aby zostać dostosowane przez `stack`.|
|[size_type](#size_type)|Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w `stack`.|
|[value_type](#value_type)|Typ, który reprezentuje typ obiektu przechowywanego jako element w `stack`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[pusty](#empty)|Sprawdza, czy `stack` jest pusty.|
|[POP](#pop)|Usuwa element z góry `stack`.|
|[push](#push)|Dodaje element do góry `stack`.|
|[Rozmiar](#size)|Zwraca liczbę elementów w `stack`.|
|[Do góry](#top)|Zwraca odwołanie do elementu w górnej części `stack`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<stosu >

**Namespace:** standardowe

## <a name="container_type"></a>  Stack::container_type

Typ, który dostarcza podstawowy kontener, aby dostosować.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Container`. Wszystkie trzy klasy kontenera sekwencja standardowej biblioteki języka C++ — klasa vector, klasa list i deque — klasa domyślne — spełniają wymagania, które ma być używany jako bazowy kontener dla obiektu stosu. Można także zmienić typy zdefiniowane przez użytkownika, spełnia te wymagania.

Aby uzyskać więcej informacji na temat `Container`, zobacz sekcję Uwagi [stack — klasa](../standard-library/stack-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [stack::stack](#stack) przykładowy sposób deklarowania i użyj `container_type`.

## <a name="empty"></a>  Stack::Empty

Sprawdza, czy stos jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli stosu jest pusta. **false** Jeśli stos jest niepusty.

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

## <a name="pop"></a>  Stack::POP

Usuwa element z góry stosu.

```cpp
void pop();
```

### <a name="remarks"></a>Uwagi

Stos może być puste do zastosowania funkcji elementu członkowskiego. Szczyt stosu jest pozycja zajmowane przez element ostatnio dodane i ostatni element na końcu kontenera.

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

## <a name="push"></a>  Stack::push

Dodaje element do górny koniec stosu.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val* elementu dodany na górze stosu.

### <a name="remarks"></a>Uwagi

Szczyt stosu jest pozycja zajmowane przez element ostatnio dodane i ostatni element na końcu kontenera.

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

## <a name="size"></a>  Stack::size

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

## <a name="size_type"></a>  Stack::size_type

Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w stosie.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `size_type` podstawowy kontenera dostosowane przez stos.

### <a name="example"></a>Przykład

Zobacz przykład [rozmiar](#size) przykładowy sposób deklarowania i użyj `size_type`.

## <a name="stack"></a>  Stack::Stack

Tworzy stosu, który jest pusty lub jest kopią klasy bazowej kontenera.

```cpp
stack();

explicit stack(const container_type& right);
```

### <a name="parameters"></a>Parametry

*prawy* kontenera, w której skonstruowany stosu jest kopią.

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

## <a name="top"></a>  Stack::Top

Zwraca odwołanie do elementu w górnej części stosu.

```cpp
reference top();

const_reference top() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do ostatniego elementu w kontenerze na górze stosu.

### <a name="remarks"></a>Uwagi

Stos może być puste do zastosowania funkcji elementu członkowskiego. Szczyt stosu jest pozycja zajmowane przez element ostatnio dodane i ostatni element na końcu kontenera.

Jeśli wartość zwracaną przez `top` jest przypisany do `const_reference`, nie można zmodyfikować obiektu stosu. Jeśli wartość zwracaną przez `top` jest przypisany do `reference`, można zmodyfikować obiekt stosu.

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

## <a name="value_type"></a>  Stack::value_type

Typ, który reprezentuje typ obiektu przechowywanego jako element w stosie.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `value_type` podstawowy kontenera dostosowane przez stos.

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

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
