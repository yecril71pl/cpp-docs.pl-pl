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
ms.openlocfilehash: 13996a8ec4ab56fc56a78606d1a2ce8d76994c0d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375853"
---
# <a name="thread-class"></a>thread — Klasa

Definiuje obiekt, który jest używany do obserwowania i zarządzania wątkiem wykonywania w obrębie aplikacji.

## <a name="syntax"></a>Składnia

```cpp
class thread;
```

## <a name="remarks"></a>Uwagi

Można użyć obiektu **wątku** do obserwowania wątku wykonywania i zarządzania nim w ramach aplikacji. Obiekt wątku, który jest tworzony przy użyciu konstruktora domyślnego nie jest skojarzony z żadnym wątkiem wykonywania. Obiekt wątku, który jest konstruowany przy użyciu wywoływanego obiektu tworzy nowy wątek wykonywania i wywołuje obiekt w tym wątku. Obiekty wątków można przenosić, ale nie kopiować. W związku z tym wątek wykonywania może być skojarzony tylko z jednym obiektem wątku.

Każdy wątek wykonywania ma unikatowy identyfikator typu `thread::id`. Funkcja `this_thread::get_id` zwraca identyfikator wywołującego wątku. Element członkowski funkcji `thread::get_id` zwraca identyfikator wątku, który jest zarządzany przez obiekt wątku. Dla obiektu wątku zbudowanego domyślnie, metoda `thread::get_id` zwraca obiekt o wartości, która jest taka sama dla wszystkich obiektów wątku zbudowanego domyślnie i różni się od wartości zwracanej przez `this_thread::get_id` dla każdego wątku wykonywania, która może być połączona w momencie wywołania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-classes"></a>Klasy publiczne

|Nazwa|Opis|
|----------|-----------------|
|[wątek::id Klasa](#id_class)|Jednoznacznie identyfikuje skojarzony wątek.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[wątek](#thread)|Konstruuje obiekt **wątku.**|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Odłączyć](#detach)|Odłącza skojarzony wątek od obiektu **wątku.**|
|[get_id](#get_id)|Zwraca unikatowy identyfikator skojarzonego wątku.|
|[hardware_concurrency](#hardware_concurrency)|Statyczny. Zwraca szacunkową liczbę kontekstów wątków sprzętu.|
|[Dołączyć](#join)|Blokuje, aż do zakończenia skojarzonego wątku.|
|[do skłączenia](#joinable)|Określa, czy skojarzony wątek podlega sprzęganiu.|
|[native_handle](#native_handle)|Zwraca typ zależny od implementacji, który reprezentuje dojście wątku.|
|[Wymiany](#swap)|Zamienia stan obiektu z określonym obiektem **wątku.**|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[gwint::operator=](#op_eq)|Kojarzy wątek z bieżącym **obiektem wątku.**|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> wątku

**Przestrzeń nazw:** std

## <a name="threaddetach"></a><a name="detach"></a>wątek::detach

Odłącza skojarzony wątek. System operacyjny staje się odpowiedzialny za zwalnianie zasobów wątku po zakończeniu.

```cpp
void detach();
```

### <a name="remarks"></a>Uwagi

Po wywołaniu, `detach`kolejne wywołania [get_id](#get_id) [zwracaj identyfikator](#id_class).

Jeśli wątek, który jest skojarzony z obiektem wywołującym, nie można dołączyć, funkcja `invalid_argument`zgłasza [system_error,](../standard-library/system-error-class.md) który ma kod błędu .

Jeśli wątek, który jest skojarzony z obiektem wywołującym jest nieprawidłowy, funkcja zgłasza, `system_error` że ma kod błędu . `no_such_process`

## <a name="threadget_id"></a><a name="get_id"></a>wątek::get_id

Zwraca unikatowy identyfikator skojarzonego wątku.

```cpp
id get_id() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

[Wątek::id](#id_class) obiekt, który jednoznacznie identyfikuje `thread::id()` skojarzony wątek lub jeśli żaden wątek nie jest skojarzony z obiektem.

## <a name="threadhardware_concurrency"></a><a name="hardware_concurrency"></a>wątek::hardware_concurrency

Metoda statyczna, która zwraca szacunkową liczbę kontekstów wątku sprzętowego.

```cpp
static unsigned int hardware_concurrency() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Oszacowanie liczby kontekstów wątku sprzętowego. Jeśli wartość nie może być obliczona lub nie jest dobrze zdefiniowana, ta metoda zwraca wartość 0.

## <a name="threadid-class"></a><a name="id_class"></a>wątek::id Klasa

Udostępnia unikatowy identyfikator dla każdego wątku wykonywania w procesie.

```cpp
class thread::id {
    id() noexcept;
};
```

### <a name="remarks"></a>Uwagi

Domyślny konstruktor tworzy obiekt, który `thread::id` nie porównuje się równa obiektowi dla istniejącego wątku.

Wszystkie obiekty konstruowane domyślnie `thread::id` porównują się równe.

## <a name="threadjoin"></a><a name="join"></a>wątek::sprzężenie

Blokuje do wątku wykonywania, który jest skojarzony z wywołującym obiektu kończy.

```cpp
void join();
```

### <a name="remarks"></a>Uwagi

Jeśli wywołanie zakończy się pomyślnie, kolejne wywołania [get_id](#get_id) dla obiektu wywołującego zwracają domyślny `thread::id` [wątek::id,](#id_class) który nie jest równy istniejącemu wątkowi; Jeśli wywołanie nie powiedzie się, wartość, która jest zwracana przez `get_id` pozostaje niezmieniona.

## <a name="threadjoinable"></a><a name="joinable"></a>wątek::do skułączenia

Określa, czy skojarzony wątek jest *łączony*.

```cpp
bool joinable() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli skojarzony wątek jest *do łączyny;* w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Obiekt wątku można `get_id() != id()` *s łączyć,* jeśli .

## <a name="threadnative_handle"></a><a name="native_handle"></a>wątek::native_handle

Zwraca typ zależny od implementacji, który reprezentuje dojście wątku. Dojście wątku może służyć w sposób specyficzny dla implementacji.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Wartość zwracana

`native_handle_type`jest zdefiniowany jako `HANDLE` Win32, `void *`który jest oddanych jako .

## <a name="threadoperator"></a><a name="op_eq"></a>gwint::operator=

Kojarzy wątek określonego obiektu z bieżącym obiektem.

```cpp
thread& operator=(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Innych*\
Obiekt **wątku.**

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Metoda wywołuje odłączyć, jeśli obiekt wywołujący jest przyłączany.

Po utworzeniu skojarzenia `Other` jest ustawiona na stan domyślny.

## <a name="threadswap"></a><a name="swap"></a>wątek::swap

Zamienia stan obiektu z stanem określonego **wątku.**

```cpp
void swap(thread& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Innych*\
Obiekt **wątku.**

## <a name="threadthread-constructor"></a><a name="thread"></a>wątek::konstruktor gwintu

Konstruuje obiekt **wątku.**

```cpp
thread() noexcept;
template <class Fn, class... Args>
explicit thread(Fn&& F, Args&&... A);

thread(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*F*\
Funkcja zdefiniowana przez aplikację, która ma być wykonywana przez wątek.

*A*\
Lista argumentów, które mają być przekazywane do *F*.

*Innych*\
Istniejący obiekt **wątku.**

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor tworzy obiekt, który nie jest skojarzony z wątku wykonywania. Wartość, która jest zwracana `get_id` przez wywołanie dla `thread::id()`skonstruowanego obiektu jest .

Drugi konstruktor tworzy obiekt, który jest skojarzony z nowym wątkiem wykonania `INVOKE` i wykonuje pseudo-funkcję, która jest zdefiniowana w [ \<>funkcjonalnym. ](../standard-library/functional.md) Jeśli nie ma wystarczającej ilości zasobów, aby uruchomić nowy wątek, funkcja `resource_unavailable_try_again`zgłasza [obiekt system_error,](../standard-library/system-error-class.md) który ma kod błędu . Jeśli wywołanie *F* kończy się z nieprzechodnionym wyjątkiem, [terminate](../standard-library/exception-functions.md#terminate) jest wywoływana.

Trzeci konstruktor tworzy obiekt, który jest skojarzony z wątkiem, który jest skojarzony z `Other`. `Other`jest następnie ustawiona na stan domyślny.

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<>gwintów](../standard-library/thread.md)
