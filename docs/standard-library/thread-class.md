---
title: Thread — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- thread/std::thread
- thread/std::thread::id Class
- thread/std::thread::thread
- thread/std::thread::detach
- thread/std::thread::get_id
- thread/std::thread::hardware_concurrency
- thread/std::thread::join
- thread/std::thread::joinable
- thread/std::thread::native_handle
- thread/std::thread::swap
dev_langs:
- C++
ms.assetid: df249bc7-ff81-4ff9-a6d6-5e3d9a8f56a1
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::thread [C++]
- std::thread [C++], thread
- std::thread [C++], detach
- std::thread [C++], get_id
- std::thread [C++], hardware_concurrency
- std::thread [C++], join
- std::thread [C++], joinable
- std::thread [C++], native_handle
- std::thread [C++], swap
ms.workload:
- cplusplus
ms.openlocfilehash: bfcb554b374d035e85d53d769d04317e52e4193b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="thread-class"></a>thread — Klasa

Definiuje obiekt, który jest używany do obserwowania i zarządzania wątkiem wykonywania w obrębie aplikacji.

## <a name="syntax"></a>Składnia

```cpp
class thread;
```

## <a name="remarks"></a>Uwagi

Można użyć obiektu `thread`, aby obserwować i zarządzać wątkiem wykonywania w obrębie aplikacji. Obiekt wątku, który jest tworzony przy użyciu konstruktora domyślnego nie jest skojarzony z żadnym wątkiem wykonywania. Obiekt wątku, który jest konstruowany przy użyciu wywoływanego obiektu tworzy nowy wątek wykonywania i wywołuje obiekt w tym wątku. Obiekty wątków można przenosić, ale nie kopiować. W związku z tym wątek wykonywania może być skojarzony tylko z jednym obiektem wątku.

Każdy wątek wykonywania ma unikatowy identyfikator typu `thread::id`. Funkcja `this_thread::get_id` zwraca identyfikator wywołującego wątku. Element członkowski funkcji `thread::get_id` zwraca identyfikator wątku, który jest zarządzany przez obiekt wątku. Dla obiektu wątku zbudowanego domyślnie, metoda `thread::get_id` zwraca obiekt o wartości, która jest taka sama dla wszystkich obiektów wątku zbudowanego domyślnie i różni się od wartości zwracanej przez `this_thread::get_id` dla każdego wątku wykonywania, która może być połączona w momencie wywołania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-classes"></a>Klas publicznych

|Nazwa|Opis|
|----------|-----------------|
|[Thread::ID — klasa](#id_class)|Jednoznacznie identyfikuje skojarzony wątek.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[wątek](#thread)|Konstruuje `thread` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Odłączanie](#detach)|Odłącza skojarzony wątek od obiektu `thread`.|
|[get_id](#get_id)|Zwraca unikatowy identyfikator skojarzonego wątku.|
|[hardware_concurrency](#hardware_concurrency)|Statyczna. Zwraca szacunkową liczbę kontekstów wątków sprzętu.|
|[join](#join)|Blokuje, aż do zakończenia skojarzonego wątku.|
|[podlegającego sprzęganiu](#joinable)|Określa, czy skojarzony wątek podlega sprzęganiu.|
|[native_handle](#native_handle)|Zwraca typ zależny od implementacji, który reprezentuje dojście wątku.|
|[swap](#swap)|Zamienia stan obiektu z określonym obiektem `thread`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Thread::operator =](#op_eq)|Kojarzy bieżący wątek z obiektem `thread`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wątku >

**Namespace:** Standard

## <a name="detach"></a>  Thread::detach

Odłącza skojarzone wątku. System operacyjny staje się odpowiedzialny za zwolnienie zasobów wątków na zakończenie.

```cpp
void detach();
```

### <a name="remarks"></a>Uwagi

Po wywołaniu `detach`, kolejnych wywołań [get_id](#get_id) zwracać [identyfikator](#id_class).

Jeśli nie podlegającego sprzęganiu wątku, który jest skojarzony z obiektem wywołującym, funkcja zwraca [system_error —](../standard-library/system-error-class.md) mający z kodem błędu `invalid_argument`.

Jeśli wątek, który jest skojarzony z obiektem wywołującym jest nieprawidłowa, funkcja zwraca `system_error` mający z kodem błędu `no_such_process`.

## <a name="get_id"></a>  Thread::get_id

Zwraca unikatowy identyfikator skojarzony wątku.

```cpp
id get_id() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

A [Thread::ID —](#id_class) obiektu, który unikatowo identyfikuje skojarzone wątku lub `thread::id()` Jeśli wątku nie jest skojarzony z obiektem.

## <a name="hardware_concurrency"></a>  Thread::hardware_concurrency

Metoda statyczna, która zwraca wartość szacunkową liczbę wątków sprzętu.

```cpp
static unsigned int hardware_concurrency() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Szacowana liczba wątków sprzętu. Jeśli wartości nie można obliczyć lub nie jest jasno określone, ta metoda zwraca wartość 0.

## <a name="id_class"></a>  Thread::ID — klasa

Zawiera unikatowy identyfikator dla każdego wątku do wykonania procesu.

```cpp
class thread::id {
    id() noexcept;
};
```

### <a name="remarks"></a>Uwagi

Domyślny konstruktor tworzy obiekt, który porównuje równa `thread::id` obiektu wszelkie istniejące wątku.

Wszystkie wykonane domyślne `thread::id` porównanie obiektów.

## <a name="join"></a>  Thread::JOIN

Bloki do chwili zakończenia wątku do wykonania, który został skojarzony z obiektem wywołującym.

```cpp
void join();
```

### <a name="remarks"></a>Uwagi

Jeśli wywołanie zakończy się powodzeniem, kolejne wywołania [get_id](#get_id) dla obiekt wywołujący zwracać wartości domyślnej [Thread::ID —](#id_class) nie porównujące równa `thread::id` wszelkie istniejące wątku; wywołanie nie powiodło się. , wartość, która jest zwracana w wyniku `get_id` niezmieniona.

## <a name="joinable"></a>  Thread::joinable

Określa, czy wątek skojarzony *podlegającego sprzęganiu*.

```cpp
bool joinable() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli wątek skojarzony jest *podlegającego sprzęganiu*; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Obiekt wątku jest *podlegającego sprzęganiu* Jeśli `get_id() != id()`.

## <a name="native_handle"></a>  Thread::native_handle

Zwraca typ zależny od implementacji, który reprezentuje dojście wątku. Dojście wątku można w sposób konkretnej implementacji.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Wartość zwracana

`native_handle_type` nie zdefiniowano jako Win32 `HANDLE` który jest rzutowany jako `void *`.

## <a name="op_eq"></a>  Thread::operator =

Kojarzy wątek określony obiekt z bieżącego obiektu.

```cpp
thread& operator=(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

`Other` A `thread` obiektu.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Wywołania metody detach w przypadku wywoływania obiektu podlegającego sprzęganiu.

Po dokonaniu skojarzenia `Other` ustawiono stanie skonstruowany domyślne.

## <a name="swap"></a>  Thread::swap

Zamienia stanu obiektu z tym określonej `thread` obiektu.

```cpp
void swap(thread& Other) noexcept;
```

### <a name="parameters"></a>Parametry

`Other` A `thread` obiektu.

## <a name="thread"></a>  Thread::Thread — Konstruktor

Konstruuje `thread` obiektu.

```cpp
thread() noexcept;
template <class Fn, class... Args>
explicit thread(Fn&& F, Args&&... A);

thread(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

`F` Zdefiniowane przez aplikację funkcji ma być wykonane przez wątek.

`A` Lista argumentów, które mają być przekazane do `F`.

`Other` Istniejące `thread` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktora tworzy obiekt, który nie został skojarzony z wykonanie wątku. Wartość zwracana przez wywołanie do `get_id` skonstruowanego obiektu jest `thread::id()`.

Drugi Konstruktor konstrukcji obiektu, który jest skojarzony z nowego wątku wykonania i wykonuje pseudo-funkcja `INVOKE` zdefiniowanego w [ \<funkcjonalności >](../standard-library/functional.md). Jeśli nie ma wystarczającej ilości zasobów są dostępne, można rozpocząć nowego wątku, funkcja zwraca [system_error —](../standard-library/system-error-class.md) obiekt, który zawiera kod błędu `resource_unavailable_try_again`. Jeśli wywołanie `F` kończy z nieprzechwycony wyjątek [przerwanie](../standard-library/exception-functions.md#terminate) jest wywoływana.

Trzeci Konstruktor konstrukcji obiektu, który jest skojarzony z wątkiem, z którym skojarzony jest `Other`. `Other` następnie ustaw stan skonstruowany domyślne.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<Wątek >](../standard-library/thread.md)<br/>
