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
ms.openlocfilehash: 19f7ae1fc95f531f509273f0eb9998c73fe7d47b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215585"
---
# <a name="thread-class"></a>thread — Klasa

Definiuje obiekt, który jest używany do obserwowania i zarządzania wątkiem wykonywania w obrębie aplikacji.

## <a name="syntax"></a>Składnia

```cpp
class thread;
```

## <a name="remarks"></a>Uwagi

Można użyć `thread` obiektu do obserwowania wątku wykonywania w aplikacji i zarządzania nim. Obiekt wątku, który jest tworzony przy użyciu konstruktora domyślnego nie jest skojarzony z żadnym wątkiem wykonywania. Obiekt wątku, który jest konstruowany przy użyciu wywoływanego obiektu tworzy nowy wątek wykonywania i wywołuje obiekt w tym wątku. Obiekty wątków można przenosić, ale nie kopiować. W związku z tym wątek wykonywania może być skojarzony tylko z jednym obiektem wątku.

Każdy wątek wykonywania ma unikatowy identyfikator typu `thread::id`. Funkcja `this_thread::get_id` zwraca identyfikator wywołującego wątku. Element członkowski funkcji `thread::get_id` zwraca identyfikator wątku, który jest zarządzany przez obiekt wątku. Dla obiektu wątku zbudowanego domyślnie, metoda `thread::get_id` zwraca obiekt o wartości, która jest taka sama dla wszystkich obiektów wątku zbudowanego domyślnie i różni się od wartości zwracanej przez `this_thread::get_id` dla każdego wątku wykonywania, która może być połączona w momencie wywołania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-classes"></a>Klasy publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Thread:: ID — Klasa](#id_class)|Jednoznacznie identyfikuje skojarzony wątek.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[wątek](#thread)|Konstruuje `thread` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ekran](#detach)|Odłącza skojarzony wątek od `thread` obiektu.|
|[get_id](#get_id)|Zwraca unikatowy identyfikator skojarzonego wątku.|
|[hardware_concurrency](#hardware_concurrency)|Statyczny. Zwraca szacunkową liczbę kontekstów wątków sprzętu.|
|[Złącza](#join)|Blokuje, aż do zakończenia skojarzonego wątku.|
|[sprzęganiu](#joinable)|Określa, czy skojarzony wątek podlega sprzęganiu.|
|[native_handle](#native_handle)|Zwraca typ zależny od implementacji, który reprezentuje dojście wątku.|
|[wymiany](#swap)|Zamienia stan obiektu na określony `thread` obiekt.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Thread:: operator =](#op_eq)|Kojarzy wątek z bieżącym `thread` obiektem.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<thread>

**Przestrzeń nazw:** std

## <a name="threaddetach"></a><a name="detach"></a>Wątek::d etach

Odłącza skojarzony wątek. System operacyjny jest odpowiedzialny za zwolnienie zasobów wątku po zakończeniu.

```cpp
void detach();
```

### <a name="remarks"></a>Uwagi

Po wywołaniu `detach` , kolejne wywołania do [get_id](#get_id) [Identyfikator](#id_class)powrotu.

Jeśli wątek, który jest skojarzony z obiektem wywołującym nie jest przyłączany, funkcja zgłasza [system_error](../standard-library/system-error-class.md) , który ma kod błędu `invalid_argument` .

Jeśli wątek skojarzony z obiektem wywołującym jest nieprawidłowy, funkcja zgłasza, `system_error` że ma kod błędu `no_such_process` .

## <a name="threadget_id"></a><a name="get_id"></a>Wątek:: get_id

Zwraca unikatowy identyfikator skojarzonego wątku.

```cpp
id get_id() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

[Wątek:: ID](#id_class) , który jednoznacznie identyfikuje skojarzony wątek, lub `thread::id()` Jeśli żaden wątek nie jest skojarzony z obiektem.

## <a name="threadhardware_concurrency"></a><a name="hardware_concurrency"></a>Wątek:: hardware_concurrency

Metoda statyczna zwracająca szacunkową liczbę kontekstów wątków sprzętowych.

```cpp
static unsigned int hardware_concurrency() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Oszacowanie liczby kontekstów wątków sprzętowych. Jeśli wartość nie może być obliczona lub nie jest prawidłowo zdefiniowana, ta metoda zwraca 0.

## <a name="threadid-class"></a><a name="id_class"></a>Thread:: ID — Klasa

Zapewnia unikatowy identyfikator dla każdego wątku wykonywania w procesie.

```cpp
class thread::id {
    id() noexcept;
};
```

### <a name="remarks"></a>Uwagi

Konstruktor domyślny tworzy obiekt, który nie jest porównywany z `thread::id` obiektem w żadnym istniejącym wątku.

Wszystkie obiekty skonstruowane domyślnie są `thread::id` równe.

## <a name="threadjoin"></a><a name="join"></a>Wątek:: join

Bloki do momentu, aż wątek wykonywania skojarzony z wywoływanym obiektem zostanie zakończony.

```cpp
void join();
```

### <a name="remarks"></a>Uwagi

Jeśli wywołanie powiedzie się, kolejne wywołania [get_id](#get_id) dla obiektu wywołującego zwracają domyślny [wątek:: ID](#id_class) , który nie jest porównywany `thread::id` z żadnym istniejącym wątkiem. Jeśli wywołanie nie powiedzie się, wartość zwracana przez `get_id` jest niezmieniona.

## <a name="threadjoinable"></a><a name="joinable"></a>Wątek:: join

Określa, czy skojarzony wątek jest *przyłączony*.

```cpp
bool joinable() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli skojarzony wątek jest *przyłączany*; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Obiekt wątku jest *przyłączany* , jeśli `get_id() != id()` .

## <a name="threadnative_handle"></a><a name="native_handle"></a>Wątek:: native_handle

Zwraca typ zależny od implementacji, który reprezentuje dojście wątku. Uchwyt wątku może być używany w sposób specyficzny dla implementacji.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Wartość zwracana

`native_handle_type`jest definiowana jako system Win32 `HANDLE` , który jest rzutowany jako `void *` .

## <a name="threadoperator"></a><a name="op_eq"></a>Thread:: operator =

Kojarzy wątek określonego obiektu z bieżącym obiektem.

```cpp
thread& operator=(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Różnych*\
Obiekt `thread`.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Wywołania metody odłączają się, gdy wywołujący obiekt jest przyłączany.

Po utworzeniu skojarzenia `Other` jest ustawiany domyślny stan skonstruowany.

## <a name="threadswap"></a><a name="swap"></a>Wątek:: swap

Zamienia stan obiektu na określony `thread` obiekt.

```cpp
void swap(thread& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Różnych*\
Obiekt `thread`.

## <a name="threadthread-constructor"></a><a name="thread"></a>Thread:: Thread — Konstruktor

Konstruuje `thread` obiekt.

```cpp
thread() noexcept;
template <class Fn, class... Args>
explicit thread(Fn&& F, Args&&... A);

thread(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*N*\
Funkcja zdefiniowana przez aplikację do wykonania przez wątek.

*Z*\
Lista argumentów do przesłania do *F*.

*Różnych*\
Istniejący `thread` obiekt.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje obiekt, który nie jest skojarzony z wątkiem wykonania. Wartość zwracana przez wywołanie `get_id` dla konstruowanego obiektu to `thread::id()` .

Drugi Konstruktor konstruuje obiekt, który jest skojarzony z nowym wątkiem wykonywania i wykonuje pseudo funkcja `INVOKE` , która jest zdefiniowana w [\<functional>](../standard-library/functional.md) . Jeśli za mało zasobów jest dostępnych do uruchomienia nowego wątku, funkcja zgłasza obiekt [system_error](../standard-library/system-error-class.md) , który ma kod błędu `resource_unavailable_try_again` . Jeśli wywołanie *F* kończy się nieprzechwyconym wyjątkem, zostanie wywołane [zakończenie](../standard-library/exception-functions.md#terminate) .

Trzeci Konstruktor konstruuje obiekt, który jest skojarzony z wątkiem, który jest skojarzony z `Other` . `Other`jest następnie ustawiany na stan skonstruowany domyślnie.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<thread>](../standard-library/thread.md)
