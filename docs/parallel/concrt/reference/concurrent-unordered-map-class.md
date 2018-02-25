---
title: "concurrent_unordered_map — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- concurrent_unordered_map class
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d37feb147cc0604081479bfae0afca933c251bc8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="concurrentunorderedmap-class"></a>concurrent_unordered_map — Klasa
`concurrent_unordered_map` Klasy jest kontenerem bezpieczne współbieżności, który określa sekwencję zróżnicowanych długość elementów typu `std::pair<const K, _Element_type>`. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczny współbieżności dołączenia, element dostępu, dostęp iteratora i operacji przechodzenia iteratora.  
  
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
 `K`  
 Typ klucza.  
  
 `_Element_type`  
 Typ mapowany.  
  
 `_Hasher`  
 Typ obiektu funkcji mieszania. Ten argument jest opcjonalny, a wartość domyślna to `std::hash<K>`.  
  
 `key_equality`  
 Typ obiektu funkcji porównywania równości. Ten argument jest opcjonalny, a wartość domyślna to `std::equal_to<K>`.  
  
 `_Allocator_type`  
 Typ reprezentujący obiekt alokatora przechowywane, który hermetyzuje szczegółowe informacje dotyczące alokacji i cofania alokacji pamięci dla jednoczesnych nieuporządkowaną mapy. Ten argument jest opcjonalny, a wartość domyślna to `std::allocator<std::pair<K`, `_Element_type>>`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
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
|[concurrent_unordered_map](#ctor)|Przeciążone. Tworzy równoczesnych nieuporządkowaną mapy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[at](#at)|Przeciążone. Odnajduje element `concurrent_unordered_map` o określonej wartości klucza. Ta metoda jest bezpieczne współbieżności.|  
|[hash_function](#hash_function)|Pobiera przechowywany obiekt funkcji mieszania.|  
|[insert](#insert)|Przeciążone. Dodaje elementy `concurrent_unordered_map` obiektu.|  
|[key_eq](#key_eq)|Pobiera obiekt funkcja porównania równości przechowywane.|  
|[swap](#swap)|Zamienia zawartość dwóch `concurrent_unordered_map` obiektów. Ta metoda nie jest bezpieczne współbieżności.|  
|[unsafe_erase](#unsafe_erase)|Przeciążone. Usuwa elementy z `concurrent_unordered_map` w określonych pozycji. Ta metoda nie jest bezpieczne współbieżności.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator]](#operator_at)|Przeciążone. Znajduje lub wstawia element z określonym kluczem. Ta metoda jest bezpieczne współbieżności.|  
|[operator=](#operator_eq)|Przeciążone. Przypisuje zawartość innego `concurrent_unordered_map` obiektu do tego. Ta metoda nie jest bezpieczne współbieżności.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać szczegółowe informacje na temat `concurrent_unordered_map` , zobacz [równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `_Traits`  
  
 `_Concurrent_hash`  
  
 `concurrent_unordered_map`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concurrent_unordered_map.h  
  
 **Namespace:** współbieżności  
  
##  <a name="at"></a> w 

 Odnajduje element `concurrent_unordered_map` o określonej wartości klucza. Ta metoda jest bezpieczne współbieżności.  
  
```
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parametry  
 `KVal`  
 Wartość klucza można znaleźć.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do wartości danych znaleziono elementu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość klucza argument nie zostanie znaleziony, funkcja zwraca obiekt klasy `out_of_range`.  
  
##  <a name="begin"></a> Rozpocznij 

 Zwraca iteratora wskazujące pierwszy element w kontenerze współbieżnych. Ta metoda jest bezpiecznym współbieżności.  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora do pierwszego elementu w kontenerze współbieżnych.  
  
##  <a name="cbegin"></a> cbegin 

 Zwraca iteratora const, wskazujące pierwszy element w kontenerze współbieżnych. Ta metoda jest bezpiecznym współbieżności.  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Const iteratora do pierwszego elementu w kontenerze współbieżnych.  
  
##  <a name="cend"></a> cend 

 Zwraca const iteratora wskazuje lokalizację pomyślne wykonanie ostatniego elementu w kontenerze współbieżnych. Ta metoda jest bezpiecznym współbieżności.  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Const iteratora do lokalizacji pomyślne wykonanie ostatniego elementu w kontenerze współbieżnych.  
  
##  <a name="clear"></a> Wyczyść 

 Usuwa wszystkie elementy w kontenerze współbieżnych. Ta funkcja nie jest bezpiecznym współbieżności.  
  
```
void clear();
```  
  
##  <a name="ctor"></a> concurrent_unordered_map 

 Tworzy równoczesnych nieuporządkowaną mapy.  
  
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
 `_Iterator`  
 Typ iteratora wejściowego.  
  
 `_Number_of_buckets`  
 Początkowa liczba zasobników dla tej nieuporządkowaną mapy.  
  
 `_Hasher`  
 Funkcja wyznaczania wartości skrótu dla tego nieuporządkowaną mapy.  
  
 `key_equality`  
 Funkcja porównania równości dla tej nieuporządkowaną mapy.  
  
 `_Allocator`  
 Program przydzielania tej nieuporządkowaną mapy.  
  
 `_Begin`  
 Pozycja pierwszego elementu w zakresie elementów do skopiowania.  
  
 `_End`  
 Pozycja pierwszego elementu poza zakres elementów do skopiowania.  
  
 `_Umap`  
 Źródło `concurrent_unordered_map` obiekt, aby skopiować lub przenieść elementy z.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie konstruktory zapisania obiektu alokatora `_Allocator` i zainicjuj nieuporządkowaną mapy.  
  
 Pierwszy Konstruktor określa pusta Mapa początkowej i jawnie określa liczbę przedziałów, funkcji skrótu, funkcja równości i przydzielania typu do użycia.  
  
 Drugi Konstruktor określa alokatora nieuporządkowaną mapy.  
  
 Trzeci konstruktora określa wartości dostarczone przez zakres iteratora [ `_Begin`, `_End`).  
  
 Konstruktory czwartym i piątym Określ kopię równoczesnych mapy nieuporządkowaną `_Umap`.  
  
 Konstruktor ostatniego określa przenoszenia równoczesnych mapy nieuporządkowaną `_Umap`.  
  
##  <a name="count"></a> Liczba 

 Oblicza liczbę elementów pasujących określonego klucza. Ta funkcja jest bezpiecznym współbieżności.  
  
```
size_type count(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parametry  
 `KVal`  
 Klucz do wyszukania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba razy liczba klucz pojawia się w kontenerze.  
  
##  <a name="empty"></a> pusty 

 Sprawdza, czy nie ma żadnych elementów. Ta metoda jest bezpiecznym współbieżności.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli równoczesnych kontenera jest pusta, `false` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Czy równoczesnych kontenera jest pusty mogą ulec zmianie obecności równoczesnych operacji wstawienia, natychmiast po wywołaniu tej funkcji, aby wartość zwracana jest nawet do odczytu.  
  
##  <a name="end"></a> Koniec 

 Zwraca iteratora wskazuje lokalizację pomyślne wykonanie ostatniego elementu w kontenerze współbieżnych. Ta metoda jest bezpiecznym współbieżności.  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora do lokalizacji pomyślne wykonanie ostatniego elementu w kontenerze współbieżnych.  
  
##  <a name="equal_range"></a> equal_range 

 Umożliwia znalezienie zakresu, który jest zgodny z określonym kluczem. Ta funkcja jest bezpiecznym współbieżności.  
  
```
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parametry  
 `KVal`  
 Wartość klucza do wyszukania.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [pary](http://msdn.microsoft.com/en-us/c5a37023-d939-4eb2-ae24-ce8e0cd4505d) gdzie pierwszy element jest iteratora na początku, a drugi element iteratora do końca zakresu.  
  
### <a name="remarks"></a>Uwagi  
 Istnieje możliwość równoczesnych operacji wstawienia spowodować dodatkowych kluczy ma zostać wstawiony po iteratora begin i przed iteratora zakończenia.  
  
##  <a name="find"></a> Znajdź 

 Wyszukuje element, który odpowiada określonemu kluczowi. Ta funkcja jest bezpiecznym współbieżności.  
  
```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parametry  
 `KVal`  
 Wartość klucza do wyszukania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazuje lokalizację iteratora pierwszy element, który pasuje do klucza dostarczonego lub iteratora `end()` Jeśli nie zawiera żadnego takiego elementu.  
  
##  <a name="get_allocator"></a> get_allocator 

 Zwraca obiekt alokatora przechowywanych dla tego kontenera współbieżnych. Ta metoda jest bezpiecznym współbieżności.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt alokatora przechowywanych dla tego kontenera współbieżnych.  
  
##  <a name="hash_function"></a> hash_function 

 Pobiera przechowywany obiekt funkcji mieszania.  
  
```
hasher hash_function() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt funkcji skrótu przechowywaną.  
  
##  <a name="insert"></a> Wstaw 

 Dodaje elementy `concurrent_unordered_map` obiektu.  
  
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
 `_Iterator`  
 Typ iteratora używane do wstawiania.  
  
 `V`  
 Typ wartości do mapy.  
  
 `value`  
 Wartości do wstawienia.  
  
 `_Where`  
 Lokalizacja początkowa do wyszukania punktu wstawiania.  
  
 `first`  
 Początek zakresu do wstawienia.  
  
 `last`  
 Koniec zakresu do wstawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pary iteratora i wartość logiczną. Zobacz sekcję uwag więcej szczegółów.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy funkcji członkowskiej Określa, czy element X istnieje w sekwencji, którego klucz został równoważne kolejności niż `value`. Jeśli nie, takiego elementu X tworzy i inicjuje go przy użyciu `value`. Funkcja określa iteratora `where` który wyznacza X. Jeśli podczas wstawiania, funkcja zwraca `std::pair(where, true)`. W przeciwnym razie zwraca `std::pair(where, false)`.  
  
 Wstaw zwraca drugie funkcji członkowskiej ( `value`), za pomocą narzędzia `_Where` do rozpoczęcia pracy w kontrolowanej sekwencji, aby wyszukać punkt wstawiania.  
  
 Trzeci funkcji członkowskiej wstawia sekwencji wartości elementów z zakresu [ `first`, `last`).  
  
 Funkcje Członkowskie ostatnich dwóch działają tak samo jak dwa pierwsze, z wyjątkiem `value` jest używany do tworzenia wstawiona wartość.  
  
##  <a name="key_eq"></a> key_eq 

 Pobiera obiekt funkcja porównania równości przechowywane.  
  
```
key_equal key_eq() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt funkcji porównania równości przechowywane.  
  
##  <a name="load_factor"></a> load_factor — 

 Oblicza i zwraca bieżący współczynnik obciążenia kontenera. Współczynnik obciążenia to liczba elementów w kontenerze podzielony przez liczbę zasobników.  
  
```
float load_factor() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Współczynnik obciążenia dla kontenera.  
  
##  <a name="max_load_factor"></a> max_load_factor — 

 Pobiera lub ustawia współczynnik maksymalne obciążenie kontenera. Współczynnik maksymalne obciążenie jest największą liczbę elementów, niż można w dowolnym przedziale przed jego tabeli wewnętrznej rozwoju kontenera.  
  
```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```  
  
### <a name="parameters"></a>Parametry  
 `_Newmax`  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy element członkowski funkcja współczynnik przechowywanych maksymalne obciążenie. Drugi funkcji członkowskiej nie zwraca wartości, ale zgłasza [out_of_range —](../../../standard-library/out-of-range-class.md) wyjątek, jeśli współczynnik podana obciążenia jest nieprawidłowy.  
  
##  <a name="max_size"></a> max_size 

 Zwraca maksymalny rozmiar równoczesnych kontenera, określany przez program przydzielania. Ta metoda jest bezpiecznym współbieżności.  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna liczba elementów, które można wstawiać do tego kontenera współbieżnych.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość górna granica faktycznie mogą być wyższe niż co faktycznie może przechowywać kontenera.  
  
##  <a name="operator_at">Operator]</a> 

 Znajduje lub wstawia element z określonym kluczem. Ta metoda jest bezpieczne współbieżności.  
  
```
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```  
  
### <a name="parameters"></a>Parametry  
 `KVal`  
 Wartość klucza  
  
 Znajdź lub wstawić.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do wartości danych została odnaleziona lub wstawionego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość klucza argumentu nie zostanie znaleziona, zostanie ona wstawiona wraz z wartością domyślną typu danych.  
  
 `operator[]` może służyć do wstawienia elementów do mapy `m` przy użyciu `m[key] = DataValue;`, gdzie `DataValue` jest wartością `mapped_type` elementu o wartości klucza `key`.  
  
 Korzystając z `operator[]` wstawianie elementów, zwracane odwołanie nie wskazuje, czy wstawiania jest zmiana istniejącego elementu lub tworzenia nowej. Funkcje Członkowskie `find` i [Wstaw](#insert) może służyć do określenia, czy element z określonym kluczem jest już obecny przed wstawieniem.  
  
##  <a name="operator_eq"></a> operator = 

 Przypisuje zawartość innego `concurrent_unordered_map` obiektu do tego. Ta metoda nie jest bezpieczne współbieżności.  
  
```
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```  
  
### <a name="parameters"></a>Parametry  
 `_Umap`  
 Źródło `concurrent_unordered_map` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego `concurrent_unordered_map` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Po wykonaniu elementy równoczesnych wektora `operator=` albo kopiuje lub przenosi zawartość `_Umap` do równoczesnych wektora.  
  
##  <a name="rehash"></a> rehash 

 Przebudowuje tabelę mieszania.  
  
```
void rehash(size_type _Buckets);
```  
  
### <a name="parameters"></a>Parametry  
 `_Buckets`  
 Żądaną liczbę zasobników.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zmienia Liczba zasobników, aby mieć co najmniej `_Buckets` i odtwarza tablicy skrótów zgodnie z potrzebami. Liczba zasobników, musi być potęgą liczby 2. Jeśli nie potęgą liczby 2, zostanie on zaokrąglony do następnego największą potęgą liczby 2.  
  
 Zgłasza [out_of_range —](../../../standard-library/out-of-range-class.md) wyjątek, jeśli liczba zasobników jest nieprawidłowy (0 lub większa niż maksymalna liczba zasobników).  
  
##  <a name="size"></a> Rozmiar 

 Zwraca liczbę elementów w tym kontenerze współbieżnych. Ta metoda jest bezpiecznym współbieżności.  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w kontenerze.  
  
### <a name="remarks"></a>Uwagi  
 Obecności równoczesnych operacji wstawienia liczba elementów w kontenerze równoczesnych mogą ulec zmianie natychmiast po wywołaniu tej funkcji, aby wartość zwracana jest nawet do odczytu.  
  
##  <a name="swap"></a> Swap 

 Zamienia zawartość dwóch `concurrent_unordered_map` obiektów. Ta metoda nie jest bezpieczne współbieżności.  
  
```
void swap(concurrent_unordered_map& _Umap);
```  
  
### <a name="parameters"></a>Parametry  
 `_Umap`  
 `concurrent_unordered_map` Obiektu wymiany.  
  
##  <a name="unsafe_begin"></a> unsafe_begin 

 Zwraca pierwszy element w tym kontenerze dla określonego przedziału iteratora.  
  
```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Bucket`  
 Indeks zasobnika.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazuje początek łańcucha iteratora.  
  
##  <a name="unsafe_bucket"></a> unsafe_bucket 

 Zwraca indeks zasobnika mapowanego określonego klucza w tym kontenerze.  
  
```
size_type unsafe_bucket(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parametry  
 `KVal`  
 Klucz elementu wyszukane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zasobnik indeks dla klucza w tym kontenerze.  
  
##  <a name="unsafe_bucket_count"></a> unsafe_bucket_count 

 Zwraca bieżącą liczbę przedziałów, w tym kontenerze.  
  
```
size_type unsafe_bucket_count() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca liczba przedziałów, w tym kontenerze.  
  
##  <a name="unsafe_bucket_size"></a> unsafe_bucket_size 

 Zwraca liczbę elementów w określonym przedziale tego kontenera.  
  
```
size_type unsafe_bucket_size(size_type _Bucket);
```  
  
### <a name="parameters"></a>Parametry  
 `_Bucket`  
 Zasobnik do wyszukania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca liczba przedziałów, w tym kontenerze.  
  
##  <a name="unsafe_cbegin"></a> unsafe_cbegin 

 Zwraca pierwszy element w tym kontenerze dla określonego przedziału iteratora.  
  
```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Bucket`  
 Indeks zasobnika.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazuje początek łańcucha iteratora.  
  
##  <a name="unsafe_cend"></a> unsafe_cend 

 Zwraca lokalizację pomyślne ostatni element w określonym przedziale iteratora.  
  
```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Bucket`  
 Indeks zasobnika.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazuje początek łańcucha iteratora.  
  
##  <a name="unsafe_end"></a> unsafe_end 

 Zwraca ostatni element w tym kontenerze dla określonego przedziału iteratora.  
  
```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Bucket`  
 Indeks zasobnika.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazuje na końcu łańcucha iteratora.  
  
##  <a name="unsafe_erase"></a> unsafe_erase 

 Usuwa elementy z `concurrent_unordered_map` w określonych pozycji. Ta metoda nie jest bezpieczne współbieżności.  
  
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
 `_Where`  
 Aby wymazać z pozycja iteratora.  
  
 `_Begin`  
 Pozycja pierwszego elementu w zakresie elementów ma zostać wymazane.  
  
 `_End`  
 Pozycja pierwszego elementu spoza zakresu elementów ma zostać wymazane.  
  
 `KVal`  
 Wartość klucza, aby wymazać.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy funkcji Członkowskich dwóch zwracać iterację wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte, lub `concurrent_unordered_map::end`(), jeśli nie zawiera żadnego takiego elementu. Trzeci funkcji członkowskiej zwraca liczbę elementów, które powoduje usunięcie.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy funkcji członkowskiej spowoduje usunięcie elementu w kontrolowanej sekwencji wskazywana przez `_Where`. Drugi funkcji członkowskiej usuwa elementy w zakresie [ `_Begin`, `_End`).  
  
 Trzeci funkcji członkowskiej usuwa elementy w zakresie rozdzielone `concurrent_unordered_map::equal_range`(KVal).  
  
##  <a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count 

 Zwraca maksymalną liczbę przedziałów, w tym kontenerze.  
  
```
size_type unsafe_max_bucket_count() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna liczba przedziałów, w tym kontenerze.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md)



