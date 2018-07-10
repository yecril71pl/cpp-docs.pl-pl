---
title: hash_map — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68d3ed6e9274fdfad38ad7ed8cdd9f8e83e0630a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849083"
---
# <a name="hashmap-class"></a>hash_map — Klasa

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Przechowuje i szybko pobiera dane z kolekcji, w którym każdy element jest parę klucza sortowania, którego wartość jest unikatowa i wartość skojarzonych danych.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<pair <const Key, Type>>>
class hash_map
```

### <a name="parameters"></a>Parametry

`Key` Typ danych klucza mają być przechowywane w hash_map.

`Type` Typ danych elementu mają być przechowywane w hash_map.

`Traits` Typu, który obejmuje dwa obiekty funkcji, jednym z Porównaj klasy możliwe do porównania dwóch wartości elementu jako klucze sortowania, aby określić ich kolejność względną i skrót funkcji, która jest predykat jednoargumentowy mapowanie wartości klucza elementów do liczb całkowitych bez znaku typu `size_t`. Ten argument jest opcjonalny, a hash_compare — < `Key`, mniej < `Key`>> jest wartością domyślną.

`Allocator` Typ reprezentujący obiekt alokatora przechowywane, który hermetyzuje szczegółowe informacje dotyczące alokacji hash_map i cofania alokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to alokatora < pair < stała `Key`, `Type`>>.

## <a name="remarks"></a>Uwagi

Hash_map — jest:

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.

- Wartość skrótu, ponieważ jej elementy są pogrupowane w pakiety na podstawie wartości funkcji skrótu zastosowane do wartości kluczy elementów.

- Unikatowy w tym sensie, że każdy z jego elementów musi mieć unikatowy klucz.

- Kontenerem skojarzonych par, ponieważ jej wartości danych elementu różnią się od wartości klucza.

- Klasą szablonu, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Główną zaletą tworzenia skrótów za pośrednictwem sortowanie jest większą wydajność; wykonuje wstawienia, usuwanie i wyszukuje w stałej Średni czas w porównaniu z danej chwili proporcjonalna do logarytmu liczba elementów w kontenerze sortowania techniki pomyślnego tworzenia skrótów. Wartość elementu w hash_map, ale nie skojarzone wartości klucza, można zmienić bezpośrednio. Zamiast tego, wartości kluczy skojarzone ze starymi elementami muszą zostać usunięte, a nowe wartości klucza skojarzone z nowymi wstawionymi elementami.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Kontenery asocjacyjna skrótu są zoptymalizowane pod kątem operacji wyszukiwania, wstawiania i usuwania. Funkcje Członkowskie, które jawnie obsługują te operacje są wydajne, gdy jest używany z funkcji skrótu dobrze zaprojektowanego, wykonywanie ich w czasie, który jest średnio stała i nie jest zależna od liczby elementów w kontenerze. Funkcja skrótu dobrze zaprojektowanego tworzy uniform rozkład wartości skrótu i minimalizuje liczbę konfliktów, gdzie jest określany kolizji występuje, gdy różne wartości klucza są zamapowane na tę samą wartość skrótu. W najgorszym przypadku przy użyciu najgorszy funkcji skrótu to możliwe liczba operacji jest proporcjonalna do liczby elementów w sekwencji (czas liniowej).

Hash_map — powinien być asocjacyjnej kontener wyboru po spełnieniu warunków kojarzenie wartości z ich kluczy przez aplikację. Model dla tego typu struktury jest uporządkowana lista jednoznacznie występującą słowa kluczowe skojarzone ciągami, zapewniając, że, definicje. Jeśli zamiast tego wyrażenie ma więcej niż jedną definicję poprawne, tak, aby nie były unikatowe klucze, hash_multimap będzie kontener wyboru. Jeśli z drugiej strony, są przechowywane tylko listę słów, hash_set będzie poprawny kontenera. W przypadku wielu wystąpień słowa były dozwolone, hash_multiset byłoby struktury odpowiedniego kontenera.

Hash_map porządkuje sekwencji kontroluje wywołując skrótu przechowywaną `Traits` obiekt klasy [value_compare](../standard-library/value-compare-class.md). Ten obiekt przechowywane, mogą być używane przez wywołanie funkcji Członkowskich [key_comp](#key_comp). Obiekt funkcji musi działają tak samo, jak obiekt klasy [hash_compare —](../standard-library/hash-compare-class.md)< klucza mniej\<klucza >>. W szczególności dla wszystkich wartości `Key` typu `Key`, wywołanie `Traits`( `Key` ) daje rozkład wartości typu `size_t`.

Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Binarny f(x y) predykatu jest obiektem funkcji, która ma dwa obiekty argument `x` i `y` i wartością zwracaną `true` lub `false`. Kolejność na hash_map jest niska strict, porządkowanie, jeśli binarne predykat jest niezwrotne antysymetryczne dają w wyniku i przechodnie i jeśli równoważność przechodnie, gdy dwa obiekty x i y są zdefiniowane jako równoważne, jeśli zarówno f (x, y), jak i f (y, x) mają wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

Rzeczywiste kolejność elementów w kontrolowanej sekwencji zależy od funkcji skrótu, funkcja porządkowania i bieżący rozmiar tablicy skrótów przechowywane w obiekcie kontenera. Nie można ustalić bieżący rozmiar tablicy skrótów, więc nie można przewidzieć ogólnie kolejność elementów w kontrolowanej sekwencji. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Iteratora podał hash_map — klasa jest iteratora dwukierunkowego, ale funkcje Członkowskie klas [Wstaw](#insert) i [hash_map](#hash_map) wersje przyjmować jako parametry szablonu słabszych iteratora wejściowych, wymagania funkcji, których są bardziej minimalne niż gwarantowane przez klasę Iteratory dwukierunkowego. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcji, ale jest wystarczające, aby można było uzyskać wiarygodny porozmawiać na temat zakresu Iteratory `[First, Last)` w kontekście funkcji elementów członkowskich klasy.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[hash_map](#hash_map)|Konstruuje `hash_map` jest pusta lub oznacza to kopie wszystkich lub niektórych innych części `hash_map`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ reprezentujący `allocator` klasy dla `hash_map` obiektu.|
|[const_iterator](#const_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element `hash_map`.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do `const` element `hash_map`.|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do `const` element przechowywane w `hash_map` do odczytu i wykonywania `const` operacji.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element `hash_map`.|
|[difference_type](#difference_type)|Wpisz liczbę całkowitą ze znakiem, służący do reprezentowania liczbę elementów `hash_map` w zakresie między elementami wskazywana przez Iteratory.|
|[iterator](#iterator)|Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować dowolny element w `hash_map`.|
|[key_compare](#key_compare)|Typ, który zawiera obiekt funkcji, które można porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `hash_map`.|
|[key_type](#key_type)|Typ zawiera opis obiektu klucza sortowania, który stanowi każdy element `hash_map`.|
|[mapped_type](#mapped_type)|Typ reprezentujący typ danych przechowywanych w `hash_map`.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu `hash_map`.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywane w `hash_map`.|
|[reverse_iterator](#reverse_iterator)|Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować elementu w odwróconej `hash_map`.|
|[size_type](#size_type)|Typu Liczba całkowita bez znaku, który może reprezentować liczbę elementów w `hash_map`.|
|[value_type](#value_type)|Typ, który zawiera obiekt funkcji, który można porównać dwóch elementów jako klucze sortowania, aby określić ich kolejność względne w `hash_map`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[at](#at)|Odnajduje element `hash_map` o określonej wartości klucza.|
|[begin](#begin)|Zwraca iteratora adresowania pierwszym elementem w `hash_map`.|
|[cbegin](#cbegin)|Zwraca const iteratora adresowania pierwszym elementem w `hash_map`.|
|[cend](#cend)|Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w `hash_map`.|
|[Wyczyść](#clear)|Usuwa wszystkie elementy `hash_map`.|
|[Liczba](#count)|Zwraca liczbę elementów w `hash_map` którego klucz odpowiada parametr określony klucz.|
|[crbegin](#crbegin)|Zwraca const iteratora adresowania pierwszym elementem w odwróconej `hash_map`.|
|[crend](#crend)|Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w odwrotnej `hash_map`.|
|[emplace](#emplace)|Wstawia element w miejscu do skonstruować `hash_map`.|
|[emplace_hint](#emplace_hint)|Wstawia element w miejscu do skonstruować `hash_map`, ze wskazówką umieszczania.|
|[pusty](#empty)|Sprawdza, czy `hash_map` jest pusta.|
|[Koniec](#end)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w `hash_map`.|
|[equal_range](#equal_range)|Zwraca parę Iteratory, odpowiednio do pierwszego elementu w `hash_map` za pomocą klucza, który jest większy niż określony klucz i pierwszy element w `hash_map` za pomocą klucza jest równa lub większa niż klucz.|
|[wymazywanie](#erase)|Usuwa element lub zakresu elementów `hash_map` od określonej pozycji|
|[Znajdź](#find)|Zwraca iteratora adresowania położenie elementu w `hash_map` mający klucz równoważne z określonym kluczem.|
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` użyty do utworzenia obiektu `hash_map`.|
|[Wstaw](#insert)|Wstawia element lub zakres elementów do `hash_map`.|
|[key_comp](#key_comp)|Zwraca pierwszy element w iteratora `hash_map` o wartości klucza, który jest równy lub większy niż określony klucz.|
|[lower_bound](#lower_bound)|Zwraca pierwszy element w iteratora `hash_map` o wartości klucza, który jest równy lub większy niż określony klucz.|
|[max_size](#max_size)|Zwraca maksymalną długość `hash_map`.|
|[rbegin](#rbegin)|Zwraca iteratora adresowania pierwszym elementem w odwróconej `hash_map`.|
|[rend](#rend)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej `hash_map`.|
|[Rozmiar](#size)|Zwraca liczbę elementów w `hash_map`.|
|[swap](#swap)|Zamienia elementy dwóch `hash_map`s.|
|[upper_bound](#upper_bound)|Zwraca pierwszy element w iteratora `hash_map` czy za pomocą klucza wartość jest większa niż określony klucz.|
|[value_comp](#value_comp)|Pobiera kopię porównania obiekt używany do wartości elementu kolejności w `hash_map`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator&#91;&#93;](#op_at)|Wstawia element do `hash_map` o określonej wartości klucza.|
|[hash_map::operator=](#op_eq)|Zastępuje elementy `hash_map` z kopią innego `hash_map`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_map >

**Namespace:** stdext —

## <a name="allocator_type"></a>  hash_map::allocator_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ, który reprezentuje klasę alokatora dla obiekt hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [get_allocator](#get_allocator) na przykład za pomocą `allocator_type`.

## <a name="at"></a>  hash_map::AT

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Odnajduje element w hash_map o określonej wartości klucza.

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|`key`|Wartość klucza elementu, który ma zostać znaleziona.|

### <a name="return-value"></a>Wartość zwracana

Odwołanie do wartości danych znaleziono elementu.

### <a name="remarks"></a>Uwagi

Jeśli wartość klucza argument nie zostanie znaleziona, funkcja zwraca obiekt klasy [out_of_range — klasa](../standard-library/out-of-range-class.md).


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

## <a name="begin"></a>  hash_map::BEGIN

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca adresowania pierwszym elementem w hash_map iteratora.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Adresowanie pierwszym elementem w hash_map lub lokalizacji pomyślne pusty hash_map iteratora dwukierunkowego.

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

## <a name="cbegin"></a>  hash_map::cbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca const iteratora adresowania pierwszym elementem w hash_map.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Const iteratora dwukierunkowego adresowania pierwszym elementem w [hash_map](../standard-library/hash-map-class.md) lub lokalizacji pomyślne pustą `hash_map`.

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

## <a name="cend"></a>  hash_map::cend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w hash_map —.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Const iteratora dwukierunkowego, który dotyczy lokalizacji pomyślne ostatnim elementem w [hash_map](../standard-library/hash-map-class.md). Jeśli `hash_map` jest pusta, następnie `hash_map::cend == hash_map::begin`.

### <a name="remarks"></a>Uwagi

`cend` Służy do sprawdzenia, czy iteratora osiągnął koniec jego `hash_map`.

Wartość zwrócona przez `cend` nie powinny być wyłuskiwany.

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

## <a name="clear"></a>  hash_map::Clear

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Usuwa wszystkie elementy hash_map.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie funkcji członkowskiej hash_map::clear.

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

## <a name="const_iterator"></a>  hash_map::const_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

`const_iterator` Zdefiniowany przez punkty hash_map dla elementów, które są obiektami [value_type](#value_type), która jest typu `pair` *\< ***const klucza, typ*** >*, którego pierwszego elementu członkowskiego ma kluczowe znaczenie dla elementu i sekundę, których element członkowski jest mapowanych elementu danych przez element.

Aby usunąć odwołania do `const_iterator` `cIter` wskazuje element hash_map, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `cIter` **-> najpierw**, który jest odpowiednikiem (\* `cIter`) **.first**. Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `cIter` **-> sekundę**, który jest odpowiednikiem (\* `cIter`) **.second**.

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin) na przykład za pomocą `const_iterator`.

## <a name="const_pointer"></a>  hash_map::const_pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ, który dostarcza wskaźnik do **const** element hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów w obiekcie hash_map.

## <a name="const_reference"></a>  hash_map::const_reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ, który zawiera odwołanie do **const** element przechowywane w hash_map do odczytu i wykonywania **const** operacji.

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

## <a name="const_reverse_iterator"></a>  hash_map::const_reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse)iterator const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i umożliwia iterację hash_map — odwrotnie.

`const_reverse_iterator` Zdefiniowany przez punkty hash_map dla elementów, które są obiektami [value_type](#value_type), która jest typu `pair` \< **const klucza, typ**>, którego pierwszego elementu członkowskiego ma kluczowe znaczenie dla Ten element i którego drugi element członkowski jest mapowanych datum posiadanych przez element.

Aby usunąć odwołania do `const_reverse_iterator` `crIter` wskazuje element hash_map, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `crIter`  ->  **pierwszy**, który jest odpowiednikiem (\* `crIter`) **.first**. Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `crIter`  ->  **drugi**, który jest odpowiednikiem (\* `crIter`). **pierwszy**.

### <a name="example"></a>Przykład

Zobacz przykład [rend](#rend) przykład sposobu deklarowanie i użycie `const_reverse_iterator`.

## <a name="count"></a>  hash_map::Count

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca liczbę elementów w hash_map, którego klucz odpowiada parametr określony klucz.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Wartość klucza elementu do dopasowania z hash_map.

### <a name="return-value"></a>Wartość zwracana

1, jeśli hash_map zawiera element, którego klucz sortowania pasuje do klucza parametr; 0, jeśli hash_map nie zawiera element z kluczem dopasowania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę elementów *x* w zakresie

[ `lower_bound` (_ *Klucza* ), `upper_bound` (\_ *klucza* ))

która jest równa 0 lub 1 w przypadku hash_map, która jest kontenerem asocjacyjnej unikatowy.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie funkcji członkowskiej hash_map::count.

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

## <a name="crbegin"></a>  hash_map::crbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca const iteratora adresowania pierwszym elementem w odwróconej hash_map.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała wstecznego iteratora dwukierunkowego adresowania pierwszym elementem w odwróconej [hash_map](../standard-library/hash-map-class.md) lub adresowania co była ostatnim elementem w stałe `hash_map`.

### <a name="remarks"></a>Uwagi

`crbegin` jest używany z odwróconej hash_map — podobnie jak [rozpocząć](#begin) jest używany z `hash_map`.

Z wartością zwracaną z `crbegin`, `hash_map` obiektu nie może być modyfikowany.

`crbegin` może służyć do iterowania po `hash_map` Wstecz.

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

## <a name="crend"></a>  hash_map::crend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej hash_map —.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała wstecznego iteratora dwukierunkowego, który dotyczy lokalizacji pomyślne ostatnim elementem w odwrotnej [hash_map](../standard-library/hash-map-class.md) (lokalizacji, która ma przed pierwszym elementem w stałe `hash_map`).

### <a name="remarks"></a>Uwagi

`crend` jest używany z odwróconej `hash_map` podobnie jak [hash_map::end](#end) jest używany z `hash_map`.

Z wartością zwracaną z `crend`, `hash_map` obiektu nie może być modyfikowany.

`crend` można sprawdzać, czy odwrotnej iteratora osiągnął koniec jego `hash_map`.

Wartość zwrócona przez `crend` nie powinny być wyłuskiwany.

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

## <a name="difference_type"></a>  hash_map::difference_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ liczbę całkowitą ze znakiem, który może służyć do reprezentowania liczba elementów hash_map w zakresie między elementami wskazywana przez Iteratory.

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

## <a name="emplace"></a>  hash_map::emplace

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Wstawia element zbudowane w miejscu do hash_map.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|`val`|Element ma zostać wstawiony do skonstruowania wartości używane do przenoszenia [hash_map](../standard-library/hash-map-class.md) chyba że `hash_map` już zawiera tego elementu (lub, ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie porządkowania).|

### <a name="return-value"></a>Wartość zwracana

`emplace` Funkcji członkowskiej zwraca parę, którego składnik bool zwraca wartość true, jeśli dokonano wstawiania i wartość false, gdy `hash_map` już zawiera element, którego klucz ma wartość równoważną w kolejności, którego składnik iteratora zwraca adresów, których dodano nowego elementu lub którym element został już znajduje się.

Aby dostęp do składnika iterator pary `pr` zwracane przez tę funkcję elementu członkowskiego, użyj `pr.first`i aby odwołania do niego, należy użyć `*(pr.first)`. Aby uzyskać dostęp do `bool` składnika pary `pr` zwracane przez tę funkcję elementu członkowskiego, użyj `pr.second`i aby odwołania do niego, należy użyć `*(pr.second)`.

### <a name="remarks"></a>Uwagi

[Hash_map::value_type](#value_type) elementu jest parę, tak, aby wartość elementu uporządkowanej pary z pierwszym składnikiem równa wartości klucza i drugi składnik wartość danych elementu.

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

## <a name="emplace_hint"></a>  hash_map::emplace_hint

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Wstawia element zbudowane w miejscu do hash_map, ze wskazówką umieszczania.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|`val`|Element ma zostać wstawiony do skonstruowania wartości używane do przenoszenia [hash_map](../standard-library/hash-map-class.md) chyba że `hash_map` już zawiera tego elementu (lub, ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie porządkowania).|
|`_Where`|Wskazówki dotyczące miejsca, aby rozpocząć wyszukiwanie poprawny punkt wstawiania.|

### <a name="return-value"></a>Wartość zwracana

[Hash_multimap::emplace](../standard-library/hash-multimap-class.md#emplace) funkcją członkowską zwracającą iterator wskazującą położenie, w którym wstawiono nowy element do `hash_map`, gdzie znajduje się istniejącego elementu z równoważne porządkowanie lub.

### <a name="remarks"></a>Uwagi

[Hash_map::value_type](#value_type) elementu jest parę, tak, aby wartość elementu uporządkowanej pary z pierwszym składnikiem równa wartości klucza i drugi składnik wartość danych elementu.

Wstawiania może wystąpić podczas amortyzowanego stałej, zamiast logarytmicznej czasu, jeśli punkt wstawiania poniższą `_Where`.

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

## <a name="empty"></a>  hash_map::Empty

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Testy, jeśli hash_map jest pusta.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli hash_map jest pusta. **false** Jeśli hash_map nie jest pusty.

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

## <a name="end"></a>  hash_map::end

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca, którego dotyczy lokalizacji pomyślne ostatnim elementem w hash_map iteratora.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowego, którego dotyczy lokalizacji pomyślne ostatnim elementem w hash_map. Jeśli hash_map jest pusty, a następnie hash_map::end == hash_map::begin.

### <a name="remarks"></a>Uwagi

**końcowy** używany do sprawdzania, czy iteratora osiągnął koniec jego hash_map.

Wartość zwrócona przez **zakończenia** nie powinny być wyłuskiwany.

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

## <a name="equal_range"></a>  hash_map::equal_range

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca parę Iteratory odpowiednio do pierwszego elementu w hash_map za pomocą klucza, który jest większy niż określony klucz i pierwszy element w hash_map za pomocą klucza jest równa lub większa niż klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

`key` Argument wartość klucza ma zostać porównane z klucza sortowania z elementem z hash_map przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

Para Iteratory tak, aby był pierwszy [lower_bound](#lower_bound) klucz, a drugi jest [upper_bound](#upper_bound) klucza.

Pierwszy iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **pierwszy** i aby usunąć odwołania do iteratora dolnej granicy, należy użyć \*( `pr`. **najpierw**). Drugi iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **drugi** i aby usunąć odwołania do iteratora górnej granicy, należy użyć \*( `pr`. **drugi**).

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
        << " matching the 2nd element of the pair"
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

## <a name="erase"></a>  hash_map::ERASE

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Usuwa element lub zakres elementów w hash_map z określonych pozycji lub usuwa elementy zgodne z określonym kluczem.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

`_Where` Położenie elementu do usunięcia z hash_map.

`first` Pozycja pierwszego elementu usunięte z hash_map.

`last` Pozycja poza ostatni element usunięty z hash_map.

`key` Wartość klucza elementu do usunięcia z hash_map.

### <a name="return-value"></a>Wartość zwracana

Dla pierwszego funkcji dwóch elementów członkowskich iteratora dwukierunkowego który wyznacza pierwszy element pozostała poza wszelkie elementy usunięte lub wskaźnika do końca hash_map nie zawiera żadnego takiego elementu.

Dla innych funkcji członkowskiej zwraca liczbę elementów, które zostały usunięte z hash_map.

### <a name="remarks"></a>Uwagi

Funkcje Członkowskie nigdy nie zgłaszają wyjątków.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie funkcji członkowskiej hash_map::erase.

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

## <a name="find"></a>  hash_map::Find

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca iteratora adresowania położenie elementu w hash_map, który ma klucz równoważne z określonym kluczem.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Wartość klucza do dopasowania za pomocą klucza sortowania z elementem z hash_map przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

Iterator, którego dotyczy lokalizacji elementu z określonym kluczem lub lokalizacji pomyślne ostatnim elementem w hash_map, jeśli nie znaleziono klucza.

### <a name="remarks"></a>Uwagi

**Znajdź** zwraca iteratora, którego dotyczy element hash_map, którego klucz sortowania jest odpowiednikiem klucza argument w predykat binarne wywołujące kolejność oparte na mniej niż porównywalności relacji.

Jeśli wartość zwracana **znaleźć** jest przypisany do [const_iterator](#const_iterator), nie można zmodyfikować obiektu hash_map. Jeśli wartość zwracana **znaleźć** jest przypisany do [iterator](#iterator), można zmodyfikować obiektu hash_map

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

## <a name="get_allocator"></a>  hash_map::get_allocator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca kopię obiektu alokatora użyta do skonstruowania hash_map.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Allocator — używane przez hash_map.

### <a name="remarks"></a>Uwagi

Allocators — dla klasy hash_map — Określ zarządzaniu klasę magazynu. Allocators — domyślna dostarczony wraz z klasy kontenerów standardowa biblioteka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.

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

## <a name="hash_map"></a>  hash_map::hash_map

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Tworzy hash_map, który jest pusta lub kopii całości lub części innych hash_map —.

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
|`Al`|Klasa przydzielania magazynu do użycia dla tego obiektu hash_map, która domyślnie określa **alokatora**.|
|`Comp`|Funkcja porównywania typu const `Traits` porządkowania elementów w hash_map, która domyślnie określa `hash_compare`.|
|`Right`|Hash_map — skonstruowane mapa ma być kopii.|
|`First`|Pozycja pierwszego elementu w zakresie elementów do skopiowania.|
|`Last`|Pozycja pierwszego elementu poza zakres elementów do skopiowania.|
|`IList`|Initializer_list|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory typu obiektu przydzielania, który zarządza przechowywania w pamięci dla hash_map magazynu i później może być zwracany przez wywołanie metody [get_allocator](#get_allocator). Parametr przydzielania jest często pomijany w deklaracjach klas i przetwarzania wstępnego makra używany do zastąpienia alternatywnych allocators —.

Wszystkie konstruktory zainicjować ich hash_map.

Wszystkie konstruktory przechowywania obiektem funkcji typu `Traits` który jest używany do ustanawiania zamówienia wśród kluczy hash_map i który później może być zwracany przez wywołanie metody [key_comp](#key_comp).

Pierwsze trzy konstruktorów Określ pusty hash_map początkowej, ponadto drugi określa typ porównania funkcji ( `Comp`) do użycia w ustalaniu kolejności elementów i trzeci jawnie określa typ alokatora ( `Al`) do użytku. Słowo kluczowe `explicit` pomija określonych rodzajów typu automatycznej konwersji.

Konstruktor czwarty Określa kopię hash_map `Right`.

Konstruktory trzech kolejnych skopiuj zakres `[First, Last)` z hash_map rosnącymi explicitness określania typu porównanie funkcji klasy `Traits` i przydzielania.

Konstruktor ostatniego przenosi hash_map `Right`.

## <a name="insert"></a>  hash_map::INSERT

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

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
|`val`|Wartość elementu ma zostać wstawiony do hash_map, chyba że hash_map już zawiera tego elementu (lub, ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie porządkowania).|
|`_Where`|Wskazówki dotyczące miejsca, aby rozpocząć wyszukiwanie poprawny punkt wstawiania.|
|`first`|Pozycja pierwszego elementu skopiowane z hash_map.|
|`last`|Pozycja poza ostatni element do skopiowania z hash_map.|

### <a name="return-value"></a>Wartość zwracana

Pierwszy **Wstaw** funkcji członkowskiej zwraca parę, którego składnik bool zwraca wartość true, jeśli wstawiania zostało wykonane i wartość false, jeśli hash_map już zawiera element, którego klucz ma wartość równoważną w kolejności i którego iteratora składnik zwraca adres, gdzie dodano nowego elementu lub którym element został już znajduje się.

Aby dostęp do składnika iterator pary `pr` zwracane przez tę funkcję elementu członkowskiego, użyj `pr`. **pierwszy**i aby odwołania do niego, należy użyć \*( `pr`. **najpierw**). Aby uzyskać dostęp do `bool` składnika pary `pr` zwracane przez tę funkcję elementu członkowskiego, użyj `pr`. **drugi**i aby odwołania do niego, należy użyć \*( `pr`. **drugi**).

Drugi **Wstaw** funkcji członkowskiej, wersja wskazówka zwracającą iterator wskazujące pozycji, których wstawiono nowy element do hash_map.

Ostatnie dwa **Wstaw** funkcje Członkowskie zachowują się taka sama jak dwa pierwsze z tą różnicą, że przechodzą skonstruować wstawiona wartość.

### <a name="remarks"></a>Uwagi

[Value_type](../standard-library/map-class.md#value_type) elementu jest parę, tak, aby wartość elementu uporządkowanej pary z pierwszym składnikiem równa wartości klucza i drugi składnik wartość danych elementu.

Wstawiania może wystąpić w amortyzowanego stałej czasu dla wersji wskazówka insert, zamiast logarytmicznej czasu, jeśli punkt wstawiania poniższą `_Where`.

Trzeci funkcji członkowskiej wstawia sekwencji wartości elementów do hash_map odpowiadający każdemu elementowi adresowane przez iterator w zakresie *[First, Last)* w określonym zestawie.

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

    cout<< "The original elements (Key => Value) of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << " " << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    pair< hash_map<int,int>::iterator, bool > pr;
    pr = hm1.insert(Int_Pair(1, 10));

    if (pr.second == true)
    {
        cout<< "The element 10 was inserted in hm1 successfully."
            << endl;
    }
    else
    {
        cout<< "The element 10 already exists in hm1\n with a key value of"
            << "((pr.first) -> first)= "<<(pr.first)-> first
            << "."<< endl;
    }

    // The hint version of insert
    hm1.insert(--hm1.end(), Int_Pair(5, 50));

    cout<< "After the insertions, the elements of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << " " << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    hm2.insert(Int_Pair(10, 100));

    // The templatized version inserting a range
    hm2.insert( ++hm1.begin(), --hm1.end() );

    cout<< "After the insertions, the elements of hm2 are:";
    for (hm2_pIter = hm2.begin(); hm2_pIter != hm2.end(); hm2_pIter++)
        cout << endl << " " << hm2_pIter -> first << " => "
             << hm2_pIter->second;
    cout << endl;

    // The templatized versions move constructing elements
    hash_map<int, string> hm3, hm4;
    pair<int, string> is1(1, "a"), is2(2, "b");

    hm3.insert(move(is1));
    cout << "After the move insertion, hm3 contains:" << endl
      << " " << hm3.begin()->first
      << " => " << hm3.begin()->second
      << endl;

    hm4.insert(hm4.begin(), move(is2));
    cout << "After the move insertion, hm4 contains:" << endl
      << " " << hm4.begin()->first
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
 with a key value of((pr.first) -> first)= 1.
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

## <a name="iterator"></a>  hash_map::iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować dowolny element w hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Uwagi

**Iterator** zdefiniowany przez punkty hash_map dla elementów, które są obiektami [value_type](#value_type), która jest typu **pary\<const klucza, wpisz >,** których pierwszego elementu członkowskiego klucz do elementu i którego drugi element członkowski jest mapowanych datum jest przechowywany przez element.

Aby usunąć odwołania do **iterator** `Iter` wskazuje element w multimap, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `Iter`  ->  **pierwszy**, który jest odpowiednikiem (\* `Iter`). **pierwszy**. Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `Iter`  ->  **drugi**, który jest odpowiednikiem (\* `Iter`). **drugi**.

Typ **iterator** może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin) przykład sposobu deklarowanie i użycie **iterator**.

## <a name="key_comp"></a>  hash_map::key_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Pobiera kopię porównania obiekt używany do kolejność kluczy w hash_map.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcja hash_map używa do porządkowania jej elementów.

### <a name="remarks"></a>Uwagi

Obiekt przechowywanych definiuje funkcję elementu członkowskiego

**bool operator**( **const klucza &** `left` **, klucz const &** `right`);

zwracającą **true** Jeśli `left` poprzedza i nie jest równa `right` w kolejności sortowania.

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

## <a name="key_compare"></a>  hash_map::key_compare

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ, który udostępnia obiekt funkcji, które można porównać dwa klucze sortowania, aby określić względną kolejność dwa elementy na mapie.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare` synonim parametru szablonu jest `Traits`.

Aby uzyskać więcej informacji na temat `Traits` zobacz [hash_map — klasa](../standard-library/hash-map-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [key_comp](#key_comp) przykład sposobu deklarowanie i użycie `key_compare`.

## <a name="key_type"></a>  hash_map::key_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ zawiera opis obiektu klucza sortowania stanowi każdy element hash_map.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type` synonim parametru szablonu jest `Key`.

Aby uzyskać więcej informacji na temat `Key`, zobacz sekcję uwag [hash_map — klasa](../standard-library/hash-map-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) przykład sposobu deklarowanie i użycie `key_type`.

## <a name="lower_bound"></a>  hash_map::lower_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca pierwszy element w hash_map o wartości klucza, który jest równy lub większy niż określony klucz iteratora.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Argument wartość klucza ma zostać porównane z klucza sortowania z elementem z hash_map przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

[Iterator](#iterator) lub [const_iterator](#const_iterator) który adresy lokalizacji elementu w hash_map, za pomocą klucza jest równa lub większa niż argument klucza, lub że adresów lokalizacji pomyślne przez ostatnie Element hash_map, jeśli nie znaleziono klucza.

Jeśli wartość zwracana `lower_bound` jest przypisany do `const_iterator`, nie można zmodyfikować obiektu hash_map. Jeśli wartość zwracana `lower_bound` jest przypisany do **iterator**, można zmodyfikować obiektu hash_map.

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

## <a name="mapped_type"></a>  hash_map::mapped_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ, który reprezentuje typ danych przechowywanych w hash_map.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Uwagi

Typ `mapped_type` jest synonimem parametru szablonu `Type`.

Aby uzyskać więcej informacji na temat `Type` zobacz [hash_map — klasa](../standard-library/hash-map-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) przykład sposobu deklarowanie i użycie `key_type`.

## <a name="max_size"></a>  hash_map::max_size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca maksymalną długość hash_map.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna długość możliwe hash_map.

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

## <a name="op_at"></a>  hash_map::operator]

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Wstawia element do `hash_map` o określonej wartości klucza.

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|`key`|Wartość klucza elementu, który ma zostać wstawiony.|

### <a name="return-value"></a>Wartość zwracana

Odwołanie do wartości danych wstawionego elementu.

### <a name="remarks"></a>Uwagi

Jeśli wartość klucza argumentu nie zostanie znaleziona, zostanie ona wstawiona wraz z wartością domyślną typu danych.

`operator[]` może być używany do wstawiania elementów do `hash_map m` przy użyciu

`m[ key] = DataValue`;

wartości danych w przypadku wartości `mapped_type` elementu o wartości klucza `key`.

Korzystając z `operator[]` wstawianie elementów, zwracane odwołanie nie wskazuje, czy wstawiania jest zmiana istniejących elementów lub tworzenia nowej. Funkcje Członkowskie [znaleźć](../standard-library/map-class.md#find) i [Wstaw](../standard-library/map-class.md#insert) może służyć do określenia, czy element z określonym kluczem jest już obecny przed wstawieniem.

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

   // opperator[] will also insert by moving a key
   hash_map <string, int> hm2;
   string str("a");
   hm2[move(str)] = 1;
   cout << "The moved key is " << hm2.begin()->first
      << ", with value " << hm2.begin()->second << endl;
}
```

## <a name="op_eq"></a>  hash_map::operator =

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zamienia elementy hash_map kopię hash_map innego.

```cpp
hash_map& operator=(const hash_map& right);

hash_map& operator=(hash_map&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|`right`|[Hash_map — klasa](../standard-library/hash-map-class.md) kopiowane do `hash_map`.|

### <a name="remarks"></a>Uwagi

Po wykonaniu elementy w `hash_map`, `operator=` albo kopiuje lub przenosi zawartość `right` do `hash_map`.

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

## <a name="pointer"></a>  hash_map::Pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ, który dostarcza wskaźnik do elementu hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ **wskaźnika** może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów w obiekcie hash_map.

## <a name="rbegin"></a>  hash_map::rbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca iteratora adresowania pierwszym elementem w hash_map odwróconej.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator odwrotnej dwukierunkowego adresowania pierwszym elementem w odwróconej hash_map lub adresowania co była ostatnim elementem w hash_map stałe.

### <a name="remarks"></a>Uwagi

`rbegin` jest używany z odwróconej hash_map — podobnie jak [rozpocząć](#begin) jest używany z hash_map.

Jeśli wartość zwracana `rbegin` jest przypisany do [const_reverse_iterator](#const_reverse_iterator), wówczas nie można zmodyfikować obiektu hash_map. Jeśli wartość zwracana `rbegin` jest przypisany do [reverse_iterator](#reverse_iterator), a następnie można zmodyfikować obiektu hash_map.

`rbegin` może służyć do iterowania po hash_map Wstecz.

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

## <a name="reference"></a>  hash_map::Reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ, który zawiera odwołanie do elementu przechowywane w hash_map.

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

## <a name="rend"></a>  hash_map::rend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej hash_map iteratora.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Iterator odwrotnej dwukierunkowego, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej hash_map (lokalizacja miał przed pierwszym elementem w stałe hash_map).

### <a name="remarks"></a>Uwagi

`rend` jest używany z odwróconej hash_map — podobnie jak [zakończenia](#end) jest używany z hash_map.

Jeśli wartość zwracana `rend` jest przypisany do [const_reverse_iterator](#const_reverse_iterator), wówczas nie można zmodyfikować obiektu hash_map. Jeśli wartość zwracana `rend` jest przypisany do [reverse_iterator](#reverse_iterator), a następnie można zmodyfikować obiektu hash_map.

`rend` można sprawdzać, czy osiągnął koniec jego hash_map odwrotnej iteratora.

Wartość zwrócona przez `rend` nie powinny być wyłuskiwany.

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

## <a name="reverse_iterator"></a>  hash_map::reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować elementu w odwróconej hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` nie można zmodyfikować wartości elementu i umożliwia iterację hash_map — odwrotnie.

`reverse_iterator` Zdefiniowany przez punkty hash_map dla elementów, które są obiektami [value_type](#value_type), która jest typu **pary\<const klucza, wpisz >**, których pierwszego elementu członkowskiego ma kluczowe znaczenie dla elementu i drugie, którego element członkowski jest mapowanych elementu danych przez element.

Aby usunąć odwołania do `reverse_iterator` `rIter` wskazuje element hash_map, użyj -> — operator.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `rIter`  ->  **pierwszy**, który jest odpowiednikiem (\* `rIter`). **pierwszy**. Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `rIter`  ->  **drugi**, który jest odpowiednikiem (\* `rIter`). **pierwszy**.

### <a name="example"></a>Przykład

Zobacz przykład [rbegin](#rbegin) przykład sposobu deklarowanie i użycie `reverse_iterator`.

## <a name="size"></a>  hash_map::size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca liczbę elementów w hash_map.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość hash_map.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie funkcji członkowskiej hash_map::size.

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

## <a name="size_type"></a>  hash_map::size_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Zobacz przykład [rozmiar](#size) przykład sposobu deklarowanie i użycie `size_type`

## <a name="swap"></a>  hash_map::swap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zamienia hash_maps dwa elementy.

```cpp
void swap(hash_map& right);
```

### <a name="parameters"></a>Parametry

`right` Hash_map — argument, zapewniając elementy, aby być zamieniona na hash_map docelowej.

### <a name="remarks"></a>Uwagi

Funkcja członkowska unieważnia nie odwołań, wskaźniki lub Iteratory, które określają elementów w dwóch hash_maps, której elementy są wymieniane.

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

## <a name="upper_bound"></a>  hash_map::upper_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Pierwszy element w hash_map zwracającą iterator za pomocą klucza o wartości, który jest większy niż określony klucz.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Wartość klucza argument ma być porównywana z wartością klucza sortowania z elementem z hash_map przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

[Iterator](#iterator) lub [const_iterator](#const_iterator) który adresy lokalizacji elementu w hash_map, który za pomocą klucza jest większa niż klucz argumentu, który dotyczy pomyślne ostatnim elementem w lokalizacji hash_map — Jeśli nie znaleziono klucza.

Jeśli wartość zwracana jest przypisany do `const_iterator`, nie można zmodyfikować obiektu hash_map. Jeśli wartość zwracana jest przypisany do **iterator**, można zmodyfikować obiektu hash_map.

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
   cout << "The 1st element of hm1 with a key greater than "
        << "that\n of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The first element of hash_map hm1 with a key greater than 2 is: 30.
The hash_map hm1 doesn't have an element with a key greater than 4.
The 1st element of hm1 with a key greater than that
 of the initial element of hm1 is: 20.
```

## <a name="value_comp"></a>  hash_map::value_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Zwraca obiekt funkcji, który określa kolejność elementów hash_map porównując wartości klucza.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcja porównania hash_map używa do porządkowania jej elementów.

### <a name="remarks"></a>Uwagi

Dla hash_map *m*, jeśli dwa elementy *e*1 *(k*1 *, d*1 *)* i *e*2 *(k*2 *, d*2 *)* obiektów typu [value_type](#value_type), gdzie *k*1 i *k*2 są ich kluczy typu [key_type](#key_type) i `d`1 i `d`2 są dane typu [mapped_type](#mapped_type), następnie *m.*  `value_comp` *() (e*1 *, e*2 *)* jest odpowiednikiem *m.* `key_comp` *() (KB*1 *, k*2 *)*. Obiekt przechowywanych definiuje funkcję elementu członkowskiego

**bool operator**( **value_type &** `left`, **value_type &** `right`) **;**

która zwraca **true** Jeśli wartość klucza `left` poprzedza i nie jest równa wartości klucza `right` w kolejności sortowania.

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

## <a name="value_type"></a>  hash_map::value_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).

Typ, który reprezentuje typ obiektu przechowywanego w hash_map.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Uwagi

`value_type` został zadeklarowany jako `pair`  *\< * **const**[key_type](#key_type), [mapped_type](#mapped_type)*> * i nie `pair`  **\<key_type, mapped_type >** , ponieważ nie można zmienić klucze asocjacyjnej kontenera za pomocą nieunikatowego iteratora lub odwołanie.

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
   // explicitely to avoid implicit type conversion
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

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
