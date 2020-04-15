---
title: promise — Klasa
ms.date: 10/18/2018
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.openlocfilehash: a6541fefb2423853f8e59a662e1c8a37777dc14c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323038"
---
# <a name="promise-class"></a>promise — Klasa

Opisuje *asynchroniiowego dostawcę*.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
class promise;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Obietnica](#promise)|Konstruuje `promise` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_future](#get_future)|Zwraca [przyszłość](../standard-library/future-class.md) skojarzoną z tą obietnicą.|
|[set_exception](#set_exception)|Niepodzielnie ustawia wynik tej obietnicy, aby wskazać wyjątek.|
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|Niepodzielnie ustawia wynik tej obietnicy, aby wskazać wyjątek i dostarcza powiadomienie tylko po wszystkie obiekty lokalne wątku w bieżącym wątku zostały zniszczone (zwykle przy wyjściu wątku).|
|[set_value](#set_value)|Atomicznie ustawia wynik tej obietnicy, aby wskazać wartość.|
|[set_value_at_thread_exit](#set_value_at_thread_exit)|Niepodzielnie ustawia wynik tej obietnicy, aby wskazać wartość i dostarcza powiadomienie tylko po wszystkie obiekty lokalne wątku w bieżącym wątku zostały zniszczone (zwykle przy wyjściu wątku).|
|[Wymiany](#swap)|Wymienia *skojarzony stan asynchroniczne* tej obietnicy z określonym obiektem obietnicy.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[obietnica::operator=](#op_eq)|Przypisanie wspólnego stanu tego obiektu obietnicy.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

*Obietnica*

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przyszłe>

**Przestrzeń nazw:** std

## <a name="promiseget_future"></a><a name="get_future"></a>obietnica::get_future

Zwraca [przyszły](../standard-library/future-class.md) obiekt, który ma ten sam *skojarzony stan asynchroniczne,* jak ta obietnica.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt promise jest pusty, ta metoda zgłasza [future_error,](../standard-library/future-error-class.md) który ma `no_state` [error_code](../standard-library/error-code-class.md) .

Jeśli ta metoda została już wywołana dla obiektu promise, który ma ten sam skojarzony stan asynchroniczne, metoda zgłasza, `future_error` że ma `error_code` . `future_already_retrieved`

## <a name="promiseoperator"></a><a name="op_eq"></a>obietnica::operator=

Przenosi *skojarzony stan asynchroniczne* `promise` z określonego obiektu.

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Innych*\
Obiekt `promise`.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Ten operator przenosi skojarzony stan asynchroniczne z *Inne*. Po *przeniesieniu, Inne* jest *puste*.

## <a name="promisepromise-constructor"></a><a name="promise"></a>obietnica::pprocesowy konstruktor

Konstruuje `promise` obiekt.

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Al*\
Alokator pamięci. Aby uzyskać [ \<więcej informacji, zobacz>alokatorów.](../standard-library/allocators-header.md)

*Innych*\
Obiekt `promise`.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor tworzy *pusty* `promise` obiekt.

Drugi konstruktor tworzy `promise` pusty obiekt i używa *Al* do alokacji pamięci.

Trzeci konstruktor `promise` konstruuje obiekt i przenosi skojarzony stan asynchroniczne z *Other*i pozostawia *Inne* puste.

## <a name="promiseset_exception"></a><a name="set_exception"></a>obietnica::set_exception

Atomically przechowuje wyjątek w `promise` wyniku tego obiektu i ustawia *skojarzony stan asynchroniczne,* aby *był gotowy.*

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>Parametry

*Exc*\
[exception_ptr,](../standard-library/exception-typedefs.md#exception_ptr) który jest przechowywany przez tę metodę jako wynik wyjątku.

### <a name="remarks"></a>Uwagi

Jeśli `promise` obiekt nie ma skojarzonego stanu asynchronitycznego, ta metoda zgłasza [future_error,](../standard-library/future-error-class.md) `no_state`który ma kod błędu .

Jeśli `set_exception`, [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value)lub [set_value_at_thread_exit](#set_value_at_thread_exit) został już wywołany `promise` dla obiektu, który ma ten sam skojarzony stan asynchroniczne, ta metoda zgłasza, `future_error` że ma kod błędu `promise_already_satisfied`.

W wyniku tej metody wszystkie wątki, które są zablokowane w skojarzonym stanie asynchroniczne stają się odblokowane.

## <a name="promiseset_exception_at_thread_exit"></a><a name="set_exception_at_thread_exit"></a>obietnica::set_exception_at_thread_exit

Niepodzielnie ustawia wynik `promise` tego, aby wskazać wyjątek, dostarczanie powiadomienia tylko po wszystkie wątku lokalnych obiektów w bieżącym wątku zostały zniszczone (zwykle przy wyjściu wątku).

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>Parametry

*Exc*\
[exception_ptr,](../standard-library/exception-typedefs.md#exception_ptr) który jest przechowywany przez tę metodę jako wynik wyjątku.

### <a name="remarks"></a>Uwagi

Jeśli obiekt promise nie ma *skojarzonego stanu asynchronicznego,* ta metoda zgłasza [future_error,](../standard-library/future-error-class.md) który ma kod błędu `no_state`.

Jeśli [set_exception](#set_exception), `set_exception_at_thread_exit` [, set_value](#set_value)lub [set_value_at_thread_exit](#set_value_at_thread_exit) został już wywołany `promise` dla obiektu, który ma ten sam skojarzony stan asynchroniczne, ta metoda zgłasza, `future_error` że ma kod błędu . `promise_already_satisfied`

W przeciwieństwie do [set_exception,](#set_exception)ta metoda nie ustawia skojarzonego stanu asynchroniczne, aby był gotowy, dopóki nie zostały zniszczone wszystkie obiekty lokalne wątku w bieżącym wątku. Zazwyczaj wątki, które są blokowane w skojarzonym stanie asynchroniiowym nie są odblokowane, dopóki bieżący wątek nie zakończy.

## <a name="promiseset_value"></a><a name="set_value"></a>obietnica::set_value

Niepodzielnie przechowuje wartość w `promise` wyniku tego obiektu i ustawia *skojarzony stan asynchroniczne* *na gotowy.*

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>Parametry

*Val*\
Wartość, która ma być przechowywana w wyniku.

### <a name="remarks"></a>Uwagi

Jeśli `promise` obiekt nie ma skojarzonego stanu asynchronitycznego, ta metoda zgłasza [future_error,](../standard-library/future-error-class.md) `no_state`który ma kod błędu .

Jeśli [set_exception](#set_exception) [, set_exception_at_thread_exit](#set_exception_at_thread_exit), `set_value`lub [set_value_at_thread_exit](#set_value_at_thread_exit) został już wywołany `promise` dla obiektu, który ma ten sam skojarzony stan asynchroniczne, ta metoda zgłasza, `future_error` że ma kod błędu . `promise_already_satisfied`

W wyniku tej metody wszystkie wątki, które są zablokowane w skojarzonym stanie asynchroniczne stają się odblokowane.

Pierwsza metoda zgłasza również wyjątek, który jest zgłaszany, gdy *Val* jest kopiowany do skojarzonego stanu asynchronitycznego. W tej sytuacji skojarzony stan asynchroniczne nie jest ustawiona na gotowe.

Druga metoda zgłasza również wyjątek, który jest zgłaszany, gdy *Val* jest przenoszony do skojarzonego stanu asynchroniczne. W tej sytuacji skojarzony stan asynchroniczne nie jest ustawiona na gotowe.

W przypadku specjalizacji `promise<Ty&>`częściowej wartość przechowywana jest w rzeczywistości odwołaniem do *Val*.

Dla specjalizacji `promise<void>`nie istnieje wartość przechowywana.

## <a name="promiseset_value_at_thread_exit"></a><a name="set_value_at_thread_exit"></a>obietnica::set_value_at_thread_exit

Atomically przechowuje wartość w `promise` wyniku tego obiektu.

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>Parametry

*Val*\
Wartość, która ma być przechowywana w wyniku.

### <a name="remarks"></a>Uwagi

Jeśli obiekt promise nie ma *skojarzonego stanu asynchronicznego,* ta metoda zgłasza [future_error,](../standard-library/future-error-class.md) który ma kod błędu `no_state`.

Jeśli [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit) [, set_value](#set_value)lub `set_value_at_thread_exit` został już wywołany `promise` dla obiektu, który ma ten sam skojarzony stan asynchroniczne, ta metoda zgłasza, `future_error` że ma kod błędu . `promise_already_satisfied`

W przeciwieństwie `set_value`do , skojarzony stan asynchroniczne nie jest ustawiona na gotowe, dopóki nie wszystkie wątku lokalnych obiektów w bieżącym wątku zostały zniszczone. Zazwyczaj wątki, które są blokowane w skojarzonym stanie asynchroniiowym nie są odblokowane, dopóki bieżący wątek nie zakończy.

Pierwsza metoda zgłasza również wyjątek, który jest zgłaszany, gdy *Val* jest kopiowany do skojarzonego stanu asynchronitycznego.

Druga metoda zgłasza również wyjątek, który jest zgłaszany, gdy *Val* jest przenoszony do skojarzonego stanu asynchroniczne.

W przypadku specjalizacji `promise<Ty&>`częściowej przechowywana wartość jest skutecznie odwołaniem do *val*.

Dla specjalizacji `promise<void>`nie istnieje wartość przechowywana.

## <a name="promiseswap"></a><a name="swap"></a>obietnica::swap

Wymienia *skojarzony stan asynchroniczne* tego obiektu obietnicy z obiektem określonego obiektu.

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Innych*\
Obiekt `promise`.

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
