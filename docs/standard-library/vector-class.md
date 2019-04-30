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
ms.openlocfilehash: 80416e3af18774a7a8bf64264dca2906995ae202
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410905"
---
# <a name="vector-class"></a>vector — Klasa

Klasa vector standardowej biblioteki języka C++ jest klasą szablonu, kontenerów sekwencji, które Rozmieść elementy danego typu w układzie liniowych i zezwolić na dostęp szybkiego losowego do dowolnego elementu. Powinny one być preferowane kontenerów sekwencji, gdy wydajność dostępu swobodnego znajduje się w warstwie premium.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Allocator = allocator<Type>>
class vector
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Typ danych elementu, który ma być przechowywany w wektora

*Allocator*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i dezalokacji pamięci wektora. Ten argument jest opcjonalny, a wartość domyślna to `allocator<Type>`.

## <a name="remarks"></a>Uwagi

Wektory zezwala na stałym czasie wstawienia i usunięcia na końcu sekwencji. Wymaga liniowo, wstawiając lub usuwając elementy w środku wektora. Wydajność [deque — klasa](../standard-library/deque-class.md) kontener jest najlepsza w odniesieniu do wstawienia i usunięcia na początku i końca sekwencji. [List, klasa](../standard-library/list-class.md) kontener jest najlepsza w odniesieniu do wstawienia i usunięcia w dowolnym miejscu w sekwencji.

Ponowne przydzielenie wektor występuje, gdy składowa należy zwiększyć sekwencji zawartej w obiekcie wektor poza jego bieżąca pojemność magazynu. Inne wstawienia i wymazywania może zmienić różnych adresów pamięci masowej w sekwencji. We wszystkich tych przypadkach, iteratorów i odwołania, które wskazują na zmienionych części kolejności stają się nieprawidłowe. Jeśli nie ponowne przydzielenie występuje, tylko Iteratory i odwołania, zanim punkt wstawiania/usuwania ważność.

[Wektor\<bool > klasa](../standard-library/vector-bool-class.md) jest pełna specjalizacją wektora klasy szablonu dla elementów typu bool, alokator dla podstawowego typu, które są używane przez specjalizację.

[Wektor\<bool > reference — klasa](../standard-library/vector-bool-class.md#reference_class) to klasa zagnieżdżona, w których obiekty są w stanie dostarczyć odniesienia do elementów (pojedynczych bitów) w obrębie wektor\<bool > obiektu.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Wektor](#vector)|Konstruuje wektor o określonym rozmiarze lub z elementami określonej wartości lub z określonego `allocator` lub jako kopię niektórych innych wektora.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje `allocator` klasy do obiektu wektora.|
|[const_iterator](#const_iterator)|Typ zapewniający iterator dostępu swobodnego, który może odczytać **const** elementu w wektorze.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do **const** elementu w wektorze.|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do **const** elementu przechowywanego w wektorze do odczytu i wykonywania **const** operacji.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ zapewniający iterator dostępu swobodnego, który może odczytać dowolny **const** elementu w wektorze.|
|[difference_type](#difference_type)|Typ, który zawiera różnicę między adresami dwóch elementów w wektorze.|
|[iterator](#iterator)|Typ, który dostarcza iterator dostępu swobodnego, który może odczytać lub zmodyfikować dowolny element w wektorze.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu w wektorze.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w wektorze.|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza iterator dostępu swobodnego, który może odczytać lub zmodyfikować dowolny element w odwróconej wektora.|
|[size_type](#size_type)|Typ, który zlicza liczbę elementów w wektorze.|
|[value_type](#value_type)|Typ, który reprezentuje typ danych przechowywanych w wektorze.|

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Przypisz](#assign)|Wymazuje wektora i kopiuje określonych elementów do pustego wektora.|
|[at](#at)|Zwraca odwołanie do elementu w określonej lokalizacji w wektorze.|
|[back](#back)|Zwraca odwołanie do ostatniego elementu wektora.|
|[begin](#begin)|Zwraca iterator dostępu losowego do pierwszego elementu w wektorze.|
|[Pojemność](#capacity)|Zwraca liczbę elementów, które mogą zawierać wektora, bez przydzielania więcej pamięci masowej.|
|[cbegin](#cbegin)|Zwraca stały iterator dostępu losowego do pierwszego elementu w wektorze.|
|[cend](#cend)|Zwraca stały iterator dostępu swobodnego, który wskazuje tuż za koniec wektora.|
|[crbegin](#crbegin)|Zwraca const iterator do pierwszego elementu w odwróconym wektora.|
|[crend](#crend)|Zwraca const iterator-to-end odwróconej wektora.|
|[Usuń zaznaczenie](#clear)|Usuwa elementów wektora.|
|[data](#data)|Zwraca wskaźnik do pierwszego elementu w wektorze.|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do wektora na określonej pozycji.|
|[emplace_back](#emplace_back)|Dodaje element skonstruowany w miejscu do końca wektora.|
|[pusty](#empty)|Sprawdza, czy kontener wektora jest pusty.|
|[koniec](#end)|Zwraca iterator dostępu swobodnego, który wskazuje na końcu elementu wektora.|
|[wymazywanie](#erase)|Usuwa element lub zakres elementów w wektorze z określonych pozycji.|
|[Frontonu](#front)|Zwraca odwołanie do pierwszego elementu w wektorze.|
|[get_allocator](#get_allocator)|Zwraca obiekt, do którego `allocator` klasy używane przez wektora.|
|[insert](#insert)|Wstawia element lub szereg elementów do wektora na określonej pozycji.|
|[max_size](#max_size)|Zwraca maksymalną długość wektora.|
|[pop_back](#pop_back)|Usuwa element na końcu wektora.|
|[push_back](#push_back)|Dodaj element do końca wektora.|
|[rbegin](#rbegin)|Zwraca iterator do pierwszego elementu w odwróconym wektora.|
|[rend](#rend)|Zwraca iterator do końca odwróconej wektora.|
|[reserve](#reserve)|Rezerwuje o długości minimalnej pamięci masowej dla obiektu wektora.|
|[Zmiana rozmiaru](#resize)|Określa nowy rozmiar wektora.|
|[shrink_to_fit](#shrink_to_fit)|Odrzuca nadmiarowej pojemności.|
|[Rozmiar](#size)|Zwraca liczbę elementów w wektorze.|
|[swap](#swap)|Zamienia elementy z dwoma wektorami.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator&#91;&#93;](#op_at)|Zwraca odwołanie do elementu wektora na określonej pozycji.|
|[operator=](#op_eq)|Zastępuje elementów wektora kopią innego wektora.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wektor >

**Namespace:** standardowe

## <a name="allocator_type"></a>  Vector::allocator_type

Typ, który reprezentuje klasę alokatora dla obiektu wektora.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type` synonim dla parametru szablonu jest `Allocator`.

### <a name="example"></a>Przykład

Zobacz przykład [get_allocator —](#get_allocator) przykład, który używa `allocator_type`.

## <a name="assign"></a>  Vector::ASSIGN

Wymazuje wektora i kopiuje określonych elementów do pustego wektora.

```cpp
void assign(size_type Count, const Type& Val);
void assign(initializer_list<Type> IList);

template <class InputIterator>
void assign(InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*ostatni*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

*Liczba*<br/>
Liczba kopii element jest wstawiany do wektora.

*Val*<br/>
Wartość elementu jest wstawiany do wektora.

*IList*<br/>
Lista initializer_list zawierająca elementy do wstawienia.

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkie elementy istniejących w wektorze, przypisz albo wstawia określony zakres elementów z oryginalnego wektora do wektora lub wstawia kopii nowego elementu z określoną wartością do wektora.

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

## <a name="at"></a>  Vector::AT

Zwraca odwołanie do elementu w określonej lokalizacji w wektorze.

```cpp
reference at(size_type _Pos);

const_reference at(size_type _Pos) const;
```

### <a name="parameters"></a>Parametry

*_Pos*<br/>
Numer indeksu dolnego lub pozycji elementu, aby odwoływać się w wektorze.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu indeksowanych w argumencie. Jeśli `_Off` jest większy niż rozmiar wektora, `at` zgłasza wyjątek.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `at` jest przypisany do `const_reference`, nie można zmodyfikować obiektu wektora. Jeśli wartość zwracaną przez `at` jest przypisany do `reference`, można zmodyfikować obiekt wektora.

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

## <a name="back"></a>  Vector::back

Zwraca odwołanie do ostatniego elementu wektora.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Ostatni element wektora. Jeśli wektora jest pusta, zwracana wartość jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `back` jest przypisany do `const_reference`, nie można zmodyfikować obiektu wektora. Jeśli wartość zwracaną przez `back` jest przypisany do `reference`, można zmodyfikować obiekt wektora.

Gdy kompilowany przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowana jako 1 lub 2, błąd czasu wykonywania występuje, jeśli użytkownik podejmie próbę uzyskania dostępu do elementu w pustego wektora.  Zobacz [Checked Iterators](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

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

## <a name="begin"></a>  Vector::BEGIN

Zwraca iterator dostępu losowego do pierwszego elementu w wektorze.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu swobodnego, odnoszący się do pierwszego elementu w `vector` lub do lokalizacji następującej po pustą `vector`. Zawsze należy porównać wartości zwracanej z [vector::end](#end) aby upewnić się, jest on prawidłowy.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `begin` jest przypisany do [vector::const_iterator](#const_iterator), `vector` nie można zmodyfikować obiektu. Jeśli wartość zwracaną przez `begin` jest przypisany do [vector::iterator](#iterator), `vector` można zmodyfikować obiektu.

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

## <a name="capacity"></a>  Vector::Capacity

Zwraca liczbę elementów, które mogą zawierać wektora, bez przydzielania więcej pamięci masowej.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość Magazyn przydzielony do wektora.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego [rozmiar](#resize) będzie bardziej wydajne, jeśli wystarczającą ilość pamięci jest przydzielany do je. Użyć funkcji elementu członkowskiego [zarezerwować](#reserve) Aby określić ilość pamięci przydzielonej.

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

## <a name="cbegin"></a>  Vector::cbegin

Zwraca **const** iterator odnoszący się do pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

A **const** iteratora dostępu swobodnego, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).

### <a name="remarks"></a>Uwagi

Wartością zwracaną `cbegin`, nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast `begin()` funkcja elementu członkowskiego w celu zagwarantowania, że wartość zwracana jest `const_iterator`. Zazwyczaj jest używana w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowem kluczowym dedukcji, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` jako modyfikowalny (nie - **const**) kontener dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  Vector::cend

Zwraca **const** iterator adresujący lokalizację tuż za ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

A **const** iteratora dostępu swobodnego, który wskazuje tuż za koniec zakresu.

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

## <a name="clear"></a>  Vector::Clear

Usuwa elementów wektora.

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

## <a name="const_iterator"></a>  Vector::const_iterator

Typ zapewniający iterator dostępu swobodnego, który może odczytać **const** elementu w wektorze.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [ponownie](#back) przykład, który używa `const_iterator`.

## <a name="const_pointer"></a>  Vector::const_pointer

Typ, który dostarcza wskaźnik do **const** elementu w wektorze.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

[Iteratora](#iterator) częściej umożliwia dostęp do elementu wektora.

## <a name="const_reference"></a>  Vector::const_reference

Typ, który zawiera odwołanie do **const** elementu przechowywanego w wektorze do odczytu i wykonywania **const** operacji.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

Typ `const_reference` nie może służyć do modyfikowania wartości elementu.

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

## <a name="const_reverse_iterator"></a>  Vector::const_reverse_iterator

Typ zapewniający iterator dostępu swobodnego, który może odczytać dowolny **const** elementu w wektorze.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i jest używany do iterowania po wektora w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz [rbegin —](#rbegin) przykładowy sposób deklarowania i użyć iteratora.

## <a name="crbegin"></a>  Vector::crbegin

Zwraca const iterator do pierwszego elementu w odwróconym wektora.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iteratora dostępu swobodnego, odnoszący się do pierwszego elementu w odwróconej [wektor](../standard-library/vector-class.md) lub adresowania, który był ostatnim elementem w nieodwróconej `vector`.

### <a name="remarks"></a>Uwagi

Wartością zwracaną `crbegin`, `vector` nie można zmodyfikować obiektu.

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

## <a name="crend"></a>  Vector::crend

Zwraca iterator stałych adresujący lokalizację następującą po ostatnim elemencie w odwróconej wektora.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iteratora dostępu swobodnego, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconej [wektor](../standard-library/vector-class.md) (miejsca przed pierwszym elementem w nieodwróconej `vector`).

### <a name="remarks"></a>Uwagi

`crend` jest używana z odwróconej `vector` podobnie jak [vector::cend](#cend) jest używana z `vector`.

Wartością zwracaną `crend` (odpowiednio odejmowane) `vector` nie można zmodyfikować obiektu.

`crend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej `vector`.

Wartość zwrócona przez obiekt `crend` nie należy usuwać odwołania.

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

## <a name="data"></a>  Vector::Data

Zwraca wskaźnik do pierwszego elementu w wektorze.

```cpp
const_pointer data() const;

pointer data();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego elementu w [wektor](../standard-library/vector-class.md) lub do lokalizacji następującej po pustą `vector`.

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

## <a name="difference_type"></a>  Vector::difference_type

Typ, który zawiera różnicę między dwoma iteratorami odwołującymi się do elementów w obrębie tego samego wektora.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Element `difference_type` można również określić jako liczbę elementów między dwoma wskaźnikami, ponieważ wskaźnik do elementu zawiera adres.

[Iteratora](#iterator) częściej umożliwia dostęp do elementu wektora.

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

## <a name="emplace"></a>  Vector::emplace

Wstawia element skonstruowany w miejscu do wektora na określonej pozycji.

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*_Where*|Pozycja w [wektor](../standard-library/vector-class.md) polegający na wstawieniu pierwszego elementu.|
|*Val*|Wartość elementu jest wstawiany do `vector`.|

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca iterator, który wskazuje miejsce, w którym wstawiono nowy element do `vector`.

### <a name="remarks"></a>Uwagi

Wszelkie operacje wstawiania może być kosztowne, zobacz [vector, klasa](../standard-library/vector-class.md) dyskusję na temat `vector` wydajności.

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

## <a name="emplace_back"></a>  Vector::emplace_back

Dodaje element skonstruowany w miejscu do końca wektora.

```cpp
template <class... Types>
void emplace_back(Types&&... _Args);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Args*|Argumenty konstruktora. Funkcja wnioskuje przeciążenia konstruktora, który można wywołać na podstawie argumentów, pod warunkiem.|

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

## <a name="empty"></a>  Vector::Empty

Sprawdza, czy wektor jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wektora jest pusta. **false** Jeśli wektora nie jest pusty.

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

## <a name="end"></a>  Vector::end

Zwraca iterator poza końcem.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator przeszłości end w wektorze. Jeśli wektora jest pusta, `vector::end() == vector::begin()`.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `end` jest przypisany do zmiennej typu `const_iterator`, nie można zmodyfikować obiektu wektora. Jeśli wartość zwracaną przez `end` jest przypisany do zmiennej typu `iterator`, można zmodyfikować obiekt wektora.

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

## <a name="erase"></a>  Vector::ERASE

Usuwa element lub zakres elementów w wektorze z określonych pozycji.

```cpp
iterator erase(
    const_iterator _Where);

iterator erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*_Where*|Pozycja elementu do usunięcia z wektora.|
|*pierwszy*|Pozycja pierwszego elementu są usuwane z wektora.|
|*last*|Pozycja tuż za ostatnim elementem usunięte z wektora.|

### <a name="return-value"></a>Wartość zwracana

Iterator opisujący pierwszy element pozostający poza wszelkimi elementami usuniętymi lub wskaźnik-to-end wektora, jeśli taki element nie istnieje.

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

## <a name="front"></a>  Vector::front

Zwraca odwołanie do pierwszego elementu w wektorze.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do pierwszego elementu w obiekcie wektora. Jeśli wektora jest pusta, zwracana wartość jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `front` jest przypisany do `const_reference`, nie można zmodyfikować obiektu wektora. Jeśli wartość zwracaną przez `front` jest przypisany do **odwołania**, można zmodyfikować obiekt wektora.

Gdy kompilowany przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowana jako 1 lub 2, błąd czasu wykonywania występuje, jeśli użytkownik podejmie próbę uzyskania dostępu do elementu w pustego wektora.  Zobacz [Checked Iterators](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

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

## <a name="get_allocator"></a>  Vector::get_allocator

Zwraca kopię obiektu programu przydzielania, używany do utworzenia wektora.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez wektora.

### <a name="remarks"></a>Uwagi

Puli buforów dla klasy vector Określ, jak klasa zarządza magazynem. Buforów domyślną dostarczony wraz z klasy kontenera standardowej biblioteki języka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.

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

## <a name="insert"></a>  Vector::INSERT

Wstawia element lub szereg elementów lub szereg elementów do wektora na określonej pozycji.

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

|Parametr|Opis|
|-|-|
|*_Where*|Pozycja w wektorze polegający na wstawieniu pierwszego elementu.|
|*Val*|Wartość elementu jest wstawiany do wektora.|
|*Liczba*|Liczba elementów jest wstawiany do wektora.|
|*pierwszy*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*last*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwa `insert` funkcje zwracają iterator, który wskazuje miejsce, w którym dodano nowy element do wektora.

### <a name="remarks"></a>Uwagi

Jako warunek wstępny do *pierwszy* i *ostatniego* nie może być Iteratory do wektora, lub zachowanie jest niezdefiniowane. Wszelkie operacje wstawiania może być kosztowne, zobacz [vector, klasa](../standard-library/vector-class.md) dyskusję na temat `vector` wydajności.

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

## <a name="iterator"></a>  Vector::iterator

Typ, który dostarcza iterator dostępu swobodnego, który może odczytać lub zmodyfikować dowolny element w wektorze.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

Typ **iteratora** może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin).

## <a name="max_size"></a>  Vector::max_size

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

## <a name="op_at"></a>  Vector::operator]

Zwraca odwołanie do elementu wektora na określonej pozycji.

```cpp
reference operator[](size_type Pos);

const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*punktu sprzedaży*|Położenie elementu wektora.|

### <a name="return-value"></a>Wartość zwracana

Jeśli określona pozycja jest większa niż lub równa rozmiarowi kontenera, wynik jest niezdefiniowany.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `operator[]` jest przypisany do `const_reference`, nie można zmodyfikować obiektu wektora. Jeśli wartość zwracaną przez `operator[]` jest przypisany do odwołania, można zmodyfikować obiektu wektora.

Gdy kompilowany przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowana jako 1 lub 2, błąd czasu wykonywania występuje, jeśli użytkownik podejmie próbę uzyskania dostępu do elementu poza granicami wektora.  Zobacz [Checked Iterators](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

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

## <a name="op_eq"></a>  Vector::operator =

Zastępuje elementów wektora kopią innego wektora.

```cpp
vector& operator=(const vector& right);

vector& operator=(vector&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*right*|[Wektor](../standard-library/vector-class.md) są kopiowane do `vector`.|

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkie elementy istniejących w `vector`, `operator=` kopiuje lub przenosi zawartość *prawo* do `vector`.

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

## <a name="pointer"></a>  Vector::Pointer

Typ, który dostarcza wskaźnik do elementu w wektorze.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ **wskaźnik** może służyć do modyfikowania wartości elementu.

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

## <a name="pop_back"></a>  Vector::pop_back

Usuwa element na końcu wektora.

```cpp
void pop_back();
```

### <a name="remarks"></a>Uwagi

Dla przykładu kodu zobacz [wektorów:: push_back()](#push_back).

## <a name="push_back"></a>  Vector::push_back

Dodaje element do końca wektora.

```cpp
void push_back(const T& Val);

void push_back(T&& Val);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość do przypisania do elementu umieszczona na końcu wektora.

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

## <a name="rbegin"></a>  Vector::rbegin

Zwraca iterator do pierwszego elementu w odwróconym wektora.

```cpp
reverse_iterator rbegin();
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnego iteratora dostępu swobodnego adresujący pierwszy element w odwróconej ataku lub adresowania, który był ostatnim elementem w wektorze nieodwróconej.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `rbegin` jest przypisany do `const_reverse_iterator`, nie można zmodyfikować obiektu wektora. Jeśli wartość zwracaną przez `rbegin` jest przypisany do `reverse_iterator`, można zmodyfikować obiekt wektora.

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

## <a name="reference"></a>  Vector::Reference

Typ, który zawiera odwołanie do elementu przechowywanego w wektorze.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Przykład

Zobacz [na](#at) przykład sposobu użycia **odwołania** w klasie wektora.

## <a name="rend"></a>  Vector::rend

Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w odwróconej wektora.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnego iteratora dostępu swobodnego, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconej wektora (miejsca przed pierwszego elementu w wektorze nieodwróconej).

### <a name="remarks"></a>Uwagi

`rend` jest używana z odwróconej wektor podobnie jak [zakończenia](#end) jest używana z wektora.

Jeśli wartość zwracaną przez `rend` jest przypisany do `const_reverse_iterator`, wówczas nie można zmodyfikować obiektu wektora. Jeśli wartość zwracaną przez `rend` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiekt wektora.

`rend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej wektora.

Wartość zwrócona przez obiekt `rend` nie należy usuwać odwołania.

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

## <a name="reserve"></a>  Vector::Reserve

Rezerwuje o długości minimalnej pamięci masowej dla obiektu wektorowego przydzielanie miejsca, w razie potrzeby.

```cpp
void reserve(size_type count);
```

### <a name="parameters"></a>Parametry

*Liczba*<br/>
Minimalna długość pamięci do przydzielenia w wektorze.

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

## <a name="resize"></a>  Vector::Resize

Określa nowy rozmiar wektora.

```cpp
void resize(size_type Newsize);
void resize(size_type Newsize, Type Val);
```

### <a name="parameters"></a>Parametry

*Newsize:*<br/>
Nowy rozmiar wektora.

*Val*<br/>
Wartość inicjalizacji nowe elementy dodane do wektora, jeśli nowy rozmiar jest większy, oryginalny rozmiar. Jeśli wartość zostanie pominięty, nowe obiekty, użyj ich domyślnego konstruktora.

### <a name="remarks"></a>Uwagi

Jeśli rozmiar kontenera jest mniejszy niż żądany rozmiar *Newsize*, elementy są dodawane do wektora, dopóki nie osiągnie żądanego rozmiaru. Jeśli jego rozmiar jest większy niż żądany rozmiar, najbliższe końca kontener elementów są usuwane, dopóki nie osiągnie rozmiar kontenera *Newsize*. Jeśli obecny rozmiar kontenera jest taki sam jak żądany rozmiar, nie podjęto żadnej akcji.

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

## <a name="reverse_iterator"></a>  Vector::reverse_iterator

Typ, który dostarcza iterator dostępu swobodnego, który może odczytać lub zmodyfikować dowolny element w odwróconej wektora.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iterowania po wektora w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład [rbegin —](#rbegin).

## <a name="shrink_to_fit"></a>  vector::shrink_to_fit

Odrzuca nadmiarowej pojemności.

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

## <a name="size"></a>  Vector::size

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

## <a name="size_type"></a>  Vector::size_type

Typ, który zlicza liczbę elementów w wektorze.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [pojemności](#capacity).

## <a name="swap"></a>  Vector::swap

Zamienia elementy z dwoma wektorami.

```cpp
void swap(
    vector<Type, Allocator>& right);

friend void swap(
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Wektor zawierająca elementy, które mają być zamienione lub wektora, której elementy są wymieniane z tymi wektora *po lewej stronie*.

*left*<br/>
Wektor, w której elementy są wymieniane z tymi wektora *prawo*.

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

## <a name="value_type"></a>  Vector::value_type

Typ, który reprezentuje typ danych przechowywanych w wektorze.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Uwagi

`value_type` synonim dla parametru szablonu jest `Type`.

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

## <a name="vector"></a>  Vector::Vector

Tworzy wektor o określonym rozmiarze lub z elementami określonej wartości lub z określonego programu przydzielania lub jako kopię całości lub części niektórych innych wektora.

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

|Parametr|Opis|
|-|-|
|*Al*|Klasa alokatora do wykorzystania z tym obiektem. [get_allocator —](#get_allocator) zwraca klasę alokatora dla obiektu.|
|*Liczba*|Liczba elementów w wektorze skonstruowany.|
|*Val*|Wartość elementów w wektorze skonstruowany.|
|*po prawej stronie*|Wektor, w której stworzonego elementu wektora jest kopią.|
|*pierwszy*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*ostatni*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|
|*IList*|Lista initializer_list zawierająca elmeents do skopiowania.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują obiekt programu przydzielania (*Al*) i inicjują wektor.

Dwa pierwsze konstruktory określają pusty wektor wstępny. Drugi jawnie określa typ programu przydzielania (*Al*) ma być używany.

Trzeci Konstruktor określa powtórzenie określonej liczby (*liczba*) elementów wartości domyślnej dla klasy `Type`.

Czwarty i piąty Konstruktor określają powtórzenia (*liczba*) elementów wartości *Val*.

Szósty Konstruktor Określa kopię wektora *po prawej stronie*.

Siódmego Konstruktor przenosi wektora *po prawej stronie*.

Konstruktor ósmego używa initializer_list w celu określenia elementów.

Dziewiąty i dziesiąty konstruktory kopiują zakres [ `First`, `Last`) wektora.

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

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
