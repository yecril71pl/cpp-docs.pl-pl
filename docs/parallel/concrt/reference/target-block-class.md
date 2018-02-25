---
title: "target_block — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- target_block
- AGENTS/concurrency::target_block
- AGENTS/concurrency::target_block::target_block
- AGENTS/concurrency::target_block::propagate
- AGENTS/concurrency::target_block::send
- AGENTS/concurrency::target_block::async_send
- AGENTS/concurrency::target_block::decline_incoming_messages
- AGENTS/concurrency::target_block::enable_batched_processing
- AGENTS/concurrency::target_block::initialize_target
- AGENTS/concurrency::target_block::link_source
- AGENTS/concurrency::target_block::process_input_messages
- AGENTS/concurrency::target_block::process_message
- AGENTS/concurrency::target_block::propagate_message
- AGENTS/concurrency::target_block::register_filter
- AGENTS/concurrency::target_block::remove_sources
- AGENTS/concurrency::target_block::send_message
- AGENTS/concurrency::target_block::sync_send
- AGENTS/concurrency::target_block::unlink_source
- AGENTS/concurrency::target_block::unlink_sources
- AGENTS/concurrency::target_block::wait_for_async_sends
dev_langs:
- C++
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2827e7bbb9a2c23804d90ccb729e990b84f3a442
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="targetblock-class"></a>target_block — Klasa
`target_block` Klasa jest abstrakcyjna klasa podstawowa, którego łącze podstawowe funkcje zarządzania i tylko sprawdzanie błędów dla elementu docelowego blokuje.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```  
  
#### <a name="parameters"></a>Parametry  
 `_SourceLinkRegistry`  
 Łącze rejestru służący do przechowywania łączy źródła.  
  
 `_MessageProcessorType`  
 Typ procesora do przetwarzania komunikatów.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`source_iterator`|Typ iteratora dla `source_link_manager` dla tego `target_block` obiektu.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[target_block](#ctor)|Konstruuje `target_block` obiektu.|  
|[~ target_block — destruktor](#dtor)|Niszczy `target_block` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[propagate](#propagate)|Asynchronicznie przekazuje komunikat z bloku źródłowego do tego bloku docelowego.|  
|[Wyślij](#send)|Synchronicznie przekazuje komunikat z bloku źródłowego do tego bloku docelowego.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[async_send](#async_send)|Asynchronicznie wysyła komunikat do przetwarzania.|  
|[decline_incoming_messages](#decline_incoming_messages)|Wskazuje do bloku nowej wiadomości powinna zostać odrzucona.|  
|[enable_batched_processing](#enable_batched_processing)|Włącza umieścić w zadaniu wsadowym przetwarzania dla tego bloku.|  
|[initialize_target](#initialize_target)|Inicjuje obiekt podstawowy. W szczególności `message_processor` obiekt musi zostać zainicjowany.|  
|[link_source](#link_source)|Łącza do tego bloku określonego źródła `target_block` obiektu.|  
|[process_input_messages](#process_input_messages)|Przetwarza wiadomości odebrane jako dane wejściowe.|  
|[process_message](#process_message)|W przypadku przesłonięcia w klasie pochodnej, przetwarza komunikat, który został zaakceptowany przez to `target_block` obiektu.|  
|[propagate_message](#propagate_message)|W przypadku przesłonięcia w klasie pochodnej, ta metoda przekazuje asynchronicznie komunikat z `ISource` bloku do tego `target_block` obiektu. Jest ono wywoływane przez `propagate` metody wywołanego bloku źródłowego.|  
|[register_filter](#register_filter)|Rejestruje metodę filtru, która zostanie wywołana na każdy komunikat.|  
|[remove_sources](#remove_sources)|Odłączenie wszystkich źródeł oczekiwania na zakończenie operacji oczekujących asynchronicznego wysyłania.|  
|[send_message](#send_message)|W przypadku przesłonięcia w klasie pochodnej, ta metoda przekazuje synchronicznie komunikat z `ISource` bloku do tego `target_block` obiektu. Jest ono wywoływane przez `send` metody wywołanego bloku źródłowego.|  
|[sync_send](#sync_send)|Synchronicznie Wyślij wiadomość do przetwarzania.|  
|[unlink_source](#unlink_source)|Odłączenie od tego bloku określonego źródła `target_block` obiektu.|  
|[unlink_sources](#unlink_sources)|Odłączenie wszystkich bloków źródła tego `target_block` obiektu. (Przesłania [ITarget::unlink_sources](itarget-class.md#unlink_sources).)|  
|[wait_for_async_sends](#wait_for_async_sends)|Czeka na wszystkich propagacji asynchroniczne zakończyć.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [Itarget —](itarget-class.md)  
  
 `target_block`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="async_send"></a> async_send 

 Asynchronicznie wysyła komunikat do przetwarzania.  
  
```
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do wysyłanej wiadomości.  
  
##  <a name="decline_incoming_messages"></a> decline_incoming_messages 

 Wskazuje do bloku nowej wiadomości powinna zostać odrzucona.  
  
```
void decline_incoming_messages();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez destruktor, aby upewnić się, gdy trwa niszczenie odrzucane nowych wiadomości.  
  
##  <a name="enable_batched_processing"></a> enable_batched_processing 

 Włącza umieścić w zadaniu wsadowym przetwarzania dla tego bloku.  
  
```
void enable_batched_processing();
```  
  
##  <a name="initialize_target"></a> initialize_target 

 Inicjuje obiekt podstawowy. W szczególności `message_processor` obiekt musi zostać zainicjowany.  
  
```
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `_PScheduler`  
 Harmonogram, który ma służyć do planowania zadań.  
  
 `_PScheduleGroup`  
 Grupa harmonogram, który ma być używana do planowania zadań.  
  
##  <a name="link_source"></a> link_source 

 Łącza do tego bloku określonego źródła `target_block` obiektu.  
  
```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PSource`  
 Wskaźnik do `ISource` bloku, który ma być połączony.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja nie powinna być wywoływana bezpośrednio na `target_block` obiektu. Bloki powinny być połączone ze sobą przy użyciu `link_target` metoda `ISource` bloków, które wywoła `link_source` metody w celu odpowiedniego.  
  
##  <a name="process_input_messages"></a> process_input_messages 

 Przetwarza wiadomości odebrane jako dane wejściowe.  
  
```
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
  
##  <a name="process_message"></a> process_message 

 W przypadku przesłonięcia w klasie pochodnej, przetwarza komunikat, który został zaakceptowany przez to `target_block` obiektu.  
  
```
virtual void process_message(message<_Source_type> *);
```  
  
##  <a name="propagate"></a> Propagacja 

 Asynchronicznie przekazuje komunikat z bloku źródłowego do tego bloku docelowego.  
  
```
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do `message` obiektu.  
  
 `_PSource`  
 Wskaźnik do bloku źródłowego oferty wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [message_status —](concurrency-namespace-enums.md) wskazanie docelowy korzystam z komunikatu.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli dowolny `_PMessage` lub `_PSource` parametr jest `NULL`.  
  
##  <a name="propagate_message"></a> propagate_message 

 W przypadku przesłonięcia w klasie pochodnej, ta metoda przekazuje asynchronicznie komunikat z `ISource` bloku do tego `target_block` obiektu. Jest ono wywoływane przez `propagate` metody wywołanego bloku źródłowego.  
  
```
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do `message` obiektu.  
  
 `_PSource`  
 Wskaźnik do bloku źródłowego oferty wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [message_status —](concurrency-namespace-enums.md) wskazanie docelowy korzystam z komunikatu.  
  
##  <a name="register_filter"></a> register_filter 

 Rejestruje metodę filtru, która zostanie wywołana na każdy komunikat.  
  
```
void register_filter(filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filter`  
 Metoda filtru.  
  
##  <a name="remove_sources"></a> remove_sources 

 Odłączenie wszystkich źródeł oczekiwania na zakończenie operacji oczekujących asynchronicznego wysyłania.  
  
```
void remove_sources();
```  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie bloki docelowy powinny wywoływać tej procedury można usunąć źródła w ich destruktora.  
  
##  <a name="send">Wyślij</a> 

 Synchronicznie przekazuje komunikat z bloku źródłowego do tego bloku docelowego.  
  
```
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do `message` obiektu.  
  
 `_PSource`  
 Wskaźnik do bloku źródłowego oferty wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [message_status —](concurrency-namespace-enums.md) wskazanie docelowy korzystam z komunikatu.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli dowolny `_PMessage` lub `_PSource` parametr jest `NULL`.  
  
 Przy użyciu `send` metody poza inicjowania wiadomości oraz propagację wiadomości w sieci jest niebezpieczny i może doprowadzić do zakleszczenia.  
  
 Gdy `send` zwraca komunikat albo już zostało zaakceptowane i przesyłane do bloku docelowego lub została odrzucona przez element docelowy.  
  
##  <a name="send_message"></a> send_message 

 W przypadku przesłonięcia w klasie pochodnej, ta metoda przekazuje synchronicznie komunikat z `ISource` bloku do tego `target_block` obiektu. Jest ono wywoływane przez `send` metody wywołanego bloku źródłowego.  
  
```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [message_status —](concurrency-namespace-enums.md) wskazanie docelowy korzystam z komunikatu.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie, zwraca ten blok `declined` Jeśli zastąpiona przez klasę pochodną.  
  
##  <a name="sync_send"></a> sync_send 

 Synchronicznie Wyślij wiadomość do przetwarzania.  
  
```
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do wysyłanej wiadomości.  
  
##  <a name="ctor"></a> target_block — 

 Konstruuje `target_block` obiektu.  
  
```
target_block();
```  
  
##  <a name="dtor"></a> ~ target_block — 

 Niszczy `target_block` obiektu.  
  
```
virtual ~target_block();
```  
  
##  <a name="unlink_source"></a> unlink_source 

 Odłączenie od tego bloku określonego źródła `target_block` obiektu.  
  
```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PSource`  
 Wskaźnik do `ISource` bloku, który ma być odłączone.  
  
##  <a name="unlink_sources"></a> unlink_sources 

 Odłączenie wszystkich bloków źródła tego `target_block` obiektu.  
  
```
virtual void unlink_sources();
```  
  
##  <a name="wait_for_async_sends"></a> wait_for_async_sends 

 Czeka na wszystkich propagacji asynchroniczne zakończyć.  
  
```
void wait_for_async_sends();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest używana przez destruktory bloku komunikatów, aby upewnić się, że wszystkie operacje asynchroniczne miały czasu, aby zakończyć działanie przed niszczenie bloku.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [ITarget, klasa](itarget-class.md)
