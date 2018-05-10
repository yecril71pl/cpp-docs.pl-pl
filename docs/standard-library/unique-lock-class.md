---
title: unique_lock — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::unique_lock
dev_langs:
- C++
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9888b847c3e52cd8b6a034e95e35ca73933acd3f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="uniquelock-class"></a>unique_lock — Klasa

Reprezentuje szablon, który można wdrożyć do tworzenia obiektów, które zarządzają blokowanie i odblokowywanie `mutex`.

## <a name="syntax"></a>Składnia

```cpp
template <class Mutex>
class unique_lock;
```

## <a name="remarks"></a>Uwagi

Argument szablonu `Mutex` nazwę *typu obiektu mutex*.

Wewnętrznie `unique_lock` wskaźnik do skojarzonego zapisuje `mutex` obiektu i `bool` wskazująca, czy bieżący wątek jest właścicielem `mutex`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Definicje typów publicznych

|Nazwa|Opis|
|----------|-----------------|
|`mutex_type`|Synonim argumentu szablonu `Mutex`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[unique_lock](#unique_lock)|Konstruuje `unique_lock` obiektu.|
|[~unique_lock Destructor](#dtorunique_lock_destructor)|Zwalnia wszystkie zasoby, które są skojarzone z `unique_lock` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Blokuje wątek wywołujący, dopóki wątek uzyskuje własność skojarzonego `mutex`.|
|[mutex](#mutex)|Pobiera przechowywanych wskaźnik do skojarzonego `mutex`.|
|[owns_lock](#owns_lock)|Określa, czy wątek wywołujący jest właścicielem skojarzony `mutex`.|
|[Zlecenia](#release)|Usuwa skojarzenia `unique_lock` skojarzony obiekt `mutex` obiektu.|
|[swap](#swap)|Zamienia skojarzony `mutex` i stan własność określonego obiektu.|
|[try_lock](#try_lock)|Próbuje uzyskać prawo własności do skojarzonego `mutex` bez blokowania.|
|[try_lock_for](#try_lock_for)|Próbuje uzyskać prawo własności do skojarzonego `mutex` bez blokowania.|
|[try_lock_until](#try_lock_until)|Próbuje uzyskać prawo własności do skojarzonego `mutex` bez blokowania.|
|[unlock](#unlock)|Zwalnia własność skojarzonego `mutex`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[bool — operator](#op_bool)|Określa, czy wątek wywołujący jest właścicielem skojarzonego `mutex`.|
|[operator=](#op_eq)|Kopiuje zapisana `mutex` wskaźnik i stan własności skojarzone z określonego obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`unique_lock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<obiektu mutex >

**Namespace:** Standard

## <a name="lock"></a>  blokady

Blokuje wątek wywołujący, dopóki wątek uzyskuje własność skojarzonego `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli zapisana `mutex` wskaźnika jest `null`, ta metoda zgłasza [system_error —](../standard-library/system-error-class.md) mający z kodem błędu `operation_not_permitted`.

Jeśli wątek wywołujący już właścicielem skojarzony `mutex`, ta metoda zgłasza `system_error` mający z kodem błędu `resource_deadlock_would_occur`.

W przeciwnym razie ta metoda wywołuje `lock` na skojarzonym `mutex` i ustawia flagę własność wewnętrzny wątek `true`.

## <a name="mutex"></a>  mutex

Pobiera przechowywanych wskaźnik do skojarzonego `mutex`.

```cpp
mutex_type *mutex() const noexcept;
```

## <a name="op_bool"></a>  bool — operator

Określa, czy wątek wywołujący jest właścicielem skojarzonego obiektu mutex.

```cpp
explicit operator bool() noexcept
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli wątek jest właścicielem obiektu mutex; w przeciwnym razie `false`.

## <a name="op_eq"></a>  operator =

Kopiuje zapisana `mutex` wskaźnik i stan własności skojarzone z określonego obiektu.

```cpp
unique_lock& operator=(unique_lock&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

`Other` A `unique_lock` obiektu.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest właścicielem wcześniej skojarzone `mutex`, zanim ta metoda wywołuje `unlock` na `mutex`, przypisuje nowe wartości.

Po kopiowania, ta metoda ustawia `Other` skonstruowany domyślny stan.

## <a name="owns_lock"></a>  owns_lock

Określa, czy wątek wywołujący jest właścicielem skojarzony `mutex`.

```cpp
bool owns_lock() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli właścicielem wątku `mutex`; w przeciwnym razie `false`.

## <a name="release"></a>  Zlecenia

Usuwa skojarzenia `unique_lock` skojarzony obiekt `mutex` obiektu.

```cpp
mutex_type *release() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Poprzednią wartość zapisana `mutex` wskaźnika.

### <a name="remarks"></a>Uwagi

Ta metoda powoduje ustawienie wartości przechowywanej `mutex` wskaźnika 0 i ustawia wewnętrznej `mutex` Flaga własność `false`.

## <a name="swap"></a>  Swap

Zamienia skojarzony `mutex` i stan własność określonego obiektu.

```cpp
void swap(unique_lock& Other) noexcept;
```

### <a name="parameters"></a>Parametry

`Other` A `unique_lock` obiektu.

## <a name="try_lock"></a>  try_lock

Próbuje uzyskać prawo własności do skojarzonego `mutex` bez blokowania.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli metoda pomyślnie uzyskuje prawo własności `mutex`; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Jeśli zapisana `mutex` wskaźnika jest `null`, metoda wygeneruje [system_error —](../standard-library/system-error-class.md) mający z kodem błędu `operation_not_permitted`.

Jeśli wątek wywołujący już właścicielem `mutex`, metoda wygeneruje `system_error` mający z kodem błędu `resource_deadlock_would_occur`.

## <a name="try_lock_for"></a>  try_lock_for

Próbuje uzyskać prawo własności do skojarzonego `mutex` bez blokowania.

```cpp
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

`Rel_time` A [chrono::duration](../standard-library/duration-class.md) obiekt, który określa maksymalną ilość czasu, który próbuje uzyskać prawo własności do metody `mutex`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli metoda pomyślnie uzyskuje prawo własności `mutex`; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Jeśli zapisana `mutex` wskaźnika jest `null`, metoda wygeneruje [system_error —](../standard-library/system-error-class.md) mający z kodem błędu `operation_not_permitted`.

Jeśli wątek wywołujący już właścicielem `mutex`, metoda wygeneruje `system_error` mający z kodem błędu `resource_deadlock_would_occur`.

## <a name="try_lock_until"></a>  try_lock_until

Próbuje uzyskać prawo własności do skojarzonego `mutex` bez blokowania.

```cpp
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

`Abs_time` Punktu w czasie, który określa próg, po upływie którego metoda nie jest już próbuje uzyskać prawo własności do `mutex`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli metoda pomyślnie uzyskuje prawo własności `mutex`; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Jeśli zapisana `mutex` wskaźnika jest `null`, metoda wygeneruje [system_error —](../standard-library/system-error-class.md) mający z kodem błędu `operation_not_permitted`.

Jeśli wątek wywołujący już właścicielem `mutex`, metoda wygeneruje `system_error` mający z kodem błędu `resource_deadlock_would_occur`.

## <a name="unique_lock"></a>  unique_lock — Konstruktor

Konstruuje `unique_lock` obiektu.

```cpp
unique_lock() noexcept;
unique_lock(unique_lock&& Other) noexcept;
explicit unique_lock(mutex_type& Mtx);

unique_lock(mutex_type& Mtx, adopt_lock_t Adopt);

unique_lock(mutex_type& Mtx, defer_lock_t Defer) noexcept;
unique_lock(mutex_type& Mtx, try_to_lock_t Try);

template <class Rep, class Period>
unique_lock(mutex_type& Mtx,
    const chrono::duration<Rep, Period>
Rel_time);

template <class Clock, class Duration>
unique_lock(mutex_type& Mtx,
    const chrono::time_point<Clock, Duration>
Abs_time);

unique_lock(mutex_type& Mtx,
    const xtime* Abs_time) noexcept;
```

### <a name="parameters"></a>Parametry

`Mtx` Obiekt typu obiektu mutex.

`Rel_time` A [chrono::duration](../standard-library/duration-class.md) obiekt, który określa maksymalną ilość czasu, który próbuje uzyskać prawo własności do metody `mutex`.

`Abs_time` Punktu w czasie, który określa próg, po upływie którego metoda nie jest już próbuje uzyskać prawo własności do `mutex`.

`Other` A `unique_lock` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstrukcji obiektu, który ma wartość wskaźnika skojarzonego obiektu mutex 0.

Drugi Konstruktor przenosi stan obiektu mutex skojarzone z `Other`. Po przeniesieniu `Other` nie jest już skojarzony z obiektu mutex.

Pozostałe magazynu konstruktorów & `Mtx` przechowywane `mutex` wskaźnika. Własność `mutex` jest określany przez drugi argument, jeśli istnieje.

|||
|-|-|
|`No argument`|Własność są uzyskiwane przez wywołanie metody `lock` metody w skojarzonym `mutex` obiektu.|
|`Adopt`|Przyjęto, że własności. `Mtx` musi być zablokowany podczas wywołania konstruktora.|
|`Defer`|Wątek wywołujący prawdopodobnie nie jest własnych `mutex` obiektu. `Mtx` nie musi być zablokowany podczas wywołania konstruktora.|
|`Try`|Własność jest określana przez wywołanie `try_lock` na skojarzonym `mutex` obiektu. Konstruktor zgłasza nothing.|
|`Rel_time`|Własność jest określana przez wywołanie metody `try_lock_for(Rel_time)`.|
|`Abs_time`|Własność jest określana przez wywołanie metody `try_lock_until(Abs_time)`.|

## <a name="dtorunique_lock_destructor"></a>  ~ unique_lock — destruktor

Zwalnia wszystkie zasoby, które są skojarzone z `unique_lock` obiektu.

```cpp
~unique_lock() noexcept;
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest właścicielem skojarzony `mutex`, własność wersjach destruktora przez wywołanie metody odblokować na `mutex` obiektu.

## <a name="unlock"></a>  odblokowywanie

Zwalnia własność skojarzonego `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący nie posiada skojarzony `mutex`, ta metoda zgłasza [system_error —](../standard-library/system-error-class.md) mający z kodem błędu `operation_not_permitted`.

W przeciwnym razie ta metoda wywołuje `unlock` na skojarzonym `mutex` i ustawia flagę własność wewnętrzny wątek `false`.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
