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
ms.openlocfilehash: 2fe9056996876d24fba285c0c7aaec8607b2509c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375433"
---
# <a name="hash_multimap-class"></a>hash_multimap — Klasa

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Klasa kontenera hash_multimap jest rozszerzeniem standardowej biblioteki języka C++ i jest używana do przechowywania i szybkiego pobierania danych z kolekcji, w której każdy element jest parą, która ma klucz sortowania, którego wartość nie musi być unikatowa i skojarzona wartość danych.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare <Key, less <Key>>,
    class Allocator=allocator <pair  <const Key, Type>>>
class hash_multimap
```

### <a name="parameters"></a>Parametry

*Klucz*\
Typ kluczowych danych, które mają być przechowywane w hash_multimap.

*Typu*\
Typ danych elementu, który ma być przechowywany w hash_multimap.

*Cechy*\
Typ, który zawiera dwa obiekty funkcji, jeden z *cech* klasy, który jest w stanie porównać dwie wartości elementu jako klucze sortowania w celu określenia ich względnej `size_t`kolejności i funkcja mieszania, która jest jednoary predykatu mapowania wartości klucza elementów do niepodpisanych liczbach całkowitych typu . Ten argument jest opcjonalny i `hash_compare<Key, less<Key>>` jest wartością domyślną.

*Programu przydzielania*\
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji hash_multimap i alokacji pamięci. Ten argument jest opcjonalny, `allocator<pair <const Key, Type>>`a wartością domyślną jest .

## <a name="remarks"></a>Uwagi

hash_multimap jest:

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.

- Hashed, ponieważ jego elementy są pogrupowane w zasobnikach na podstawie wartości funkcji mieszania stosowane do wartości klucza elementów.

- Wielokrotna, ponieważ jej elementy nie muszą mieć unikatowych kluczy, więc jedna wartość klucza może mieć wiele wartości elementów danych z nią skojarzonych.

- Kontener zespolone pary, ponieważ jego wartości elementu różnią się od jego wartości klucza.

- Szablon klasy, ponieważ funkcje, które zapewnia, jest ogólny i tak niezależne od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Główną zaletą mieszania nad sortowanie jest większa wydajność; pomyślne mieszanie wykonuje wstawienia, usunięcia i znajduje w stałym średnim czasie w porównaniu z czasem proporcjonalnym do logarytmu liczby elementów w kontenerze dla technik sortowania. Wartość elementu w hash_multimap, ale nie jego skojarzonej wartości klucza, może zostać zmieniona bezpośrednio. Zamiast tego, wartości kluczy skojarzone ze starymi elementami muszą zostać usunięte, a nowe wartości klucza skojarzone z nowymi wstawionymi elementami.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Haszowane kontenery zespolone są zoptymalizowane pod kątem operacji wyszukiwania, wstawiania i usuwania. Funkcje członkowskie, które jawnie obsługują te operacje są wydajne, gdy są używane z dobrze zaprojektowaną funkcją mieszania, wykonując je w czasie, który jest średnio stały i nie zależy od liczby elementów w kontenerze. Dobrze zaprojektowana funkcja mieszania tworzy jednolity rozkład wartości skrótu i minimalizuje liczbę kolizji, gdzie mówi się, że kolizja występuje, gdy różne wartości klucza są mapowane na tę samą wartość skrótu. W najgorszym przypadku z najgorszą możliwą funkcją mieszania liczba operacji jest proporcjonalna do liczby elementów w sekwencji (czas liniowy).

hash_multimap powinny być kontenerem zespolonego z wyboru, gdy warunki kojarzenia wartości z ich klucze są spełnione przez aplikację. Modelem dla tego typu struktury jest uporządkowana lista słów kluczowych ze skojarzonymi wartościami ciągów, dostarczająca np. definicje, w których słowa nie były zawsze zdefiniowane unikalnie. Jeśli zamiast tego słowa kluczowe zostały jednoznacznie zdefiniowane tak, że klucze były unikatowe, a następnie hash_map będzie kontener wyboru. Jeśli, z drugiej strony, tylko lista słów były przechowywane, to hash_set będzie właściwym kontenerem. Jeśli wiele wystąpień wyrazów były dozwolone, a następnie hash_multiset będzie odpowiedniej struktury kontenera.

Hash_multimap porządkuuje sekwencję, jaką kontroluje, wywołując `Traits` przechowywany obiekt mieszania typu [value_compare](../standard-library/value-compare-class.md). Ten przechowywany obiekt może być dostępny, wywołując funkcję elementu członkowskiego [key_comp](../standard-library/hash-map-class.md#key_comp). Taki obiekt funkcji musi zachowywać się tak samo jak obiekt klasy [hash_compare](../standard-library/hash-compare-class.md)`<Key, less<Key>>`. W szczególności dla `Key` wszystkich `Key`wartości typu `Traits (Key)` wywołanie daje rozkład `size_t`wartości typu .

Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Powoduje to kolejność między elementami nieekwidującymi. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarny f(x, y) jest obiektem `x` `y` funkcyjnym, który ma dwa obiekty argumentów i zwraca wartość **true** lub **false**. Kolejność nałożona na hash_multimap jest ścisłym słabym porządkiem, jeśli predykat binarny jest niereflexive, antysymetryczny i przechodni, `x` `y` a jeśli równoważność jest przechodnia, gdzie dwa obiekty i są zdefiniowane jako równoważne, gdy zarówno f(x, y) i f(y, x) są **fałszywe**. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

Rzeczywista kolejność elementów w kontrolowanej sekwencji zależy od funkcji mieszania, funkcji zamawiania i bieżącego rozmiaru tabeli mieszania przechowywanej w obiekcie kontenera. Nie można określić bieżący rozmiar tabeli mieszania, więc nie można ogólnie przewidzieć kolejność elementów w kontrolowanej sekwencji. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Iterator dostarczony przez klasę hash_multimap jest dwukierunkowym iteratorem, ale funkcje członkowskie klasy [wstawiają](#insert) i [hash_multimap](#hash_multimap) mają wersje, które przyjmują jako parametry szablonu słabszy iterator wejściowy, którego wymagania dotyczące funkcjonalności są bardziej minimalne niż wymagania gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każda koncepcja iteratora ma swój własny hash_multimap wymagań, a algorytmy, które z nimi współpracują, muszą ograniczać swoje założenia do wymagań dostarczonych przez ten typ iteratora. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny hash_multimap funkcjonalności, ale wystarczy, aby móc mówić sensownie o zakresie iteratorów `[First, Last)` w kontekście funkcji członkowskich.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Hash_multimap](#hash_multimap)|Tworzy listę określonego rozmiaru lub z elementami określonej wartości `allocator` lub z określonym `hash_multimap`lub jako kopia innego .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który `allocator` reprezentuje klasę `hash_multimap` dla obiektu.|
|[const_iterator](#const_iterator)|Typ, który zapewnia dwukierunkowy iterator, `const` który może `hash_multimap`odczytać element w .|
|[const_pointer](#const_pointer)|Typ, który zapewnia wskaźnik do **const** elementu w `hash_multimap`.|
|[const_reference](#const_reference)|Typ, który zapewnia odwołanie do **const** `hash_multimap` element przechowywane w do odczytu i wykonywania operacji **const.**|
|[Const_reverse_iterator](#const_reverse_iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytać `hash_multimap`dowolny element **const** w .|
|[difference_type](#difference_type)|Typ liczby całkowitej podpisana, który może służyć do `hash_multimap` reprezentowania liczby elementów w zakresie między elementami wskazanymi przez iteratory.|
|[Sterująca](#iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować dowolny element w . `hash_multimap`|
|[key_compare](#key_compare)|Typ, który udostępnia obiekt funkcji, który może porównać dwa klucze `hash_multimap`sortowania, aby określić względną kolejność dwóch elementów w programie .|
|[Key_type](#key_type)|Typ opisujący obiekt klucza sortowania, który `hash_multimap`stanowi każdy element .|
|[mapped_type](#mapped_type)|Typ reprezentujący typ danych przechowywany `hash_multimap`w pliku .|
|[pointer](#pointer)|Typ, który zapewnia wskaźnik do `hash_multimap`elementu w .|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu `hash_multimap`przechowywanego w .|
|[Reverse_iterator](#reverse_iterator)|Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować element w odwróconym `hash_multimap`.|
|[size_type](#size_type)|Niepodpisany typ liczby całkowitej, który może `hash_multimap`reprezentować liczbę elementów w programie .|
|[value_type](#value_type)|Typ, który udostępnia obiekt funkcji, który może porównać dwa elementy `hash_multimap`jako klucze sortowania, aby określić ich względną kolejność w programie .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Rozpocząć](#begin)|Zwraca iteratora adresującego pierwszy `hash_multimap`element w pliku .|
|[cbegin ( cbegin )](#cbegin)|Zwraca iterator const adresowania pierwszego `hash_multimap`elementu w .|
|[cend](#cend)|Zwraca iterator const, który odnosi się do `hash_multimap`lokalizacji, która po pomyślnym ostatnim elemencie w pliku .|
|[Wyczyść](#clear)|Usuwa wszystkie elementy pliku `hash_multimap`.|
|[Liczba](#count)|Zwraca liczbę elementów, `hash_multimap` w których klucz pasuje do klucza określonego przez parametr.|
|[Crbegin](#crbegin)|Zwraca iterator const adresowania pierwszego elementu `hash_multimap`w odwróconym .|
|[Crend](#crend)|Zwraca iterator const, który odnosi się do lokalizacji, która po pomyślnym ostatnim elemencie w odwróconym `hash_multimap`.|
|[miejsce](#emplace)|Wstawia element skonstruowany w `hash_multimap`miejscu do .|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w `hash_multimap`miejscu do , z wskazówką położenia.|
|[Pusty](#empty)|Sprawdza, `hash_multimap` czy a jest pusty.|
|[Końcu](#end)|Zwraca iterator, który odnosi się do lokalizacji, która po pomyślnym ostatnim elemencie w pliku `hash_multimap`.|
|[equal_range](#equal_range)|Zwraca iterator, który odnosi się do lokalizacji, która po pomyślnym ostatnim elemencie w pliku `hash_multimap`.|
|[Wymazać](#erase)|Usuwa element lub zakres elementów `hash_multimap` w określonym położeniu|
|[find](#find)|Zwraca iterator adresowania lokalizacji elementu w, `hash_multimap` który ma klucz równoważny określony klucz.|
|[Get_allocator](#get_allocator)|Zwraca kopię `allocator` obiektu używanego do `hash_multimap`konstruowania pliku .|
|[Wstawić](#insert)|Wstawia element lub zakres elementów do `hash_multimap` określonego położenia.|
|[Key_comp](#key_comp)|Pobiera kopię obiektu porównania używanego do zamawiania kluczy w pliku `hash_multimap`.|
|[lower_bound](#lower_bound)|Zwraca iteratora do pierwszego `hash_multimap` elementu w tym z wartością klucza, która jest równa lub większa niż określony klucz.|
|[Max_size](#max_size)|Zwraca maksymalną długość `hash_multimap`pliku .|
|[rbegin (rbegin)](#rbegin)|Zwraca iteratora adresującego pierwszy element `hash_multimap`w odwróconym .|
|[Rend](#rend)|Zwraca iterator, który odnosi się do lokalizacji, `hash_multimap`która zastępuje ostatni element w odwróconym .|
|[Rozmiar](#size)|Określa nowy rozmiar pliku `hash_multimap`.|
|[Wymiany](#swap)|Wymienia elementy dwóch `hash_multimap`s.|
|[upper_bound](#upper_bound)|Zwraca iteratora do pierwszego `hash_multimap` elementu w tym z wartością klucza, która jest większa niż określony klucz.|
|[value_comp](#value_comp)|Pobiera kopię obiektu porównania używanego do zamawiania `hash_multimap`wartości elementów w pliku .|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[hash_multimap::operator=](#op_eq)|Zastępuje elementy a `hash_multimap` kopią innego `hash_multimap`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_map>

**Obszar nazw:** stdext

## <a name="hash_multimapallocator_type"></a><a name="allocator_type"></a>hash_multimap::allocator_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Typ reprezentujący klasę alokatora dla hash_multimap obiektu.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type`jest synonimem parametru `Allocator`szablonu .

Aby uzyskać `Allocator`więcej informacji na temat , zobacz uwagi sekcji [hash_multimap class](../standard-library/hash-multimap-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [get_allocator](#get_allocator) na przykład za `allocator_type`pomocą .

## <a name="hash_multimapbegin"></a><a name="begin"></a>hash_multimap::begin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator adresowania pierwszy element w hash_multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator adresowania pierwszy element w hash_multimap lub lokalizacji po zastąpieniu pustego hash_multimap.

### <a name="remarks"></a>Uwagi

Jeśli zwracana `begin` wartość jest przypisana `const_iterator`do , elementy w hash_multimap obiektu nie można modyfikować. Jeśli zwracana `begin` wartość jest przypisana `iterator`do , elementy w hash_multimap obiektu mogą być modyfikowane.

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

## <a name="hash_multimapcbegin"></a><a name="cbegin"></a>hash_multimap::cbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator konstacyjny adresowania pierwszy element w hash_multimap.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator const adresujący pierwszy element w [hash_multimap](../standard-library/hash-multimap-class.md) lub lokalizację, która `hash_multimap`zastępuje pusty plik .

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

## <a name="hash_multimapcend"></a><a name="cend"></a>hash_multimap::cend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator const, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_multimap.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator konspiracyjny, który odnosi się do lokalizacji, która zastępuje ostatni element w [hash_multimap](../standard-library/hash-multimap-class.md). Jeśli `hash_multimap` jest pusty, `hash_multimap::cend == hash_multimap::begin`a następnie .

### <a name="remarks"></a>Uwagi

`cend`służy do testowania, czy iterator osiągnął koniec hash_multimap.

Wartość zwrócona `cend` przez nie powinny być wyłuskiwane.

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

## <a name="hash_multimapclear"></a><a name="clear"></a>hash_multimap::wyczyść

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Usuwa wszystkie elementy hash_multimap.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie funkcji hash_multimap:clear elementu członkowskiego.

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

## <a name="hash_multimapconst_iterator"></a><a name="const_iterator"></a>hash_multimap::const_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Typ, który zapewnia dwukierunkowe iteratora, który można odczytać **const** element w hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

Zdefiniowane `const_iterator` przez hash_multimap wskazuje na obiekty [value_type](#value_type), które `pair<const Key, Type>`są typu . Wartość klucza jest dostępna za pośrednictwem pierwszej pary elementów członkowskich, a wartość zamapowany element jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

Aby wyłuskać `const_iterator` `cIter` wskazując element w hash_multimap, należy `->` użyć operatora.

Aby uzyskać dostęp do wartości klucza `cIter->first`dla elementu, `(*cIter).first`należy użyć , co odpowiada . Aby uzyskać dostęp do wartości zamapowanej `cIter->second`bazy pomiarowej `(*cIter).second`dla elementu, należy użyć , co odpowiada .

### <a name="example"></a>Przykład

Zobacz [przykład, aby rozpocząć](#begin) `const_iterator`przykład przy użyciu .

## <a name="hash_multimapconst_pointer"></a><a name="const_pointer"></a>hash_multimap::const_pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Typ, który zapewnia wskaźnik do **const** elementu w hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien służyć do uzyskiwania dostępu do elementów w hash_multimap obiektu.

## <a name="hash_multimapconst_reference"></a><a name="const_reference"></a>hash_multimap::const_reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Typ, który zapewnia odwołanie do **const** element przechowywane w hash_multimap do odczytu i wykonywania operacji **const.**

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

## <a name="hash_multimapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>hash_multimap::const_reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Typ, który zapewnia dwukierunkowy iterator, który może odczytać dowolny element **const** w hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartość elementu i jest używany do iteracji za pośrednictwem hash_multimap w odwrotnej kolejności.

Zdefiniowane `const_reverse_iterator` przez hash_multimap wskazuje na obiekty [value_type](#value_type), które `pair<const Key, Type>`są typu , których pierwszy element członkowski jest kluczem do elementu i którego drugi element jest mapowane bazy pomiarowej przechowywane przez element.

Aby wyłuskać `const_reverse_iterator` `crIter` wskazując element w hash_multimap, należy `->` użyć operatora.

Aby uzyskać dostęp do wartości klucza `crIter->first`dla elementu, `(*crIter).first`należy użyć , co odpowiada . Aby uzyskać dostęp do wartości zamapowanej `crIter->second`bazy pomiarowej `(*crIter).second`dla elementu, należy użyć , co odpowiada .

### <a name="example"></a>Przykład

Zobacz przykład [rend](#rend) na przykład jak zadeklarować `const_reverse_iterator`i użyć .

## <a name="hash_multimapcount"></a><a name="count"></a>hash_multimap::count

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca liczbę elementów w hash_multimap którego klucz pasuje do klucza określonego przez parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz elementów, które mają być dopasowane z hash_multimap.

### <a name="return-value"></a>Wartość zwracana

1, jeśli hash_multimap zawiera element, którego klucz sortowania pasuje do klucza parametru; 0, jeśli hash_multimap nie zawiera elementu z pasującym kluczem.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca liczbę elementów w zakresie

**[lower_bound (** `key` **), upper_bound (** `key` **)**

które mają klucz wartości *klucza*.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie funkcji elementu członkowskiego hash_multimap::count.

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

## <a name="hash_multimapcrbegin"></a><a name="crbegin"></a>hash_multimap::crbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator konstacyjny adresowania pierwszy element w odwróconej hash_multimap.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Const odwrotnej dwukierunkowej iteratora adresowania pierwszego elementu w odwróconej [hash_multimap](../standard-library/hash-multimap-class.md) lub adresowania, co `hash_multimap`było ostatnim elementem w nieodwrotzony .

### <a name="remarks"></a>Uwagi

`crbegin`jest używany z odwróconym hash_multimap tak jak [hash_multimap::begin](#begin) jest `hash_multimap`używany z .

Z wartością `crbegin`zwracaną `hash_multimap` obiektu nie można modyfikować obiektu.

`crbegin`może być używany do iteracji do `hash_multimap` tyłu.

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

## <a name="hash_multimapcrend"></a><a name="crend"></a>hash_multimap::crend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator const, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w odwróconym hash_multimap.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Const odwrotnej dwukierunkowej iteratora, który odnosi się do lokalizacji po ostatniej pozycji elementu w odwróconym [hash_multimap](../standard-library/hash-multimap-class.md) (lokalizacja, która poprzedziła pierwszy element w nieodwrotzony). `hash_multimap`

### <a name="remarks"></a>Uwagi

`crend`jest używany z odwróconym hash_multimap tak jak [hash_multimap::end](#end) jest używany z hash_multimap.

Z wartością `crend`zwracaną `hash_multimap` obiektu nie można modyfikować obiektu.

`crend`można użyć do sprawdzenia, czy odwrotny iterator osiągnął koniec hash_multimap.

Wartość zwrócona `crend` przez nie powinny być wyłuskiwane.

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

## <a name="hash_multimapdifference_type"></a><a name="difference_type"></a>hash_multimap::d00_typ

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Typ liczby całkowitej podpisana, który może służyć do reprezentowania liczby elementów hash_multimap w zakresie między elementami wskazywane przez iteratory.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Jest `difference_type` to typ zwracany podczas odejmowania lub zwiększania za pośrednictwem iteratorów kontenera. Jest `difference_type` zazwyczaj używany do reprezentowania liczby elementów w zakresie *[ pierwszy, ostatni)* między iteratorów `first` i `last`, zawiera element wskazany przez `first` i `last`zakres elementów do, ale nie w tym element wskazany przez .

Należy zauważyć, że chociaż `difference_type` jest dostępny dla wszystkich iteratorów, które spełniają wymagania iteratora wejściowego, który obejmuje klasę dwukierunkowych iteratorów obsługiwanych przez odwracalne kontenery, takie jak zestaw, odejmowanie między iteratorami jest obsługiwane tylko przez iteratory dostępu losowego dostarczane przez kontener dostępu losowego, taki jak wektor.

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

## <a name="hash_multimapemplace"></a><a name="emplace"></a>hash_multimap::miejsce

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Wstawia element skonstruowany w miejscu do hash_multimap.

```cpp
template <class ValTy>
iterator emplace(ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Wartość używana do przenoszenia konstrukcji elementu, który ma zostać wstawiony do [hash_multimap](../standard-library/hash-multimap-class.md).|

### <a name="return-value"></a>Wartość zwracana

Funkcja `emplace` elementu członkowskiego zwraca iteratora, który wskazuje na pozycję, w której nowy element został wstawiony.

### <a name="remarks"></a>Uwagi

[hash_multimap::value_type](#value_type) elementu jest parą, dzięki czemu wartość elementu będzie uporządkowaną parą z pierwszym składnikiem równym wartości klucza, a drugim składnikiem równym wartości danych elementu.

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

## <a name="hash_multimapemplace_hint"></a><a name="emplace_hint"></a>hash_multimap::emplace_hint

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Wstawia element skonstruowany w miejscu do hash_multimap, z podpowiedzią o umieszczeniu.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Wartość używana do przenoszenia konstruowania elementu, który ma `hash_multimap` zostać wstawiony do [hash_multimap,](../standard-library/hash-multimap-class.md) chyba że już zawiera ten element (lub, bardziej ogólnie, element, którego klucz jest równoważno uporządkowany).|
|*_where*|Wskazówka dotycząca miejsca, aby rozpocząć wyszukiwanie prawidłowego punktu wstawiania.|

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego [hash_multimap::emplace](#emplace) zwraca iterator, który wskazuje pozycję, w której `hash_multimap`nowy element został wstawiony do pliku .

### <a name="remarks"></a>Uwagi

[hash_multimap::value_type](#value_type) elementu jest parą, dzięki czemu wartość elementu będzie uporządkowaną parą z pierwszym składnikiem równym wartości klucza, a drugim składnikiem równym wartości danych elementu.

Wstawienie może wystąpić w zamortyzowanym czasie stałym, a nie w czasie logarytmicznym, jeśli punkt wstawiania natychmiast następuje *po _Where*.

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

## <a name="hash_multimapempty"></a><a name="empty"></a>hash_multimap::empty

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Sprawdza, czy hash_multimap jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli hash_multimap jest pusta; **false,** jeśli hash_multimap jest niepusty.

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

## <a name="hash_multimapend"></a><a name="end"></a>hash_multimap::end

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_multimap.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Dwukierunkowy iterator, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_multimap. Jeśli hash_multimap jest pusta, hash_multimap::end == hash_multimap::begin.

### <a name="remarks"></a>Uwagi

`end`służy do testowania, czy iterator osiągnął koniec hash_multimap.

Wartość zwrócona `end` przez nie powinny być wyłuskiwane.

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

## <a name="hash_multimapequal_range"></a><a name="equal_range"></a>hash_multimap::equal_range

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca parę iteratorów odpowiednio do pierwszego elementu w hash_multimap z kluczem, który jest większy niż określony klucz i do pierwszego elementu w hash_multimap z kluczem, który jest równy lub większy niż klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz argumentu, który ma być porównywany z kluczem sortowania elementu z hash_multimap przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

Para iteratorów taka, że pierwsza jest [lower_bound](#lower_bound) klucza, a druga [jest upper_bound](#upper_bound) klucza.

Aby uzyskać dostęp do pierwszego `pr` iteratora pary `pr`zwróconej przez funkcję elementu członkowskiego, należy użyć programu . **pierwszy** i wyłuskać dolną iterator, użyj \*( `pr`. **po pierwsze**). Aby uzyskać dostęp do drugiego `pr` iteratora pary `pr`zwróconej przez funkcję elementu członkowskiego, należy użyć programu . **drugi** i wyłuskać górną granicę iteratora, użyj \*( `pr`. **drugi**).

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

## <a name="hash_multimaperase"></a><a name="erase"></a>hash_multimap::wymaż

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Usuwa element lub zakres elementów w hash_multimap z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_where*\
Położenie elementu, który ma zostać usunięty z hash_multimap.

*Pierwszym*\
Położenie pierwszego elementu usunięte z hash_multimap.

*Ostatnio*\
Pozycja tuż za ostatnim elementem usuniętym z hash_multimap.

*Klucz*\
Klucz elementów, które mają zostać usunięte z hash_multimap.

### <a name="return-value"></a>Wartość zwracana

Dla pierwszych dwóch funkcji elementów członkowskich dwukierunkowe iterator, który wyznacza pierwszy element pozostałych poza wszystkie elementy usunięte lub wskaźnik na końcu hash_multimap jeśli taki element nie istnieje.

Dla funkcji trzeciego elementu członkowskiego zwraca liczbę elementów, które zostały usunięte z hash_multimap.

### <a name="remarks"></a>Uwagi

Funkcje członkowskie nigdy nie zgłaszają wyjątku.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie funkcji hash_multimap::erase element członkowski.

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

## <a name="hash_multimapfind"></a><a name="find"></a>hash_multimap::znajdź

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator adresowania pierwszej lokalizacji elementu w hash_multimap, który ma klucz równoważny określony klucz.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz, który ma być dopasowany przez klucz sortowania elementu z hash_multimap przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

Iterator, który odnosi się do pierwszej lokalizacji elementu z określonym kluczem lub lokalizacji po pomyślnym ostatniego elementu w hash_multimap jeśli nie zostanie znalezione żadne dopasowanie dla klucza.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iteratora, który odnosi się do `equivalent` elementu w hash_multimap którego klucz sortowania jest klucz argumentu w predykacie binarnym, który wywołuje kolejność na podstawie relacji mniejszej niż porównywalność.

Jeśli wartość zwracana `find` jest przypisana `const_iterator`do , hash_multimap obiektu nie można zmodyfikować. Jeśli wartość zwracana `find` jest przypisana `iterator`do , hash_multimap obiekt może być modyfikowany.

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

## <a name="hash_multimapget_allocator"></a><a name="get_allocator"></a>hash_multimap::get_allocator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca kopię obiektu alokatora używanego do konstruowania hash_multimap.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez hash_multimap.

### <a name="remarks"></a>Uwagi

Alokatory dla klasy hash_multimap określają sposób zarządzania magazynem przez klasę. Domyślne alokatory dostarczane z klasami kontenerów biblioteki standardowej języka C++ są wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym tematem języka C++.

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

## <a name="hash_multimaphash_multimap"></a><a name="hash_multimap"></a>hash_multimap::hash_multimap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Tworzy hash_multimap, który jest pusty lub jest kopią całości lub części innego hash_multimap.

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
|*Al*|Klasa alokatora magazynu, która ma być używana dla tego `Allocator`obiektu hash_multimap, który domyślnie ma wartość .|
|*Comp*|Funkcja porównywania `const Traits` typu używana do zamawiania elementów na `Traits`mapie, która domyślnie ma wartość .|
|*Prawo*|Mapa, której skonstruowany zestaw ma być kopią.|
|*Pierwszym*|Położenie pierwszego elementu w zakresie elementów do skopiowania.|
|*Ostatnio*|Położenie pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|
|*Ilist*|initializer_list do skopiowania.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują typ obiektu alokatora, który zarządza magazynem pamięci dla hash_multimap i który można później zwrócić, wywołując [get_allocator](#get_allocator). Parametr alokatora jest często pomijany w deklaracjach klas, a makra przetwarzania wstępnego są używane do zastępowania alternatywnych alokatorów.

Wszystkie konstruktory inicjują swoje hash_multimap.

Wszystkie konstruktory przechowują `Traits` obiekt funkcji typu, który jest używany do ustanawiania kolejności wśród kluczy hash_multimap i może być później zwrócony przez wywołanie [key_comp](#key_comp).

Pierwsze trzy konstruktory określają pusty początkowy hash_multimap; drugi określa typ funkcji porównania (*Comp*), która ma być używana do ustalenia kolejności elementów, a`_Al`trzecia jawnie określa typ alokatora ( ) do użycia. Słowo `explicit` kluczowe pomija niektóre rodzaje konwersji typu automatycznego.

Czwarty konstruktor określa kopię hash_multimap `Right`.

Następne trzy konstruktory `First, Last)` skopiować zakres mapy z coraz jawności w `Traits` określaniu typu funkcji porównania klasy i alokatora.

Ósmy konstruktor przesuwa `Right`hash_multimap .

Ostatnich trzech konstruktorów użyć initializer_list.

## <a name="hash_multimapinsert"></a><a name="insert"></a>hash_multimap::wstawianie

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

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
|*Val*|Wartość elementu, który ma zostać wstawiony do hash_multimap, chyba że zawiera już ten element lub bardziej ogólnie, chyba że zawiera już element, którego klucz jest równocześnie uporządkowany.|
|*Gdzie*|Wskazówka, gdzie rozpocząć wyszukiwanie prawidłowego punktu wstawiania.|
|*Pierwszym*|Położenie pierwszego elementu, który ma zostać skopiowany z mapy.|
|*Ostatnio*|Pozycja tuż za ostatnim elementem, który ma zostać skopiowany z mapy.|

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie `insert` funkcje elementu członkowskiego zwracają iteratora, który wskazuje na pozycję, w której nowy element został wstawiony.

Funkcja trzeciego elementu członkowskiego używa initializer_list dla elementów, które mają zostać wstawione.

Funkcja czwartego elementu członkowskiego wstawia sekwencję wartości elementów do mapy, która odpowiada `[First, Last)` każdemu elementowi adresowanemu przez iteratora w zakresie określonego zestawu.

Ostatnie dwie `insert` funkcje członkowskie zachowują się tak samo jak pierwsze dwa, z tą różnicą, że przenoszą-konstruują wstawioną wartość.

### <a name="remarks"></a>Uwagi

[value_type](#value_type) elementu jest parą, dzięki czemu wartość elementu będzie uporządkowaną parą, w której pierwszy składnik jest równy wartości klucza, a drugi składnik jest równy wartości danych elementu.

Wstawienie może wystąpić w zamortyzowanym stałym czasie dla wersji podpowiedzi `insert`, zamiast czasu logarytmicznego, jeśli punkt wstawiania natychmiast następuje *Gdzie*.

## <a name="hash_multimapiterator"></a><a name="iterator"></a>hash_multimap::iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować dowolny element w hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Uwagi

`iterator` Zdefiniowane przez hash_multimap wskazuje na obiekty [value_type](#value_type), które `pair` \< są typu **const Key, Type**>, którego pierwszy element członkowski jest kluczem do elementu i którego drugim elementem jest mapowana baza pomiarowa utrzymywana przez element.

Aby wyłuskać **iteratora** `Iter` wskazującego element w hash_multimap, `->` należy użyć operatora.

Aby uzyskać dostęp do wartości klucza `Iter`  -> dla elementu, należy\* `Iter`użyć **najpierw**, co odpowiada ( ). **pierwszy**. Aby uzyskać dostęp do wartości zamapowanych datum dla elementu, należy `Iter`  -> użyć **drugiej**, która jest równoważna (\* `Iter`). **pierwszy**.

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz [przykład, aby rozpocząć](#begin) przykład jak zadeklarować i używać `iterator`.

## <a name="hash_multimapkey_comp"></a><a name="key_comp"></a>hash_multimap::key_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Pobiera kopię obiektu porównania używanego do zamawiania kluczy w hash_multimap.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji używany przez hash_multimap do uporządkowania jego elementów.

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję elementu członkowskiego

**bool operator(const Key&** `left` **, const Key** `right` **&);**

który zwraca `left` **true,** jeśli poprzedza `right` i nie jest równa w kolejności sortowania.

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

## <a name="hash_multimapkey_compare"></a><a name="key_compare"></a>hash_multimap::key_compare

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Typ, który udostępnia obiekt funkcji, który można porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w hash_multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare`jest synonimem parametru szablonu *Cechy*.

Aby uzyskać więcej informacji na temat *cech,* zobacz temat [hash_multimap Klasa.](../standard-library/hash-multimap-class.md)

### <a name="example"></a>Przykład

Zobacz przykład [key_comp](#key_comp) na przykład jak zadeklarować i `key_compare`używać .

## <a name="hash_multimapkey_type"></a><a name="key_type"></a>hash_multimap::key_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Typ, który opisuje obiekt klucza sortowania, który stanowi każdy element hash_multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type`jest synonimem parametru *szablonu Key*.

Aby uzyskać więcej informacji na temat *klucza,* zobacz uwagi sekcji [hash_multimap class](../standard-library/hash-multimap-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) na przykład jak zadeklarować i `key_compare`używać .

## <a name="hash_multimaplower_bound"></a><a name="lower_bound"></a>hash_multimap::lower_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator do pierwszego elementu w hash_multimap z kluczem, który jest równy lub większy niż określony klucz.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz argumentu, który ma być porównywany z kluczem sortowania elementu z hash_multimap przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

[Iterator](#iterator) lub [const_iterator,](#const_iterator) który odnosi się do lokalizacji elementu w hash_multimap z kluczem, który jest równy lub większy niż klucz argumentu lub który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_multimap jeśli nie znaleziono dopasowania dla klucza.

Jeśli wartość zwracana `lower_bound` jest przypisana `const_iterator`do , hash_multimap obiektu nie można zmodyfikować. Jeśli wartość zwracana `lower_bound` jest przypisana `iterator`do , hash_multimap obiekt może być modyfikowany.

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

## <a name="hash_multimapmapped_type"></a><a name="mapped_type"></a>hash_multimap::mapped_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Typ reprezentujący typ danych przechowywany w hash_multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Uwagi

`mapped_type`jest synonimem parametru szablonu *Typ*.

Aby uzyskać więcej informacji na temat *Typ* zobacz [hash_multimap temat klasy.](../standard-library/hash-multimap-class.md)

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) na przykład jak zadeklarować i `key_type`używać .

## <a name="hash_multimapmax_size"></a><a name="max_size"></a>hash_multimap::max_size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

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

## <a name="hash_multimapoperator"></a><a name="op_eq"></a>hash_multimap::operator=

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zastępuje elementy hash_multimap kopią innego hash_multimap.

```cpp
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Prawo*|[hash_multimap](../standard-library/hash-multimap-class.md) kopiowany do pliku `hash_multimap`.|

### <a name="remarks"></a>Uwagi

Po wymazaniu istniejących elementów `hash_multimap` `operator=` w programie , albo kopiuje `hash_multimap`lub przenosi zawartość w *prawo* do .

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

## <a name="hash_multimappointer"></a><a name="pointer"></a>hash_multimap::pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Typ, który zapewnia wskaźnik do elementu w hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien służyć do uzyskiwania dostępu do elementów w hash_multimap obiektu.

## <a name="hash_multimaprbegin"></a><a name="rbegin"></a>hash_multimap::rbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator adresowania pierwszy element w odwróconej hash_multimap.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnej dwukierunkowej iteratora adresowania pierwszego elementu w odwróconej hash_multimap lub adresowania, co było ostatnim elementem w hash_multimap nieodwróconych.

### <a name="remarks"></a>Uwagi

`rbegin`jest używany z odwróconym hash_multimap tak jak [begin](#begin) jest używany z hash_multimap.

Jeśli wartość zwracana `rbegin` jest przypisana `const_reverse_iterator`do , wówczas nie można zmodyfikować hash_multimap obiektu. Jeśli zwracana `rbegin` wartość jest przypisana do `reverse_iterator`, a następnie hash_multimap obiekt może być modyfikowany.

`rbegin`może być używany do iteracji przez hash_multimap do tyłu.

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

## <a name="hash_multimapreference"></a><a name="reference"></a>hash_multimap::odwołanie

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

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

## <a name="hash_multimaprend"></a><a name="rend"></a>hash_multimap::rend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator, który odnosi się do lokalizacji po pomyślnym ostatniego elementu w odwróconym hash_multimap.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnej dwukierunkowej iteratora, który odnosi się do lokalizacji po pomyślnym ostatni element w odwróconej hash_multimap (lokalizacja, która poprzedziła pierwszy element w hash_multimap nieodwrotnych).

### <a name="remarks"></a>Uwagi

`rend`jest używany z odwróconym hash_multimap tak jak [koniec](#end) jest używany z hash_multimap.

Jeśli wartość zwracana jest przypisana `rend` do [const_reverse_iterator](#const_reverse_iterator), nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracana `rend` jest przypisana do [reverse_iterator](#reverse_iterator), wówczas można zmodyfikować hash_multimap obiekt.

`rend`można użyć do sprawdzenia, czy odwrotny iterator osiągnął koniec hash_multimap.

Wartość zwrócona `rend` przez nie powinny być wyłuskiwane.

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

## <a name="hash_multimapreverse_iterator"></a><a name="reverse_iterator"></a>hash_multimap::reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Typ, który zapewnia dwukierunkowy iterator, który może odczytywać lub modyfikować element w odwróconym hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iteracji przez hash_multimap w odwrotnej kolejności.

Zdefiniowane `reverse_iterator` przez hash_multimap wskazuje na obiekty [value_type](#value_type), które są `pair` \< typu **const Key, Type**>. Wartość klucza jest dostępna za pośrednictwem pierwszej pary elementów członkowskich, a wartość zamapowany element jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

### <a name="example"></a>Przykład

Zobacz przykład [dla rbegin](#rbegin) na przykład jak `reverse_iterator`zadeklarować i używać .

## <a name="hash_multimapsize"></a><a name="size"></a>hash_multimap::size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca liczbę elementów w hash_multimap.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość hash_multimap.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie funkcji elementu członkowskiego hash_multimap::size.

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

## <a name="hash_multimapsize_type"></a><a name="size_type"></a>hash_multimap::size_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Niepodpisany typ liczby całkowitej, który zlicza liczbę elementów w hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Zobacz przykład [rozmiaru,](#size) aby uzyskać przykład deklarowania i używania`size_type`

## <a name="hash_multimapswap"></a><a name="swap"></a>hash_multimap::swap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Wymienia elementy dwóch hash_multimaps.

```cpp
void swap(hash_multimap& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
hash_multimap dostarczenie elementów, które mają być zamienione lub hash_multimap których elementy mają być wymieniane z elementami hash_multimap.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego unieważnia żadnych odwołań, wskaźników lub iteratorów, które wyznaczają elementy w dwóch hash_multimaps których elementy są wymieniane.

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

## <a name="hash_multimapupper_bound"></a><a name="upper_bound"></a>hash_multimap::upper_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Zwraca iteratora do pierwszego elementu w hash_multimap z kluczem, który jest większy niż określony klucz.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*\
Klucz argumentu, który ma być porównywany z kluczem sortowania elementu z hash_multimap przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

[Iterator](#iterator) lub [const_iterator,](#const_iterator) który odnosi się do lokalizacji elementu w hash_multimap z kluczem, który jest większy niż klucz argumentu lub który odnosi się do lokalizacji po pomyślnym ostatniego elementu w hash_multimap jeśli nie znaleziono dopasowania dla klucza.

Jeśli wartość zwracana `upper_bound` jest przypisana `const_iterator`do , hash_multimap obiektu nie można zmodyfikować. Jeśli wartość zwracana `upper_bound` jest przypisana `iterator`do , hash_multimap obiekt może być modyfikowany.

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

## <a name="hash_multimapvalue_comp"></a><a name="value_comp"></a>hash_multimap::value_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Funkcja elementu członkowskiego zwraca obiekt funkcji, który określa kolejność elementów w hash_multimap, porównując ich wartości klucza.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji porównania, który hash_multimap używa do uporządkowania jego elementów.

### <a name="remarks"></a>Uwagi

Dla hash_multimap *m*, jeśli dwa elementy *e1* (*k1*, *d1*) i *e2*(*k2*, *d2*) są obiektami typu [value_type,](#value_type)gdzie *k1* i *k2* są ich klucze typu `m.key_comp()(k1, k2)` [key_type](#key_type) i *d1* i *d2* są ich dane typu [mapped_type,](#mapped_type)a następnie `m.value_comp()(e1, e2)` jest odpowiednikiem . Przechowywany obiekt definiuje funkcję elementu członkowskiego

`bool operator( value_type& left, value_type& right);`

który zwraca **wartość true,** jeśli wartość klucza `left` poprzedza i `right` nie jest równa wartości klucza w kolejności sortowania.

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

## <a name="hash_multimapvalue_type"></a><a name="value_type"></a>hash_multimap::value_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Typ reprezentujący typ obiektu przechowywanego w hash_multimap.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Uwagi

`value_type`jest zadeklarowany\<jako par const [key_type, mapped_type](#mapped_type)> i nie\<parować key_type, mapped_type>, ponieważ klucze kontenera zespolone nie mogą być zmieniane za pomocą niejednostkowe iteratora lub odwołania. [key_type](#key_type)

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

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Odwołanie do standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
