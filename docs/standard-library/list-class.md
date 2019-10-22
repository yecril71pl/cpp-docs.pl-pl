---
title: list — Klasa
ms.date: 11/04/2016
f1_keywords:
- list/std::list
- list/std::list::allocator_type
- list/std::list::const_iterator
- list/std::list::const_pointer
- list/std::list::const_reference
- list/std::list::const_reverse_iterator
- list/std::list::difference_type
- list/std::list::iterator
- list/std::list::pointer
- list/std::list::reference
- list/std::list::reverse_iterator
- list/std::list::size_type
- list/std::list::value_type
- list/std::list::assign
- list/std::list::back
- list/std::list::begin
- list/std::list::cbegin
- list/std::list::cend
- list/std::list::clear
- list/std::list::crbegin
- list/std::list::crend
- list/std::list::emplace
- list/std::list::emplace_back
- list/std::list::emplace_front
- list/std::list::empty
- list/std::list::end
- list/std::list::erase
- list/std::list::front
- list/std::list::get_allocator
- list/std::list::insert
- list/std::list::max_size
- list/std::list::merge
- list/std::list::pop_back
- list/std::list::pop_front
- list/std::list::push_back
- list/std::list::push_front
- list/std::list::rbegin
- list/std::list::remove
- list/std::list::remove_if
- list/std::list::rend
- list/std::list::resize
- list/std::list::reverse
- list/std::list::size
- list/std::list::sort
- list/std::list::splice
- list/std::list::swap
- list/std::list::unique
helpviewer_keywords:
- std::list [C++]
- std::list [C++], allocator_type
- std::list [C++], const_iterator
- std::list [C++], const_pointer
- std::list [C++], const_reference
- std::list [C++], const_reverse_iterator
- std::list [C++], difference_type
- std::list [C++], iterator
- std::list [C++], pointer
- std::list [C++], reference
- std::list [C++], reverse_iterator
- std::list [C++], size_type
- std::list [C++], value_type
- std::list [C++], assign
- std::list [C++], back
- std::list [C++], begin
- std::list [C++], cbegin
- std::list [C++], cend
- std::list [C++], clear
- std::list [C++], crbegin
- std::list [C++], crend
- std::list [C++], emplace
- std::list [C++], emplace_back
- std::list [C++], emplace_front
- std::list [C++], empty
- std::list [C++], end
- std::list [C++], erase
- std::list [C++], front
- std::list [C++], get_allocator
- std::list [C++], insert
- std::list [C++], max_size
- std::list [C++], merge
- std::list [C++], pop_back
- std::list [C++], pop_front
- std::list [C++], push_back
- std::list [C++], push_front
- std::list [C++], rbegin
- std::list [C++], remove
- std::list [C++], remove_if
- std::list [C++], rend
- std::list [C++], resize
- std::list [C++], reverse
- std::list [C++], size
- std::list [C++], sort
- std::list [C++], splice
- std::list [C++], swap
- std::list [C++], unique
ms.assetid: d3707f4a-10fd-444f-b856-f9ca2077c1cd
ms.openlocfilehash: d5f64f44ec62a8bd1862af2b8f9cb72b2d0210e4
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687824"
---
# <a name="list-class"></a>list — Klasa

Klasa C++ standardowej biblioteki klas to szablon klasy kontenerów sekwencji, które utrzymują elementy w rozmieszczeniu liniowym i umożliwiają efektywne Wstawianie i usuwanie w dowolnej lokalizacji w ramach sekwencji. Sekwencja jest przechowywana jako dwukierunkowa, połączona lista elementów, z których każdy zawiera element członkowski pewnego *typu.*

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Allocator= allocator<Type>>
class list
```

### <a name="parameters"></a>Parametry

*Typ* \
Typ danych elementu, który ma być przechowywany na liście.

@No__t_1 *alokatora*
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji listy i cofania alokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to **alokator** \<*typu*>.

## <a name="remarks"></a>Uwagi

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Wektory powinny być preferowanym kontenerem do zarządzania sekwencją, gdy losowy dostęp do dowolnego elementu znajduje się w warstwie Premium, a wstawienia lub usunięcia elementów są wymagane tylko na końcu sekwencji. Wydajność kontenera deque klasy jest wyższa, gdy wymagany jest dostęp losowy, a wstawienia i usunięcia na początku i na końcu sekwencji są w wersji Premium.

Funkcje elementów członkowskich listy [scalanie](#merge), [odwrócenie](#reverse), [unikatowe](#unique), [usuwanie](#remove)i [remove_if](#remove_if) zostały zoptymalizowane pod kątem operacji na obiektach list i oferują alternatywną wydajność dla ich rodzajowych odpowiedników.

Ponowna Alokacja listy występuje, gdy funkcja członkowska musi wstawić lub wymazać elementy listy. We wszystkich takich przypadkach tylko Iteratory lub odwołania wskazujące na wymazane fragmenty kontrolowanej sekwencji stają się nieprawidłowe.

C++ Uwzględnij standardowy nagłówek standardowej biblioteki \<list >, aby zdefiniować listę szablonów klas [kontenerów](../standard-library/stl-containers.md) i kilka szablonów pomocniczych.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[list](#list)|Tworzy listę o określonym rozmiarze lub z elementami określonej wartości lub z określonym `allocator` lub jako kopią innej listy.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje klasę `allocator` dla obiektu list.|
|[const_iterator](#const_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać element **const** na liście.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do elementu **const** na liście.|
|[const_reference](#const_reference)|Typ, który dostarcza odwołanie do elementu **const** przechowywanego na liście do odczytu i wykonywania operacji **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny element **const** na liście.|
|[difference_type](#difference_type)|Typ, który zawiera różnicę między dwoma iteratorami odwołującymi się do elementów w obrębie tej samej listy.|
|[Iterator](#iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element na liście.|
|[przytrzymaj](#pointer)|Typ, który dostarcza wskaźnik do elementu na liście.|
|[odwoła](#reference)|Typ, który dostarcza odwołanie do elementu **const** przechowywanego na liście do odczytu i wykonywania operacji **const** .|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element na liście odwróconej.|
|[size_type](#size_type)|Typ, który zlicza liczbę elementów na liście.|
|[value_type](#value_type)|Typ, który reprezentuje typ danych przechowywany na liście.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[ponownie](#assign)|Wymazuje elementy z listy i kopiuje nowy zestaw elementów na listę docelową.|
|[Wstecz](#back)|Zwraca odwołanie do ostatniego elementu listy.|
|[zaczną](#begin)|Zwraca iterator odnoszący się do pierwszego elementu na liście.|
|[cbegin](#cbegin)|Zwraca iterator const odnoszący się do pierwszego elementu na liście.|
|[cend](#cend)|Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie na liście.|
|[Wyczyść](#clear)|Usuwa wszystkie elementy listy.|
|[crbegin —](#crbegin)|Zwraca iterator const odnoszący się do pierwszego elementu na liście odwróconej.|
|[crend](#crend)|Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie na liście odwróconej.|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do listy w określonym położeniu.|
|[emplace_back](#emplace_back)|Dodaje element skonstruowany w miejscu na końcu listy.|
|[emplace_front](#emplace_front)|Dodaje element skonstruowany w miejscu na początku listy.|
|[ciągiem](#empty)|Testuje, czy lista jest pusta.|
|[punktów](#end)|Zwraca iterator, który odnosi się do lokalizacji na końcu ostatniego elementu na liście.|
|[Wyłączanie](#erase)|Usuwa element lub zakres elementów na liście z określonych pozycji.|
|[FSB](#front)|Zwraca odwołanie do pierwszego elementu na liście.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu `allocator` użytego do konstruowania listy.|
|[wstawienia](#insert)|Wstawia element lub liczbę elementów lub zakres elementów do listy w określonym położeniu.|
|[max_size](#max_size)|Zwraca maksymalną długość listy.|
|[połączenie](#merge)|Usuwa elementy z listy argumentów, wstawia je do listy docelowej i porządkuje nowy, połączony zestaw elementów w kolejności rosnącej lub w innej określonej kolejności.|
|[pop_back](#pop_back)|Usuwa element na końcu listy.|
|[pop_front](#pop_front)|Usuwa element na początku listy.|
|[push_back](#push_back)|Dodaje element na końcu listy.|
|[push_front](#push_front)|Dodaje element na początku listy.|
|[rbegin](#rbegin)|Zwraca iterator odnoszący się do pierwszego elementu na liście odwróconej.|
|[remove](#remove)|Wymazuje elementy znajdujące się na liście, które pasują do określonej wartości.|
|[remove_if](#remove_if)|Usuwa elementy z listy, dla których jest spełniony określony predykat.|
|[rend](#rend)|Zwraca iterator, który odnosi się do lokalizacji po ostatnim elemencie na liście odwróconej.|
|[Zmień rozmiar](#resize)|Określa nowy rozmiar listy.|
|[cofnięci](#reverse)|Odwraca kolejność elementów na liście.|
|[zmienia](#size)|Zwraca liczbę elementów na liście.|
|[porządku](#sort)|Rozmieszcza elementy listy w kolejności rosnącej lub w odniesieniu do innej relacji Order.|
|[splice](#splice)|Usuwa elementy z listy argumentów i wstawia je do listy elementów docelowych.|
|[wymiany](#swap)|Wymienia elementy dwóch list.|
|[unique](#unique)|Usuwa sąsiadujące zduplikowane elementy lub sąsiadujące elementy, które spełniają inny Predykat binarny z listy.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#op_eq)|Zamienia elementy listy na kopię innej listy.|

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<list >

## <a name="allocator_type"></a>allocator_type

Typ, który reprezentuje klasę alokatora dla obiektu list.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type` jest synonimem dla *alokatora*parametrów szablonu.

### <a name="example"></a>Przykład

Zobacz przykład dla [get_allocator](#get_allocator).

## <a name="assign"></a>ponownie

Wymazuje elementy z listy i kopiuje nowy zestaw elementów na listę docelową.

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign
    initializer_list<Type> IList);

template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>Parametry

*Pierwszy* \
Pozycja pierwszego elementu w zakresie elementów, który ma zostać skopiowany z listy argumentów.

*Ostatni* \
Pozycja pierwszego elementu tuż poza zakresem elementów, które mają być skopiowane z listy argumentów.

*Liczba* \
Liczba kopii elementu wstawianych do listy.

*Val* \
Wartość wstawianego elementu do listy.

@No__t_1 *IList*
Initializer_list, który zawiera elementy do wstawienia.

### <a name="remarks"></a>Uwagi

Po wymazaniu wszystkich istniejących elementów z listy docelowej Przypisz do listy docelowej lub wstawi z niej określony zakres elementów z listy pierwotnej lub z innej listy lub wstawia kopie nowego elementu z określoną wartością do listy elementów docelowych.

### <a name="example"></a>Przykład

```cpp
// list_assign.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    list<int> c1, c2;
    list<int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign({ 10, 20, 30, 40 });
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 10 20 30c1 = 50 60c1 = 4 4 4 4 4 4 4c1 = 10 20 30 40
```

## <a name="back"></a>Wstecz

Zwraca odwołanie do ostatniego elementu listy.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Ostatni element listy. Jeśli lista jest pusta, wartość zwracana jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana `back` jest przypisana do `const_reference`, nie można zmodyfikować obiektu listy. Jeśli wartość zwracana `back` jest przypisana do `reference`, można zmodyfikować obiekt listy.

Po skompilowaniu przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowanego jako 1 lub 2, wystąpi błąd czasu wykonywania, jeśli spróbujesz uzyskać dostęp do elementu na pustej liście.  Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md) .

### <a name="example"></a>Przykład

```cpp
// list_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.back( );
   const int& ii = c1.front( );

   cout << "The last integer of c1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of c1 is " << ii << endl;
}
```

```Output
The last integer of c1 is 11
The next-to-last integer of c1 is 10
```

## <a name="begin"></a>zaczną

Zwraca iterator odnoszący się do pierwszego elementu na liście.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pierwszego elementu na liście lub do lokalizacji, która pomyślnie ma pustą listę.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana `begin` jest przypisana do `const_iterator`, nie można modyfikować elementów w obiekcie list. Jeśli wartość zwracana `begin` jest przypisana do `iterator`, elementy w obiekcie listy mogą być modyfikowane.

### <a name="example"></a>Przykład

```cpp
// list_begin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::const_iterator c1_cIter;

   c1.push_back( 1 );
   c1.push_back( 2 );

   c1_Iter = c1.begin( );
   cout << "The first element of c1 is " << *c1_Iter << endl;

*c1_Iter = 20;
   c1_Iter = c1.begin( );
   cout << "The first element of c1 is now " << *c1_Iter << endl;

   // The following line would be an error because iterator is const
   // *c1_cIter = 200;
}
```

```Output
The first element of c1 is 1
The first element of c1 is now 20
```

## <a name="cbegin"></a>cbegin

Zwraca iterator **const** , który dotyczy pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

**Stałe** Iterator dostępu dwukierunkowego, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).

### <a name="remarks"></a>Uwagi

Z wartością zwracaną `cbegin` nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast funkcji składowej `begin()`, aby zagwarantować, że wartość zwracana jest `const_iterator`. Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy, że `Container` być kontenerem modyfikowalnym (innym niż **const**) dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

Zwraca iterator `const`, który odnosi się do lokalizacji jedynie poza ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

@No__t_0 Iterator dostępu dwukierunkowego, który wskazuje tuż poza końcem zakresu.

### <a name="remarks"></a>Uwagi

`cend` służy do sprawdzania, czy iterator przeszedł koniec zakresu.

Można użyć tej funkcji elementu członkowskiego zamiast funkcji składowej `end()`, aby zagwarantować, że wartość zwracana jest `const_iterator`. Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy, że `Container` być kontenerem modyfikowalnym (innym niż **const**) dowolnego rodzaju, który obsługuje `end()` i `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Nie należy wywoływać wartości zwracanej przez `cend`.

## <a name="clear"></a>Wyczyść

Usuwa wszystkie elementy listy.

```cpp
void clear();
```

### <a name="example"></a>Przykład

```cpp
// list_clear.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the list is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of list after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the list is initially 3
The size of list after clearing is 0
```

## <a name="const_iterator"></a>const_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać element **const** na liście.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typu `const_iterator` nie można użyć do zmodyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład dla z [tyłu](#back).

## <a name="const_pointer"></a>const_pointer

Udostępnia wskaźnik do elementu **const** na liście.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typu `const_pointer` nie można użyć do zmodyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie list.

## <a name="const_reference"></a>const_reference

Typ, który dostarcza odwołanie do elementu **const** przechowywanego na liście do odczytu i wykonywania operacji **const** .

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

Typu `const_reference` nie można użyć do zmodyfikowania wartości elementu.

### <a name="example"></a>Przykład

```cpp
// list_const_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const list <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error because c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a>const_reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny element **const** na liście.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartości elementu i służy do iterowania przez listę w odwrotnej.

### <a name="example"></a>Przykład

Zobacz przykład dla [rbegin](#rbegin).

## <a name="crbegin"></a>crbegin —

Zwraca iterator const odnoszący się do pierwszego elementu na liście odwróconej.

```cpp
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Nieodwrócony iterator dwukierunkowy, odnoszący się do pierwszego elementu na liście odwróconej (lub adresowania ostatniego elementu w nieodwróconej `list`).

### <a name="remarks"></a>Uwagi

`crbegin` jest używany z odwróconą listą, tak jak [Lista:: BEGIN](#begin) jest używany z `list`.

Po wartości zwracanej `crbegin` nie można zmodyfikować obiektu list. [list:: rbegin](#rbegin) można użyć do iteracji listy wstecz.

### <a name="example"></a>Przykład

```cpp
// list_crbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_crIter = c1.crbegin( );
   cout << "The last element in the list is " << *c1_crIter << "." << endl;
}
```

```Output
The last element in the list is 30.
```

## <a name="crend"></a>crend

Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie na liście odwróconej.

```cpp
const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Wartość zwracana

Nieodwrócony iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie na [liście](../standard-library/list-class.md) odwróconej (lokalizacja, która poprzedza pierwszy element w nieodwróconym `list`).

### <a name="remarks"></a>Uwagi

`crend` jest używany z odwróconą listą, podobnie jak [list:: end](#end) jest używany z `list`.

Z wartością zwracaną `crend` nie można zmodyfikować obiektu `list`.

`crend` można użyć do przetestowania, czy iterator odwrotny osiągnął koniec jego `list`.

Nie należy wywoływać wartości zwracanej przez `crend`.

### <a name="example"></a>Przykład

```cpp
// list_crend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_crIter = c1.crend( );
   c1_crIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_crIter << endl;
}
```

```Output
The first element in the list is: 10
```

## <a name="difference_type"></a>difference_type

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów listy w zakresie między elementami wskazywanymi przez Iteratory.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

@No__t_0 jest typem zwracanym podczas odejmowania lub zwiększania przez Iteratory kontenera. @No__t_0 jest zwykle używany do reprezentowania liczby elementów w zakresie [`first`, `last`) między iteratorami `first` i `last`, zawiera element wskazywany przez `first` i zakres elementów do , ale nie obejmuje, element wskazywany przez `last`.

Należy zauważyć, że chociaż `difference_type` jest dostępny dla wszystkich iteratorów, które spełniają wymagania iteratora danych wejściowych, który obejmuje klasę iteratorów dwukierunkowych obsługiwanych przez kontenery odwracalne, takie jak Set, odejmowanie między iteratorami jest obsługiwane tylko przez Iteratory dostępu swobodnego udostępniane przez kontener dostępu swobodnego, taki jak [Klasa wektora](../standard-library/vector-class.md).

### <a name="example"></a>Przykład

```cpp
// list_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <list>
#include <algorithm>

int main( )
{
   using namespace std;

   list <int> c1;
   list <int>::iterator   c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

    list <int>::difference_type df_typ1, df_typ2, df_typ3;

   df_typ1 = count( c1_Iter, c2_Iter, 10 );
   df_typ2 = count( c1_Iter, c2_Iter, 20 );
   df_typ3 = count( c1_Iter, c2_Iter, 30 );
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";
}
```

```Output
The number '10' is in c1 collection 1 times.
The number '20' is in c1 collection 2 times.
The number '30' is in c1 collection 3 times.
```

## <a name="emplace"></a>emplace

Wstawia element skonstruowany w miejscu do listy w określonym położeniu.

```cpp
void emplace(iterator Where, Type&& val);
```

### <a name="parameters"></a>Parametry

*Gdzie* \
Pozycja na [liście](../standard-library/list-class.md) docelowej, w której wstawiany jest pierwszy element.

*val* \
Element dodany na końcu `list`.

### <a name="remarks"></a>Uwagi

Jeśli wystąpi wyjątek, `list` pozostaje niezmieniona i wyjątek zostanie ponownie zgłoszony.

### <a name="example"></a>Przykład

```cpp
// list_emplace.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace(c2.begin(), move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_back"></a>emplace_back

Dodaje element skonstruowany w miejscu na końcu listy.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Parametry

*val* \
Element dodany na końcu [listy](../standard-library/list-class.md).

### <a name="remarks"></a>Uwagi

Jeśli wystąpi wyjątek, `list` pozostaje niezmieniona i wyjątek zostanie ponownie zgłoszony.

### <a name="example"></a>Przykład

```cpp
// list_emplace_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_front"></a>emplace_front

Dodaje element skonstruowany w miejscu na początku listy.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

*val* \
Element dodany na początku [listy](../standard-library/list-class.md).

### <a name="remarks"></a>Uwagi

Jeśli wystąpi wyjątek, `list` pozostaje niezmieniona i wyjątek zostanie ponownie zgłoszony.

### <a name="example"></a>Przykład

```cpp
// list_emplace_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="empty"></a>ciągiem

Testuje, czy lista jest pusta.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli lista jest pusta. **Fałsz** , jeśli lista nie jest pusta.

### <a name="example"></a>Przykład

```cpp
// list_empty.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The list is empty." << endl;
   else
      cout << "The list is not empty." << endl;
}
```

```Output
The list is not empty.
```

## <a name="end"></a>punktów

Zwraca iterator, który odnosi się do lokalizacji na końcu ostatniego elementu na liście.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy, który odnosi się do lokalizacji na końcu ostatniego elementu na liście. Jeśli lista jest pusta, a następnie `list::end == list::begin`.

### <a name="remarks"></a>Uwagi

`end` służy do sprawdzania, czy iterator osiągnął koniec listy.

### <a name="example"></a>Przykład

```cpp
// list_end.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
*c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is "
        << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // list <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The list is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The list is now: 10 400 30
```

## <a name="erase"></a>Wyłączanie

Usuwa element lub zakres elementów na liście z określonych pozycji.

```cpp
iterator erase(iterator Where);
iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Parametry

*Gdzie* \
Pozycja elementu, który ma zostać usunięty z listy.

*pierwszy* \
Pozycja pierwszego elementu usunięty z listy.

*ostatni* \
Umieść tuż poza ostatnim elementem usuniętym z listy.

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy, który wyznacza pierwszy element pozostały poza elementami usuniętymi lub wskaźnik do końca listy, jeśli taki element nie istnieje.

### <a name="remarks"></a>Uwagi

Nie ma żadnych ponownych alokacji, dlatego Iteratory i odwołania stają się nieprawidłowe tylko dla wymazanych elementów.

`erase` nigdy nie zgłasza wyjątku.

### <a name="example"></a>Przykład

```cpp
// list_erase.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial list is:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the list becomes:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, the list becomes: ";
   for (Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
The initial list is: 10 20 30 40 50
After erasing the first element, the list becomes: 20 30 40 50
After erasing all elements but the first, the list becomes:  20
```

## <a name="front"></a>FSB

Zwraca odwołanie do pierwszego elementu na liście.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest pusta, zwracana jest wartość undefined.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana `front` jest przypisana do `const_reference`, nie można zmodyfikować obiektu listy. Jeśli wartość zwracana `front` jest przypisana do `reference`, można zmodyfikować obiekt listy.

Po skompilowaniu przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowanego jako 1 lub 2, wystąpi błąd czasu wykonywania, jeśli spróbujesz uzyskać dostęp do elementu na pustej liście.  Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md) .

### <a name="example"></a>Przykład

```cpp
// list_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );

   int& i = c1.front();
   const int& ii = c1.front();

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The first integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The first integer of c1 is 11
```

## <a name="get_allocator"></a>get_allocator

Zwraca kopię obiektu alokatora używanego do konstruowania listy.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez listę.

### <a name="remarks"></a>Uwagi

Przypisania klasy list określają sposób zarządzania magazynem przez klasę. Domyślne przydzielenie klas kontenerów C++ biblioteki standardowej jest wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym C++ tematem.

### <a name="example"></a>Przykład

```cpp
// list_get_allocator.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   list <int> c1;
   list <int, allocator<int> > c2 = list <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   list <int> c3( c1.get_allocator( ) );

   list<int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a>wstawienia

Wstawia element lub liczbę elementów lub zakres elementów do listy w określonym położeniu.

```cpp
iterator insert(iterator Where, const Type& Val);
iterator insert(iterator Where, Type&& Val);

void insert(iterator Where, size_type Count, const Type& Val);
iterator insert(iterator Where, initializer_list<Type> IList);

template <class InputIterator>
void insert(iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parametry

*Gdzie* \
Pozycja na liście docelowej, w której wstawiany jest pierwszy element.

*Val* \
Wartość wstawianego elementu do listy.

*Liczba* \
Liczba elementów, które są wstawiane do listy.

*Pierwszy* \
Pozycja pierwszego elementu w zakresie elementów na liście argumentów do skopiowania.

*Ostatni* \
Pozycja pierwszego elementu poza zakresem elementów na liście argumentów do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie funkcje INSERT zwracają iterator, który wskazuje na miejsce, w którym nowy element został wstawiony do listy.

### <a name="example"></a>Przykład

```cpp
// list_class_insert.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    list <int> c1, c2;
    list <int>::iterator Iter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    c1.insert(Iter, 100);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    Iter++;
    c1.insert(Iter, 2, 200);

    cout << "c1 =";
    for(auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.insert(++c1.begin(), c2.begin(), --c2.end());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    // initialize a list of strings by moving
    list < string > c3;
    string str("a");

    c3.insert(c3.begin(), move(str));
    cout << "Moved first element: " << c3.front() << endl;

    // Assign with an initializer_list
    list <int> c4{ {1, 2, 3, 4} };
    c4.insert(c4.begin(), { 5, 6, 7, 8 });

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;
}
```

## <a name="iterator"></a>Iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element na liście.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpoczęcia](#begin).

## <a name="list"></a>staw

Tworzy listę o określonym rozmiarze lub z elementami określonej wartości lub z określonym alokatorem lub jako kopią całości lub części innej listy.

```cpp
list();
explicit list(const Allocator& Al);
explicit list(size_type Count);
list(size_type Count, const Type& Val);
list(size_type Count, const Type& Val, const Allocator& Al);

list(const list& Right);
list(list&& Right);
list(initializer_list<Type> IList, const Allocator& Al);

template <class InputIterator>
list(InputIterator First, InputIterator Last);

template <class InputIterator>
list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>Parametry

*Al* \
Klasa alokatora do wykorzystania z tym obiektem.

*Liczba* \
Liczba elementów na liście skonstruowane.

*Val* \
Wartość elementów na liście.

*Prawa* \
Lista, której skonstruowaną listą jest kopia.

*Pierwszy* \
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*Ostatni* \
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

@No__t_1 *IList*
Initializer_list, który zawiera elementy, które mają zostać skopiowane.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują obiekt alokatora (*Al*) i inicjują listę.

[get_allocator](#get_allocator) zwraca kopię obiektu alokatora używanego do konstruowania listy.

Pierwsze dwa konstruktory określają pustą listę początkową, drugą określającą typ alokatora (*Al*), który ma być używany.

Trzeci konstruktor określa powtarzanie określonej liczby (*Count*) elementów wartości domyślnej dla klasy `Type`.

Czwarty i piąty konstruktory określają powtórzenia (*Count*) elementów wartości *Val*.

Szósty konstruktor określa kopię *po prawej stronie*listy.

Siódmy Konstruktor przenosi listę w *prawo*.

Ósmy Konstruktor używa elementu initializer_list, aby określić elementy.

Dwa następne konstruktory skopiują zakres `[First, Last)` listy.

Żaden z konstruktorów nie wykonuje żadnych tymczasowych ponownych alokacji.

### <a name="example"></a>Przykład

```cpp
// list_class_list.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty list c0
    list <int> c0;

    // Create a list c1 with 3 elements of default value 0
    list <int> c1(3);

    // Create a list c2 with 5 elements of value 2
    list <int> c2(5, 2);

    // Create a list c3 with 3 elements of value 1 and with the
    // allocator of list c2
    list <int> c3(3, 1, c2.get_allocator());

    // Create a copy, list c4, of list c2
    list <int> c4(c2);

    // Create a list c5 by copying the range c4[ first,  last)
    list <int>::iterator c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    list <int> c5(c4.begin(), c4_Iter);

    // Create a list c6 by copying the range c4[ first,  last) and with
    // the allocator of list c2
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    list <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    cout << "c2 =";
    for (auto c : c2)
        cout << " " << c;
    cout << endl;

    cout << "c3 =";
    for (auto c : c3)
        cout << " " << c;
    cout << endl;

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;

    cout << "c6 =";
    for (auto c : c6)
        cout << " " << c;
    cout << endl;

    // Move list c6 to list c7
    list <int> c7(move(c6));
    cout << "c7 =";
    for (auto c : c7)
        cout << " " << c;
    cout << endl;

    // Construct with initializer_list
    list<int> c8({ 1, 2, 3, 4 });
    cout << "c8 =";
    for (auto c : c8)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 0 0 0c2 = 2 2 2 2 2c3 = 1 1 1c4 = 2 2 2 2 2c5 = 2 2c6 = 2 2 2c7 = 2 2 2c8 = 1 2 3 4
```

## <a name="max_size"></a>max_size

Zwraca maksymalną długość listy.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna możliwa długość listy.

### <a name="example"></a>Przykład

```cpp
// list_max_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   i = c1.max_size( );
   cout << "Maximum possible length of the list is " << i << "." << endl;
}
```

## <a name="merge"></a>połączenie

Usuwa elementy z listy argumentów, wstawia je do listy docelowej i porządkuje nowy, połączony zestaw elementów w kolejności rosnącej lub w innej określonej kolejności.

```cpp
void merge(list<Type, Allocator>& right);

template <class Traits>
void merge(list<Type, Allocator>& right, Traits comp);
```

### <a name="parameters"></a>Parametry

*prawa* \
Lista argumentów, która ma zostać scalona z listą docelową.

\ *zgodności*
Operator porównania używany do porządkowania elementów listy docelowej.

### <a name="remarks"></a>Uwagi

*Prawo* listy argumentów jest scalane z listą docelową.

Oba argumenty i listy docelowe muszą być uporządkowane przy użyciu tej samej relacji porównania, w której ma być uporządkowana wynikowa sekwencja. Kolejność domyślna pierwszej składowej to rosnąca kolejność. Druga funkcja członkowska nakłada określony przez użytkownika *zgodność* operacji porównania klasy `Traits`.

### <a name="example"></a>Przykład

```cpp
// list_merge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter, c2_Iter, c3_Iter;

   c1.push_back( 3 );
   c1.push_back( 6 );
   c2.push_back( 2 );
   c2.push_back( 4 );
   c3.push_back( 5 );
   c3.push_back( 1 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   cout << "c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   c2.merge( c1 );  // Merge c1 into c2 in (default) ascending order
   c2.sort( greater<int>( ) );
   cout << "After merging c1 with c2 and sorting with >: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   cout << "c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;

   c2.merge( c3, greater<int>( ) );
   cout << "After merging c3 with c2 according to the '>' comparison relation: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
c1 = 3 6
c2 = 2 4
After merging c1 with c2 and sorting with >: c2 = 6 4 3 2
c3 = 5 1
After merging c3 with c2 according to the '>' comparison relation: c2 = 6 5 4 3 2 1
```

## <a name="op_eq"></a>operator =

Zamienia elementy listy na kopię innej listy.

```cpp
list& operator=(const list& right);
list& operator=(list&& right);
```

### <a name="parameters"></a>Parametry

*prawa* \
[Lista](../standard-library/list-class.md) kopiowana do `list`.

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkich istniejących elementów w `list` operator kopiuje lub przenosi zawartość *bezpośrednio* do `list`.

### <a name="example"></a>Przykład

```cpp
// list_operator_as.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int> v1, v2, v3;
   list<int>::iterator iter;

   v1.push_back(10);
   v1.push_back(20);
   v1.push_back(30);
   v1.push_back(40);
   v1.push_back(50);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = forward< list<int> >(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a>przytrzymaj

Udostępnia wskaźnik do elementu na liście.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie list.

## <a name="pop_back"></a>pop_back

Usuwa element na końcu listy.

```cpp
void pop_back();
```

### <a name="remarks"></a>Uwagi

Ostatni element nie może być pusty. `pop_back` nigdy nie zgłasza wyjątku.

### <a name="example"></a>Przykład

```cpp
// list_pop_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the list, "
           "the last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the list, the last element is: 1
```

## <a name="pop_front"></a>pop_front

Usuwa element na początku listy.

```cpp
void pop_front();
```

### <a name="remarks"></a>Uwagi

Pierwszy element nie może być pusty. `pop_front` nigdy nie zgłasza wyjątku.

### <a name="example"></a>Przykład

```cpp
// list_pop_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the list, "
         "the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the list, the first element is: 2
```

## <a name="push_back"></a>push_back

Dodaje element na końcu listy.

```cpp
void push_back(void push_back(Type&& val);
```

### <a name="parameters"></a>Parametry

*val* \
Element dodany na końcu listy.

### <a name="remarks"></a>Uwagi

Jeśli wyjątek jest zgłaszany, lista pozostaje niezmieniona i wyjątek jest zgłaszany ponownie.

### <a name="example"></a>Przykład

```cpp
// list_push_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   if ( c1.size( ) != 0 )
      cout << "Last element: " << c1.back( ) << endl;

   c1.push_back( 2 );
   if ( c1.size( ) != 0 )
      cout << "New last element: " << c1.back( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved first element: a
```

## <a name="push_front"></a>push_front

Dodaje element na początku listy.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

*val* \
Element dodany na początku listy.

### <a name="remarks"></a>Uwagi

Jeśli wyjątek jest zgłaszany, lista pozostaje niezmieniona i wyjątek jest zgłaszany ponownie.

### <a name="example"></a>Przykład

```cpp
// list_push_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
First element: 1
New first element: 2
Moved first element: a
```

## <a name="rbegin"></a>rbegin

Zwraca iterator, który odnosi się do pierwszego elementu na liście odwróconej.

```cpp
const_reverse_iterator rbegin() const;
reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do pierwszego elementu na liście odwróconej (lub adresowania ostatniego elementu na liście nieodwróconej).

### <a name="remarks"></a>Uwagi

`rbegin` jest używany z odwróconą listą, tak jak [początek](#begin) jest używany z listą.

Jeśli wartość zwracana `rbegin` jest przypisana do `const_reverse_iterator`, nie można zmodyfikować obiektu listy. Jeśli wartość zwracana `rbegin` jest przypisana do `reverse_iterator`, można zmodyfikować obiekt listy.

`rbegin` można użyć do iteracji listy wstecz.

### <a name="example"></a>Przykład

```cpp
// list_rbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line replaced the line above, *c1_rIter = 40;
   // (below) would be an error
   //list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_rIter = c1.rbegin( );
   cout << "The last element in the list is " << *c1_rIter << "." << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration through a list in
   // reverse order
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rbegin( );
*c1_rIter = 40;
   cout << "The last element in the list is now " << *c1_rIter << "." << endl;
}
```

```Output
The last element in the list is 30.
The list is: 10 20 30
The reversed list is: 30 20 10
The last element in the list is now 40.
```

## <a name="reference"></a>odwoła

Typ, który zawiera odwołanie do elementu przechowywanego na liście.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Przykład

```cpp
// list_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="remove"></a>usuwa

Wymazuje elementy znajdujące się na liście, które pasują do określonej wartości.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Parametry

*val* \
Wartość, która, jeśli jest przechowywana przez element, spowoduje usunięcie tego elementu z listy.

### <a name="remarks"></a>Uwagi

Nie ma to oddziaływać na kolejność pozostałych elementów.

### <a name="example"></a>Przykład

```cpp
// list_remove.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 5 );
   c1.push_back( 100 );
   c1.push_back( 5 );
   c1.push_back( 200 );
   c1.push_back( 5 );
   c1.push_back( 300 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove( 5 );
   cout << "After removing elements with value 5, the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 5 100 5 200 5 300
After removing elements with value 5, the list becomes c2 = 100 200 300
```

## <a name="remove_if"></a>remove_if

Usuwa elementy z listy, dla których jest spełniony określony predykat.

```cpp
template <class Predicate>
void remove_if(Predicate pred)
```

### <a name="parameters"></a>Parametry

*pred* \
Predykat jednoargumentowy, który, jeśli jest spełniony przez element, powoduje usunięcie tego elementu z listy.

### <a name="example"></a>Przykład

```cpp
// list_remove_if.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

template <class T> class is_odd : public std::unary_function<T, bool>
{
public:
   bool operator( ) ( T& val )
   {
   return ( val % 2 ) == 1;
   }
};

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 3 );
   c1.push_back( 4 );
   c1.push_back( 5 );
   c1.push_back( 6 );
   c1.push_back( 7 );
   c1.push_back( 8 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove_if( is_odd<int>( ) );

   cout << "After removing the odd elements, "
        << "the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 3 4 5 6 7 8
After removing the odd elements, the list becomes c2 = 4 6 8
```

## <a name="rend"></a>rend

Zwraca iterator, który odnosi się do lokalizacji, która następuje po ostatnim elemencie na liście odwróconej.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie na liście odwróconej (lokalizacja, która poprzedza pierwszy element na liście nieodwróconej).

### <a name="remarks"></a>Uwagi

`rend` jest używany z odwróconą listą, tak jak [koniec](#end) jest używany z listą.

Jeśli wartość zwracana `rend` jest przypisana do `const_reverse_iterator`, nie można zmodyfikować obiektu listy. Jeśli wartość zwracana `rend` jest przypisana do `reverse_iterator`, można zmodyfikować obiekt listy.

`rend` można użyć do przetestowania, czy iterator odwrotny osiągnął koniec listy.

Nie należy wywoływać wartości zwracanej przez `rend`.

### <a name="example"></a>Przykład

```cpp
// list_rend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error would
   // have resulted in the line modifying an element (commented below)
   // because the iterator would have been const
   // list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_rIter << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rend can be used to test if an iteration is through all of the
   // elements of a reversed list
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--;  // Decrementing the reverse iterator moves it backward
                // in the reversed list (to the last element here)

*c1_rIter = 40;  // This modification of the last element would have
                    // caused an error if a const_reverse iterator had
                    // been declared (as noted above)

   cout << "The modified reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;
}
```

```Output
The first element in the list is: 10
The list is: 10 20 30
The reversed list is: 30 20 10
The modified reversed list is: 30 20 40
```

## <a name="resize"></a>Zmień rozmiar

Określa nowy rozmiar listy.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Parametry

*_Newsize* \
Nowy rozmiar listy.

*val* \
Wartość nowych elementów, które mają zostać dodane do listy, jeśli nowy rozmiar jest większy niż rozmiar oryginalny. W przypadku pominięcia wartości nowe elementy są przypisywane do wartości domyślnej klasy.

### <a name="remarks"></a>Uwagi

Jeśli rozmiar listy jest mniejszy niż żądany rozmiar, *_Newsize*, elementy są dodawane do listy do momentu osiągnięcia żądanego rozmiaru.

Jeśli rozmiar listy jest większy niż żądany rozmiar, elementy znajdujące się najbliżej końca listy są usuwane, dopóki lista osiągnie rozmiar *_Newsize*.

Jeśli obecny rozmiar listy jest taki sam jak żądany rozmiar, nie jest podejmowana żadna akcja.

[rozmiar](#size) odzwierciedla bieżący rozmiar listy.

### <a name="example"></a>Przykład

```cpp
// list_resize.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is 4
The value of the last element is 40
The size of c1 is now 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse"></a>cofnięci

Odwraca kolejność elementów na liście.

```cpp
void reverse();
```

### <a name="example"></a>Przykład

```cpp
// list_reverse.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.reverse( );
   cout << "Reversed c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
c1 = 10 20 30
Reversed c1 = 30 20 10
```

## <a name="reverse_iterator"></a>reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element na liście odwróconej.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iteracji listy w odwrotnej.

### <a name="example"></a>Przykład

Zobacz przykład dla [rbegin](#rbegin).

## <a name="size"></a>zmienia

Zwraca liczbę elementów na liście.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość listy.

### <a name="example"></a>Przykład

```cpp
// list_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   c1.push_back( 5 );
   i = c1.size( );
   cout << "List length is " << i << "." << endl;

   c1.push_back( 7 );
   i = c1.size( );
   cout << "List length is now " << i << "." << endl;
}
```

```Output
List length is 1.
List length is now 2.
```

## <a name="size_type"></a>size_type

Typ, który zlicza liczbę elementów na liście.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [rozmiaru](#size).

## <a name="sort"></a>porządku

Rozmieszcza elementy listy w kolejności rosnącej lub w odniesieniu do innej kolejności określonej przez użytkownika.

```cpp
void sort();

template <class Traits>
    void sort(Traits comp);
```

### <a name="parameters"></a>Parametry

\ *zgodności*
Operator porównania używany do uporządkowania kolejnych elementów.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska domyślnie umieszcza elementy w kolejności rosnącej.

Funkcja szablonu elementu członkowskiego Porządkuje elementy zgodnie z określoną przez użytkownika *kompozycją* operacji porównywania klasy `Traits`.

### <a name="example"></a>Przykład

```cpp
// list_sort.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 20 );
   c1.push_back( 10 );
   c1.push_back( 30 );

   cout << "Before sorting: c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( );
   cout << "After sorting c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( greater<int>( ) );
   cout << "After sorting with 'greater than' operation, c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
Before sorting: c1 = 20 10 30
After sorting c1 = 10 20 30
After sorting with 'greater than' operation, c1 = 30 20 10
```

## <a name="splice"></a>splice

Usuwa elementy z listy źródłowej i wstawia je do listy docelowej.

```cpp
// insert the entire source list
void splice(const_iterator Where, list<Type, Allocator>& Source);
void splice(const_iterator Where, list<Type, Allocator>&& Source);

// insert one element of the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator Iter);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator Iter);

// insert a range of elements from the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator First, const_iterator Last);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator First, const_iterator Last);
```

### <a name="parameters"></a>Parametry

*Gdzie* \
Pozycja na liście docelowej przed wstawieniem.

@No__t_1 *źródłowa*
Lista źródłowa, która ma zostać wstawiona na listę docelową.

@No__t_1 *ITER*
Element, który ma zostać wstawiony z listy źródłowej.

*Pierwszy* \
Pierwszy element z zakresu, który ma zostać wstawiony z listy źródłowej.

*Ostatni* \
Pierwsza pozycja poza ostatnim elementem w zakresie, który ma zostać wstawiony z listy źródłowej.

### <a name="remarks"></a>Uwagi

Pierwsza para funkcji Członkowskich wstawia wszystkie elementy z listy źródłowej na listę docelową przed pozycją, *do której odwołuje się i usuwa* wszystkie elementy z listy źródłowej. (`&Source` nie może być równe `this`.)

Druga para funkcji Członkowskich wstawia element, do którego odnosi się *ITER* przed pozycją na liście docelowej, do której odwołuje się, *gdzie* i usuwa *ITER* z listy źródłowej. (Jeśli `Where == Iter || Where == ++Iter`, nie ma zmian).

Trzecia para funkcji Członkowskich wstawia zakres wystawiony przez [`First`, `Last`) przed elementem na liście docelowej, do którego odwołuje się, *gdzie* i usuwa ten zakres elementów z listy źródłowej. (W przypadku `&Source == this` zakres `[First, Last)` nie może zawierać elementu wskazywanego przez *WHERE*.)

Jeśli metoda łączenia w zakresie wstawia `N` elementy, a `&Source != this`, obiekt [iteratora](../standard-library/forward-list-class.md#iterator) klas jest zwiększany `N` razy.

We wszystkich przypadkach Iteratory, wskaźniki lub odwołania odwołujące się do rozmieszczonych elementów pozostają prawidłowe i są przekazywane do kontenera docelowego.

### <a name="example"></a>Przykład

```cpp
// list_splice.cpp
// compile with: /EHsc /W4
#include <list>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    list<int> c1{10,11};
    list<int> c2{20,21,22};
    list<int> c3{30,31};
    list<int> c4{40,41,42,43};

    list<int>::iterator where_iter;
    list<int>::iterator first_iter;
    list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    --last_iter;
    c2.splice(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = 2 elements: (10) (11)c2 = 3 elements: (20) (21) (22)c3 = 2 elements: (30) (31)c4 = 4 elements: (40) (41) (42) (43)After splicing c1 into c2:c1 = 0 elements:c2 = 5 elements: (20) (10) (11) (21) (22)After splicing the first element of c3 into c2:c3 = 1 elements: (31)c2 = 6 elements: (20) (10) (11) (30) (21) (22)After splicing a range of c4 into c2:c4 = 2 elements: (40) (43)c2 = 8 elements: (20) (10) (11) (30) (41) (42) (21) (22)
```

## <a name="swap"></a>wymiany

Wymienia elementy dwóch list.

```cpp
void swap(list<Type, Allocator>& right);
friend void swap(list<Type, Allocator>& left, list<Type, Allocator>& right)
```

### <a name="parameters"></a>Parametry

*prawa* \
Lista zawierająca elementy, które mają zostać zamienione, lub listę, której elementy mają być wymieniane z tymi wymienionymi na liście *po lewej stronie*.

\ *lewo*
Lista, której elementy mają być wymieniane z listami *po prawej stronie*.

### <a name="example"></a>Przykład

```cpp
// list_swap.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original list c1 is: 1 2 3
After swapping with c2, list c1 is: 10 20
After swapping with c3, list c1 is: 100
```

## <a name="unique"></a>unikatowy

Usuwa sąsiadujące zduplikowane elementy lub sąsiadujące elementy, które spełniają inny Predykat binarny z listy.

```cpp
void unique();

template <class BinaryPredicate>
void unique(BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*pred* \
Predykat binarny używany do porównywania kolejnych elementów.

### <a name="remarks"></a>Uwagi

Ta funkcja zakłada, że lista jest sortowana, dzięki czemu wszystkie zduplikowane elementy są przyległe. Duplikaty, które nie sąsiadują ze sobą, nie zostaną usunięte.

Pierwsza funkcja członkowska usuwa każdy element, który porównuje wartość równą jego poprzedzającemu elementowi.

Druga funkcja członkowska usuwa każdy element, który spełnia funkcję predykatu *pred* w porównaniu z poprzednim elementem. Można użyć dowolnego z obiektów funkcji binarnych zadeklarowanych w nagłówku \<functional > dla argumentu *pred* lub można utworzyć własny.

### <a name="example"></a>Przykład

```cpp
// list_unique.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter,c3_Iter;
   not_equal_to<int> mypred;

   c1.push_back( -10 );
   c1.push_back( 10 );
   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 20 );
   c1.push_back( -10 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.unique( );
   cout << "After removing successive duplicate elements, c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   list <int> c3 = c2;
   c3.unique( mypred );
   cout << "After removing successive unequal elements, c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = -10 10 10 20 20 -10
After removing successive duplicate elements, c2 = -10 10 20 -10
After removing successive unequal elements, c3 = -10 -10
```

## <a name="value_type"></a>value_type

Typ, który reprezentuje typ danych przechowywany na liście.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Uwagi

`value_type` jest synonimem dla *typu*parametru szablonu.

### <a name="example"></a>Przykład

```cpp
// list_value_type.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```
