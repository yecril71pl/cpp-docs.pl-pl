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
ms.openlocfilehash: 5bb04b84b723f239c338c02befa8cd3468cec3f2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450083"
---
# <a name="packagedtask-class"></a>packaged_task — Klasa

Opisuje *dostawcę asynchronicznego* , który jest otoką wywołania, której sygnatura `Ty(ArgTypes...)`wywołania to. Skojarzony z nim *stan asynchroniczny* zawiera kopię obiektu, który można wywołać, oprócz potencjalnego wyniku.

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
|[packaged_task:: ~ packaged_task, destruktor](#dtorpackaged_task_destructor)|`packaged_task` Niszczy obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_future](#get_future)|Zwraca [przyszły](../standard-library/future-class.md) obiekt, który ma ten sam stan asynchroniczny.|
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|Wywołuje możliwy do wywołania obiekt, który jest przechowywany w skojarzonym stanie asynchronicznym, i niepodzielnie zapisuje zwracaną wartość.|
|[zresetować](#reset)|Zastępuje skojarzony stan asynchroniczny.|
|[swap](#swap)|Wymienia skojarzony stan asynchroniczny z określonym obiektem.|
|[prawidłowa](#valid)|Określa, czy obiekt ma skojarzony stan asynchroniczny.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[packaged_task:: operator =](#op_eq)|Przenosi skojarzony stan asynchroniczny z określonego obiektu.|
|[packaged_task::operator()](#op_call)|Wywołuje możliwy do wywołania obiekt, który jest przechowywany w skojarzonym stanie asynchronicznym, niepodzielnie zapisuje zwracaną wartość i ustawia stan na *gotowe*.|
|[packaged_task:: operator — bool](#op_bool)|Określa, czy obiekt ma skojarzony stan asynchroniczny.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przyszłe >

**Przestrzeń nazw:** std

## <a name="get_future"></a>packaged_task::get_future

Zwraca obiekt typu `future<Ty>` , który ma ten sam *skojarzony stan asynchroniczny*.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt nie ma skojarzonego stanu asynchronicznego, ta metoda zgłasza [future_error](../standard-library/future-error-class.md) o kodzie `no_state`błędu. `packaged_task`

Jeśli ta metoda została już wywołana dla `packaged_task` obiektu, który ma ten sam, skojarzony stan asynchroniczny, Metoda `future_error` zgłasza, że `future_already_retrieved`ma kod błędu.

## <a name="make_ready_at_thread_exit"></a>packaged_task::make_ready_at_thread_exit

Wywołuje możliwy do wywołania obiekt, który jest przechowywany w *skojarzonym stanie asynchronicznym* , i niepodzielnie zapisuje zwracaną wartość.

```cpp
void make_ready_at_thread_exit(ArgTypes... args);
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt nie ma skojarzonego stanu asynchronicznego, ta metoda zgłasza [future_error](../standard-library/future-error-class.md) o kodzie `no_state`błędu. `packaged_task`

Jeśli ta metoda lub [make_ready_at_thread_exit](#make_ready_at_thread_exit) została już wywołana dla `packaged_task` obiektu, który ma ten sam, skojarzony stan asynchroniczny, metoda zgłasza `future_error` , że ma kod `promise_already_satisfied`błędu.

W przeciwnym razie ten operator `INVOKE(fn, args..., Ty)`wywołuje, gdzie *Fn* jest obiektem możliwym do przechowania w skojarzonym stanie asynchronicznym. Zwracana wartość jest przechowywana niepodzielnie jako wynikowy skojarzony stan asynchroniczny.

W przeciwieństwie do [packaged_task:: operator ()](#op_call), skojarzony stan asynchroniczny nie jest ustawiony `ready` na dopóki wszystkie obiekty lokalne wątku w wątku wywołującym zostaną zniszczone. Zazwyczaj wątki, które są blokowane w skojarzonym stanie asynchronicznym, nie są odblokowywane do momentu zakończenia wątku wywołującego.

## <a name="op_eq"></a>packaged_task:: operator =

Przenosi *skojarzony stan asynchroniczny* z określonego obiektu.

```cpp
packaged_task& operator=(packaged_task&& Right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Element `packaged_task` obiektu.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Po *operacji nie ma* już skojarzonego stanu asynchronicznego.

## <a name="op_call"></a>packaged_task:: operator ()

Wywołuje możliwy do wywołania obiekt, który jest przechowywany w *skojarzonym stanie asynchronicznym*, niepodzielnie zapisuje zwracaną wartość i ustawia stan na *gotowe*.

```cpp
void operator()(ArgTypes... args);
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt nie ma skojarzonego stanu asynchronicznego, ta metoda zgłasza [future_error](../standard-library/future-error-class.md) o kodzie `no_state`błędu. `packaged_task`

Jeśli ta metoda lub [make_ready_at_thread_exit](#make_ready_at_thread_exit) została już wywołana dla `packaged_task` obiektu, który ma ten sam, skojarzony stan asynchroniczny, metoda zgłasza `future_error` , że ma kod `promise_already_satisfied`błędu.

W przeciwnym razie ten operator `INVOKE(fn, args..., Ty)`wywołuje, gdzie *Fn* jest obiektem możliwym do przechowania w skojarzonym stanie asynchronicznym. Każda zwrócona wartość jest przechowywana niepodzielnie jako wynikowy skojarzony stan asynchroniczny, a stan jest ustawiony na gotowe. W efekcie wszystkie wątki, które są blokowane w skojarzonym stanie asynchronicznym, zostaną odblokowane.

## <a name="op_bool"></a>packaged_task:: operator — bool

Określa, czy obiekt ma `associated asynchronous state`.

```cpp
operator bool() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

ma **wartość true** , jeśli obiekt ma skojarzony stan asynchroniczny; w przeciwnym razie **false**.

## <a name="packaged_task"></a>packaged_task::p Konstruktor ackaged_task

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

*Kliknij*\
Element `packaged_task` obiektu.

*alokacj*\
Alokator pamięci. Aby uzyskać więcej informacji, zobacz [ \<przypisania >](../standard-library/allocators-header.md).

*Fn*\
Obiekt funkcyjny.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje `packaged_task` obiekt, który nie ma *skojarzonego stanu asynchronicznego*.

Drugi Konstruktor konstruuje `packaged_task` obiekt i transferuje skojarzony stan asynchroniczny z *prawej strony*. Po *operacji nie ma* już skojarzonego stanu asynchronicznego.

Trzeci Konstruktor konstruuje `packaged_task` obiekt, który ma kopię *Fn* przechowywaną w skojarzonym stanie asynchronicznym.

Czwarty Konstruktor konstruuje `packaged_task` obiekt, który ma kopię *Fn* przechowywaną w skojarzonym stanie asynchronicznym, `alloc` i używa dla alokacji pamięci.

## <a name="dtorpackaged_task_destructor"></a>packaged_task:: ~ packaged_task, destruktor

`packaged_task` Niszczy obiekt.

```cpp
~packaged_task();
```

### <a name="remarks"></a>Uwagi

Jeśli *skojarzony stan asynchroniczny* nie jest *gotowy*, destruktor przechowuje wyjątek [future_error](../standard-library/future-error-class.md) , który `broken_promise` ma kod błędu jako wynik w skojarzonym stanie asynchronicznym, oraz wszystkie wątki, które są blokowane na skojarzony stan asynchroniczny zostaje odblokowany.

## <a name="reset"></a>packaged_task:: Reset

Używa nowego *skojarzonego stanu asynchronicznego* w celu zastąpienia istniejącego skojarzonego stanu asynchronicznego.

```cpp
void reset();
```

### <a name="remarks"></a>Uwagi

W efekcie ta metoda jest wykonywana `*this = packaged_task(move(fn))`, gdzie *Fn* jest obiektem funkcji, który jest przechowywany w skojarzonym stanie asynchronicznym dla tego obiektu. W związku z tym, stan obiektu jest wyczyszczony, a [get_future](#get_future), [operator ()](#op_call)i [make_ready_at_thread_exit](#make_ready_at_thread_exit) można wywołać tak jak w przypadku nowo skonstruowanego obiektu.

## <a name="swap"></a>packaged_task:: swap

Wymienia skojarzony stan asynchroniczny z określonym obiektem.

```cpp
void swap(packaged_task& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Element `packaged_task` obiektu.

## <a name="valid"></a>packaged_task:: prawidłowe

Określa, czy obiekt ma `associated asynchronous state`.

```cpp
bool valid() const;
```

### <a name="return-value"></a>Wartość zwracana

ma **wartość true** , jeśli obiekt ma skojarzony stan asynchroniczny; w przeciwnym razie **false**.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
