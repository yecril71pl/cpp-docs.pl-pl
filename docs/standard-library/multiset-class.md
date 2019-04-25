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
ms.openlocfilehash: 3b059db877d24f5e4414745ba6c2f9ee4f6591e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62205089"
---
# <a name="multiset-class"></a>multiset — Klasa

Standardowej biblioteki C++ multiset — klasa jest używana do przechowywania i pobierania danych z kolekcji, w której wartości zawartych elementów nie muszą być unikatowe, i które służą jako wartości klucza, zgodnie z którymi dane są automatycznie porządkowane. Nie można bezpośrednio zmienić wartości klucza elementu w zestawie wielokrotnym. Zamiast tego trzeba usunąć stare wartości i wstawić elementy z nowymi wartościami.

## <a name="syntax"></a>Składnia

```cpp
template <class Key, class Compare =less <Key>, class Allocator =allocator <Key>>
class multiset
```

### <a name="parameters"></a>Parametry

*Key*<br/>
Typ danych elementu do przechowywania w zestawie wielokrotnym.

*Compare*<br/>
Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w zestawie wielokrotnym. Predykat dwuelementowy **mniej**\<Key > jest wartością domyślną.

W języku C ++ 14 można włączyć heterogeniczne wyszukiwanie, określając `std::less<>` lub `std::greater<>` predykat, który nie ma parametrów typu. Aby uzyskać więcej informacji, zobacz [heterogeniczne wyszukiwanie w kontenerach asocjacyjnych](../standard-library/stl-containers.md#sequence_containers)

*Allocator*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji zestawu wielokrotnego i dezalokacji pamięci. Wartość domyślna to `allocator<Key>`.

## <a name="remarks"></a>Uwagi

Standardowej biblioteki C++ multiset — klasa to:

- Kontener asocjacyjny, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowe iteratory do dostępu do jego elementów.

- Posortowany, ponieważ jego elementy są uporządkowane według wartości kluczy w kontenerze zgodnie z określoną funkcją porównywania.

- Wielokrotny w tym sensie, że jego elementy nie muszą mieć unikatowych kluczy, więc jedna wartość klucza może mieć wiele wartości elementów z nią skojarzonych.

- Prosty kontener asocjacyjny, ponieważ jego wartości elementu są jego wartościami klucza.

- Klasa szablonu, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy. Typ danych, który ma być użyty, jest zamiast tego określony jako parametr w klasie szablonu wraz z funkcją porównania i alokatorem.

Iterator dostarczony przez klasę zestawu wielokrotnego jest iteratorem dwukierunkowym, ale funkcje składowych klasy [Wstaw](#insert) i [multiset](#multiset) mają wersje przyjmujące jako parametry szablonu słabszy iterator danych wejściowych którego wymagania funkcjonalności są mniejsze niż te gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcjonalności, ale jest wystarczający, aby można było mówić znacząco o zakresie iteratorów [ `First`, `Last`) w kontekście funkcji składowych klasy.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Kontenery asocjacyjne są zoptymalizowane dla operacji wyszukiwania, wstawiania oraz usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, są skuteczne, wykonując je w czasie, który jest średnio proporcjonalny do logarytmu liczby elementów w kontenerze. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Zestaw wielokrotny powinien być kontenerem asocjacyjnym z wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Elementów zestawu wielokrotnego może być wiele, mogą służyć jako własne klucze sortowania, więc klucze nie są unikatowe. Model dla tego typu konstrukcji jest uporządkowaną listą, np. wyrazów, w których wyrazy mogą występować więcej niż jeden raz. Gdyby nie zezwolono na wiele wystąpień wyrazów, odpowiednią strukturą kontenera byłby zestaw. Gdyby unikatowe definicje zostały dołączone jako wartości do listy unikatowych słów kluczowych, mapa byłaby odpowiednią strukturą zawierającą te dane. Gdyby natomiast definicje nie były unikatowe, mapa wielokrotna byłaby kontenerem z wyboru.

Zestaw wielokrotny porządkuje sekwencję którą kontroluje, przez wywołanie przechowywanego obiektu funkcji typu *porównaj*. Ten przechowywany obiekt jest funkcją porównywania, która może być dostępna poprzez wywołanie funkcji elementu członkowskiego [key_comp](#key_comp). Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Binarny predykat *f*( *x*, *y*) jest obiektem funkcji, która ma dwa obiekty argumentu *x* i *y* i wartość zwracana przez **true** lub **false**. Kolejność nałożona na zestaw jest ścisłym słabym porządkowaniem, jeśli predykat binarny jest niezwrotny, przeciwsymetryczny i przechodni oraz jeśli równoważność jest przechodnia, gdzie dwa obiekty x i y są zdefiniowane jako równoważne, gdy oba *f*( *x, y*) i *f*( *y, x*) mają wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

W języku C ++ 14 można włączyć heterogeniczne wyszukiwanie, określając `std::less<>` lub `std::greater<>` predykat, który nie ma parametrów typu. Aby uzyskać więcej informacji, zobacz [heterogeniczne wyszukiwanie w kontenerach asocjacyjnych](../standard-library/stl-containers.md#sequence_containers)

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[multiset](#multiset)|Konstruuje `multiset` oznacza to pusta lub czyli kopią całości lub części określonego `multiset`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Element typedef dla `allocator` klasy dla `multiset` obiektu.|
|[const_iterator](#const_iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytać **const** element `multiset`.|
|[const_pointer](#const_pointer)|Element typedef dla wskaźnika do **const** element `multiset`.|
|[const_reference](#const_reference)|Element typedef dla odwołania do **const** przechowywanego w `multiset` do odczytu i wykonywania **const** operacji.|
|[const_reverse_iterator](#const_reverse_iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytać dowolny **const** element `multiset`.|
|[difference_type](#difference_type)|Element typedef liczby całkowitej ze znakiem dla liczby elementów `multiset` w zakresie pomiędzy elementami wskazywanymi przez Iteratory.|
|[iterator](#iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytać lub zmodyfikować dowolny element w `multiset`.|
|[key_compare —](#key_compare)|Element typedef dla obiektu funkcji, która może porównać dwa klucze, aby określić względną kolejność dwóch elementów w `multiset`.|
|[key_type](#key_type)|Element typedef dla obiektu funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `multiset`.|
|[pointer](#pointer)|Element typedef dla wskaźnika do elementu w `multiset`.|
|[Odwołanie](#reference)|Element typedef dla odwołania do elementu przechowywanego w `multiset`.|
|[reverse_iterator](#reverse_iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytać lub zmodyfikować element w odwróconej `multiset`.|
|[size_type](#size_type)|Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w `multiset`.|
|[value_compare —](#value_compare)|Element typedef dla obiektu funkcji, która może porównać dwa elementy jako klucze sortowania, aby określić ich względną kolejność w `multiset`.|
|[value_type](#value_type)|Element typedef, który opisuje obiekt zapisany jako element jako `multiset` w charakterze wartości.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[begin](#begin)|Zwraca iterator, który wskazuje na pierwszy element w `multiset`.|
|[cbegin](#cbegin)|Zwraca iterator const, który dotyczy pierwszego elementu w `multiset`.|
|[cend](#cend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w `multiset`.|
|[Usuń zaznaczenie](#clear)|Usuwa wszystkie elementy `multiset`.|
|[Liczba](#count)|Zwraca liczbę elementów w `multiset` których klucz pasuje do klucza określonego jako parametr.|
|[crbegin](#crbegin)|Zwraca iterator const, który dotyczy pierwszego elementu w odwróconym zestawie.|
|[crend](#crend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconym zestawie.|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do `multiset`.|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do `multiset`, ze wskazówką położenia.|
|[pusty](#empty)|Sprawdza, czy `multiset` jest pusty.|
|[koniec](#end)|Zwraca iterator, który wskazuje na lokalizację po ostatnim elemencie w `multiset`.|
|[equal_range](#equal_range)|Zwraca parę iteratorów. Pierwszy iterator w parze wskazuje na pierwszy element w `multiset` przy użyciu klucza, który jest większy od określonego klucza. Drugi iterator w parze wskazuje na pierwszy element w `multiset` z kluczem, który jest równy lub większy niż określony klucz.|
|[wymazywanie](#erase)|Usuwa element lub zakres elementów w `multiset` z określonych pozycji lub usuwa elementy, które odpowiadają określonemu kluczowi.|
|[Znajdź](#find)|Zwraca iterator, który wskazuje na pierwszą lokalizację elementu w `multiset` ma klucz równy określonemu kluczowi.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu `allocator` obiektu, który służy do konstruowania `multiset`.|
|[insert](#insert)|Wstawia element lub zakres elementów do `multiset`.|
|[key_comp](#key_comp)|Dostarcza obiekt funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `multiset`.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu w `multiset` z kluczem, który jest równy lub większy od określonego klucza.|
|[max_size](#max_size)|Zwraca maksymalną długość `multiset`.|
|[rbegin](#rbegin)|Zwraca iterator, który wskazuje na pierwszy element w odwróconej `multiset`.|
|[rend](#rend)|Zwraca iterator, który wskazuje na lokalizację po ostatnim elemencie w odwróconej `multiset`.|
|[Rozmiar](#size)|Zwraca liczbę elementów w `multiset`.|
|[swap](#swap)|Zamienia elementy z dwóch `multiset`s.|
|[upper_bound —](#upper_bound)|Zwraca iterator do pierwszego elementu w `multiset` przy użyciu klucza, który jest większy od określonego klucza.|
|[value_comp](#value_comp)|Pobiera kopię obiektu porównania, która jest używana do uporządkowania wartości elementów w `multiset`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Zastępuje elementy `multiset` kopią innego `multiset`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<Ustaw >

**Namespace:** standardowe

## <a name="allocator_type"></a>  multiset::allocator_type

Typ, który reprezentuje klasę alokatora dla obiektu zestawów wielokrotnych

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type` synonim dla parametru szablonu jest `Allocator`.

Aby uzyskać więcej informacji na temat `Allocator`, zobacz sekcję Uwagi [multiset — klasa](../standard-library/multiset-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [get_allocator —](#get_allocator) dla usługi przy użyciu przykładu `allocator_type`

## <a name="begin"></a>  multiset::BEGIN

Zwraca iterator odnoszący się do pierwszego elementu w zestawie wielokrotnym.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pierwszego elementu w zestawie wielokrotnym lub lokalizacji następującej po pustego zestawu wielokrotnego.

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

## <a name="cbegin"></a>  multiset::cbegin

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

## <a name="cend"></a>  multiset::cend

Zwraca **const** iterator adresujący lokalizację tuż za ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

A **const** iterator dostępu dwukierunkowego, który wskazuje tuż za koniec zakresu.

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

## <a name="clear"></a>  multiset::Clear

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

## <a name="const_iterator"></a>  multiset::const_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać **const** elementu w zestawie wielokrotnym.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin) dla przykłady dotyczące używania `const_iterator`.

## <a name="const_pointer"></a>  multiset::const_pointer

Typ, który dostarcza wskaźnik do **const** elementu w zestawie wielokrotnym.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

W większości przypadków [iteratora](#iterator) powinien być używany do uzyskania dostępu do elementów w obiekcie multiset.

## <a name="const_reference"></a>  multiset::const_reference

Typ, który zawiera odwołanie do **const** elementu przechowywanego w zestawie wielokrotnym do odczytu i wykonywania **const** operacji.

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

## <a name="const_reverse_iterator"></a>  multiset::const_reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **const** elementu w zestawie wielokrotnym.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i jest używany do iterowania po multiset w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład [rend —](#rend) przykładowy sposób deklarowania i użyj `const_reverse_iterator`.

## <a name="count"></a>  multiset::Count

Zwraca liczbę elementów w zestawie wielokrotnym, których klucz pasuje do klucza określonego jako parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz elementy, które mają być dopasowywane w zestawie wielokrotnym.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w zestawie wielokrotnym, których klucz pasuje do klucza parametru.

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca liczbę elementów *x* w zakresie

\[ lower_bound (*klucz*), upper_bound (*klucz*))

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie multiset::count funkcja elementu członkowskiego.

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

## <a name="crbegin"></a>  multiset::crbegin

Zwraca iterator stałych adresujący pierwszy element w odwróconym zestawie wielokrotnym.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrócić iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconym zestawie wielokrotnym lub adresowania, który był ostatnim elementem w zestawie wielokrotnym nieodwróconej.

### <a name="remarks"></a>Uwagi

`crbegin` jest używana z odwróconej multiset tak samo jak rozpocząć jest używana z zestawu wielokrotnego.

Wartością zwracaną `crbegin`, nie można zmodyfikować obiektu multiset.

`crbegin` może służyć do iterowania po multiset Wstecz.

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

## <a name="crend"></a>  multiset::crend

Zwraca iterator stałych adresujący lokalizację następującą po ostatnim elemencie w odwróconym zestawie wielokrotnym.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iteratora dwukierunkowego, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconym zestawie wielokrotnym (miejsca przed pierwszego elementu w zestawie wielokrotnym nieodwróconej).

### <a name="remarks"></a>Uwagi

`crend` jest używana z odwróconej multiset podobnie jak [zakończenia](#end) jest używana z zestawu wielokrotnego.

Wartością zwracaną `crend`, nie można zmodyfikować obiektu multiset.

`crend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej multiset.

Wartość zwrócona przez obiekt `crend` nie należy usuwać odwołania.

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

## <a name="difference_type"></a>  multiset::difference_type

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów zestawu wielokrotnego w zakresie pomiędzy elementami wskazywanymi przez Iteratory.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` Jest typ zwracany, jeśli odjęcie lub inkrementacji poprzez Iteratory kontenera. `difference_type` Jest zazwyczaj używany do reprezentowania liczby elementów w zakresie [ `first`, `last`) między Iteratory `first` i `last`, zawiera element wskazywany przez `first` i zakres elementów do , ale bez element wskazane przez `last`.

Należy pamiętać, że chociaż `difference_type` jest dostępna dla wszystkich iteratorów, które spełniają wymagania iteratora danych wejściowych zawiera klasę iteratorów dwukierunkowych obsługiwane przez odwracalnego kontenerów, takich jak zestaw, odejmowania między Iteratory jest tylko obsługiwane przez Iteratory dostępu swobodnego, dostarczone przez kontener dostępu swobodnego, takich jak wektora.

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

## <a name="emplace"></a>  multiset::emplace

Wstawia element skonstruowany w miejscu (nie kopiowania lub przenoszenia operacji), ze wskazówką położenia.

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*argumenty*|Argumenty przekazywane do konstruowania element do wstawienia w zestawie wielokrotnym.|

### <a name="return-value"></a>Wartość zwracana

Iterator do nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Nie odwołania do elementów kontenera nie są unieważniane przez tę funkcję, ale może unieważnić, wszystkie Iteratory do kontenera.

Podczas umieszczanie Jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany.

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

## <a name="emplace_hint"></a>  multiset::emplace_hint

Wstawia element skonstruowany w miejscu (nie kopiowania lub przenoszenia operacji), ze wskazówką położenia.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*argumenty*|Argumenty przekazywane do konstruowania element do wstawienia w zestawie wielokrotnym.|
|*gdzie*|Miejsce, aby rozpocząć wyszukiwanie poprawne punktu wstawiania. (Jeśli danego punktu bezpośrednio poprzedza *gdzie*, wstawiania może wystąpić w amortyzowanym stałym czasie zamiast czasu logarytmicznych.)|

### <a name="return-value"></a>Wartość zwracana

Iterator do nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Nie odwołania do elementów kontenera nie są unieważniane przez tę funkcję, ale może unieważnić, wszystkie Iteratory do kontenera.

Podczas umieszczanie Jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany.

Dla przykładu kodu zobacz [set::emplace_hint](../standard-library/set-class.md#emplace_hint).

## <a name="empty"></a>  multiset::Empty

Sprawdza, czy zestaw wielokrotny jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli zestaw wielokrotny jest pusta. **false** przypadku niepustych zestawie wielokrotnym.

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

## <a name="end"></a>  multiset::end

Zwraca iterator poza końcem.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator przeszłości zakończenia. Jeśli zestaw wielokrotny jest pusta, następnie `multiset::end() == multiset::begin()`.

### <a name="remarks"></a>Uwagi

**koniec** służy do sprawdzenia, czy iterator minął koniec jego multiset.

Wartość zwrócona przez obiekt **zakończenia** nie należy usuwać odwołania.

Dla przykładu kodu zobacz [multiset::find](#find).

## <a name="equal_range"></a>  multiset::equal_range

Zwraca parę iteratorów odpowiednio do pierwszego elementu w zestawie wielokrotnym przy użyciu klucza, który jest większy od określonego klucza i do pierwszego elementu w zestawie wielokrotnym przy użyciu klucza, który jest równy lub większy niż określony klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucza, który ma zostać porównane z klucza sortowania elementu w zestawie wielokrotnym wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Parę iteratorów tak, aby był pierwszym [lower_bound](#lower_bound) klucz, a drugi jest [upper_bound](#upper_bound) klucza.

Pierwszym iteratorem pary dostęp do `pr` zwróconą przez funkcję elementu członkowskiego, użyj `pr`. **pierwszy**, wyłuskać iteratora dolną granicę użyj \*( `pr`. **najpierw**). Aby uzyskać dostęp drugi iterator w parze `pr` zwróconą przez funkcję elementu członkowskiego, użyj `pr`. **drugi**, wyłuskać iteratora górną granicę użyj \*( `pr`. **Po drugie**).

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

## <a name="erase"></a>  multiset::ERASE

Usuwa element lub zakres elementów w zestawie wielokrotnym z określonych pozycji lub usuwa elementy, które odpowiadają określonemu kluczowi.

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

*Where*<br/>
Pozycja elementu, który ma zostać usunięty.

*pierwszy*<br/>
Pozycja pierwszego elementu do usunięcia.

*ostatni*<br/>
Pozycja tuż za ostatni element do usunięcia.

*Key*<br/>
Wartość klucza elementów do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie funkcje Członkowskie, aby uzyskać iteratora dwukierunkowego, określa pierwszy element pozostający poza wszelkimi elementami usuniętymi lub element, który jest końcem zestaw wielokrotny, jeśli taki element nie istnieje.

Dla trzeciego funkcja elementu członkowskiego zwraca liczbę elementów, które zostały usunięte w zestawie wielokrotnym.

### <a name="remarks"></a>Uwagi

Dla przykładu kodu zobacz [set::erase](../standard-library/set-class.md#erase).

## <a name="find"></a>  multiset::Find

Zwraca iterator, który odwołuje się do lokalizacji elementu w zestawie wielokrotnym, który ma klucz równoważny z określonym kluczem.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza, które mają być dopasowywane o klucz sortowania elementu w zestawie wielokrotnym wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Iterator, który odwołuje się do lokalizacji elementu z określonym kluczem lub lokalizację po ostatnim elemencie w zestawie wielokrotnym ( `multiset::end()`) Jeśli nie zostanie znalezione dopasowanie dla klucza.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator, który odwołuje się do elementu w zestawie wielokrotnym, którego klucz jest równoważne argumentowi *klucza* w obszarze predykat binarny, który wymusza kolejność oparte na mniej niż porównywalności relacji.

Jeśli wartość zwracaną przez `find` jest przypisany do `const_iterator`, nie można zmodyfikować obiektu multiset. Jeśli wartość zwracaną przez `find` jest przypisany do `iterator`, można zmodyfikować multiset — obiekt

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

## <a name="get_allocator"></a>  multiset::get_allocator

Zwraca kopię obiektu programu przydzielania użytego do stworzenia zestawie wielokrotnym.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez zestaw wielokrotny.

### <a name="remarks"></a>Uwagi

Puli buforów dla klasy multiset — Określ, jak klasa zarządza magazynem. Buforów domyślną dostarczony wraz z klasy kontenera standardowej biblioteki języka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.

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

## <a name="insert"></a>  multiset::INSERT

Wstawia element lub zakres elementów w zestawie wielokrotnym.

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
|*Val*|Wartość elementu do wstawienia w zestawie wielokrotnym.|
|*Where*|Miejsce, aby rozpocząć wyszukiwanie poprawne punktu wstawiania. (Jeśli danego punktu bezpośrednio poprzedza *gdzie*, wstawiania może wystąpić w amortyzowanym stałym czasie zamiast czasu logarytmicznych.)|
|*ValTy*|Parametr szablonu określający typ argumentu, który zestaw wielokrotny służy do konstruowania elementu [value_type](../standard-library/map-class.md#value_type)i przekazuje doskonałe rozwiązanie *Val* jako argument.|
|*pierwszy*|Pozycja pierwszego elementu, który ma być skopiowany.|
|*ostatni*|Pozycja tuż za ostatnim elementem do skopiowania.|
|*InputIterator*|Argument funkcji szablonu, który spełnia wymagania [iterator danych wejściowych](../standard-library/input-iterator-tag-struct.md) wskazującej elementów typu, który może służyć do konstruowania [value_type](../standard-library/map-class.md#value_type) obiektów.|
|*IList*|[Initializer_list](../standard-library/initializer-list.md) z którego można skopiować elementy.|

### <a name="return-value"></a>Wartość zwracana

Funkcje elementów członkowskich pojedynczego elementu Wstawianie (1) i (2), zwracają iterator miejsce, gdy nowy element została umieszczona w zestawie wielokrotnym.

Funkcje Członkowskie jednego elementu za pomocą wskazówki, (3) i (4) zwraca iterator, który wskazuje miejsce, gdy nowy element została umieszczona w zestawie wielokrotnym.

### <a name="remarks"></a>Uwagi

Nie wskaźników lub odwołań są unieważniane przez tę funkcję, ale może unieważnić, wszystkie Iteratory do kontenera.

Podczas wstawiania tylko jeden element Jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany. Podczas wstawiania wielu elementów jeśli wyjątek jest zgłaszany, kontener pozostanie w stanie nieokreślony, ale prawidłowe.

[Value_type](../standard-library/map-class.md#value_type) kontenera jest typedef, który należy do kontenera, a w przypadku zestawu, `multiset<V>::value_type` jest typem `const V`.

Zakres funkcji członkowskiej (5) wstawia sekwencji wartości elementów na zestaw wielokrotny odpowiadający każdemu elementowi dotyczy iterację w zakresie `[First, Last)`; w związku z tym `Last` nie Pobierz wstawione. Funkcja elementu członkowskiego kontenera `end()` odwołuje się do pozycji zaraz po ostatnim elemencie w kontenerze — na przykład instrukcja `s.insert(v.begin(), v.end());` wstawia wszystkie elementy `v` do `s`.

(6) używa funkcji elementu członkowskiego listy inicjatorów [initializer_list](../standard-library/initializer-list.md) można skopiować elementów w zestawie wielokrotnym.

Do wstawienia element skonstruowany w miejscu — oznacza to, że są wykonywane żadne operacje kopiowania lub przenoszenia — zobacz [multiset::emplace](#emplace) i [multiset::emplace_hint](#emplace_hint).

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

## <a name="iterator"></a>  multiset::iterator

Typ, który zapewnia stałą [iteratora dwukierunkowego](../standard-library/bidirectional-iterator-tag-struct.md) służące do odczytywania dowolnego elementu w zestawie wielokrotnym.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin) przykładowy sposób deklarowania i użyj `iterator`.

## <a name="key_comp"></a>  multiset::key_comp

Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w zestawie wielokrotnym.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji, który zestaw wielokrotny używa do porządkowania jego elementów, czyli wartość parametru szablonu `Compare`.

Aby uzyskać więcej informacji na temat `Compare`, zobacz sekcję Uwagi [multiset — klasa](../standard-library/multiset-class.md) tematu.

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członka:

**bool — operator**( **const Key &** *x*, **const Key &** *y*);

które zwraca wartość true, jeśli *x* ściśle poprzedza *y* w porządku sortowania.

Należy pamiętać, że oba [key_compare](#key_compare) i [value_compare](#value_compare) synonimy dla parametru szablonu są `Compare`. Oba typy są dostarczane dla zestawu klas i multiset, gdzie są identyczne, zgodność z mapy klasy i multimap, gdy są one różne.

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

## <a name="key_compare"></a>  multiset::key_compare

Typ, który dostarcza obiekt funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w zestawie wielokrotnym.

```cpp
typedef Compare key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare` synonim dla parametru szablonu jest `Compare`.

Aby uzyskać więcej informacji na temat `Compare`, zobacz sekcję Uwagi [multiset — klasa](../standard-library/multiset-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [key_comp](#key_comp) przykładowy sposób deklarowania i użyj `key_compare`.

## <a name="key_type"></a>  multiset::key_type

Typ, który dostarcza obiekt funkcji, która może porównać klucze sortowania, aby określić względną kolejność dwóch elementów w zestawie wielokrotnym.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type` synonim dla parametru szablonu jest `Key`.

Aby uzyskać więcej informacji na temat `Key`, zobacz sekcję Uwagi [multiset — klasa](../standard-library/multiset-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) przykładowy sposób deklarowania i użyj `key_type`.

## <a name="lower_bound"></a>  multiset::lower_bound

Zwraca iterator do pierwszego elementu w zestawie wielokrotnym przy użyciu klucza, który jest równy lub większy od określonego klucza.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucza, który ma zostać porównane z klucza sortowania elementu w zestawie wielokrotnym wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

`iterator` Lub `const_iterator` , adresy lokalizację elementu w zestawie wielokrotnym czy za pomocą klucza, który jest równy lub większy niż określony klucz argument lub który zapewnia lokalizację po ostatnim elemencie w zestawie wielokrotnym, jeśli nie są zgodne, zostanie znaleziony dla klucza.

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

## <a name="max_size"></a>  multiset::max_size

Zwraca maksymalną długość zestawie wielokrotnym.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna możliwa długość zestawie wielokrotnym.

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

## <a name="multiset"></a>  multiset::multiset

Tworzy zestaw wielokrotny, który jest pusty lub jest kopią całości lub części niektórych innych multiset.

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
|*Al*|Klasa alokatora magazynu, który ma być używany dla tego obiektu multiset, która domyślnie `Allocator`.|
|*Comp*|Funkcja porównywania typu `const Compare` porządkowania elementów w zestawie wielokrotnym, wartość domyślna to `Compare`.|
|*po prawej stronie*|Multiset, w której skonstruowany multiset jest kopią.|
|*pierwszy*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*ostatni*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|
|*IList*|Lista initializer_list, z której mają być skopiowane elementy.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują obiekt alokatora, który zarządza przechowywania w pamięci dla zestaw wielokrotny, a które później mogą być zwracane przez wywołanie metody typu [get_allocator —](#get_allocator). Parametr alokatora jest często pomijane w deklaracji klasy i wstępnego przetwarzania makra używane do zastąpienia buforów alternatywne.

Wszystkie konstruktory inicjują ich multiset.

Wszystkie konstruktory magazynu, obiektu funkcji typu porównania, który jest używany do ustanawiania zamówienie klawiszy zestaw wielokrotny i które później mogą być zwracane przez wywołanie metody [key_comp](#key_comp).

Pierwsze trzy konstruktory określić pustego zestawu wielokrotnego początkowej, drugi określając typ funkcji porównywania (*Comp*) ma być używany, ustalając kolejność elementów, a trzeci, jawnie określając alokator wpisz (*Al*) ma być używany. Słowo kluczowe **jawne** powoduje pominięcie niektórych rodzajów konwersji typu automatyczne.

Czwarty Konstruktor Określa kopię zestaw wielokrotny *po prawej stronie*.

Piąty Konstruktor Określa kopię zestaw wielokrotny, przenosząc *po prawej stronie*.

Szóstego, siódmy i ósmy Konstruktor określają initializer_list, z którego można skopiować elementy.

Następne trzy konstruktory kopiują zakres `[First, Last)` multiset uwzględni się rosnącą explicitness, określając typ funkcją porównywania oraz alokatorem.

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

## <a name="op_eq"></a>  multiset::operator =

Zastępuje elementy to `multiset` za pomocą elementów z innego `multiset`.

```cpp
multiset& operator=(const multiset& right);

multiset& operator=(multiset&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*right*|`multiset` z elementy, które są kopiowane lub przeniesiony.|

### <a name="remarks"></a>Uwagi

`operator=` kopiuje lub przenosi elementy *prawo* do tego `multiset`, w zależności od typu odwołania (lvalue lub rvalue) używane. Elementy, które znajdują się w tym `multiset` przed `operator=` wykonuje zostaną odrzucone.

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

## <a name="pointer"></a>  multiset::Pointer

Typ, który dostarcza wskaźnik do elementu w zestawie wielokrotnym.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ **wskaźnik** może służyć do modyfikowania wartości elementu.

W większości przypadków [iteratora](#iterator) powinien być używany do uzyskania dostępu do elementów w obiekcie multiset.

## <a name="rbegin"></a>  multiset::rbegin

Zwraca iterator odnoszący się do pierwszego elementu w odwróconym zestawie wielokrotnym.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconym zestawie wielokrotnym lub adresowania, który był ostatnim elementem w zestawie wielokrotnym nieodwróconej.

### <a name="remarks"></a>Uwagi

`rbegin` jest używana z odwróconej multiset, tak samo, jak rbegin — jest używana z zestawu wielokrotnego.

Jeśli wartość zwracaną przez `rbegin` jest przypisany do `const_reverse_iterator`, wówczas nie można zmodyfikować obiektu multiset. Jeśli wartość zwracaną przez `rbegin` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiekt multiset.

`rbegin` może służyć do iterowania po multiset Wstecz.

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

## <a name="reference"></a>  multiset::Reference

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

## <a name="rend"></a>  multiset::rend

Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w odwróconym zestawie wielokrotnym.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do lokalizacji następującej po ostatnim elemencie w odwróconym zestawie wielokrotnym (miejsca przed pierwszego elementu w zestawie wielokrotnym nieodwróconej).

### <a name="remarks"></a>Uwagi

`rend` jest używana z odwróconej multiset podobnie jak [zakończenia](#end) jest używana z zestawu wielokrotnego.

Jeśli wartość zwracaną przez `rend` jest przypisany do `const_reverse_iterator`, wówczas nie można zmodyfikować obiektu multiset. Jeśli wartość zwracaną przez `rend` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiekt multiset.

`rend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej multiset.

Wartość zwrócona przez obiekt `rend` nie należy usuwać odwołania.

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

## <a name="reverse_iterator"></a>  multiset::reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconym zestawie wielokrotnym.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iterowania po multiset w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład dotyczący [rbegin —](#rbegin) przykładowy sposób deklarowania i użyj `reverse_iterator`.

## <a name="size"></a>  multiset::size

Zwraca liczbę elementów w zestawie wielokrotnym.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość zestawie wielokrotnym.

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

## <a name="size_type"></a>  multiset::size_type

Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w zestawie wielokrotnym.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Przykład

Zobacz przykład dotyczący [rozmiar](#size) przykładem sposobu deklarowanie i użycie `size_type`

## <a name="swap"></a>  multiset::swap

Zamienia elementy z dwóch multisets.

```cpp
void swap(
    multiset<Key, Compare, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Zestaw wielokrotny argumentu, zawierająca elementy, które zamianę z docelowym zestawie wielokrotnym.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego powoduje unieważnienie nie odwołania wskaźniki i Iteratory, które wyznaczają elementy w dwóch multisets, której elementy są wymianie.

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

## <a name="upper_bound"></a>  multiset::upper_bound

Zwraca iterator do pierwszego elementu w zestawie wielokrotnym przy użyciu klucza, który jest większy od określonego klucza.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucza, który ma zostać porównane z klucza sortowania elementu w zestawie wielokrotnym wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

**Iteratora** lub `const_iterator` który dotyczy lokalizacji elementu w zestawie wielokrotnym przy użyciu klucza, który jest większy niż określony klucz argument, lub który adresów lokalizację po ostatnim elemencie w zestawie wielokrotnym, jeśli nie zostanie znalezione dopasowanie dla klucz.

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

## <a name="value_comp"></a>  multiset::value_comp

Pobiera kopię obiektu porównania, używany do uporządkowania wartości elementów w zestawie wielokrotnym.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji, który zestaw wielokrotny używa do porządkowania jego elementów, czyli wartość parametru szablonu `Compare`.

Aby uzyskać więcej informacji na temat `Compare`, zobacz sekcję Uwagi [multiset — klasa](../standard-library/multiset-class.md) tematu.

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członka:

**bool — operator**( **const Key &**`_xVal`, **const Key &**`_yVal`);

które zwraca wartość true, jeśli `_xVal` poprzedza i nie jest równa `_yVal` w porządku sortowania.

Należy pamiętać, że oba [key_compare](#key_compare) i [value_compare](#value_compare) synonimy dla parametru szablonu są `Compare`. Oba typy są dostarczane dla zestawu klas i multiset, gdzie są identyczne, zgodność z mapy klasy i multimap, gdy są one różne.

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

## <a name="value_compare"></a>  multiset::value_compare

Typ, który dostarcza obiekt funkcji, która może porównać dwa klucze sortowania, aby określić ich względną kolejność w zestawie wielokrotnym.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Uwagi

`value_compare` synonim dla parametru szablonu jest `Compare`.

Należy pamiętać, że oba [key_compare](#key_compare) i `value_compare` synonimy dla parametru szablonu są `Compare`. Oba typy są dostarczane dla zestawu klas i multiset, gdzie są identyczne, zgodność z mapy klasy i multimap, gdy są one różne.

Aby uzyskać więcej informacji na temat `Compare`, zobacz sekcję Uwagi [multiset — klasa](../standard-library/multiset-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [value_comp —](#value_comp) przykładowy sposób deklarowania i użyj `value_compare`.

## <a name="value_type"></a>  multiset::value_type

Typ, który opisuje obiekt zapisany jako element jako zestaw wielokrotny w charakterze wartości.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Uwagi

`value_type` synonim dla parametru szablonu jest `Key`.

Należy pamiętać, że oba [key_type](#key_type) i `value_type` synonimy dla parametru szablonu są `Key`. Oba typy są dostarczane dla zestawu klas i multiset, gdzie są identyczne, zgodność z mapy klasy i multimap, gdy są one różne.

Aby uzyskać więcej informacji na temat `Key`, zobacz sekcję Uwagi w temacie.

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

[Kontenery](../cpp/containers-modern-cpp.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
