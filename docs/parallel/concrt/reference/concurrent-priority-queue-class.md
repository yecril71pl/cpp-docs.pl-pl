---
title: concurrent_priority_queue — Klasa
ms.date: 11/04/2016
f1_keywords:
- concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::clear
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::empty
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::get_allocator
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::push
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::size
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::swap
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::try_pop
helpviewer_keywords:
- concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
ms.openlocfilehash: 1d8651d1391ded2970a00a7429c36f341a438659
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143214"
---
# <a name="concurrent_priority_queue-class"></a>concurrent_priority_queue — Klasa

Klasa `concurrent_priority_queue` jest kontenerem, który umożliwia wielu wątkom równoczesne wypychanie i wypunktowanie elementów. Elementy są zdjęte w kolejności priorytetu, gdzie priorytet jest określany przez Funktor dostarczone jako argument szablonu.

## <a name="syntax"></a>Składnia

```cpp
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ danych elementów, które mają być przechowywane w kolejce priorytetów.

*_Compare*<br/>
Typ obiektu funkcji, który może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w kolejce priorytetów. Ten argument jest opcjonalny, a Predykat binarny `less<T>` jest wartością domyślną.

*_Ax*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i cofania alokacji pamięci dla kolejki współbieżnych priorytetów. Ten argument jest opcjonalny, a wartość domyślna to `allocator<T>`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`allocator_type`|Typ, który reprezentuje klasę alokatora dla kolejki współbieżnych priorytetów.|
|`const_reference`|Typ, który reprezentuje odwołanie stałe do elementu typu przechowywanego w kolejce współbieżnych priorytetów.|
|`reference`|Typ, który reprezentuje odwołanie do elementu typu przechowywanego w kolejce współbieżnych priorytetów.|
|`size_type`|Typ, który zlicza liczbę elementów w kolejce współbieżnych priorytetów.|
|`value_type`|Typ, który reprezentuje typ danych przechowywany w kolejce współbieżnych priorytetów.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[concurrent_priority_queue](#ctor)|Przeciążone. Tworzy kolejkę współbieżnych priorytetów.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Wyczyść](#clear)|Kasuje wszystkie elementy w współbieżnym priorytecie. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[ciągiem](#empty)|Testuje, czy kolejka współbieżnych priorytetów jest pusta w momencie wywołania tej metody. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[get_allocator](#get_allocator)|Zwraca kopię alokatora używaną do konstruowania kolejki współbieżnych priorytetów. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[push](#push)|Przeciążone. Dodaje element do kolejki współbieżnych priorytetów. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[zmienia](#size)|Zwraca liczbę elementów w kolejce współbieżnych priorytetów. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[wymiany](#swap)|Zamienia zawartość dwóch współbieżnych kolejek priorytetowych. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[try_pop](#try_pop)|Usuwa i zwraca element o najwyższym priorytecie z kolejki, jeśli kolejka nie jest pusta. Ta metoda jest bezpieczna pod kątem współbieżności.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator =](#operator_eq)|Przeciążone. Przypisuje do niego zawartość innego obiektu `concurrent_priority_queue`. Ta metoda nie jest bezpieczna pod kątem współbieżności.|

## <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje na temat klasy `concurrent_priority_queue`, zobacz [Parallel Containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`concurrent_priority_queue`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concurrent_priority_queue. h

**Przestrzeń nazw:** współbieżność

## <a name="clear"></a>Wyczyść

Kasuje wszystkie elementy w współbieżnym priorytecie. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

`clear` nie jest bezpieczna pod kątem współbieżności. Należy upewnić się, że żadne inne wątki nie wywołuje metod w kolejce współbieżnych priorytetów podczas wywoływania tej metody. `clear` nie zwalnia pamięci.

## <a name="ctor"></a>concurrent_priority_queue

Tworzy kolejkę współbieżnych priorytetów.

```cpp
explicit concurrent_priority_queue(
    const allocator_type& _Al = allocator_type());

explicit concurrent_priority_queue(
    size_type _Init_capacity,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_priority_queue(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());

concurrent_priority_queue(
    const concurrent_priority_queue& _Src);

concurrent_priority_queue(
    const concurrent_priority_queue& _Src,
    const allocator_type& _Al);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src,
    const allocator_type& _Al);
```

### <a name="parameters"></a>Parametry

*_InputIterator*<br/>
Typ iteratora wejściowego.

*_Al*<br/>
Klasa alokatora do wykorzystania z tym obiektem.

*_Init_capacity*<br/>
Początkowa pojemność obiektu `concurrent_priority_queue`.

*_Begin*<br/>
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*_End*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

*_Src*<br/>
Obiekt źródłowy `concurrent_priority_queue` do kopiowania lub przenoszenia elementów.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują obiekt alokatora `_Al` i inicjują kolejki priorytetów.

Pierwszy Konstruktor określa pustą początkową kolejkę priorytetów i opcjonalnie określa Alokator.

Drugi Konstruktor określa kolejkę priorytetową z początkową pojemnością `_Init_capacity` i opcjonalnie określa Alokator.

Trzeci konstruktor określa wartości dostarczone przez zakres iteratora [`_Begin`, `_End`) i opcjonalnie określa Alokator.

Czwarty i piąty konstruktory określają kopię kolejki priorytetu `_Src`.

Szóste i siódme konstruktory określają przeniesienie kolejki priorytetu `_Src`.

## <a name="empty"></a>ciągiem

Testuje, czy kolejka współbieżnych priorytetów jest pusta w momencie wywołania tej metody. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli kolejka priorytetów była pusta w momencie wywołania funkcji, w przeciwnym razie **zwraca wartość false** .

## <a name="get_allocator"></a>get_allocator

Zwraca kopię alokatora używaną do konstruowania kolejki współbieżnych priorytetów. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwrócona

Kopia alokatora używana do konstruowania obiektu `concurrent_priority_queue`.

## <a name="operator_eq"></a>operator =

Przypisuje do niego zawartość innego obiektu `concurrent_priority_queue`. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Obiekt źródłowy `concurrent_priority_queue`.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do tego obiektu `concurrent_priority_queue`.

## <a name="push"></a>wydajności

Dodaje element do kolejki współbieżnych priorytetów. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```

### <a name="parameters"></a>Parametry

*_Elem*<br/>
Element, który ma zostać dodany do kolejki współbieżnych priorytetów.

## <a name="size"></a>zmienia

Zwraca liczbę elementów w kolejce współbieżnych priorytetów. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwrócona

Liczba elementów w tym obiekcie `concurrent_priority_queue`.

### <a name="remarks"></a>Uwagi

Zwrócony rozmiar jest gwarantowany do uwzględnienia wszystkich elementów dodanych przez wywołania do funkcji `push`. Może jednak nie odzwierciedlać wyników oczekujących operacji współbieżnych.

## <a name="swap"></a>wymiany

Zamienia zawartość dwóch współbieżnych kolejek priorytetowych. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
void swap(concurrent_priority_queue& _Queue);
```

### <a name="parameters"></a>Parametry

*_Queue*<br/>
Obiekt `concurrent_priority_queue`, za pomocą którego ma zostać zamieniony zawartość.

## <a name="try_pop"></a>try_pop

Usuwa i zwraca element o najwyższym priorytecie z kolejki, jeśli kolejka nie jest pusta. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
bool try_pop(reference _Elem);
```

### <a name="parameters"></a>Parametry

*_Elem*<br/>
Odwołanie do zmiennej, która zostanie wypełniona z najwyższym priorytetem elementu, jeśli kolejka nie jest pusta.

### <a name="return-value"></a>Wartość zwrócona

wartość **true** , jeśli wartość została zdjętea, w przeciwnym razie **false** .

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md)
