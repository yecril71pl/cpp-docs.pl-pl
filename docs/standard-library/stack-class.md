---
title: "Stack — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stack/std::stack::container_type
- stack/std::stack::size_type
- stack/std::stack::value_type
- stack/std::stack::empty
- stack/std::stack::pop
- stack/std::stack::push
- stack/std::stack::size
- stack/std::stack::top
dev_langs: C++
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
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a0c593042bf92e63b1c1514326440d9aee8101b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="stack-class"></a>stack — Klasa
Klasa karty kontenera szablonu, która umożliwia ograniczenie funkcjonalności ograniczanie dostępu do elementu ostatnio dodane do niektórych podstawowy typ kontenera. Klasa stosu jest używana, jeśli ważne jest, aby być jasne, czy tylko stosu operacje są wykonywane w kontenerze.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Type, class Container= deque <Type>>  
class stack  
```  
  
#### <a name="parameters"></a>Parametry  
 *Typ*  
 Typ danych elementu mają być przechowywane w stosie.  
  
 `Container`  
 Typ podstawowy kontenera używaną do zaimplementowania stosu. Wartość domyślna to klasa `deque`  *\<typu >*.  
  
## <a name="remarks"></a>Uwagi  
 Elementy klasy **typu** określone w szablonie pierwszy parametr obiektu stosu są synonimem [value_type](#value_type) i musi odpowiadać typowi element w klasie podstawowej kontenera **Kontenera** określone przez drugi parametr szablonu. **Typu** musi być możliwa do przypisania, dzięki czemu możliwe jest do kopii obiektów tego typu i można przypisać wartości do zmiennych typu.  
  
 Dołączyć odpowiednie podstawowej klasy kontenerów stosu [deque —](../standard-library/deque-class.md), [list — klasa](../standard-library/list-class.md), i [vector — klasa](../standard-library/vector-class.md), lub inne kontenera sekwencji, która obsługuje operacje **ponownie**, `push_back`, i `pop_back`. Podstawowe klasy kontenera jest hermetyzowany w ramach karty kontenera, który udostępnia tylko ograniczony zestaw funkcji Członkowskich sekwencji kontener jako publiczny interfejs.  
  
 Stos obiektów, to jeśli można porównywać pod względem równości i tylko wtedy, gdy elementy klasy **typu** są można porównywać pod względem równości i mniejsza-niż porównywalne w przypadku i tylko wtedy, gdy elementy klasy **typu** są mniejsze-niż porównywanie.  
  
-   Klasa stosu obsługuje ostatni na, wytworzenia struktura danych. Dobrym analogowy należy wziąć pod uwagę będzie stosu tablic. Elementy (płyty) może wstawiania, inspekcji lub usunąć tylko z góry stosu, w którym jest ostatni element w końcu podstawowej kontenera. Ograniczenie do uzyskiwania dostępu do górnego elementu jest przyczyna za pomocą klasy stosu.  
  
-   [Kolejka klasy](../standard-library/queue-class.md) obsługuje pierwszy w, FIFO (FIFO) struktury danych. Dobrym analogowy należy wziąć pod uwagę będzie Wyrównywanie dla kasjerów bankowych osób. Elementy (użytkownicy) mogą być dodawane do tyłu wiersza i są usuwane z na początku wiersza. Może być sprawdzany przodu i z powrotem wiersza. Ograniczenie do uzyskiwania dostępu do tylko front i back elementów w ten sposób jest futerkowych Przyczyna za pomocą klasy kolejki.  
  
-   [Priority_queue — klasa](../standard-library/priority-queue-class.md) porządkuje swoich elementów, aby największy element zawsze znajduje się w górnej pozycji. Obsługuje ona wstawiania elementu oraz inspekcji i usuwaniu górnego elementu. Dobrym analogowy należy wziąć pod uwagę będzie osób wyrównywanie, gdzie są uporządkowane według ważności, wysokość lub innego kryterium.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[stos](#stack)|Konstruuje `stack` pusta lub jest kopię obiektu podstawowego kontenera.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[container_type](#container_type)|Typ, który zapewnia podstawową kontener należy dostosować przez `stack`.|  
|[size_type](#size_type)|Typu Liczba całkowita bez znaku, który może reprezentować liczbę elementów w `stack`.|  
|[value_type](#value_type)|Typ, który reprezentuje typ obiektu przechowywane jako elementu `stack`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[pusty](#empty)|Sprawdza, czy `stack` jest pusta.|  
|[POP](#pop)|Usuwa element z góry `stack`.|  
|[wypychania](#push)|Dodaje element do góry `stack`.|  
|[rozmiar](#size)|Zwraca liczbę elementów w `stack`.|  
|[Do góry](#top)|Zwraca odwołanie do elementu w górnej części `stack`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<stosu >  
  
 **Namespace:** Standard  
  
##  <a name="container_type"></a>Stack::container_type  
 Typ, który zapewnia podstawową kontener dostosowania.  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu `Container`. Wszystkie trzy klasy kontenerów sekwencji standardowa biblioteka C++ — klasa vector, list — klasa i deque — klasa domyślny — spełniać wymagania dotyczące służyć jako podstawowa kontener dla obiekt stosu. Typy danych zdefiniowane przez użytkownika spełnia te wymagania mogą również.  
  
 Aby uzyskać więcej informacji na temat `Container`, zobacz sekcję uwag [stack — klasa](../standard-library/stack-class.md) tematu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [stack::stack](#stack) przykład sposobu deklarowanie i użycie `container_type`.  
  
##  <a name="empty"></a>Stack::Empty  
 Testy, jeśli stos jest pusty.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli stos jest pusty; **false** Jeśli stos jest pusty.  
  
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
  
##  <a name="pop"></a>Stack::POP  
 Usuwa element z góry stosu.  
  
```  
void pop();
```  
  
### <a name="remarks"></a>Uwagi  
 Stos musi być niepustym do zastosowania funkcji członkowskiej. Wierzchołek stosu jest zajmowane przez element ostatnio dodane stanowisko i ostatni element w końcu kontenera.  
  
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
  
##  <a name="push"></a>Stack::push  
 Dodaje element do górny koniec stosu.  
  
```  
void push(const Type& val);
```  
  
### <a name="parameters"></a>Parametry  
 `val`  
 Element dodany do góry stosu.  
  
### <a name="remarks"></a>Uwagi  
 Wierzchołek stosu jest zajmowane przez element ostatnio dodane stanowisko i ostatni element w końcu kontenera.  
  
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
  
##  <a name="size"></a>Stack::size  
 Zwraca liczbę elementów w stosie.  
  
```  
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
  
##  <a name="size_type"></a>Stack::size_type  
 Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w stosie.  
  
```  
typedef typename Container::size_type size_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem `size_type` podstawowej kontenera dostosowane przez stos.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozmiar](#size) przykład sposobu deklarowanie i użycie `size_type`.  
  
##  <a name="stack"></a>Stack::Stack  
 Tworzy stos jest pusty lub który jest kopią klasy podstawowej kontenera.  
  
```  
stack();

explicit stack(const container_type& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Kontener skonstruowane stosu ma być kopii.  
  
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
  
##  <a name="top"></a>Stack::Top  
 Zwraca odwołanie do elementu w górnej części stosu.  
  
```  
reference top();

const_reference top() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do ostatniego elementu w kontenerze na wierzchu stosu.  
  
### <a name="remarks"></a>Uwagi  
 Stos musi być niepustym do zastosowania funkcji członkowskiej. Wierzchołek stosu jest zajmowane przez element ostatnio dodane stanowisko i ostatni element w końcu kontenera.  
  
 Jeśli wartość zwracana **górnej** jest przypisany do `const_reference`, nie można zmodyfikować obiektu stosu. Jeśli wartość zwracana **górnej** jest przypisany do **odwołania**, można zmodyfikować obiektu stosu.  
  
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
  
##  <a name="value_type"></a>Stack::value_type  
 Typ, który reprezentuje typ obiektu przechowywane jako element na stosie.  
  
```  
typedef typename Container::value_type value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem `value_type` podstawowej kontenera dostosowane przez stos.  
  
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
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Odwołanie do biblioteki C++ Standard](../standard-library/cpp-standard-library-reference.md)

