---
title: Klasa single_assignment | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- single_assignment
- AGENTS/concurrency::single_assignment
- AGENTS/concurrency::single_assignment::single_assignment
- AGENTS/concurrency::single_assignment::has_value
- AGENTS/concurrency::single_assignment::value
- AGENTS/concurrency::single_assignment::accept_message
- AGENTS/concurrency::single_assignment::consume_message
- AGENTS/concurrency::single_assignment::link_target_notification
- AGENTS/concurrency::single_assignment::propagate_message
- AGENTS/concurrency::single_assignment::propagate_to_any_targets
- AGENTS/concurrency::single_assignment::release_message
- AGENTS/concurrency::single_assignment::reserve_message
- AGENTS/concurrency::single_assignment::resume_propagation
- AGENTS/concurrency::single_assignment::send_message
dev_langs:
- C++
helpviewer_keywords:
- single_assignment class
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bacbdaa4af141101863b4d6d81d114d43aced9f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="singleassignment-class"></a>Klasa single_assignment
A `single_assignment` blok komunikatów jest wiele docelowych, wielu źródłach, uporządkowanych `propagator_block` można przechowywać jeden zapisu — po `message`.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ ładunku komunikatu przechowywane i propagowane przez bufor.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[single_assignment](#ctor)|Przeciążone. Konstruuje `single_assignment` bloku obsługi wiadomości.|  
|[~ single_assignment — destruktor](#dtor)|Niszczy `single_assignment` bloku obsługi wiadomości.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[has_value](#has_value)|Sprawdza, czy to `single_assignment` bloku komunikatów został zainicjowany z wartością jeszcze.|  
|[value](#value)|Pobiera odwołanie do bieżącego ładunku komunikatu są przechowywane w `single_assignment` bloku obsługi wiadomości.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Akceptuje wiadomość została przyjęta przez to `single_assignment` bloku obsługi wiadomości, zwracając kopia wiadomości do obiektu wywołującego.|  
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowane przez `single_assignment` i zastrzeżone przez element docelowy, zwracając kopia wiadomości do obiektu wywołującego.|  
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które informuje, że nowy element docelowy został powiązany to `single_assignment` bloku obsługi wiadomości.|  
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `single_assignment` bloku obsługi wiadomości. Jest ono wywoływane przez `propagate` metody wywołanego bloku źródłowego.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Miejsca `message _PMessage` w tym `single_assignment` wiadomości bloku i udostępnia go do wszystkich połączonych elementów docelowych.|  
|[release_message](#release_message)|Zwalnia Poprzednia rezerwacja wiadomości. (Przesłania [source_block::release_message](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowane przez to `single_assignment` bloku obsługi wiadomości. (Przesłania [source_block::reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Wznawia propagacji po zastrzeżenie został zwolniony. (Przesłania [source_block::resume_propagation](source-block-class.md#resume_propagation).)|  
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z `ISource` bloku do tego `single_assignment` bloku obsługi wiadomości. Jest ono wywoływane przez `send` metody wywołanego bloku źródłowego.|  
  
## <a name="remarks"></a>Uwagi  
 A `single_assignment` propaguje bloku komunikatów wychodzących kopie komunikatu do każdego obiektu docelowego.  
  
 Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [Isource —](isource-class.md)  
  
 [Itarget —](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `single_assignment`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="accept_message"></a> accept_message 

 Akceptuje wiadomość została przyjęta przez to `single_assignment` bloku obsługi wiadomości, zwracając kopia wiadomości do obiektu wywołującego.  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z oferowany `message` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiekt, aby wywołującego ma teraz własności.  
  
### <a name="remarks"></a>Uwagi  
 `single_assignment` Wiadomości bloku kopie zwraca komunikat do jego elementów docelowych, a nie przeniesieniem własności wiadomości przechowywanych obecnie.  
  
##  <a name="consume_message"></a> consume_message 

 Wykorzystuje komunikat wcześniej oferowane przez `single_assignment` i zastrzeżone przez element docelowy, zwracając kopia wiadomości do obiektu wywołującego.  
  
```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiektu są używane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiekt, aby wywołującego ma teraz własności.  
  
### <a name="remarks"></a>Uwagi  
 Podobnie jak `accept`, ale zawsze jest poprzedzony przez wywołanie `reserve`.  
  
##  <a name="has_value"></a> has_value 

 Sprawdza, czy to `single_assignment` bloku komunikatów został zainicjowany z wartością jeszcze.  
  
```
bool has_value() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli blok otrzymał wartość `false` inaczej.  
  
##  <a name="link_target_notification"></a> link_target_notification 

 Wywołanie zwrotne, które informuje, że nowy element docelowy został powiązany to `single_assignment` bloku obsługi wiadomości.  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do nowo połączonego obiektu docelowego.  
  
##  <a name="propagate_message"></a> propagate_message 

 Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `single_assignment` bloku obsługi wiadomości. Jest ono wywoływane przez `propagate` metody wywołanego bloku źródłowego.  
  
```
virtual message_status propagate_message(
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

 Miejsca `message` `_PMessage` w tym `single_assignment` wiadomości bloku i udostępnia go do wszystkich połączonych elementów docelowych.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do `message` tego `single_assignment` bloku komunikatów trwało własności.  
  
##  <a name="release_message"></a> release_message 

 Zwalnia Poprzednia rezerwacja wiadomości.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiekt został wydany.  
  
##  <a name="reserve_message"></a> reserve_message 

 Rezerwuje komunikat wcześniej oferowane przez to `single_assignment` bloku obsługi wiadomości.  
  
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

 Synchronicznie przekazuje komunikat z `ISource` bloku do tego `single_assignment` bloku obsługi wiadomości. Jest ono wywoływane przez `send` metody wywołanego bloku źródłowego.  
  
```
virtual message_status send_message(
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
  
##  <a name="ctor"></a> single_assignment 

 Konstruuje `single_assignment` bloku obsługi wiadomości.  
  
```
single_assignment();

single_assignment(
    filter_method const& _Filter);

single_assignment(
    Scheduler& _PScheduler);

single_assignment(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

single_assignment(
    ScheduleGroup& _PScheduleGroup);

single_assignment(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filter`  
 Funkcja filtru, który określa, czy oferowany wiadomości powinna być akceptowana.  
  
 `_PScheduler`  
 `Scheduler` Obiektu, w którym zadanie propagacji `single_assignment` zaplanowano bloku obsługi wiadomości.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Obiektu, w którym zadanie propagacji `single_assignment` zaplanowano bloku obsługi wiadomości. `Scheduler` Technicznego obiekt używany przez grupę harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.  
  
 Typ `filter_method` jest obiekt podpisem `bool (T const &)` który jest wywoływany przez to `single_assignment` obsługi komunikatów bloku, aby ustalić, czy powinna obsługiwać komunikatu oferowany.  
  
##  <a name="dtor"></a> ~ single_assignment 

 Niszczy `single_assignment` bloku obsługi wiadomości.  
  
```
~single_assignment();
```  
  
##  <a name="value"></a> Wartość 

 Pobiera odwołanie do bieżącego ładunku komunikatu są przechowywane w `single_assignment` bloku obsługi wiadomości.  
  
```
T const& value();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obciążenie komunikatu przechowywane.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda będzie czekać, aż do nadejścia wiadomości, jeśli komunikat nie są obecnie przechowywane w `single_assignment` bloku obsługi wiadomości.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Klasa overwrite_buffer](overwrite-buffer-class.md)   
 [Klasa unbounded_buffer](unbounded-buffer-class.md)

