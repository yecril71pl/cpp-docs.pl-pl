---
title: Klasa unbounded_buffer | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- unbounded_buffer
- AGENTS/concurrency::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::dequeue
- AGENTS/concurrency::unbounded_buffer::enqueue
- AGENTS/concurrency::unbounded_buffer::accept_message
- AGENTS/concurrency::unbounded_buffer::consume_message
- AGENTS/concurrency::unbounded_buffer::link_target_notification
- AGENTS/concurrency::unbounded_buffer::process_input_messages
- AGENTS/concurrency::unbounded_buffer::propagate_message
- AGENTS/concurrency::unbounded_buffer::propagate_output_messages
- AGENTS/concurrency::unbounded_buffer::release_message
- AGENTS/concurrency::unbounded_buffer::reserve_message
- AGENTS/concurrency::unbounded_buffer::resume_propagation
- AGENTS/concurrency::unbounded_buffer::send_message
- AGENTS/concurrency::unbounded_buffer::supports_anonymous_source
dev_langs:
- C++
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ecddf2327e3b2e29dd3c9a857227c03d9e880ef4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
`unbounded_buffer` Blok komunikatów jest wiele docelowych, wielu źródłach, uporządkowanych `propagator_block` można przechowywać niepowiązany liczba komunikatów.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<  
   class             _Type  
>  
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Type`  
 Rodzaj ładunku komunikaty przechowywane i propagowane przez bufor.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[unbounded_buffer](#ctor)|Przeciążone. Konstruuje `unbounded_buffer` bloku obsługi wiadomości.|  
|[~ unbounded_buffer — destruktor](#dtor)|Niszczy `unbounded_buffer` bloku obsługi wiadomości.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Usuwania z kolejki](#dequeue)|Usuwa element z `unbounded_buffer` bloku obsługi wiadomości.|  
|[enqueue](#enqueue)|Dodaje element do `unbounded_buffer` bloku obsługi wiadomości.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Akceptuje wiadomość została przyjęta przez to `unbounded_buffer` bloku obsługi wiadomości, przeniesieniem własności do obiektu wywołującego.|  
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowane przez `unbounded_buffer` wiadomości bloku oraz zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.|  
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które informuje, że nowy element docelowy został powiązany to `unbounded_buffer` bloku obsługi wiadomości.|  
|[process_input_messages](#process_input_messages)|Miejsca `message` `_PMessage` w tym `unbounded_buffer` Blok obsługi wiadomości i próbuje oferują go do wszystkich połączonych elementów docelowych.|  
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `unbounded_buffer` bloku obsługi wiadomości. Jest ono wywoływane przez `propagate` metody wywołanego bloku źródłowego.|  
|[propagate_output_messages](#propagate_output_messages)|Miejsca `message` `_PMessage` w tym `unbounded_buffer` Blok obsługi wiadomości i próbuje oferują go do wszystkich połączonych elementów docelowych. (Przesłania [source_block::propagate_output_messages](source-block-class.md#propagate_output_messages).)|  
|[release_message](#release_message)|Zwalnia Poprzednia rezerwacja wiadomości. (Przesłania [source_block::release_message](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowane przez to `unbounded_buffer` bloku obsługi wiadomości. (Przesłania [source_block::reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Wznawia propagacji po zastrzeżenie został zwolniony. (Przesłania [source_block::resume_propagation](source-block-class.md#resume_propagation).)|  
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z `ISource` bloku do tego `unbounded_buffer` bloku obsługi wiadomości. Jest ono wywoływane przez `send` metody wywołanego bloku źródłowego.|  
|[supports_anonymous_source](#supports_anonymous_source)|Zastępuje `supports_anonymous_source` metody, aby wskazać, że ten blok może akceptować komunikaty oferowane przez źródło, który nie jest połączony. (Przesłania [ITarget::supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|  

 Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [Isource —](isource-class.md)  
  
 [Itarget —](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `unbounded_buffer`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="accept_message"></a> accept_message 

 Akceptuje wiadomość została przyjęta przez to `unbounded_buffer` bloku obsługi wiadomości, przeniesieniem własności do obiektu wywołującego.  
  
```  
virtual message<_Type> * accept_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z oferowany `message` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiekt, aby wywołującego ma teraz własności.  
  
##  <a name="consume_message"></a> consume_message 

 Wykorzystuje komunikat wcześniej oferowane przez `unbounded_buffer` wiadomości bloku oraz zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.  
  
```  
virtual message<_Type> * consume_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiektu są używane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiekt, aby wywołującego ma teraz własności.  
  
### <a name="remarks"></a>Uwagi  
 Podobnie jak `accept`, ale zawsze jest poprzedzony przez wywołanie `reserve`.  
  
##  <a name="dequeue">Usuwania z kolejki</a> 

 Usuwa element z `unbounded_buffer` bloku obsługi wiadomości.  
  
```  
_Type dequeue();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ładunek komunikatu usunięte z `unbounded_buffer`.  
  
##  <a name="enqueue"></a> Umieścić w kolejce 

 Dodaje element do `unbounded_buffer` bloku obsługi wiadomości.  
  
```  
bool enqueue(  
   _Type const&                 _Item  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Item`  
 Element do dodania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli element został zaakceptowany, `false` inaczej.  
  
##  <a name="link_target_notification"></a> link_target_notification 

 Wywołanie zwrotne, które informuje, że nowy element docelowy został powiązany to `unbounded_buffer` bloku obsługi wiadomości.  
  
```  
virtual void link_target_notification(  
   _Inout_ ITarget<_Type> *                 _PTarget  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do nowo połączonego obiektu docelowego.  
  
##  <a name="propagate_message"></a> propagate_message 

 Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `unbounded_buffer` bloku obsługi wiadomości. Jest ono wywoływane przez `propagate` metody wywołanego bloku źródłowego.  
  
```  
virtual message_status propagate_message(  
   _Inout_ message<_Type> *                 _PMessage,  
   _Inout_ ISource<_Type> *                 _PSource  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do `message` obiektu.  
  
 `_PSource`  
 Wskaźnik do bloku źródłowego oferty wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [message_status —](concurrency-namespace-enums.md#message_status) wskazanie docelowy korzystam z komunikatu.  
  
##  <a name="propagate_output_messages"></a> propagate_output_messages 

 Miejsca `message` `_PMessage` w tym `unbounded_buffer` Blok obsługi wiadomości i próbuje oferują go do wszystkich połączonych elementów docelowych.  
  
```  
virtual void propagate_output_messages();  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli kolejną wiadomość jest już wcześniejsze pokazanego w `unbounded_buffer`, nie nastąpi propagacji połączone elementy docelowe, do momentu zaakceptowania lub używane wszystkie wcześniejsze komunikaty. Pierwszy połączony pomyślnie docelowych i `accept` lub `consume` przejmuje wiadomości i bez obiektu docelowego, można uzyskać komunikatu.  
  
##  <a name="process_input_messages"></a> process_input_messages 

 Miejsca `message` `_PMessage` w tym `unbounded_buffer` Blok obsługi wiadomości i próbuje oferują go do wszystkich połączonych elementów docelowych.  
  
```  
virtual void process_input_messages(  
   _Inout_ message<_Type> *                 _PMessage  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
  
##  <a name="release_message"></a> release_message 

 Zwalnia Poprzednia rezerwacja wiadomości.  
  
```  
virtual void release_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiekt został wydany.  
  
##  <a name="reserve_message"></a> reserve_message 

 Rezerwuje komunikat wcześniej oferowane przez to `unbounded_buffer` bloku obsługi wiadomości.  
  
```  
virtual bool reserve_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiektu pozostaje zarezerwowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli komunikat został pomyślnie zarezerwowany, `false` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Po `reserve` jest wywoływana, jeśli zwróci ona `true`, albo `consume` lub `release` musi zostać wywołana albo lub zwolnij własność wiadomości.  
  
##  <a name="resume_propagation"></a> resume_propagation 

 Wznawia propagacji po zastrzeżenie został zwolniony.  
  
```  
virtual void resume_propagation();  
```  
  
##  <a name="send_message"></a> send_message 

 Synchronicznie przekazuje komunikat z `ISource` bloku do tego `unbounded_buffer` bloku obsługi wiadomości. Jest ono wywoływane przez `send` metody wywołanego bloku źródłowego.  
  
```  
virtual message_status send_message(  
   _Inout_ message<_Type> *                 _PMessage,  
   _Inout_ ISource<_Type> *                 _PSource  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do `message` obiektu.  
  
 `_PSource`  
 Wskaźnik do bloku źródłowego oferty wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [message_status —](concurrency-namespace-enums.md#message_status) wskazanie docelowy korzystam z komunikatu.  
  
##  <a name="supports_anonymous_source"></a> supports_anonymous_source 

 Zastępuje `supports_anonymous_source` metody, aby wskazać, że ten blok może akceptować komunikaty oferowane przez źródło, który nie jest połączony.  
  
```  
virtual bool supports_anonymous_source();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` ponieważ bloku nie odłożyć oferowane wiadomości.  
  
##  <a name="ctor">unbounded_buffer</a> 

 Konstruuje `unbounded_buffer` bloku obsługi wiadomości.  
  
```  
unbounded_buffer();  
  
unbounded_buffer(  
   filter_method const&                 _Filter  
);  
  
unbounded_buffer(  
   Scheduler&                 _PScheduler  
);  
  
unbounded_buffer(  
   Scheduler&                 _PScheduler,  
   filter_method const&                 _Filter  
);  
  
unbounded_buffer(  
   ScheduleGroup&                 _PScheduleGroup  
);  
  
unbounded_buffer(  
   ScheduleGroup&                 _PScheduleGroup,  
   filter_method const&                 _Filter  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Filter`  
 Funkcja filtru, który określa, czy oferowany wiadomości powinna być akceptowana.  
  
 `_PScheduler`  
 `Scheduler` Obiektu, w którym zadanie propagacji `unbounded_buffer` zaplanowano bloku obsługi wiadomości.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Obiektu, w którym zadanie propagacji `unbounded_buffer` zaplanowano bloku obsługi wiadomości. `Scheduler` Technicznego obiekt używany przez grupę harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.  
  
 Typ `filter_method` jest obiekt podpisem `bool (_Type const &)` który jest wywoływany przez to `unbounded_buffer` obsługi komunikatów bloku, aby ustalić, czy powinna obsługiwać komunikatu oferowany.  
  
##  <a name="dtor"></a> ~ unbounded_buffer 

 Niszczy `unbounded_buffer` bloku obsługi wiadomości.  
  
```  
~unbounded_buffer();  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Klasa overwrite_buffer](overwrite-buffer-class.md)   
 [single_assignment, klasa](single-assignment-class.md)


