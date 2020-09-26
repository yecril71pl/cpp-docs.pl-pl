---
title: multimap — Klasa
description: Dokumentacja interfejsu API dla klasy języka C++ (standard Template Library) `multimap` , która jest używana do przechowywania i pobierania danych z kolekcji, w której każdy element jest parą, która ma zarówno wartość danych, jak i klucz sortowania.
ms.date: 9/9/2020
f1_keywords:
- map/std::multimap
- map/std::multimap::allocator_type
- map/std::multimap::const_iterator
- map/std::multimap::const_pointer
- map/std::multimap::const_reference
- map/std::multimap::const_reverse_iterator
- map/std::multimap::difference_type
- map/std::multimap::iterator
- map/std::multimap::key_compare
- map/std::multimap::key_type
- map/std::multimap::mapped_type
- map/std::multimap::pointer
- map/std::multimap::reference
- map/std::multimap::reverse_iterator
- map/std::multimap::size_type
- map/std::multimap::value_type
- map/std::multimap::begin
- map/std::multimap::cbegin
- map/std::multimap::cend
- map/std::multimap::clear
- map/std::multimap::contains
- map/std::multimap::count
- map/std::multimap::crbegin
- map/std::multimap::crend
- map/std::multimap::emplace
- map/std::multimap::emplace_hint
- map/std::multimap::empty
- map/std::multimap::end
- map/std::multimap::equal_range
- map/std::multimap::erase
- map/std::multimap::find
- map/std::multimap::get_allocator
- map/std::multimap::insert
- map/std::multimap::key_comp
- map/std::multimap::lower_bound
- map/std::multimap::max_size
- map/std::multimap::rbegin
- map/std::multimap::rend
- map/std::multimap::size
- map/std::multimap::swap
- map/std::multimap::upper_bound
- map/std::multimap::value_comp
helpviewer_keywords:
- std::multimap [C++]
- std::multimap [C++], allocator_type
- std::multimap [C++], const_iterator
- std::multimap [C++], const_pointer
- std::multimap [C++], const_reference
- std::multimap [C++], const_reverse_iterator
- std::multimap [C++], difference_type
- std::multimap [C++], iterator
- std::multimap [C++], key_compare
- std::multimap [C++], key_type
- std::multimap [C++], mapped_type
- std::multimap [C++], pointer
- std::multimap [C++], reference
- std::multimap [C++], reverse_iterator
- std::multimap [C++], size_type
- std::multimap [C++], value_type
- std::multimap [C++], begin
- std::multimap [C++], cbegin
- std::multimap [C++], cend
- std::multimap [C++], clear
- std::multimap [C++], contains
- std::multimap [C++], count
- std::multimap [C++], crbegin
- std::multimap [C++], crend
- std::multimap [C++], emplace
- std::multimap [C++], emplace_hint
- std::multimap [C++], empty
- std::multimap [C++], end
- std::multimap [C++], equal_range
- std::multimap [C++], erase
- std::multimap [C++], find
- std::multimap [C++], get_allocator
- std::multimap [C++], insert
- std::multimap [C++], key_comp
- std::multimap [C++], lower_bound
- std::multimap [C++], max_size
- std::multimap [C++], rbegin
- std::multimap [C++], rend
- std::multimap [C++], size
- std::multimap [C++], swap
- std::multimap [C++], upper_bound
- std::multimap [C++], value_comp
ms.assetid: 8796ae05-37c4-475a-9e61-75fde9d4a463
ms.openlocfilehash: 446c1af793b885646dbb5658242e75482ebb92de
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353197"
---
# <a name="multimap-class"></a>multimap — Klasa

Klasa multimap standardowej biblioteki C++ służy do przechowywania i pobierania danych z kolekcji, w której każdy element jest parą, która ma zarówno wartość danych, jak i klucz sortowania. Wartość klucza nie musi być unikatowa i służy do automatycznego porządkowania danych. Wartość elementu w mapie wielokrotnej, ale nie wartość jego skojarzonego klucza, może być zmieniona bezpośrednio. Zamiast tego, wartości kluczy skojarzone ze starymi elementami muszą zostać usunięte, a nowe wartości klucza skojarzone z nowymi wstawionymi elementami.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Type,
    class Traits=less <Key>,
    class Allocator=allocator <pair  <const Key, Type>>>
class multimap;
```

### <a name="parameters"></a>Parametry

*Głównych*\
Typ danych klucza, który ma być przechowywany w mapie wielokrotnej.

*Wprowadź*\
Typ danych elementu, który ma być przechowywany w mapie wielokrotnej.

*Cech*\
Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w mapie wielokrotnej. Predykat binarny `less<Key>` jest wartością domyślną.

W języku C++ 14 można włączyć wyszukiwanie heterogeniczne, określając `std::less<>` `std::greater<>` predykat or, który nie ma parametrów typu. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie heterogeniczne w kontenerach asocjacyjnych](../standard-library/stl-containers.md#heterogeneous-lookup-in-associative-containers-c14)

*Alokator*\
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji mapy i dezalokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to `allocator<pair <const Key, Type> >` .

## <a name="remarks"></a>Uwagi

Klasa multimap standardowej biblioteki C++ to

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowe iteratory do dostępu do jego elementów.

- Posortowany, ponieważ jego elementy są uporządkowane według wartości kluczy w kontenerze zgodnie z określoną funkcją porównywania.

- Wiele, ponieważ jego elementy nie muszą mieć unikatowego klucza, więc jedna wartość klucza może mieć wiele wartości danych elementu skojarzonych z nim.

- Kontenerem skojarzonych par, ponieważ jej wartości danych elementu różnią się od wartości klucza.

- Szablon klasy, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Iterator dostarczony przez klasę mapy jest iteratorem dwukierunkowym, ale funkcje składowych klasy [INSERT](#insert) i [multimap](#multimap) mają wersje przyjmujące jako parametry szablonu słabszy iterator danych wejściowych, którego wymagania funkcjonalności są mniejsze niż te gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcjonalności, ale jest wystarczający, aby można było mówić istotnie o zakresie iteratorów `[First, Last)` w kontekście funkcji składowych klasy.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Kontenery asocjacyjne są zoptymalizowane dla operacji wyszukiwania, wstawiania i usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, są skuteczne, wykonując je w czasie, który jest średnio proporcjonalny do logarytmu liczby elementów w kontenerze. Wstawianie elementów unieważnia brak iteratorów i usunięcie elementów unieważnia tylko te Iteratory, które wskazywały na usunięte elementy.

Mapa wielokrotna powinna być kontenerem asocjacyjnym z wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Model dla tego typu struktury jest uporządkowaną listą słów kluczowych ze skojarzonymi wartościami ciągu dostarczającymi, wymawianymi, definicjami, w których wyrazy nie były zawsze jednoznacznie zdefiniowane. Jeśli zamiast tego słowa kluczowe zostały unikalnie zdefiniowane, tak że klucze są unikalne, wybranym kontenerem będzie map. Jeśli z drugiej strony, przechowywana była tylko lista wyrazów, poprawnym kontenerem będzie set. Jeśli dozwolone są wiele wystąpień wyrazów, będzie to `multiset` odpowiednia struktura kontenera.

Multimap porządkuje sekwencję, która kontroluje, przez wywołanie przechowywanego obiektu funkcji typu [key_compare](#key_compare). Ten przechowywany obiekt jest funkcją porównywania, do której można uzyskać dostęp, wywołując funkcję członkowską [key_comp](#key_comp). Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarny `f(x,y)` jest obiektem funkcji, który ma dwa obiekty argumentów `x` i `y` zwraca wartość true lub false. Kolejność nałożona na zestaw jest ścisłym słabym porządkowaniem, jeśli Predykat binarny jest niezwrotny, niesymetryczny i przechodni oraz jeśli równoważność jest przechodnia, gdzie dwa obiekty `x` i `y` są zdefiniowane jako równoważne, gdy oba `f(x,y)` i `f(y,x)` mają wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

W języku C++ 14 można włączyć wyszukiwanie heterogeniczne, określając `std::less<>` `std::greater<>` predykat or, który nie ma parametrów typu. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie heterogeniczne w kontenerach asocjacyjnych](../standard-library/stl-containers.md#sequence_containers) .

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[multimap](#multimap)|Tworzy obiekt `multimap` , który jest pusty lub jest kopią całości lub części innej `multimap` .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje `allocator` klasę dla `multimap` obiektu.|
|[const_iterator](#const_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać **`const`** element w `multimap` .|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do **`const`** elementu w `multimap` .|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do **`const`** elementu przechowywanego w trakcie `multimap` operacji odczytywania i wykonywania **`const`** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **`const`** element w `multimap` .|
|[difference_type](#difference_type)|Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów `multimap` w zakresie między elementami wskazywanymi przez Iteratory.|
|[Iterator](#iterator)|Typ, który zawiera różnicę między dwoma iteratorami odwołującymi się do elementów w obrębie tego samego `multimap` .|
|[key_compare](#key_compare)|Typ, który dostarcza obiekt funkcji, który może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `multimap` .|
|[key_type](#key_type)|Typ, który opisuje obiekt klucza sortowania, który składa się z każdego elementu `multimap` .|
|[mapped_type](#mapped_type)|Typ, który reprezentuje typ danych przechowywany w `multimap` .|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do **`const`** elementu w `multimap` .|
|[odwoła](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w `multimap` .|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej postaci `multimap` .|
|[size_type](#size_type)|Typ liczby całkowitej bez znaku, który dostarcza wskaźnik do **`const`** elementu w `multimap` .|
|[value_type](#value_type)|Typ, który dostarcza obiekt funkcji, który może porównać dwa elementy jako klucze sortowania, aby określić ich względną kolejność w obiekcie `multimap` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[zaczną](#begin)|Zwraca iterator odnoszący się do pierwszego elementu w `multimap` .|
|[cbegin](#cbegin)|Zwraca iterator const odnoszący się do pierwszego elementu w `multimap` .|
|[cend](#cend)|Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie w `multimap` .|
|[Wyczyść](#clear)|Kasuje wszystkie elementy `multimap` .|
|[zawiera](#contains)<sup>c++ 20</sup>|Sprawdza, czy w elemencie istnieje element z określonym kluczem `multimap` .|
|[liczbą](#count)|Zwraca liczbę elementów w zakresie, `multimap` których klucz pasuje do klucza określonego przez parametr.|
|[crbegin —](#crbegin)|Zwraca iterator const odnoszący się do pierwszego elementu w odwróconym `multimap` .|
|[crend](#crend)|Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym stanie `multimap` .|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do `multimap` .|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do `multimap` , z wskazówką umieszczenia|
|[puste](#empty)|Testuje, czy `multimap` jest pusty.|
|[punktów](#end)|Zwraca iterator, który odnosi się do lokalizacji po ostatnim elemencie w `multimap` .|
|[equal_range](#equal_range)|Wyszukuje zakres elementów, gdzie klucz elementu pasuje do określonej wartości.|
|[Wyłączanie](#erase)|Usuwa element lub zakres elementów `multimap` z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.|
|[wyświetlić](#find)|Zwraca iterator odnoszący się do pierwszej lokalizacji elementu w `multimap` , który ma klucz równoważny do określonego klucza.|
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` obiektu użytego do skonstruowania `multimap` .|
|[wstawienia](#insert)|Wstawia element lub zakres elementów do `multimap` .|
|[key_comp](#key_comp)|Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w obiekcie `multimap` .|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu w `multimap` , który jest kluczem, który jest równy lub większy niż określony klucz.|
|[max_size](#max_size)|Zwraca maksymalną długość `multimap` .|
|[rbegin](#rbegin)|Zwraca iterator odnoszący się do pierwszego elementu w odwróconym `multimap` .|
|[rend](#rend)|Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w odwróconym `multimap` .|
|[zmienia](#size)|Zwraca liczbę elementów w `multimap` .|
|[wymiany](#swap)|Wymienia elementy dwóch `multimap` s.|
|[upper_bound](#upper_bound)|Zwraca iterator do pierwszego elementu w elemencie `multimap` , który jest większy niż określony klucz.|
|[value_comp](#value_comp)|Funkcja członkowska zwraca obiekt funkcji, który określa kolejność elementów w a `multimap` przez porównanie ich wartości klucza.|

|Operator|Opis|
|-|-|
|[operator =](#op_eq)|Zastępuje elementy a `multimap` kopią inną `multimap` .|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<map>

**Przestrzeń nazw:** std

Pary ( **klucz**, **wartość**) są przechowywane w multimap jako obiekty typu `pair` . Klasa para wymaga nagłówka \<utility> , który jest automatycznie dołączany przez \<map> .

## <a name="multimapallocator_type"></a><a name="allocator_type"></a> multimap:: allocator_type

Typ, który reprezentuje klasę alokatora dla obiektu multimap.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [get_allocator](#get_allocator) , aby uzyskać przykład użycia `allocator_type` .

## <a name="multimapbegin"></a><a name="begin"></a> multimap:: BEGIN

Zwraca iterator odnoszący się do pierwszego elementu w multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pierwszego elementu w multimap lub lokalizacji po pomyślnym wykonaniu pustej multimap.

### <a name="example"></a>Przykład

```cpp
// multimap_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err as the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "First element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
First element of m1 is now 1
```

## <a name="multimapcbegin"></a><a name="cbegin"></a> multimap:: cbegin

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

## <a name="multimapcend"></a><a name="cend"></a> multimap:: cend

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

Nie można usunąć odwołania do wartości zwracanej przez nie `cend` .

## <a name="multimapclear"></a><a name="clear"></a> multimap:: Clear

Usuwa wszystkie elementy multimap.

```cpp
void clear();
```

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie funkcji multimap:: Clear member.

```cpp
// multimap_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1;
   multimap<int, int>::size_type i;
   typedef pair<int, int> Int_Pair;

   m1.insert(Int_Pair(1, 1));
   m1.insert(Int_Pair(2, 4));

   i = m1.size();
   cout << "The size of the multimap is initially "
        << i << "." << endl;

   m1.clear();
   i = m1.size();
   cout << "The size of the multimap after clearing is "
        << i << "." << endl;
}
```

```Output
The size of the multimap is initially 2.
The size of the multimap after clearing is 0.
```

## <a name="multimapconst_iterator"></a><a name="const_iterator"></a> multimap:: const_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać **`const`** element w multimap.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może być używany do modyfikacji wartości elementu.

`const_iterator`Zdefiniowane przez multimap wskazują na obiekty [value_type](#value_type), które są typu `pair<const Key, Type>` . Wartość klucza jest dostępna za pomocą pierwszej pary elementu członkowskiego, a wartość mapowanego elementu jest dostępna za pomocą drugiego elementu członkowskiego pary.

Aby usunąć odwołanie do `const_iterator` *cytowania* wskazującego element w multimap, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `cIter->first` , który jest odpowiednikiem `(*cIter).first` . Aby uzyskać dostęp do wartości mapowanej podstawy dla elementu, użyj `cIter->second` , który jest odpowiednikiem `(*cIter).second` .

### <a name="example"></a>Przykład

Zobacz przykład [rozpoczęcia](#begin) korzystania z polecenia `const_iterator` .

## <a name="multimapconst_pointer"></a><a name="const_pointer"></a> multimap:: const_pointer

Typ, który dostarcza wskaźnik do **`const`** elementu w multimap.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może być używany do modyfikacji wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie multimap.

## <a name="multimapconst_reference"></a><a name="const_reference"></a> multimap:: const_reference

Typ, który dostarcza odwołanie do **`const`** elementu przechowywanego w multimap do odczytu i wykonywania **`const`** operacji.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Przykład

```cpp
// multimap_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference can't be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of the first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of the first element in the multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the multimap is 1.
The data value of the first element in the multimap is 10.
```

## <a name="multimapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> multimap:: const_reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **`const`** element w multimap.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartości elementu i służy do iteracji przez multimap w odwrocie.

`const_reverse_iterator`Zdefiniowane przez multimap wskazują na obiekty [value_type](#value_type), które są typu `pair<const Key, Type>` . Wartość klucza jest dostępna za pomocą pierwszej pary elementu członkowskiego, a wartość mapowanego elementu jest dostępna za pomocą drugiego elementu członkowskiego pary.

Aby usunąć odwołanie do `const_reverse_iterator` *crIter* wskazującego element w multimap, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `crIter->first` , który jest odpowiednikiem `(*crIter).first` . Aby uzyskać dostęp do wartości mapowanej podstawy dla elementu, użyj `crIter->second` , który jest odpowiednikiem `(*crIter).first` .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rend](#rend) , aby zapoznać się z przykładem sposobu deklarowania i używania `const_reverse_iterator` .

## <a name="multimapcontains"></a><a name="contains"></a> multimap:: Contains

Sprawdź, czy w. istnieje element z określonym kluczem `multimap` .

```cpp
bool contains(const Key& key) const;
template<class K> bool contains(const K& key) const;
```

### <a name="parameters"></a>Parametry

*K*\
Typ klucza.

*głównych*\
Wartość klucza elementu do wyszukania.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli element znajduje się w kontenerze; `false` w przeciwnym razie.

### <a name="remarks"></a>Uwagi

`contains()` Nowość w języku C++ 20. Aby go użyć, określ [/std: c + + Najnowsza](../build/reference/std-specify-language-standard-version.md) opcja kompilatora.

`template<class K> bool contains(const K& key) const` występuje tylko w przypadku, gdy `key_compare` jest przezroczysty. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie heterogeniczne w kontenerach asocjacyjnych](https://docs.microsoft.com/cpp/standard-library/stl-containers#heterogeneous-lookup-in-associative-containers-c14) .

### <a name="example"></a>Przykład

```cpp
// Requires /std:c++latest
#include <map>
#include <string>
#include <iostream>
#include <functional>

int main()
{
    std::multimap<int, bool> m = {{0, false}, {1, true}};

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << m.contains(1) << '\n';
    std::cout << m.contains(2) << '\n';

    // call template function
    std::multimap<std::string, int, std::less<>> m2 = {{"ten", 10}, {"twenty", 20}, {"thirty", 30}};
    std::cout << m2.contains("ten");
    
    return 0;
}
```

```Output
true
false
true
```

## <a name="multimapcount"></a><a name="count"></a> multimap:: Count

Zwraca liczbę elementów w multimap, których klucze pasują do klucza określonego przez parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Klucz elementów do dopasowania z multimap.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, których klucze sortowania pasują do klucza parametru; 0, jeśli multimap nie zawiera elementu z pasującym kluczem.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę elementów w zakresie

\[ lower_bound (*klucz*), upper_bound (*klucz*))

ma *klucz*wartości klucza.

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie funkcji składowej multimap:: Count.

```cpp
// multimap_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
    using namespace std;
    multimap<int, int> m1;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Elements don't need to have unique keys in multimap,
    // so duplicates are allowed and counted
    i = m1.count(1);
    cout << "The number of elements in m1 with a sort key of 1 is: "
         << i << "." << endl;

    i = m1.count(2);
    cout << "The number of elements in m1 with a sort key of 2 is: "
         << i << "." << endl;

    i = m1.count(3);
    cout << "The number of elements in m1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in m1 with a sort key of 1 is: 2.
The number of elements in m1 with a sort key of 2 is: 2.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="multimapcrbegin"></a><a name="crbegin"></a> multimap:: crbegin —

Zwraca iterator const odnoszący się do pierwszego elementu w odwróconej multimap.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stałe odwrotne Iteratory, odnoszące się do pierwszego elementu w odwróconej [multimap](../standard-library/multimap-class.md) lub adresowania ostatniego elementu w odwrót `multimap` .

### <a name="remarks"></a>Uwagi

`crbegin` jest używany z odwróconą opcją `multimap` [BEGIN](#begin) AS jest używana z `multimap` .

`crbegin` `multimap` Nie można zmodyfikować obiektu z wartością zwracaną.

`crbegin` może służyć do iteracji w `multimap` tył.

### <a name="example"></a>Przykład

```cpp
// multimap_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
```

## <a name="multimapcrend"></a><a name="crend"></a> multimap:: crend

Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej multimap.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Niepowodzenie odwrotnego iteratora dwukierunkowego, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej [multimap](../standard-library/multimap-class.md) (lokalizacja, która poprzedza pierwszy element w odwrót `multimap` ).

### <a name="remarks"></a>Uwagi

`crend` jest używany z odwróconą opcją `multimap` [multimap:: end](#end) , która jest używana z `multimap` .

`crend` `multimap` Nie można zmodyfikować obiektu z wartością zwracaną.

`crend` można go użyć do przetestowania, czy iterator odwrotny osiągnął koniec jego `multimap` .

Nie można usunąć odwołania do wartości zwracanej przez nie `crend` .

### <a name="example"></a>Przykład

```cpp
// multimap_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
```

## <a name="multimapdifference_type"></a><a name="difference_type"></a> multimap::d ifference_type

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów multimap w zakresie między elementami wskazywanymi przez Iteratory.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type`Jest typem zwracanym podczas odejmowania lub zwiększania przez Iteratory kontenera. `difference_type`Jest zazwyczaj używany do reprezentowania liczby elementów w zakresie [*First*, *Last*) między iteratorami `first` i `last` , zawiera element wskazywany przez `first` i zakres elementów do, ale nie obejmują, elementu wskazywanego przez `last` .

Chociaż `difference_type` jest dostępny dla wszystkich iteratorów, które spełniają wymagania iteratora danych wejściowych, który obejmuje klasę iteratorów dwukierunkowych obsługiwanych przez kontenery odwracalne, takie jak zestaw, odejmowanie między iteratorami jest obsługiwane tylko przez Iteratory dostępu swobodnego, dostarczone przez kontener dostępu swobodnego, taki jak wektor.

### <a name="example"></a>Przykład

```cpp
// multimap_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );

   // The following will insert as multimap keys are not unique
   m1.insert ( Int_Pair ( 2, 30 ) );

   multimap <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a multimap
   multimap <int, int>::difference_type  df_count = 0;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter )
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the multimap m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the multimap m1 is: 4.
```

## <a name="multimapemplace"></a><a name="emplace"></a> multimap:: emplace

Wstawia element skonstruowany w miejscu (nie są wykonywane żadne operacje kopiowania ani przenoszenia).

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Parametry

*argumentów*\
Argumenty przekazywane do konstruowania elementu, który ma zostać wstawiony do multimap.

### <a name="return-value"></a>Wartość zwracana

Iterator do nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie zawiera żadnych odwołań do elementów kontenera, ale może unieważnić wszystkie Iteratory do kontenera.

Jeśli wyjątek jest zgłaszany podczas wstawiania, kontener pozostanie niezmienione i zostanie ponownie zgłoszony wyjątek.

[Value_type](../standard-library/map-class.md#value_type) elementu to para, dzięki czemu wartość elementu będzie przymówionej pary z pierwszym składnikiem równym wartości klucza i drugi składnik równy wartości danych elementu.

### <a name="example"></a>Przykład

```cpp
// multimap_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: " << endl;

    for (const auto& p : m) {
        cout << "(" << p.first <<  "," << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    multimap<string, string> m1;

    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;

    m1.emplace("Bob", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;
}
```

## <a name="multimapemplace_hint"></a><a name="emplace_hint"></a> multimap:: emplace_hint

Wstawia element skonstruowany w miejscu (nie są wykonywane żadne operacje kopiowania ani przenoszenia) z wskazówką dotyczącą położenia.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parametry

*argumentów*\
Argumenty przekazywane do konstruowania elementu, który ma zostać wstawiony do multimap.

*miejscu*\
Miejsce, w którym rozpocznie się wyszukiwanie poprawnego punktu wstawiania. (Jeśli ten punkt bezpośrednio poprzedza miejsce, w *którym*może następować amortyzowany stały czas zamiast czasu logarytmu).

### <a name="return-value"></a>Wartość zwracana

Iterator do nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie zawiera żadnych odwołań do elementów kontenera, ale może unieważnić wszystkie Iteratory do kontenera.

Podczas umieszczanie, jeśli wystąpi wyjątek, stan kontenera nie jest modyfikowany.

[Value_type](../standard-library/map-class.md#value_type) elementu to para, dzięki czemu wartość elementu będzie przymówionej pary z pierwszym składnikiem równym wartości klucza i drugi składnik równy wartości danych elementu.

Aby uzyskać przykład kodu, zobacz [map:: emplace_hint](../standard-library/map-class.md#emplace_hint).

## <a name="multimapempty"></a><a name="empty"></a> multimap:: Empty

Testuje, czy element multimap jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli multimap jest pusty; **`false`** jeśli multimap nie jest pusty.

### <a name="example"></a>Przykład

```cpp
// multimap_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The multimap m1 is empty." << endl;
   else
      cout << "The multimap m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The multimap m2 is empty." << endl;
   else
      cout << "The multimap m2 is not empty." << endl;
}
```

```Output
The multimap m1 is not empty.
The multimap m2 is empty.
```

## <a name="multimapend"></a><a name="end"></a> multimap:: end

Zwraca iterator poza końcem.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator Past. Jeśli multimap jest pusty, a następnie `multimap::end() == multimap::begin()` .

### <a name="remarks"></a>Uwagi

**koniec** służy do sprawdzania, czy iterator przeszedł koniec jego multimap.

Nie należy wywoływać wartości zwracanej przez **koniec** .

Aby uzyskać przykład kodu, zobacz [multimap:: find](#find).

## <a name="multimapequal_range"></a><a name="equal_range"></a> multimap:: equal_range

Wyszukuje zakres elementów, gdzie klucz elementu pasuje do określonej wartości.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*głównych*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego multimap.

### <a name="return-value"></a>Wartość zwracana

Para iteratorów, takich jak pierwszy jest [lower_bound](#lower_bound) klucza, a drugi to [upper_bound](#upper_bound) klucza.

Aby uzyskać dostęp do pierwszego iteratora pary `pr` zwracanej przez funkcję członkowską, użyj `pr` . **najpierw** i aby usunąć odwołanie do dolnego powiązanego iteratora, użyj \* ( `pr` . **pierwszy**). Aby uzyskać dostęp do drugiego iteratora pary `pr` zwracanej przez funkcję członkowską, użyj `pr` . **drugi** i aby usunąć odwołanie do górnego powiązanego iteratora, użyj \* ( `pr` . **sekundę**).

### <a name="example"></a>Przykład

```cpp
// multimap_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef multimap <int, int, less<int> > IntMMap;
   IntMMap m1;
   multimap <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair "
        << "returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of multimap m1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the multimap m1 is: 20.
The upper bound of the element with a key of 2 in the multimap m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The multimap m1 doesn't have an element with a key less than 4.
```

## <a name="multimaperase"></a><a name="erase"></a> multimap:: Erase

Usuwa element lub zakres elementów w multimap z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.

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
Klucz elementów do usunięcia.

### <a name="return-value"></a>Wartość zwracana

W przypadku pierwszych dwóch funkcji składowych iterator dwukierunkowy, który wyznacza pierwszy element, który jest poza wszystkimi elementami usuniętymi lub element, który jest końcem mapy, jeśli taki element nie istnieje.

Dla trzeciej funkcji składowej zwraca liczbę elementów, które zostały usunięte z multimap.

### <a name="remarks"></a>Uwagi

Aby uzyskać przykład kodu, zobacz [map:: Erase](../standard-library/map-class.md#erase).

## <a name="multimapfind"></a><a name="find"></a> multimap:: find

Zwraca iterator odwołujący się do pierwszej lokalizacji elementu w multimap, który ma klucz równoważny do określonego klucza.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza do dopasowania przez klucz sortowania elementu z przeszukiwanego multimap.

### <a name="return-value"></a>Wartość zwracana

Iterator, który odwołuje się do lokalizacji elementu z określonym kluczem lub lokalizacji, w której znajduje się ostatni element w multimap ( `multimap::end()` ), jeśli nie znaleziono żadnego dopasowania dla klucza.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator, który odwołuje się do elementu w multimap, którego klucz sortowania jest równoważny z kluczem argumentu w predykacie binarnym, który wywołuje kolejność na podstawie mniejszej niż porównywalności relacji.

Jeśli wartość zwracana `find` jest przypisana do `const_iterator` , obiekt multimap nie może być modyfikowany. Jeśli wartość zwracana `find` jest przypisana do `iterator` , obiekt multimap może być modyfikowany.

### <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4 /MTd
#include <map>
#include <iostream>
#include <vector>
#include <string>
#include <utility>  // make_pair()

using namespace std;

template <typename A, typename B> void print_elem(const pair<A, B>& p) {
    cout << "(" << p.first << ", " << p.second << ") ";
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
    multimap<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting multimap m1 is (key, value):" << endl;
    print_collection(m1);

    vector<pair<int, string>> v;
    v.push_back(make_pair(43, "Tc"));
    v.push_back(make_pair(41, "Nb"));
    v.push_back(make_pair(46, "Pd"));
    v.push_back(make_pair(42, "Mo"));
    v.push_back(make_pair(44, "Ru"));
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate

    cout << "Inserting the following vector data into m1:" << endl;
    print_collection(v);

    m1.insert(v.begin(), v.end());

    cout << "The modified multimap m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}
```

## <a name="multimapget_allocator"></a><a name="get_allocator"></a> multimap:: get_allocator

Zwraca kopię obiektu alokatora używanego do konstruowania multimap.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez multimap.

### <a name="remarks"></a>Uwagi

Przypisania klasy multimap określają sposób, w jaki Klasa zarządza magazynem. Domyślne przydzielenie klas kontenerów standardowej biblioteki języka C++ jest wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym tematem języka C++.

### <a name="example"></a>Przykład

```cpp
// multimap_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int>::allocator_type m1_Alloc;
   multimap <int, int>::allocator_type m2_Alloc;
   multimap <int, double>::allocator_type m3_Alloc;
   multimap <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   multimap <int, int> m1;
   multimap <int, int, allocator<int> > m2;
   multimap <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a multimap m4
   // with the allocator of multimap m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated via the other
   if( m1_Alloc == m4_Alloc )
   {
      cout << "The allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="multimapinsert"></a><a name="insert"></a> multimap:: INSERT

Wstawia element lub zakres elementów do multimap.

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
Wartość elementu, który ma zostać wstawiony do multimap.

*Miejscu*\
Miejsce, w którym rozpocznie się wyszukiwanie poprawnego punktu wstawiania. (Jeśli ten punkt bezpośrednio poprzedza miejsce, w *którym*może następować amortyzowany stały czas zamiast czasu logarytmu).

*ValTy*\
Parametr szablonu, który określa typ argumentu, który może być używany przez mapę do konstruowania elementu [value_type](../standard-library/map-class.md#value_type)i idealny do przesyłania dalej *jako argument* .

*Pierwszego*\
Pozycja pierwszego elementu, który ma zostać skopiowany.

*Ostatniego*\
Pozycja tuż poza ostatnim elementem, który ma zostać skopiowany.

*InputIterator*\
Argument funkcji szablonu, który spełnia wymagania [iteratora danych wejściowych](../standard-library/input-iterator-tag-struct.md) , który wskazuje elementy typu, które mogą być używane do konstruowania obiektów [value_type](../standard-library/map-class.md#value_type) .

*IList*\
[Initializer_list](../standard-library/initializer-list.md) , z którego mają zostać skopiowane elementy.

### <a name="return-value"></a>Wartość zwracana

Funkcje składowe pojedynczego elementu, (1) i (2) zwracają iterator do pozycji, w której nowy element został wstawiony do multimap.

Funkcje członkowskie jednoelementowe z wskazówką, (3) i (4) zwracają iterator, który wskazuje na pozycję, gdzie nowy element został wstawiony do multimap.

### <a name="remarks"></a>Uwagi

Ta funkcja nie sprawdza wskaźników ani odwołań, ale może unieważnić wszystkie Iteratory do kontenera.

Podczas wstawiania tylko jednego elementu, jeśli wystąpi wyjątek, stan kontenera nie jest modyfikowany. Podczas wstawiania wielu elementów, jeśli wyjątek jest zgłaszany, kontener pozostaje w nieokreślonym, ale prawidłowym stanie.

[Value_type](../standard-library/map-class.md#value_type) kontenera jest elementem TypeDef, który należy do kontenera, a dla mapy, `multimap<K, V>::value_type` to `pair<const K, V>` . Wartość elementu to uporządkowana para, w której pierwszy składnik jest równy wartości klucza, a drugi składnik jest równy wartości danych elementu.

Funkcja elementu członkowskiego zakresu (5) wstawia sekwencję wartości elementów do multimap, która odnosi się do każdego elementu, który jest adresowany do zakresu, w `[First, Last)` związku z czym *ostatni* nie zostanie wstawiony. Funkcja elementu członkowskiego kontenera `end()` odwołuje się do pozycji tuż po ostatnim elemencie w kontenerze — na przykład, instrukcja `m.insert(v.begin(), v.end());` wstawia wszystkie elementy `v` do `m` .

Funkcja członkowska listy inicjatorów (6) używa [initializer_list](../standard-library/initializer-list.md) do kopiowania elementów do mapy.

Do wstawienia elementu skonstruowanego w miejscu — to znaczy, że nie są wykonywane żadne operacje kopiowania ani przenoszenia — zobacz [multimap:: emplace](#emplace) i [multimap:: emplace_hint](#emplace_hint).

### <a name="example"></a>Przykład

```cpp
// multimap_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>
#include <vector>
#include <utility>  // make_pair()

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    multimap<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    m1.insert(make_pair(1, 111));

    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    multimap<int, int> m2;
    vector<pair<int, int>> v;
    v.push_back(make_pair(43, 294));
    v.push_back(make_pair(41, 262));
    v.push_back(make_pair(45, 330));
    v.push_back(make_pair(42, 277));
    v.push_back(make_pair(44, 311));

    cout << "Inserting the following vector data into m2:" << endl;
    print(v);

    m2.insert(v.begin(), v.end());

    cout << "The modified key and mapped values of m2 are:" << endl;
    print(m2);
    cout << endl;

    // The templatized versions move-constructing elements
    multimap<int, string>  m3;
    pair<int, string> ip1(475, "blue"), ip2(510, "green");

    // single element
    m3.insert(move(ip1));
    cout << "After the first move insertion, m3 contains:" << endl;
    print(m3);

    // single element with hint
    m3.insert(m3.end(), move(ip2));
    cout << "After the second move insertion, m3 contains:" << endl;
    print(m3);
    cout << endl;

    multimap<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}
```

## <a name="multimapiterator"></a><a name="iterator"></a> multimap:: iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w multimap.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

`iterator`Zdefiniowane przez multimap wskazują na obiekty [value_type](#value_type), które są typu `pair<const Key, Type>` . Wartość klucza jest dostępna za pomocą pierwszej pary elementu członkowskiego, a wartość mapowanego elementu jest dostępna za pomocą drugiego elementu członkowskiego pary.

Aby usunąć odwołanie do `iterator` *ITER* wskazujące element w multimap, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `Iter->first` , który jest odpowiednikiem `(*Iter).first` . Aby uzyskać dostęp do wartości mapowanej podstawy dla elementu, użyj `Iter->second` , który jest odpowiednikiem `(*Iter).second` .

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zapoznaj [się](#begin) z przykładem dotyczącym sposobu deklarowania i używania `iterator` .

## <a name="multimapkey_comp"></a><a name="key_comp"></a> multimap:: key_comp

Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w multimap.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt Function, którego multimap używa do porządkowania jego elementów.

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członkowską

`bool operator( const Key& x, const Key& y);`

Zwraca wartość true, jeśli *x* ściśle poprzedza *y* w kolejności sortowania.

### <a name="example"></a>Przykład

```cpp
// multimap_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of m1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of m1."
           << endl;
   }

   multimap <int, int, greater<int> > m2;
   multimap <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of m2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of m2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.
```

## <a name="multimapkey_compare"></a><a name="key_compare"></a> multimap:: key_compare

Typ, który dostarcza obiekt funkcji, który może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare` jest synonimem dla parametru szablonu `Traits` .

Aby uzyskać więcej informacji na temat `Traits` , zobacz temat [Klasa multimap](../standard-library/multimap-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [key_comp](#key_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_compare` .

## <a name="multimapkey_type"></a><a name="key_type"></a> multimap:: key_type

Typ, który opisuje obiekt klucza sortowania, który stanowi każdy element multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type` jest synonimem dla parametru szablonu `Key` .

Aby uzyskać więcej informacji na temat `Key` , zobacz sekcję Uwagi w temacie [Klasa multimap](../standard-library/multimap-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [value_type](#value_type) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_type` .

## <a name="multimaplower_bound"></a><a name="lower_bound"></a> multimap:: lower_bound

Zwraca iterator do pierwszego elementu w multimap, z kluczem, który jest równy lub większy niż określony klucz.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego multimap.

### <a name="return-value"></a>Wartość zwracana

Iterator lub `const_iterator` który odnosi się do lokalizacji elementu w multimap, który ma klucz, który jest równy lub większy od klucza argumentu lub który odnosi się do lokalizacji po ostatnim elemencie w multimap, jeśli nie znaleziono żadnego dopasowania dla klucza.

Jeśli wartość zwracana `lower_bound` jest przypisana do `const_iterator` , obiekt multimap nie może być modyfikowany. Jeśli wartość zwracana `lower_bound` jest przypisana do **iteratora**, obiekt multimap może być modyfikowany.

### <a name="example"></a>Przykład

```cpp
// multimap_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The element of multimap m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.lower_bound( 3 );
   cout << "The first element of multimap m1 with a key of 3 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
              << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
                << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1.lower_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key matching\n"
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( m1_RcIter == --m1.end( ) )
      cout << "This is the last element of multimap m1."
           << endl;
   else
      cout << "This is not the last element of multimap m1."
           << endl;
}
```

```Output
The element of multimap m1 with a key of 2 is: 20.
The first element of multimap m1 with a key of 3 is: 20.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key matching
that of the last element is: 20.
This is not the last element of multimap m1.
```

## <a name="multimapmapped_type"></a><a name="mapped_type"></a> multimap:: mapped_type

Typ, który reprezentuje typ danych przechowywany w multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Uwagi

`mapped_type` jest synonimem dla parametru szablonu `Type` .

Aby uzyskać więcej informacji na temat `Type` , zobacz temat [Klasa multimap](../standard-library/multimap-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [value_type](#value_type) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_type` .

## <a name="multimapmax_size"></a><a name="max_size"></a> multimap:: max_size

Zwraca maksymalną długość multimap.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna możliwa długość multimap.

### <a name="example"></a>Przykład

```cpp
// multimap_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the multimap is " << i << "." << endl;
}
```

## <a name="multimapmultimap"></a><a name="multimap"></a> multimap:: multimap

Konstruuje multimap, który jest pusty lub jest kopią całości lub części innej multimap.

```cpp
multimap();

explicit multimap(
    const Traits& Comp);

multimap(
    const Traits& Comp,
    const Allocator& Al);

map(
    const multimap& Right);

multimap(
    multimap&& Right);

multimap(
    initializer_list<value_type> IList);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

*Wsp*\
Klasa alokatora magazynu, która ma być używana dla tego obiektu multimap, który domyślnie jest alokatorem.

*Przepisów*\
Funkcja porównywania typu `constTraits` służąca do porządkowania elementów w mapie, które są domyślnie `Traits` .

*Kliknij*\
Mapa, której skonstruowany zestaw ma być kopią.

*Pierwszego*\
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*Ostatniego*\
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

*IList*\
Lista initializer_list, z której mają być skopiowane elementy.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują typ obiektu alokatora, który zarządza magazynem pamięci dla multimap i który może być później zwracany przez wywołanie [get_allocator](#get_allocator). Parametr alokatora jest często pomijany w deklaracjach klas i makrach przetwarzania wstępnego służących do podstawiania alternatywnych metod przydzielania.

Wszystkie konstruktory inicjują multimap.

Wszystkie konstruktory przechowują obiekt funkcji typu `Traits` , który jest używany do ustanowienia zamówienia między kluczami multimap i, które później mogą być zwracane przez wywołanie [key_comp](#key_comp).

Pierwsze trzy konstruktory określają pustą multimap początkową, drugą określającą typ funkcji porównywania (*COMP*), która ma zostać użyta w celu ustalenia kolejności elementów i trzeciego jawnie określającego typ alokatora (*Al*), który ma być używany. Słowo kluczowe **`explicit`** pomija niektóre rodzaje automatycznej konwersji typów.

Czwarty Konstruktor określa kopię multimap *po prawej stronie*.

Piąty Konstruktor określa kopię multimap, przenosząc *prawo*.

Konstruktory szóste, siódme i ósmy kopiują elementy członkowskie initializer_list.

Następne trzy konstruktory kopiują zakres `[First, Last)` mapy ze wzrostem jawności w określaniu typu funkcji porównania klasy `Traits` i alokatora.

### <a name="example"></a>Przykład

```cpp
// multimap_ctor.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;

    // Create an empty multimap m0 of key type integer
    multimap <int, int> m0;

    // Create an empty multimap m1 with the key comparison
    // function of less than, then insert 4 elements
    multimap <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty multimap m2 with the key comparison
    // function of greater than, then insert 2 elements
    multimap <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a multimap m3 with the
    // allocator of multimap m1
    multimap <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    multimap <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, multimap m4, of multimap m1
    multimap <int, int> m4(m1);

    // Create a multimap m5 by copying the range m1[ first,  last)
    multimap <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    multimap <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a multimap m6 by copying the range m4[ first,  last)
    // and with the allocator of multimap m2
    multimap <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    multimap <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for (auto i : m2)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m3 =";
    for (auto i : m3)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m4 =";
    for (auto i : m4)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m5 =";
    for (auto i : m5)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m6 =";
    for (auto i : m6)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m8 by copying in an initializer_list
    multimap<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m9 with an initializer_list and a comparator
    multimap<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m10 with an initializer_list, a comparator, and an allocator
    multimap<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

}
```

## <a name="multimapoperator"></a><a name="op_eq"></a> multimap:: operator =

Zastępuje elementy elementu multimap kopią innego multimap.

```cpp
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Multimap](../standard-library/multimap-class.md) kopiowany do `multimap` .

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkich istniejących elementów w programie `multimap` , `operator=` kopiuje lub przenosi zawartość *bezpośrednio* do `multimap` .

### <a name="example"></a>Przykład

```cpp
// multimap_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   multimap<int, int> v1, v2, v3;
   multimap<int, int>::iterator iter;

   v1.insert(pair<int, int>(1, 10));

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;
   }
```

## <a name="multimappointer"></a><a name="pointer"></a> multimap::p ointer

Typ, który dostarcza wskaźnik do elementu w multimap.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie multimap.

## <a name="multimaprbegin"></a><a name="rbegin"></a> multimap:: rbegin

Zwraca iterator odnoszący się do pierwszego elementu w odwróconej multimap.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconej multimap lub adresowania ostatniego elementu w nieodwróconym multimap.

### <a name="remarks"></a>Uwagi

`rbegin` jest używany z odwróconym multimapm, tak jak [BEGIN](#begin) jest używany z multimap.

Jeśli wartość zwracana `rbegin` jest przypisana do `const_reverse_iterator` , obiekt multimap nie może być modyfikowany. Jeśli wartość zwracana elementu `rbegin` jest przypisana do `reverse_iterator` , można zmodyfikować obiekt multimap.

`rbegin` może służyć do iteracji w multimap wstecz.

### <a name="example"></a>Przykład

```cpp
// multimap_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the first element in the reversed multimap is 2.
```

## <a name="multimapreference"></a><a name="reference"></a> multimap:: Reference

Typ, który zawiera odwołanie do elementu przechowywanego w multimap.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Przykład

```cpp
// multimap_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference can't be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the multimap is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The modified data value of first element is 15.
```

## <a name="multimaprend"></a><a name="rend"></a> multimap:: rend

Zwraca iterator, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej multimap.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej multimap (lokalizacja, która poprzedza pierwszy element w odwrocie multimap).

### <a name="remarks"></a>Uwagi

`rend` jest używany z odwróconym multimapm, tak samo jak [koniec](../standard-library/map-class.md#end) jest używany z multimap.

Jeśli wartość zwracana `rend` jest przypisana do `const_reverse_iterator` , obiekt multimap nie może być modyfikowany. Jeśli wartość zwracana elementu `rend` jest przypisana do `reverse_iterator` , można zmodyfikować obiekt multimap.

`rend` może służyć do sprawdzenia, czy iterator odwrotny osiągnął koniec multimap.

Nie można usunąć odwołania do wartości zwracanej przez nie `rend` .

### <a name="example"></a>Przykład

```cpp
// multimap_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the last element in the reversed multimap is 2.
```

## <a name="multimapreverse_iterator"></a><a name="reverse_iterator"></a> multimap:: reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej multimap.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iteracji przez multimap w odwrocie.

`reverse_iterator`Zdefiniowane przez multimap wskazują na obiekty [value_type](#value_type), które są typu `pair<const Key, Type>` . Wartość klucza jest dostępna za pomocą pierwszej pary elementu członkowskiego, a wartość mapowanego elementu jest dostępna za pomocą drugiego elementu członkowskiego pary.

Aby usunąć odwołanie do `reverse_iterator` *rIter* elementu, który wskazuje element w multimap, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `rIter->first` , który jest odpowiednikiem `(*rIter).first` . Aby uzyskać dostęp do wartości mapowanej podstawy dla elementu, użyj `rIter->second` , który jest odpowiednikiem `(*rIter).second` .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rbegin](#rbegin) , aby zapoznać się z przykładem sposobu deklarowania i używania `reverse_iterator` .

## <a name="multimapsize"></a><a name="size"></a> multimap:: size

Zwraca liczbę elementów w multimap.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość multimap.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia funkcji składowej multimap:: size.

```cpp
// multimap_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    multimap<int, int> m1, m2;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The multimap length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The multimap length is now " << i << "." << endl;
}
```

```Output
The multimap length is 1.
The multimap length is now 2.
```

## <a name="multimapsize_type"></a><a name="size_type"></a> multimap:: size_type

Typ liczby całkowitej bez znaku, który zlicza liczbę elementów w multimap.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dotyczącym [rozmiaru](#size) przykładu sposobu deklarowania i używania `size_type`

## <a name="multimapswap"></a><a name="swap"></a> multimap:: swap

Wymienia elementy dwóch map.

```cpp
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Multimap udostępniający elementy, które mają zostać zamienione, lub multimap, których elementy mają być wymieniane z tymi multimap `left` .

### <a name="remarks"></a>Uwagi

Funkcja członkowska unieważnia odwołania, wskaźniki lub Iteratory, które wyznaczają elementy w dwóch mapowaniach, których elementy są wymieniane.

### <a name="example"></a>Przykład

```cpp
// multimap_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   multimap <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   m1.swap( m2 );

   cout << "After swapping with m2, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original multimap m1 is: 10 20 30.
After swapping with m2, multimap m1 is: 100 200.
After swapping with m3, multimap m1 is: 300.
```

## <a name="multimapupper_bound"></a><a name="upper_bound"></a> multimap:: upper_bound

Zwraca iterator do pierwszego elementu w multimap, z kluczem, który jest większy niż określony klucz.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego multimap.

### <a name="return-value"></a>Wartość zwracana

Iterator lub `const_iterator` który odnosi się do lokalizacji elementu w multimap, który jest większy niż klucz argumentu lub który odnosi się do lokalizacji po ostatnim elemencie w multimap, jeśli nie znaleziono żadnego dopasowania dla klucza.

Jeśli wartość zwracana jest przypisana do `const_iterator` , obiekt multimap nie może być modyfikowany. Jeśli wartość zwracana jest przypisana do `iterator` , obiekt multimap może być modyfikowany.

### <a name="example"></a>Przykład

```cpp
// multimap_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m1.insert ( Int_Pair ( 3, 40 ) );

   m1_RcIter = m1.upper_bound( 1 );
   cout << "The 1st element of multimap m1 with "
        << "a key greater than 1 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of multimap m1 with a key "
        << " greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1.upper_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of multimap m1 with a key greater than 1 is: 20.
The first element of multimap m1 with a key  greater than 2 is: 30.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="multimapvalue_comp"></a><a name="value_comp"></a> multimap:: value_comp

Funkcja członkowska zwraca obiekt funkcji, który określa kolejność elementów w multimap, porównując ich wartości klucza.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji porównania, którego multimap używa do porządkowania jego elementów.

### <a name="remarks"></a>Uwagi

Dla multimap *m*, jeśli dwa elementy *E1*(*K1*, *D1*) i *E2*(*K2*, *D2*) są obiektami typu `value_type` , gdzie *K1* i *K2* są ich klucze typu `key_type` i *D1* i *D2* są ich danymi typu, a następnie są `mapped_type` `m.value_comp(e1, e2)` równoważne `m.key_comp(k1, k2)` .

### <a name="example"></a>Przykład

```cpp
// multimap_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   multimap<int,int>::iterator Iter1, Iter2;

   Iter1= m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= m1.insert ( multimap <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *Iter1, *Iter2 ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does "
           << "not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1( *Iter2, *Iter1 ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does "
           << "not precede the element ( 1,10 )."
           << endl;
   }
}
```

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="multimapvalue_type"></a><a name="value_type"></a> multimap:: value_type

Typ, który reprezentuje typ obiektu przechowywanego jako element na mapie.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>Przykład

```cpp
// multimap_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   multimap <int, int> m1;
   multimap <int, int> :: key_type key1;
   multimap <int, int> :: mapped_type mapped1;
   multimap <int, int> :: value_type value1;
   multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   m1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the multimap is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>Zobacz też

[Opakowania](./stl-containers.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
