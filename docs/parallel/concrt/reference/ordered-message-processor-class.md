---
title: "ordered_message_processor — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ordered_message_processor class
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 83f3181d797b0146cc7e57950da6b5e9569b2ab1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="orderedmessageprocessor-class"></a>ordered_message_processor — Klasa
`ordered_message_processor` Jest `message_processor` umożliwiająca bloki komunikatów do przetwarzania komunikatów w kolejności ich zostały odebrane.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>
class ordered_message_processor : public message_processor<T>;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ ładunku komunikaty obsługiwane przez procesor.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
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
|[async_send](#async_send)|Asynchronicznie kolejki zapasowych wiadomości i uruchamia zadanie przetwarzania, jeśli to nie już zostało wykonane. (Przesłania [message_processor::async_send](message-processor-class.md#async_send).)|  
|[Inicjowanie](#initialize)|Inicjuje `ordered_message_processor` obiektu z odpowiedniego wywołania zwrotnego grupy funkcja, harmonogram i harmonogram.|  
|[initialize_batched_processing](#initialize_batched_processing)|Inicjowanie przetwarzania komunikatów wsadów|  
|[sync_send](#sync_send)|Synchronicznie kolejki zapasowych wiadomości i uruchamia zadanie przetwarzania, jeśli to nie już zostało wykonane. (Przesłania [message_processor::sync_send](message-processor-class.md#sync_send).)|  
|[oczekiwania](#wait)|Zaczekaj pokrętła specyficznych dla procesora, używane w destruktory bloki komunikatów, aby upewnić się, że wszystkie zadania przetwarzania asynchronicznego czasu, aby zakończyć działanie przed niszczenie bloku. (Przesłania [message_processor::wait](message-processor-class.md#wait).)|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[process_incoming_message](#process_incoming_message)|Funkcja przetwarzania, która jest wywoływana asynchronicznie. On dequeues wiadomości i rozpoczyna przetwarzanie je. (Przesłania [message_processor::process_incoming_message](message-processor-class.md#process_incoming_message).)|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [message_processor](message-processor-class.md)  
  
 `ordered_message_processor`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="async_send"></a> async_send 

 Asynchronicznie kolejki zapasowych wiadomości i uruchamia zadanie przetwarzania, jeśli to nie już zostało wykonane.  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```  
  
### <a name="parameters"></a>Parametry  
 `_Msg`  
 Wskaźnik do wiadomości.  
  
##  <a name="initialize">Inicjowanie</a> 

 Inicjuje `ordered_message_processor` obiektu z odpowiedniego wywołania zwrotnego grupy funkcja, harmonogram i harmonogram.  
  
```
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```  
  
### <a name="parameters"></a>Parametry  
 `_PScheduler`  
 Wskaźnik do harmonogramu do zastosowania w przypadku planowania zadań lekki.  
  
 `_PScheduleGroup`  
 Wskaźnik do grupa harmonogram, który ma być używana do planowania zadań lekki.  
  
 `_Handler`  
 Obiekt programu obsługi, wywoływane podczas wywołania zwrotnego.  
  
##  <a name="initialize_batched_processing"></a> initialize_batched_processing 

 Inicjowanie przetwarzania komunikatów wsadów  
  
```
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```  
  
### <a name="parameters"></a>Parametry  
 `_Processor`  
 Obiekt procesora, wywoływane podczas wywołania zwrotnego.  
  
 `_Propagator`  
 Obiekt propagator, wywoływane podczas wywołania zwrotnego.  
  
##  <a name="ctor"></a> ordered_message_processor — 

 Konstruuje `ordered_message_processor` obiektu.  
  
```
ordered_message_processor();
```  
  
### <a name="remarks"></a>Uwagi  
 To `ordered_message_processor` nie będzie zaplanować asynchroniczne i synchroniczne obsługi do `initialize` funkcja jest wywoływana.  
  
##  <a name="dtor"></a> ~ordered_message_processor 

 Niszczy `ordered_message_processor` obiektu.  
  
```
virtual ~ordered_message_processor();
```  
  
### <a name="remarks"></a>Uwagi  
 Czeka na wszystkich oczekujących operacji asynchronicznych przed niszczenie procesora.  
  
##  <a name="process_incoming_message"></a> process_incoming_message 

 Funkcja przetwarzania, która jest wywoływana asynchronicznie. On dequeues wiadomości i rozpoczyna przetwarzanie je.  
  
```
virtual void process_incoming_message();
```  
  
##  <a name="sync_send"></a> sync_send 

 Synchronicznie kolejki zapasowych wiadomości i uruchamia zadanie przetwarzania, jeśli to nie już zostało wykonane.  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```  
  
### <a name="parameters"></a>Parametry  
 `_Msg`  
 Wskaźnik do wiadomości.  
  
##  <a name="wait"></a> oczekiwania 

 Zaczekaj pokrętła specyficznych dla procesora, używane w destruktory bloki komunikatów, aby upewnić się, że wszystkie zadania przetwarzania asynchronicznego czasu, aby zakończyć działanie przed niszczenie bloku.  
  
```
virtual void wait();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
