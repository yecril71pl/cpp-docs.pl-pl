---
title: set — Klasa
ms.date: 11/04/2016
f1_keywords:
- set/std::set
- set/std::set::allocator_type
- set/std::set::const_iterator
- set/std::set::const_pointer
- set/std::set::const_reference
- set/std::set::const_reverse_iterator
- set/std::set::difference_type
- set/std::set::iterator
- set/std::set::key_compare
- set/std::set::key_type
- set/std::set::pointer
- set/std::set::reference
- set/std::set::reverse_iterator
- set/std::set::size_type
- set/std::set::value_compare
- set/std::set::value_type
- set/std::set::begin
- set/std::set::cbegin
- set/std::set::cend
- set/std::set::clear
- set/std::set::count
- set/std::set::crbegin
- set/std::set::crend
- set/std::set::emplace
- set/std::set::emplace_hint
- set/std::set::empty
- set/std::set::end
- set/std::set::equal_range
- set/std::set::erase
- set/std::set::find
- set/std::set::get_allocator
- set/std::set::insert
- set/std::set::key_comp
- set/std::set::lower_bound
- set/std::set::max_size
- set/std::set::rbegin
- set/std::set::rend
- set/std::set::size
- set/std::set::swap
- set/std::set::upper_bound
- set/std::set::value_comp
helpviewer_keywords:
- std::set [C++]
- std::set [C++], allocator_type
- std::set [C++], const_iterator
- std::set [C++], const_pointer
- std::set [C++], const_reference
- std::set [C++], const_reverse_iterator
- std::set [C++], difference_type
- std::set [C++], iterator
- std::set [C++], key_compare
- std::set [C++], key_type
- std::set [C++], pointer
- std::set [C++], reference
- std::set [C++], reverse_iterator
- std::set [C++], size_type
- std::set [C++], value_compare
- std::set [C++], value_type
- std::set [C++], begin
- std::set [C++], cbegin
- std::set [C++], cend
- std::set [C++], clear
- std::set [C++], count
- std::set [C++], crbegin
- std::set [C++], crend
- std::set [C++], emplace
- std::set [C++], emplace_hint
- std::set [C++], empty
- std::set [C++], end
- std::set [C++], equal_range
- std::set [C++], erase
- std::set [C++], find
- std::set [C++], get_allocator
- std::set [C++], insert
- std::set [C++], key_comp
- std::set [C++], lower_bound
- std::set [C++], max_size
- std::set [C++], rbegin
- std::set [C++], rend
- std::set [C++], size
- std::set [C++], swap
- std::set [C++], upper_bound
- std::set [C++], value_comp
ms.assetid: 8991f9aa-5509-4440-adc1-371512d32018
ms.openlocfilehash: e879e7ffd9f674769e32548195f5017e27e64576
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846241"
---
# <a name="set-class"></a>set — Klasa

Zestaw klas kontenerów standardowej biblioteki C++ służy do przechowywania i pobierania danych z kolekcji, w której wartości zawartych elementów są unikatowe i służą jako wartości klucza, zgodnie z którymi dane są automatycznie porządkowane. Nie można bezpośrednio zmienić wartości elementu w zestawie. Zamiast tego musisz usunąć stare wartości i wstawić elementy z nowymi wartościami.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

### <a name="parameters"></a>Parametry

*Głównych*\
Typ danych elementu, który ma być przechowywany w zestawie.

*Cech*\
Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w zestawie. Ten argument jest opcjonalny, a Predykat binarny **mniej** *\<Key>* jest wartością domyślną.

W języku C++ 14 można włączyć wyszukiwanie heterogeniczne, określając `std::less<>` `std::greater<>` predykat or, który nie ma parametrów typu. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie heterogeniczne w kontenerach asocjacyjnych](../standard-library/stl-containers.md#sequence_containers)

*Alokator*\
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji zestawu i dezalokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to `allocator<Key>` .

## <a name="remarks"></a>Uwagi

Standardowy zestaw bibliotek języka C++ to:

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza. Ponadto, jest prostym kontenerem asocjacyjnym, ponieważ jego wartości elementu są jego wartościami klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.

- Posortowany, ponieważ jego elementy są uporządkowane według wartości kluczy w kontenerze zgodnie z określoną funkcją porównywania.

- Unikatowy w tym sensie, że każdy z jego elementów musi mieć unikatowy klucz. Ponieważ zestaw jest również prostym kontenerem asocjacyjnym, jego elementy są również unikatowe.

Zestaw jest również opisany jako szablon klasy, ponieważ udostępniana funkcja jest rodzajowa i niezależna od określonego typu danych zawartych jako elementy. Typ danych, który ma być użyty, jest zamiast tego określony jako parametr w klasie szablonu wraz z funkcją porównania i alokatorem.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Kontenery asocjacyjne są zoptymalizowane dla operacji wyszukiwania, wstawiania oraz usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, są skuteczne, wykonując je w czasie, który jest średnio proporcjonalny do logarytmu liczby elementów w kontenerze. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Zestaw powinien być kontenerem asocjacyjnym z wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Elementy zestawu są unikatowe i służą jako ich własne klucze sortowania. Model dla tego typu konstrukcji jest uporządkowaną listą, np. wyrazów, w których wyrazy mogą występować tylko raz. Jeżeli zezwolono na wiele wystąpień wyrazów, odpowiednią strukturą kontenera będzie multiset. Gdyby wartości potrzebowały dołączenia do listy unikatowych słów kluczowych, mapa byłaby odpowiednią strukturą zawierającą te dane. Gdyby natomiast klucze nie były unikatowe, mapa wielokrotna byłaby kontenerem z wyboru.

Zestaw porządkuje sekwencję, która kontroluje, wywołując obiekt funkcji przechowywanej typu [key_compare](#key_compare). Ten przechowywany obiekt jest funkcją porównywania, do której można uzyskać dostęp, wywołując funkcję członkowską [key_comp](#key_comp). Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność, tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarny *f*( *x, y*) jest obiektem funkcji, który ma dwa obiekty argumentu *x* i *y* oraz wartość zwracaną **`true`** lub **`false`** . Kolejność nałożona na zestaw jest ścisłym słabym porządkowaniem, jeśli Predykat binarny jest niezwrotny, niesymetryczny i przechodni oraz jeśli równoważność jest przechodnia, gdzie dwa obiekty *x* i *y* są zdefiniowane jako równoważne, gdy zarówno *f*( *x, y*), jak i *f*( *y, x*) mają wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

W języku C++ 14 można włączyć wyszukiwanie heterogeniczne, określając `std::less<>` `std::greater<>` predykat or, który nie ma parametrów typu. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie heterogeniczne w kontenerach asocjacyjnych](../standard-library/stl-containers.md#sequence_containers)

Iterator dostarczony przez klasę zestawu jest iteratorem dwukierunkowym, ale funkcje składowych klasy [INSERT](#insert) i [Set](#set) mają wersje przyjmujące jako parametry szablonu słabszy iterator danych wejściowych, którego wymagania funkcjonalności są mniejsze niż te gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcjonalności, ale jest wystarczający, aby można było mówić istotnie o zakresie iteratorów [ `First` , `Last` ) w kontekście funkcji składowych klasy.

### <a name="constructors"></a>Konstruktory

|Nazwa|Opis|
|-|-|
|[zbiór](#set)|Konstruuje zestaw, który jest pusty lub jest kopią całości lub części innego zestawu.|

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje `allocator` klasę dla obiektu zestawu.|
|[const_iterator](#const_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać **`const`** element w zestawie.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do **`const`** elementu w zestawie.|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do **`const`** elementu przechowywanego w zestawie do odczytu i wykonania **`const`** operacji.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **`const`** element w zestawie.|
|[difference_type](#difference_type)|Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów zestawu w zakresie pomiędzy elementami wskazywanymi przez iteratory.|
|[Iterator](#iterator)|Typ, który dostarcza iterator dwukierunkowy do odczytu i modyfikacji dowolnego elementu w zestawie.|
|[key_compare](#key_compare)|Typ, który dostarcza obiekt funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w zestawie.|
|[key_type](#key_type)|Typ opisuje obiekt zapisany jako element zestawu w charakterze klucza sortowania.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu w zestawie.|
|[odwoła](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w zestawie.|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy do odczytu i modyfikacji elementu w odwróconym zestawie.|
|[size_type](#size_type)|Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w zestawie.|
|[value_compare](#value_compare)|Typ, który dostarcza obiekt funkcji, która może porównać dwa elementy jako klucze sortowania, aby określić ich względną kolejność w zestawie.|
|[value_type](#value_type)|Typ opisuje obiekt zapisany jako element zestawu w charakterze wartości.|

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[zaczną](#begin)|Zwraca iterator, który dotyczy pierwszego elementu w zestawie.|
|[cbegin](#cbegin)|Zwraca iterator const, który dotyczy pierwszego elementu w zestawie.|
|[cend](#cend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w zestawie.|
|[Wyczyść](#clear)|Usuwa wszystkie elementy zestawu.|
|[count](#count)|Zwraca liczbę elementów w zestawie, których klucz pasuje do klucza określonego jako parametr.|
|[crbegin —](#rbegin)|Zwraca iterator const, który dotyczy pierwszego elementu w odwróconym zestawie.|
|[crend](#rend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconym zestawie.|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do zestawu.|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do zestawu, ze wskazówką położenia.|
|[puste](#empty)|Sprawdza, czy zestaw jest pusty.|
|[punktów](#end)|Zwraca iterator odnoszący się do lokalizacji następującej po ostatnim elemencie w zestawie.|
|[equal_range](#equal_range)|Zwraca parę iteratorów odpowiednio do pierwszego elementu w zestawie przy użyciu klucza, który jest większy niż określony klucz, i do pierwszego elementu w zestawie przy użyciu klucza, który jest równy lub większy niż ten klucz.|
|[Wyłączanie](#erase)|Usuwa element lub zakres elementów w zestawie z określonych pozycji lub usuwa elementy, które odpowiadają określonemu kluczowi.|
|[find](#find)|Zwraca iterator odnoszący się do pierwszej lokalizacji elementu w zestawie, który ma klucz równoważny z określonym kluczem.|
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` obiektu użytego do skonstruowania zestawu.|
|[wstawienia](#insert)|Wstawia element lub zakres elementów do zestawu.|
|[key_comp](#key_comp)|Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w zestawie.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu w zestawie, z kluczem, który jest równy lub większy od określonego klucza.|
|[max_size](#max_size)|Zwraca maksymalną długość zestawu.|
|[rbegin](#rbegin)|Zwraca iterator odnoszący się do pierwszego elementu w odwróconym zestawie.|
|[rend](#rend)|Zwraca iterator odnoszący się do lokalizacji następującej po ostatnim elemencie w odwróconym zestawie.|
|[zmienia](#size)|Zwraca liczbę elementów w zestawie.|
|[wymiany](#swap)|Zamienia elementy z dwóch zestawów.|
|[upper_bound](#upper_bound)|Zwraca iterator do pierwszego elementu w zestawie z kluczem, który jest większy od określonego klucza.|
|[value_comp](#value_comp)|Pobiera kopię obiektu porównania, użytego do uporządkowania wartości elementów w zestawie.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[operator =](#op_eq)|Zastępuje elementy zestawu kopią innego zestawu.|

## <a name="allocator_type"></a><a name="allocator_type"></a> allocator_type

Typ, który reprezentuje klasę alokatora dla obiektu zestawu.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type` jest synonimem dla [alokatora](../standard-library/set-class.md)parametrów szablonu.

Zwraca obiekt funkcji używany przez zestaw wielokrotny do porządkowania jego elementów, który jest parametrem szablonu `Allocator` .

Aby uzyskać więcej informacji na temat `Allocator` , zobacz sekcję Uwagi w temacie [Ustawianie klasy](../standard-library/set-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [get_allocator](#get_allocator) , aby uzyskać przykład, który używa programu `allocator_type` .

## <a name="begin"></a><a name="begin"></a> zaczną

Zwraca iterator, który dotyczy pierwszego elementu w zestawie.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pierwszego elementu w zestawie lub lokalizacji, która powiodła się.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana elementu `begin` jest przypisana do `const_iterator` , elementy w obiekcie zestawu nie mogą być modyfikowane. Jeśli wartość zwracana `begin` jest przypisana do elementu `iterator` , można modyfikować elementy w obiekcie zestawu.

### <a name="example"></a>Przykład

```cpp
// set_begin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::const_iterator s1_cIter;

   s1.insert( 1 );
   s1.insert( 2 );
   s1.insert( 3 );

   s1_Iter = s1.begin( );
   cout << "The first element of s1 is " << *s1_Iter << endl;

   s1_Iter = s1.begin( );
   s1.erase( s1_Iter );

   // The following 2 lines would err because the iterator is const
   // s1_cIter = s1.begin( );
   // s1.erase( s1_cIter );

   s1_cIter = s1.begin( );
   cout << "The first element of s1 is now " << *s1_cIter << endl;
}
```

```Output
The first element of s1 is 1
The first element of s1 is now 2
```

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

Zwraca **`const`** iterator, który odnosi się do pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

**`const`** Iterator dostępu dwukierunkowego, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu `cbegin() == cend()` ).

### <a name="remarks"></a>Uwagi

Z wartością zwracaną `cbegin` nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast `begin()` funkcji składowej, aby zagwarantować, że wartość zwracana to `const_iterator` . Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy, `Container` że jest to modyfikowalny **`const`** kontener dowolnego rodzaju, który obsługuje `begin()` i `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> cend

Zwraca **`const`** iterator, który odnosi się do lokalizacji jedynie poza ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

**`const`** Iterator dostępu dwukierunkowego, który wskazuje tuż poza końcem zakresu.

### <a name="remarks"></a>Uwagi

`cend` służy do sprawdzania, czy iterator przeszedł koniec zakresu.

Można użyć tej funkcji elementu członkowskiego zamiast `end()` funkcji składowej, aby zagwarantować, że wartość zwracana to `const_iterator` . Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy, `Container` że jest to modyfikowalny **`const`** kontener dowolnego rodzaju, który obsługuje `end()` i `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Nie można usunąć odwołania do wartości zwracanej przez `cend` .

## <a name="clear"></a><a name="clear"></a> Wyczyść

Usuwa wszystkie elementy zestawu.

```cpp
void clear();
```

### <a name="example"></a>Przykład

```cpp
// set_clear.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 1 );
   s1.insert( 2 );

   cout << "The size of the set is initially " << s1.size( )
        << "." << endl;

   s1.clear( );
   cout << "The size of the set after clearing is "
        << s1.size( ) << "." << endl;
}
```

```Output
The size of the set is initially 2.
The size of the set after clearing is 0.
```

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać **`const`** element w zestawie.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może być używany do modyfikacji wartości elementu.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [rozpoczęcia](#begin) korzystania z programu `const_iterator` .

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

Typ, który dostarcza wskaźnik do **`const`** elementu w zestawie.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może być używany do modyfikacji wartości elementu.

W większości przypadków [const_iterator](#const_iterator) należy używać w celu uzyskania dostępu do elementów w obiekcie zestawu const.

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

Typ, który zawiera odwołanie do **`const`** elementu przechowywanego w zestawie do odczytu i wykonania **`const`** operacji.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Przykład

```cpp
// set_const_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the set is 10.
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> const_reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **`const`** element w zestawie.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartości elementu i służy do iterowania przez zestaw w odwrotnej postaci.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rend](#rend) , aby zapoznać się z przykładem sposobu deklarowania i używania `const_reverse_iterator` .

## <a name="count"></a><a name="count"></a> liczbą

Zwraca liczbę elementów w zestawie, których klucz pasuje do klucza określonego jako parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Klucz elementów do dopasowania z zestawu.

### <a name="return-value"></a>Wartość zwracana

1, jeśli zestaw zawiera element, którego klucz sortowania pasuje do klucza parametru. 0, jeśli zestaw nie zawiera elementu z pasującym kluczem.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę elementów w następującym zakresie:

\[ lower_bound (*klucz*), upper_bound (*klucz*)).

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie zestawu:: Count funkcja członkowska.

```cpp
// set_count.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    set<int> s1;
    set<int>::size_type i;

    s1.insert(1);
    s1.insert(1);

    // Keys must be unique in set, so duplicates are ignored
    i = s1.count(1);
    cout << "The number of elements in s1 with a sort key of 1 is: "
         << i << "." << endl;

    i = s1.count(2);
    cout << "The number of elements in s1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in s1 with a sort key of 1 is: 1.
The number of elements in s1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a><a name="crbegin"></a> crbegin —

Zwraca iterator const, który dotyczy pierwszego elementu w odwróconym zestawie.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stałe odwrotne Iteratory, odnoszące się do pierwszego elementu w odwróconym zestawie lub adresowania ostatniego elementu w nieodwróconym zestawie.

### <a name="remarks"></a>Uwagi

`crbegin` jest używany z odwróconym zestawem, tak jak [początek](#begin) jest używany z zestawem.

Z wartością zwracaną `crbegin` , nie można zmodyfikować obiektu zestawu.

### <a name="example"></a>Przykład

```cpp
// set_crbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crbegin( );
   cout << "The first element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
```

## <a name="crend"></a><a name="crend"></a> crend

Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconym zestawie.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Niepowodzenie odwrotnego iteratora dwukierunkowego, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym zestawie (lokalizacja, która poprzedza pierwszy element w nieodwróconym zestawie).

### <a name="remarks"></a>Uwagi

`crend` jest używany z odwróconym zestawem, tak jak [koniec](#end) jest używany z zestawem.

Z wartością zwracaną `crend` , nie można zmodyfikować obiektu zestawu. Nie można usunąć odwołania do wartości zwracanej przez `crend` .

`crend` może służyć do sprawdzenia, czy iterator odwrotny osiągnął koniec zestawu.

### <a name="example"></a>Przykład

```cpp
// set_crend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crend( );
   s1_crIter--;
   cout << "The last element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów zestawu w zakresie pomiędzy elementami wskazywanymi przez iteratory.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type`Jest typem zwracanym podczas odejmowania lub zwiększania przez Iteratory kontenera. `difference_type`Jest zazwyczaj używany do reprezentowania liczby elementów w zakresie *[First, Last)* między iteratorami `first` i `last` , zawiera element wskazywany przez `first` i zakres elementów do, ale nie obejmują, elementu wskazywanego przez `last` .

Należy zauważyć, że chociaż `difference_type` jest dostępny dla wszystkich iteratorów, które spełniają wymagania iteratora danych wejściowych, który obejmuje klasę iteratorów dwukierunkowych obsługiwanych przez kontenery odwracalne, takie jak zestaw, odejmowanie między iteratorami jest obsługiwane tylko przez Iteratory dostępu swobodnego, dostarczone przez kontener dostępu swobodnego, taki jak wektor.

### <a name="example"></a>Przykład

```cpp
// set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <set>
#include <algorithm>

int main( )
{
   using namespace std;

   set <int> s1;
   set <int>::iterator s1_Iter, s1_bIter, s1_eIter;

   s1.insert( 20 );
   s1.insert( 10 );
   s1.insert( 20 );   // won't insert as set elements are unique

   s1_bIter = s1.begin( );
   s1_eIter = s1.end( );

   set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( s1_bIter, s1_eIter, 5 );
   df_typ10 = count( s1_bIter, s1_eIter, 10 );
   df_typ20 = count( s1_bIter, s1_eIter, 20 );

   // the keys, and hence the elements of a set are unique,
   // so there is at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in set s1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in set s1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in set s1.\n";

   // count the number of elements in a set
   set <int>::difference_type  df_count = 0;
   s1_Iter = s1.begin( );
   while ( s1_Iter != s1_eIter)
   {
      df_count++;
      s1_Iter++;
   }

   cout << "The number of elements in the set s1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in set s1.
The number '10' occurs 1 times in set s1.
The number '20' occurs 1 times in set s1.
The number of elements in the set s1 is: 2.
```

## <a name="emplace"></a><a name="emplace"></a> emplace

Wstawia element skonstruowany w miejscu (nie są wykonywane żadne operacje kopiowania ani przenoszenia).

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>Parametry

*argumentów*\
Argumenty przekazywane do konstruowania elementu, który ma zostać wstawiony do zestawu, chyba że zawiera już element o równoważnej kolejności.

### <a name="return-value"></a>Wartość zwracana

[Para](../standard-library/pair-structure.md) , której składnik bool zwraca wartość true, jeśli wykonano wstawienie, i wartość false, jeśli mapa już zawiera element, którego wartość miała odpowiednik wartości w kolejności. Składnik iteratora pary wartość zwracana zwraca adres, pod którym wstawiono nowy element (jeśli składnik bool ma wartość true) lub miejsce, w którym element został już zlokalizowany (jeśli składnik bool ma wartość false).

### <a name="remarks"></a>Uwagi

Ta funkcja nie unieważnia iteratorów ani odwołań.

Podczas umieszczanie, jeśli wystąpi wyjątek, stan kontenera nie jest modyfikowany.

### <a name="example"></a>Przykład

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
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
    set<string> s1;

    auto ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
        cout << "set not modified" << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;

    ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;
}
```

## <a name="emplace_hint"></a><a name="emplace_hint"></a> emplace_hint

Wstawia element skonstruowany w miejscu (nie są wykonywane żadne operacje kopiowania ani przenoszenia) z wskazówką dotyczącą położenia.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parametry

*argumentów*\
Argumenty przekazywane do konstruowania elementu, który ma zostać wstawiony do zestawu, chyba że zestaw już zawiera ten element lub, bardziej ogólnie, chyba że zawiera już element, którego wartość jest równorzędna uporządkowana.

*miejscu*\
Miejsce, w którym rozpocznie się wyszukiwanie poprawnego punktu wstawiania. (Jeśli ten punkt bezpośrednio poprzedza miejsce, w *którym*może następować amortyzowany stały czas zamiast czasu logarytmu).

### <a name="return-value"></a>Wartość zwracana

Iterator do nowo wstawionego elementu.

Jeśli wstawianie nie powiodło się, ponieważ element już istnieje, zwraca iterator do istniejącego elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie unieważnia iteratorów ani odwołań.

Podczas umieszczanie, jeśli wystąpi wyjątek, stan kontenera nie jest modyfikowany.

### <a name="example"></a>Przykład

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: " << endl;

    for (const auto& p : s) {
        cout << "(" << p <<  ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    // Emplace some test data
    s1.emplace("Anna");
    s1.emplace("Bob");
    s1.emplace("Carmine");

    cout << "set starting data: ";
    print(s1);
    cout << endl;

    // Emplace with hint
    // s1.end() should be the "next" element after this emplacement
    s1.emplace_hint(s1.end(), "Doug");

    cout << "set modified, now contains ";
    print(s1);
    cout << endl;
}
```

## <a name="empty"></a><a name="empty"></a> ciągiem

Sprawdza, czy zestaw jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli zestaw jest pusty; **`false`** Jeśli zestaw nie jest pusty.

### <a name="example"></a>Przykład

```cpp
// set_empty.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2;
   s1.insert ( 1 );

   if ( s1.empty( ) )
      cout << "The set s1 is empty." << endl;
   else
      cout << "The set s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The set s2 is empty." << endl;
   else
      cout << "The set s2 is not empty." << endl;
}
```

```Output
The set s1 is not empty.
The set s2 is empty.
```

## <a name="end"></a><a name="end"></a> punktów

Zwraca iterator poza końcem.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator Past. Jeśli zestaw jest pusty, a następnie `set::end() == set::begin()` .

### <a name="remarks"></a>Uwagi

**koniec** służy do sprawdzania, czy iterator przeszedł koniec jego zestawu.

Nie należy wywoływać wartości zwracanej przez **koniec** .

Aby zapoznać się z przykładem kodu, zobacz [set:: find](#find).

## <a name="equal_range"></a><a name="equal_range"></a> equal_range

Zwraca parę iteratorów odpowiednio do pierwszego elementu w zestawie z kluczem, który jest większy niż lub równy określonemu kluczowi i do pierwszego elementu w zestawie z kluczem, który jest większy niż klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*głównych*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego zestawu.

### <a name="return-value"></a>Wartość zwracana

Para iteratorów, w których pierwszy jest [lower_bound](#lower_bound) klucza, a drugi to [upper_bound](#upper_bound) klucza.

Aby uzyskać dostęp do pierwszego iteratora pary `pr` zwracanej przez funkcję członkowską, użyj `pr` . **najpierw**i aby usunąć odwołanie do dolnego powiązanego iteratora, użyj \* ( `pr` . **pierwszy**). Aby uzyskać dostęp do drugiego iteratora pary `pr` zwracanej przez funkcję członkowską, użyj `pr` . **drugi**i aby usunąć odwołanie do górnego powiązanego iteratora, użyj \* ( `pr` . **sekundę**).

### <a name="example"></a>Przykład

```cpp
// set_equal_range.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   typedef set<int, less< int > > IntSet;
   IntSet s1;
   set <int, less< int > > :: const_iterator s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;
   p1 = s1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   s1_RcIter = s1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *s1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = s1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == s1.end( ) ) && ( p2.second == s1.end( ) ) )
      cout << "The set s1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of set s1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the set s1 is: 30.
The lower bound of the element with a key of 20 in the set s1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The set s1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a><a name="erase"></a> Wyłączanie

Usuwa element lub zakres elementów w zestawie z określonych pozycji lub usuwa elementy, które odpowiadają określonemu kluczowi.

```cpp
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,
    const_iterator Last);

size_type erase(
    const key_type& Key);
```

### <a name="parameters"></a>Parametry

*Miejscu*\
Pozycja elementu, który ma zostać usunięty.

*Pierwszego*\
Pozycja pierwszego elementu, który ma zostać usunięty.

*Ostatniego*\
Umieść tuż poza ostatnim elementem, który ma zostać usunięty.

*Głównych*\
Wartość klucza elementów do usunięcia.

### <a name="return-value"></a>Wartość zwracana

W przypadku pierwszych dwóch funkcji składowych iterator dwukierunkowy, który wyznacza pierwszy element pozostały poza elementami usuniętymi lub element, który jest końcem zestawu, jeśli taki element nie istnieje.

Dla trzeciej funkcji składowej zwraca liczbę elementów, które zostały usunięte z zestawu.

### <a name="example"></a>Przykład

```cpp
// set_erase.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions

using namespace std;

using myset = set<string>;

void printset(const myset& s) {
    for (const auto& iter : s) {
        cout << " [" << iter << "]";
    }
    cout << endl << "size() == " << s.size() << endl << endl;
}

int main()
{
    myset s1;

    // Fill in some data to test with, one at a time
    s1.insert("Bob");
    s1.insert("Robert");
    s1.insert("Bert");
    s1.insert("Rob");
    s1.insert("Bobby");

    cout << "Starting data of set s1 is:" << endl;
    printset(s1);
    // The 1st member function removes an element at a given position
    s1.erase(next(s1.begin()));
    cout << "After the 2nd element is deleted, the set s1 is:" << endl;
    printset(s1);

    // Fill in some data to test with, one at a time, using an initializer list
    myset s2{ "meow", "hiss", "purr", "growl", "yowl" };

    cout << "Starting data of set s2 is:" << endl;
    printset(s2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    s2.erase(next(s2.begin()), prev(s2.end()));
    cout << "After the middle elements are deleted, the set s2 is:" << endl;
    printset(s2);

    myset s3;

    // Fill in some data to test with, one at a time, using emplace
    s3.emplace("C");
    s3.emplace("C#");
    s3.emplace("D");
    s3.emplace("D#");
    s3.emplace("E");
    s3.emplace("E#");
    s3.emplace("F");
    s3.emplace("F#");
    s3.emplace("G");
    s3.emplace("G#");
    s3.emplace("A");
    s3.emplace("A#");
    s3.emplace("B");

    cout << "Starting data of set s3 is:" << endl;
    printset(s3);
    // The 3rd member function removes elements with a given Key
    myset::size_type count = s3.erase("E#");
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from s3 is: " << count << "." << endl;
    cout << "After the element with a key of \"E#\" is deleted, the set s3 is:" << endl;
    printset(s3);
}
```

## <a name="find"></a><a name="find"></a> wyświetlić

Zwraca iterator odwołujący się do lokalizacji elementu w zestawie, który ma klucz równoważny do określonego klucza.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza do dopasowania przez klucz sortowania elementu z przeszukiwanego zestawu.

### <a name="return-value"></a>Wartość zwracana

Iterator, który odwołuje się do lokalizacji elementu z określonym kluczem lub lokalizacji, w której znajduje się ostatni element w zestawie ( `set::end()` ), jeśli nie znaleziono żadnego dopasowania dla klucza.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator, który odwołuje się do elementu w zestawie, którego klucz jest równoważny *kluczowi* argumentu w predykacie binarnym, który wywołuje kolejność na podstawie mniejszej niż porównywalnej relacji.

Jeśli wartość zwracana `find` jest przypisana do `const_iterator` , nie można zmodyfikować obiektu zestawu. Jeśli wartość zwracana `find` jest przypisana do `iterator` , można zmodyfikować obiekt zestawu.

### <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4 /MTd
#include <set>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

template <typename C, class T> void findit(const C& c, T val) {
    cout << "Trying find() on value " << val << endl;
    auto result = c.find(val);
    if (result != c.end()) {
        cout << "Element found: "; print_elem(*result); cout << endl;
    } else {
        cout << "Element not found." << endl;
    }
}

int main()
{
    set<int> s1({ 40, 45 });
    cout << "The starting set s1 is: " << endl;
    print_collection(s1);

    vector<int> v;
    v.push_back(43);
    v.push_back(41);
    v.push_back(46);
    v.push_back(42);
    v.push_back(44);
    v.push_back(44); // attempt a duplicate

    cout << "Inserting the following vector data into s1: " << endl;
    print_collection(v);

    s1.insert(v.begin(), v.end());

    cout << "The modified set s1 is: " << endl;
    print_collection(s1);
    cout << endl;
    findit(s1, 45);
    findit(s1, 6);
}
```

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

Zwraca kopię obiektu alokatora użytego do skonstruowania zestawu.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez zestaw do zarządzania pamięcią, która jest parametrem szablonu `Allocator` .

Aby uzyskać więcej informacji na temat `Allocator` , zobacz sekcję Uwagi w temacie [Ustawianie klasy](../standard-library/set-class.md) .

### <a name="remarks"></a>Uwagi

Przypisania dla klasy zestawu określają sposób zarządzania magazynem przez klasę. Domyślne przydzielenie klas kontenerów standardowej biblioteki języka C++ jest wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym tematem języka C++.

### <a name="example"></a>Przykład

```cpp
// set_get_allocator.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int>::allocator_type s1_Alloc;
   set <int>::allocator_type s2_Alloc;
   set <double>::allocator_type s3_Alloc;
   set <int>::allocator_type s4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   set <int> s1;
   set <int, allocator<int> > s2;
   set <double, allocator<double> > s3;

   s1_Alloc = s1.get_allocator( );
   s2_Alloc = s2.get_allocator( );
   s3_Alloc = s3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << s2.max_size( ) << "." << endl;

   cout << "\nThe number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << s3.max_size( ) <<  "." << endl;

   // The following line creates a set s4
   // with the allocator of multiset s1.
   set <int> s4( less<int>( ), s1_Alloc );

   s4_Alloc = s4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( s1_Alloc == s4_Alloc )
   {
      cout << "\nThe allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "\nThe allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="insert"></a><a name="insert"></a> wstawienia

Wstawia element lub zakres elementów do zestawu.

```cpp
// (1) single element
pair<iterator, bool> insert(
    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(
    ValTy&& Val);

// (3) single element with hint
iterator insert(
    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(
    initializer_list<value_type>
IList);
```

### <a name="parameters"></a>Parametry

*Użyte*\
Wartość elementu, który ma zostać wstawiony do zestawu, chyba że zawiera już element o równoważnej kolejności.

*Miejscu*\
Miejsce, w którym rozpocznie się wyszukiwanie poprawnego punktu wstawiania. (Jeśli ten punkt bezpośrednio poprzedza miejsce, w *którym*może następować amortyzowany stały czas zamiast czasu logarytmu).

*ValTy*\
Parametr szablonu, który określa typ argumentu, który może być używany przez zestaw do konstruowania elementu [value_type](../standard-library/map-class.md#value_type)i idealny do przesyłania dalej *jako argument* .

*Pierwszego*\
Pozycja pierwszego elementu, który ma zostać skopiowany.

*Ostatniego*\
Pozycja tuż poza ostatnim elementem, który ma zostać skopiowany.

*InputIterator*\
Argument funkcji szablonu, który spełnia wymagania [iteratora danych wejściowych](../standard-library/input-iterator-tag-struct.md) , który wskazuje elementy typu, które mogą być używane do konstruowania obiektów [value_type](../standard-library/map-class.md#value_type) .

*IList*\
[Initializer_list](../standard-library/initializer-list.md) , z którego mają zostać skopiowane elementy.

### <a name="return-value"></a>Wartość zwracana

Jednoelementowe funkcje członkowskie, (1) i (2) zwracają [parę](../standard-library/pair-structure.md) , których **`bool`** składnik ma wartość true, jeśli wykonano wstawienie, i wartość false, jeśli zestaw już zawiera element o równoważnej wartości w kolejności. Składnik iteratora pary zwracanych wartości wskazuje nowo wstawiony element **`bool`** , jeśli składnik ma wartość true lub do istniejącego elementu, jeśli **`bool`** składnik ma wartość false.

Funkcje członkowskie jednoelementowe z wskazówką, (3) i (4) zwracają iterator, który wskazuje na pozycję, gdzie nowy element został wstawiony do zestawu lub, jeśli element z równoważnym kluczem już istnieje, do istniejącego elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie unieważnia iteratorów, wskaźników ani odwołań.

Podczas wstawiania tylko jednego elementu, jeśli wystąpi wyjątek, stan kontenera nie jest modyfikowany. Podczas wstawiania wielu elementów, jeśli wyjątek jest zgłaszany, kontener pozostaje w nieokreślonym, ale prawidłowym stanie.

Aby uzyskać dostęp do składnika iteratora `pair` `pr` , który jest zwracany przez jednoelementowe funkcje członkowskie, użyj `pr.first` ;, aby usunąć odwołanie do iteratora w zwróconej parze, użyj `*pr.first` , dając Ci element. Aby uzyskać dostęp do **`bool`** składnika, użyj `pr.second` . Aby zapoznać się z przykładem, zobacz przykładowy kod w dalszej części tego artykułu.

[Value_type](../standard-library/map-class.md#value_type) kontenera jest elementem TypeDef, który należy do kontenera, a dla zestawu, `set<V>::value_type` jest typ `const V` .

Funkcja elementu członkowskiego zakresu (5) wstawia sekwencję wartości elementów do zestawu, który odnosi się do każdego elementu, który jest adresowany do zakresu, dlatego nie zostanie `[First, Last)` `Last` wstawiony. Funkcja elementu członkowskiego kontenera `end()` odwołuje się do pozycji tuż po ostatnim elemencie w kontenerze — na przykład, instrukcja `s.insert(v.begin(), v.end());` próbuje wstawić wszystkie elementy `v` do `s` . Wstawiane są tylko elementy, które mają unikatowe wartości z zakresu; duplikaty zostały zignorowane. Aby sprawdzić, które elementy są odrzucane, użyj jednoelementowych wersji programu `insert` .

Funkcja członkowska listy inicjatorów (6) używa [initializer_list](../standard-library/initializer-list.md) do kopiowania elementów do zestawu.

Do wstawienia elementu skonstruowanego w miejscu — to znaczy, że nie są wykonywane żadne operacje kopiowania ani przenoszenia — zobacz [set:: emplace](#emplace) i [set:: emplace_hint](#emplace_hint).

### <a name="example"></a>Przykład

```cpp
// set_insert.cpp
// compile with: /EHsc
#include <set>
#include <iostream>
#include <string>
#include <vector>

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

    // insert single values
    set<int> s1;
    // call insert(const value_type&) version
    s1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    s1.insert(20);

    cout << "The original set values of s1 are:" << endl;
    print(s1);

    // intentionally attempt a duplicate, single element
    auto ret = s1.insert(1);
    if (!ret.second){
        auto elem = *ret.first;
        cout << "Insert failed, element with value 1 already exists."
            << endl << "  The existing element is (" << elem << ")"
            << endl;
    }
    else{
        cout << "The modified set values of s1 are:" << endl;
        print(s1);
    }
    cout << endl;

    // single element, with hint
    s1.insert(s1.end(), 30);
    cout << "The modified set values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // The templatized version inserting a jumbled range
    set<int> s2;
    vector<int> v;
    v.push_back(43);
    v.push_back(294);
    v.push_back(41);
    v.push_back(330);
    v.push_back(42);
    v.push_back(45);

    cout << "Inserting the following vector data into s2:" << endl;
    print(v);

    s2.insert(v.begin(), v.end());

    cout << "The modified set values of s2 are:" << endl;
    print(s2);
    cout << endl;

    // The templatized versions move-constructing elements
    set<string>  s3;
    string str1("blue"), str2("green");

    // single element
    s3.insert(move(str1));
    cout << "After the first move insertion, s3 contains:" << endl;
    print(s3);

    // single element with hint
    s3.insert(s3.end(), move(str2));
    cout << "After the second move insertion, s3 contains:" << endl;
    print(s3);
    cout << endl;

    set<int> s4;
    // Insert the elements from an initializer_list
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });
    cout << "After initializer_list insertion, s4 contains:" << endl;
    print(s4);
    cout << endl;
}
```

## <a name="iterator"></a><a name="iterator"></a> Iterator

Typ, który zapewnia stały [iterator dwukierunkowy](../standard-library/bidirectional-iterator-tag-struct.md) , który może odczytać dowolny element w zestawie.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Przykład

Zapoznaj [się](#begin) z przykładem dotyczącym sposobu deklarowania i używania `iterator` .

## <a name="key_comp"></a><a name="key_comp"></a> key_comp

Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w zestawie.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji, którego zestaw używa do porządkowania jego elementów, który jest parametrem szablonu `Traits` .

Aby uzyskać więcej informacji `Traits` , zobacz temat [Ustawianie klasy](../standard-library/set-class.md) .

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członkowską:

**operator logiczny ()**(**klucz const&** `_xVal` , **klucz const&** `_yVal` );

zwraca, **`true`** Jeśli `_xVal` poprzedza, i nie jest równa `_yVal` w kolejności sortowania.

Należy zauważyć, że zarówno [key_compare](#key_compare) , jak i [value_compare](#value_compare) są synonimami dla parametru szablonu `Traits` . Oba typy są dostarczane dla klas zestawu i zestawów wielokrotnych, gdzie są identyczne, w celu zapewnienia zgodności z klasami map i multimap, gdzie są różne.

### <a name="example"></a>Przykład

```cpp
// set_key_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set<int, less<int> >::key_compare kc1 = s1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::key_compare kc2 = s2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of s2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of s2.
```

## <a name="key_compare"></a><a name="key_compare"></a> key_compare

Typ, który dostarcza obiekt funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w zestawie.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare` jest synonimem dla parametru szablonu `Traits` .

Aby uzyskać więcej informacji `Traits` , zobacz temat [Ustawianie klasy](../standard-library/set-class.md) .

Należy zauważyć, że oba `key_compare` i [value_compare](#value_compare) są synonimami dla parametru szablonu `Traits` . Oba typy są dostarczane dla klas zestawu i zestawów wielokrotnych, gdzie są identyczne, w celu zapewnienia zgodności z klasami map i multimap, gdzie są różne.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [key_comp](#key_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_compare` .

## <a name="key_type"></a><a name="key_type"></a> key_type

Typ, który opisuje obiekt zapisany jako element zestawu w jego pojemności jako klucz sortowania.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type` jest synonimem dla parametru szablonu `Key` .

Aby uzyskać więcej informacji na temat `Key` , zobacz sekcję Uwagi w temacie [Ustawianie klasy](../standard-library/set-class.md) .

Należy zauważyć, że oba `key_type` i [value_type](#value_type) są synonimami dla parametru szablonu `Key` . Oba typy są dostarczane dla klas zestawu i zestawów wielokrotnych, gdzie są identyczne, w celu zapewnienia zgodności z klasami map i multimap, gdzie są różne.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [value_type](#value_type) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_type` .

## <a name="lower_bound"></a><a name="lower_bound"></a> lower_bound

Zwraca iterator do pierwszego elementu w zestawie, z kluczem, który jest równy lub większy od określonego klucza.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*głównych*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego zestawu.

### <a name="return-value"></a>Wartość zwracana

Iterator lub `const_iterator` który odnosi się do lokalizacji elementu w zestawie, który jest równy lub większy od klucza argumentu lub który odnosi się do lokalizacji po ostatnim elemencie w zestawie, jeśli nie znaleziono żadnego dopasowania dla klucza.

### <a name="example"></a>Przykład

```cpp
// set_lower_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.lower_bound( 20 );
   cout << "The element of set s1 with a key of 20 is: "
        << *s1_RcIter << "." << endl;

   s1_RcIter = s1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of set s1 with a key of 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator that addresses the location
   s1_AcIter = s1.end( );
   s1_AcIter--;
   s1_RcIter = s1.lower_bound( *s1_AcIter );
   cout << "The element of s1 with a key matching "
        << "that of the last element is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The element of set s1 with a key of 20 is: 20.
The set s1 doesn't have an element with a key of 40.
The element of s1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a><a name="max_size"></a> max_size

Zwraca maksymalną długość zestawu.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna możliwa długość zestawu.

### <a name="example"></a>Przykład

```cpp
// set_max_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::size_type i;

   i = s1.max_size( );
   cout << "The maximum possible length "
        << "of the set is " << i << "." << endl;
}
```

## <a name="operator"></a><a name="op_eq"></a> operator =

Zastępuje elementy tego elementu `set` przy użyciu elementów z innego `set` .

```cpp
set& operator=(const set& right);

set& operator=(set&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
`set`Udostępnianie nowych elementów do przypisania `set` .

### <a name="remarks"></a>Uwagi

Pierwsza wersja programu `operator=` używa [odwołania lvalue](../cpp/lvalue-reference-declarator-amp.md) dla *prawa*, aby skopiować elementy z *prawej strony* do tego `set` .

Druga wersja używa [odwołania rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) z prawej strony. Przenosi elementy z *prawej* do tego `set` .

Wszystkie elementy w tym elemencie `set` przed wykonaniem funkcji operatora są odrzucane.

### <a name="example"></a>Przykład

```cpp
// set_operator_as.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
   {
   using namespace std;
   set<int> v1, v2, v3;
   set<int>::iterator iter;

   v1.insert(10);

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

## <a name="pointer"></a><a name="pointer"></a> przytrzymaj

Typ, który dostarcza wskaźnik do elementu w zestawie.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Uwagi

**Wskaźnik** typu może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie zestawu.

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

Zwraca iterator odnoszący się do pierwszego elementu w odwróconym zestawie.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconym zestawie lub, który miał być ostatnim elementem w nieodwróconym zestawie.

### <a name="remarks"></a>Uwagi

`rbegin` jest używany z odwróconym zestawem, tak jak [początek](#begin) jest używany z zestawem.

Jeśli wartość zwracana elementu `rbegin` jest przypisana do `const_reverse_iterator` , wówczas nie można zmodyfikować obiektu zestawu. Jeśli wartość zwracana elementu `rbegin` jest przypisana do `reverse_iterator` , wówczas można zmodyfikować obiekt zestawu.

`rbegin` może służyć do iteracji przez zestaw wstecz.

### <a name="example"></a>Przykład

```cpp
// set_rbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rbegin( );
   cout << "The first element in the reversed set is "
        << *s1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a set in a forward order
   cout << "The set is:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration
   // through a set in a reverse order
   cout << "The reversed set is:";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << " " << *s1_rIter;
   cout << endl;

   // A set element can be erased by dereferencing to its key
   s1_rIter = s1.rbegin( );
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed set is "<< *s1_rIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
The set is: 10 20 30
The reversed set is: 30 20 10
After the erasure, the first element in the reversed set is 20.
```

## <a name="reference"></a><a name="reference"></a> odwoła

Typ, który zawiera odwołanie do elementu przechowywanego w zestawie.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Przykład

```cpp
// set_reference.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;
}
```

```Output
The first element in the set is 10.
```

## <a name="rend"></a><a name="rend"></a> rend

Zwraca iterator odnoszący się do lokalizacji następującej po ostatnim elemencie w odwróconym zestawie.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym zestawie (lokalizacja, która poprzedza pierwszy element w nieodwróconym zestawie).

### <a name="remarks"></a>Uwagi

`rend` jest używany z odwróconym zestawem, tak jak [koniec](#end) jest używany z zestawem.

Jeśli wartość zwracana elementu `rend` jest przypisana do `const_reverse_iterator` , wówczas nie można zmodyfikować obiektu zestawu. Jeśli wartość zwracana elementu `rend` jest przypisana do `reverse_iterator` , wówczas można zmodyfikować obiekt zestawu. Nie można usunąć odwołania do wartości zwracanej przez `rend` .

`rend` może służyć do sprawdzenia, czy iterator odwrotny osiągnął koniec zestawu.

### <a name="example"></a>Przykład

```cpp
// set_rend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rend( );
   s1_rIter--;
   cout << "The last element in the reversed set is "
        << *s1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a set in a forward order
   cout << "The set is: ";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << *s1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a set in a reverse order
   cout << "The reversed set is: ";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << *s1_rIter << " ";
   cout << "." << endl;

   s1_rIter = s1.rend( );
   s1_rIter--;
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rend( );
   --s1_rIter;
   cout << "After the erasure, the last element in the "
        << "reversed set is " << *s1_rIter << "." << endl;
}
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> reverse_iterator

Typ, który dostarcza iterator dwukierunkowy do odczytu i modyfikacji elementu w odwróconym zestawie.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` służy do iterowania przez zestaw w odwrotnej postaci.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rbegin](#rbegin) , aby zapoznać się z przykładem sposobu deklarowania i używania `reverse_iterator` .

## <a name="set"></a><a name="set"></a> zbiór

Konstruuje zestaw, który jest pusty lub jest kopią całości lub części innego zestawu.

```cpp
set();

explicit set(
    const Traits& Comp);

set(
    const Traits& Comp,
    const Allocator& Al);

set(
    const set& Right);

set(
    set&& Right);

set(
    initializer_list<Type> IList);

set(
    initializer_list<Type> IList,
    const Compare& Comp);

set(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

*Wsp*\
Klasa alokatora magazynu, która ma zostać użyta dla tego obiektu zestawu, która jest domyślna `Allocator` .

*Przepisów*\
Funkcja porównania typu `const Traits` użyta do uporządkowania elementów w zestawie, które domyślnie są `Compare` .

*Rght*\
Zestaw, którego skonstruowany zestaw ma być kopią.

*Pierwszego*\
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*Ostatniego*\
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

*IList*\
Lista initializer_list, z której mają być skopiowane elementy.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują typ obiektu alokatora, który zarządza magazynem pamięci dla zestawu i który może być później zwracany przez wywołanie [get_allocator](#get_allocator). Parametr alokatora jest często pomijany w deklaracjach klas i makrach przetwarzania wstępnego służących do podstawiania alternatywnych metod przydzielania.

Wszystkie konstruktory inicjują swoje zestawy.

Wszystkie konstruktory przechowują obiekt funkcji typu `Traits` , który jest używany do ustanowienia zamówienia między kluczami zestawu i który może być później zwracany przez wywołanie [key_comp](#key_comp).

Pierwsze trzy konstruktory określają pusty zestaw początkowy, drugi określa typ funkcji porównywania ( `comp` ), która ma zostać użyta w celu ustalenia kolejności elementów i trzeciego jawnie określającego typ alokatora (), `al` który ma być używany. Słowo kluczowe **`explicit`** pomija pewne rodzaje automatycznej konwersji typów.

Czwarty Konstruktor określa kopię zestawu `right` .

Następne trzy konstruktory używają initializer_list, aby określić elementy.

Następne trzy konstruktory skopiują zakres [ `first` , `last` ) zestawu i zwiększają jawność w określaniu typu funkcji porównania klasy `Traits` i **alokatora**.

Ósmy Konstruktor określa kopię zestawu przez przesunięcia `right` .

### <a name="example"></a>Przykład

```cpp
// set_set.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;

    // Create an empty set s0 of key type integer
    set <int> s0;

    // Create an empty set s1 with the key comparison
    // function of less than, then insert 4 elements
    set <int, less<int> > s1;
    s1.insert(10);
    s1.insert(20);
    s1.insert(30);
    s1.insert(40);

    // Create an empty set s2 with the key comparison
    // function of less than, then insert 2 elements
    set <int, less<int> > s2;
    s2.insert(10);
    s2.insert(20);

    // Create a set s3 with the
    // allocator of set s1
    set <int>::allocator_type s1_Alloc;
    s1_Alloc = s1.get_allocator();
    set <int> s3(less<int>(), s1_Alloc);
    s3.insert(30);

    // Create a copy, set s4, of set s1
    set <int> s4(s1);

    // Create a set s5 by copying the range s1[ first,  last)
    set <int>::const_iterator s1_bcIter, s1_ecIter;
    s1_bcIter = s1.begin();
    s1_ecIter = s1.begin();
    s1_ecIter++;
    s1_ecIter++;
    set <int> s5(s1_bcIter, s1_ecIter);

    // Create a set s6 by copying the range s4[ first,  last)
    // and with the allocator of set s2
    set <int>::allocator_type s2_Alloc;
    s2_Alloc = s2.get_allocator();
    set <int> s6(s4.begin(), ++s4.begin(), less<int>(), s2_Alloc);

    cout << "s1 =";
    for (auto i : s1)
        cout << " " << i;
    cout << endl;

    cout << "s2 = " << *s2.begin() << " " << *++s2.begin() << endl;

    cout << "s3 =";
    for (auto i : s3)
        cout << " " << i;
    cout << endl;

    cout << "s4 =";
    for (auto i : s4)
        cout << " " << i;
    cout << endl;

    cout << "s5 =";
    for (auto i : s5)
        cout << " " << i;
    cout << endl;

    cout << "s6 =";
    for (auto i : s6)
        cout << " " << i;
    cout << endl;

    // Create a set by moving s5
    set<int> s7(move(s5));
    cout << "s7 =";
    for (auto i : s7)
        cout << " " << i;
    cout << endl;

    // Create a set with an initializer_list
    cout << "s8 =";
    set<int> s8{ { 1, 2, 3, 4 } };
    for (auto i : s8)
        cout << " " << i;
    cout << endl;

    cout << "s9 =";
    set<int> s9{ { 5, 6, 7, 8 }, less<int>() };
    for (auto i : s9)
        cout << " " << i;
    cout << endl;

    cout << "s10 =";
    set<int> s10{ { 10, 20, 30, 40 }, less<int>(), s9.get_allocator() };
    for (auto i : s10)
        cout << " " << i;
    cout << endl;
}
```

```Output
s1 = 10 20 30 40s2 = 10 20s3 = 30s4 = 10 20 30 40s5 = 10 20s6 = 10s7 = 10 20s8 = 1 2 3 4s9 = 5 6 7 8s10 = 10 20 30 40
```

## <a name="size"></a><a name="size"></a> zmienia

Zwraca liczbę elementów w zestawie.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość zestawu.

### <a name="example"></a>Przykład

```cpp
// set_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: size_type i;

   s1.insert( 1 );
   i = s1.size( );
   cout << "The set length is " << i << "." << endl;

   s1.insert( 2 );
   i = s1.size( );
   cout << "The set length is now " << i << "." << endl;
}
```

```Output
The set length is 1.
The set length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w zestawie.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dotyczącym [rozmiaru](#size) przykładu sposobu deklarowania i używania `size_type`

## <a name="swap"></a><a name="swap"></a> wymiany

Zamienia elementy z dwóch zestawów.

```cpp
void swap(
    set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Zestaw argumentów, który udostępnia elementy do zamiany na zestaw docelowy.

### <a name="remarks"></a>Uwagi

Funkcja członkowska unieważnia odwołania, wskaźniki lub Iteratory, które wyznaczają elementy w dwóch zestawach, których elementy są wymieniane.

### <a name="example"></a>Przykład

```cpp
// set_swap.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   set <int>::iterator s1_Iter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );
   s2.insert( 100 );
   s2.insert( 200 );
   s3.insert( 300 );

   cout << "The original set s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   s1.swap( s2 );

   cout << "After swapping with s2, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( s1, s3 );

   cout << "After swapping with s3, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;
}
```

```Output
The original set s1 is: 10 20 30.
After swapping with s2, list s1 is: 100 200.
After swapping with s3, list s1 is: 300.
```

## <a name="upper_bound"></a><a name="upper_bound"></a> upper_bound

Zwraca iterator do pierwszego elementu w zestawie, który ma klucz, który jest większy niż określony klucz.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*głównych*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego zestawu.

### <a name="return-value"></a>Wartość zwracana

`iterator`Lub `const_iterator` który odnosi się do lokalizacji elementu w zestawie, który jest większy niż klucz argumentu lub który odnosi się do lokalizacji po ostatnim elemencie w zestawie, jeśli nie zostanie znaleziony żaden pasujący klucz.

### <a name="example"></a>Przykład

```cpp
// set_upper_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.upper_bound( 20 );
   cout << "The first element of set s1 with a key greater "
        << "than 20 is: " << *s1_RcIter << "." << endl;

   s1_RcIter = s1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of set s1 with a key > 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator addressing the location
   s1_AcIter = s1.begin( );
   s1_RcIter = s1.upper_bound( *s1_AcIter );
   cout << "The first element of s1 with a key greater than"
        << endl << "that of the initial element of s1 is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The first element of set s1 with a key greater than 20 is: 30.
The set s1 doesn't have an element with a key greater than 30.
The first element of s1 with a key greater than
that of the initial element of s1 is: 20.
```

## <a name="value_comp"></a><a name="value_comp"></a> value_comp

Pobiera kopię obiektu porównania, użytego do uporządkowania wartości elementów w zestawie.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji, którego zestaw używa do porządkowania jego elementów, który jest parametrem szablonu `Traits` .

Aby uzyskać więcej informacji `Traits` , zobacz temat [Ustawianie klasy](../standard-library/set-class.md) .

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członkowską:

**operator bool**(**klucz const&** `_xVal` , **klucz const&** `_yVal` );

zwraca, **`true`** Jeśli `_xVal` poprzedza, i nie jest równa `_yVal` w kolejności sortowania.

Należy zauważyć, że zarówno [value_compare](#value_compare) , jak i [key_compare](#key_compare) są synonimami dla parametru szablonu `Traits` . Oba typy są dostarczane dla klas zestawu i zestawów wielokrotnych, gdzie są identyczne, w celu zapewnienia zgodności z klasami map i multimap, gdzie są różne.

### <a name="example"></a>Przykład

```cpp
// set_value_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set <int, less<int> >::value_compare vc1 = s1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::value_compare vc2 = s2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of s2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of s1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of s2.
```

## <a name="value_compare"></a><a name="value_compare"></a> value_compare

Typ, który dostarcza obiekt funkcji, który może porównać dwie wartości elementów, aby określić ich względną kolejność w zestawie.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Uwagi

`value_compare` jest synonimem dla parametru szablonu `Traits` .

Aby uzyskać więcej informacji `Traits` , zobacz temat [Ustawianie klasy](../standard-library/set-class.md) .

Należy zauważyć, że zarówno [key_compare](#key_compare) , jak i `value_compare` są synonimami dla parametru szablonu `Traits` . Oba typy są dostarczane dla klas zestawu i zestawów wielokrotnych, gdzie są identyczne, w celu zapewnienia zgodności z klasami map i multimap, gdzie są różne.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [value_comp](#value_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania `value_compare` .

## <a name="value_type"></a><a name="value_type"></a> value_type

Typ, który opisuje obiekt zapisany jako element zestawu w jego pojemności jako wartość.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Uwagi

`value_type` jest synonimem dla parametru szablonu `Key` .

Aby uzyskać więcej informacji na temat `Key` , zobacz sekcję Uwagi w temacie [Ustawianie klasy](../standard-library/set-class.md) .

Należy zauważyć, że zarówno [key_type](#key_type) , jak i `value_type` są synonimami dla parametru szablonu `Key` . Oba typy są dostarczane dla klas zestawu i zestawów wielokrotnych, gdzie są identyczne, w celu zapewnienia zgodności z klasami map i multimap, gdzie są różne.

### <a name="example"></a>Przykład

```cpp
// set_value_type.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;

   set <int>::value_type svt_Int;   // Declare value_type
   svt_Int = 10;            // Initialize value_type

   set <int> :: key_type skt_Int;   // Declare key_type
   skt_Int = 20;             // Initialize key_type

   s1.insert( svt_Int );         // Insert value into s1
   s1.insert( skt_Int );         // Insert key into s1

   // A set accepts key_types or value_types as elements
   cout << "The set has elements:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++)
      cout << " " << *s1_Iter;
   cout << "." << endl;
}
```

```Output
The set has elements: 10 20.
```
