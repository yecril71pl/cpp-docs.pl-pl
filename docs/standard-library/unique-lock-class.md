---
title: unique_lock — Klasa
ms.date: 11/04/2016
f1_keywords:
- mutex/std::unique_lock
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
ms.openlocfilehash: 59201fbaba6f2e8ae0ed5f53925b287b4d33aab3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367255"
---
# <a name="unique_lock-class"></a>unique_lock — Klasa

Reprezentuje szablon, który można utworzyć w celu utworzenia obiektów, które `mutex`zarządzają blokowaniem i odblokowywaniem pliku .

## <a name="syntax"></a>Składnia

```cpp
template <class Mutex>
class unique_lock;
```

## <a name="remarks"></a>Uwagi

Argument `Mutex` szablonu musi nadać nazwę *typowi obiektu mutex*.

Wewnętrznie przechowuje `unique_lock` wskaźnik do skojarzonego `mutex` obiektu i **bool,** który wskazuje, `mutex`czy bieżący wątek jest właścicielem .

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|`mutex_type`|Synonim argumentu `Mutex`szablonu .|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[unique_lock](#unique_lock)|Konstruuje `unique_lock` obiekt.|
|[~unique_lock Destruktor](#dtorunique_lock_destructor)|Zwalnia wszystkie zasoby, które `unique_lock` są skojarzone z obiektem.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Blokuje wątek wywołujący, dopóki wątek nie uzyska własności skojarzonego `mutex`.|
|[Mutex](#mutex)|Pobiera zapisany wskaźnik do skojarzonego `mutex`.|
|[owns_lock](#owns_lock)|Określa, czy wątek wywołujący jest właścicielem skojarzonego `mutex`pliku .|
|[Wydania](#release)|Odłącza `unique_lock` obiekt od skojarzonego `mutex` obiektu.|
|[Wymiany](#swap)|Zamienia stan skojarzony `mutex` i własności z stanem określonego obiektu.|
|[try_lock](#try_lock)|Próbuje uzyskać własność skojarzonego `mutex` bez blokowania.|
|[try_lock_for](#try_lock_for)|Próbuje uzyskać własność skojarzonego `mutex` bez blokowania.|
|[try_lock_until](#try_lock_until)|Próbuje uzyskać własność skojarzonego `mutex` bez blokowania.|
|[Odblokować](#unlock)|Zwalnia własność skojarzonego `mutex`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[bool operatora](#op_bool)|Określa, czy wątek wywołujący `mutex`jest własnością skojarzonego pliku .|
|[operator=](#op_eq)|Kopiuje `mutex` przechowywany wskaźnik i skojarzony stan własności z określonego obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

*unique_lock*

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mutex>

**Przestrzeń nazw:** std

## <a name="lock"></a><a name="lock"></a>Blokady

Blokuje wątek wywołujący, dopóki wątek nie uzyska własności skojarzonego `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli przechowywany `mutex` wskaźnik ma wartość NULL, ta metoda zgłasza [system_error,](../standard-library/system-error-class.md) `operation_not_permitted`który ma kod błędu .

Jeśli wątek wywołujący `mutex`jest już właścicielem `system_error` skojarzonego, ta `resource_deadlock_would_occur`metoda zgłasza, że ma kod błędu .

W przeciwnym razie `lock` ta metoda `mutex` wywołuje skojarzone i ustawia flagę własności wątku wewnętrznego na **true**.

## <a name="mutex"></a><a name="mutex"></a>Mutex

Pobiera zapisany wskaźnik do skojarzonego `mutex`.

```cpp
mutex_type *mutex() const noexcept;
```

## <a name="operator-bool"></a><a name="op_bool"></a>bool operatora

Określa, czy wątek wywołujący jest własnością skojarzonego obiektu mutex.

```cpp
explicit operator bool() noexcept
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli wątek jest właścicielem mutex; w przeciwnym razie **false**.

## <a name="operator"></a><a name="op_eq"></a>operator=

Kopiuje `mutex` przechowywany wskaźnik i skojarzony stan własności z określonego obiektu.

```cpp
unique_lock& operator=(unique_lock&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Innych*\
Obiekt `unique_lock`.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest `mutex`właścicielem wcześniej `unlock` skojarzone, przed tej metody wywołuje `mutex`, przypisuje nowe wartości.

Po kopii ta metoda ustawia *Inne* do stanu domyślnego skonstruowane.

## <a name="owns_lock"></a><a name="owns_lock"></a>owns_lock

Określa, czy wątek wywołujący jest właścicielem skojarzonego `mutex`pliku .

```cpp
bool owns_lock() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli wątek jest właścicielem `mutex`; w przeciwnym razie **false**.

## <a name="release"></a><a name="release"></a>Wydania

Odłącza `unique_lock` obiekt od skojarzonego `mutex` obiektu.

```cpp
mutex_type *release() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Poprzednia wartość przechowywanego wskaźnika. `mutex`

### <a name="remarks"></a>Uwagi

Ta metoda ustawia wartość `mutex` zapisanego wskaźnika na `mutex` 0 i ustawia flagę własności wewnętrznej na **false**.

## <a name="swap"></a><a name="swap"></a>Wymiany

Zamienia stan skojarzony `mutex` i własności z stanem określonego obiektu.

```cpp
void swap(unique_lock& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Innych*\
Obiekt `unique_lock`.

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Próbuje uzyskać własność skojarzonego `mutex` bez blokowania.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli metoda pomyślnie uzyskuje `mutex`własność ; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli przechowywany `mutex` wskaźnik ma wartość NULL, metoda zgłasza [system_error,](../standard-library/system-error-class.md) który `operation_not_permitted`ma kod błędu .

Jeśli wątek wywołujący jest już właścicielem `mutex`, metoda `system_error` zgłasza, który ma kod błędu `resource_deadlock_would_occur`.

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Próbuje uzyskać własność skojarzonego `mutex` bez blokowania.

```cpp
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
A [chrono::duration](../standard-library/duration-class.md) object, który określa maksymalny czas, przez jaki metoda `mutex`próbuje uzyskać własność .

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli metoda pomyślnie uzyskuje `mutex`własność ; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli przechowywany `mutex` wskaźnik ma wartość NULL, metoda zgłasza [system_error,](../standard-library/system-error-class.md) który `operation_not_permitted`ma kod błędu .

Jeśli wątek wywołujący jest już właścicielem `mutex`, metoda `system_error` zgłasza, który ma kod błędu `resource_deadlock_would_occur`.

## <a name="try_lock_until"></a><a name="try_lock_until"></a>try_lock_until

Próbuje uzyskać własność skojarzonego `mutex` bez blokowania.

```cpp
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Punkt w czasie, który określa próg, po którym metoda nie `mutex`próbuje już uzyskać własność .

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli metoda pomyślnie uzyskuje `mutex`własność ; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli przechowywany `mutex` wskaźnik ma wartość NULL, metoda zgłasza [system_error,](../standard-library/system-error-class.md) który `operation_not_permitted`ma kod błędu .

Jeśli wątek wywołujący jest już właścicielem `mutex`, metoda `system_error` zgłasza, który ma kod błędu `resource_deadlock_would_occur`.

## <a name="unique_lock-constructor"></a><a name="unique_lock"></a>konstruktor unique_lock

Konstruuje `unique_lock` obiekt.

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

*Mtx*\
Obiekt typu mutex.

*Rel_time*\
A [chrono::duration](../standard-library/duration-class.md) object, który określa maksymalny czas, przez jaki metoda `mutex`próbuje uzyskać własność .

*Abs_time*\
Punkt w czasie, który określa próg, po którym metoda nie `mutex`próbuje już uzyskać własność .

*Innych*\
Obiekt `unique_lock`.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor tworzy obiekt, który ma skojarzoną wartość wskaźnika mutex 0.

Drugi konstruktor przenosi skojarzony stan mutex z *Inne*. Po przeprowadzce *Inne* nie jest już skojarzony z obiektu mutex.

Pozostałe konstruktory magazynu & *Mtx* `mutex` jako przechowywany wskaźnik. Własność `mutex` jest określana przez drugi argument, jeśli istnieje.

|||
|-|-|
|`No argument`|Własność uzyskuje się `lock` przez wywołanie `mutex` metody na skojarzonym obiekcie.|
|`Adopt`|Zakłada się własność. `Mtx`musi być zablokowany, gdy wywoływany jest konstruktor.|
|`Defer`|Zakłada się, że wątek wywołujący `mutex` nie jest właścicielem obiektu. `Mtx`nie może być zablokowany, gdy wywoływany jest konstruktor.|
|`Try`|Własność jest określana przez `try_lock` `mutex` wywołanie skojarzonego obiektu. Konstruktor nic nie rzuca.|
|`Rel_time`|Własność jest określana przez wywołanie `try_lock_for(Rel_time)`.|
|`Abs_time`|Własność jest określana przez wywołanie `try_lock_until(Abs_time)`.|

## <a name="unique_lock-destructor"></a><a name="dtorunique_lock_destructor"></a>~unique_lock Destruktor

Zwalnia wszystkie zasoby, które `unique_lock` są skojarzone z obiektem.

```cpp
~unique_lock() noexcept;
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący `mutex`jest właścicielem skojarzonego, destruktor `mutex` zwalnia własność, wywołując odblokowanie na obiekcie.

## <a name="unlock"></a><a name="unlock"></a>Odblokować

Zwalnia własność skojarzonego `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący nie `mutex`jest właścicielem skojarzonego, ta metoda zgłasza [system_error,](../standard-library/system-error-class.md) który ma kod błędu `operation_not_permitted`.

W przeciwnym razie `unlock` ta metoda `mutex` wywołuje skojarzone i ustawia flagę własności wątku wewnętrznego na **false**.

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
