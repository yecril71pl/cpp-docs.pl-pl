---
title: hash_multiset — Klasa
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_multiset
- hash_set/stdext::hash_multiset::allocator_type
- hash_set/stdext::hash_multiset::const_iterator
- hash_set/stdext::hash_multiset::const_pointer
- hash_set/stdext::hash_multiset::const_reference
- hash_set/stdext::hash_multiset::const_reverse_iterator
- hash_set/stdext::hash_multiset::difference_type
- hash_set/stdext::hash_multiset::iterator
- hash_set/stdext::hash_multiset::key_compare
- hash_set/stdext::hash_multiset::key_type
- hash_set/stdext::hash_multiset::pointer
- hash_set/stdext::hash_multiset::reference
- hash_set/stdext::hash_multiset::reverse_iterator
- hash_set/stdext::hash_multiset::size_type
- hash_set/stdext::hash_multiset::value_compare
- hash_set/stdext::hash_multiset::value_type
- hash_set/stdext::hash_multiset::begin
- hash_set/stdext::hash_multiset::cbegin
- hash_set/stdext::hash_multiset::cend
- hash_set/stdext::hash_multiset::clear
- hash_set/stdext::hash_multiset::count
- hash_set/stdext::hash_multiset::crbegin
- hash_set/stdext::hash_multiset::crend
- hash_set/stdext::hash_multiset::emplace
- hash_set/stdext::hash_multiset::emplace_hint
- hash_set/stdext::hash_multiset::empty
- hash_set/stdext::hash_multiset::end
- hash_set/stdext::hash_multiset::equal_range
- hash_set/stdext::hash_multiset::erase
- hash_set/stdext::hash_multiset::find
- hash_set/stdext::hash_multiset::get_allocator
- hash_set/stdext::hash_multiset::insert
- hash_set/stdext::hash_multiset::key_comp
- hash_set/stdext::hash_multiset::lower_bound
- hash_set/stdext::hash_multiset::max_size
- hash_set/stdext::hash_multiset::rbegin
- hash_set/stdext::hash_multiset::rend
- hash_set/stdext::hash_multiset::size
- hash_set/stdext::hash_multiset::swap
- hash_set/stdext::hash_multiset::upper_bound
- hash_set/stdext::hash_multiset::value_comp
helpviewer_keywords:
- stdext::hash_multiset
- stdext::hash_multiset::allocator_type
- stdext::hash_multiset::const_iterator
- stdext::hash_multiset::const_pointer
- stdext::hash_multiset::const_reference
- stdext::hash_multiset::const_reverse_iterator
- stdext::hash_multiset::difference_type
- stdext::hash_multiset::iterator
- stdext::hash_multiset::key_compare
- stdext::hash_multiset::key_type
- stdext::hash_multiset::pointer
- stdext::hash_multiset::reference
- stdext::hash_multiset::reverse_iterator
- stdext::hash_multiset::size_type
- stdext::hash_multiset::value_compare
- stdext::hash_multiset::value_type
- stdext::hash_multiset::begin
- stdext::hash_multiset::cbegin
- stdext::hash_multiset::cend
- stdext::hash_multiset::clear
- stdext::hash_multiset::count
- stdext::hash_multiset::crbegin
- stdext::hash_multiset::crend
- stdext::hash_multiset::emplace
- stdext::hash_multiset::emplace_hint
- stdext::hash_multiset::empty
- stdext::hash_multiset::end
- stdext::hash_multiset::equal_range
- stdext::hash_multiset::erase
- stdext::hash_multiset::find
- stdext::hash_multiset::get_allocator
- stdext::hash_multiset::insert
- stdext::hash_multiset::key_comp
- stdext::hash_multiset::lower_bound
- stdext::hash_multiset::max_size
- stdext::hash_multiset::rbegin
- stdext::hash_multiset::rend
- stdext::hash_multiset::size
- stdext::hash_multiset::swap
- stdext::hash_multiset::upper_bound
- stdext::hash_multiset::value_comp
ms.assetid: 0580397a-a76e-40ad-aea2-5c6f3a9d0a21
ms.openlocfilehash: 8888f393e1058e3cd5ff968d9433b5306cac4949
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370658"
---
# <a name="hash_multiset-class"></a>hash_multiset — Klasa

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Klasa kontenera hash_multiset jest rozszerzeniem standardowej biblioteki języka C++ i jest używana do przechowywania i szybkiego pobierania danych z kolekcji, w której wartości zawartych elementów służą jako wartości klucza i nie muszą być unikatowe.

## <a name="syntax"></a>Składnia

```cpp
template <class Key, class Traits =hash_compare<Key, less <Key>>, class Allocator =allocator <Key>>
class hash_multiset
```

### <a name="parameters"></a>Parametry

*Klucz*\
Typ danych elementu, który ma być przechowywany w hash_multiset.

*Cechy*\
Typ, który zawiera dwa obiekty funkcji, jeden z klasy porównania, który jest binarnym predykatem w stanie porównać dwie wartości elementu jako klucze sortowania w celu określenia `size_t`ich względnej kolejności i funkcję mieszania, która jest jednoarowym odwzorowaniem mapowania wartości klucza elementów do niepodpisanych liczb całkowitych typu . Ten argument jest opcjonalny i `hash_compare<Key, less<Key> >` jest wartością domyślną.

*Programu przydzielania*\
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji hash_multiset i alokacji pamięci. Ten argument jest opcjonalny, `allocator<Key>`a wartością domyślną jest .

## <a name="remarks"></a>Uwagi

hash_multiset jest:

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza. Ponadto, jest prostym kontenerem asocjacyjnym, ponieważ jego wartości elementu są jego wartościami klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.

- Hashed, ponieważ jego elementy są pogrupowane w zasobnikach na podstawie wartości funkcji mieszania stosowane do wartości klucza elementów.

- Unikatowy w tym sensie, że każdy z jego elementów musi mieć unikatowy klucz. Ponieważ hash_multiset jest również prostym kontenerem zespolowym, jego elementy są również unikatowe.

- Szablon klasy, ponieważ funkcje, które zapewnia, jest ogólny i tak niezależne od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Główną zaletą mieszania nad sortowanie jest większa wydajność: pomyślne mieszanie wykonuje wstawienia, usunięcia i znajduje w stałym średnim czasie w porównaniu z czasem proporcjonalnym do logarytmu liczby elementów w kontenerze dla technik sortowania. Nie można bezpośrednio zmienić wartości elementu w zestawie. Zamiast tego musisz usunąć stare wartości i wstawić elementy z nowymi wartościami.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Haszowane kontenery zespolone są zoptymalizowane pod kątem operacji wyszukiwania, wstawiania i usuwania. Funkcje członkowskie, które jawnie obsługują te operacje są wydajne, gdy są używane z dobrze zaprojektowaną funkcją mieszania, wykonując je w czasie, który jest średnio stały i nie zależy od liczby elementów w kontenerze. Dobrze zaprojektowana funkcja mieszania tworzy jednolity rozkład wartości skrótu i minimalizuje liczbę kolizji, gdzie mówi się, że kolizja występuje, gdy różne wartości klucza są mapowane na tę samą wartość skrótu. W najgorszym przypadku z najgorszą możliwą funkcją mieszania liczba operacji jest proporcjonalna do liczby elementów w sekwencji (czas liniowy).

hash_multiset powinny być kontenerem zespolonego z wyboru, gdy warunki kojarzenia wartości z ich kluczami są spełniane przez aplikację. Elementy hash_multiset mogą być wielokrotne i służyć jako własne klucze sortowania, więc klucze nie są unikatowe. Model dla tego typu konstrukcji jest uporządkowaną listą, np. wyrazów, w których wyrazy mogą występować więcej niż jeden raz. Gdyby wiele wystąpień wyrazów nie było dozwolone, hash_set byłaby odpowiednią strukturą kontenera. Jeśli unikatowe definicje zostały dołączone jako wartości do listy unikatowych słów kluczowych, hash_map byłoby odpowiednią strukturą zawierającą te dane. Jeśli zamiast tego definicje nie były unikatowe, hash_multimap byłby kontenerem z wyboru.

Hash_multiset porządkuje sekwencję, jaką kontroluje, wywołując obiekt przechowywanych cech mieszania typu [value_compare](#value_compare). Ten przechowywany obiekt może być dostępny, wywołując funkcję elementu członkowskiego [key_comp](#key_comp). Taki obiekt funkcji musi zachowywać się `hash_compare<Key, less<Key> >`tak samo jak obiekt klasy . W szczególności dla *Key* wszystkich wartości `Key`Klucz `Trait(Key)` typu, wywołanie daje `size_t`rozkład wartości typu .

Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarny *f*( *x*, *y*) jest obiektem funkcyjnym, który ma dwa obiekty argumentów x i y oraz zwracaną wartość true lub false. Kolejność nałożona na hash_multiset jest ścisłym słabym porządkiem, jeśli predykat binarny jest niereflexive, antysymetryczny i przechodni, a jeśli równoważność jest przechodnia, gdzie dwa obiekty x i y są zdefiniowane jako równoważne, gdy zarówno *f*( *x*, *y*) i *f*( *y*, *x*) są fałszywe. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

Rzeczywista kolejność elementów w kontrolowanej sekwencji zależy od funkcji mieszania, funkcji zamawiania i bieżącego rozmiaru tabeli mieszania przechowywanej w obiekcie kontenera. Nie można określić bieżący rozmiar tabeli mieszania, więc nie można ogólnie przewidzieć kolejność elementów w kontrolowanej sekwencji. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Iterator dostarczony przez klasę hash_multiset jest dwukierunkowym iteratorem, ale funkcje członkowskie klasy wstawiają i hash_multiset mają wersje, które przyjmują jako parametry szablonu słabszy iterator wejściowy, którego wymagania dotyczące funkcjonalności są bardziej minimalne niż wymagania gwarantowane przez klasę dwukierunkowych iteratorów. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każda koncepcja iteratora ma swój własny hash_multiset wymagań, a algorytmy, które z nimi współpracują, muszą ograniczać swoje założenia do wymagań dostarczonych przez ten typ iteratora. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny hash_multiset funkcjonalności, ale wystarczy, aby móc sensownie mówić o szeregu iteratorów [ `first`, `last`) w kontekście funkcji elementu członkowskiego klasy.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Hash_multiset](#hash_multiset)|Konstruuje, `hash_multiset` który jest pusty lub który jest kopią całości lub części innego `hash_multiset`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który `allocator` reprezentuje klasę `hash_multiset` dla obiektu.|
|[const_iterator](#const_iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytać `hash_multiset` **const** element w .|
|[const_pointer](#const_pointer)|Typ, który zapewnia wskaźnik do **const** elementu w `hash_multiset`.|
|[const_reference](#const_reference)|Typ, który zapewnia odwołanie do **const** `hash_multiset` element przechowywane w do odczytu i wykonywania operacji **const.**|
|[Const_reverse_iterator](#const_reverse_iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytać `hash_multiset`dowolny element **const** w .|
|[difference_type](#difference_type)|Typ liczby całkowitej podpisanej, który zapewnia różnicę między dwoma iteratorami, które adresują elementy w ramach tego samego `hash_multiset`.|
|[Sterująca](#iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować dowolny element w . `hash_multiset`|
|[key_compare](#key_compare)|Typ, który udostępnia obiekt funkcji, który może porównać dwa klucze `hash_multiset`sortowania, aby określić względną kolejność dwóch elementów w programie .|
|[Key_type](#key_type)|Typ, który opisuje obiekt przechowywany jako `hash_set` element w jego pojemności jako klucz sortowania.|
|[pointer](#pointer)|Typ, który zapewnia wskaźnik do `hash_multiset`elementu w .|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu `hash_multiset`przechowywanego w .|
|[Reverse_iterator](#reverse_iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować element w odwróconym `hash_multiset`.|
|[size_type](#size_type)|Niepodpisany typ liczby całkowitej, który może `hash_multiset`reprezentować liczbę elementów w programie .|
|[Value_compare](#value_compare)|Typ, który zawiera dwa obiekty funkcji, predykat binarny klasy `hash_multiset` porównania, które można porównać dwie wartości elementu a, aby określić ich względnej kolejności i predykatu unary, który skróty elementów.|
|[value_type](#value_type)|Typ, który opisuje obiekt przechowywany jako `hash_multiset` element w jego pojemności jako wartość.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Rozpocząć](#begin)|Zwraca iterator, który odnosi się `hash_multiset`do pierwszego elementu w .|
|[cbegin ( cbegin )](#cbegin)|Zwraca iterator const adresowania pierwszego `hash_multiset`elementu w .|
|[cend](#cend)|Zwraca iterator const, który odnosi się do `hash_multiset`lokalizacji, która po pomyślnym ostatnim elemencie w pliku .|
|[Wyczyść](#clear)|Usuwa wszystkie elementy pliku `hash_multiset`.|
|[Liczba](#count)|Zwraca liczbę elementów, `hash_multiset` w których klucz odpowiada kluczowi określonej parametrowi|
|[Crbegin](#crbegin)|Zwraca iterator const adresowania pierwszego elementu `hash_multiset`w odwróconym .|
|[Crend](#crend)|Zwraca iterator const, który odnosi się do lokalizacji, która po pomyślnym ostatnim elemencie w odwróconym `hash_multiset`.|
|[miejsce](#emplace)|Wstawia element skonstruowany w `hash_multiset`miejscu do .|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w `hash_multiset`miejscu do , z wskazówką położenia.|
|[Pusty](#empty)|Sprawdza, `hash_multiset` czy a jest pusty.|
|[Końcu](#end)|Zwraca iterator, który odnosi się do lokalizacji, która po pomyślnym ostatnim elemencie w pliku `hash_multiset`.|
|[equal_range](#equal_range)|Zwraca parę iteratorów odpowiednio do pierwszego elementu `hash_multiset` w kluczu, który jest większy niż określony `hash_multiset` klucz i do pierwszego elementu w kluczu, który jest równy lub większy niż klucz.|
|[Wymazać](#erase)|Usuwa element lub zakres elementów `hash_multiset` w określonym położeniu lub usuwa elementy, które pasują do określonego klucza.|
|[find](#find)|Zwraca iterator adresowania lokalizacji elementu w, `hash_multiset` który ma klucz równoważny określony klucz.|
|[Get_allocator](#get_allocator)|Zwraca kopię `allocator` obiektu używanego do `hash_multiset`konstruowania pliku .|
|[Wstawić](#insert)|Wstawia element lub zakres elementów do pliku `hash_multiset`.|
|[Key_comp](#key_compare)|Pobiera kopię obiektu porównania używanego do zamawiania kluczy w pliku `hash_multiset`.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu `hash_multiset` w kluczu, który jest równy lub większy niż określony klucz.|
|[Max_size](#max_size)|Zwraca maksymalną długość `hash_multiset`pliku .|
|[rbegin (rbegin)](#rbegin)|Zwraca iteratora adresującego pierwszy element `hash_multiset`w odwróconym .|
|[Rend](#rend)|Zwraca iterator, który odnosi się do lokalizacji, `hash_multiset`która zastępuje ostatni element w odwróconym .|
|[Rozmiar](#size)|Zwraca liczbę elementów `hash_multiset`w pliku .|
|[Wymiany](#swap)|Wymienia elementy dwóch `hash_multiset`s.|
|[upper_bound](#upper_bound)|Zwraca iterator do pierwszego elementu `hash_multiset` w kluczu, który jest równy lub większy niż określony klucz.|
|[value_comp](#value_comp)|Pobiera kopię obiektu cech mieszania używanego do mieszania i kolejności `hash_multiset`wartości klucza elementu w pliku .|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[hash_multiset::operator=](#op_eq)|Zastępuje elementy hash_multiset kopią innego hash_multiset.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_set>

**Obszar nazw:** stdext

## <a name="hash_multisetallocator_type"></a><a name="allocator_type"></a>hash_multiset::allocator_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Typ reprezentujący klasę alokatora dla hash_multiset obiektu.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [get_allocator](#get_allocator) na przykład za pomocą`allocator_type`

## <a name="hash_multisetbegin"></a><a name="begin"></a>hash_multiset::begin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator, który odnosi się do pierwszego elementu w hash_multiset.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator adresowania pierwszy element w hash_multiset lub lokalizacji po zastąpieniu pustego hash_multiset.

### <a name="remarks"></a>Uwagi

Jeśli zwracana `begin` wartość jest przypisana `const_iterator`do , elementy w hash_multiset obiektu nie można modyfikować. Jeśli zwracana `begin` wartość jest przypisana `iterator`do , elementy w hash_multiset obiektu mogą być modyfikowane.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.begin( );
   cout << "The first element of hms1 is " << *hms1_Iter << endl;

   hms1_Iter = hms1.begin( );
   hms1.erase( hms1_Iter );

   // The following 2 lines would err because the iterator is const
   // hms1_cIter = hms1.begin( );
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.begin( );
   cout << "The first element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The first element of hms1 is 1
The first element of hms1 is now 2
```

## <a name="hash_multisetcbegin"></a><a name="cbegin"></a>hash_multiset::cbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator konspiratora, który odnosi się do pierwszego elementu w hash_multiset.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator const adresujący pierwszy element w [hash_multiset](../standard-library/hash-multiset-class.md) lub lokalizację, która `hash_multiset`zastępuje pusty plik .

### <a name="remarks"></a>Uwagi

Z wartością `cbegin`zwracaną , `hash_multiset` elementy w obiekcie nie mogą być modyfikowane.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_cbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cbegin( );
   cout << "The first element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
```

## <a name="hash_multisetcend"></a><a name="cend"></a>hash_multiset::cend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator const, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_multiset.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator konspiracyjny, który odnosi się do lokalizacji, która zastępuje ostatni element w [hash_multiset](../standard-library/hash-multiset-class.md). Jeśli `hash_multiset` jest pusty, `hash_multiset::cend == hash_multiset::begin`a następnie .

### <a name="remarks"></a>Uwagi

`cend`służy do sprawdzenia, czy iterator osiągnął `hash_multiset`koniec jego . Wartość zwrócona `cend` przez nie powinny być wyłuskiwane.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_cend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cend( );
   hs1_cIter--;
   cout << "The last element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
```

## <a name="hash_multisetclear"></a><a name="clear"></a>hash_multiset::wyczyść

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Usuwa wszystkie elementy hash_multiset.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multiset_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 1 );
   hms1.insert( 2 );

   cout << "The size of the hash_multiset is initially " << hms1.size( )
        << "." << endl;

   hms1.clear( );
   cout << "The size of the hash_multiset after clearing is "
        << hms1.size( ) << "." << endl;
}
```

```Output
The size of the hash_multiset is initially 2.
The size of the hash_multiset after clearing is 0.
```

## <a name="hash_multisetconst_iterator"></a><a name="const_iterator"></a>hash_multiset::const_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Typ, który zapewnia dwukierunkowe iteratora, który można odczytać **const** element w hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz [przykład, aby](#begin) rozpocząć `const_iterator`przykład przy użyciu .

## <a name="hash_multisetconst_pointer"></a><a name="const_pointer"></a>hash_multiset::const_pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Typ, który zapewnia wskaźnik do **const** elementu w hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

W większości przypadków [const_iterator](#const_iterator) powinien służyć do uzyskiwania dostępu do elementów w **const** hash_multiset obiektu.

## <a name="hash_multisetconst_reference"></a><a name="const_reference"></a>hash_multiset::const_reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Typ, który zapewnia odwołanie do **const** element przechowywane w hash_multiset do odczytu i wykonywania operacji **const.**

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multiset_const_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_multiset
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_multiset is 10.
```

## <a name="hash_multisetconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>hash_multiset::const_reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Typ, który zapewnia dwukierunkowy iterator, który może odczytać dowolny element **const** w hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartość elementu i jest używany do iteracji za pośrednictwem hash_multiset w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład [rend](#rend) na przykład jak zadeklarować `const_reverse_iterator`i użyć .

## <a name="hash_multisetcount"></a><a name="count"></a>hash_multiset::count

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca liczbę elementów w hash_multiset którego klucz odpowiada kluczowi określonej parametru.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz elementów, które mają być dopasowane z hash_multiset.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w hash_multiset z kluczem określonym przez parametr.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca liczbę elementów w następującym zakresie:

\[lower_bound(*klucz*), upper_bound(*klucz*) ).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie funkcji elementu członkowskiego hash_multiset::count.

```cpp
// hash_multiset_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1;
    hash_multiset<int>::size_type i;

    hms1.insert(1);
    hms1.insert(1);

    // Keys do not need to be unique in hash_multiset,
    // so duplicates may exist.
    i = hms1.count(1);
    cout << "The number of elements in hms1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hms1.count(2);
    cout << "The number of elements in hms1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hms1 with a sort key of 1 is: 2.
The number of elements in hms1 with a sort key of 2 is: 0.
```

## <a name="hash_multisetcrbegin"></a><a name="crbegin"></a>hash_multiset::crbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator konstacyjny adresowania pierwszy element w odwróconej hash_multiset.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Const odwrotnej dwukierunkowej iteratora adresowania pierwszego elementu w odwróconej [hash_multiset](../standard-library/hash-multiset-class.md) lub adresowania, co `hash_multiset`było ostatnim elementem w nieodwrotowej .

### <a name="remarks"></a>Uwagi

`crbegin`jest używany z `hash_multiset` odwróconym tak samo, jak [hash_multiset::begin](#begin) jest używany z . `hash_multiset`

Z wartością `crbegin`zwracaną `hash_multiset` obiektu nie można modyfikować obiektu.

`crbegin`może być używany do iteracji do `hash_multiset` tyłu.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_crbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
```

## <a name="hash_multisetcrend"></a><a name="crend"></a>hash_multiset::crend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator const, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w odwróconym hash_multiset.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Const odwrotnej dwukierunkowej iteratora, który odnosi się do lokalizacji po ostatniej pozycji elementu w odwróconym [hash_multiset](../standard-library/hash-multiset-class.md) (lokalizacja, która poprzedziła pierwszy element w nieodwrotzony). `hash_multiset`

### <a name="remarks"></a>Uwagi

`crend`jest używany z `hash_multiset` odwróconym tak samo, jak [hash_multiset::end](#end) jest używany z . `hash_multiset`

Z wartością `crend`zwracaną `hash_multiset` obiektu nie można modyfikować obiektu.

`crend`można użyć do sprawdzenia, czy odwrotny iterator osiągnął koniec hash_multiset.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_crend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
```

## <a name="hash_multisetdifference_type"></a><a name="difference_type"></a>hash_multiset::d00_typ

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Typ liczby całkowitej podpisana, która zapewnia różnicę między dwoma iteratorami, które adresują elementy w ramach tej samej hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Jest `difference_type` to typ zwracany podczas odejmowania lub zwiększania za pośrednictwem iteratorów kontenera. Jest `difference_type` zazwyczaj używany do reprezentowania liczby elementów `first` `last`w zakresie [ , `first` `last`) między iteratorów i , zawiera element wskazany przez `first` i `last`zakres elementów do, ale nie w tym element wskazany przez .

Należy zauważyć, że chociaż `difference_type` jest dostępny dla wszystkich iteratorów, które spełniają wymagania iteratora wejściowego, który zawiera klasę dwukierunkowych iteratorów obsługiwanych przez odwracalne kontenery, takie jak zestaw. Odejmowanie między iteratorami jest obsługiwane tylko przez iteratory dostępu losowego dostarczane przez kontener dostępu losowego, taki jak wektor lub deque.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter, hms1_bIter, hms1_eIter;

   hms1.insert( 20 );
   hms1.insert( 10 );

   // hash_multiset elements need not be unique
   hms1.insert( 20 );

   hms1_bIter = hms1.begin( );
   hms1_eIter = hms1.end( );

   hash_multiset <int>::difference_type   df_typ5, df_typ10,
        df_typ20;

   df_typ5 = count( hms1_bIter, hms1_eIter, 5 );
   df_typ10 = count( hms1_bIter, hms1_eIter, 10 );
   df_typ20 = count( hms1_bIter, hms1_eIter, 20 );

   // The keys & hence the elements of a hash_multiset
   // need not be unique and may occur multiple times
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_multiset hms1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_multiset hms1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_multiset hms1.\n";

   // Count the number of elements in a hash_multiset
   hash_multiset <int>::difference_type  df_count = 0;
   hms1_Iter = hms1.begin( );
   while ( hms1_Iter != hms1_eIter)
   {
      df_count++;
      hms1_Iter++;
   }

   cout << "The number of elements in the hash_multiset hms1 is "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_multiset hms1.
The number '10' occurs 1 times in hash_multiset hms1.
The number '20' occurs 2 times in hash_multiset hms1.
The number of elements in the hash_multiset hms1 is 3.
```

## <a name="hash_multisetemplace"></a><a name="emplace"></a>hash_multiset::miejsce

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Wstawia element skonstruowany w miejscu do hash_multiset.

```cpp
template <class ValTy>
iterator insert(ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Wartość elementu, który ma zostać wstawiony `hash_multiset` do [hash_multiset,](../standard-library/hash-multiset-class.md) chyba że już zawiera ten element lub, bardziej ogólnie, element, którego klucz jest równoważno uporządkowany.|

### <a name="return-value"></a>Wartość zwracana

Funkcja `emplace` elementu członkowskiego zwraca iteratora, który wskazuje na pozycję, w której nowy element został wstawiony.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multiset_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms3;
   string str1("a");

   hms3.emplace(move(str1));
   cout << "After the emplace insertion, hms3 contains "
      << *hms3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms3 contains a.
```

## <a name="hash_multisetemplace_hint"></a><a name="emplace_hint"></a>hash_multiset::emplace_hint

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Wstawia element skonstruowany w miejscu do hash_multiset, z podpowiedzią o umieszczeniu.

```cpp
template <class ValTy>
iterator insert(
    const_iterator where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Wartość elementu, który ma zostać wstawiony `hash_multiset` do [hash_multiset,](../standard-library/hash-multiset-class.md) chyba że już zawiera ten element lub, bardziej ogólnie, element, którego klucz jest równoważno uporządkowany.

*Gdzie*\
Miejsce, aby rozpocząć wyszukiwanie prawidłowego punktu wstawiania. (Wstawienie może wystąpić w zamortyzowanym czasie stałym, a nie w czasie logarytmicznym, jeśli punkt wstawiania nastąpi natychmiast, *gdzie*.)

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego [hash_multiset::emplace](#emplace) zwraca iterator, który wskazuje pozycję, w której `hash_multiset`nowy element został wstawiony do .

### <a name="remarks"></a>Uwagi

Wstawienie może wystąpić w zamortyzowanym czasie stałym, a nie w czasie logarytmicznym, jeśli punkt wstawiania natychmiast następuje *tam, gdzie*.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms1;
   string str1("a");

   hms1.insert(hms1.begin(), move(str1));
   cout << "After the emplace insertion, hms1 contains "
      << *hms1.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms1 contains a.
```

## <a name="hash_multisetempty"></a><a name="empty"></a>hash_multiset::empty

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Sprawdza, czy hash_multiset jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli hash_multiset jest pusta; **false,** jeśli hash_multiset jest niepusty.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multiset_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2;
   hms1.insert ( 1 );

   if ( hms1.empty( ) )
      cout << "The hash_multiset hms1 is empty." << endl;
   else
      cout << "The hash_multiset hms1 is not empty." << endl;

   if ( hms2.empty( ) )
      cout << "The hash_multiset hms2 is empty." << endl;
   else
      cout << "The hash_multiset hms2 is not empty." << endl;
}
```

```Output
The hash_multiset hms1 is not empty.
The hash_multiset hms2 is empty.
```

## <a name="hash_multisetend"></a><a name="end"></a>hash_multiset::end

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_multiset.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_multiset. Jeśli hash_multiset jest pusta, hash_multiset::end == hash_multiset::begin.

### <a name="remarks"></a>Uwagi

`end`służy do testowania, czy iterator osiągnął koniec hash_multiset. Wartość zwrócona `end` przez nie powinny być wyłuskiwane.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: iterator hms1_Iter;
   hash_multiset <int> :: const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.end( );
   hms1_Iter--;
   cout << "The last element of hms1 is " << *hms1_Iter << endl;

   hms1.erase( hms1_Iter );

   // The following 3 lines would err because the iterator is const
   // hms1_cIter = hms1.end( );
   // hms1_cIter--;
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.end( );
   hms1_cIter--;
   cout << "The last element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The last element of hms1 is 3
The last element of hms1 is now 2
```

## <a name="hash_multisetequal_range"></a><a name="equal_range"></a>hash_multiset::equal_range

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca parę iteratorów odpowiednio do pierwszego elementu w hash_multiset z kluczem, który jest większy niż określony klucz i do pierwszego elementu w hash_multiset z kluczem, który jest równy lub większy niż klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz argumentu, który ma być porównywany z kluczem sortowania elementu z hash_multiset przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

Para iteratorów, gdzie pierwszy jest [lower_bound](#lower_bound) klucza, a drugi jest [upper_bound](#upper_bound) klucza.

Aby uzyskać dostęp do pierwszego `pr` iteratora pary `pr`zwróconej przez funkcję elementu członkowskiego, należy użyć programu . **pierwszy** i wyłuskać dolną iterator, użyj \*( `pr`. **po pierwsze**). Aby uzyskać dostęp do drugiego `pr` iteratora pary `pr`zwróconej przez funkcję elementu członkowskiego, należy użyć programu . **drugi** i wyłuskać górną granicę iteratora, użyj \*( `pr`. **drugi**).

### <a name="example"></a>Przykład

```cpp
// hash_multiset_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multiset<int> IntHSet;
   IntHSet hms1;
   hash_multiset <int> :: const_iterator hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hms1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hms1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hms1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hms1.end( ) )
      && ( p2.second == hms1.end( ) ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20
in the hash_multiset hms1 is: 30.
The lower bound of the element with a key of 20
in the hash_multiset hms1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_multiset hms1 doesn't have an element with a key less than 40.
```

## <a name="hash_multiseterase"></a><a name="erase"></a>hash_multiset::wymaż

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Usuwa element lub zakres elementów w hash_multiset z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.

```cpp
iterator erase(iterator where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*Gdzie*\
Położenie elementu, który ma zostać usunięty z hash_multiset.

*Pierwszym*\
Położenie pierwszego elementu usunięte z hash_multiset.

*Ostatnio*\
Umieść tuż za ostatnim elementem usuniętym z hash_multiset.

*Klucz*\
Klucz elementów, które mają zostać usunięte z hash_multiset.

### <a name="return-value"></a>Wartość zwracana

Dla pierwszych dwóch funkcji elementów członkowskich dwukierunkowe iterator, który wyznacza pierwszy element pozostałych poza wszystkie elementy usunięte lub wskaźnik na końcu hash_multiset jeśli taki element nie istnieje. Dla funkcji trzeciego elementu członkowskiego liczba elementów, które zostały usunięte z hash_multiset.

### <a name="remarks"></a>Uwagi

Funkcje członkowskie nigdy nie zgłaszają wyjątku.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie funkcji hash_multiset::erase elementu członkowskiego.

```cpp
// hash_multiset_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1, hms2, hms3;
    hash_multiset<int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multiset<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hms1.insert(i);
        hms2.insert(i * i);
        hms3.insert(i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hms1.begin();
    hms1.erase(Iter1);

    cout << "After the 2nd element is deleted,\n"
         << "the hash_multiset hms1 is:" ;
    for (pIter = hms1.begin(); pIter != hms1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hms2.begin();
    Iter2 = --hms2.end();
    hms2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted,\n"
         << "the hash_multiset hms2 is:" ;
    for (pIter = hms2.begin(); pIter != hms2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hms3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hms3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hms3.begin();
    hms3.erase(Iter1);

    cout << "After another element with a key "
         << "equal to that of the 2nd element\n"
         << "is deleted, the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted,
the hash_multiset hms1 is: 1 3 4.
After the middle two elements are deleted,
the hash_multiset hms2 is: 16 4.
After the element with a key of 2 is deleted,
the hash_multiset hms3 is: 0 1 3.
The number of elements removed from hms3 is: 1.
After another element with a key equal to that of the 2nd element
is deleted, the hash_multiset hms3 is: 0 3.
```

## <a name="hash_multisetfind"></a><a name="find"></a>hash_multiset::znajdź

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator adresowania lokalizacji elementu w hash_multiset, który ma klucz równoważny określony klucz.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz argumentu, który ma być dopasowany przez klucz sortowania elementu z przeszukiwanego hash_multiset.

### <a name="return-value"></a>Wartość zwracana

[Iterator](#iterator) lub [const_iterator,](#const_iterator) który odnosi się do lokalizacji elementu równoważnego określonego klucza lub który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_multiset, jeśli nie zostanie znalezione żadne dopasowanie dla klucza.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iteratora, który odnosi się do `equivalent` elementu w hash_multiset którego klucz sortowania jest klucz argumentu w predykacie binarnym, który wywołuje kolejność na podstawie relacji mniej niż porównywalności.

Jeśli wartość zwracana `find` jest przypisana `const_iterator`do , hash_multiset obiektu nie można zmodyfikować. Jeśli wartość zwracana `find` jest przypisana `iterator`do , hash_multiset obiekt może być modyfikowany.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.find( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // The element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.find( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The element of hash_multiset hms1 with a key of 20 is: 20.
The hash_multiset hms1 doesn't have an element with a key of 40.
The element of hms1 with a key matching that of the last element is: 30.
```

## <a name="hash_multisetget_allocator"></a><a name="get_allocator"></a>hash_multiset::get_allocator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca kopię obiektu alokatora używanego do konstruowania hash_multiset.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez hash_multiset do zarządzania pamięcią, która jest `Allocator`parametrem szablonu klasy .

Aby uzyskać `Allocator`więcej informacji na temat , zobacz uwagi sekcji [hash_multiset class](../standard-library/hash-multiset-class.md) tematu.

### <a name="remarks"></a>Uwagi

Alokatory dla klasy hash_multiset określają sposób zarządzania magazynem przez klasę. Domyślne alokatory dostarczane z klasami kontenerów biblioteki standardowej języka C++ są wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym tematem języka C++.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_multiset <int, hash_compare <int, less<int> > > hms1;
   hash_multiset <int, hash_compare <int, greater<int> > > hms2;
   hash_multiset <double, hash_compare <double,
      less<double> >, allocator<double> > hms3;

   hash_multiset <int, hash_compare <int,
      greater<int> > >::allocator_type hms2_Alloc;
   hash_multiset <double>::allocator_type hms3_Alloc;
   hms2_Alloc = hms2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms3.max_size( ) <<  "." << endl;

   // The following lines create a hash_multiset hms4
   // with the allocator of hash_multiset hms1.
   hash_multiset <int>::allocator_type hms4_Alloc;
   hash_multiset <int> hms4;
   hms4_Alloc = hms2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hms2_Alloc == hms4_Alloc )
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

## <a name="hash_multisethash_multiset"></a><a name="hash_multiset"></a>hash_multiset::hash_multiset

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Konstruuje, `hash_multiset` który jest pusty lub który jest kopią całości lub części innego `hash_multiset`.

```cpp
hash_multiset();

explicit hash_multiset(
    const Traits& Comp);

hash_multiset(
    const Traits& Comp,
    const Allocator& Al);

hash_multiset(
    const hash_multiset<Key, Traits, Allocator>& Right);

hash_multiset(
    hash_multiset&& Right
};
hash_multiset (initializer_list<Type> IList);

hash_multiset(
    initializer_list<Tu[e> IList, const Compare& Comp):
hash_multiset(
    initializer_list<Type> IList, const Compare& Comp, const Allocator& Al);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last,
    const Traits& Comp);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

*Al*\
Klasa alokatora magazynu, która `hash_multiset` ma być używana `Allocator`dla tego obiektu, która domyślnie ma wartość .

*Komp*\
Funkcja porównania typu `const Traits` używanego do zamawiania elementów w `hash_multiset`programie , który domyślnie `hash_compare`ma wartość .

*Prawo*\
Z `hash_multiset` których skonstruowane `hash_multiset` ma być kopią.

*Pierwszym*\
Położenie pierwszego elementu w zakresie elementów do skopiowania.

*Ostatnio*\
Położenie pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

*Ilist*\
initializer_list, który zawiera elementy do skopiowania.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują typ obiektu alokatora, który zarządza magazynem pamięci dla `hash_multiset` i który może być później zwrócony przez wywołanie [hash_multiset::get_allocator](#get_allocator). Parametr alokatora jest często pomijany w deklaracjach klas i przetwarzaniu wstępnym makr używanych do zastępowania alternatywnych alokatorów.

Wszystkie konstruktory inicjują swoje hash_multisets.

Wszystkie konstruktory przechowują `Traits` obiekt funkcji typu, który jest `hash_multiset` używany do ustanowienia kolejności wśród kluczy i które mogą być później zwracane przez wywołanie [hash_multiset::key_comp](#key_comp). Aby uzyskać `Traits` więcej informacji na temat zobacz [hash_multiset temat klasy.](../standard-library/hash-multiset-class.md)

Pierwsze trzy konstruktory `hash_multiset`określają pusty początkowy, drugi określający typ funkcji porównania (*Comp*), która ma być używana do ustalenia kolejności elementów, a trzeci jawnie określający typ alokatora (*Al*), który ma być używany. Słowo kluczowe **jawne** pomija niektóre rodzaje konwersji typu automatycznego.

Czwarty konstruktor `hash_multiset` `Right`przesuwa .

Konstruktory piątego, szóstego i siódmego używają initializer_list.

Ostatnie trzy konstruktory `first`kopiują zakres [ , `last`) `hash_multiset` z coraz większą jawności w określaniu typu funkcji porównania klasy Porównaj i przydzielania.

Rzeczywista kolejność elementów w kontenerze zestawu mieszania zależy od funkcji mieszania, funkcji zamawiania i bieżącego rozmiaru tabeli mieszania i nie można, ogólnie rzecz biorąc, być przewidywane, jak to możliwe z kontenera zestawu, gdzie został określony przez funkcję zamawiania sam.

## <a name="hash_multisetinsert"></a><a name="insert"></a>hash_multiset::wstawianie

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Wstawia element lub zakres elementów do hash_multiset.

```cpp
iterator insert(
    const Type& value);

iterator insert(
    iterator where,
    const Type& Al);

void insert(
    initializer_list<Type> IList);

iterator insert(
    const Type& value);

iterator insert(
    Iterator where,
    const Type& value);

template <class InputIterator>
void insert(
    InputIterator first,
    InputIterator last);

template <class ValTy>
iterator insert(
    ValTy&& value);

template <class ValTy>
iterator insert(
    const_iterator where,
    ValTy&& value);
```

### <a name="parameters"></a>Parametry

*Wartość*\
Wartość elementu, który ma zostać wstawiony do hash_multiset, chyba że hash_multiset już zawiera ten element lub, bardziej ogólnie, element, którego klucz jest równoważno uporządkowany.

*Gdzie*\
Miejsce, aby rozpocząć wyszukiwanie prawidłowego punktu wstawiania. (Wstawienie może wystąpić w zamortyzowanym czasie stałym, a nie w czasie logarytmicznym, jeśli punkt wstawiania nastąpi natychmiast, *gdzie*.)

*Pierwszym*\
Położenie pierwszego elementu, który ma zostać skopiowany z hash_multiset.

*Ostatnio*\
Pozycja tuż poza ostatnim elementem, który ma zostać skopiowany z hash_multiset.

*Ilist*\
initializer_list, który zawiera elementy do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie funkcje elementu wstawiania zwracają iteratora, który wskazuje pozycję, w której nowy element został wstawiony.

Następne trzy funkcje członkowskie używają initializer_list.

Funkcja trzeciego elementu członkowskiego wstawia sekwencję wartości elementu do hash_multiset odpowiadającego każdemu elementowi `first`adresowanemu przez iteratora w zakresie [ , `last`) określonego hash_multiset.

### <a name="remarks"></a>Uwagi

Wstawienie może wystąpić w zamortyzowanym stałym czasie dla wersji podpowiedzi wstawiania, zamiast czasu logarytmicznego, jeśli punkt wstawiania natychmiast następuje *tam, gdzie*.

## <a name="hash_multisetiterator"></a><a name="iterator"></a>hash_multiset::iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować dowolny element w hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Uwagi

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz [przykład, aby rozpocząć](#begin) przykład jak `iterator`zadeklarować i używać .

## <a name="hash_multisetkey_comp"></a><a name="key_comp"></a>hash_multiset::key_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Pobiera kopię obiektu porównania używanego do zamawiania kluczy w hash_multiset.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca parametr hash_multiset *szablonu Cechy*, który zawiera obiekty funkcji, które są używane do mieszania i uporządkowania elementów kontenera.

Aby uzyskać więcej informacji na temat *cech,* zobacz temat [hash_multiset Klasa.](../standard-library/hash-multiset-class.md)

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję elementu członkowskiego:

`bool operator<(const Key& _xVal, const Key& _yVal);`

który zwraca `_xVal` **true,** jeśli poprzedza `_yVal` i nie jest równa w kolejności sortowania.

Należy zauważyć, że zarówno [key_compare,](#key_compare) jak i [value_compare](#value_compare) są synonimami parametru szablonu *Cechy*. Oba typy są przewidziane dla hash_multiset i hash_multiset klas, gdzie są one identyczne, dla zgodności z klas hash_map i hash_multimap, gdzie są one różne.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > >hms1;
   hash_multiset<int, hash_compare < int, less<int> > >::key_compare kc1
          = hms1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hms1."
        << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hms2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
}
```

## <a name="hash_multisetkey_compare"></a><a name="key_compare"></a>hash_multiset::key_compare

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Typ, który zawiera dwa obiekty funkcji, predykat binarny klasy porównania, które można porównać dwie wartości elementów hash_multiset w celu określenia ich względnej kolejności i predykatu bezemisowego, który skróty elementów.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare`jest synonimem parametru szablonu *Cechy*.

Aby uzyskać więcej informacji na temat *cech,* zobacz temat [hash_multiset Klasa.](../standard-library/hash-multiset-class.md)

Należy zauważyć, że zarówno `key_compare` i value_compare są synonimami parametru szablonu *Cechy*. Oba typy są przewidziane dla hash_set i hash_multiset klas, gdzie są identyczne, dla zgodności z hash_map i hash_multimap klas, gdzie są one różne.

### <a name="example"></a>Przykład

Zobacz przykład [key_comp](#key_comp) na przykład jak zadeklarować i `key_compare`używać .

## <a name="hash_multisetkey_type"></a><a name="key_type"></a>hash_multiset::key_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Typ, który udostępnia obiekt funkcji, który może porównywać klucze sortowania w celu określenia względnej kolejności dwóch elementów w hash_multiset.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type`jest synonimem parametru *szablonu Key*.

Należy zauważyć, że zarówno `key_type` i [value_type](../standard-library/hash-set-class.md#value_type) są synonimami parametru *szablonu Key*. Oba typy są przewidziane dla klas zestawu i wielu zestawów, gdzie są one identyczne, dla zgodności z mapą i multimap klas, gdzie są one różne.

Aby uzyskać więcej informacji na temat *klucza,* zobacz uwagi sekcji [hash_multiset class](../standard-library/hash-multiset-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) na przykład jak zadeklarować `key_type`i używać .

## <a name="hash_multisetlower_bound"></a><a name="lower_bound"></a>hash_multiset::lower_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator do pierwszego elementu w hash_multiset z kluczem, który jest równy lub większy niż określony klucz.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz argumentu, który ma być porównywany z kluczem sortowania elementu z hash_multiset przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

[Iterator](#iterator) lub [const_iterator,](#const_iterator) który odnosi się do lokalizacji pierwszego elementu w hash_multiset z kluczem, który jest równy lub większy niż klucz argumentu lub który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_multiset jeśli nie znaleziono dopasowania dla klucza.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multiset_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main() {
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.lower_bound( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator that addresses the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.lower_bound( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

## <a name="hash_multisetmax_size"></a><a name="max_size"></a>hash_multiset::max_size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca maksymalną długość hash_multiset.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna możliwa długość hash_multiset.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multiset_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::size_type i;

   i = hms1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multiset is " << i << "." << endl;
}
```

## <a name="hash_multisetoperator"></a><a name="op_eq"></a>hash_multiset::operator=

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zastępuje elementy hash_multiset kopią innego hash_multiset.

```cpp
hash_multiset& operator=(const hash_multiset& right);

hash_multiset& operator=(hash_multiset&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Prawo*|[hash_multiset](../standard-library/hash-multiset-class.md) kopiowany do pliku `hash_multiset`.|

### <a name="remarks"></a>Uwagi

Po wymazaniu istniejących elementów `hash_multiset` `operator=` w programie , albo kopiuje `hash_multiset`lub przenosi zawartość w *prawo* do .

### <a name="example"></a>Przykład

```cpp
// hash_multiset_operator_as.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<int> v1, v2, v3;
   hash_multiset<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;
}
```

## <a name="hash_multisetpointer"></a><a name="pointer"></a>hash_multiset::pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Typ, który zapewnia wskaźnik do elementu w hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien służyć do uzyskiwania dostępu do elementów w obiekcie wielosetowym.

## <a name="hash_multisetrbegin"></a><a name="rbegin"></a>hash_multiset::rbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator adresowania pierwszy element w odwróconej hash_multiset.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnej dwukierunkowej iteratora adresowania pierwszego elementu w odwróconej hash_multiset lub adresowania, co było ostatnim elementem w hash_multiset nieodwróconych.

### <a name="remarks"></a>Uwagi

`rbegin`jest używany z odwróconym hash_multiset tak jak [begin](#begin) jest używany z hash_multiset.

Jeśli zwracana `rbegin` wartość jest przypisana `const_reverse_iterator`do , wówczas nie można zmodyfikować hash_multiset obiektu. Jeśli zwracana `rbegin` wartość jest przypisana do `reverse_iterator`, a następnie hash_multiset obiekt może być modyfikowany.

`rbegin`może być używany do iteracji przez hash_multiset do tyłu.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // through a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << endl;

   // A hash_multiset element can be erased by dereferencing to its key
   hms1_rIter = hms1.rbegin( );
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_multiset is "<< *hms1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
The hash_multiset is: 10 20 30
The reversed hash_multiset is: 30 20 10
After the erasure, the first element in the reversed hash_multiset is 20.
```

## <a name="hash_multisetreference"></a><a name="reference"></a>hash_multiset::odwołanie

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Typ, który zawiera odwołanie do elementu przechowywanego w hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multiset_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_multiset can be
   // changed by operating on its (non const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_multiset is now "
        << *hms1.begin() << "." << endl;
}
```

```Output
The first element in the hash_multiset is 10.
The first element in the hash_multiset is now 15.
```

## <a name="hash_multisetrend"></a><a name="rend"></a>hash_multiset::rend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w odwróconym hash_multiset.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnej dwukierunkowej iteratora, który odnosi się do lokalizacji po pomyślnym ostatni element w odwróconej hash_multiset (lokalizacja, która poprzedziła pierwszy element w hash_multiset nieodwrotnych).

### <a name="remarks"></a>Uwagi

`rend`jest używany z odwróconym hash_multiset tak jak [koniec](#end) jest używany z hash_multiset.

Jeśli zwracana `rend` wartość jest przypisana `const_reverse_iterator`do , wówczas nie można zmodyfikować hash_multiset obiektu. Jeśli zwracana `rend` wartość jest przypisana do `reverse_iterator`, a następnie hash_multiset obiekt może być modyfikowany. Wartość zwrócona `rend` przez nie powinny być wyłuskiwane.

`rend`można użyć do sprawdzenia, czy odwrotny iterator osiągnął koniec hash_multiset.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;
   hash_multiset <int>::const_reverse_iterator hms1_crIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << "." << endl;

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_multiset is " << *hms1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
The hash_multiset is: 10 20 30 .
The reversed hash_multiset is: 30 20 10 .
After the erasure, the last element in the reversed hash_multiset is 20.
```

## <a name="hash_multisetreverse_iterator"></a><a name="reverse_iterator"></a>hash_multiset::reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować element w odwróconym hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` służy do iteracji przez hash_multiset w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład [dla rbegin](#rbegin) na przykład jak `reverse_iterator`zadeklarować i używać .

## <a name="hash_multisetsize"></a><a name="size"></a>hash_multiset::size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca liczbę elementów w hash_multiset.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość hash_multiset.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multiset_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: size_type i;

   hms1.insert( 1 );
   i = hms1.size( );
   cout << "The hash_multiset length is " << i << "." << endl;

   hms1.insert( 2 );
   i = hms1.size( );
   cout << "The hash_multiset length is now " << i << "." << endl;
}
```

```Output
The hash_multiset length is 1.
The hash_multiset length is now 2.
```

## <a name="hash_multisetsize_type"></a><a name="size_type"></a>hash_multiset::size_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Niepodpisany typ liczby całkowitej, który może reprezentować liczbę elementów w hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Zobacz przykład [rozmiaru,](#size) aby uzyskać przykład deklarowania i używania`size_type`

## <a name="hash_multisetswap"></a><a name="swap"></a>hash_multiset::swap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Wymienia elementy dwóch hash_multisets.

```cpp
void swap(hash_multiset& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Argument hash_multiset zapewniając elementy, które mają być zamienione z hash_multiset docelowego.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego unieważnia żadnych odwołań, wskaźników lub iteratorów, które wyznaczają elementy w dwóch hash_multisets których elementy są wymieniane.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2, hms3;
   hash_multiset <int>::iterator hms1_Iter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );
   hms2.insert( 100 );
   hms2.insert( 200 );
   hms3.insert( 300 );

   cout << "The original hash_multiset hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hms1.swap( hms2 );

   cout << "After swapping with hms2, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hms1, hms3 );

   cout << "After swapping with hms3, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_multiset hms1 is: 10 20 30.
After swapping with hms2, list hms1 is: 200 100.
After swapping with hms3, list hms1 is: 300.
```

## <a name="hash_multisetupper_bound"></a><a name="upper_bound"></a>hash_multiset::upper_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Zwraca iteratora do pierwszego elementu w hash_multiset z kluczem, który jest większy niż określony klucz.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz argumentu, który ma być porównywany z kluczem sortowania elementu z hash_multiset przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

[Iterator](#iterator) lub [const_iterator,](#const_iterator) który odnosi się do lokalizacji pierwszego elementu w hash_multiset z kluczem większym niż klucz argumentu lub który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_multiset jeśli nie zostanie znalezione żadne dopasowanie dla klucza.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multiset_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "The first element of hash_multiset hms1" << endl
        << "with a key greater than 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element\n"
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key > 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be
   // found by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.begin( );
   hms1_RcIter = hms1.upper_bound( *hms1_AcIter );
   cout << "The first element of hms1 with a key greater than "
        << endl << "that of the initial element of hms1 is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The first element of hash_multiset hms1
with a key greater than 20 is: 30.
The hash_multiset hms1 doesn't have an element
with a key greater than 30.
The first element of hms1 with a key greater than
that of the initial element of hms1 is: 20.
```

## <a name="hash_multisetvalue_comp"></a><a name="value_comp"></a>hash_multiset::value_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Pobiera kopię obiektu porównania używanego do zamawiania wartości elementów w hash_multiset.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca parametr hash_multiset *szablonu Cechy*, który zawiera obiekty funkcji, które są używane do mieszania i zamawiania elementów kontenera.

Aby uzyskać więcej informacji na temat *cech,* zobacz temat [hash_multiset Klasa.](../standard-library/hash-multiset-class.md)

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję elementu członkowskiego:

**operator bool**( **constKey&** `_xVal`, **const Key&_yVal** *);*

który zwraca `_xVal` **true,** jeśli poprzedza `_yVal` i nie jest równa w kolejności sortowania.

Należy zauważyć, że zarówno [key_compare,](#key_compare) jak i [value_compare](#value_compare) są synonimami parametru szablonu *Cechy*. Oba typy są przewidziane dla hash_multiset i hash_multiset klas, gdzie są one identyczne, dla zgodności z klas hash_map i hash_multimap, gdzie są one różne.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > > hms1;
   hash_multiset <int, hash_compare < int, less<int> > >::value_compare
      vc1 = hms1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hms1."
           << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::
           value_compare vc2 = hms2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of hms1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of hms2.
```

## <a name="hash_multisetvalue_compare"></a><a name="value_compare"></a>hash_multiset::value_compare

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Typ, który zawiera dwa obiekty funkcji, predykat binarny klasy porównania, które można porównać dwie wartości elementów hash_multiset w celu określenia ich względnej kolejności i predykatu bezemisowego, który skróty elementów.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Uwagi

`value_compare`jest synonimem parametru szablonu *Cechy*.

Aby uzyskać więcej informacji na temat *cech,* zobacz temat [hash_multiset Klasa.](../standard-library/hash-multiset-class.md)

Należy zauważyć, że zarówno `value_compare` [key_compare,](#key_compare) jak i są synonimami parametru szablonu *Cechy*. Oba typy są przewidziane dla klas zestaw i multiset, gdzie są one identyczne, dla zgodności z mapami klas i multimap, gdzie są one różne.

### <a name="example"></a>Przykład

Zobacz przykład [value_comp](#value_comp) na przykład jak zadeklarować `value_compare`i używać .

## <a name="hash_multisetvalue_type"></a><a name="value_type"></a>hash_multiset::value_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset Klasa](../standard-library/unordered-multiset-class.md).

Typ, który opisuje obiekt przechowywany jako element jako hash_multiset w jego pojemności jako wartość.

```cpp
typedef Key value_type;
```

### <a name="example"></a>Przykład

```cpp
// hash_multiset_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;

   // Declare value_type
   hash_multiset <int> :: value_type hmsvt_Int;

   hmsvt_Int = 10;   // Initialize value_type

   // Declare key_type
   hash_multiset <int> :: key_type hmskt_Int;
   hmskt_Int = 20;             // Initialize key_type

   hms1.insert( hmsvt_Int );         // Insert value into s1
   hms1.insert( hmskt_Int );         // Insert key into s1

   // A hash_multiset accepts key_types or value_types as elements
   cout << "The hash_multiset has elements:";
   for ( hms1_Iter = hms1.begin() ; hms1_Iter != hms1.end( );
         hms1_Iter++)
      cout << " " << *hms1_Iter;
      cout << "." << endl;
}
```

```Output
The hash_multiset has elements: 10 20.
```

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Odwołanie do standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
