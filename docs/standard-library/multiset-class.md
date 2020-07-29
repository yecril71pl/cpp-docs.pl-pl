---
title: multiset — Klasa
ms.date: 11/04/2016
f1_keywords:
- set/std::multiset
- set/std::multiset::allocator_type
- set/std::multiset::const_iterator
- set/std::multiset::const_pointer
- set/std::multiset::const_reference
- set/std::multiset::const_reverse_iterator
- set/std::multiset::difference_type
- set/std::multiset::iterator
- set/std::multiset::key_compare
- set/std::multiset::key_type
- set/std::multiset::pointer
- set/std::multiset::reference
- set/std::multiset::reverse_iterator
- set/std::multiset::size_type
- set/std::multiset::value_compare
- set/std::multiset::value_type
- set/std::multiset::begin
- set/std::multiset::cbegin
- set/std::multiset::cend
- set/std::multiset::clear
- set/std::multiset::count
- set/std::multiset::crbegin
- set/std::multiset::crend
- set/std::multiset::emplace
- set/std::multiset::emplace_hint
- set/std::multiset::empty
- set/std::multiset::end
- set/std::multiset::equal_range
- set/std::multiset::erase
- set/std::multiset::find
- set/std::multiset::get_allocator
- set/std::multiset::insert
- set/std::multiset::key_comp
- set/std::multiset::lower_bound
- set/std::multiset::max_size
- set/std::multiset::rbegin
- set/std::multiset::rend
- set/std::multiset::size
- set/std::multiset::swap
- set/std::multiset::upper_bound
- set/std::multiset::value_comp
helpviewer_keywords:
- std::multiset [C++]
- std::multiset [C++], allocator_type
- std::multiset [C++], const_iterator
- std::multiset [C++], const_pointer
- std::multiset [C++], const_reference
- std::multiset [C++], const_reverse_iterator
- std::multiset [C++], difference_type
- std::multiset [C++], iterator
- std::multiset [C++], key_compare
- std::multiset [C++], key_type
- std::multiset [C++], pointer
- std::multiset [C++], reference
- std::multiset [C++], reverse_iterator
- std::multiset [C++], size_type
- std::multiset [C++], value_compare
- std::multiset [C++], value_type
- std::multiset [C++], begin
- std::multiset [C++], cbegin
- std::multiset [C++], cend
- std::multiset [C++], clear
- std::multiset [C++], count
- std::multiset [C++], crbegin
- std::multiset [C++], crend
- std::multiset [C++], emplace
- std::multiset [C++], emplace_hint
- std::multiset [C++], empty
- std::multiset [C++], end
- std::multiset [C++], equal_range
- std::multiset [C++], erase
- std::multiset [C++], find
- std::multiset [C++], get_allocator
- std::multiset [C++], insert
- std::multiset [C++], key_comp
- std::multiset [C++], lower_bound
- std::multiset [C++], max_size
- std::multiset [C++], rbegin
- std::multiset [C++], rend
- std::multiset [C++], size
- std::multiset [C++], swap
- std::multiset [C++], upper_bound
- std::multiset [C++], value_comp
ms.assetid: 630e8c10-0ce9-4ad9-8d79-9e91a600713f
ms.openlocfilehash: f481848228e1d93e457ce79948bacd5f3e6d4760
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224724"
---
# <a name="multiset-class"></a>multiset — Klasa

Klasa zestawu wielokrotnego biblioteki standardowej języka C++ jest używana do przechowywania i pobierania danych z kolekcji, w której wartości zawartych elementów nie muszą być unikatowe i które służą jako wartości klucza, zgodnie z którymi dane są automatycznie porządkowane. Nie można bezpośrednio zmienić wartości klucza elementu w zestawie wielokrotnym. Zamiast tego trzeba usunąć stare wartości i wstawić elementy z nowymi wartościami.

## <a name="syntax"></a>Składnia

```cpp
template <class Key, class Compare =less <Key>, class Allocator =allocator <Key>>
class multiset
```

### <a name="parameters"></a>Parametry

*Głównych*\
Typ danych elementu do przechowywania w zestawie wielokrotnym.

*Porównaniu*\
Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w zestawie wielokrotnym. Wartość domyślna predykatu binarnego jest **mniejsza** \<Key> .

W języku C++ 14 można włączyć wyszukiwanie heterogeniczne, określając `std::less<>` `std::greater<>` predykat or, który nie ma parametrów typu. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie heterogeniczne w kontenerach asocjacyjnych](../standard-library/stl-containers.md#sequence_containers)

*Alokator*\
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji zestawu wielokrotnego i dezalokacji pamięci. Wartość domyślna to `allocator<Key>`.

## <a name="remarks"></a>Uwagi

Klasa zestawu wielokrotnego biblioteki standardowej języka C++ to:

- Kontener asocjacyjny, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowe iteratory do dostępu do jego elementów.

- Posortowany, ponieważ jego elementy są uporządkowane według wartości kluczy w kontenerze zgodnie z określoną funkcją porównywania.

- Wielokrotny w tym sensie, że jego elementy nie muszą mieć unikatowych kluczy, więc jedna wartość klucza może mieć wiele wartości elementów z nią skojarzonych.

- Prosty kontener asocjacyjny, ponieważ jego wartości elementu są jego wartościami klucza.

- Szablon klasy, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy. Typ danych, który ma być użyty, jest zamiast tego określony jako parametr w klasie szablonu wraz z funkcją porównania i alokatorem.

Iterator dostarczony przez klasę zestawu wielokrotnego jest iteratorem dwukierunkowym, ale funkcje składowych klasy [INSERT](#insert) i zestaw [wielokrotny](#multiset) mają wersje przyjmujące jako parametry szablonu słabszy iterator danych wejściowych, którego wymagania dotyczące funkcjonalności są mniejsze niż te gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcjonalności, ale jest wystarczający, aby można było mówić istotnie o zakresie iteratorów [ `First` , `Last` ) w kontekście funkcji składowych klasy.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Kontenery asocjacyjne są zoptymalizowane dla operacji wyszukiwania, wstawiania oraz usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, są skuteczne, wykonując je w czasie, który jest średnio proporcjonalny do logarytmu liczby elementów w kontenerze. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Zestaw wielokrotny powinien być kontenerem asocjacyjnym z wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Elementów zestawu wielokrotnego może być wiele, mogą służyć jako własne klucze sortowania, więc klucze nie są unikatowe. Model dla tego typu konstrukcji jest uporządkowaną listą, np. wyrazów, w których wyrazy mogą występować więcej niż jeden raz. Gdyby nie zezwolono na wiele wystąpień wyrazów, odpowiednią strukturą kontenera byłby zestaw. Gdyby unikatowe definicje zostały dołączone jako wartości do listy unikatowych słów kluczowych, mapa byłaby odpowiednią strukturą zawierającą te dane. Gdyby natomiast definicje nie były unikatowe, mapa wielokrotna byłaby kontenerem z wyboru.

Zestaw wielokrotny porządkuje sekwencję, którą kontroluje, przez wywołanie przechowywanego obiektu funkcji typu *Compare*. Ten przechowywany obiekt jest funkcją porównywania, do której można uzyskać dostęp, wywołując funkcję członkowską [key_comp](#key_comp). Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarny *f*( *x*, *y*) jest obiektem funkcji, który ma dwa obiekty argumentu *x* i *y* oraz wartość zwracaną **`true`** lub **`false`** . Kolejność nałożona na zestaw jest ścisłym słabym porządkowaniem, jeśli Predykat binarny jest niezwrotny, niesymetryczny i przechodni oraz jeśli równoważność jest przechodnia, gdzie dwa obiekty x i y są zdefiniowane jako równoważne, gdy zarówno *f*( *x, y*), jak i *f*( *y, x*) mają wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

W języku C++ 14 można włączyć wyszukiwanie heterogeniczne, określając `std::less<>` `std::greater<>` predykat or, który nie ma parametrów typu. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie heterogeniczne w kontenerach asocjacyjnych](../standard-library/stl-containers.md#sequence_containers)

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[multiset](#multiset)|Tworzy obiekt `multiset` , który jest pusty lub jest kopią całości lub części określonego `multiset` .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Element typedef dla `allocator` klasy dla `multiset` obiektu.|
|[const_iterator](#const_iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytywać **`const`** element w `multiset` .|
|[const_pointer](#const_pointer)|Element typedef dla wskaźnika do **`const`** elementu w `multiset` .|
|[const_reference](#const_reference)|Element typedef dla odwołania do **`const`** elementu przechowywanego w trakcie `multiset` operacji odczytywania i wykonywania **`const`** .|
|[const_reverse_iterator](#const_reverse_iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytać dowolny **`const`** element w `multiset` .|
|[difference_type](#difference_type)|Element typedef ze znakiem Integer dla liczby elementów `multiset` w zakresie między elementami wskazywanymi przez Iteratory.|
|[Iterator](#iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytać lub zmodyfikować dowolny element w `multiset` .|
|[key_compare](#key_compare)|Element typedef dla obiektu funkcji, który może porównać dwa klucze, aby określić względną kolejność dwóch elementów w `multiset` .|
|[key_type](#key_type)|Element typedef dla obiektu funkcji, który może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `multiset` .|
|[pointer](#pointer)|Element typedef dla wskaźnika do elementu w `multiset` .|
|[odwoła](#reference)|Element typedef dla odwołania do elementu przechowywanego w `multiset` .|
|[reverse_iterator](#reverse_iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytać lub zmodyfikować element w odwróconej postaci `multiset` .|
|[size_type](#size_type)|Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w `multiset` .|
|[value_compare](#value_compare)|Element typedef dla obiektu funkcji, który może porównać dwa elementy jako klucze sortowania, aby określić ich względną kolejność w obiekcie `multiset` .|
|[value_type](#value_type)|Element typedef, który opisuje obiekt przechowywany jako element jako jako `multiset` wartość.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[zaczną](#begin)|Zwraca iterator, który wskazuje na pierwszy element w `multiset` .|
|[cbegin](#cbegin)|Zwraca iterator const, który odnosi się do pierwszego elementu w `multiset` .|
|[cend](#cend)|Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie w `multiset` .|
|[Wyczyść](#clear)|Kasuje wszystkie elementy `multiset` .|
|[liczbą](#count)|Zwraca liczbę elementów w `multiset` zakresie, których klucz pasuje do klucza określonego jako parametr.|
|[crbegin —](#crbegin)|Zwraca iterator const, który dotyczy pierwszego elementu w odwróconym zestawie.|
|[crend](#crend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconym zestawie.|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do `multiset` .|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do `multiset` , z wskazówką umieszczenia.|
|[puste](#empty)|Testuje, czy `multiset` jest pusty.|
|[punktów](#end)|Zwraca iterator, który wskazuje na lokalizację po ostatnim elemencie w `multiset` .|
|[equal_range](#equal_range)|Zwraca parę iteratorów. Pierwszy iterator w parze wskazuje na pierwszy element w a `multiset` z kluczem, który jest większy niż określony klucz. Drugi iterator w parze wskazuje na pierwszy element w `multiset` kluczu, który jest równy lub większy niż klucz.|
|[Wyłączanie](#erase)|Usuwa element lub zakres elementów `multiset` z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.|
|[find](#find)|Zwraca iterator, który wskazuje na pierwszą lokalizację elementu w `multiset` , który ma klucz równy określonemu kluczowi.|
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` obiektu, który jest używany do konstruowania `multiset` .|
|[wstawienia](#insert)|Wstawia element lub zakres elementów do `multiset` .|
|[key_comp](#key_comp)|Udostępnia obiekt funkcji, który może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `multiset` .|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu w elemencie `multiset` z kluczem, który jest równy lub większy niż określony klucz.|
|[max_size](#max_size)|Zwraca maksymalną długość `multiset` .|
|[rbegin](#rbegin)|Zwraca iterator, który wskazuje na pierwszy element w odwróconej `multiset` .|
|[rend](#rend)|Zwraca iterator, który wskazuje na lokalizację po ostatnim elemencie w odwróconym `multiset` .|
|[zmienia](#size)|Zwraca liczbę elementów w `multiset` .|
|[wymiany](#swap)|Wymienia elementy dwóch `multiset` s.|
|[upper_bound](#upper_bound)|Zwraca iterator do pierwszego elementu w a `multiset` z kluczem, który jest większy niż określony klucz.|
|[value_comp](#value_comp)|Pobiera kopię obiektu porównania, który jest używany do porządkowania wartości elementów w `multiset` .|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator =](#op_eq)|Zastępuje elementy a `multiset` kopią inną `multiset` .|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<set>

**Przestrzeń nazw:** std

## <a name="multisetallocator_type"></a><a name="allocator_type"></a>zestaw wielokrotny:: allocator_type

Typ reprezentujący klasę alokatora dla obiektu zestawu wielokrotnego

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type`jest synonimem dla parametru szablonu `Allocator` .

Aby uzyskać więcej informacji na temat `Allocator` , zobacz sekcję Uwagi w temacie [klasy zestaw wielokrotny](../standard-library/multiset-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [get_allocator](#get_allocator) , aby uzyskać przykład użycia`allocator_type`

## <a name="multisetbegin"></a><a name="begin"></a>zestaw wielokrotny:: BEGIN

Zwraca iterator odnoszący się do pierwszego elementu w zestawie wielokrotnym.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pierwszego elementu w zestawie wielokrotnym lub lokalizacji, która pomyślnie ma pusty zestaw wielokrotny.

### <a name="example"></a>Przykład

```cpp
// multiset_begin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::const_iterator ms1_cIter;

   ms1.insert( 1 );
   ms1.insert( 2 );
   ms1.insert( 3 );

   ms1_Iter = ms1.begin( );
   cout << "The first element of ms1 is " << *ms1_Iter << endl;

   ms1_Iter = ms1.begin( );
   ms1.erase( ms1_Iter );

   // The following 2 lines would err as the iterator is const
   // ms1_cIter = ms1.begin( );
   // ms1.erase( ms1_cIter );

   ms1_cIter = ms1.begin( );
   cout << "The first element of ms1 is now " << *ms1_cIter << endl;
}
```

```Output
The first element of ms1 is 1
The first element of ms1 is now 2
```

## <a name="multisetcbegin"></a><a name="cbegin"></a>zestaw wielokrotny:: cbegin

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

## <a name="multisetcend"></a><a name="cend"></a>zestaw wielokrotny:: cend

Zwraca **`const`** iterator, który odnosi się do lokalizacji jedynie poza ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

**`const`** Iterator dostępu dwukierunkowego, który wskazuje tuż poza końcem zakresu.

### <a name="remarks"></a>Uwagi

`cend`służy do sprawdzania, czy iterator przeszedł koniec zakresu.

Można użyć tej funkcji elementu członkowskiego zamiast `end()` funkcji składowej, aby zagwarantować, że wartość zwracana to `const_iterator` . Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy, `Container` że jest to modyfikowalny **`const`** kontener dowolnego rodzaju, który obsługuje `end()` i `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Nie można usunąć odwołania do wartości zwracanej przez `cend` .

## <a name="multisetclear"></a><a name="clear"></a>zestaw wielokrotny:: Clear

Usuwa wszystkie elementy zestawu wielokrotnego.

```cpp
void clear();
```

### <a name="example"></a>Przykład

```cpp
// multiset_clear.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 1 );
   ms1.insert( 2 );

   cout << "The size of the multiset is initially "
        << ms1.size( ) << "." << endl;

   ms1.clear( );
   cout << "The size of the multiset after clearing is "
        << ms1.size( ) << "." << endl;
}
```

```Output
The size of the multiset is initially 2.
The size of the multiset after clearing is 0.
```

## <a name="multisetconst_iterator"></a><a name="const_iterator"></a>zestaw wielokrotny:: const_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać **`const`** element w zestawie wielokrotnym.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może być używany do modyfikacji wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpoczęcia](#begin) korzystania z polecenia `const_iterator` .

## <a name="multisetconst_pointer"></a><a name="const_pointer"></a>zestaw wielokrotny:: const_pointer

Typ, który dostarcza wskaźnik do **`const`** elementu w zestawie wielokrotnym.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może być używany do modyfikacji wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie zestawu wielokrotnego.

## <a name="multisetconst_reference"></a><a name="const_reference"></a>zestaw wielokrotny:: const_reference

Typ, który zawiera odwołanie do **`const`** elementu przechowywanego w zestawie wielokrotnym do odczytu i wykonywania **`const`** operacji.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Przykład

```cpp
// multiset_const_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 10 );
   ms1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *ms1.begin( );

   cout << "The first element in the multiset is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the multiset
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the multiset is 10.
```

## <a name="multisetconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>zestaw wielokrotny:: const_reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **`const`** element w zestawie wielokrotnym.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartości elementu i służy do iteracji w odwrocie zestawu wielokrotnego.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rend](#rend) , aby zapoznać się z przykładem sposobu deklarowania i używania `const_reverse_iterator` .

## <a name="multisetcount"></a><a name="count"></a>zestaw wielokrotny:: Count

Zwraca liczbę elementów w zestawie wielokrotnym, których klucz pasuje do klucza określonego przez parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Klucz elementów, które mają być dopasowane z zestawu wielokrotnego.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w zestawie wielokrotnym, których klucz sortowania pasuje do klucza parametru.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę elementów *x* z zakresu

\[lower_bound (*klucz*), upper_bound (*klucz*))

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie funkcji składowej zestawu wielokrotnego:: Count.

```cpp
// multiset_count.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    multiset<int> ms1;
    multiset<int>::size_type i;

    ms1.insert(1);
    ms1.insert(1);
    ms1.insert(2);

    // Elements do not need to be unique in multiset,
    // so duplicates are allowed and counted.
    i = ms1.count(1);
    cout << "The number of elements in ms1 with a sort key of 1 is: "
         << i << "." << endl;

    i = ms1.count(2);
    cout << "The number of elements in ms1 with a sort key of 2 is: "
         << i << "." << endl;

    i = ms1.count(3);
    cout << "The number of elements in ms1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in ms1 with a sort key of 1 is: 2.
The number of elements in ms1 with a sort key of 2 is: 1.
The number of elements in ms1 with a sort key of 3 is: 0.
```

## <a name="multisetcrbegin"></a><a name="crbegin"></a>zestaw wielokrotny:: crbegin —

Zwraca iterator const odnoszący się do pierwszego elementu w odwróconym zestawie wielokrotnym.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stałe odwrotne Iteratory, odnoszące się do pierwszego elementu w odwróconym zestawie wielokrotnym lub na adres, który był ostatnim elementem w nieodwróconym zestawie wielokrotnym.

### <a name="remarks"></a>Uwagi

`crbegin`jest używany z odwróconym zestawem wielokrotnym, tak jak początek jest używany z zestawem wielokrotnym.

Z wartością zwracaną `crbegin` nie można zmodyfikować obiektu zestawu wielokrotnego.

`crbegin`może służyć do iteracji zestawu wielokrotnego do tyłu.

### <a name="example"></a>Przykład

```cpp
// multiset_crbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_crIter = ms1.crbegin( );
   cout << "The first element in the reversed multiset is "
        << *ms1_crIter << "." << endl;
}
```

```Output
The first element in the reversed multiset is 30.
```

## <a name="multisetcrend"></a><a name="crend"></a>zestaw wielokrotny:: crend

Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym zestawie wielokrotnym.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Niepowodzenie odwrotnego iteratora dwukierunkowego, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym zestawie wielokrotnym (lokalizacja, która poprzedza pierwszy element w nieodwróconym zestawie wielokrotnym).

### <a name="remarks"></a>Uwagi

`crend`jest używany z odwróconym zestawem wielokrotnym, tak jak [koniec](#end) jest używany z zestawem wielokrotnym.

Z wartością zwracaną `crend` nie można zmodyfikować obiektu zestawu wielokrotnego.

`crend`może służyć do sprawdzenia, czy iterator odwrotny osiągnął koniec zestawu wielokrotnego.

Nie można usunąć odwołania do wartości zwracanej przez `crend` .

### <a name="example"></a>Przykład

```cpp
// multiset_crend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   multiset <int> ms1;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_crIter = ms1.crend( ) ;
   ms1_crIter--;
   cout << "The last element in the reversed multiset is "
        << *ms1_crIter << "." << endl;
}
```

## <a name="multisetdifference_type"></a><a name="difference_type"></a>zestaw wielokrotny::d ifference_type

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów zestawu wielokrotnego w zakresie między elementami wskazywanymi przez Iteratory.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type`Jest typem zwracanym podczas odejmowania lub zwiększania przez Iteratory kontenera. `difference_type`Jest zazwyczaj używany do reprezentowania liczby elementów w zakresie [ `first` , `last` ) między iteratorami `first` i `last` , zawiera element wskazywany przez `first` i zakres elementów do, ale nie obejmują, elementu wskazywanego przez `last` .

Należy zauważyć, że chociaż `difference_type` jest dostępny dla wszystkich iteratorów, które spełniają wymagania iteratora danych wejściowych, który obejmuje klasę iteratorów dwukierunkowych obsługiwanych przez kontenery odwracalne, takie jak Set, odejmowanie między iteratorami jest obsługiwane tylko przez Iteratory dostępu swobodnego, dostarczone przez kontener dostępu swobodnego, taki jak wektor.

### <a name="example"></a>Przykład

```cpp
// multiset_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <set>
#include <algorithm>

int main( )
{
   using namespace std;

   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter, ms1_bIter, ms1_eIter;

   ms1.insert( 20 );
   ms1.insert( 10 );
   ms1.insert( 20 );

   ms1_bIter = ms1.begin( );
   ms1_eIter = ms1.end( );

   multiset <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( ms1_bIter, ms1_eIter, 5 );
   df_typ10 = count( ms1_bIter, ms1_eIter, 10 );
   df_typ20 = count( ms1_bIter, ms1_eIter, 20 );

   // The keys, and hence the elements, of a multiset are not unique
   cout << "The number '5' occurs " << df_typ5
        << " times in multiset ms1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in multiset ms1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in multiset ms1.\n";

   // Count the number of elements in a multiset
   multiset <int>::difference_type  df_count = 0;
   ms1_Iter = ms1.begin( );
   while ( ms1_Iter != ms1_eIter)
   {
      df_count++;
      ms1_Iter++;
   }

   cout << "The number of elements in the multiset ms1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in multiset ms1.
The number '10' occurs 1 times in multiset ms1.
The number '20' occurs 2 times in multiset ms1.
The number of elements in the multiset ms1 is: 3.
```

## <a name="multisetemplace"></a><a name="emplace"></a>zestaw wielokrotny:: emplace

Wstawia element skonstruowany w miejscu (nie są wykonywane żadne operacje kopiowania ani przenoszenia) z wskazówką dotyczącą położenia.

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*argumentów*|Argumenty przekazywane do konstruowania elementu, który ma zostać wstawiony do zestawu wielokrotnego.|

### <a name="return-value"></a>Wartość zwracana

Iterator do nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie zawiera żadnych odwołań do elementów kontenera, ale może unieważnić wszystkie Iteratory do kontenera.

Podczas umieszczanie, jeśli wystąpi wyjątek, stan kontenera nie jest modyfikowany.

### <a name="example"></a>Przykład

```cpp
// multiset_emplace.cpp
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
    multiset<string> s1;

    s1.emplace("Anna");
    s1.emplace("Bob");
    s1.emplace("Carmine");

    cout << "multiset modified, now contains ";
    print(s1);
    cout << endl;

    s1.emplace("Bob");

    cout << "multiset modified, now contains ";
    print(s1);
    cout << endl;
}
```

## <a name="multisetemplace_hint"></a><a name="emplace_hint"></a>zestaw wielokrotny:: emplace_hint

Wstawia element skonstruowany w miejscu (nie są wykonywane żadne operacje kopiowania ani przenoszenia) z wskazówką dotyczącą położenia.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*argumentów*|Argumenty przekazywane do konstruowania elementu, który ma zostać wstawiony do zestawu wielokrotnego.|
|*miejscu*|Miejsce, w którym rozpocznie się wyszukiwanie poprawnego punktu wstawiania. (Jeśli ten punkt bezpośrednio poprzedza miejsce, w *którym*może następować amortyzowany stały czas zamiast czasu logarytmu).|

### <a name="return-value"></a>Wartość zwracana

Iterator do nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie zawiera żadnych odwołań do elementów kontenera, ale może unieważnić wszystkie Iteratory do kontenera.

Podczas umieszczanie, jeśli wystąpi wyjątek, stan kontenera nie jest modyfikowany.

Aby zapoznać się z przykładem kodu, zobacz [set:: emplace_hint](../standard-library/set-class.md#emplace_hint).

## <a name="multisetempty"></a><a name="empty"></a>zestaw wielokrotny:: Empty

Testuje, czy zestaw wielokrotny jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli zestaw wielokrotny jest pusty; **`false`** Jeśli zestaw wielokrotny nie jest pusty.

### <a name="example"></a>Przykład

```cpp
// multiset_empty.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1, ms2;
   ms1.insert ( 1 );

   if ( ms1.empty( ) )
      cout << "The multiset ms1 is empty." << endl;
   else
      cout << "The multiset ms1 is not empty." << endl;

   if ( ms2.empty( ) )
      cout << "The multiset ms2 is empty." << endl;
   else
      cout << "The multiset ms2 is not empty." << endl;
}
```

```Output
The multiset ms1 is not empty.
The multiset ms2 is empty.
```

## <a name="multisetend"></a><a name="end"></a>zestaw wielokrotny:: end

Zwraca iterator poza końcem.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator Past. Jeśli zestaw wielokrotny jest pusty, a następnie `multiset::end() == multiset::begin()` .

### <a name="remarks"></a>Uwagi

**koniec** służy do sprawdzania, czy iterator przeszedł koniec zestawu wielokrotnego.

Nie należy wywoływać wartości zwracanej przez **koniec** .

Aby zapoznać się z przykładem kodu, zobacz zestaw [wielokrotny:: find](#find).

## <a name="multisetequal_range"></a><a name="equal_range"></a>zestaw wielokrotny:: equal_range

Zwraca parę iteratorów odpowiednio do pierwszego elementu w zestawie wielokrotnym z kluczem, który jest większy niż określony klucz i do pierwszego elementu w zestawie wielokrotnym z kluczem, który jest równy lub większy niż klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*głównych*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego zestawu wielokrotnego.

### <a name="return-value"></a>Wartość zwracana

Para iteratorów, takich jak pierwszy jest [lower_bound](#lower_bound) klucza, a drugi to [upper_bound](#upper_bound) klucza.

Aby uzyskać dostęp do pierwszego iteratora pary `pr` zwracanej przez funkcję członkowską, użyj `pr` . **najpierw**i aby usunąć odwołanie do dolnego powiązanego iteratora, użyj \* ( `pr` . **pierwszy**). Aby uzyskać dostęp do drugiego iteratora pary `pr` zwracanej przez funkcję członkowską, użyj `pr` . **drugi**i aby usunąć odwołanie do górnego powiązanego iteratora, użyj \* ( `pr` . **sekundę**).

### <a name="example"></a>Przykład

```cpp
// multiset_equal_range.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   typedef multiset<int, less<int> > IntSet;
   IntSet ms1;
   multiset <int> :: const_iterator ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;
   p1 = ms1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the multiset ms1 is: "
        << *( p1.second ) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the multiset ms1 is: "
        << *( p1.first ) << "." << endl;

   // Compare the upper_bound called directly
   ms1_RcIter = ms1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *ms1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = ms1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == ms1.end( ) ) && ( p2.second == ms1.end( ) ) )
      cout << "The multiset ms1 doesn't have an element "
              << "with a key less than 40." << endl;
   else
      cout << "The element of multiset ms1 with a key >= 40 is: "
                << *( p1.first ) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the multiset ms1 is: 30.
The lower bound of the element with a key of 20 in the multiset ms1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The multiset ms1 doesn't have an element with a key less than 40.
```

## <a name="multiseterase"></a><a name="erase"></a>zestaw wielokrotny:: wymazywanie

Usuwa element lub zakres elementów w zestawie wielokrotnym z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.

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

W przypadku pierwszych dwóch funkcji składowych iterator dwukierunkowy, który wyznacza pierwszy element pozostały poza elementami usuniętymi lub element, który jest końcem zestawu wielokrotnego, jeśli taki element nie istnieje.

Dla trzeciej funkcji składowej zwraca liczbę elementów, które zostały usunięte z zestawu wielokrotnego.

### <a name="remarks"></a>Uwagi

Aby zapoznać się z przykładem kodu, zobacz [set:: Erase](../standard-library/set-class.md#erase).

## <a name="multisetfind"></a><a name="find"></a>zestaw wielokrotny:: find

Zwraca iterator, który odwołuje się do lokalizacji elementu w zestawie wielokrotnym, który ma klucz równoważny do określonego klucza.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza do dopasowania przez klucz sortowania elementu z przeszukiwanego zestawu wielokrotnego.

### <a name="return-value"></a>Wartość zwracana

Iterator, który odwołuje się do lokalizacji elementu z określonym kluczem lub lokalizacji, w której znajduje się ostatni element w zestawie wielokrotnym ( `multiset::end()` ), jeśli nie znaleziono żadnego dopasowania dla klucza.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator, który odwołuje się do elementu w zestawie wielokrotnym, którego klucz jest równoważny *kluczowi* argumentu w predykacie binarnym, który wywołuje kolejność na podstawie mniejszej niż porównywalności relacji.

Jeśli wartość zwracana `find` jest przypisana do `const_iterator` , nie można zmodyfikować obiektu zestawu wielokrotnego. Jeśli wartość zwracana `find` jest przypisana do `iterator` , można zmodyfikować obiekt wielokrotnego użycia.

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
    multiset<int> s1({ 40, 45 });
    cout << "The starting multiset s1 is: " << endl;
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

    cout << "The modified multiset s1 is: " << endl;
    print_collection(s1);
    cout << endl;
    findit(s1, 45);
    findit(s1, 6);
}
```

## <a name="multisetget_allocator"></a><a name="get_allocator"></a>zestaw wielokrotny:: get_allocator

Zwraca kopię obiektu alokatora używanego do konstruowania zestawu wielokrotnego.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez zestaw wielokrotny.

### <a name="remarks"></a>Uwagi

Przydzielenie dla klasy wielokrotnej określają sposób zarządzania magazynem przez klasę. Domyślne przydzielenie klas kontenerów standardowej biblioteki języka C++ jest wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym tematem języka C++.

### <a name="example"></a>Przykład

```cpp
// multiset_get_allocator.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int>::allocator_type ms1_Alloc;
   multiset <int>::allocator_type ms2_Alloc;
   multiset <double>::allocator_type ms3_Alloc;
   multiset <int>::allocator_type ms4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   multiset <int> ms1;
   multiset <int, allocator<int> > ms2;
   multiset <double, allocator<double> > ms3;

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << ms2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << ms3.max_size( ) <<  "." << endl;

   // The following lines create a multiset ms4
   // with the allocator of multiset ms1
   ms1_Alloc = ms1.get_allocator( );
   multiset <int> ms4( less<int>( ), ms1_Alloc );
   ms4_Alloc = ms4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( ms1_Alloc == ms4_Alloc )
   {
      cout << "Allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "Allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="multisetinsert"></a><a name="insert"></a>zestaw wielokrotny:: INSERT

Wstawia element lub zakres elementów do zestawu wielokrotnego.

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

|Parametr|Opis|
|-|-|
|*Użyte*|Wartość elementu, który ma zostać wstawiony do zestawu wielokrotnego.|
|*Miejscu*|Miejsce, w którym rozpocznie się wyszukiwanie poprawnego punktu wstawiania. (Jeśli ten punkt bezpośrednio poprzedza miejsce, w *którym*może następować amortyzowany stały czas zamiast czasu logarytmu).|
|*ValTy*|Parametr szablonu, który określa typ argumentu, który może być używany przez zestaw wielokrotny do konstruowania elementu [value_type](../standard-library/map-class.md#value_type)i idealny do przesyłania *dalej jako argument* .|
|*Pierwsze*|Pozycja pierwszego elementu, który ma zostać skopiowany.|
|*Ostatniego*|Pozycja tuż poza ostatnim elementem, który ma zostać skopiowany.|
|*InputIterator*|Argument funkcji szablonu, który spełnia wymagania [iteratora danych wejściowych](../standard-library/input-iterator-tag-struct.md) , który wskazuje elementy typu, które mogą być używane do konstruowania obiektów [value_type](../standard-library/map-class.md#value_type) .|
|*IList*|[Initializer_list](../standard-library/initializer-list.md) , z którego mają zostać skopiowane elementy.|

### <a name="return-value"></a>Wartość zwracana

Funkcje składowe pojedynczego elementu, (1) i (2) zwracają iterator do położenia, gdzie nowy element został wstawiony do zestawu wielokrotnego.

Jednoelementowa funkcja członkowska, (3) i (4) zwraca iterator, który wskazuje na pozycję, w której nowy element został wstawiony do zestawu wielokrotnego.

### <a name="remarks"></a>Uwagi

Ta funkcja nie sprawdza wskaźników ani odwołań, ale może unieważnić wszystkie Iteratory do kontenera.

Podczas wstawiania tylko jednego elementu, jeśli wystąpi wyjątek, stan kontenera nie jest modyfikowany. Podczas wstawiania wielu elementów, jeśli wyjątek jest zgłaszany, kontener pozostaje w nieokreślonym, ale prawidłowym stanie.

[Value_type](../standard-library/map-class.md#value_type) kontenera jest elementem TypeDef, który należy do kontenera, a dla zestawu, `multiset<V>::value_type` jest typ `const V` .

Funkcja elementu członkowskiego zakresu (5) wstawia sekwencję wartości elementów do zestawu wielokrotnego, który odnosi się do każdego elementu, który jest adresowany do zakresu, w związku z czym nie zostanie `[First, Last)` `Last` wstawiony. Funkcja elementu członkowskiego kontenera `end()` odwołuje się do pozycji tuż po ostatnim elemencie w kontenerze — na przykład, instrukcja `s.insert(v.begin(), v.end());` wstawia wszystkie elementy `v` do `s` .

Funkcja członkowska listy inicjatorów (6) używa [initializer_list](../standard-library/initializer-list.md) do kopiowania elementów do zestawu wielokrotnego.

Do wstawienia elementu skonstruowanego w miejscu — to znaczy, że nie są wykonywane żadne operacje kopiowania ani przenoszenia — zobacz zestaw [wielokrotny:: emplace](#emplace) i zestaw [wielokrotny:: emplace_hint](#emplace_hint).

### <a name="example"></a>Przykład

```cpp
// multiset_insert.cpp
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
    multiset<int> s1;
    // call insert(const value_type&) version
    s1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    s1.insert(20);

    cout << "The original multiset values of s1 are:" << endl;
    print(s1);

    // intentionally attempt a duplicate, single element
    s1.insert(1);
    cout << "The modified multiset values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // single element, with hint
    s1.insert(s1.end(), 30);
    cout << "The modified multiset values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // The templatized version inserting a jumbled range
    multiset<int> s2;
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

    cout << "The modified multiset values of s2 are:" << endl;
    print(s2);
    cout << endl;

    // The templatized versions move-constructing elements
    multiset<string>  s3;
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

    multiset<int> s4;
    // Insert the elements from an initializer_list
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });
    cout << "After initializer_list insertion, s4 contains:" << endl;
    print(s4);
    cout << endl;
}
```

## <a name="multisetiterator"></a><a name="iterator"></a>zestaw wielokrotny:: iterator

Typ, który zapewnia stały [iterator dwukierunkowy](../standard-library/bidirectional-iterator-tag-struct.md) , który może odczytać dowolny element w zestawie wielokrotnym.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Przykład

Zapoznaj [się](#begin) z przykładem dotyczącym sposobu deklarowania i używania `iterator` .

## <a name="multisetkey_comp"></a><a name="key_comp"></a>zestaw wielokrotny:: key_comp

Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w zestawie wielokrotnym.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji używany przez zestaw wielokrotny do porządkowania jego elementów, który jest parametrem szablonu `Compare` .

Aby uzyskać więcej informacji na temat `Compare` , zobacz sekcję Uwagi w temacie [klasy zestaw wielokrotny](../standard-library/multiset-class.md) .

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członkowską:

**operator bool**( **klucz const&** *x*, **const Key&** *y*);

Zwraca wartość true, jeśli *x* ściśle poprzedza *y* w kolejności sortowania.

Należy zauważyć, że zarówno [key_compare](#key_compare) , jak i [value_compare](#value_compare) są synonimami dla parametru szablonu `Compare` . Oba typy są dostarczane dla klas zestawów i zestawów wielokrotnych, gdzie są identyczne, aby zapewnić zgodność z mapami klas i multimap, gdzie są różne.

### <a name="example"></a>Przykład

```cpp
// multiset_key_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   multiset <int, less<int> > ms1;
   multiset <int, less<int> >::key_compare kc1 = ms1.key_comp( ) ;
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
           << "where kc1 is the function object of ms1."
           << endl;
   }

   multiset <int, greater<int> > ms2;
   multiset <int, greater<int> >::key_compare kc2 = ms2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of ms2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of ms2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of ms2.
```

## <a name="multisetkey_compare"></a><a name="key_compare"></a>zestaw wielokrotny:: key_compare

Typ, który dostarcza obiekt funkcji, który może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w zestawie wielokrotnym.

```cpp
typedef Compare key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare`jest synonimem dla parametru szablonu `Compare` .

Aby uzyskać więcej informacji na temat `Compare` , zobacz sekcję Uwagi w temacie [klasy zestaw wielokrotny](../standard-library/multiset-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [key_comp](#key_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_compare` .

## <a name="multisetkey_type"></a><a name="key_type"></a>zestaw wielokrotny:: key_type

Typ, który dostarcza obiekt funkcji, który może porównać klucze sortowania, aby określić względną kolejność dwóch elementów w zestawie wielokrotnym.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type`jest synonimem dla parametru szablonu `Key` .

Aby uzyskać więcej informacji na temat `Key` , zobacz sekcję Uwagi w temacie [klasy zestaw wielokrotny](../standard-library/multiset-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [value_type](#value_type) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_type` .

## <a name="multisetlower_bound"></a><a name="lower_bound"></a>zestaw wielokrotny:: lower_bound

Zwraca iterator do pierwszego elementu w zestawie wielokrotnym z kluczem, który jest równy lub większy niż określony klucz.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*głównych*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego zestawu wielokrotnego.

### <a name="return-value"></a>Wartość zwracana

`iterator`Lub `const_iterator` który odnosi się do lokalizacji elementu w zestawie wielokrotnym z kluczem, który jest równy lub większy niż klucz argumentu lub który odnosi się do lokalizacji po ostatnim elemencie w zestawie wielokrotnym, jeśli nie zostanie znaleziony żaden pasujący klucz.

### <a name="example"></a>Przykład

```cpp
// multiset_lower_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_RcIter = ms1.lower_bound( 20 );
   cout << "The element of multiset ms1 with a key of 20 is: "
        << *ms1_RcIter << "." << endl;

   ms1_RcIter = ms1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( ms1_RcIter == ms1.end( ) )
      cout << "The multiset ms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of multiset ms1 with a key of 40 is: "
           << *ms1_RcIter << "." << endl;

   // The element at a specific location in the multiset can be
   // found using a dereferenced iterator addressing the location
   ms1_AcIter = ms1.end( );
   ms1_AcIter--;
   ms1_RcIter = ms1.lower_bound( *ms1_AcIter );
   cout << "The element of ms1 with a key matching "
        << "that of the last element is: "
        << *ms1_RcIter << "." << endl;
}
```

```Output
The element of multiset ms1 with a key of 20 is: 20.
The multiset ms1 doesn't have an element with a key of 40.
The element of ms1 with a key matching that of the last element is: 30.
```

## <a name="multisetmax_size"></a><a name="max_size"></a>zestaw wielokrotny:: max_size

Zwraca maksymalną długość zestawu wielokrotnego.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna możliwa długość zestawu wielokrotnego.

### <a name="example"></a>Przykład

```cpp
// multiset_max_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::size_type i;

   i = ms1.max_size( );
   cout << "The maximum possible length "
        << "of the multiset is " << i << "." << endl;
}
```

## <a name="multisetmultiset"></a><a name="multiset"></a>zestaw wielokrotny:: zestaw wielokrotny

Konstruuje zestaw wielokrotny, który jest pusty lub jest kopią całości lub części innego zestawu wielokrotnego.

```cpp
multiset();

explicit multiset (
    const Compare& Comp);

multiset (
    const Compare& Comp,
    const Allocator& Al);

multiset(
    const multiset& Right);

multiset(
    multiset&& Right);

multiset(
    initializer_list<Type> IList);

multiset(
    initializer_list<Type> IList,
    const Compare& Comp);

multiset(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last,
    const Compare& Comp);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last,
    const Compare& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Wsp*|Klasa alokatora magazynu, która ma być używana dla tego obiektu zestawu wielokrotnego, który ma wartość domyślną `Allocator` .|
|*Comp*|Funkcja porównywania typu `const Compare` służąca do uporządkowania elementów w zestawie wielokrotnym, które domyślnie `Compare` .|
|*Kliknij*|Zestaw wielokrotny, którego skonstruowany zestaw wielokrotny ma być kopią.|
|*Pierwsze*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*Ostatniego*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|
|*IList*|Lista initializer_list, z której mają być skopiowane elementy.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują typ obiektu alokatora, który zarządza magazynem pamięci dla zestawu wielokrotnego i można go później zwrócić przez wywołanie [get_allocator](#get_allocator). Parametr alokatora jest często pomijany w deklaracjach klas i makrach przetwarzania wstępnego służących do podstawiania alternatywnych metod przydzielania.

Wszystkie konstruktory inicjują zestaw wielokrotny.

Wszystkie konstruktory przechowują obiekt funkcji typu Compare, który jest używany do ustanowienia zamówienia między kluczami zestawu wielokrotnego i który może być później zwracany przez wywołanie [key_comp](#key_comp).

Pierwsze trzy konstruktory określają pusty początkowy zestaw wielokrotny, drugi określa typ funkcji porównywania (*COMP*), która ma być używana w celu ustalenia kolejności elementów i trzeciego jawnie określającego typ alokatora (*Al*), który ma być używany. Słowo kluczowe **`explicit`** pomija pewne rodzaje automatycznej konwersji typów.

Czwarty Konstruktor określa kopię *zestawu wielokrotnego*.

Piąty Konstruktor określa kopię zestawu wielokrotnego, przenosząc *prawo*.

Szósty, siódmy i ósmy konstruktory określają initializer_list, z których mają być kopiowane elementy.

Następne trzy konstruktory kopiują zakres `[First, Last)` zestawu wielokrotnego z rosnącą jawnością w określaniu typu funkcji porównania i alokatora.

### <a name="example"></a>Przykład

```cpp
// multiset_ctor.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    //multiset <int>::iterator ms1_Iter, ms2_Iter, ms3_Iter;
    multiset <int>::iterator ms4_Iter, ms5_Iter, ms6_Iter, ms7_Iter;

    // Create an empty multiset ms0 of key type integer
    multiset <int> ms0;

    // Create an empty multiset ms1 with the key comparison
    // function of less than, then insert 4 elements
    multiset <int, less<int> > ms1;
    ms1.insert(10);
    ms1.insert(20);
    ms1.insert(20);
    ms1.insert(40);

    // Create an empty multiset ms2 with the key comparison
    // function of greater than, then insert 2 elements
    multiset <int, less<int> > ms2;
    ms2.insert(10);
    ms2.insert(20);

    // Create a multiset ms3 with the
    // allocator of multiset ms1
    multiset <int>::allocator_type ms1_Alloc;
    ms1_Alloc = ms1.get_allocator();
    multiset <int> ms3(less<int>(), ms1_Alloc);
    ms3.insert(30);

    // Create a copy, multiset ms4, of multiset ms1
    multiset <int> ms4(ms1);

    // Create a multiset ms5 by copying the range ms1[ first,  last)
    multiset <int>::const_iterator ms1_bcIter, ms1_ecIter;
    ms1_bcIter = ms1.begin();
    ms1_ecIter = ms1.begin();
    ms1_ecIter++;
    ms1_ecIter++;
    multiset <int> ms5(ms1_bcIter, ms1_ecIter);

    // Create a multiset ms6 by copying the range ms4[ first,  last)
    // and with the allocator of multiset ms2
    multiset <int>::allocator_type ms2_Alloc;
    ms2_Alloc = ms2.get_allocator();
    multiset <int> ms6(ms4.begin(), ++ms4.begin(), less<int>(), ms2_Alloc);

    cout << "ms1 =";
    for (auto i : ms1)
        cout << " " << i;
    cout << endl;

    cout << "ms2 =";
    for (auto i : ms2)
        cout << " " << i;
   cout << endl;

   cout << "ms3 =";
   for (auto i : ms3)
       cout << " " << i;
    cout << endl;

    cout << "ms4 =";
    for (auto i : ms4)
        cout << " " << i;
    cout << endl;

    cout << "ms5 =";
    for (auto i : ms5)
        cout << " " << i;
    cout << endl;

    cout << "ms6 =";
    for (auto i : ms6)
        cout << " " << i;
    cout << endl;

    // Create a multiset by moving ms5
    multiset<int> ms7(move(ms5));
    cout << "ms7 =";
    for (auto i : ms7)
        cout << " " << i;
    cout << endl;

    // Create a multiset with an initializer_list
    multiset<int> ms8({1, 2, 3, 4});
    cout << "ms8=";
    for (auto i : ms8)
        cout << " " << i;
    cout << endl;
}
```

## <a name="multisetoperator"></a><a name="op_eq"></a>zestaw wielokrotny:: operator =

Zastępuje elementy tego elementu `multiset` przy użyciu elementów z innego `multiset` .

```cpp
multiset& operator=(const multiset& right);

multiset& operator=(multiset&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Kliknij*|`multiset`Z którego elementów są kopiowane lub przenoszone.|

### <a name="remarks"></a>Uwagi

`operator=`kopiuje lub przenosi elementy w *prawo* do tego `multiset` , w zależności od typu odwołania (lvalue lub rvalue). Elementy znajdujące się w tym `multiset` przed wykonaniem `operator=` są odrzucane.

### <a name="example"></a>Przykład

```cpp
// multiset_operator_as.cpp
// compile with: /EHsc
#include <multiset>
#include <iostream>

int main( )
   {
   using namespace std;
   multiset<int> v1, v2, v3;
   multiset<int>::iterator iter;

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

## <a name="multisetpointer"></a><a name="pointer"></a>zestaw wielokrotny::p ointer

Typ, który dostarcza wskaźnik do elementu w zestawie wielokrotnym.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Uwagi

**Wskaźnik** typu może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie zestawu wielokrotnego.

## <a name="multisetrbegin"></a><a name="rbegin"></a>zestaw wielokrotny:: rbegin

Zwraca iterator odnoszący się do pierwszego elementu w odwróconym zestawie wielokrotnym.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconym zestawie wielokrotnym lub na adres, który był ostatnim elementem w nieodwróconym zestawie wielokrotnym.

### <a name="remarks"></a>Uwagi

`rbegin`jest używany z odwróconym zestawem wielokrotnym, tak jak rbegin jest używany z zestawem wielokrotnym.

Jeśli wartość zwracana elementu `rbegin` jest przypisana do `const_reverse_iterator` , wówczas nie można zmodyfikować obiektu zestawu wielokrotnego. Jeśli wartość zwracana elementu `rbegin` jest przypisana do `reverse_iterator` , można zmodyfikować obiekt wielokrotnego użycia.

`rbegin`może służyć do iteracji zestawu wielokrotnego do tyłu.

### <a name="example"></a>Przykład

```cpp
// multiset_rbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::reverse_iterator ms1_rIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_rIter = ms1.rbegin( );
   cout << "The first element in the reversed multiset is "
        << *ms1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a multiset in a forward order
   cout << "The multiset is:";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration
   // through a multiset in a reverse order
   cout << "The reversed multiset is:";
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )
      cout << " " << *ms1_rIter;
   cout << endl;

   // A multiset element can be erased by dereferencing to its key
   ms1_rIter = ms1.rbegin( );
   ms1.erase ( *ms1_rIter );

   ms1_rIter = ms1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed multiset is "<< *ms1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed multiset is 30.
The multiset is: 10 20 30
The reversed multiset is: 30 20 10
After the erasure, the first element in the reversed multiset is 20.
```

## <a name="multisetreference"></a><a name="reference"></a>zestaw wielokrotny:: odwołanie

Typ, który zawiera odwołanie do elementu przechowywanego w zestawie wielokrotnym.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Przykład

```cpp
// multiset_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 10 );
   ms1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   const int &Ref1 = *ms1.begin( );

   cout << "The first element in the multiset is "
        << Ref1 << "." << endl;
}
```

```Output
The first element in the multiset is 10.
```

## <a name="multisetrend"></a><a name="rend"></a>zestaw wielokrotny:: rend

Zwraca iterator, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym zestawie wielokrotnym.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym zestawie wielokrotnym (lokalizacja, która poprzedza pierwszy element w nieodwróconym zestawie wielokrotnym).

### <a name="remarks"></a>Uwagi

`rend`jest używany z odwróconym zestawem wielokrotnym, tak jak [koniec](#end) jest używany z zestawem wielokrotnym.

Jeśli wartość zwracana elementu `rend` jest przypisana do `const_reverse_iterator` , wówczas nie można zmodyfikować obiektu zestawu wielokrotnego. Jeśli wartość zwracana elementu `rend` jest przypisana do `reverse_iterator` , można zmodyfikować obiekt wielokrotnego użycia.

`rend`może służyć do sprawdzenia, czy iterator odwrotny osiągnął koniec zestawu wielokrotnego.

Nie można usunąć odwołania do wartości zwracanej przez `rend` .

### <a name="example"></a>Przykład

```cpp
// multiset_rend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::reverse_iterator ms1_rIter;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_rIter = ms1.rend( ) ;
   ms1_rIter--;
   cout << "The last element in the reversed multiset is "
        << *ms1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a multiset in a forward order
   cout << "The multiset is: ";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << *ms1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a multiset in a reverse order
   cout << "The reversed multiset is: ";
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )
      cout << *ms1_rIter << " ";
   cout << "." << endl;

   ms1_rIter = ms1.rend( );
   ms1_rIter--;
   ms1.erase ( *ms1_rIter );

   ms1_rIter = ms1.rend( );
   --ms1_rIter;
   cout << "After the erasure, the last element in the "
        << "reversed multiset is " << *ms1_rIter << "." << endl;
}
```

## <a name="multisetreverse_iterator"></a><a name="reverse_iterator"></a>zestaw wielokrotny:: reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconym zestawie wielokrotnym.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` służy do iteracji w odwrotnym zestawie wielokrotności.

### <a name="example"></a>Przykład

Zobacz przykład dla [rbegin](#rbegin) , aby zapoznać się z przykładem sposobu deklarowania i używania `reverse_iterator` .

## <a name="multisetsize"></a><a name="size"></a>zestaw wielokrotny:: rozmiar

Zwraca liczbę elementów w zestawie wielokrotnym.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość zestawu wielokrotnego.

### <a name="example"></a>Przykład

```cpp
// multiset_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: size_type i;

   ms1.insert( 1 );
   i = ms1.size( );
   cout << "The multiset length is " << i << "." << endl;

   ms1.insert( 2 );
   i = ms1.size( );
   cout << "The multiset length is now " << i << "." << endl;
}
```

```Output
The multiset length is 1.
The multiset length is now 2.
```

## <a name="multisetsize_type"></a><a name="size_type"></a>zestaw wielokrotny:: size_type

Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w zestawie wielokrotnym.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [rozmiaru](#size) , aby zapoznać się z przykładem sposobu deklarowania i używania`size_type`

## <a name="multisetswap"></a><a name="swap"></a>zestaw wielokrotny:: swap

Wymienia elementy dwóch zestawów wielozbiorówowych.

```cpp
void swap(
    multiset<Key, Compare, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Argument wielokrotny udostępniający elementy, które mają zostać zastąpione docelowym zestawem wielokrotnym.

### <a name="remarks"></a>Uwagi

Funkcja członkowska unieważnia brak odwołań, wskaźników lub iteratorów, które wyznaczają elementy w dwóch zestawach wielozbiorów, których elementy są wymieniane.

### <a name="example"></a>Przykład

```cpp
// multiset_swap.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1, ms2, ms3;
   multiset <int>::iterator ms1_Iter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );
   ms2.insert( 100 );
   ms2.insert( 200 );
   ms3.insert( 300 );

   cout << "The original multiset ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;

   // This is the member function version of swap
   ms1.swap( ms2 );

   cout << "After swapping with ms2, list ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;

   // This is the specialized template version of swap
   swap( ms1, ms3 );

   cout << "After swapping with ms3, list ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout   << "." << endl;
}
```

```Output
The original multiset ms1 is: 10 20 30.
After swapping with ms2, list ms1 is: 100 200.
After swapping with ms3, list ms1 is: 300.
```

## <a name="multisetupper_bound"></a><a name="upper_bound"></a>zestaw wielokrotny:: upper_bound

Zwraca iterator do pierwszego elementu w zestawie wielokrotnym z kluczem, który jest większy niż określony klucz.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*głównych*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego zestawu wielokrotnego.

### <a name="return-value"></a>Wartość zwracana

**Iterator** lub `const_iterator` który odnosi się do lokalizacji elementu w zestawie wielokrotnym z kluczem, który jest większy niż klucz argumentu lub który odnosi się do lokalizacji po ostatnim elemencie w zestawie wielokrotnym, jeśli nie znaleziono żadnego dopasowania dla klucza.

### <a name="example"></a>Przykład

```cpp
// multiset_upper_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_RcIter = ms1.upper_bound( 20 );
   cout << "The first element of multiset ms1 with a key greater "
           << "than 20 is: " << *ms1_RcIter << "." << endl;

   ms1_RcIter = ms1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( ms1_RcIter == ms1.end( ) )
      cout << "The multiset ms1 doesn't have an element "
              << "with a key greater than 30." << endl;
   else
      cout << "The element of multiset ms1 with a key > 40 is: "
           << *ms1_RcIter << "." << endl;

   // The element at a specific location in the multiset can be
   // found using a dereferenced iterator addressing the location
   ms1_AcIter = ms1.begin( );
   ms1_RcIter = ms1.upper_bound( *ms1_AcIter );
   cout << "The first element of ms1 with a key greater than"
        << endl << "that of the initial element of ms1 is: "
        << *ms1_RcIter << "." << endl;
}
```

```Output
The first element of multiset ms1 with a key greater than 20 is: 30.
The multiset ms1 doesn't have an element with a key greater than 30.
The first element of ms1 with a key greater than
that of the initial element of ms1 is: 20.
```

## <a name="multisetvalue_comp"></a><a name="value_comp"></a>zestaw wielokrotny:: value_comp

Pobiera kopię obiektu porównania użytego do uporządkowania wartości elementów w zestawie wielokrotnym.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji używany przez zestaw wielokrotny do porządkowania jego elementów, który jest parametrem szablonu `Compare` .

Aby uzyskać więcej informacji na temat `Compare` , zobacz sekcję Uwagi w temacie [klasy zestaw wielokrotny](../standard-library/multiset-class.md) .

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członkowską:

**operator bool**( **klucz const&** `_xVal` , **klucz const&** `_yVal` );

Zwraca wartość true `_xVal` , jeśli poprzedza i nie jest równa `_yVal` w kolejności sortowania.

Należy zauważyć, że zarówno [key_compare](#key_compare) , jak i [value_compare](#value_compare) są synonimami dla parametru szablonu `Compare` . Oba typy są dostarczane dla klas zestawów i zestawów wielokrotnych, gdzie są identyczne, aby zapewnić zgodność z mapami klas i multimap, gdzie są różne.

### <a name="example"></a>Przykład

```cpp
// multiset_value_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   multiset <int, less<int> > ms1;
   multiset <int, less<int> >::value_compare vc1 = ms1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of ms1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of ms1."
           << endl;
   }

   set <int, greater<int> > ms2;
   set<int, greater<int> >::value_compare vc2 = ms2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of ms2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of ms2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of ms1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of ms2.
```

## <a name="multisetvalue_compare"></a><a name="value_compare"></a>zestaw wielokrotny:: value_compare

Typ, który dostarcza obiekt funkcji, który może porównać dwa klucze sortowania, aby określić ich względną kolejność w zestawie wielokrotnym.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Uwagi

`value_compare`jest synonimem dla parametru szablonu `Compare` .

Należy zauważyć, że zarówno [key_compare](#key_compare) , jak i `value_compare` są synonimami dla parametru szablonu `Compare` . Oba typy są dostarczane dla klas zestawów i zestawów wielokrotnych, gdzie są identyczne, aby zapewnić zgodność z mapami klas i multimap, gdzie są różne.

Aby uzyskać więcej informacji na temat `Compare` , zobacz sekcję Uwagi w temacie [klasy zestaw wielokrotny](../standard-library/multiset-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [value_comp](#value_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania `value_compare` .

## <a name="multisetvalue_type"></a><a name="value_type"></a>zestaw wielokrotny:: value_type

Typ, który opisuje obiekt przechowywany jako element jako wartość zestawu wielokrotnego.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Uwagi

`value_type`jest synonimem dla parametru szablonu `Key` .

Należy zauważyć, że zarówno [key_type](#key_type) , jak i `value_type` są synonimami dla parametru szablonu `Key` . Oba typy są dostarczane dla klas zestawów i zestawów wielokrotnych, gdzie są identyczne, aby zapewnić zgodność z mapami klas i multimap, gdzie są różne.

Aby uzyskać więcej informacji na temat `Key` , zobacz sekcję Uwagi w temacie.

### <a name="example"></a>Przykład

```cpp
// multiset_value_type.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;

   multiset <int> :: value_type svt_Int;   // Declare value_type
   svt_Int = 10;             // Initialize value_type

   multiset <int> :: key_type skt_Int;   // Declare key_type
   skt_Int = 20;             // Initialize key_type

   ms1.insert( svt_Int );         // Insert value into s1
   ms1.insert( skt_Int );         // Insert key into s1

   // A multiset accepts key_types or value_types as elements
   cout << "The multiset has elements:";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;
}
```

```Output
The multiset has elements: 10 20.
```

## <a name="see-also"></a>Zobacz także

[Opakowania](../cpp/containers-modern-cpp.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
