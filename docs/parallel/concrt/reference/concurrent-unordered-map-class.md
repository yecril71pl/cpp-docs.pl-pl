---
title: concurrent_unordered_map — Klasa
ms.date: 11/04/2016
f1_keywords:
- concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::at
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::hash_function
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::insert
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::key_eq
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::swap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::unsafe_erase
helpviewer_keywords:
- concurrent_unordered_map class
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
ms.openlocfilehash: 04fdfb767645cb2db31a453a2378881a8b3e3a04
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143163"
---
# <a name="concurrent_unordered_map-class"></a>concurrent_unordered_map — Klasa

Klasa `concurrent_unordered_map` jest bezpiecznym pod kątem współbieżności kontenerem, który kontroluje różnej długości sekwencje elementów typu `std::pair<const K, _Element_type>`. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczne wykonywanie operacji dołączania, dostęp do elementów, dostęp iteratora i przechodzenie iteratora. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia.

## <a name="syntax"></a>Składnia

```cpp
template <typename K,
    typename _Element_type,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>
>,
typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>> class concurrent_unordered_map : public details::_Concurrent_hash<details::_Concurrent_unordered_map_traits<K,
    _Element_type,
details::_Hash_compare<K,
    _Hasher,
key_equality>,
    _Allocator_type,
false>>;
```

### <a name="parameters"></a>Parametry

*K*<br/>
Typ klucza.

*_Element_type*<br/>
Typ mapowany.

*_Hasher*<br/>
Typ obiektu funkcji mieszania. Ten argument jest opcjonalny, a wartość domyślna to `std::hash<K>`.

*key_equality*<br/>
Typ obiektu funkcji porównywania równości. Ten argument jest opcjonalny, a wartość domyślna to `std::equal_to<K>`.

*_Allocator_type*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i cofania alokacji pamięci dla współbieżnej mapy nieuporządkowanej. Ten argument jest opcjonalny, a wartość domyślna to `std::allocator<std::pair<K`, `_Element_type>>`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`allocator_type`|Typ alokatora do zarządzania pamięcią.|
|`const_iterator`|Typ iteratora stałego dla kontrolowanej sekwencji.|
|`const_local_iterator`|Typ iteratora stałego przedziału dla kontrolowanej sekwencji.|
|`const_pointer`|Typ stałego wskaźnika do elementu.|
|`const_reference`|Typ stałego odwołania do elementu.|
|`difference_type`|Typ odległości ze znakiem między dwoma elementami.|
|`hasher`|Typ funkcji mieszania.|
|`iterator`|Typ iteratora dla kontrolowanej sekwencji.|
|`key_equal`|Typ funkcji porównywania.|
|`key_type`|Typ klucza sortowania.|
|`local_iterator`|Typ iteratora przedziału dla kontrolowanej sekwencji.|
|`mapped_type`|Typ mapowanej wartości skojarzonej z poszczególnymi kluczami.|
|`pointer`|Typ wskaźnika do elementu.|
|`reference`|Typ odwołania do elementu.|
|`size_type`|Typ odległości bez znaku między dwoma elementami.|
|`value_type`|Typ elementu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[concurrent_unordered_map](#ctor)|Przeciążone. Konstruuje współbieżną mapę nieuporządkowaną.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[w](#at)|Przeciążone. Znajduje element w `concurrent_unordered_map` z określoną wartością klucza.. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[hash_function](#hash_function)|Pobiera przechowywany obiekt funkcji mieszania.|
|[wstawienia](#insert)|Przeciążone. Dodaje elementy do obiektu `concurrent_unordered_map`.|
|[key_eq](#key_eq)|Pobiera przechowywany obiekt funkcji porównywania równości.|
|[wymiany](#swap)|Zamienia zawartość dwóch `concurrent_unordered_map` obiektów. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[unsafe_erase](#unsafe_erase)|Przeciążone. Usuwa elementy z `concurrent_unordered_map` w określonych położeniach. Ta metoda nie jest bezpieczna pod kątem współbieżności.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[\[operatora \]](#operator_at)|Przeciążone. Znajduje lub wstawia element z określonym kluczem. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[operator =](#operator_eq)|Przeciążone. Przypisuje do niego zawartość innego obiektu `concurrent_unordered_map`. Ta metoda nie jest bezpieczna pod kątem współbieżności.|

## <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje na temat klasy `concurrent_unordered_map`, zobacz [Parallel Containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_map`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concurrent_unordered_map. h

**Przestrzeń nazw:** współbieżność

## <a name="at"></a>w

Znajduje element w `concurrent_unordered_map` z określoną wartością klucza.. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Wartość klucza do wyszukania.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do wartości danych znalezionego elementu.

### <a name="remarks"></a>Uwagi

Jeśli wartość klucza argumentu nie zostanie znaleziona, funkcja generuje obiekt klasy `out_of_range`.

## <a name="begin"></a>zaczną

Zwraca iterator wskazujący na pierwszy element w kontenerze współbieżnym. Ta metoda jest bezpieczna pod względem współbieżności.

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Wartość zwrócona

Iterator do pierwszego elementu w kontenerze współbieżnym.

## <a name="cbegin"></a>cbegin

Zwraca iterator const wskazujący na pierwszy element w kontenerze współbieżnym. Ta metoda jest bezpieczna pod względem współbieżności.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwrócona

Iterator const do pierwszego elementu w kontenerze współbieżnym.

## <a name="cend"></a>cend

Zwraca iterator const wskazujący lokalizację, która kończy się ostatnim elementem w kontenerze współbieżnym. Ta metoda jest bezpieczna pod względem współbieżności.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwrócona

Iterator const do lokalizacji po ostatnim elemencie w kontenerze współbieżnym.

## <a name="clear"></a>Wyczyść

Usuwa wszystkie elementy w kontenerze współbieżnym. Ta funkcja nie jest bezpieczna pod kątem współbieżności.

```cpp
void clear();
```

## <a name="ctor"></a>concurrent_unordered_map

Konstruuje współbieżną mapę nieuporządkowaną.

```cpp
explicit concurrent_unordered_map(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_map(_Iterator _Begin,
    _Iterator _End,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap);

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap,
    const allocator_type& _Allocator);

concurrent_unordered_map(
    concurrent_unordered_map&& _Umap);
```

### <a name="parameters"></a>Parametry

*_Iterator*<br/>
Typ iteratora wejściowego.

*_Number_of_buckets*<br/>
Początkowa liczba przedziałów dla tej mapy nieuporządkowanej.

*_Hasher*<br/>
Funkcja skrótu dla tej mapy nieuporządkowanej.

*key_equality*<br/>
Funkcja porównywania równości dla tej mapy nieuporządkowanej.

*_Allocator*<br/>
Program przydzielający dla tej mapy nieuporządkowanej.

*_Begin*<br/>
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*_End*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

*_Umap*<br/>
Obiekt źródłowy `concurrent_unordered_map` do kopiowania lub przenoszenia elementów.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują obiekt alokatora `_Allocator` i inicjują mapę nieuporządkowaną.

Pierwszy Konstruktor określa pustą mapę początkową i jawnie określa liczbę przedziałów, funkcję mieszania, funkcję równości i typ alokatora, który ma być używany.

Drugi Konstruktor Określa Alokator dla mapy nieuporządkowanej.

Trzeci konstruktor określa wartości dostarczone przez zakres iteratora [`_Begin`, `_End`).

Czwarty i piąty konstruktory określają kopię współbieżnej mapy nieuporządkowanej `_Umap`.

Ostatni konstruktor określa przenoszenie współbieżnie nieuporządkowanej mapy `_Umap`.

## <a name="count"></a>liczbą

Zlicza elementy pasujące do określonego klucza. Ta funkcja jest bezpieczna pod względem współbieżności.

```cpp
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Klucz, który ma zostać wyszukany.

### <a name="return-value"></a>Wartość zwrócona

Liczba przypadków, gdy klucz pojawia się w kontenerze.

## <a name="empty"></a>ciągiem

Sprawdza, czy nie ma żadnych elementów. Ta metoda jest bezpieczna pod względem współbieżności.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli kontener współbieżny jest pusty, w przeciwnym razie **zwraca wartość false** .

### <a name="remarks"></a>Uwagi

W obecności współbieżnych operacji wstawiania, niezależnie od tego, czy współbieżny kontener jest pusty, może ulec zmianie natychmiast po wywołaniu tej funkcji, zanim zwracana wartość zostanie odczytana.

## <a name="end"></a>punktów

Zwraca iterator wskazujący lokalizację, która kończy się ostatnim elementem w kontenerze współbieżnym. Ta metoda jest bezpieczna pod względem współbieżności.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Wartość zwrócona

Iterator do lokalizacji po ostatnim elemencie w kontenerze współbieżnym.

## <a name="equal_range"></a>equal_range

Znajduje zakres pasujący do określonego klucza. Ta funkcja jest bezpieczna pod względem współbieżności.

```cpp
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Wartość klucza do wyszukania.

### <a name="return-value"></a>Wartość zwrócona

[Para](../../../standard-library/pair-structure.md) , w której pierwszy element jest iteratorem do początku, a drugi element jest iteratorem do końca zakresu.

### <a name="remarks"></a>Uwagi

Możliwe jest jednoczesne wstawianie, aby spowodować Wstawianie dodatkowych kluczy po iteratoru BEGIN i przed iteratorem końcowym.

## <a name="find"></a>wyświetlić

Wyszukuje element, który odpowiada określonemu kluczowi. Ta funkcja jest bezpieczna pod względem współbieżności.

```cpp
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Wartość klucza do wyszukania.

### <a name="return-value"></a>Wartość zwrócona

Iterator wskazujący lokalizację pierwszego elementu, który pasuje do podanego klucza lub iterator `end()`, jeśli taki element nie istnieje.

## <a name="get_allocator"></a>get_allocator

Zwraca przechowywany obiekt alokatora dla tego współbieżnego kontenera. Ta metoda jest bezpieczna pod względem współbieżności.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwrócona

Przechowywany obiekt alokatora dla tego współbieżnego kontenera.

## <a name="hash_function"></a>hash_function

Pobiera przechowywany obiekt funkcji mieszania.

```cpp
hasher hash_function() const;
```

### <a name="return-value"></a>Wartość zwrócona

Przechowywany obiekt funkcji skrótu.

## <a name="insert"></a>wstawienia

Dodaje elementy do obiektu `concurrent_unordered_map`.

```cpp
std::pair<iterator,
    bool> insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
std::pair<iterator,
    bool> insert(
    V&& value);

template<class V>
typename std::enable_if<!std::is_same<const_iterator,
    typename std::remove_reference<V>::type>::value,
    iterator>::type insert(
    const_iterator _Where,
    V&& value);
```

### <a name="parameters"></a>Parametry

*_Iterator*<br/>
Typ iteratora używany do wstawiania.

*V*<br/>
Typ wartości wstawionej do mapy.

*value*<br/>
Wartość, która ma zostać wstawiona.

*_Where*<br/>
Początkowa lokalizacja, w której ma zostać wyszukany punkt wstawiania.

*pierwszego*<br/>
Początek zakresu do wstawienia.

*ostatniego*<br/>
Koniec zakresu do wstawienia.

### <a name="return-value"></a>Wartość zwrócona

Para, która zawiera iterator i wartość logiczną. Zobacz sekcję Uwagi, aby uzyskać więcej szczegółów.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska określa, czy element X istnieje w sekwencji, którego klucz ma równoważne porządkowanie do `value`. W przeciwnym razie tworzy taki element X i inicjuje go `value`. Następnie funkcja określa `where` iteratora, który wyznacza X. Jeśli nastąpiło wstawienie, funkcja zwraca `std::pair(where, true)`. W przeciwnym razie zwraca `std::pair(where, false)`.

Druga funkcja członkowska zwraca Insert (`value`), używając `_Where` jako początku w kontrolowanej sekwencji, aby wyszukać punkt wstawiania.

Trzecia funkcja członkowska wstawia sekwencję wartości elementów z zakresu [`first`, `last`).

Ostatnie dwie funkcje członkowskie zachowują się tak samo jak pierwsze dwa, z wyjątkiem tego, że `value` jest używany do konstruowania wstawionej wartości.

## <a name="key_eq"></a>key_eq

Pobiera przechowywany obiekt funkcji porównywania równości.

```cpp
key_equal key_eq() const;
```

### <a name="return-value"></a>Wartość zwrócona

Przechowywany obiekt funkcji porównywania równości.

## <a name="load_factor"></a>load_factor

Oblicza i zwraca bieżący współczynnik obciążenia kontenera. Współczynnik obciążenia to liczba elementów w kontenerze podzielona przez liczbę przedziałów.

```cpp
float load_factor() const;
```

### <a name="return-value"></a>Wartość zwrócona

Współczynnik obciążenia dla kontenera.

## <a name="max_load_factor"></a>max_load_factor

Pobiera lub ustawia maksymalny współczynnik obciążenia kontenera. Maksymalny współczynnik obciążenia to największą liczbę elementów, która może znajdować się w dowolnym zasobniku, zanim kontener zostanie powiększony do swojej wewnętrznej tabeli.

```cpp
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>Parametry

`_Newmax`

### <a name="return-value"></a>Wartość zwrócona

Pierwsza funkcja członkowska zwraca przechowywany maksymalny współczynnik obciążenia. Druga funkcja członkowska nie zwraca wartości, ale zgłasza wyjątek [out_of_range](../../../standard-library/out-of-range-class.md) , jeśli podany współczynnik obciążenia jest nieprawidłowy.

## <a name="max_size"></a>max_size

Zwraca maksymalny rozmiar kontenera współbieżnego, który jest określany przez Alokator. Ta metoda jest bezpieczna pod względem współbieżności.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwrócona

Maksymalna liczba elementów, które można wstawić do tego współbieżnego kontenera.

### <a name="remarks"></a>Uwagi

Ta Górna granica może być w rzeczywistości wyższa niż wartość kontenera, w której ma zostać wstrzymana.

## <a name="operator_at"></a>operator []

Znajduje lub wstawia element z określonym kluczem. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Wartość klucza do

Znajdź lub Wstaw.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do wartości danych znalezionego lub wstawionego elementu.

### <a name="remarks"></a>Uwagi

Jeśli wartość klucza argumentu nie zostanie znaleziona, zostanie ona wstawiona wraz z wartością domyślną typu danych.

`operator[]` może służyć do wstawiania elementów do mapy `m` przy użyciu `m[key] = DataValue;`, gdzie `DataValue` jest wartością `mapped_type` elementu z wartością klucza `key`.

W przypadku używania `operator[]` do wstawiania elementów, zwrócone odwołanie nie wskazuje, czy wstawienie zmienia istniejący element lub tworzy nowy. Funkcje składowe `find` i [INSERT](#insert) mogą służyć do określenia, czy element z określonym kluczem jest już obecny przed wstawieniem.

## <a name="operator_eq"></a>operator =

Przypisuje do niego zawartość innego obiektu `concurrent_unordered_map`. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```

### <a name="parameters"></a>Parametry

*_Umap*<br/>
Obiekt źródłowy `concurrent_unordered_map`.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do tego obiektu `concurrent_unordered_map`.

### <a name="remarks"></a>Uwagi

Po wymazaniu wszystkich istniejących elementów jako współbieżnych wektorów `operator=` kopiuje lub przenosi zawartość `_Umap` do współbieżnego wektora.

## <a name="rehash"></a>rehash —

Przebudowuje tabelę mieszania.

```cpp
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>Parametry

*_Buckets*<br/>
Wymagana liczba zasobników.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zmienia liczbę przedziałów, które mają być co najmniej `_Buckets` i ponownie kompiluje tabelę skrótów zgodnie z wymaganiami. Liczba przedziałów musi być potęgą liczby 2. Jeśli nie jest potęgą liczby 2, będzie zaokrąglana do najbliższej największej potęgi 2.

Zgłasza wyjątek [out_of_range](../../../standard-library/out-of-range-class.md) , jeśli liczba przedziałów jest nieprawidłowa (0 lub większa niż maksymalna liczba przedziałów).

## <a name="size"></a>zmienia

Zwraca liczbę elementów w tym współbieżnym kontenerze. Ta metoda jest bezpieczna pod względem współbieżności.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwrócona

Liczba elementów w kontenerze.

### <a name="remarks"></a>Uwagi

W przypadku występowania równoczesnych operacji wstawiania liczba elementów w kontenerze współbieżnym może ulec zmianie natychmiast po wywołaniu tej funkcji, zanim zwracana wartość zostanie odczytana.

## <a name="swap"></a>wymiany

Zamienia zawartość dwóch `concurrent_unordered_map` obiektów. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
void swap(concurrent_unordered_map& _Umap);
```

### <a name="parameters"></a>Parametry

*_Umap*<br/>
Obiekt `concurrent_unordered_map` do zamiany na.

## <a name="unsafe_begin"></a>unsafe_begin

Zwraca iterator do pierwszego elementu w tym kontenerze dla określonego przedziału.

```cpp
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Indeks przedziału.

### <a name="return-value"></a>Wartość zwrócona

Iterator wskazujący początek zasobnika.

## <a name="unsafe_bucket"></a>unsafe_bucket

Zwraca indeks zasobnika, do którego określony klucz jest mapowany w tym kontenerze.

```cpp
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Wyszukiwany klucz elementu.

### <a name="return-value"></a>Wartość zwrócona

Indeks zasobnika klucza w tym kontenerze.

## <a name="unsafe_bucket_count"></a>unsafe_bucket_count

Zwraca bieżącą liczbę przedziałów w tym kontenerze.

```cpp
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>Wartość zwrócona

Bieżąca liczba przedziałów w tym kontenerze.

## <a name="unsafe_bucket_size"></a>unsafe_bucket_size

Zwraca liczbę elementów w określonym przedziale tego kontenera.

```cpp
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Zasobnik, który ma zostać wyszukany.

### <a name="return-value"></a>Wartość zwrócona

Bieżąca liczba przedziałów w tym kontenerze.

## <a name="unsafe_cbegin"></a>unsafe_cbegin

Zwraca iterator do pierwszego elementu w tym kontenerze dla określonego przedziału.

```cpp
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Indeks przedziału.

### <a name="return-value"></a>Wartość zwrócona

Iterator wskazujący początek zasobnika.

## <a name="unsafe_cend"></a>unsafe_cend

Zwraca iterator do lokalizacji, która kończy ostatni element w określonym przedziale.

```cpp
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Indeks przedziału.

### <a name="return-value"></a>Wartość zwrócona

Iterator wskazujący początek zasobnika.

## <a name="unsafe_end"></a>unsafe_end

Zwraca iterator do ostatniego elementu w tym kontenerze dla określonego przedziału.

```cpp
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Indeks przedziału.

### <a name="return-value"></a>Wartość zwrócona

Iterator wskazujący koniec przedziału.

## <a name="unsafe_erase"></a>unsafe_erase

Usuwa elementy z `concurrent_unordered_map` w określonych położeniach. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
iterator unsafe_erase(
    const_iterator _Where);

iterator unsafe_erase(
    const_iterator _Begin,
    const_iterator _End);

size_type unsafe_erase(
    const key_type& KVal);
```

### <a name="parameters"></a>Parametry

*_Where*<br/>
Pozycja iteratora, z której można wymazać.

*_Begin*<br/>
Pozycja pierwszego elementu w zakresie elementów, które mają być wymazane.

*_End*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają być wymazane.

*KVal*<br/>
Wartość klucza do wymazania.

### <a name="return-value"></a>Wartość zwrócona

Pierwsze dwie funkcje członkowskie zwracają iterator, który wyznacza pierwszy element, który nie został usunięty, lub `concurrent_unordered_map::end`(), jeśli taki element nie istnieje. Trzecia funkcja członkowska zwraca liczbę elementów, które usuwa.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska usuwa element kontrolowanej sekwencji wskazywany przez `_Where`. Druga funkcja członkowska usuwa elementy z zakresu [`_Begin`, `_End`).

Trzecia funkcja członkowska usuwa elementy z zakresu oddzielone `concurrent_unordered_map::equal_range`(KVal).

## <a name="unsafe_max_bucket_count"></a>unsafe_max_bucket_count

Zwraca maksymalną liczbę przedziałów w tym kontenerze.

```cpp
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>Wartość zwrócona

Maksymalna liczba przedziałów w tym kontenerze.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md)
