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
ms.openlocfilehash: eb171e09451e16e89716dfdc44ed6c611e2d2280
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372120"
---
# <a name="packaged_task-class"></a>packaged_task — Klasa

W tym artykule opisano *asynchronikę dostawcy,* `Ty(ArgTypes...)`który jest otoką wywołań, której podpis wywołania jest . Jego *skojarzony stan asynchroniczne* posiada kopię jego wywoływany obiekt oprócz potencjalnego wyniku.

## <a name="syntax"></a>Składnia

```cpp
template <class>
class packaged_task;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[packaged_task](#packaged_task)|Konstruuje `packaged_task` obiekt.|
|[packaged_task::~packaged_task Destruktor](#dtorpackaged_task_destructor)|Niszczy `packaged_task` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_future](#get_future)|Zwraca [przyszły](../standard-library/future-class.md) obiekt, który ma ten sam skojarzony stan asynchroniczne.|
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|Wywołuje wywoływany obiekt, który jest przechowywany w skojarzonym stanie asynchronialnym i niepodzielnie przechowuje zwróconą wartość.|
|[Zresetować](#reset)|Zastępuje skojarzony stan asynchroniczne.|
|[Wymiany](#swap)|Wymienia skojarzony stan asynchroniczne z stanem określonego obiektu.|
|[Prawidłowe](#valid)|Określa, czy obiekt ma skojarzony stan asynchroniczne.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[packaged_task::operator=](#op_eq)|Przenosi skojarzony stan asynchroniczne z określonego obiektu.|
|[packaged_task::operator()](#op_call)|Wywołuje wywoływany obiekt, który jest przechowywany w skojarzonym stanie asynchronialnym, niepodzielnie przechowuje zwróconą wartość i ustawia stan *na gotowy.*|
|[packaged_task::operator bool](#op_bool)|Określa, czy obiekt ma skojarzony stan asynchroniczne.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przyszłe>

**Przestrzeń nazw:** std

## <a name="packaged_taskget_future"></a><a name="get_future"></a>packaged_task::get_future

Zwraca obiekt typu, `future<Ty>` który ma ten sam *skojarzony stan asynchroniczne*.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Uwagi

Jeśli `packaged_task` obiekt nie ma skojarzonego stanu asynchronitycznego, ta metoda zgłasza [future_error,](../standard-library/future-error-class.md) który `no_state`ma kod błędu .

Jeśli ta metoda została już `packaged_task` wywołana dla obiektu, który ma ten sam skojarzony `future_error` stan asynchroniczne, metoda zgłasza, który ma kod błędu `future_already_retrieved`.

## <a name="packaged_taskmake_ready_at_thread_exit"></a><a name="make_ready_at_thread_exit"></a>packaged_task::make_ready_at_thread_exit

Wywołuje wywoływany obiekt, który jest przechowywany w *skojarzonym stanie asynchronialnym* i niepodzielnie przechowuje zwróconą wartość.

```cpp
void make_ready_at_thread_exit(ArgTypes... args);
```

### <a name="remarks"></a>Uwagi

Jeśli `packaged_task` obiekt nie ma skojarzonego stanu asynchronitycznego, ta metoda zgłasza [future_error,](../standard-library/future-error-class.md) który ma `no_state`kod błędu .

Jeśli ta metoda lub [make_ready_at_thread_exit](#make_ready_at_thread_exit) został już `packaged_task` wywołany dla obiektu, który ma ten sam skojarzony `future_error` stan asynchroniczne, metoda zgłasza, który ma kod błędu `promise_already_satisfied`.

W przeciwnym razie `INVOKE(fn, args..., Ty)`ten operator wywołuje , gdzie *fn* jest wywoływany obiekt, który jest przechowywany w stanie asynchroniczne skojarzone. Każda zwracana wartość jest przechowywana niepodzielnie jako zwrócony wynik skojarzonego stanu asynchronicznie.

W przeciwieństwie do [packaged_task::operator()](#op_call), skojarzony stan asynchroniczne `ready` nie jest ustawiony na dopóki wszystkie obiekty lokalne wątku w wątku wywołującym zostały zniszczone. Zazwyczaj wątki, które są blokowane w skojarzonym stanie asynchroniiowym nie są odblokowane, dopóki wątek wywołujący zakończy działanie.

## <a name="packaged_taskoperator"></a><a name="op_eq"></a>packaged_task::operator=

Przenosi *skojarzony stan asynchroniczne* z określonego obiektu.

```cpp
packaged_task& operator=(packaged_task&& Right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Obiekt `packaged_task`.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Po operacji *Right* nie ma już skojarzonego stanu asynchroniowego.

## <a name="packaged_taskoperator"></a><a name="op_call"></a>packaged_task::operator()

Wywołuje wywoływany obiekt, który jest przechowywany w *skojarzonym stanie asynchronialnym,* niepodzielnie przechowuje zwróconą wartość i ustawia stan *na gotowy.*

```cpp
void operator()(ArgTypes... args);
```

### <a name="remarks"></a>Uwagi

Jeśli `packaged_task` obiekt nie ma skojarzonego stanu asynchronitycznego, ta metoda zgłasza [future_error,](../standard-library/future-error-class.md) który ma `no_state`kod błędu .

Jeśli ta metoda lub [make_ready_at_thread_exit](#make_ready_at_thread_exit) został już `packaged_task` wywołany dla obiektu, który ma ten sam skojarzony `future_error` stan asynchroniczne, metoda zgłasza, który ma kod błędu `promise_already_satisfied`.

W przeciwnym razie `INVOKE(fn, args..., Ty)`ten operator wywołuje , gdzie *fn* jest wywoływany obiekt, który jest przechowywany w stanie asynchroniczne skojarzone. Każda zwracana wartość jest przechowywana niepodzielnie jako zwrócony wynik skojarzonego stanu asynchronicznie, a stan jest ustawiony na gotowy. W rezultacie wszystkie wątki, które są zablokowane w skojarzonym stanie asynchronizańskim, zostaną odblokowane.

## <a name="packaged_taskoperator-bool"></a><a name="op_bool"></a>packaged_task::operator bool

Określa, czy obiekt `associated asynchronous state`ma plik .

```cpp
operator bool() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli obiekt ma skojarzony stan asynchroniczne; w przeciwnym razie **false**.

## <a name="packaged_taskpackaged_task-constructor"></a><a name="packaged_task"></a>packaged_task::packaged_task Konstruktor

Konstruuje `packaged_task` obiekt.

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

*Prawo*\
Obiekt `packaged_task`.

*Alloc*\
Alokator pamięci. Aby uzyskać więcej informacji, zobacz [ \<>alokatorów ](../standard-library/allocators-header.md).

*Fn*\
Obiekt funkcyjny.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor tworzy `packaged_task` obiekt, który nie ma *skojarzonego stanu asynchroniowego.*

Drugi konstruktor konstruuje `packaged_task` obiekt i przenosi skojarzony stan asynchroniczne z *Right*. Po operacji *Right* nie ma już skojarzonego stanu asynchroniowego.

Trzeci konstruktor tworzy `packaged_task` obiekt, który ma kopię *fn* przechowywane w jego skojarzony stan asynchroniczne.

Czwarty konstruktor tworzy `packaged_task` obiekt, który ma kopię *fn* przechowywane w jego skojarzony stan `alloc` asynchroniczne i używa do alokacji pamięci.

## <a name="packaged_taskpackaged_task-destructor"></a><a name="dtorpackaged_task_destructor"></a>packaged_task::~packaged_task Destruktor

Niszczy `packaged_task` obiekt.

```cpp
~packaged_task();
```

### <a name="remarks"></a>Uwagi

Jeśli *skojarzony stan asynchroniczne* nie jest *gotowy,* destruktor przechowuje wyjątek [future_error,](../standard-library/future-error-class.md) który ma kod błędu `broken_promise` jako wynik w skojarzonym stanie asynchronialnym, a wszystkie wątki, które są blokowane w skojarzonym stanie asynchronialnym, zostają odblokowane.

## <a name="packaged_taskreset"></a><a name="reset"></a>packaged_task::reset

Używa nowego *skojarzonego stanu asynchroniowego,* aby zastąpić istniejący skojarzony stan asynchroniczne.

```cpp
void reset();
```

### <a name="remarks"></a>Uwagi

W efekcie ta metoda `*this = packaged_task(move(fn))`wykonuje , gdzie *fn* jest obiektem funkcji, który jest przechowywany w skojarzonym stanie asynchronicznego dla tego obiektu. W związku z tym stan obiektu jest czyszczony i [get_future](#get_future), [operator()](#op_call)i [make_ready_at_thread_exit](#make_ready_at_thread_exit) można wywołać tak, jakby na nowo skonstruowany obiekt.

## <a name="packaged_taskswap"></a><a name="swap"></a>packaged_task::swap

Wymienia skojarzony stan asynchroniczne z stanem określonego obiektu.

```cpp
void swap(packaged_task& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Obiekt `packaged_task`.

## <a name="packaged_taskvalid"></a><a name="valid"></a>packaged_task::prawidłowy

Określa, czy obiekt `associated asynchronous state`ma plik .

```cpp
bool valid() const;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli obiekt ma skojarzony stan asynchroniczne; w przeciwnym razie **false**.

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<przyszłych>](../standard-library/future.md)
