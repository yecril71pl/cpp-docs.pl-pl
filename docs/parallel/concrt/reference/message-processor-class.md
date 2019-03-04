---
title: message_processor — Klasa
ms.date: 11/04/2016
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
helpviewer_keywords:
- message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
ms.openlocfilehash: be6cb1c614a41919663a4cc063da66679556e498
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295243"
---
# <a name="messageprocessor-class"></a>message_processor — Klasa

`message_processor` Klasa jest abstrakcyjna klasa bazowa dla przetwarzania `message` obiektów. Nie ma żadnej gwarancji, w kolejności wiadomości.

## <a name="syntax"></a>Składnia

```
template<class T>
class message_processor;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych ładunku w komunikatach obsługiwanych przez to `message_processor` obiektu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`type`|Alias typu `T`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[async_send](#async_send)|W przypadku przesłonięcia w klasie pochodnej, umieszcza komunikaty w bloku asynchronicznie.|
|[sync_send](#sync_send)|W przypadku przesłonięcia w klasie pochodnej, umieszcza komunikaty w bloku synchronicznie.|
|[Czekaj](#wait)|W przypadku przesłonięcia w klasie pochodnej, czeka na zakończenie wszystkich operacji asynchronicznych.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|W przypadku przesłonięcia w klasie pochodnej, wykonuje przetwarzanie komunikatów w bloku do przodu. Volat pouze jednou za każdym razem, gdy nowy komunikat zostanie dodany i kolejki pozostaje puste.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`message_processor`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="async_send"></a> async_send —

W przypadku przesłonięcia w klasie pochodnej, umieszcza komunikaty w bloku asynchronicznie.

```
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
A `message` obiekt do wysyłania asynchronicznie.

### <a name="remarks"></a>Uwagi

Implementacji procesora, powinny przesłaniać tę metodę.

##  <a name="process_incoming_message"></a> process_incoming_message —

W przypadku przesłonięcia w klasie pochodnej, wykonuje przetwarzanie komunikatów w bloku do przodu. Volat pouze jednou za każdym razem, gdy nowy komunikat zostanie dodany i kolejki pozostaje puste.

```
virtual void process_incoming_message() = 0;
```

### <a name="remarks"></a>Uwagi

Implementacji bloku komunikatu powinny przesłaniać tę metodę.

##  <a name="sync_send"></a> sync_send —

W przypadku przesłonięcia w klasie pochodnej, umieszcza komunikaty w bloku synchronicznie.

```
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
A `message` obiekt do wysyłania synchronicznie.

### <a name="remarks"></a>Uwagi

Implementacji procesora, powinny przesłaniać tę metodę.

##  <a name="wait"></a> Czekaj

W przypadku przesłonięcia w klasie pochodnej, czeka na zakończenie wszystkich operacji asynchronicznych.

```
virtual void wait() = 0;
```

### <a name="remarks"></a>Uwagi

Implementacji procesora, powinny przesłaniać tę metodę.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[ordered_message_processor, klasa](ordered-message-processor-class.md)
