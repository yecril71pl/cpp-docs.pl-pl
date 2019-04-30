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
ms.openlocfilehash: c7d5df87dc6c8529d18b9f5fb960148c7362129a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405043"
---
# <a name="hashset-class"></a>hash_set — Klasa

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Hash_set — klasa kontenera jest rozszerzeniem C++ standardowej biblioteki i jest używany do przechowywania i szybkiego pobierania danych z kolekcji, w której wartości zawartych elementów są unikatowe i służą jako wartości klucza.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<Key>>
class hash_set
```

### <a name="parameters"></a>Parametry

*Key*<br/>
Typ danych elementu, który ma być przechowywany w hash_set.

*Cechy*<br/>
Typu, który obejmuje dwa obiekty funkcji, jednej klasy porównania oznacza to predykat binarny, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność i funkcję mieszania, która jest jednoargumentowy predykatu mapowania klucza wartości elementów na typy bez znaku liczby całkowite typu `size_t`. Ten argument jest opcjonalny, a `hash_compare<Key, less<Key> >` jest wartością domyślną.

*Allocator*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i dezalokacji pamięci hash_set. Ten argument jest opcjonalny, a wartość domyślna to `allocator<Key>`.

## <a name="remarks"></a>Uwagi

Hash_set — jest:

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza. Ponadto, jest prostym kontenerem asocjacyjnym, ponieważ jego wartości elementu są jego wartościami klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.

- Mieszany, ponieważ jego elementy są pogrupowane w przedziały, na podstawie wartości funkcji skrótu dotyczą kluczowych wartości elementów.

- Unikatowy w tym sensie, że każdy z jego elementów musi mieć unikatowy klucz. Ponieważ hash_set jest również prostym kontenerem asocjacyjnym, jego elementy są również unikatowe.

- Klasą szablonu, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Główną zaletą wyznaczania wartości skrótu, za pośrednictwem sortowania jest większą wydajność; Pomyślne mieszania wykonuje wstawień, usuwanie i znajduje w stałej Średni czas w porównaniu z danym proporcjonalny do logarytmu liczby elementów w kontenerze sortowania technik. Nie można bezpośrednio zmienić wartości elementu w zestawie. Zamiast tego musisz usunąć stare wartości i wstawić elementy z nowymi wartościami.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Skrótu kontenery asocjacyjne są zoptymalizowane dla operacji wyszukiwania, wstawiania i usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje są wydajne, gdy jest używana z funkcją dobrze zaprojektowanego wyznaczania wartości skrótu, wykonując je w czasie, który jest średnio stała i nie jest zależna od liczby elementów w kontenerze. Funkcja skrótu dobrze zaprojektowanego generuje jednolity rozkład wartości skrótu i minimalizuje liczbę konfliktów, w którym kolizji jest wyświetlany po odrębnych wartości klucza są mapowane na taką samą wartość skrótu. W najgorszym przypadku za pomocą funkcji skrótu możliwe najgorszy liczby operacji jest proporcjonalna do liczby elementów w sekwencji (liniowy czas).

Hash_set — powinna być kontenerem asocjacyjnym z wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Elementy hash_set są unikatowe i służą jako ich własne klucze sortowania. Model dla tego typu konstrukcji jest uporządkowaną listą, np. wyrazów, w których wyrazy mogą występować tylko raz. Gdyby zezwolono na wiele wystąpień wyrazów, hash_multiset byłaby odpowiednią strukturą kontenera. Gdyby wartości muszą być dołączone do listy unikatowych słów kluczowych, hash_map byłaby odpowiednią strukturą zawierającą te dane. Gdyby natomiast klucze nie są unikatowe, hash_multimap byłaby kontenerem z wyboru.

Hash_set — porządkuje sekwencję którą kontroluje, przez wywołanie metody skrótu przechowywaną `Traits` obiektu typu [value_compare](#value_compare). Ten przechowywany obiekt może być dostępna poprzez wywołanie funkcji elementu członkowskiego [key_comp](#key_comp). Obiekt funkcyjny musi zachowywać się taka sama jak obiekt klasy *hash_compare — < klucz, mniej\<klucz >>.* W szczególności dla wszystkich wartości `key` typu klucza, wywołanie cechy (`key`) daje w wyniku rozkład wartości typu size_t.

Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Powoduje to dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Binarny predykat *f*( *x*, *y*) jest obiektem funkcji, która ma dwa obiekty argumentu x i y oraz wartość zwracaną true lub false. Kolejność nałożona na hash_set jest ścisłym słabym porządkowaniem, jeśli predykat binarny jest niezwrotny, przeciwsymetryczny i przechodni oraz jeśli równoważność jest przechodnia, gdzie dwa obiekty *x* i *y* są zdefiniowane jako równoważne, gdy oba *f*( *x*, *y*) i *f*( *y*, *x*) mają wartość FAŁSZ. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

Rzeczywista kolejność elementów w kontrolowanej sekwencji zależy od funkcji mieszania, funkcja szeregowania i bieżący rozmiar tabeli mieszania przechowywanych w obiekcie kontenera. Nie można określić bieżący rozmiar tabeli wyznaczania wartości skrótu, dlatego ogólnie rzecz biorąc nie można przewidzieć kolejności elementów w kontrolowanej sekwencji. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Iterator dostarczony przez klasę hash_set jest iteratorem dwukierunkowym, ale funkcje składowych klasy [Wstaw](#insert) i [hash_set](#hash_set) mają wersje przyjmujące jako parametry szablonu słabszy iterator danych wejściowych którego wymagania funkcjonalności są mniejsze niż te gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcjonalności, ale jest wystarczający, aby można było mówić znacząco o zakresie iteratorów [ `first`, `last`) w kontekście funkcji składowych klasy.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[hash_set](#hash_set)|Konstruuje `hash_set` oznacza to pusta lub czyli kopią całości lub części innej `hash_set`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje `allocator` klasy dla `hash_set` obiektu.|
|[const_iterator](#const_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać `const` element `hash_set`.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do **const** element `hash_set`.|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do **const** przechowywanego w `hash_set` do odczytu i wykonywania **const** operacji.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **const** element `hash_set`.|
|[difference_type](#difference_type)|Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów `hash_set` w zakresie pomiędzy elementami wskazywanymi przez Iteratory.|
|[iterator](#iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w `hash_set`.|
|[key_compare —](#key_compare)|Typ, który dostarcza obiekt funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `hash_set`.|
|[key_type](#key_type)|Typ, który opisuje obiekt zapisany jako element `hash_set` w charakterze klucza sortowania.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu w `hash_set`.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w `hash_set`.|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej `hash_set`.|
|[size_type](#size_type)|Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w `hash_set`.|
|[value_compare —](#value_compare)|Typ, który zawiera dwa obiekty funkcyjne, predykat binarny porównania klasy, która może porównać dwie wartości elementów z `hash_set` ustalenie ich względne kolejności i jednoargumentowy predykat, który wyznacza wartość skrótu elementów.|
|[value_type](#value_type)|Typ, który opisuje obiekt zapisany jako element `hash_set` w charakterze wartości.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[begin](#begin)|Zwraca iterator odnoszący się do pierwszego elementu w `hash_set`.|
|[cbegin](#cbegin)|Zwraca iterator stałych adresujący pierwszy element w `hash_set`.|
|[cend](#cend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w `hash_set`.|
|[Usuń zaznaczenie](#clear)|Usuwa wszystkie elementy `hash_set`.|
|[Liczba](#count)|Zwraca liczbę elementów w `hash_set` których klucz pasuje do klucza określonego jako parametr.|
|[crbegin](#crbegin)|Zwraca iterator stałych adresujący pierwszy element w odwróconej `hash_set`.|
|[crend](#crend)|Zwraca iterator stałych adresujący lokalizację następującą po ostatnim elemencie w odwróconej `hash_set`.|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do `hash_set`.|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do `hash_set`, ze wskazówką położenia.|
|[pusty](#empty)|Sprawdza, czy `hash_set` jest pusty.|
|[koniec](#end)|Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w `hash_set`.|
|[equal_range](#equal_range)|Zwraca parę iteratorów odpowiednio do pierwszego elementu w `hash_set` przy użyciu klucza, który jest większy niż określony klucz i do pierwszego elementu w `hash_set` z kluczem, który jest równy lub większy niż określony klucz.|
|[wymazywanie](#erase)|Usuwa element lub zakres elementów w `hash_set` z określonych pozycji lub usuwa elementy, które odpowiadają określonemu kluczowi.|
|[Znajdź](#find)|Zwraca iterator odnoszący się lokalizację elementu w `hash_set` który ma klucz równoważny z określonym kluczem.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu `allocator` użytego do stworzenia `hash_set`.|
|[insert](#insert)|Wstawia element lub zakres elementów do `hash_set`.|
|[key_comp](#key_comp)|Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w `hash_set`.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu w `hash_set` z kluczem, który jest równy lub większy od określonego klucza.|
|[max_size](#max_size)|Zwraca maksymalną długość `hash_set`.|
|[rbegin](#rbegin)|Zwraca iterator odnoszący się do pierwszego elementu w odwróconej `hash_set`.|
|[rend](#rend)|Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w odwróconej `hash_set`.|
|[Rozmiar](#size)|Zwraca liczbę elementów w `hash_set`.|
|[swap](#swap)|Zamienia elementy z dwóch `hash_set`s.|
|[upper_bound —](#upper_bound)|Zwraca iterator do pierwszego elementu w `hash_set` , wraz z kluczem, który jest równy lub większy od określonego klucza.|
|[value_comp](#value_comp)|Pobiera kopię obiektu cech mieszania używany do wyznaczania wartości skrótu i kolejność wartości kluczy w elemencie `hash_set`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[hash_set::operator=](#op_eq)|Zastępuje elementy `hash_set` kopią innego `hash_set`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_set >

**Namespace:** stdext

## <a name="allocator_type"></a>  hash_set::allocator_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Typ, który reprezentuje klasę alokatora dla obiektu hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type` synonim dla parametru szablonu jest *alokatora*.

Aby uzyskać więcej informacji na temat *alokatora*, zobacz sekcję Uwagi [hash_set — klasa](../standard-library/hash-set-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład dotyczący [get_allocator —](#get_allocator) przykład, który używa `allocator_type`.

## <a name="begin"></a>  hash_set::BEGIN

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zwraca iterator odnoszący się do pierwszego elementu w hash_set.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pierwszego elementu w hash_set lub lokalizacji następującej po hash_set puste.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `begin` jest przypisany do `const_iterator`, nie można modyfikować elementów w obiekcie hash_set. Jeśli wartość zwracaną przez `begin` jest przypisany do `iterator`, elementów w obiekcie hash_set może być modyfikowany.

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

## <a name="cbegin"></a>  hash_set::cbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zwraca iterator const, który dotyczy pierwszego elementu w hash_set.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stały iterator dwukierunkowy odnoszący się do pierwszego elementu w [hash_set](../standard-library/hash-set-class.md) lub lokalizacji następującej po pustą `hash_set`.

### <a name="remarks"></a>Uwagi

Wartością zwracaną `cbegin`, elementy w `hash_set` nie można zmodyfikować obiektu.

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

## <a name="cend"></a>  hash_set::cend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zwraca iterator stałych adresujący lokalizację następującą po ostatnim elemencie w hash_set.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Const iteratora dwukierunkowego, który dotyczy lokalizacji następującej po ostatnim elemencie w [hash_set](../standard-library/hash-set-class.md). Jeśli `hash_set` jest pusta, następnie `hash_set::cend == hash_set::begin`.

### <a name="remarks"></a>Uwagi

`cend` Służy do sprawdzenia, czy iterator osiągnął koniec swojej `hash_set`. Wartość zwrócona przez obiekt `cend` nie należy usuwać odwołania.

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

## <a name="clear"></a>  hash_set::Clear

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

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

## <a name="const_iterator"></a>  hash_set::const_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać **const** element hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład dotyczący [rozpocząć](#begin) przykład, który używa `const_iterator`.

## <a name="const_pointer"></a>  hash_set::const_pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Typ, który dostarcza wskaźnik do **const** element hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

W większości przypadków [const_iterator](#const_iterator) powinien być używany do uzyskania dostępu do elementów w **const** hash_set obiektu.

## <a name="const_reference"></a>  hash_set::const_reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Typ, który zawiera odwołanie do **const** elementu przechowywanego w hash_set do odczytu i wykonywania **const** operacji.

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

## <a name="const_reverse_iterator"></a>  hash_set::const_reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **const** element hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i jest używany do iterowania po hash_set w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład [rend —](#rend) przykładem sposobu deklarowanie i użycie `const_reverse_iterator`

## <a name="count"></a>  hash_set::Count

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zwraca liczbę elementów w hash_set, w których klucz pasuje do klucza określonego jako parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz elementy, które mają być dopasowywane z hash_set.

### <a name="return-value"></a>Wartość zwracana

1, jeśli hash_set zawiera element, którego klucz sortowania jest zgodny z kluczem parametru.

0, jeśli hash_set nie zawiera elementu przy użyciu zgodnego klucza.

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca liczbę elementów w następującym zakresie:

\[ lower_bound (*klucz*), upper_bound (*klucz*)).

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie hash_set::count funkcja elementu członkowskiego.

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

## <a name="crbegin"></a>  hash_set::crbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zwraca iterator stałych adresujący pierwszy element w odwróconej hash_set.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconej [hash_set](../standard-library/hash-set-class.md) lub adresowania, który był ostatnim elementem w nieodwróconej `hash_set`.

### <a name="remarks"></a>Uwagi

`crbegin` jest używana z odwróconej hash_set — podobnie jak [hash_set::begin](#begin) jest używana z hash_set.

Wartością zwracaną `crbegin`, `hash_set` nie można zmodyfikować obiektu.

`crbegin` może służyć do iterowania po `hash_set` Wstecz.

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

## <a name="crend"></a>  hash_set::crend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconej hash_set.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iteratora dwukierunkowego, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconej [hash_set](../standard-library/hash-set-class.md) (miejsca przed pierwszym elementem w nieodwróconej `hash_set`).

### <a name="remarks"></a>Uwagi

`crend` jest używana z odwróconej `hash_set` podobnie jak [hash_set::end](#end) jest używana z `hash_set`.

Wartością zwracaną `crend`, `hash_set` nie można zmodyfikować obiektu.

`crend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej `hash_set`.

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

## <a name="difference_type"></a>  hash_set::difference_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów hash_set w zakresie pomiędzy elementami wskazywanymi przez Iteratory.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` Jest typ zwracany, jeśli odjęcie lub inkrementacji poprzez Iteratory kontenera. `difference_type` Jest zazwyczaj używany do reprezentowania liczby elementów w zakresie [ `first`, `last`) między Iteratory `first` i `last`, zawiera element wskazywany przez `first` i zakres elementów do , ale bez element wskazane przez `last`.

Należy pamiętać, że chociaż `difference_type` jest dostępna dla wszystkich iteratorów, które spełniają wymagania iteratora danych wejściowych zawiera klasę iteratorów dwukierunkowych obsługiwane przez odwracalnego kontenerów, takie jak zestaw, odejmowania między Iteratory są tylko obsługiwane przez Iteratory dostępu swobodnego, dostarczone przez kontener swobodnego dostępu, takich jak wektor lub deque.

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

## <a name="emplace"></a>  hash_set::emplace

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

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
|*Val*|Wartość elementu do wstawienia do [hash_set](../standard-library/hash-set-class.md) chyba że `hash_set` zawiera już ten element, lub bardziej ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie są porządkowane.|

### <a name="return-value"></a>Wartość zwracana

`emplace` Funkcja elementu członkowskiego zwraca parę którego **bool** składnik zwraca **true** jeśli wstawienie upewnij i **false** Jeśli `hash_set` już zawiera element, którego klucz ma wartość równoważne w kolejności i którego składnik iterator zwraca adres, w których dodano nowy element lub którym element został już znajduje się.

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

## <a name="emplace_hint"></a>  hash_set::emplace_hint

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

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
|*Val*|Wartość elementu do wstawienia do [hash_set](../standard-library/hash-set-class.md) chyba że `hash_set` zawiera już ten element, lub bardziej ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie są porządkowane.|
|*_Where*|Miejsce, aby rozpocząć wyszukiwanie poprawne punktu wstawiania. (Wstawiania może wystąpić w amortyzowanym stałym czasie zamiast wartość czasu, jeśli poprzedza punkt wstawiania *_Where*.)|

### <a name="return-value"></a>Wartość zwracana

[Hash_set::emplace](#emplace) funkcja elementu członkowskiego zwraca iterator, który wskazuje miejsce, w którym wstawiono nowy element do `hash_set`, lub w którym znajduje się istniejącego elementu z równoważną kolejność.

### <a name="remarks"></a>Uwagi

Wstawiania może wystąpić w amortyzowanym stałym czasie zamiast wartość czasu, jeśli poprzedza punkt wstawiania *_Where*.

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

## <a name="empty"></a>  hash_set::Empty

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Sprawdza, czy hash_set jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli hash_set jest pusta. **false** Jeśli hash_set jest niepusty.

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

## <a name="end"></a>  hash_set::end

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w hash_set.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do lokalizacji następującej po ostatnim elemencie w hash_set. Jeśli hash_set jest pusty, a następnie hash_set::end == hash_set::begin.

### <a name="remarks"></a>Uwagi

`end` Służy do sprawdzenia, czy iterator osiągnął koniec swojej hash_set. Wartość zwrócona przez obiekt `end` nie należy usuwać odwołania.

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

## <a name="equal_range"></a>  hash_set::equal_range

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zwraca parę iteratorów odpowiednio do pierwszego elementu w skrót zestawu z kluczem, który jest taki sam, z określonym kluczem i do pierwszego elementu w skrócie, ustaw za pomocą klucza, który jest większy niż określony klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucz, który ma zostać porównane z klucza sortowania elementu z hash_set wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Para iteratorów, w których pierwsza to [lower_bound](../standard-library/set-class.md#lower_bound) klucz, a drugi jest [upper_bound](../standard-library/set-class.md#upper_bound) klucza.

Aby uzyskać dostęp do pierwszym iteratorem pary żądania ściągnięcia, zwrócona przez funkcję elementu członkowskiego, należy użyć `pr`. **pierwszy**, wyłuskać iteratora dolną granicę użyj \*( `pr`. **najpierw**). Aby uzyskać dostęp drugi iterator w parze `pr` zwróconą przez funkcję elementu członkowskiego, użyj `pr`. **drugi**, wyłuskać iteratora górną granicę użyj \*( `pr`. **Po drugie**).

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

## <a name="erase"></a>  hash_set::ERASE

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Usuwa element lub zakres elementów w hash_set z określonych pozycji lub usuwa elementy, które odpowiadają określonemu kluczowi.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_Where*<br/>
Pozycja elementu do usunięcia z hash_set.

*pierwszy*<br/>
Pozycja pierwszego elementu są usuwane z hash_set.

*last*<br/>
Pozycja tuż za ostatnim elementem usunięte z hash_set.

*Klucz*<br/>
Klucz elementów do usunięcia z hash_set.

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie funkcje Członkowskie, aby uzyskać iteratora dwukierunkowego, określa pierwszy element pozostający poza wszelkimi elementami usuniętymi lub wskaźnika do końca hash_set, jeśli taki element nie istnieje. Aby uzyskać trzecia funkcji członkowska, liczbę elementów, które zostały usunięte z hash_set.

### <a name="remarks"></a>Uwagi

Funkcje elementów członkowskich nigdy nie zgłasza wyjątku.

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie hash_set::erase funkcja elementu członkowskiego.

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

## <a name="find"></a>  hash_set::Find

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zwraca iterator odnoszący się lokalizację elementu w hash_set, który ma klucz równoważny z określonym kluczem.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz argumentu mają być dopasowywane o klucz sortowania elementu z hash_set wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

`iterator` Lub `const_iterator` który dotyczy lokalizacji elementu równoważny z określonym kluczem, lub który adresów lokalizację po ostatnim elemencie w hash_set, jeśli nie zostanie znalezione dopasowanie dla klucza.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator odnoszący się do elementu w hash_set, którego klucz sortowania jest `equivalent` do argumentu opartego na kluczu w obszarze predykat binarny, który wymusza kolejność, w mniej-niż porównywalności relacji.

Jeśli wartość zwracaną przez `find` jest przypisany do `const_iterator`, nie można zmodyfikować obiektu hash_set. Jeśli wartość zwracaną przez `find` jest przypisany do `iterator`, można zmodyfikować obiekt hash_set.

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

## <a name="get_allocator"></a>  hash_set::get_allocator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zwraca kopię obiektu programu przydzielania użytego do stworzenia hash_set.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez hash_set do zarządzania pamięci, która jest parametr szablonu *alokatora*.

Aby uzyskać więcej informacji na temat *alokatora*, zobacz sekcję Uwagi [hash_set — klasa](../standard-library/hash-set-class.md) tematu.

### <a name="remarks"></a>Uwagi

Puli buforów dla klasy hash_set — Określ, jak klasa zarządza magazynem. Buforów domyślną dostarczony wraz z klasy kontenera standardowej biblioteki języka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.

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

## <a name="hash_set"></a>  hash_set::hash_set

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Konstruuje `hash_set` oznacza to pusta lub czyli kopią całości lub części innej `hash_set`.

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
|*Al*|Klasa alokatora magazynu, który ma być używany dla tego `hash_set` obiektu, który domyślnie przyjmuje wartość `Allocator`.|
|*Comp*|Funkcja porównywania typu `const Traits` porządkowania elementów w `hash_set`, które domyślnie używa `hash_compare`.|
|*po prawej stronie*|`hash_set` Którego stworzonego elementu `hash_set` jest kopią.|
|*pierwszy*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*ostatni*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują obiekt alokatora, który zarządza magazynem pamięci dla typu `hash_set` i które później mogą być zwracane przez wywołanie metody [hash_set::get_allocator](#get_allocator). Parametr alokatora jest często pomijane w deklaracji klasy i wstępnego przetwarzania makra używane do zastąpienia buforów alternatywne.

Wszystkie konstruktory inicjują ich hash_sets.

Wszystkie konstruktory zapisują obiekt funkcyjny tego typu `Traits` który jest używany do ustanawiania kolejność kluczy `hash_set` i które później mogą być zwracane przez wywołanie metody [hash_set::key_comp](#key_comp). Aby uzyskać więcej informacji na temat `Traits` zobacz [hash_set — klasa](../standard-library/hash-set-class.md) tematu.

Pierwszy Konstruktor tworzy pustą początkową `hash_set` drugi określa typ funkcji porównywania ( `Comp`) do użycia podczas ustalania kolejności elementów, a trzeci jawnie określa typ programu przydzielania ( `Al`) jako używane. Słowo kluczowe `explicit` powoduje pominięcie niektórych rodzajów konwersji typu automatyczne.

Czwarty i piąty Konstruktor określają kopię `hash_set` `Right`.

Ostatni szóstego, siódmy i ósmy konstruktory używają initializer_list dla elementów.

Ostatnie konstruktory kopiują zakres [ `First`, `Last`) z `hash_set` uwzględni się rosnącą explicitness, określając typ funkcji porównywania cech klasy i alokatora.

Ósmego Konstruktor przenosi `hash_set` `Right`.

Rzeczywista kolejność elementów w `hash_set` kontenera jest zależny od funkcji mieszania, funkcji szeregowania i bieżący rozmiar skrót tabeli i ogólnie rzecz biorąc, nie można przewidzieć, ponieważ może to za pomocą kontenera zestawu, w której został określana przez kolejność Funkcja samodzielnie.

## <a name="insert"></a>  hash_set::INSERT

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

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
|*Val*|Wartość elementu do wstawienia do `hash_set` chyba że `hash_set` zawiera już ten element, lub bardziej ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie są porządkowane.|
|*Where*|Miejsce, aby rozpocząć wyszukiwanie poprawne punktu wstawiania. (Wstawiania może wystąpić w amortyzowanym stałym czasie zamiast wartość czasu, jeśli poprzedza punkt wstawiania `_Where`.)|
|*pierwszy*|Pozycja pierwszego elementu mają być kopiowane z `hash_set`.|
|*ostatni*|Pozycja tuż za ostatnim elementem skopiowane z `hash_set`.|
|*IList*|Lista initializer_list, z której mają być skopiowane elementy.|

### <a name="return-value"></a>Wartość zwracana

Pierwszy `insert` funkcja elementu członkowskiego zwraca parę którego **bool** składnik zwraca **true** jeśli wstawienie upewnij i **false** Jeśli `hash_set` już zawiera element, którego klucz ma wartość równoważne w kolejności i którego składnik iterator zwraca adres, w których dodano nowy element lub którym element został już znajduje się.

Aby dostęp do składnika iterator w parze `pr` zwracana przez tę funkcję elementu członkowskiego, użyj `pr.first` odwołania do niego użyj `*(pr.first)`. Aby uzyskać dostęp do **bool** składnika pary `pr` zwracana przez tę funkcję elementu członkowskiego, użyj `pr.second`, odwołania do niego użyj `*(pr.second)`.

Drugi `insert` funkcja elementu członkowskiego zwraca iterator, który wskazuje miejsce, w którym wstawiono nowy element do `hash_set`.

### <a name="remarks"></a>Uwagi

Trzecia funkcja członkowska Wstawia elementy initializer_list.

Trzecia funkcja członkowska wstawia sekwencję wartości elementu `hash_set` odpowiadający każdego elementu kierowanego przez iterator w zakresie [ `First`, `Last`) określonego `hash_set`.

## <a name="iterator"></a>  hash_set::iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Uwagi

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin) przykładowy sposób deklarowania i użyj `iterator`.

## <a name="key_comp"></a>  hash_set::key_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Pobiera kopię obiektu cech mieszania używany do wyznaczania wartości skrótu i kolejność wartości klucza elementu w hash_set.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji, która hash_set używa do porządkowania jego elementów, czyli wartość parametru szablonu *cech*.

Aby uzyskać więcej informacji na temat *cech* zobacz [hash_set — klasa](../standard-library/hash-set-class.md) tematu.

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członka:

`bool operator( const Key& _xVal, const Key& _yVal );`

Zwraca ona **true** Jeśli `_xVal` poprzedza i nie jest równa `_yVal` w porządku sortowania.

Należy pamiętać, że oba [key_compare](#key_compare) i [value_compare](#value_compare) synonimy dla parametru szablonu są *cech*. Oba typy są dostarczane dla klasy hash_set i hash_multiset, w której są identyczne, zgodność z klas hash_map i hash_multimap, gdy są one różne.

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

## <a name="key_compare"></a>  hash_set::key_compare

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Typ, który dostarcza obiekt funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w hash_set.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare` synonim dla parametru szablonu jest *cech*.

Aby uzyskać więcej informacji na temat *cech* zobacz [hash_set — klasa](../standard-library/hash-set-class.md) tematu.

Należy pamiętać, że oba `key_compare` i [value_compare](#value_compare) synonimy dla parametru szablonu są *cech*. Oba typy są dostarczane dla zestawu i zestawów wielokrotnych klas, w której są identyczne, zgodność z mapy i multimap klas, gdy są one różne.

### <a name="example"></a>Przykład

Zobacz przykład [key_comp](#key_comp) przykładowy sposób deklarowania i użyj `key_compare`.

## <a name="key_type"></a>  hash_set::key_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Typ, który opisuje obiekt zapisany jako element hash_set w charakterze klucza sortowania.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type` synonim dla parametru szablonu jest *klucz*.

Aby uzyskać więcej informacji na temat *klucz*, zobacz sekcję Uwagi [hash_set — klasa](../standard-library/hash-set-class.md) tematu.

Należy pamiętać, że oba `key_type` i [value_type](#value_type) synonimy dla parametru szablonu są *klucz*. Oba typy są dostarczane dla klasy hash_set i hash_multiset, w której są identyczne, zgodność z klas hash_map i hash_multimap, gdy są one różne.

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) przykładowy sposób deklarowania i użyj `key_type`.

## <a name="lower_bound"></a>  hash_set::lower_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zwraca iterator do pierwszego elementu w hash_set z kluczem, który jest równy lub większy od określonego klucza.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucz, który ma zostać porównane z klucza sortowania elementu z hash_set wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

`iterator` Lub `const_iterator` czy adresy lokalizację elementu w hash_set, że za pomocą klucza, który jest równy lub większy niż określony klucz argument lub który dotyczy lokalizacji następującej po ostatnim elemencie w hash_set, jeśli nie są takie same znajduje się dla klucza.

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

## <a name="max_size"></a>  hash_set::max_size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

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

## <a name="op_eq"></a>  hash_set::operator =

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zastępuje elementy hash_set kopią innego hash_set.

```cpp
hash_set& operator=(const hash_set& right);

hash_set& operator=(hash_set&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*right*|[Hash_set](../standard-library/hash-set-class.md) są kopiowane do `hash_set`.|

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkie elementy istniejących w `hash_set`, `operator=` kopiuje lub przenosi zawartość *prawo* do `hash_set`.

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

## <a name="pointer"></a>  hash_set::Pointer

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Typ, który dostarcza wskaźnik do elementu w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iteratora](#iterator) powinien być używany do uzyskania dostępu do elementów w obiekcie hash_set.

## <a name="rbegin"></a>  hash_set::rbegin

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zwraca iterator odnoszący się do pierwszego elementu w odwróconym hash_set.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconym hash_set lub adresowania, który był ostatnim elementem w nieodwróconej hash_set.

### <a name="remarks"></a>Uwagi

`rbegin` jest używana z odwróconej hash_set — podobnie jak [rozpocząć](#begin) jest używana z hash_set.

Jeśli wartość zwracaną przez `rbegin` jest przypisany do `const_reverse_iterator`, wówczas nie można zmodyfikować obiektu hash_set. Jeśli wartość zwracaną przez `rbegin` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiekt hash_set.

`rbegin` może służyć do iterowania po hash_set Wstecz.

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

## <a name="reference"></a>  hash_set::Reference

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

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

## <a name="rend"></a>  hash_set::rend

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w odwróconej hash_set.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do lokalizacji następującej po ostatnim elemencie w odwróconej hash_set (miejsca przed pierwszym elementem w hash_set nieodwróconej).

### <a name="remarks"></a>Uwagi

`rend` jest używana z odwróconej hash_set — podobnie jak [zakończenia](#end) jest używana z hash_set.

Jeśli wartość zwracaną przez `rend` jest przypisany do `const_reverse_iterator`, wówczas nie można zmodyfikować obiektu hash_set. Jeśli wartość zwracaną przez `rend` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiekt hash_set. Wartość zwrócona przez obiekt `rend` nie należy usuwać odwołania.

`rend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej hash_set.

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

## <a name="reverse_iterator"></a>  hash_set::reverse_iterator

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iterowania po hash_set w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład [rbegin —](#rbegin) przykładowy sposób deklarowania i użyj `reverse_iterator`.

## <a name="size"></a>  hash_set::size

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

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

## <a name="size_type"></a>  hash_set::size_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Zobacz przykład [rozmiar](#size) przykładem sposobu deklarowanie i użycie `size_type`

## <a name="swap"></a>  hash_set::swap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zamienia elementy z dwóch hash_sets.

```cpp
void swap(hash_set& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Hash_set — argument, zawierająca elementy, które mają być zamienione z hash_set docelowej.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego powoduje unieważnienie nie odwołania wskaźniki i Iteratory, które wyznaczają elementy w dwóch hash_sets, której elementy są wymianie.

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

## <a name="upper_bound"></a>  hash_set::upper_bound

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zwraca iterator do pierwszego elementu w hash_set, za pomocą klucza, który jest większy od określonego klucza.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucz, który ma zostać porównane z klucza sortowania elementu z hash_set wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

`iterator` Lub `const_iterator` czy adresy lokalizację elementu w hash_set, że za pomocą klucza, który jest równy lub większy niż określony klucz argument lub który dotyczy lokalizacji następującej po ostatnim elemencie w hash_set, jeśli nie są takie same znajduje się dla klucza.

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

## <a name="value_comp"></a>  hash_set::value_comp

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Pobiera kopię obiektu porównania, użytego do uporządkowania wartości elementów w hash_set.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji, która hash_set używa do porządkowania jego elementów, czyli wartość parametru szablonu *porównaj*.

Aby uzyskać więcej informacji na temat *porównania*, zobacz sekcję Uwagi [hash_set — klasa](../standard-library/hash-set-class.md) tematu.

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członka:

`bool operator( const Key& _xVal, const Key& _yVal );`

Zwraca ona **true** Jeśli `_xVal` poprzedza i nie jest równa `_yVal` w porządku sortowania.

Należy pamiętać, że oba [value_compare](../standard-library/set-class.md#value_compare) i [key_compare](../standard-library/set-class.md#key_compare) synonimy dla parametru szablonu są *porównaj*. Oba typy są dostarczane dla klasy hash_set i hash_multiset, w której są identyczne, zgodność z klas hash_map i hash_multimap, gdy są one różne.

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

## <a name="value_compare"></a>  hash_set::value_compare

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Typ, który zawiera dwa obiekty funkcyjne, predykat binarny porównania klasy, która może porównać dwie wartości elementów z hash_set, aby określić ich względną kolejność i Predykat jednoelementowy, który wyznacza wartość skrótu elementów.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Uwagi

`value_compare` synonim dla parametru szablonu jest *cech*.

Aby uzyskać więcej informacji na temat *cech* zobacz [hash_set — klasa](../standard-library/hash-set-class.md) tematu.

Należy pamiętać, że oba [key_compare](#key_compare) i `value_compare` synonimy dla parametru szablonu są *cech*. Oba typy są dostarczane dla klasy hash_set i hash_multiset, w której są identyczne, zgodność z klas hash_map i hash_multimap, gdy są one różne.

### <a name="example"></a>Przykład

Zobacz przykład [value_comp —](#value_comp) przykładowy sposób deklarowania i użyj `value_compare`.

## <a name="value_type"></a>  hash_set::value_type

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Typ, który opisuje obiekt zapisany jako element hash_set w charakterze wartości.

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

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
