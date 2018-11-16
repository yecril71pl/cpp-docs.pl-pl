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
ms.openlocfilehash: 8510bbc89a22fe3eb8df6bbf8ce77db44c7a65a0
ms.sourcegitcommit: d441305fb19131afbd7fc259d8cda63ea26f2343
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51678538"
---
# <a name="hashmultimap-class"></a>hash_multimap — Klasa

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Hash_multimap — klasa kontenera jest rozszerzeniem standardowej biblioteki języka C++ i jest używany do przechowywania i szybkie pobieranie danych z kolekcji, w której każdy element jest parą, która ma klucz sortowania, którego wartość nie musi być unikatowa i skojarzone dane wartości.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare <Key, less <Key>>,
    class Allocator=allocator <pair  <const Key, Type>>>
class hash_multimap
```

### <a name="parameters"></a>Parametry

*Key*<br/>
Typ danych klucza, który ma być przechowywany w hash_multimap.

*Typ*<br/>
Typ danych elementu, który ma być przechowywany w hash_multimap.

*Cechy*<br/>
Typ, który zawiera dwa obiekty funkcyjne, jednej klasy *cech* który będzie można porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność i funkcję mieszania, która jest jednoargumentowy wartości klucza predykatu Mapowanie elementów do niepodpisane liczby całkowite typu `size_t`. Ten argument jest opcjonalny, a `hash_compare<Key, less<Key>>` jest wartością domyślną.

*Allocator*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i dezalokacji pamięci hash_multimap. Ten argument jest opcjonalny, a wartość domyślna to `allocator<pair <const Key, Type>>`.

## <a name="remarks"></a>Uwagi

Hash_multimap — jest:

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.

- Mieszany, ponieważ jego elementy są pogrupowane w przedziały, na podstawie wartości funkcji skrótu dotyczą kluczowych wartości elementów.

- Wielokrotna, ponieważ jej elementy nie muszą mieć unikatowych kluczy, więc jedna wartość klucza może mieć wiele wartości elementów danych z nią skojarzonych.

- Kontenerem skojarzonych par, ponieważ jego wartości elementu różnią się od wartości klucza.

- Klasą szablonu, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Główną zaletą wyznaczania wartości skrótu, za pośrednictwem sortowania jest większą wydajność; Pomyślne mieszania wykonuje wstawień, usuwanie i znajduje w stałej Średni czas w porównaniu z danym proporcjonalny do logarytmu liczby elementów w kontenerze sortowania technik. Wartość elementu w hash_multimap, ale nie wartość jego skojarzonego klucza, może być zmieniona bezpośrednio. Zamiast tego, wartości kluczy skojarzone ze starymi elementami muszą zostać usunięte, a nowe wartości klucza skojarzone z nowymi wstawionymi elementami.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Skrótu kontenery asocjacyjne są zoptymalizowane dla operacji wyszukiwania, wstawiania i usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje są wydajne, gdy jest używana z funkcją dobrze zaprojektowanego wyznaczania wartości skrótu, wykonując je w czasie, który jest średnio stała i nie jest zależna od liczby elementów w kontenerze. Funkcja skrótu dobrze zaprojektowanego generuje jednolity rozkład wartości skrótu i minimalizuje liczbę konfliktów, w którym kolizji jest wyświetlany po odrębnych wartości klucza są mapowane na taką samą wartość skrótu. W najgorszym przypadku za pomocą funkcji skrótu możliwe najgorszy liczby operacji jest proporcjonalna do liczby elementów w sekwencji (liniowy czas).

Hash_multimap — powinna być kontenerem asocjacyjnym z wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Modelem dla tego typu struktury jest uporządkowana lista słów kluczowych ze skojarzonymi wartościami ciągów, dostarczająca np. definicje, w których słowa nie były zawsze zdefiniowane unikalnie. Jeśli zamiast tego słowa kluczowe zostały unikalnie zdefiniowane, tak że klucze są unikatowe, hash_map byłaby kontenerem z wyboru. Jeśli z drugiej strony, przechowywana była tylko lista wyrazów, hash_set będzie poprawny kontener. Gdyby zezwolono na wiele wystąpień wyrazów, hash_multiset byłaby odpowiednią strukturą kontenera.

Hash_multimap — porządkuje sekwencję którą kontroluje, przez wywołanie metody skrótu przechowywaną `Traits` obiektu typu [value_compare](../standard-library/value-compare-class.md). Ten przechowywany obiekt może być dostępna poprzez wywołanie funkcji elementu członkowskiego [key_comp](../standard-library/hash-map-class.md#key_comp). Obiekt funkcyjny musi zachowywać się taka sama jak obiekt klasy [hash_compare —](../standard-library/hash-compare-class.md)`<Key, less<Key>>`. W szczególności dla wszystkich wartości `Key` typu `Key`, wywołanie `Traits (Key)` daje w wyniku rozkład wartości typu `size_t`.

Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Powoduje to dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarny f (x, y) jest obiektem funkcji, która ma dwa obiekty argumentu `x` i `y` i wartość zwracana przez **true** lub **false**. Kolejność nałożona na hash_multimap jest ścisłym słabym porządkowaniem, jeśli predykat binarny jest niezwrotny, przeciwsymetryczny i przechodni oraz jeśli równoważność jest przechodnia, gdzie dwa obiekty `x` i `y` są zdefiniowane jako równoważne, gdy oba f (x y) i są f (y, x) **false**. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

Rzeczywista kolejność elementów w kontrolowanej sekwencji zależy od funkcji mieszania, funkcja szeregowania i bieżący rozmiar tabeli mieszania przechowywanych w obiekcie kontenera. Nie można określić bieżący rozmiar tabeli wyznaczania wartości skrótu, dlatego ogólnie rzecz biorąc nie można przewidzieć kolejności elementów w kontrolowanej sekwencji. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Iterator dostarczony przez klasę hash_multimap jest iteratorem dwukierunkowym, ale funkcje składowych klasy [Wstaw](#insert) i [hash_multimap](#hash_multimap) mają wersje przyjmujące jako parametry szablonu słabszy danych wejściowych Iterator, którego wymagania funkcjonalności są mniejsze niż te gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny hash_multimap wymagania, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny hash_multimap funkcji, ale jest wystarczający, aby można było mówić znacząco o zakresie iteratorów `[First, Last)` w kontekście funkcji składowych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[hash_multimap](#hash_multimap)|Tworzy listę o określonym rozmiarze lub z elementami określonej wartości lub z określonego `allocator` lub jako kopię innej `hash_multimap`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje `allocator` klasy dla `hash_multimap` obiektu.|
|[const_iterator](#const_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać `const` element `hash_multimap`.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do **const** element `hash_multimap`.|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do **const** przechowywanego w `hash_multimap` do odczytu i wykonywania **const** operacji.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **const** element `hash_multimap`.|
|[difference_type](#difference_type)|Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów `hash_multimap` w zakresie pomiędzy elementami wskazywanymi przez Iteratory.|
|[iterator](#iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w `hash_multimap`.|
|[key_compare —](#key_compare)|Typ, który dostarcza obiekt funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `hash_multimap`.|
|[key_type](#key_type)|Typ, który opisuje obiekt klucza sortowania, stanowiący każdy element obiektu `hash_multimap`.|
|[mapped_type](#mapped_type)|Typ, który reprezentuje typ danych przechowywanych w `hash_multimap`.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu w `hash_multimap`.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w `hash_multimap`.|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej `hash_multimap`.|
|[size_type](#size_type)|Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w `hash_multimap`.|
|[value_type](#value_type)|Typ, który dostarcza obiekt funkcji, która może porównać dwa elementy jako klucze sortowania, aby określić ich względną kolejność w `hash_multimap`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[begin](#begin)|Zwraca iterator odnoszący się do pierwszego elementu w `hash_multimap`.|
|[cbegin](#cbegin)|Zwraca iterator stałych adresujący pierwszy element w `hash_multimap`.|
|[cend](#cend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w `hash_multimap`.|
|[Usuń zaznaczenie](#clear)|Usuwa wszystkie elementy `hash_multimap`.|
|[Liczba](#count)|Zwraca liczbę elementów w `hash_multimap` których klucz pasuje do klucza określonego jako parametr.|
|[crbegin](#crbegin)|Zwraca iterator stałych adresujący pierwszy element w odwróconej `hash_multimap`.|
|[crend —](#crend)|Zwraca iterator stałych adresujący lokalizację następującą po ostatnim elemencie w odwróconej `hash_multimap`.|
|[emplace —](#emplace)|Wstawia element skonstruowany w miejscu do `hash_multimap`.|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do `hash_multimap`, ze wskazówką położenia.|
|[pusty](#empty)|Sprawdza, czy `hash_multimap` jest pusty.|
|[koniec](#end)|Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w `hash_multimap`.|
|[equal_range](#equal_range)|Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w `hash_multimap`.|
|[wymazywanie](#erase)|Usuwa element lub zakres elementów w `hash_multimap` z określonych pozycji|
|[Znajdź](#find)|Zwraca iterator odnoszący się lokalizację elementu w `hash_multimap` który ma klucz równoważny z określonym kluczem.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu `allocator` użytego do stworzenia `hash_multimap`.|
|[Wstaw](#insert)|Wstawia element lub zakres elementów do `hash_multimap` na określonej pozycji.|
|[key_comp](#key_comp)|Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w `hash_multimap`.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu w `hash_multimap` , za pomocą klucza wartość, która jest równa lub większa od określonego klucza.|
|[max_size](#max_size)|Zwraca maksymalną długość `hash_multimap`.|
|[rbegin](#rbegin)|Zwraca iterator odnoszący się do pierwszego elementu w odwróconej `hash_multimap`.|
|[rend —](#rend)|Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w odwróconej `hash_multimap`.|
|[Rozmiar](#size)|Określa nowy rozmiar `hash_multimap`.|
|[swap](#swap)|Zamienia elementy z dwóch `hash_multimap`s.|
|[upper_bound —](#upper_bound)|Zwraca iterator do pierwszego elementu w `hash_multimap` , za pomocą klucza wartość, która jest większa od określonego klucza.|
|[value_comp](#value_comp)|Pobiera kopię obiektu porównania, użytego do uporządkowania wartości elementów w `hash_multimap`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[hash_multimap::operator=](#op_eq)|Zastępuje elementy `hash_multimap` kopią innego `hash_multimap`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_map >

**Namespace:** stdext

## <a name="allocator_type"></a>  hash_multimap::allocator_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Typ, który reprezentuje klasę alokatora dla obiektu hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type` synonim dla parametru szablonu jest `Allocator`.

Aby uzyskać więcej informacji na temat `Allocator`, zobacz sekcję Uwagi [hash_multimap — klasa](../standard-library/hash-multimap-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [get_allocator —](#get_allocator) dla przykłady dotyczące używania `allocator_type`.

## <a name="begin"></a>  hash_multimap::BEGIN

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator odnoszący się do pierwszego elementu w hash_multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pierwszego elementu w hash_multimap lub lokalizacji następującej po hash_multimap puste.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `begin` jest przypisany do `const_iterator`, nie można modyfikować elementów w obiekcie hash_multimap. Jeśli wartość zwracaną przez `begin` jest przypisany do `iterator`, elementów w obiekcie hash_multimap może być modyfikowany.

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

## <a name="cbegin"></a>  hash_multimap::cbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator stałych adresujący pierwszy element w hash_multimap.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stały iterator dwukierunkowy odnoszący się do pierwszego elementu w [hash_multimap](../standard-library/hash-multimap-class.md) lub lokalizacji następującej po pustą `hash_multimap`.

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

## <a name="cend"></a>  hash_multimap::cend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator stałych adresujący lokalizację następującą po ostatnim elemencie w hash_multimap.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Const iteratora dwukierunkowego, który dotyczy lokalizacji następującej po ostatnim elemencie w [hash_multimap](../standard-library/hash-multimap-class.md). Jeśli `hash_multimap` jest pusta, następnie `hash_multimap::cend == hash_multimap::begin`.

### <a name="remarks"></a>Uwagi

`cend` Służy do sprawdzenia, czy iterator osiągnął koniec swojej hash_multimap.

Wartość zwrócona przez obiekt `cend` nie należy usuwać odwołania.

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

## <a name="clear"></a>  hash_multimap::Clear

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Usuwa wszystkie elementy hash_multimap.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie hash_multimap::clear funkcja elementu członkowskiego.

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

## <a name="const_iterator"></a>  hash_multimap::const_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać **const** element hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

`const_iterator` Zdefiniowane przez punkty hash_multimap do obiektów [value_type](#value_type), które są typu `pair<const Key, Type>`. Wartość klucza jest dostępna za pośrednictwem pary pierwszego elementu członkowskiego, a wartość elementu zmapowanego jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

Próbę `const_iterator` `cIter` wskazuje element hash_multimap, użyj `->` operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, należy użyć `cIter->first`, który jest odpowiednikiem `(*cIter).first`. Aby uzyskać dostęp do wartości zamapowanego datum dla elementu, należy użyć `cIter->second`, który jest odpowiednikiem `(*cIter).second`.

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin) dla przykłady dotyczące używania `const_iterator`.

## <a name="const_pointer"></a>  hash_multimap::const_pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza wskaźnik do **const** element hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

W większości przypadków [iteratora](#iterator) powinien być używany do uzyskania dostępu do elementów w obiekcie hash_multimap.

## <a name="const_reference"></a>  hash_multimap::const_reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Typ, który zawiera odwołanie do **const** elementu przechowywanego w hash_multimap do odczytu i wykonywania **const** operacji.

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

## <a name="const_reverse_iterator"></a>  hash_multimap::const_reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **const** element hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i jest używany do iterowania po hash_multimap w odwrotnej kolejności.

`const_reverse_iterator` Zdefiniowane przez punkty hash_multimap do obiektów [value_type](#value_type), które są typu `pair<const Key, Type>`, którego pierwszy element członkowski jest kluczem do elementu, jak i drugi, którego element członkowski jest zamapowany podstawy wymiarowej utrzymywane przez element.

Próbę `const_reverse_iterator` `crIter` wskazuje element hash_multimap, użyj `->` operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, należy użyć `crIter->first`, który jest odpowiednikiem `(*crIter).first`. Aby uzyskać dostęp do wartości zamapowanego datum dla elementu, należy użyć `crIter->second`, który jest odpowiednikiem `(*crIter).second`.

### <a name="example"></a>Przykład

Zobacz przykład [rend —](#rend) przykładowy sposób deklarowania i użyj `const_reverse_iterator`.

## <a name="count"></a>  hash_multimap::Count

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca liczbę elementów w hash_multimap, w których klucz pasuje do klucza określonego jako parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz elementy, które mają być dopasowywane z hash_multimap.

### <a name="return-value"></a>Wartość zwracana

1, jeśli hash_multimap zawiera element, którego klucz sortowania jest zgodny z kluczem parametru; 0, jeśli hash_multimap nie zawierają element z kluczem dopasowania.

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca liczbę elementów w zakresie

**[lower_bound (** `key` **), upper_bound (** `key` **))**

które mają wartość klucza *klucz*.

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie hash_multimap::count funkcja elementu członkowskiego.

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

## <a name="crbegin"></a>  hash_multimap::crbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator stałych adresujący pierwszy element w odwróconej hash_multimap.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconej [hash_multimap](../standard-library/hash-multimap-class.md) lub adresowania, który był ostatnim elementem w nieodwróconej `hash_multimap`.

### <a name="remarks"></a>Uwagi

`crbegin` jest używana z odwróconej hash_multimap — podobnie jak [hash_multimap::begin](#begin) jest używana z `hash_multimap`.

Wartością zwracaną `crbegin`, `hash_multimap` nie można zmodyfikować obiektu.

`crbegin` może służyć do iterowania po `hash_multimap` Wstecz.

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

## <a name="crend"></a>  hash_multimap::crend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator stałych adresujący lokalizację następującą po ostatnim elemencie w odwróconej hash_multimap.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iteratora dwukierunkowego, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconej [hash_multimap](../standard-library/hash-multimap-class.md) (miejsca przed pierwszym elementem w nieodwróconej `hash_multimap`).

### <a name="remarks"></a>Uwagi

`crend` jest używana z odwróconej hash_multimap — podobnie jak [hash_multimap::end](#end) jest używana z hash_multimap.

Wartością zwracaną `crend`, `hash_multimap` nie można zmodyfikować obiektu.

`crend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej hash_multimap.

Wartość zwrócona przez obiekt `crend` nie należy usuwać odwołania.

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

## <a name="difference_type"></a>  hash_multimap::difference_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów hash_multimap w zakresie pomiędzy elementami wskazywanymi przez Iteratory.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` Jest typ zwracany, jeśli odjęcie lub inkrementacji poprzez Iteratory kontenera. `difference_type` Jest zazwyczaj używany do reprezentowania liczby elementów w zakresie *[Imię i nazwisko)* między Iteratory `first` i `last`, zawiera element wskazywany przez `first` i zakresu elementy do, z wyjątkiem element wskazywany przez `last`.

Należy pamiętać, że chociaż `difference_type` jest dostępna dla wszystkich iteratorów, które spełniają wymagania iteratora danych wejściowych zawiera klasę iteratorów dwukierunkowych obsługiwane przez odwracalnego kontenerów, takie jak zestaw, odejmowania między Iteratory są tylko obsługiwane przez Iteratory dostępu swobodnego, dostarczone przez kontener dostępu swobodnego, takich jak wektora.

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

## <a name="emplace"></a>  hash_multimap::emplace

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Wstawia element skonstruowany w miejscu do hash_multimap.

```cpp
template <class ValTy>
iterator emplace(ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Wartości używane do przenoszenia konstruowania element do wstawienia do [hash_multimap](../standard-library/hash-multimap-class.md).|

### <a name="return-value"></a>Wartość zwracana

`emplace` Funkcja elementu członkowskiego zwraca iterator, który wskazuje miejsce, w którym dodano nowy element.

### <a name="remarks"></a>Uwagi

[Hash_multimap::value_type](#value_type) elementu jest parą, tak aby wartość elementu zostanie uporządkowana para z pierwszym składnikiem równa wartości klucza i składnik sekundy wartości danych elementu.

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

## <a name="emplace_hint"></a>  hash_multimap::emplace_hint

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Wstawia element skonstruowany w miejscu do hash_multimap, ze wskazówką położenia.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Wartości używane do przenoszenia konstruowania element do wstawienia do [hash_multimap](../standard-library/hash-multimap-class.md) chyba że `hash_multimap` już zawiera tego elementu (lub bardziej ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie są porządkowane).|
|*_Where*|Wskazówki dotyczące właściwe miejsce rozpoczęcia wyszukiwania prawidłowy punkt wstawiania.|

### <a name="return-value"></a>Wartość zwracana

[Hash_multimap::emplace](#emplace) funkcja elementu członkowskiego zwraca iterator, który wskazuje miejsce, w którym wstawiono nowy element do `hash_multimap`.

### <a name="remarks"></a>Uwagi

[Hash_multimap::value_type](#value_type) elementu jest parą, tak aby wartość elementu zostanie uporządkowana para z pierwszym składnikiem równa wartości klucza i składnik sekundy wartości danych elementu.

Wstawiania może wystąpić w amortyzowanym stałym czasie zamiast wartość czasu, jeśli poprzedza punkt wstawiania *_Where*.

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

## <a name="empty"></a>  hash_multimap::Empty

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Sprawdza, czy hash_multimap jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli hash_multimap jest pusta. **false** Jeśli hash_multimap jest niepusty.

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

## <a name="end"></a>  hash_multimap::end

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w hash_multimap.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do lokalizacji następującej po ostatnim elemencie w hash_multimap. Jeśli hash_multimap jest pusty, a następnie hash_multimap::end == hash_multimap::begin.

### <a name="remarks"></a>Uwagi

`end` Służy do sprawdzenia, czy iterator osiągnął koniec swojej hash_multimap.

Wartość zwrócona przez obiekt `end` nie należy usuwać odwołania.

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

## <a name="equal_range"></a>  hash_multimap::equal_range

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca parę iteratorów odpowiednio do pierwszego elementu w hash_multimap z kluczem, który jest większy niż określony klucz i do pierwszego elementu w hash_multimap z kluczem, który jest równy lub większy niż określony klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucz, który ma zostać porównane z klucza sortowania elementu z hash_multimap wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Parę iteratorów tak, aby był pierwszym [lower_bound](#lower_bound) klucz, a drugi jest [upper_bound](#upper_bound) klucza.

Pierwszym iteratorem pary dostęp do `pr` zwróconą przez funkcję elementu członkowskiego, użyj `pr`. **pierwszy** wyłuskać iteratora dolną granicę użyj \*( `pr`. **najpierw**). Aby uzyskać dostęp drugi iterator w parze `pr` zwróconą przez funkcję elementu członkowskiego, użyj `pr`. **drugi** wyłuskać iteratora górną granicę użyj \*( `pr`. **Po drugie**).

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

## <a name="erase"></a>  hash_multimap::ERASE

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Usuwa element lub zakres elementów w hash_multimap z określonych pozycji lub usuwa elementy, które odpowiadają określonemu kluczowi.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_Where*<br/>
Pozycja elementu do usunięcia z hash_multimap.

*pierwszy*<br/>
Pozycja pierwszego elementu są usuwane z hash_multimap.

*ostatni*<br/>
Pozycja tuż za ostatnim elementem usunięte z hash_multimap.

*Klucz*<br/>
Klucz elementów do usunięcia z hash_multimap.

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie funkcje Członkowskie, aby uzyskać iteratora dwukierunkowego, określa pierwszy element pozostający poza wszelkimi elementami usuniętymi lub wskaźnika do końca hash_multimap, jeśli taki element nie istnieje.

Dla trzeciego funkcja elementu członkowskiego zwraca liczbę elementów, które zostały usunięte z hash_multimap.

### <a name="remarks"></a>Uwagi

Funkcje elementów członkowskich nigdy nie zgłasza wyjątku.

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie hash_multimap::erase funkcja elementu członkowskiego.

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

## <a name="find"></a>  hash_multimap::Find

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator odnoszący się do pierwszej lokalizacji elementu w hash_multimap, który ma klucz równoważny z określonym kluczem.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz, które mają być dopasowywane o klucz sortowania elementu z hash_multimap wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Iterator odnoszący się do pierwszej lokalizacji elementu z określonym kluczem lub lokalizację po ostatnim elemencie w hash_multimap, jeśli nie zostanie znalezione dopasowanie dla klucza.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator odnoszący się do elementu w hash_multimap, którego klucz sortowania jest `equivalent` do argumentu opartego na kluczu w obszarze predykat binarny, który wymusza kolejność, w mniej niż porównywalności relacji.

Jeśli wartość zwracaną przez `find` jest przypisany do `const_iterator`, nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracaną przez `find` jest przypisany do `iterator`, można zmodyfikować obiekt hash_multimap.

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

## <a name="get_allocator"></a>  hash_multimap::get_allocator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca kopię obiektu programu przydzielania użytego do stworzenia hash_multimap.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez hash_multimap.

### <a name="remarks"></a>Uwagi

Puli buforów dla klasy hash_multimap — Określ, jak klasa zarządza magazynem. Buforów domyślną dostarczony wraz z klasy kontenera standardowej biblioteki języka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.

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

## <a name="hash_multimap"></a>  hash_multimap::hash_multimap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Tworzy hash_multimap, który jest pusty lub jest kopią całości lub części niektórych innych hash_multimap.

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
|*Al*|Klasa alokatora magazynu ma być używany dla tego obiektu hash_multimap, wartość domyślna to `Allocator`.|
|*Comp*|Funkcja porównywania typu `const Traits` porządkowania elementów w mapie, którego wartość domyślna to `Traits`.|
|*po prawej stronie*|Mapa, w której zestaw zbudowany jest kopią.|
|*pierwszy*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*ostatni*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|
|*IList*|Lista initializer_list do skopiowania.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują obiekt alokatora, który zarządza magazynem pamięci dla hash_multimap i które później mogą być zwracane przez wywołanie metody typu [get_allocator —](#get_allocator). Parametr alokatora jest często pomijane w deklaracjach klas i wstępnego przetwarzania, makra są używane do zastąpienia buforów alternatywne.

Wszystkie konstruktory inicjują ich hash_multimap.

Wszystkie konstruktory zapisują obiekt funkcyjny tego typu `Traits` , jest używany do ustanawiania zamówienie klawiszy hash_multimap, a później mogą być zwracane przez wywołanie metody [key_comp](#key_comp).

Pierwsze trzy konstruktory Określ pusty hash_multimap początkowej; drugi określa typ funkcji porównywania (*Comp*) do użycia podczas ustalania kolejności elementów, a trzeci jawnie określa typ programu przydzielania (`_Al`) ma być używany. Słowo kluczowe `explicit` powoduje pominięcie niektórych rodzajów konwersji typu automatyczne.

Czwarty Konstruktor Określa kopię hash_multimap `Right`.

Następne trzy konstruktory kopiują zakres `First, Last)` mapy uwzględni się rosnącą explicitness, określając typ funkcji porównywania klasy `Traits` oraz alokatorem.

Ósmego Konstruktor przenosi hash_multimap `Right`.

Końcowe trzy konstruktory używają initializer_list.

## <a name="insert"></a>  hash_multimap::INSERT

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

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
|*Val*|Wartość elementu do wstawienia do hash_multimap, chyba że zawiera już ten element lub bardziej ogólnie rzecz biorąc, chyba że jest on już zawiera element, którego klucz ekwiwalentnie porządkowania.|
|*Where*|Wskazówka o tym, gdzie się rozpocząć wyszukiwanie poprawne punktu wstawiania.|
|*pierwszy*|Pozycja pierwszego elementu mają być kopiowane z mapy.|
|*ostatni*|Pozycja tuż za ostatnim elemencie, który można skopiować z mapy.|

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwa `insert` funkcje Członkowskie zwracają iterator, który wskazuje miejsce, w którym dodano nowy element.

Trzecia funkcja członkowska używa initializer_list dla elementów do wstawienia.

Czwarty funkcja elementu członkowskiego wstawia sekwencję wartości elementu do mapy, która odnosi się do każdego elementu kierowanego przez iterator w zakresie `[First, Last)` w określonym zestawie.

Ostatnie dwa `insert` funkcji elementów członkowskich działa tak samo jak pierwsze dwa z tą różnicą, że ich przenoszenia — konstrukcja wstawiona wartość.

### <a name="remarks"></a>Uwagi

[Value_type](#value_type) elementu jest parą, tak, aby wartość elementu uporządkowana para, w którym wartość klucza równą znajduje się pierwszy składnik i drugiego składnika jest równa wartości danych elementu.

Wstawiania może wystąpić w amortyzowanym stałym czasie wskazówki wersji `insert`, zamiast wartość czasu, jeżeli poprzedza punkt wstawiania *gdzie*.

## <a name="iterator"></a>  hash_multimap::iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Uwagi

`iterator` Zdefiniowane przez punkty hash_multimap do obiektów [value_type](#value_type), są typu `pair` \< **const Key, typ**>, którego pierwszy element członkowski jest kluczem do elementu i którego element członkowski jest zamapowany podstawy wymiarowej utrzymywane przez element.

Próbę **iteratora** `Iter` wskazuje element hash_multimap, użyj `->` operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, należy użyć `Iter`  ->  **pierwszy**, która jest równoważna (\* `Iter`). **pierwszy**. Aby uzyskać dostęp do wartości zamapowanego datum dla elementu, należy użyć `Iter`  ->  **drugi**, która jest równoważna (\* `Iter`). **pierwszy**.

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin) przykładowy sposób deklarowania i użyj `iterator`.

## <a name="key_comp"></a>  hash_multimap::key_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w hash_multimap.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji, który hash_multimap używa do porządkowania jego elementów.

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członka

**bool — operator (const Key &** `left` **, const Key &** `right` **);**

Zwraca ona **true** Jeśli `left` poprzedza i nie jest równa `right` w porządku sortowania.

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

## <a name="key_compare"></a>  hash_multimap::key_compare

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza obiekt funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w hash_multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare` synonim dla parametru szablonu jest *cech*.

Aby uzyskać więcej informacji na temat *cech* zobacz [hash_multimap — klasa](../standard-library/hash-multimap-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [key_comp](#key_comp) przykładowy sposób deklarowania i użyj `key_compare`.

## <a name="key_type"></a>  hash_multimap::key_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Typ, który opisuje obiekt klucza sortowania, stanowiący każdy element hash_multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type` synonim dla parametru szablonu jest *klucz*.

Aby uzyskać więcej informacji na temat *klucz*, zobacz sekcję Uwagi [hash_multimap — klasa](../standard-library/hash-multimap-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) przykładowy sposób deklarowania i użyj `key_compare`.

## <a name="lower_bound"></a>  hash_multimap::lower_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator do pierwszego elementu w hash_multimap z kluczem, który jest równy lub większy od określonego klucza.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucz, który ma zostać porównane z klucza sortowania elementu z hash_multimap wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

[Iteratora](#iterator) lub [const_iterator](#const_iterator) który zapewnia lokalizacji elementu w hash_multimap przy użyciu klucza, który jest równy lub większy niż określony klucz argument lub który dotyczy lokalizacji następującej po ostatniej Element hash_multimap, jeśli nie zostanie znalezione dopasowanie dla klucza.

Jeśli wartość zwracaną przez `lower_bound` jest przypisany do `const_iterator`, nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracaną przez `lower_bound` jest przypisany do `iterator`, można zmodyfikować obiekt hash_multimap.

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

## <a name="mapped_type"></a>  hash_multimap::mapped_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Typ, który reprezentuje typ danych przechowywanych w hash_multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Uwagi

`mapped_type` synonim dla parametru szablonu jest *typu*.

Aby uzyskać więcej informacji na temat *typu* zobacz [hash_multimap — klasa](../standard-library/hash-multimap-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) przykładowy sposób deklarowania i użyj `key_type`.

## <a name="max_size"></a>  hash_multimap::max_size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

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

## <a name="op_eq"></a>  hash_multimap::operator =

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zastępuje elementy hash_multimap kopią innego hash_multimap.

```cpp
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*right*|[Hash_multimap](../standard-library/hash-multimap-class.md) są kopiowane do `hash_multimap`.|

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkie elementy istniejących w `hash_multimap`, `operator=` kopiuje lub przenosi zawartość *prawo* do `hash_multimap`.

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

## <a name="pointer"></a>  hash_multimap::Pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza wskaźnik do elementu w hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iteratora](#iterator) powinien być używany do uzyskania dostępu do elementów w obiekcie hash_multimap.

## <a name="rbegin"></a>  hash_multimap::rbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator odnoszący się do pierwszego elementu w odwróconym hash_multimap.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconym hash_multimap lub adresowania, który był ostatnim elementem w nieodwróconej hash_multimap.

### <a name="remarks"></a>Uwagi

`rbegin` jest używana z odwróconej hash_multimap — podobnie jak [rozpocząć](#begin) jest używana z hash_multimap.

Jeśli wartość zwracaną przez `rbegin` jest przypisany do `const_reverse_iterator`, wówczas nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracaną przez `rbegin` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiekt hash_multimap.

`rbegin` może służyć do iterowania po hash_multimap Wstecz.

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

## <a name="reference"></a>  hash_multimap::Reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

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

## <a name="rend"></a>  hash_multimap::rend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w odwróconej hash_multimap.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do lokalizacji następującej po ostatnim elemencie w odwróconej hash_multimap (miejsca przed pierwszym elementem w nieodwróconej hash_multimap).

### <a name="remarks"></a>Uwagi

`rend` jest używana z odwróconej hash_multimap — podobnie jak [zakończenia](#end) jest używana z hash_multimap.

Jeśli wartość zwracaną przez `rend` jest przypisany do [const_reverse_iterator](#const_reverse_iterator), wówczas nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracaną przez `rend` jest przypisany do [reverse_iterator](#reverse_iterator), a następnie można zmodyfikować obiekt hash_multimap.

`rend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej hash_multimap.

Wartość zwrócona przez obiekt `rend` nie należy usuwać odwołania.

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

## <a name="reverse_iterator"></a>  hash_multimap::reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iterowania po hash_multimap w odwrotnej kolejności.

`reverse_iterator` Zdefiniowane przez punkty hash_multimap do obiektów [value_type](#value_type), które są typu `pair` \< **const Key, typ**>. Wartość klucza jest dostępna za pośrednictwem pary pierwszego elementu członkowskiego, a wartość elementu zmapowanego jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

### <a name="example"></a>Przykład

Zobacz przykład [rbegin —](#rbegin) przykładowy sposób deklarowania i użyj `reverse_iterator`.

## <a name="size"></a>  hash_multimap::size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca liczbę elementów w hash_multimap.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość hash_multimap.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie hash_multimap::size funkcja elementu członkowskiego.

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

## <a name="size_type"></a>  hash_multimap::size_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Typ całkowitoliczbowy bez znaku, który zlicza liczbę elementów w hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Zobacz przykład [rozmiar](#size) przykładem sposobu deklarowanie i użycie `size_type`

## <a name="swap"></a>  hash_multimap::swap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zamienia elementy z dwóch hash_multimaps.

```cpp
void swap(hash_multimap& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Hash_multimap, zawierająca elementy, które mają być zamienione lub hash_multimap, której elementy są wymieniane z tymi hash_multimap.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego powoduje unieważnienie nie odwołania wskaźniki i Iteratory, które wyznaczają elementy w dwóch hash_multimaps, której elementy są wymianie.

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

## <a name="upper_bound"></a>  hash_multimap::upper_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zwraca iterator do pierwszego elementu w hash_multimap przy użyciu klucza, który jest większy od określonego klucza.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucz, który ma zostać porównane z klucza sortowania elementu z hash_multimap wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

[Iteratora](#iterator) lub [const_iterator](#const_iterator) który zapewnia lokalizacji elementu w hash_multimap przy użyciu klucza, który jest większy niż określony klucz argument lub który dotyczy lokalizacji następującej po ostatnim elemencie w hash_multimap — Jeśli nie zostanie znalezione dopasowanie dla klucza.

Jeśli wartość zwracaną przez `upper_bound` jest przypisany do `const_iterator`, nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracaną przez `upper_bound` jest przypisany do `iterator`, można zmodyfikować obiekt hash_multimap.

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

## <a name="value_comp"></a>  hash_multimap::value_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Funkcja elementu członkowskiego zwraca obiekt funkcji, która określa kolejność elementów w hash_multimap przez porównanie ich wartości klucza.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji porównywania, korzystającą z hash_multimap celu porządkowania jego elementów.

### <a name="remarks"></a>Uwagi

Aby uzyskać hash_multimap *m*, jeśli dwa elementy *e1* (*k1*, *d1*) i *e2*(*k2* , *d2*) są obiektami typu [value_type](#value_type), gdzie *k1* i *k2* są dla nich kluczami typu [key_type](#key_type) i *d1* i *d2* są ich dane typu [mapped_type](#mapped_type), następnie `m.value_comp()(e1, e2)` jest odpowiednikiem `m.key_comp()(k1, k2)` . Przechowywany obiekt definiuje funkcję członka

`bool operator( value_type& left, value_type& right);`

Zwraca ona **true** Jeśli wartość klucza `left` poprzedza i nie jest równa wartości klucza `right` w porządku sortowania.

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

## <a name="value_type"></a>  hash_multimap::value_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Typ, który reprezentuje typ obiektu przechowywanego w hash_multimap.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Uwagi

`value_type` został zadeklarowany jako pary\<const [key_type](#key_type), [mapped_type](#mapped_type)> i Sparuj nie\<typ_klucza, mapped_type >, ponieważ nie można zmieniać klucze kontenerem za pomocą iteratora stałymi lub odwołania.

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

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
