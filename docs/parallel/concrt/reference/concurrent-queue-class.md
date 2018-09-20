---
title: concurrent_queue — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::clear
- CONCURRENT_QUEUE/concurrency::concurrent_queue::empty
- CONCURRENT_QUEUE/concurrency::concurrent_queue::get_allocator
- CONCURRENT_QUEUE/concurrency::concurrent_queue::push
- CONCURRENT_QUEUE/concurrency::concurrent_queue::try_pop
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_begin
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_end
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_size
dev_langs:
- C++
helpviewer_keywords:
- concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41e4c6f3a540f44f6cec0d94ffab74d65a1ffe52
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386590"
---
# <a name="concurrentqueue-class"></a>concurrent_queue — Klasa

`concurrent_queue` Klasa jest klasą kontenera sekwencji, umożliwiającym w pierwszym, first-out dostęp do jego elementów. Umożliwia ona ograniczony zestaw operacji bezpieczne pod względem współbieżności, takich jak `push` i `try_pop`.

## <a name="syntax"></a>Składnia

```
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów, które mają być przechowywane w kolejce.

*_Ax*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i dezalokacji pamięci dla tej kolejki współbieżnych. Ten argument jest opcjonalny, a wartość domyślna to `allocator<T>`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`allocator_type`|Typ, który reprezentuje klasę alokatora dla kolejka współbieżna.|
|`const_iterator`|Typ, który reprezentuje bez wątkowo `const` iteratora za pośrednictwem elementów w kolejce współbieżnych.|
|`const_reference`|Typ, który zawiera odwołanie do `const` elementu przechowywanego w kolejka współbieżna do odczytu i wykonywania `const` operacji.|
|`difference_type`|Typ, który dostarcza podpisem odległość między dwoma elementami w kolejka współbieżna.|
|`iterator`|Typ, która reprezentuje iterator bez wątkowo nad elementami w kolejka współbieżna.|
|`reference`|Typ, który zawiera odwołanie do elementu przechowywanego w kolejce współbieżnych.|
|`size_type`|Typ, który zlicza liczbę elementów w kolejce współbieżnych.|
|`value_type`|Typ, który reprezentuje typ danych przechowywanych w kolejce współbieżnych.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[concurrent_queue](#ctor)|Przeciążone. Tworzy kolejka współbieżna.|
|[~concurrent_queue Destructor](#dtor)|Niszczy kolejka współbieżna.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Usuń zaznaczenie](#clear)|Czyści kolejka współbieżna, niszczenie dowolnego aktualnie elementów umieszczonych w kolejce. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[pusty](#empty)|Sprawdza, czy kolejka współbieżna jest pusty w tej chwili ta metoda jest wywoływana. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu programu przydzielania użytego do stworzenia kolejka współbieżna. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[push](#push)|Przeciążone. Element na końcu tail kolejka współbieżna umieszczeniu. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[try_pop](#try_pop)|Dequeues elementu z kolejki, jeśli jest dostępny. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[unsafe_begin](#unsafe_begin)|Przeciążone. Zwraca iterator typu `iterator` lub `const_iterator` na początku kolejka współbieżna. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[unsafe_end](#unsafe_end)|Przeciążone. Zwraca iterator typu `iterator` lub `const_iterator` na końcu kolejka współbieżna. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[unsafe_size](#unsafe_size)|Zwraca liczbę elementów w kolejce. Ta metoda nie jest bezpieczna pod kątem współbieżności.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`concurrent_queue`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concurrent_queue.h

**Namespace:** współbieżności

##  <a name="clear"></a> Usuń zaznaczenie

Czyści kolejka współbieżna, niszczenie dowolnego aktualnie elementów umieszczonych w kolejce. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
void clear();
```

##  <a name="ctor"></a> concurrent_queue —

Tworzy kolejka współbieżna.

```
explicit concurrent_queue(
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    const concurrent_queue& _OtherQ,
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    concurrent_queue&& _OtherQ,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_queue(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>Parametry

*_InputIterator*<br/>
Typ iteratora danych wejściowych, która określa zakres wartości.

*_Al*<br/>
Klasa alokatora do wykorzystania z tym obiektem.

*_OtherQ*<br/>
Źródło `concurrent_queue` obiektu do kopiowania lub przenoszenia elementów z.

*_Rozpocznij*<br/>
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*_Zakończ*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują obiekt programu przydzielania `_Al` i zainicjować kolejki.

Pierwszy Konstruktor określa pustej kolejce początkowej i wyraźnie określa typ alokatora, który ma być używany.

Drugi Konstruktor Określa kopię kolejka współbieżna `_OtherQ`.

Trzeci Konstruktor Określa przeniesienie kolejka współbieżna `_OtherQ`.

Czwarty Konstruktor określa wartości dostarczone przez zakres iteratora [ `_Begin`, `_End`).

##  <a name="dtor"></a> ~ concurrent_queue

Niszczy kolejka współbieżna.

```
~concurrent_queue();
```

##  <a name="empty"></a> pusty

Sprawdza, czy kolejka współbieżna jest pusty w tej chwili ta metoda jest wywoływana. Ta metoda jest bezpieczna pod kątem współbieżności.

```
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli kolejka współbieżna był pusty w tej chwili analizujemy, `false` inaczej.

### <a name="remarks"></a>Uwagi

Gdy ta metoda jest bezpieczna pod kątem współbieżności w odniesieniu do wywołania metody `push`, `try_pop`, i `empty`, wartość zwracana może być niepoprawny według czasu sprawdzana jest przez wywołującego wątku.

##  <a name="get_allocator"></a> get_allocator —

Zwraca kopię obiektu programu przydzielania użytego do stworzenia kolejka współbieżna. Ta metoda jest bezpieczna pod kątem współbieżności.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Kopia alokator używany do budowy kolejka współbieżna.

##  <a name="push"></a> wypychania

Element na końcu tail kolejka współbieżna umieszczeniu. Ta metoda jest bezpieczna pod kątem współbieżności.

```
void push(const T& _Src);

void push(T&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Element które mają zostać dodane do kolejki.

### <a name="remarks"></a>Uwagi

`push` jest bezpieczna pod względem współbieżności w odniesieniu do wywołania metody `push`, `try_pop`, i `empty`.

##  <a name="try_pop"></a> try_pop —

Dequeues elementu z kolejki, jeśli jest dostępny. Ta metoda jest bezpieczna pod kątem współbieżności.

```
bool try_pop(T& _Dest);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Odwołanie do lokalizację do zapisania elementu dequeued.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli element został pomyślnie dequeued `false` inaczej.

### <a name="remarks"></a>Uwagi

Jeśli element został pomyślnie dequeued parametru `_Dest` otrzymuje wartość dequeued oryginalnej wartości, które są przechowywane w kolejce jest niszczony, a funkcja zwraca `true`. Jeśli nie było żadnych elementów do usuwania z kolejki, ta funkcja zwraca `false` bez blokowania i zawartość `_Dest` parametru są niezdefiniowane.

`try_pop` jest bezpieczna pod względem współbieżności w odniesieniu do wywołania metody `push`, `try_pop`, i `empty`.

##  <a name="unsafe_begin"></a> unsafe_begin

Zwraca iterator typu `iterator` lub `const_iterator` na początku kolejka współbieżna. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `iterator` lub `const_iterator` na początku tego obiektu kolejka współbieżna.

### <a name="remarks"></a>Uwagi

Iteratory for `concurrent_queue` klasy są przeznaczona głównie do debugowania, jak powolne i iteracji nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych operacji kolejki.

##  <a name="unsafe_end"></a> unsafe_end —

Zwraca iterator typu `iterator` lub `const_iterator` na końcu kolejka współbieżna. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
iterator unsafe_end();

const_iterator unsafe_end() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu `iterator` lub `const_iterator` na końcu kolejka współbieżna.

### <a name="remarks"></a>Uwagi

Iteratory for `concurrent_queue` klasy są przeznaczona głównie do debugowania, jak powolne i iteracji nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych operacji kolejki.

##  <a name="unsafe_size"></a> unsafe_size —

Zwraca liczbę elementów w kolejce. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```
size_type unsafe_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar kolejki współbieżnych.

### <a name="remarks"></a>Uwagi

`unsafe_size` nie jest bezpieczna pod kątem współbieżności i może wygenerować niepoprawne wyniki, jeśli wywołania będą równocześnie z wywołaniami metod `push`, `try_pop`, i `empty`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
