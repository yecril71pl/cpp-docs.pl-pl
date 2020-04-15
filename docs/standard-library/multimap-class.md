---
title: multimap — Klasa
ms.date: 10/18/2018
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
ms.openlocfilehash: 2f6ae50a825d6eff2eb64c84b209fa81c4b7949f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363853"
---
# <a name="multimap-class"></a>multimap — Klasa

Klasa multimap biblioteki standardowej języka C++ jest używana do przechowywania i pobierania danych z kolekcji, w której każdy element jest parą, która ma zarówno wartość danych, jak i klucz sortowania. Wartość klucza nie musi unikatowa i jest używana do automatycznego porządkowania danych. Wartość elementu w mapie wielokrotnej, ale nie wartość jego skojarzonego klucza, może być zmieniona bezpośrednio. Zamiast tego, wartości kluczy skojarzone ze starymi elementami muszą zostać usunięte, a nowe wartości klucza skojarzone z nowymi wstawionymi elementami.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Type,
    class Traits=less <Key>,
    class Allocator=allocator <pair  <const Key, Type>>>
class multimap;
```

### <a name="parameters"></a>Parametry

*Klucz*\
Typ danych klucza, który ma być przechowywany w mapie wielokrotnej.

*Typu*\
Typ danych elementu, który ma być przechowywany w mapie wielokrotnej.

*Cechy*\
Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w mapie wielokrotnej. Predykat `less<Key>` binarny jest wartością domyślną.

W języku C++14 można włączyć heterogeniczne wyszukiwanie, określając `std::less<>` lub `std::greater<>` predykatu, który nie ma parametrów typu. Aby uzyskać więcej informacji, zobacz [Heterogeniczne wyszukiwanie w kontenerach zespolonych](../standard-library/stl-containers.md#heterogeneous-lookup-in-associative-containers-c14)

*Programu przydzielania*\
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji mapy i dezalokacji pamięci. Ten argument jest opcjonalny, `allocator<pair <const Key, Type> >`a wartością domyślną jest .

## <a name="remarks"></a>Uwagi

Klasa multimap biblioteki standardowej języka C++ jest

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowe iteratory do dostępu do jego elementów.

- Posortowany, ponieważ jego elementy są uporządkowane według wartości kluczy w kontenerze zgodnie z określoną funkcją porównywania.

- Wielokrotna, ponieważ jej elementy nie muszą mieć unikatowych kluczy, więc jedna wartość klucza może mieć wiele wartości elementów danych z nią skojarzonych.

- Kontenerem skojarzonych par, ponieważ jej wartości danych elementu różnią się od wartości klucza.

- Szablon klasy, ponieważ funkcje, które zapewnia, jest ogólny i tak niezależne od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Iterator dostarczony przez klasę mapy jest dwukierunkowym iteratorem, ale funkcje członkowskie klasy [wstawiają](#insert) i [multimapują](#multimap) wersje, które przyjmują jako parametry szablonu słabszy iterator wejściowy, którego wymagania dotyczące funkcjonalności są bardziej minimalne niż wymagania gwarantowane przez klasę dwukierunkowych iteratorów. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcji, ale wystarczy, aby móc mówić sensownie o zakresie `[First, Last)` iteratorów w kontekście funkcji elementów członkowskich klasy.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Kontenery asocjacyjne są zoptymalizowane dla operacji wyszukiwania, wstawiania oraz usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, są skuteczne, wykonując je w czasie, który jest średnio proporcjonalny do logarytmu liczby elementów w kontenerze. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Mapa wielokrotna powinna być kontenerem asocjacyjnym z wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Modelem dla tego typu struktury jest uporządkowana lista słów kluczowych ze skojarzonymi wartościami ciągów, dostarczająca np. definicje, w których słowa nie były zawsze zdefiniowane unikalnie. Jeśli zamiast tego słowa kluczowe zostały unikalnie zdefiniowane, tak że klucze są unikalne, wybranym kontenerem będzie map. Jeśli z drugiej strony, przechowywana była tylko lista wyrazów, poprawnym kontenerem będzie set. Jeżeli zezwolono na wiele wystąpień wyrazów, odpowiednią strukturą kontenera będzie multiset.

Multimap porządkuuje sekwencję, która kontroluje, wywołując przechowywany obiekt funkcji typu [key_compare](#key_compare). Ten przechowywany obiekt jest funkcją porównania, do którą można uzyskać dostęp, wywołując funkcję elementu członkowskiego [key_comp](#key_comp). Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat `f(x,y)` binarny jest obiektem funkcji, który ma dwa obiekty `x` argumentów i `y` zwraca wartość true lub false. Kolejność nałożona na zestaw jest ścisłym słabym porządkiem, jeśli predykat binarny jest niereflexive, antysymetryczny i `x` przechodnie i jeśli równoważność jest przechodnie, gdzie dwa obiekty i `y` są zdefiniowane jako równoważne, gdy oba `f(x,y)` i `f(y,x)` są fałszywe. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

W języku C++14 można włączyć heterogeniczne wyszukiwanie, określając `std::less<>` lub `std::greater<>` predykatu, który nie ma parametrów typu. Aby uzyskać więcej informacji, zobacz [Heterogeniczne wyszukiwanie w kontenerach zespolonych](../standard-library/stl-containers.md#sequence_containers)

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Multimap](#multimap)|Konstruuje, `multimap` który jest pusty lub który jest kopią całości lub części innego `multimap`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który `allocator` reprezentuje klasę `multimap` dla obiektu.|
|[const_iterator](#const_iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytać `multimap` **const** element w .|
|[const_pointer](#const_pointer)|Typ, który zapewnia wskaźnik do **const** elementu w `multimap`.|
|[const_reference](#const_reference)|Typ, który zapewnia odwołanie do **const** `multimap` element przechowywane w do odczytu i wykonywania operacji **const.**|
|[Const_reverse_iterator](#const_reverse_iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytać `multimap`dowolny element **const** w .|
|[difference_type](#difference_type)|Typ liczby całkowitej podpisana, który może służyć do `multimap` reprezentowania liczby elementów w zakresie między elementami wskazanymi przez iteratory.|
|[Sterująca](#iterator)|Typ, który zapewnia różnicę między dwoma iteratorami, `multimap`które odwołują się do elementów w ramach tego samego .|
|[key_compare](#key_compare)|Typ, który udostępnia obiekt funkcji, który może porównać dwa klucze `multimap`sortowania, aby określić względną kolejność dwóch elementów w programie .|
|[Key_type](#key_type)|Typ opisujący obiekt klucza sortowania, który `multimap`stanowi każdy element .|
|[mapped_type](#mapped_type)|Typ reprezentujący typ danych przechowywany `multimap`w pliku .|
|[pointer](#pointer)|Typ, który zapewnia wskaźnik do **const** elementu w `multimap`.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu `multimap`przechowywanego w .|
|[Reverse_iterator](#reverse_iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować element w odwróconym `multimap`.|
|[size_type](#size_type)|Niepodpisany typ liczby całkowitej, który zapewnia wskaźnik `multimap`do **const** elementu w .|
|[value_type](#value_type)|Typ, który udostępnia obiekt funkcji, który może porównać dwa elementy `multimap`jako klucze sortowania, aby określić ich względną kolejność w programie .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Rozpocząć](#begin)|Zwraca iteratora adresującego pierwszy `multimap`element w pliku .|
|[cbegin ( cbegin )](#cbegin)|Zwraca iterator const adresowania pierwszego `multimap`elementu w .|
|[cend](#cend)|Zwraca iterator const, który odnosi się do `multimap`lokalizacji, która po pomyślnym ostatnim elemencie w pliku .|
|[Wyczyść](#clear)|Usuwa wszystkie elementy pliku `multimap`.|
|[Liczba](#count)|Zwraca liczbę elementów, `multimap` w których klucz pasuje do klucza określonego przez parametr.|
|[Crbegin](#crbegin)|Zwraca iterator const adresowania pierwszego elementu `multimap`w odwróconym .|
|[Crend](#crend)|Zwraca iterator const, który odnosi się do lokalizacji, która po pomyślnym ostatnim elemencie w odwróconym `multimap`.|
|[miejsce](#emplace)|Wstawia element skonstruowany w `multimap`miejscu do .|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w `multimap`miejscu do , z wskazówką o umieszczeniu|
|[Pusty](#empty)|Sprawdza, `multimap` czy a jest pusty.|
|[Końcu](#end)|Zwraca iterator, który odnosi się do lokalizacji, która po pomyślnym ostatnim elemencie w pliku `multimap`.|
|[equal_range](#equal_range)|Wyszukuje zakres elementów, gdzie klucz elementu pasuje do określonej wartości.|
|[Wymazać](#erase)|Usuwa element lub zakres elementów `multimap` w określonym położeniu lub usuwa elementy, które pasują do określonego klucza.|
|[find](#find)|Zwraca iterator adresowania pierwszej lokalizacji elementu `multimap` w, który ma klucz równoważny określony klucz.|
|[Get_allocator](#get_allocator)|Zwraca kopię `allocator` obiektu używanego do `multimap`konstruowania pliku .|
|[Wstawić](#insert)|Wstawia element lub zakres elementów do pliku `multimap`.|
|[Key_comp](#key_comp)|Pobiera kopię obiektu porównania używanego do zamawiania kluczy w pliku `multimap`.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu `multimap` w kluczu, który jest równy lub większy niż określony klucz.|
|[Max_size](#max_size)|Zwraca maksymalną długość `multimap`pliku .|
|[rbegin (rbegin)](#rbegin)|Zwraca iteratora adresującego pierwszy element `multimap`w odwróconym .|
|[Rend](#rend)|Zwraca iterator, który odnosi się do lokalizacji, `multimap`która zastępuje ostatni element w odwróconym .|
|[Rozmiar](#size)|Zwraca liczbę elementów `multimap`w pliku .|
|[Wymiany](#swap)|Wymienia elementy dwóch `multimap`s.|
|[upper_bound](#upper_bound)|Zwraca iterator do pierwszego elementu `multimap` w tym z kluczem, który jest większy niż określony klucz.|
|[value_comp](#value_comp)|Funkcja elementu członkowskiego zwraca obiekt funkcji, który określa `multimap` kolejność elementów w a, porównując ich wartości klucza.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Zastępuje elementy a `multimap` kopią innego `multimap`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> mapy

**Przestrzeń nazw:** std

Pary **(klucz,** **wartość)** są przechowywane w multimapie `pair`jako obiekty typu. Klasa pary wymaga \<narzędzia nagłówka>, które jest automatycznie \<uwzględniane przez> mapy.

## <a name="multimapallocator_type"></a><a name="allocator_type"></a>multimap::allocator_type

Typ reprezentujący klasę alokatora dla obiektu wielomapowego.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [get_allocator](#get_allocator) na przykład za `allocator_type`pomocą .

## <a name="multimapbegin"></a><a name="begin"></a>multimap::begin

Zwraca iterator adresowania pierwszy element w multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator adresowania pierwszy element w multimap lub lokalizacji po zastąpieniu pustej multimapy.

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

## <a name="multimapcbegin"></a><a name="cbegin"></a>multimap::cbegin

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

## <a name="multimapcend"></a><a name="cend"></a>multimap::cend

Zwraca **iterator const,** który odnosi się do lokalizacji tuż poza ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

**Dwukierunkowy** iterator dostępu dwukierunkowego, który wskazuje tuż za końcem zakresu.

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

## <a name="multimapclear"></a><a name="clear"></a>multimap::wyczyść

Usuwa wszystkie elementy multimapy.

```cpp
void clear();
```

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie funkcji multimap::clear elementu członkowskiego.

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

## <a name="multimapconst_iterator"></a><a name="const_iterator"></a>multimap::const_iterator

Typ, który zapewnia dwukierunkowy iterator, który może odczytać **const** element w multimap.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

Zdefiniowane `const_iterator` przez multimapy wskazują na obiekty [value_type](#value_type), `pair<const Key, Type>`które są typu . Wartość klucza jest dostępna za pośrednictwem pierwszej pary elementów członkowskich, a wartość zamapowany element jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

Aby wyłuskać `const_iterator` *cIter* wskazując element w multimap, należy użyć **->** operatora.

Aby uzyskać dostęp do wartości klucza `cIter->first`dla elementu, `(*cIter).first`należy użyć , co odpowiada . Aby uzyskać dostęp do wartości zamapowanej `cIter->second`bazy pomiarowej `(*cIter).second`dla elementu, należy użyć , co odpowiada .

### <a name="example"></a>Przykład

Zobacz [przykład, aby rozpocząć](#begin) `const_iterator`przykład przy użyciu .

## <a name="multimapconst_pointer"></a><a name="const_pointer"></a>multimap::const_pointer

Typ, który zapewnia wskaźnik do **const** elementu w multimap.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien służyć do uzyskiwania dostępu do elementów w obiekcie wielomapowym.

## <a name="multimapconst_reference"></a><a name="const_reference"></a>multimap::const_reference

Typ, który zapewnia odwołanie do **const** element przechowywane w multimap do odczytu i wykonywania operacji **const.**

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
   // non-const_reference cannot be used to access the key
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

## <a name="multimapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>multimap::const_reverse_iterator

Typ, który zapewnia dwukierunkowy iterator, który może odczytać dowolny element **const** w multimap.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartość elementu i jest używany do iteracji za pośrednictwem multimap w odwrotnej kolejności.

Zdefiniowane `const_reverse_iterator` przez multimapy wskazują na obiekty [value_type](#value_type), `pair<const Key, Type>`które są typu . Wartość klucza jest dostępna za pośrednictwem pierwszej pary elementów członkowskich, a wartość zamapowany element jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

Aby wyłuskać `const_reverse_iterator` *crIter* wskazując na element w **->** multimap, należy użyć operatora.

Aby uzyskać dostęp do wartości klucza `crIter->first`dla elementu, `(*crIter).first`należy użyć , co odpowiada . Aby uzyskać dostęp do wartości zamapowanej `crIter->second`bazy pomiarowej `(*crIter).first`dla elementu, należy użyć , co odpowiada .

### <a name="example"></a>Przykład

Zobacz przykład [rend](#rend) na przykład jak zadeklarować `const_reverse_iterator`i używać .

## <a name="multimapcount"></a><a name="count"></a>multimap::count

Zwraca liczbę elementów w multimapie, których klucze są zgodne z kluczem określonym przez parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz elementów, które mają być dopasowane z multimapy.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, których klucze sortowania są zgodne z kluczem parametru; 0, jeśli multimapa nie zawiera elementu z pasującym kluczem.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca liczbę elementów w zakresie

\[lower_bound(*klucz*), upper_bound(*klucz*)

które mają klucz wartości *klucza*.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie funkcji elementu członkowskiego multimap::count.

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

    // Elements do not need to have unique keys in multimap,
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

## <a name="multimapcrbegin"></a><a name="crbegin"></a>multimap::crbegin

Zwraca iterator konstacyjny adresowania pierwszy element w odwróconej multimapy.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Const odwrotnej dwukierunkowej iteratora adresowania pierwszego elementu w odwróconej [multimapy](../standard-library/multimap-class.md) lub adresowania, co było ostatnim elementem w nieodwrotzony `multimap`.

### <a name="remarks"></a>Uwagi

`crbegin`jest używany z `multimap` odwróconym tak jak `multimap` [begin](#begin) jest używany z .

Z wartością `crbegin`zwracaną `multimap` obiektu nie można modyfikować obiektu.

`crbegin`może być używany do iteracji do `multimap` tyłu.

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

## <a name="multimapcrend"></a><a name="crend"></a>multimap::crend

Zwraca iterator const, który odnosi się do lokalizacji po ostatniej pozycji elementu w odwróconej multimapy.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Const odwrotnej dwukierunkowej iteratora, który odnosi się do lokalizacji po ostatniej pozycji elementu w odwróconej [multimapy](../standard-library/multimap-class.md) (lokalizacja, która poprzedziła pierwszy element w nieodwrotnych `multimap`).

### <a name="remarks"></a>Uwagi

`crend`jest używany z `multimap` odwróconym tak jak [multimap::end](#end) jest używany z . `multimap`

Z wartością `crend`zwracaną `multimap` obiektu nie można modyfikować obiektu.

`crend`można użyć do sprawdzenia, czy iterator odwrotny `multimap`osiągnął koniec jego .

Wartość zwrócona `crend` przez nie powinny być wyłuskiwane.

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

## <a name="multimapdifference_type"></a><a name="difference_type"></a>multimap::dfference_type

Typ liczby całkowitej podpisana, który może służyć do reprezentowania liczby elementów multimapy w zakresie między elementami wskazywane przez iteratory.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Jest `difference_type` to typ zwracany podczas odejmowania lub zwiększania za pośrednictwem iteratorów kontenera. Jest `difference_type` zazwyczaj używany do reprezentowania liczby elementów w zakresie [*pierwszy*, `first` `last` *ostatni*) między iteratorów i , zawiera element wskazany przez `first` `last`i zakres elementów do, ale nie w tym element wskazany przez .

Należy zauważyć, że chociaż `difference_type` jest dostępny dla wszystkich iteratorów, które spełniają wymagania iteratora wejściowego, który obejmuje klasę dwukierunkowych iteratorów obsługiwanych przez odwracalne kontenery, takie jak zestaw, odejmowanie między iteratorami jest obsługiwane tylko przez iteratory dostępu losowego dostarczane przez kontener dostępu losowego, taki jak wektor.

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

## <a name="multimapemplace"></a><a name="emplace"></a>multimap::miejsce

Wstawia element skonstruowany w miejscu (nie są wykonywane żadne operacje kopiowania lub przenoszenia).

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Args*|Argumenty przekazane do konstruowania elementu, który ma zostać wstawiony do multimapy.|

### <a name="return-value"></a>Wartość zwracana

Iterator do nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Żadne odwołania do elementów kontenera są unieważnione przez tę funkcję, ale może unieważnić wszystkie iteratory do kontenera.

Jeśli wyjątek zostanie zgłoszony podczas wstawiania, kontener pozostaje bez ekwiwalom i wyjątek jest rethrown.

[value_type](../standard-library/map-class.md#value_type) elementu jest parą, dzięki czemu wartość elementu będzie uporządkowaną parą z pierwszym składnikiem równym wartości klucza, a drugim składnikiem równym wartości danych elementu.

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

## <a name="multimapemplace_hint"></a><a name="emplace_hint"></a>multimap::emplace_hint

Wstawia element skonstruowany w miejscu (nie są wykonywane operacje kopiowania lub przenoszenia), z wskazówką dotyczące umieszczania.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Args*|Argumenty przekazane do konstruowania elementu, który ma zostać wstawiony do multimapy.|
|*where*|Miejsce, aby rozpocząć wyszukiwanie prawidłowego punktu wstawiania. (Jeśli ten punkt bezpośrednio *poprzedza, gdzie*, wstawienie może wystąpić w zamortyzowanym czasie stałym zamiast czasu logarytmicznego.)|

### <a name="return-value"></a>Wartość zwracana

Iterator do nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Żadne odwołania do elementów kontenera są unieważnione przez tę funkcję, ale może unieważnić wszystkie iteratory do kontenera.

Podczas umieszczenia, jeśli wyjątek, stan kontenera nie jest modyfikowany.

[value_type](../standard-library/map-class.md#value_type) elementu jest parą, dzięki czemu wartość elementu będzie uporządkowaną parą z pierwszym składnikiem równym wartości klucza, a drugim składnikiem równym wartości danych elementu.

Przykładowy kod można znaleźć na [mapie::emplace_hint](../standard-library/map-class.md#emplace_hint).

## <a name="multimapempty"></a><a name="empty"></a>multimap::empty

Sprawdza, czy multimapa jest pusta.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli multimapa jest pusta; **false,** jeśli multimapa jest niepusty.

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

## <a name="multimapend"></a><a name="end"></a>multimap::end

Zwraca iterator poza końcem.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator przeszłości końca. Jeśli multimapa jest `multimap::end() == multimap::begin()`pusta, to .

### <a name="remarks"></a>Uwagi

**jest** używany do testowania, czy iterator przeszedł koniec jego multimap.

Wartość zwracana do **końca** nie powinna być wyłuskana.

Przykładowy kod można znaleźć w [trybie multimap::find](#find).

## <a name="multimapequal_range"></a><a name="equal_range"></a>multimap::equal_range

Wyszukuje zakres elementów, gdzie klucz elementu pasuje do określonej wartości.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz argumentu, który ma być porównywany z kluczem sortowania elementu z przeszukiwanej wielomapy.

### <a name="return-value"></a>Wartość zwracana

Para iteratorów taka, że pierwsza jest [lower_bound](#lower_bound) klucza, a druga [jest upper_bound](#upper_bound) klucza.

Aby uzyskać dostęp do pierwszego `pr` iteratora pary `pr`zwróconej przez funkcję elementu członkowskiego, należy użyć programu . **pierwszy** i wyłuskać dolną iterator, użyj \*( `pr`. **po pierwsze**). Aby uzyskać dostęp do drugiego `pr` iteratora pary `pr`zwróconej przez funkcję elementu członkowskiego, należy użyć programu . **drugi** i wyłuskać górną granicę iteratora, użyj \*( `pr`. **drugi**).

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

## <a name="multimaperase"></a><a name="erase"></a>multimap::wymaż

Usuwa element lub zakres elementów w multimapie z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.

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

*Gdzie*\
Położenie elementu, który ma zostać usunięty.

*Pierwszym*\
Położenie pierwszego elementu do usunięcia.

*Ostatnio*\
Umieść tuż za ostatnim elementem do usunięcia.

*Klucz*\
Klucz elementów, które mają zostać usunięte.

### <a name="return-value"></a>Wartość zwracana

Dla pierwszych dwóch funkcji elementów członkowskich dwukierunkowe iterator, który wyznacza pierwszy element pozostałych poza wszystkie elementy usunięte lub element, który jest koniec mapy, jeśli taki element nie istnieje.

Dla funkcji trzeciego elementu członkowskiego zwraca liczbę elementów, które zostały usunięte z multimapy.

### <a name="remarks"></a>Uwagi

Przykładowy kod można znaleźć na [mapie::erase](../standard-library/map-class.md#erase).

## <a name="multimapfind"></a><a name="find"></a>multimap::znajdź

Zwraca iterator, który odwołuje się do pierwszej lokalizacji elementu w multimapie, który ma klucz równoważny określony klucz.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*\
Wartość klucza, która ma być dopasowana przez klucz sortowania elementu z przeszukiwanej wielomapy.

### <a name="return-value"></a>Wartość zwracana

Iterator, który odwołuje się do lokalizacji elementu z określonym kluczem lub lokalizacji po stronie`multimap::end()`ostatniego elementu w multimapa ( ), jeśli nie znaleziono dopasowania dla klucza.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iteratora, który odwołuje się do elementu w multimap, którego klucz sortowania jest odpowiednikiem klucza argumentu w predykacie binarnym, który indukuje kolejność na podstawie relacji mniejszej niż porównywalność.

Jeśli wartość zwracana `find` jest przypisana `const_iterator`do obiektu, nie można zmodyfikować obiektu wielomapowego. Jeśli wartość zwracana `find` jest przypisana `iterator`do obiektu , obiekt wielomapowy może zostać zmodyfikowany.

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

## <a name="multimapget_allocator"></a><a name="get_allocator"></a>multimap::get_allocator

Zwraca kopię obiektu alokatora używanego do konstruowania multimapy.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez multimapę.

### <a name="remarks"></a>Uwagi

Alokatory dla klasy multimap określają sposób zarządzania magazynem przez klasę. Domyślne alokatory dostarczane z klasami kontenerów biblioteki standardowej języka C++ są wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym tematem języka C++.

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

## <a name="multimapinsert"></a><a name="insert"></a>multimap::wstawianie

Wstawia element lub zakres elementów do multimapy.

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
|*Val*|Wartość elementu, który ma zostać wstawiony do multimapy.|
|*Gdzie*|Miejsce, aby rozpocząć wyszukiwanie prawidłowego punktu wstawiania. (Jeśli ten punkt bezpośrednio poprzedza *Gdzie*, wstawienie może wystąpić w zamortyzowanym czasie stałym zamiast czasu logarytmicznego.)|
|*ValTy (właśc.*|Parametr szablonu, który określa typ argumentu, którego mapa może użyć do skonstruowania elementu [value_type](../standard-library/map-class.md#value_type)i perfect-forwards *Val* jako argument.|
|*Pierwszym*|Położenie pierwszego elementu do skopiowania.|
|*Ostatnio*|Pozycja tuż poza ostatnim elementem do skopiowania.|
|*InputIterator*|Argument funkcji szablonu, który spełnia wymagania [iteratora wejściowego,](../standard-library/input-iterator-tag-struct.md) który wskazuje na elementy typu, który może służyć do konstruowania [obiektów value_type.](../standard-library/map-class.md#value_type)|
|*Ilist*|[initializer_list,](../standard-library/initializer-list.md) z którego mają być kopiowane elementy.|

### <a name="return-value"></a>Wartość zwracana

Funkcje elementów jednoelementowych, (1) i (2), zwracają iteratora do pozycji, w której nowy element został wstawiony do multimapy.

Funkcje członkowskie pojedynczego elementu z wskazówką (3) i (4) zwracają iteratora wskazującego pozycję, w której nowy element został wstawiony do multimapy.

### <a name="remarks"></a>Uwagi

Żadna liczba wskaźników ani odwołań nie jest unieważniona przez tę funkcję, ale może unieważnić wszystkie iteratory do kontenera.

Podczas wstawiania tylko jeden element, jeśli wyjątek, stan kontenera nie jest modyfikowany. Podczas wstawiania wielu elementów, jeśli wyjątek, kontener pozostaje w nieokreślonym, ale prawidłowym stanie.

[value_type](../standard-library/map-class.md#value_type) kontenera jest typedef, który należy do kontenera, a `multimap<K, V>::value_type` dla `pair<const K, V>`mapy, jest . Wartość elementu jest uporządkowaną parą, w której pierwszy składnik jest równy wartości klucza, a drugi składnik jest równy wartości danych elementu.

Funkcja elementów członkowskich zakresu (5) wstawia sekwencję wartości elementów do multimapy, która `[First, Last)`odpowiada każdemu elementowi adresowanemu przez iteratora w zakresie; w związku z tym *Last* nie jest wstawiany. Funkcja `end()` elementu członkowskiego kontenera odnosi się do pozycji tuż po ostatnim `m.insert(v.begin(), v.end());` elemencie `v` w `m`kontenerze — na przykład instrukcja wstawia wszystkie elementy do .

Funkcja elementu członkowskiego listy inicjatora (6) używa [initializer_list](../standard-library/initializer-list.md) do kopiowania elementów na mapie.

Aby wstawić element skonstruowany w miejscu — to znaczy, że nie są wykonywane żadne operacje kopiowania lub przenoszenia — zobacz [multimap::emplace](#emplace) i [multimap::emplace_hint](#emplace_hint).

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

## <a name="multimapiterator"></a><a name="iterator"></a>multimap::iterator

Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować dowolny element w multimapie.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

Zdefiniowane `iterator` przez multimapy wskazują na obiekty [value_type](#value_type), `pair<const Key, Type>`które są typu . Wartość klucza jest dostępna za pośrednictwem pierwszej pary elementów członkowskich, a wartość zamapowany element jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

Aby wyłuskać `iterator` *iter* wskazując element w multimap, należy użyć **->** operatora.

Aby uzyskać dostęp do wartości klucza `Iter->first`dla elementu, `(*Iter).first`należy użyć , co odpowiada . Aby uzyskać dostęp do wartości zamapowanej `Iter->second`bazy pomiarowej `(*Iter).second`dla elementu, należy użyć , co odpowiada .

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz [przykład, aby rozpocząć](#begin) przykład jak zadeklarować i używać `iterator`.

## <a name="multimapkey_comp"></a><a name="key_comp"></a>multimap::key_comp

Pobiera kopię obiektu porównania używanego do zamawiania kluczy w multimapie.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji używany przez multimapę do uporządkowania jego elementów.

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję elementu członkowskiego

`bool operator( const Key& x, const Key& y);`

który zwraca true, jeśli *x* ściśle poprzedza *y* w kolejności sortowania.

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

## <a name="multimapkey_compare"></a><a name="key_compare"></a>multimap::key_compare

Typ, który udostępnia obiekt funkcji, który można porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w multimapie.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare`jest synonimem parametru `Traits`szablonu .

Aby uzyskać `Traits` więcej informacji na temat [klasy multimap.](../standard-library/multimap-class.md)

### <a name="example"></a>Przykład

Zobacz przykład [key_comp](#key_comp) na przykład jak zadeklarować i `key_compare`używać .

## <a name="multimapkey_type"></a><a name="key_type"></a>multimap::key_type

Typ opisujący obiekt klucza sortowania, który stanowi każdy element multimapy.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type`jest synonimem parametru `Key`szablonu .

Aby uzyskać `Key`więcej informacji na temat , zobacz uwagi sekcji [tematu klasy multimap.](../standard-library/multimap-class.md)

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) na przykład jak zadeklarować i `key_type`używać .

## <a name="multimaplower_bound"></a><a name="lower_bound"></a>multimap::lower_bound

Zwraca iterator do pierwszego elementu w multimap, który z kluczem, który jest równy lub większy niż określony klucz.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz argumentu, który ma być porównywany z kluczem sortowania elementu z przeszukiwanej wielomapy.

### <a name="return-value"></a>Wartość zwracana

Iterator lub `const_iterator` który odnosi się do lokalizacji elementu w multimapie, który z kluczem, który jest równy lub większy niż klucz argumentu lub który odnosi się do lokalizacji po pomyślnym ostatniego elementu w multimapie, jeśli nie znaleziono dopasowania dla klucza.

Jeśli wartość zwracana `lower_bound` jest przypisana `const_iterator`do obiektu, nie można zmodyfikować obiektu wielomapowego. Jeśli wartość zwracana `lower_bound` jest przypisana do **iteratora,** obiekt multimap można zmodyfikować.

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

## <a name="multimapmapped_type"></a><a name="mapped_type"></a>multimap::mapped_type

Typ reprezentujący typ danych przechowywany w multimapie.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Uwagi

`mapped_type`jest synonimem parametru `Type`szablonu .

Aby uzyskać `Type` więcej informacji na temat [klasy multimap.](../standard-library/multimap-class.md)

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) na przykład jak zadeklarować i `key_type`używać .

## <a name="multimapmax_size"></a><a name="max_size"></a>multimap::max_size

Zwraca maksymalną długość multimapy.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna możliwa długość multimapy.

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

## <a name="multimapmultimap"></a><a name="multimap"></a>multimap::multimap

Konstruuje multimapę, która jest pusta lub która jest kopią całości lub części innego multimapy.

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

|Parametr|Opis|
|-|-|
|*Al*|Klasa alokatora magazynu, który ma być używany dla tego obiektu wielomapowego, który domyślnie ma wartość Alokator.|
|*Comp*|Funkcja porównywania `constTraits` typu używana do zamawiania elementów na `Traits`mapie, która domyślnie ma wartość .|
|*Prawo*|Mapa, której skonstruowany zestaw ma być kopią.|
|*Pierwszym*|Położenie pierwszego elementu w zakresie elementów do skopiowania.|
|*Ostatnio*|Położenie pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|
|*Ilist*|Lista initializer_list, z której mają być skopiowane elementy.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują typ obiektu alokatora, który zarządza magazynem pamięci dla multimapy i który można później zwrócić, wywołując [get_allocator](#get_allocator). Parametr alokatora jest często pomijany w deklaracjach klas i przetwarzaniu wstępnym makr używanych do zastępowania alternatywnych alokatorów.

Wszystkie konstruktory inicjują ich multimap.

Wszystkie konstruktory przechowują `Traits` obiekt funkcji typu, który jest używany do ustanawiania kolejności wśród kluczy multimapy i który może być później zwrócony przez wywołanie [key_comp](#key_comp).

Pierwsze trzy konstruktory określają pustą początkową multimapę, drugą określającą typ funkcji porównania (*Comp*), która ma być używana do ustalenia kolejności elementów, a trzecią jawnie określającą typ alokatora (*Al*), który ma być używany. Słowo kluczowe **jawne** pomija pewne rodzaje automatycznej konwersji typu.

Czwarty konstruktor określa kopię multimap *Right*.

Piąty konstruktor określa kopię multimapy, przesuwając *prawy*.

Szósty, siódmy i ósmy konstruktorzy kopiują członków initializer_list.

Następne trzy konstruktory `[First, Last)` skopiować zakres mapy z coraz jawności w `Traits` określaniu typu funkcji porównania klasy i alokatora.

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

## <a name="multimapoperator"></a><a name="op_eq"></a>multimapa::operator=

Zastępuje elementy multimapy kopią innej multimapy.

```cpp
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Prawo*|[Multimapa](../standard-library/multimap-class.md) kopiowana do `multimap`pliku .|

### <a name="remarks"></a>Uwagi

Po wymazaniu istniejących elementów `multimap` `operator=` w programie , albo kopiuje `multimap`lub przenosi zawartość w *prawo* do .

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

## <a name="multimappointer"></a><a name="pointer"></a>multimap::pointer

Typ, który zapewnia wskaźnik do elementu w multimapie.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien służyć do uzyskiwania dostępu do elementów w obiekcie wielomapowym.

## <a name="multimaprbegin"></a><a name="rbegin"></a>multimap::rbegin

Zwraca iterator adresowania pierwszy element w odwróconej multimapy.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnej dwukierunkowej iterator adresowania pierwszy element w odwróconej multimapy lub adresowania, co było ostatnim elementem w nieodwrotowej multimap.

### <a name="remarks"></a>Uwagi

`rbegin`jest używany z odwróconą multimapą, tak jak [begin](#begin) jest używany z multimapą.

Jeśli zwracana `rbegin` wartość jest przypisana `const_reverse_iterator`do obiektu , wówczas nie można zmodyfikować obiektu wielomapowego. Jeśli zwracana `rbegin` wartość jest przypisana `reverse_iterator`do , następnie obiekt multimap można zmodyfikować.

`rbegin`można iterować za pomocą wielomapowej mapy do tyłu.

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

## <a name="multimapreference"></a><a name="reference"></a>multimap::odwołanie

Typ, który zawiera odwołanie do elementu przechowywanego w multimapie.

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
   // non-const_reference cannot be used to access the key
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

## <a name="multimaprend"></a><a name="rend"></a>multimap::rend

Zwraca iterator, który odnosi się do lokalizacji po ostatniej pozycji elementu w odwróconej multimapy.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnej dwukierunkowej iteratora, który odnosi się do lokalizacji po pomyślnym ostatni element w odwróconej multimapy (lokalizacja, która poprzedziła pierwszy element w nieodwrotowej multimap).

### <a name="remarks"></a>Uwagi

`rend`jest używany z odwróconą multimapą, tak jak [koniec](../standard-library/map-class.md#end) jest używany z multimapą.

Jeśli zwracana `rend` wartość jest przypisana `const_reverse_iterator`do obiektu , wówczas nie można zmodyfikować obiektu wielomapowego. Jeśli zwracana `rend` wartość jest przypisana `reverse_iterator`do , następnie obiekt multimap można zmodyfikować.

`rend`można użyć do sprawdzenia, czy odwrotny iterator osiągnął koniec jego multimap.

Wartość zwrócona `rend` przez nie powinny być wyłuskiwane.

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

## <a name="multimapreverse_iterator"></a><a name="reverse_iterator"></a>multimap::reverse_iterator

Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować element w odwróconej multimapie.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iteracji za pomocą multimapy w odwrotnej kolejności.

Zdefiniowane `reverse_iterator` przez multimapy wskazują na obiekty [value_type](#value_type), `pair<const Key, Type>`które są typu . Wartość klucza jest dostępna za pośrednictwem pierwszej pary elementów członkowskich, a wartość zamapowany element jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

Aby wyłuskać `reverse_iterator` *rIter* wskazujący element w multimapie, należy użyć **->** operatora.

Aby uzyskać dostęp do wartości klucza `rIter->first`dla elementu, `(*rIter).first`należy użyć , co odpowiada . Aby uzyskać dostęp do wartości zamapowanej `rIter->second`bazy pomiarowej `(*rIter).second`dla elementu, należy użyć , co odpowiada .

### <a name="example"></a>Przykład

Zobacz przykład [dla rbegin](#rbegin) na przykład jak `reverse_iterator`zadeklarować i używać .

## <a name="multimapsize"></a><a name="size"></a>multimap::size

Zwraca liczbę elementów w multimapie.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość multimapy.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie funkcji elementu członkowskiego multimap::size.

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

## <a name="multimapsize_type"></a><a name="size_type"></a>multimap::size_type

Niepodpisany typ liczby całkowitej, który zlicza liczbę elementów w multimapie.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [rozmiaru,](#size) aby uzyskać przykład deklarowania i używania`size_type`

## <a name="multimapswap"></a><a name="swap"></a>multimap::swap

Wymienia elementy dwóch multimap.

```cpp
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Multimapa zapewniająca elementy, które mają zostać zamienione, lub multimapa, której `left`elementy mają być wymieniane z elementami multimapy .

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego unieważnia żadnych odwołań, wskaźników lub iteratorów, które wyznaczają elementy w dwóch multimapach, których elementy są wymieniane.

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

## <a name="multimapupper_bound"></a><a name="upper_bound"></a>multimap::upper_bound

Zwraca iterator do pierwszego elementu w multimap, który z kluczem, który jest większy niż określony klucz.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz argumentu, który ma być porównywany z kluczem sortowania elementu z przeszukiwanej wielomapy.

### <a name="return-value"></a>Wartość zwracana

Iterator lub `const_iterator` który odnosi się do lokalizacji elementu w multimapie, który z kluczem, który jest większy niż klucz argumentu lub który odnosi się do lokalizacji po pomyślnym ostatniego elementu w multimapie, jeśli nie znaleziono dopasowania dla klucza.

Jeśli wartość zwracana jest `const_iterator`przypisana do obiektu, nie można zmodyfikować obiektu wielomapowego. Jeśli wartość zwracana jest `iterator`przypisana do , obiekt multimap można zmodyfikować.

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

## <a name="multimapvalue_comp"></a><a name="value_comp"></a>multimap::value_comp

Funkcja elementu członkowskiego zwraca obiekt funkcji, który określa kolejność elementów w multimapie, porównując ich wartości klucza.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji porównania, który jest używany przez multimapę do uporządkowania jego elementów.

### <a name="remarks"></a>Uwagi

Dla multimap *m*, jeśli dwa elementy *e1*(*k1*, *d1*) i `value_type` *e2*(*k2*, *d2*) są obiektami typu, gdzie *k1* `m.key_comp(k1, k2)`i *k2* są ich klucze typu `key_type` i *d1* i *d2* są ich dane typu, `mapped_type`a następnie `m.value_comp(e1, e2)` jest odpowiednikiem .

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

## <a name="multimapvalue_type"></a><a name="value_type"></a>multimap::value_type

Typ reprezentujący typ obiektu przechowywanego jako element na mapie.

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

[Pojemniki](../cpp/containers-modern-cpp.md)\
[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Odwołanie do standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
