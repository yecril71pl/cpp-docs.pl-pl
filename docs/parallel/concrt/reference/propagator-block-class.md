---
title: propagator_block — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- propagator_block
- AGENTS/concurrency::propagator_block
- AGENTS/concurrency::propagator_block::propagator_block
- AGENTS/concurrency::propagator_block::propagate
- AGENTS/concurrency::propagator_block::send
- AGENTS/concurrency::propagator_block::decline_incoming_messages
- AGENTS/concurrency::propagator_block::initialize_source_and_target
- AGENTS/concurrency::propagator_block::link_source
- AGENTS/concurrency::propagator_block::process_input_messages
- AGENTS/concurrency::propagator_block::propagate_message
- AGENTS/concurrency::propagator_block::register_filter
- AGENTS/concurrency::propagator_block::remove_network_links
- AGENTS/concurrency::propagator_block::send_message
- AGENTS/concurrency::propagator_block::unlink_source
- AGENTS/concurrency::propagator_block::unlink_sources
dev_langs:
- C++
helpviewer_keywords:
- propagator_block class
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb908bf108bb3ddff375506225b9be97b2898ca5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694017"
---
# <a name="propagatorblock-class"></a>propagator_block — Klasa
`propagator_block` Klasa jest abstrakcyjna klasa podstawowa dla bloków komunikatów, które są źródłowym i docelowym. Łączy funkcje obu `source_block` i `target_block` klasy.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
 public ITarget<typename _SourceLinkRegistry::type::source_type>;
```  
  
#### <a name="parameters"></a>Parametry  
 `_TargetLinkRegistry`  
 Łącze rejestru służący do przechowywania łącza docelowego.  
  
 `_SourceLinkRegistry`  
 Łącze rejestru służący do przechowywania łączy źródła.  
  
 `_MessageProcessorType`  
 Typ procesora do przetwarzania komunikatów.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`source_iterator`|Typ iteratora dla `source_link_manager` dla tego `propagator_block`.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[propagator_block](#ctor)|Konstruuje `propagator_block` obiektu.|  
|[~propagator_block Destructor](#dtor)|Niszczy `propagator_block` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[propagate](#propagate)|Asynchronicznie przekazuje komunikat z bloku źródłowego do tego bloku docelowego.|  
|[Wyślij](#send)|Inicjuje synchronicznie wiadomość do tego bloku. Wywoływane przez `ISource` bloku. Po zakończeniu tej funkcji, komunikat już zostaną rozpropagowane w bloku.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[decline_incoming_messages](#decline_incoming_messages)|Wskazuje do bloku nowej wiadomości powinna zostać odrzucona.|  
|[initialize_source_and_target](#initialize_source_and_target)|Inicjuje obiekt podstawowy. W szczególności `message_processor` obiekt musi zostać zainicjowany.|  
|[link_source](#link_source)|Łącza do tego bloku określonego źródła `propagator_block` obiektu.|  
|[process_input_messages](#process_input_messages)|Przetwarzanie komunikatów wejściowych. Ta opcja jest przydatna dla bloków propagator, które wynikają z source_block — (zastępuje [source_block::process_input_messages](source-block-class.md#process_input_messages).)|  
|[propagate_message](#propagate_message)|W przypadku przesłonięcia w klasie pochodnej, ta metoda przekazuje asynchronicznie komunikat z `ISource` bloku do tego `propagator_block` obiektu. Jest ono wywoływane przez `propagate` metody wywołanego bloku źródłowego.|  
|[register_filter](#register_filter)|Rejestruje metodę filtru, która zostanie wywołana podczas każdego odebranego komunikatu.|  
|[remove_network_links](#remove_network_links)|Usuwa wszystkie źródłowe i docelowe sieci łącza z tego `propagator_block` obiektu.|  
|[send_message](#send_message)|W przypadku przesłonięcia w klasie pochodnej, ta metoda przekazuje synchronicznie komunikat z `ISource` bloku do tego `propagator_block` obiektu. Jest ono wywoływane przez `send` metody wywołanego bloku źródłowego.|  
|[unlink_source](#unlink_source)|Odłączenie od tego bloku określonego źródła `propagator_block` obiektu.|  
|[unlink_sources](#unlink_sources)|Odłączenie wszystkich bloków źródła tego `propagator_block` obiektu. (Przesłania [ITarget::unlink_sources](itarget-class.md#unlink_sources).)|  
  
## <a name="remarks"></a>Uwagi  
 Aby uniknąć dziedziczenie wielokrotne `propagator_block` klasa dziedziczy `source_block` klasy i `ITarget` klasy abstrakcyjnej. Większość funkcji w `target_block` klasy są replikowane w tym miejscu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [Isource —](isource-class.md)  
  
 [Itarget —](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 `propagator_block`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="decline_incoming_messages"></a> decline_incoming_messages 

 Wskazuje do bloku nowej wiadomości powinna zostać odrzucona.  
  
```
void decline_incoming_messages();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez destruktor, aby upewnić się, gdy trwa niszczenie odrzucane nowych wiadomości.  
  
##  <a name="initialize_source_and_target"></a> initialize_source_and_target 

 Inicjuje obiekt podstawowy. W szczególności `message_processor` obiekt musi zostać zainicjowany.  
  
```
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `_PScheduler`  
 Harmonogram, który ma służyć do planowania zadań.  
  
 `_PScheduleGroup`  
 Grupa harmonogram, który ma być używana do planowania zadań.  
  
##  <a name="link_source"></a> link_source 

 Łącza do tego bloku określonego źródła `propagator_block` obiektu.  
  
```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PSource`  
 Wskaźnik do `ISource` bloku, który ma być połączony.  
  
##  <a name="process_input_messages"></a> process_input_messages 

 Przetwarzanie komunikatów wejściowych. Ta opcja jest przydatna dla bloków propagator, które wynikają z source_block —  
  
```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
  
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
 `propagate` Metoda jest wywoływana w bloku docelowego za pomocą bloku połączonego źródła. Kolejkuje go zadanie asynchroniczne, by obsłużyć komunikat, jeśli nie jest już Zakolejkowane lub wykonywania.  
  
 Metoda zgłasza [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli dowolny `_PMessage` lub `_PSource` parametr jest `NULL`.  
  
##  <a name="propagate_message"></a> propagate_message 

 W przypadku przesłonięcia w klasie pochodnej, ta metoda przekazuje asynchronicznie komunikat z `ISource` bloku do tego `propagator_block` obiektu. Jest ono wywoływane przez `propagate` metody wywołanego bloku źródłowego.  
  
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
  
##  <a name="ctor"></a> propagator_block — 

 Konstruuje `propagator_block` obiektu.  
  
```
propagator_block();
```  
  
##  <a name="dtor"></a> ~ propagator_block — 

 Niszczy `propagator_block` obiektu.  
  
```
virtual ~propagator_block();
```  
  
##  <a name="register_filter"></a> register_filter 

 Rejestruje metodę filtru, która zostanie wywołana podczas każdego odebranego komunikatu.  
  
```
void register_filter(filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filter`  
 Metoda filtru.  
  
##  <a name="remove_network_links"></a> remove_network_links 

 Usuwa wszystkie źródłowe i docelowe sieci łącza z tego `propagator_block` obiektu.  
  
```
void remove_network_links();
```  
  
##  <a name="send"></a> Wyślij 

 Inicjuje synchronicznie wiadomość do tego bloku. Wywoływane przez `ISource` bloku. Po zakończeniu tej funkcji, komunikat już zostaną rozpropagowane w bloku.  
  
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
 Ta metoda zgłasza [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli dowolny `_PMessage` lub `_PSource` parametr jest `NULL`.  
  
##  <a name="send_message"></a> send_message 

 W przypadku przesłonięcia w klasie pochodnej, ta metoda przekazuje synchronicznie komunikat z `ISource` bloku do tego `propagator_block` obiektu. Jest ono wywoływane przez `send` metody wywołanego bloku źródłowego.  
  
```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [message_status —](concurrency-namespace-enums.md) wskazanie docelowy korzystam z komunikatu.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie, zwraca ten blok `declined` Jeśli zastąpiona przez klasę pochodną.  
  
##  <a name="unlink_source"></a> unlink_source 

 Odłączenie od tego bloku określonego źródła `propagator_block` obiektu.  
  
```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PSource`  
 Wskaźnik do `ISource` bloku, który ma być odłączone.  
  
##  <a name="unlink_sources"></a> unlink_sources 

 Odłączenie wszystkich bloków źródła tego `propagator_block` obiektu.  
  
```
virtual void unlink_sources();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [source_block — klasa](source-block-class.md)   
 [ITarget, klasa](itarget-class.md)
