---
title: Klasa transformatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- transformer
- AGENTS/concurrency::transformer
- AGENTS/concurrency::transformer::transformer
- AGENTS/concurrency::transformer::accept_message
- AGENTS/concurrency::transformer::consume_message
- AGENTS/concurrency::transformer::link_target_notification
- AGENTS/concurrency::transformer::propagate_message
- AGENTS/concurrency::transformer::propagate_to_any_targets
- AGENTS/concurrency::transformer::release_message
- AGENTS/concurrency::transformer::reserve_message
- AGENTS/concurrency::transformer::resume_propagation
- AGENTS/concurrency::transformer::send_message
- AGENTS/concurrency::transformer::supports_anonymous_source
dev_langs:
- C++
helpviewer_keywords:
- transformer class
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac9ea43e1d3f6f369b93e92e91fa3606cf7d6af5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="transformer-class"></a>Klasa transformatora
A `transformer` Blok obsługi wiadomości jest element docelowy jednym wielu źródłach, uporządkowanych `propagator_block` co mogą akceptować wiadomości danego typu i jest w stanie przechowywania niepowiązany liczba wiadomości jest innego typu.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```   
  
#### <a name="parameters"></a>Parametry  
 `_Input`  
 Typ ładunku zaakceptowane przez bufor komunikatów.  
  
 `_Output`  
 Rodzaj ładunku komunikaty przechowywane i propagowane limitu przez bufor.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[transformer](#ctor)|Przeciążone. Konstruuje `transformer` bloku obsługi wiadomości.|  
|[~ transformer — destruktor](#dtor)|Niszczy `transformer` bloku obsługi wiadomości.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Akceptuje wiadomość została przyjęta przez to `transformer` bloku obsługi wiadomości, przeniesieniem własności do obiektu wywołującego.|  
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowane przez `transformer` i zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.|  
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które informuje, że nowy element docelowy został powiązany to `transformer` bloku obsługi wiadomości.|  
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `transformer` bloku obsługi wiadomości. Jest ono wywoływane przez `propagate` metody wywołanego bloku źródłowego.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Wykonuje funkcję transformatora na komunikaty wejściowe.|  
|[release_message](#release_message)|Zwalnia Poprzednia rezerwacja wiadomości. (Przesłania [source_block::release_message](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowane przez to `transformer` bloku obsługi wiadomości. (Przesłania [source_block::reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Wznawia propagacji po zastrzeżenie został zwolniony. (Przesłania [source_block::resume_propagation](source-block-class.md#resume_propagation).)|  
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z `ISource` bloku do tego `transformer` bloku obsługi wiadomości. Jest ono wywoływane przez `send` metody wywołanego bloku źródłowego.|  
|[supports_anonymous_source](#supports_anonymous_source)|Zastępuje `supports_anonymous_source` metody, aby wskazać, że ten blok może akceptować komunikaty oferowane przez źródło, który nie jest połączony. (Przesłania [ITarget::supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [Isource —](isource-class.md)  
  
 [Itarget —](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `transformer`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="accept_message"></a> accept_message 

 Akceptuje wiadomość została przyjęta przez to `transformer` bloku obsługi wiadomości, przeniesieniem własności do obiektu wywołującego.  
  
```
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z oferowany `message` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiekt, aby wywołującego ma teraz własności.  
  
##  <a name="consume_message"></a> consume_message 

 Wykorzystuje komunikat wcześniej oferowane przez `transformer` i zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.  
  
```
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiektu są używane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiekt, aby wywołującego ma teraz własności.  
  
### <a name="remarks"></a>Uwagi  
 Podobnie jak `accept`, ale zawsze jest poprzedzony przez wywołanie `reserve`.  
  
##  <a name="link_target_notification"></a> link_target_notification 

 Wywołanie zwrotne, które informuje, że nowy element docelowy został powiązany to `transformer` bloku obsługi wiadomości.  
  
```
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```  
  
##  <a name="propagate_message"></a> propagate_message 

 Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `transformer` bloku obsługi wiadomości. Jest ono wywoływane przez `propagate` metody wywołanego bloku źródłowego.  
  
```
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do `message` obiektu.  
  
 `_PSource`  
 Wskaźnik do bloku źródłowego oferty wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [message_status —](concurrency-namespace-enums.md) wskazanie docelowy korzystam z komunikatu.  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets 

 Wykonuje funkcję transformatora na komunikaty wejściowe.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
```  
  
##  <a name="release_message"></a> release_message 

 Zwalnia Poprzednia rezerwacja wiadomości.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiekt został wydany.  
  
##  <a name="reserve_message"></a> reserve_message 

 Rezerwuje komunikat wcześniej oferowane przez to `transformer` bloku obsługi wiadomości.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
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

 Synchronicznie przekazuje komunikat z `ISource` bloku do tego `transformer` bloku obsługi wiadomości. Jest ono wywoływane przez `send` metody wywołanego bloku źródłowego.  
  
```
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do `message` obiektu.  
  
 `_PSource`  
 Wskaźnik do bloku źródłowego oferty wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [message_status —](concurrency-namespace-enums.md) wskazanie docelowy korzystam z komunikatu.  
  
##  <a name="supports_anonymous_source"></a> supports_anonymous_source 

 Zastępuje `supports_anonymous_source` metody, aby wskazać, że ten blok może akceptować komunikaty oferowane przez źródło, który nie jest połączony.  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` ponieważ bloku nie odłożyć oferowane wiadomości.  
  
##  <a name="ctor"></a> transformatora 

 Konstruuje `transformer` bloku obsługi wiadomości.  
  
```
transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parametry  
 `_Func`  
 Funkcja, która zostanie wywołana dla każdego komunikatu zaakceptowane.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, aby połączyć z transformator.  
  
 `_Filter`  
 Funkcja filtru, który określa, czy oferowany wiadomości powinna być akceptowana.  
  
 `_PScheduler`  
 `Scheduler` Obiektu, w którym zadanie propagacji `transformer` zaplanowano bloku obsługi wiadomości.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Obiektu, w którym zadanie propagacji `transformer` zaplanowano bloku obsługi wiadomości. `Scheduler` Technicznego obiekt używany przez grupę harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.  
  
 Typ `_Transform_method` jest obiekt podpisem `_Output (_Input const &)` który jest wywoływany przez to `transformer` Blok obsługi komunikatów do przetworzenia komunikatu.  
  
 Typ `filter_method` jest obiekt podpisem `bool (_Input const &)` który jest wywoływany przez to `transformer` obsługi komunikatów bloku, aby ustalić, czy powinna obsługiwać komunikatu oferowany.  
  
##  <a name="dtor"></a> ~ transformer 

 Niszczy `transformer` bloku obsługi wiadomości.  
  
```
~transformer();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [call, klasa](call-class.md)
