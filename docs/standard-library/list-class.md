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
ms.openlocfilehash: 7e30583a185a46e5e0f0544ac2b00848dc989f26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377323"
---
# <a name="list-class"></a>list — Klasa

Klasa listy biblioteki standardowej języka C++ jest szablonem klasy kontenerów sekwencji, które utrzymują swoje elementy w układzie liniowym i umożliwiają wydajne wstawiania i usuwanie w dowolnym miejscu w sekwencji. Sekwencja jest przechowywana jako dwukierunkowa połączona lista elementów, z których każda zawiera element członkowski pewnego typu *Type*.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Allocator= allocator<Type>>
class list
```

### <a name="parameters"></a>Parametry

*Typu*\
Typ danych elementu, który ma być przechowywany na liście.

*Programu przydzielania*\
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji listy i alokacji pamięci. Ten argument jest opcjonalny, a wartością domyślną jest **typ> alokatora.**\<*Type*

## <a name="remarks"></a>Uwagi

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Wektory powinny być preferowanym kontenerem do zarządzania sekwencją, gdy losowy dostęp do dowolnego elementu jest na poziomie premium, a wstawienia lub usunięcia elementów są wymagane tylko na końcu sekwencji. Wydajność kontenera deque klasy jest lepsza, gdy wymagany jest dostęp losowy, a wstawienia i usunięcia na początku i na końcu sekwencji są na poziomie premium.

Funkcje członkowskie listy [łączą się,](#merge) [odwrotnie,](#reverse) [unikatowe,](#unique) [usuwaj](#remove)i [remove_if](#remove_if) zostały zoptymalizowane pod kątem działania na obiektach listy i oferują wysoką wydajność alternatywy dla ich ogólnych odpowiedników.

Ponowne przydzielanie listy występuje, gdy funkcja elementu członkowskiego musi wstawić lub wymazać elementy listy. We wszystkich takich przypadkach tylko iteratory lub odwołania, które wskazują na wymazane części kontrolowanej sekwencji stają się nieważne.

Dołącz standardową listę nagłówków \<biblioteki standardowej języka C++>, aby zdefiniować listę szablonów klas [kontenera](../standard-library/stl-containers.md) i kilka szablonów pomocniczych.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[list](#list)|Tworzy listę określonego rozmiaru lub z elementami określonej wartości `allocator` lub z określoną lub jako kopię innej listy.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|Typ reprezentujący `allocator` klasę obiektu listy.|
|[const_iterator](#const_iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytać **const** element na liście.|
|[const_pointer](#const_pointer)|Typ, który zapewnia wskaźnik do **const** elementu na liście.|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do **const** element przechowywane na liście do odczytu i wykonywania operacji **const.**|
|[Const_reverse_iterator](#const_reverse_iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytać dowolny element **const** na liście.|
|[difference_type](#difference_type)|Typ, który zapewnia różnicę między dwoma iteratorami, które odwołują się do elementów w tej samej liście.|
|[Sterująca](#iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować dowolny element na liście.|
|[pointer](#pointer)|Typ, który udostępnia wskaźnik do elementu na liście.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do **const** element przechowywane na liście do odczytu i wykonywania operacji **const.**|
|[Reverse_iterator](#reverse_iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować element na odwróconej liście.|
|[size_type](#size_type)|Typ, który zlicza liczbę elementów na liście.|
|[value_type](#value_type)|Typ reprezentujący typ danych przechowywany na liście.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[Przypisać](#assign)|Usuwa elementy z listy i kopiuje nowy zestaw elementów do listy docelowej.|
|[Wstecz](#back)|Zwraca odwołanie do ostatniego elementu listy.|
|[Rozpocząć](#begin)|Zwraca iterator adresowania pierwszy element na liście.|
|[cbegin ( cbegin )](#cbegin)|Zwraca iterator konstacyjny adresowania pierwszy element na liście.|
|[cend](#cend)|Zwraca iterator konstacyjny, który odnosi się do lokalizacji, która zastępuje ostatni element na liście.|
|[Wyczyść](#clear)|Wymazywanie wszystkich elementów listy.|
|[Crbegin](#crbegin)|Zwraca iterator konstacyjny adresowania pierwszy element na liście odwróconych.|
|[Crend](#crend)|Zwraca iterator konspiratora, który odnosi się do lokalizacji, która zastępuje ostatni element na odwróconej liście.|
|[miejsce](#emplace)|Wstawia element skonstruowany w miejscu do listy w określonym położeniu.|
|[emplace_back](#emplace_back)|Dodaje element skonstruowany w miejscu na końcu listy.|
|[emplace_front](#emplace_front)|Dodaje element skonstruowany w miejscu na początku listy.|
|[Pusty](#empty)|Sprawdza, czy lista jest pusta.|
|[Końcu](#end)|Zwraca iterator, który odnosi się do lokalizacji, która zastępuje ostatni element na liście.|
|[Wymazać](#erase)|Usuwa element lub zakres elementów na liście z określonych pozycji.|
|[Przednie](#front)|Zwraca odwołanie do pierwszego elementu na liście.|
|[Get_allocator](#get_allocator)|Zwraca kopię obiektu `allocator` używanego do konstruowania listy.|
|[Wstawić](#insert)|Wstawia element lub liczbę elementów lub zakres elementów do listy w określonym położeniu.|
|[Max_size](#max_size)|Zwraca maksymalną długość listy.|
|[Scalania](#merge)|Usuwa elementy z listy argumentów, wstawia je do listy docelowej i porządkuje nowy, połączony zestaw elementów w porządku rosnącym lub w innej określonej kolejności.|
|[pop_back](#pop_back)|Usuwa element na końcu listy.|
|[pop_front](#pop_front)|Usuwa element na początku listy.|
|[push_back](#push_back)|Dodaje element na końcu listy.|
|[push_front](#push_front)|Dodaje element na początku listy.|
|[rbegin (rbegin)](#rbegin)|Zwraca iterator adresowania pierwszy element na liście odwróconych.|
|[remove](#remove)|Usuwa elementy na liście, które pasują do określonej wartości.|
|[remove_if](#remove_if)|Usuwa elementy z listy, dla których określony predykat jest spełniony.|
|[Rend](#rend)|Zwraca iterator, który odnosi się do lokalizacji, która zastępuje ostatni element na odwróconej liście.|
|[Zmienić rozmiar](#resize)|Określa nowy rozmiar listy.|
|[Odwrócić](#reverse)|Odwraca kolejność, w jakiej występują elementy na liście.|
|[Rozmiar](#size)|Zwraca liczbę elementów na liście.|
|[Sortowania](#sort)|Rozmieszcza elementy listy w porządku rosnącym lub w odniesieniu do innej relacji zamówienia.|
|[splice](#splice)|Usuwa elementy z listy argumentów i wstawia je do listy docelowej.|
|[Wymiany](#swap)|Wymienia elementy dwóch list.|
|[Unikatowy](#unique)|Usuwa sąsiednie zduplikowane elementy lub sąsiednie elementy, które spełniają niektóre inne predykatu binarnego z listy.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator=](#op_eq)|Zastępuje elementy listy kopią innej listy.|

## <a name="requirements"></a>Wymagania

**Nagłówek** \<: lista>

## <a name="allocator_type"></a><a name="allocator_type"></a>allocator_type

Typ reprezentujący klasę alokatora dla obiektu listy.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type`jest synonimem parametru szablonu *Alokator .*

### <a name="example"></a>Przykład

Zobacz przykład [get_allocator](#get_allocator).

## <a name="assign"></a><a name="assign"></a>Przypisać

Wymazywanie elementów z listy i kopiowanie nowego zestawu elementów do listy docelowej.

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

*Pierwszym*\
Położenie pierwszego elementu w zakresie elementów, które mają zostać skopiowane z listy argumentów.

*Ostatnio*\
Położenie pierwszego elementu tuż poza zakresem elementów, które mają zostać skopiowane z listy argumentów.

*Liczba*\
Liczba kopii elementu wstawianego do listy.

*Val*\
Wartość elementu wstawianego do listy.

*Ilist*\
initializer_list, który zawiera elementy, które mają zostać wstawione.

### <a name="remarks"></a>Uwagi

Po wymazaniu istniejących elementów na liście docelowej, przypisz do listy docelowej określony zakres elementów z oryginalnej listy lub z innej listy lub wstawia kopie nowego elementu o określonej wartości.

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

## <a name="back"></a><a name="back"></a>Wstecz

Zwraca odwołanie do ostatniego elementu listy.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Ostatni element listy. Jeśli lista jest pusta, zwracana wartość jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli zwracana `back` wartość jest przypisana `const_reference`do obiektu , nie można zmodyfikować obiektu listy. Jeśli zwracana `back` wartość jest przypisana `reference`do , obiekt listy może być modyfikowany.

Podczas kompilowania przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowane jako 1 lub 2, błąd środowiska uruchomieniowego wystąpi, jeśli spróbujesz uzyskać dostęp do elementu na pustej liście.  Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów.](../standard-library/checked-iterators.md)

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

## <a name="begin"></a><a name="begin"></a>Rozpocząć

Zwraca iterator adresowania pierwszy element na liście.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator adresowania pierwszy element na liście lub lokalizacji po pomyślnym pustej listy.

### <a name="remarks"></a>Uwagi

Jeśli zwracana `begin` wartość jest przypisana `const_iterator`do , elementy w obiekcie listy nie mogą być modyfikowane. Jeśli zwracana `begin` wartość jest przypisana `iterator`do , elementy w obiekcie listy mogą być modyfikowane.

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

## <a name="cbegin"></a><a name="cbegin"></a>cbegin ( cbegin )

Zwraca **iterator konspiratora,** który odnosi się do pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

**Dwukierunkowy** iterator dostępu dwukierunkowego, który wskazuje pierwszy element zakresu lub lokalizację tuż za końcem pustego zakresu `cbegin() == cend()`(dla pustego zakresu).

### <a name="remarks"></a>Uwagi

Z wartością `cbegin`zwracaną , elementy w zakresie nie mogą być modyfikowane.

Tej funkcji elementu członkowskiego można `begin()` użyć zamiast funkcji elementu członkowskiego, aby zagwarantować, że zwracana jest `const_iterator`wartość . Zazwyczaj jest on używany w połączeniu ze słowem kluczowym [auto](../cpp/auto-cpp.md) odliczanie typu, jak pokazano w poniższym przykładzie. W przykładzie `Container` należy wziąć pod uwagę modyfikowalne (non-const) kontener wszelkiego rodzaju, który obsługuje **const** `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a>cend

Zwraca `const` iterator, który odnosi się do lokalizacji tuż poza ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy `const` iterator dostępu, który wskazuje tuż za końcem zakresu.

### <a name="remarks"></a>Uwagi

`cend`służy do testowania, czy iterator przeszedł koniec jego zakresu.

Tej funkcji elementu członkowskiego można `end()` użyć zamiast funkcji elementu członkowskiego, aby zagwarantować, że zwracana jest `const_iterator`wartość . Zazwyczaj jest on używany w połączeniu ze słowem kluczowym [auto](../cpp/auto-cpp.md) odliczanie typu, jak pokazano w poniższym przykładzie. W przykładzie `Container` należy wziąć pod uwagę modyfikowalne (non-const) kontener wszelkiego rodzaju, który obsługuje **const** `end()` i `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Wartość zwrócona `cend` przez nie powinny być wyłuskiwane.

## <a name="clear"></a><a name="clear"></a>Wyczyść

Wymazywanie wszystkich elementów listy.

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

## <a name="const_iterator"></a><a name="const_iterator"></a>Const_iterator

Typ, który zapewnia dwukierunkowy iterator, który może odczytać **const** element na liście.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [z powrotem](#back).

## <a name="const_pointer"></a><a name="const_pointer"></a>const_pointer

Udostępnia wskaźnik do **const** elementu na liście.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien służyć do uzyskiwania dostępu do elementów w obiekcie listy.

## <a name="const_reference"></a><a name="const_reference"></a>Const_reference

Typ, który zawiera odwołanie do **const** element przechowywane na liście do odczytu i wykonywania operacji **const.**

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

Typ `const_reference` nie może służyć do modyfikowania wartości elementu.

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

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a>Const_reverse_iterator

Typ, który zapewnia dwukierunkowy iterator, który może odczytać dowolny element **const** na liście.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartość elementu i jest używany do iteracji za pośrednictwem listy w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład [dla rbegin](#rbegin).

## <a name="crbegin"></a><a name="crbegin"></a>Crbegin

Zwraca iterator konstacyjny adresowania pierwszy element na liście odwróconych.

```cpp
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Const odwrotnej dwukierunkowej iteratora adresowania pierwszego elementu na liście odwróconych (lub adresowania, `list`co było ostatnim elementem w nieodwrotowej ).

### <a name="remarks"></a>Uwagi

`crbegin`jest używany z odwróconą listą tak jak `list` [lista::begin](#begin) jest używana z .

Z wartością `crbegin`zwracaną obiektu listy nie można modyfikować obiektu listy. [lista::rbegin](#rbegin) może służyć do iteracji za pośrednictwem listy do tyłu.

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

## <a name="crend"></a><a name="crend"></a>Crend

Zwraca iterator konspiratora, który odnosi się do lokalizacji, która zastępuje ostatni element na odwróconej liście.

```cpp
const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Wartość zwracana

Const odwrotnej dwukierunkowej iteratora, który odnosi się do lokalizacji po ostatnim elemencie na [liście](../standard-library/list-class.md) `list`odwróconych (lokalizacja, która poprzedziła pierwszy element w nieodwrotowej ).

### <a name="remarks"></a>Uwagi

`crend`jest używany z odwróconą listą tak jak `list` [lista::end](#end) jest używany z .

Z wartością `crend`zwracaną `list` obiektu nie można modyfikować obiektu.

`crend`można użyć do sprawdzenia, czy iterator odwrotny `list`osiągnął koniec jego .

Wartość zwrócona `crend` przez nie powinny być wyłuskiwane.

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

## <a name="difference_type"></a><a name="difference_type"></a>difference_type

Typ liczby całkowitej podpisana, który może służyć do reprezentowania liczby elementów listy w zakresie między elementami wskazywane przez iteratory.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Jest `difference_type` to typ zwracany podczas odejmowania lub zwiększania za pośrednictwem iteratorów kontenera. Jest `difference_type` zazwyczaj używany do reprezentowania liczby elementów `first` `last`w zakresie [ , `first` `last`) między iteratorów i , zawiera element wskazany przez `first` i `last`zakres elementów do, ale nie w tym element wskazany przez .

Należy zauważyć, że chociaż `difference_type` jest dostępny dla wszystkich iteratorów, które spełniają wymagania iteratora wejściowego, który obejmuje klasę dwukierunkowych iteratorów obsługiwanych przez odwracalne kontenery, takie jak zestaw, odejmowanie między iteratorami jest obsługiwane tylko przez iteratory dostępu losowego dostarczane przez kontener dostępu losowego, takie jak klasa [wektorowa](../standard-library/vector-class.md).

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

## <a name="emplace"></a><a name="emplace"></a>miejsce

Wstawia element skonstruowany w miejscu do listy w określonym położeniu.

```cpp
void emplace(iterator Where, Type&& val);
```

### <a name="parameters"></a>Parametry

*Gdzie*\
Pozycja na [liście](../standard-library/list-class.md) docelowej, w której jest wstawiany pierwszy element.

*Val*\
Element dodany na końcu `list`.

### <a name="remarks"></a>Uwagi

Jeśli wyjątek, `list` pozostaje bez ekwiwalom i wyjątek jest rethrown.

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

## <a name="emplace_back"></a><a name="emplace_back"></a>emplace_back

Dodaje element skonstruowany w miejscu na końcu listy.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Element dodany na końcu [listy](../standard-library/list-class.md).

### <a name="remarks"></a>Uwagi

Jeśli wyjątek, `list` pozostaje bez ekwiwalom i wyjątek jest rethrown.

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

## <a name="emplace_front"></a><a name="emplace_front"></a>emplace_front

Dodaje element skonstruowany w miejscu na początku listy.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Element dodany na początku [listy](../standard-library/list-class.md).

### <a name="remarks"></a>Uwagi

Jeśli wyjątek, `list` pozostaje bez ekwiwalom i wyjątek jest rethrown.

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

## <a name="empty"></a><a name="empty"></a>Pusty

Sprawdza, czy lista jest pusta.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli lista jest pusta; **false,** jeśli lista nie jest pusta.

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

## <a name="end"></a><a name="end"></a>Końcu

Zwraca iterator, który odnosi się do lokalizacji, która zastępuje ostatni element na liście.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator, który odnosi się do lokalizacji po pomyślnym ostatniego elementu na liście. Jeśli lista jest pusta, to `list::end == list::begin`.

### <a name="remarks"></a>Uwagi

`end`służy do testowania, czy iterator osiągnął koniec swojej listy.

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

## <a name="erase"></a><a name="erase"></a>Wymazać

Usuwa element lub zakres elementów na liście z określonych pozycji.

```cpp
iterator erase(iterator Where);
iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Parametry

*Gdzie*\
Położenie elementu, który ma zostać usunięty z listy.

*Pierwszym*\
Położenie pierwszego elementu usunięte z listy.

*Ostatnio*\
Pozycja tuż za ostatnim elementem usunięte z listy.

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator, który wyznacza pierwszy element pozostałych poza wszystkie elementy usunięte lub wskaźnik na końcu listy, jeśli taki element nie istnieje.

### <a name="remarks"></a>Uwagi

Nie występuje ponownelokalizacja, więc iteratory i odwołania stają się nieprawidłowe tylko dla usuniętych elementów.

`erase`nigdy nie zgłasza wyjątku.

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

## <a name="front"></a><a name="front"></a>Przednie

Zwraca odwołanie do pierwszego elementu na liście.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest pusta, zwrot jest niezdefiniowany.

### <a name="remarks"></a>Uwagi

Jeśli zwracana `front` wartość jest przypisana `const_reference`do obiektu , nie można zmodyfikować obiektu listy. Jeśli zwracana `front` wartość jest przypisana `reference`do , obiekt listy może być modyfikowany.

Podczas kompilowania przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowane jako 1 lub 2, błąd środowiska uruchomieniowego wystąpi, jeśli spróbujesz uzyskać dostęp do elementu na pustej liście.  Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów.](../standard-library/checked-iterators.md)

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

## <a name="get_allocator"></a><a name="get_allocator"></a>Get_allocator

Zwraca kopię obiektu alokatora używanego do konstruowania listy.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez listę.

### <a name="remarks"></a>Uwagi

Alokatory dla klasy listy określają sposób zarządzania magazynem przez klasę. Domyślne alokatory dostarczane z klasami kontenerów biblioteki standardowej języka C++ są wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym tematem języka C++.

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

## <a name="insert"></a><a name="insert"></a>Wstawić

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

*Gdzie*\
Pozycja na liście docelowej, w której jest wstawiany pierwszy element.

*Val*\
Wartość elementu wstawianego do listy.

*Liczba*\
Liczba elementów wstawianych do listy.

*Pierwszym*\
Położenie pierwszego elementu w zakresie elementów na liście argumentów do skopiowania.

*Ostatnio*\
Położenie pierwszego elementu poza zakresem elementów na liście argumentów do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie funkcje wstawiania zwracają iteratora, który wskazuje pozycję, w której nowy element został wstawiony do listy.

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

## <a name="iterator"></a><a name="iterator"></a>Sterująca

Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować dowolny element na liście.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpoczęcia](#begin).

## <a name="list"></a><a name="list"></a>Listy

Tworzy listę określonego rozmiaru lub z elementami określonej wartości lub z określonego alokatora lub jako kopię całości lub części innej listy.

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

*Al*\
Klasa alokatora do wykorzystania z tym obiektem.

*Liczba*\
Liczba elementów na liście skonstruowane.

*Val*\
Wartość elementów na liście.

*Prawo*\
Lista, której skonstruowana lista ma być kopią.

*Pierwszym*\
Położenie pierwszego elementu w zakresie elementów do skopiowania.

*Ostatnio*\
Położenie pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

*Ilist*\
initializer_list, który zawiera elementy do skopiowania.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują obiekt alokatora *(Al)* i inicjują listę.

[get_allocator](#get_allocator) zwraca kopię obiektu alokatora używanego do konstruowania listy.

Pierwsze dwa konstruktory określają pustą listę początkową, drugą określającą typ alokatora (*Al*), który ma być używany.

Trzeci konstruktor określa powtórzenie określonej liczby (*Liczba*) elementów `Type`wartości domyślnej dla klasy .

Konstruktory czwarty i piąty określają powtórzenie *(Count*) elementów wartości *Val*.

Szósty konstruktor określa kopię listy *Right*.

Siódmy konstruktor przesuwa listę *Right*.

Ósmy konstruktor używa initializer_list do określenia elementów.

Następne dwa konstruktory `[First, Last)` kopiują zakres listy.

Żaden z konstruktorów wykonać żadnych tymczasowych realokacji.

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

## <a name="max_size"></a><a name="max_size"></a>Max_size

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

## <a name="merge"></a><a name="merge"></a>Scalania

Usuwa elementy z listy argumentów, wstawia je do listy docelowej i porządkuje nowy, połączony zestaw elementów w porządku rosnącym lub w innej określonej kolejności.

```cpp
void merge(list<Type, Allocator>& right);

template <class Traits>
void merge(list<Type, Allocator>& right, Traits comp);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Lista argumentów, które mają zostać scalone z listą docelową.

*Komp*\
Operator porównania używany do zamawiania elementów listy docelowej.

### <a name="remarks"></a>Uwagi

Prawo *do* listy argumentów jest scalane z listą docelową.

Zarówno argument i listy docelowe muszą być uporządkowane z taką samą relacją porównania, za pomocą której ma zostać uporządkowana wynikowa sekwencja. Domyślna kolejność dla pierwszej funkcji elementu członkowskiego jest rosnąca. Druga funkcja elementu członkowskiego nakłada *na* użytkownika komp `Traits`operacji porównania określonej przez użytkownika .

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

## <a name="operator"></a><a name="op_eq"></a>operator=

Zastępuje elementy listy kopią innej listy.

```cpp
list& operator=(const list& right);
list& operator=(list&& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
[Lista](../standard-library/list-class.md) kopiowana do `list`pliku .

### <a name="remarks"></a>Uwagi

Po wymazaniu istniejących elementów `list`w programie operator kopiuje lub przenosi `list`zawartość w *prawo* do pliku .

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

## <a name="pointer"></a><a name="pointer"></a>Wskaźnik

Zawiera wskaźnik do elementu na liście.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien służyć do uzyskiwania dostępu do elementów w obiekcie listy.

## <a name="pop_back"></a><a name="pop_back"></a>pop_back

Usuwa element na końcu listy.

```cpp
void pop_back();
```

### <a name="remarks"></a>Uwagi

Ostatni element nie może być pusty. `pop_back`nigdy nie zgłasza wyjątku.

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

## <a name="pop_front"></a><a name="pop_front"></a>pop_front

Usuwa element na początku listy.

```cpp
void pop_front();
```

### <a name="remarks"></a>Uwagi

Pierwszy element nie może być pusty. `pop_front`nigdy nie zgłasza wyjątku.

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

## <a name="push_back"></a><a name="push_back"></a>push_back

Dodaje element na końcu listy.

```cpp
void push_back(const Type& val);
void push_back(Type&& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Element dodany na końcu listy.

### <a name="remarks"></a>Uwagi

Jeśli wyjątek, lista pozostaje bez ńska i wyjątek jest rethrown.

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

## <a name="push_front"></a><a name="push_front"></a>push_front

Dodaje element na początku listy.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Element dodany na początku listy.

### <a name="remarks"></a>Uwagi

Jeśli wyjątek, lista pozostaje bez ńska i wyjątek jest rethrown.

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

## <a name="rbegin"></a><a name="rbegin"></a>rbegin (rbegin)

Zwraca iterator, który odnosi się do pierwszego elementu na odwróconej liście.

```cpp
const_reverse_iterator rbegin() const;
reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnej dwukierunkowej iterator adresowania pierwszy element na liście odwróconych (lub adresowania, co było ostatnim elementem na liście niewersygnowane).

### <a name="remarks"></a>Uwagi

`rbegin`jest używany z odwróconą listą, tak jak [begin](#begin) jest używany z listą.

Jeśli zwracana `rbegin` wartość jest przypisana `const_reverse_iterator`do obiektu , nie można zmodyfikować obiektu listy. Jeśli zwracana `rbegin` wartość jest przypisana `reverse_iterator`do , obiekt listy może być modyfikowany.

`rbegin`można iterować za pośrednictwem listy do tyłu.

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

## <a name="reference"></a><a name="reference"></a>Odwołanie

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

## <a name="remove"></a><a name="remove"></a>Usunąć

Usuwa elementy na liście, które pasują do określonej wartości.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Wartość, która, jeśli jest utrzymywana przez element, spowoduje usunięcie tego elementu z listy.

### <a name="remarks"></a>Uwagi

Kolejność pozostałych elementów nie ma wpływu.

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

## <a name="remove_if"></a><a name="remove_if"></a>remove_if

Usuwa elementy z listy, dla których określony predykat jest spełniony.

```cpp
template <class Predicate>
void remove_if(Predicate pred)
```

### <a name="parameters"></a>Parametry

*pred*\
Predykat jednoznaczny, który, jeśli zostanie spełniony przez element, powoduje usunięcie tego elementu z listy.

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

## <a name="rend"></a><a name="rend"></a>Rend

Zwraca iterator, który odnosi się do lokalizacji, która następuje po ostatnim elemencie na liście odwróconych.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnej dwukierunkowej iteratora, który odnosi się do lokalizacji po ostatniej pozycji elementu na liście odwróconych (lokalizacja, która poprzedziła pierwszy element na liście nieodwrotowej).

### <a name="remarks"></a>Uwagi

`rend`jest używany z odwróconą listą, tak jak [koniec](#end) jest używany z listą.

Jeśli zwracana `rend` wartość jest przypisana `const_reverse_iterator`do obiektu , nie można zmodyfikować obiektu listy. Jeśli zwracana `rend` wartość jest przypisana `reverse_iterator`do , obiekt listy może być modyfikowany.

`rend`można użyć do sprawdzenia, czy odwrotny iterator osiągnął koniec swojej listy.

Wartość zwrócona `rend` przez nie powinny być wyłuskiwane.

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

## <a name="resize"></a><a name="resize"></a>Zmienić rozmiar

Określa nowy rozmiar listy.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Parametry

*_Newsize*\
Nowy rozmiar listy.

*Val*\
Wartość nowych elementów, które mają zostać dodane do listy, jeśli nowy rozmiar jest większy niż oryginalny rozmiar. Jeśli wartość zostanie pominięta, nowe elementy są przypisywane wartość domyślną dla klasy.

### <a name="remarks"></a>Uwagi

Jeśli rozmiar listy jest mniejszy niż żądany rozmiar, *_Newsize*, elementy są dodawane do listy, dopóki nie osiągnie żądanego rozmiaru.

Jeśli rozmiar listy jest większy niż żądany rozmiar, elementy najbliżej końca listy są usuwane, dopóki lista nie osiągnie rozmiaru *_Newsize*.

Jeśli obecny rozmiar listy jest taki sam jak żądany rozmiar, nie są podejmowane żadne działania.

[odzwierciedla](#size) bieżący rozmiar listy.

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

## <a name="reverse"></a><a name="reverse"></a>Odwrócić

Odwraca kolejność, w jakiej występują elementy na liście.

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

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a>Reverse_iterator

Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować element na odwróconej liście.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iteracji za pośrednictwem listy w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład [dla rbegin](#rbegin).

## <a name="size"></a><a name="size"></a>Rozmiar

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

## <a name="size_type"></a><a name="size_type"></a>Size_type

Typ, który zlicza liczbę elementów na liście.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [rozmiaru](#size).

## <a name="sort"></a><a name="sort"></a>Sortowania

Rozmieszcza elementy listy w porządku rosnącym lub w odniesieniu do innej kolejności określonej przez użytkownika.

```cpp
void sort();

template <class Traits>
    void sort(Traits comp);
```

### <a name="parameters"></a>Parametry

*Komp*\
Operator porównania używany do zamawiania kolejnych elementów.

### <a name="remarks"></a>Uwagi

Funkcja pierwszego elementu członkowskiego domyślnie umieszcza elementy w porządku rosnącym.

Funkcja szablonu elementu członkowskiego porządkuuje elementy zgodnie z `Traits` *kompem* operacji porównania określonej przez użytkownika klasy .

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

## <a name="splice"></a><a name="splice"></a>splice

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

*Gdzie*\
Pozycja na liście docelowej, przed którą należy wstawić.

*Źródła*\
Lista źródłowsza, która ma zostać wstawiona do listy docelowej.

*Iter*\
Element, który ma zostać wstawiony z listy źródłowej.

*Pierwszym*\
Pierwszy element w zakresie, który ma zostać wstawiony z listy źródłowej.

*Ostatnio*\
Pierwsza pozycja poza ostatnim elementem w zakresie, który ma zostać wstawiony z listy źródłowej.

### <a name="remarks"></a>Uwagi

Pierwsza para funkcji elementów członkowskich wstawia wszystkie elementy na liście źródłowej do listy docelowej przed stanowiskiem, o którym mowa *w where* i usuwa wszystkie elementy z listy źródłowej. (`&Source` nie `this`może być równa .)

Druga para funkcji elementów członkowskich wstawia element, o którym mowa przez *iter* przed pozycją na liście docelowej, o której mowa *w Where* i usuwa *iter* z listy źródłowej. (Jeśli `Where == Iter || Where == ++Iter`nie nastąpi żadna zmiana).

Trzecia para funkcji elementów członkowskich wstawia `First` `Last`zakres wyznaczony przez [ , ) przed elementem na liście docelowej, o której mowa *w Where* i usuwa ten zakres elementów z listy źródłowej. (Jeżeli `&Source == this`, `[First, Last)` zakres nie może zawierać elementu wskazanego przez *Where*.)

Jeśli splice wahała `N` wstawia `&Source != this`elementy i , obiekt [iteratora](../standard-library/forward-list-class.md#iterator) klasy jest przyrostowe `N` razy.

We wszystkich przypadkach iteratory, wskaźniki lub odwołania, które odwołują się do elementów spliced pozostają prawidłowe i są przenoszone do kontenera docelowego.

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

## <a name="swap"></a><a name="swap"></a>Wymiany

Wymienia elementy dwóch list.

```cpp
void swap(list<Type, Allocator>& right);
friend void swap(list<Type, Allocator>& left, list<Type, Allocator>& right)
```

### <a name="parameters"></a>Parametry

*Prawo*\
Lista zawierająca elementy, które mają zostać zamienione, lub lista, której elementy mają być wymieniane z elementami *listy, pozostała*.

*Lewej*\
Lista, której elementy mają być wymieniane z elementami *listy po prawej stronie*.

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

## <a name="unique"></a><a name="unique"></a>Unikatowy

Usuwa sąsiednie zduplikowane elementy lub sąsiednie elementy, które spełniają niektóre inne predykatu binarnego z listy.

```cpp
void unique();

template <class BinaryPredicate>
void unique(BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*pred*\
Predykat binarny używany do porównywania kolejnych elementów.

### <a name="remarks"></a>Uwagi

Ta funkcja zakłada, że lista jest sortowana, tak aby wszystkie zduplikowane elementy sąsiadują. Duplikaty, które nie sąsiadują, nie zostaną usunięte.

Funkcja pierwszego elementu członkowskiego usuwa każdy element, który porównuje się równy jego poprzedni element.

Funkcja drugiego elementu członkowskiego usuwa każdy element, który spełnia funkcję predykatu *poprzedzaną* w porównaniu z jego poprzednim elementem. Można użyć dowolnego z obiektów funkcji \<binarnych zadeklarowanych w nagłówku> funkcjonalnego dla argumentu *pred* lub można utworzyć własne.

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

## <a name="value_type"></a><a name="value_type"></a>Value_type

Typ reprezentujący typ danych przechowywany na liście.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Uwagi

`value_type`jest synonimem parametru szablonu *Typ*.

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
