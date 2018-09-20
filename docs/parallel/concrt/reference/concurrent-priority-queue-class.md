---
title: concurrent_priority_queue — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b87ac316c08f93a95f7791297b74cbbb20d5452a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413877"
---
# <a name="concurrentpriorityqueue-class"></a>concurrent_priority_queue — Klasa

`concurrent_priority_queue` Klasy jest kontenerem, który zezwala na wiele wątków jednocześnie elementów wypychania i pop. Elementy są zdjęte ze stosu w kolejności priorytetów, których priorytet jest określana przez funktorem dostarczone jako argument szablonu.

## <a name="syntax"></a>Składnia

```
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów, które mają być przechowywane w kolejce priorytetu.

*_Porównaj*<br/>
Typ obiektu funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w kolejce priorytetu. Ten argument jest opcjonalny i predykat dwuelementowy `less<T>` jest wartością domyślną.

*_Ax*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i dezalokacji pamięci dla kolejki priorytetowej współbieżnych. Ten argument jest opcjonalny, a wartość domyślna to `allocator<T>`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`allocator_type`|Typ, który reprezentuje klasę alokatora dla kolejki priorytetowej współbieżnych.|
|`const_reference`|Typ, który reprezentuje stałą odwołanie do elementu typu przechowywane w kolejce priorytetu współbieżnych.|
|`reference`|Typ, który reprezentuje odwołanie do elementu typu przechowywane w kolejce priorytetu współbieżnych.|
|`size_type`|Typ, który zlicza liczbę elementów w kolejce priorytetu współbieżnych.|
|`value_type`|Typ, który reprezentuje typ danych przechowywanych w kolejce priorytetu współbieżnych.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[concurrent_priority_queue](#ctor)|Przeciążone. Tworzy kolejki priorytetowej współbieżnych.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Usuń zaznaczenie](#clear)|Usuwa wszystkie elementy z priorytetem współbieżnych. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[pusty](#empty)|Sprawdza, czy kolejka priorytetowa współbieżnych jest pusta w czasie ta metoda jest wywoływana. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu alokator używany do utworzenia kolejki priorytetowej współbieżnych. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[push](#push)|Przeciążone. Dodaje element do kolejki priorytetowej współbieżnych. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[Rozmiar](#size)|Zwraca liczbę elementów w kolejce priorytetu współbieżnych. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[swap](#swap)|Zamienia zawartości dwóch jednoczesnych priorytet kolejki. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[try_pop](#try_pop)|Usuwa i zwraca najwyższy element priorytet z kolejki, jeśli kolejka jest pusta. Ta metoda jest bezpieczna pod kątem współbieżności.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator=](#operator_eq)|Przeciążone. Przypisuje zawartość innego `concurrent_priority_queue` obiektu do wskazanego. Ta metoda nie jest bezpieczna pod kątem współbieżności.|

## <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje na temat `concurrent_priority_queue` klasy, zobacz [równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`concurrent_priority_queue`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concurrent_priority_queue.h

**Namespace:** współbieżności

##  <a name="clear"></a> Usuń zaznaczenie

Usuwa wszystkie elementy z priorytetem współbieżnych. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
void clear();
```

### <a name="remarks"></a>Uwagi

`clear` nie jest bezpieczna pod kątem współbieżności. Należy się upewnić, że nie ma innych wątków są wywoływanie metod na kolejki priorytetowej współbieżnych, po wywołaniu tej metody. `clear` nie spowoduje zwolnienia pamięci.

##  <a name="ctor"></a> concurrent_priority_queue —

Tworzy kolejki priorytetowej współbieżnych.

```
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
Pojemność `concurrent_priority_queue` obiektu.

*_Rozpocznij*<br/>
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*_Zakończ*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

*_Src*<br/>
Źródło `concurrent_priority_queue` obiektu do kopiowania lub przenoszenia elementów z.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują obiekt programu przydzielania `_Al` i zainicjuj kolejkę priorytetów.

Pierwszy Konstruktor Określa kolejki pusty priorytet początkowego i opcjonalnie określa alokatora.

Drugi Konstruktor Określa kolejki priorytetowej za pomocą początkową pojemność `_Init_capacity` i opcjonalnie określa alokatora.

Trzeci Konstruktor określa wartości dostarczone przez zakres iteratora [ `_Begin`, `_End`) i opcjonalnie określa alokatora.

Czwarty i piąty Konstruktor określają kopię kolejki priorytetowej `_Src`.

Szósty i siódmego Konstruktor określają przeniesienie kolejki priorytetowej `_Src`.

##  <a name="empty"></a> pusty

Sprawdza, czy kolejka priorytetowa współbieżnych jest pusta w czasie ta metoda jest wywoływana. Ta metoda jest bezpieczna pod kątem współbieżności.

```
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli kolejka priorytetowa był pusty w tej chwili funkcja została wywołana, `false` inaczej.

##  <a name="get_allocator"></a> get_allocator —

Zwraca kopię obiektu alokator używany do utworzenia kolejki priorytetowej współbieżnych. Ta metoda jest bezpieczna pod kątem współbieżności.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Kopię alokator używany do budowy `concurrent_priority_queue` obiektu.

##  <a name="operator_eq"></a> operator =

Przypisuje zawartość innego `concurrent_priority_queue` obiektu do wskazanego. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Źródło `concurrent_priority_queue` obiektu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `concurrent_priority_queue` obiektu.

##  <a name="push"></a> wypychania

Dodaje element do kolejki priorytetowej współbieżnych. Ta metoda jest bezpieczna pod kątem współbieżności.

```
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```

### <a name="parameters"></a>Parametry

*_Elem*<br/>
Element, który ma zostać dodany do kolejki priorytetowej współbieżnych.

##  <a name="size"></a> Rozmiar

Zwraca liczbę elementów w kolejce priorytetu współbieżnych. Ta metoda jest bezpieczna pod kątem współbieżności.

```
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tym `concurrent_priority_queue` obiektu.

### <a name="remarks"></a>Uwagi

Rozmiar zwrócony jest gwarantowane, obejmują wszystkie elementy dodane przez wywołań funkcji `push`. Jednakże mogą nie odzwierciedlać wyniki oczekujących współbieżnych operacji.

##  <a name="swap"></a> swap

Zamienia zawartości dwóch jednoczesnych priorytet kolejki. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
void swap(concurrent_priority_queue& _Queue);
```

### <a name="parameters"></a>Parametry

*_Fronty*<br/>
`concurrent_priority_queue` Obiekt do wymiany zawartości z.

##  <a name="try_pop"></a> try_pop —

Usuwa i zwraca najwyższy element priorytet z kolejki, jeśli kolejka jest pusta. Ta metoda jest bezpieczna pod kątem współbieżności.

```
bool try_pop(reference _Elem);
```

### <a name="parameters"></a>Parametry

*_Elem*<br/>
Odwołanie do zmiennej, która zostanie wypełniona element najwyższy priorytet, jeśli kolejka jest pusta.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli wartość została zdjęte ze stosu, `false` inaczej.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md)

