---
title: concurrent_queue — Klasa
ms.date: 11/04/2016
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
helpviewer_keywords:
- concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
ms.openlocfilehash: 4e913af40b2218da5699da2659ec2e9189e32994
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143204"
---
# <a name="concurrent_queue-class"></a>concurrent_queue — Klasa

Klasa `concurrent_queue` jest klasą kontenera sekwencji, która umożliwia pierwszy i pierwszy dostęp do jego elementów. Umożliwia ograniczony zestaw operacji związanych z współbieżnością, takich jak `push` i `try_pop`. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia.

## <a name="syntax"></a>Składnia

```cpp
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ danych elementów, które mają być przechowywane w kolejce.

*_Ax*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i cofania alokacji pamięci dla tej współbieżnej kolejki. Ten argument jest opcjonalny, a wartość domyślna to `allocator<T>`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`allocator_type`|Typ, który reprezentuje klasę alokatora dla kolejki współbieżnej.|
|`const_iterator`|Typ, który reprezentuje niewątkowo bezpieczny `const` iterator dla elementów w kolejce współbieżnej.|
|`const_reference`|Typ, który zawiera odwołanie do `const` elementu przechowywanego w współbieżnej kolejce do odczytu i wykonywania `const` operacji.|
|`difference_type`|Typ, który zawiera podpisaną odległość między dwoma elementami w kolejce współbieżnej.|
|`iterator`|Typ, który reprezentuje iterator niebezpieczny dla wątków dla elementów w kolejce współbieżnej.|
|`reference`|Typ, który zawiera odwołanie do elementu przechowywanego w kolejce współbieżnej.|
|`size_type`|Typ, który zlicza liczbę elementów w kolejce współbieżnej.|
|`value_type`|Typ, który reprezentuje typ danych przechowywany w kolejce współbieżnej.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[concurrent_queue](#ctor)|Przeciążone. Konstruuje kolejkę współbieżną.|
|[~ concurrent_queue destruktor](#dtor)|Niszczy współbieżną kolejkę.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Wyczyść](#clear)|Czyści kolejkę współbieżną, zniszczyć wszystkie elementy znajdujące się w kolejce. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[ciągiem](#empty)|Testuje, czy kolejka współbieżna jest pusta w chwili, gdy ta metoda jest wywoływana. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[get_allocator](#get_allocator)|Zwraca kopię alokatora używaną do konstruowania kolejki współbieżnej. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[push](#push)|Przeciążone. Enqueues element na końcu końca kolejki współbieżnej. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[try_pop](#try_pop)|Usuwa element z kolejki, jeśli jest dostępny. Ta metoda jest bezpieczna pod kątem współbieżności.|
|[unsafe_begin](#unsafe_begin)|Przeciążone. Zwraca iterator typu `iterator` lub `const_iterator` do początku kolejki współbieżnej. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[unsafe_end](#unsafe_end)|Przeciążone. Zwraca iterator typu `iterator` lub `const_iterator` do końca kolejki współbieżnej. Ta metoda nie jest bezpieczna pod kątem współbieżności.|
|[unsafe_size](#unsafe_size)|Zwraca liczbę elementów w kolejce. Ta metoda nie jest bezpieczna pod kątem współbieżności.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Parallel Containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`concurrent_queue`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concurrent_queue. h

**Przestrzeń nazw:** współbieżność

## <a name="clear"></a>Wyczyść

Czyści kolejkę współbieżną, zniszczyć wszystkie elementy znajdujące się w kolejce. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
void clear();
```

## <a name="ctor"></a>concurrent_queue

Konstruuje kolejkę współbieżną.

```cpp
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
Typ iteratora wejściowego, który określa zakres wartości.

*_Al*<br/>
Klasa alokatora do wykorzystania z tym obiektem.

*_OtherQ*<br/>
Obiekt źródłowy `concurrent_queue` do kopiowania lub przenoszenia elementów.

*_Begin*<br/>
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*_End*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują obiekt alokatora `_Al` i inicjują kolejkę.

Pierwszy Konstruktor określa pustą kolejkę początkową i jawnie określa typ alokatora, który ma być używany.

Drugi Konstruktor określa kopię współbieżnej kolejki `_OtherQ`.

Trzeci konstruktor określa przechodzenie współbieżnej kolejki `_OtherQ`.

Czwarty Konstruktor Określa wartości dostarczone przez zakres iteratora [`_Begin`, `_End`).

## <a name="dtor"></a>~ concurrent_queue

Niszczy współbieżną kolejkę.

```cpp
~concurrent_queue();
```

## <a name="empty"></a>ciągiem

Testuje, czy kolejka współbieżna jest pusta w chwili, gdy ta metoda jest wywoływana. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli kolejka współbieżna była pusta w momencie wyszukanej, w przeciwnym razie **zwraca wartość false** .

### <a name="remarks"></a>Uwagi

Chociaż ta metoda jest bezpieczna pod kątem współbieżności w odniesieniu do wywołań metod `push`, `try_pop`i `empty`, zwracana wartość może być niepoprawna przez czas, który jest sprawdzany przez wątek wywołujący.

## <a name="get_allocator"></a>get_allocator

Zwraca kopię alokatora używaną do konstruowania kolejki współbieżnej. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwrócona

Kopia alokatora użyta do skonstruowania kolejki współbieżnej.

## <a name="push"></a>wydajności

Enqueues element na końcu końca kolejki współbieżnej. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
void push(const T& _Src);

void push(T&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Element, który ma zostać dodany do kolejki.

### <a name="remarks"></a>Uwagi

`push` jest bezpieczny dla współbieżności w odniesieniu do wywołań metod `push`, `try_pop`i `empty`.

## <a name="try_pop"></a>try_pop

Usuwa element z kolejki, jeśli jest dostępny. Ta metoda jest bezpieczna pod kątem współbieżności.

```cpp
bool try_pop(T& _Dest);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Odwołanie do lokalizacji do przechowywania podkolejki elementu.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli element został pomyślnie usunięty z kolejki, w przeciwnym razie **zwraca wartość false** .

### <a name="remarks"></a>Uwagi

Jeśli element został pomyślnie usunięty z kolejki, parametr `_Dest` otrzymuje wartość unqueued, oryginalna wartość przechowywana w kolejce zostanie zniszczona, a funkcja zwraca **wartość true**. Jeśli nie ma żadnego elementu do wygenerowania z kolejki, ta funkcja zwraca `false` bez blokowania, a zawartość parametru `_Dest` jest niezdefiniowana.

`try_pop` jest bezpieczny dla współbieżności w odniesieniu do wywołań metod `push`, `try_pop`i `empty`.

## <a name="unsafe_begin"></a>unsafe_begin

Zwraca iterator typu `iterator` lub `const_iterator` do początku kolejki współbieżnej. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```

### <a name="return-value"></a>Wartość zwrócona

Iterator typu `iterator` lub `const_iterator` do początku współbieżnego obiektu kolejki.

### <a name="remarks"></a>Uwagi

Iteratory dla klasy `concurrent_queue` są przeznaczone głównie do debugowania, ponieważ są wolne, a iteracja nie jest bezpieczna pod względem współbieżności w odniesieniu do innych operacji w kolejce.

## <a name="unsafe_end"></a>unsafe_end

Zwraca iterator typu `iterator` lub `const_iterator` do końca kolejki współbieżnej. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
iterator unsafe_end();

const_iterator unsafe_end() const;
```

### <a name="return-value"></a>Wartość zwrócona

Iterator typu `iterator` lub `const_iterator` do końca kolejki współbieżnej.

### <a name="remarks"></a>Uwagi

Iteratory dla klasy `concurrent_queue` są przeznaczone głównie do debugowania, ponieważ są wolne, a iteracja nie jest bezpieczna pod względem współbieżności w odniesieniu do innych operacji w kolejce.

## <a name="unsafe_size"></a>unsafe_size

Zwraca liczbę elementów w kolejce. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
size_type unsafe_size() const;
```

### <a name="return-value"></a>Wartość zwrócona

Rozmiar kolejki współbieżnej.

### <a name="remarks"></a>Uwagi

`unsafe_size` nie jest bezpieczna pod kątem współbieżności i może generować nieprawidłowe wyniki, jeśli są wywoływane współbieżnie przy użyciu wywołań metod `push`, `try_pop`i `empty`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
