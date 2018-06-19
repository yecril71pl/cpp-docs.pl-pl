---
title: source_block — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- source_block
- AGENTS/concurrency::source_block
- AGENTS/concurrency::source_block::source_block
- AGENTS/concurrency::source_block::accept
- AGENTS/concurrency::source_block::acquire_ref
- AGENTS/concurrency::source_block::consume
- AGENTS/concurrency::source_block::link_target
- AGENTS/concurrency::source_block::release
- AGENTS/concurrency::source_block::release_ref
- AGENTS/concurrency::source_block::reserve
- AGENTS/concurrency::source_block::unlink_target
- AGENTS/concurrency::source_block::unlink_targets
- AGENTS/concurrency::source_block::accept_message
- AGENTS/concurrency::source_block::async_send
- AGENTS/concurrency::source_block::consume_message
- AGENTS/concurrency::source_block::enable_batched_processing
- AGENTS/concurrency::source_block::initialize_source
- AGENTS/concurrency::source_block::link_target_notification
- AGENTS/concurrency::source_block::process_input_messages
- AGENTS/concurrency::source_block::propagate_output_messages
- AGENTS/concurrency::source_block::propagate_to_any_targets
- AGENTS/concurrency::source_block::release_message
- AGENTS/concurrency::source_block::remove_targets
- AGENTS/concurrency::source_block::reserve_message
- AGENTS/concurrency::source_block::resume_propagation
- AGENTS/concurrency::source_block::sync_send
- AGENTS/concurrency::source_block::unlink_target_notification
- AGENTS/concurrency::source_block::wait_for_outstanding_async_sends
dev_langs:
- C++
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64b9873ef6da00b4ef0fb03e43f61fa704484389
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694966"
---
# <a name="sourceblock-class"></a>source_block — Klasa
`source_block` Klasa jest abstrakcyjna klasa podstawowa dla bloków tylko do źródła. Ta klasa dostarcza łącze podstawowe funkcje zarządzania jako również jako wspólne sprawdzanie błędów.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```  
  
#### <a name="parameters"></a>Parametry  
 `_TargetLinkRegistry`  
 Łącze rejestru służący do przechowywania łącza docelowego.  
  
 `_MessageProcessorType`  
 Typ procesora do przetwarzania komunikatów.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`target_iterator`|Iterator przeprowadzenie połączonych elementów docelowych.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[source_block](#ctor)|Konstruuje `source_block` obiektu.|  
|[~ source_block — destruktor](#dtor)|Niszczy `source_block` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Zaakceptuj](#accept)|Akceptuje wiadomość została przyjęta przez to `source_block` obiektu przeniesieniem własności do obiektu wywołującego.|  
|[acquire_ref](#acquire_ref)|Uzyskuje liczebności referencyjnej na tym `source_block` obiekt, aby zapobiec usunięciu.|  
|[Korzystać z](#consume)|Wykorzystuje komunikat wcześniej oferowane przez to `source_block` obiektu i pomyślnie zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.|  
|[link_target](#link_target)|Łącza do tego bloku docelowego `source_block` obiektu.|  
|[Zlecenia](#release)|Zwalnia Poprzednia rezerwacja wiadomości powiodło się.|  
|[release_ref](#release_ref)|Zwalnia liczebności referencyjnej na tym `source_block` obiektu.|  
|[reserve](#reserve)|Rezerwuje komunikat wcześniej oferowane przez to `source_block` obiektu.|  
|[unlink_target](#unlink_target)|Odłączenie od tego bloku docelowego `source_block` obiektu.|  
|[unlink_targets](#unlink_targets)|Odłączenie wszystkich bloków docelowej tego `source_block` obiektu. (Przesłania [ISource::unlink_targets](isource-class.md#unlink_targets).)|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[accept_message](#accept_message)|W przypadku przesłonięcia w klasie pochodnej, akceptuje komunikat oferowane przez źródło. Bloki komunikatów powinny przesłaniać tę metodę do sprawdzania poprawności `_MsgId` i zwraca komunikat.|  
|[async_send](#async_send)|Asynchronicznie kolejki zapasowych wiadomości i uruchamia zadanie propagacji, jeśli to nie wykonano już|  
|[consume_message](#consume_message)|W przypadku przesłonięcia w klasie pochodnej, zużywa komunikat, który wcześniej został zarezerwowany.|  
|[enable_batched_processing](#enable_batched_processing)|Włącza umieścić w zadaniu wsadowym przetwarzania dla tego bloku.|  
|[initialize_source](#initialize_source)|Inicjuje `message_propagator` w ramach tego `source_block`.|  
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które informuje, że nowy element docelowy został powiązany to `source_block` obiektu.|  
|[process_input_messages](#process_input_messages)|Przetwarzanie komunikatów wejściowych. Ta opcja jest przydatna dla bloków propagator, które wynikają z source_block —|  
|[propagate_output_messages](#propagate_output_messages)|Propagacja komunikatów do obiektów docelowych.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|W przypadku przesłonięcia w klasie pochodnej, propaguje tego komunikatu do dowolnego lub wszystkich połączonych elementów docelowych. Jest to procedura propagacji głównego dla bloków komunikatów.|  
|[release_message](#release_message)|W przypadku przesłonięcia w klasie pochodnej, zwalnia Poprzednia rezerwacja wiadomości.|  
|[remove_targets](#remove_targets)|Usuwa wszystkie linki docelowego dla tego bloku źródła. Ta powinna być wywoływana ze destruktor.|  
|[reserve_message](#reserve_message)|W przypadku przesłonięcia w klasie pochodnej, rezerwuje komunikat wcześniej oferowane przez to `source_block` obiektu.|  
|[resume_propagation](#resume_propagation)|W przypadku przesłonięcia w klasie pochodnej, wznawia propagacji po zastrzeżenie został zwolniony.|  
|[sync_send](#sync_send)|Synchronicznie kolejki zapasowych wiadomości i uruchamia zadanie propagacji, jeśli to nie już zostało wykonane.|  
|[unlink_target_notification](#unlink_target_notification)|Wywołanie zwrotne, które informuje, że element docelowy zostało odłączone od to `source_block` obiektu.|  
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|Czeka na wszystkich propagacji asynchroniczne zakończyć. Tego oczekiwania specyficzne dla propagator pokrętła jest używany podczas destruktory bloki komunikatów do upewnij się, że wszystkie propagacji asynchroniczne czasu, aby zakończyć działanie przed niszczenie bloku.|  
  
## <a name="remarks"></a>Uwagi  
 Bloki komunikatów powinien pochodzić z tego bloku, aby skorzystać z łącza zarządzania i synchronizacji udostępniane przez tę klasę.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [Isource —](isource-class.md)  
  
 `source_block`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="accept"></a> Zaakceptuj 

 Akceptuje wiadomość została przyjęta przez to `source_block` obiektu przeniesieniem własności do obiektu wywołującego.  
  
```
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z oferowany `message` obiektu.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który wywołuje `accept` metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiekt, aby wywołującego ma teraz własności.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątek Jeśli parametr `_PTarget` jest `NULL`.  
  
 `accept` Metoda jest wywoływana przez element docelowy, gdy komunikat jest oferowany przez to `ISource` bloku. Wskaźnik komunikat zwrócony mogą być inne niż ten, który został przekazany do `propagate` metody `ITarget` zablokować, jeśli to źródło postanawia kopia wiadomości.  
  
##  <a name="accept_message"></a> accept_message 

 W przypadku przesłonięcia w klasie pochodnej, akceptuje komunikat oferowane przez źródło. Bloki komunikatów powinny przesłaniać tę metodę do sprawdzania poprawności `_MsgId` i zwraca komunikat.  
  
```
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 Tożsamość obiektu środowiska wykonawczego `message` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do wywołującego ma teraz własność komunikat.  
  
### <a name="remarks"></a>Uwagi  
 Aby przetransferować własność, powinny być zwracane wskaźnik oryginalnej wiadomości. Aby zachować prawa własności, kopię ładunek komunikatu musi się i zwrócony.  
  
##  <a name="acquire_ref"></a> acquire_ref 

 Uzyskuje liczebności referencyjnej na tym `source_block` obiekt, aby zapobiec usunięciu.  
  
```
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez `ITarget` obiekt, który jest połączone z tym źródłem podczas `link_target` metody.  
  
##  <a name="async_send"></a> async_send 

 Asynchronicznie kolejki zapasowych wiadomości i uruchamia zadanie propagacji, jeśli to nie wykonano już  
  
```
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```  
  
### <a name="parameters"></a>Parametry  
 `_Msg`  
 Wskaźnik do `message` obiektu do wysłania asynchronicznie.  
  
##  <a name="consume"></a> Korzystać z 

 Wykorzystuje komunikat wcześniej oferowane przez to `source_block` obiektu i pomyślnie zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.  
  
```
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z zarezerwowanego `message` obiektu.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który wywołuje `consume` metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiekt, aby wywołującego ma teraz własności.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątek Jeśli parametr `_PTarget` jest `NULL`.  
  
 Metoda zgłasza [bad_target —](bad-target-class.md) wyjątek Jeśli parametr `_PTarget` nie reprezentuje element docelowy, który wywołał `reserve`.  
  
 `consume` Metoda jest podobna do `accept`, ale zawsze musi być poprzedzony przez wywołanie do `reserve` zwróconą `true`.  
  
##  <a name="consume_message"></a> consume_message 

 W przypadku przesłonięcia w klasie pochodnej, zużywa komunikat, który wcześniej został zarezerwowany.  
  
```
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiektu są używane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do wywołującego ma teraz własność komunikat.  
  
### <a name="remarks"></a>Uwagi  
 Podobnie jak `accept`, ale zawsze jest poprzedzony przez wywołanie `reserve`.  
  
##  <a name="enable_batched_processing"></a> enable_batched_processing 

 Włącza umieścić w zadaniu wsadowym przetwarzania dla tego bloku.  
  
```
void enable_batched_processing();
```  
  
##  <a name="initialize_source"></a> initialize_source 

 Inicjuje `message_propagator` w ramach tego `source_block`.  
  
```
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `_PScheduler`  
 Harmonogram, który ma służyć do planowania zadań.  
  
 `_PScheduleGroup`  
 Grupa harmonogram, który ma być używana do planowania zadań.  
  
##  <a name="link_target"></a> link_target 

 Łącza do tego bloku docelowego `source_block` obiektu.  
  
```
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do `ITarget` bloku, aby połączyć się z: `source_block` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątek Jeśli parametr `_PTarget` jest `NULL`.  
  
##  <a name="link_target_notification"></a> link_target_notification 

 Wywołanie zwrotne, które informuje, że nowy element docelowy został powiązany to `source_block` obiektu.  
  
```
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```  
  
##  <a name="process_input_messages"></a> process_input_messages 

 Przetwarzanie komunikatów wejściowych. Ta opcja jest przydatna dla bloków propagator, które wynikają z source_block —  
  
```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
  
##  <a name="propagate_output_messages"></a> propagate_output_messages 

 Propagacja komunikatów do obiektów docelowych.  
  
```
virtual void propagate_output_messages();
```  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets 

 W przypadku przesłonięcia w klasie pochodnej, propaguje tego komunikatu do dowolnego lub wszystkich połączonych elementów docelowych. Jest to procedura propagacji głównego dla bloków komunikatów.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do elementu, który ma być propagowane.  
  
##  <a name="release"></a> Zlecenia 

 Zwalnia Poprzednia rezerwacja wiadomości powiodło się.  
  
```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z zarezerwowanego `message` obiektu.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który wywołuje `release` metody.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątek Jeśli parametr `_PTarget` jest `NULL`.  
  
 Metoda zgłasza [bad_target —](bad-target-class.md) wyjątek Jeśli parametr `_PTarget` nie reprezentuje element docelowy, który wywołał `reserve`.  
  
##  <a name="release_message"></a> release_message 

 W przypadku przesłonięcia w klasie pochodnej, zwalnia Poprzednia rezerwacja wiadomości.  
  
```
virtual void release_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiekt został wydany.  
  
##  <a name="release_ref"></a> release_ref 

 Zwalnia liczebności referencyjnej na tym `source_block` obiektu.  
  
```
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który jest wywołaniem tej metody.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez `ITarget` obiekt, który jest jest rozłączony z tego źródła. Blok źródła może zwolnić wszystkie zasoby zarezerwowane dla blok docelowy.  
  
##  <a name="remove_targets"></a> remove_targets 

 Usuwa wszystkie linki docelowego dla tego bloku źródła. Ta powinna być wywoływana ze destruktor.  
  
```
void remove_targets();
```  
  
##  <a name="reserve"></a> rezerwowa 

 Rezerwuje komunikat wcześniej oferowane przez to `source_block` obiektu.  
  
```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z oferowany `message` obiektu.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który wywołuje `reserve` metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli komunikat został pomyślnie zarezerwowany, `false` inaczej. Zastrzeżenia może zakończyć się niepowodzeniem dla wielu powodów, takich jak: wiadomość już została zastrzeżone lub zaakceptowane przez inny element docelowy, źródła można odmówić zastrzeżenia i tak dalej.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątek Jeśli parametr `_PTarget` jest `NULL`.  
  
 Po wywołaniu metody `reserve`, jeśli próba powiedzie się, należy wywołać albo `consume` lub `release` Aby przejąć lub zrezygnować posiadania wiadomości, odpowiednio.  
  
##  <a name="reserve_message"></a> reserve_message 

 W przypadku przesłonięcia w klasie pochodnej, rezerwuje komunikat wcześniej oferowane przez to `source_block` obiektu.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiektu pozostaje zarezerwowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli komunikat został pomyślnie zarezerwowany, `false` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Po `reserve` jest wywoływana, jeśli zwróci ona `true`, albo `consume` lub `release` musi zostać wywołana albo lub zwolnij własność wiadomości.  
  
##  <a name="resume_propagation"></a> resume_propagation 

 W przypadku przesłonięcia w klasie pochodnej, wznawia propagacji po zastrzeżenie został zwolniony.  
  
```
virtual void resume_propagation() = 0;
```  
  
##  <a name="ctor"></a> source_block — 

 Konstruuje `source_block` obiektu.  
  
```
source_block();
```  
  
##  <a name="dtor"></a> ~ source_block — 

 Niszczy `source_block` obiektu.  
  
```
virtual ~source_block();
```  
  
##  <a name="sync_send"></a> sync_send 

 Synchronicznie kolejki zapasowych wiadomości i uruchamia zadanie propagacji, jeśli to nie już zostało wykonane.  
  
```
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```  
  
### <a name="parameters"></a>Parametry  
 `_Msg`  
 Wskaźnik do `message` obiektu do wysłania synchronicznie.  
  
##  <a name="unlink_target"></a> unlink_target 

 Odłączenie od tego bloku docelowego `source_block` obiektu.  
  
```
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do `ITarget` bloku, aby odłączyć od tego `source_block` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątek Jeśli parametr `_PTarget` jest `NULL`.  
  
##  <a name="unlink_target_notification"></a> unlink_target_notification 

 Wywołanie zwrotne, które informuje, że element docelowy zostało odłączone od to `source_block` obiektu.  
  
```
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 `ITarget` Bloku, które zostało odłączone.  
  
##  <a name="unlink_targets"></a> unlink_targets 

 Odłączenie wszystkich bloków docelowej tego `source_block` obiektu.  
  
```
virtual void unlink_targets();
```  
  
##  <a name="wait_for_outstanding_async_sends"></a> wait_for_outstanding_async_sends 

 Czeka na wszystkich propagacji asynchroniczne zakończyć. Tego oczekiwania specyficzne dla propagator pokrętła jest używany podczas destruktory bloki komunikatów do upewnij się, że wszystkie propagacji asynchroniczne czasu, aby zakończyć działanie przed niszczenie bloku.  
  
```
void wait_for_outstanding_async_sends();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [ISource, klasa](isource-class.md)
