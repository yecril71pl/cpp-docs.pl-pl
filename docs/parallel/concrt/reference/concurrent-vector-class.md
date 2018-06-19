---
title: concurrent_vector — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::assign
- CONCURRENT_VECTOR/concurrency::concurrent_vector::at
- CONCURRENT_VECTOR/concurrency::concurrent_vector::back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::begin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::capacity
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::clear
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::empty
- CONCURRENT_VECTOR/concurrency::concurrent_vector::end
- CONCURRENT_VECTOR/concurrency::concurrent_vector::front
- CONCURRENT_VECTOR/concurrency::concurrent_vector::get_allocator
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_by
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_to_at_least
- CONCURRENT_VECTOR/concurrency::concurrent_vector::max_size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::push_back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::reserve
- CONCURRENT_VECTOR/concurrency::concurrent_vector::resize
- CONCURRENT_VECTOR/concurrency::concurrent_vector::shrink_to_fit
- CONCURRENT_VECTOR/concurrency::concurrent_vector::size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::swap
dev_langs:
- C++
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e120e072fb3f56788cbf39fbbc3887f5c816f4ef
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695356"
---
# <a name="concurrentvector-class"></a>concurrent_vector — Klasa
`concurrent_vector` Klasa jest klasą kontenerem sekwencji umożliwiająca losowe dostęp do dowolnych. Umożliwia bezpieczne współbieżności dołączenia, element dostępu, dostęp iteratora i operacji przechodzenia iteratora.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
 private details::_Concurrent_vector_base_v4;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych elementów, które mają być przechowywane w wektora.  
  
 `_Ax`  
 Typ reprezentujący obiekt alokatora przechowywane, który hermetyzuje szczegółowe informacje dotyczące alokacji i cofania alokacji pamięci dla jednoczesnych wektora. Ten argument jest opcjonalny, a wartość domyślna to `allocator<T>`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`allocator_type`|Typ, który reprezentuje klasę alokatora równoczesnych wektora.|  
|`const_iterator`|Typ, który udostępnia iteratora dostępie swobodnym, który może odczytać `const` elementów w wektorze równoczesnych.|  
|`const_pointer`|Typ, który dostarcza wskaźnik do `const` elementów w wektorze równoczesnych.|  
|`const_reference`|Typ, który zawiera odwołanie do `const` element przechowywane w równoczesnych wektorów do odczytu i wykonywania `const` operacji.|  
|`const_reverse_iterator`|Typ, który udostępnia iteratora dostępie swobodnym, który może odczytać `const` elementów w wektorze równoczesnych.|  
|`difference_type`|Typ, który udostępnia podpisem odległość między dwóch elementów w wektorze współbieżnych.|  
|`iterator`|Typ, który udostępnia iteratora dostępie swobodnym, który może odczytywać dowolny element w przypadku wektora współbieżnych. Modyfikacja elementu za pomocą iterator nie jest bezpieczne współbieżności.|  
|`pointer`|Typ, który dostarcza wskaźnik do elementu w przypadku wektora współbieżnych.|  
|`reference`|Typ, który zawiera odwołanie do elementu przechowywane w równoczesnych wektora.|  
|`reverse_iterator`|Typ, który udostępnia iteratora dostępie swobodnym, który może odczytywać dowolny element w odwróconej wektor współbieżnych. Modyfikacja elementu za pomocą iterator nie jest bezpieczne współbieżności.|  
|`size_type`|Typ, który oblicza liczbę elementów w wektorze współbieżnych.|  
|`value_type`|Typ, który reprezentuje typ danych przechowywanych w równoczesnych wektora.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[concurrent_vector](#ctor)|Przeciążone. Tworzy równoczesnych wektora.|  
|[~ concurrent_vector — destruktor](#dtor)|Usuwa wszystkie elementy i niszczy tego równoczesnych wektora.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Przypisz](#assign)|Przeciążone. Powoduje usunięcie elementów wektora jednoczesnych, a następnie przypisuje do niego albo `_N` kopie `_Item`, lub wartości określonych przez zakres iteratora [ `_Begin`, `_End`). Ta metoda nie jest bezpieczne współbieżności.|  
|[at](#at)|Przeciążone. Zapewnia dostęp do elementu pod danym indeksem w przypadku wektora współbieżnych. Ta metoda jest bezpieczne współbieżności dla operacji odczytu, a także podczas powiększania wektora, jak długo upewnieniu się, że wartość `_Index` jest mniejszy niż rozmiar wektora współbieżnych.|  
|[back](#back)|Przeciążone. Zwraca odwołanie lub a `const` odwołania do ostatniego elementu w równoczesnych wektora. Jeśli równoczesnych wektora jest pusta, zwracana wartość jest niezdefiniowany. Ta metoda jest bezpieczne współbieżności.|  
|[begin](#begin)|Przeciążone. Zwraca iteratora typu `iterator` lub `const_iterator` na początku równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.|  
|[pojemność](#capacity)|Zwraca maksymalny rozmiar do którego równoczesnych wektora bez konieczności przydzielenie większej ilości pamięci. Ta metoda jest bezpieczne współbieżności.|  
|[cbegin](#cbegin)|Zwraca iteratora typu `const_iterator` na początku równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.|  
|[cend](#cend)|Zwraca iteratora typu `const_iterator` na końcu równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.|  
|[Wyczyść](#clear)|Powoduje wymazanie wszystkich elementów w wektorze współbieżnych. Ta metoda nie jest bezpieczne współbieżności.|  
|[crbegin](#crbegin)|Zwraca iteratora typu `const_reverse_iterator` na początku równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.|  
|[crend](#crend)|Zwraca iteratora typu `const_reverse_iterator` na końcu równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.|  
|[pusty](#empty)|Testy, jeśli równoczesnych wektora jest pusta w momencie ta metoda jest wywoływana. Ta metoda jest bezpieczne współbieżności.|  
|[Koniec](#end)|Przeciążone. Zwraca iteratora typu `iterator` lub `const_iterator` na końcu równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.|  
|[Front](#front)|Przeciążone. Zwraca odwołanie lub a `const` odwołanie do pierwszego elementu w przypadku wektora współbieżnych. Jeśli równoczesnych wektora jest pusta, zwracana wartość jest niezdefiniowany. Ta metoda jest bezpieczne współbieżności.|  
|[get_allocator](#get_allocator)|Zwraca kopię programu przydzielania użyty do utworzenia wektora współbieżnych. Ta metoda jest bezpieczne współbieżności.|  
|[grow_by](#grow_by)|Przeciążone. Rozwoju tego równoczesnych wektor przez `_Delta` elementów. Ta metoda jest bezpieczne współbieżności.|  
|[grow_to_at_least](#grow_to_at_least)|Rozwoju tego równoczesnych wektora, dopóki nie będzie co najmniej `_N` elementów. Ta metoda jest bezpieczne współbieżności.|  
|[max_size](#max_size)|Zwraca maksymalną liczbę elementów, które może przechowywać równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.|  
|[push_back](#push_back)|Przeciążone. Dołącza podany element na końcu równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.|  
|[rbegin](#rbegin)|Przeciążone. Zwraca iteratora typu `reverse_iterator` lub `const_reverse_iterator` na początku równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.|  
|[rend](#rend)|Przeciążone. Zwraca iteratora typu `reverse_iterator` lub `const_reverse_iterator` na końcu równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.|  
|[reserve](#reserve)|Przydziela wystarczającej ilości miejsca do zwiększenia do rozmiaru wektora równoczesnych `_N` bez konieczności później przydzielenie większej ilości pamięci. Ta metoda nie jest bezpieczne współbieżności.|  
|[Zmiana rozmiaru](#resize)|Przeciążone. Zmienia rozmiar wektora równoczesnych żądany rozmiar, usunięcie lub dodawania elementów w razie potrzeby. Ta metoda nie jest bezpieczne współbieżności.|  
|[shrink_to_fit](#shrink_to_fit)|Kompaktuje reprezentacji wewnętrznej równoczesnych wektora zmniejszenie fragmentacji i optymalizować wykorzystanie pamięci. Ta metoda nie jest bezpieczne współbieżności.|  
|[Rozmiar](#size)|Zwraca liczbę elementów w wektorze współbieżnych. Ta metoda jest bezpieczne współbieżności.|  
|[swap](#swap)|Zamienia zawartość dwóch wektorów współbieżnych. Ta metoda nie jest bezpieczne współbieżności.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator]](#operator_at)|Przeciążone. Zapewnia dostęp do elementu pod danym indeksem w przypadku wektora współbieżnych. Ta metoda jest bezpieczne współbieżności dla operacji odczytu, a także podczas powiększania wektora, jak długo upewnieniu się, że wartość `_Index` jest mniejszy niż rozmiar wektora współbieżnych.|  
|[operator=](#operator_eq)|Przeciążone. Przypisuje zawartość innego `concurrent_vector` obiektu do tego. Ta metoda nie jest bezpieczne współbieżności.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać szczegółowe informacje na temat `concurrent_vector` , zobacz [równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `_Concurrent_vector_base_v4`  
  
 `_Allocator_base`  
  
 `concurrent_vector`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concurrent_vector.h  
  
 **Namespace:** współbieżności  
  
##  <a name="assign"></a> Przypisz 

 Powoduje usunięcie elementów wektora jednoczesnych, a następnie przypisuje do niego albo `_N` kopie `_Item`, lub wartości określonych przez zakres iteratora [ `_Begin`, `_End`). Ta metoda nie jest bezpieczne współbieżności.  
  
```
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```  
  
### <a name="parameters"></a>Parametry  
 `_InputIterator`  
 Typ określony iteratora.  
  
 `_N`  
 Liczba elementów, które ma zostać skopiowany do równoczesnych wektora.  
  
 `_Item`  
 Odwołanie do wartość używaną do wypełniania równoczesnych wektora.  
  
 `_Begin`  
 Pierwszy element źródłowy zakres iteratora.  
  
 `_End`  
 Iterator do jednego po ostatnim elemencie zakresu źródła.  
  
### <a name="remarks"></a>Uwagi  
 `assign` nie jest bezpieczne współbieżności. Należy się upewnić, że nie ma innych wątków są wywoływanie metod na równoczesnych wektor podczas wywoływania tej metody.  
  
##  <a name="at"></a> w 

 Zapewnia dostęp do elementu pod danym indeksem w przypadku wektora współbieżnych. Ta metoda jest bezpieczne współbieżności dla operacji odczytu, a także podczas powiększania wektora, jak długo upewnieniu się, że wartość `_Index` jest mniejszy niż rozmiar wektora współbieżnych.  
  
```
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Indeks elementu do pobrania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do elementu pod danym indeksem.  
  
### <a name="remarks"></a>Uwagi  
 Wersja funkcji `at` zwracającą niż `const` odwołania nie można użyć jednocześnie zapisu do elementu w różnych wątkach. Obiekt inny synchronizacji należy zsynchronizować równoczesnych odczytu i zapisu do tego samego elementu danych.  
  
 Metoda zgłasza `out_of_range` Jeśli `_Index` jest większe lub równe rozmiarowi równoczesnych wektora i `range_error` Jeśli indeks jest uszkodzony części wektora. Szczegółowe informacje dotyczące sposobu wektora może to spowodować, zobacz [równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
##  <a name="back"></a> Wstecz 

 Zwraca odwołanie lub a `const` odwołania do ostatniego elementu w równoczesnych wektora. Jeśli równoczesnych wektora jest pusta, zwracana wartość jest niezdefiniowany. Ta metoda jest bezpieczne współbieżności.  
  
```
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie lub a `const` odwołania do ostatniego elementu w równoczesnych wektora.  
  
##  <a name="begin"></a> Rozpocznij 

 Zwraca iteratora typu `iterator` lub `const_iterator` na początku równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora typu `iterator` lub `const_iterator` na początku równoczesnych wektora.  
  
##  <a name="capacity"></a> pojemność 

 Zwraca maksymalny rozmiar do którego równoczesnych wektora bez konieczności przydzielenie większej ilości pamięci. Ta metoda jest bezpieczne współbieżności.  
  
```
size_type capacity() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalny rozmiar do którego równoczesnych wektora bez konieczności przydzielenie większej ilości pamięci.  
  
### <a name="remarks"></a>Uwagi  
 W odróżnieniu od standardowej biblioteki C++ `vector`, `concurrent_vector` obiektu nie przenosi istniejących elementów, jeśli przydzielania pamięci.  
  
##  <a name="cbegin"></a> cbegin 

 Zwraca iteratora typu `const_iterator` na początku równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora typu `const_iterator` na początku równoczesnych wektora.  
  
##  <a name="cend"></a> cend 

 Zwraca iteratora typu `const_iterator` na końcu równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora typu `const_iterator` na końcu równoczesnych wektora.  
  
##  <a name="clear"></a> Wyczyść 

 Powoduje wymazanie wszystkich elementów w wektorze współbieżnych. Ta metoda nie jest bezpieczne współbieżności.  
  
```
void clear();
```  
  
### <a name="remarks"></a>Uwagi  
 `clear` nie jest bezpieczne współbieżności. Należy się upewnić, że nie ma innych wątków są wywoływanie metod na równoczesnych wektor podczas wywoływania tej metody. `clear` nie spowoduje zwolnienia wewnętrzny tablic. Aby zwolnić wewnętrzny tablic, wywołaj funkcję `shrink_to_fit` po `clear`.  
  
##  <a name="ctor"></a> concurrent_vector — 

 Tworzy równoczesnych wektora.  
  
```
explicit concurrent_vector(
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector(
    const concurrent_vector<T,
    M>& _Vector,
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    concurrent_vector&& _Vector);

explicit concurrent_vector(
    size_type _N);

concurrent_vector(
    size_type _N,
    const_reference _Item,
    const allocator_type& _Al = allocator_type());

template<class _InputIterator>
concurrent_vector(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());
```  
  
### <a name="parameters"></a>Parametry  
 `M`  
 Typ alokatora wektorze źródłowym.  
  
 `_InputIterator`  
 Typ iteratora wejściowego.  
  
 `_Al`  
 Klasa alokatora do wykorzystania z tym obiektem.  
  
 `_Vector`  
 Źródło `concurrent_vector` obiekt, aby skopiować lub przenieść elementy z.  
  
 `_N`  
 Początkowa pojemność `concurrent_vector` obiektu.  
  
 `_Item`  
 Wartość elementów w skonstruowanego obiektu.  
  
 `_Begin`  
 Pozycja pierwszego elementu w zakresie elementów do skopiowania.  
  
 `_End`  
 Pozycja pierwszego elementu poza zakres elementów do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie konstruktory zapisania obiektu alokatora `_Al` i wektor inicjowania.  
  
 Pierwszy Konstruktor Określ pusty wektor początkowej i jawnie określa typ przydzielania. do użytku.  
  
 Konstruktory drugiego i trzeciego Określ kopię równoczesnych wektor `_Vector`.  
  
 Konstruktor czwarty określa przenoszenia równoczesnych wektora `_Vector`.  
  
 Konstruktor piątej określa powtórzenia określonej liczby ( `_N`) elementów wartości domyślnej dla klasy `T`.  
  
 Konstruktor szóstego określa powtórzenia ( `_N`) elementy wartości `_Item`.  
  
 Konstruktor ostatniego określa wartości dostarczone przez zakres iteratora [ `_Begin`, `_End`).  
  
##  <a name="dtor"></a> ~ concurrent_vector — 

 Usuwa wszystkie elementy i niszczy tego równoczesnych wektora.  
  
```
~concurrent_vector();
```  
  
##  <a name="crbegin"></a> crbegin 

 Zwraca iteratora typu `const_reverse_iterator` na początku równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.  
  
```
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora typu `const_reverse_iterator` na początku równoczesnych wektora.  
  
##  <a name="crend"></a> crend 

 Zwraca iteratora typu `const_reverse_iterator` na końcu równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.  
  
```
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora typu `const_reverse_iterator` na końcu równoczesnych wektora.  
  
##  <a name="empty"></a> pusty 

 Testy, jeśli równoczesnych wektora jest pusta w momencie ta metoda jest wywoływana. Ta metoda jest bezpieczne współbieżności.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli wektor był pusty w tej chwili wywołano funkcję `false` inaczej.  
  
##  <a name="end"></a> Koniec 

 Zwraca iteratora typu `iterator` lub `const_iterator` na końcu równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora typu `iterator` lub `const_iterator` na końcu równoczesnych wektora.  
  
##  <a name="front"></a> Front 

 Zwraca odwołanie lub a `const` odwołanie do pierwszego elementu w przypadku wektora współbieżnych. Jeśli równoczesnych wektora jest pusta, zwracana wartość jest niezdefiniowany. Ta metoda jest bezpieczne współbieżności.  
  
```
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie lub a `const` odwołanie do pierwszego elementu w przypadku wektora współbieżnych.  
  
##  <a name="get_allocator"></a> get_allocator 

 Zwraca kopię programu przydzielania użyty do utworzenia wektora współbieżnych. Ta metoda jest bezpieczne współbieżności.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kopia programu przydzielania użyta do skonstruowania `concurrent_vector` obiektu.  
  
##  <a name="grow_by"></a> grow_by 

 Rozwoju tego równoczesnych wektor przez `_Delta` elementów. Ta metoda jest bezpieczne współbieżności.  
  
```
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```  
  
### <a name="parameters"></a>Parametry  
 `_Delta`  
 Liczba elementów do dołączenia do obiektu.  
  
 `_Item`  
 Wartość zainicjować nowe elementy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dołączany iteratora do pierwszego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `_Item` nie zostanie określony, nowe elementy są domyślne skonstruowany.  
  
##  <a name="grow_to_at_least"></a> grow_to_at_least 

 Rozwoju tego równoczesnych wektora, dopóki nie będzie co najmniej `_N` elementów. Ta metoda jest bezpieczne współbieżności.  
  
```
iterator grow_to_at_least(size_type _N);
```  
  
### <a name="parameters"></a>Parametry  
 `_N`  
 Nowy rozmiar minimalny `concurrent_vector` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora wskazujące na początku sekwencji dołączany lub element pod indeksem `_N` jeśli zostały dołączone nie elementy.  
  
##  <a name="max_size"></a> max_size 

 Zwraca maksymalną liczbę elementów, które może przechowywać równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna liczba elementów `concurrent_vector` obiekt może przechowywać.  
  
##  <a name="operator_eq"></a> operator = 

 Przypisuje zawartość innego `concurrent_vector` obiektu do tego. Ta metoda nie jest bezpieczne współbieżności.  
  
```
concurrent_vector& operator= (
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector& operator= (
    const concurrent_vector<T, M>& _Vector);

concurrent_vector& operator= (
    concurrent_vector&& _Vector);
```  
  
### <a name="parameters"></a>Parametry  
 `M`  
 Typ alokatora wektorze źródłowym.  
  
 `_Vector`  
 Źródło `concurrent_vector` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego `concurrent_vector` obiektu.  
  
##  <a name="operator_at"></a> Operator] 

 Zapewnia dostęp do elementu pod danym indeksem w przypadku wektora współbieżnych. Ta metoda jest bezpieczne współbieżności dla operacji odczytu, a także podczas powiększania wektora, jak długo upewnieniu się, że wartość `_Index` jest mniejszy niż rozmiar wektora współbieżnych.  
  
```
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Indeks elementu do pobrania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do elementu pod danym indeksem.  
  
### <a name="remarks"></a>Uwagi  
 Wersja `operator []` zwracającą niż `const` odwołania nie można użyć jednocześnie zapisu do elementu w różnych wątkach. Obiekt inny synchronizacji należy zsynchronizować równoczesnych odczytu i zapisu do tego samego elementu danych.  
  
 Nie granice sprawdzanie jest wykonywane w celu zapewnienia, że `_Index` jest prawidłowym indeksem w równoczesnych wektora.  
  
##  <a name="push_back"></a> push_back 

 Dołącza podany element na końcu równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.  
  
```
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```  
  
### <a name="parameters"></a>Parametry  
 `_Item`  
 Wartość do dołączenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dołączany iteratora do elementu.  
  
##  <a name="rbegin"></a> rbegin 

 Zwraca iteratora typu `reverse_iterator` lub `const_reverse_iterator` na początku równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.  
  
```
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora typu `reverse_iterator` lub `const_reverse_iterator` na początku równoczesnych wektora.  
  
##  <a name="rend"></a> rend 

 Zwraca iteratora typu `reverse_iterator` lub `const_reverse_iterator` na końcu równoczesnych wektora. Ta metoda jest bezpieczne współbieżności.  
  
```
reverse_iterator rend();

const_reverse_iterator rend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora typu `reverse_iterator` lub `const_reverse_iterator` na końcu równoczesnych wektora.  
  
##  <a name="reserve"></a> rezerwowa 

 Przydziela wystarczającej ilości miejsca do zwiększenia do rozmiaru wektora równoczesnych `_N` bez konieczności później przydzielenie większej ilości pamięci. Ta metoda nie jest bezpieczne współbieżności.  
  
```
void reserve(size_type _N);
```  
  
### <a name="parameters"></a>Parametry  
 `_N`  
 Liczba elementów, aby zarezerwować miejsce.  
  
### <a name="remarks"></a>Uwagi  
 `reserve` nie jest bezpieczne współbieżności. Należy się upewnić, że nie ma innych wątków są wywoływanie metod na równoczesnych wektor podczas wywoływania tej metody. Pojemność równoczesnych wektora po metoda zwraca może być większy niż żądany rezerwacji.  
  
##  <a name="resize"></a> Zmiana rozmiaru 

 Zmienia rozmiar wektora równoczesnych żądany rozmiar, usunięcie lub dodawania elementów w razie potrzeby. Ta metoda nie jest bezpieczne współbieżności.  
  
```
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```  
  
### <a name="parameters"></a>Parametry  
 `_N`  
 Nowy rozmiar concurrent_vector —.  
  
 `val`  
 Wartość nowe elementy dodane do wektora, jeśli nowy rozmiar jest większy niż oryginalny rozmiar. W przypadku pominięcia wartości nowe obiekty są przypisywane wartość domyślna dla jego typu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli rozmiar kontenera jest mniejsza niż żądany rozmiar, elementy są dodawane do wektora, dopóki nie osiągnie żądanego rozmiaru. Jeśli rozmiar kontenera jest większy niż żądany rozmiar, najbliżej końca kontenera elementy są usuwane aż do kontenera osiągnie rozmiar `_N`. Jeśli występuje rozmiar kontenera jest taki sam jak żądany rozmiar, nie podjęto żadnej akcji.  
  
 `resize` nie jest współbieżności bezpieczne. Należy się upewnić, że nie ma innych wątków są wywoływanie metod na równoczesnych wektor podczas wywoływania tej metody.  
  
##  <a name="shrink_to_fit"></a> shrink_to_fit 

 Kompaktuje reprezentacji wewnętrznej równoczesnych wektora zmniejszenie fragmentacji i optymalizować wykorzystanie pamięci. Ta metoda nie jest bezpieczne współbieżności.  
  
```
void shrink_to_fit();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda będzie wewnętrznie ponownie przydzielić pamięci przenoszenia elementów, unieważnienie wszystkich Iteratory. `shrink_to_fit` nie jest bezpieczne współbieżności. Należy się upewnić, że nie ma innych wątków są wywoływanie metod na równoczesnych wektor podczas wywoływania tej funkcji.  
  
##  <a name="size"></a> Rozmiar 

 Zwraca liczbę elementów w wektorze współbieżnych. Ta metoda jest bezpieczne współbieżności.  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w tym `concurrent_vector` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Zwrócony rozmiar jest zagwarantować uwzględnienie wszystkich elementów przez wywołania funkcji `push_back`, lub zwiększ operacje, które zostały ukończone przed wywołaniem tej metody. Jednak może również obejmować elementy, które są przydzielane, ale nadal konstruowanego współbieżnych wywołań dowolnej z metod wzrostu.  
  
##  <a name="swap"></a> Swap 

 Zamienia zawartość dwóch wektorów współbieżnych. Ta metoda nie jest bezpieczne współbieżności.  
  
```
void swap(concurrent_vector& _Vector);
```  
  
### <a name="parameters"></a>Parametry  
 `_Vector`  
 `concurrent_vector` Obiekt do wymiany zawartości z.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md)



