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
ms.openlocfilehash: 50868d020224e7bade9766f7307bfcc46ce4be47
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657594"
---
# <a name="concurrentunorderedmap-class"></a>concurrent_unordered_map — Klasa

`concurrent_unordered_map` Klasa jest kontenerem bezpieczne pod względem współbieżności, który kontroluje różnej długości sekwencje elementów typu `std::pair<const K, _Element_type>`. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczne pod względem współbieżności dołączyć element dostępu, dostępu do iteratora i operacji przechodzenia iteratora.

## <a name="syntax"></a>Składnia

```
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

#### <a name="parameters"></a>Parametry

*K*<br/>
Typ klucza.

*_Element_type*<br/>
Typ mapowany.

*_Hasher*<br/>
Typ obiektu funkcji mieszania. Ten argument jest opcjonalny, a wartość domyślna to `std::hash<K>`.

*key_equality*<br/>
Typ obiektu funkcji porównywania równości. Ten argument jest opcjonalny, a wartość domyślna to `std::equal_to<K>`.

*_Allocator_type*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i dezalokacji pamięci współbieżnej mapy nieuporządkowanej. Ten argument jest opcjonalny, a wartość domyślna to `std::allocator<std::pair<K`, `_Element_type>>`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
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

|Nazwa|Opis|
|----------|-----------------|
|[concurrent_unordered_map](#ctor)|Przeciążone. Tworzy równoczesna mapę nieuporządkowaną.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[at](#at)|Przeciążone. Wyszukuje element w `concurrent_unordered_map` z określoną wartością klucza... Ta metoda jest bezpieczna pod kątem współbieżności.|
|[hash_function](#hash_function)|Pobiera przechowywany obiekt funkcji mieszania.|
|[Wstaw](#insert)|Przeciążone. Dodaje elementy do `concurrent_unordered_map` obiektu.|
|[key_eq](#key_eq)|Pobiera obiekt funkcji porównywania równości przechowywanych.|
|[swap](#swap)|Zamienia zawartości dwóch `concurrent_unordered_map` obiektów. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[unsafe_erase](#unsafe_erase)|Przeciążone. Usuwa elementy z `concurrent_unordered_map` określonych pozycji. Ta metoda nie jest bezpieczna pod kątem współbieżności.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Operator\[\]](#operator_at)|Przeciążone. Znajduje lub wstawia element z określonym kluczem. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[operator=](#operator_eq)|Przeciążone. Przypisuje zawartość innego `concurrent_unordered_map` obiektu do wskazanego. Ta metoda nie jest bezpieczna pod kątem współbieżności.|

## <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje na temat `concurrent_unordered_map` klasy, zobacz [równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_map`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concurrent_unordered_map.h

**Namespace:** współbieżności

##  <a name="at"></a> w

Wyszukuje element w `concurrent_unordered_map` z określoną wartością klucza... Ta metoda jest bezpieczna pod kątem współbieżności.

```
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Wartość klucza do znalezienia.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do wartości danych znalezionego elementu.

### <a name="remarks"></a>Uwagi

Jeśli wartość klucza argumentu nie zostanie znaleziony, funkcja zgłasza obiekt klasy `out_of_range`.

##  <a name="begin"></a> Rozpocznij

Zwraca iterator, który wskazuje na pierwszy element w kontenerze współbieżnych. Ta metoda jest bezpieczny dla współbieżności.

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator do pierwszego elementu w kontenerze współbieżnych.

##  <a name="cbegin"></a> cbegin —

Zwraca iterator const, wskazuje na pierwszy element w kontenerze współbieżnych. Ta metoda jest bezpieczny dla współbieżności.

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator const do pierwszego elementu w kontenerze współbieżnych.

##  <a name="cend"></a> cend

Zwraca iterator const, która wskazuje lokalizację po ostatnim elemencie w kontenerze współbieżnych. Ta metoda jest bezpieczny dla współbieżności.

```
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator const do lokalizacji następującej po ostatnim elemencie w kontenerze współbieżnych.

##  <a name="clear"></a> Usuń zaznaczenie

Usuwa wszystkie elementy w kontenerze współbieżnych. Ta funkcja nie jest bezpieczny dla współbieżności.

```
void clear();
```

##  <a name="ctor"></a> concurrent_unordered_map —

Tworzy równoczesna mapę nieuporządkowaną.

```
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
Początkowa liczba zasobników dla tej mapy nieuporządkowanej.

*_Hasher*<br/>
Funkcja wyznaczania wartości skrótu dla tej mapy nieuporządkowanej.

*key_equality*<br/>
Funkcja porównywania równości tej mapy nieuporządkowanej.

*_Allocator*<br/>
Alokator dla tej mapy nieuporządkowanej.

*_Rozpocznij*<br/>
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*_Zakończ*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

*_Umap*<br/>
Źródło `concurrent_unordered_map` obiektu do kopiowania lub przenoszenia elementów z.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują obiekt programu przydzielania `_Allocator` i zainicjuj mapy nieuporządkowanej.

Pierwszy Konstruktor określa pustą mapę początkowej i wyraźnie określa liczbę przedziałów, typ funkcji mieszania, funkcją porównania oraz alokatorem ma być używany.

Drugi Konstruktor określa alokatora do mapy nieuporządkowanej.

Trzeci Konstruktor określa wartości dostarczone przez zakres iteratora [ `_Begin`, `_End`).

Czwarty i piąty Konstruktor określają kopię równoczesna mapę nieuporządkowaną `_Umap`.

Ostatni Konstruktor Określa przeniesienie równoczesna mapę nieuporządkowaną `_Umap`.

##  <a name="count"></a> Liczba

Zlicza liczbę elementów pasujących do określonego klucza. Ta funkcja jest bezpieczny dla współbieżności.

```
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Klucz do wyszukania.

### <a name="return-value"></a>Wartość zwracana

Liczba razy liczba przypadków, gdy klucz jest wyświetlany w kontenerze.

##  <a name="empty"></a> pusty

Sprawdza, czy nie ma żadnych elementów. Ta metoda jest bezpieczny dla współbieżności.

```
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli współbieżnych kontener jest pusty, **false** inaczej.

### <a name="remarks"></a>Uwagi

Czy współbieżnych kontener jest pusty mogą ulec zmianie w obecności równoczesnych operacji wstawiania, natychmiast po wywołaniu tej funkcji, zanim wartość zwracana jest nawet do odczytu.

##  <a name="end"></a> koniec

Zwraca iterator wskazujący lokalizację po ostatnim elemencie w kontenerze współbieżnych. Ta metoda jest bezpieczny dla współbieżności.

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator do lokalizacji następującej po ostatnim elemencie w kontenerze współbieżnych.

##  <a name="equal_range"></a> equal_range —

Wyszukuje zakres, który odpowiada określonemu kluczowi. Ta funkcja jest bezpieczny dla współbieżności.

```
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

### <a name="return-value"></a>Wartość zwracana

A [pary](../../../standard-library/pair-structure.md) gdzie pierwszy element jest iterację do początku, a drugi element stanowi iterator do końca zakresu.

### <a name="remarks"></a>Uwagi

Istnieje możliwość współbieżnych operacji wstawienia powodować dodatkowych kluczy, które ma zostać wstawiony po iteratora begin i przed iteratora zakończenia.

##  <a name="find"></a> Znajdź

Wyszukuje element, który odpowiada określonemu kluczowi. Ta funkcja jest bezpieczny dla współbieżności.

```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Wartość klucza do wyszukania.

### <a name="return-value"></a>Wartość zwracana

Iterator wskazuje lokalizację pierwszego elementu, który pasuje do klucza dostarczonego lub iteratora `end()` jeśli taki element nie istnieje.

##  <a name="get_allocator"></a> get_allocator —

Zwraca przechowywany obiekt alokatora dla tego kontenera współbieżnych. Ta metoda jest bezpieczny dla współbieżności.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Przechowywany obiekt alokatora dla tego kontenera współbieżnych.

##  <a name="hash_function"></a> hash_function —

Pobiera przechowywany obiekt funkcji mieszania.

```
hasher hash_function() const;
```

### <a name="return-value"></a>Wartość zwracana

Przechowywany obiekt funkcji mieszania.

##  <a name="insert"></a> Wstaw

Dodaje elementy do `concurrent_unordered_map` obiektu.

```
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
Typ iteratora, używany do wstawienia.

*V*<br/>
Typ wartości do mapy.

*value*<br/>
Wartość, która ma zostać wstawiony.

*_Where*<br/>
Począwszy od lokalizacji do wyszukiwania punkt wstawiania.

*pierwszy*<br/>
Początek zakresu do wstawienia.

*ostatni*<br/>
Koniec zakresu do wstawienia.

### <a name="return-value"></a>Wartość zwracana

Parą, która zawiera iteratora i wartość logiczną. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego Określa, czy element X istnieje w kolejności, w których klucz ma równoważną kolejność, tak aby w przypadku `value`. Jeśli nie, tworzy takiego elementu X i inicjuje ją za pomocą `value`. Funkcja następnie określa iterator `where` który wyznacza X. Jeśli wystąpił wstawieniem, funkcja zwraca `std::pair(where, true)`. W przeciwnym razie zwraca `std::pair(where, false)`.

Druga funkcja elementu członkowskiego zwraca wstawiania ( `value`) przy użyciu `_Where` jako punkt wyjścia w kontrolowanej sekwencji, aby wyszukać punkt wstawiania.

Trzecia funkcja członkowska wstawia sekwencję wartości elementu z zakresu [ `first`, `last`).

Ostatnie dwie funkcje Członkowskie, działa tak samo jako pierwsze dwa, chyba że `value` służy do konstruowania wstawiona wartość.

##  <a name="key_eq"></a> key_eq —

Pobiera obiekt funkcji porównywania równości przechowywanych.

```
key_equal key_eq() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt funkcji porównywania równości przechowywanych.

##  <a name="load_factor"></a> load_factor —

Oblicza i zwraca bieżący współczynnik obciążenia kontenera. Współczynnik obciążenia jest liczba elementów w kontenerze dzielona przez liczbę przedziałów.

```
float load_factor() const;
```

### <a name="return-value"></a>Wartość zwracana

Współczynnik obciążenia kontenera.

##  <a name="max_load_factor"></a> max_load_factor —

Pobiera lub ustawia współczynnik maksymalnego obciążenia kontenera. Współczynnik maksymalnego obciążenia jest największą liczbę elementów, nie może być w dowolnym zasobniku, zanim kontenera rozwoju swojej wewnętrznej tabeli.

```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>Parametry

`_Newmax`

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego zwraca współczynnik przechowywanych maksymalnego obciążenia. Funkcja drugiego członka nie zwraca wartości, ale zgłasza [out_of_range —](../../../standard-library/out-of-range-class.md) wyjątek, jeśli współczynnik podane obciążenia jest nieprawidłowy.

##  <a name="max_size"></a> max_size —

Zwraca maksymalny rozmiar kontenera współbieżnych, określane przez alokator. Ta metoda jest bezpieczny dla współbieżności.

```
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba elementów, które mogą być wstawiane do tego kontenera współbieżnych.

### <a name="remarks"></a>Uwagi

Ta wartość górna granica faktycznie może być wyższy niż co faktycznie może zawierać kontenera.

##  <a name="operator_at"></a> Operator]

Znajduje lub wstawia element z określonym kluczem. Ta metoda jest bezpieczna pod kątem współbieżności.

```
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Wartość klucza

znaleziona lub wstawiona.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do wartości danych elementu znaleziona lub wstawiona.

### <a name="remarks"></a>Uwagi

Jeśli wartość klucza argumentu nie zostanie znaleziona, zostanie ona wstawiona wraz z wartością domyślną typu danych.

`operator[]` może służyć do wstawienia elementów do mapy `m` przy użyciu `m[key] = DataValue;`, gdzie `DataValue` jest wartością `mapped_type` elementu o wartości klucza `key`.

Korzystając z `operator[]` do wstawienia elementów, zwracane odwołanie nie wskazuje, czy wstawienie jest zmiana istniejący element lub tworzenia nowej. Funkcje elementów członkowskich `find` i [Wstaw](#insert) może służyć do określenia, czy element z określonym kluczem już występuje przed wstawieniem.

##  <a name="operator_eq"></a> operator =

Przypisuje zawartość innego `concurrent_unordered_map` obiektu do wskazanego. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```

### <a name="parameters"></a>Parametry

*_Umap*<br/>
Źródło `concurrent_unordered_map` obiektu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `concurrent_unordered_map` obiektu.

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkie elementy istniejących współbieżnego wektora `operator=` kopiuje lub przenosi zawartość `_Umap` do współbieżnego wektora.

##  <a name="rehash"></a> rehash —

Przebudowuje tabelę mieszania.

```
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>Parametry

*_Buckets*<br/>
Żądaną liczbę przedziałów.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zmienia liczbę przedziałów, na co najmniej `_Buckets` i odbudowuje tabelę mieszania, stosownie do potrzeb. Liczba przedziałów musi być potęgą liczby 2. Jeśli nie potęgą liczby 2, jego kopia zapasowa zostanie zaokrąglona do następną największą potęgą liczby 2.

Wyniku weryfikacji zgłasza wyjątek [out_of_range —](../../../standard-library/out-of-range-class.md) wyjątek, jeśli liczba przedziałów jest nieprawidłowy (0 lub większa niż maksymalna liczba zasobników).

##  <a name="size"></a> Rozmiar

Zwraca liczbę elementów w tym kontenerze współbieżnych. Ta metoda jest bezpieczny dla współbieżności.

```
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w kontenerze.

### <a name="remarks"></a>Uwagi

W obecności równoczesnych operacji wstawiania liczba elementów w kontenerze współbieżnych, które mogą ulec zmianie natychmiast po wywołaniu tej funkcji, zanim wartość zwracana jest nawet do odczytu.

##  <a name="swap"></a> swap

Zamienia zawartości dwóch `concurrent_unordered_map` obiektów. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
void swap(concurrent_unordered_map& _Umap);
```

### <a name="parameters"></a>Parametry

*_Umap*<br/>
`concurrent_unordered_map` Zamień na obiekt.

##  <a name="unsafe_begin"></a> unsafe_begin

Zwraca iterator do pierwszego elementu w tym kontenerze dla określonego przedziału.

```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Indeks przedziału.

### <a name="return-value"></a>Wartość zwracana

Iterator wskazuje początek przedziału.

##  <a name="unsafe_bucket"></a> unsafe_bucket —

Zwraca indeks przedział, który mapuje określonego klucza w tym kontenerze.

```
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Klucz elementu wyszukane.

### <a name="return-value"></a>Wartość zwracana

Zasobnik indeks klucza, w tym kontenerze.

##  <a name="unsafe_bucket_count"></a> unsafe_bucket_count

Zwraca bieżącą liczbę zasobników, w tym kontenerze.

```
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca liczba zasobników, w tym kontenerze.

##  <a name="unsafe_bucket_size"></a> unsafe_bucket_size

Zwraca liczbę elementów w określonym zasobniku tego kontenera.

```
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Zasobnik do wyszukania.

### <a name="return-value"></a>Wartość zwracana

Bieżąca liczba zasobników, w tym kontenerze.

##  <a name="unsafe_cbegin"></a> unsafe_cbegin —

Zwraca iterator do pierwszego elementu w tym kontenerze dla określonego przedziału.

```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Indeks przedziału.

### <a name="return-value"></a>Wartość zwracana

Iterator wskazuje początek przedziału.

##  <a name="unsafe_cend"></a> unsafe_cend

Zwraca iterator do lokalizacji następującej po ostatnim elemencie w określonym zasobniku.

```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Indeks przedziału.

### <a name="return-value"></a>Wartość zwracana

Iterator wskazuje początek przedziału.

##  <a name="unsafe_end"></a> unsafe_end —

Zwraca iterator do ostatniego elementu w tym kontenerze dla określonego przedziału.

```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Indeks przedziału.

### <a name="return-value"></a>Wartość zwracana

Iterator wskazuje koniec przedziału.

##  <a name="unsafe_erase"></a> unsafe_erase —

Usuwa elementy z `concurrent_unordered_map` określonych pozycji. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
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
Pozycja sterująca do wymazania z.

*_Rozpocznij*<br/>
Pozycja pierwszego elementu w zakresie elementów, które mają zostać wymazane.

*_Zakończ*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać wymazane.

*KVal*<br/>
Wartość klucza do wymazania.

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie funkcje Członkowskie zwracają iterator opisujący pierwszy element pozostający poza wszelkimi elementami usuniętymi lub `concurrent_unordered_map::end`(), jeśli taki element nie istnieje. Trzecia funkcji członkowska zwraca liczbę elementów, które usuwa.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkostwa usuwa element kontrolowanej sekwencji wskazywany przez `_Where`. Funkcja drugiego członka usuwa elementy z zakresu [ `_Begin`, `_End`).

Trzecia funkcja członkowska usuwa elementy z zakresu rozdzielone `concurrent_unordered_map::equal_range`(KVal).

##  <a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count

Zwraca maksymalną liczbę przedziałów, w tym kontenerze.

```
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba zasobników, w tym kontenerze.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md)

