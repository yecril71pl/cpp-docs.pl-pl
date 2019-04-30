---
title: thread — Klasa
ms.date: 11/04/2016
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
ms.assetid: df249bc7-ff81-4ff9-a6d6-5e3d9a8f56a1
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
ms.openlocfilehash: d1405062ef553dbfea3b60b5f39e0546707343b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412075"
---
# <a name="thread-class"></a>thread — Klasa

Definiuje obiekt, który jest używany do obserwowania i zarządzania wątkiem wykonywania w obrębie aplikacji.

## <a name="syntax"></a>Składnia

```cpp
class thread;
```

## <a name="remarks"></a>Uwagi

Możesz użyć **wątku** obiektu do obserwowania i zarządzania wątkiem wykonywania w obrębie aplikacji. Obiekt wątku, który jest tworzony przy użyciu konstruktora domyślnego nie jest skojarzony z żadnym wątkiem wykonywania. Obiekt wątku, który jest konstruowany przy użyciu wywoływanego obiektu tworzy nowy wątek wykonywania i wywołuje obiekt w tym wątku. Obiekty wątków można przenosić, ale nie kopiować. W związku z tym wątek wykonywania może być skojarzony tylko z jednym obiektem wątku.

Każdy wątek wykonywania ma unikatowy identyfikator typu `thread::id`. Funkcja `this_thread::get_id` zwraca identyfikator wywołującego wątku. Element członkowski funkcji `thread::get_id` zwraca identyfikator wątku, który jest zarządzany przez obiekt wątku. Dla obiektu wątku zbudowanego domyślnie, metoda `thread::get_id` zwraca obiekt o wartości, która jest taka sama dla wszystkich obiektów wątku zbudowanego domyślnie i różni się od wartości zwracanej przez `this_thread::get_id` dla każdego wątku wykonywania, która może być połączona w momencie wywołania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-classes"></a>Publiczne klasy

|Nazwa|Opis|
|----------|-----------------|
|[Thread::ID — klasa](#id_class)|Jednoznacznie identyfikuje skojarzony wątek.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[wątek](#thread)|Konstruuje **wątku** obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Odłącz](#detach)|Odłącza skojarzony wątek od **wątku** obiektu.|
|[get_id](#get_id)|Zwraca unikatowy identyfikator skojarzonego wątku.|
|[hardware_concurrency](#hardware_concurrency)|Statyczne. Zwraca szacunkową liczbę kontekstów wątków sprzętu.|
|[join](#join)|Blokuje, aż do zakończenia skojarzonego wątku.|
|[sprzęganiu](#joinable)|Określa, czy skojarzony wątek podlega sprzęganiu.|
|[native_handle](#native_handle)|Zwraca typ zależny od implementacji, który reprezentuje dojście wątku.|
|[swap](#swap)|Zamienia stan obiektu z określonym **wątku** obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Thread::operator =](#op_eq)|Kojarzy wątku z bieżącej **wątku** obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wątku >

**Namespace:** standardowe

## <a name="detach"></a>  Thread::detach —

Odłącza skojarzony wątek. System operacyjny staje się odpowiedzialny za przy zwalnianiu zasobów wątków na zakończenie.

```cpp
void detach();
```

### <a name="remarks"></a>Uwagi

Po wywołaniu `detach`, kolejne wywołania [get_id —](#get_id) zwracają [identyfikator](#id_class).

Jeśli wątek, który ma skojarzony obiekt wywołujący nie jest sprzęganiu, funkcja zgłasza [system_error](../standard-library/system-error-class.md) zawierający kod błędu `invalid_argument`.

Jeśli wątek, który jest skojarzony z obiektem wywołującym jest nieprawidłowa, funkcja zgłasza `system_error` zawierający kod błędu `no_such_process`.

## <a name="get_id"></a>  Thread::get_id —

Zwraca unikatowy identyfikator skojarzonego wątku.

```cpp
id get_id() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

A [Thread::ID —](#id_class) obiekt, który jednoznacznie identyfikuje skojarzony wątek lub `thread::id()` Jeśli żaden wątek nie jest skojarzony z obiektem.

## <a name="hardware_concurrency"></a>  Thread::hardware_concurrency —

Metoda statyczna zwraca szacunkową liczbę kontekstów wątków sprzętu.

```cpp
static unsigned int hardware_concurrency() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Szacunkową liczbę kontekstów wątków sprzętu. Jeśli wartość nie można obliczyć lub nie jest dobrze zdefiniowane, ta metoda zwraca wartość 0.

## <a name="id_class"></a>  Thread::ID — klasa

Zawiera unikatowy identyfikator dla każdego wątku wykonywania procesu.

```cpp
class thread::id {
    id() noexcept;
};
```

### <a name="remarks"></a>Uwagi

Domyślny konstruktor tworzy obiekt, który porównuje równa `thread::id` obiekt dla każdego istniejącego wątku.

Wszystkie zbudowanego domyślnie `thread::id` obiekty są sobie równe.

## <a name="join"></a>  Thread::JOIN —

Blokuje, aż do zakończenia wątku wykonywania, który jest skojarzony z obiektem wywołującym.

```cpp
void join();
```

### <a name="remarks"></a>Uwagi

Jeśli wywołanie zakończy się powodzeniem, kolejne wywołania [get_id —](#get_id) obiekt wywołujący można powrócić w domyślnego [Thread::ID —](#id_class) nie porównujące równa `thread::id` z dowolnego istniejącego wątku; Jeśli wywołanie powiedzie się , wartość, która jest zwracana przez `get_id` pozostaje niezmieniony.

## <a name="joinable"></a>  Thread::joinable —

Określa, czy skojarzony wątek podlega *sprzęganiu*.

```cpp
bool joinable() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** jeśli skojarzony wątek podlega *sprzęganiu*; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Obiekt wątku jest *sprzęganiu* Jeśli `get_id() != id()`.

## <a name="native_handle"></a>  Thread::native_handle —

Zwraca typ zależny od implementacji, który reprezentuje dojście wątku. Dojście wątku może służyć w sposób specyficzne dla implementacji.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Wartość zwracana

`native_handle_type` jest zdefiniowany jako Win32 `HANDLE` , jest rzutowany jako `void *`.

## <a name="op_eq"></a>  Thread::operator =

Kojarzy wątku określony obiekt z bieżącego obiektu.

```cpp
thread& operator=(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Inne*<br/>
A **wątku** obiektu.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Wywołań metod odłączyć, jeśli obiekt wywołujący podlega sprzęganiu.

Po dokonaniu skojarzenia `Other` ustawiono stan zbudowanego domyślnie.

## <a name="swap"></a>  Thread::swap —

Zamienia stan obiektu, z którego określonego **wątku** obiektu.

```cpp
void swap(thread& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Inne*<br/>
A **wątku** obiektu.

## <a name="thread"></a>  Thread::Thread — Konstruktor

Konstruuje **wątku** obiektu.

```cpp
thread() noexcept;
template <class Fn, class... Args>
explicit thread(Fn&& F, Args&&... A);

thread(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*F*<br/>
Zdefiniowane przez aplikację funkcji wykonywanej przez wątek.

*A*<br/>
Lista argumentów do przekazania do *F*.

*Inne*<br/>
Istniejące **wątku** obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje obiekt, który nie został skojarzony z wątkiem wykonywania. Wartość, która jest zwracana przez wywołanie `get_id` skonstruowanego obiektu jest `thread::id()`.

Drugi Konstruktor konstruuje obiekt, który jest skojarzony z nowy wątek wykonywania i wykonuje pseudo-funkcję `INVOKE` zdefiniowanego w [ \<funkcjonalności >](../standard-library/functional.md). Jeśli nie ma wystarczającej ilości zasobów dostępnych może rozpocząć nowego wątku, funkcja zgłasza [system_error](../standard-library/system-error-class.md) obiekt, który ma kod błędu `resource_unavailable_try_again`. Jeśli wywołanie *F* kończy nieprzechwycony wyjątek [zakończyć](../standard-library/exception-functions.md#terminate) jest wywoływana.

Trzeci Konstruktor konstruuje obiekt, który jest skojarzony z wątkiem, który jest skojarzony z `Other`. `Other` następnie ustaw stan zbudowanego domyślnie.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<Wątek >](../standard-library/thread.md)<br/>
