---
title: Klasa overwrite_buffer | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- overwrite_buffer
- AGENTS/concurrency::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::has_value
- AGENTS/concurrency::overwrite_buffer::value
- AGENTS/concurrency::overwrite_buffer::accept_message
- AGENTS/concurrency::overwrite_buffer::consume_message
- AGENTS/concurrency::overwrite_buffer::link_target_notification
- AGENTS/concurrency::overwrite_buffer::propagate_message
- AGENTS/concurrency::overwrite_buffer::propagate_to_any_targets
- AGENTS/concurrency::overwrite_buffer::release_message
- AGENTS/concurrency::overwrite_buffer::reserve_message
- AGENTS/concurrency::overwrite_buffer::resume_propagation
- AGENTS/concurrency::overwrite_buffer::send_message
- AGENTS/concurrency::overwrite_buffer::supports_anonymous_source
dev_langs:
- C++
helpviewer_keywords:
- overwrite_buffer class
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dccde651898bf5ff0986dc2e577a1d2ee5765e3f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="overwritebuffer-class"></a>Klasa overwrite_buffer
`overwrite_buffer` Blok komunikatów jest wiele docelowych, wielu źródłach, uporządkowanych `propagator_block` można przechowywać w czasie pojedynczym komunikacie. Nowe komunikaty zastąpienie wcześniej przechowywanych z nich.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Rodzaj ładunku komunikaty przechowywane i propagowane przez bufor.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[overwrite_buffer](#ctor)|Przeciążone. Konstruuje `overwrite_buffer` bloku obsługi wiadomości.|  
|[~overwrite_buffer Destructor](#dtor)|Niszczy `overwrite_buffer` bloku obsługi wiadomości.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[has_value](#has_value)|Sprawdza, czy to `overwrite_buffer` bloku obsługi wiadomości nie został jeszcze wartość.|  
|[value](#value)|Pobiera odwołanie do bieżącego ładunku komunikatu są przechowywane w `overwrite_buffer` bloku obsługi wiadomości.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Akceptuje wiadomość została przyjęta przez to `overwrite_buffer` bloku obsługi wiadomości, zwracając kopia wiadomości do obiektu wywołującego.|  
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowane przez `overwrite_buffer` wiadomości bloku oraz zastrzeżone przez element docelowy, zwracając kopia wiadomości do obiektu wywołującego.|  
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które informuje, że nowy element docelowy został powiązany to `overwrite_buffer` bloku obsługi wiadomości.|  
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `overwrite_buffer` bloku obsługi wiadomości. Jest ono wywoływane przez `propagate` metody wywołanego bloku źródłowego.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Miejsca `message _PMessage` w tym `overwrite_buffer` wiadomości bloku i udostępnia go do wszystkich połączonych elementów docelowych.|  
|[release_message](#release_message)|Zwalnia Poprzednia rezerwacja wiadomości. (Przesłania [source_block::release_message](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowane przez to `overwrite_buffer` bloku obsługi wiadomości. (Przesłania [source_block::reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Wznawia propagacji po zastrzeżenie został zwolniony. (Przesłania [source_block::resume_propagation](source-block-class.md#resume_propagation).)|  
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z `ISource` bloku do tego `overwrite_buffer` bloku obsługi wiadomości. Jest ono wywoływane przez `send` metody wywołanego bloku źródłowego.|  
|[supports_anonymous_source](#supports_anonymous_source)|Zastępuje `supports_anonymous_source` metody, aby wskazać, że ten blok może akceptować komunikaty oferowane przez źródło, który nie jest połączony. (Przesłania [ITarget::supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|  
  
## <a name="remarks"></a>Uwagi  
 `overwrite_buffer` Propaguje bloku komunikatów wychodzących kopie komunikatu przechowywanych dla każdego z jego elementów docelowych.  
  
 Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [Isource —](isource-class.md)  
  
 [Itarget —](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `overwrite_buffer`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="accept_message"></a> accept_message 

 Akceptuje wiadomość została przyjęta przez to `overwrite_buffer` bloku obsługi wiadomości, zwracając kopia wiadomości do obiektu wywołującego.  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z oferowany `message` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiekt, aby wywołującego ma teraz własności.  
  
### <a name="remarks"></a>Uwagi  
 `overwrite_buffer` Wiadomości bloku kopie zwraca komunikat do jego elementów docelowych, a nie przeniesieniem własności wiadomości przechowywanych obecnie.  
  
##  <a name="consume_message"></a> consume_message 

 Wykorzystuje komunikat wcześniej oferowane przez `overwrite_buffer` wiadomości bloku oraz zastrzeżone przez element docelowy, zwracając kopia wiadomości do obiektu wywołującego.  
  
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

 Sprawdza, czy to `overwrite_buffer` bloku obsługi wiadomości nie został jeszcze wartość.  
  
```
bool has_value() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli blok otrzymał wartość `false` inaczej.  
  
##  <a name="link_target_notification"></a> link_target_notification 

 Wywołanie zwrotne, które informuje, że nowy element docelowy został powiązany to `overwrite_buffer` bloku obsługi wiadomości.  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do nowo połączonego obiektu docelowego.  
  
##  <a name="dtor"></a> ~overwrite_buffer 

 Niszczy `overwrite_buffer` bloku obsługi wiadomości.  
  
```
~overwrite_buffer();
```  
  
##  <a name="ctor"></a> overwrite_buffer 

 Konstruuje `overwrite_buffer` bloku obsługi wiadomości.  
  
```
overwrite_buffer();

overwrite_buffer(
    filter_method const& _Filter);

overwrite_buffer(
    Scheduler& _PScheduler);

overwrite_buffer(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filter`  
 Funkcja filtru, który określa, czy oferowany wiadomości powinna być akceptowana.  
  
 `_PScheduler`  
 `Scheduler` Obiektu, w którym zadanie propagacji `overwrite_buffer` zaplanowano bloku obsługi wiadomości.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Obiektu, w którym zadanie propagacji `overwrite_buffer` zaplanowano bloku obsługi wiadomości. `Scheduler` Technicznego obiekt używany przez grupę harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.  
  
 Typ `filter_method` jest obiekt podpisem `bool (T const &)` który jest wywoływany przez to `overwrite_buffer` obsługi komunikatów bloku, aby ustalić, czy powinna obsługiwać komunikatu oferowany.  
  
##  <a name="propagate_message"></a> propagate_message 

 Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `overwrite_buffer` bloku obsługi wiadomości. Jest ono wywoływane przez `propagate` metody wywołanego bloku źródłowego.  
  
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

 Miejsca `message _PMessage` w tym `overwrite_buffer` wiadomości bloku i udostępnia go do wszystkich połączonych elementów docelowych.  
  
```
virtual void propagate_to_any_targets(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do `message` obiektu tego `overwrite_buffer` trwało własności.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje do bieżącej wiadomości w `overwrite_buffer` z nowo odebrane wiadomości `_PMessage`.  
  
##  <a name="send_message"></a> send_message 

 Synchronicznie przekazuje komunikat z `ISource` bloku do tego `overwrite_buffer` bloku obsługi wiadomości. Jest ono wywoływane przez `send` metody wywołanego bloku źródłowego.  
  
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
  
##  <a name="supports_anonymous_source"></a> supports_anonymous_source 

 Zastępuje `supports_anonymous_source` metody, aby wskazać, że ten blok może akceptować komunikaty oferowane przez źródło, który nie jest połączony.  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` ponieważ bloku nie odłożyć oferowane wiadomości.  
  
##  <a name="release_message"></a> release_message 

 Zwalnia Poprzednia rezerwacja wiadomości.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiekt został wydany.  
  
##  <a name="reserve_message"></a> reserve_message 

 Rezerwuje komunikat wcześniej oferowane przez to `overwrite_buffer` bloku obsługi wiadomości.  
  
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
  
##  <a name="value"></a> Wartość 

 Pobiera odwołanie do bieżącego ładunku komunikatu są przechowywane w `overwrite_buffer` bloku obsługi wiadomości.  
  
```
T value();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obciążenie komunikatu aktualnie przechowywana.  
  
### <a name="remarks"></a>Uwagi  
 Wartość przechowywana we `overwrite_buffer` można zmienić natychmiast po powrocie z tej metody. Ta metoda będzie czekać, aż do nadejścia wiadomości, jeśli komunikat nie są obecnie przechowywane w `overwrite_buffer`.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Klasa unbounded_buffer](unbounded-buffer-class.md)   
 [single_assignment, klasa](single-assignment-class.md)
