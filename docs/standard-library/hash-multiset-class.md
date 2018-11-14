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
ms.openlocfilehash: b12c782ff7071987214acfe1ef8c52ca391b25ad
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51333566"
---
# <a name="hashmultiset-class"></a>hash_multiset — Klasa

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Hash_multiset — klasa kontenera jest rozszerzeniem standardowej biblioteki języka C++ i jest używany do przechowywania i szybkie pobieranie danych z kolekcji, w której wartości zawartych elementów służą jako wartości klucza i nie muszą być unikatowe.

## <a name="syntax"></a>Składnia

```cpp
template <class Key, class Traits =hash_compare<Key, less <Key>>, class Allocator =allocator <Key>>
class hash_multiset
```

### <a name="parameters"></a>Parametry

*Key*<br/>
Typ danych elementu, który ma być przechowywany w hash_multiset.

*Cechy*<br/>
Typu, który obejmuje dwa obiekty funkcji, jednej klasy porównania oznacza to predykat binarny, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność i funkcję mieszania, która jest jednoargumentowy predykatu mapowania klucza wartości elementów na typy bez znaku liczby całkowite typu `size_t`. Ten argument jest opcjonalny, a `hash_compare<Key, less<Key> >` jest wartością domyślną.

*Allocator*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i dezalokacji pamięci hash_multiset. Ten argument jest opcjonalny, a wartość domyślna to `allocator<Key>`.

## <a name="remarks"></a>Uwagi

Hash_multiset — jest:

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza. Ponadto, jest prostym kontenerem asocjacyjnym, ponieważ jego wartości elementu są jego wartościami klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.

- Mieszany, ponieważ jego elementy są pogrupowane w przedziały, na podstawie wartości funkcji skrótu dotyczą kluczowych wartości elementów.

- Unikatowy w tym sensie, że każdy z jego elementów musi mieć unikatowy klucz. Ponieważ hash_multiset jest również prostym kontenerem asocjacyjnym, jego elementy są również unikatowe.

- Klasą szablonu, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Główną zaletą wyznaczania wartości skrótu, za pośrednictwem sortowania jest większą wydajność: wykonuje wstawień, usuwanie i znajduje w stałej Średni czas w porównaniu z danym proporcjonalny do logarytmu liczby elementów w kontenerze sortowania pomyślnego tworzenia skrótów techniki. Nie można bezpośrednio zmienić wartości elementu w zestawie. Zamiast tego musisz usunąć stare wartości i wstawić elementy z nowymi wartościami.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Skrótu kontenery asocjacyjne są zoptymalizowane dla operacji wyszukiwania, wstawiania i usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje są wydajne, gdy jest używana z funkcją dobrze zaprojektowanego wyznaczania wartości skrótu, wykonując je w czasie, który jest średnio stała i nie jest zależna od liczby elementów w kontenerze. Funkcja skrótu dobrze zaprojektowanego generuje jednolity rozkład wartości skrótu i minimalizuje liczbę konfliktów, w którym kolizji jest wyświetlany po odrębnych wartości klucza są mapowane na taką samą wartość skrótu. W najgorszym przypadku za pomocą funkcji skrótu możliwe najgorszy liczby operacji jest proporcjonalna do liczby elementów w sekwencji (liniowy czas).

Hash_multiset — powinien być kontenerem asocjacyjnym z wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Elementy hash_multiset może być wiele i służyć jako własne klucze sortowania, więc klucze nie są unikatowe. Model dla tego typu konstrukcji jest uporządkowaną listą, np. wyrazów, w których wyrazy mogą występować więcej niż jeden raz. Ma wiele wystąpień wyrazów została niedozwolona, a następnie hash_set byłaby odpowiednią strukturą kontenera. Gdyby unikatowe definicje zostały dołączone jako wartości do listy unikatowych słów kluczowych, hash_map byłaby odpowiednią strukturą zawierającą te dane. Gdyby natomiast definicje nie były unikatowe, hash_multimap byłaby kontenerem z wyboru.

Hash_multiset — porządkuje sekwencję którą kontroluje, przez wywołanie obiektu przechowywanej wyznaczania wartości skrótu cech typu [value_compare](#value_compare). Ten przechowywany obiekt może być dostępna poprzez wywołanie funkcji elementu członkowskiego [key_comp](#key_comp). Obiekt funkcyjny musi zachowywać się taka sama jak obiekt klasy `hash_compare<Key, less<Key> >`. W szczególności dla wszystkich wartości *klucz* typu `Key`, wywołanie `Trait(Key)` daje w wyniku rozkład wartości typu `size_t`.

Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Binarny predykat *f*( *x*, *y*) jest obiektem funkcji, która ma dwa obiekty argumentu x i y oraz wartość zwracaną true lub false. Kolejność nałożona na hash_multiset jest ścisłym słabym porządkowaniem, jeśli predykat binarny jest niezwrotny, przeciwsymetryczny i przechodni oraz jeśli równoważność jest przechodnia, gdzie dwa obiekty x i y są zdefiniowane jako równoważne, gdy oba *f* ( *x*, *y*) i *f*( *y*, *x*) mają wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

Rzeczywista kolejność elementów w kontrolowanej sekwencji zależy od funkcji mieszania, funkcja szeregowania i bieżący rozmiar tabeli mieszania przechowywanych w obiekcie kontenera. Nie można określić bieżący rozmiar tabeli wyznaczania wartości skrótu, dlatego ogólnie rzecz biorąc nie można przewidzieć kolejności elementów w kontrolowanej sekwencji. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Iterator dostarczony przez klasę hash_multiset jest iteratorem dwukierunkowym, ale funkcje składowych klasy wstawiania i hash_multiset mają wersje przyjmujące jako parametry szablonu słabszy iterator danych wejściowych, którego wymagania funkcjonalności są mniejsze niż te gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny hash_multiset wymagania, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny hash_multiset funkcji, ale jest wystarczający, aby można było mówić znacząco o zakresie iteratorów [ `first`, `last`) w kontekście funkcji składowych klasy.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[hash_multiset —](#hash_multiset)|Konstruuje `hash_multiset` oznacza to pusta lub czyli kopią całości lub części innej `hash_multiset`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje `allocator` klasy dla `hash_multiset` obiektu.|
|[const_iterator](#const_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać **const** element `hash_multiset`.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do **const** element `hash_multiset`.|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do **const** przechowywanego w `hash_multiset` do odczytu i wykonywania **const** operacji.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **const** element `hash_multiset`.|
|[difference_type](#difference_type)|Typ liczby całkowitej ze znakiem, który zawiera różnicę między dwoma iteratorami odwołującymi adresów elementów w tej samej `hash_multiset`.|
|[iterator](#iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w `hash_multiset`.|
|[key_compare —](#key_compare)|Typ, który dostarcza obiekt funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `hash_multiset`.|
|[key_type](#key_type)|Typ, który opisuje obiekt zapisany jako element `hash_set` w charakterze klucza sortowania.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu w `hash_multiset`.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w `hash_multiset`.|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej `hash_multiset`.|
|[size_type](#size_type)|Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w `hash_multiset`.|
|[value_compare —](#value_compare)|Typ, który zawiera dwa obiekty funkcyjne, predykat binarny porównania klasy, która może porównać dwie wartości elementów z `hash_multiset` ustalenie ich względne kolejności i jednoargumentowy predykat, który wyznacza wartość skrótu elementów.|
|[value_type](#value_type)|Typ, który opisuje obiekt zapisany jako element `hash_multiset` w charakterze wartości.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[begin](#begin)|Zwraca iterator odnoszący się do pierwszego elementu w `hash_multiset`.|
|[cbegin](#cbegin)|Zwraca iterator stałych adresujący pierwszy element w `hash_multiset`.|
|[cend](#cend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w `hash_multiset`.|
|[Usuń zaznaczenie](#clear)|Usuwa wszystkie elementy `hash_multiset`.|
|[Liczba](#count)|Zwraca liczbę elementów w `hash_multiset` których klucz pasuje do klucza określonego jako parametr|
|[crbegin](#crbegin)|Zwraca iterator stałych adresujący pierwszy element w odwróconej `hash_multiset`.|
|[crend —](#crend)|Zwraca iterator stałych adresujący lokalizację następującą po ostatnim elemencie w odwróconej `hash_multiset`.|
|[emplace —](#emplace)|Wstawia element skonstruowany w miejscu do `hash_multiset`.|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do `hash_multiset`, ze wskazówką położenia.|
|[pusty](#empty)|Sprawdza, czy `hash_multiset` jest pusty.|
|[koniec](#end)|Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w `hash_multiset`.|
|[equal_range](#equal_range)|Zwraca parę iteratorów odpowiednio do pierwszego elementu w `hash_multiset` przy użyciu klucza, który jest większy niż określony klucz i do pierwszego elementu w `hash_multiset` z kluczem, który jest równy lub większy niż określony klucz.|
|[wymazywanie](#erase)|Usuwa element lub zakres elementów w `hash_multiset` z określonych pozycji lub usuwa elementy, które odpowiadają określonemu kluczowi.|
|[Znajdź](#find)|Zwraca iterator odnoszący się lokalizację elementu w `hash_multiset` który ma klucz równoważny z określonym kluczem.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu `allocator` użytego do stworzenia `hash_multiset`.|
|[Wstaw](#insert)|Wstawia element lub zakres elementów do `hash_multiset`.|
|[key_comp](#key_compare)|Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w `hash_multiset`.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu w `hash_multiset` z kluczem, który jest równy lub większy od określonego klucza.|
|[max_size](#max_size)|Zwraca maksymalną długość `hash_multiset`.|
|[rbegin](#rbegin)|Zwraca iterator odnoszący się do pierwszego elementu w odwróconej `hash_multiset`.|
|[rend —](#rend)|Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w odwróconej `hash_multiset`.|
|[Rozmiar](#size)|Zwraca liczbę elementów w `hash_multiset`.|
|[swap](#swap)|Zamienia elementy z dwóch `hash_multiset`s.|
|[upper_bound —](#upper_bound)|Zwraca iterator do pierwszego elementu w `hash_multiset` , wraz z kluczem, który jest równy lub większy od określonego klucza.|
|[value_comp](#value_comp)|Pobiera kopię obiektu cech mieszania używany do wyznaczania wartości skrótu i kolejność wartości kluczy w elemencie `hash_multiset`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[hash_multiset::operator =](#op_eq)|Zastępuje elementy hash_multiset kopią innego hash_multiset.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_set >

**Namespace:** stdext

## <a name="allocator_type"></a>  hash_multiset::allocator_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Typ, który reprezentuje klasę alokatora dla obiektu hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>Przykład

Zobacz przykład dotyczący [get_allocator —](#get_allocator) dla usługi przy użyciu przykładu `allocator_type`

## <a name="begin"></a>  hash_multiset::BEGIN

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator odnoszący się do pierwszego elementu w hash_multiset.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pierwszego elementu w hash_multiset lub lokalizacji następującej po hash_multiset puste.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `begin` jest przypisany do `const_iterator`, nie można modyfikować elementów w obiekcie hash_multiset. Jeśli wartość zwracaną przez `begin` jest przypisany do `iterator`, elementów w obiekcie hash_multiset może być modyfikowany.

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

## <a name="cbegin"></a>  hash_multiset::cbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator const, który dotyczy pierwszego elementu w hash_multiset.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stały iterator dwukierunkowy odnoszący się do pierwszego elementu w [hash_multiset](../standard-library/hash-multiset-class.md) lub lokalizacji następującej po pustą `hash_multiset`.

### <a name="remarks"></a>Uwagi

Wartością zwracaną `cbegin`, elementy w `hash_multiset` nie można zmodyfikować obiektu.

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

## <a name="cend"></a>  hash_multiset::cend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator stałych adresujący lokalizację następującą po ostatnim elemencie w hash_multiset.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Const iteratora dwukierunkowego, który dotyczy lokalizacji następującej po ostatnim elemencie w [hash_multiset](../standard-library/hash-multiset-class.md). Jeśli `hash_multiset` jest pusta, następnie `hash_multiset::cend == hash_multiset::begin`.

### <a name="remarks"></a>Uwagi

`cend` Służy do sprawdzenia, czy iterator osiągnął koniec swojej `hash_multiset`. Wartość zwrócona przez obiekt `cend` nie należy usuwać odwołania.

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

## <a name="clear"></a>  hash_multiset::Clear

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

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

## <a name="const_iterator"></a>  hash_multiset::const_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać **const** element hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład dotyczący [rozpocząć](#begin) dla przykłady dotyczące używania `const_iterator`.

## <a name="const_pointer"></a>  hash_multiset::const_pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza wskaźnik do **const** element hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

W większości przypadków [const_iterator](#const_iterator) powinien być używany do uzyskania dostępu do elementów w **const** hash_multiset obiektu.

## <a name="const_reference"></a>  hash_multiset::const_reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Typ, który zawiera odwołanie do **const** elementu przechowywanego w hash_multiset do odczytu i wykonywania **const** operacji.

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

## <a name="const_reverse_iterator"></a>  hash_multiset::const_reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **const** element hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i jest używany do iterowania po hash_multiset w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład [rend —](#rend) przykładowy sposób deklarowania i użyj `const_reverse_iterator`.

## <a name="count"></a>  hash_multiset::Count

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zwraca liczbę elementów w hash_multiset, w których klucz pasuje do klucza określonego jako parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz elementy, które mają być dopasowywane z hash_multiset.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w hash_multiset przy użyciu klucza określonego jako parametr.

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca liczbę elementów w następującym zakresie:

\[ lower_bound (*klucz*), upper_bound (*klucz*)).

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie hash_multiset::count funkcja elementu członkowskiego.

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

## <a name="crbegin"></a>  hash_multiset::crbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator stałych adresujący pierwszy element w odwróconej hash_multiset.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconej [hash_multiset](../standard-library/hash-multiset-class.md) lub adresowania, który był ostatnim elementem w nieodwróconej `hash_multiset`.

### <a name="remarks"></a>Uwagi

`crbegin` jest używana z odwróconej `hash_multiset` podobnie jak [hash_multiset::begin](#begin) jest używana z `hash_multiset`.

Wartością zwracaną `crbegin`, `hash_multiset` nie można zmodyfikować obiektu.

`crbegin` może służyć do iterowania po `hash_multiset` Wstecz.

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

## <a name="crend"></a>  hash_multiset::crend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator stałych adresujący lokalizację następującą po ostatnim elemencie w odwróconej hash_multiset.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iteratora dwukierunkowego, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconej [hash_multiset](../standard-library/hash-multiset-class.md) (miejsca przed pierwszym elementem w nieodwróconej `hash_multiset`).

### <a name="remarks"></a>Uwagi

`crend` jest używana z odwróconej `hash_multiset` podobnie jak [hash_multiset::end](#end) jest używana z `hash_multiset`.

Wartością zwracaną `crend`, `hash_multiset` nie można zmodyfikować obiektu.

`crend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej hash_multiset.

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

## <a name="difference_type"></a>  hash_multiset::difference_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Typ liczby całkowitej ze znakiem, który zawiera różnicę między dwoma iteratorami odwołującymi elementów w obrębie tego samego hash_multiset adresów.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` Jest typ zwracany, jeśli odjęcie lub inkrementacji poprzez Iteratory kontenera. `difference_type` Jest zazwyczaj używany do reprezentowania liczby elementów w zakresie [ `first`, `last`) między Iteratory `first` i `last`, zawiera element wskazywany przez `first` i zakres elementów do , ale bez element wskazane przez `last`.

Należy pamiętać, że chociaż `difference_type` jest dostępna dla wszystkich iteratorów, które spełniają wymagania iteratora danych wejściowych zawiera klasę iteratorów dwukierunkowych obsługiwane przez odwracalnego kontenerów, takiego jak zestaw. Odejmowanie między Iteratory jest obsługiwana tylko przez Iteratory dostępu swobodnego, dostarczone przez kontener dostępu swobodnego, takich jak wektor lub deque.

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

## <a name="emplace"></a>  hash_multiset::emplace

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Wstawia element skonstruowany w miejscu do hash_multiset.

```cpp
template <class ValTy>
iterator insert(ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Wartość elementu do wstawienia do [hash_multiset](../standard-library/hash-multiset-class.md) chyba że `hash_multiset` zawiera już ten element, lub bardziej ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie są porządkowane.|

### <a name="return-value"></a>Wartość zwracana

`emplace` Funkcja elementu członkowskiego zwraca iterator, który wskazuje miejsce, w którym dodano nowy element.

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

## <a name="emplace_hint"></a>  hash_multiset::emplace_hint

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Wstawia element skonstruowany w miejscu do hash_multiset, ze wskazówką położenia.

```cpp
template <class ValTy>
iterator insert(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Wartość elementu do wstawienia do [hash_multiset](../standard-library/hash-multiset-class.md) chyba że `hash_multiset` zawiera już ten element, lub bardziej ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie są porządkowane.|
|*_Where*|Miejsce, aby rozpocząć wyszukiwanie poprawne punktu wstawiania. (Wstawiania może wystąpić w amortyzowanym stałym czasie zamiast wartość czasu, jeśli poprzedza punkt wstawiania *_Where*.)|

### <a name="return-value"></a>Wartość zwracana

[Hash_multiset::emplace](#emplace) funkcja elementu członkowskiego zwraca iterator, który wskazuje miejsce, w którym wstawiono nowy element do `hash_multiset`.

### <a name="remarks"></a>Uwagi

Wstawiania może wystąpić w amortyzowanym stałym czasie zamiast wartość czasu, jeśli poprzedza punkt wstawiania *_Where*.

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

## <a name="empty"></a>  hash_multiset::Empty

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Sprawdza, czy hash_multiset jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli hash_multiset jest pusta. **false** Jeśli hash_multiset jest niepusty.

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

## <a name="end"></a>  hash_multiset::end

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w hash_multiset.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do lokalizacji następującej po ostatnim elemencie w hash_multiset. Jeśli hash_multiset jest pusty, a następnie hash_multiset::end == hash_multiset::begin.

### <a name="remarks"></a>Uwagi

`end` Służy do sprawdzenia, czy iterator osiągnął koniec swojej hash_multiset. Wartość zwrócona przez obiekt `end` nie należy usuwać odwołania.

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

## <a name="equal_range"></a>  hash_multiset::equal_range

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zwraca parę iteratorów odpowiednio do pierwszego elementu w hash_multiset z kluczem, który jest większy niż określony klucz i do pierwszego elementu w hash_multiset z kluczem, który jest równy lub większy niż określony klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucz, który ma zostać porównane z klucza sortowania elementu z hash_multiset wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Para iteratorów, w których pierwsza to [lower_bound](#lower_bound) klucz, a drugi jest [upper_bound](#upper_bound) klucza.

Pierwszym iteratorem pary dostęp do `pr` zwróconą przez funkcję elementu członkowskiego, użyj `pr`. **pierwszy** wyłuskać iteratora dolną granicę użyj \*( `pr`. **najpierw**). Aby uzyskać dostęp drugi iterator w parze `pr` zwróconą przez funkcję elementu członkowskiego, użyj `pr`. **drugi** wyłuskać iteratora górną granicę użyj \*( `pr`. **Po drugie**).

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

## <a name="erase"></a>  hash_multiset::ERASE

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Usuwa element lub zakres elementów w hash_multiset z określonych pozycji lub usuwa elementy, które odpowiadają określonemu kluczowi.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_Where*<br/>
Pozycja elementu do usunięcia z hash_multiset.

*pierwszy*<br/>
Pozycja pierwszego elementu są usuwane z hash_multiset.

*ostatni*<br/>
Pozycja tuż za ostatnim elementem usunięte z hash_multiset.

*Klucz*<br/>
Klucz elementów do usunięcia z hash_multiset.

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie funkcje Członkowskie, aby uzyskać iteratora dwukierunkowego, określa pierwszy element pozostający poza wszelkimi elementami usuniętymi lub wskaźnika do końca hash_multiset, jeśli taki element nie istnieje. Aby uzyskać trzecia funkcji członkowska, liczbę elementów, które zostały usunięte z hash_multiset.

### <a name="remarks"></a>Uwagi

Funkcje elementów członkowskich nigdy nie zgłasza wyjątku.

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie hash_multiset::erase funkcja elementu członkowskiego.

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

## <a name="find"></a>  hash_multiset::Find

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator odnoszący się lokalizację elementu w hash_multiset, który ma klucz równoważny z określonym kluczem.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz argumentu mają być dopasowywane o klucz sortowania elementu z hash_multiset wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

[Iteratora](#iterator) lub [const_iterator](#const_iterator) który dotyczy lokalizacji elementu równoważny z określonym kluczem, lub który dotyczy lokalizacji następującej po ostatnim elemencie w hash_multiset — w przypadku braku dopasowania Znaleziono klucz.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator odnoszący się do elementu w hash_multiset, którego klucz sortowania jest `equivalent` do argumentu opartego na kluczu w obszarze predykat binarny, który wymusza kolejność, w mniej-niż porównywalności relacji.

Jeśli wartość zwracaną przez `find` jest przypisany do `const_iterator`, nie można zmodyfikować obiektu hash_multiset. Jeśli wartość zwracaną przez `find` jest przypisany do `iterator`, można zmodyfikować obiekt hash_multiset.

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

## <a name="get_allocator"></a>  hash_multiset::get_allocator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zwraca kopię obiektu programu przydzielania użytego do stworzenia hash_multiset.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez hash_multiset do zarządzania pamięci, która jest parametr szablonu klasy `Allocator`.

Aby uzyskać więcej informacji na temat `Allocator`, zobacz sekcję Uwagi [hash_multiset — klasa](../standard-library/hash-multiset-class.md) tematu.

### <a name="remarks"></a>Uwagi

Puli buforów dla klasy hash_multiset — Określ, jak klasa zarządza magazynem. Buforów domyślną dostarczony wraz z klasy kontenera standardowej biblioteki języka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.

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

## <a name="hash_multiset"></a>  hash_multiset::hash_multiset

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Konstruuje `hash_multiset` oznacza to pusta lub czyli kopią całości lub części innej `hash_multiset`.

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
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_multiset(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_multiset(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Al*|Klasa alokatora magazynu, który ma być używany dla tego `hash_multiset` obiektu, który domyślnie przyjmuje wartość `Allocator`.|
|*Comp*|Funkcja porównywania typu `const Traits` porządkowania elementów w `hash_multiset`, które domyślnie używa `hash_compare`.|
|*po prawej stronie*|`hash_multiset` Którego stworzonego elementu `hash_multiset` jest kopią.|
|*pierwszy*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*ostatni*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|
|*IList*|Lista initializer_list zawierająca elementy, które ma być skopiowany.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują obiekt alokatora, który zarządza magazynem pamięci dla typu `hash_multiset` i które później mogą być zwracane przez wywołanie metody [hash_multiset::get_allocator](#get_allocator). Parametr alokatora jest często pomijane w deklaracji klasy i wstępnego przetwarzania makra używane do zastąpienia buforów alternatywne.

Wszystkie konstruktory inicjują ich hash_multisets.

Wszystkie konstruktory zapisują obiekt funkcyjny tego typu `Traits` który jest używany do ustanawiania kolejność kluczy `hash_multiset` i które później mogą być zwracane przez wywołanie metody [hash_multiset::key_comp](#key_comp). Aby uzyskać więcej informacji na temat `Traits` zobacz [hash_multiset — klasa](../standard-library/hash-multiset-class.md) tematu.

Pierwsze trzy konstruktory Określ pusty początkową `hash_multiset`, drugi określa typ porównania funkcji (*Comp*) do użycia podczas ustalania kolejności elementów i trzeci jawne określenie Typ programu przydzielania (*Al*) ma być używany. Słowo kluczowe **jawne** powoduje pominięcie niektórych rodzajów konwersji typu automatyczne.

Czwarty Konstruktor przenosi `hash_multiset` `Right`.

Piąta szóstego i siódmego konstruktory używają initializer_list.

Ostatnie trzy konstruktory kopiują zakres [ `First`, `Last`) z `hash_multiset` uwzględni się rosnącą explicitness, określając typ porównania funkcji klasy porównania oraz alokatorem.

Rzeczywista kolejność elementów w kontenerze skrótu zestawu zależy od funkcji mieszania, funkcji szeregowania i bieżący rozmiar tabeli mieszania i ogólnie rzecz biorąc, nie można przewidzieć, ponieważ może to za pomocą kontenera zestawu, w której była określana przez funkcję sortowania samodzielnie.

## <a name="insert"></a>  hash_multiset::INSERT

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Wstawia element lub zakres elementów do hash_multiset.

```cpp
iterator insert(
    const Type& Val);

iterator insert(
    iterator Where,
    const Type& Al);

void insert(
    initializer_list<Type> IList);

iterator insert(
    const Type& Val);

iterator insert(
    Iterator Where,
    const Type& Val);

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
|*Val*|Wartość elementu do wstawienia do hash_multiset, chyba że hash_multiset zawiera już ten element, lub bardziej ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie są porządkowane.|
|*Where*|Miejsce, aby rozpocząć wyszukiwanie poprawne punktu wstawiania. (Wstawiania może wystąpić w amortyzowanym stałym czasie zamiast wartość czasu, jeśli poprzedza punkt wstawiania `_Where`.)|
|*pierwszy*|Pozycja pierwszego elementu mają być kopiowane z hash_multiset.|
|*ostatni*|Pozycja tuż za ostatnim elementem skopiowane z hash_multiset.|
|*IList*|Lista initializer_list zawierająca elementy do skopiowania.|

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwa Wstaw funkcje Członkowskie zwracają iterator, który wskazuje miejsce, w którym dodano nowy element.

Funkcje Członkowskie trzech kolejnych używają initializer_list.

Trzecia funkcja członkowska wstawia sekwencję wartości elementu do hash_multiset, odpowiadający każdego elementu kierowanego przez iterator w zakresie [ `First`, `Last`) z określoną hash_multiset.

### <a name="remarks"></a>Uwagi

Wstawiania może wystąpić w amortyzowanym stałym czasie dla wersji wskazówka wstawiania zamiast wartość czasu, jeśli poprzedza punkt wstawiania *gdzie*.

## <a name="iterator"></a>  hash_multiset::iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Uwagi

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład dotyczący [rozpocząć](#begin) przykładowy sposób deklarowania i użyj `iterator`.

## <a name="key_comp"></a>  hash_multiset::key_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w hash_multiset.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość parametru szablonu hash_multiset *cech*, który zawiera obiekty funkcji, które są używane do wyznaczania wartości skrótu oraz do porządkowania elementów kontenera.

Aby uzyskać więcej informacji na temat *cech* zobacz [hash_multiset — klasa](../standard-library/hash-multiset-class.md) tematu.

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członka:

**bool — operator**( **const Key &** *_xVal,* **const Key &** _ `yVal`);

Zwraca ona **true** Jeśli `_xVal` poprzedza i nie jest równa `_yVal` w porządku sortowania.

Należy pamiętać, że oba [key_compare](#key_compare) i [value_compare](#value_compare) synonimy dla parametru szablonu są *cech*. Oba typy są dostarczane dla hash_multiset i klas hash_multiset, gdzie są identyczne, na potrzeby utrzymywania zgodności z klas hash_map i hash_multimap, gdy są one różne.

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

## <a name="key_compare"></a>  hash_multiset::key_compare

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Typ, który zawiera dwa obiekty funkcyjne, predykat binarny porównania klasy, która może porównać dwie wartości elementów z hash_multiset, aby określić ich względną kolejność i Predykat jednoelementowy, który wyznacza wartość skrótu elementów.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare` synonim dla parametru szablonu jest *cech*.

Aby uzyskać więcej informacji na temat *cech* zobacz [hash_multiset — klasa](../standard-library/hash-multiset-class.md) tematu.

Należy pamiętać, że oba `key_compare` i value_compare synonimy dla parametru szablonu *cech*. Oba typy są dostarczane dla klasy hash_set i hash_multiset, w której są identyczne, zgodność z klas hash_map i hash_multimap, gdy są one różne.

### <a name="example"></a>Przykład

Zobacz przykład dotyczący [key_comp](#key_comp) przykładowy sposób deklarowania i użyj `key_compare`.

## <a name="key_type"></a>  hash_multiset::key_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza obiekt funkcji, która może porównać klucze sortowania, aby określić względną kolejność dwóch elementów w hash_multiset.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type` synonim dla parametru szablonu jest *klucz*.

Należy pamiętać, że oba `key_type` i [value_type](../standard-library/hash-set-class.md#value_type) synonimy dla parametru szablonu są *klucz*. Oba typy są dostarczane dla zestawu i zestawów wielokrotnych klas, w której są identyczne, zgodność z mapy i multimap klas, gdy są one różne.

Aby uzyskać więcej informacji na temat *klucz*, zobacz sekcję Uwagi [hash_multiset — klasa](../standard-library/hash-multiset-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład dotyczący [value_type](#value_type) przykładowy sposób deklarowania i użyj `key_type`.

## <a name="lower_bound"></a>  hash_multiset::lower_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator do pierwszego elementu w hash_multiset z kluczem, który jest równy lub większy od określonego klucza.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucz, który ma zostać porównane z klucza sortowania elementu z hash_multiset wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

[Iteratora](#iterator) lub [const_iterator](#const_iterator) położenie pierwszego elementu w hash_multiset, adresy przy użyciu klucza jest równy lub większy niż określony klucz argument lub który zapewnia, że kolejne lokalizacji ostatni element hash_multiset, jeśli nie zostanie znalezione dopasowanie dla klucza.

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

## <a name="max_size"></a>  hash_multiset::max_size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

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

## <a name="op_eq"></a>  hash_multiset::operator =

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zastępuje elementy hash_multiset kopią innego hash_multiset.

```cpp
hash_multiset& operator=(const hash_multiset& right);

hash_multiset& operator=(hash_multiset&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*right*|[Hash_multiset](../standard-library/hash-multiset-class.md) są kopiowane do `hash_multiset`.|

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkie elementy istniejących w `hash_multiset`, `operator=` kopiuje lub przenosi zawartość *prawo* do `hash_multiset`.

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

## <a name="pointer"></a>  hash_multiset::Pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza wskaźnik do elementu w hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iteratora](#iterator) powinien być używany do uzyskania dostępu do elementów w obiekcie multiset.

## <a name="rbegin"></a>  hash_multiset::rbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator odnoszący się do pierwszego elementu w odwróconym hash_multiset.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconym hash_multiset lub adresowania, który był ostatnim elementem w nieodwróconej hash_multiset.

### <a name="remarks"></a>Uwagi

`rbegin` jest używana z odwróconej hash_multiset — podobnie jak [rozpocząć](#begin) jest używana z hash_multiset.

Jeśli wartość zwracaną przez `rbegin` jest przypisany do `const_reverse_iterator`, wówczas nie można zmodyfikować obiektu hash_multiset. Jeśli wartość zwracaną przez `rbegin` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiekt hash_multiset.

`rbegin` może służyć do iterowania po hash_multiset Wstecz.

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
   // throught a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // throught a hash_multiset in a reverse order
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

## <a name="reference"></a>  hash_multiset::Reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

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

## <a name="rend"></a>  hash_multiset::rend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w odwróconej hash_multiset.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do lokalizacji następującej po ostatnim elemencie w odwróconej hash_multiset (miejsca przed pierwszym elementem w nieodwróconej hash_multiset).

### <a name="remarks"></a>Uwagi

`rend` jest używana z odwróconej hash_multiset — podobnie jak [zakończenia](#end) jest używana z hash_multiset.

Jeśli wartość zwracaną przez `rend` jest przypisany do `const_reverse_iterator`, wówczas nie można zmodyfikować obiektu hash_multiset. Jeśli wartość zwracaną przez `rend` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiekt hash_multiset. Wartość zwrócona przez obiekt `rend` nie należy usuwać odwołania.

`rend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej hash_multiset.

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
   // throught a hash_multiset in a reverse order
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

## <a name="reverse_iterator"></a>  hash_multiset::reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iterowania po hash_multiset w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład dotyczący [rbegin —](#rbegin) przykładowy sposób deklarowania i użyj `reverse_iterator`.

## <a name="size"></a>  hash_multiset::size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

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

## <a name="size_type"></a>  hash_multiset::size_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Zobacz przykład dotyczący [rozmiar](#size) przykładem sposobu deklarowanie i użycie `size_type`

## <a name="swap"></a>  hash_multiset::swap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zamienia elementy z dwóch hash_multisets.

```cpp
void swap(hash_multiset& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Hash_multiset — argument, zawierająca elementy, które mają być zamienione z hash_multiset docelowej.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego powoduje unieważnienie nie odwołania wskaźniki i Iteratory, które wyznaczają elementy w dwóch hash_multisets, której elementy są wymianie.

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

## <a name="upper_bound"></a>  hash_multiset::upper_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Zwraca iterator do pierwszego elementu w hash_multiset przy użyciu klucza, który jest większy od określonego klucza.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucz, który ma zostać porównane z klucza sortowania elementu z hash_multiset wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

[Iteratora](#iterator) lub [const_iterator](#const_iterator) który zapewnia lokalizacji do pierwszego elementu w hash_multiset kluczem większy niż określony klucz argument lub który dotyczy lokalizacji następującej po ostatnim elemencie w hash_multiset — Jeśli nie zostanie znalezione dopasowanie dla klucza.

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

## <a name="value_comp"></a>  hash_multiset::value_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Pobiera kopię obiektu porównania, użytego do uporządkowania wartości elementów w hash_multiset.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość parametru szablonu hash_multiset *cech*, który zawiera obiekty funkcji, które są używane do wyznaczania wartości skrótu i kolejność elementów kontenera.

Aby uzyskać więcej informacji na temat *cech* zobacz [hash_multiset — klasa](../standard-library/hash-multiset-class.md) tematu.

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członka:

**bool — operator**( **constKey &**`_xVal`, **const Key &** *_yVal*);

Zwraca ona **true** Jeśli `_xVal` poprzedza i nie jest równa `_yVal` w porządku sortowania.

Należy pamiętać, że oba [key_compare](#key_compare) i [value_compare](#value_compare) synonimy dla parametru szablonu są *cech*. Oba typy są dostarczane dla hash_multiset i klas hash_multiset, gdzie są identyczne, na potrzeby utrzymywania zgodności z klas hash_map i hash_multimap, gdy są one różne.

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

## <a name="value_compare"></a>  hash_multiset::value_compare

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Typ, który zawiera dwa obiekty funkcyjne, predykat binarny porównania klasy, która może porównać dwie wartości elementów z hash_multiset, aby określić ich względną kolejność i Predykat jednoelementowy, który wyznacza wartość skrótu elementów.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Uwagi

`value_compare` synonim dla parametru szablonu jest *cech*.

Aby uzyskać więcej informacji na temat *cech* zobacz [hash_multiset — klasa](../standard-library/hash-multiset-class.md) tematu.

Należy pamiętać, że oba [key_compare](#key_compare) i `value_compare` synonimy dla parametru szablonu są *cech*. Oba typy są dostarczane dla zestawu klas i multiset, gdzie są identyczne, zgodność z mapy klasy i multimap, gdy są one różne.

### <a name="example"></a>Przykład

Zobacz przykład dotyczący [value_comp —](#value_comp) przykładowy sposób deklarowania i użyj `value_compare`.

## <a name="value_type"></a>  hash_multiset::value_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Typ, który opisuje obiekt zapisany jako element jako hash_multiset w charakterze wartości.

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

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
