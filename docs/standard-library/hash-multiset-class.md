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
ms.openlocfilehash: 7881b1d6775206fbea40c3ba4b15572a6d4b3580
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421682"
---
# <a name="hash_multiset-class"></a>hash_multiset — Klasa

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Klasa kontenera hash_multiset jest rozszerzeniem C++ standardowej biblioteki i służy do przechowywania oraz szybkiego pobierania danych z kolekcji, w której wartości elementów są przechowywane jako wartości klucza i nie muszą być unikatowe.

## <a name="syntax"></a>Składnia

```cpp
template <class Key, class Traits =hash_compare<Key, less <Key>>, class Allocator =allocator <Key>>
class hash_multiset
```

### <a name="parameters"></a>Parametry

*Klucz*\
Typ danych elementu, który ma być przechowywany w hash_multiset.

*Cechy*\
Typ, który zawiera dwa obiekty funkcji, jeden z porównywanych klas, który jest predykatem binarnym, może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność i funkcję mieszania, która jest jednoargumentową wartością klucza mapowania predykatów elementów do niepodpisanych liczb całkowitych typu `size_t`. Ten argument jest opcjonalny, a `hash_compare<Key, less<Key> >` jest wartością domyślną.

\ *alokatora*
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji hash_multiset i dealokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to `allocator<Key>`.

## <a name="remarks"></a>Uwagi

Hash_multiset:

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza. Ponadto, jest prostym kontenerem asocjacyjnym, ponieważ jego wartości elementu są jego wartościami klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.

- Skrót, ponieważ jego elementy są pogrupowane w zasobniki na podstawie wartości funkcji skrótu zastosowanej do wartości klucza elementów.

- Unikatowy w tym sensie, że każdy z jego elementów musi mieć unikatowy klucz. Ponieważ hash_multiset jest również prostym kontenerem asocjacyjnym, jego elementy również są unikatowe.

- Szablon klasy, ponieważ funkcja, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Główną zaletą tworzenia skrótów w porównaniu z sortowaniem jest większa wydajność: pomyślne wykonywanie skrótów wykonuje wstawienia, usunięcia i znajduje się w stałym średnim czasie w porównaniu z czasem proporcjonalnym do logarytmu liczby elementów w kontenerze do sortowania powodują. Nie można bezpośrednio zmienić wartości elementu w zestawie. Zamiast tego musisz usunąć stare wartości i wstawić elementy z nowymi wartościami.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Przyłączone Kontenery asocjacyjne są zoptymalizowane pod kątem operacji wyszukiwania, wstawiania i usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, są wydajne, gdy są używane z dobrze zaprojektowaną funkcją skrótu, wykonując je w czasie, który jest obliczany jako stała średnia i nie zależy od liczby elementów w kontenerze. Dobrze zaprojektowana funkcja skrótu generuje jednorodną dystrybucję wartości skrótów i minimalizuje liczbę kolizji, w których występuje kolizja, gdy wartości unikatowego klucza są mapowane na tę samą wartość skrótu. W najgorszym przypadku z najgorszą możliwą funkcją skrótu liczba operacji jest proporcjonalna do liczby elementów w sekwencji (czas liniowy).

Hash_multiset powinien być kontenerem asocjacyjnym wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Elementy hash_multiset mogą być wielokrotne i służyć jako własne klucze sortowania, dlatego klucze nie są unikatowe. Model dla tego typu konstrukcji jest uporządkowaną listą, np. wyrazów, w których wyrazy mogą występować więcej niż jeden raz. Nie zezwolono na wiele wystąpień wyrazów, a następnie hash_set być odpowiednią strukturą kontenera. Jeśli unikatowe definicje zostały dołączone jako wartości do listy unikatowych słów kluczowych, hash_map będzie odpowiednią strukturą zawierającą te dane. Jeśli zamiast tego definicje nie były unikatowe, hash_multimap będzie kontenerem wyboru.

Hash_multiset porządkuje sekwencję, którą kontroluje, przez wywołanie zapisanego obiektu cechy skrótu typu [value_compare](#value_compare). Dostęp do tego przechowywanego obiektu można uzyskać, wywołując funkcję członkowską [key_comp](#key_comp). Taki obiekt funkcji musi zachowywać się tak samo jak obiekt klasy `hash_compare<Key, less<Key> >`. W odniesieniu do wszystkich *kluczy* wartości typu `Key`wywołanie `Trait(Key)` daje rozkład wartości typu `size_t`.

Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarny *f*( *x*, *y*) jest obiektem funkcji, który ma dwa obiekty argumentu x i y oraz wartość zwracaną true lub false. Kolejność nałożona na hash_multiset jest ściśle słabym porządkowaniem, jeśli Predykat binarny jest niezwrotny, niesymetryczny i przechodni oraz jeśli równoważność jest przechodnia, gdzie dwa obiekty x i y są zdefiniowane jako równoważne, gdy zarówno *f*( *x*, *y*), jak i *f*( *y*, *x*) mają wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

Rzeczywista kolejność elementów w kontrolowanej sekwencji zależy od funkcji skrótu, funkcji porządkowania i bieżącego rozmiaru tabeli skrótów przechowywanej w obiekcie kontenera. Nie można określić bieżącego rozmiaru tabeli skrótów, dlatego nie można ogólnie przewidzieć kolejności elementów w kontrolowanej sekwencji. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Iterator dostarczony przez klasę hash_multiset jest iteratorem dwukierunkowym, ale funkcje składowych klasy INSERT i hash_multiset mają wersje przyjmujące jako parametry szablonu słabszy iterator danych wejściowych, którego wymagania dotyczące funkcjonalności są mniejsze niż te gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma własne hash_multiset wymagania, a algorytmy, które z nich pracują, muszą ograniczyć ich założenia do wymagań dostarczonych przez ten typ iteratora. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny hash_multiset funkcjonalności, ale jest wystarczający, aby można było mówić istotnie o zakresie iteratorów [`first`, `last`) w kontekście funkcji składowych klasy.

### <a name="constructors"></a>Konstruktorzy

|Konstruktor|Opis|
|-|-|
|[hash_multiset](#hash_multiset)|Konstruuje `hash_multiset`, która jest pusta lub jest kopią wszystkich lub części niektórych innych `hash_multiset`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje klasę `allocator` dla obiektu `hash_multiset`.|
|[const_iterator](#const_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać element **const** w `hash_multiset`.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do elementu **const** w `hash_multiset`.|
|[const_reference](#const_reference)|Typ, który dostarcza odwołanie do elementu **const** przechowywanego w `hash_multiset` do odczytu i wykonywania operacji **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny element **const** w `hash_multiset`.|
|[difference_type](#difference_type)|Typ liczby całkowitej ze znakiem, który zawiera różnicę między dwoma iteratorami, które są adresowane do elementów w obrębie tego samego `hash_multiset`.|
|[Iterator](#iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w `hash_multiset`.|
|[key_compare](#key_compare)|Typ, który dostarcza obiekt funkcji, który może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `hash_multiset`.|
|[key_type](#key_type)|Typ, który opisuje obiekt przechowywany jako element `hash_set` w swojej pojemności jako klucz sortowania.|
|[przytrzymaj](#pointer)|Typ, który dostarcza wskaźnik do elementu w `hash_multiset`.|
|[odwoła](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w `hash_multiset`.|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej `hash_multiset`.|
|[size_type](#size_type)|Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w `hash_multiset`.|
|[value_compare](#value_compare)|Typ, który dostarcza dwa obiekty funkcji, Predykat binarny klasy Compare, który może porównać dwie wartości elementów `hash_multiset`, aby określić ich względną kolejność i predykat jednoargumentowy, który miesza elementy.|
|[value_type](#value_type)|Typ, który opisuje obiekt przechowywany jako element `hash_multiset` w swojej pojemności jako wartość.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[zaczną](#begin)|Zwraca iterator, który odnosi się do pierwszego elementu w `hash_multiset`.|
|[cbegin](#cbegin)|Zwraca iterator const odnoszący się do pierwszego elementu w `hash_multiset`.|
|[cend](#cend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w `hash_multiset`.|
|[Wyczyść](#clear)|Usuwa wszystkie elementy `hash_multiset`.|
|[count](#count)|Zwraca liczbę elementów w `hash_multiset`, których klucz pasuje do klucza określonego przez parametr|
|[crbegin —](#crbegin)|Zwraca iterator const odnoszący się do pierwszego elementu w odwróconej `hash_multiset`.|
|[crend](#crend)|Zwraca iterator const, który odnosi się do lokalizacji następującej po ostatnim elemencie w odwróconym `hash_multiset`.|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do `hash_multiset`.|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do `hash_multiset`z wskazówką dotyczącą położenia.|
|[ciągiem](#empty)|Testuje, czy `hash_multiset` jest pusty.|
|[punktów](#end)|Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w `hash_multiset`.|
|[equal_range](#equal_range)|Zwraca parę iteratorów odpowiednio do pierwszego elementu w `hash_multiset` z kluczem, który jest większy niż określony klucz i do pierwszego elementu w `hash_multiset`, z kluczem, który jest równy lub większy niż klucz.|
|[Wyłączanie](#erase)|Usuwa element lub zakres elementów w `hash_multiset` z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.|
|[find](#find)|Zwraca iterator odnoszący się do lokalizacji elementu w `hash_multiset`, który ma klucz równoważny określonemu kluczowi.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu `allocator` użytego do skonstruowania `hash_multiset`.|
|[wstawienia](#insert)|Wstawia element lub zakres elementów do `hash_multiset`.|
|[key_comp](#key_compare)|Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w `hash_multiset`.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu w `hash_multiset` z kluczem, który jest równy lub większy niż określony klucz.|
|[max_size](#max_size)|Zwraca maksymalną długość `hash_multiset`.|
|[rbegin](#rbegin)|Zwraca iterator odnoszący się do pierwszego elementu w odwróconej `hash_multiset`.|
|[rend](#rend)|Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w odwróconym `hash_multiset`.|
|[zmienia](#size)|Zwraca liczbę elementów w `hash_multiset`.|
|[wymiany](#swap)|Wymienia elementy dwóch `hash_multiset`s.|
|[upper_bound](#upper_bound)|Zwraca iterator do pierwszego elementu w `hash_multiset`, z kluczem, który jest równy lub większy niż określony klucz.|
|[value_comp](#value_comp)|Pobiera kopię obiektu cechy skrótu służącego do mieszania i wartości klucza elementu Order w `hash_multiset`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[hash_multiset:: operator =](#op_eq)|Zastępuje elementy hash_multiset kopią innego hash_multiset.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_set >

**Przestrzeń nazw:** stdext

## <a name="allocator_type"></a>hash_multiset:: allocator_type

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Typ, który reprezentuje klasę alokatora dla obiektu hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>Przykład

Zobacz przykład dla [get_allocator](#get_allocator) przykład przy użyciu `allocator_type`

## <a name="begin"></a>hash_multiset:: BEGIN

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca iterator, który odnosi się do pierwszego elementu w hash_multiset.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwrócona

Iterator dwukierunkowy odnoszący się do pierwszego elementu w hash_multiset lub lokalizacji po pomyślnym wypełnieniu pustego hash_multiset.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana `begin` jest przypisana do `const_iterator`, nie można modyfikować elementów w obiekcie hash_multiset. Jeśli wartość zwracana `begin` jest przypisana do `iterator`, można modyfikować elementy w hash_multiset obiekcie.

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

## <a name="cbegin"></a>hash_multiset:: cbegin

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca iterator const, który dotyczy pierwszego elementu w hash_multiset.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwrócona

Stały iterator dwukierunkowy odnoszący się do pierwszego elementu w [hash_multiset](../standard-library/hash-multiset-class.md) lub lokalizacji po pomyślnym wypełnieniu pustego `hash_multiset`.

### <a name="remarks"></a>Uwagi

W przypadku wartości zwracanej `cbegin`nie można modyfikować elementów w obiekcie `hash_multiset`.

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

## <a name="cend"></a>hash_multiset:: cend

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w hash_multiset.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwrócona

Stały iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w [hash_multiset](../standard-library/hash-multiset-class.md). Jeśli `hash_multiset` jest puste, a następnie `hash_multiset::cend == hash_multiset::begin`.

### <a name="remarks"></a>Uwagi

`cend` służy do sprawdzania, czy iterator osiągnął koniec jego `hash_multiset`. Nie należy wywoływać wartości zwracanej przez `cend`.

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

## <a name="clear"></a>hash_multiset:: Clear

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

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

## <a name="const_iterator"></a>hash_multiset:: const_iterator

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać element **const** w hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Uwagi

Typu `const_iterator` nie można użyć do zmodyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpoczęcia](#begin) korzystania z `const_iterator`.

## <a name="const_pointer"></a>hash_multiset:: const_pointer

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza wskaźnik do elementu **const** w hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typu `const_pointer` nie można użyć do zmodyfikowania wartości elementu.

W większości przypadków [const_iterator](#const_iterator) należy używać w celu uzyskania dostępu do elementów w obiekcie **const** hash_multiset.

## <a name="const_reference"></a>hash_multiset:: const_reference

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza odwołanie do elementu **const** przechowywanego w hash_multiset do odczytu i wykonywania operacji **const** .

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

## <a name="const_reverse_iterator"></a>hash_multiset:: const_reverse_iterator

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny element **const** w hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartości elementu i służy do iteracji przez hash_multiset w odwrocie.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rend](#rend) , aby zapoznać się z przykładem sposobu deklarowania i używania `const_reverse_iterator`.

## <a name="count"></a>hash_multiset:: Count

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca liczbę elementów w hash_multiset, których klucz pasuje do klucza określonego przez parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*klucz*\
Klucz elementów do dopasowania z hash_multiset.

### <a name="return-value"></a>Wartość zwrócona

Liczba elementów w hash_multiset z kluczem określonym parametrem.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę elementów w następującym zakresie:

\[ lower_bound (*klucz*), upper_bound (*klucz*)).

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie funkcji składowej hash_multiset:: Count.

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

## <a name="crbegin"></a>hash_multiset:: crbegin —

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca iterator const odnoszący się do pierwszego elementu w odwróconej hash_multiset.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwrócona

Stałe odwrotne Iteratory, odnoszące się do pierwszego elementu w odwróconej [hash_multiset](../standard-library/hash-multiset-class.md) lub adresowania ostatniego elementu w nieodwróconej `hash_multiset`.

### <a name="remarks"></a>Uwagi

`crbegin` jest używany z odwróconym `hash_multiset` tak samo jak [hash_multiset:: BEGIN](#begin) jest używany z `hash_multiset`.

Z wartością zwracaną `crbegin`nie można zmodyfikować obiektu `hash_multiset`.

`crbegin` można użyć do iteracji `hash_multiset` do tyłu.

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

## <a name="crend"></a>hash_multiset:: crend

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca iterator const, który odnosi się do lokalizacji następującej po ostatnim elemencie w odwróconym hash_multiset.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwrócona

Nieodwrócony iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym [hash_multiset](../standard-library/hash-multiset-class.md) (lokalizacja, która poprzedza pierwszy element w nieodwróconym `hash_multiset`).

### <a name="remarks"></a>Uwagi

`crend` jest używany z odwróconym `hash_multiset` tak samo jak [hash_multiset:: end](#end) jest używany z `hash_multiset`.

Z wartością zwracaną `crend`nie można zmodyfikować obiektu `hash_multiset`.

`crend` można użyć do przetestowania, czy iterator odwrotny osiągnął koniec jego hash_multiset.

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

## <a name="difference_type"></a>hash_multiset::d ifference_type

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Typ liczby całkowitej ze znakiem, który zawiera różnicę między dwoma iteratorami, które są adresowane do elementów w obrębie tego samego hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` jest typem zwracanym podczas odejmowania lub zwiększania przez Iteratory kontenera. `difference_type` jest zwykle używany do reprezentowania liczby elementów w zakresie [`first`, `last`) między iteratorami `first` i `last`, zawiera element wskazywany przez `first` i zakres elementów do, ale nie obejmuje elementu wskazywanego przez `last`.

Należy zauważyć, że chociaż `difference_type` jest dostępny dla wszystkich iteratorów, które spełniają wymagania iteratora danych wejściowych, który obejmuje klasę iteratorów dwukierunkowych obsługiwanych przez kontenery odwracalne, takie jak Set. Odejmowanie między iteratorami jest obsługiwane tylko przez Iteratory dostępu swobodnego zapewniane przez kontener dostępu swobodnego, taki jak Vector lub deque.

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

## <a name="emplace"></a>hash_multiset:: emplace

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Wstawia element skonstruowany w miejscu do hash_multiset.

```cpp
template <class ValTy>
iterator insert(ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*użyte*|Wartość elementu, który ma zostać wstawiony do [hash_multiset](../standard-library/hash-multiset-class.md) , chyba że `hash_multiset` już zawiera ten element lub, bardziej ogólnie, elementu, którego klucz jest uporządkowany równorzędnie.|

### <a name="return-value"></a>Wartość zwrócona

Funkcja członkowska `emplace` zwraca iterator, który wskazuje na pozycję, w której został wstawiony nowy element.

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

## <a name="emplace_hint"></a>hash_multiset:: emplace_hint

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Wstawia element skonstruowany w miejscu do hash_multiset z wskazówką dotyczącą położenia.

```cpp
template <class ValTy>
iterator insert(
    const_iterator where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

*val*\
Wartość elementu, który ma zostać wstawiony do [hash_multiset](../standard-library/hash-multiset-class.md) , chyba że `hash_multiset` już zawiera ten element lub, bardziej ogólnie, elementu, którego klucz jest uporządkowany równorzędnie.

*gdzie*\
Miejsce, w którym rozpocznie się wyszukiwanie poprawnego punktu wstawiania. (Wstawianie może odbywać się w amortyzowanym stałym czasie, a nie w czasie logarytmu, jeśli punkt wstawiania *następuje zaraz*po elemencie).

### <a name="return-value"></a>Wartość zwrócona

Funkcja członkowska [hash_multiset:: emplace](#emplace) zwraca iterator, który wskazuje na położenie, w którym nowy element został wstawiony do `hash_multiset`.

### <a name="remarks"></a>Uwagi

Wstawianie może odbywać się w amortyzowanym stałym czasie, a nie w czasie logarytmu, jeśli punkt wstawiania następuje zaraz po tym *miejscu*.

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

## <a name="empty"></a>hash_multiset:: Empty

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Testuje, czy hash_multiset jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli hash_multiset jest pusty. **wartość false** , jeśli hash_multiset nie jest pusta.

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

## <a name="end"></a>hash_multiset:: end

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w hash_multiset.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwrócona

Iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w hash_multiset. Jeśli hash_multiset jest puste, a następnie hash_multiset:: end = = hash_multiset:: BEGIN.

### <a name="remarks"></a>Uwagi

`end` służy do sprawdzania, czy iterator osiągnął koniec jego hash_multiset. Nie należy wywoływać wartości zwracanej przez `end`.

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

## <a name="equal_range"></a>hash_multiset:: equal_range

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca parę iteratorów odpowiednio do pierwszego elementu w hash_multiset z kluczem, który jest większy niż określony klucz i do pierwszego elementu w hash_multiset, z kluczem, który jest równy lub większy niż klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*klucz*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego hash_multiset.

### <a name="return-value"></a>Wartość zwrócona

Para iteratorów, w których pierwszy jest [lower_bound](#lower_bound) klucza, a drugi to [upper_bound](#upper_bound) klucza.

Aby uzyskać dostęp do pierwszego iteratora pary `pr` zwrócone przez funkcję członkowską, należy użyć `pr`. **najpierw** i aby usunąć odwołanie do dolnego powiązanego iteratora, użyj \*(`pr`. **pierwszy**). Aby uzyskać dostęp do drugiego iteratora pary `pr` zwrócone przez funkcję członkowską, należy użyć `pr`. **drugi** i aby usunąć odwołanie do górnego powiązanego iteratora, użyj \*(`pr`. **sekundę**).

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

## <a name="erase"></a>hash_multiset:: Erase

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Usuwa element lub zakres elementów w hash_multiset z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.

```cpp
iterator erase(iterator where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*gdzie*\
Pozycja elementu, który ma zostać usunięty z hash_multiset.

*pierwszy*\
Pozycja pierwszego elementu usuniętego z hash_multiset.

*ostatni*\
Umieść tuż poza ostatnim elementem usuniętym z hash_multiset.

*klucz*\
Klucz elementów do usunięcia z hash_multiset.

### <a name="return-value"></a>Wartość zwrócona

W przypadku pierwszych dwóch funkcji składowych iterator dwukierunkowy, który wyznacza pierwszy element pozostały poza elementami usuniętymi lub wskaźnik do końca hash_multiset, jeśli taki element nie istnieje. W przypadku trzeciej funkcji składowej liczba elementów usuniętych z hash_multiset.

### <a name="remarks"></a>Uwagi

Funkcja członkowska nigdy nie zgłasza wyjątku.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia funkcji członkowskiej hash_multiset:: Erase.

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

## <a name="find"></a>hash_multiset:: find

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca iterator odnoszący się do lokalizacji elementu w hash_multiset, który ma klucz równoważny określonemu kluczowi.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*klucz*\
Klucz argumentu, który ma zostać dopasowany przez klucz sortowania elementu z przeszukiwanego hash_multiset.

### <a name="return-value"></a>Wartość zwrócona

[Iterator](#iterator) lub [const_iterator](#const_iterator) , który odnosi się do lokalizacji elementu równoważnego określonemu kluczowi lub który odnosi się do lokalizacji po ostatnim elemencie w hash_multiset, jeśli nie znaleziono żadnego dopasowania dla klucza.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator, który odnosi się do elementu w hash_multiset którego klucz sortowania jest `equivalent` do klucza argumentu pod predykatem binarnym, który wywołuje kolejność na podstawie mniejszej niż porównywalnej relacji.

Jeśli wartość zwracana `find` jest przypisana do `const_iterator`, nie można zmodyfikować obiektu hash_multiset. Jeśli wartość zwracana `find` jest przypisana do `iterator`, można zmodyfikować obiekt hash_multiset.

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

## <a name="get_allocator"></a>hash_multiset:: get_allocator

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca kopię obiektu alokatora używanego do konstruowania hash_multiset.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwrócona

Alokator używany przez hash_multiset do zarządzania pamięcią, która jest parametrem szablonu klasy `Allocator`.

Aby uzyskać więcej informacji na `Allocator`, zobacz sekcję Uwagi w temacie [klasy hash_multiset](../standard-library/hash-multiset-class.md) .

### <a name="remarks"></a>Uwagi

Przypisania klasy hash_multiset określają sposób zarządzania magazynem przez klasę. Domyślne przydzielenie klas kontenerów C++ biblioteki standardowej jest wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym C++ tematem.

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

## <a name="hash_multiset"></a>hash_multiset:: hash_multiset

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Konstruuje `hash_multiset`, która jest pusta lub jest kopią wszystkich lub części niektórych innych `hash_multiset`.

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
Klasa alokatora magazynu, która ma być używana dla tego obiektu `hash_multiset`, który ma wartość domyślną `Allocator`.

\ *zgodności*
Funkcja porównania typu `const Traits` użyta do uporządkowania elementów w `hash_multiset`, które są wartościami domyślnymi `hash_compare`.

*Prawa*\
`hash_multiset`, do której skonstruowany `hash_multiset` ma być kopia.

*pierwszy*\
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*ostatni*\
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

\ *IList*
Initializer_list, który zawiera elementy, które mają zostać skopiowane.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują typ obiektu alokatora, który zarządza magazynem pamięci dla `hash_multiset` i który może być później zwracany przez wywołanie [hash_multiset:: get_allocator](#get_allocator). Parametr alokatora jest często pomijany w deklaracjach klas i makrach przetwarzania wstępnego służących do podstawiania alternatywnych metod przydzielania.

Wszystkie konstruktory inicjują hash_multisets.

Wszystkie konstruktory przechowują obiekt funkcji typu `Traits`, który jest używany do ustanowienia zamówienia między kluczami `hash_multiset` i który może być później zwracany przez wywołanie [hash_multiset:: key_comp](#key_comp). Aby uzyskać więcej informacji na `Traits` Zobacz temat [klasy hash_multiset](../standard-library/hash-multiset-class.md) .

Pierwsze trzy konstruktory określają pustą `hash_multiset`początkową, drugi określa typ funkcji porównywania (*COMP*), która ma być używana w celu ustalenia kolejności elementów i trzeciego jawnie określającego typ alokatora (*Al*), który ma być używany. Słowo kluczowe **Explicit** pomija pewne rodzaje automatycznej konwersji typów.

Czwarty Konstruktor przenosi `Right``hash_multiset`.

W przypadku konstruktorów piąty, szósty i siódmy użyto initializer_list.

Ostatnie trzy konstruktory skopiują zakres [`first`, `last`) `hash_multiset` z rosnącą jawnością w określaniu typu funkcji porównania klasy porównującej i alokatora.

Rzeczywista kolejność elementów w kontenerze zestawu skrótów zależy od funkcji mieszania, funkcji porządkowania i bieżącego rozmiaru tabeli skrótów i nie może być ogólnie przewidywalna, ponieważ może to być obiektem zestawu, gdzie został ustalony przez funkcję porządkowania niezależne.

## <a name="insert"></a>hash_multiset:: INSERT

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

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

\ *wartości*
Wartość elementu, który ma zostać wstawiony do hash_multiset, chyba że hash_multiset już zawiera ten element lub, bardziej ogólnie, elementu, którego klucz jest uporządkowany równorzędnie.

*gdzie*\
Miejsce, w którym rozpocznie się wyszukiwanie poprawnego punktu wstawiania. (Wstawianie może odbywać się w amortyzowanym stałym czasie, a nie w czasie logarytmu, jeśli punkt wstawiania *następuje zaraz*po elemencie).

*pierwszy*\
Pozycja pierwszego elementu, który ma zostać skopiowany z hash_multiset.

*ostatni*\
Pozycja tuż poza ostatnim elementem, który ma zostać skopiowany z hash_multiset.

\ *IList*
Initializer_list, który zawiera elementy do skopiowania.

### <a name="return-value"></a>Wartość zwrócona

Pierwsze dwie funkcje elementu członkowskiego INSERT zwracają iterator, który wskazuje na pozycję, w której został wstawiony nowy element.

W następnych trzech funkcjach składowych użyto initializer_list.

Trzecia funkcja członkowska wstawia sekwencję wartości elementów do hash_multiset odpowiadającej każdemu elementowi, który jest kierowany przez iterator w zakresie [`first`, `last`) określonego hash_multiset.

### <a name="remarks"></a>Uwagi

Wstawianie może odbywać się w amortyzowanym stałym czasie dla wskazówki dotyczącej wersji instrukcji INSERT zamiast logarytmu czasu, gdy punkt wstawiania następuje zaraz po tym *miejscu*.

## <a name="iterator"></a>hash_multiset:: iterator

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Uwagi

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład rozpoczęcia, aby zapoznać [się](#begin) z przykładem sposobu deklarowania i używania `iterator`.

## <a name="key_comp"></a>hash_multiset:: key_comp

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w hash_multiset.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca *cechy*parametrów szablonu hash_multiset, które zawierają obiekty funkcji, które są używane do mieszania i porządkowania elementów kontenera.

Aby uzyskać więcej informacji o *cechach* , zobacz temat [Klasa hash_multiset](../standard-library/hash-multiset-class.md) .

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członkowską:

`bool operator<(const Key& _xVal, const Key& _yVal);`

zwraca **wartość true** , jeśli `_xVal` poprzedza i nie jest równa `_yVal` w kolejności sortowania.

Należy zauważyć, że zarówno [key_compare](#key_compare) , jak i [value_compare](#value_compare) są synonimami dla *cech*parametrów szablonu. Oba typy są dostępne dla klas hash_multiset i hash_multiset, w których są identyczne, w celu zapewnienia zgodności z klasami hash_map i hash_multimap, gdzie są różne.

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

## <a name="key_compare"></a>hash_multiset:: key_compare

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza dwa obiekty funkcji, Predykat binarny klasy Compare, który może porównać dwie wartości elementów hash_multiset, aby określić ich względną kolejność i predykat jednoargumentowy, który miesza elementy.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare` jest synonimem dla *cech*parametrów szablonu.

Aby uzyskać więcej informacji o *cechach* , zobacz temat [Klasa hash_multiset](../standard-library/hash-multiset-class.md) .

Należy zauważyć, że zarówno `key_compare`, jak i value_compare są synonimami dla *cech*parametrów szablonu. Oba typy są dostępne dla klas hash_set i hash_multiset, w których są identyczne, w celu zapewnienia zgodności z klasami hash_map i hash_multimap, gdzie są różne.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [key_comp](#key_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_compare`.

## <a name="key_type"></a>hash_multiset:: key_type

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza obiekt funkcji, który może porównać klucze sortowania, aby określić względną kolejność dwóch elementów w hash_multiset.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type` jest synonimem dla *klucza*parametru szablonu.

Należy zauważyć, że zarówno `key_type`, jak i [value_type](../standard-library/hash-set-class.md#value_type) są synonimami dla *klucza*parametru szablonu. Oba typy są dostarczane dla klas zestawu i zestawów wielokrotnych, gdzie są identyczne, w celu zapewnienia zgodności z klasami map i multimap, gdzie są różne.

Aby uzyskać więcej informacji o *kluczu*, zobacz sekcję Uwagi w temacie [hash_multiset Class](../standard-library/hash-multiset-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [value_type](#value_type) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_type`.

## <a name="lower_bound"></a>hash_multiset:: lower_bound

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca iterator do pierwszego elementu w hash_multiset z kluczem, który jest równy lub większy niż określony klucz.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*klucz*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego hash_multiset.

### <a name="return-value"></a>Wartość zwrócona

[Iterator](#iterator) lub [const_iterator](#const_iterator) , który odnosi się do lokalizacji pierwszego elementu w hash_multiset z kluczem, który jest równy lub większy od klucza argumentu lub który odnosi się do lokalizacji po ostatnim elemencie w hash_multiset, jeśli nie zostanie znaleziony żaden pasujący klucz.

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

## <a name="max_size"></a>hash_multiset:: max_size

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca maksymalną długość hash_multiset.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwrócona

Maksymalna możliwa Długość hash_multiset.

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

## <a name="op_eq"></a>hash_multiset:: operator =

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zastępuje elementy hash_multiset kopią innego hash_multiset.

```cpp
hash_multiset& operator=(const hash_multiset& right);

hash_multiset& operator=(hash_multiset&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Kliknij*|[Hash_multiset](../standard-library/hash-multiset-class.md) kopiowana do `hash_multiset`.|

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkich istniejących elementów w `hash_multiset`, `operator=` kopiuje lub przenosi zawartość *bezpośrednio* do `hash_multiset`.

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

## <a name="pointer"></a>hash_multiset::p ointer

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza wskaźnik do elementu w hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie zestawu wielokrotnego.

## <a name="rbegin"></a>hash_multiset:: rbegin

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca iterator odnoszący się do pierwszego elementu w odwróconej hash_multiset.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwrócona

Odwrotny iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconym hash_multiset lub adresowania ostatniego elementu w nieodwróconej hash_multiset.

### <a name="remarks"></a>Uwagi

`rbegin` jest używany z odwróconym hash_multiset, tak jak [początek](#begin) jest używany z hash_multisetem.

Jeśli wartość zwracana `rbegin` jest przypisana do `const_reverse_iterator`, nie można zmodyfikować obiektu hash_multiset. Jeśli wartość zwracana `rbegin` jest przypisana do `reverse_iterator`, można zmodyfikować obiekt hash_multiset.

`rbegin` można użyć do iteracji hash_multiset do tyłu.

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

## <a name="reference"></a>hash_multiset:: Reference

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

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

## <a name="rend"></a>hash_multiset:: rend

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w odwróconym hash_multiset.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwrócona

Odwrotny iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym hash_multiset (lokalizacja, która poprzedza pierwszy element w nieodwróconym hash_multiset).

### <a name="remarks"></a>Uwagi

`rend` jest używany z odwróconym hash_multiset, tak jak [koniec](#end) jest używany z hash_multisetem.

Jeśli wartość zwracana `rend` jest przypisana do `const_reverse_iterator`, nie można zmodyfikować obiektu hash_multiset. Jeśli wartość zwracana `rend` jest przypisana do `reverse_iterator`, można zmodyfikować obiekt hash_multiset. Nie należy wywoływać wartości zwracanej przez `rend`.

`rend` można użyć do przetestowania, czy iterator odwrotny osiągnął koniec jego hash_multiset.

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

## <a name="reverse_iterator"></a>hash_multiset:: reverse_iterator

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iteracji przez hash_multiset w odwrocie.

### <a name="example"></a>Przykład

Zobacz przykład dla [rbegin](#rbegin) , aby zapoznać się z przykładem sposobu deklarowania i używania `reverse_iterator`.

## <a name="size"></a>hash_multiset:: size

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca liczbę elementów w hash_multiset.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwrócona

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

## <a name="size_type"></a>hash_multiset:: size_type

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Zobacz przykład [rozmiaru](#size) , aby zapoznać się z przykładem sposobu deklarowania i używania `size_type`

## <a name="swap"></a>hash_multiset:: swap

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Wymienia elementy dwóch hash_multisets.

```cpp
void swap(hash_multiset& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Argument hash_multiset zapewniający elementy, które mają zostać zamienione na hash_multiset docelowy.

### <a name="remarks"></a>Uwagi

Funkcja członkowska unieważnia brak odwołań, wskaźników lub iteratorów, które wyznaczają elementy w dwóch hash_multisets których elementy są wymieniane.

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

## <a name="upper_bound"></a>hash_multiset:: upper_bound

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Zwraca iterator do pierwszego elementu w hash_multiset z kluczem, który jest większy niż określony klucz.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*klucz*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego hash_multiset.

### <a name="return-value"></a>Wartość zwrócona

[Iterator](#iterator) lub [const_iterator](#const_iterator) , który odnosi się do lokalizacji pierwszego elementu w hash_multiset z kluczem większym niż klucz argumentu lub który odnosi się do lokalizacji po ostatnim elemencie w hash_multiset, jeśli nie znaleziono żadnego dopasowania dla klucza.

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

## <a name="value_comp"></a>hash_multiset:: value_comp

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Pobiera kopię obiektu porównania użytego do uporządkowania wartości elementów w hash_multiset.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca *cechy*parametrów szablonu hash_multiset, które zawierają obiekty funkcji, które są używane do mieszania i do porządkowania elementów kontenera.

Aby uzyskać więcej informacji o *cechach* , zobacz temat [Klasa hash_multiset](../standard-library/hash-multiset-class.md) .

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członkowską:

**operator bool**( **constKey &** `_xVal`, **klucz const &** *_yVal*);

zwraca **wartość true** , jeśli `_xVal` poprzedza i nie jest równa `_yVal` w kolejności sortowania.

Należy zauważyć, że zarówno [key_compare](#key_compare) , jak i [value_compare](#value_compare) są synonimami dla *cech*parametrów szablonu. Oba typy są dostępne dla klas hash_multiset i hash_multiset, w których są identyczne, w celu zapewnienia zgodności z klasami hash_map i hash_multimap, gdzie są różne.

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

## <a name="value_compare"></a>hash_multiset:: value_compare

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza dwa obiekty funkcji, Predykat binarny klasy Compare, który może porównać dwie wartości elementów hash_multiset, aby określić ich względną kolejność i predykat jednoargumentowy, który miesza elementy.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Uwagi

`value_compare` jest synonimem dla *cech*parametrów szablonu.

Aby uzyskać więcej informacji o *cechach* , zobacz temat [Klasa hash_multiset](../standard-library/hash-multiset-class.md) .

Należy zauważyć, że zarówno [key_compare](#key_compare) , jak i `value_compare` są synonimami dla *cech*parametrów szablonu. Oba typy są dostarczane dla klas zestawów i zestawów wielokrotnych, gdzie są identyczne, aby zapewnić zgodność z mapami klas i multimap, gdzie są różne.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [value_comp](#value_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania `value_compare`.

## <a name="value_type"></a>hash_multiset:: value_type

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Typ, który opisuje obiekt przechowywany jako element jako hash_multiset w swojej pojemności jako wartość.

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

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
