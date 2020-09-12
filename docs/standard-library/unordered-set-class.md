---
title: unordered_set — Klasa
description: Dokumentacja interfejsu API dla klasy kontenera standardowej biblioteki języka C++ `unordered_set` , która jest używana do przechowywania i pobierania danych z nieuporządkowanej kolekcji.
ms.date: 9/9/2020
f1_keywords:
- unordered_set/std::unordered_set
- unordered_set/std::unordered_set::allocator_type
- unordered_set/std::unordered_set::const_iterator
- unordered_set/std::unordered_set::const_local_iterator
- unordered_set/std::unordered_set::const_pointer
- unordered_set/std::unordered_set::const_reference
- unordered_set/std::unordered_set::difference_type
- unordered_set/std::unordered_set::hasher
- unordered_set/std::unordered_set::iterator
- unordered_set/std::unordered_set::key_equal
- unordered_set/std::unordered_set::key_type
- unordered_set/std::unordered_set::local_iterator
- unordered_set/std::unordered_set::pointer
- unordered_set/std::unordered_set::reference
- unordered_set/std::unordered_set::size_type
- unordered_set/std::unordered_set::value_type
- unordered_set/std::unordered_set::begin
- unordered_set/std::unordered_set::bucket
- unordered_set/std::unordered_set::bucket_count
- unordered_set/std::unordered_set::bucket_size
- unordered_set/std::unordered_set::cbegin
- unordered_set/std::unordered_set::cend
- unordered_set/std::unordered_set::clear
- unordered_set/std::unordered_set::count
- unordered_set/std::unordered_set::contains
- unordered_set/std::unordered_set::emplace
- unordered_set/std::unordered_set::emplace_hint
- unordered_set/std::unordered_set::empty
- unordered_set/std::unordered_set::end
- unordered_set/std::unordered_set::equal_range
- unordered_set/std::unordered_set::erase
- unordered_set/std::unordered_set::find
- unordered_set/std::unordered_set::get_allocator
- unordered_set/std::unordered_set::hash
- unordered_set/std::unordered_set::insert
- unordered_set/std::unordered_set::key_eq
- unordered_set/std::unordered_set::load_factor
- unordered_set/std::unordered_set::max_bucket_count
- unordered_set/std::unordered_set::max_load_factor
- unordered_set/std::unordered_set::max_size
- unordered_set/std::unordered_set::rehash
- unordered_set/std::unordered_set::size
- unordered_set/std::unordered_set::swap
- unordered_set/std::unordered_set::unordered_set
- unordered_set/std::unordered_set::operator=
- unordered_set/std::unordered_set::hash_function
helpviewer_keywords:
- std::unordered_set
- std::unordered_set::allocator_type
- std::unordered_set::const_iterator
- std::unordered_set::const_local_iterator
- std::unordered_set::const_pointer
- std::unordered_set::const_reference
- std::unordered_set::difference_type
- std::unordered_set::hasher
- std::unordered_set::iterator
- std::unordered_set::key_equal
- std::unordered_set::key_type
- std::unordered_set::local_iterator
- std::unordered_set::pointer
- std::unordered_set::reference
- std::unordered_set::size_type
- std::unordered_set::value_type
- std::unordered_set::begin
- std::unordered_set::bucket
- std::unordered_set::bucket_count
- std::unordered_set::bucket_size
- std::unordered_set::cbegin
- std::unordered_set::cend
- std::unordered_set::clear
- std::unordered_set::contains
- std::unordered_set::count
- std::unordered_set::emplace
- std::unordered_set::emplace_hint
- std::unordered_set::empty
- std::unordered_set::end
- std::unordered_set::equal_range
- std::unordered_set::erase
- std::unordered_set::find
- std::unordered_set::get_allocator
- std::unordered_set::hash
- std::unordered_set::insert
- std::unordered_set::key_eq
- std::unordered_set::load_factor
- std::unordered_set::max_bucket_count
- std::unordered_set::max_load_factor
- std::unordered_set::max_size
- std::unordered_set::rehash
- std::unordered_set::size
- std::unordered_set::swap
- std::unordered_set::unordered_set
- std::unordered_set::operator=
- std::unordered_set::allocator_type
- std::unordered_set::const_iterator
- std::unordered_set::const_local_iterator
- std::unordered_set::const_pointer
- std::unordered_set::const_reference
- std::unordered_set::difference_type
- std::unordered_set::hasher
- std::unordered_set::iterator
- std::unordered_set::key_equal
- std::unordered_set::key_type
- std::unordered_set::local_iterator
- std::unordered_set::pointer
- std::unordered_set::reference
- std::unordered_set::size_type
- std::unordered_set::value_type
- std::unordered_set::begin
- std::unordered_set::bucket
- std::unordered_set::bucket_count
- std::unordered_set::bucket_size
- std::unordered_set::cbegin
- std::unordered_set::cend
- std::unordered_set::clear
- std::unordered_set::count
- std::unordered_set::emplace
- std::unordered_set::emplace_hint
- std::unordered_set::empty
- std::unordered_set::end
- std::unordered_set::equal_range
- std::unordered_set::erase
- std::unordered_set::find
- std::unordered_set::get_allocator
- std::unordered_set::hash_function
- std::unordered_set::insert
- std::unordered_set::key_eq
- std::unordered_set::load_factor
- std::unordered_set::max_bucket_count
- std::unordered_set::max_load_factor
- std::unordered_set::max_size
- std::unordered_set::rehash
- std::unordered_set::size
- std::unordered_set::swap
ms.assetid: ac08084e-05a7-48c0-9ae4-d40c529922dd
ms.openlocfilehash: 396465b24e9d7cf0facbe324c7b01479fe8e9b6b
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040044"
---
# <a name="unordered_set-class"></a>unordered_set — Klasa

Szablon klasy opisuje obiekt, który kontroluje różnej długości sekwencje elementów typu `const Key` . Sekwencja jest słabo uporządkowana według funkcji mieszania, która dzieli sekwencję na uporządkowany zestaw podsekwencji, zwanych przedziałami, segmentami lub pakietami. W każdym przedziale funkcja porównywania określa, czy dowolna para elementów ma równoważne porządkowanie. Każdy element służy jako zarówno klucz sortowania, jak i wartość. Sekwencja jest reprezentowana w sposób, który pozwala na wyszukiwanie, wstawianie i usuwanie dowolnego elementu z wielu operacji, które mogą być niezależne od liczby elementów w sekwencji (stały czas), co najmniej kiedy wszystkie przedziały są w przybliżeniu jednakowej długości. W najgorszym przypadku, gdy wszystkie elementy znajdują się w jednym przedziale, liczba operacji jest proporcjonalna do liczby elementów w sekwencji (liniowy czas). Wstawianie elementu unieważnia brak iteratorów i usunięcie elementu unieważnia tylko te Iteratory, które wskazują na usunięty element.

## <a name="syntax"></a>Składnia

```cpp
template <
   class Key,
   class Hash = std::hash<Key>,
   class Pred = std::equal_to<Key>,
   class Alloc = std::allocator<Key>>
class unordered_set;
```

### <a name="parameters"></a>Parametry

*Głównych*\
Typ klucza.

*Skrótu*\
Typ obiektu funkcji mieszania.

*Pred*\
Typ obiektu funkcji porównywania równości.

*Alokacj*\
Klasa alokatora.

## <a name="members"></a>Elementy członkowskie

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ alokatora do zarządzania pamięcią.|
|[const_iterator](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|
|[const_local_iterator](#const_local_iterator)|Typ iteratora stałego przedziału dla kontrolowanej sekwencji.|
|[const_pointer](#const_pointer)|Typ stałego wskaźnika do elementu.|
|[const_reference](#const_reference)|Typ stałego odwołania do elementu.|
|[difference_type](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|
|[programu tworzącego skróty](#hasher)|Typ funkcji mieszania.|
|[Iterator](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[key_equal](#key_equal)|Typ funkcji porównywania.|
|[key_type](#key_type)|Typ klucza sortowania.|
|[local_iterator](#local_iterator)|Typ iteratora przedziału dla kontrolowanej sekwencji.|
|[pointer](#pointer)|Typ wskaźnika do elementu.|
|[odwoła](#reference)|Typ odwołania do elementu.|
|[size_type](#size_type)|Typ odległości bez znaku między dwoma elementami.|
|[value_type](#value_type)|Typ elementu.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|-|-|
|[zaczną](#begin)|Określa początek kontrolowanej sekwencji.|
|[porcj](#bucket)|Pobiera numer przedziału dla wartości klucza.|
|[bucket_count](#bucket_count)|Pobiera liczbę przedziałów.|
|[bucket_size](#bucket_size)|Pobiera rozmiar przedziału.|
|[cbegin](#cbegin)|Określa początek kontrolowanej sekwencji.|
|[cend](#cend)|Określa koniec kontrolowanej sekwencji.|
|[Wyczyść](#clear)|Usuwa wszystkie elementy.|
|[zawiera](#contains)<sup>c++ 20</sup>|Sprawdź, czy istnieje element z określonym kluczem w `unordered_set` .|
|[liczbą](#count)|Wyszukuje liczbę elementów pasujących do określonego klucza.|
|[emplace](#emplace)|Dodaje element skonstruowany na miejscu.|
|[emplace_hint](#emplace_hint)|Dodaje element skonstruowany na miejscu, z podpowiedzią.|
|[puste](#empty)|Sprawdza, czy nie ma żadnych elementów.|
|[punktów](#end)|Określa koniec kontrolowanej sekwencji.|
|[equal_range](#equal_range)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|
|[Wyłączanie](#erase)|Usuwa elementy z określonych pozycji.|
|[find](#find)|Wyszukuje element, który odpowiada określonemu kluczowi.|
|[get_allocator](#get_allocator)|Pobiera przechowywany obiekt alokatora.|
|[hash_function](#hash)|Pobiera przechowywany obiekt funkcji mieszania.|
|[wstawienia](#insert)|Dodaje elementy.|
|[key_eq](#key_eq)|Pobiera przechowywany obiekt funkcji porównywania.|
|[load_factor](#load_factor)|Oblicza średnią liczbę elementów na przedział.|
|[max_bucket_count](#max_bucket_count)|Pobiera maksymalną liczbę przedziałów.|
|[max_load_factor](#max_load_factor)|Pobiera lub ustawia maksymalną liczbę elementów na przedział.|
|[max_size](#max_size)|Pobiera maksymalny rozmiar kontrolowanej sekwencji.|
|[rehash —](#rehash)|Przebudowuje tabelę mieszania.|
|[zmienia](#size)|Liczy liczbę elementów.|
|[wymiany](#swap)|Zamienia zawartości dwóch kontenerów.|
|[unordered_set](#unordered_set)|Konstruuje obiekt kontenera.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[unordered_set:: operator =](#op_eq)|Kopiuje tabelę mieszania.|

## <a name="remarks"></a>Uwagi

Obiekt porządkuje sekwencję, która kontroluje, wywołując dwa przechowywane obiekty, obiekt funkcji porównania typu [unordered_set:: key_equal](#key_equal) i obiektu funkcji hash typu [unordered_set:: Hasher](#hasher). Dostęp do pierwszego przechowywanego obiektu można uzyskać, wywołując funkcję członkowską [unordered_set:: key_eq](#key_eq) `()` ; i uzyskując dostęp do drugiego przechowywanego obiektu przez wywołanie funkcji składowej [unordered_set:: hash_function](#hash) `()` . W odniesieniu do wszystkich wartości `X` i `Y` typu `Key` , wywołanie `key_eq()(X, Y)` zwraca wartość true tylko wtedy, gdy dwie wartości argumentu mają równoważne porządkowanie; `hash_function()(keyval)` wywołanie daje rozkład wartości typu `size_t` . W odróżnieniu od szablonu klasy [Unordered_multiset Klasa](../standard-library/unordered-multiset-class.md), obiekt typu `unordered_set` gwarantuje, że `key_eq()(X, Y)` zawsze ma wartość false dla każdego z dwóch elementów kontrolowanej sekwencji. (Klucze są unikatowe).

Obiekt przechowuje również współczynnik maksymalnego obciążenia, który określa maksymalną żądaną średnią liczbę elementów na przedział. Jeśli wstawianie elementu powoduje, że [unordered_set:: load_factor](#load_factor) `()` do przekroczenia maksymalnego współczynnika obciążenia, kontener zwiększa liczbę zasobników i ponownie kompiluje tabelę skrótów zgodnie z wymaganiami.

Rzeczywista kolejność elementów w kontrolowanej sekwencji zależy od funkcji mieszania, funkcji porównywania, kolejności wstawiania, współczynnika maksymalnego obciążenia i bieżącej liczby przedziałów. Nie można ogólnie przewidzieć kolejności elementów w kontrolowanej sekwencji. Można jednak zawsze mieć pewność, że dowolny podzbiór elementów, które mają równoważną kolejność, są obok siebie w kontrolowanej sekwencji.

Obiekt przydziela i zwalnia magazyn dla sekwencji, która kontroluje przez przechowywany obiekt alokatora typu [unordered_set:: allocator_type](#allocator_type). Taki obiekt alokatora musi mieć ten sam interfejs zewnętrzny co obiekt typu `allocator` . Przechowywany obiekt alokatora nie jest kopiowany po przypisaniu obiektu kontenera.

## <a name="unordered_setallocator_type"></a><a name="allocator_type"></a> unordered_set:: allocator_type

Typ alokatora do zarządzania pamięcią.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Alloc` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_allocator_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Myset c1;

    Myset::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
    << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="begin"></a><a name="begin"></a> zaczną

Określa początek kontrolowanej sekwencji lub przedziału.

```cpp
iterator begin();

const_iterator begin() const;

local_iterator begin(size_type nbucket);

const_local_iterator begin(size_type nbucket) const;
```

### <a name="parameters"></a>Parametry

*nbucket*\
Numer zasobnika.

### <a name="remarks"></a>Uwagi

Pierwsze dwie funkcje członkowskie zwracają iterator do przodu, który wskazuje na pierwszy element sekwencji (lub tuż poza końcem pustej sekwencji). Ostatnie dwie funkcje członkowskie zwracają iterator do przodu, który wskazuje na pierwszy element zasobnika *nbucket* (lub tuż poza końcem pustego zasobnika).

### <a name="example"></a>Przykład

```cpp
// unordered_set_begin.cpp
// compile using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>

using namespace std;

typedef unordered_set<char> MySet;

int main()
{
    MySet c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents using range-based for
    for (auto it : c1) {
    cout << "[" << it << "] ";
    }

    cout << endl;

    // display contents using explicit for
    for (MySet::const_iterator it = c1.begin(); it != c1.end(); ++it) {
        cout << "[" << *it << "] ";
    }

    cout << std::endl;

    // display first two items
    MySet::iterator it2 = c1.begin();
    cout << "[" << *it2 << "] ";
    ++it2;
    cout << "[" << *it2 << "] ";
    cout << endl;

    // display bucket containing 'a'
    MySet::const_local_iterator lit = c1.begin(c1.bucket('a'));
    cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[a] [b] [c]
[a] [b] [c]
[a] [b]
[a]
```

## <a name="bucket"></a><a name="bucket"></a> porcj

Pobiera numer przedziału dla wartości klucza.

```cpp
size_type bucket(const Key& keyval) const;
```

### <a name="parameters"></a>Parametry

*keyval*\
Wartość klucza do zamapowania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca numer zasobnika aktualnie odpowiadający wartości klucza *keyval*.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_bucket.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // display buckets for keys
    Myset::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
    << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="bucket_count"></a><a name="bucket_count"></a> bucket_count

Pobiera liczbę przedziałów.

```cpp
size_type bucket_count() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca bieżącą liczbę zasobników.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_bucket_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="bucket_size"></a><a name="bucket_size"></a> bucket_size

Pobiera rozmiar zasobnika

```cpp
size_type bucket_size(size_type nbucket) const;
```

### <a name="parameters"></a>Parametry

*nbucket*\
Numer zasobnika.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca rozmiar zasobnika *nbucket*.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_bucket_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // display buckets for keys
    Myset::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
    << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

Zwraca **`const`** iterator, który odnosi się do pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

**`const`** Iterator dostępu do przodu, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu `cbegin() == cend()` ).

### <a name="remarks"></a>Uwagi

Z wartością zwracaną `cbegin` nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast `begin()` funkcji składowej, aby zagwarantować, że wartość zwracana to `const_iterator` . Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy, `Container` że jest to modyfikowalny **`const`** kontener dowolnego rodzaju, który obsługuje `begin()` i `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 isContainer<T>::iterator
auto i2 = Container.cbegin();

// i2 isContainer<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> cend

Zwraca **`const`** iterator, który odnosi się do lokalizacji jedynie poza ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

**`const`** Iterator dostępu do przodu, który wskazuje tuż poza końcem zakresu.

### <a name="remarks"></a>Uwagi

`cend` służy do sprawdzania, czy iterator przeszedł koniec zakresu.

Można użyć tej funkcji elementu członkowskiego zamiast `end()` funkcji składowej, aby zagwarantować, że wartość zwracana to `const_iterator` . Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy, `Container` że jest to modyfikowalny **`const`** kontener dowolnego rodzaju, który obsługuje `end()` i `cend()` .

```cpp
auto i1 = Container.end();
// i1 isContainer<T>::iterator
auto i2 = Container.cend();

// i2 isContainer<T>::const_iterator
```

Nie można usunąć odwołania do wartości zwracanej przez nie `cend` .

## <a name="clear"></a><a name="clear"></a> Wyczyść

Usuwa wszystkie elementy.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [unordered_set:: Erase](#erase) `(` [unordered_set:: BEGIN](#begin) `(),` [unordered_set:: end](#end) `())` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_clear.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
size == 0
empty() == true
[e] [d]
size == 2
empty() == false
```

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

Typ iteratora stałego dla kontrolowanej sekwencji.

```cpp
typedef T1 const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może działać jako ciągły iterator do przodu dla kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla typu zdefiniowanego przez implementację `T1` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_const_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
    std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="const_local_iterator"></a><a name="const_local_iterator"></a> const_local_iterator

Typ iteratora stałego przedziału dla kontrolowanej sekwencji.

```cpp
typedef T5 const_local_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć ciągły iterator do przodu dla przedziału. Jest on opisany tutaj jako synonim dla typu zdefiniowanego przez implementację `T5` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_const_local_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a]
```

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

Typ stałego wskaźnika do elementu.

```cpp
typedef Alloc::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć jako stały wskaźnik do elementu kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_const_pointer.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::const_pointer p = &*it;
        std::cout << "[" << *p << "] ";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

Typ stałego odwołania do elementu.

```cpp
typedef Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może stanowić stałe odwołanie do elementu kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_const_reference.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::const_reference ref = *it;
        std::cout << "[" << ref << "] ";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="contains"></a><a name="contains"></a> wyświetlana

Sprawdza, czy istnieje element z określonym kluczem w `unordered_set` .

```cpp
bool contains(const Key& key) const;
template<class K> bool contains(const K& key) const;
```

### <a name="parameters"></a>Parametry

*K*\
Typ klucza.

*głównych*\
Wartość klucza elementu do wyszukania.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli element znajduje się w kontenerze; `false` w przeciwnym razie.

### <a name="remarks"></a>Uwagi

`contains()` Nowość w języku C++ 20. Aby go użyć, określ [/std: c + + Najnowsza](../build/reference/std-specify-language-standard-version.md) opcja kompilatora.

`template<class K> bool contains(const K& key) const` występuje tylko w przypadku, gdy `key_compare` jest przezroczysty.

### <a name="example"></a>Przykład

```cpp
// Requires /std:c++latest
#include <unordered_set>
#include <iostream>

int main()
{
    std::unordered_set<int> theUnorderedSet = { 1, 2 };

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << theUnorderedSet.contains(2) << '\n';
    std::cout << theUnorderedSet.contains(3) << '\n';
    
    return 0;
}
```

```Output
true
false
```

## <a name="count"></a><a name="count"></a> liczbą

Wyszukuje liczbę elementów pasujących do określonego klucza.

```cpp
size_type count(const Key& keyval) const;
```

### <a name="parameters"></a>Parametry

*keyval*\
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę elementów w zakresie rozdzielonym przez [unordered_set:: equal_range](#equal_range) `(keyval)` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
count('A') == 0
count('b') == 1
count('C') == 0
```

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

Typ odległości ze znakiem między dwoma elementami.

```cpp
typedef T3 difference_type;
```

### <a name="remarks"></a>Uwagi

Typ Liczba całkowita ze znakiem opisuje obiekt, który może reprezentować różnicę między adresami wszystkich dwóch elementów w kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla typu zdefiniowanego przez implementację `T3` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_difference_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // compute positive difference
    Myset::difference_type diff = 0;
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference
    diff = 0;
    for (Myset::const_iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
end()-begin() == 3
begin()-end() == -3
```

## <a name="emplace"></a><a name="emplace"></a> emplace

Wstawia element skonstruowany w miejscu (nie są wykonywane żadne operacje kopiowania ani przenoszenia).

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
Args&&... args);
```

### <a name="parameters"></a>Parametry

*argumentów*\
Argumenty przekazywane do konstruowania elementu, który ma zostać wstawiony do unordered_set, chyba że zawiera już element, którego wartość jest uporządkowana równorzędnie.

### <a name="return-value"></a>Wartość zwracana

`pair`Którego **`bool`** składnik zwraca wartość true, jeśli wstawiono, i wartość false `unordered_set` , jeśli już zawiera element, którego klucz ma odpowiednik wartości w kolejności, a Składnik iteratora zwraca adres, w którym został wstawiony nowy element lub w którym znajduje się już element.

Aby uzyskać dostęp do składnika iteratora pary `pr` zwracanej przez tę funkcję elementu członkowskiego, użyj `pr.first` , i aby usunąć odwołanie do niego, użyj `*(pr.first)` . Aby uzyskać dostęp do **`bool`** składnika pary `pr` zwracanej przez tę funkcję elementu członkowskiego, użyj `pr.second` .

### <a name="remarks"></a>Uwagi

Ta funkcja nie unieważnia iteratorów ani odwołań.

Podczas wstawiania, jeśli wyjątek jest zgłaszany, ale nie występuje w funkcji skrótu kontenera, kontener nie jest modyfikowany. Jeśli wyjątek jest zgłaszany w funkcji skrótu, wynik jest niezdefiniowany.

Aby zapoznać się z przykładem kodu, zobacz [set:: emplace](../standard-library/set-class.md#emplace).

## <a name="emplace_hint"></a><a name="emplace_hint"></a> emplace_hint

Wstawia element skonstruowany w miejscu (nie są wykonywane żadne operacje kopiowania ani przenoszenia) z wskazówką dotyczącą położenia.

```cpp
template <class... Args>
iterator emplace_hint(
const_iteratorwhere,
Args&&... args);
```

### <a name="parameters"></a>Parametry

*argumentów*\
Argumenty przekazywane do konstruowania elementu, który ma zostać wstawiony do unordered_set, chyba że unordered_set już zawiera ten element lub, bardziej ogólnie, chyba że zawiera już element, którego klucz jest równoważny uporządkowanie.

*miejscu*\
Wskazówka dotycząca miejsca, w którym rozpoczyna się wyszukiwanie poprawnego punktu wstawiania.

### <a name="return-value"></a>Wartość zwracana

Iterator do nowo wstawionego elementu.

Jeśli wstawianie nie powiodło się, ponieważ element już istnieje, zwraca iterator do istniejącego elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie unieważnia iteratorów ani odwołań.

Podczas wstawiania, jeśli wyjątek jest zgłaszany, ale nie występuje w funkcji skrótu kontenera, kontener nie jest modyfikowany. Jeśli wyjątek jest zgłaszany w funkcji skrótu, wynik jest niezdefiniowany.

Aby zapoznać się z przykładem kodu, zobacz [set:: emplace_hint](../standard-library/set-class.md#emplace_hint).

## <a name="empty"></a><a name="empty"></a> ciągiem

Sprawdza, czy nie ma żadnych elementów.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość true dla pustej kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_empty.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
size == 0
empty() == true
[e] [d]
size == 2
empty() == false
```

## <a name="end"></a><a name="end"></a> punktów

Określa koniec kontrolowanej sekwencji.

```cpp
iterator end();

const_iterator end() const;

local_iterator end(size_type nbucket);

const_local_iterator end(size_type nbucket) const;
```

### <a name="parameters"></a>Parametry

*nbucket*\
Numer zasobnika.

### <a name="remarks"></a>Uwagi

Pierwsze dwie funkcje członkowskie zwracają iterator do przodu, który wskazuje tuż poza końcem sekwencji. Ostatnie dwie funkcje członkowskie zwracają iterator do przodu, który wskazuje tuż poza końcem zasobnika *nbucket*.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_end.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect last two items "[a] [b] "
    Myset::iterator it2 = c1.end();
    --it2;
    std::cout << "[" << *it2 << "] ";
    --it2;
    std::cout << "[" << *it2 << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.end(c1.bucket('a'));
    --lit;
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a] [b]
[a]
```

## <a name="equal_range"></a><a name="equal_range"></a> equal_range

Wyszukuje zakres, który odpowiada określonemu kluczowi.

```cpp
std::pair<iterator, iterator>
equal_range(const Key& keyval);

std::pair<const_iterator, const_iterator>
equal_range(const Key& keyval) const;
```

### <a name="parameters"></a>Parametry

*keyval*\
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca parę iteratorów `X` , które `[X.first, X.second)` ograniczają tylko te elementy kontrolowanej sekwencji, które mają równoważne porządkowanie z *keyval*. Jeśli takie elementy nie istnieją, oba Iteratory są `end()` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_equal_range.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // display results of failed search
    std::pair<Myset::iterator, Myset::iterator> pair1 =
    c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << "[" << *pair1.first << "] ";
    std::cout << std::endl;

    // display results of successful search
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << "[" << *pair1.first << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
equal_range('x'):
equal_range('b'): [b]
```

## <a name="erase"></a><a name="erase"></a> Wyłączanie

Usuwa element lub zakres elementów w unordered_set z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.

```cpp
iterator erase(const_iterator Where);

iterator erase(const_iterator First, const_iterator Last);

size_type erase(const key_type& Key);
```

### <a name="parameters"></a>Parametry

*Miejscu*\
Pozycja elementu, który ma zostać usunięty.

*Pierwszego*\
Pozycja pierwszego elementu, który ma zostać usunięty.

*Ostatniego*\
Umieść tuż poza ostatnim elementem, który ma zostać usunięty.

*Głównych*\
Wartość klucza elementów do usunięcia.

### <a name="return-value"></a>Wartość zwracana

W przypadku pierwszych dwóch funkcji składowych iterator dwukierunkowy, który wyznacza pierwszy element, który jest poza wszystkimi elementami usuniętymi lub element, który jest końcem unordered_set, jeśli taki element nie istnieje.

Dla trzeciej funkcji składowej zwraca liczbę elementów usuniętych z unordered_set.

### <a name="remarks"></a>Uwagi

Aby zapoznać się z przykładem kodu, zobacz [set:: Erase](../standard-library/set-class.md#erase).

## <a name="find"></a><a name="find"></a> wyświetlić

Wyszukuje element, który odpowiada określonemu kluczowi.

```cpp
const_iterator find(const Key& keyval) const;
```

### <a name="parameters"></a>Parametry

*keyval*\
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [unordered_set:: equal_range](#equal_range) `(keyval).first` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_find.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // try to find and fail
    std::cout << "find('A') == "
    << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed
    Myset::iterator it = c1.find('b');
    std::cout << "find('b') == "
    << std::boolalpha << (it != c1.end())
    << ": [" << *it << "] " << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
find('A') == false
find('b') == true: [b]
```

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

Pobiera przechowywany obiekt alokatora.

```cpp
Alloc get_allocator() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca przechowywany obiekt alokatora.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_get_allocator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Myset c1;

    Myset::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
    << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="hash_function"></a><a name="hash"></a> hash_function

Pobiera przechowywany obiekt funkcji mieszania.

```cpp
Hash hash_function() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca przechowywany obiekt funkcji skrótu.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_hash_function.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="hasher"></a><a name="hasher"></a> programu tworzącego skróty

Typ funkcji mieszania.

```cpp
typedef Hash hasher;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Hash` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_hasher.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="insert"></a><a name="insert"></a> wstawienia

Wstawia element lub zakres elementów do unordered_set.

```cpp
// (1) single element
pair<iterator, bool> insert(const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool> insert(ValTy&& Val);

// (3) single element with hint
iterator insert(const_iterator Where, const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(const_iterator Where, ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(InputIterator First, InputIterator Last);

// (6) initializer list
void insert(initializer_list<value_type> IList);
```

### <a name="parameters"></a>Parametry

*Użyte*\
Wartość elementu, który ma zostać wstawiony do unordered_set, chyba że zawiera już element, którego klucz jest uporządkowany równorzędnie.

*Miejscu*\
Miejsce, w którym rozpocznie się wyszukiwanie poprawnego punktu wstawiania.

*ValTy*\
Parametr szablonu, który określa typ argumentu, który unordered_set może używać do konstruowania elementu [value_type](../standard-library/map-class.md#value_type)i idealny do przesyłania *dalej jako argumentu* .

*Pierwszego*\
Pozycja pierwszego elementu, który ma zostać skopiowany.

*Ostatniego*\
Pozycja tuż poza ostatnim elementem, który ma zostać skopiowany.

*InputIterator*\
Argument funkcji szablonu, który spełnia wymagania [iteratora danych wejściowych](../standard-library/input-iterator-tag-struct.md) , który wskazuje elementy typu, które mogą być używane do konstruowania obiektów [value_type](../standard-library/map-class.md#value_type) .

*IList*\
[Initializer_list](../standard-library/initializer-list.md) , z którego mają zostać skopiowane elementy.

### <a name="return-value"></a>Wartość zwracana

Jednoelementowe funkcje składowe, (1) i (2) zwracają [parę](../standard-library/pair-structure.md) , których **`bool`** składnik ma wartość true, jeśli wykonano wstawienie, i wartość false, jeśli unordered_set już zawiera element, którego klucz ma odpowiednik wartości w kolejności. Składnik iteratora pary zwracanych wartości wskazuje nowo wstawiony element **`bool`** , jeśli składnik ma wartość true lub do istniejącego elementu, jeśli **`bool`** składnik ma wartość false.

Funkcje członkowskie jednoelementowe z wskazówką, (3) i (4) zwracają iterator, który wskazuje na miejsce, w którym nowy element został wstawiony do unordered_set lub, jeśli element z równoważnym kluczem już istnieje, do istniejącego elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie unieważnia iteratorów, wskaźników ani odwołań.

Podczas wstawiania tylko jednego elementu, jeśli wyjątek jest zgłaszany, ale nie występuje w funkcji skrótu kontenera, stan kontenera nie jest modyfikowany. Jeśli wyjątek jest zgłaszany w funkcji skrótu, wynik jest niezdefiniowany. Podczas wstawiania wielu elementów, jeśli wyjątek jest zgłaszany, kontener pozostaje w nieokreślonym, ale prawidłowym stanie.

Aby uzyskać dostęp do składnika iteratora `pair` `pr` , który jest zwracany przez jednoelementowe funkcje członkowskie, użyj `pr.first` ;, aby usunąć odwołanie do iteratora w zwróconej parze, użyj `*pr.first` , dając Ci element. Aby uzyskać dostęp do **`bool`** składnika, użyj `pr.second` . Aby zapoznać się z przykładem, zobacz przykładowy kod w dalszej części tego artykułu.

[Value_type](../standard-library/map-class.md#value_type) kontenera jest elementem TypeDef, który należy do kontenera, a dla zestawu, `unordered_set<V>::value_type` jest typ `const V` .

Funkcja elementu członkowskiego zakresu (5) wstawia sekwencję wartości elementów do unordered_set, która odnosi się do każdego elementu, którego dotyczy iterator w zakresie `[First, Last)` ; w związku z tym *ostatni* nie zostanie wstawiony. Funkcja elementu członkowskiego kontenera `end()` odwołuje się do pozycji tuż po ostatnim elemencie w kontenerze — na przykład, instrukcja `s.insert(v.begin(), v.end());` próbuje wstawić wszystkie elementy `v` do `s` . Wstawiane są tylko elementy, które mają unikatowe wartości z zakresu; duplikaty zostały zignorowane. Aby sprawdzić, które elementy są odrzucane, użyj jednoelementowych wersji programu `insert` .

Funkcja członkowska listy inicjatorów (6) używa [initializer_list](../standard-library/initializer-list.md) do kopiowania elementów do unordered_set.

Do wstawienia elementu skonstruowanego w miejscu — to znaczy, że nie są wykonywane żadne operacje kopiowania ani przenoszenia — zobacz [set:: emplace](../standard-library/set-class.md#emplace) i [set:: emplace_hint](../standard-library/set-class.md#emplace_hint).

Aby zapoznać się z przykładem kodu, zobacz [set:: INSERT](../standard-library/set-class.md#insert).

## <a name="iterator"></a><a name="iterator"></a> Iterator

Typ, który zapewnia ciągły [iterator do przodu](../standard-library/forward-iterator-tag-struct.md) , który może odczytywać elementy w unordered_set.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Przykład

Zapoznaj się z przykładem początku, aby zapoznać [się](../standard-library/set-class.md#begin) z przykładem sposobu deklarowania**iteratora**i korzystania z niego.

## <a name="key_eq"></a><a name="key_eq"></a> key_eq

Pobiera przechowywany obiekt funkcji porównywania.

```cpp
Pred key_eq() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca przechowywany obiekt funkcji porównywania.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_key_eq.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
    << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
    << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
}
```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="key_equal"></a><a name="key_equal"></a> key_equal

Typ funkcji porównywania.

```cpp
typedef Pred key_equal;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Pred` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_key_equal.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
    << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
    << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
}
```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="key_type"></a><a name="key_type"></a> key_type

Typ klucza sortowania.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Key` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_key_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // add a value and reinspect
    Myset::key_type key = 'd';
    Myset::value_type val = key;
    c1.insert(val);

    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[d] [c] [b] [a]
```

## <a name="load_factor"></a><a name="load_factor"></a> load_factor

Oblicza średnią liczbę elementów na przedział.

```cpp
float load_factor() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `(float)` [unordered_set:: size](#size) `() / (float)` [unordered_set:: bucket_count](#bucket_count) `()` , średnią liczbę elementów na przedział.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_load_factor.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="local_iterator"></a><a name="local_iterator"></a> local_iterator

Typ iteratora zasobnika.

```cpp
typedef T4 local_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć iterator do przodu dla przedziału. Jest on opisany tutaj jako synonim dla typu zdefiniowanego przez implementację `T4` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_local_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a]
```

## <a name="max_bucket_count"></a><a name="max_bucket_count"></a> max_bucket_count

Pobiera maksymalną liczbę przedziałów.

```cpp
size_type max_bucket_count() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca maksymalną dozwoloną liczbę zasobników.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_max_bucket_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="max_load_factor"></a><a name="max_load_factor"></a> max_load_factor

Pobiera lub ustawia maksymalną liczbę elementów na przedział.

```cpp
float max_load_factor() const;

void max_load_factor(float factor);
```

### <a name="parameters"></a>Parametry

*1U*\
Nowy maksymalny współczynnik obciążenia.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca przechowywany maksymalny współczynnik obciążenia. Druga funkcja członkowska zastępuje zachowaną wartość maksymalnego obciążenia *czynnikem*.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_max_load_factor.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="max_size"></a><a name="max_size"></a> max_size

Pobiera maksymalny rozmiar kontrolowanej sekwencji.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca długość najdłuższej sekwencji, którą obiekt może kontrolować.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_max_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    std::cout << "max_size() == " << c1.max_size() << std::endl;

    return (0);
}
```

```Output
max_size() == 4294967295
```

## <a name="operator"></a><a name="op_eq"></a> operator =

Kopiuje tabelę mieszania.

```cpp
unordered_set& operator=(const unordered_set& right);

unordered_set& operator=(unordered_set&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Unordered_set](../standard-library/unordered-set-class.md) kopiowana do programu `unordered_set` .

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkich istniejących elementów w programie `unordered_set` , `operator=` kopiuje lub przenosi zawartość *bezpośrednio* do `unordered_set` .

### <a name="example"></a>Przykład

```cpp
// unordered_set_operator_as.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

int main( )
{
    using namespace std;
    unordered_set<int> v1, v2, v3;
    unordered_set<int>::iterator iter;

    v1.insert(10);

    cout << "v1 = " ;
    for (iter = v1.begin(); iter != v1.end(); iter++)
        cout << *iter << " ";
    cout << endl;

    v2 = v1;
    cout << "v2 = ";
    for (iter = v2.begin(); iter != v2.end(); iter++)
        cout << *iter << " ";
    cout << endl;

    // move v1 into v2
    v2.clear();
    v2 = move(v1);
    cout << "v2 = ";
    for (iter = v2.begin(); iter != v2.end(); iter++)
        cout << *iter << " ";
    cout << endl;
}
```

## <a name="pointer"></a><a name="pointer"></a> przytrzymaj

Typ wskaźnika do elementu.

```cpp
typedef Alloc::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć jako wskaźnik do elementu kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_pointer.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::key_type key = *it;
        Myset::pointer p = &key;
        std::cout << "[" << *p << "] ";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="reference"></a><a name="reference"></a> odwoła

Typ odwołania do elementu.

```cpp
typedef Alloc::reference reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć jako odwołanie do elementu kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_reference.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::key_type key = *it;
        Myset::reference ref = key;
        std::cout << "[" << ref << "] ";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="rehash"></a><a name="rehash"></a> rehash —

Przebudowuje tabelę mieszania.

```cpp
void rehash(size_type nbuckets);
```

### <a name="parameters"></a>Parametry

*nbuckets*\
Żądana liczba zasobników.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zmienia liczbę przedziałów na co najmniej *nbuckets* i ponownie kompiluje tabelę skrótów zgodnie z wymaganiami.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_rehash.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_load_factor() == 0.1
```

## <a name="size"></a><a name="size"></a> zmienia

Liczy liczbę elementów.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca długość kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
size == 0
empty() == true

[e] [d]
size == 2
empty() == false
```

## <a name="size_type"></a><a name="size_type"></a> size_type

Typ odległości bez znaku między dwoma elementami.

```cpp
typedef T2 size_type;
```

### <a name="remarks"></a>Uwagi

Typ liczby całkowitej bez znaku opisuje obiekt, który może reprezentować długość dowolnej kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla typu zdefiniowanego przez implementację `T2` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_size_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;
    Myset::size_type sz = c1.size();

    std::cout << "size == " << sz << std::endl;

    return (0);
}
```

```Output
size == 0
```

## <a name="swap"></a><a name="swap"></a> wymiany

Zamienia zawartości dwóch kontenerów.

```cpp
void swap(unordered_set& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Kontener, w którym ma zostać zamieniony.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia kontrolowane sekwencje między **`*this`** i *po prawej*. Jeśli [unordered_set:: get_allocator](#get_allocator) `() == right.get_allocator()` , robi to w stałym czasie, zgłasza wyjątek tylko w wyniku kopiowania obiektu składowanych cech typu `Tr` i unieważnia odwołania, wskaźniki lub Iteratory, które wyznaczają elementy w dwóch kontrolowanej sekwencji. W przeciwnym razie wykonuje wiele przypisań elementów i wywołań konstruktora proporcjonalnie do liczby elementów w dwóch kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_swap.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    Myset c2;

    c2.insert('d');
    c2.insert('e');
    c2.insert('f');

    c1.swap(c2);

    // display contents "[f] [e] [d] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    swap(c1, c2);

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[f] [e] [d]
[c] [b] [a]
```

## <a name="unordered_set"></a><a name="unordered_set"></a> unordered_set

Konstruuje obiekt kontenera.

```cpp
unordered_set(const unordered_set& Right);

explicit unordered_set(
    size_typebucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());

unordered_set(unordered_set&& Right);

unordered_set(initializer_list<Type> IList);

unordered_set(initializer_list<Type> IList, size_typebucket_count);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash,
    const Comp& Comp);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash,
    const Comp& Comp,
    const Allocator& Al);

template <class InputIterator>
unordered_set(
    InputIteratorfirst,
    InputIteratorlast,
    size_typebucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());
```

### <a name="parameters"></a>Parametry

*InputIterator*\
Typ iteratora.

*Wsp*\
Obiekt alokatora, który ma być przechowywany.

*Przepisów*\
Obiekt funkcji porównywania, który ma być przechowywany.

*Skrótu*\
Obiekt funkcji mieszania, który ma być przechowywany.

*bucket_count*\
Minimalna liczba przedziałów.

*Kliknij*\
Kontener, który ma być skopiowany.

*IList*\
Lista initializer_list zawierająca elementy do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor określa kopię sekwencji kontrolowanej przez *prawo*. Drugi konstruktor określa pustą kontrolowaną sekwencję. Trzeci konstruktor określa kopię sekwencji, przenosząc *ją w prawo* czwarty za pomocą ósmego konstruktorów, użyj initializer_list, aby określić elementy do skopiowania. Dziewiąty Konstruktor wstawia sekwencję wartości elementów `[first, last)` .

Wszystkie konstruktory również inicjują kilka przechowywanych wartości. W przypadku konstruktora kopiującego wartości są uzyskiwane z *prawej strony*. W przeciwnym razie:

Minimalna liczba przedziałów jest argumentem *bucket_count*, jeśli istnieje; w przeciwnym razie jest to wartość domyślna opisana tutaj jako wartość zdefiniowana przez implementację `N0` .

Obiekt funkcji mieszania jest *wartością skrótu*argumentu (jeśli istnieje); w przeciwnym razie `Hash()` .

Obiekt funkcji porównywania jest argumentem *COMP*, jeśli jest obecny; w przeciwnym razie `Comp()` .

Obiekt alokatora jest argumentem *Al*, jeśli jest obecny; w przeciwnym razie `Alloc()` .

## <a name="value_type"></a><a name="value_type"></a> value_type

Typ elementu.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje element kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_set__unordered_set_value_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // add a value and reinspect
    Myset::key_type key = 'd';
    Myset::value_type val = key;
    c1.insert(val);

    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[d] [c] [b] [a]
```
