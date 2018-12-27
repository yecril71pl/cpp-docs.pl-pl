---
title: concurrent_vector — Klasa
ms.date: 11/04/2016
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
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
ms.openlocfilehash: e8036b0942600e5d47254583e2675c525010a5c1
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657568"
---
# <a name="concurrentvector-class"></a>concurrent_vector — Klasa

`concurrent_vector` Klasy jest klasą kontenera sekwencji, która zezwala na dostępie do dowolnego elementu. Umożliwia bezpieczne pod względem współbieżności dołączyć element dostępu, dostępu do iteratora i operacji przechodzenia iteratora.

## <a name="syntax"></a>Składnia

```
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
private details::_Concurrent_vector_base_v4;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów, które mają być przechowywane w wektorze.

*_Ax*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i dezalokacji pamięci współbieżnego wektora. Ten argument jest opcjonalny, a wartość domyślna to `allocator<T>`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`allocator_type`|Typ, który reprezentuje klasę alokatora dla współbieżnego wektora.|
|`const_iterator`|Typ zapewniający iterator dostępu swobodnego, który może odczytać `const` element współbieżnego wektora.|
|`const_pointer`|Typ, który dostarcza wskaźnik do `const` element współbieżnego wektora.|
|`const_reference`|Typ, który zawiera odwołanie do `const` elementu przechowywanego w współbieżnego wektora do odczytu i wykonywania `const` operacji.|
|`const_reverse_iterator`|Typ zapewniający iterator dostępu swobodnego, który może odczytać dowolny `const` element współbieżnego wektora.|
|`difference_type`|Typ, który zawiera podpisaną odległość między dwoma elementami w współbieżnego wektora.|
|`iterator`|Typ, który dostarcza iterator dostępu swobodnego, który może odczytać dowolny element w współbieżnego wektora. Modyfikacja elementu za pomocą iterator który nie jest bezpieczna pod kątem współbieżności.|
|`pointer`|Typ, który dostarcza wskaźnik do elementu w współbieżnego wektora.|
|`reference`|Typ, który zawiera odwołanie do elementu przechowywanego w współbieżnego wektora.|
|`reverse_iterator`|Typ, który dostarcza iterator dostępu swobodnego, który może odczytać dowolny element w odwróconej współbieżnego wektora. Modyfikacja elementu za pomocą iterator który nie jest bezpieczna pod kątem współbieżności.|
|`size_type`|Typ, który zlicza liczbę elementów w współbieżnego wektora.|
|`value_type`|Typ, który reprezentuje typ danych przechowywanych w współbieżnego wektora.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[concurrent_vector](#ctor)|Przeciążone. Tworzy równoległy wektor.|
|[~ concurrent_vector — destruktor](#dtor)|Usuwa wszystkie elementy i niszczy to współbieżnego wektora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Przypisz](#assign)|Przeciążone. Usuwa elementy współbieżnego wektora i przypisuje do niego albo `_N` kopie `_Item`, lub wartości określonych przez zakres iteratora [ `_Begin`, `_End`). Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[at](#at)|Przeciążone. Zapewnia dostęp do elementu pod danym indeksem współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności dla operacji odczytu, a także podczas powiększania wektora, tak długo, jak upewnieniu się, że wartość `_Index` jest mniejszy niż rozmiar współbieżnego wektora.|
|[back](#back)|Przeciążone. Zwraca odwołanie lub a `const` odwoływać się do ostatniego elementu w współbieżnego wektora. Jeśli współbieżnego wektora jest pusta, zwracana wartość jest niezdefiniowana. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[begin](#begin)|Przeciążone. Zwraca iterator typu `iterator` lub `const_iterator` na początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[Pojemność](#capacity)|Zwraca maksymalny rozmiar, do którego współbieżnego wektora można rozwijać bez konieczności przydzielanie większej ilości pamięci. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[cbegin](#cbegin)|Zwraca iterator typu `const_iterator` na początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[cend](#cend)|Zwraca iterator typu `const_iterator` w celu współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[Usuń zaznaczenie](#clear)|Usuwa wszystkie elementy w współbieżnego wektora. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[crbegin](#crbegin)|Zwraca iterator typu `const_reverse_iterator` na początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[crend —](#crend)|Zwraca iterator typu `const_reverse_iterator` w celu współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[pusty](#empty)|Sprawdza, czy współbieżnego wektora jest pusta, gdy ta metoda jest wywoływana. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[koniec](#end)|Przeciążone. Zwraca iterator typu `iterator` lub `const_iterator` w celu współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[Frontonu](#front)|Przeciążone. Zwraca odwołanie lub a `const` odwołanie do pierwszego elementu w współbieżnego wektora. Jeśli współbieżnego wektora jest pusta, zwracana wartość jest niezdefiniowana. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu programu przydzielania użytego do stworzenia współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[grow_by](#grow_by)|Przeciążone. Powiększa się tym współbieżnego wektora przez `_Delta` elementów. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[grow_to_at_least](#grow_to_at_least)|Powiększa się tym współbieżnego wektora, dopóki nie jest to co najmniej `_N` elementów. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[max_size](#max_size)|Zwraca maksymalną liczbę elementów, które może przechowywać współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[push_back](#push_back)|Przeciążone. Dołącza określony element do końca współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[rbegin](#rbegin)|Przeciążone. Zwraca iterator typu `reverse_iterator` lub `const_reverse_iterator` na początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[rend —](#rend)|Przeciążone. Zwraca iterator typu `reverse_iterator` lub `const_reverse_iterator` w celu współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[reserve](#reserve)|Przydziela wystarczająca ilość miejsca na rozwój współbieżnego wektora rozmiarowi `_N` bez konieczności dalszej przydzielanie większej ilości pamięci. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[Zmiana rozmiaru](#resize)|Przeciążone. Zmienia rozmiar współbieżnego wektora żądany rozmiar, usuwanie lub dodawanie elementów zgodnie z potrzebami. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[shrink_to_fit](#shrink_to_fit)|Kompaktuje wewnętrznej reprezentacji współbieżnego wektora, aby ograniczyć fragmentację i zoptymalizowania użycia pamięci. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[Rozmiar](#size)|Zwraca liczbę elementów w współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[swap](#swap)|Zamienia zawartości dwóch wektorów współbieżnych. Ta metoda nie jest bezpieczna pod kątem współbieżności.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Operator\[\]](#operator_at)|Przeciążone. Zapewnia dostęp do elementu pod danym indeksem współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności dla operacji odczytu, a także podczas powiększania wektora, tak długo, jak upewnieniu się, że wartość `_Index` jest mniejszy niż rozmiar współbieżnego wektora.|
|[operator=](#operator_eq)|Przeciążone. Przypisuje zawartość innego `concurrent_vector` obiektu do wskazanego. Ta metoda nie jest bezpieczna pod kątem współbieżności.|

## <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje na temat `concurrent_vector` klasy, zobacz [równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_Concurrent_vector_base_v4`

`_Allocator_base`

`concurrent_vector`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concurrent_vector.h

**Namespace:** współbieżności

##  <a name="assign"></a> Przypisz

Usuwa elementy współbieżnego wektora i przypisuje do niego albo `_N` kopie `_Item`, lub wartości określonych przez zakres iteratora [ `_Begin`, `_End`). Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>Parametry

*_InputIterator*<br/>
Typ iteratora określony.

*_N*<br/>
Liczba elementów do skopiowania do współbieżnego wektora.

*_Element*<br/>
Odwołanie do wartości, używany do wypełniania współbieżnego wektora.

*_Rozpocznij*<br/>
Iterator do pierwszego elementu w zakresie źródłowym.

*_Zakończ*<br/>
Iterator do pierwszego ostatniego elementu w zakresie źródłowym.

### <a name="remarks"></a>Uwagi

`assign` nie jest bezpieczna pod kątem współbieżności. Należy się upewnić, że nie ma innych wątków są wywoływanie metod na współbieżnego wektora, gdy chcesz wywołać tę metodę.

##  <a name="at"></a> w

Zapewnia dostęp do elementu pod danym indeksem współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności dla operacji odczytu, a także podczas powiększania wektora, tak długo, jak upewnieniu się, że wartość `_Index` jest mniejszy niż rozmiar współbieżnego wektora.

```
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
Indeks elementu do pobrania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu pod danym indeksem.

### <a name="remarks"></a>Uwagi

Wersja tej funkcji `at` zwracającego innej niż `const` odwołanie, nie można jednocześnie zapis elementu z różnych wątków. Obiekt synchronizacji różnych należy zsynchronizować współbieżne odczytu i zapisu do tego samego elementu danych.

Metoda zgłasza `out_of_range` Jeśli `_Index` jest większa niż lub równy rozmiarowi współbieżnego wektora i `range_error` Jeśli indeks jest uszkodzony część wektora. Aby uzyskać szczegółowe informacje dotyczące sposobu wektor może stać się uszkodzone, zobacz [równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md).

##  <a name="back"></a> Wstecz

Zwraca odwołanie lub a `const` odwoływać się do ostatniego elementu w współbieżnego wektora. Jeśli współbieżnego wektora jest pusta, zwracana wartość jest niezdefiniowana. Ta metoda jest bezpieczna pod kątem współbieżności.

```
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie lub a `const` odwoływać się do ostatniego elementu w współbieżnego wektora.

##  <a name="begin"></a> Rozpocznij

Zwraca iterator typu `iterator` lub `const_iterator` na początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `iterator` lub `const_iterator` na początku współbieżnego wektora.

##  <a name="capacity"></a> Pojemność

Zwraca maksymalny rozmiar, do którego współbieżnego wektora można rozwijać bez konieczności przydzielanie większej ilości pamięci. Ta metoda jest bezpieczna pod kątem współbieżności.

```
size_type capacity() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalny rozmiar, do którego współbieżnego wektora można rozwijać bez konieczności przydzielanie większej ilości pamięci.

### <a name="remarks"></a>Uwagi

W odróżnieniu od standardowej biblioteki języka C++ `vector`, `concurrent_vector` obiektu nie przenosi istniejących elementów, jeśli przydziela większej ilości pamięci.

##  <a name="cbegin"></a> cbegin —

Zwraca iterator typu `const_iterator` na początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `const_iterator` na początku współbieżnego wektora.

##  <a name="cend"></a> cend

Zwraca iterator typu `const_iterator` w celu współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `const_iterator` w celu współbieżnego wektora.

##  <a name="clear"></a> Usuń zaznaczenie

Usuwa wszystkie elementy w współbieżnego wektora. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
void clear();
```

### <a name="remarks"></a>Uwagi

`clear` nie jest bezpieczna pod kątem współbieżności. Należy się upewnić, że nie ma innych wątków są wywoływanie metod na współbieżnego wektora, gdy chcesz wywołać tę metodę. `clear` nie spowoduje zwolnienia wewnętrznych tablic. Aby zwolnić wewnętrznych tablic, wywołaj funkcję `shrink_to_fit` po `clear`.

##  <a name="ctor"></a> concurrent_vector —

Tworzy równoległy wektor.

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

*M*<br/>
Typ programu przydzielania wektora źródła.

*_InputIterator*<br/>
Typ iteratora wejściowego.

*_Al*<br/>
Klasa alokatora do wykorzystania z tym obiektem.

*_Vector*<br/>
Źródło `concurrent_vector` obiektu do kopiowania lub przenoszenia elementów z.

*_N*<br/>
Pojemność `concurrent_vector` obiektu.

*_Element*<br/>
Wartość elementów w utworzonym obiekcie.

*_Rozpocznij*<br/>
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*_Zakończ*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują obiekt programu przydzielania `_Al` i inicjują wektor.

Pierwszy Konstruktor Określ pusty wektor wstępny i wyraźnie określa typ programu przydzielania. ma być używany.

Drugi i trzeci Konstruktor określają kopię współbieżnego wektora `_Vector`.

Czwarty Konstruktor Określa przeniesienie współbieżnego wektora `_Vector`.

Piąty Konstruktor określa powtórzenie określonej liczby ( `_N`) elementów wartości domyślnej dla klasy `T`.

Szósty Konstruktor określa powtórzenia ( `_N`) elementów wartości `_Item`.

Ostatni Konstruktor określa wartości dostarczone przez zakres iteratora [ `_Begin`, `_End`).

##  <a name="dtor"></a> ~ concurrent_vector

Usuwa wszystkie elementy i niszczy to współbieżnego wektora.

```
~concurrent_vector();
```

##  <a name="crbegin"></a> crbegin —

Zwraca iterator typu `const_reverse_iterator` na początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `const_reverse_iterator` na początku współbieżnego wektora.

##  <a name="crend"></a> crend —

Zwraca iterator typu `const_reverse_iterator` w celu współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `const_reverse_iterator` w celu współbieżnego wektora.

##  <a name="empty"></a> pusty

Sprawdza, czy współbieżnego wektora jest pusta, gdy ta metoda jest wywoływana. Ta metoda jest bezpieczna pod kątem współbieżności.

```
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wektora był pusty w tej chwili funkcja została wywołana, **false** inaczej.

##  <a name="end"></a> koniec

Zwraca iterator typu `iterator` lub `const_iterator` w celu współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `iterator` lub `const_iterator` w celu współbieżnego wektora.

##  <a name="front"></a> Frontonu

Zwraca odwołanie lub a `const` odwołanie do pierwszego elementu w współbieżnego wektora. Jeśli współbieżnego wektora jest pusta, zwracana wartość jest niezdefiniowana. Ta metoda jest bezpieczna pod kątem współbieżności.

```
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie lub a `const` odwołanie do pierwszego elementu w współbieżnego wektora.

##  <a name="get_allocator"></a> get_allocator —

Zwraca kopię obiektu programu przydzielania użytego do stworzenia współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Kopię alokator używany do budowy `concurrent_vector` obiektu.

##  <a name="grow_by"></a> grow_by —

Powiększa się tym współbieżnego wektora przez `_Delta` elementów. Ta metoda jest bezpieczna pod kątem współbieżności.

```
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```

### <a name="parameters"></a>Parametry

*_Delta*<br/>
Liczba elementów do dołączenia do obiektu.

*_Element*<br/>
Wartość można zainicjować nowe elementy.

### <a name="return-value"></a>Wartość zwracana

Iterator do pierwszego elementu dołączane.

### <a name="remarks"></a>Uwagi

Jeśli `_Item` nie zostanie określony, nowe elementy są domyślne.

##  <a name="grow_to_at_least"></a> grow_to_at_least —

Powiększa się tym współbieżnego wektora, dopóki nie jest to co najmniej `_N` elementów. Ta metoda jest bezpieczna pod kątem współbieżności.

```
iterator grow_to_at_least(size_type _N);
```

### <a name="parameters"></a>Parametry

*_N*<br/>
Nowy rozmiar minimalny `concurrent_vector` obiektu.

### <a name="return-value"></a>Wartość zwracana

Iterator, który wskazuje na początku sekwencji dołączonych lub element w indeksie `_N` Jeśli elementy nie zostały dołączone.

##  <a name="max_size"></a> max_size —

Zwraca maksymalną liczbę elementów, które może przechowywać współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba elementów `concurrent_vector` obiekt może przechowywać.

##  <a name="operator_eq"></a> operator =

Przypisuje zawartość innego `concurrent_vector` obiektu do wskazanego. Ta metoda nie jest bezpieczna pod kątem współbieżności.

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

*M*<br/>
Typ programu przydzielania wektora źródła.

*_Vector*<br/>
Źródło `concurrent_vector` obiektu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `concurrent_vector` obiektu.

##  <a name="operator_at"></a> Operator]

Zapewnia dostęp do elementu pod danym indeksem współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności dla operacji odczytu, a także podczas powiększania wektora, tak długo, jak upewnieniu się, że wartość `_Index` jest mniejszy niż rozmiar współbieżnego wektora.

```
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
Indeks elementu do pobrania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu pod danym indeksem.

### <a name="remarks"></a>Uwagi

Wersja `operator []` zwracającego innej niż `const` odwołanie, nie można jednocześnie zapis elementu z różnych wątków. Obiekt synchronizacji różnych należy zsynchronizować współbieżne odczytu i zapisu do tego samego elementu danych.

Nie granice sprawdzanie jest wykonywane, aby upewnić się, że `_Index` jest prawidłowy indeks do współbieżnego wektora.

##  <a name="push_back"></a> push_back —

Dołącza określony element do końca współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```

### <a name="parameters"></a>Parametry

*_Element*<br/>
Wartość do dołączenia.

### <a name="return-value"></a>Wartość zwracana

Iterator do elementu dołączane.

##  <a name="rbegin"></a> rbegin —

Zwraca iterator typu `reverse_iterator` lub `const_reverse_iterator` na początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `reverse_iterator` lub `const_reverse_iterator` na początku współbieżnego wektora.

##  <a name="rend"></a> rend —

Zwraca iterator typu `reverse_iterator` lub `const_reverse_iterator` w celu współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```
reverse_iterator rend();

const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `reverse_iterator` lub `const_reverse_iterator` w celu współbieżnego wektora.

##  <a name="reserve"></a> Zarezerwuj

Przydziela wystarczająca ilość miejsca na rozwój współbieżnego wektora rozmiarowi `_N` bez konieczności dalszej przydzielanie większej ilości pamięci. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
void reserve(size_type _N);
```

### <a name="parameters"></a>Parametry

*_N*<br/>
Liczba elementów, aby zarezerwować miejsce.

### <a name="remarks"></a>Uwagi

`reserve` nie jest bezpieczna pod kątem współbieżności. Należy się upewnić, że nie ma innych wątków są wywoływanie metod na współbieżnego wektora, gdy chcesz wywołać tę metodę. Pojemność współbieżnego wektora po powrocie z metody może być większy niż żądany rezerwacji.

##  <a name="resize"></a> Zmiana rozmiaru

Zmienia rozmiar współbieżnego wektora żądany rozmiar, usuwanie lub dodawanie elementów zgodnie z potrzebami. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```

### <a name="parameters"></a>Parametry

*_N*<br/>
Nowy rozmiar concurrent_vector.

*Val*<br/>
Wartość nowe elementy dodane do wektora, jeśli nowy rozmiar jest większy niż rozmiar oryginalnego. Jeśli wartość zostanie pominięty, nowe obiekty są przypisywane wartością domyślną dla ich typu.

### <a name="remarks"></a>Uwagi

Jeśli rozmiar kontenera jest mniejszy niż żądany rozmiar, elementy są dodawane do wektora, aż do osiągnięcia żądanego rozmiaru. Jeśli rozmiar kontenera jest większy niż żądany rozmiar, najbliższe końca kontener elementów są usuwane, dopóki nie osiągnie rozmiar kontenera `_N`. Jeśli obecny rozmiar kontenera jest taki sam jak żądany rozmiar, nie podjęto żadnej akcji.

`resize` nie jest współbieżności bezpieczne. Należy się upewnić, że nie ma innych wątków są wywoływanie metod na współbieżnego wektora, gdy chcesz wywołać tę metodę.

##  <a name="shrink_to_fit"></a> shrink_to_fit —

Kompaktuje wewnętrznej reprezentacji współbieżnego wektora, aby ograniczyć fragmentację i zoptymalizowania użycia pamięci. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
void shrink_to_fit();
```

### <a name="remarks"></a>Uwagi

Ta metoda będzie wewnętrznie ponownie przydzielić pamięci przenoszenia elementów, co unieważniło wszystkie Iteratory. `shrink_to_fit` nie jest bezpieczna pod kątem współbieżności. Należy się upewnić, że nie ma innych wątków jest wywoływanie metod na współbieżnego wektora, po wywołaniu tej funkcji.

##  <a name="size"></a> Rozmiar

Zwraca liczbę elementów w współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tym `concurrent_vector` obiektu.

### <a name="remarks"></a>Uwagi

Rozmiar zwrócony jest gwarantowane, obejmują wszystkie elementy, które dołączono wywołań funkcji `push_back`, lub operacji, które zostały wykonane przed wywołaniem tej metody. Jednak również mogą zawierać elementy, które są przydzielane, ale nadal w konstrukcji współbieżnych wywołań dowolnej z metod wzrostu.

##  <a name="swap"></a> swap

Zamienia zawartości dwóch wektorów współbieżnych. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
void swap(concurrent_vector& _Vector);
```

### <a name="parameters"></a>Parametry

*_Vector*<br/>
`concurrent_vector` Obiekt do wymiany zawartości z.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md)

