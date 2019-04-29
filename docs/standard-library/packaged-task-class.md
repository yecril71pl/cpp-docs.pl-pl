---
title: packaged_task — Klasa
ms.date: 11/04/2016
f1_keywords:
- future/std::packaged_task
- future/std::packaged_task::packaged_task
- future/std::packaged_task::get_future
- future/std::packaged_task::make_ready_at_thread_exit
- future/std::packaged_task::reset
- future/std::packaged_task::swap
- future/std::packaged_task::valid
- future/std::packaged_task::operator()
- future/std::packaged_task::operator bool
ms.assetid: 0a72cbe3-f22a-4bfe-8e50-dcb268c98780
helpviewer_keywords:
- std::packaged_task [C++]
- std::packaged_task [C++], packaged_task
- std::packaged_task [C++], get_future
- std::packaged_task [C++], make_ready_at_thread_exit
- std::packaged_task [C++], reset
- std::packaged_task [C++], swap
- std::packaged_task [C++], valid
ms.openlocfilehash: e759b1bc8cb47c5c943f29545e3b03ee535f3df7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370674"
---
# <a name="packagedtask-class"></a>packaged_task — Klasa

W tym artykule opisano *dostawcę asynchronicznego* czyli otokę wywołania ma podpis wywołania `Ty(ArgTypes...)`. Jego *asynchroniczny stan stowarzyszony* przechowuje kopię jego wywoływanego obiektu, oprócz potencjalnym wynik.

## <a name="syntax"></a>Składnia

```cpp
template <class>
class packaged_task;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[packaged_task](#packaged_task)|Konstruuje `packaged_task` obiektu.|
|[packaged_task:: ~ packaged_task — destruktor](#dtorpackaged_task_destructor)|Niszczy `packaged_task` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_future](#get_future)|Zwraca [przyszłych](../standard-library/future-class.md) obiekt, który ma ten sam asynchroniczny stan stowarzyszony.|
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|Wywołuje wywoływanego obiektu, który znajduje się w stanie stowarzyszonym asynchroniczne i niepodzielne przechowuje zwracanej wartości.|
|[Resetuj](#reset)|Zastępuje stowarzyszonym stanie asynchronicznym.|
|[swap](#swap)|Zamienia asynchronicznego stanu stowarzyszonego z tym określonego obiektu.|
|[Nieprawidłowa](#valid)|Określa, czy obiekt posiada asynchronicznego stanu stowarzyszonego.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[packaged_task::operator=](#op_eq)|Przesyła asynchronicznego stanu stowarzyszonego z określonego obiektu.|
|[packaged_task::operator()](#op_call)|Wywołuje obiekt, który znajduje się w stanie stowarzyszonym asynchroniczne niepodzielnie przechowuje zwrócona wartość i ustawia stan *gotowe*.|
|[packaged_task::operator bool](#op_bool)|Określa, czy obiekt posiada asynchronicznego stanu stowarzyszonego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przyszłych >

**Namespace:** standardowe

## <a name="get_future"></a>  packaged_task::get_future —

Zwraca obiekt typu `future<Ty>` ma taką samą *asynchroniczny stan stowarzyszony*.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Uwagi

Jeśli `packaged_task` obiekt nie posiada asynchronicznego stanu stowarzyszonego, ta metoda wyrzuca [future_error](../standard-library/future-error-class.md) zawierający kod błędu `no_state`.

Jeśli ta metoda została już wywołana dla `packaged_task` obiekt, który ma ten sam asynchroniczny stan stowarzyszony, metoda zgłasza `future_error` zawierający kod błędu `future_already_retrieved`.

## <a name="make_ready_at_thread_exit"></a>  packaged_task::make_ready_at_thread_exit —

Wywołuje obiekt, który jest przechowywany w *asynchroniczny stan stowarzyszony* i niepodzielne przechowuje zwracanej wartości.

```cpp
void make_ready_at_thread_exit(ArgTypes... args);
```

### <a name="remarks"></a>Uwagi

Jeśli `packaged_task` obiekt nie ma asynchronicznego stanu stowarzyszonego, ta metoda wyrzuca [future_error](../standard-library/future-error-class.md) zawierający kod błędu `no_state`.

Jeśli ta metoda lub [make_ready_at_thread_exit](#make_ready_at_thread_exit) została już wywołana dla `packaged_task` obiekt, który ma ten sam asynchroniczny stan stowarzyszony, metoda zgłasza `future_error` zawierający kod błędu `promise_already_satisfied`.

W przeciwnym razie wywołuje ten operator `INVOKE(fn, args..., Ty)`, gdzie *fn* jest wywoływane obiekt, który znajduje się w stanie stowarzyszonym asynchroniczne. Wartości zwracane są przechowywane niepodzielne zwróconego wyniku asynchronicznego stanu stowarzyszonego.

W przeciwieństwie do [packaged_task:: operator() —](#op_call), stowarzyszony stan asynchroniczny nie jest ustawiony na `ready` do momentu zniszczenia wszystkich wątków lokalnych obiektów w wątku wywołującego. Zazwyczaj wątki, które są blokowane w stanie stowarzyszonym asynchroniczne nie są odblokowane, dopóki kończy działanie wątku wywołującego.

## <a name="op_eq"></a>  packaged_task::operator =

Transfery *asynchroniczny stan stowarzyszony* od określonego obiektu.

```cpp
packaged_task& operator=(packaged_task&& Right);
```

### <a name="parameters"></a>Parametry

*po prawej stronie*<br/>
Element `packaged_task` obiektu.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Po tej operacji *po prawej stronie* nie posiada już stowarzyszonego stanu asynchronicznego.

## <a name="op_call"></a>  packaged_task:: operator() —

Wywołuje obiekt, który jest przechowywany w *asynchroniczny stan stowarzyszony*niepodzielnie przechowuje zwrócona wartość i ustawia stan *gotowe*.

```cpp
void operator()(ArgTypes... args);
```

### <a name="remarks"></a>Uwagi

Jeśli `packaged_task` obiekt nie ma asynchronicznego stanu stowarzyszonego, ta metoda wyrzuca [future_error](../standard-library/future-error-class.md) zawierający kod błędu `no_state`.

Jeśli ta metoda lub [make_ready_at_thread_exit](#make_ready_at_thread_exit) została już wywołana dla `packaged_task` obiekt, który ma ten sam asynchroniczny stan stowarzyszony, metoda zgłasza `future_error` zawierający kod błędu `promise_already_satisfied`.

W przeciwnym razie wywołuje ten operator `INVOKE(fn, args..., Ty)`, gdzie *fn* jest wywoływane obiekt, który znajduje się w stanie stowarzyszonym asynchroniczne. Dowolny zwracana wartość jest przechowywana niepodzielne zwróconego wyniku asynchronicznego stanu stowarzyszonego, a stan jest ustawiony na gotowe. Co w efekcie wszelkie wątki, które są zablokowane w stowarzyszonym stanie asynchronicznym zostają odblokowane.

## <a name="op_bool"></a>  packaged_task::operator bool

Określa, czy obiekt ma `associated asynchronous state`.

```cpp
operator bool() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekt ma asynchronicznego stanu stowarzyszonego; w przeciwnym razie **false**.

## <a name="packaged_task"></a>  packaged_task::packaged_task — Konstruktor

Konstruuje `packaged_task` obiektu.

```cpp
packaged_task() noexcept;
packaged_task(packaged_task&& Right) noexcept;
template <class Fn>
   explicit packaged_task(Fn&& fn);

template <class Fn, class Alloc>
   explicit packaged_task(
      allocator_arg_t, const Alloc& alloc, Fn&& fn);
```

### <a name="parameters"></a>Parametry

*po prawej stronie*<br/>
Element `packaged_task` obiektu.

*Alokacji*<br/>
Alokator pamięci. Aby uzyskać więcej informacji, zobacz [ \<buforów >](../standard-library/allocators-header.md).

*FN*<br/>
Obiekt funkcyjny.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje `packaged_task` obiektu, który nie ma *asynchroniczny stan stowarzyszony*.

Drugi Konstruktor konstruuje `packaged_task` obiekt i dokonuje transferu asynchronicznego stanu stowarzyszonego z *po prawej stronie*. Po tej operacji *po prawej stronie* nie posiada już stowarzyszonego stanu asynchronicznego.

Trzeci Konstruktor konstruuje `packaged_task` obiekt, który ma kopię *fn* przechowywane w jego asynchronicznie powiązanym stanie.

Czwarty Konstruktor konstruuje `packaged_task` obiekt, który ma kopię *fn* przechowywane w jego asynchronicznie powiązanym stanie i używa `alloc` dla alokacji pamięci.

## <a name="dtorpackaged_task_destructor"></a>  packaged_task:: ~ packaged_task — destruktor

Niszczy `packaged_task` obiektu.

```cpp
~packaged_task();
```

### <a name="remarks"></a>Uwagi

Jeśli *asynchroniczny stan stowarzyszony* nie jest *gotowe*, magazyny destruktor [future_error](../standard-library/future-error-class.md) wyjątek, który ma kod błędu `broken_promise` jako wynik w asynchronicznie powiązanym stanie i wszelkie wątki, które są zablokowane w stowarzyszonym stanie asynchronicznym zostają odblokowane.

## <a name="reset"></a>  packaged_task::reset —

Używa nowego *asynchroniczny stan stowarzyszony* Aby zastąpić istniejącą asynchroniczny stan stowarzyszony.

```cpp
void reset();
```

### <a name="remarks"></a>Uwagi

W efekcie ta metoda jest wykonywana `*this = packaged_task(move(fn))`, gdzie *fn* jest obiekt funkcji, która jest przechowywana w stowarzyszonym stanie asynchronicznym dla tego obiektu. W związku z tym, stan obiektu jest wyczyszczone, a [get_future](#get_future), [operator()](#op_call), i [make_ready_at_thread_exit](#make_ready_at_thread_exit) może być wywoływana tak, jakby dla nowo utworzonego obiektu.

## <a name="swap"></a>  packaged_task::swap —

Zamienia asynchronicznego stanu stowarzyszonego z tym określonego obiektu.

```cpp
void swap(packaged_task& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*po prawej stronie*<br/>
Element `packaged_task` obiektu.

## <a name="valid"></a>  packaged_task::valid —

Określa, czy obiekt ma `associated asynchronous state`.

```cpp
bool valid() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekt ma asynchronicznego stanu stowarzyszonego; w przeciwnym razie **false**.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<future>](../standard-library/future.md)<br/>
