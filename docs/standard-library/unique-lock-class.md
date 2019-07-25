---
title: unique_lock — Klasa
ms.date: 11/04/2016
f1_keywords:
- mutex/std::unique_lock
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
ms.openlocfilehash: 655d7b08c452bed94277aaed2cc8368aaeb462c9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454929"
---
# <a name="uniquelock-class"></a>unique_lock — Klasa

Reprezentuje szablon, który może być skonkretyzowany do tworzenia obiektów, które zarządzają blokowaniem i odblokowywaniem `mutex`.

## <a name="syntax"></a>Składnia

```cpp
template <class Mutex>
class unique_lock;
```

## <a name="remarks"></a>Uwagi

Argument `Mutex` szablonu musi mieć nazwę *typu muteksu*.

Wewnętrznie program `unique_lock` zapisuje wskaźnik do skojarzonego `mutex` obiektu i wartość **logiczną** , która `mutex`wskazuje, czy bieżący wątek jest właścicielem.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`mutex_type`|Synonim argumentu `Mutex`szablonu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[unique_lock](#unique_lock)|Konstruuje `unique_lock` obiekt.|
|[~unique_lock Destructor](#dtorunique_lock_destructor)|Zwalnia wszystkie zasoby skojarzone z `unique_lock` obiektem.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Blokuje wątek wywołujący do momentu, aż wątek uzyska własność skojarzonego `mutex`elementu.|
|[mutex](#mutex)|Pobiera przechowywany wskaźnik do skojarzonego `mutex`.|
|[owns_lock](#owns_lock)|Określa, czy wywołujący wątek jest właścicielem `mutex`skojarzonego obiektu.|
|[Usuwanie](#release)|Usuwa obiekt z skojarzonego `mutex`obiektu. `unique_lock`|
|[swap](#swap)|Zamienia stan skojarzonych `mutex` i własności na określony obiekt.|
|[try_lock](#try_lock)|Próbuje uzyskać własność skojarzoną `mutex` bez blokowania.|
|[try_lock_for](#try_lock_for)|Próbuje uzyskać własność skojarzoną `mutex` bez blokowania.|
|[try_lock_until](#try_lock_until)|Próbuje uzyskać własność skojarzoną `mutex` bez blokowania.|
|[unlock](#unlock)|Zwalnia własność skojarzonych `mutex`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[wartość logiczna operatora](#op_bool)|Określa, czy wywołujący wątek ma własność skojarzonego `mutex`elementu.|
|[operator=](#op_eq)|Kopiuje zapisany `mutex` wskaźnik i stan powiązanej własności z określonego obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

*unique_lock*

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> mutex

**Przestrzeń nazw:** std

## <a name="lock"></a>skręt

Blokuje wątek wywołujący do momentu, aż wątek uzyska własność skojarzonego `mutex`elementu.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli przechowywany `mutex` wskaźnik ma wartość null, ta metoda zgłasza [system_error](../standard-library/system-error-class.md) o kodzie `operation_not_permitted`błędu.

Jeśli wątek wywołujący jest już właścicielem skojarzonej `mutex`metody, ta metoda `system_error` zgłasza, że `resource_deadlock_would_occur`ma kod błędu.

W przeciwnym razie ta metoda `lock` wywołuje dla skojarzonych `mutex` i ustawia flagę wewnętrznego własności wątku na **wartość true**.

## <a name="mutex"></a>mutex

Pobiera przechowywany wskaźnik do skojarzonego `mutex`.

```cpp
mutex_type *mutex() const noexcept;
```

## <a name="op_bool"></a>wartość logiczna operatora

Określa, czy wywołujący wątek ma własność skojarzonego obiektu mutex.

```cpp
explicit operator bool() noexcept
```

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli wątek jest właścicielem obiektu mutex; w przeciwnym razie **false**.

## <a name="op_eq"></a>operator =

Kopiuje zapisany `mutex` wskaźnik i stan powiązanej własności z określonego obiektu.

```cpp
unique_lock& operator=(unique_lock&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Różnych*\
Element `unique_lock` obiektu.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest właścicielem wcześniej skojarzonej `mutex`, przed wywołaniem `unlock` tej metody w `mutex`, przypisze nowe wartości.

Po skopiowaniu ta metoda jest ustawiana jako *inna* do stanu utworzonego domyślnie.

## <a name="owns_lock"></a>owns_lock

Określa, czy wywołujący wątek jest właścicielem `mutex`skojarzonego obiektu.

```cpp
bool owns_lock() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli wątek jest właścicielem `mutex`; w przeciwnym razie, **Fałsz**.

## <a name="release"></a>Usuwanie

Usuwa obiekt z skojarzonego `mutex`obiektu. `unique_lock`

```cpp
mutex_type *release() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Poprzednia wartość przechowywanego `mutex` wskaźnika.

### <a name="remarks"></a>Uwagi

Ta metoda ustawia wartość przechowywanego `mutex` wskaźnika na 0 i ustawia flagę wewnętrznej `mutex` własności na **false**.

## <a name="swap"></a>wymiany

Zamienia stan skojarzonych `mutex` i własności na określony obiekt.

```cpp
void swap(unique_lock& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Różnych*\
Element `unique_lock` obiektu.

## <a name="try_lock"></a>try_lock

Próbuje uzyskać własność skojarzoną `mutex` bez blokowania.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli metoda pomyślnie uzyska własność `mutex`; w przeciwnym razie, **Fałsz**.

### <a name="remarks"></a>Uwagi

Jeśli przechowywany `mutex` wskaźnik ma wartość null, metoda zgłasza [system_error](../standard-library/system-error-class.md) , który ma kod `operation_not_permitted`błędu.

Jeśli wątek wywołujący jest już właścicielem `mutex`, Metoda `system_error` zgłasza, że `resource_deadlock_would_occur`ma kod błędu.

## <a name="try_lock_for"></a>try_lock_for

Próbuje uzyskać własność skojarzoną `mutex` bez blokowania.

```cpp
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Obiekt [chrono::d wersja](../standard-library/duration-class.md) , który określa maksymalną ilość czasu, jaką Metoda próbuje uzyskać własność `mutex`.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli metoda pomyślnie uzyska własność `mutex`; w przeciwnym razie, **Fałsz**.

### <a name="remarks"></a>Uwagi

Jeśli przechowywany `mutex` wskaźnik ma wartość null, metoda zgłasza [system_error](../standard-library/system-error-class.md) , który ma kod `operation_not_permitted`błędu.

Jeśli wątek wywołujący jest już właścicielem `mutex`, Metoda `system_error` zgłasza, że `resource_deadlock_would_occur`ma kod błędu.

## <a name="try_lock_until"></a>try_lock_until

Próbuje uzyskać własność skojarzoną `mutex` bez blokowania.

```cpp
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Punkt w czasie, który określa próg, po którym metoda nie próbuje uzyskać własności `mutex`.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli metoda pomyślnie uzyska własność `mutex`; w przeciwnym razie, **Fałsz**.

### <a name="remarks"></a>Uwagi

Jeśli przechowywany `mutex` wskaźnik ma wartość null, metoda zgłasza [system_error](../standard-library/system-error-class.md) , który ma kod `operation_not_permitted`błędu.

Jeśli wątek wywołujący jest już właścicielem `mutex`, Metoda `system_error` zgłasza, że `resource_deadlock_would_occur`ma kod błędu.

## <a name="unique_lock"></a>Konstruktor unique_lock

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

*MTX*\
Obiekt typu mutex.

*Rel_time*\
Obiekt [chrono::d wersja](../standard-library/duration-class.md) , który określa maksymalną ilość czasu, jaką Metoda próbuje uzyskać własność `mutex`.

*Abs_time*\
Punkt w czasie, który określa próg, po którym metoda nie próbuje uzyskać własności `mutex`.

*Różnych*\
Element `unique_lock` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje obiekt, który ma skojarzoną wartość wskaźnika mutex równą 0.

Drugi Konstruktor przenosi skojarzony stan obiektu mutex z *innego*. Po przeniesieniu *inne* nie są już skojarzone z mutex.

Pozostałe konstruktory przechowują & *MTX* jako składowany `mutex` wskaźnik. `mutex` Własność jest określana przez drugi argument, jeśli istnieje.

|||
|-|-|
|`No argument`|Własność jest uzyskiwana przez wywołanie `lock` metody dla skojarzonego `mutex` obiektu.|
|`Adopt`|Przyjęto własność. `Mtx`musi być zablokowany, gdy Konstruktor jest wywoływany.|
|`Defer`|Założono, że wątek wywołujący nie jest właocicielem `mutex` obiektu. `Mtx`nie może być zablokowany, gdy Konstruktor jest wywoływany.|
|`Try`|Własność jest określana przez `try_lock` wywołanie skojarzonego `mutex` obiektu. Konstruktor zgłasza Nothing.|
|`Rel_time`|Własność jest określana przez `try_lock_for(Rel_time)`wywołanie.|
|`Abs_time`|Własność jest określana przez `try_lock_until(Abs_time)`wywołanie.|

## <a name="dtorunique_lock_destructor"></a>~ unique_lock destruktor

Zwalnia wszystkie zasoby skojarzone z `unique_lock` obiektem.

```cpp
~unique_lock() noexcept;
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest właścicielem skojarzonego `mutex`, destruktor zwalnia własność przez wywołanie metody Unlock `mutex` dla obiektu.

## <a name="unlock"></a>odblokowania

Zwalnia własność skojarzonych `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący nie jest elementem skojarzonym `mutex`, Metoda ta zgłasza [system_error](../standard-library/system-error-class.md) , który ma kod `operation_not_permitted`błędu.

W przeciwnym razie ta metoda `unlock` wywołuje dla skojarzonych `mutex` i ustawia flagę wewnętrznego własności wątku na **wartość false**.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
