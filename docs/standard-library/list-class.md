---
title: list — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86e1c74d3aa53dd64a48676e4fe9bdbc2065b9c5
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107493"
---
# <a name="list-class"></a>list — Klasa

Klasa listy standardowej biblioteki języka C++ jest klasą szablonu, kontenerów sekwencji, obsługa ich elementy w układzie liniowych, które umożliwia wydajne wstawienia i usunięcia w dowolnym miejscu w sekwencji. Sekwencja jest przechowywany jako dwukierunkowy połączonej listy elementów, każdy z nich zawierający członkiem pewnego typu *typu*.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Allocator= allocator<Type>>
class list
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Typ danych elementu mają być przechowywane na liście.

*Allocator*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i dezalokacji pamięci listy. Ten argument jest opcjonalny, a wartość domyślna to **alokatora**\<*typu*>.

## <a name="remarks"></a>Uwagi

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Wektory powinny być preferowane kontenera do zarządzania sekwencji, gdy jest losowe do dowolnego elementu w warstwie premium i wstawienia i usunięcia elementów tylko wymagane na końcu sekwencji. Wydajność kontenera deque — klasa jest przełożonego, gdy wymagany jest dostęp losowy i wstawienia i usunięcia na początku i na końcu sekwencji w warstwie premium.

Funkcje elementów członkowskich listy [scalania](#merge), [odwrotnej](#reverse), [unikatowy](#unique), [Usuń](#remove), i [remove_if —](#remove_if) zostały zoptymalizowane pod kątem operacji na listę obiektów i oferty o wysokiej wydajności alternatywa ich odpowiedniki ogólnego.

Ponowne przydzielenie listy występuje, gdy składowa należy wstawić taśmie ani wymazać elementy listy. W takich przypadkach jedynym Iteratory lub odwołania, które wskazują na usuwane części kontrolowanej sekwencji stają się nieprawidłowe.

Dołączyć standardowy nagłówek biblioteki standardowej języka C++ \<listy > do definiowania [kontenera](../standard-library/stl-containers.md) szablonu listy klas i kilka szablonów pomocniczych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[list](#list)|Tworzy listę o określonym rozmiarze lub z elementami określonej wartości lub z określonego `allocator` lub jako kopię niektórych innych list.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje `allocator` klasy dla obiektu listy.|
|[const_iterator](#const_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać **const** element na liście.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do **const** element na liście.|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do **const** element przechowywane na liście do odczytu i wykonywania **const** operacji.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **const** element na liście.|
|[difference_type](#difference_type)|Typ, który zawiera różnicę między dwoma iteratorami odwołującymi się do elementów w obrębie tej samej listy.|
|[iterator](#iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element na liście.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu na liście.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do **const** element przechowywane na liście do odczytu i wykonywania **const** operacji.|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element na liście odwróconej.|
|[size_type](#size_type)|Typ, który zlicza liczbę elementów na liście.|
|[value_type](#value_type)|Typ, który reprezentuje typ danych przechowywanych na liście.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Przypisz](#assign)|Usuwa elementy z listy i kopiuje nowy zbiór elementów do listy docelowej.|
|[back](#back)|Zwraca odwołanie do ostatniego elementu listy.|
|[begin](#begin)|Zwraca iterator adresujący pierwszy element na liście.|
|[cbegin](#cbegin)|Zwraca iterator stałych adresujący pierwszy element na liście.|
|[cend](#cend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie na liście.|
|[Usuń zaznaczenie](#clear)|Usuwa wszystkie elementy listy.|
|[crbegin](#crbegin)|Zwraca iterator stałych adresujący pierwszy element na liście odwróconej.|
|[crend —](#crend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie na liście odwróconej.|
|[emplace —](#emplace)|Wstawia element skonstruowany w miejscu do listy na określonej pozycji.|
|[emplace_back](#emplace_back)|Dodaje element skonstruowany w miejscu do końca listy.|
|[emplace_front](#emplace_front)|Dodaje element skonstruowany w miejscu na początku listy.|
|[pusty](#empty)|Sprawdza, czy lista jest pusta.|
|[koniec](#end)|Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie na liście.|
|[wymazywanie](#erase)|Usuwa element lub zakres elementów na liście z określonych pozycji.|
|[Frontonu](#front)|Zwraca odwołanie do pierwszego elementu na liście.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu `allocator` użytego do stworzenia listy.|
|[Wstaw](#insert)|Wstawia element lub szereg elementów lub szereg elementów do listy na określonej pozycji.|
|[max_size](#max_size)|Zwraca maksymalną długość listy.|
|[merge](#merge)|Usuwa elementy z listy argumentów, wstawia je do listy docelowej i porządkuje nowe, połączone zbiór elementów w kolejności rosnącej lub w określonej kolejności.|
|[pop_back](#pop_back)|Usuwa element na końcu listy.|
|[pop_front](#pop_front)|Usuwa element na początku listy.|
|[push_back](#push_back)|Dodaje element do końca listy.|
|[push_front](#push_front)|Dodaje element do początku listy.|
|[rbegin](#rbegin)|Zwraca iterator adresujący pierwszy element na liście odwróconej.|
|[remove](#remove)|Usuwa elementy na liście, które pasują do określonej wartości.|
|[remove_if](#remove_if)|Usuwa elementy z listy, dla których jest spełniony określony predykat.|
|[rend —](#rend)|Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie na liście odwróconej.|
|[Zmiana rozmiaru](#resize)|Określa nowy rozmiar listy.|
|[zwrotny](#reverse)|Odwraca kolejność, w której elementy występują na liście.|
|[Rozmiar](#size)|Zwraca liczbę elementów na liście.|
|[sort](#sort)|Rozmieszcza elementy listy w kolejności rosnącej lub w odniesieniu do innych relacji zamówienia.|
|[splice](#splice)|Usuwa elementy z listy argumentów i wstawia je do listy docelowej.|
|[swap](#swap)|Zamienia elementy z dwóch list.|
|[unique](#unique)|Usuwa sąsiadujących zduplikowane elementy lub sąsiadujące elementy, które spełniają pewne binarny predykat z listy.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[list::operator =](#op_eq)|Zamienia elementy listy kopię innej listy.|

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<listy >

## <a name="allocator_type"></a>  list::allocator_type

Typ, który reprezentuje klasę alokatora dla obiektu listy.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type` synonim dla parametru szablonu jest *alokatora*.

### <a name="example"></a>Przykład

Zobacz przykład [get_allocator —](#get_allocator).

## <a name="assign"></a>  list::ASSIGN

Usuwa elementy z listy i kopiuje nowy zbiór elementów do listy docelowej.

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

*pierwszy*<br/>
Pozycja pierwszego elementu w zakresie elementów, które mają być kopiowane z listy argumentów.

*ostatni*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają być kopiowane z listy argumentów.

*Liczba*<br/>
Liczba kopii element jest wstawiany do listy.

*Val*<br/>
Wartość elementu jest wstawiany do listy.

*IList*<br/>
Lista initializer_list zawierająca elementy, które ma zostać wstawiony.

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkie istniejące elementy na liście, przypisz Wstawia określony zakres elementów z oryginalnej listy lub niektórych innych list na listę docelową lub wstawia kopii nowego elementu z określoną wartością do listy docelowej

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

## <a name="back"></a>  list::back

Zwraca odwołanie do ostatniego elementu listy.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Ostatni element listy. Jeśli lista jest pusta, zwracana wartość jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `back` jest przypisany do `const_reference`, nie można zmodyfikować obiektu list. Jeśli wartość zwracaną przez `back` jest przypisany do `reference`, można zmodyfikować obiekt list.

Gdy kompilowany przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowana jako 1 lub 2, wystąpi błąd czasu wykonywania przy próbie uzyskania dostępu do elementu na pustej liście.  Zobacz [Checked Iterators](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

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

## <a name="begin"></a>  list::BEGIN

Zwraca iterator adresujący pierwszy element na liście.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pierwszego elementu na liście lub do lokalizacji następującej po pustej listy.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `begin` jest przypisany do `const_iterator`, nie można modyfikować elementów w obiekcie listy. Jeśli wartość zwracaną przez `begin` jest przypisany do `iterator`, można modyfikować elementów w obiekcie listy.

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

## <a name="cbegin"></a>  list::cbegin

Zwraca **const** iterator odnoszący się do pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

A **const** iterator dostępu dwukierunkowego, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).

### <a name="remarks"></a>Uwagi

Wartością zwracaną `cbegin`, nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast `begin()` funkcja elementu członkowskiego w celu zagwarantowania, że wartość zwracana jest `const_iterator`. Zazwyczaj jest używana w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowem kluczowym dedukcji, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` jako modyfikowalny (nie - **const**) kontener dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  list::cend

Zwraca `const` iterator adresujący lokalizację tuż za ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

A `const` iterator dostępu dwukierunkowego, który wskazuje tuż za koniec zakresu.

### <a name="remarks"></a>Uwagi

`cend` Służy do sprawdzenia, czy iterator minął koniec swojego zakresu.

Można użyć tej funkcji elementu członkowskiego zamiast `end()` funkcja elementu członkowskiego w celu zagwarantowania, że wartość zwracana jest `const_iterator`. Zazwyczaj jest używana w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowem kluczowym dedukcji, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` jako modyfikowalny (nie - **const**) kontener dowolnego rodzaju, który obsługuje `end()` i `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Wartość zwrócona przez obiekt `cend` nie należy usuwać odwołania.

## <a name="clear"></a>  list::Clear

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

## <a name="const_iterator"></a>  list::const_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać **const** element na liście.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [ponownie](#back).

## <a name="const_pointer"></a>  list::const_pointer

Zawiera wskaźnik do **const** element na liście.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

W większości przypadków [iteratora](#iterator) powinien być używany do uzyskania dostępu do elementów w obiekcie listy.

## <a name="const_reference"></a>  list::const_reference

Typ, który zawiera odwołanie do **const** element przechowywane na liście do odczytu i wykonywania **const** operacji.

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

## <a name="const_reverse_iterator"></a>  list::const_reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **const** element na liście.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i jest używana do iteracji przez listę w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład [rbegin —](#rbegin).

## <a name="crbegin"></a>  list::crbegin

Zwraca iterator stałych adresujący pierwszy element na liście odwróconej.

```cpp
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iterator dwukierunkowy odnoszący się do pierwszego elementu na liście odwróconej (lub adresowania, który był ostatnim elementem w nieodwróconej `list`).

### <a name="remarks"></a>Uwagi

`crbegin` jest używana z listą odwróconą tak jak [list::begin](#begin) jest używana z `list`.

Wartością zwracaną `crbegin`, nie można zmodyfikować obiektu list. [list::rbegin](#rbegin) może służyć do iteracji przez listę wstecz.

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

## <a name="crend"></a>  list::crend

Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie na liście odwróconej.

```cpp
const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iteratora dwukierunkowego, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconej [listy](../standard-library/list-class.md) (miejsca przed pierwszym elementem w nieodwróconej `list`).

### <a name="remarks"></a>Uwagi

`crend` jest używana z listą odwróconą tak jak [list::end](#end) jest używana z `list`.

Wartością zwracaną `crend`, `list` nie można zmodyfikować obiektu.

`crend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej `list`.

Wartość zwrócona przez obiekt `crend` nie należy usuwać odwołania.

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

## <a name="difference_type"></a>  list::difference_type

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów na liście w zakresie pomiędzy elementami wskazywanymi przez Iteratory.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` Jest typ zwracany, jeśli odjęcie lub inkrementacji poprzez Iteratory kontenera. `difference_type` Jest zazwyczaj używany do reprezentowania liczby elementów w zakresie [ `first`, `last`) między Iteratory `first` i `last`, zawiera element wskazywany przez `first` i zakres elementów do , ale bez element wskazane przez `last`.

Należy pamiętać, że chociaż `difference_type` jest dostępna dla wszystkich iteratorów, które spełniają wymagania iteratora danych wejściowych zawiera klasę iteratorów dwukierunkowych obsługiwane przez odwracalnego kontenerów, takich jak zestaw, odejmowania między Iteratory jest tylko obsługiwane przez Iteratory dostępu swobodnego, dostarczone przez kontener dostępu swobodnego, takich jak [vector, klasa](../standard-library/vector-class.md).

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

## <a name="emplace"></a>  list::emplace

Wstawia element skonstruowany w miejscu do listy na określonej pozycji.

```cpp
void emplace(iterator Where, Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Where*|Położenie w elemencie docelowym [listy](../standard-library/list-class.md) polegający na wstawieniu pierwszego elementu.|
|*Val*|Element dodany na końcu `list`.|

### <a name="remarks"></a>Uwagi

Jeśli wyjątek jest zgłaszany, `list` jest niezmieniony po lewej stronie, a wyjątek jest zgłaszany ponownie.

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

## <a name="emplace_back"></a>  list::emplace_back

Dodaje element skonstruowany w miejscu do końca listy.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Element dodany na końcu [listy](../standard-library/list-class.md).|

### <a name="remarks"></a>Uwagi

Jeśli wyjątek jest zgłaszany, `list` jest niezmieniony po lewej stronie, a wyjątek jest zgłaszany ponownie.

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

## <a name="emplace_front"></a>  list::emplace_front

Dodaje element skonstruowany w miejscu na początku listy.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Element dodany do stanu sprzed [listy](../standard-library/list-class.md).|

### <a name="remarks"></a>Uwagi

Jeśli wyjątek jest zgłaszany, `list` jest niezmieniony po lewej stronie, a wyjątek jest zgłaszany ponownie.

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

## <a name="empty"></a>  list::Empty

Sprawdza, czy lista jest pusta.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli lista jest pusta. **false** Jeśli lista nie jest pusty.

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

## <a name="end"></a>  list::end

Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie na liście.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do lokalizacji następującej po ostatnim elemencie na liście. Jeśli lista jest pusta, następnie `list::end == list::begin`.

### <a name="remarks"></a>Uwagi

`end` Służy do sprawdzenia, czy iterator osiągnął koniec swojej listy.

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

## <a name="erase"></a>  list::ERASE

Usuwa element lub zakres elementów na liście z określonych pozycji.

```cpp
iterator erase(iterator Where);
iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Parametry

*Where*<br/>
Pozycja elementu do usunięcia z listy.

*pierwszy*<br/>
Pozycja pierwszego elementu usunięty z listy.

*ostatni*<br/>
Pozycja tuż za ostatnim elementem usunięty z listy.

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy, który wskazuje na pierwszy element pozostający poza wszelkimi elementami usuniętymi lub wskaźnik do końca listy, jeśli taki element nie istnieje.

### <a name="remarks"></a>Uwagi

Nie ponowne przydzielenie występuje, iteratorów i odwołania stają się nieprawidłowe tylko dla elementów wymazane.

`erase` nigdy nie zgłasza wyjątek.

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

## <a name="front"></a>  list::front

Zwraca odwołanie do pierwszego elementu na liście.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest pusta, zwracana jest niezdefiniowane.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `front` jest przypisany do `const_reference`, nie można zmodyfikować obiektu list. Jeśli wartość zwracaną przez `front` jest przypisany do `reference`, można zmodyfikować obiekt list.

Gdy kompilowany przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowana jako 1 lub 2, wystąpi błąd czasu wykonywania przy próbie uzyskania dostępu do elementu na pustej liście.  Zobacz [Checked Iterators](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

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

## <a name="get_allocator"></a>  list::get_allocator

Zwraca kopię obiektu programu przydzielania, używany do utworzenia listy.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez listy.

### <a name="remarks"></a>Uwagi

Puli buforów dla klasy listy Określ, jak klasa zarządza magazynem. Buforów domyślną dostarczony wraz z klasy kontenera standardowej biblioteki języka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.

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

## <a name="insert"></a>  list::INSERT

Wstawia element lub szereg elementów lub szereg elementów do listy na określonej pozycji.

```cpp
iterator insert(iterator Where, const Type& Val);
iterator insert(iterator Where, Type&& Val);

void insert(iterator Where, size_type Count, const Type& Val);
iterator insert(iterator Where, initializer_list<Type> IList);

template <class InputIterator>
void insert(iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Where*|Pozycja na liście cel polegający na wstawieniu pierwszego elementu.|
|*Val*|Wartość elementu jest wstawiany do listy.|
|*Liczba*|Liczba elementów, które są umieszczone na liście.|
|*pierwszy*|Pozycja pierwszego elementu w zakresie elementów na liście argumentów do skopiowania.|
|*ostatni*|Pozycja pierwszego elementu poza zakresem elementów na liście argumentów do skopiowania.|

### <a name="return-value"></a>Wartość zwracana

Wstaw dwa pierwsze zwracają iterator, który wskazuje miejsce, gdzie dodano nowy element do listy.

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

## <a name="iterator"></a>  list::iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element na liście.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin).

## <a name="list"></a>  list::list

Tworzy listę o określonym rozmiarze lub z elementami określonej wartości lub z określonego programu przydzielania lub jako kopię całości lub części niektórych innych list.

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

|Parametr|Opis|
|-|-|
|*Al*|Klasa alokatora do wykorzystania z tym obiektem.|
|*Liczba*|Liczba elementów na utworzonej liście.|
|*Val*|Wartość elementów na liście.|
|*po prawej stronie*|Lista, z której kopią jest lista skonstruowana.|
|*pierwszy*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*ostatni*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|
|*IList*|Lista initializer_list zawierająca elementy, które ma być skopiowany.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują obiekt programu przydzielania (*Al*) i inicjują listy.

[get_allocator —](#get_allocator) zwraca kopię obiektu programu przydzielania, używany do utworzenia listy.

Dwa pierwsze konstruktory określają pustą listę wstępną, drugi określa typ programu przydzielania (*Al*) ma być używany.

Trzeci Konstruktor określa powtórzenie określonej liczby (*liczba*) elementów wartości domyślnej dla klasy `Type`.

Czwarty i piąty Konstruktor określają powtórzenia (*liczba*) elementów wartości *Val*.

Szósty Konstruktor Określa kopię listy *po prawej stronie*.

Siódmego Konstruktor przenosi listę *po prawej stronie*.

Konstruktor ósmego używa initializer_list w celu określenia elementów.

Następne dwa konstruktory kopiują zakres `[First, Last)` listy.

Żaden z konstruktorów wykonuje żadnych tymczasowych realokacji.

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

## <a name="max_size"></a>  list::max_size

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

## <a name="merge"></a>  list::merge

Usuwa elementy z listy argumentów, wstawia je do listy docelowej i porządkuje nowe, połączone zbiór elementów w kolejności rosnącej lub w określonej kolejności.

```cpp
void merge(list<Type, Allocator>& right);

template <class Traits>
void merge(list<Type, Allocator>& right, Traits comp);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Lista argumentów, które ma zostać scalona z listy docelowej.

*Comp*<br/>
Operator porównania ustawiał elementów listy docelowej.

### <a name="remarks"></a>Uwagi

Lista argumentów *prawo* jest scalany z listy docelowej.

Muszą być uporządkowane listy zarówno argument, jak i obiektem docelowym za pomocą tej samej relacji porównania, za pomocą którego ma zostać określona wynikowa sekwencja. Domyślna kolejność Pierwsza funkcja członkowska jest rosnąco. Funkcja drugiego członka nakłada operacji porównania określonych przez użytkownika *comp* klasy `Traits`.

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

## <a name="op_eq"></a>  list::operator =

Zamienia elementy listy kopię innej listy.

```cpp
list& operator=(const list& right);
list& operator=(list&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*right*|[Listy](../standard-library/list-class.md) są kopiowane do `list`.|

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkie elementy istniejących w `list`, użytkownik kopiuje lub przenosi zawartość *prawo* do `list`.

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

## <a name="pointer"></a>  list::Pointer

Udostępnia wskaźnik do elementu na liście.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iteratora](#iterator) powinien być używany do uzyskania dostępu do elementów w obiekcie listy.

## <a name="pop_back"></a>  list::pop_back

Usuwa element na końcu listy.

```cpp
void pop_back();
```

### <a name="remarks"></a>Uwagi

Ostatni element nie może być pusta. `pop_back` nigdy nie zgłasza wyjątek.

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

## <a name="pop_front"></a>  list::pop_front

Usuwa element na początku listy.

```cpp
void pop_front();
```

### <a name="remarks"></a>Uwagi

Pierwszy element nie może być pusta. `pop_front` nigdy nie zgłasza wyjątek.

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

## <a name="push_back"></a>  list::push_back

Dodaje element do końca listy.

```cpp
void push_back(void push_back(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Element dodany na końcu listy.|

### <a name="remarks"></a>Uwagi

Jeśli wyjątek jest zgłaszany, lista pozostanie niezmieniony, a wyjątek jest zgłaszany ponownie.

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

## <a name="push_front"></a>  list::push_front

Dodaje element do początku listy.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Element dodany na początku listy.|

### <a name="remarks"></a>Uwagi

Jeśli wyjątek jest zgłaszany, lista pozostanie niezmieniony, a wyjątek jest zgłaszany ponownie.

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

## <a name="rbegin"></a>  list::rbegin

Zwraca iterator adresujący pierwszy element na liście odwróconej.

```cpp
const_reverse_iterator rbegin() const;
reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnej dwukierunkowy iterator odnoszący się do pierwszego elementu na liście odwróconej (lub adresowania, który był ostatnim elementem na liście nieodwróconej).

### <a name="remarks"></a>Uwagi

`rbegin` jest używana z listą odwróconą tak jak [rozpocząć](#begin) jest używana z listą.

Jeśli wartość zwracaną przez `rbegin` jest przypisany do `const_reverse_iterator`, nie można zmodyfikować obiektu list. Jeśli wartość zwracaną przez `rbegin` jest przypisany do `reverse_iterator`, można zmodyfikować obiekt list.

`rbegin` może służyć do iteracji przez listę wstecz.

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

## <a name="reference"></a>  list::Reference

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

## <a name="remove"></a>  list::Remove

Usuwa elementy na liście, które pasują do określonej wartości.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość, która posiadaniu elementu, spowoduje usunięcie tego elementu z listy.

### <a name="remarks"></a>Uwagi

Nie wpływa na kolejność pozostałych elementów.

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

## <a name="remove_if"></a>  list::remove_if

Usuwa elementy z listy, dla których jest spełniony określony predykat.

```cpp
template <class Predicate>
void remove_if(Predicate pred)
```

### <a name="parameters"></a>Parametry

*P.*<br/>
Predykat jednoelementowy, który, jeżeli zostanie spełniony przez element, powoduje usunięcie tego elementu z listy.

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

## <a name="rend"></a>  list::rend

Zwraca iterator odnoszący się do lokalizacji, która następuje po ostatnim elemencie na liście odwróconej.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do lokalizacji następującej po ostatnim elemencie na liście odwróconej (miejsca przed pierwszy element na liście nieodwróconej).

### <a name="remarks"></a>Uwagi

`rend` jest używana z listą odwróconą tak jak [zakończenia](#end) jest używana z listą.

Jeśli wartość zwracaną przez `rend` jest przypisany do `const_reverse_iterator`, nie można zmodyfikować obiektu list. Jeśli wartość zwracaną przez `rend` jest przypisany do `reverse_iterator`, można zmodyfikować obiekt list.

`rend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej listy.

Wartość zwrócona przez obiekt `rend` nie należy usuwać odwołania.

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

## <a name="resize"></a>  list::Resize

Określa nowy rozmiar listy.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Parametry

*_Newsize*<br/>
Nowy rozmiar listy.

*Val*<br/>
Wartość nowych elementów do dodania do listy nowy rozmiar jest większy, oryginalnym rozmiarze. W przypadku pominięcia wartości, nowym elementom zostanie przypisana wartość domyślna dla klasy.

### <a name="remarks"></a>Uwagi

Jeśli rozmiar listy jest mniejszy niż rozmiar żądanej *_Newsize*, elementy są dodawane do listy, dopóki nie osiągnie żądanego rozmiaru.

Jeśli rozmiar listy jest większy niż wymagany, najbliższe końca listy elementy są usuwane do momentu osiągnięcia przez listę rozmiaru *_Newsize*.

Jeśli obecny rozmiar listy jest taki sam jak żądany rozmiar, nie podjęto żadnej akcji.

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

## <a name="reverse"></a>  list::reverse

Odwraca kolejność, w której elementy występują na liście.

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

## <a name="reverse_iterator"></a>  list::reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element na liście odwróconej.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używana do iteracji przez listę w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład [rbegin —](#rbegin).

## <a name="size"></a>  list::size

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

## <a name="size_type"></a>  list::size_type

Typ, który zlicza liczbę elementów na liście.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [rozmiar](#size).

## <a name="sort"></a>  list::sort

Rozmieszcza elementy listy w kolejności rosnącej lub w odniesieniu do niektórych określonych przez użytkownika kolejności.

```cpp
void sort();

template <class Traits>
void sort(Traits comp);
```

### <a name="parameters"></a>Parametry

*Comp*<br/>
Operator porównania ustawiał kolejne elementy.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska umieszcza elementy w kolejności rosnącej według domyślnie.

Funkcję szablonu członka Porządkuje elementy według operacji porównania określonych przez użytkownika *comp* klasy `Traits`.

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

## <a name="splice"></a>  list::splice

Usuwa elementy z listy źródeł i wstawia je do listy docelowej.

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

*Where*<br/>
Pozycja na liście docelowy, przed którym ma zostać wstawiony.

*Źródło*<br/>
Lista źródeł, który ma zostać wstawiony do listy docelowej.

*ITER*<br/>
Element, który ma zostać wstawiony z listy źródeł.

*pierwszy*<br/>
Pierwszy element w zakresie, który ma zostać wstawiony z listy źródeł.

*ostatni*<br/>
Do pierwszej pozycji poza ostatnim elementem w zakresie, który ma zostać wstawiony z listy źródeł.

### <a name="remarks"></a>Uwagi

Pierwszy pary elementów członkowskich wstawia wszystkie elementy z listy źródeł do listy docelowej przed pozycji odwołuje się *gdzie* i usuwa wszystkie elementy z listy źródeł. (`&Source` nie musi być równa `this`.)

Druga para elementów członkowskich wstawia element przywoływany przez *Iter* przed pozycji na liście docelowego określonego przez *gdzie* i usuwa *Iter* z Lista źródeł. (Jeśli `Where == Iter || Where == ++Iter`, nie zmienią.)

Trzecia para elementów członkowskich wstawia zakresu wyznaczonego przez [ `First`, `Last`) przed elementu na liście docelowego określonego przez *gdzie* oraz usunięcie tego zakresu elementów z listy źródeł. (Jeśli `&Source == this`, zakres `[First, Last)` nie może zawierać element wskazane przez *gdzie*.)

Jeśli ranged splice wstawia `N` elementów, a `&Source != this`, obiekt klasy [iteratora](../standard-library/forward-list-class.md#iterator) jest zwiększany `N` razy.

We wszystkich przypadkach Iteratory, wskaźników lub odwołań, które odwołują się do elementów spliced zachowają ważność i są przekazywane do kontenera docelowego.

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

## <a name="swap"></a>  list::swap

Zamienia elementy z dwóch list.

```cpp
void swap(list<Type, Allocator>& right);
friend void swap(list<Type, Allocator>& left, list<Type, Allocator>& right)
```

### <a name="parameters"></a>Parametry

*right*<br/>
Lista zawierająca elementy, które mają być zamienione lub lista, której elementy są wymieniane z postanowieniami listy *po lewej stronie*.

*left*<br/>
Lista, której elementy są wymieniane z postanowieniami listy *prawo*.

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

## <a name="unique"></a>  list::UNIQUE

Usuwa sąsiadujących zduplikowane elementy lub sąsiadujące elementy, które spełniają pewne binarny predykat z listy.

```cpp
void unique();

template <class BinaryPredicate>
void unique(BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*P.*<br/>
Jeśli predykat binarny jest użyty do porównania kolejne elementy.

### <a name="remarks"></a>Uwagi

Ta funkcja przyjęto założenie, że lista jest sortowana, tak, aby wszystkie zduplikowane elementy znajdują się obok siebie. Duplikaty, które nie są one sąsiadujące nie zostaną usunięte.

Pierwsza funkcja członkostwa Usuwa każdy element, który porównuje równa jego poprzedzający element.

Funkcja drugiego członka Usuwa każdy element, który spełnia funkcji predykatu *pred* w porównaniu z jej poprzedniego elementu. Możesz użyć dowolnej obiektów funkcji binarne zadeklarowanych w \<funkcjonalności > nagłówka dla argumentu *pred* lub możesz utworzyć swój własny.

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

## <a name="value_type"></a>  list::value_type

Typ, który reprezentuje typ danych przechowywanych na liście.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Uwagi

`value_type` synonim dla parametru szablonu jest *typu*.

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

## <a name="see-also"></a>Zobacz także

[\<list>](../standard-library/list.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
