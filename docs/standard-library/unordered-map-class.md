---
title: unordered_map — Klasa
description: Dokumentacja interfejsu API dla klasy kontenera standardowej biblioteki języka C++ `unordered_map` , która kontroluje różnej długości sekwencji elementów.
ms.date: 9/9/2020
f1_keywords:
- unordered_map/std::unordered_map
- unordered_map/std::unordered_map::allocator_type
- unordered_map/std::unordered_map::const_iterator
- unordered_map/std::unordered_map::const_local_iterator
- unordered_map/std::unordered_map::const_pointer
- unordered_map/std::unordered_map::const_reference
- unordered_map/std::unordered_map::difference_type
- unordered_map/std::unordered_map::hasher
- unordered_map/std::unordered_map::iterator
- unordered_map/std::unordered_map::key_equal
- unordered_map/std::unordered_map::key_type
- unordered_map/std::unordered_map::local_iterator
- unordered_map/std::unordered_map::mapped_type
- unordered_map/std::unordered_map::pointer
- unordered_map/std::unordered_map::reference
- unordered_map/std::unordered_map::size_type
- unordered_map/std::unordered_map::value_type
- unordered_map/std::unordered_map::at
- unordered_map/std::unordered_map::begin
- unordered_map/std::unordered_map::bucket
- unordered_map/std::unordered_map::bucket_count
- unordered_map/std::unordered_map::bucket_size
- unordered_map/std::unordered_map::cbegin
- unordered_map/std::unordered_map::cend
- unordered_map/std::unordered_map::clear
- unordered_map/std::unordered_map::contains
- unordered_map/std::unordered_map::count
- unordered_map/std::unordered_map::emplace
- unordered_map/std::unordered_map::emplace_hint
- unordered_map/std::unordered_map::empty
- unordered_map/std::unordered_map::end
- unordered_map/std::unordered_map::equal_range
- unordered_map/std::unordered_map::erase
- unordered_map/std::unordered_map::find
- unordered_map/std::unordered_map::get_allocator
- unordered_map/std::unordered_map::hash
- unordered_map/std::unordered_map::insert
- unordered_map/std::unordered_map::key_eq
- unordered_map/std::unordered_map::load_factor
- unordered_map/std::unordered_map::max_bucket_count
- unordered_map/std::unordered_map::max_load_factor
- unordered_map/std::unordered_map::max_size
- unordered_map/std::unordered_map::rehash
- unordered_map/std::unordered_map::size
- unordered_map/std::unordered_map::swap
- unordered_map/std::unordered_map::unordered_map
- unordered_map/std::unordered_map::hash_function
helpviewer_keywords:
- std::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::contains
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
- std::unordered_map::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash_function
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
ms.assetid: 7cf7cfa1-16e7-461c-a9b2-3b8d8ec24e0d
ms.openlocfilehash: 2f30b5683d8487830d596fc8185430c8a4c4c7b0
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352417"
---
# <a name="unordered_map-class"></a>unordered_map — Klasa

Szablon klasy opisuje obiekt, który kontroluje różnej długości sekwencje elementów typu `std::pair<const Key, Ty>` . Sekwencja jest słabo uporządkowana według funkcji mieszania, która dzieli sekwencję na uporządkowany zestaw podsekwencji, zwanych przedziałami, segmentami lub pakietami. W ramach każdego przedziału funkcja porównania określa, czy jakaś para elementów ma równoważną kolejność. Każdy element przechowuje dwa obiekty, klucz sortowania i wartość. Sekwencja jest reprezentowana w sposób, który pozwala na wyszukiwanie, wstawianie i usuwanie dowolnego elementu z wielu operacji, które mogą być niezależne od liczby elementów w sekwencji (stały czas), co najmniej kiedy wszystkie przedziały są w przybliżeniu jednakowej długości. W najgorszym przypadku, gdy wszystkie elementy znajdują się w jednym przedziale, liczba operacji jest proporcjonalna do liczby elementów w sekwencji (liniowy czas). Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Ty,
    class Hash = std::hash<Key>,
    class Pred = std::equal_to<Key>,
    class Alloc = std::allocator<std::pair<const Key, Ty>>>
class unordered_map;
```

### <a name="parameters"></a>Parametry

*Głównych*\
Typ klucza.

*Br*\
Typ mapowany.

*Skrótu*\
Typ obiektu funkcji mieszania.

*Pred*\
Typ obiektu funkcji porównywania równości.

*Alokacj*\
Klasa alokatora.

## <a name="members"></a>Elementy członkowskie

|Definicja typu|Opis|
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
|[mapped_type](#mapped_type)|Typ mapowanej wartości skojarzonej z poszczególnymi kluczami.|
|[pointer](#pointer)|Typ wskaźnika do elementu.|
|[odwoła](#reference)|Typ odwołania do elementu.|
|[size_type](#size_type)|Typ odległości bez znaku między dwoma elementami.|
|[value_type](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|-|-|
|[w](#at)|Wyszukuje element z określonym kluczem.|
|[zaczną](#begin)|Określa początek kontrolowanej sekwencji.|
|[porcj](#bucket)|Pobiera numer przedziału dla wartości klucza.|
|[bucket_count](#bucket_count)|Pobiera liczbę przedziałów.|
|[bucket_size](#bucket_size)|Pobiera rozmiar przedziału.|
|[cbegin](#cbegin)|Określa początek kontrolowanej sekwencji.|
|[cend](#cend)|Określa koniec kontrolowanej sekwencji.|
|[Wyczyść](#clear)|Usuwa wszystkie elementy.|
|[liczbą](#count)|Wyszukuje liczbę elementów pasujących do określonego klucza.|
|[zawiera](#contains)<sup>c++ 20</sup>|Sprawdź, czy w. istnieje element z określonym kluczem `unordered_map` .|
|[emplace](#emplace)|Dodaje element skonstruowany na miejscu.|
|[emplace_hint](#emplace_hint)|Dodaje element skonstruowany na miejscu, z podpowiedzią.|
|[puste](#empty)|Sprawdza, czy nie ma żadnych elementów.|
|[punktów](#end)|Określa koniec kontrolowanej sekwencji.|
|[equal_range](#equal_range)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|
|[Wyłączanie](#erase)|Usuwa elementy z określonych pozycji.|
|[wyświetlić](#find)|Wyszukuje element, który odpowiada określonemu kluczowi.|
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
|[unordered_map](#unordered_map)|Konstruuje obiekt kontenera.|

|Operator|Opis|
|-|-|
|[unordered_map:: operator []](#op_at)|Znajduje lub wstawia element z określonym kluczem.|
|[unordered_map:: operator =](#op_eq)|Kopiuje tabelę mieszania.|

## <a name="remarks"></a>Uwagi

Obiekt porządkuje sekwencję, która kontroluje, wywołując dwa przechowywane obiekty, obiekt funkcji porównania typu [unordered_map:: key_equal](#key_equal) i obiektu funkcji hash typu [unordered_map:: Hasher](#hasher). Dostęp do pierwszego przechowywanego obiektu można uzyskać, wywołując funkcję członkowską [unordered_map:: key_eq](#key_eq) `()` ; i uzyskując dostęp do drugiego przechowywanego obiektu przez wywołanie funkcji składowej [unordered_map:: hash_function](#hash) `()` . W odniesieniu do wszystkich wartości `X` i `Y` typu `Key` , wywołanie `key_eq()(X, Y)` zwraca wartość true tylko wtedy, gdy dwie wartości argumentu mają równoważne porządkowanie; `hash_function()(keyval)` wywołanie daje rozkład wartości typu `size_t` . W odróżnieniu od szablonu klasy [Unordered_multimap Klasa](../standard-library/unordered-multimap-class.md), obiekt typu `unordered_map` gwarantuje, że `key_eq()(X, Y)` zawsze ma wartość false dla każdego z dwóch elementów kontrolowanej sekwencji. (Klucze są unikatowe).

Obiekt przechowuje również współczynnik maksymalnego obciążenia, który określa maksymalną żądaną średnią liczbę elementów na przedział. Jeśli wstawianie elementu powoduje, że [unordered_map:: load_factor](#load_factor) `()` do przekroczenia maksymalnego współczynnika obciążenia, kontener zwiększa liczbę zasobników i ponownie kompiluje tabelę skrótów zgodnie z wymaganiami.

Rzeczywista kolejność elementów w kontrolowanej sekwencji zależy od funkcji mieszania, funkcji porównywania, kolejności wstawiania, współczynnika maksymalnego obciążenia i bieżącej liczby przedziałów. Na ogół nie można przewidzieć kolejności elementów w kontrolowanej sekwencji. Można jednak zawsze mieć pewność, że dowolny podzbiór elementów, które mają równoważną kolejność, są obok siebie w kontrolowanej sekwencji.

Obiekt przydziela i zwalnia magazyn dla sekwencji, która kontroluje przez przechowywany obiekt alokatora typu [unordered_map:: allocator_type](#allocator_type). Taki obiekt alokatora musi mieć ten sam interfejs zewnętrzny co obiekt typu `allocator` . Należy zauważyć, że przechowywany obiekt alokatora nie jest kopiowany po przypisaniu obiektu kontenera.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<unordered_map>

**Przestrzeń nazw:** std

## <a name="unordered_mapallocator_type"></a><a name="allocator_type"></a> unordered_map:: allocator_type

Typ alokatora do zarządzania pamięcią.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Alloc` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_allocator_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="unordered_mapat"></a><a name="at"></a> unordered_map:: at

Znajduje element w unordered_map z określoną wartością klucza.

```cpp
Ty& at(const Key& key);
const Ty& at(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza do wyszukania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do wartości danych znalezionego elementu.

### <a name="remarks"></a>Uwagi

Jeśli wartość klucza argumentu nie zostanie znaleziona, funkcja zgłasza obiekt klasy `out_of_range` .

### <a name="example"></a>Przykład

```cpp
// unordered_map_at.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // find and show elements
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;

    return (0);
}
```

## <a name="unordered_mapbegin"></a><a name="begin"></a> unordered_map:: BEGIN

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
// std__unordered_map__unordered_map_begin.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

#typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect first two items " [c 3] [b 2]"
    Mymap::iterator it2 = c1.begin();
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    ++it2;
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[c, 3] [b, 2]
[a, 1]
```

## <a name="unordered_mapbucket"></a><a name="bucket"></a> unordered_map:: zasobnik

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
// std__unordered_map__unordered_map_bucket.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="unordered_mapbucket_count"></a><a name="bucket_count"></a> unordered_map:: bucket_count

Pobiera liczbę przedziałów.

```cpp
size_type bucket_count() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca bieżącą liczbę zasobników.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_bucket_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
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
[c, 3][b, 2][a, 1]
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

## <a name="unordered_mapbucket_size"></a><a name="bucket_size"></a> unordered_map:: bucket_size

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
// std__unordered_map__unordered_map_bucket_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="unordered_mapcbegin"></a><a name="cbegin"></a> unordered_map:: cbegin

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
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="unordered_mapcend"></a><a name="cend"></a> unordered_map:: cend

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
// i1 is Container<T>::iterator
auto i2 = Container.cend();
// i2 is Container<T>::const_iterator
```

Nie można usunąć odwołania do wartości zwracanej przez `cend` .

## <a name="unordered_mapclear"></a><a name="clear"></a> unordered_map:: Clear

Usuwa wszystkie elementy.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [unordered_map:: Erase](#erase) `(` [unordered_map:: BEGIN](#begin) `(),` [unordered_map:: end](#end) `())` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_clear.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapconst_iterator"></a><a name="const_iterator"></a> unordered_map:: const_iterator

Typ iteratora stałego dla kontrolowanej sekwencji.

```cpp
typedef T1 const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może działać jako ciągły iterator do przodu dla kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla typu zdefiniowanego przez implementację `T1` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_const_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapconst_local_iterator"></a><a name="const_local_iterator"></a> unordered_map:: const_local_iterator

Typ iteratora stałego przedziału dla kontrolowanej sekwencji.

```cpp
typedef T5 const_local_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć ciągły iterator do przodu dla przedziału. Jest on opisany tutaj jako synonim dla typu zdefiniowanego przez implementację `T5` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_const_local_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[a, 1]
```

## <a name="unordered_mapconst_pointer"></a><a name="const_pointer"></a> unordered_map:: const_pointer

Typ stałego wskaźnika do elementu.

```cpp
typedef Alloc::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć jako stały wskaźnik do elementu kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_const_pointer.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapconst_reference"></a><a name="const_reference"></a> unordered_map:: const_reference

Typ stałego odwołania do elementu.

```cpp
typedef Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może stanowić stałe odwołanie do elementu kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_const_reference.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapcontains"></a><a name="contains"></a> unordered_map:: zawiera

Sprawdza, czy istnieje element `unordered_map` z określonym kluczem.
Wprowadzono w języku C++ 20.

```cpp
bool contains(const Key& key) const;
<class K> bool contains(const K& key) const;
```

### <a name="parameters"></a>Parametry

*K*\
Typ klucza.

*głównych*\
Wartość klucza elementu, który ma zostać wyszukany.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli element znajduje się w kontenerze; `false` w przeciwnym razie. 

### <a name="remarks"></a>Uwagi

`contains()` Nowość w języku C++ 20. Aby go użyć, określ [/std: c + + Najnowsza](../build/reference/std-specify-language-standard-version.md) opcja kompilatora.

`template<class K> bool contains(const K& key) const` występuje tylko w przypadku, gdy `key_compare` jest przezroczysty.

### <a name="example"></a>Przykład

```cpp
// Requires /std:c++latest
#include <unordered_map>
#include <iostream>

int main()
{
    std::unordered_map<int, bool> theUnorderedMap = {{0, false}, {1,true}};

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << theUnorderedMap.contains(1) << '\n';
    std::cout << theUnorderedMap.contains(2) << '\n';
    
    return 0;
}
```

```Output
true
false
```

## <a name="unordered_mapcount"></a><a name="count"></a> unordered_map:: Count

Wyszukuje liczbę elementów pasujących do określonego klucza.

```cpp
size_type count(const Key& keyval) const;
```

### <a name="parameters"></a>Parametry

*keyval*\
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę elementów w zakresie rozdzielonym przez [unordered_map:: equal_range](#equal_range) `(keyval)` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
count('A') == 0
count('b') == 1
count('C') == 0
```

## <a name="unordered_mapdifference_type"></a><a name="difference_type"></a> unordered_map::d ifference_type

Typ odległości ze znakiem między dwoma elementami.

```cpp
typedef T3 difference_type;
```

### <a name="remarks"></a>Uwagi

Typ Liczba całkowita ze znakiem opisuje obiekt, który może reprezentować różnicę między adresami wszystkich dwóch elementów w kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla typu zdefiniowanego przez implementację `T3` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_difference_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // compute positive difference
    Mymap::difference_type diff = 0;
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference
    diff = 0;
    for (Mymap::const_iterator it = c1.end();
        it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
end()-begin() == 3
begin()-end() == -3
```

## <a name="unordered_mapemplace"></a><a name="emplace"></a> unordered_map:: emplace

Wstawia element skonstruowany w miejscu (nie są wykonywane żadne operacje kopiowania ani przenoszenia) do unordered_map.

```cpp
template <class... Args>
pair<iterator, bool>  emplace( Args&&... args);
```

### <a name="parameters"></a>Parametry

*argumentów*\
Argumenty przekazywane do konstrukcji elementu, który ma zostać wstawiony do obiektu, `unordered_map` chyba że zawiera już element, którego wartość jest uporządkowana równorzędnie.

### <a name="return-value"></a>Wartość zwracana

`pair`Którego **`bool`** składnik zwraca wartość true, jeśli wstawiono, i wartość false `unordered_map` , jeśli już zawiera element, którego klucz ma odpowiednik wartości w kolejności, a Składnik iteratora zwraca adres, w którym został wstawiony nowy element lub w którym znajduje się już element.

Aby uzyskać dostęp do składnika iteratora pary `pr` zwracanej przez tę funkcję elementu członkowskiego, użyj `pr.first` , i aby usunąć odwołanie do niego, użyj `*(pr.first)` . Aby uzyskać dostęp do **`bool`** składnika pary `pr` zwracanej przez tę funkcję elementu członkowskiego, użyj `pr.second` .

### <a name="remarks"></a>Uwagi

Ta funkcja nie unieważnia iteratorów ani odwołań.

Podczas wstawiania, jeśli wyjątek jest zgłaszany, ale nie występuje w funkcji skrótu kontenera, kontener nie jest modyfikowany. Jeśli wyjątek jest zgłaszany w funkcji skrótu, wynik jest niezdefiniowany.

Aby uzyskać przykład kodu, zobacz [map:: emplace](../standard-library/map-class.md#emplace).

## <a name="unordered_mapemplace_hint"></a><a name="emplace_hint"></a> unordered_map:: emplace_hint

Wstawia element skonstruowany w miejscu (nie są wykonywane żadne operacje kopiowania ani przenoszenia) z wskazówką dotyczącą położenia.

```cpp
template <class... Args>
iterator emplace_hint(const_iterator where, Args&&... args);
```

### <a name="parameters"></a>Parametry

*argumentów*\
Argumenty przekazywane do konstruowania elementu, który ma zostać wstawiony do unordered_map, chyba że unordered_map już zawiera ten element lub, bardziej ogólnie, chyba że zawiera już element, którego klucz jest równoważny uporządkowanie.

*miejscu*\
Wskazówka dotycząca miejsca, w którym rozpoczyna się wyszukiwanie poprawnego punktu wstawiania.

### <a name="return-value"></a>Wartość zwracana

Iterator do nowo wstawionego elementu.

Jeśli wstawianie nie powiodło się, ponieważ element już istnieje, zwraca iterator do istniejącego elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie unieważnia żadnych odwołań.

Podczas wstawiania, jeśli wyjątek jest zgłaszany, ale nie występuje w funkcji skrótu kontenera, kontener nie jest modyfikowany. Jeśli wyjątek jest zgłaszany w funkcji skrótu, wynik jest niezdefiniowany.

[Value_type](../standard-library/map-class.md#value_type) elementu to para, dzięki czemu wartość elementu będzie przymówionej pary z pierwszym składnikiem równym wartości klucza i drugi składnik równy wartości danych elementu.

Aby uzyskać przykład kodu, zobacz [map:: emplace_hint](../standard-library/map-class.md#emplace_hint).

## <a name="unordered_mapempty"></a><a name="empty"></a> unordered_map:: Empty

Sprawdza, czy nie ma żadnych elementów.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość true dla pustej kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_empty.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapend"></a><a name="end"></a> unordered_map:: end

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

## <a name="unordered_mapequal_range"></a><a name="equal_range"></a> unordered_map:: equal_range

Wyszukuje zakres, który odpowiada określonemu kluczowi.

```cpp
std::pair<iterator, iterator>  equal_range(const Key& keyval);
std::pair<const_iterator, const_iterator>  equal_range(const Key& keyval) const;
```

### <a name="parameters"></a>Parametry

*keyval*\
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca parę iteratorów `X` , które `[X.first, X.second)` ograniczają tylko te elementy kontrolowanej sekwencji, które mają równoważne porządkowanie z *keyval*. Jeśli takie elementy nie istnieją, oba Iteratory są `end()` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_equal_range.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display results of failed search
    std::pair<Mymap::iterator, Mymap::iterator> pair1 =
        c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    // display results of successful search
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
equal_range('x'):
equal_range('b'): [b, 2]
```

## <a name="unordered_maperase"></a><a name="erase"></a> unordered_map:: Erase

Usuwa element lub zakres elementów w unordered_map z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.

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

W przypadku pierwszych dwóch funkcji składowych iterator dwukierunkowy, który wyznacza pierwszy element, który jest poza wszystkimi elementami usuniętymi lub element, który jest końcem mapy, jeśli taki element nie istnieje.

Dla trzeciej funkcji składowej zwraca liczbę elementów usuniętych z unordered_map.

### <a name="remarks"></a>Uwagi

Aby uzyskać przykład kodu, zobacz [map:: Erase](../standard-library/map-class.md#erase).

## <a name="unordered_mapfind"></a><a name="find"></a> unordered_map:: find

Wyszukuje element, który odpowiada określonemu kluczowi.

```cpp
const_iterator find(const Key& keyval) const;
```

### <a name="parameters"></a>Parametry

*keyval*\
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [unordered_map:: equal_range](#equal_range) `(keyval).first` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_find.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // try to find and fail
    std::cout << "find('A') == "
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed
    Mymap::iterator it = c1.find('b');
    std::cout << "find('b') == "
        << std::boolalpha << (it != c1.end())
        << ": [" << it->first << ", " << it->second << "]" << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
find('A') == false
find('b') == true: [b, 2]
```

## <a name="unordered_mapget_allocator"></a><a name="get_allocator"></a> unordered_map:: get_allocator

Pobiera przechowywany obiekt alokatora.

```cpp
Alloc get_allocator() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca przechowywany obiekt alokatora.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_get_allocator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="unordered_maphash_function"></a><a name="hash"></a> unordered_map:: hash_function

Pobiera przechowywany obiekt funkcji mieszania.

```cpp
Hash hash_function() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca przechowywany obiekt funkcji skrótu.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_hash_function.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="unordered_maphasher"></a><a name="hasher"></a> unordered_map:: Hasher

Typ funkcji mieszania.

```cpp
typedef Hash hasher;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Hash` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_hasher.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="unordered_mapinsert"></a><a name="insert"></a> unordered_map:: INSERT

Wstawia element lub zakres elementów do unordered_map.

```cpp
// (1) single element
pair<iterator, bool> insert(    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(    ValTy&& Val);

// (3) single element with hint
iterator insert(    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(initializer_list<value_type>
IList);
```

### <a name="parameters"></a>Parametry

*Użyte*\
Wartość elementu, który ma zostać wstawiony do unordered_map, chyba że zawiera już element, którego klucz jest uporządkowany równorzędnie.

*Miejscu*\
Miejsce, w którym rozpocznie się wyszukiwanie poprawnego punktu wstawiania.

*ValTy*\
Parametr szablonu, który określa typ argumentu, który unordered_map może używać do konstruowania elementu [value_type](../standard-library/map-class.md#value_type)i idealny do przesyłania *dalej jako argumentu* .

*Pierwszego*\
Pozycja pierwszego elementu, który ma zostać skopiowany.

*Ostatniego*\
Pozycja tuż poza ostatnim elementem, który ma zostać skopiowany.

*InputIterator*\
Argument funkcji szablonu, który spełnia wymagania [iteratora danych wejściowych](../standard-library/input-iterator-tag-struct.md) , który wskazuje elementy typu, które mogą być używane do konstruowania obiektów [value_type](../standard-library/map-class.md#value_type) .

*IList*\
[Initializer_list](../standard-library/initializer-list.md) , z którego mają zostać skopiowane elementy.

### <a name="return-value"></a>Wartość zwracana

Jednoelementowe funkcje składowe, (1) i (2) zwracają [parę](../standard-library/pair-structure.md) , których **`bool`** składnik ma wartość true, jeśli wykonano wstawienie, i wartość false, jeśli unordered_map już zawiera element, którego klucz ma odpowiednik wartości w kolejności. Składnik iteratora pary zwracanych wartości wskazuje nowo wstawiony element **`bool`** , jeśli składnik ma wartość true lub do istniejącego elementu, jeśli **`bool`** składnik ma wartość false.

Funkcje członkowskie jednoelementowe z wskazówką, (3) i (4) zwracają iterator, który wskazuje na miejsce, w którym nowy element został wstawiony do unordered_map lub, jeśli element z równoważnym kluczem już istnieje, do istniejącego elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie unieważnia iteratorów, wskaźników ani odwołań.

Podczas wstawiania tylko jednego elementu, jeśli wyjątek jest zgłaszany, ale nie występuje w funkcji skrótu kontenera, stan kontenera nie jest modyfikowany. Jeśli wyjątek jest zgłaszany w funkcji skrótu, wynik jest niezdefiniowany. Podczas wstawiania wielu elementów, jeśli wyjątek jest zgłaszany, kontener pozostaje w nieokreślonym, ale prawidłowym stanie.

Aby uzyskać dostęp do składnika iteratora `pair` `pr` , który jest zwracany przez jednoelementowe funkcje członkowskie, użyj `pr.first` ;, aby usunąć odwołanie do iteratora w zwróconej parze, użyj `*pr.first` , dając Ci element. Aby uzyskać dostęp do **`bool`** składnika, użyj `pr.second` . Aby zapoznać się z przykładem, zobacz przykładowy kod w dalszej części tego artykułu.

[Value_type](../standard-library/map-class.md#value_type) kontenera jest elementem TypeDef, który należy do kontenera, a dla mapy, `map<K, V>::value_type` to `pair<const K, V>` . Wartość elementu to uporządkowana para, w której pierwszy składnik jest równy wartości klucza, a drugi składnik jest równy wartości danych elementu.

Funkcja elementu członkowskiego zakresu (5) wstawia sekwencję wartości elementów do unordered_map, która odnosi się do każdego elementu, który jest objęty iteratorem w zakresie; w związku z tym nie zostanie `[First, Last)` `Last` wstawiony. Funkcja elementu członkowskiego kontenera `end()` odwołuje się do pozycji tuż po ostatnim elemencie w kontenerze — na przykład, instrukcja `m.insert(v.begin(), v.end());` próbuje wstawić wszystkie elementy `v` do `m` . Wstawiane są tylko elementy, które mają unikatowe wartości z zakresu; duplikaty zostały zignorowane. Aby sprawdzić, które elementy są odrzucane, użyj jednoelementowych wersji programu `insert` .

Funkcja członkowska listy inicjatorów (6) używa [initializer_list](../standard-library/initializer-list.md) do kopiowania elementów do unordered_map.

Do wstawienia elementu skonstruowanego w miejscu — to znaczy, że nie są wykonywane żadne operacje kopiowania ani przenoszenia — zobacz [unordered_map:: emplace](#emplace) i [unordered_map:: emplace_hint](#emplace_hint).

Aby uzyskać przykład kodu, zobacz [map:: INSERT](../standard-library/map-class.md#insert).

## <a name="unordered_mapiterator"></a><a name="iterator"></a> unordered_map:: iterator

Typ iteratora dla kontrolowanej sekwencji.

```cpp
typedef T0 iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć iterator do przodu dla kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla typu zdefiniowanego przez implementację `T0` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapkey_eq"></a><a name="key_eq"></a> unordered_map:: key_eq

Pobiera przechowywany obiekt funkcji porównywania.

```cpp
Pred key_eq() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca przechowywany obiekt funkcji porównywania.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_key_eq.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    Mymap::key_equal cmpfn = c1.key_eq();
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

## <a name="unordered_mapkey_equal"></a><a name="key_equal"></a> unordered_map:: key_equal

Typ funkcji porównywania.

```cpp
typedef Pred key_equal;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Pred` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_key_equal.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    Mymap::key_equal cmpfn = c1.key_eq();
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

## <a name="unordered_mapkey_type"></a><a name="key_type"></a> unordered_map:: key_type

Typ klucza sortowania.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Key` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_key_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapload_factor"></a><a name="load_factor"></a> unordered_map:: load_factor

Oblicza średnią liczbę elementów na przedział.

```cpp
float load_factor() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `(float)` [unordered_map:: size](#size) `() / (float)` [unordered_map:: bucket_count](#bucket_count) `()` , średnią liczbę elementów na przedział.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_load_factor.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
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
[c, 3] [b, 2] [a, 1]
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

## <a name="unordered_maplocal_iterator"></a><a name="local_iterator"></a> unordered_map:: local_iterator

Typ iteratora zasobnika.

```cpp
typedef T4 local_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć iterator do przodu dla przedziału. Jest on opisany tutaj jako synonim dla typu zdefiniowanego przez implementację `T4` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_local_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect bucket containing 'a'
    Mymap::local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[a, 1]
```

## <a name="unordered_mapmapped_type"></a><a name="mapped_type"></a> unordered_map:: mapped_type

Typ mapowanej wartości skojarzonej z poszczególnymi kluczami.

```cpp
typedef Ty mapped_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Ty` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_mapped_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapmax_bucket_count"></a><a name="max_bucket_count"></a> unordered_map:: max_bucket_count

Pobiera maksymalną liczbę przedziałów.

```cpp
size_type max_bucket_count() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca maksymalną dozwoloną liczbę zasobników.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_max_bucket_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
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
[c, 3] [b, 2] [a, 1]
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

## <a name="unordered_mapmax_load_factor"></a><a name="max_load_factor"></a> unordered_map:: max_load_factor

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
// std__unordered_map__unordered_map_max_load_factor.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
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
[c, 3] [b, 2] [a, 1]
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

## <a name="unordered_mapmax_size"></a><a name="max_size"></a> unordered_map:: max_size

Pobiera maksymalny rozmiar kontrolowanej sekwencji.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca długość najdłuższej sekwencji, którą obiekt może kontrolować.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_max_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    std::cout << "max_size() == " << c1.max_size() << std::endl;

    return (0);
    }
```

```Output
max_size() == 536870911
```

## <a name="unordered_mapoperator"></a><a name="op_at"></a> unordered_map:: operator []

Znajduje lub wstawia element z określonym kluczem.

```cpp
Ty& operator[](const Key& keyval);

Ty& operator[](Key&& keyval);
```

### <a name="parameters"></a>Parametry

*Keyval*\
Wartość klucza, która ma być znaleziona lub wstawiona.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do wartości danych wstawionego elementu.

### <a name="remarks"></a>Uwagi

Jeśli wartość klucza argumentu nie zostanie znaleziona, zostanie ona wstawiona wraz z wartością domyślną typu danych.

`operator[]` może służyć do wstawiania elementów do mapy *m* przy użyciu *m*[*Key*] = `DataValue` ; gdzie `DataValue` jest wartością `mapped_type` elementu z kluczową wartością *klucza*.

Podczas używania `operator[]` do wstawiania elementów, zwrócone odwołanie nie wskazuje, czy wstawienie zmienia istniejący element lub tworzy nowy. Funkcje członkowskie [Znajdź](../standard-library/map-class.md#find) i [Wstaw](../standard-library/map-class.md#insert) mogą służyć do określenia, czy element z określonym kluczem jest już obecny przed wstawieniem.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_operator_sub.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>
#include <string>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// try to find and fail
    std::cout << "c1['A'] == " << c1['A'] << std::endl;

// try to find and succeed
    std::cout << "c1['a'] == " << c1['a'] << std::endl;

// redisplay contents
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// insert by moving key
    std::unordered_map<string, int> c2;
    std::string str("abc");
    std::cout << "c2[std::move(str)] == " << c2[std::move(str)] << std::endl;
    std::cout << "c2["abc"] == " << c2["abc"] << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
c1['A'] == 0
c1['a'] == 1
[c, 3] [b, 2] [A, 0] [a, 1]
c2[move(str)] == 0
c2["abc"] == 1
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska określa iterator `where` jako wartość zwracaną [unordered_map:: INSERT](#insert) `(` [unordered_map:: value_type](#value_type) `(keyval, Ty())` . (Wstawia element z określonym kluczem, jeśli taki element nie istnieje). Następnie zwraca odwołanie do `(*where).second` .

## <a name="unordered_mapoperator"></a><a name="op_eq"></a> unordered_map:: operator =

Zastępuje elementy tego unordered_map przy użyciu elementów z innego unordered_map.

```cpp
unordered_map& operator=(const unordered_map& right);

unordered_map& operator=(unordered_map&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Unordered_map, z której funkcja operatora przypisuje zawartość.

### <a name="remarks"></a>Uwagi

Pierwsza wersja kopiuje wszystkie elementy z *prawej strony* do tej unordered_map.

Druga wersja przenosi wszystkie elementy z *prawej strony* do tej unordered_map.

Wszystkie elementy znajdujące się w tym unordered_map przed wykonaniem `operator=` zostaną odrzucone.

### <a name="example"></a>Przykład

```cpp
// unordered_map_operator_as.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

int main( )
   {
   using namespace std;
   unordered_map<int, int> v1, v2, v3;
   unordered_map<int, int>::iterator iter;

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

## <a name="unordered_mappointer"></a><a name="pointer"></a> unordered_map::p ointer

Typ wskaźnika do elementu.

```cpp
typedef Alloc::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć jako wskaźnik do elementu kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_pointer.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Mymap::pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
        }
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapreference"></a><a name="reference"></a> unordered_map:: Reference

Typ odwołania do elementu.

```cpp
typedef Alloc::reference reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć jako odwołanie do elementu kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_reference.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Mymap::reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
        }
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_maprehash"></a><a name="rehash"></a> unordered_map:: rehash

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
// std__unordered_map__unordered_map_rehash.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
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
[c, 3] [b, 2] [a, 1]
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

## <a name="unordered_mapsize"></a><a name="size"></a> unordered_map:: size

Liczy liczbę elementów.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca długość kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

// display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapsize_type"></a><a name="size_type"></a> unordered_map:: size_type

Typ odległości bez znaku między dwoma elementami.

```cpp
typedef T2 size_type;
```

### <a name="remarks"></a>Uwagi

Typ liczby całkowitej bez znaku opisuje obiekt, który może reprezentować długość dowolnej kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla typu zdefiniowanego przez implementację `T2` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_size_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::size_type sz = c1.size();

    std::cout << "size == " << sz << std::endl;

    return (0);
    }
```

```Output
size == 0
```

## <a name="unordered_mapswap"></a><a name="swap"></a> unordered_map:: swap

Zamienia zawartości dwóch kontenerów.

```cpp
void swap(unordered_map& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Kontener, w którym ma zostać zamieniony.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia kontrolowane sekwencje między **`*this`** i *po prawej*. Jeśli [unordered_map:: get_allocator](#get_allocator) `() == right.get_allocator()` , robi to w stałym czasie, zgłasza wyjątek tylko w wyniku kopiowania obiektu składowanych cech typu `Tr` i unieważnia odwołania, wskaźniki lub Iteratory, które wyznaczają elementy w dwóch kontrolowanej sekwencji. W przeciwnym razie wykonuje wiele przypisań elementów i wywołań konstruktora proporcjonalnie do liczby elementów w dwóch kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_swap.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    Mymap c2;

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    c1.swap(c2);

// display contents " [f 6] [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    swap(c1, c2);

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[f, 6] [e, 5] [d, 4]
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapunordered_map"></a><a name="unordered_map"></a> unordered_map:: unordered_map

Konstruuje obiekt kontenera.

```cpp
unordered_map(const unordered_map& Right);

explicit unordered_map(
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Allocator());

unordered_map(unordered_map&& Right);
unordered_map(initializer_list<Type> IList);
unordered_map(initializer_list<Type> IList, size_type Bucket_count);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    KeyEqual& equal);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    KeyEqual& Equal
    const Allocator& Al);

template <class InIt>
unordered_map(
    InputIterator First,
    InputIterator Last,
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());
```

### <a name="parameters"></a>Parametry

*Wsp*\
Obiekt alokatora, który ma być przechowywany.

*Przepisów*\
Obiekt funkcji porównywania, który ma być przechowywany.

*Skrótu*\
Obiekt funkcji mieszania, który ma być przechowywany.

*Bucket_count*\
Minimalna liczba przedziałów.

*Kliknij*\
Kontener, który ma być skopiowany.

*Pierwszego*\
Pozycja pierwszego elementu, który ma zostać skopiowany.

*Ostatniego*\
Pozycja tuż poza ostatnim elementem, który ma zostać skopiowany.

*IList*\
Initializer_list, który zawiera elementy, które mają zostać skopiowane.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor określa kopię sekwencji kontrolowanej przez `right` . Drugi konstruktor określa pustą kontrolowaną sekwencję. Trzeci Konstruktor wstawia sekwencję wartości elementów `[first, last)` . Czwarty Konstruktor określa kopię sekwencji poprzez przechodzenie `right` .

Wszystkie konstruktory również inicjują kilka przechowywanych wartości. W przypadku konstruktora kopiującego wartości są uzyskiwane z *prawej strony*. W przeciwnym razie:

Minimalna liczba przedziałów jest argumentem *Bucket_count*, jeśli istnieje; w przeciwnym razie jest to wartość domyślna opisana tutaj jako wartość zdefiniowana przez implementację `N0` .

Obiekt funkcji mieszania jest *wartością skrótu*argumentu (jeśli istnieje); w przeciwnym razie `Hash()` .

Obiekt funkcji porównywania jest argumentem *COMP*, jeśli jest obecny; w przeciwnym razie `Pred()` .

Obiekt alokatora jest argumentem *Al*, jeśli jest obecny; w przeciwnym razie jest to `Alloc()` .

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_construct.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>
#include <initializer_list>

using namespace std;

using Mymap = unordered_map<char, int>;

int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c2(8,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >());

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    // display contents " [f 6] [e 5] [d 4]"
    for (const auto& c : c2) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c3(c1.begin(),
        c1.end(),
        8,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >());

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c3) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c4(move(c3));

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c4) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
    cout << endl;

    // Construct with an initializer_list
    unordered_map<int, char> c5({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } });
    for (const auto& c : c5) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size
    unordered_map<int, char> c6({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } }, 4);
    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
    cout << endl;

    // Initializer_list plus size and hash
    unordered_map<int, char, hash<char>> c7(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size, hash, and key_equal
    unordered_map<int, char, hash<char>, equal_to<char>> c8(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>(),
        equal_to<char>()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size, hash, key_equal, and allocator
    unordered_map<int, char, hash<char>, equal_to<char>> c9(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
}
```

```Output
[a, 1] [b, 2] [c, 3]
[d, 4] [e, 5] [f, 6]
[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]

[5, g] [6, h] [7, i] [8, j]
[a, 1] [b, 2] [c, 3]

[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]
```

## <a name="unordered_mapvalue_type"></a><a name="value_type"></a> unordered_map:: value_type

Typ elementu.

```cpp
typedef std::pair<const Key, Ty> value_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje element kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__unordered_map__unordered_map_value_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="see-also"></a>Zobacz też

[<unordered_map>](../standard-library/unordered-map.md)\
[Opakowania](./stl-containers.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
