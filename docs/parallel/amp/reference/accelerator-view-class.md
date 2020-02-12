---
title: accelerator_view — Klasa
ms.date: 03/27/2019
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view::accelerator_view
- AMPRT/Concurrency::accelerator_view::create_marker
- AMPRT/Concurrency::accelerator_view::flush
- AMPRT/Concurrency::accelerator_view::get_accelerator
- AMPRT/Concurrency::accelerator_view::get_is_auto_selection
- AMPRT/Concurrency::accelerator_view::get_is_debug
- AMPRT/Concurrency::accelerator_view::get_queuing_mode
- AMPRT/Concurrency::accelerator_view::get_version
- AMPRT/Concurrency::accelerator_view::wait
- AMPRT/Concurrency::accelerator_view::accelerator
- AMPRT/Concurrency::accelerator_view::is_auto_selection
- AMPRT/Concurrency::accelerator_view::is_debug
- AMPRT/Concurrency::accelerator_view::queuing_mode
- AMPRT/Concurrency::accelerator_view::version
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
ms.openlocfilehash: 8990566fb3a700d61de324f725dea3ec00006d04
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127179"
---
# <a name="accelerator_view-class"></a>accelerator_view — Klasa

Reprezentuje abstrakcję urządzenia wirtualnego w akceleratorze C++ danych amp-równoległym.

## <a name="syntax"></a>Składnia

```cpp
class accelerator_view;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor accelerator_view](#ctor)|Inicjuje nowe wystąpienie klasy `accelerator_view`.|
|[~ accelerator_view destruktor](#dtor)|Niszczy obiekt `accelerator_view`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[create_marker](#create_marker)|Zwraca przyszłość, aby śledzić ukończenie wszystkich poleceń przesłanych do tego obiektu `accelerator_view`.|
|[płukan](#flush)|Przesyła wszystkie oczekujące polecenia w kolejce do obiektu `accelerator_view` do akceleratora do wykonania.|
|[get_accelerator](#get_accelerator)|Zwraca obiekt `accelerator` dla `accelerator_view` obiektu.|
|[get_is_auto_selection](#get_is_auto_selection)|Zwraca wartość logiczną wskazującą, czy środowisko wykonawcze automatycznie wybiera odpowiedni akcelerator, gdy obiekt `accelerator_view` jest przenoszona do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[get_is_debug](#get_is_debug)|Zwraca wartość logiczną wskazującą, czy obiekt `accelerator_view` ma włączoną warstwę debugowania dla obszernego raportowania błędów.|
|[get_queuing_mode](#get_queuing_mode)|Zwraca tryb kolejkowania dla obiektu `accelerator_view`.|
|[get_version](#get_version)|Zwraca wersję `accelerator_view`.|
|[trwa](#wait)|Czeka na zakończenie wszystkich poleceń przesłanych do obiektu `accelerator_view`.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator!=](#operator_neq)|Porównuje ten obiekt `accelerator_view` z innym i zwraca **wartość false** , jeśli są takie same; w przeciwnym razie zwraca **wartość true**.|
|[operator =](#operator_eq)|Kopiuje zawartość określonego obiektu `accelerator_view` do tego.|
|[operator = =](#operator_eq_eq)|Porównuje ten obiekt `accelerator_view` z innym i zwraca **wartość true** , jeśli są one takie same; w przeciwnym razie zwraca **wartość false**.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[skrót](#accelerator)|Pobiera obiekt `accelerator` dla `accelerator_view` obiektu.|
|[is_auto_selection](#is_auto_selection)|Pobiera wartość logiczną wskazującą, czy środowisko wykonawcze automatycznie wybiera odpowiedni akcelerator, gdy obiekt `accelerator_view` jest przenoszona do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[is_debug](#is_debug)|Pobiera wartość logiczną wskazującą, czy obiekt `accelerator_view` ma włączoną warstwę debugowania dla obszernego raportowania błędów.|
|[queuing_mode](#queuing_mode)|Pobiera tryb kolejkowania dla obiektu `accelerator_view`.|
|[version](#version)|Pobiera wersję akceleratora.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`accelerator_view`

### <a name="remarks"></a>Uwagi

Obiekt `accelerator_view` reprezentuje logiczny, izolowany widok akceleratora. Pojedyncze fizyczne urządzenie obliczeniowe może mieć wiele logicznych, izolowanych obiektów `accelerator_view`. Każdy akcelerator ma domyślny obiekt `accelerator_view`. Można utworzyć dodatkowe obiekty `accelerator_view`.

Urządzenia fizyczne mogą być współużytkowane przez wiele wątków klienta. Wątki klienta mogą wspólnie korzystać z tego samego obiektu `accelerator_view` akceleratora lub każdy klient może komunikować się z urządzeniem obliczeniowym za pośrednictwem niezależnego obiektu `accelerator_view` na potrzeby izolacji z innych wątków klienta.

Obiekt `accelerator_view` może mieć jeden z dwóch queuing_mode Stanów [wyliczenia](concurrency-namespace-enums-amp.md#queuing_mode) . Jeśli tryb kolejkowania jest `immediate`, polecenia takie jak `copy` i `parallel_for_each` są wysyłane do odpowiedniego urządzenia akceleratora zaraz po powrocie do obiektu wywołującego. Jeśli tryb kolejkowania jest `deferred`, takie polecenia są umieszczane w kolejce poleceń, która odpowiada obiektowi `accelerator_view`. Polecenia nie są faktycznie wysyłane do urządzenia do momentu wywołania `flush()`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt. h

**Przestrzeń nazw:** Współbieżności

## <a name="accelerator"></a>skrót

Pobiera obiekt akceleratora dla obiektu accelerator_view.

### <a name="syntax"></a>Składnia

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="ctor"></a>accelerator_view

Inicjuje nowe wystąpienie klasy accelerator_view przez skopiowanie istniejącego obiektu `accelerator_view`.

### <a name="syntax"></a>Składnia

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Obiekt `accelerator_view` do skopiowania.

## <a name="create_marker"></a>create_marker

Zwraca przyszłość, aby śledzić ukończenie wszystkich poleceń przesłanych do tego obiektu `accelerator_view`.

### <a name="syntax"></a>Składnia

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Wartość zwrócona

Przyszłość do śledzenia ukończenia wszystkich poleceń przesłanych do tego obiektu `accelerator_view`.

## <a name="flush"></a>opróżnianie

Przesyła wszystkie oczekujące polecenia w kolejce do obiektu accelerator_view do akceleratora do wykonania.

### <a name="syntax"></a>Składnia

```cpp
void flush();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość `void`.

## <a name="get_accelerator"></a>get_accelerator

Zwraca obiekt akceleratora dla obiektu accelerator_view.

### <a name="syntax"></a>Składnia

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>Wartość zwrócona

Obiekt akceleratora dla obiektu accelerator_view.

## <a name="get_is_auto_selection"></a>get_is_auto_selection

Zwraca wartość logiczną wskazującą, czy środowisko wykonawcze automatycznie wybiera odpowiedni akcelerator, gdy accelerator_view jest przenoszona do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Składnia

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli środowisko uruchomieniowe automatycznie wybierze odpowiedni akcelerator; w przeciwnym razie **false**.

## <a name="get_is_debug"></a>get_is_debug

Zwraca wartość logiczną wskazującą, czy obiekt accelerator_view ma włączoną warstwę debugowania dla obszernego raportowania błędów.

### <a name="syntax"></a>Składnia

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wartość logiczna wskazująca, czy obiekt `accelerator_view` ma włączoną warstwę debugowania dla obszernego raportowania błędów.

## <a name="get_queuing_mode"></a>get_queuing_mode

Zwraca tryb kolejkowania dla obiektu accelerator_view.

### <a name="syntax"></a>Składnia

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Wartość zwrócona

Tryb kolejkowania dla obiektu `accelerator_view`.

## <a name="get_version"></a>get_version

Zwraca wersję accelerator_view.

### <a name="syntax"></a>Składnia

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wersja `accelerator_view`.

## <a name="is_auto_selection"></a>is_auto_selection

Pobiera wartość logiczną wskazującą, czy środowisko wykonawcze automatycznie wybiera odpowiedni akcelerator, gdy accelerator_view jest przenoszona do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Składnia

```cpp
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="is_debug"></a>is_debug

Pobiera wartość logiczną wskazującą, czy obiekt accelerator_view ma włączoną warstwę debugowania dla obszernego raportowania błędów.

### <a name="syntax"></a>Składnia

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator_neq"></a>operator! =

Porównuje ten obiekt accelerator_view z innym i zwraca **wartość false** , jeśli są takie same; w przeciwnym razie zwraca **wartość true**.

### <a name="syntax"></a>Składnia

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Obiekt `accelerator_view`, który ma zostać porównany z tym elementem.

### <a name="return-value"></a>Wartość zwrócona

**Fałsz** , jeśli dwa obiekty są takie same; w przeciwnym razie **wartość true**.

## <a name="operator_eq"></a>operator =

Kopiuje zawartość określonego obiektu accelerator_view do tego.

### <a name="syntax"></a>Składnia

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Obiekt `accelerator_view`, z którego ma być kopiowany.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do zmodyfikowanego obiektu `accelerator_view`.

## <a name="operator_eq_eq"></a>operator = =

Porównuje ten obiekt accelerator_view z innym i zwraca **wartość true** , jeśli są one takie same; w przeciwnym razie zwraca **wartość false**.

### <a name="syntax"></a>Składnia

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Obiekt `accelerator_view`, który ma zostać porównany z tym elementem.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli dwa obiekty są takie same; w przeciwnym razie **false**.

## <a name="queuing_mode"></a>queuing_mode

Pobiera tryb kolejkowania dla obiektu accelerator_view.

### <a name="syntax"></a>Składnia

```cpp
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>version

Pobiera wersję accelerator_view.

### <a name="syntax"></a>Składnia

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="wait"></a>trwa

Czeka na zakończenie wszystkich poleceń przesłanych do obiektu accelerator_view.

### <a name="syntax"></a>Składnia

```cpp
void wait();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość `void`.

### <a name="remarks"></a>Uwagi

Jeśli [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) jest `immediate`, Metoda ta zwraca natychmiast bez blokowania.

## <a name="dtor"></a>~ accelerator_view

Niszczy obiekt accelerator_view.

### <a name="syntax"></a>Składnia

```cpp
~accelerator_view();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
