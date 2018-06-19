---
title: Klasa czasomierza | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- timer
- AGENTS/concurrency::timer
- AGENTS/concurrency::timer::timer
- AGENTS/concurrency::timer::pause
- AGENTS/concurrency::timer::start
- AGENTS/concurrency::timer::stop
- AGENTS/concurrency::timer::accept_message
- AGENTS/concurrency::timer::consume_message
- AGENTS/concurrency::timer::link_target_notification
- AGENTS/concurrency::timer::propagate_to_any_targets
- AGENTS/concurrency::timer::release_message
- AGENTS/concurrency::timer::reserve_message
- AGENTS/concurrency::timer::resume_propagation
dev_langs:
- C++
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8372e32b408b97a6ac652b0ff2ff5cc19de69b54
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693227"
---
# <a name="timer-class"></a>Klasa czasomierza
A `timer` Blok obsługi wiadomości jest element docelowy jednym `source_block` mogą wysyłać wiadomości do jego obiektu docelowego po określonym okresie czasu lub w określonych odstępach czasu.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ ładunku komunikaty z tego bloku.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Czasomierz](#ctor)|Przeciążone. Konstruuje `timer` wiadomości blok, którego zostanie zastosowana danej wiadomości po upływie określonego czasu.|  
|[~ timer — destruktor](#dtor)|Niszczy `timer` bloku obsługi wiadomości.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Wstrzymaj](#pause)|Zatrzymuje `timer` bloku obsługi wiadomości. Jeśli jest powtarzanej `timer` wiadomości bloku, ponownym uruchomieniem przy kolejnej `start()` wywołania. Powtarzalnych czasomierze, ma ten sam efekt co `stop` wywołania.|  
|[start](#start)|Uruchamia `timer` bloku obsługi wiadomości. Nazywa się określoną liczbę milisekund, po to, określona wartość będzie propagowane podrzędne jako `message`.|  
|[Zatrzymaj](#stop)|Zatrzymuje `timer` bloku obsługi wiadomości.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Akceptuje wiadomość została przyjęta przez to `timer` bloku obsługi wiadomości, przeniesieniem własności do obiektu wywołującego.|  
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowane przez `timer` i zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.|  
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które informuje, że nowy element docelowy został powiązany to `timer` bloku obsługi wiadomości.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Zaoferować komunikat utworzonego przez `timer` bloku do wszystkich połączonych elementów docelowych.|  
|[release_message](#release_message)|Zwalnia Poprzednia rezerwacja wiadomości. (Przesłania [source_block::release_message](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowane przez to `timer` bloku obsługi wiadomości. (Przesłania [source_block::reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Wznawia propagacji po zastrzeżenie został zwolniony. (Przesłania [source_block::resume_propagation](source-block-class.md#resume_propagation).)|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [Isource —](isource-class.md)  
  
 [source_block](source-block-class.md)  
  
 `timer`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="accept_message"></a> accept_message 

 Akceptuje wiadomość została przyjęta przez to `timer` bloku obsługi wiadomości, przeniesieniem własności do obiektu wywołującego.  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z oferowany `message` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiekt, aby wywołującego ma teraz własności.  
  
##  <a name="consume_message"></a> consume_message 

 Wykorzystuje komunikat wcześniej oferowane przez `timer` i zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.  
  
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
  
##  <a name="link_target_notification"></a> link_target_notification 

 Wywołanie zwrotne, które informuje, że nowy element docelowy został powiązany to `timer` bloku obsługi wiadomości.  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do nowo połączonego obiektu docelowego.  
  
##  <a name="pause"></a> Wstrzymaj 

 Zatrzymuje `timer` bloku obsługi wiadomości. Jeśli jest powtarzanej `timer` wiadomości bloku, ponownym uruchomieniem przy kolejnej `start()` wywołania. Powtarzalnych czasomierze, ma ten sam efekt co `stop` wywołania.  
  
```
void pause();
```  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets 

 Zaoferować komunikat utworzonego przez `timer` bloku do wszystkich połączonych elementów docelowych.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
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

 Rezerwuje komunikat wcześniej oferowane przez to `timer` bloku obsługi wiadomości.  
  
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
  
##  <a name="start"></a> Początek 

 Uruchamia `timer` bloku obsługi wiadomości. Nazywa się określoną liczbę milisekund, po to, określona wartość będzie propagowane podrzędne jako `message`.  
  
```
void start();
```  
  
##  <a name="stop"></a> Zatrzymaj 

 Zatrzymuje `timer` bloku obsługi wiadomości.  
  
```
void stop();
```  
  
##  <a name="ctor"></a> Czasomierz 

 Konstruuje `timer` wiadomości blok, którego zostanie zastosowana danej wiadomości po upływie określonego czasu.  
  
```
timer(
    unsigned int _Ms,
    T const& value,
    ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    Scheduler& _Scheduler,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    ScheduleGroup& _ScheduleGroup,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ms`  
 Liczba milisekund, które muszą upłynąć od wywołania można uruchomić dla określonego komunikatu propagację poniżej.  
  
 `value`  
 Wartość, która będzie propagowane downstream po upływie czasomierza.  
  
 `_PTarget`  
 Obiekt docelowy, do którego czasomierza rozpropaguje komunikatu.  
  
 `_Repeating`  
 Wartość true wskazuje, czy czasomierz będzie okresowo wyzwalać co `_Ms` milisekund.  
  
 `_Scheduler`  
 `Scheduler` Obiektu, w którym zadanie propagacji `timer` zaplanowano bloku komunikatów zostało zaplanowane.  
  
 `_ScheduleGroup`  
 `ScheduleGroup` Obiektu, w którym zadanie propagacji `timer` zaplanowano bloku obsługi wiadomości. `Scheduler` Technicznego obiekt używany przez grupę harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz `_Scheduler` lub `_ScheduleGroup` parametrów.  
  
##  <a name="dtor"></a> ~ czasomierza 

 Niszczy `timer` bloku obsługi wiadomości.  
  
```
~timer();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
