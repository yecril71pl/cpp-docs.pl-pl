---
title: accelerator_view — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view:accelerator_view
- AMPRT/Concurrency::accelerator_view:create_marker
- AMPRT/Concurrency::accelerator_view:flush
- AMPRT/Concurrency::accelerator_view:get_accelerator
- AMPRT/Concurrency::accelerator_view:get_is_auto_selection
- AMPRT/Concurrency::accelerator_view:get_is_debug
- AMPRT/Concurrency::accelerator_view:get_queuing_mode
- AMPRT/Concurrency::accelerator_view:get_version
- AMPRT/Concurrency::accelerator_view:wait
- AMPRT/Concurrency::accelerator_view:accelerator
- AMPRT/Concurrency::accelerator_view:is_auto_selection
- AMPRT/Concurrency::accelerator_view:is_debug
- AMPRT/Concurrency::accelerator_view:queuing_mode
- AMPRT/Concurrency::accelerator_view:version
dev_langs:
- C++
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b556a86506e3aae73f7ac4e1ac961b539364d6db
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053567"
---
# <a name="acceleratorview-class"></a>accelerator_view — Klasa

Reprezentuje abstrakcję urządzenia wirtualnego na akceleratorze danych równoległych C++ AMP.

### <a name="syntax"></a>Składnia

```
class accelerator_view;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Obiekt accelerator_view, Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `accelerator_view` klasy.|
|[~ accelerator_view — destruktor](#dtor)|Niszczy `accelerator_view` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[create_marker](#create_marker)|Zwraca stan w przyszłości do śledzenia wykonania wszystkich poleceń dotychczas przekazanych do tego `accelerator_view` obiektu.|
|[flush](#flush)|Przesyła wszystkie oczekujące polecenia w kolejce do `accelerator_view` obiektu do akceleratora do wykonania.|
|[get_accelerator](#get_accelerator)|Zwraca `accelerator` dla obiektu `accelerator_view` obiektu.|
|[get_is_auto_selection](#get_is_auto_selection)|Zwraca wartość logiczną wskazującą, czy środowisko wykonawcze automatycznie wybiera odpowiedni akcelerator podczas `accelerator_view` obiekt jest przekazywany do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[get_is_debug](#get_is_debug)|Zwraca wartość logiczną wskazującą, czy `accelerator_view` obiekt ma włączoną warstwę debugowanie dla obszernego raportowania błędów.|
|[get_queuing_mode](#get_queuing_mode)|Zwraca tryb kolejkowania dla `accelerator_view` obiektu.|
|[get_version](#get_version)|Zwraca wersję `accelerator_view`.|
|[Czekaj](#wait)|Czeka, aż wszystkie polecenia przesłane do `accelerator_view` obiektu, aby zakończyć.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator!=](#operator_neq)|Porównuje ten `accelerator_view` obiekt z innym i zwraca **false** jeśli są one takie same; w przeciwnym razie zwraca **true**.|
|[operator=](#operator_eq)|Kopiuje zawartość określonego `accelerator_view` obiektu do wskazanego.|
|[operator==](#operator_eq_eq)|Porównuje ten `accelerator_view` obiekt z innym i zwraca **true** jeśli są one takie same; w przeciwnym razie zwraca **false**.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[accelerator](#accelerator)|Pobiera `accelerator` dla obiektu `accelerator_view` obiektu.|
|[is_auto_selection](#is_auto_selection)|Pobiera wartość logiczną, wskazującą, czy środowisko wykonawcze automatycznie wybiera odpowiedni akcelerator podczas `accelerator_view` obiekt jest przekazywany do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[is_debug](#is_debug)|Pobiera wartość logiczną, wskazującą, czy `accelerator_view` obiekt ma włączoną warstwę debugowanie dla obszernego raportowania błędów.|
|[queuing_mode](#queuing_mode)|Pobiera tryb kolejkowania dla `accelerator_view` obiektu.|
|[version](#version)|Pobiera wersję akceleratora.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`accelerator_view`

### <a name="remarks"></a>Uwagi

`accelerator_view` Obiekt reprezentuje logiczny, izolowany widok akceleratora. Pojedynczy fizyczne urządzenie do obliczeń może mieć wiele logicznych, izolowanych `accelerator_view` obiektów. Każdy akcelerator ma wartość domyślną `accelerator_view` obiektu. Dodatkowe `accelerator_view` obiekty mogą być tworzone.

Urządzenia fizyczne mogą być współużytkowane przez wiele wątków klienta. Wątki klienta mogą wspólnie używać takie same `accelerator_view` obiektu akceleratorze lub każdy klient może komunikować się z urządzeniem obliczeniowym przez niezależny `accelerator_view` obiektu w celu izolacji od innych wątków klienta.

`accelerator_view` Obiekt może mieć jeden z dwóch [queuing_mode — wyliczenie](concurrency-namespace-enums-amp.md#queuing_mode) stanów. Jeśli tryb kolejkowania to `immediate`, polecenia takie jak `copy` i `parallel_for_each` są wysyłane do odpowiadającego urządzenia akceleratora, jak tylko powrócą do wywołującego. Jeśli tryb kolejkowania to `deferred`, takie polecenia są kolejkowane w kolejce poleceń, który odpowiada `accelerator_view` obiektu. Polecenia nie są faktycznie przesyłane do urządzenia, dopóki nie `flush()` jest wywoływana.

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt.h

**Namespace:** współbieżności

## <a name="accelerator"></a> Akcelerator

Pobiera obiekt akceleratora dla obiektu accelerator_view.

### <a name="syntax"></a>Składnia

```
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="ctor"></a> accelerator_view

Inicjuje nowe wystąpienie klasy accelerator_view przez skopiowanie istniejącego `accelerator_view` obiektu.

### <a name="syntax"></a>Składnia

```
accelerator_view( const accelerator_view & _Other );
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`accelerator_view` Obiektu do skopiowania.

## <a name="accelerator_view__create_marker"></a> create_marker

Zwraca stan w przyszłości do śledzenia wykonania wszystkich poleceń dotychczas przekazanych do tego `accelerator_view` obiektu.

### <a name="syntax"></a>Składnia

```
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Wartość zwracana

Stan w przyszłości do śledzenia wykonania wszystkich poleceń dotychczas przekazanych do tego `accelerator_view` obiektu.

## <a name="flush"></a> Flush

Przesyła się, że wszystkie oczekujące polecenia w kolejce do obiektu accelerator_view do akceleratora do wykonania.

### <a name="syntax"></a>Składnia

```
void flush();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `void`.

## <a name="accelerator_view__get_accelerator"></a> get_accelerator —

Zwraca obiekt akceleratora dla obiektu accelerator_view.
### <a name="syntax"></a>Składnia

```
accelerator get_accelerator() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt akceleratora dla obiektu accelerator_view.

## <a name="accelerator_view__get_is_auto_selection"></a> get_is_auto_selection

Zwraca wartość logiczną wskazującą, czy środowisko wykonawcze automatycznie wybiera odpowiedni akcelerator, gdy accelerator_view jest przekazywany do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Składnia

```
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli środowisko wykonawcze automatycznie wybiera odpowiedni akcelerator; w przeciwnym razie **false**.

## <a name="accelerator_view__get_is_debug"></a> get_is_debug —

Zwraca wartość logiczną wskazującą, czy obiekt accelerator_view ma włączoną warstwę debugowanie dla obszernego raportowania błędów.

### <a name="syntax"></a>Składnia

```
bool get_is_debug() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna, która wskazuje, czy `accelerator_view` obiekt ma włączoną warstwę debugowanie dla obszernego raportowania błędów.

## <a name="accelerator_view__get_queuing_mode"></a> get_queuing_mode

Zwraca tryb kolejkowania dla obiektu accelerator_view.

### <a name="syntax"></a>Składnia

```
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Wartość zwracana

Tryb kolejkowania dla `accelerator_view` obiektu.

## <a name="accelerator_view__get_version"></a> get_version —

Zwraca wersję accelerator_view.

### <a name="syntax"></a>Składnia

```
unsigned int get_version() const;
```

### <a name="return-value"></a>Wartość zwracana

Wersja `accelerator_view`.

## <a name="accelerator_view__is_auto_selection"></a> is_auto_selection

Pobiera wartość logiczną, wskazującą, czy środowisko wykonawcze automatycznie wybiera odpowiedni akcelerator, gdy accelerator_view jest przekazywany do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Składnia

```
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="accelerator_view__is_debug"></a> is_debug —

Pobiera wartość logiczną, wskazującą, czy obiekt accelerator_view ma włączoną warstwę debugowanie dla obszernego raportowania błędów.

### <a name="syntax"></a>Składnia

```
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="accelerator_view__operator_neq"></a> operator! =

Porównuje ten obiekt accelerator_view, z innym i zwraca **false** jeśli są one takie same; w przeciwnym razie zwraca **true**.

### <a name="syntax"></a>Składnia

```
bool operator!= (    const accelerator_view & _Other ) const;
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`accelerator_view` Obiekt do porównania z tym kontem.

### <a name="return-value"></a>Wartość zwracana

**FALSE** Jeśli dwa obiekty są takie same; w przeciwnym razie **true**.

## <a name="accelerator_view__operator_eq"></a> operator =

Kopiuje zawartość określonego obiektu accelerator_view obiektu do wskazanego.

### <a name="syntax"></a>Składnia

```
accelerator_view & operator= (    const accelerator_view & _Other );
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`accelerator_view` Obiektu do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zmodyfikowanego `accelerator_view` obiektu.

## <a name="accelerator_view__operator_eq_eq"></a> operator ==

Porównuje ten obiekt accelerator_view, z innym i zwraca **true** jeśli są one takie same; w przeciwnym razie zwraca **false**.

### <a name="syntax"></a>Składnia

```
bool operator= = (    const accelerator_view & _Other ) const;
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`accelerator_view` Obiekt do porównania z tym kontem.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli dwa obiekty są takie same; w przeciwnym razie **false**.

## <a name="accelerator_view__queuing_mode"></a> queuing_mode

Pobiera tryb kolejkowania dla obiektu accelerator_view.

### <a name="syntax"></a>Składnia

```
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="accelerator_view__version"></a> Wersja

Pobiera wersję accelerator_view.

### <a name="syntax"></a>Składnia

```
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="accelerator_view__wait"></a> Czekaj

Czeka, aż wszystkie polecenia przesłane do obiektu accelerator_view zakończyć.

### <a name="syntax"></a>Składnia

```
void wait();
```

#### <a name="return-value"></a>Wartość zwracana

Zwraca `void`.

#### <a name="remarks"></a>Uwagi

Jeśli [queuing_mode —](concurrency-namespace-enums-amp.md#queuing_mode) jest `immediate`, ta metoda zwraca natychmiast bez blokowania.

##  <a name="dtor"></a> ~ accelerator_view

Niszczy obiekt accelerator_view.

#### <a name="syntax"></a>Składnia

```
~accelerator_view();
```

### <a name="return-value"></a>Wartość zwracana

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
