---
title: ordered_message_processor — Klasa
ms.date: 11/04/2016
f1_keywords:
- ordered_message_processor
- AGENTS/concurrency::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::async_send
- AGENTS/concurrency::ordered_message_processor::initialize
- AGENTS/concurrency::ordered_message_processor::initialize_batched_processing
- AGENTS/concurrency::ordered_message_processor::sync_send
- AGENTS/concurrency::ordered_message_processor::wait
- AGENTS/concurrency::ordered_message_processor::process_incoming_message
helpviewer_keywords:
- ordered_message_processor class
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
ms.openlocfilehash: b88544f399031a5f770fa39aa1f3300306158511
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270751"
---
# <a name="orderedmessageprocessor-class"></a>ordered_message_processor — Klasa

`ordered_message_processor` Jest `message_processor` umożliwiająca bloki komunikatów do przetwarzania wiadomości w kolejności zostały odebrane.

## <a name="syntax"></a>Składnia

```
template<class T>
class ordered_message_processor : public message_processor<T>;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ ładunku komunikaty obsługiwane przez procesor.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`type`|Alias typu `T`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ordered_message_processor](#ctor)|Konstruuje `ordered_message_processor` obiektu.|
|[~ordered_message_processor Destructor](#dtor)|Niszczy `ordered_message_processor` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[async_send](#async_send)|Asynchronicznie ustawia w kolejce komunikaty i uruchamia zadanie przetwarzania, jeśli nie zostało to zrobione już. (Przesłania [message_processor::async_send —](message-processor-class.md#async_send).)|
|[Inicjowanie](#initialize)|Inicjuje `ordered_message_processor` obiektu przy użyciu funkcji, harmonogram i Zaplanuj grupy odpowiednie wywołania zwrotnego.|
|[initialize_batched_processing](#initialize_batched_processing)|Przetwarzanie komunikatów wsadowej inicjowania|
|[sync_send](#sync_send)|Synchronicznie kolejki komunikaty i uruchamia zadanie przetwarzania, jeśli nie zostało to zrobione już. (Przesłania [message_processor::sync_send —](message-processor-class.md#sync_send).)|
|[Czekaj](#wait)|Zaczekaj pokrętła specyficznych dla procesora, upewnij się, że wszystkie zadania przetwarzania asynchronicznego czasu na zakończenie przed niszczenie bloku, umożliwia w destruktorach bloków komunikatów. (Przesłania [message_processor::wait —](message-processor-class.md#wait).)|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|Funkcja przetwarzania, która jest wywoływana asynchronicznie. On dequeues wiadomości i rozpoczyna przetwarzanie je. (Przesłania [message_processor::process_incoming_message —](message-processor-class.md#process_incoming_message).)|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[message_processor](message-processor-class.md)

`ordered_message_processor`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="async_send"></a> async_send —

Asynchronicznie ustawia w kolejce komunikaty i uruchamia zadanie przetwarzania, jeśli nie zostało to zrobione już.

```
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
Wskaźnik do wiadomości.

##  <a name="initialize"></a> Inicjowanie

Inicjuje `ordered_message_processor` obiektu przy użyciu funkcji, harmonogram i Zaplanuj grupy odpowiednie wywołania zwrotnego.

```
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
Wskaźnik do harmonogramu, który ma być używany w przypadku planowania zadań lekki.

*_PScheduleGroup*<br/>
Wskaźnik do grupy harmonogramu, który ma być używany w przypadku planowania zadań lekki.

*_Handler*<br/>
Funkcję obsługi wywoływane podczas wywołania zwrotnego.

##  <a name="initialize_batched_processing"></a> initialize_batched_processing —

Przetwarzanie komunikatów wsadowej inicjowania

```
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```

### <a name="parameters"></a>Parametry

*_Processor*<br/>
Funkcję procesora wywoływane podczas wywołania zwrotnego.

*_Propagator*<br/>
Funkcję propagator wywoływane podczas wywołania zwrotnego.

##  <a name="ctor"></a> ordered_message_processor —

Konstruuje `ordered_message_processor` obiektu.

```
ordered_message_processor();
```

### <a name="remarks"></a>Uwagi

To `ordered_message_processor` nie będą planować asynchronicznego lub synchronicznego obsługi do momentu `initialize` funkcja jest wywoływana.

##  <a name="dtor"></a> ~ordered_message_processor

Niszczy `ordered_message_processor` obiektu.

```
virtual ~ordered_message_processor();
```

### <a name="remarks"></a>Uwagi

Czeka na wszystkie oczekujące operacje asynchroniczne przed niszczenie procesora.

##  <a name="process_incoming_message"></a> process_incoming_message —

Funkcja przetwarzania, która jest wywoływana asynchronicznie. On dequeues wiadomości i rozpoczyna przetwarzanie je.

```
virtual void process_incoming_message();
```

##  <a name="sync_send"></a> sync_send —

Synchronicznie kolejki komunikaty i uruchamia zadanie przetwarzania, jeśli nie zostało to zrobione już.

```
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
Wskaźnik do wiadomości.

##  <a name="wait"></a> Czekaj

Zaczekaj pokrętła specyficznych dla procesora, upewnij się, że wszystkie zadania przetwarzania asynchronicznego czasu na zakończenie przed niszczenie bloku, umożliwia w destruktorach bloków komunikatów.

```
virtual void wait();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
