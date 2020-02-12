---
title: cancellation_token_source — Klasa
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancel
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::create_linked_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::get_token
helpviewer_keywords:
- cancellation_token_source class
ms.assetid: 3548b1a0-12b0-4334-95db-4bf57141c066
ms.openlocfilehash: 131c4155ad902221d14f90f750f89c31479e2067
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142231"
---
# <a name="cancellation_token_source-class"></a>cancellation_token_source — Klasa

Klasa `cancellation_token_source` reprezentuje możliwość anulowania niektórych operacji do anulowania.

## <a name="syntax"></a>Składnia

```cpp
class cancellation_token_source;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[cancellation_token_source](#ctor)|Przeciążone. Tworzy nowy `cancellation_token_source`. Źródło może służyć do flagi anulowania niektórych operacji do anulowania.|
|[~ cancellation_token_source destruktor](#dtor)||

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Anuluj](#cancel)|Anuluje token. Wszelkie `task_group`, `structured_task_group`lub `task` korzystające z tokenu zostanie anulowane dla tego wywołania i zgłosić wyjątek w następnym punkcie przerwania.|
|[create_linked_source](#create_linked_source)|Przeciążone. Tworzy `cancellation_token_source`, która została anulowana po anulowaniu podanego tokenu.|
|[get_token](#get_token)|Zwraca token anulowania skojarzony z tym źródłem. Zwrócony token może być sondowany w celu anulowania lub podania wywołania zwrotnego, jeśli i gdy następuje anulowanie.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator =](#operator_eq)||
|[operator = =](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`cancellation_token_source`

## <a name="requirements"></a>Wymagania

**Nagłówek:** pplcancellation_token. h

**Przestrzeń nazw:** współbieżność

## <a name="dtor"></a>~ cancellation_token_source

```cpp
~cancellation_token_source();
```

## <a name="cancel"></a>Anuluj

Anuluje token. Wszelkie `task_group`, `structured_task_group`lub `task` korzystające z tokenu zostanie anulowane dla tego wywołania i zgłosić wyjątek w następnym punkcie przerwania.

```cpp
void cancel() const;
```

## <a name="ctor"></a>cancellation_token_source

Tworzy nowy `cancellation_token_source`. Źródło może służyć do flagi anulowania niektórych operacji do anulowania.

```cpp
cancellation_token_source();

cancellation_token_source(const cancellation_token_source& _Src);

cancellation_token_source(cancellation_token_source&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Obiekt do skopiowania lub przeniesienia.

## <a name="create_linked_source"></a>create_linked_source

Tworzy `cancellation_token_source`, która została anulowana po anulowaniu podanego tokenu.

```cpp
static cancellation_token_source create_linked_source(
    cancellation_token& _Src);

template<typename _Iter>
static cancellation_token_source create_linked_source(_Iter _Begin, _Iter _End);
```

### <a name="parameters"></a>Parametry

*_Iter*<br/>
Typ iteratora.

*_Src*<br/>
Token, którego anulowanie spowoduje anulowanie zwróconego źródła tokenu. Zwróć uwagę, że zwrócone Źródło tokenu może być również anulowane niezależnie od źródła zawartego w tym parametrze.

*_Begin*<br/>
Iterator C++ biblioteki standardowej odpowiadający początkowi zakresu tokenów do nasłuchiwania na potrzeby anulowania.

*_End*<br/>
C++ Wzorzec standardowej biblioteki odpowiadający końcowi zakresu tokenów do nasłuchiwania na potrzeby anulowania.

### <a name="return-value"></a>Wartość zwrócona

`cancellation_token_source`, która została anulowana, gdy token dostarczony przez parametr `_Src` zostanie anulowany.

## <a name="get_token"></a>get_token

Zwraca token anulowania skojarzony z tym źródłem. Zwrócony token może być sondowany w celu anulowania lub podania wywołania zwrotnego, jeśli i gdy następuje anulowanie.

```cpp
cancellation_token get_token() const;
```

### <a name="return-value"></a>Wartość zwrócona

Token anulowania skojarzony z tym źródłem.

## <a name="operator_neq"></a>operator! =

```cpp
bool operator!= (const cancellation_token_source& _Src) const;
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Parametru.

### <a name="return-value"></a>Wartość zwrócona

## <a name="operator_eq"></a>operator =

```cpp
cancellation_token_source& operator= (const cancellation_token_source& _Src);

cancellation_token_source& operator= (cancellation_token_source&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Parametru.

### <a name="return-value"></a>Wartość zwrócona

## <a name="operator_eq_eq"></a>operator = =

```cpp
bool operator== (const cancellation_token_source& _Src) const;
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Parametru.

### <a name="return-value"></a>Wartość zwrócona

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
