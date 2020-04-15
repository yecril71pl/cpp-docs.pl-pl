---
title: hash_set — Klasa
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_set
- hash_set/stdext::hash_set::allocator_type
- hash_set/stdext::hash_set::const_iterator
- hash_set/stdext::hash_set::const_pointer
- hash_set/stdext::hash_set::const_reference
- hash_set/stdext::hash_set::const_reverse_iterator
- hash_set/stdext::hash_set::difference_type
- hash_set/stdext::hash_set::iterator
- hash_set/stdext::hash_set::key_compare
- hash_set/stdext::hash_set::key_type
- hash_set/stdext::hash_set::pointer
- hash_set/stdext::hash_set::reference
- hash_set/stdext::hash_set::reverse_iterator
- hash_set/stdext::hash_set::size_type
- hash_set/stdext::hash_set::value_compare
- hash_set/stdext::hash_set::value_type
- hash_set/stdext::hash_set::begin
- hash_set/stdext::hash_set::cbegin
- hash_set/stdext::hash_set::cend
- hash_set/stdext::hash_set::clear
- hash_set/stdext::hash_set::count
- hash_set/stdext::hash_set::crbegin
- hash_set/stdext::hash_set::crend
- hash_set/stdext::hash_set::emplace
- hash_set/stdext::hash_set::emplace_hint
- hash_set/stdext::hash_set::empty
- hash_set/stdext::hash_set::end
- hash_set/stdext::hash_set::equal_range
- hash_set/stdext::hash_set::erase
- hash_set/stdext::hash_set::find
- hash_set/stdext::hash_set::get_allocator
- hash_set/stdext::hash_set::insert
- hash_set/stdext::hash_set::key_comp
- hash_set/stdext::hash_set::lower_bound
- hash_set/stdext::hash_set::max_size
- hash_set/stdext::hash_set::rbegin
- hash_set/stdext::hash_set::rend
- hash_set/stdext::hash_set::size
- hash_set/stdext::hash_set::swap
- hash_set/stdext::hash_set::upper_bound
- hash_set/stdext::hash_set::value_comp
helpviewer_keywords:
- stdext::hash_set
- stdext::hash_set::allocator_type
- stdext::hash_set::const_iterator
- stdext::hash_set::const_pointer
- stdext::hash_set::const_reference
- stdext::hash_set::const_reverse_iterator
- stdext::hash_set::difference_type
- stdext::hash_set::iterator
- stdext::hash_set::key_compare
- stdext::hash_set::key_type
- stdext::hash_set::pointer
- stdext::hash_set::reference
- stdext::hash_set::reverse_iterator
- stdext::hash_set::size_type
- stdext::hash_set::value_compare
- stdext::hash_set::value_type
- stdext::hash_set::begin
- stdext::hash_set::cbegin
- stdext::hash_set::cend
- stdext::hash_set::clear
- stdext::hash_set::count
- stdext::hash_set::crbegin
- stdext::hash_set::crend
- stdext::hash_set::emplace
- stdext::hash_set::emplace_hint
- stdext::hash_set::empty
- stdext::hash_set::end
- stdext::hash_set::equal_range
- stdext::hash_set::erase
- stdext::hash_set::find
- stdext::hash_set::get_allocator
- stdext::hash_set::insert
- stdext::hash_set::key_comp
- stdext::hash_set::lower_bound
- stdext::hash_set::max_size
- stdext::hash_set::rbegin
- stdext::hash_set::rend
- stdext::hash_set::size
- stdext::hash_set::swap
- stdext::hash_set::upper_bound
- stdext::hash_set::value_comp
ms.assetid: c765c06e-cbb6-48c2-93ca-d15468eb28d7
ms.openlocfilehash: 3bf4065b4c409e1baad3183cc8ccbd8c97d43d5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370599"
---
# <a name="hash_set-class"></a>hash_set — Klasa

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Klasa kontenera hash_set jest rozszerzeniem standardowej biblioteki języka C++ i jest używana do przechowywania i szybkiego pobierania danych z kolekcji, w której wartości zawartych elementów są unikatowe i służą jako wartości klucza.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<Key>>
class hash_set
```

### <a name="parameters"></a>Parametry

*Klucz*\
Typ danych elementu, który ma być przechowywany w hash_set.

*Cechy*\
Typ, który zawiera dwa obiekty funkcji, jeden z klasy porównania, który jest binarnym predykatem w stanie porównać dwie wartości elementu jako klucze sortowania w celu określenia `size_t`ich względnej kolejności i funkcję mieszania, która jest jednoarowym odwzorowaniem mapowania wartości klucza elementów do niepodpisanych liczb całkowitych typu . Ten argument jest opcjonalny i `hash_compare<Key, less<Key> >` jest wartością domyślną.

*Programu przydzielania*\
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji hash_set i alokacji pamięci. Ten argument jest opcjonalny, `allocator<Key>`a wartością domyślną jest .

## <a name="remarks"></a>Uwagi

hash_set jest:

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza. Ponadto, jest prostym kontenerem asocjacyjnym, ponieważ jego wartości elementu są jego wartościami klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.

- Hashed, ponieważ jego elementy są pogrupowane w zasobnikach na podstawie wartości funkcji mieszania stosowane do wartości klucza elementów.

- Unikatowy w tym sensie, że każdy z jego elementów musi mieć unikatowy klucz. Ponieważ hash_set jest również prostym kontenerem zespolowym, jego elementy są również unikatowe.

- Szablon klasy, ponieważ funkcje, które zapewnia, jest ogólny i tak niezależne od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Główną zaletą mieszania nad sortowanie jest większa wydajność; pomyślne mieszanie wykonuje wstawienia, usunięcia i znajduje w stałym średnim czasie w porównaniu z czasem proporcjonalnym do logarytmu liczby elementów w kontenerze dla technik sortowania. Nie można bezpośrednio zmienić wartości elementu w zestawie. Zamiast tego musisz usunąć stare wartości i wstawić elementy z nowymi wartościami.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Haszowane kontenery zespolone są zoptymalizowane pod kątem operacji wyszukiwania, wstawiania i usuwania. Funkcje członkowskie, które jawnie obsługują te operacje są wydajne, gdy są używane z dobrze zaprojektowaną funkcją mieszania, wykonując je w czasie, który jest średnio stały i nie zależy od liczby elementów w kontenerze. Dobrze zaprojektowana funkcja mieszania tworzy jednolity rozkład wartości skrótu i minimalizuje liczbę kolizji, gdzie mówi się, że kolizja występuje, gdy różne wartości klucza są mapowane na tę samą wartość skrótu. W najgorszym przypadku z najgorszą możliwą funkcją mieszania liczba operacji jest proporcjonalna do liczby elementów w sekwencji (czas liniowy).

hash_set powinny być kontenerem zespolonego z wyboru, gdy warunki kojarzenia wartości z ich klucze są spełnione przez aplikację. Elementy hash_set są unikatowe i służą jako własne klucze sortowania. Model dla tego typu konstrukcji jest uporządkowaną listą, np. wyrazów, w których wyrazy mogą występować tylko raz. Jeśli wiele wystąpień wyrazów były dozwolone, a następnie hash_multiset będzie odpowiedniej struktury kontenera. Jeśli wartości muszą być dołączone do listy unikatowych słów kluczowych, hash_map będzie odpowiednią strukturą zawierającą te dane. Jeśli zamiast tego klucze nie są unikatowe, a następnie hash_multimap będzie kontenera z wyboru.

Hash_set porządkuuje sekwencję, jaką kontroluje, wywołując `Traits` przechowywany obiekt mieszania typu [value_compare](#value_compare). Ten przechowywany obiekt może być dostępny, wywołując funkcję elementu członkowskiego [key_comp](#key_comp). Taki obiekt funkcji musi zachowywać się tak samo jak obiekt klasy *hash_compare<Key, mniej\<Key> >.* W szczególności dla `key` wszystkich wartości typu Key wywołanie Trait(`key`) daje rozkład wartości typu size_t.

Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Powoduje to kolejność między elementami nieekwidującymi. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarny *f*( *x*, *y*) jest obiektem funkcyjnym, który ma dwa obiekty argumentów x i y oraz zwracaną wartość true lub false. Kolejność nałożona na hash_set jest ścisłym słabym porządkiem, jeśli predykat binarny jest niereflexive, antysymetryczny i przechodni, a jeśli równoważność jest przechodnia, gdzie dwa obiekty *x* i y są zdefiniowane jako *równoważne,* gdy zarówno *f*( *x*, *y*) i *f*( *y*, *x*) są fałszywe. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

Rzeczywista kolejność elementów w kontrolowanej sekwencji zależy od funkcji mieszania, funkcji zamawiania i bieżącego rozmiaru tabeli mieszania przechowywanej w obiekcie kontenera. Nie można określić bieżący rozmiar tabeli mieszania, więc nie można ogólnie przewidzieć kolejność elementów w kontrolowanej sekwencji. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Iterator dostarczony przez klasę hash_set jest dwukierunkowym iteratorem, ale funkcje członkowskie klasy [wstawiają](#insert) i [hash_set](#hash_set) mają wersje, które przyjmują jako parametry szablonu słabszy iterator wejściowy, którego wymagania dotyczące funkcjonalności są bardziej minimalne niż wymagania gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcji, ale wystarczy, aby móc mówić sensownie o zakresie `first`iteratorów [ , `last`) w kontekście funkcji elementu członkowskiego klasy.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Hash_set](#hash_set)|Konstruuje, `hash_set` który jest pusty lub który jest kopią całości lub części innego `hash_set`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który `allocator` reprezentuje klasę `hash_set` dla obiektu.|
|[const_iterator](#const_iterator)|Typ, który zapewnia dwukierunkowy iterator, `const` który może `hash_set`odczytać element w .|
|[const_pointer](#const_pointer)|Typ, który zapewnia wskaźnik do **const** elementu w `hash_set`.|
|[const_reference](#const_reference)|Typ, który zapewnia odwołanie do **const** `hash_set` element przechowywane w do odczytu i wykonywania operacji **const.**|
|[Const_reverse_iterator](#const_reverse_iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytać `hash_set`dowolny element **const** w .|
|[difference_type](#difference_type)|Typ liczby całkowitej podpisana, który może służyć do `hash_set` reprezentowania liczby elementów w zakresie między elementami wskazanymi przez iteratory.|
|[Sterująca](#iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować dowolny element w . `hash_set`|
|[key_compare](#key_compare)|Typ, który udostępnia obiekt funkcji, który może porównać dwa klucze `hash_set`sortowania, aby określić względną kolejność dwóch elementów w programie .|
|[Key_type](#key_type)|Typ, który opisuje obiekt przechowywany jako `hash_set` element w jego pojemności jako klucz sortowania.|
|[pointer](#pointer)|Typ, który zapewnia wskaźnik do `hash_set`elementu w .|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu `hash_set`przechowywanego w .|
|[Reverse_iterator](#reverse_iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować element w odwróconym `hash_set`.|
|[size_type](#size_type)|Niepodpisany typ liczby całkowitej, który może `hash_set`reprezentować liczbę elementów w programie .|
|[Value_compare](#value_compare)|Typ, który zawiera dwa obiekty funkcji, predykat binarny klasy `hash_set` porównania, które można porównać dwie wartości elementu a, aby określić ich względnej kolejności i predykatu unary, który skróty elementów.|
|[value_type](#value_type)|Typ, który opisuje obiekt przechowywany jako `hash_set` element w jego pojemności jako wartość.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Rozpocząć](#begin)|Zwraca iterator, który odnosi się `hash_set`do pierwszego elementu w .|
|[cbegin ( cbegin )](#cbegin)|Zwraca iterator const adresowania pierwszego `hash_set`elementu w .|
|[cend](#cend)|Zwraca iterator const, który odnosi się do `hash_set`lokalizacji, która po pomyślnym ostatnim elemencie w pliku .|
|[Wyczyść](#clear)|Usuwa wszystkie elementy pliku `hash_set`.|
|[Liczba](#count)|Zwraca liczbę elementów, `hash_set` w których klucz pasuje do klucza określonego przez parametr.|
|[Crbegin](#crbegin)|Zwraca iterator const adresowania pierwszego elementu `hash_set`w odwróconym .|
|[Crend](#crend)|Zwraca iterator const, który odnosi się do lokalizacji, która po pomyślnym ostatnim elemencie w odwróconym `hash_set`.|
|[miejsce](#emplace)|Wstawia element skonstruowany w `hash_set`miejscu do .|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w `hash_set`miejscu do , z wskazówką położenia.|
|[Pusty](#empty)|Sprawdza, `hash_set` czy a jest pusty.|
|[Końcu](#end)|Zwraca iterator, który odnosi się do lokalizacji, która po pomyślnym ostatnim elemencie w pliku `hash_set`.|
|[equal_range](#equal_range)|Zwraca parę iteratorów odpowiednio do pierwszego elementu `hash_set` w kluczu, który jest większy niż określony `hash_set` klucz i do pierwszego elementu w kluczu, który jest równy lub większy niż klucz.|
|[Wymazać](#erase)|Usuwa element lub zakres elementów `hash_set` w określonym położeniu lub usuwa elementy, które pasują do określonego klucza.|
|[find](#find)|Zwraca iterator adresowania lokalizacji elementu w, `hash_set` który ma klucz równoważny określony klucz.|
|[Get_allocator](#get_allocator)|Zwraca kopię `allocator` obiektu używanego do `hash_set`konstruowania pliku .|
|[Wstawić](#insert)|Wstawia element lub zakres elementów do pliku `hash_set`.|
|[Key_comp](#key_comp)|Pobiera kopię obiektu porównania używanego do zamawiania kluczy w pliku `hash_set`.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu `hash_set` w kluczu, który jest równy lub większy niż określony klucz.|
|[Max_size](#max_size)|Zwraca maksymalną długość `hash_set`pliku .|
|[rbegin (rbegin)](#rbegin)|Zwraca iteratora adresującego pierwszy element `hash_set`w odwróconym .|
|[Rend](#rend)|Zwraca iterator, który odnosi się do lokalizacji, `hash_set`która zastępuje ostatni element w odwróconym .|
|[Rozmiar](#size)|Zwraca liczbę elementów `hash_set`w pliku .|
|[Wymiany](#swap)|Wymienia elementy dwóch `hash_set`s.|
|[upper_bound](#upper_bound)|Zwraca iterator do pierwszego elementu `hash_set` w kluczu, który jest równy lub większy niż określony klucz.|
|[value_comp](#value_comp)|Pobiera kopię obiektu cech mieszania używanego do mieszania i kolejności `hash_set`wartości klucza elementu w pliku .|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[hash_set::operator=](#op_eq)|Zastępuje elementy a `hash_set` kopią innego `hash_set`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_set>

**Obszar nazw:** stdext

## <a name="hash_setallocator_type"></a><a name="allocator_type"></a>hash_set::allocator_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Typ reprezentujący klasę alokatora dla hash_set obiektu.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type`jest synonimem parametru szablonu *Alokator .*

Aby uzyskać więcej informacji na temat *alokatora,* zobacz uwagi sekcji [hash_set class](../standard-library/hash-set-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [get_allocator](#get_allocator) na przykład, który `allocator_type`używa .

## <a name="hash_setbegin"></a><a name="begin"></a>hash_set::begin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca iterator, który odnosi się do pierwszego elementu w hash_set.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator adresowania pierwszy element w hash_set lub lokalizacji po wystąpieniu pustego hash_set.

### <a name="remarks"></a>Uwagi

Jeśli zwracana `begin` wartość jest przypisana `const_iterator`do , elementy w hash_set obiektu nie można modyfikować. Jeśli zwracana `begin` wartość jest przypisana `iterator`do , elementy w hash_set obiektu mogą być modyfikowane.

### <a name="example"></a>Przykład

```cpp
// hash_set_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.begin( );
   cout << "The first element of hs1 is " << *hs1_Iter << endl;

   hs1_Iter = hs1.begin( );
   hs1.erase( hs1_Iter );

   // The following 2 lines would err because the iterator is const
   // hs1_cIter = hs1.begin( );
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.begin( );
   cout << "The first element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
The first element of hs1 is now 2
```

## <a name="hash_setcbegin"></a><a name="cbegin"></a>hash_set::cbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca iterator const, który odnosi się do pierwszego elementu w hash_set.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator const adresujący pierwszy element w [hash_set](../standard-library/hash-set-class.md) lub lokalizację, która `hash_set`zastępuje pusty plik .

### <a name="remarks"></a>Uwagi

Z wartością `cbegin`zwracaną , `hash_set` elementy w obiekcie nie mogą być modyfikowane.

### <a name="example"></a>Przykład

```cpp
// hash_set_cbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_iterator hs1_cIter;

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

## <a name="hash_setcend"></a><a name="cend"></a>hash_set::cend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca iterator const, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_set.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator konspiracyjny, który odnosi się do lokalizacji, która zastępuje ostatni element w [hash_set](../standard-library/hash-set-class.md). Jeśli `hash_set` jest pusty, `hash_set::cend == hash_set::begin`a następnie .

### <a name="remarks"></a>Uwagi

`cend`służy do sprawdzenia, czy iterator osiągnął `hash_set`koniec jego . Wartość zwrócona `cend` przez nie powinny być wyłuskiwane.

### <a name="example"></a>Przykład

```cpp
// hash_set_cend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_cIter;

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

## <a name="hash_setclear"></a><a name="clear"></a>hash_set::wyczyść

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Usuwa wszystkie elementy hash_set.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_set_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 1 );
   hs1.insert( 2 );

   cout << "The size of the hash_set is initially " << hs1.size( )
        << "." << endl;

   hs1.clear( );
   cout << "The size of the hash_set after clearing is "
        << hs1.size( ) << "." << endl;
}
```

```Output
The size of the hash_set is initially 2.
The size of the hash_set after clearing is 0.
```

## <a name="hash_setconst_iterator"></a><a name="const_iterator"></a>hash_set::const_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Typ, który zapewnia dwukierunkowe iteratora, który można odczytać **const** element w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz [przykład, aby rozpocząć](#begin) przykład, który używa `const_iterator`.

## <a name="hash_setconst_pointer"></a><a name="const_pointer"></a>hash_set::const_pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Typ, który zapewnia wskaźnik do **const** elementu w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

W większości przypadków [const_iterator](#const_iterator) powinien służyć do uzyskiwania dostępu do elementów w **const** hash_set obiektu.

## <a name="hash_setconst_reference"></a><a name="const_reference"></a>hash_set::const_reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Typ, który zapewnia odwołanie do **const** element przechowywane w hash_set do odczytu i wykonywania operacji **const.**

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_set_const_ref.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_set is 10.
```

## <a name="hash_setconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>hash_set::const_reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Typ, który zapewnia dwukierunkowy iterator, który może odczytać dowolny element **const** w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartość elementu i jest używany do iteracji za pośrednictwem hash_set w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład [rend](#rend) na przykład, jak zadeklarować i użyć`const_reverse_iterator`

## <a name="hash_setcount"></a><a name="count"></a>hash_set::count

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca liczbę elementów w hash_set którego klucz odpowiada kluczowi określonej parametru.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz elementów, które mają być dopasowane z hash_set.

### <a name="return-value"></a>Wartość zwracana

1, jeśli hash_set zawiera element, którego klucz sortowania pasuje do klucza parametru.

0, jeśli hash_set nie zawiera elementu z pasującym kluczem.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca liczbę elementów w następującym zakresie:

\[lower_bound(*klucz*), upper_bound(*klucz*) ).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie funkcji elementu członkowskiego hash_set::count.

```cpp
// hash_set_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1;
    hash_set<int>::size_type i;

    hs1.insert(1);
    hs1.insert(1);

    // Keys must be unique in hash_set, so duplicates are ignored.
    i = hs1.count(1);
    cout << "The number of elements in hs1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hs1.count(2);
    cout << "The number of elements in hs1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hs1 with a sort key of 1 is: 1.
The number of elements in hs1 with a sort key of 2 is: 0.
```

## <a name="hash_setcrbegin"></a><a name="crbegin"></a>hash_set::crbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca iterator konstacyjny adresowania pierwszy element w odwróconej hash_set.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Const odwrotnej dwukierunkowej iteratora adresowania pierwszego elementu w odwróconej [hash_set](../standard-library/hash-set-class.md) lub adresowania, co `hash_set`było ostatnim elementem w nieodwrotowej .

### <a name="remarks"></a>Uwagi

`crbegin`jest używany z odwróconym hash_set tak jak [hash_set::begin](#begin) jest używany z hash_set.

Z wartością `crbegin`zwracaną `hash_set` obiektu nie można modyfikować obiektu.

`crbegin`może być używany do iteracji do `hash_set` tyłu.

### <a name="example"></a>Przykład

```cpp
// hash_set_crbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
```

## <a name="hash_setcrend"></a><a name="crend"></a>hash_set::crend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca iterator const, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w odwróconym hash_set.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Const odwrotnej dwukierunkowej iteratora, który odnosi się do lokalizacji po ostatniej pozycji elementu w odwróconym [hash_set](../standard-library/hash-set-class.md) (lokalizacja, która poprzedziła pierwszy element w nieodwrotzony). `hash_set`

### <a name="remarks"></a>Uwagi

`crend`jest używany z `hash_set` odwróconym tak samo, jak [hash_set::end](#end) jest używany z . `hash_set`

Z wartością `crend`zwracaną `hash_set` obiektu nie można modyfikować obiektu.

`crend`można użyć do sprawdzenia, czy iterator odwrotny `hash_set`osiągnął koniec jego .

### <a name="example"></a>Przykład

```cpp
// hash_set_crend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
```

## <a name="hash_setdifference_type"></a><a name="difference_type"></a>hash_set::d00_typ

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Typ liczby całkowitej podpisana, który może służyć do reprezentowania liczby elementów hash_set w zakresie między elementami wskazywane przez iteratory.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Jest `difference_type` to typ zwracany podczas odejmowania lub zwiększania za pośrednictwem iteratorów kontenera. Jest `difference_type` zazwyczaj używany do reprezentowania liczby elementów `first` `last`w zakresie [ , `first` `last`) między iteratorów i , zawiera element wskazany przez `first` i `last`zakres elementów do, ale nie w tym element wskazany przez .

Należy zauważyć, że chociaż `difference_type` jest dostępny dla wszystkich iteratorów, które spełniają wymagania iteratora wejściowego, który obejmuje klasę dwukierunkowych iteratorów obsługiwanych przez odwracalne kontenery, takie jak zestaw, odejmowanie między iteratorami jest obsługiwane tylko przez iteratory dostępu losowego dostarczane przez kontener dostępu losowego, takie jak wektor lub deque.

### <a name="example"></a>Przykład

```cpp
// hash_set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter, hs1_bIter, hs1_eIter;

   hs1.insert( 20 );
   hs1.insert( 10 );
   hs1.insert( 20 );   // Won't insert as hash_set elements are unique

   hs1_bIter = hs1.begin( );
   hs1_eIter = hs1.end( );

   hash_set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( hs1_bIter, hs1_eIter, 5 );
   df_typ10 = count( hs1_bIter, hs1_eIter, 10 );
   df_typ20 = count( hs1_bIter, hs1_eIter, 20 );

   // The keys, and hence the elements, of a hash_set are unique,
   // so there is at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_set hs1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_set hs1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_set hs1.\n";

   // Count the number of elements in a hash_set
   hash_set <int>::difference_type  df_count = 0;
   hs1_Iter = hs1.begin( );
   while ( hs1_Iter != hs1_eIter)
   {
      df_count++;
      hs1_Iter++;
   }

   cout << "The number of elements in the hash_set hs1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_set hs1.
The number '10' occurs 1 times in hash_set hs1.
The number '20' occurs 1 times in hash_set hs1.
The number of elements in the hash_set hs1 is: 2.
```

## <a name="hash_setemplace"></a><a name="emplace"></a>hash_set::miejsce

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Wstawia element skonstruowany w miejscu do hash_set.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Wartość elementu, który ma zostać wstawiony do `hash_set` [hash_set,](../standard-library/hash-set-class.md) chyba że już zawiera ten element lub, bardziej ogólnie, element, którego klucz jest równoważno uporządkowany.|

### <a name="return-value"></a>Wartość zwracana

Funkcja `emplace` elementu członkowskiego zwraca parę, której składnik **bool** zwraca wartość `hash_set` **true,** jeśli wstawianie zostało wprowadzone i **false,** jeśli już zawierał element, którego klucz miał równoważną wartość w kolejności i którego składnik iterator zwraca adres, w którym nowy element został wstawiony lub gdzie element został już zlokalizowany.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_set_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.emplace(move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="hash_setemplace_hint"></a><a name="emplace_hint"></a>hash_set::emplace_hint

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Wstawia element skonstruowany w miejscu do hash_set.

```cpp
template <class ValTy>
iterator emplace(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Wartość elementu, który ma zostać wstawiony do `hash_set` [hash_set,](../standard-library/hash-set-class.md) chyba że już zawiera ten element lub, bardziej ogólnie, element, którego klucz jest równoważno uporządkowany.|
|*_where*|Miejsce, aby rozpocząć wyszukiwanie prawidłowego punktu wstawiania. (Wstawienie może wystąpić w zamortyzowanym czasie stałym, a nie w czasie logarytmicznym, jeśli punkt wstawiania natychmiast następuje *_Where.)*|

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego [hash_set::emplace](#emplace) zwraca iterator, który wskazuje pozycję, w której `hash_set`nowy element został wstawiony do , lub gdzie znajduje się istniejący element o równoważnej kolejności.

### <a name="remarks"></a>Uwagi

Wstawienie może wystąpić w zamortyzowanym czasie stałym, a nie w czasie logarytmicznym, jeśli punkt wstawiania natychmiast następuje *po _Where*.

### <a name="example"></a>Przykład

```cpp
// hash_set_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.insert(hs3.begin(), move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="hash_setempty"></a><a name="empty"></a>hash_set::empty

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Sprawdza, czy hash_set jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli hash_set jest pusta; **false,** jeśli hash_set jest niepusty.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_set_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2;
   hs1.insert ( 1 );

   if ( hs1.empty( ) )
      cout << "The hash_set hs1 is empty." << endl;
   else
      cout << "The hash_set hs1 is not empty." << endl;

   if ( hs2.empty( ) )
      cout << "The hash_set hs2 is empty." << endl;
   else
      cout << "The hash_set hs2 is not empty." << endl;
}
```

```Output
The hash_set hs1 is not empty.
The hash_set hs2 is empty.
```

## <a name="hash_setend"></a><a name="end"></a>hash_set::end

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca iterator, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_set.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_set. Jeśli hash_set jest pusta, hash_set::end == hash_set::begin.

### <a name="remarks"></a>Uwagi

`end`służy do testowania, czy iterator osiągnął koniec hash_set. Wartość zwrócona `end` przez nie powinny być wyłuskiwane.

### <a name="example"></a>Przykład

```cpp
// hash_set_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: iterator hs1_Iter;
   hash_set <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.end( );
   hs1_Iter--;
   cout << "The last element of hs1 is " << *hs1_Iter << endl;

   hs1.erase( hs1_Iter );

   // The following 3 lines would err because the iterator is const:
   // hs1_cIter = hs1.end( );
   // hs1_cIter--;
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.end( );
   hs1_cIter--;
   cout << "The last element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
The last element of hs1 is now 2
```

## <a name="hash_setequal_range"></a><a name="equal_range"></a>hash_set::equal_range

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca parę iteratorów odpowiednio do pierwszego elementu w zestawie mieszania z kluczem, który jest równy określonemu kluczowi i pierwszemu elementowi w zestawie mieszania z kluczem, który jest większy niż klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz argumentu, który ma być porównywany z kluczem sortowania elementu z przeszukiwanego hash_set.

### <a name="return-value"></a>Wartość zwracana

Para iteratorów, gdzie pierwszy jest [lower_bound](../standard-library/set-class.md#lower_bound) klucza, a drugi jest [upper_bound](../standard-library/set-class.md#upper_bound) klucza.

Aby uzyskać dostęp do pierwszego iteratora pary pr `pr`zwróconej przez funkcję elementu członkowskiego, należy użyć programu . **najpierw**i wyłuskać dolną iterator, użyj \*( `pr`. **po pierwsze**). Aby uzyskać dostęp do drugiego `pr` iteratora pary `pr`zwróconej przez funkcję elementu członkowskiego, należy użyć programu . **po drugie**i wyłuskać górną \*granicę iteratora, użyj ( `pr`. **drugi**).

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_set_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_set<int> IntHSet;
   IntHSet hs1;
   hash_set <int> :: const_iterator hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hs1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hs1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hs1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hs1.end( ) ) && ( p2.second == hs1.end( ) ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than or equal to 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the hash_set hs1 is: 30.
The lower bound of the element with a key of 20 in the hash_set hs1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_set hs1 doesn't have an element with a key greater than or equal to 40.
```

## <a name="hash_seterase"></a><a name="erase"></a>hash_set::wymaż

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Usuwa element lub zakres elementów w hash_set z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_where*\
Położenie elementu, który ma zostać usunięty z hash_set.

*Pierwszym*\
Położenie pierwszego elementu usunięte z hash_set.

*Ostatnio*\
Umieść tuż za ostatnim elementem usuniętym z hash_set.

*Klucz*\
Klucz elementów, które mają zostać usunięte z hash_set.

### <a name="return-value"></a>Wartość zwracana

Dla pierwszych dwóch funkcji elementów członkowskich dwukierunkowe iterator, który wyznacza pierwszy element pozostałych poza wszystkie elementy usunięte lub wskaźnik na końcu hash_set jeśli taki element nie istnieje. Dla funkcji trzeciego elementu członkowskiego liczba elementów, które zostały usunięte z hash_set.

### <a name="remarks"></a>Uwagi

Funkcje członkowskie nigdy nie zgłaszają wyjątku.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie funkcji hash_set::erase element członkowski.

```cpp
// hash_set_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1, hs2, hs3;
    hash_set<int>::iterator pIter, Iter1, Iter2;
    int i;
    hash_set<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hs1.insert (i);
        hs2.insert (i * i);
        hs3.insert (i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hs1.begin();
    hs1.erase(Iter1);

    cout << "After the 2nd element is deleted, the hash_set hs1 is:";
    for (pIter = hs1.begin(); pIter != hs1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hs2.begin();
    Iter2 = --hs2.end();
    hs2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_set hs2 is:";
    for (pIter = hs2.begin(); pIter != hs2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hs3.erase(2);

    cout << "After the element with a key of 2 is deleted, "
         << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hs3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hs3.begin();
    hs3.erase(Iter1);

    cout << "After another element (unique for hash_set) with a key "
         << endl;
    cout  << "equal to that of the 2nd element is deleted, "
          << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_set hs1 is: 1 3 4.
After the middle two elements are deleted, the hash_set hs2 is: 16 4.
After the element with a key of 2 is deleted, the hash_set hs3 is: 0 1 3.
The number of elements removed from hs3 is: 1.
After another element (unique for hash_set) with a key
equal to that of the 2nd element is deleted, the hash_set hs3 is: 0 3.
```

## <a name="hash_setfind"></a><a name="find"></a>hash_set::znajdź

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca iterator adresowania lokalizacji elementu w hash_set, który ma klucz równoważny określony klucz.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz argumentu, który ma być dopasowany przez klucz sortowania elementu z przeszukiwanego hash_set.

### <a name="return-value"></a>Wartość zwracana

Lub `iterator` `const_iterator` który odnosi się do lokalizacji elementu równoważne określonego klucza lub który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_set, jeśli nie znaleziono dopasowania dla klucza.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iteratora, który odnosi się do `equivalent` elementu w hash_set którego klucz sortowania jest klucz argumentu w predykacie binarnym, który wywołuje kolejność na podstawie relacji mniej niż porównywalności.

Jeśli wartość zwracana `find` jest przypisana `const_iterator`do , hash_set obiektu nie można zmodyfikować. Jeśli wartość zwracana `find` jest przypisana `iterator`do , hash_set obiekt może być modyfikowany.

### <a name="example"></a>Przykład

```cpp
// hash_set_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.find( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // The element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.find( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="hash_setget_allocator"></a><a name="get_allocator"></a>hash_set::get_allocator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca kopię obiektu alokatora używanego do konstruowania hash_set.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez hash_set do zarządzania pamięcią, który jest parametrem szablonu *Alokator*.

Aby uzyskać więcej informacji na temat *alokatora,* zobacz uwagi sekcji [hash_set class](../standard-library/hash-set-class.md) tematu.

### <a name="remarks"></a>Uwagi

Alokatory dla klasy hash_set określają sposób zarządzania magazynem przez klasę. Domyślne alokatory dostarczane z klasami kontenerów biblioteki standardowej języka C++ są wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym tematem języka C++.

### <a name="example"></a>Przykład

```cpp
// hash_set_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_set <int, hash_compare <int, less<int> > > hs1;
   hash_set <int,  hash_compare <int, greater<int> > > hs2;
   hash_set <double, hash_compare <double,
      less<double> >, allocator<double> > hs3;

   hash_set <int, hash_compare <int,
      greater<int> > >::allocator_type hs2_Alloc;
   hash_set <double>::allocator_type hs3_Alloc;
   hs2_Alloc = hs2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs3.max_size( ) <<  "." << endl;

   // The following lines create a hash_set hs4
   // with the allocator of hash_set hs1.
   hash_set <int>::allocator_type hs4_Alloc;
   hash_set <int> hs4;
   hs4_Alloc = hs2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hs2_Alloc == hs4_Alloc )
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

## <a name="hash_sethash_set"></a><a name="hash_set"></a>hash_set::hash_set

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Konstruuje, `hash_set` który jest pusty lub który jest kopią całości lub części innego `hash_set`.

```cpp
hash_set();

explicit hash_set(
    const Traits& Comp);

hash_set(
    const Traits& Comp,
    const Allocator& Al);

hash_set(
    const hash_set<Key, Traits, Allocator>& Right);

hash_set(
    hash_set&& Right);

hash_set(
    initializer_list<Type> IList);

hash_set(
    initializer_list<Type> IList,
    const Compare& Comp);

hash_set(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Al*|Klasa alokatora magazynu, która `hash_set` ma być używana `Allocator`dla tego obiektu, która domyślnie ma wartość .|
|*Comp*|Funkcja porównania typu `const Traits` używanego do zamawiania elementów w `hash_set`programie , który domyślnie `hash_compare`ma wartość .|
|*Prawo*|Z `hash_set` których skonstruowane `hash_set` ma być kopią.|
|*Pierwszym*|Położenie pierwszego elementu w zakresie elementów do skopiowania.|
|*Ostatnio*|Położenie pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują typ obiektu alokatora, który zarządza magazynem pamięci dla `hash_set` i który może być później zwrócony przez wywołanie [hash_set::get_allocator](#get_allocator). Parametr alokatora jest często pomijany w deklaracjach klas i przetwarzaniu wstępnym makr używanych do zastępowania alternatywnych alokatorów.

Wszystkie konstruktory inicjują swoje hash_sets.

Wszystkie konstruktory przechowują `Traits` obiekt funkcji typu, który jest `hash_set` używany do ustanowienia kolejności wśród kluczy i które mogą być później zwracane przez wywołanie [hash_set::key_comp](#key_comp). Aby uzyskać `Traits` więcej informacji na temat zobacz [hash_set temat klasy.](../standard-library/hash-set-class.md)

Pierwszy konstruktor tworzy `hash_set` pusty początkowy Drugi określa typ `Comp`funkcji porównania ( ) do użycia w ustalaniu kolejności elementów, a `Al`trzeci jawnie określa typ alokatora ( ) do użycia. Słowo `explicit` kluczowe pomija pewne rodzaje automatycznej konwersji typu.

Konstruktory czwarty i piąty `hash_set` `Right`określają kopię pliku .

Ostatni, siódmy i ósmy konstruktorzy używają initializer_list dla elementów.

Ostatnie konstruktory kopiują zakres [ `First`, `Last`) `hash_set` z coraz większą jawności w określaniu typu funkcji porównania cech klasy i alokatora.

Ósmy konstruktor `hash_set` `Right`przesuwa .

Rzeczywista kolejność elementów `hash_set` w kontenerze zależy od funkcji mieszania, funkcji zamawiania i bieżącego rozmiaru tabeli mieszania i nie można, ogólnie rzecz biorąc, być przewidywane, jak to możliwe z kontenera zestawu, gdzie został określony przez funkcję zamawiania sam.

## <a name="hash_setinsert"></a><a name="insert"></a>hash_set::wstawianie

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Wstawia element lub zakres elementów do pliku `hash_set`.

```cpp
pair<iterator, bool> insert(
    const value_type& Val);

iterator insert(
    iterator Where,
    const value_type& Val);

void insert(
    initializer_list<value_type> IList)
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Wartość elementu, który ma zostać `hash_set` wstawiony do chyba że `hash_set` już zawiera ten element lub, bardziej ogólnie, element, którego klucz jest równoważno uporządkowany.|
|*Gdzie*|Miejsce, aby rozpocząć wyszukiwanie prawidłowego punktu wstawiania. (Wstawienie może wystąpić w zamortyzowanym czasie stałym, a nie w `_Where`czasie logarytmicznym, jeśli punkt wstawiania natychmiast następuje.)|
|*Pierwszym*|Położenie pierwszego elementu, który ma zostać `hash_set`skopiowany z pliku .|
|*Ostatnio*|Pozycja tuż za ostatnim elementem, który `hash_set`ma zostać skopiowany z pliku .|
|*Ilist*|Lista initializer_list, z której mają być skopiowane elementy.|

### <a name="return-value"></a>Wartość zwracana

Funkcja `insert` pierwszego elementu członkowskiego zwraca parę, której składnik **bool** zwraca wartość `hash_set` **true,** jeśli wstawianie zostało wprowadzone i **false,** jeśli już zawierał element, którego klucz miał równoważną wartość w kolejności i którego składnik iterator zwraca adres, w którym nowy element został wstawiony lub gdzie element został już zlokalizowany.

Aby uzyskać dostęp do składnika `pr` iteratora pary `pr.first` zwróconej przez tę `*(pr.first)`funkcję elementu członkowskiego, użyj i wyłudź go, użyj . Aby uzyskać dostęp do składnika **bool** pary `pr` `pr.second`zwróconej przez tę funkcję `*(pr.second)`elementu członkowskiego, użyj i wyłudził ją, użyj .

Druga `insert` funkcja elementu członkowskiego zwraca iterator, który wskazuje na pozycję, `hash_set`w której nowy element został wstawiony do .

### <a name="remarks"></a>Uwagi

Funkcja trzeciego elementu członkowskiego wstawia elementy w initializer_list.

Funkcja `hash_set` trzeciego elementu członkowskiego wstawia sekwencję wartości elementu do odpowiadającego każdemu elementowi `First` `Last`adresowanemu `hash_set`przez iteratora w zakresie [ , ) określonego .

## <a name="hash_setiterator"></a><a name="iterator"></a>hash_set::iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować dowolny element w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Uwagi

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz [przykład, aby rozpocząć](#begin) przykład jak zadeklarować i używać `iterator`.

## <a name="hash_setkey_comp"></a><a name="key_comp"></a>hash_set::key_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Pobiera kopię obiektu cech mieszania używanego do mieszania i kolejności wartości klucza elementu w hash_set.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji używany przez hash_set do uporządkowania swoich elementów, który jest parametrem szablonu *Traits*.

Aby uzyskać więcej informacji na temat *cech,* zobacz temat [hash_set Klasa.](../standard-library/hash-set-class.md)

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję elementu członkowskiego:

`bool operator( const Key& _xVal, const Key& _yVal );`

który zwraca `_xVal` **true,** jeśli poprzedza `_yVal` i nie jest równa w kolejności sortowania.

Należy zauważyć, że zarówno [key_compare,](#key_compare) jak i [value_compare](#value_compare) są synonimami parametru szablonu *Cechy*. Oba typy są przewidziane dla hash_set i hash_multiset klas, gdzie są identyczne, dla zgodności z hash_map i hash_multimap klas, gdzie są one różne.

### <a name="example"></a>Przykład

```cpp
// hash_set_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > >hs1;
   hash_set<int, hash_compare < int, less<int> > >::key_compare kc1
          = hs1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hs1."
        << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hs2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="hash_setkey_compare"></a><a name="key_compare"></a>hash_set::key_compare

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Typ, który udostępnia obiekt funkcji, który można porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w hash_set.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare`jest synonimem parametru szablonu *Cechy*.

Aby uzyskać więcej informacji na temat *cech,* zobacz temat [hash_set Klasa.](../standard-library/hash-set-class.md)

Należy zauważyć, że zarówno `key_compare` i [value_compare](#value_compare) są synonimami parametru szablonu *Cechy*. Oba typy są przewidziane dla klas zestawu i wielu zestawów, gdzie są one identyczne, dla zgodności z mapą i multimap klas, gdzie są one różne.

### <a name="example"></a>Przykład

Zobacz przykład [key_comp](#key_comp) na przykład jak zadeklarować i `key_compare`używać .

## <a name="hash_setkey_type"></a><a name="key_type"></a>hash_set::key_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Typ, który opisuje obiekt przechowywany jako element hash_set w jego pojemności jako klucz sortowania.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type`jest synonimem parametru *szablonu Key*.

Aby uzyskać więcej informacji na temat *klucza,* zobacz uwagi sekcji [hash_set class](../standard-library/hash-set-class.md) tematu.

Należy zauważyć, że zarówno `key_type` i [value_type](#value_type) są synonimami parametru *szablonu Key*. Oba typy są przewidziane dla hash_set i hash_multiset klas, gdzie są identyczne, dla zgodności z hash_map i hash_multimap klas, gdzie są one różne.

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) na przykład jak zadeklarować i `key_type`używać .

## <a name="hash_setlower_bound"></a><a name="lower_bound"></a>hash_set::lower_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca iteratora do pierwszego elementu w hash_set z kluczem, który jest równy lub większy niż określony klucz.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz argumentu, który ma być porównywany z kluczem sortowania elementu z przeszukiwanego hash_set.

### <a name="return-value"></a>Wartość zwracana

Lub `iterator` `const_iterator` który odnosi się do lokalizacji elementu w hash_set, który z kluczem, który jest równy lub większy niż klucz argumentu lub który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_set jeśli nie znaleziono dopasowania dla klucza.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_set_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.lower_bound( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator that addresses the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.lower_bound( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="hash_setmax_size"></a><a name="max_size"></a>hash_set::max_size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca maksymalną długość hash_set.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna możliwa długość hash_set.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_set_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::size_type i;

   i = hs1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_set is " << i << "." << endl;
}
```

## <a name="hash_setoperator"></a><a name="op_eq"></a>hash_set::operator=

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zastępuje elementy hash_set kopią innego hash_set.

```cpp
hash_set& operator=(const hash_set& right);

hash_set& operator=(hash_set&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Prawo*|[hash_set](../standard-library/hash-set-class.md) kopiowane do pliku `hash_set`.|

### <a name="remarks"></a>Uwagi

Po wymazaniu istniejących elementów `hash_set` `operator=` w programie , albo kopiuje `hash_set`lub przenosi zawartość w *prawo* do .

### <a name="example"></a>Przykład

```cpp
// hash_set_operator_as.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<int> v1, v2, v3;
   hash_set<int>::iterator iter;

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

## <a name="hash_setpointer"></a><a name="pointer"></a>hash_set::pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Typ, który zapewnia wskaźnik do elementu w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien służyć do uzyskiwania dostępu do elementów w hash_set obiektu.

## <a name="hash_setrbegin"></a><a name="rbegin"></a>hash_set::rbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca iterator adresowania pierwszy element w odwróconej hash_set.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnej dwukierunkowej iteratora adresowania pierwszego elementu w odwróconej hash_set lub adresowania, co było ostatnim elementem w hash_set nieodwróconych.

### <a name="remarks"></a>Uwagi

`rbegin`jest używany z odwróconym hash_set tak jak [begin](#begin) jest używany z hash_set.

Jeśli zwracana `rbegin` wartość jest przypisana `const_reverse_iterator`do , a następnie hash_set obiektu nie można zmodyfikować. Jeśli zwracana `rbegin` wartość jest przypisana `reverse_iterator`do , a następnie hash_set obiekt może być modyfikowany.

`rbegin`może być używany do iteracji przez hash_set do tyłu.

### <a name="example"></a>Przykład

```cpp
// hash_set_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // through a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << endl;

   // A hash_set element can be erased by dereferencing to its key
   hs1_rIter = hs1.rbegin( );
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_set is "<< *hs1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
The hash_set is: 10 20 30
The reversed hash_set is: 30 20 10
After the erasure, the first element in the reversed hash_set is 20.
```

## <a name="hash_setreference"></a><a name="reference"></a>hash_set::odwołanie

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Typ, który zawiera odwołanie do elementu przechowywanego w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_set_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_set can be changed
   // by operating on its (non-const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_set is now "
        << *hs1.begin() << "." << endl;
}
```

```Output
The first element in the hash_set is 10.
The first element in the hash_set is now 15.
```

## <a name="hash_setrend"></a><a name="rend"></a>hash_set::rend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca iterator, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w odwróconym hash_set.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnej dwukierunkowej iteratora, który odnosi się do lokalizacji po pomyślnym ostatni element w odwróconej hash_set (lokalizacja, która poprzedziła pierwszy element w hash_set nieodwrotnych).

### <a name="remarks"></a>Uwagi

`rend`jest używany z odwróconym hash_set tak jak [koniec](#end) jest używany z hash_set.

Jeśli zwracana `rend` wartość jest przypisana `const_reverse_iterator`do , a następnie hash_set obiektu nie można zmodyfikować. Jeśli zwracana `rend` wartość jest przypisana `reverse_iterator`do , a następnie hash_set obiekt może być modyfikowany. Wartość zwrócona `rend` przez nie powinny być wyłuskiwane.

`rend`można użyć do sprawdzenia, czy odwrotny iterator osiągnął koniec hash_set.

### <a name="example"></a>Przykład

```cpp
// hash_set_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << "." << endl;

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_set is " << *hs1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
The hash_set is: 10 20 30 .
The reversed hash_set is: 30 20 10 .
After the erasure, the last element in the reversed hash_set is 20.
```

## <a name="hash_setreverse_iterator"></a><a name="reverse_iterator"></a>hash_set::reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować element w odwróconym hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` służy do iteracji przez hash_set w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład [dla rbegin](#rbegin) na przykład jak `reverse_iterator`zadeklarować i używać .

## <a name="hash_setsize"></a><a name="size"></a>hash_set::size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca liczbę elementów w hash_set.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość hash_set.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_set_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: size_type i;

   hs1.insert( 1 );
   i = hs1.size( );
   cout << "The hash_set length is " << i << "." << endl;

   hs1.insert( 2 );
   i = hs1.size( );
   cout << "The hash_set length is now " << i << "." << endl;
}
```

```Output
The hash_set length is 1.
The hash_set length is now 2.
```

## <a name="hash_setsize_type"></a><a name="size_type"></a>hash_set::size_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Niepodpisany typ liczby całkowitej, który może reprezentować liczbę elementów w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Zobacz przykład [rozmiaru,](#size) aby uzyskać przykład deklarowania i używania`size_type`

## <a name="hash_setswap"></a><a name="swap"></a>hash_set::swap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Wymienia elementy dwóch hash_sets.

```cpp
void swap(hash_set& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Argument hash_set zapewniając elementy, które mają być zamienione z hash_set docelowego.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego unieważnia żadnych odwołań, wskaźników lub iteratorów, które wyznaczają elementy w dwóch hash_sets których elementy są wymieniane.

### <a name="example"></a>Przykład

```cpp
// hash_set_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   hash_set <int>::iterator hs1_Iter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );
   hs2.insert( 100 );
   hs2.insert( 200 );
   hs3.insert( 300 );

   cout << "The original hash_set hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hs1.swap( hs2 );

   cout << "After swapping with hs2, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hs1, hs3 );

   cout << "After swapping with hs3, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_set hs1 is: 10 20 30.
After swapping with hs2, list hs1 is: 200 100.
After swapping with hs3, list hs1 is: 300.
```

## <a name="hash_setupper_bound"></a><a name="upper_bound"></a>hash_set::upper_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Zwraca iteratora do pierwszego elementu w hash_set, który z kluczem, który jest większy niż określony klucz.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz argumentu, który ma być porównywany z kluczem sortowania elementu z przeszukiwanego hash_set.

### <a name="return-value"></a>Wartość zwracana

Lub `iterator` `const_iterator` który odnosi się do lokalizacji elementu w hash_set, który z kluczem, który jest równy lub większy niż klucz argumentu lub który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_set jeśli nie znaleziono dopasowania dla klucza.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_set_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "The first element of hash_set hs1 with a key greater "
        << "than 20 is: " << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_set hs1 with a key > 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.begin( );
   hs1_RcIter = hs1.upper_bound( *hs1_AcIter );
   cout << "The first element of hs1 with a key greater than "
        << endl << "that of the initial element of hs1 is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The first element of hash_set hs1 with a key greater than 20 is: 30.
The hash_set hs1 doesn't have an element with a key greater than 30.
The first element of hs1 with a key greater than
that of the initial element of hs1 is: 20.
```

## <a name="hash_setvalue_comp"></a><a name="value_comp"></a>hash_set::value_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Pobiera kopię obiektu porównania używanego do zamawiania wartości elementów w hash_set.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji używany przez hash_set do uporządkowania jego elementów, czyli parametr *szablonu Porównaj*.

Aby uzyskać więcej informacji na temat *Porównania,* zobacz sekcję Uwagi w temacie [hash_set klasa.](../standard-library/hash-set-class.md)

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję elementu członkowskiego:

`bool operator( const Key& _xVal, const Key& _yVal );`

który zwraca `_xVal` **true,** jeśli poprzedza `_yVal` i nie jest równa w kolejności sortowania.

Należy zauważyć, że zarówno [value_compare,](../standard-library/set-class.md#value_compare) jak i [key_compare](../standard-library/set-class.md#key_compare) są synonimami parametru *szablonu Porównaj*. Oba typy są przewidziane dla hash_set i hash_multiset klas, gdzie są identyczne, dla zgodności z hash_map i hash_multimap klas, gdzie są one różne.

### <a name="example"></a>Przykład

```cpp
// hash_set_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > > hs1;
   hash_set <int, hash_compare < int, less<int> >  >::value_compare
      vc1 = hs1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hs1."
           << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::value_compare
      vc2 = hs2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="hash_setvalue_compare"></a><a name="value_compare"></a>hash_set::value_compare

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Typ, który zawiera dwa obiekty funkcji, predykat binarny klasy porównania, które można porównać dwie wartości elementów hash_set w celu określenia ich względnej kolejności i predykatu unary, który skróty elementów.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Uwagi

`value_compare`jest synonimem parametru szablonu *Cechy*.

Aby uzyskać więcej informacji na temat *cech,* zobacz temat [hash_set Klasa.](../standard-library/hash-set-class.md)

Należy zauważyć, że zarówno `value_compare` [key_compare,](#key_compare) jak i są synonimami parametru szablonu *Cechy*. Oba typy są przewidziane dla hash_set i hash_multiset klas, gdzie są identyczne, dla zgodności z hash_map i hash_multimap klas, gdzie są one różne.

### <a name="example"></a>Przykład

Zobacz przykład [value_comp](#value_comp) na przykład jak zadeklarować i `value_compare`używać .

## <a name="hash_setvalue_type"></a><a name="value_type"></a>hash_set::value_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Typ, który opisuje obiekt przechowywany jako element hash_set w jego pojemności jako wartość.

```cpp
typedef Key value_type;
```

### <a name="example"></a>Przykład

```cpp
// hash_set_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;

   hash_set <int> :: value_type hsvt_Int;   // Declare value_type
   hsvt_Int = 10;             // Initialize value_type

   hash_set <int> :: key_type hskt_Int;   // Declare key_type
   hskt_Int = 20;             // Initialize key_type

   hs1.insert( hsvt_Int );         // Insert value into hs1
   hs1.insert( hskt_Int );         // Insert key into hs1

   // A hash_set accepts key_types or value_types as elements
   cout << "The hash_set has elements:";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( ); hs1_Iter++)
      cout << " " << *hs1_Iter;
   cout << "." << endl;
}
```

```Output
The hash_set has elements: 10 20.
```

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Odwołanie do standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
