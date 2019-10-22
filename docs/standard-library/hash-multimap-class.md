---
title: hash_multimap — Klasa
ms.date: 10/18/2018
f1_keywords:
- hash_map/stdext::hash_multimap
- hash_map/stdext::hash_multimap::allocator_type
- hash_map/stdext::hash_multimap::const_iterator
- hash_map/stdext::hash_multimap::const_pointer
- hash_map/stdext::hash_multimap::const_reference
- hash_map/stdext::hash_multimap::const_reverse_iterator
- hash_map/stdext::hash_multimap::difference_type
- hash_map/stdext::hash_multimap::iterator
- hash_map/stdext::hash_multimap::key_compare
- hash_map/stdext::hash_multimap::key_type
- hash_map/stdext::hash_multimap::mapped_type
- hash_map/stdext::hash_multimap::pointer
- hash_map/stdext::hash_multimap::reference
- hash_map/stdext::hash_multimap::reverse_iterator
- hash_map/stdext::hash_multimap::size_type
- hash_map/stdext::hash_multimap::value_type
- hash_map/stdext::hash_multimap::begin
- hash_map/stdext::hash_multimap::cbegin
- hash_map/stdext::hash_multimap::cend
- hash_map/stdext::hash_multimap::clear
- hash_map/stdext::hash_multimap::count
- hash_map/stdext::hash_multimap::crbegin
- hash_map/stdext::hash_multimap::crend
- hash_map/stdext::hash_multimap::emplace
- hash_map/stdext::hash_multimap::emplace_hint
- hash_map/stdext::hash_multimap::empty
- hash_map/stdext::hash_multimap::end
- hash_map/stdext::hash_multimap::equal_range
- hash_map/stdext::hash_multimap::erase
- hash_map/stdext::hash_multimap::find
- hash_map/stdext::hash_multimap::get_allocator
- hash_map/stdext::hash_multimap::insert
- hash_map/stdext::hash_multimap::key_comp
- hash_map/stdext::hash_multimap::lower_bound
- hash_map/stdext::hash_multimap::max_size
- hash_map/stdext::hash_multimap::rbegin
- hash_map/stdext::hash_multimap::rend
- hash_map/stdext::hash_multimap::size
- hash_map/stdext::hash_multimap::swap
- hash_map/stdext::hash_multimap::upper_bound
- hash_map/stdext::hash_multimap::value_comp
helpviewer_keywords:
- stdext::hash_multimap
- stdext::hash_multimap::allocator_type
- stdext::hash_multimap::const_iterator
- stdext::hash_multimap::const_pointer
- stdext::hash_multimap::const_reference
- stdext::hash_multimap::const_reverse_iterator
- stdext::hash_multimap::difference_type
- stdext::hash_multimap::iterator
- stdext::hash_multimap::key_compare
- stdext::hash_multimap::key_type
- stdext::hash_multimap::mapped_type
- stdext::hash_multimap::pointer
- stdext::hash_multimap::reference
- stdext::hash_multimap::reverse_iterator
- stdext::hash_multimap::size_type
- stdext::hash_multimap::value_type
- stdext::hash_multimap::begin
- stdext::hash_multimap::cbegin
- stdext::hash_multimap::cend
- stdext::hash_multimap::clear
- stdext::hash_multimap::count
- stdext::hash_multimap::crbegin
- stdext::hash_multimap::crend
- stdext::hash_multimap::emplace
- stdext::hash_multimap::emplace_hint
- stdext::hash_multimap::empty
- stdext::hash_multimap::end
- stdext::hash_multimap::equal_range
- stdext::hash_multimap::erase
- stdext::hash_multimap::find
- stdext::hash_multimap::get_allocator
- stdext::hash_multimap::insert
- stdext::hash_multimap::key_comp
- stdext::hash_multimap::lower_bound
- stdext::hash_multimap::max_size
- stdext::hash_multimap::rbegin
- stdext::hash_multimap::rend
- stdext::hash_multimap::size
- stdext::hash_multimap::swap
- stdext::hash_multimap::upper_bound
- stdext::hash_multimap::value_comp
ms.assetid: f41a6db9-67aa-43a3-a3c5-dbfe9ec3ae7d
ms.openlocfilehash: b42dd5ba4aa3df12e3ef1aba930b2214dde19756
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687970"
---
# <a name="hash_multimap-class"></a>hash_multimap — Klasa

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Klasa kontenera hash_multimap jest rozszerzeniem C++ standardowej biblioteki i służy do przechowywania oraz szybkiego pobierania danych z kolekcji, w której każdy element jest parą z kluczem sortowania, którego wartość nie musi być unikatowa i skojarzona wartość danych.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare <Key, less <Key>>,
    class Allocator=allocator <pair  <const Key, Type>>>
class hash_multimap
```

### <a name="parameters"></a>Parametry

*Klucz* \
Typ danych klucza, który ma być przechowywany w hash_multimap.

*Typ* \
Typ danych elementu, który ma być przechowywany w hash_multimap.

*Cechy* \
Typ, który zawiera dwa obiekty funkcji, jedną z *cech* klasy, która jest w stanie porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność i funkcję mieszania, która jest predykatem jednoargumentowym dla wartości elementów do niepodpisanych liczb całkowitych Wpisz `size_t`. Ten argument jest opcjonalny, a `hash_compare<Key, less<Key>>` jest wartością domyślną.

@No__t_1 *alokatora*
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji hash_multimap's i dealokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to `allocator<pair <const Key, Type>>`.

## <a name="remarks"></a>Uwagi

Hash_multimap:

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.

- Skrót, ponieważ jego elementy są pogrupowane w zasobniki na podstawie wartości funkcji skrótu zastosowanej do wartości klucza elementów.

- Wielokrotna, ponieważ jej elementy nie muszą mieć unikatowych kluczy, więc jedna wartość klucza może mieć wiele wartości elementów danych z nią skojarzonych.

- Kojarzy Kontener asocjacyjny, ponieważ jego wartości elementów są różne od wartości klucza.

- Szablon klasy, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Główną zaletą tworzenia skrótów w porównaniu z sortowaniem jest większa wydajność. pomyślne wykonywanie skrótów wykonuje wstawienia, usunięcia i znajduje się w stałym średnim czasie w porównaniu z czasem proporcjonalnym do logarytmu liczby elementów w kontenerze dla technik sortowania. Wartość elementu w hash_multimap, ale nie skojarzona z nim wartość klucza, może zostać zmieniona bezpośrednio. Zamiast tego, wartości kluczy skojarzone ze starymi elementami muszą zostać usunięte, a nowe wartości klucza skojarzone z nowymi wstawionymi elementami.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Przyłączone Kontenery asocjacyjne są zoptymalizowane pod kątem operacji wyszukiwania, wstawiania i usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, są wydajne, gdy są używane z dobrze zaprojektowaną funkcją skrótu, wykonując je w czasie, który jest obliczany jako stała średnia i nie zależy od liczby elementów w kontenerze. Dobrze zaprojektowana funkcja skrótu generuje jednorodną dystrybucję wartości skrótów i minimalizuje liczbę kolizji, w których występuje kolizja, gdy wartości unikatowego klucza są mapowane na tę samą wartość skrótu. W najgorszym przypadku z najgorszą możliwą funkcją skrótu liczba operacji jest proporcjonalna do liczby elementów w sekwencji (czas liniowy).

Hash_multimap powinien być kontenerem asocjacyjnym wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Modelem dla tego typu struktury jest uporządkowana lista słów kluczowych ze skojarzonymi wartościami ciągów, dostarczająca np. definicje, w których słowa nie były zawsze zdefiniowane unikalnie. Jeśli zamiast tego, słowa kluczowe zostały jednoznacznie zdefiniowane, dzięki czemu klucze były unikatowe, a następnie hash_map będzie kontenerem wyboru. Jeśli z drugiej strony jest przechowywanych tylko Lista wyrazów, hash_set będzie prawidłowym kontenerem. Jeśli dozwolone jest wiele wystąpień wyrazów, hash_multiset będzie odpowiednią strukturą kontenera.

Hash_multimap porządkuje sekwencję, która kontroluje, wywołując zapisany skrót `Traits` obiektu typu [value_compare](../standard-library/value-compare-class.md). Dostęp do tego przechowywanego obiektu można uzyskać, wywołując funkcję elementu członkowskiego [key_comp](../standard-library/hash-map-class.md#key_comp). Taki obiekt funkcji musi działać tak samo jak obiekt klasy [hash_compare](../standard-library/hash-compare-class.md) `<Key, less<Key>>`. W odniesieniu do wszystkich wartości `Key` typu `Key`, wywołanie `Traits (Key)` daje rozkład wartości typu `size_t`.

Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Powoduje to porządkowanie między nierównoważnymi elementami. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarny f (x, y) jest obiektem funkcji, który ma dwa obiekty argumentów `x` i `y` i wartość zwracaną **true** lub **false**. Kolejność nałożona na hash_multimap jest ściśle słabym porządkowaniem, jeśli Predykat binarny jest niezwrotny, antysymetryczny i przechodni oraz jeśli równoważność jest przechodnia, gdzie dwa obiekty `x` i `y` są zdefiniowane jako równoważne, gdy zarówno f (x, y), jak i f (y , x) mają **wartość false**. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

Rzeczywista kolejność elementów w kontrolowanej sekwencji zależy od funkcji skrótu, funkcji porządkowania i bieżącego rozmiaru tabeli skrótów przechowywanej w obiekcie kontenera. Nie można określić bieżącego rozmiaru tabeli skrótów, dlatego nie można ogólnie przewidzieć kolejności elementów w kontrolowanej sekwencji. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Iterator dostarczony przez klasę hash_multimap jest iteratorem dwukierunkowym, ale funkcje składowych klasy [INSERT](#insert) i [hash_multimap](#hash_multimap) mają wersje przyjmujące jako parametry szablonu słabszy iterator danych wejściowych, którego wymagania dotyczące funkcjonalności są mniejsze niż te gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma własne hash_multimap wymagania, a algorytmy, które z nimi pracują, muszą ograniczyć ich założenia do wymagań dostarczonych przez ten typ iteratora. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny hash_multimap funkcjonalności, ale jest wystarczający, aby można było mówić istotnie o zakresie iteratorów `[First, Last)` w kontekście funkcji składowych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[hash_multimap](#hash_multimap)|Tworzy listę o określonym rozmiarze lub z elementami określonej wartości lub z określonym `allocator` lub jako kopią innego `hash_multimap`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje klasę `allocator` dla obiektu `hash_multimap`.|
|[const_iterator](#const_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytywać `const` element w `hash_multimap`.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do elementu **const** w `hash_multimap`.|
|[const_reference](#const_reference)|Typ, który dostarcza odwołanie do elementu **const** przechowywanego w `hash_multimap` do odczytu i wykonywania operacji **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny element **const** w `hash_multimap`.|
|[difference_type](#difference_type)|Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów `hash_multimap` w zakresie między elementami wskazywanymi przez Iteratory.|
|[Iterator](#iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w `hash_multimap`.|
|[key_compare](#key_compare)|Typ, który dostarcza obiekt funkcji, który może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `hash_multimap`.|
|[key_type](#key_type)|Typ, który opisuje obiekt klucza sortowania, który stanowi każdy element `hash_multimap`.|
|[mapped_type](#mapped_type)|Typ, który reprezentuje typ danych przechowywany w `hash_multimap`.|
|[przytrzymaj](#pointer)|Typ, który dostarcza wskaźnik do elementu w `hash_multimap`.|
|[odwoła](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w `hash_multimap`.|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej `hash_multimap`.|
|[size_type](#size_type)|Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w `hash_multimap`.|
|[value_type](#value_type)|Typ, który dostarcza obiekt funkcji, który może porównać dwa elementy jako klucze sortowania, aby określić ich względną kolejność w `hash_multimap`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[zaczną](#begin)|Zwraca iterator odnoszący się do pierwszego elementu w `hash_multimap`.|
|[cbegin](#cbegin)|Zwraca iterator const odnoszący się do pierwszego elementu w `hash_multimap`.|
|[cend](#cend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w `hash_multimap`.|
|[Wyczyść](#clear)|Usuwa wszystkie elementy `hash_multimap`.|
|[liczbą](#count)|Zwraca liczbę elementów w `hash_multimap`, których klucz pasuje do klucza określonego przez parametr.|
|[crbegin —](#crbegin)|Zwraca iterator const odnoszący się do pierwszego elementu w odwróconej `hash_multimap`.|
|[crend](#crend)|Zwraca iterator const, który odnosi się do lokalizacji następującej po ostatnim elemencie w odwróconym `hash_multimap`.|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do `hash_multimap`.|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do `hash_multimap` z wskazówką dotyczącą położenia.|
|[ciągiem](#empty)|Testuje, czy `hash_multimap` jest pusty.|
|[punktów](#end)|Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w `hash_multimap`.|
|[equal_range](#equal_range)|Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w `hash_multimap`.|
|[Wyłączanie](#erase)|Usuwa element lub zakres elementów w `hash_multimap` z określonych pozycji|
|[wyświetlić](#find)|Zwraca iterator odnoszący się do lokalizacji elementu w `hash_multimap`, który ma klucz równoważny określonemu kluczowi.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu `allocator` użytego do skonstruowania `hash_multimap`.|
|[wstawienia](#insert)|Wstawia element lub zakres elementów do `hash_multimap` w określonym położeniu.|
|[key_comp](#key_comp)|Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w `hash_multimap`.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu w `hash_multimap`, którego wartość klucza jest równa lub większa od określonego klucza.|
|[max_size](#max_size)|Zwraca maksymalną długość `hash_multimap`.|
|[rbegin](#rbegin)|Zwraca iterator odnoszący się do pierwszego elementu w odwróconej `hash_multimap`.|
|[rend](#rend)|Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w odwróconym `hash_multimap`.|
|[zmienia](#size)|Określa nowy rozmiar `hash_multimap`.|
|[wymiany](#swap)|Wymienia elementy dwóch `hash_multimap`s.|
|[upper_bound](#upper_bound)|Zwraca iterator do pierwszego elementu w `hash_multimap`, którego wartość klucza jest większa od określonego klucza.|
|[value_comp](#value_comp)|Pobiera kopię obiektu porównania użytego do uporządkowania wartości elementów w `hash_multimap`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[hash_multimap:: operator =](#op_eq)|Zastępuje elementy `hash_multimap` kopią innego `hash_multimap`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_map >

**Przestrzeń nazw:** stdext

## <a name="allocator_type"></a>hash_multimap::allocator_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, który reprezentuje klasę alokatora dla obiektu hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type` jest synonimem dla `Allocator` parametru szablonu.

Aby uzyskać więcej informacji na `Allocator`, zobacz sekcję Uwagi w temacie [Klasa hash_multimap](../standard-library/hash-multimap-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [get_allocator](#get_allocator) przy użyciu `allocator_type`.

## <a name="begin"></a>hash_multimap:: BEGIN

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca iterator odnoszący się do pierwszego elementu w hash_multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pierwszego elementu w hash_multimap lub lokalizacji po pomyślnym wykonaniu pustej hash_multimap.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana `begin` jest przypisana do `const_iterator`, nie można modyfikować elementów w obiekcie hash_multimap. Jeśli wartość zwracana `begin` jest przypisana do `iterator`, można modyfikować elementy w obiekcie hash_multimap.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_begin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 0, 0 ) );
   hm1.insert ( Int_Pair ( 1, 1 ) );
   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.begin ( );
   cout << "The first element of hm1 is " << hm1_cIter -> first
        << "." << endl;

   hm1_Iter = hm1.begin ( );
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.begin ( );
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.begin( );
   cout << "The first element of hm1 is now " << hm1_cIter -> first
        << "." << endl;
}
```

```Output
The first element of hm1 is 0.
The first element of hm1 is now 1.
```

## <a name="cbegin"></a>hash_multimap:: cbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca iterator const odnoszący się do pierwszego elementu w hash_multimap.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

A const iteratora dwukierunkowego odwołującego się do pierwszego elementu w [hash_multimap](../standard-library/hash-multimap-class.md) lub lokalizacja powiodła się puste `hash_multimap`.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_cbegin.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.cbegin ( );
   cout << "The first element of hm1 is "
        << hm1_cIter -> first << "." << endl;
   }
```

```Output
The first element of hm1 is 2.
```

## <a name="cend"></a>hash_multimap:: cend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w hash_multimap.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

A const iteratora dwukierunkowego, który odnosi się do lokalizacji po ostatnim elemencie w [hash_multimap](../standard-library/hash-multimap-class.md). Jeśli `hash_multimap` jest puste, a następnie `hash_multimap::cend == hash_multimap::begin`.

### <a name="remarks"></a>Uwagi

`cend` służy do sprawdzania, czy iterator osiągnął koniec jego hash_multimap.

Nie należy wywoływać wartości zwracanej przez `cend`.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_cend.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.cend( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;
   }
```

```Output
The value of last element of hm1 is 30.
```

## <a name="clear"></a>hash_multimap:: Clear

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Usuwa wszystkie elementy hash_multimap.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie funkcji hash_multimap:: Clear member.

```cpp
// hash_multimap_clear.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 4));

    i = hm1.size();
    cout << "The size of the hash_multimap is initially "
         << i  << "." << endl;

    hm1.clear();
    i = hm1.size();
    cout << "The size of the hash_multimap after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the hash_multimap is initially 2.
The size of the hash_multimap after clearing is 0.
```

## <a name="const_iterator"></a>hash_multimap::const_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać element **const** w hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Uwagi

Typu `const_iterator` nie można użyć do zmodyfikowania wartości elementu.

@No__t_0 zdefiniowane przez hash_multimap wskazują obiekty [value_type](#value_type), które są typu `pair<const Key, Type>`. Wartość klucza jest dostępna za pomocą pierwszej pary elementu członkowskiego, a wartość mapowanego elementu jest dostępna za pomocą drugiego elementu członkowskiego pary.

Aby usunąć odwołanie do `const_iterator` `cIter` wskazujące element w hash_multimap, użyj operatora `->`.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `cIter->first`, która jest równoważna z `(*cIter).first`. Aby uzyskać dostęp do wartości mapowanej podstawy dla elementu, użyj `cIter->second`, który jest odpowiednikiem `(*cIter).second`.

### <a name="example"></a>Przykład

Zapoznaj [się](#begin) z przykładem dla przykładu korzystającego z `const_iterator`.

## <a name="const_pointer"></a>hash_multimap::const_pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza wskaźnik do elementu **const** w hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typu `const_pointer` nie można użyć do zmodyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie hash_multimap.

## <a name="const_reference"></a>hash_multimap::const_reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza odwołanie do elementu **const** przechowywanego w hash_multimap do odczytu i wykonywania operacji **const** .

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multimap_const_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin() -> second );

   cout << "The data value of 1st element in the hash_multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of 1st element in the hash_multimap is 10.
```

## <a name="const_reverse_iterator"></a>hash_multimap::const_reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny element **const** w hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartości elementu i służy do iteracji przez hash_multimap w odwrocie.

@No__t_0 zdefiniowane przez hash_multimap wskazują na obiekty [value_type](#value_type), które są typu `pair<const Key, Type>`, których pierwszy element członkowski jest kluczem do elementu, a drugi element członkowski jest zmapowaną podstawą zawartą w elemencie.

Aby usunąć odwołanie do `const_reverse_iterator` `crIter` wskazujące element w hash_multimap, użyj operatora `->`.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `crIter->first`, która jest równoważna z `(*crIter).first`. Aby uzyskać dostęp do wartości mapowanej podstawy dla elementu, użyj `crIter->second`, który jest odpowiednikiem `(*crIter).second`.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rend](#rend) , aby zapoznać się z przykładem sposobu deklarowania i używania `const_reverse_iterator`.

## <a name="count"></a>hash_multimap:: Count

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca liczbę elementów w hash_multimap, których klucz pasuje do klucza określonego przez parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*klucz* \
Klucz elementów do dopasowania z hash_multimap.

### <a name="return-value"></a>Wartość zwracana

1 Jeśli hash_multimap zawiera element, którego klucz sortowania jest zgodny z kluczem parametru; 0, jeśli hash_multimap nie zawiera elementu z pasującym kluczem.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę elementów w zakresie

**[lower_bound (** `key` **), upper_bound (** `key` **))**

*klucz wartości klucza*.

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie funkcji składowej hash_multimap:: Count.

```cpp
// hash_multimap_count.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 1));
    hm1.insert(Int_Pair(1, 4));
    hm1.insert(Int_Pair(2, 1));

    // Elements do not need to have unique keys in hash_multimap,
    // so duplicates are allowed and counted
    i = hm1.count(1);
    cout << "The number of elements in hm1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hm1.count(2);
    cout << "The number of elements in hm1 with a sort key of 2 is: "
         << i << "." << endl;

    i = hm1.count(3);
    cout << "The number of elements in hm1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hm1 with a sort key of 1 is: 2.
The number of elements in hm1 with a sort key of 2 is: 2.
The number of elements in hm1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>hash_multimap:: crbegin —

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca iterator const odnoszący się do pierwszego elementu w odwróconej hash_multimap.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stałe odwrotne Iteratory, odnoszące się do pierwszego elementu w odwróconej [hash_multimap](../standard-library/hash-multimap-class.md) lub adresowania ostatniego elementu w nieodwróconej `hash_multimap`.

### <a name="remarks"></a>Uwagi

`crbegin` jest używany z odwróconym hash_multimap tak samo jak [hash_multimap:: BEGIN](#begin) jest używany z `hash_multimap`.

Z wartością zwracaną `crbegin` nie można zmodyfikować obiektu `hash_multimap`.

`crbegin` można użyć do iteracji `hash_multimap` do tyłu.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_crbegin.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crbegin( );
   cout << "The first element of the reversed hash_multimap hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_multimap hm1 is 3.
```

## <a name="crend"></a>hash_multimap:: crend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej hash_multimap.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Nieodwrócony iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej [hash_multimap](../standard-library/hash-multimap-class.md) (lokalizacja, która poprzedza pierwszy element w nieodwróconym `hash_multimap`).

### <a name="remarks"></a>Uwagi

`crend` jest używany z odwróconym hash_multimap tak samo jak [hash_multimap:: end](#end) jest używany z hash_multimap.

Z wartością zwracaną `crend` nie można zmodyfikować obiektu `hash_multimap`.

`crend` można użyć do przetestowania, czy iterator odwrotny osiągnął koniec hash_multimap.

Nie należy wywoływać wartości zwracanej przez `crend`.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_crend.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crend( );
   hm1_crIter--;
   cout << "The last element of the reversed hash_multimap hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_multimap hm1 is 3.
```

## <a name="difference_type"></a>hash_multimap::d ifference_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów hash_multimap w zakresie między elementami wskazywanymi przez Iteratory.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

@No__t_0 jest typem zwracanym podczas odejmowania lub zwiększania przez Iteratory kontenera. @No__t_0 jest zwykle używany do reprezentowania liczby elementów w zakresie *[First, Last)* między iteratorami `first` i `last`, zawiera element wskazywany przez `first` i zakres elementów do, ale nie obejmuje , element wskazywany przez `last`.

Należy zauważyć, że chociaż `difference_type` jest dostępny dla wszystkich iteratorów, które spełniają wymagania iteratora danych wejściowych, który obejmuje klasę iteratorów dwukierunkowych obsługiwanych przez kontenery odwracalne, takie jak zestaw, odejmowanie między iteratorami jest obsługiwane tylko przez Iteratory dostępu swobodnego zapewniane przez kontener dostępu swobodnego, taki jak wektor.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_difference_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>
#include <algorithm>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(3, 20));

    // The following will insert, because map keys
    // do not need to be unique
    hm1.insert(Int_Pair(2, 30));

    hash_multimap<int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;
    hm1_bIter = hm1.begin();
    hm1_eIter = hm1.end();

    // Count the number of elements in a hash_multimap
    hash_multimap<int, int>::difference_type df_count = 0;
    hm1_Iter = hm1.begin();
    while (hm1_Iter != hm1_eIter)
    {
        df_count++;
        hm1_Iter++;
    }

    cout << "The number of elements in the hash_multimap hm1 is: "
         << df_count << "." << endl;

    cout << "The keys of the mapped elements are:";
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();
        hm1_Iter++)
        cout << " " << hm1_Iter-> first;
    cout << "." << endl;

    cout << "The values of the mapped elements are:";
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();
        hm1_Iter++)
        cout << " " << hm1_Iter-> second;
    cout << "." << endl;
}
```

```Output
The number of elements in the hash_multimap hm1 is: 4.
The keys of the mapped elements are: 1 2 2 3.
The values of the mapped elements are: 10 20 30 20.
```

## <a name="emplace"></a>hash_multimap:: emplace

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Wstawia element skonstruowany w miejscu do hash_multimap.

```cpp
template <class ValTy>
iterator emplace(ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*użyte*|Wartość służąca do przenoszenia elementu konstrukcja, który ma zostać wstawiony do [hash_multimap](../standard-library/hash-multimap-class.md).|

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska `emplace` zwraca iterator, który wskazuje na pozycję, w której został wstawiony nowy element.

### <a name="remarks"></a>Uwagi

[Hash_multimap:: value_type](#value_type) elementu to para, tak aby wartość elementu była uporządkowaną parą z pierwszym składnikiem równym wartości klucza i drugi składnik równy wartości danych elementu.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_emplace.cpp
// compile with: /EHsc
#include<hash_multimap>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(move(is1));
    cout << "After the emplace, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
1 => a
```

## <a name="emplace_hint"></a>hash_multimap::emplace_hint

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Wstawia element skonstruowany w miejscu do elementu hash_multimap z wskazówką dotyczącą położenia.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*użyte*|Wartość służąca do przenoszenia elementu konstruowania do [hash_multimap](../standard-library/hash-multimap-class.md) , chyba że `hash_multimap` już zawiera ten element (lub, bardziej ogólnie, element, którego klucz jest równoważny).|
|*_Where*|Wskazówka dotycząca miejsca, w którym rozpoczyna się wyszukiwanie poprawnego punktu wstawiania.|

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska [hash_multimap:: emplace](#emplace) zwraca iterator, który wskazuje na pozycję, w której nowy element został wstawiony do `hash_multimap`.

### <a name="remarks"></a>Uwagi

[Hash_multimap:: value_type](#value_type) elementu to para, tak aby wartość elementu była uporządkowaną parą z pierwszym składnikiem równym wartości klucza i drugi składnik równy wartości danych elementu.

Wstawianie może odbywać się w amortyzowanym stałym czasie, a nie w czasie logarytmu, jeśli punkt wstawiania następuje zaraz po *_Where*.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_emplace_hint.cpp
// compile with: /EHsc
#include<hash_multimap>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(hm1.begin(), move(is1));
    cout << "After the emplace insertion, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
1 => a
```

## <a name="empty"></a>hash_multimap:: Empty

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Testuje, czy element hash_multimap jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true** , jeśli hash_multimap jest pusta; **Fałsz** , jeśli hash_multimap nie jest pusty.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multimap_empty.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2;

   typedef pair <int, int> Int_Pair;
   hm1.insert ( Int_Pair ( 1, 1 ) );

   if ( hm1.empty( ) )
      cout << "The hash_multimap hm1 is empty." << endl;
   else
      cout << "The hash_multimap hm1 is not empty." << endl;

   if ( hm2.empty( ) )
      cout << "The hash_multimap hm2 is empty." << endl;
   else
      cout << "The hash_multimap hm2 is not empty." << endl;
}
```

```Output
The hash_multimap hm1 is not empty.
The hash_multimap hm2 is empty.
```

## <a name="end"></a>hash_multimap:: end

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca iterator, który odnosi się do lokalizacji po ostatnim elemencie w hash_multimap.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w hash_multimap. Jeśli hash_multimap jest pusty, a następnie hash_multimap:: end = = hash_multimap:: BEGIN.

### <a name="remarks"></a>Uwagi

`end` służy do sprawdzania, czy iterator osiągnął koniec jego hash_multimap.

Nie należy wywoływać wartości zwracanej przez `end`.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_end.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;

   hm1_Iter = hm1.end( );
   hm1_Iter--;
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.end ( );
   // hm1_cIter--;
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is now "
        << hm1_cIter -> second << "." << endl;
}
```

```Output
The value of last element of hm1 is 30.
The value of last element of hm1 is now 20.
```

## <a name="equal_range"></a>hash_multimap::equal_range

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca parę iteratorów odpowiednio do pierwszego elementu w hash_multimap z kluczem, który jest większy niż określony klucz i do pierwszego elementu w hash_multimap, z kluczem, który jest równy lub większy niż klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*klucz* \
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego hash_multimap.

### <a name="return-value"></a>Wartość zwracana

Para iteratorów, takich jak pierwszy to [lower_bound](#lower_bound) klucza, a drugi to [upper_bound](#upper_bound) klucza.

Aby uzyskać dostęp do pierwszego iteratora pary `pr` zwrócone przez funkcję członkowską, należy użyć `pr`. **najpierw** i aby usunąć odwołanie do dolnego powiązanego iteratora, użyj \* (`pr`. **pierwszy**). Aby uzyskać dostęp do drugiego iteratora pary `pr` zwrócone przez funkcję członkowską, należy użyć `pr`. **drugi** i aby usunąć odwołanie do górnego powiązanego iteratora, użyj \* (`pr`. **sekundę**).

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multimap_equal_range.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multimap <int, int> IntMMap;
   IntMMap hm1;
   hash_multimap <int, int> :: const_iterator hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = hm1.equal_range( 2 );

   cout << "The lower bound of the element with a key of 2\n"
        << "in the hash_multimap hm1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with a key of 2\n"
        << "in the hash_multimap hm1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   hm1_RcIter = hm1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << hm1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair "
        << "returned by equal_range( 2 )." << endl;

   p2 = hm1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2
in the hash_multimap hm1 is: 20.
The upper bound of the element with a key of 2
in the hash_multimap hm1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The hash_multimap hm1 doesn't have an element with a key less than 4.
```

## <a name="erase"></a>hash_multimap:: Erase

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Usuwa element lub zakres elementów w hash_multimap z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_Where* \
Pozycja elementu, który ma zostać usunięty z hash_multimap.

*pierwszy* \
Pozycja pierwszego elementu usuniętego z hash_multimap.

*ostatni* \
Umieść tuż poza ostatnim elementem usuniętym z hash_multimap.

*klucz* \
Klucz elementów do usunięcia z hash_multimap.

### <a name="return-value"></a>Wartość zwracana

Dla pierwszych dwóch funkcji składowych, jednokierunkowy iterator, który wyznacza pierwszy element poza elementami usuniętymi lub wskaźnikiem do końca hash_multimap, jeśli taki element nie istnieje.

Dla trzeciej funkcji składowej zwraca liczbę elementów, które zostały usunięte z hash_multimap.

### <a name="remarks"></a>Uwagi

Funkcja członkowska nigdy nie zgłasza wyjątku.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia funkcji składowej hash_multimap:: wymazywania.

```cpp
// hash_multimap_erase.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1, hm2, hm3;
    hash_multimap<int, int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multimap<int, int>::size_type n;
    typedef pair<int, int> Int_Pair;

    for (i = 1; i < 5; i++)
    {
        hm1.insert(Int_Pair (i, i) );
        hm2.insert(Int_Pair (i, i*i) );
        hm3.insert(Int_Pair (i, i-1) );
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hm1.begin();
    hm1.erase(Iter1);

    cout << "After the 2nd element is deleted, "
         << "the hash_multimap hm1 is:";
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hm2.begin();
    Iter2 = --hm2.end();
    hm2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_multimap hm2 is:";
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    hm3.insert(Int_Pair (2, 5));
    n = hm3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multimap hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hm3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hm3.begin();
    hm3.erase(Iter1);

    cout << "After another element with a key equal to that of the"
         << endl;
    cout  << "2nd element is deleted, "
          << "the hash_multimap hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_multimap hm1 is: 1 3 4.
After the middle two elements are deleted, the hash_multimap hm2 is: 1 16.
After the element with a key of 2 is deleted,
the hash_multimap hm3 is: 0 2 3.
The number of elements removed from hm3 is: 2.
After another element with a key equal to that of the
2nd element is deleted, the hash_multimap hm3 is: 0 3.
```

## <a name="find"></a>hash_multimap:: find

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca iterator odnoszący się do pierwszej lokalizacji elementu w hash_multimap, który ma klucz równoważny do określonego klucza.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*klucz* \
Klucz, który ma zostać dopasowany przez klucz sortowania elementu z przeszukiwanego hash_multimap.

### <a name="return-value"></a>Wartość zwracana

Iterator, który odnosi się do pierwszej lokalizacji elementu z określonym kluczem lub lokalizacji, która kończy się na ostatnim elemencie w hash_multimap, jeśli nie znaleziono żadnego dopasowania dla klucza.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator, który odnosi się do elementu w hash_multimap, którego klucz sortowania jest `equivalent` do klucza argumentu pod predykatem binarnym, który wywołuje porządkowanie na podstawie mniejszej niż porównywalnej relacji.

Jeśli wartość zwracana `find` jest przypisana do `const_iterator`, nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracana `find` jest przypisana do `iterator`, można zmodyfikować obiekt hash_multimap.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_find.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(3, 20));
    hm1.insert(Int_Pair(3, 30));

    hm1_RcIter = hm1.find(2);
    cout << "The element of hash_multimap hm1 with a key of 2 is: "
          << hm1_RcIter -> second << "." << endl;

    hm1_RcIter = hm1.find(3);
    cout << "The first element of hash_multimap hm1 with a key of 3 is: "
          << hm1_RcIter -> second << "." << endl;

    // If no match is found for the key, end() is returned
    hm1_RcIter = hm1.find(4);

    if (hm1_RcIter == hm1.end())
        cout << "The hash_multimap hm1 doesn't have an element "
             << "with a key of 4." << endl;
    else
        cout << "The element of hash_multimap hm1 with a key of 4 is: "
             << hm1_RcIter -> second << "." << endl;

    // The element at a specific location in the hash_multimap can be
    // found using a dereferenced iterator addressing the location
    hm1_AcIter = hm1.end();
    hm1_AcIter--;
    hm1_RcIter = hm1.find(hm1_AcIter -> first);
    cout << "The first element of hm1 with a key matching"
         << endl << "that of the last element is: "
         << hm1_RcIter -> second << "." << endl;

    // Note that the first element with a key equal to
    // the key of the last element is not the last element
    if (hm1_RcIter == --hm1.end())
        cout << "This is the last element of hash_multimap hm1."
             << endl;
    else
        cout << "This is not the last element of hash_multimap hm1."
             << endl;
}
```

```Output
The element of hash_multimap hm1 with a key of 2 is: 20.
The first element of hash_multimap hm1 with a key of 3 is: 20.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key matching
that of the last element is: 20.
This is not the last element of hash_multimap hm1.
```

## <a name="get_allocator"></a>hash_multimap::get_allocator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca kopię obiektu alokatora używanego do konstruowania hash_multimap.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez hash_multimap.

### <a name="remarks"></a>Uwagi

Przypisania klasy hash_multimap określają sposób, w jaki Klasa zarządza magazynem. Domyślne przydzielenie klas kontenerów C++ biblioteki standardowej jest wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym C++ tematem.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_get_allocator.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int>::allocator_type hm1_Alloc;
   hash_multimap <int, int>::allocator_type hm2_Alloc;
   hash_multimap <int, double>::allocator_type hm3_Alloc;
   hash_multimap <int, int>::allocator_type hm4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> hm2;
   hash_multimap <int, double> hm3;

   hm1_Alloc = hm1.get_allocator( );
   hm2_Alloc = hm2.get_allocator( );
   hm3_Alloc = hm3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << " before free memory is exhausted: "
        << hm2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << " before free memory is exhausted: "
        << hm3.max_size( ) <<  "." << endl;

   // The following line creates a hash_multimap hm4
   // with the allocator of hash_multimap hm1.
   hash_multimap <int, int> hm4( less<int>( ), hm1_Alloc );

   hm4_Alloc = hm4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hm1_Alloc == hm4_Alloc )
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

## <a name="hash_multimap"></a>hash_multimap::hash_multimap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Konstruuje hash_multimap, który jest pusty lub jest kopią całości lub części innej hash_multimap.

```cpp
hash_multimap();

explicit hash_multimap(
    const Compare& Comp);

hash_multimap(
    const Compare& Comp,
    const Allocator& Al);

hash_multimap(
    const hash_multimap& Right);

hash_multimap(
    hash_multimap&& Right);

hash_multimap(
    initializer_list<Type> IList);

hash_multimap(
    initializer_list<Type> IList,
    const Compare& Comp);

hash_multimap(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last,
    const Compare& Comp);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last,
    const Compare& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Wsp*|Klasa alokatora magazynu, która ma być używana dla tego obiektu hash_multimap, który jest wartością domyślną `Allocator`.|
|*Przepisów*|Funkcja porównania typu `const Traits` użyta do uporządkowania elementów w mapie, których wartością domyślną jest `Traits`.|
|*Kliknij*|Mapa, której skonstruowany zestaw ma być kopią.|
|*Pierwszego*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*Ostatniego*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|
|*IList*|Initializer_list do skopiowania.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują typ obiektu alokatora, który zarządza magazynem pamięci dla hash_multimap i który może być później zwracany przez wywołanie [get_allocator](#get_allocator). Parametr alokatora jest często pomijany w deklaracjach klas i makra wstępnego przetwarzania są używane do podstawiania alternatywnych metod przydzielania.

Wszystkie konstruktory inicjują hash_multimap.

Wszystkie konstruktory przechowują obiekt funkcji typu `Traits`, który jest używany do ustanowienia zamówienia między kluczami hash_multimap, a później może być zwracany przez wywołanie [key_comp](#key_comp).

Pierwsze trzy konstruktory określają pustą początkową hash_multimap; Druga określa typ funkcji porównywania (*COMP*), która ma zostać użyta w celu ustalenia kolejności elementów, a trzeci jawnie określa typ alokatora (`_Al`), który ma być używany. Słowo kluczowe `explicit` pomija niektórych rodzajów konwersji typu automatycznego.

Czwarty Konstruktor określa kopię `Right` hash_multimap.

Następne trzy konstruktory kopiują zakres `First, Last)` mapy z rosnącą jawnością w określaniu typu funkcji porównania klas `Traits` i alokatora.

Ósmy Konstruktor przenosi `Right` hash_multimap.

Ostatnie trzy konstruktory używają initializer_list.

## <a name="insert"></a>hash_multimap:: INSERT

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Wstawia element lub zakres elementów do hash_multimap.

```cpp
iterator insert(
    const value_type& Val);

iterator insert(
    const_iterator Where,
    const value_type& Val);void insert(
    initializer_list<value_type> IList);

template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

template <class ValTy>
iterator insert(
    ValTy&& Val);

template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Użyte*|Wartość elementu, który ma zostać wstawiony do hash_multimap, chyba że już zawiera ten element lub bardziej ogólnie, chyba że zawiera już element, którego klucz jest równoważny uporządkowany.|
|*Miejscu*|Wskazówka dotycząca miejsca rozpoczęcia wyszukiwania w poszukiwaniu poprawnego punktu wstawiania.|
|*Pierwszego*|Pozycja pierwszego elementu, który ma zostać skopiowany z mapy.|
|*Ostatniego*|Pozycja tuż poza ostatnim elementem, który ma zostać skopiowany z mapy.|

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie `insert` funkcje członkowskie zwracają iterator, który wskazuje na pozycję, w której został wstawiony nowy element.

Trzecia funkcja członkowska używa elementu initializer_list dla elementów do wstawienia.

Czwarta funkcja członkowska wstawia sekwencję wartości elementów do mapy, która odnosi się do każdego elementu, który jest adresowany do zakresu `[First, Last)` określonego zestawu.

Ostatnie dwa `insert` funkcje członkowskie zachowują się tak samo jak dwa pierwsze, z tym wyjątkiem, że są one przenoszone.

### <a name="remarks"></a>Uwagi

[Value_type](#value_type) elementu to para, dzięki czemu wartość elementu będzie przymówionej pary, w której pierwszy składnik jest równy wartości klucza, a drugi składnik jest równy wartości danych elementu.

Wstawianie może odbywać się w amortyzowanym stałym czasie dla wskazówki `insert`, zamiast czasu logarytmu, jeśli punkt wstawiania następuje zaraz po tym *miejscu*.

## <a name="iterator"></a>hash_multimap:: iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Uwagi

@No__t_0 zdefiniowane przez hash_multimap wskazują obiekty [value_type](#value_type), które są typu `pair` \< **const, typ**>, którego pierwszy element członkowski jest kluczem do elementu, a drugi element członkowski jest zmapowaną podstawą przechowywaną przez element.

Aby usunąć odwołanie do **iteratora** `Iter` wskazujące element w hash_multimap, użyj operatora `->`.

Aby uzyskać dostęp do wartości klucza dla elementu, należy**najpierw**użyć `Iter`  -> , który jest odpowiednikiem (\* `Iter`). **najpierw**. Aby uzyskać dostęp do wartości mapowanej podstawy dla elementu, użyj `Iter`  -> **sekunda**, która jest równoważna z (\* `Iter`). **najpierw**.

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zapoznaj [się](#begin) z przykładem dotyczącym sposobu deklarowania i używania `iterator`.

## <a name="key_comp"></a>hash_multimap::key_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w hash_multimap.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt Function, którego hash_multimap używa do porządkowania jego elementów.

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członkowską

**operator bool (klucz const &** `left` **, klucz const &** `right` **);**

zwraca **wartość true** , jeśli `left` poprzedza i nie jest równa `right` w kolejności sortowania.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_key_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;
   hash_multimap <int, int, hash_compare<int, less<int>>
      >::key_compare kc1 = hm1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true,\n"
           << "where kc1 is the function object of hm1.\n"
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false,\n"
           << "where kc1 is the function object of hm1.\n"
           << endl;
   }

   hash_multimap <int, int, hash_compare<int, greater<int>>> hm2;
   hash_multimap <int, int, hash_compare<int, greater<int>>
      >::key_compare kc2 = hm2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true,\n"
           << "where kc2 is the function object of hm2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false,\n"
           << "where kc2 is the function object of hm2."
           << endl;
   }
}
```

## <a name="key_compare"></a>hash_multimap::key_compare

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza obiekt funkcji, który może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w hash_multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare` jest synonimem dla *cech*parametrów szablonu.

Aby uzyskać więcej informacji o *cechach* , zobacz temat [Klasa hash_multimap](../standard-library/hash-multimap-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [key_comp](#key_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_compare`.

## <a name="key_type"></a>hash_multimap::key_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, który opisuje obiekt klucza sortowania, który stanowi każdy element hash_multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type` jest synonimem dla *klucza*parametru szablonu.

Aby uzyskać więcej informacji o *kluczu*, zobacz sekcję Uwagi w temacie [Klasa hash_multimap](../standard-library/hash-multimap-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [value_type](#value_type) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_compare`.

## <a name="lower_bound"></a>hash_multimap::lower_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca iterator do pierwszego elementu w hash_multimap z kluczem, który jest równy lub większy niż określony klucz.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*klucz* \
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego hash_multimap.

### <a name="return-value"></a>Wartość zwracana

[Iterator](#iterator) lub [const_iterator](#const_iterator) , który odnosi się do lokalizacji elementu w hash_multimap, z kluczem, który jest równy lub większy od klucza argumentu lub który odnosi się do lokalizacji po ostatnim elemencie w hash_multimap, jeśli nie ma dopasowania znaleziono klucz.

Jeśli wartość zwracana `lower_bound` jest przypisana do `const_iterator`, nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracana `lower_bound` jest przypisana do `iterator`, można zmodyfikować obiekt hash_multimap.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multimap_lower_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: const_iterator hm1_AcIter,
      hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.lower_bound( 2 );
   cout << "The element of hash_multimap hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   hm1_RcIter = hm1.lower_bound( 3 );
   cout << "The first element of hash_multimap hm1 with a key of 3 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.lower_bound( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_multimap can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1.lower_bound( hm1_AcIter -> first );
   cout << "The first element of hm1 with a key matching"
        << endl << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( hm1_RcIter == --hm1.end( ) )
      cout << "This is the last element of hash_multimap hm1."
           << endl;
   else
      cout << "This is not the last element of hash_multimap hm1."
           << endl;
}
```

```Output
The element of hash_multimap hm1 with a key of 2 is: 20.
The first element of hash_multimap hm1 with a key of 3 is: 20.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key matching
that of the last element is: 20.
This is not the last element of hash_multimap hm1.
```

## <a name="mapped_type"></a>hash_multimap::mapped_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, który reprezentuje typ danych przechowywany w hash_multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Uwagi

`mapped_type` jest synonimem dla *typu*parametru szablonu.

Aby uzyskać więcej informacji na temat *typu* , zobacz temat [Klasa hash_multimap](../standard-library/hash-multimap-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [value_type](#value_type) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_type`.

## <a name="max_size"></a>hash_multimap::max_size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca maksymalną długość hash_multimap.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna możliwa długość hash_multimap.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multimap_max_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: size_type i;

   i = hm1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multimap is " << i << "." << endl;
}
```

## <a name="op_eq"></a>hash_multimap:: operator =

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zastępuje elementy hash_multimap kopią innego hash_multimap.

```cpp
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Kliknij*|[Hash_multimap](../standard-library/hash-multimap-class.md) jest kopiowana do `hash_multimap`.|

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkich istniejących elementów w `hash_multimap`, `operator=` kopiuje lub przenosi zawartość *bezpośrednio* do `hash_multimap`.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_operator_as.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> v1, v2, v3;
   hash_multimap<int, int>::iterator iter;

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

## <a name="pointer"></a>hash_multimap::p ointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza wskaźnik do elementu w hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie hash_multimap.

## <a name="rbegin"></a>hash_multimap:: rbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca iterator odnoszący się do pierwszego elementu w odwróconej hash_multimap.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconej hash_multimap lub adresowania ostatniego elementu w nieodwróconym hash_multimap.

### <a name="remarks"></a>Uwagi

`rbegin` jest używany z odwróconym hash_multimapm, tak jak [BEGIN](#begin) jest używany z hash_multimap.

Jeśli wartość zwracana `rbegin` jest przypisana do `const_reverse_iterator`, nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracana `rbegin` jest przypisana do `reverse_iterator`, można zmodyfikować obiekt hash_multimap.

`rbegin` można użyć do iteracji w hash_multimap wstecz.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_rbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rbegin( );
   cout << "The first element of the reversed hash_multimap hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multimap in a forward order
   cout << "The hash_multimap is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_multimap in a reverse order
   cout << "The reversed hash_multimap is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_multimap element can be erased by dereferencing its key
   hm1_rIter = hm1.rbegin( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rbegin( );
   cout << "After the erasure, the first element\n"
        << "in the reversed hash_multimap is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_multimap hm1 is 3.
The hash_multimap is: 1 2 3 .
The reversed hash_multimap is: 3 2 1 .
After the erasure, the first element
in the reversed hash_multimap is 2.
```

## <a name="reference"></a>hash_multimap:: Reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, który zawiera odwołanie do elementu przechowywanego w hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multimap_reference.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of first element in the hash_multimap is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of first element in the hash_multimap is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>hash_multimap:: rend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca iterator, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej hash_multimap.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej hash_multimap (lokalizacja, która poprzedza pierwszy element w odwrocie hash_multimap).

### <a name="remarks"></a>Uwagi

`rend` jest używany z odwróconym hash_multimapm, tak samo jak [koniec](#end) jest używany z hash_multimap.

Jeśli wartość zwracana `rend` jest przypisana do elementu [const_reverse_iterator](#const_reverse_iterator), wówczas nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracana `rend` jest przypisana do elementu [reverse_iterator](#reverse_iterator), można zmodyfikować obiekt hash_multimap.

`rend` można użyć do przetestowania, czy iterator odwrotny osiągnął koniec hash_multimap.

Nie należy wywoływać wartości zwracanej przez `rend`.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_rend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "The last element of the reversed hash_multimap hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multimap in a forward order
   cout << "The hash_multimap is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_multimap in a reverse order
   cout << "The reversed hash_multimap is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_multimap element can be erased by dereferencing its key
   hm1_rIter = --hm1.rend( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed hash_multimap is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_multimap hm1 is 1.
The hash_multimap is: 1 2 3 .
The reversed hash_multimap is: 3 2 1 .
After the erasure, the last element in the reversed hash_multimap is 2.
```

## <a name="reverse_iterator"></a>hash_multimap::reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iteracji przez hash_multimap w odwrocie.

@No__t_0 zdefiniowane przez hash_multimap wskazują obiekty [value_type](#value_type), które są typu `pair` \< **const, > typ**. Wartość klucza jest dostępna za pomocą pierwszej pary elementu członkowskiego, a wartość mapowanego elementu jest dostępna za pomocą drugiego elementu członkowskiego pary.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rbegin](#rbegin) , aby zapoznać się z przykładem sposobu deklarowania i używania `reverse_iterator`.

## <a name="size"></a>hash_multimap:: size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca liczbę elementów w hash_multimap.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość hash_multimap.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia funkcji składowej hash_multimap:: size.

```cpp
// hash_multimap_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1, hm2;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    i = hm1.size();
    cout << "The hash_multimap length is " << i << "." << endl;

    hm1.insert(Int_Pair(2, 4));
    i = hm1.size();
    cout << "The hash_multimap length is now " << i << "." << endl;
}
```

```Output
The hash_multimap length is 1.
The hash_multimap length is now 2.
```

## <a name="size_type"></a>hash_multimap::size_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ liczby całkowitej bez znaku, który zlicza liczbę elementów w hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dotyczącym [rozmiaru](#size) przykładu sposobu deklarowania i używania `size_type`

## <a name="swap"></a>hash_multimap:: swap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Wymienia elementy dwóch hash_multimaps.

```cpp
void swap(hash_multimap& right);
```

### <a name="parameters"></a>Parametry

*prawa* \
Hash_multimap udostępniający elementy, które mają zostać zamienione lub hash_multimap, których elementy mają być wymieniane z tymi hash_multimap.

### <a name="remarks"></a>Uwagi

Funkcja członkowska unieważnia brak odwołań, wskaźników lub iteratorów, które wyznaczają elementy w dwóch hash_multimaps, których elementy są wymieniane.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_swap.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   hash_multimap <int, int>::iterator hm1_Iter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm2.insert ( Int_Pair ( 10, 100 ) );
   hm2.insert ( Int_Pair ( 20, 200 ) );
   hm3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   hm1.swap( hm2 );

   cout << "After swapping with hm2, hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hm1, hm3 );

   cout << "After swapping with hm3, hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original hash_multimap hm1 is: 10 20 30.
After swapping with hm2, hash_multimap hm1 is: 100 200.
After swapping with hm3, hash_multimap hm1 is: 300.
```

## <a name="upper_bound"></a>hash_multimap::upper_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Zwraca iterator do pierwszego elementu w hash_multimap z kluczem, który jest większy niż określony klucz.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*klucz* \
Klucz argumentu, który ma zostać porównany z kluczem sortowania elementu z przeszukiwanego hash_multimap.

### <a name="return-value"></a>Wartość zwracana

[Iterator](#iterator) lub [const_iterator](#const_iterator) , który odnosi się do lokalizacji elementu w hash_multimap z kluczem, który jest większy niż klucz argumentu lub który odnosi się do lokalizacji po ostatnim elemencie w hash_multimap, jeśli nie znaleziono żadnego dopasowania dla głównych.

Jeśli wartość zwracana `upper_bound` jest przypisana do `const_iterator`, nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracana `upper_bound` jest przypisana do `iterator`, można zmodyfikować obiekt hash_multimap.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_multimap_upper_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm1.insert ( Int_Pair ( 3, 40 ) );

   hm1_RcIter = hm1.upper_bound( 1 );
   cout << "The 1st element of hash_multimap hm1 with "
        << "a key greater than 1 is: "
        << hm1_RcIter -> second << "." << endl;

   hm1_RcIter = hm1.upper_bound( 2 );
   cout << "The first element of hash_multimap hm1\n"
        << "with a key greater than 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.lower_bound( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_multimap can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.begin( );
   hm1_RcIter = hm1.upper_bound( hm1_AcIter -> first );
   cout << "The first element of hm1 with a key greater than"
        << endl << "that of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of hash_multimap hm1 with a key greater than 1 is: 20.
The first element of hash_multimap hm1
with a key  greater than 2 is: 30.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key greater than
that of the initial element of hm1 is: 20.
```

## <a name="value_comp"></a>hash_multimap::value_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Funkcja członkowska zwraca obiekt funkcji, który określa kolejność elementów w hash_multimap, porównując ich wartości klucza.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji porównania, którego hash_multimap używa do porządkowania jego elementów.

### <a name="remarks"></a>Uwagi

Dla hash_multimap *m*, jeśli dwa elementy *E1* (*K1*, *D1*) i *E2*(*K2*, *D2*) są obiektami typu [value_type](#value_type), gdzie *K1* i *K2* są ich klucze typu [key_type](#key_type) i *D1* i *D2* są swoimi danymi typu [mapped_type](#mapped_type), a następnie 4 jest równoznaczne z 5. Przechowywany obiekt definiuje funkcję członkowską

`bool operator( value_type& left, value_type& right);`

Zwraca wartość **true** , jeśli wartość klucza `left` poprzedza i nie jest równa wartości klucza `right` w kolejności sortowania.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_value_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;
   hash_multimap <int, int, hash_compare<int, less<int>>
      >::value_compare vc1 = hm1.value_comp( );
   hash_multimap <int,int>::iterator Iter1, Iter2;

   Iter1= hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= hm1.insert ( hash_multimap <int, int> :: value_type ( 2, 5 ) );

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

## <a name="value_type"></a>hash_multimap::value_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, który reprezentuje typ obiektu przechowywanego w hash_multimap.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Uwagi

`value_type` jest zadeklarowany jako para \<const [key_type](#key_type), [mapped_type](#mapped_type)> i not para \<key_type, mapped_type >, ponieważ klucze kontenera asocjacyjnego nie mogą być zmieniane przy użyciu niestałego iteratora lub odwołania.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_value_type.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: key_type key1;
   hash_multimap <int, int> :: mapped_type mapped1;
   hash_multimap <int, int> :: value_type value1;
   hash_multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   hm1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( hm1.begin( ) -> first );
   mapped1 = ( hm1.begin( ) -> second );

   cout << "The key of first element in the hash_multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the hash_multimap is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of first element in the hash_multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
