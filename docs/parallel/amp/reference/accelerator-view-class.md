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
ms.openlocfilehash: f3be8cc3ab9a0f36027cc38c88f026570d1fdb55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370889"
---
# <a name="accelerator_view-class"></a>accelerator_view — Klasa

Reprezentuje abstrakcję urządzenia wirtualnego w akceleratorze równoległym danych C++ AMP.

## <a name="syntax"></a>Składnia

```cpp
class accelerator_view;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktor accelerator_view](#ctor)|Inicjuje nowe wystąpienie klasy `accelerator_view`.|
|[~accelerator_view Destruktor](#dtor)|Niszczy `accelerator_view` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[create_marker](#create_marker)|Zwraca przyszłość, aby śledzić zakończenie wszystkich poleceń `accelerator_view` przesłanych do tej pory do tego obiektu.|
|[opróżnianie](#flush)|Przesyła wszystkie oczekujące polecenia w `accelerator_view` kolejce do obiektu do akceleratora do wykonania.|
|[get_accelerator](#get_accelerator)|Zwraca `accelerator` obiekt dla `accelerator_view` obiektu.|
|[get_is_auto_selection](#get_is_auto_selection)|Zwraca wartość logiczną, która wskazuje, czy środowisko wykonawcze automatycznie `accelerator_view` wybierze odpowiedni akcelerator, gdy obiekt zostanie przekazany do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[get_is_debug](#get_is_debug)|Zwraca wartość logiczną, która `accelerator_view` wskazuje, czy obiekt ma włączoną warstwę DEBUG dla obszernego raportowania błędów.|
|[get_queuing_mode](#get_queuing_mode)|Zwraca tryb kolejkowania `accelerator_view` obiektu.|
|[get_version](#get_version)|Zwraca wersję pliku `accelerator_view`.|
|[Czekać](#wait)|Czeka na zakończenie wszystkich poleceń `accelerator_view` przesłanych do obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator!=](#operator_neq)|Porównuje ten `accelerator_view` obiekt z innym i zwraca **false,** jeśli są one takie same; w przeciwnym razie zwraca **wartość true**.|
|[operator=](#operator_eq)|Kopiuje zawartość określonego `accelerator_view` obiektu do tego obiektu.|
|[operator==](#operator_eq_eq)|Porównuje ten `accelerator_view` obiekt z innym i zwraca **wartość true,** jeśli są one takie same; w przeciwnym razie zwraca **false**.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[Akcelerator](#accelerator)|Pobiera `accelerator` obiekt dla `accelerator_view` obiektu.|
|[is_auto_selection](#is_auto_selection)|Pobiera wartość logiczną, która wskazuje, czy środowisko uruchomieniowe automatycznie `accelerator_view` wybierze odpowiedni akcelerator, gdy obiekt zostanie przekazany do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[is_debug](#is_debug)|Pobiera wartość logiczną, która `accelerator_view` wskazuje, czy obiekt ma włączoną warstwę DEBUG dla raportowania błędów rozległe.|
|[queuing_mode](#queuing_mode)|Pobiera tryb kolejkowania `accelerator_view` dla obiektu.|
|[Wersja](#version)|Pobiera wersję akceleratora.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`accelerator_view`

### <a name="remarks"></a>Uwagi

Obiekt `accelerator_view` reprezentuje logiczny, izolowany widok akceleratora. Pojedyncze fizyczne urządzenie obliczeniowe może `accelerator_view` mieć wiele logicznych, izolowanych obiektów. Każdy akcelerator ma obiekt domyślny. `accelerator_view` Można `accelerator_view` tworzyć dodatkowe obiekty.

Urządzenia fizyczne mogą być współużytkowane przez wiele wątków klienta. Wątki klienta można wspólnie `accelerator_view` używać tego samego obiektu akceleratora lub każdy `accelerator_view` klient może komunikować się z urządzeniem obliczeniowym za pośrednictwem niezależnego obiektu do izolacji od innych wątków klienta.

Obiekt `accelerator_view` może mieć jeden z dwóch [stanów wyliczenia queuing_mode.](concurrency-namespace-enums-amp.md#queuing_mode) Jeśli tryb kolejkowania `immediate`jest , `copy` `parallel_for_each` polecenia jak i są wysyłane do odpowiedniego urządzenia akceleratora, jak tylko wrócą do rozmówcy. Jeśli jest `deferred`tryb kolejkowania , takie polecenia są umieszczane w kolejce poleceń odpowiadających obiektowi. `accelerator_view` Polecenia nie są faktycznie wysyłane `flush()` do urządzenia, dopóki nie zostanie wywołana.

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt.h

**Obszar nazw:** Współbieżności

## <a name="accelerator"></a><a name="accelerator"></a>Akcelerator

Pobiera obiekt akceleratora dla accelerator_view obiektu.

### <a name="syntax"></a>Składnia

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="accelerator_view"></a><a name="ctor"></a>Accelerator_view

Inicjuje nowe wystąpienie klasy accelerator_view, kopiując `accelerator_view` istniejący obiekt.

### <a name="syntax"></a>Składnia

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Obiekt `accelerator_view` do skopiowania.

## <a name="create_marker"></a><a name="create_marker"></a>create_marker

Zwraca przyszłość, aby śledzić zakończenie wszystkich poleceń `accelerator_view` przesłanych do tej pory do tego obiektu.

### <a name="syntax"></a>Składnia

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Wartość zwracana

Przyszłość śledzenia zakończenia wszystkich poleceń przesłanych do `accelerator_view` tej pory do tego obiektu.

## <a name="flush"></a>opróżnianie

Przesyła wszystkie oczekujące polecenia w kolejce do obiektu accelerator_view do akceleratora do wykonania.

### <a name="syntax"></a>Składnia

```cpp
void flush();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `void`.

## <a name="get_accelerator"></a><a name="get_accelerator"></a>get_accelerator

Zwraca obiekt akceleratora dla accelerator_view obiektu.

### <a name="syntax"></a>Składnia

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt akceleratora dla accelerator_view obiektu.

## <a name="get_is_auto_selection"></a><a name="get_is_auto_selection"></a>get_is_auto_selection

Zwraca wartość logiczną, która wskazuje, czy środowisko wykonawcze automatycznie wybierze odpowiedni akcelerator, gdy accelerator_view zostanie przekazana do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Składnia

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli środowisko wykonawcze automatycznie wybierze odpowiedni akcelerator; w przeciwnym razie **false**.

## <a name="get_is_debug"></a><a name="get_is_debug"></a>get_is_debug

Zwraca wartość logiczną, która wskazuje, czy obiekt accelerator_view ma włączoną warstwę DEBUG dla obszernego raportowania błędów.

### <a name="syntax"></a>Składnia

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna, która wskazuje, czy `accelerator_view` obiekt ma włączoną warstwę DEBUG dla obszernego raportowania błędów.

## <a name="get_queuing_mode"></a><a name="get_queuing_mode"></a>get_queuing_mode

Zwraca tryb kolejkowania dla obiektu accelerator_view.

### <a name="syntax"></a>Składnia

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Wartość zwracana

Tryb kolejkowania `accelerator_view` obiektu.

## <a name="get_version"></a><a name="get_version"></a>get_version

Zwraca wersję accelerator_view.

### <a name="syntax"></a>Składnia

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Wartość zwracana

Wersja `accelerator_view`.

## <a name="is_auto_selection"></a><a name="is_auto_selection"></a>is_auto_selection

Pobiera wartość logiczną, która wskazuje, czy środowisko uruchomieniowe automatycznie wybierze odpowiedni akcelerator, gdy accelerator_view jest przekazywana do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Składnia

```cpp
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="is_debug"></a><a name="is_debug"></a>is_debug

Pobiera wartość logiczną, która wskazuje, czy obiekt accelerator_view ma włączoną warstwę DEBUG dla obszernego raportowania błędów.

### <a name="syntax"></a>Składnia

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator"></a><a name="operator_neq"></a>operator!=

Porównuje ten obiekt accelerator_view z innym i zwraca **false,** jeśli są one takie same; w przeciwnym razie zwraca **wartość true**.

### <a name="syntax"></a>Składnia

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Obiekt `accelerator_view` do porównania z tym.

### <a name="return-value"></a>Wartość zwracana

**false,** jeśli dwa obiekty są takie same; w przeciwnym **razie, prawda**.

## <a name="operator"></a><a name="operator_eq"></a>operator=

Kopiuje zawartość określonego obiektu accelerator_view do tego obiektu.

### <a name="syntax"></a>Składnia

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Obiekt `accelerator_view` do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zmodyfikowanego `accelerator_view` obiektu.

## <a name="operator"></a><a name="operator_eq_eq"></a>operator==

Porównuje ten obiekt accelerator_view z innym i zwraca **wartość true,** jeśli są one takie same; w przeciwnym razie zwraca **false**.

### <a name="syntax"></a>Składnia

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Obiekt `accelerator_view` do porównania z tym.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli dwa obiekty są takie same; w przeciwnym razie **false**.

## <a name="queuing_mode"></a><a name="queuing_mode"></a>queuing_mode

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

## <a name="wait"></a>czas oczekiwania

Czeka na zakończenie wszystkich poleceń przesłanych do obiektu accelerator_view.

### <a name="syntax"></a>Składnia

```cpp
void wait();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `void`.

### <a name="remarks"></a>Uwagi

Jeśli [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) jest `immediate`, ta metoda zwraca natychmiast bez blokowania.

## <a name="accelerator_view"></a><a name="dtor"></a>~accelerator_view

Niszczy obiekt accelerator_view.

### <a name="syntax"></a>Składnia

```cpp
~accelerator_view();
```

## <a name="see-also"></a>Zobacz też

[Obszar nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
