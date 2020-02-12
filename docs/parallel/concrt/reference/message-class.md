---
title: message — Klasa
ms.date: 11/04/2016
f1_keywords:
- message
- AGENTS/concurrency::message
- AGENTS/concurrency::message::message
- AGENTS/concurrency::message::add_ref
- AGENTS/concurrency::message::msg_id
- AGENTS/concurrency::message::remove_ref
- AGENTS/concurrency::message::payload
helpviewer_keywords:
- message class
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
ms.openlocfilehash: 700d052b6f22c970387a3ab45d299538a5b74e1b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139542"
---
# <a name="message-class"></a>message — Klasa

Podstawowa koperta komunikatów zawierająca ładunek danych przesyłanych między blokami obsługi komunikatów.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ danych ładunku w komunikacie.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`type`|Alias typu dla `T`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[komunikat](#ctor)|Przeciążone. Konstruuje obiekt `message`.|
|[~ Message — destruktor](#dtor)|Niszczy obiekt `message`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[add_ref](#add_ref)|Dodaje do liczby odwołań dla obiektu `message`. Używany dla bloków komunikatów, które wymagają zliczania odwołań, aby określić okresy istnienia wiadomości.|
|[msg_id](#msg_id)|Zwraca identyfikator obiektu `message`.|
|[remove_ref](#remove_ref)|Odejmuje od liczby odwołań dla obiektu `message`. Używany dla bloków komunikatów, które wymagają zliczania odwołań, aby określić okresy istnienia wiadomości.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[ładunku](#payload)|Ładunek obiektu `message`.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`message`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="add_ref"></a>add_ref

Dodaje do liczby odwołań dla obiektu `message`. Używany dla bloków komunikatów, które wymagają zliczania odwołań, aby określić okresy istnienia wiadomości.

```cpp
long add_ref();
```

### <a name="return-value"></a>Wartość zwrócona

Nowa wartość liczby odwołań.

## <a name="ctor"></a>Komunikat

Konstruuje obiekt `message`.

```cpp
message(
    T const& _P);

message(
    T const& _P,
    runtime_object_identity _Id);

message(
    message const& _Msg);

message(
    _In_ message const* _Msg);
```

### <a name="parameters"></a>Parametry

*_P*<br/>
Ładunek tej wiadomości.

*_Id*<br/>
Unikatowy identyfikator tej wiadomości.

*_Msg*<br/>
Odwołanie lub wskaźnik do obiektu `message`.

### <a name="remarks"></a>Uwagi

Konstruktor, który Pobiera wskaźnik do obiektu `message` jako argument zgłasza wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) , jeśli `_Msg` parametr jest `NULL`.

## <a name="dtor"></a>komunikat ~

Niszczy obiekt `message`.

```cpp
virtual ~message();
```

## <a name="msg_id"></a>msg_id

Zwraca identyfikator obiektu `message`.

```cpp
runtime_object_identity msg_id() const;
```

### <a name="return-value"></a>Wartość zwrócona

`runtime_object_identity` obiektu `message`.

## <a name="payload"></a>ładunku

Ładunek obiektu `message`.

```cpp
T const payload;
```

## <a name="remove_ref"></a>remove_ref

Odejmuje od liczby odwołań dla obiektu `message`. Używany dla bloków komunikatów, które wymagają zliczania odwołań, aby określić okresy istnienia wiadomości.

```cpp
long remove_ref();
```

### <a name="return-value"></a>Wartość zwrócona

Nowa wartość liczby odwołań.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
