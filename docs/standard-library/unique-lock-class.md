---
title: unique_lock, klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 780ccdb7f16ed79ef8205c07e1390e778bc33ef5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711389"
---
# <a name="uniquelock-class"></a>unique_lock — Klasa

Reprezentuje szablon, który można utworzyć wystąpienia do tworzenia obiektów, które zarządzają blokowanie i odblokowywanie `mutex`.

## <a name="syntax"></a>Składnia

```cpp
template <class Mutex>
class unique_lock;
```

## <a name="remarks"></a>Uwagi

Argument szablonu `Mutex` należy nazywać *typu obiektu mutex*.

Wewnętrznie `unique_lock` przechowuje wskaźnik do skojarzonego `mutex` obiektu i **bool** oznacza to, czy bieżący wątek jest właścicielem `mutex`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`mutex_type`|Synonim dla argumentu szablonu `Mutex`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[unique_lock](#unique_lock)|Konstruuje `unique_lock` obiektu.|
|[~unique_lock Destructor](#dtorunique_lock_destructor)|Zwalnia wszelkie zasoby, które są skojarzone z `unique_lock` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Blokuje wątek wywołujący, aż wątek uzyskuje własność skojarzonego `mutex`.|
|[mutex](#mutex)|Pobiera przechowywany wskaźnik do powiązanych `mutex`.|
|[owns_lock](#owns_lock)|Określa, czy wątek wywołujący posiada skojarzonej `mutex`.|
|[Wydania](#release)|Powoduje usunięcie `unique_lock` obiektu z powiązanego `mutex` obiektu.|
|[swap](#swap)|Zamienia skojarzonego `mutex` i stan własności określonego obiektu.|
|[try_lock —](#try_lock)|Próby uzyskania własności skojarzonego `mutex` bez blokowania.|
|[try_lock_for](#try_lock_for)|Próby uzyskania własności skojarzonego `mutex` bez blokowania.|
|[try_lock_until](#try_lock_until)|Próby uzyskania własności skojarzonego `mutex` bez blokowania.|
|[unlock](#unlock)|Zwalnia własność skojarzonego `mutex`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[bool — operator](#op_bool)|Określa, czy wątek wywołujący ma własności skojarzonego `mutex`.|
|[operator=](#op_eq)|Kopiuje przechowywaną `mutex` wskaźnik i stan własności skojarzone z określonego obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

*unique_lock*<br/>

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mutex >

**Namespace:** standardowe

## <a name="lock"></a>  Blokady

Blokuje wątek wywołujący, aż wątek uzyskuje własność skojarzonego `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli przechowywane `mutex` wskaźnik jest pusty, ta metoda wyrzuca [system_error](../standard-library/system-error-class.md) zawierający kod błędu `operation_not_permitted`.

Jeśli wątek wywołujący już właścicielem skojarzonego `mutex`, ta metoda wyrzuca `system_error` zawierający kod błędu `resource_deadlock_would_occur`.

W przeciwnym razie ta metoda wywołuje `lock` dla powiązanego `mutex` i ustawia flagę własność wewnętrznego wątku **true**.

## <a name="mutex"></a>  mutex

Pobiera przechowywany wskaźnik do powiązanych `mutex`.

```cpp
mutex_type *mutex() const noexcept;
```

## <a name="op_bool"></a>  bool — operator

Określa, czy wątek wywołujący ma własności skojarzony element mutex.

```cpp
explicit operator bool() noexcept
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wątek jest właścicielem obiektu mutex; w przeciwnym razie **false**.

## <a name="op_eq"></a>  operator =

Kopiuje przechowywaną `mutex` wskaźnik i stan własności skojarzone z określonego obiektu.

```cpp
unique_lock& operator=(unique_lock&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Inne*<br/>
Element `unique_lock` obiektu.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest właścicielem wcześniej skojarzony `mutex`, zanim ta metoda wywołuje `unlock` na `mutex`, przypisuje nowe wartości.

Po kopii tej metody ustawia *innych* stan zbudowanego domyślnie.

## <a name="owns_lock"></a>  owns_lock

Określa, czy wątek wywołujący posiada skojarzonej `mutex`.

```cpp
bool owns_lock() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wątek jest właścicielem `mutex`; w przeciwnym razie **false**.

## <a name="release"></a>  Wydania

Powoduje usunięcie `unique_lock` obiektu z powiązanego `mutex` obiektu.

```cpp
mutex_type *release() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Poprzednią wartość przechowywaną `mutex` wskaźnika.

### <a name="remarks"></a>Uwagi

Ta metoda ustawia wartość przechowywaną `mutex` wskaźnik do 0 i zestawy wewnętrzny `mutex` Flaga własność **false**.

## <a name="swap"></a>  swap

Zamienia skojarzonego `mutex` i stan własności określonego obiektu.

```cpp
void swap(unique_lock& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Inne*<br/>
Element `unique_lock` obiektu.

## <a name="try_lock"></a>  try_lock —

Próby uzyskania własności skojarzonego `mutex` bez blokowania.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli metoda pomyślnie uzyskuje własność `mutex`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli przechowywane `mutex` wskaźnik ma wartość NULL, metoda zgłasza [system_error](../standard-library/system-error-class.md) zawierający kod błędu `operation_not_permitted`.

Jeśli wątek wywołujący jest już właścicielem `mutex`, metoda zgłasza `system_error` zawierający kod błędu `resource_deadlock_would_occur`.

## <a name="try_lock_for"></a>  try_lock_for —

Próby uzyskania własności skojarzonego `mutex` bez blokowania.

```cpp
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*<br/>
A [chrono::duration](../standard-library/duration-class.md) obiektu, który określa maksymalną ilość czasu, która metoda podejmuje próbę uzyskania własności `mutex`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli metoda pomyślnie uzyskuje własność `mutex`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli przechowywane `mutex` wskaźnik ma wartość NULL, metoda zgłasza [system_error](../standard-library/system-error-class.md) zawierający kod błędu `operation_not_permitted`.

Jeśli wątek wywołujący jest już właścicielem `mutex`, metoda zgłasza `system_error` zawierający kod błędu `resource_deadlock_would_occur`.

## <a name="try_lock_until"></a>  try_lock_until

Próby uzyskania własności skojarzonego `mutex` bez blokowania.

```cpp
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*<br/>
Punkt w czasie, który określa próg, po upływie którego metoda nie jest już próby uzyskania własności `mutex`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli metoda pomyślnie uzyskuje własność `mutex`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli przechowywane `mutex` wskaźnik ma wartość NULL, metoda zgłasza [system_error](../standard-library/system-error-class.md) zawierający kod błędu `operation_not_permitted`.

Jeśli wątek wywołujący jest już właścicielem `mutex`, metoda zgłasza `system_error` zawierający kod błędu `resource_deadlock_would_occur`.

## <a name="unique_lock"></a>  unique_lock konstruktora

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

*Mtx*<br/>
Obiekt typu obiektu mutex.

*Rel_time*<br/>
A [chrono::duration](../standard-library/duration-class.md) obiektu, który określa maksymalną ilość czasu, która metoda podejmuje próbę uzyskania własności `mutex`.

*Abs_time*<br/>
Punkt w czasie, który określa próg, po upływie którego metoda nie jest już próby uzyskania własności `mutex`.

*Inne*<br/>
Element `unique_lock` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje obiekt, który ma wartość wskaźnika skojarzonego obiektu mutex 0.

Drugi Konstruktor przenosi stan skojarzonego obiektu mutex z *innych*. Po przeniesieniu *innych* nie jest już skojarzony z elementu mutex.

Pozostałe magazynu konstruktorów & *Mtx* jako przechowywane `mutex` wskaźnika. Własność `mutex` jest określana przez drugi argument, jeśli taki istnieje.

|||
|-|-|
|`No argument`|Własność można uzyskać przez wywołanie `lock` metody skojarzonego `mutex` obiektu.|
|`Adopt`|Przyjęto, że własność. `Mtx` musi być zablokowane, gdy Konstruktor jest wywoływana.|
|`Defer`|Wątek wywołujący prawdopodobnie nie jest własnych `mutex` obiektu. `Mtx` nie musi być zablokowane, gdy Konstruktor jest wywoływana.|
|`Try`|Własność jest określana przez wywołanie metody `try_lock` dla powiązanego `mutex` obiektu. Konstruktor wyrzuca nothing.|
|`Rel_time`|Własność jest określana przez wywołanie metody `try_lock_for(Rel_time)`.|
|`Abs_time`|Własność jest określana przez wywołanie metody `try_lock_until(Abs_time)`.|

## <a name="dtorunique_lock_destructor"></a>  ~ unique_lock — destruktor

Zwalnia wszelkie zasoby, które są skojarzone z `unique_lock` obiektu.

```cpp
~unique_lock() noexcept;
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący posiada skojarzonej `mutex`, własność wersji destruktora, wywołując Odblokuj na `mutex` obiektu.

## <a name="unlock"></a>  Odblokowywanie

Zwalnia własność skojarzonego `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący nie posiada skojarzonej `mutex`, ta metoda wyrzuca [system_error](../standard-library/system-error-class.md) zawierający kod błędu `operation_not_permitted`.

W przeciwnym razie ta metoda wywołuje `unlock` dla powiązanego `mutex` i ustawia flagę własność wewnętrznego wątku **false**.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
