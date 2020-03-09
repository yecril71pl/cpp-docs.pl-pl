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
ms.openlocfilehash: becf038678f4abbe285e719e4d1cc1f3f12de982
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865142"
---
# <a name="hash_set-class"></a>hash_set — Klasa

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Klasa kontenera hash_set jest rozszerzeniem C++ standardowej biblioteki i służy do przechowywania oraz szybkiego pobierania danych z kolekcji, w której wartości zawartych elementów są unikatowe i służą jako wartości klucza.

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
Typ, który zawiera dwa obiekty funkcji, jeden z porównywanych klas, który jest predykatem binarnym, może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność i funkcję mieszania, która jest jednoargumentową wartością klucza mapowania predykatów elementów do niepodpisanych liczb całkowitych typu `size_t`. Ten argument jest opcjonalny, a `hash_compare<Key, less<Key> >` jest wartością domyślną.

\ *alokatora*
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji hash_set i dealokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to `allocator<Key>`.

## <a name="remarks"></a>Uwagi

Hash_set:

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza. Ponadto, jest prostym kontenerem asocjacyjnym, ponieważ jego wartości elementu są jego wartościami klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.

- Skrót, ponieważ jego elementy są pogrupowane w zasobniki na podstawie wartości funkcji skrótu zastosowanej do wartości klucza elementów.

- Unikatowy w tym sensie, że każdy z jego elementów musi mieć unikatowy klucz. Ponieważ hash_set jest również prostym kontenerem asocjacyjnym, jego elementy również są unikatowe.

- Szablon klasy, ponieważ funkcja, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Główną zaletą tworzenia skrótów w porównaniu z sortowaniem jest większa wydajność. pomyślne wykonywanie skrótów wykonuje wstawienia, usunięcia i znajduje się w stałym średnim czasie w porównaniu z czasem proporcjonalnym do logarytmu liczby elementów w kontenerze dla technik sortowania. Nie można bezpośrednio zmienić wartości elementu w zestawie. Zamiast tego musisz usunąć stare wartości i wstawić elementy z nowymi wartościami.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Przyłączone Kontenery asocjacyjne są zoptymalizowane pod kątem operacji wyszukiwania, wstawiania i usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, są wydajne, gdy są używane z dobrze zaprojektowaną funkcją skrótu, wykonując je w czasie, który jest obliczany jako stała średnia i nie zależy od liczby elementów w kontenerze. Dobrze zaprojektowana funkcja skrótu generuje jednorodną dystrybucję wartości skrótów i minimalizuje liczbę kolizji, w których występuje kolizja, gdy wartości unikatowego klucza są mapowane na tę samą wartość skrótu. W najgorszym przypadku z najgorszą możliwą funkcją skrótu liczba operacji jest proporcjonalna do liczby elementów w sekwencji (czas liniowy).

Hash_set powinna być kontenerem asocjacyjnym wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Elementy hash_set są unikatowe i służą jako własne klucze sortowania. Model dla tego typu konstrukcji jest uporządkowaną listą, np. wyrazów, w których wyrazy mogą występować tylko raz. Jeśli dozwolone jest wiele wystąpień wyrazów, hash_multiset będzie odpowiednią strukturą kontenera. Jeśli konieczne jest dołączenie wartości do listy unikatowych słów kluczowych, hash_map będzie odpowiednią strukturą zawierającą te dane. Jeśli zamiast tego klucze nie są unikatowe, hash_multimap będzie kontenerem wyboru.

Hash_set porządkuje sekwencję, którą kontroluje, przez wywołanie przechowywanego `Traits` obiektu skrótu typu [value_compare](#value_compare). Dostęp do tego przechowywanego obiektu można uzyskać, wywołując funkcję członkowską [key_comp](#key_comp). Taki obiekt funkcji musi zachowywać się tak samo jak obiekt klasy *hash_compare < Key, mniej\<klucz > >.* W odniesieniu do wszystkich wartości `key` typu klucz, cecha wywołania (`key`) daje rozkład wartości typu size_t.

Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Powoduje to porządkowanie między nierównoważnymi elementami. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarny *f*( *x*, *y*) jest obiektem funkcji, który ma dwa obiekty argumentu x i y oraz wartość zwracaną true lub false. Kolejność nałożona na hash_set jest ściśle słabym porządkowaniem, jeśli Predykat binarny jest niezwrotny, niesymetryczny i przechodni oraz jeśli równoważność jest przechodnia, gdzie dwa obiekty *x* i *y* są zdefiniowane jako równoważne, gdy zarówno *f*( *x*, *y*), jak i *f*( *y*, *x*) mają wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

Rzeczywista kolejność elementów w kontrolowanej sekwencji zależy od funkcji skrótu, funkcji porządkowania i bieżącego rozmiaru tabeli skrótów przechowywanej w obiekcie kontenera. Nie można określić bieżącego rozmiaru tabeli skrótów, dlatego nie można ogólnie przewidzieć kolejności elementów w kontrolowanej sekwencji. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Iterator dostarczony przez klasę hash_set jest iteratorem dwukierunkowym, ale funkcje składowych klasy [INSERT](#insert) i [hash_set](#hash_set) mają wersje przyjmujące jako parametry szablonu słabszy iterator danych wejściowych, którego wymagania funkcjonalności są mniejsze niż te gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcjonalności, ale jest wystarczający, aby można było mówić istotnie o zakresie iteratorów [`first`, `last`) w kontekście funkcji składowych klasy.

### <a name="constructors"></a>Konstruktorzy

|Konstruktor|Opis|
|-|-|
|[hash_set](#hash_set)|Konstruuje `hash_set`, która jest pusta lub jest kopią wszystkich lub części niektórych innych `hash_set`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje klasę `allocator` dla obiektu `hash_set`.|
|[const_iterator](#const_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytywać `const` element w `hash_set`.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do elementu **const** w `hash_set`.|
|[const_reference](#const_reference)|Typ, który dostarcza odwołanie do elementu **const** przechowywanego w `hash_set` do odczytu i wykonywania operacji **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny element **const** w `hash_set`.|
|[difference_type](#difference_type)|Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów `hash_set` w zakresie między elementami wskazywanymi przez Iteratory.|
|[Iterator](#iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w `hash_set`.|
|[key_compare](#key_compare)|Typ, który dostarcza obiekt funkcji, który może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `hash_set`.|
|[key_type](#key_type)|Typ, który opisuje obiekt przechowywany jako element `hash_set` w swojej pojemności jako klucz sortowania.|
|[przytrzymaj](#pointer)|Typ, który dostarcza wskaźnik do elementu w `hash_set`.|
|[odwoła](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w `hash_set`.|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej `hash_set`.|
|[size_type](#size_type)|Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w `hash_set`.|
|[value_compare](#value_compare)|Typ, który dostarcza dwa obiekty funkcji, Predykat binarny klasy Compare, który może porównać dwie wartości elementów `hash_set`, aby określić ich względną kolejność i predykat jednoargumentowy, który miesza elementy.|
|[value_type](#value_type)|Typ, który opisuje obiekt przechowywany jako element `hash_set` w swojej pojemności jako wartość.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[zaczną](#begin)|Zwraca iterator, który odnosi się do pierwszego elementu w `hash_set`.|
|[cbegin](#cbegin)|Zwraca iterator const odnoszący się do pierwszego elementu w `hash_set`.|
|[cend](#cend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w `hash_set`.|
|[Wyczyść](#clear)|Usuwa wszystkie elementy `hash_set`.|
|[count](#count)|Zwraca liczbę elementów w `hash_set`, których klucz pasuje do klucza określonego przez parametr.|
|[crbegin —](#crbegin)|Zwraca iterator const odnoszący się do pierwszego elementu w odwróconej `hash_set`.|
|[crend](#crend)|Zwraca iterator const, który odnosi się do lokalizacji następującej po ostatnim elemencie w odwróconym `hash_set`.|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do `hash_set`.|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do `hash_set`z wskazówką dotyczącą położenia.|
|[ciągiem](#empty)|Testuje, czy `hash_set` jest pusty.|
|[punktów](#end)|Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w `hash_set`.|
|[equal_range](#equal_range)|Zwraca parę iteratorów odpowiednio do pierwszego elementu w `hash_set` z kluczem, który jest większy niż określony klucz i do pierwszego elementu w `hash_set`, z kluczem, który jest równy lub większy niż klucz.|
|[Wyłączanie](#erase)|Usuwa element lub zakres elementów w `hash_set` z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.|
|[find](#find)|Zwraca iterator odnoszący się do lokalizacji elementu w `hash_set`, który ma klucz równoważny określonemu kluczowi.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu `allocator` użytego do skonstruowania `hash_set`.|
|[wstawienia](#insert)|Wstawia element lub zakres elementów do `hash_set`.|
|[key_comp](#key_comp)|Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w `hash_set`.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu w `hash_set` z kluczem, który jest równy lub większy niż określony klucz.|
|[max_size](#max_size)|Zwraca maksymalną długość `hash_set`.|
|[rbegin](#rbegin)|Zwraca iterator odnoszący się do pierwszego elementu w odwróconej `hash_set`.|
|[rend](#rend)|Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w odwróconym `hash_set`.|
|[zmienia](#size)|Zwraca liczbę elementów w `hash_set`.|
|[wymiany](#swap)|Wymienia elementy dwóch `hash_set`s.|
|[upper_bound](#upper_bound)|Zwraca iterator do pierwszego elementu w `hash_set`, z kluczem, który jest równy lub większy niż określony klucz.|
|[value_comp](#value_comp)|Pobiera kopię obiektu cechy skrótu służącego do mieszania i wartości klucza elementu Order w `hash_set`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[hash_set:: operator =](#op_eq)|Zastępuje elementy `hash_set` kopią innego `hash_set`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_set >

**Przestrzeń nazw:** stdext

## <a name="allocator_type"></a>hash_set:: allocator_type

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Typ, który reprezentuje klasę alokatora dla obiektu hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type` jest synonimem dla *alokatora*parametrów szablonu.

Aby uzyskać więcej informacji na temat *alokatora*, zobacz sekcję Uwagi w temacie [hash_set Class](../standard-library/hash-set-class.md) .

### <a name="example"></a>Przykład

Zobacz przykład dla [get_allocator](#get_allocator) , aby uzyskać przykład, który używa `allocator_type`.

## <a name="begin"></a>hash_set:: BEGIN

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca iterator, który odnosi się do pierwszego elementu w hash_set.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwrócona

Iterator dwukierunkowy odnoszący się do pierwszego elementu w hash_set lub lokalizacji po pomyślnym wypełnieniu pustego hash_set.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana `begin` jest przypisana do `const_iterator`, nie można modyfikować elementów w obiekcie hash_set. Jeśli wartość zwracana `begin` jest przypisana do `iterator`, można modyfikować elementy w hash_set obiekcie.

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

## <a name="cbegin"></a>hash_set:: cbegin

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca iterator const, który dotyczy pierwszego elementu w hash_set.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwrócona

Stały iterator dwukierunkowy odnoszący się do pierwszego elementu w [hash_set](../standard-library/hash-set-class.md) lub lokalizacji po pomyślnym wypełnieniu pustego `hash_set`.

### <a name="remarks"></a>Uwagi

W przypadku wartości zwracanej `cbegin`nie można modyfikować elementów w obiekcie `hash_set`.

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

## <a name="cend"></a>hash_set:: cend

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w hash_set.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwrócona

Stały iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w [hash_set](../standard-library/hash-set-class.md). Jeśli `hash_set` jest puste, a następnie `hash_set::cend == hash_set::begin`.

### <a name="remarks"></a>Uwagi

`cend` służy do sprawdzania, czy iterator osiągnął koniec jego `hash_set`. Nie należy wywoływać wartości zwracanej przez `cend`.

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

## <a name="clear"></a>hash_set:: Clear

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

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

## <a name="const_iterator"></a>hash_set:: const_iterator

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać element **const** w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Uwagi

Typu `const_iterator` nie można użyć do zmodyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpoczęcia](#begin) dla przykładu korzystającego z `const_iterator`.

## <a name="const_pointer"></a>hash_set:: const_pointer

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Typ, który dostarcza wskaźnik do elementu **const** w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typu `const_pointer` nie można użyć do zmodyfikowania wartości elementu.

W większości przypadków [const_iterator](#const_iterator) należy używać w celu uzyskania dostępu do elementów w obiekcie **const** hash_set.

## <a name="const_reference"></a>hash_set:: const_reference

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Typ, który dostarcza odwołanie do elementu **const** przechowywanego w hash_set do odczytu i wykonywania operacji **const** .

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

## <a name="const_reverse_iterator"></a>hash_set:: const_reverse_iterator

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny element **const** w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartości elementu i służy do iteracji przez hash_set w odwrocie.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rend](#rend) , aby zapoznać się z przykładem sposobu deklarowania i używania `const_reverse_iterator`

## <a name="count"></a>hash_set:: Count

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca liczbę elementów w hash_set, których klucz pasuje do klucza określonego przez parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*klucz*\
Klucz elementów do dopasowania z hash_set.

### <a name="return-value"></a>Wartość zwrócona

1, jeśli hash_set zawiera element, którego klucz sortowania pasuje do klucza parametru.

0, jeśli hash_set nie zawiera elementu z pasującym kluczem.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę elementów w następującym zakresie:

\[ lower_bound (*klucz*), upper_bound (*klucz*)).

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie funkcji składowej hash_set:: Count.

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

## <a name="crbegin"></a>hash_set:: crbegin —

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca iterator const odnoszący się do pierwszego elementu w odwróconej hash_set.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwrócona

Stałe odwrotne Iteratory, odnoszące się do pierwszego elementu w odwróconej [hash_set](../standard-library/hash-set-class.md) lub adresowania ostatniego elementu w nieodwróconej `hash_set`.

### <a name="remarks"></a>Uwagi

`crbegin` jest używany z odwróconym hash_set tak samo jak [hash_set:: BEGIN](#begin) jest używany z hash_set.

Z wartością zwracaną `crbegin`nie można zmodyfikować obiektu `hash_set`.

`crbegin` można użyć do iteracji `hash_set` do tyłu.

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

## <a name="crend"></a>hash_set:: crend

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca iterator const, który odnosi się do lokalizacji następującej po ostatnim elemencie w odwróconym hash_set.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwrócona

Nieodwrócony iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym [hash_set](../standard-library/hash-set-class.md) (lokalizacja, która poprzedza pierwszy element w nieodwróconym `hash_set`).

### <a name="remarks"></a>Uwagi

`crend` jest używany z odwróconym `hash_set` tak samo jak [hash_set:: end](#end) jest używany z `hash_set`.

Z wartością zwracaną `crend`nie można zmodyfikować obiektu `hash_set`.

`crend` można użyć do przetestowania, czy iterator odwrotny osiągnął koniec jego `hash_set`.

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

## <a name="difference_type"></a>hash_set::d ifference_type

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów hash_set w zakresie między elementami wskazywanymi przez Iteratory.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` jest typem zwracanym podczas odejmowania lub zwiększania przez Iteratory kontenera. `difference_type` jest zwykle używany do reprezentowania liczby elementów w zakresie [`first`, `last`) między iteratorami `first` i `last`, zawiera element wskazywany przez `first` i zakres elementów do, ale nie obejmuje elementu wskazywanego przez `last`.

Należy zauważyć, że chociaż `difference_type` jest dostępny dla wszystkich iteratorów, które spełniają wymagania iteratora danych wejściowych, który obejmuje klasę iteratorów dwukierunkowych obsługiwanych przez kontenery odwracalne, takie jak zestaw, odejmowanie między iteratorami jest obsługiwane tylko przez Iteratory dostępu swobodnego, dostarczone przez kontener dostępu losowego, takie jak Vector lub deque.

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

## <a name="emplace"></a>hash_set:: emplace

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

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
|*użyte*|Wartość elementu, który ma zostać wstawiony do [hash_set](../standard-library/hash-set-class.md) , chyba że `hash_set` już zawiera ten element lub, bardziej ogólnie, elementu, którego klucz jest uporządkowany równorzędnie.|

### <a name="return-value"></a>Wartość zwrócona

Funkcja członkowska `emplace` zwraca parę, której składnik **bool** zwraca **wartość true** , jeśli wstawiono, i **wartość false** , jeśli `hash_set` już zawierała element, którego klucz ma odpowiednik wartości w kolejności, a Składnik iteratora zwraca adres, w którym został wstawiony nowy element lub w którym już znajduje się element.

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

## <a name="emplace_hint"></a>hash_set:: emplace_hint

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

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
|*użyte*|Wartość elementu, który ma zostać wstawiony do [hash_set](../standard-library/hash-set-class.md) , chyba że `hash_set` już zawiera ten element lub, bardziej ogólnie, elementu, którego klucz jest uporządkowany równorzędnie.|
|*_Where*|Miejsce, w którym rozpocznie się wyszukiwanie poprawnego punktu wstawiania. (Wstawianie może odbywać się w amortyzowanym stałym czasie, a nie w czasie logarytmu, jeśli punkt wstawiania natychmiast następuje *_Where*).|

### <a name="return-value"></a>Wartość zwrócona

Funkcja członkowska [hash_set:: emplace](#emplace) zwraca iterator, który wskazuje na położenie, w którym nowy element został wstawiony do `hash_set`lub gdzie znajduje się istniejący element o równoważnej kolejności.

### <a name="remarks"></a>Uwagi

Wstawianie może odbywać się w amortyzowanym stałym czasie, a nie w czasie logarytmu, jeśli punkt wstawiania natychmiast następuje *_Where*.

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

## <a name="empty"></a>hash_set:: Empty

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Testuje, czy hash_set jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli hash_set jest pusty. **wartość false** , jeśli hash_set nie jest pusta.

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

## <a name="end"></a>hash_set:: end

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w hash_set.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwrócona

Iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w hash_set. Jeśli hash_set jest puste, a następnie hash_set:: end = = hash_set:: BEGIN.

### <a name="remarks"></a>Uwagi

`end` służy do sprawdzania, czy iterator osiągnął koniec jego hash_set. Nie należy wywoływać wartości zwracanej przez `end`.

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

## <a name="equal_range"></a>hash_set:: equal_range

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca parę iteratorów odpowiednio do pierwszego elementu w zestawie skrótu z kluczem, który jest równy określonemu kluczowi i do pierwszego elementu w zestawie skrótu z kluczem, który jest większy niż klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*klucz*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego hash_set.

### <a name="return-value"></a>Wartość zwrócona

Para iteratorów, w których pierwszy jest [lower_bound](../standard-library/set-class.md#lower_bound) klucza, a drugi to [upper_bound](../standard-library/set-class.md#upper_bound) klucza.

Aby uzyskać dostęp do pierwszego iteratora pary żądania ściągnięcia zwróconego przez funkcję członkowską, użyj `pr`. **najpierw**i aby usunąć odwołanie do dolnego powiązanego iteratora, użyj \*(`pr`. **pierwszy**). Aby uzyskać dostęp do drugiego iteratora pary `pr` zwrócone przez funkcję członkowską, należy użyć `pr`. **drugi**i aby usunąć odwołanie do górnego powiązanego iteratora, użyj \*(`pr`. **sekundę**).

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

## <a name="erase"></a>hash_set:: Erase

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Usuwa element lub zakres elementów w hash_set z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_Where*\
Pozycja elementu, który ma zostać usunięty z hash_set.

*pierwszy*\
Pozycja pierwszego elementu usuniętego z hash_set.

*ostatni*\
Umieść tuż poza ostatnim elementem usuniętym z hash_set.

*klucz*\
Klucz elementów do usunięcia z hash_set.

### <a name="return-value"></a>Wartość zwrócona

W przypadku pierwszych dwóch funkcji składowych iterator dwukierunkowy, który wyznacza pierwszy element pozostały poza elementami usuniętymi lub wskaźnik do końca hash_set, jeśli taki element nie istnieje. W przypadku trzeciej funkcji składowej liczba elementów usuniętych z hash_set.

### <a name="remarks"></a>Uwagi

Funkcja członkowska nigdy nie zgłasza wyjątku.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia funkcji członkowskiej hash_set:: Erase.

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

## <a name="find"></a>hash_set:: find

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca iterator odnoszący się do lokalizacji elementu w hash_set, który ma klucz równoważny określonemu kluczowi.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*klucz*\
Klucz argumentu, który ma zostać dopasowany przez klucz sortowania elementu z przeszukiwanego hash_set.

### <a name="return-value"></a>Wartość zwrócona

`iterator` lub `const_iterator`, które odnoszą się do lokalizacji elementu odpowiadającego określonemu kluczowi lub który odnosi się do lokalizacji po ostatnim elemencie w hash_set, jeśli nie zostanie znaleziony żaden pasujący klucz.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator, który odnosi się do elementu w hash_set którego klucz sortowania jest `equivalent` do klucza argumentu pod predykatem binarnym, który wywołuje kolejność na podstawie mniejszej niż porównywalnej relacji.

Jeśli wartość zwracana `find` jest przypisana do `const_iterator`, nie można zmodyfikować obiektu hash_set. Jeśli wartość zwracana `find` jest przypisana do `iterator`, można zmodyfikować obiekt hash_set.

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

## <a name="get_allocator"></a>hash_set:: get_allocator

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca kopię obiektu alokatora używanego do konstruowania hash_set.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwrócona

Alokator używany przez hash_set do zarządzania pamięcią, która jest programem *przydzielania*parametrów szablonu.

Aby uzyskać więcej informacji na temat *alokatora*, zobacz sekcję Uwagi w temacie [hash_set Class](../standard-library/hash-set-class.md) .

### <a name="remarks"></a>Uwagi

Przypisania klasy hash_set określają sposób zarządzania magazynem przez klasę. Domyślne przydzielenie klas kontenerów C++ biblioteki standardowej jest wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym C++ tematem.

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

## <a name="hash_set"></a>hash_set:: hash_set

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Konstruuje `hash_set`, która jest pusta lub jest kopią wszystkich lub części niektórych innych `hash_set`.

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
|*Wsp*|Klasa alokatora magazynu, która ma być używana dla tego obiektu `hash_set`, który ma wartość domyślną `Allocator`.|
|*Przepisów*|Funkcja porównania typu `const Traits` użyta do uporządkowania elementów w `hash_set`, które są wartościami domyślnymi `hash_compare`.|
|*Kliknij*|`hash_set`, do której skonstruowany `hash_set` ma być kopia.|
|*Pierwszego*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*Ostatniego*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują typ obiektu alokatora, który zarządza magazynem pamięci dla `hash_set` i który może być później zwracany przez wywołanie [hash_set:: get_allocator](#get_allocator). Parametr alokatora jest często pomijany w deklaracjach klas i makrach przetwarzania wstępnego służących do podstawiania alternatywnych metod przydzielania.

Wszystkie konstruktory inicjują hash_sets.

Wszystkie konstruktory przechowują obiekt funkcji typu `Traits`, który jest używany do ustanowienia zamówienia między kluczami `hash_set` i który może być później zwracany przez wywołanie [hash_set:: key_comp](#key_comp). Aby uzyskać więcej informacji na `Traits` Zobacz temat [klasy hash_set](../standard-library/hash-set-class.md) .

Pierwszy Konstruktor tworzy puste początkowy `hash_set` sekunda określa typ funkcji porównywania (`Comp`), która ma być używana w celu ustalenia kolejności elementów, a trzeci jawnie określa typ alokatora (`Al`), który ma być używany. Słowo kluczowe `explicit` pomija niektórych rodzajów konwersji typu automatycznego.

Czwarty i piąty konstruktory określają kopię `Right``hash_set`.

Ostatni szósty, siódmy i ósmy konstruktory używają initializer_list dla elementów.

Ostatni konstruktorzy skopiują zakres [`First`, `Last`) `hash_set` z rosnącą jawnością w określaniu typu funkcji porównania cech klasy i alokatora.

Ósmy Konstruktor przenosi `Right``hash_set`.

Rzeczywista kolejność elementów w kontenerze `hash_set` zależy od funkcji skrótu, funkcji porządkowania i bieżącego rozmiaru tabeli skrótów i nie może być ogólnie przewidywalna, ponieważ może ona znajdować się w kontenerze zestawu, który został ustalony przez funkcję porządkowania.

## <a name="insert"></a>hash_set:: INSERT

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Wstawia element lub zakres elementów do `hash_set`.

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
|*Użyte*|Wartość elementu, który ma zostać wstawiony do `hash_set`, chyba że `hash_set` już zawiera ten element lub, bardziej ogólnie, elementu, którego klucz jest uporządkowany równorzędnie.|
|*Miejscu*|Miejsce, w którym rozpocznie się wyszukiwanie poprawnego punktu wstawiania. (Wstawianie może odbywać się w amortyzowanym stałym czasie, a nie w czasie logarytmu, jeśli punkt wstawiania natychmiast następuje `_Where`).|
|*Pierwszego*|Pozycja pierwszego elementu, który ma zostać skopiowany z `hash_set`.|
|*Ostatniego*|Pozycja tuż poza ostatnim elementem, który ma zostać skopiowany z `hash_set`.|
|*IList*|Lista initializer_list, z której mają być skopiowane elementy.|

### <a name="return-value"></a>Wartość zwrócona

Pierwsza `insert` funkcja członkowska zwraca parę, której składnik **bool** zwraca **wartość true** , jeśli wstawiono, i **wartość false** , jeśli `hash_set` już zawierała element, którego klucz ma odpowiednik wartości w kolejności, a Składnik iteratora zwraca adres, w którym został wstawiony nowy element lub gdzie już znajduje się element.

Aby uzyskać dostęp do składnika iteratora pary `pr` zwrócone przez tę funkcję elementu członkowskiego, użyj `pr.first` i aby usunąć odwołanie do niego, użyj `*(pr.first)`. Aby uzyskać dostęp do składnika **bool** pary `pr` zwrócone przez tę funkcję elementu członkowskiego, użyj `pr.second`i aby usunąć odwołanie do niego, użyj `*(pr.second)`.

Druga funkcja członkowska `insert` zwraca iterator, który wskazuje na położenie, w którym nowy element został wstawiony do `hash_set`.

### <a name="remarks"></a>Uwagi

Trzecia funkcja członkowska wstawia elementy w initializer_list.

Trzecia funkcja członkowska wstawia sekwencję wartości elementów do `hash_set` odpowiadającej każdemu elementowi, który jest kierowany przez iterator w zakresie [`First`, `Last`) określonego `hash_set`.

## <a name="iterator"></a>hash_set:: iterator

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Uwagi

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zapoznaj [się](#begin) z przykładem dotyczącym sposobu deklarowania i używania `iterator`.

## <a name="key_comp"></a>hash_set:: key_comp

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Pobiera kopię obiektu cechy skrótu służącego do mieszania i wartości klucza elementu Order w hash_set.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca obiekt funkcji, którego hash_set używa do porządkowania jego elementów, które są *cechami*parametru szablonu.

Aby uzyskać więcej informacji o *cechach* , zobacz temat [Klasa hash_set](../standard-library/hash-set-class.md) .

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członkowską:

`bool operator( const Key& _xVal, const Key& _yVal );`

zwraca **wartość true** , jeśli `_xVal` poprzedza i nie jest równa `_yVal` w kolejności sortowania.

Należy zauważyć, że zarówno [key_compare](#key_compare) , jak i [value_compare](#value_compare) są synonimami dla *cech*parametrów szablonu. Oba typy są dostępne dla klas hash_set i hash_multiset, w których są identyczne, w celu zapewnienia zgodności z klasami hash_map i hash_multimap, gdzie są różne.

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

## <a name="key_compare"></a>hash_set:: key_compare

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Typ, który dostarcza obiekt funkcji, który może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w hash_set.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare` jest synonimem dla *cech*parametrów szablonu.

Aby uzyskać więcej informacji o *cechach* , zobacz temat [Klasa hash_set](../standard-library/hash-set-class.md) .

Należy zauważyć, że zarówno `key_compare`, jak i [value_compare](#value_compare) są synonimami dla *cech*parametrów szablonu. Oba typy są dostarczane dla klas zestawu i zestawów wielokrotnych, gdzie są identyczne, w celu zapewnienia zgodności z klasami map i multimap, gdzie są różne.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [key_comp](#key_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_compare`.

## <a name="key_type"></a>hash_set:: key_type

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Typ, który opisuje obiekt przechowywany jako element hash_set w swojej pojemności jako klucz sortowania.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type` jest synonimem dla *klucza*parametru szablonu.

Aby uzyskać więcej informacji o *kluczu*, zobacz sekcję Uwagi w temacie [hash_set Class](../standard-library/hash-set-class.md) .

Należy zauważyć, że zarówno `key_type`, jak i [value_type](#value_type) są synonimami dla *klucza*parametru szablonu. Oba typy są dostępne dla klas hash_set i hash_multiset, w których są identyczne, w celu zapewnienia zgodności z klasami hash_map i hash_multimap, gdzie są różne.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [value_type](#value_type) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_type`.

## <a name="lower_bound"></a>hash_set:: lower_bound

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca iterator do pierwszego elementu w hash_set z kluczem, który jest równy lub większy niż określony klucz.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*klucz*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego hash_set.

### <a name="return-value"></a>Wartość zwrócona

`iterator` lub `const_iterator`, które odnoszą się do lokalizacji elementu w hash_set, z kluczem, który jest równy lub większy od klucza argumentu lub który odnosi się do lokalizacji po ostatnim elemencie w hash_set, jeśli nie zostanie znaleziony żaden pasujący klucz.

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

## <a name="max_size"></a>hash_set:: max_size

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca maksymalną długość hash_set.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwrócona

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

## <a name="op_eq"></a>hash_set:: operator =

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zastępuje elementy hash_set kopią innego hash_set.

```cpp
hash_set& operator=(const hash_set& right);

hash_set& operator=(hash_set&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Kliknij*|[Hash_set](../standard-library/hash-set-class.md) kopiowana do `hash_set`.|

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkich istniejących elementów w `hash_set`, `operator=` kopiuje lub przenosi zawartość *bezpośrednio* do `hash_set`.

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

## <a name="pointer"></a>hash_set::p ointer

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Typ, który dostarcza wskaźnik do elementu w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie hash_set.

## <a name="rbegin"></a>hash_set:: rbegin

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca iterator odnoszący się do pierwszego elementu w odwróconej hash_set.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwrócona

Odwrotny iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconym hash_set lub adresowania ostatniego elementu w nieodwróconej hash_set.

### <a name="remarks"></a>Uwagi

`rbegin` jest używany z odwróconym hash_set, tak jak [początek](#begin) jest używany z hash_setem.

Jeśli wartość zwracana `rbegin` jest przypisana do `const_reverse_iterator`, nie można zmodyfikować obiektu hash_set. Jeśli wartość zwracana `rbegin` jest przypisana do `reverse_iterator`, można zmodyfikować obiekt hash_set.

`rbegin` można użyć do iteracji hash_set do tyłu.

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

## <a name="reference"></a>hash_set:: Reference

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

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

## <a name="rend"></a>hash_set:: rend

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w odwróconym hash_set.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwrócona

Odwrotny iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym hash_set (lokalizacja, która poprzedza pierwszy element w nieodwróconym hash_set).

### <a name="remarks"></a>Uwagi

`rend` jest używany z odwróconym hash_set, tak jak [koniec](#end) jest używany z hash_setem.

Jeśli wartość zwracana `rend` jest przypisana do `const_reverse_iterator`, nie można zmodyfikować obiektu hash_set. Jeśli wartość zwracana `rend` jest przypisana do `reverse_iterator`, można zmodyfikować obiekt hash_set. Nie należy wywoływać wartości zwracanej przez `rend`.

`rend` można użyć do przetestowania, czy iterator odwrotny osiągnął koniec jego hash_set.

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

## <a name="reverse_iterator"></a>hash_set:: reverse_iterator

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iteracji przez hash_set w odwrocie.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rbegin](#rbegin) , aby zapoznać się z przykładem sposobu deklarowania i używania `reverse_iterator`.

## <a name="size"></a>hash_set:: size

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca liczbę elementów w hash_set.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwrócona

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

## <a name="size_type"></a>hash_set:: size_type

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dotyczącym [rozmiaru](#size) przykładu sposobu deklarowania i używania `size_type`

## <a name="swap"></a>hash_set:: swap

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Wymienia elementy dwóch hash_sets.

```cpp
void swap(hash_set& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Argument hash_set zapewniający elementy, które mają zostać zamienione na hash_set docelowy.

### <a name="remarks"></a>Uwagi

Funkcja członkowska unieważnia brak odwołań, wskaźników lub iteratorów, które wyznaczają elementy w dwóch hash_sets których elementy są wymieniane.

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

## <a name="upper_bound"></a>hash_set:: upper_bound

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Zwraca iterator do pierwszego elementu w hash_set, który ma klucz, który jest większy niż określony klucz.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*klucz*\
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego hash_set.

### <a name="return-value"></a>Wartość zwrócona

`iterator` lub `const_iterator`, który odnosi się do lokalizacji elementu w hash_set, który jest równy lub większy od klucza argumentu lub który odnosi się do lokalizacji po ostatnim elemencie w hash_set, jeśli nie znaleziono żadnego dopasowania dla klucza.

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

## <a name="value_comp"></a>hash_set:: value_comp

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Pobiera kopię obiektu porównania użytego do uporządkowania wartości elementów w hash_set.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca obiekt funkcji, którego hash_set używa do porządkowania jego elementów, który jest *porównywany*parametrem szablonu.

Aby uzyskać więcej informacji na temat *porównywania*, zobacz sekcję Uwagi w temacie [hash_set Class](../standard-library/hash-set-class.md) .

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członkowską:

`bool operator( const Key& _xVal, const Key& _yVal );`

zwraca **wartość true** , jeśli `_xVal` poprzedza i nie jest równa `_yVal` w kolejności sortowania.

Należy zauważyć, że oba [value_compare](../standard-library/set-class.md#value_compare) i [key_compare](../standard-library/set-class.md#key_compare) są synonimami dla *porównania*parametrów szablonu. Oba typy są dostępne dla klas hash_set i hash_multiset, w których są identyczne, w celu zapewnienia zgodności z klasami hash_map i hash_multimap, gdzie są różne.

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

## <a name="value_compare"></a>hash_set:: value_compare

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Typ, który dostarcza dwa obiekty funkcji, Predykat binarny klasy Compare, który może porównać dwie wartości elementów hash_set, aby określić ich względną kolejność i predykat jednoargumentowy, który miesza elementy.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Uwagi

`value_compare` jest synonimem dla *cech*parametrów szablonu.

Aby uzyskać więcej informacji o *cechach* , zobacz temat [Klasa hash_set](../standard-library/hash-set-class.md) .

Należy zauważyć, że zarówno [key_compare](#key_compare) , jak i `value_compare` są synonimami dla *cech*parametrów szablonu. Oba typy są dostępne dla klas hash_set i hash_multiset, w których są identyczne, w celu zapewnienia zgodności z klasami hash_map i hash_multimap, gdzie są różne.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [value_comp](#value_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania `value_compare`.

## <a name="value_type"></a>hash_set:: value_type

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Typ, który opisuje obiekt przechowywany jako element hash_set w swojej pojemności jako wartość.

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

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
