---
title: JOIN — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- join
- AGENTS/concurrency::join
- AGENTS/concurrency::join::join
- AGENTS/concurrency::join::accept_message
- AGENTS/concurrency::join::consume_message
- AGENTS/concurrency::join::link_target_notification
- AGENTS/concurrency::join::propagate_message
- AGENTS/concurrency::join::propagate_to_any_targets
- AGENTS/concurrency::join::release_message
- AGENTS/concurrency::join::reserve_message
- AGENTS/concurrency::join::resume_propagation
dev_langs:
- C++
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a37b6d3dce5d41578999aa54c8dff2dd2271fe9e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692642"
---
# <a name="join-class"></a>join — Klasa
A `join` Blok obsługi wiadomości jest element docelowy jednym wielu źródłach, uporządkowanych `propagator_block` które łączy ze sobą komunikaty typu `T` każdego z jego źródła.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```   
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Rodzaj ładunku komunikaty przyłączone i propagowane przez bloku.  
  
 `_Jtype`  
 Rodzaj elementu `join` bloku jest, albo `greedy` lub `non_greedy`  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[join](#ctor)|Przeciążone. Konstruuje `join` bloku obsługi wiadomości.|  
|[~ join — destruktor](#dtor)|Niszczy `join` bloku.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Akceptuje wiadomość została przyjęta przez to `join` bloku obsługi wiadomości, przeniesieniem własności do obiektu wywołującego.|  
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowane przez `join` wiadomości bloku oraz zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.|  
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które informuje, że nowy element docelowy został powiązany to `join` bloku obsługi wiadomości.|  
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `join` bloku obsługi wiadomości. Jest ono wywoływane przez `propagate` metody wywołanego bloku źródłowego.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Tworzy dane wyjściowe wiadomość komunikat wejściowy z każdego źródła przy ich ma wszystkie propagacji wiadomości. Wysyła tę wiadomość dane wyjściowe do każdego z jego elementów docelowych.|  
|[release_message](#release_message)|Zwalnia Poprzednia rezerwacja wiadomości. (Przesłania [source_block::release_message](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowane przez to `join` bloku obsługi wiadomości. (Przesłania [source_block::reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Wznawia propagacji po zastrzeżenie został zwolniony. (Przesłania [source_block::resume_propagation](source-block-class.md#resume_propagation).)|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [Isource —](isource-class.md)  
  
 [Itarget —](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `join`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="accept_message"></a> accept_message 

 Akceptuje wiadomość została przyjęta przez to `join` bloku obsługi wiadomości, przeniesieniem własności do obiektu wywołującego.  
  
```
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z oferowany `message` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiekt, aby wywołującego ma teraz własności.  
  
##  <a name="consume_message"></a> consume_message 

 Wykorzystuje komunikat wcześniej oferowane przez `join` wiadomości bloku oraz zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.  
  
```
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiektu są używane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiekt, aby wywołującego ma teraz własności.  
  
### <a name="remarks"></a>Uwagi  
 Podobnie jak `accept`, ale zawsze jest poprzedzony przez wywołanie `reserve`.  
  
##  <a name="ctor"></a> Dołącz 

 Konstruuje `join` bloku obsługi wiadomości.  
  
```
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parametry  
 `_NumInputs`  
 Liczba danych wejściowych to `join` bloku będą dozwolone.  
  
 `_Filter`  
 Funkcja filtru, który określa, czy oferowany wiadomości powinna być akceptowana.  
  
 `_PScheduler`  
 `Scheduler` Obiektu, w którym zadanie propagacji `join` zaplanowano bloku obsługi wiadomości.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Obiektu, w którym zadanie propagacji `join` zaplanowano bloku obsługi wiadomości. `Scheduler` Technicznego obiekt używany przez grupę harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.  
  
 Typ `filter_method` jest obiekt podpisem `bool (T const &)` który jest wywoływany przez to `join` obsługi komunikatów bloku, aby ustalić, czy powinna obsługiwać komunikatu oferowany.  
  
##  <a name="dtor"></a> ~ join 

 Niszczy `join` bloku.  
  
```
~join();
```  
  
##  <a name="link_target_notification"></a> link_target_notification 

 Wywołanie zwrotne, które informuje, że nowy element docelowy został powiązany to `join` bloku obsługi wiadomości.  
  
```
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```  
  
##  <a name="propagate_message"></a> propagate_message 

 Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `join` bloku obsługi wiadomości. Jest ono wywoływane przez `propagate` metody wywołanego bloku źródłowego.  
  
```
message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do `message` obiektu.  
  
 `_PSource`  
 Wskaźnik do bloku źródłowego oferty wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [message_status —](concurrency-namespace-enums.md) wskazanie docelowy korzystam z komunikatu.  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets 

 Tworzy dane wyjściowe wiadomość komunikat wejściowy z każdego źródła przy ich ma wszystkie propagacji wiadomości. Wysyła tę wiadomość dane wyjściowe do każdego z jego elementów docelowych.  
  
```
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
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

 Rezerwuje komunikat wcześniej oferowane przez to `join` bloku obsługi wiadomości.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z oferowany `message` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli komunikat został pomyślnie zarezerwowany, `false` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Po `reserve` jest wywoływana, jeśli zwróci ona `true`, albo `consume` lub `release` musi zostać wywołana albo lub zwolnij własność wiadomości.  
  
##  <a name="resume_propagation"></a> resume_propagation 

 Wznawia propagacji po zastrzeżenie został zwolniony.  
  
```
virtual void resume_propagation();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Klasa wyboru](choice-class.md)   
 [multitype_join, klasa](multitype-join-class.md)
