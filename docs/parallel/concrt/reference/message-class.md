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
ms.openlocfilehash: 83cfdb5807581f7092709691a1839052abdd657c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263081"
---
# <a name="message-class"></a>message — Klasa

Koperty wiadomości podstawowe zawierającego ładunek danych przekazywany pomiędzy blokami obsługi komunikatów.

## <a name="syntax"></a>Składnia

```
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych ładunku w komunikacie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`type`|Alias typu `T`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[komunikat](#ctor)|Przeciążone. Konstruuje `message` obiektu.|
|[~ message — destruktor](#dtor)|Niszczy `message` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[add_ref](#add_ref)|Dodaje do licznika odwołań do `message` obiektu. Używane dla bloków komunikatów, wymagających zliczania odniesień, by określić okres istnienia komunikatu.|
|[msg_id](#msg_id)|Zwraca identyfikator `message` obiektu.|
|[remove_ref](#remove_ref)|Odejmuje z licznikiem odwołań do `message` obiektu. Używane dla bloków komunikatów, wymagających zliczania odniesień, by określić okres istnienia komunikatu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[payload](#payload)|Ładunek `message` obiektu.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`message`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="add_ref"></a> add_ref —

Dodaje do licznika odwołań do `message` obiektu. Używane dla bloków komunikatów, wymagających zliczania odniesień, by określić okres istnienia komunikatu.

```
long add_ref();
```

### <a name="return-value"></a>Wartość zwracana

Nowa wartość licznika odwołań.

##  <a name="ctor"></a> Komunikat

Konstruuje `message` obiektu.

```
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
Obciążenie tego komunikatu.

*_Id*<br/>
Unikatowy identyfikator tego komunikatu.

*_Msg*<br/>
Odwołanie lub wskaźnik do `message` obiektu.

### <a name="remarks"></a>Uwagi

Konstruktor, który pobiera wskaźnik do `message` obiekt jako argument zgłasza [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek Jeśli parametr `_Msg` jest `NULL`.

##  <a name="dtor"></a> ~ wiadomości

Niszczy `message` obiektu.

```
virtual ~message();
```

##  <a name="msg_id"></a> msg_id

Zwraca identyfikator `message` obiektu.

```
runtime_object_identity msg_id() const;
```

### <a name="return-value"></a>Wartość zwracana

`runtime_object_identity` z `message` obiektu.

##  <a name="payload"></a> ładunek

Ładunek `message` obiektu.

```
T const payload;
```

##  <a name="remove_ref"></a> remove_ref —

Odejmuje z licznikiem odwołań do `message` obiektu. Używane dla bloków komunikatów, wymagających zliczania odniesień, by określić okres istnienia komunikatu.

```
long remove_ref();
```

### <a name="return-value"></a>Wartość zwracana

Nowa wartość licznika odwołań.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
