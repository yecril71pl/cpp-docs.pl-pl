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
ms.openlocfilehash: 88944b2d935eebd0e031be1431c2a0f4efa3d760
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139468"
---
# <a name="message_processor-class"></a>message_processor — Klasa

Klasa `message_processor` jest abstrakcyjną klasą bazową do przetwarzania obiektów `message`. Nie ma gwarancji dotyczącej kolejności komunikatów.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
class message_processor;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ danych ładunku w komunikatach obsłużonych przez ten obiekt `message_processor`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`type`|Alias typu dla `T`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[async_send](#async_send)|Gdy jest zastępowany w klasie pochodnej, umieszcza komunikaty w bloku asynchronicznie.|
|[sync_send](#sync_send)|Gdy jest zastępowany w klasie pochodnej, umieszcza komunikaty w bloku synchronicznie.|
|[trwa](#wait)|Gdy jest zastępowany w klasie pochodnej, czeka na zakończenie wszystkich operacji asynchronicznych.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|W przypadku zastąpienia w klasie pochodnej program wykonuje przetwarzanie komunikatów do przodu w bloku. Wywoływana raz za każdym razem, gdy zostanie dodany nowy komunikat, a kolejka jest pusta.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`message_processor`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="async_send"></a>async_send

Gdy jest zastępowany w klasie pochodnej, umieszcza komunikaty w bloku asynchronicznie.

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
Obiekt `message` do wysłania asynchronicznie.

### <a name="remarks"></a>Uwagi

Implementacje procesora powinny przesłaniać tę metodę.

## <a name="process_incoming_message"></a>process_incoming_message

W przypadku zastąpienia w klasie pochodnej program wykonuje przetwarzanie komunikatów do przodu w bloku. Wywoływana raz za każdym razem, gdy zostanie dodany nowy komunikat, a kolejka jest pusta.

```cpp
virtual void process_incoming_message() = 0;
```

### <a name="remarks"></a>Uwagi

Implementacje bloku komunikatów powinny przesłaniać tę metodę.

## <a name="sync_send"></a>sync_send

Gdy jest zastępowany w klasie pochodnej, umieszcza komunikaty w bloku synchronicznie.

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
Obiekt `message` do wysłania synchronicznie.

### <a name="remarks"></a>Uwagi

Implementacje procesora powinny przesłaniać tę metodę.

## <a name="wait"></a>trwa

Gdy jest zastępowany w klasie pochodnej, czeka na zakończenie wszystkich operacji asynchronicznych.

```cpp
virtual void wait() = 0;
```

### <a name="remarks"></a>Uwagi

Implementacje procesora powinny przesłaniać tę metodę.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[ordered_message_processor, klasa](ordered-message-processor-class.md)
