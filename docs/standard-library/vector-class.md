---
title: vector — Klasa
ms.date: 11/04/2016
f1_keywords:
- vector/std::vector::allocator_type
- vector/std::vector::const_iterator
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::const_reverse_iterator
- vector/std::vector::difference_type
- vector/std::vector::iterator
- vector/std::vector::pointer
- vector/std::vector::reference
- vector/std::vector::reverse_iterator
- vector/std::vector::size_type
- vector/std::vector::value_type
- vector/std::vector::assign
- vector/std::vector::at
- vector/std::vector::back
- vector/std::vector::begin
- vector/std::vector::capacity
- vector/std::vector::cbegin
- vector/std::vector::cend
- vector/std::vector::crbegin
- vector/std::vector::crend
- vector/std::vector::clear
- vector/std::vector::data
- vector/std::vector::emplace
- vector/std::vector::emplace_back
- vector/std::vector::empty
- vector/std::vector::end
- vector/std::vector::erase
- vector/std::vector::front
- vector/std::vector::get_allocator
- vector/std::vector::insert
- vector/std::vector::max_size
- vector/std::vector::pop_back
- vector/std::vector::push_back
- vector/std::vector::rbegin
- vector/std::vector::rend
- vector/std::vector::reserve
- vector/std::vector::resize
- vector/std::vector::shrink_to_fit
- vector/std::vector::size
- vector/std::vector::swap
helpviewer_keywords:
- std::vector [C++], allocator_type
- std::vector [C++], const_iterator
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], const_reverse_iterator
- std::vector [C++], difference_type
- std::vector [C++], iterator
- std::vector [C++], pointer
- std::vector [C++], reference
- std::vector [C++], reverse_iterator
- std::vector [C++], size_type
- std::vector [C++], value_type
- std::vector [C++], assign
- std::vector [C++], at
- std::vector [C++], back
- std::vector [C++], begin
- std::vector [C++], capacity
- std::vector [C++], cbegin
- std::vector [C++], cend
- std::vector [C++], crbegin
- std::vector [C++], crend
- std::vector [C++], clear
- std::vector [C++], data
- std::vector [C++], emplace
- std::vector [C++], emplace_back
- std::vector [C++], empty
- std::vector [C++], end
- std::vector [C++], erase
- std::vector [C++], front
- std::vector [C++], get_allocator
- std::vector [C++], insert
- std::vector [C++], max_size
- std::vector [C++], pop_back
- std::vector [C++], push_back
- std::vector [C++], rbegin
- std::vector [C++], rend
- std::vector [C++], reserve
- std::vector [C++], resize
- std::vector [C++], shrink_to_fit
- std::vector [C++], size
- std::vector [C++], swap
ms.assetid: a3e0a8f8-7565-4fe0-93e4-e4d74ae1b70d
ms.openlocfilehash: 887f41d4dc3eac728b70ac653964903957d78930
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454569"
---
# <a name="vector-class"></a>vector — Klasa

Klasa C++ wektorów standardowej biblioteki jest klasą szablonów kontenerów sekwencji, które układają elementy danego typu w rozmieszczeniu liniowym i umożliwiają szybki dostęp losowy do dowolnego elementu. Powinny to być preferowany kontener dla sekwencji, gdy wydajność dostępu swobodnego jest w warstwie Premium.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Allocator = allocator<Type>>
class vector
```

### <a name="parameters"></a>Parametry

*Wprowadź*\
Typ danych elementu, który ma być przechowywany w wektorze

*Alokator*\
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji wektora i cofania alokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to `allocator<Type>`.

## <a name="remarks"></a>Uwagi

Wektory umożliwiają stałe wstawienia i usunięcia na końcu sekwencji. Wstawianie lub usuwanie elementów w środku wektora wymaga czasu liniowego. Wydajność kontenera [klasy deque](../standard-library/deque-class.md) jest najwyższa w odniesieniu do wstawień i usunięć na początku i na końcu sekwencji. Kontener [klasy listy](../standard-library/list-class.md) jest nadrzędny w odniesieniu do wstawień i usunięć w dowolnej lokalizacji w ramach sekwencji.

Ponowna alokacja wektora występuje, gdy funkcja członkowska musi zwiększyć sekwencję zawartą w obiekcie Vector poza bieżącą pojemność magazynu. Inne wstawienia i wymazy mogą zmieniać różne adresy magazynu w ramach sekwencji. We wszystkich takich przypadkach Iteratory lub odwołania wskazujące na zmienione fragmenty sekwencji stają się nieprawidłowe. W przypadku braku ponownej alokacji tylko Iteratory i odwołania przed punktem wstawiania/usuwania pozostają prawidłowe.

[Klasa bool\<Vector >](../standard-library/vector-bool-class.md) jest pełną specjalizacją wektora klasy szablonu dla elementów typu bool z alokatorem dla typu podstawowego używanego przez specjalizację.

[Klasa referencyjna bool\<wektora Vector >](../standard-library/vector-bool-class.md#reference_class) jest klasą zagnieżdżoną, której obiekty mogą dostarczać odwołania do elementów (pojedynczych bitów) w obrębie obiektu logicznego > wektora.\<

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[niemożliwe](#vector)|Konstruuje wektor o określonym rozmiarze lub z elementami określonej wartości lub z konkretną `allocator` lub jako kopią innego wektora.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje `allocator` klasę obiektu Vector.|
|[const_iterator](#const_iterator)|Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać element **const** w wektorze.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do elementu **const** w wektorze.|
|[const_reference](#const_reference)|Typ, który dostarcza odwołanie do elementu **const** przechowywanego w wektorze do odczytu i wykonywania operacji **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać dowolny element **const** w wektorze.|
|[difference_type](#difference_type)|Typ, który zawiera różnicę między adresami dwóch elementów w wektorze.|
|[iterator](#iterator)|Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać lub zmodyfikować dowolny element w wektorze.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu w wektorze.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w wektorze.|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać lub zmodyfikować dowolny element w odwróconym wektorze.|
|[size_type](#size_type)|Typ, który zlicza liczbę elementów w wektorze.|
|[value_type](#value_type)|Typ, który reprezentuje typ danych przechowywany w wektorze.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[ponownie](#assign)|Wymazuje wektor i kopiuje określone elementy do pustego wektora.|
|[at](#at)|Zwraca odwołanie do elementu w określonej lokalizacji wektora.|
|[back](#back)|Zwraca odwołanie do ostatniego elementu wektora.|
|[begin](#begin)|Zwraca iterator dostępu swobodnego do pierwszego elementu w wektorze.|
|[pojemności](#capacity)|Zwraca liczbę elementów, które może zawierać wektor bez przydziału większej ilości miejsca w magazynie.|
|[cbegin](#cbegin)|Zwraca iterator const dostępu swobodnego do pierwszego elementu w wektorze.|
|[cend](#cend)|Zwraca iterator const dostępu swobodnego, który wskazuje tuż poza końcem wektora.|
|[crbegin](#crbegin)|Zwraca iterator const do pierwszego elementu w odwróconym wektorze.|
|[crend](#crend)|Zwraca iterator const do końca odwróconego wektora.|
|[Wyczyść](#clear)|Wymazuje elementy wektora.|
|[Data](#data)|Zwraca wskaźnik do pierwszego elementu w wektorze.|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do wektora w określonym położeniu.|
|[emplace_back](#emplace_back)|Dodaje element skonstruowany w miejscu do końca wektora.|
|[empty](#empty)|Testuje, czy kontener wektora jest pusty.|
|[punktów](#end)|Zwraca iterator dostępu swobodnego, który wskazuje na koniec wektora.|
|[Wyłączanie](#erase)|Usuwa element lub zakres elementów w wektorze z określonych pozycji.|
|[FSB](#front)|Zwraca odwołanie do pierwszego elementu w wektorze.|
|[get_allocator](#get_allocator)|Zwraca obiekt do `allocator` klasy używanej przez wektor.|
|[wstawienia](#insert)|Wstawia element lub liczbę elementów do wektora w określonym położeniu.|
|[max_size](#max_size)|Zwraca maksymalną długość wektora.|
|[pop_back](#pop_back)|Usuwa element na końcu wektora.|
|[push_back](#push_back)|Dodaj element na końcu wektora.|
|[rbegin](#rbegin)|Zwraca iterator do pierwszego elementu w odwróconym wektorze.|
|[rend](#rend)|Zwraca iterator do końca odwróconego wektora.|
|[reserve](#reserve)|Rezerwuje minimalną długość magazynu dla obiektu Vector.|
|[Zmień rozmiar](#resize)|Określa nowy rozmiar wektora.|
|[shrink_to_fit](#shrink_to_fit)|Odrzuca nadmiarową pojemność.|
|[zmienia](#size)|Zwraca liczbę elementów w wektorze.|
|[swap](#swap)|Wymienia elementy dwóch wektorów.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator&#91;&#93;](#op_at)|Zwraca odwołanie do elementu wektora na określonej pozycji.|
|[operator=](#op_eq)|Zastępuje elementy wektora kopią innego wektora.|

## <a name="allocator_type"></a>allocator_type

Typ, który reprezentuje klasę alokatora dla obiektu Vector.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type`jest synonimem dla parametru `Allocator`szablonu.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla programu [get_allocator](#get_allocator) , `allocator_type`korzystając z programu.

## <a name="assign"></a>ponownie

Wymazuje wektor i kopiuje określone elementy do pustego wektora.

```cpp
void assign(size_type Count, const Type& Val);
void assign(initializer_list<Type> IList);

template <class InputIterator>
void assign(InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parametry

*Pierwszego*\
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*Ostatniego*\
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

*Liczbą*\
Liczba kopii elementu wstawianych do wektora.

*Użyte*\
Wartość wstawianego elementu do wektora.

*IList*\
Initializer_list zawierający elementy do wstawienia.

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkich istniejących elementów w wektorze należy przypisać do wektora lub wstawiał do wektora kopie określonego zakresu elementów z oryginalnego wektora.

### <a name="example"></a>Przykład

```cpp
/ vector_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2, v3;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(30);
    v1.push_back(40);
    v1.push_back(50);

    cout << "v1 = ";
    for (auto& v : v1){
        cout << v << " ";
    }
    cout << endl;

    v2.assign(v1.begin(), v1.end());
    cout << "v2 = ";
    for (auto& v : v2){
        cout << v << " ";
    }
    cout << endl;

    v3.assign(7, 4);
    cout << "v3 = ";
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;

    v3.assign({ 5, 6, 7 });
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;
}
```

## <a name="at"></a>w

Zwraca odwołanie do elementu w określonej lokalizacji wektora.

```cpp
reference at(size_type _Pos);

const_reference at(size_type _Pos) const;
```

### <a name="parameters"></a>Parametry

*_Pos*\
Indeks dolny lub numer pozycji elementu do odwołania w wektorze.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu w indeksie w argumencie. Jeśli `_Off` jest większy niż rozmiar wektora, `at` zgłasza wyjątek.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana elementu `at` jest przypisana `const_reference`do, nie można zmodyfikować obiektu wektora. Jeśli wartość `at` zwracana jest przypisana `reference`do, obiekt Vector może być modyfikowany.

### <a name="example"></a>Przykład

```cpp
// vector_at.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const int &i = v1.at( 0 );
   int &j = v1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a>Wstecz

Zwraca odwołanie do ostatniego elementu wektora.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Ostatni element wektora. Jeśli wektor jest pusty, wartość zwracana jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana elementu `back` jest przypisana `const_reference`do, nie można zmodyfikować obiektu wektora. Jeśli wartość `back` zwracana jest przypisana `reference`do, obiekt Vector może być modyfikowany.

Podczas kompilowania przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowanego jako 1 lub 2, wystąpi błąd czasu wykonywania, jeśli próbujesz uzyskać dostęp do elementu w pustym wektorze.  Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md) .

### <a name="example"></a>Przykład

```cpp
// vector_back.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.back( );
   const int& ii = v1.front( );

   cout << "The last integer of v1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of v1 is "<< ii << endl;
}
```

## <a name="begin"></a>zaczną

Zwraca iterator dostępu swobodnego do pierwszego elementu w wektorze.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu swobodnego odnoszący się do pierwszego elementu `vector` w lub do lokalizacji, która powiodła `vector`się, jest pusta. Należy zawsze porównać wartość zwracaną z [Vector:: end](#end) , aby upewnić się, że jest ona prawidłowa.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana elementu `begin` jest przypisana do wektora [::](#const_iterator) `vector` const_iterator, nie można zmodyfikować obiektu. Jeśli wartość zwracana elementu `begin` jest przypisana do wektora: [:](#iterator) `vector` iterator, obiekt może być modyfikowany.

### <a name="example"></a>Przykład

```cpp
// vector_begin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::iterator c1_Iter;
    vector<int>::const_iterator c1_cIter;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_Iter = c1.begin();
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1_Iter = c1.begin();
    *c1_Iter = 20;
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    // The following line would be an error because iterator is const
    // *c1_cIter = 200;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="capacity"></a>pojemności

Zwraca liczbę elementów, które może zawierać wektor bez przydziału większej ilości miejsca w magazynie.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość magazynu przydzieloną dla wektora.

### <a name="remarks"></a>Uwagi

[Zmiana rozmiaru](#resize) funkcji składowej będzie wydajniejsza w przypadku przydzielenia wystarczającej ilości pamięci. Użyj rezerwy funkcji [](#reserve) składowej, aby określić ilość przydzieloną pamięci.

### <a name="example"></a>Przykład

```cpp
// vector_capacity.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 1 );
   cout << "The length of storage allocated is "
        << v1.capacity( ) << "." << endl;

   v1.push_back( 2 );
   cout << "The length of storage allocated is now "
        << v1.capacity( ) << "." << endl;
}
```

```Output
The length of storage allocated is 1.
The length of storage allocated is now 2.
```

## <a name="cbegin"></a>cbegin

Zwraca iterator **const** , który dotyczy pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator **stałej** dostępu swobodnego, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu `cbegin() == cend()`).

### <a name="remarks"></a>Uwagi

Z wartością `cbegin`zwracaną nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast `begin()` funkcji składowej, aby zagwarantować, że wartość zwracana to. `const_iterator` Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy `Container` , że jest to modyfikowalny kontener dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

Zwraca iterator **const** , który odnosi się do lokalizacji jedynie poza ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator **stałej** dostępu swobodnego, który wskazuje tuż poza końcem zakresu.

### <a name="remarks"></a>Uwagi

`cend`służy do sprawdzania, czy iterator przeszedł koniec zakresu.

Można użyć tej funkcji elementu członkowskiego zamiast `end()` funkcji składowej, aby zagwarantować, że wartość zwracana to. `const_iterator` Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy `Container` , że jest to modyfikowalny kontener dowolnego rodzaju, który obsługuje `end()` i `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Nie można usunąć odwołania `cend` do wartości zwracanej przez.

## <a name="clear"></a>Wyczyść

Wymazuje elementy wektora.

```cpp
void clear();
```

### <a name="example"></a>Przykład

```cpp
// vector_clear.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "The size of v1 is " << v1.size( ) << endl;
   v1.clear( );
   cout << "The size of v1 after clearing is " << v1.size( ) << endl;
}
```

```Output
The size of v1 is 3
The size of v1 after clearing is 0
```

## <a name="const_iterator"></a>const_iterator

Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać element **const** w wektorze.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może być używany do modyfikacji wartości elementu.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem z [powrotem](#back) dla przykładu korzystającego `const_iterator`z programu.

## <a name="const_pointer"></a>const_pointer

Typ, który dostarcza wskaźnik do elementu **const** w wektorze.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może być używany do modyfikacji wartości elementu.

[Iterator](#iterator) jest najczęściej używany do uzyskiwania dostępu do elementu Vector.

## <a name="const_reference"></a>const_reference

Typ, który dostarcza odwołanie do elementu **const** przechowywanego w wektorze do odczytu i wykonywania operacji **const** .

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

Typ `const_reference` nie może być używany do modyfikacji wartości elementu.

### <a name="example"></a>Przykład

```cpp
// vector_const_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const vector <int> v2 = v1;
   const int &i = v2.front( );
   const int &j = v2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as v2 is const
   // v2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a>const_reverse_iterator

Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać dowolny element **const** w wektorze.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartości elementu i służy do iteracji w odwrotnej części wektora.

### <a name="example"></a>Przykład

Zobacz [rbegin](#rbegin) , aby zapoznać się z przykładem sposobu deklarowania iteratora i korzystania z niego.

## <a name="crbegin"></a>crbegin —

Zwraca iterator const do pierwszego elementu w odwróconym wektorze.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu stała odwrotnie dostęp losowy odnoszący się do pierwszego elementu [](../standard-library/vector-class.md) w odwróconym wektorze lub na adres, który był ostatnim elementem w `vector`odwrót.

### <a name="remarks"></a>Uwagi

Z wartością `crbegin`zwracaną `vector` , nie można zmodyfikować obiektu.

### <a name="example"></a>Przykład

```cpp
// vector_crbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="crend"></a>crend

Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym wektorze.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu const odwrotnie, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym wektorze [](../standard-library/vector-class.md) (lokalizacja, która poprzedza pierwszy element w odwrót `vector`).

### <a name="remarks"></a>Uwagi

`crend`jest używany z odwróconym `vector` , podobnie jak [Vector:: cend](#cend) `vector`jest używany z.

Po wartości `crend` zwracanej (odpowiednio zmniejszonej) `vector` nie można zmodyfikować obiektu.

`crend`można go użyć do przetestowania, czy iterator odwrotny osiągnął koniec jego `vector`.

Nie można usunąć odwołania `crend` do wartości zwracanej przez.

### <a name="example"></a>Przykład

```cpp
// vector_crend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="data"></a>Data

Zwraca wskaźnik do pierwszego elementu w wektorze.

```cpp
const_pointer data() const;

pointer data();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego elementu w wektorze lub [](../standard-library/vector-class.md) do lokalizacji powiodło się puste `vector`.

### <a name="example"></a>Przykład

```cpp
// vector_data.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::pointer c1 ptr;
    vector<int>::const_pointer c1_cPtr;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_cPtr = c1.data();
    for (size_t n = c1.size(); 0 < n; --n, c1_cPtr++)
    {
        cout << " " << *c1_cPtr;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1 ptr = c1.data();
    *c1 ptr = 20;
    for (size_t n = c1.size(); 0 < n; --n, c1 ptr++)
    {
        cout << " " << *c1 ptr;
    }
    cout << endl;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="difference_type"></a>difference_type

Typ, który zawiera różnicę między dwoma iteratorami odwołującymi się do elementów w obrębie tego samego wektora.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` Można również opisać jako liczbę elementów między dwoma wskaźnikami, ponieważ wskaźnik do elementu zawiera swój adres.

[Iterator](#iterator) jest najczęściej używany do uzyskiwania dostępu do elementu Vector.

### <a name="example"></a>Przykład

```cpp
// vector_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <vector>
#include <algorithm>

int main( )
{
   using namespace std;

   vector <int> c1;
   vector <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   vector <int>::difference_type   df_typ1, df_typ2, df_typ3;

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

Wstawia element skonstruowany w miejscu do wektora w określonym położeniu.

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>Parametry

*_Where*\
Pozycja w wektorze [](../standard-library/vector-class.md) , w której wstawiany jest pierwszy element.

*użyte*\
Wartość wstawianego elementu do `vector`.

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca iterator, który wskazuje na położenie, w którym nowy element został wstawiony do `vector`.

### <a name="remarks"></a>Uwagi

Każda operacja wstawiania może być kosztowna, zobacz [Klasa Vector](../standard-library/vector-class.md) w celu omówienia `vector` wydajności.

### <a name="example"></a>Przykład

```cpp
// vector_emplace.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.emplace( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
vv1[0] = 10 20 30
```

## <a name="emplace_back"></a>emplace_back

Dodaje element skonstruowany w miejscu do końca wektora.

```cpp
template <class... Types>
void emplace_back(Types&&... _Args);
```

### <a name="parameters"></a>Parametry

*_Args*\
Argumenty konstruktora. Funkcja wnioskuje, jakie przeciążenie konstruktora ma zostać wywołane na podstawie podanych argumentów.

### <a name="example"></a>Przykład

```cpp
#include <vector>
struct obj
{
   obj(int, double) {}
};

int main()
{
   std::vector<obj> v;
   v.emplace_back(1, 3.14); // obj in created in place in the vector
}
```

## <a name="empty"></a>ciągiem

Testuje, czy wektor jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli wektor jest pusty. **Fałsz** , jeśli wektor nie jest pusty.

### <a name="example"></a>Przykład

```cpp
// vector_empty.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );

   if ( v1.empty( ) )
      cout << "The vector is empty." << endl;
   else
      cout << "The vector is not empty." << endl;
}
```

```Output
The vector is not empty.
```

## <a name="end"></a>punktów

Zwraca iterator poza końcem.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Wartość zwracana

Poprzedni-końcowy iterator dla wektora. Jeśli wektor jest pusty, `vector::end() == vector::begin()`.

### <a name="remarks"></a>Uwagi

Jeśli wartość `end` zwracana jest przypisana do zmiennej typu `const_iterator`, nie można zmodyfikować obiektu wektora. Jeśli wartość `end` zwracana jest przypisana do zmiennej typu `iterator`, można zmodyfikować obiekt wektora.

### <a name="example"></a>Przykład

```cpp
// vector_end.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << endl;
}
```

```Output
1
2
```

## <a name="erase"></a>Wyłączanie

Usuwa element lub zakres elementów w wektorze z określonych pozycji.

```cpp
iterator erase(
    const_iterator _Where);

iterator erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

*_Where*\
Pozycja elementu, który ma zostać usunięty z wektora.

*pierwszego*\
Pozycja pierwszego elementu usuniętego z wektora.

*ostatniego*\
Umieść tuż poza ostatnim elementem usuniętym z wektora.

### <a name="return-value"></a>Wartość zwracana

Iterator, który wyznacza pierwszy element pozostający poza elementami usuniętymi lub wskaźnik do końca wektora, jeśli taki element nie istnieje.

### <a name="example"></a>Przykład

```cpp
// vector_erase.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );
   v1.push_back( 40 );
   v1.push_back( 50 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) + 1, v1.begin( ) + 3 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
v1 = 10 20 30 40 50
v1 = 20 30 40 50
v1 = 20 50
```

## <a name="front"></a>FSB

Zwraca odwołanie do pierwszego elementu w wektorze.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do pierwszego elementu w obiekcie Vector. Jeśli wektor jest pusty, zwracany jest niezdefiniowany.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana elementu `front` jest przypisana `const_reference`do, nie można zmodyfikować obiektu wektora. Jeśli wartość `front` zwracana jest przypisana do **odwołania**, obiekt Vector może być modyfikowany.

Podczas kompilowania przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowanego jako 1 lub 2, wystąpi błąd czasu wykonywania, jeśli próbujesz uzyskać dostęp do elementu w pustym wektorze.  Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md) .

### <a name="example"></a>Przykład

```cpp
// vector_front.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.front( );
   const int& ii = v1.front( );

   cout << "The first integer of v1 is "<< i << endl;
   // by incrementing i, we move the front reference to the second element
   i++;
   cout << "Now, the first integer of v1 is "<< i << endl;
}
```

## <a name="get_allocator"></a>get_allocator

Zwraca kopię obiektu alokatora użytego do skonstruowania wektora.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez wektor.

### <a name="remarks"></a>Uwagi

Przypisania klasy Vector określają sposób zarządzania magazynem przez klasę. Domyślne przydzielenie klas kontenerów C++ biblioteki standardowej jest wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym C++ tematem.

### <a name="example"></a>Przykład

```cpp
// vector_get_allocator.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   vector<int> v1;
   vector<int, allocator<int> > v2 = vector<int, allocator<int> >(allocator<int>( )) ;

   // v3 will use the same allocator class as v1
   vector <int> v3( v1.get_allocator( ) );

   vector<int>::allocator_type xvec = v3.get_allocator( );
   // You can now call functions on the allocator class used by vec
}
```

## <a name="insert"></a>wstawienia

Wstawia element lub liczbę elementów lub zakres elementów do wektora w określonym położeniu.

```cpp
iterator insert(
    const_iterator _Where,
    const Type& val);

iterator insert(
    const_iterator _Where,
    Type&& val);

void insert(
    const_iterator _Where,
    size_type count,
    const Type& val);

template <class InputIterator>
void insert(
    const_iterator _Where,
    InputIterator first,
    InputIterator last);
```

### <a name="parameters"></a>Parametry

*_Where*\
Pozycja w wektorze, w której wstawiany jest pierwszy element.

*użyte*\
Wartość wstawianego elementu do wektora.

*liczbą*\
Liczba elementów wstawianych do wektora.

*pierwszego*\
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*ostatniego*\
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie `insert` funkcje zwracają iterator, który wskazuje na położenie, w którym nowy element został wstawiony do wektora.

### <a name="remarks"></a>Uwagi

Jako warunek wstępny, *First* i *Last* nie mogą być iteratorami do wektora lub zachowanie jest niezdefiniowane. Każda operacja wstawiania może być kosztowna, zobacz [Klasa Vector](../standard-library/vector-class.md) w celu omówienia `vector` wydajności.

### <a name="example"></a>Przykład

```cpp
// vector_insert.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.insert( v1.begin( ) + 1, 40 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
   v1.insert( v1.begin( ) + 2, 4, 50 );

   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   const auto v2 = v1;
   v1.insert( v1.begin( )+1, v2.begin( )+2, v2.begin( )+4 );
   cout << "v1 =";
   for (Iter = v1.begin( ); Iter != v1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.insert( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
v1 = 10 40 20 30
v1 = 10 40 50 50 50 50 20 30
v1 = 10 50 50 40 50 50 50 50 20 30
vv1[0] = 10 50 50 40 50 50 50 50 20 30
```

## <a name="iterator"></a>Iterator

Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać lub zmodyfikować dowolny element w wektorze.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

**Iterator** typu może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpoczęcia](#begin).

## <a name="max_size"></a>max_size

Zwraca maksymalną długość wektora.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna możliwa długość wektora.

### <a name="example"></a>Przykład

```cpp
// vector_max_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   i = v1.max_size( );
   cout << "The maximum possible length of the vector is " << i << "." << endl;
}
```

## <a name="op_at"></a>operator []

Zwraca odwołanie do elementu wektora na określonej pozycji.

```cpp
reference operator[](size_type Pos);

const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>Parametry

*Terminal*\
Położenie elementu wektora.

### <a name="return-value"></a>Wartość zwracana

Jeśli określona pozycja jest większa niż lub równa rozmiarowi kontenera, wynik jest niezdefiniowany.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana elementu `operator[]` jest przypisana `const_reference`do, nie można zmodyfikować obiektu wektora. Jeśli wartość `operator[]` zwracana jest przypisana do odwołania, obiekt Vector może być modyfikowany.

Podczas kompilowania przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowanego jako 1 lub 2, wystąpi błąd czasu wykonywania, jeśli próbujesz uzyskać dostęp do elementu poza granicami wektora.  Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md) .

### <a name="example"></a>Przykład

```cpp
// vector_op_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   int& i = v1[1];
   cout << "The second integer of v1 is " << i << endl;
}
```

## <a name="op_eq"></a>operator =

Zastępuje elementy wektora kopią innego wektora.

```cpp
vector& operator=(const vector& right);

vector& operator=(vector&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Wektor](../standard-library/vector-class.md) kopiowany do `vector`.

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkich istniejących elementów w programie `vector`, `operator=` kopiuje lub przenosi `vector`zawartość *bezpośrednio* do.

### <a name="example"></a>Przykład

```cpp
// vector_operator_as.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> v1, v2, v3;
   vector<int>::iterator iter;

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
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a>przytrzymaj

Typ, który dostarcza wskaźnik do elementu w wektorze.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Uwagi

**Wskaźnik** typu może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

```cpp
// vector_pointer.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
    using namespace std;
    vector<int> v;
    v.push_back( 11 );
    v.push_back( 22 );

    vector<int>::pointer ptr = &v[0];
    cout << *ptr << endl;
    ptr++;
    cout << *ptr << endl;
    *ptr = 44;
    cout << *ptr << endl;
}
```

```Output
11
22
44
```

## <a name="pop_back"></a>pop_back

Usuwa element na końcu wektora.

```cpp
void pop_back();
```

### <a name="remarks"></a>Uwagi

Aby zapoznać się z przykładowym kodem, zobacz [Vector::p ush_back ()](#push_back).

## <a name="push_back"></a>push_back

Dodaje element na końcu wektora.

```cpp
void push_back(const T& Val);

void push_back(T&& Val);
```

### <a name="parameters"></a>Parametry

*Użyte*\
Wartość do przypisania do elementu dodanego do końca wektora.

### <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << "  " << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

int main()
{
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(10 + i);
    }

    cout << "vector data: " << endl;
    print_collection(v);

    // pop_back() until it's empty, printing the last element as we go
    while (v.begin() != v.end()) {
        cout << "v.back(): "; print_elem(v.back()); cout << endl;
        v.pop_back();
    }
}
```

## <a name="rbegin"></a>rbegin

Zwraca iterator do pierwszego elementu w odwróconym wektorze.

```cpp
reverse_iterator rbegin();
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator odwrotnego dostępu swobodnego, odnoszący się do pierwszego elementu w odwróconym wektorze lub adresowania ostatniego elementu w nieodwróconym wektorze.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana elementu `rbegin` jest przypisana `const_reverse_iterator`do, nie można zmodyfikować obiektu wektora. Jeśli wartość `rbegin` zwracana jest przypisana `reverse_iterator`do, obiekt Vector może być modyfikowany.

### <a name="example"></a>Przykład

```cpp
// vector_rbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.rbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="reference"></a>odwoła

Typ, który zawiera odwołanie do elementu przechowywanego w wektorze.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Przykład

Zobacz [na](#at) przykład, jak używać **odwołania** w klasie Vector.

## <a name="rend"></a>rend

Zwraca iterator, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym wektorze.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dostępu swobodnego, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym wektorze (lokalizacja, która poprzedza pierwszy element w wektorze nieodwróconym).

### <a name="remarks"></a>Uwagi

`rend`jest używany z odwróconym wektorem, tak jak [koniec](#end) jest używany z wektorem.

Jeśli wartość zwracana elementu `rend` jest przypisana `const_reverse_iterator`do, obiekt Vector nie może być modyfikowany. Jeśli wartość zwracana elementu `rend` jest przypisana `reverse_iterator`do, można zmodyfikować obiekt wektora.

`rend`może służyć do sprawdzenia, czy iterator odwrotny osiągnął koniec jego wektora.

Nie można usunąć odwołania `rend` do wartości zwracanej przez.

### <a name="example"></a>Przykład

```cpp
// vector_rend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="reserve"></a>zarezerwować

Rezerwuje minimalną długość magazynu dla obiektu Vector, przydzielając miejsce w razie potrzeby.

```cpp
void reserve(size_type count);
```

### <a name="parameters"></a>Parametry

*liczbą*\
Minimalna długość magazynu do przydzielenia dla wektora.

### <a name="example"></a>Przykład

```cpp
// vector_reserve.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
```

## <a name="resize"></a>Zmień rozmiar

Określa nowy rozmiar wektora.

```cpp
void resize(size_type Newsize);
void resize(size_type Newsize, Type Val);
```

### <a name="parameters"></a>Parametry

*NewSize*\
Nowy rozmiar wektora.

*Użyte*\
Wartość inicjująca nowych elementów dodanych do wektora, jeśli nowy rozmiar jest większy niż rozmiar oryginalny. W przypadku pominięcia wartości nowe obiekty używają ich domyślnego konstruktora.

### <a name="remarks"></a>Uwagi

Jeśli rozmiar kontenera jest mniejszy niż żądany rozmiar, *NewSize*, elementy są dodawane do wektora do momentu osiągnięcia żądanego rozmiaru. Jeśli rozmiar kontenera jest większy niż żądany rozmiar, elementy znajdujące się najbliżej końca kontenera są usuwane, dopóki rozmiar kontenera osiągnie wartość *NewSize*. Jeśli obecny rozmiar kontenera jest taki sam jak żądany rozmiar, nie jest podejmowana żadna akcja.

[rozmiar](#size) odzwierciedla bieżący rozmiar wektora.

### <a name="example"></a>Przykład

```cpp
// vectorsizing.cpp
// compile with: /EHsc /W4
// Illustrates vector::reserve, vector::max_size,
// vector::resize, vector::resize, and vector::capacity.
//
// Functions:
//
//    vector::max_size - Returns maximum number of elements vector could
//                       hold.
//
//    vector::capacity - Returns number of elements for which memory has
//                       been allocated.
//
//    vector::size - Returns number of elements in the vector.
//
//    vector::resize - Reallocates memory for vector, preserves its
//                     contents if new size is larger than existing size.
//
//    vector::reserve - Allocates elements for vector to ensure a minimum
//                      size, preserving its contents if the new size is
//                      larger than existing size.
//
//    vector::push_back - Appends (inserts) an element to the end of a
//                        vector, allocating memory for it if necessary.
//
//////////////////////////////////////////////////////////////////////

// The debugger cannot handle symbols more than 255 characters long.
// The C++ Standard Library often creates symbols longer than that.
// The warning can be disabled:
//#pragma warning(disable:4786)

#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }
    cout << endl;
}

void printvstats(const vector<int>& v) {
    cout << "   the vector's size is: " << v.size() << endl;
    cout << "   the vector's capacity is: " << v.capacity() << endl;
    cout << "   the vector's maximum size is: " << v.max_size() << endl;
}

int main()
{
    // declare a vector that begins with 0 elements.
    vector<int> v;

    // Show statistics about vector.
    cout << endl << "After declaring an empty vector:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Add one element to the end of the vector.
    v.push_back(-1);
    cout << endl << "After adding an element:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }
    cout << endl << "After adding 10 elements:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(6);
    cout << endl << "After resizing to 6 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(9, 999);
    cout << endl << "After resizing to 9 elements with an initialization value of 999:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(12);
    cout << endl << "After resizing to 12 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Ensure there's room for at least 1000 elements.
    v.reserve(1000);
    cout << endl << "After vector::reserve(1000):" << endl;
    printvstats(v);

    // Ensure there's room for at least 2000 elements.
    v.resize(2000);
    cout << endl << "After vector::resize(2000):" << endl;
    printvstats(v);
}
```

## <a name="reverse_iterator"></a>reverse_iterator

Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać lub zmodyfikować dowolny element w odwróconym wektorze.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iteracji w odróżnieniu od wektora.

### <a name="example"></a>Przykład

Zobacz przykład dla [rbegin](#rbegin).

## <a name="shrink_to_fit"></a>shrink_to_fit

Odrzuca nadmiarową pojemność.

```cpp
void shrink_to_fit();
```

### <a name="example"></a>Przykład

```cpp
// vector_shrink_to_fit.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.shrink_to_fit();
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
Current capacity of v1 = 1
```

## <a name="size"></a>zmienia

Zwraca liczbę elementów w wektorze.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość wektora.

### <a name="example"></a>Przykład

```cpp
// vector_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   v1.push_back( 1 );
   i = v1.size( );
   cout << "Vector length is " << i << "." << endl;

   v1.push_back( 2 );
   i = v1.size( );
   cout << "Vector length is now " << i << "." << endl;
}
```

```Output
Vector length is 1.
Vector length is now 2.
```

## <a name="size_type"></a>size_type

Typ, który zlicza liczbę elementów w wektorze.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [pojemności](#capacity).

## <a name="swap"></a>wymiany

Wymienia elementy dwóch wektorów.

```cpp
void swap(
    vector<Type, Allocator>& right);

friend void swap(
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Wektor udostępniający elementy do zamiany lub wektor, którego elementy mają być wymieniane z pozostałymi środkami wektora.

*lewym*\
Wektor, którego elementy są wymieniane z prawami do wektora.

### <a name="example"></a>Przykład

```cpp
// vector_swap.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1, v2;

   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 3 );

   v2.push_back( 10 );
   v2.push_back( 20 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
   cout << endl;

   v1.swap( v2 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
}
```

```Output
The number of elements in v1 = 3
The number of elements in v2 = 2

The number of elements in v1 = 2
The number of elements in v2 = 3
```

## <a name="value_type"></a>value_type

Typ, który reprezentuje typ danych przechowywany w wektorze.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Uwagi

`value_type`jest synonimem dla parametru `Type`szablonu.

### <a name="example"></a>Przykład

```cpp
// vector_value_type.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="vector"></a>niemożliwe

Konstruuje wektor o określonym rozmiarze lub z elementami określonej wartości lub z określonym alokatorem lub jako kopią całości lub części innego wektora.

```cpp
vector();
explicit vector(const Allocator& Al);
explicit vector(size_type Count);
vector(size_type Count, const Type& Val);
vector(size_type Count, const Type& Val, const Allocator& Al);

vector(const vector& Right);
vector(vector&& Right);
vector(initializer_list<Type> IList, const _Allocator& Al);

template <class InputIterator>
vector(InputIterator First, InputIterator Last);
template <class InputIterator>
vector(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>Parametry

*Wsp*\
Klasa alokatora do wykorzystania z tym obiektem. [get_allocator](#get_allocator) zwraca klasę alokatora dla obiektu.

*Liczbą*\
Liczba elementów w skonstruowanym wektorze.

*Użyte*\
Wartość elementów w skonstruowanym wektorze.

*Kliknij*\
Wektor, którego skonstruowany wektor ma być kopią.

*Pierwszego*\
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*Ostatniego*\
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

*IList*\
Initializer_list zawierający elmeents do skopiowania.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują obiekt alokatora (*Al*) i inicjują wektor.

Pierwsze dwa konstruktory określają pusty wektor początkowy. Drugi jawnie określa typ alokatora (*Al*), który ma być używany.

Trzeci konstruktor określa powtarzanie określonej liczby (*Count*) elementów wartości domyślnej dla klasy `Type`.

Czwarty i piąty konstruktory określają powtórzenia (*Count*) elementów wartości *Val*.

Szósty konstruktor określa kopię *po prawej stronie*wektora.

Siódmy Konstruktor przenosi *prawo*wektora.

Ósmy Konstruktor używa elementu initializer_list, aby określić elementy.

"Dziewiąte i dziesiąte konstruktory"`First`kopiują zakres [, `Last`) wektora.

### <a name="example"></a>Przykład

```cpp
// vector_ctor.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector <int>::iterator v1_Iter, v2_Iter, v3_Iter, v4_Iter, v5_Iter, v6_Iter;

    // Create an empty vector v0
    vector <int> v0;

    // Create a vector v1 with 3 elements of default value 0
    vector <int> v1(3);

    // Create a vector v2 with 5 elements of value 2
    vector <int> v2(5, 2);

    // Create a vector v3 with 3 elements of value 1 and with the allocator
    // of vector v2
    vector <int> v3(3, 1, v2.get_allocator());

    // Create a copy, vector v4, of vector v2
    vector <int> v4(v2);

    // Create a new temporary vector for demonstrating copying ranges
    vector <int> v5(5);
    for (auto i : v5) {
        v5[i] = i;
    }

    // Create a vector v6 by copying the range v5[ first,  last)
    vector <int> v6(v5.begin() + 1, v5.begin() + 3);

    cout << "v1 =";
    for (auto& v : v1){
        cout << " " << v;
    }
    cout << endl;

    cout << "v2 =";
    for (auto& v : v2){
        cout << " " << v;
    }
    cout << endl;

    cout << "v3 =";
    for (auto& v : v3){
        cout << " " << v;
    }
    cout << endl;
    cout << "v4 =";
    for (auto& v : v4){
        cout << " " << v;
    }
    cout << endl;

    cout << "v5 =";
    for (auto& v : v5){
        cout << " " << v;
    }
    cout << endl;

    cout << "v6 =";
    for (auto& v : v6){
        cout << " " << v;
    }
    cout << endl;

    // Move vector v2 to vector v7
    vector <int> v7(move(v2));
    vector <int>::iterator v7_Iter;

    cout << "v7 =";
    for (auto& v : v7){
        cout << " " << v;
    }
    cout << endl;

    vector<int> v8{ { 1, 2, 3, 4 } };
    for (auto& v : v8){
        cout << " " << v ;
    }
    cout << endl;
}
```

```Output
v1 = 0 0 0v2 = 2 2 2 2 2v3 = 1 1 1v4 = 2 2 2 2 2v5 = 0 1 2 3 4v6 = 1 2v7 = 2 2 2 2 21 2 3 4
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
