---
title: hash_map — Klasa
ms.date: 11/04/2016
f1_keywords:
- hash_map/stdext::hash_map
- hash_map/stdext::hash_map::allocator_type
- hash_map/stdext::hash_map::const_iterator
- hash_map/stdext::hash_map::const_pointer
- hash_map/stdext::hash_map::const_reference
- hash_map/stdext::hash_map::const_reverse_iterator
- hash_map/stdext::hash_map::difference_type
- hash_map/stdext::hash_map::iterator
- hash_map/stdext::hash_map::key_compare
- hash_map/stdext::hash_map::key_type
- hash_map/stdext::hash_map::mapped_type
- hash_map/stdext::hash_map::pointer
- hash_map/stdext::hash_map::reference
- hash_map/stdext::hash_map::reverse_iterator
- hash_map/stdext::hash_map::size_type
- hash_map/stdext::hash_map::value_type
- hash_map/stdext::hash_map::at
- hash_map/stdext::hash_map::begin
- hash_map/stdext::hash_map::cbegin
- hash_map/stdext::hash_map::cend
- hash_map/stdext::hash_map::clear
- hash_map/stdext::hash_map::count
- hash_map/stdext::hash_map::crbegin
- hash_map/stdext::hash_map::crend
- hash_map/stdext::hash_map::emplace
- hash_map/stdext::hash_map::emplace_hint
- hash_map/stdext::hash_map::empty
- hash_map/stdext::hash_map::end
- hash_map/stdext::hash_map::equal_range
- hash_map/stdext::hash_map::erase
- hash_map/stdext::hash_map::find
- hash_map/stdext::hash_map::get_allocator
- hash_map/stdext::hash_map::insert
- hash_map/stdext::hash_map::key_comp
- hash_map/stdext::hash_map::lower_bound
- hash_map/stdext::hash_map::max_size
- hash_map/stdext::hash_map::rbegin
- hash_map/stdext::hash_map::rend
- hash_map/stdext::hash_map::size
- hash_map/stdext::hash_map::swap
- hash_map/stdext::hash_map::upper_bound
- hash_map/stdext::hash_map::value_comp
helpviewer_keywords:
- stdext::hash_map
- stdext::hash_map::allocator_type
- stdext::hash_map::const_iterator
- stdext::hash_map::const_pointer
- stdext::hash_map::const_reference
- stdext::hash_map::const_reverse_iterator
- stdext::hash_map::difference_type
- stdext::hash_map::iterator
- stdext::hash_map::key_compare
- stdext::hash_map::key_type
- stdext::hash_map::mapped_type
- stdext::hash_map::pointer
- stdext::hash_map::reference
- stdext::hash_map::reverse_iterator
- stdext::hash_map::size_type
- stdext::hash_map::value_type
- stdext::hash_map::at
- stdext::hash_map::begin
- stdext::hash_map::cbegin
- stdext::hash_map::cend
- stdext::hash_map::clear
- stdext::hash_map::count
- stdext::hash_map::crbegin
- stdext::hash_map::crend
- stdext::hash_map::emplace
- stdext::hash_map::emplace_hint
- stdext::hash_map::empty
- stdext::hash_map::end
- stdext::hash_map::equal_range
- stdext::hash_map::erase
- stdext::hash_map::find
- stdext::hash_map::get_allocator
- stdext::hash_map::insert
- stdext::hash_map::key_comp
- stdext::hash_map::lower_bound
- stdext::hash_map::max_size
- stdext::hash_map::rbegin
- stdext::hash_map::rend
- stdext::hash_map::size
- stdext::hash_map::swap
- stdext::hash_map::upper_bound
- stdext::hash_map::value_comp
ms.assetid: 40879dfc-51ba-4a59-9f9e-26208de568a8
ms.openlocfilehash: 5939e2b4b0f8054ae5f7db7babd01dbeffc7f359
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520619"
---
# <a name="hash_map-class"></a>hash_map — Klasa

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Umożliwia szybkie przechowywanie i pobieranie danych z kolekcji, w której każdy element jest parą, która ma klucz sortowania, którego wartość jest unikatowa i skojarzona z nią wartość danych.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<pair <const Key, Type>>>
class hash_map
```

### <a name="parameters"></a>Parametry

*Głównych*\
Typ danych klucza, który ma być przechowywany w hash_map.

*Wprowadź*\
Typ danych elementu, który ma być przechowywany w hash_map.

*Cech*\
Typ, który zawiera dwa obiekty Functions, jedna z klas Compare może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność i funkcję mieszania, która jest jednoargumentową wartością klucza mapowania predykatów elementów do niepodpisanych liczb całkowitych typu `size_t` . Ten argument jest opcjonalny, a hash_compare<`Key` , mniej<`Key`> > jest wartością domyślną.

*Alokator*\
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji hash_map i dealokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to Alokator \<pair <const `Key`, `Type`>>.

## <a name="remarks"></a>Uwagi

Hash_map:

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.

- Skrót, ponieważ jego elementy są pogrupowane w zasobniki na podstawie wartości funkcji skrótu zastosowanej do wartości klucza elementów.

- Unikatowy w tym sensie, że każdy z jego elementów musi mieć unikatowy klucz.

- Kontenerem skojarzonych par, ponieważ jej wartości danych elementu różnią się od wartości klucza.

- Szablon klasy, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Główną zaletą tworzenia skrótów w porównaniu z sortowaniem jest większa wydajność. pomyślne wykonywanie skrótów wykonuje wstawienia, usunięcia i znajduje się w stałym średnim czasie w porównaniu z czasem proporcjonalnym do logarytmu liczby elementów w kontenerze dla technik sortowania. Wartość elementu w hash_map, ale nie skojarzona z nim wartość klucza, może zostać zmieniona bezpośrednio. Zamiast tego, wartości kluczy skojarzone ze starymi elementami muszą zostać usunięte, a nowe wartości klucza skojarzone z nowymi wstawionymi elementami.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Przyłączone Kontenery asocjacyjne są zoptymalizowane pod kątem operacji wyszukiwania, wstawiania i usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, są wydajne, gdy są używane z dobrze zaprojektowaną funkcją skrótu, wykonując je w czasie, który jest obliczany jako stała średnia i nie zależy od liczby elementów w kontenerze. Dobrze zaprojektowana funkcja skrótu generuje jednorodną dystrybucję wartości skrótów i minimalizuje liczbę kolizji, w których występuje kolizja, gdy wartości unikatowego klucza są mapowane na tę samą wartość skrótu. W najgorszym przypadku z najgorszą możliwą funkcją skrótu liczba operacji jest proporcjonalna do liczby elementów w sekwencji (czas liniowy).

Hash_map powinna być kontenerem asocjacyjnym wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Model dla tego typu struktury jest uporządkowaną listą jednoznacznie występujących słów kluczowych ze skojarzonymi wartościami ciągu, które dostarczają, mówią, definicje. Jeśli zamiast tego, wyrazy zawierały więcej niż jedną poprawną definicję, więc klucze nie były unikatowe, a następnie hash_multimap będzie kontenerem wyboru. Jeśli z drugiej strony jest przechowywanych tylko Lista wyrazów, hash_set będzie prawidłowym kontenerem. Jeśli dozwolone jest wiele wystąpień wyrazów, hash_multiset będzie odpowiednią strukturą kontenera.

Hash_map porządkuje sekwencję, którą kontroluje, przez wywołanie zapisanego obiektu *cechy* skrótu klasy [value_compare](../standard-library/value-compare-class.md). Dostęp do tego przechowywanego obiektu można uzyskać, wywołując funkcję członkowską [key_comp](#key_comp). Taki obiekt funkcji musi zachowywać się tak samo jak obiekt klasy [hash_compare](../standard-library/hash-compare-class.md)<klucz, mniej \<Key>>. W odniesieniu do *Key* wszystkich wartości klucza *typu,* wywołanie `Traits` ( `Key` ) daje rozkład wartości typu `size_t` .

Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarny f (x y) jest obiektem funkcji, który ma dwa obiekty argumentu `x` i `y` i zwraca wartość **`true`** lub **`false`** . Kolejność nałożona na hash_map jest ściśle słabym porządkowaniem, jeśli Predykat binarny jest niezwrotny, niesymetryczny i przechodni oraz jeśli równoważność jest przechodnia, gdzie dwa obiekty x i y są zdefiniowane jako równoważne, gdy zarówno f (x, y), jak i f (y, x) mają wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

Rzeczywista kolejność elementów w kontrolowanej sekwencji zależy od funkcji skrótu, funkcji porządkowania i bieżącego rozmiaru tabeli skrótów przechowywanej w obiekcie kontenera. Nie można określić bieżącego rozmiaru tabeli skrótów, dlatego nie można ogólnie przewidzieć kolejności elementów w kontrolowanej sekwencji. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Iterator dostarczony przez klasę hash_map jest iteratorem dwukierunkowym, ale funkcje składowych klasy [INSERT](#insert) i [hash_map](#hash_map) mają wersje przyjmujące jako parametry szablonu słabszy iterator danych wejściowych, którego wymagania funkcjonalności są mniejsze niż te gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcjonalności, ale jest wystarczający, aby można było mówić istotnie o zakresie iteratorów `[First, Last)` w kontekście funkcji składowych klasy.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[hash_map](#hash_map)|Tworzy obiekt `hash_map` , który jest pusty lub jest kopią całości lub części innej `hash_map` .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje `allocator` klasę dla `hash_map` obiektu.|
|[const_iterator](#const_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać **`const`** element w `hash_map` .|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do **`const`** elementu w `hash_map` .|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do **`const`** elementu przechowywanego w trakcie `hash_map` operacji odczytywania i wykonywania **`const`** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **`const`** element w `hash_map` .|
|[difference_type](#difference_type)|Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów `hash_map` w zakresie między elementami wskazywanymi przez Iteratory.|
|[Iterator](#iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w `hash_map` .|
|[key_compare](#key_compare)|Typ, który dostarcza obiekt funkcji, który może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `hash_map` .|
|[key_type](#key_type)|Typ opisuje obiekt klucza sortowania, który stanowi każdy element `hash_map` .|
|[mapped_type](#mapped_type)|Typ, który reprezentuje typ danych przechowywany w `hash_map` .|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu w `hash_map` .|
|[odwoła](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w `hash_map` .|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej postaci `hash_map` .|
|[size_type](#size_type)|Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w `hash_map` .|
|[value_type](#value_type)|Typ, który dostarcza obiekt funkcji, który może porównać dwa elementy jako klucze sortowania, aby określić ich względną kolejność w obiekcie `hash_map` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[w](#at)|Znajduje element w a `hash_map` z określoną wartością klucza.|
|[zaczną](#begin)|Zwraca iterator odnoszący się do pierwszego elementu w `hash_map` .|
|[cbegin](#cbegin)|Zwraca iterator const odnoszący się do pierwszego elementu w `hash_map` .|
|[cend](#cend)|Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie w `hash_map` .|
|[Wyczyść](#clear)|Kasuje wszystkie elementy `hash_map` .|
|[liczbą](#count)|Zwraca liczbę elementów w zakresie, `hash_map` których klucz pasuje do klucza określonego przez parametr.|
|[crbegin —](#crbegin)|Zwraca iterator const odnoszący się do pierwszego elementu w odwróconym `hash_map` .|
|[crend](#crend)|Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym stanie `hash_map` .|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do `hash_map` .|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do `hash_map` , z wskazówką umieszczenia.|
|[puste](#empty)|Testuje, czy `hash_map` jest pusty.|
|[punktów](#end)|Zwraca iterator, który odnosi się do lokalizacji po ostatnim elemencie w `hash_map` .|
|[equal_range](#equal_range)|Zwraca parę iteratorów odpowiednio do pierwszego elementu w a `hash_map` z kluczem, który jest większy niż określony klucz i do pierwszego elementu w `hash_map` kluczu, który jest równy lub większy niż klucz.|
|[Wyłączanie](#erase)|Usuwa element lub zakres elementów `hash_map` z określonych pozycji|
|[find](#find)|Zwraca iterator odnoszący się do lokalizacji elementu w elemencie `hash_map` , który ma klucz równoważny określonemu kluczowi.|
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` obiektu użytego do skonstruowania `hash_map` .|
|[wstawienia](#insert)|Wstawia element lub zakres elementów do `hash_map` .|
|[key_comp](#key_comp)|Zwraca iterator do pierwszego elementu w elemencie `hash_map` z wartością klucza, która jest równa lub większa od określonego klucza.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu w elemencie `hash_map` z wartością klucza, która jest równa lub większa od określonego klucza.|
|[max_size](#max_size)|Zwraca maksymalną długość `hash_map` .|
|[rbegin](#rbegin)|Zwraca iterator odnoszący się do pierwszego elementu w odwróconym `hash_map` .|
|[rend](#rend)|Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w odwróconym `hash_map` .|
|[zmienia](#size)|Zwraca liczbę elementów w `hash_map` .|
|[wymiany](#swap)|Wymienia elementy dwóch `hash_map` s.|
|[upper_bound](#upper_bound)|Zwraca iterator do pierwszego elementu w elemencie `hash_map` , którego wartość klucza jest większa od określonego klucza.|
|[value_comp](#value_comp)|Pobiera kopię obiektu porównania użytego do uporządkowania wartości elementów w `hash_map` .|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[&#91;&#93;operatora](#op_at)|Wstawia element do elementu `hash_map` z określoną wartością klucza.|
|[hash_map:: operator =](#op_eq)|Zastępuje elementy a `hash_map` kopią inną `hash_map` .|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<hash_map>

**Przestrzeń nazw:** stdext

## <a name="hash_mapallocator_type"></a><a name="allocator_type"></a>hash_map:: allocator_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ, który reprezentuje klasę alokatora dla obiektu hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>Przykład

Zobacz przykład dla [get_allocator](#get_allocator) , aby zapoznać się z przykładem `allocator_type` .

## <a name="hash_mapat"></a><a name="at"></a>hash_map:: at

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Znajduje element w hash_map z określoną wartością klucza.

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*key*|Wartość klucza elementu, który ma zostać znaleziony.|

### <a name="return-value"></a>Wartość zwracana

Odwołanie do wartości danych znalezionego elementu.

### <a name="remarks"></a>Uwagi

Jeśli wartość klucza argumentu nie zostanie znaleziona, funkcja zgłasza obiekt klasy [Out_of_range klasy](../standard-library/out-of-range-class.md).

### <a name="example"></a>Przykład

```cpp
// hash_map_at.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;

   // Insert data values
   hm1.insert ( cInt2Int ( 1, 10 ) );
   hm1.insert ( cInt2Int ( 2, 20 ) );
   hm1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The values of the mapped elements are:";
   for ( int i = 1 ; i <= hm1.size() ; i++ )
      cout << " " << hm1.at(i);
   cout << "." << endl;
}
```

## <a name="hash_mapbegin"></a><a name="begin"></a>hash_map:: BEGIN

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca iterator odnoszący się do pierwszego elementu w hash_map.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pierwszego elementu w hash_map lub lokalizacji po pomyślnym wypełnieniu pustego hash_map.

### <a name="example"></a>Przykład

```cpp
// hash_map_begin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 0, 0 ) );
   hm1.insert ( Int_Pair ( 1, 1 ) );
   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.begin ( );
   cout << "The first element of hm1 is "
        << hm1_cIter -> first << "." << endl;

   hm1_Iter = hm1.begin ( );
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.begin ( );
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.begin( );
   cout << "The first element of hm1 is now "
        << hm1_cIter -> first << "." << endl;
}
```

```Output
The first element of hm1 is 0.
The first element of hm1 is now 1.
```

## <a name="hash_mapcbegin"></a><a name="cbegin"></a>hash_map:: cbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca iterator const odnoszący się do pierwszego elementu w hash_map.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stały iterator dwukierunkowy odnoszący się do pierwszego elementu w [hash_map](../standard-library/hash-map-class.md) lub lokalizacja powiodła się `hash_map` .

### <a name="example"></a>Przykład

```cpp
// hash_map_cbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_iterator hm1_cIter;
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

## <a name="hash_mapcend"></a><a name="cend"></a>hash_map:: cend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w hash_map.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Stały iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w [hash_map](../standard-library/hash-map-class.md). Jeśli `hash_map` jest pusty, to `hash_map::cend == hash_map::begin` .

### <a name="remarks"></a>Uwagi

`cend`służy do sprawdzania, czy iterator osiągnął koniec jego `hash_map` .

Nie można usunąć odwołania do wartości zwracanej przez `cend` .

### <a name="example"></a>Przykład

```cpp
// hash_map_cend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_iterator hm1_cIter;
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

## <a name="hash_mapclear"></a><a name="clear"></a>hash_map:: Clear

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Usuwa wszystkie elementy hash_map.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia funkcji członkowskiej hash_map:: Clear.

```cpp
// hash_map_clear.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 4));

    i = hm1.size();
    cout << "The size of the hash_map is initially "
         << i << "." << endl;

    hm1.clear();
    i = hm1.size();
    cout << "The size of the hash_map after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the hash_map is initially 2.
The size of the hash_map after clearing is 0.
```

## <a name="hash_mapconst_iterator"></a><a name="const_iterator"></a>hash_map:: const_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać **`const`** element w hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może być używany do modyfikacji wartości elementu.

`const_iterator`Zdefiniowane przez hash_map wskazuje elementy, które są obiektami [value_type](#value_type), które są typu `pair< const Key, Type >` , którego pierwszy element członkowski jest kluczem do elementu, a drugi element członkowski jest zmapowaną podstawą zawartą w elemencie.

Aby usunąć odwołanie do `const_iterator` `cIter` elementu w hash_map, użyj `->` operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `cIter->first` , który jest odpowiednikiem `(*cIter).first` . Aby uzyskać dostęp do wartości mapowanej podstawy dla elementu, użyj `cIter->second` , który jest odpowiednikiem `(*cIter).second` .

### <a name="example"></a>Przykład

Zobacz przykład [rozpoczęcia](#begin) korzystania z polecenia `const_iterator` .

## <a name="hash_mapconst_pointer"></a><a name="const_pointer"></a>hash_map:: const_pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ, który dostarcza wskaźnik do **`const`** elementu w hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może być używany do modyfikacji wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie hash_map.

## <a name="hash_mapconst_reference"></a><a name="const_reference"></a>hash_map:: const_reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ, który zawiera odwołanie do **`const`** elementu przechowywanego w hash_map do odczytywania i wykonywania **`const`** operacji.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_map_const_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map<int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of the first element in the hash_map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of the first element in the hash_map is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the hash_map is 1.
The data value of the first element in the hash_map is 10.
```

## <a name="hash_mapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>hash_map:: const_reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **`const`** element w hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse)iterator const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartości elementu i służy do iterowania przez hash_map w odwrocie.

`const_reverse_iterator`Zdefiniowane przez hash_map wskazuje elementy, które są obiektami [value_type](#value_type), które są typu `pair` \< **const Key, Type**> , którego pierwszy element członkowski jest kluczem do elementu, a drugi element członkowski jest zmapowaną podstawą zawartą w elemencie.

Aby usunąć odwołanie do `const_reverse_iterator` `crIter` elementu w hash_map, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `crIter`  ->  **najpierw**, który jest odpowiednikiem ( \* `crIter` ) **. First**. Aby uzyskać dostęp do wartości mapowanej podstawy dla elementu, użyj `crIter`  ->  **sekundy**, który jest odpowiednikiem ( \* `crIter` ). **najpierw**.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rend](#rend) , aby zapoznać się z przykładem sposobu deklarowania i używania `const_reverse_iterator` .

## <a name="hash_mapcount"></a><a name="count"></a>hash_map:: Count

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca liczbę elementów w hash_map, których klucz pasuje do klucza określonego przez parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza elementów do dopasowania z hash_map.

### <a name="return-value"></a>Wartość zwracana

1, jeśli hash_map zawiera element, którego klucz sortowania jest zgodny z kluczem parametru; 0, jeśli hash_map nie zawiera elementu z pasującym kluczem.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę elementów *x* z zakresu

\[lower_bound (*klucz*), upper_bound (*klucz*))

jest to 0 lub 1 w przypadku hash_map, który jest unikatowym kontenerem asocjacyjnym.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie funkcji składowej hash_map:: Count.

```cpp
// hash_map_count.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair (1, 1));
    hm1.insert(Int_Pair (2, 1));
    hm1.insert(Int_Pair (1, 4));
    hm1.insert(Int_Pair (2, 1));

    // Keys must be unique in hash_map, so duplicates are ignored
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
The number of elements in hm1 with a sort key of 1 is: 1.
The number of elements in hm1 with a sort key of 2 is: 1.
The number of elements in hm1 with a sort key of 3 is: 0.
```

## <a name="hash_mapcrbegin"></a><a name="crbegin"></a>hash_map:: crbegin —

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca iterator const odnoszący się do pierwszego elementu w odwróconej hash_map.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stałe odwrotne Iteratory, odnoszące się do pierwszego elementu w odwróconej [hash_map](../standard-library/hash-map-class.md) lub adresowania ostatniego elementu w odwrót `hash_map` .

### <a name="remarks"></a>Uwagi

`crbegin`jest używany z odwróconą hash_map, tak jak [początek](#begin) jest używany z `hash_map` .

Z wartością zwracaną `crbegin` , `hash_map` nie można zmodyfikować obiektu.

`crbegin`może służyć do iteracji w `hash_map` tył.

### <a name="example"></a>Przykład

```cpp
// hash_map_crbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crbegin( );
   cout << "The first element of the reversed hash_map hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_map hm1 is 3.
```

## <a name="hash_mapcrend"></a><a name="crend"></a>hash_map:: crend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca iterator const, który odnosi się do lokalizacji następującej po ostatnim elemencie w odwróconym hash_map.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Niepowodzenie odwrotnego iteratora dwukierunkowego, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym [hash_map](../standard-library/hash-map-class.md) (lokalizacja, która poprzedza pierwszy element w odwrót `hash_map` ).

### <a name="remarks"></a>Uwagi

`crend`jest używany z odwróconym działaniem `hash_map` tak samo jak [hash_map:: end](#end) jest używany z `hash_map` .

Z wartością zwracaną `crend` , `hash_map` nie można zmodyfikować obiektu.

`crend`można go użyć do przetestowania, czy iterator odwrotny osiągnął koniec jego `hash_map` .

Nie można usunąć odwołania do wartości zwracanej przez `crend` .

### <a name="example"></a>Przykład

```cpp
// hash_map_crend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crend( );
   hm1_crIter--;
   cout << "The last element of the reversed hash_map hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_map hm1 is 3.
```

## <a name="hash_mapdifference_type"></a><a name="difference_type"></a>hash_map::d ifference_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów hash_map w zakresie między elementami wskazywanymi przez Iteratory.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="example"></a>Przykład

```cpp
// hash_map_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 3, 20 ) );

   // The following won't insert, because map keys are unique
   hm1.insert ( Int_Pair ( 2, 30 ) );

   hash_map <int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;
   hm1_bIter = hm1.begin( );
   hm1_eIter = hm1.end( );

   // Count the number of elements in a hash_map
   hash_map <int, int>::difference_type  df_count = 0;
   hm1_Iter = hm1.begin( );
   while ( hm1_Iter != hm1_eIter)
   {
      df_count++;
      hm1_Iter++;
   }

   cout << "The number of elements in the hash_map hm1 is: "
        << df_count << "." << endl;

   cout  << "The keys of the mapped elements are:";
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;
         hm1_Iter++)
      cout << " " << hm1_Iter-> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;
         hm1_Iter++)
      cout << " " << hm1_Iter-> second;
   cout << "." << endl;
}
```

```Output
The number of elements in the hash_map hm1 is: 3.
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 20.
```

## <a name="hash_mapemplace"></a><a name="emplace"></a>hash_map:: emplace

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Wstawia element skonstruowany w miejscu do hash_map.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*użyte*|Wartość służąca do przenoszenia elementu konstrukcja, który ma zostać wstawiony do [hash_map](../standard-library/hash-map-class.md) , chyba że `hash_map` zawiera już ten element (lub, bardziej ogólnie, element, którego klucz jest równoważny).|

### <a name="return-value"></a>Wartość zwracana

`emplace`Funkcja członkowska zwraca parę, której składnik bool zwraca wartość true, jeśli wstawiono, i wartość false `hash_map` , jeśli już zawiera element, którego klucz ma odpowiednik wartości w kolejności, a Składnik iteratora zwraca adres, w którym wstawiono nowy element lub miejsce, w którym element został już umieszczony.

Aby uzyskać dostęp do składnika iteratora pary `pr` zwracanej przez tę funkcję elementu członkowskiego, użyj `pr.first` , i aby usunąć odwołanie do niego, użyj `*(pr.first)` . Aby uzyskać dostęp do **`bool`** składnika pary `pr` zwracanej przez tę funkcję elementu członkowskiego, należy użyć `pr.second` , i aby usunąć odwołanie do niego, użyj `*(pr.second)` .

### <a name="remarks"></a>Uwagi

[Hash_map:: value_type](#value_type) elementu to para, tak aby wartość elementu była uporządkowaną parą z pierwszym składnikiem równym wartości klucza i drugi składnik równy wartości danych elementu.

### <a name="example"></a>Przykład

```cpp
// hash_map_emplace.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(move(is1));
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

## <a name="hash_mapemplace_hint"></a><a name="emplace_hint"></a>hash_map:: emplace_hint

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Wstawia element skonstruowany w miejscu do hash_map z wskazówką dotyczącą położenia.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*użyte*|Wartość służąca do przenoszenia elementu konstrukcja, który ma zostać wstawiony do [hash_map](../standard-library/hash-map-class.md) , chyba że `hash_map` zawiera już ten element (lub, bardziej ogólnie, element, którego klucz jest równoważny).|
|*_Where*|Wskazówka dotycząca miejsca, w którym rozpoczyna się wyszukiwanie poprawnego punktu wstawiania.|

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska [hash_multimap:: emplace](../standard-library/hash-multimap-class.md#emplace) zwraca iterator, który wskazuje na położenie, w którym nowy element został wstawiony do `hash_map` lub gdzie znajduje się istniejący element o równoważnej kolejności.

### <a name="remarks"></a>Uwagi

[Hash_map:: value_type](#value_type) elementu to para, tak aby wartość elementu była uporządkowaną parą z pierwszym składnikiem równym wartości klucza i drugi składnik równy wartości danych elementu.

Wstawianie może odbywać się w amortyzowanym stałym czasie, a nie w czasie logarytmu, jeśli punkt wstawiania natychmiast następuje *_Where*.

### <a name="example"></a>Przykład

```cpp
// hash_map_emplace_hint.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(hm1.begin(), move(is1));
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

## <a name="hash_mapempty"></a><a name="empty"></a>hash_map:: Empty

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Testuje, czy hash_map jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli hash_map jest puste; **`false`** jeśli hash_map nie jest pusty.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_map_empty.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2;

   typedef pair <int, int> Int_Pair;
   hm1.insert ( Int_Pair ( 1, 1 ) );

   if ( hm1.empty( ) )
      cout << "The hash_map hm1 is empty." << endl;
   else
      cout << "The hash_map hm1 is not empty." << endl;

   if ( hm2.empty( ) )
      cout << "The hash_map hm2 is empty." << endl;
   else
      cout << "The hash_map hm2 is not empty." << endl;
}
```

```Output
The hash_map hm1 is not empty.
The hash_map hm2 is empty.
```

## <a name="hash_mapend"></a><a name="end"></a>hash_map:: end

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w hash_map.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w hash_map. Jeśli hash_map jest puste, a następnie hash_map:: end = = hash_map:: BEGIN.

### <a name="remarks"></a>Uwagi

`end`służy do sprawdzania, czy iterator osiągnął koniec hash_map.

Nie można usunąć odwołania do wartości zwracanej przez `end` .

### <a name="example"></a>Przykład

```cpp
// hash_map_end.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: const_iterator hm1_cIter;
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

## <a name="hash_mapequal_range"></a><a name="equal_range"></a>hash_map:: equal_range

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca parę iteratorów odpowiednio do pierwszego elementu w hash_map z kluczem, który jest większy niż określony klucz i do pierwszego elementu w hash_map, z kluczem, który jest równy lub większy niż klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza argumentu do porównania z kluczem sortowania elementu z przeszukiwanego hash_map.

### <a name="return-value"></a>Wartość zwracana

Para iteratorów, takich jak pierwszy jest [lower_bound](#lower_bound) klucza, a drugi to [upper_bound](#upper_bound) klucza.

Aby uzyskać dostęp do pierwszego iteratora pary `pr` zwracanej przez funkcję członkowską, użyj `pr` . **najpierw** i aby usunąć odwołanie do dolnego powiązanego iteratora, użyj \* ( `pr` . **pierwszy**). Aby uzyskać dostęp do drugiego iteratora pary `pr` zwracanej przez funkcję członkowską, użyj `pr` . **drugi** i aby usunąć odwołanie do górnego powiązanego iteratora, użyj \* ( `pr` . **sekundę**).

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_map_equal_range.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_map <int, int> IntMap;
   IntMap hm1;
   hash_map <int, int> :: const_iterator hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;
   p1 = hm1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the hash_map hm1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the hash_map hm1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   hm1_RcIter = hm1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << hm1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = hm1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )
      cout << "The hash_map hm1 doesn't have an element "
             << "with a key less than 40." << endl;
   else
      cout << "The element of hash_map hm1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the hash_map hm1 is: 20.
The upper bound of the element with a key of 2 in the hash_map hm1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The hash_map hm1 doesn't have an element with a key less than 40.
```

## <a name="hash_maperase"></a><a name="erase"></a>hash_map:: Erase

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Usuwa element lub zakres elementów w hash_map z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_Where*\
Pozycja elementu, który ma zostać usunięty z hash_map.

*pierwszego*\
Pozycja pierwszego elementu usuniętego z hash_map.

*ostatniego*\
Umieść tuż poza ostatnim elementem usuniętym z hash_map.

*głównych*\
Wartość klucza elementów do usunięcia z hash_map.

### <a name="return-value"></a>Wartość zwracana

W przypadku pierwszych dwóch funkcji składowych iterator dwukierunkowy, który wyznacza pierwszy element pozostały poza elementami usuniętymi lub wskaźnik do końca hash_map, jeśli taki element nie istnieje.

Dla trzeciej funkcji składowej zwraca liczbę elementów usuniętych z hash_map.

### <a name="remarks"></a>Uwagi

Funkcja członkowska nigdy nie zgłasza wyjątku.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia funkcji członkowskiej hash_map:: Erase.

```cpp
// hash_map_erase.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1, hm2, hm3;
    hash_map<int, int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_map<int, int>::size_type n;
    typedef pair<int, int> Int_Pair;

    for (i = 1; i < 5; i++)
    {
        hm1.insert(Int_Pair (i, i));
        hm2.insert(Int_Pair (i, i*i));
        hm3.insert(Int_Pair (i, i-1));
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hm1.begin();
    hm1.erase(Iter1);

    cout << "After the 2nd element is deleted, the hash_map hm1 is:";
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hm2.begin();
    Iter2 = --hm2.end();
    hm2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_map hm2 is:";
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hm3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_map hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hm3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hm3.begin();
    hm3.erase(Iter1);

    cout << "After another element with a key equal to that"
         << endl;
    cout  << "of the 2nd element is deleted, "
          << "the hash_map hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_map hm1 is: 1 3 4.
After the middle two elements are deleted, the hash_map hm2 is: 1 16.
After the element with a key of 2 is deleted,
the hash_map hm3 is: 0 2 3.
The number of elements removed from hm3 is: 1.
After another element with a key equal to that
of the 2nd element is deleted, the hash_map hm3 is: 0 3.
```

## <a name="hash_mapfind"></a><a name="find"></a>hash_map:: find

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca iterator odnoszący się do lokalizacji elementu w hash_map, który ma klucz równoważny określonemu kluczowi.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza do dopasowania przez klucz sortowania elementu z przeszukiwanego hash_map.

### <a name="return-value"></a>Wartość zwracana

Iterator, który odnosi się do lokalizacji elementu z określonym kluczem lub lokalizacji, w której znajduje się ostatni element w hash_map, jeśli nie znaleziono żadnego dopasowania dla klucza.

### <a name="remarks"></a>Uwagi

`find`zwraca iterator, który odnosi się do elementu w hash_map którego klucz sortowania jest równoważny z kluczem argumentu w predykacie binarnym, który wywołuje kolejność na podstawie mniejszej niż porównywalności relacji.

Jeśli wartość zwracana `find` jest przypisana do [const_iterator](#const_iterator), nie można zmodyfikować obiektu hash_map. Jeśli wartość zwracana `find` jest przypisana do [iteratora](#iterator), można zmodyfikować obiekt hash_map

### <a name="example"></a>Przykład

```cpp
// hash_map_find.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.find( 2 );
   cout << "The element of hash_map hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.find( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_map can be found
   // using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1.find( hm1_AcIter -> first );
   cout << "The element of hm1 with a key matching "
        << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The element of hash_map hm1 with a key of 2 is: 20.
The hash_map hm1 doesn't have an element with a key of 4.
The element of hm1 with a key matching that of the last element is: 30.
```

## <a name="hash_mapget_allocator"></a><a name="get_allocator"></a>hash_map:: get_allocator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca kopię obiektu alokatora używanego do konstruowania hash_map.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez hash_map.

### <a name="remarks"></a>Uwagi

Przypisania klasy hash_map określają sposób zarządzania magazynem przez klasę. Domyślne przydzielenie klas kontenerów standardowej biblioteki języka C++ jest wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym tematem języka C++.

### <a name="example"></a>Przykład

```cpp
// hash_map_get_allocator.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int>::allocator_type hm1_Alloc;
   hash_map <int, int>::allocator_type hm2_Alloc;
   hash_map <int, double>::allocator_type hm3_Alloc;
   hash_map <int, int>::allocator_type hm4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   hash_map <int, int> hm1;
   hash_map <int, int> hm2;
   hash_map <int, double> hm3;

   hm1_Alloc = hm1.get_allocator( );
   hm2_Alloc = hm2.get_allocator( );
   hm3_Alloc = hm3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hm2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hm3.max_size( ) <<  "." << endl;

   // The following line creates a hash_map hm4
   // with the allocator of hash_map hm1.
   hash_map <int, int> hm4( less<int>( ), hm1_Alloc );

   hm4_Alloc = hm4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
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

## <a name="hash_maphash_map"></a><a name="hash_map"></a>hash_map:: hash_map

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Konstruuje hash_map, która jest pusta lub jest kopią wszystkich lub części niektórych innych hash_map.

```cpp
hash_map();

explicit hash_map(
    const Traits& Comp);

hash_map(
    const Traits& Comp,
    const Allocator& Al);

hash_map(
    const hash_map& Right);

hash_map(
    hash_map&& Right);

hash_map(
    initializer_list<Type> IList);hash_map(initializer_list<Type> IList,
    const key_compare& Comp);

hash_map(
    initializer_list<Type> IList,
    const key_compare& Comp,
    const allocator_type& Al);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Wsp*|Klasa alokatora magazynu, która ma być używana dla tego obiektu hash_map, który domyślnie jest `Allocator` .|
|*Comp*|Funkcja porównania typu const `Traits` użyta do uporządkowania elementów w hash_map, których wartością domyślną jest `hash_compare` .|
|*Kliknij*|Hash_map, dla którego skonstruowana Mapa ma być kopią.|
|*Pierwsze*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*Ostatniego*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|
|*IList*|Initializer_list|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują typ obiektu alokatora, który zarządza magazynem pamięci dla hash_map i można później zwrócić, wywołując [get_allocator](#get_allocator). Parametr alokatora jest często pomijany w deklaracjach klas i makrach przetwarzania wstępnego służących do podstawiania alternatywnych metod przydzielania.

Wszystkie konstruktory inicjują hash_map.

Wszystkie konstruktory przechowują obiekt funkcji typu `Traits` , który jest używany do ustanowienia zamówienia między kluczami hash_map i który może być później zwracany przez wywoływanie [key_comp](#key_comp).

Pierwsze trzy konstruktory określają pustą hash_map początkową, a ponadto drugi określa typ funkcji porównywania (*COMP*), która ma być używana w ustalaniu kolejności elementów, a trzeci jawnie określa typ alokatora (*Al*), który ma być używany. Słowo kluczowe **`explicit`** pomija pewne rodzaje automatycznej konwersji typów.

Czwarty Konstruktor określa kopię hash_map *prawej*.

Kolejne trzy konstruktory kopiują zakres `[First, Last)` hash_map, zwiększając jawność w określaniu typu funkcji porównania klasy `Traits` i alokatora.

Ostatni konstruktor przenosi hash_map w *prawo*.

## <a name="hash_mapinsert"></a><a name="insert"></a>hash_map:: INSERT

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Wstawia element lub zakres elementów do hash_map.

```cpp
pair <iterator, bool> insert(
    const value_type& val);

iterator insert(
    const_iterator _Where,
    const value_type& val);

template <class InputIterator>
void insert(
    InputIterator first,
    InputIterator last);

template <class ValTy>
pair <iterator, bool>
insert(
    ValTy&& val);

template <class ValTy>
iterator insert(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*użyte*|Wartość elementu, który ma zostać wstawiony do hash_map, chyba że hash_map już zawiera ten element (lub, bardziej ogólnie rzecz biorąc, element, którego klucz jest równoważny uporządkowany).|
|*_Where*|Wskazówka dotycząca miejsca, w którym rozpoczyna się wyszukiwanie poprawnego punktu wstawiania.|
|*pierwszego*|Pozycja pierwszego elementu, który ma zostać skopiowany z hash_map.|
|*ostatniego*|Pozycja tuż poza ostatnim elementem, który ma zostać skopiowany z hash_map.|

### <a name="return-value"></a>Wartość zwracana

Pierwsza `insert` funkcja członkowska zwraca parę, której składnik bool zwraca wartość true (prawda), jeśli wstawiono, i wartość false, jeśli hash_map już zawiera element, którego klucz ma odpowiednik wartości w kolejności, a Składnik iteratora zwraca adres, w którym został wstawiony nowy element lub gdzie już znajduje się element.

Aby uzyskać dostęp do składnika iteratora pary `pr` zwracanej przez tę funkcję elementu członkowskiego, użyj `pr` . **najpierw**, aby usunąć odwołanie do niego, użyj \* ( `pr` . **pierwszy**). Aby uzyskać dostęp do **`bool`** składnika pary `pr` zwracanej przez tę funkcję elementu członkowskiego, użyj `pr` . **drugi**i aby usunąć odwołanie do niego, użyj \* ( `pr` . **sekundę**).

Druga `insert` funkcja członkowska, wersja wskazówki, zwraca iterator, który wskazuje na położenie, w którym nowy element został wstawiony do hash_map.

Ostatnie dwie `insert` funkcje członkowskie zachowują się tak samo jak dwa pierwsze, z tą różnicą, że przechodzą konstruowaną wartość.

### <a name="remarks"></a>Uwagi

[Value_type](../standard-library/map-class.md#value_type) elementu to para, dzięki czemu wartość elementu będzie przymówionej pary z pierwszym składnikiem równym wartości klucza i drugi składnik równy wartości danych elementu.

Wstawianie może wystąpić w amortyzowanym stałym czasie dla wskazówki dotyczącej wersji instrukcji INSERT, a nie logarytmu czasu, jeśli punkt wstawiania natychmiast następuje po *_Where*.

Trzecia funkcja członkowska wstawia sekwencję wartości elementów do hash_map odpowiadającą każdemu elementowi, do którego odnosił się iterator w zakresie *[First, Last)* określonego zestawu.

### <a name="example"></a>Przykład

```cpp
// hash_map_insert.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int>::iterator hm1_pIter, hm2_pIter;

    hash_map<int, int> hm1, hm2;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(3, 30));
    hm1.insert(Int_Pair(4, 40));

    cout << "The original elements (Key => Value) of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << " " << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    pair< hash_map<int,int>::iterator, bool > pr;
    pr = hm1.insert(Int_Pair(1, 10));

    if (pr.second == true)
    {
        cout << "The element 10 was inserted in hm1 successfully."
            << endl;
    }
    else
    {
        cout << "The element 10 already exists in hm1\n"
            << "with a key value of "
            << "((pr.first) -> first) = " << (pr.first)->first
            << "." << endl;
    }

    // The hint version of insert
    hm1.insert(--hm1.end(), Int_Pair(5, 50));

    cout << "After the insertions, the elements of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    hm2.insert(Int_Pair(10, 100));

    // The templatized version inserting a range
    hm2.insert( ++hm1.begin(), --hm1.end() );

    cout << "After the insertions, the elements of hm2 are:";
    for (hm2_pIter = hm2.begin(); hm2_pIter != hm2.end(); hm2_pIter++)
        cout << endl << hm2_pIter -> first << " => "
             << hm2_pIter->second;
    cout << endl;

    // The templatized versions move constructing elements
    hash_map<int, string> hm3, hm4;
    pair<int, string> is1(1, "a"), is2(2, "b");

    hm3.insert(move(is1));
    cout << "After the move insertion, hm3 contains:" << endl
      << hm3.begin()->first
      << " => " << hm3.begin()->second
      << endl;

    hm4.insert(hm4.begin(), move(is2));
    cout << "After the move insertion, hm4 contains:" << endl
      << hm4.begin()->first
      << " => " << hm4.begin()->second
      << endl;
}
```

```Output
The original elements (Key => Value) of hm1 are:
1 => 10
2 => 20
3 => 30
4 => 40
The element 10 already exists in hm1
with a key value of ((pr.first) -> first) = 1.
After the insertions, the elements of hm1 are:
1 => 10
2 => 20
3 => 30
4 => 40
5 => 50
After the insertions, the elements of hm2 are:
2 => 20
10 => 100
3 => 30
4 => 40
After the move insertion, hm3 contains:
1 => a
After the move insertion, hm4 contains:
2 => b
```

## <a name="hash_mapiterator"></a><a name="iterator"></a>hash_map:: iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Uwagi

`iterator`Zdefiniowane przez hash_map wskazuje elementy, które są obiektami [value_type](#value_type), które są typu `pair<const Key, Type>` , którego pierwszy element członkowski jest kluczem do elementu, a drugi element członkowski jest zmapowaną podstawą zawartą w elemencie.

Aby usunąć odwołanie do iteratora o nazwie `Iter` wskazującej element w multimap, użyj `->` operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `Iter->first` , który jest odpowiednikiem `(*Iter).first` . Aby uzyskać dostęp do wartości mapowanej podstawy dla elementu, użyj `Iter->second` , który jest odpowiednikiem `(*Iter).second` .

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład rozpoczęcia, aby zapoznać [się](#begin) z przykładem sposobu deklarowania i używania `iterator` .

## <a name="hash_mapkey_comp"></a><a name="key_comp"></a>hash_map:: key_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w hash_map.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji, którego hash_map używa do porządkowania jego elementów.

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członkowską

`bool operator( const Key& left, const Key&right );`

zwraca, **`true`** Jeśli `left` poprzedza i nie jest równe `right` w kolejności sortowania.

### <a name="example"></a>Przykład

```cpp
// hash_map_key_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_map <int, int, hash_compare<int, less<int> > > hm1;
   hash_map <int, int, hash_compare<int, less<int> > >::key_compare
      kc1 = hm1.key_comp( ) ;

   // Operator stored in kc1 tests order & returns bool value
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true,"
           << "\n where kc1 is the function object of hm1"
           << " of type key_compare." << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false"
           << "\n where kc1 is the function object of hm1"
           << " of type key_compare." << endl;
   }

   hash_map <int, int, hash_compare<int, greater<int> > > hm2;
   hash_map <int, int, hash_compare<int, greater<int> > >
      ::key_compare kc2 = hm2.key_comp( );

   // Operator stored in kc2 tests order & returns bool value
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true,"
           << "\n where kc2 is the function object of hm2"
           << " of type key_compare." << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false,"
           << "\n where kc2 is the function object of hm2"
           << " of type key_compare." << endl;
   }
}
```

## <a name="hash_mapkey_compare"></a><a name="key_compare"></a>hash_map:: key_compare

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ, który dostarcza obiekt funkcji, który może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów na mapie.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare`jest synonimem dla parametru szablonu `Traits` .

Aby uzyskać więcej informacji na temat `Traits` , zobacz temat [Klasa hash_map](../standard-library/hash-map-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem na [key_comp](#key_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_compare` .

## <a name="hash_mapkey_type"></a><a name="key_type"></a>hash_map:: key_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ opisuje obiekt klucza sortowania, który stanowi każdy element hash_map.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type`jest synonimem dla parametru szablonu `Key` .

Aby uzyskać więcej informacji na temat `Key` , zobacz sekcję Uwagi w temacie [hash_map Class](../standard-library/hash-map-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem na [value_type](#value_type) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_type` .

## <a name="hash_maplower_bound"></a><a name="lower_bound"></a>hash_map:: lower_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca iterator do pierwszego elementu w hash_map z wartością klucza, która jest równa lub większa od określonego klucza.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza argumentu do porównania z kluczem sortowania elementu z przeszukiwanego hash_map.

### <a name="return-value"></a>Wartość zwracana

[Iterator](#iterator) lub [const_iterator](#const_iterator) , który odnosi się do lokalizacji elementu w hash_map, który jest równy lub większy od klucza argumentu lub który odnosi się do lokalizacji po ostatnim elemencie w hash_map, jeśli nie znaleziono żadnego dopasowania dla klucza.

Jeśli wartość zwracana `lower_bound` jest przypisana do `const_iterator` , nie można zmodyfikować obiektu hash_map. Jeśli wartość zwracana `lower_bound` jest przypisana do `iterator` , obiekt hash_map może być modyfikowany.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_map_lower_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.lower_bound( 2 );
   cout << "The first element of hash_map hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1. lower_bound ( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // An element at a specific location in the hash_map can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1. lower_bound ( hm1_AcIter -> first );
   cout << "The element of hm1 with a key matching "
        << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The first element of hash_map hm1 with a key of 2 is: 20.
The hash_map hm1 doesn't have an element with a key of 4.
The element of hm1 with a key matching that of the last element is: 30.
```

## <a name="hash_mapmapped_type"></a><a name="mapped_type"></a>hash_map:: mapped_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ, który reprezentuje typ danych przechowywany w hash_map.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Uwagi

Typ `mapped_type` jest synonimem dla parametru szablonu `Type` .

Aby uzyskać więcej informacji na temat `Type` , zobacz temat [Klasa hash_map](../standard-library/hash-map-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem na [value_type](#value_type) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_type` .

## <a name="hash_mapmax_size"></a><a name="max_size"></a>hash_map:: max_size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca maksymalną długość hash_map.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna możliwa długość hash_map.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_map_max_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: size_type i;

   i = hm1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_map is " << i << "."
        << endl << "(Magnitude is machine specific.)";
}
```

## <a name="hash_mapoperator"></a><a name="op_at"></a>hash_map:: operator []

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Wstawia element do elementu `hash_map` z określoną wartością klucza.

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*key*|Wartość klucza elementu, który ma zostać wstawiony.|

### <a name="return-value"></a>Wartość zwracana

Odwołanie do wartości danych wstawionego elementu.

### <a name="remarks"></a>Uwagi

Jeśli wartość klucza argumentu nie zostanie znaleziona, zostanie ona wstawiona wraz z wartością domyślną typu danych.

`operator[]`może służyć do wstawiania elementów do elementu `hash_map m` using

`m[ key] = DataValue`;

gdzie DataValue jest wartością `mapped_type` elementu z kluczową wartością *klucza*.

Podczas używania `operator[]` do wstawiania elementów, zwrócone odwołanie nie wskazuje, czy wstawienie zmienia istniejący element lub tworzy nowy. Funkcje członkowskie [Znajdź](../standard-library/map-class.md#find) i [Wstaw](../standard-library/map-class.md#insert) mogą służyć do określenia, czy element z określonym kluczem jest już obecny przed wstawieniem.

### <a name="example"></a>Przykład

```cpp
// hash_map_op_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;
   hash_map <int, int> :: iterator pIter;

   // Insert a data value of 10 with a key of 1
   // into a hash_map using the operator[] member function
   hm1[ 1 ] = 10;

   // Compare other ways to insert objects into a hash_map
   hm1.insert ( hash_map <int, int> :: value_type ( 2, 20 ) );
   hm1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // If the key already exists, operator[]
   // changes the value of the datum in the element
   hm1[ 2 ] = 40;

   // operator[] will also insert the value of the data
   // type's default constructor if the value is unspecified
   hm1[5];

   cout  << "The keys of the mapped elements are now:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are now:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // operator[] will also insert by moving a key
   hash_map <string, int> hm2;
   string str("a");
   hm2[move(str)] = 1;
   cout << "The moved key is " << hm2.begin()->first
      << ", with value " << hm2.begin()->second << endl;
}
```

## <a name="hash_mapoperator"></a><a name="op_eq"></a>hash_map:: operator =

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zastępuje elementy hash_map kopią innego hash_map.

```cpp
hash_map& operator=(const hash_map& right);

hash_map& operator=(hash_map&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Kliknij*|[Klasa hash_map](../standard-library/hash-map-class.md) kopiowana do `hash_map` .|

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkich istniejących elementów w programie `hash_map` , `operator=` kopiuje lub przenosi zawartość *bezpośrednio* do `hash_map` .

### <a name="example"></a>Przykład

```cpp
// hash_map_operator_as.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map<int, int> v1, v2, v3;
   hash_map<int, int>::iterator iter;

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

## <a name="hash_mappointer"></a><a name="pointer"></a>hash_map::p ointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ, który dostarcza wskaźnik do elementu w hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie hash_map.

## <a name="hash_maprbegin"></a><a name="rbegin"></a>hash_map:: rbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca iterator odnoszący się do pierwszego elementu w odwróconej hash_map.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconym hash_map lub adresowania ostatniego elementu w nieodwróconej hash_map.

### <a name="remarks"></a>Uwagi

`rbegin`jest używany z odwróconą hash_map, tak jak [początek](#begin) jest używany z hash_map.

Jeśli wartość zwracana `rbegin` jest przypisana do [const_reverse_iterator](#const_reverse_iterator), obiekt hash_map nie może być modyfikowany. Jeśli wartość zwracana `rbegin` jest przypisana do [reverse_iterator](#reverse_iterator), obiekt hash_map można modyfikować.

`rbegin`może służyć do iteracji w hash_map do tyłu.

### <a name="example"></a>Przykład

```cpp
// hash_map_rbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: reverse_iterator hm1_rIter;
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rbegin( );
   cout << "The first element of the reversed hash_map hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_map in a forward order
   cout << "The hash_map is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_map in a reverse order
   cout << "The reversed hash_map is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_map element can be erased by dereferencing to its key
   hm1_rIter = hm1.rbegin( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_map is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_map hm1 is 3.
The hash_map is: 1 2 3 .
The reversed hash_map is: 3 2 1 .
After the erasure, the first element in the reversed hash_map is 2.
```

## <a name="hash_mapreference"></a><a name="reference"></a>hash_map:: Reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ, który zawiera odwołanie do elementu przechowywanego w hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_map_reference.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of first element in the hash_map is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_map is 1.
The data value of first element in the hash_map is 10.
The modified data value of first element is 15.
```

## <a name="hash_maprend"></a><a name="rend"></a>hash_map:: rend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w odwróconym hash_map.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym hash_map (lokalizacja, która poprzedza pierwszy element w nieodwróconym hash_map).

### <a name="remarks"></a>Uwagi

`rend`jest używany z odwróconą hash_map, tak jak [koniec](#end) jest używany z hash_map.

Jeśli wartość zwracana `rend` jest przypisana do [const_reverse_iterator](#const_reverse_iterator), obiekt hash_map nie może być modyfikowany. Jeśli wartość zwracana `rend` jest przypisana do [reverse_iterator](#reverse_iterator), obiekt hash_map można modyfikować.

`rend`może służyć do sprawdzenia, czy iterator odwrotny osiągnął koniec hash_map.

Nie można usunąć odwołania do wartości zwracanej przez `rend` .

### <a name="example"></a>Przykład

```cpp
// hash_map_rend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: reverse_iterator hm1_rIter;
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "The last element of the reversed hash_map hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_map in a forward order
   cout << "The hash_map is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( );
   hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_map in a reverse order
   cout << "The reversed hash_map is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( );
      hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_map element can be erased by dereferencing to its key
   hm1_rIter = --hm1.rend( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed hash_map is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_map hm1 is 1.
The hash_map is: 1 2 3 .
The reversed hash_map is: 3 2 1 .
After the erasure, the last element in the reversed hash_map is 2.
```

## <a name="hash_mapreverse_iterator"></a><a name="reverse_iterator"></a>hash_map:: reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` nie może zmodyfikować wartości elementu i służy do iterowania przez hash_map w odwrocie.

`reverse_iterator`Zdefiniowane przez hash_map wskazuje elementy, które są obiektami [value_type](#value_type), które są typu ** \<const Key, Type> pary**, których pierwszy element członkowski jest kluczem do elementu, a drugi element członkowski jest zmapowaną podstawą posiadaną przez element.

Aby usunąć odwołanie do `reverse_iterator` `rIter` elementu w hash_map, użyj operatora->.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `rIter`  ->  **pierwszej**, który jest odpowiednikiem ( \* `rIter` ). **najpierw**. Aby uzyskać dostęp do wartości mapowanej podstawy dla elementu, użyj `rIter`  ->  **sekundy**, który jest odpowiednikiem ( \* `rIter` ). **najpierw**.

### <a name="example"></a>Przykład

Zobacz przykład dla [rbegin](#rbegin) , aby zapoznać się z przykładem sposobu deklarowania i używania `reverse_iterator` .

## <a name="hash_mapsize"></a><a name="size"></a>hash_map:: size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca liczbę elementów w hash_map.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość hash_map.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie funkcji składowej hash_map:: size.

```cpp
// hash_map_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1, hm2;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    i = hm1.size();
    cout << "The hash_map length is " << i << "." << endl;

    hm1.insert(Int_Pair(2, 4));
    i = hm1.size();
    cout << "The hash_map length is now " << i << "." << endl;
}
```

```Output
The hash_map length is 1.
The hash_map length is now 2.
```

## <a name="hash_mapsize_type"></a><a name="size_type"></a>hash_map:: size_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Zobacz przykład [rozmiaru](#size) , aby zapoznać się z przykładem sposobu deklarowania i używania`size_type`

## <a name="hash_mapswap"></a><a name="swap"></a>hash_map:: swap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Wymienia elementy dwóch hash_maps.

```cpp
void swap(hash_map& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Argument hash_map zapewniający elementy, które mają zostać zamienione na hash_map docelowy.

### <a name="remarks"></a>Uwagi

Funkcja członkowska unieważnia brak odwołań, wskaźników lub iteratorów, które wyznaczają elementy w dwóch hash_maps których elementy są wymieniane.

### <a name="example"></a>Przykład

```cpp
// hash_map_swap.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   hash_map <int, int>::iterator hm1_Iter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm2.insert ( Int_Pair ( 10, 100 ) );
   hm2.insert ( Int_Pair ( 20, 200 ) );
   hm3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   // hm2 is said to be the argument hash_map;
   // hm1 is said to be the target hash_map
   hm1.swap( hm2 );

   cout << "After swapping with hm2, hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hm1, hm3 );

   cout << "After swapping with hm3, hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original hash_map hm1 is: 10 20 30.
After swapping with hm2, hash_map hm1 is: 100 200.
After swapping with hm3, hash_map hm1 is: 300.
```

## <a name="hash_mapupper_bound"></a><a name="upper_bound"></a>hash_map:: upper_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca iterator do pierwszego elementu w hash_map, który ma klucz o wartości większej niż wartość określonego klucza.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza argumentu do porównania z wartością klucza sortowania elementu z przeszukiwanego hash_map.

### <a name="return-value"></a>Wartość zwracana

[Iterator](#iterator) lub [const_iterator](#const_iterator) , który odnosi się do lokalizacji elementu w hash_map, który jest większy niż klucz argumentu lub który odnosi się do lokalizacji po ostatnim elemencie w hash_map, jeśli nie znaleziono żadnego dopasowania dla klucza.

Jeśli wartość zwracana jest przypisana do `const_iterator` , nie można zmodyfikować obiektu hash_map. Jeśli wartość zwracana jest przypisana do `iterator` , można zmodyfikować obiekt hash_map.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// hash_map_upper_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.upper_bound( 2 );
   cout << "The first element of hash_map hm1 with a key "
        << "greater than 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end is returned
   hm1_RcIter = hm1. upper_bound ( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key greater than 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key > 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_map can be found
   // using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.begin( );
   hm1_RcIter = hm1. upper_bound ( hm1_AcIter -> first );
   cout << "The 1st element of hm1 with a key greater than that\n"
        << "of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The first element of hash_map hm1 with a key greater than 2 is: 30.
The hash_map hm1 doesn't have an element with a key greater than 4.
The 1st element of hm1 with a key greater than that
of the initial element of hm1 is: 20.
```

## <a name="hash_mapvalue_comp"></a><a name="value_comp"></a>hash_map:: value_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Zwraca obiekt funkcji, który określa kolejność elementów w hash_map, porównując ich wartości klucza.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji porównania, którego hash_map używa do porządkowania jego elementów.

### <a name="remarks"></a>Uwagi

W przypadku hash_map *m*, jeśli dwa elementy *E1* (*K1*, *D1*) i *e2* (*K2*, *D2*) są obiektami typu [value_type](#value_type), gdzie *K1* i *K2* są ich klucze typu [key_type](#key_type) i *D1* i *D2* są danymi typu [mapped_type](#mapped_type), a następnie `m.value_comp()(e1, e2)` jest równoważne `m.key_comp()(k1, k2)` . Przechowywany obiekt definiuje funkcję członkowską

`bool operator(value_type& left, value_type& right);`

zwraca, **`true`** Jeśli wartość klucza `left` poprzedza i nie jest równa wartości klucza `right` w kolejności sortowania.

### <a name="example"></a>Przykład

```cpp
// hash_map_value_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_map <int, int, hash_compare<int, less<int> > > hm1;
   hash_map <int, int, hash_compare<int, less<int> > >
   ::value_compare vc1 = hm1.value_comp( );
   pair< hash_map<int,int>::iterator, bool > pr1, pr2;

   pr1= hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );
   pr2= hm1.insert ( hash_map <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *pr1.first, *pr2.first ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1 ( *pr2.first, *pr1.first ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."
           << endl;
   }
}
```

## <a name="hash_mapvalue_type"></a><a name="value_type"></a>hash_map:: value_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Typ, który reprezentuje typ obiektu przechowywanego w hash_map.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Uwagi

`value_type`jest zadeklarowany jako `pair<const key_type, mapped_type>` , a nie `pair<key_type, mapped_type>` ponieważ klucze kontenera asocjacyjnego nie mogą być zmieniane przy użyciu niestałego iteratora lub odwołania.

### <a name="example"></a>Przykład

```cpp
// hash_map_value_type.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;
   hash_map <int, int> :: key_type key1;
   hash_map <int, int> :: mapped_type mapped1;
   hash_map <int, int> :: value_type value1;
   hash_map <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );

   // Compare other ways to insert objects into a hash_map
   hm1.insert ( cInt2Int ( 2, 20 ) );
   hm1[ 3 ] = 30;

   // Initializing key1 and mapped1
   key1 = ( hm1.begin( ) -> first );
   mapped1 = ( hm1.begin( ) -> second );

   cout << "The key of first element in the hash_map is "
        << key1 << "." << endl;

   cout << "The data value of first element in the hash_map is "
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
The key of first element in the hash_map is 1.
The data value of first element in the hash_map is 10.
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 30.
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
