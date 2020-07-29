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
ms.openlocfilehash: 9144fd0870bfb72e923a7271ffdd655e03a9bd57
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215845"
---
# <a name="concurrent_vector-class"></a>concurrent_vector — Klasa

`concurrent_vector`Klasa jest klasą kontenera sekwencji, która umożliwia losowy dostęp do dowolnego elementu. Umożliwia ona bezpieczne łączenie, dostęp do elementów, dostęp iteratora i operacje przechodzenia iteratora. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia.

## <a name="syntax"></a>Składnia

```cpp
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
private details::_Concurrent_vector_base_v4;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów, które mają być przechowywane w wektorze.

*_Ax*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i dealokacji pamięci dla współbieżnego wektora. Ten argument jest opcjonalny, a wartość domyślna to `allocator<T>` .

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`allocator_type`|Typ, który reprezentuje klasę alokatora dla współbieżnego wektora.|
|`const_iterator`|Typ, który dostarcza Iterator dostępu swobodnego, który może odczytywać **`const`** element w współbieżnym wektorze.|
|`const_pointer`|Typ, który dostarcza wskaźnik do **`const`** elementu w współbieżnym wektorze.|
|`const_reference`|Typ, który zawiera odwołanie do **`const`** elementu przechowywanego w współbieżnym wektorze w celu odczytu i wykonywania **`const`** operacji.|
|`const_reverse_iterator`|Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać dowolny **`const`** element w współbieżnym wektorze.|
|`difference_type`|Typ, który zawiera podpisaną odległość między dwoma elementami w równoległym wektorze.|
|`iterator`|Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać dowolny element w współbieżnym wektorze. Modyfikacja elementu przy użyciu iteratora nie jest bezpieczna pod kątem współbieżności.|
|`pointer`|Typ, który dostarcza wskaźnik do elementu w współbieżnym wektorze.|
|`reference`|Typ, który zawiera odwołanie do elementu przechowywanego w współbieżnym wektorze.|
|`reverse_iterator`|Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać dowolny element w odwróconym wektorze współbieżnym. Modyfikacja elementu przy użyciu iteratora nie jest bezpieczna pod kątem współbieżności.|
|`size_type`|Typ, który zlicza liczbę elementów w współbieżnym wektorze.|
|`value_type`|Typ, który reprezentuje typ danych przechowywany w współbieżnym wektorze.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[concurrent_vector](#ctor)|Przeciążone. Konstruuje współbieżny wektor.|
|[~ concurrent_vector destruktor](#dtor)|Kasuje wszystkie elementy i niszczy ten współbieżny wektor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[przypisać](#assign)|Przeciążone. Wymazuje elementy współbieżnego wektora i przypisuje do niego `_N` kopie `_Item` lub wartości określone przez zakres iteratora [ `_Begin` , `_End` ). Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[w](#at)|Przeciążone. Zapewnia dostęp do elementu pod danym indeksem w wektorze współbieżnym. Ta metoda jest współbieżnie bezpieczna dla operacji odczytu, a także podczas rozwijania wektora, o ile jest to gwarantowane, że wartość `_Index` jest mniejsza niż wielkość współbieżnego wektora.|
|[Wstecz](#back)|Przeciążone. Zwraca odwołanie lub **`const`** odwołanie do ostatniego elementu w współbieżnym wektorze. Jeśli wektor współbieżny jest pusty, wartość zwracana jest niezdefiniowana. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[zaczną](#begin)|Przeciążone. Zwraca iterator typu `iterator` lub `const_iterator` do początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[pojemności](#capacity)|Zwraca maksymalny rozmiar, do którego można zwiększyć współbieżny wektor bez konieczności przydzielenia większej ilości pamięci. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[cbegin](#cbegin)|Zwraca iterator typu `const_iterator` do początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[cend](#cend)|Zwraca iterator typu `const_iterator` do końca współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[Wyczyść](#clear)|Usuwa wszystkie elementy z współbieżnego wektora. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[crbegin —](#crbegin)|Zwraca iterator typu `const_reverse_iterator` do początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[crend](#crend)|Zwraca iterator typu `const_reverse_iterator` do końca współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[puste](#empty)|Testuje, czy współbieżny wektor jest pusty w momencie wywołania tej metody. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[punktów](#end)|Przeciążone. Zwraca iterator typu `iterator` lub `const_iterator` do końca współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[FSB](#front)|Przeciążone. Zwraca odwołanie lub **`const`** odwołanie do pierwszego elementu w współbieżnym wektorze. Jeśli wektor współbieżny jest pusty, wartość zwracana jest niezdefiniowana. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[get_allocator](#get_allocator)|Zwraca kopię alokatora używaną do konstruowania współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[grow_by](#grow_by)|Przeciążone. Powiększa ten współbieżny wektor według `_Delta` elementów. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[grow_to_at_least](#grow_to_at_least)|Powiększa ten współbieżny wektor do momentu, gdy ma on co najmniej `_N` elementy. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[max_size](#max_size)|Zwraca maksymalną liczbę elementów, które mogą być przechowywane przez współbieżny wektor. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[push_back](#push_back)|Przeciążone. Dołącza dany element na końcu współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[rbegin](#rbegin)|Przeciążone. Zwraca iterator typu `reverse_iterator` lub `const_reverse_iterator` do początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[rend](#rend)|Przeciążone. Zwraca iterator typu `reverse_iterator` lub `const_reverse_iterator` do końca współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[zarezerwować](#reserve)|Przypisuje wystarczającą ilość miejsca, aby zwiększyć współbieżny wektor do rozmiaru `_N` bez konieczności przydzielenia większej ilości pamięci. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[Zmień rozmiar](#resize)|Przeciążone. Zmienia rozmiar współbieżnego wektora na żądany rozmiar, usuwając lub dodając elementy w razie potrzeby. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[shrink_to_fit](#shrink_to_fit)|Kompaktuje wewnętrzną reprezentację współbieżnego wektora, aby zmniejszyć fragmentację i zoptymalizować użycie pamięci. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[zmienia](#size)|Zwraca liczbę elementów w wektorze współbieżnym. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[wymiany](#swap)|Zamienia zawartość dwóch współbieżnych wektorów. Ta metoda nie jest bezpieczna pod kątem współbieżności.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator\[\]](#operator_at)|Przeciążone. Zapewnia dostęp do elementu pod danym indeksem w wektorze współbieżnym. Ta metoda jest bezpieczna pod kątem współbieżności dla operacji odczytu, a także podczas rozwijania wektora, o ile jest to gwarantowane, że wartość `_Index` jest mniejsza niż rozmiar współbieżnego wektora.|
|[operator =](#operator_eq)|Przeciążone. Przypisuje zawartość innego `concurrent_vector` obiektu do tego elementu. Ta metoda nie jest bezpieczna pod kątem współbieżności.|

## <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje na temat `concurrent_vector` klasy, zobacz [Parallel Containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_Concurrent_vector_base_v4`

`_Allocator_base`

`concurrent_vector`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concurrent_vector. h

**Przestrzeń nazw:** współbieżność

## <a name="assign"></a><a name="assign"></a>ponownie

Wymazuje elementy współbieżnego wektora i przypisuje do niego `_N` kopie `_Item` lub wartości określone przez zakres iteratora [ `_Begin` , `_End` ). Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>Parametry

*_InputIterator*<br/>
Typ określonego iteratora.

*_N*<br/>
Liczba elementów, które mają zostać skopiowane do współbieżnego wektora.

*_Item*<br/>
Odwołanie do wartości używanej do wypełniania wektora współbieżności.

*_Begin*<br/>
Iterator do pierwszego elementu zakresu źródłowego.

*_End*<br/>
Iterator do jednego z nich poza ostatnim elementem zakresu źródłowego.

### <a name="remarks"></a>Uwagi

`assign`nie jest bezpieczny dla współbieżności. Należy upewnić się, że żadne inne wątki nie wywołuje metod w wektorze współbieżnym podczas wywoływania tej metody.

## <a name="at"></a><a name="at"></a>w

Zapewnia dostęp do elementu pod danym indeksem w wektorze współbieżnym. Ta metoda jest współbieżnie bezpieczna dla operacji odczytu, a także podczas rozwijania wektora, o ile jest to gwarantowane, że wartość `_Index` jest mniejsza niż wielkość współbieżnego wektora.

```cpp
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Indeks elementu, który ma zostać pobrany.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu pod podanym indeksem.

### <a name="remarks"></a>Uwagi

Wersja funkcji `at` zwracającej **`const`** odwołanie nie może być używana do równoczesnego zapisu w elemencie z różnych wątków. Do synchronizacji współbieżnych operacji odczytu i zapisu do tego samego elementu danych należy użyć innego obiektu synchronizacji.

Metoda generuje `out_of_range` , jeśli `_Index` jest większa lub równa rozmiarowi współbieżnego wektora, a `range_error` Jeśli indeks jest podzielonym fragmentem wektora. Aby uzyskać szczegółowe informacje o tym, jak wektor może ulec uszkodzeniu, zobacz [Parallel Containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="back"></a><a name="back"></a>Wstecz

Zwraca odwołanie lub **`const`** odwołanie do ostatniego elementu w współbieżnym wektorze. Jeśli wektor współbieżny jest pusty, wartość zwracana jest niezdefiniowana. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie lub **`const`** odwołanie do ostatniego elementu w współbieżnym wektorze.

## <a name="begin"></a><a name="begin"></a>zaczną

Zwraca iterator typu `iterator` lub `const_iterator` do początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `iterator` lub `const_iterator` do początku współbieżnego wektora.

## <a name="capacity"></a><a name="capacity"></a>pojemności

Zwraca maksymalny rozmiar, do którego można zwiększyć współbieżny wektor bez konieczności przydzielenia większej ilości pamięci. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalny rozmiar, do którego można zwiększyć współbieżny wektor bez konieczności przydzielenia większej ilości pamięci.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do standardowej biblioteki C++ `vector` , `concurrent_vector` obiekt nie przenosi istniejących elementów, jeśli przydziela więcej pamięci.

## <a name="cbegin"></a><a name="cbegin"></a>cbegin

Zwraca iterator typu `const_iterator` do początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `const_iterator` do początku współbieżnego wektora.

## <a name="cend"></a><a name="cend"></a>cend

Zwraca iterator typu `const_iterator` do końca współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `const_iterator` do końca współbieżnego wektora.

## <a name="clear"></a><a name="clear"></a>Wyczyść

Usuwa wszystkie elementy z współbieżnego wektora. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

`clear`nie jest bezpieczny dla współbieżności. Należy upewnić się, że żadne inne wątki nie wywołuje metod w wektorze współbieżnym podczas wywoływania tej metody. `clear`nie zwalnia tablic wewnętrznych. Aby zwolnić tablice wewnętrzne, wywołaj funkcję `shrink_to_fit` po `clear` .

## <a name="concurrent_vector"></a><a name="ctor"></a>concurrent_vector

Konstruuje współbieżny wektor.

```cpp
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
Typ alokatora wektora źródłowego.

*_InputIterator*<br/>
Typ iteratora wejściowego.

*_Al*<br/>
Klasa alokatora do wykorzystania z tym obiektem.

*_Vector*<br/>
Obiekt źródłowy `concurrent_vector` do kopiowania lub przenoszenia elementów z.

*_N*<br/>
Początkowa pojemność `concurrent_vector` obiektu.

*_Item*<br/>
Wartość elementów w skonstruowanym obiekcie.

*_Begin*<br/>
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*_End*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują obiekt alokatora `_Al` i inicjują wektor.

Pierwszy Konstruktor Określa pusty wektor początkowy i jawnie określa typ alokatora. do użycia.

Drugi i trzeci konstruktory określają kopię współbieżnego wektora `_Vector` .

Czwarty Konstruktor Określa przechodzenie współbieżnego wektora `_Vector` .

Piąty Konstruktor Określa powtarzanie określonej liczby ( `_N` ) elementów wartości domyślnej dla klasy `T` .

Szósty konstruktor określa powtórzenia ( `_N` ) elementów wartości `_Item` .

Ostatni konstruktor określa wartości dostarczone przez zakres iteratora [ `_Begin` , `_End` ).

## <a name="concurrent_vector"></a><a name="dtor"></a>~ concurrent_vector

Kasuje wszystkie elementy i niszczy ten współbieżny wektor.

```cpp
~concurrent_vector();
```

## <a name="crbegin"></a><a name="crbegin"></a>crbegin —

Zwraca iterator typu `const_reverse_iterator` do początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `const_reverse_iterator` do początku współbieżnego wektora.

## <a name="crend"></a><a name="crend"></a>crend

Zwraca iterator typu `const_reverse_iterator` do końca współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `const_reverse_iterator` do końca współbieżnego wektora.

## <a name="empty"></a><a name="empty"></a>ciągiem

Testuje, czy współbieżny wektor jest pusty w momencie wywołania tej metody. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wektor był pusty w momencie wywołania funkcji, **`false`** w przeciwnym razie.

## <a name="end"></a><a name="end"></a>punktów

Zwraca iterator typu `iterator` lub `const_iterator` do końca współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `iterator` lub `const_iterator` do końca współbieżnego wektora.

## <a name="front"></a><a name="front"></a>FSB

Zwraca odwołanie lub **`const`** odwołanie do pierwszego elementu w współbieżnym wektorze. Jeśli wektor współbieżny jest pusty, wartość zwracana jest niezdefiniowana. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie lub **`const`** odwołanie do pierwszego elementu w współbieżnym wektorze.

## <a name="get_allocator"></a><a name="get_allocator"></a>get_allocator

Zwraca kopię alokatora używaną do konstruowania współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Kopia alokatora użyta do skonstruowania `concurrent_vector` obiektu.

## <a name="grow_by"></a><a name="grow_by"></a>grow_by

Powiększa ten współbieżny wektor według `_Delta` elementów. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```

### <a name="parameters"></a>Parametry

*_Delta*<br/>
Liczba elementów do dołączenia do obiektu.

*_Item*<br/>
Wartość, za pomocą której mają zostać zainicjowane nowe elementy.

### <a name="return-value"></a>Wartość zwracana

Dołączany iterator do pierwszego elementu.

### <a name="remarks"></a>Uwagi

Jeśli `_Item` nie jest określony, nowe elementy są domyślnie skonstruowane.

## <a name="grow_to_at_least"></a><a name="grow_to_at_least"></a>grow_to_at_least

Powiększa ten współbieżny wektor do momentu, gdy ma on co najmniej `_N` elementy. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
iterator grow_to_at_least(size_type _N);
```

### <a name="parameters"></a>Parametry

*_N*<br/>
Nowy minimalny rozmiar `concurrent_vector` obiektu.

### <a name="return-value"></a>Wartość zwracana

Iterator, który wskazuje na początek dołączonej sekwencji lub do elementu w indeksie, `_N` Jeśli nie zostały dołączone żadne elementy.

## <a name="max_size"></a><a name="max_size"></a>max_size

Zwraca maksymalną liczbę elementów, które mogą być przechowywane przez współbieżny wektor. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba elementów, które `concurrent_vector` mogą być przechowywane w obiekcie.

## <a name="operator"></a><a name="operator_eq"></a>operator =

Przypisuje zawartość innego `concurrent_vector` obiektu do tego elementu. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
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
Typ alokatora wektora źródłowego.

*_Vector*<br/>
Obiekt źródłowy `concurrent_vector` .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do tego `concurrent_vector` obiektu.

## <a name="operator"></a><a name="operator_at"></a>operator []

Zapewnia dostęp do elementu pod danym indeksem w wektorze współbieżnym. Ta metoda jest bezpieczna pod kątem współbieżności dla operacji odczytu, a także podczas rozwijania wektora, o ile jest to gwarantowane, że wartość `_Index` jest mniejsza niż rozmiar współbieżnego wektora.

```cpp
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Indeks elementu, który ma zostać pobrany.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu pod podanym indeksem.

### <a name="remarks"></a>Uwagi

Wersja `operator []` , która zwraca element, który **`const`** nie jest odwołaniem, nie może być używana do równoczesnego zapisu w elemencie z różnych wątków. Do synchronizacji współbieżnych operacji odczytu i zapisu do tego samego elementu danych należy użyć innego obiektu synchronizacji.

Nie jest przeprowadzane sprawdzanie granic, aby upewnić `_Index` się, że jest prawidłowym indeksem dla współbieżnego wektora.

## <a name="push_back"></a><a name="push_back"></a>push_back

Dołącza dany element na końcu współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```

### <a name="parameters"></a>Parametry

*_Item*<br/>
Wartość, która ma zostać dołączona.

### <a name="return-value"></a>Wartość zwracana

Dołączany iterator do elementu.

## <a name="rbegin"></a><a name="rbegin"></a>rbegin

Zwraca iterator typu `reverse_iterator` lub `const_reverse_iterator` do początku współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `reverse_iterator` lub `const_reverse_iterator` do początku współbieżnego wektora.

## <a name="rend"></a><a name="rend"></a>rend

Zwraca iterator typu `reverse_iterator` lub `const_reverse_iterator` do końca współbieżnego wektora. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
reverse_iterator rend();

const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `reverse_iterator` lub `const_reverse_iterator` do końca współbieżnego wektora.

## <a name="reserve"></a><a name="reserve"></a>zarezerwować

Przypisuje wystarczającą ilość miejsca, aby zwiększyć współbieżny wektor do rozmiaru `_N` bez konieczności przydzielenia większej ilości pamięci. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
void reserve(size_type _N);
```

### <a name="parameters"></a>Parametry

*_N*<br/>
Liczba elementów, dla których ma zostać zarezerwowane miejsce.

### <a name="remarks"></a>Uwagi

`reserve`nie jest bezpieczny dla współbieżności. Należy upewnić się, że żadne inne wątki nie wywołuje metod w wektorze współbieżnym podczas wywoływania tej metody. Pojemność wektora współbieżnego po powrocie metody może być większa niż żądana rezerwacja.

## <a name="resize"></a><a name="resize"></a>Zmień rozmiar

Zmienia rozmiar współbieżnego wektora na żądany rozmiar, usuwając lub dodając elementy w razie potrzeby. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```

### <a name="parameters"></a>Parametry

*_N*<br/>
Nowy rozmiar concurrent_vector.

*użyte*<br/>
Wartość nowych elementów dodanych do wektora, jeśli nowy rozmiar jest większy niż rozmiar oryginalny. W przypadku pominięcia wartości nowe obiekty są przypisywane do wartości domyślnej dla ich typu.

### <a name="remarks"></a>Uwagi

Jeśli rozmiar kontenera jest mniejszy niż żądany rozmiar, elementy są dodawane do wektora do momentu osiągnięcia żądanego rozmiaru. Jeśli rozmiar kontenera przekracza żądany rozmiar, elementy znajdujące się najbliżej końca kontenera są usuwane do momentu osiągnięcia rozmiaru kontenera `_N` . Jeśli obecny rozmiar kontenera jest taki sam jak żądany rozmiar, nie jest podejmowana żadna akcja.

`resize`nie jest bezpieczne dla współbieżności. Należy upewnić się, że żadne inne wątki nie wywołuje metod w wektorze współbieżnym podczas wywoływania tej metody.

## <a name="shrink_to_fit"></a><a name="shrink_to_fit"></a>shrink_to_fit

Kompaktuje wewnętrzną reprezentację współbieżnego wektora, aby zmniejszyć fragmentację i zoptymalizować użycie pamięci. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Uwagi

Ta metoda wewnętrznie ponownie przydzieli elementy przenoszenia pamięci wokół, unieważnienie wszystkich iteratorów. `shrink_to_fit`nie jest bezpieczny dla współbieżności. Należy upewnić się, że żadne inne wątki nie wywołuje metod w wektorze współbieżnym podczas wywoływania tej funkcji.

## <a name="size"></a><a name="size"></a>zmienia

Zwraca liczbę elementów w wektorze współbieżnym. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tym `concurrent_vector` obiekcie.

### <a name="remarks"></a>Uwagi

Zwrócony rozmiar jest gwarantowany do uwzględnienia wszystkich elementów dołączanych przez wywołania funkcji `push_back` lub wzrostu operacji zakończonych przed wywołaniem tej metody. Może jednak zawierać również elementy, które są przydzielone, ale nadal w trakcie tworzenia przez współbieżne wywołania do którejkolwiek z metod wzrostu.

## <a name="swap"></a><a name="swap"></a>wymiany

Zamienia zawartość dwóch współbieżnych wektorów. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
void swap(concurrent_vector& _Vector);
```

### <a name="parameters"></a>Parametry

*_Vector*<br/>
`concurrent_vector`Obiekt, za pomocą którego ma zostać zamieniony zawartość.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Równoległe kontenery i obiekty](../../../parallel/concrt/parallel-containers-and-objects.md)
