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
ms.openlocfilehash: 46073d07cbca27256ca169ab94e0fe027bf98b15
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118859"
---
# <a name="join-class"></a>join — Klasa
A `join` blok komunikatów jest docelowy pojedynczego wielu źródeł, uporządkowanych `propagator_block` które łączy ze sobą komunikaty typu `T` z każdej z jej źródła.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```   
  
#### <a name="parameters"></a>Parametry  
*T*<br/>
Typ ładunku komunikatów przyłączone i rozprowadzane przez blok.  
  
*_Jtype*<br/>
Rodzaj elementu `join` bloku jest, albo `greedy` lub `non_greedy`  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[join](#ctor)|Przeciążone. Konstruuje `join` Blok obsługi wiadomości.|  
|[~ join — destruktor](#dtor)|Niszczy `join` bloku.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Akceptuje wiadomości, które było oferowane przez to `join` Blok obsługi wiadomości, transfer praw własności do obiektu wywołującego.|  
|[consume_message](#consume_message)|Wykorzystuje komunikat, który został poprzednio oferowana przez `join` bloku komunikatów i zastrzeżona przez element docelowy przenoszenia własności do obiektu wywołującego.|  
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które informuje, że nowy obiekt docelowy została połączona z tym `join` Blok obsługi wiadomości.|  
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `join` Blok obsługi wiadomości. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Tworzy komunikat wyjściowy zawierający komunikat wejściowy z każdego źródła po ich wykonaniu wszystkich propagacji wiadomość. Wysyła wiadomość dane wyjściowe do każdego z jego elementów docelowych.|  
|[release_message](#release_message)|Zwalnia poprzedniej wiadomości rezerwacji. (Przesłania [source_block::release_message —](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Zarezerwowaniu wiadomości przez oferowane wcześniej to `join` Blok obsługi wiadomości. (Przesłania [source_block::reserve_message —](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Wznawia działanie propagacji, po udostępnieniu rezerwacji. (Przesłania [source_block::resume_propagation —](source-block-class.md#resume_propagation).)|  
  
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

 Akceptuje wiadomości, które było oferowane przez to `join` Blok obsługi wiadomości, transfer praw własności do obiektu wywołującego.  
  
```
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z oferowane `message` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiektu, że obiekt wywołujący ma teraz własności.  
  
##  <a name="consume_message"></a> consume_message 

 Wykorzystuje komunikat, który został poprzednio oferowana przez `join` bloku komunikatów i zastrzeżona przez element docelowy przenoszenia własności do obiektu wywołującego.  
  
```
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu są używane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiektu, że obiekt wywołujący ma teraz własności.  
  
### <a name="remarks"></a>Uwagi  
 Podobnie jak `accept`, ale zawsze jest poprzedzony przez wywołanie `reserve`.  
  
##  <a name="ctor"></a> sprzężenia 

 Konstruuje `join` Blok obsługi wiadomości.  
  
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
*_NumInputs*<br/>
Liczba danych wejściowych to `join` bloku będzie możliwe.  
  
*_Filtruj*<br/>
Funkcja filtrowania, określający, czy powinna być akceptowana oferowane wiadomości.  
  
*_PScheduler*<br/>
`Scheduler` Obiekt, w którym zadanie propagacji dla `join` zaplanowano Blok obsługi wiadomości.  
  
*_PScheduleGroup*<br/>
`ScheduleGroup` Obiekt, w którym zadanie propagacji dla `join` zaplanowano Blok obsługi wiadomości. `Scheduler` Obiekt używany jest implikowany przez grupę harmonogramów.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko wykonawcze używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.  
  
 Typ `filter_method` jest funktor za pomocą podpisu `bool (T const &)` który zostanie wywołany przez to `join` Blok obsługi wiadomości, aby ustalić, czy nie powinien akceptować wiadomości oferowane.  
  
##  <a name="dtor"></a> ~ join 

 Niszczy `join` bloku.  
  
```
~join();
```  
  
##  <a name="link_target_notification"></a> link_target_notification — 

 Wywołanie zwrotne, które informuje, że nowy obiekt docelowy została połączona z tym `join` Blok obsługi wiadomości.  
  
```
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```  
  
##  <a name="propagate_message"></a> propagate_message 

 Asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `join` Blok obsługi wiadomości. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.  
  
```
message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
*_PMessage*<br/>
Wskaźnik do `message` obiektu.  
  
*_PSource*<br/>
Wskaźnik do blok źródłowy oferty wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [message_status —](concurrency-namespace-enums.md) sygnał docelowy postanowiła zrobić z komunikatem.  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets 

 Tworzy komunikat wyjściowy zawierający komunikat wejściowy z każdego źródła po ich wykonaniu wszystkich propagacji wiadomość. Wysyła wiadomość dane wyjściowe do każdego z jego elementów docelowych.  
  
```
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
```  
  
##  <a name="release_message"></a> release_message 

 Zwalnia poprzedniej wiadomości rezerwacji.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu, zostały udostępnione.  
  
##  <a name="reserve_message"></a> reserve_message 

 Zarezerwowaniu wiadomości przez oferowane wcześniej to `join` Blok obsługi wiadomości.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z oferowane `message` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli komunikat został pomyślnie zarezerwowany, `false` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Po `reserve` jest wywoływana, jeśli zwróci ona `true`, albo `consume` lub `release` musi zostać wywołana wersji własności wiadomości lub wykonać.  
  
##  <a name="resume_propagation"></a> resume_propagation 

 Wznawia działanie propagacji, po udostępnieniu rezerwacji.  
  
```
virtual void resume_propagation();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [choice, klasa](choice-class.md)   
 [multitype_join, klasa](multitype-join-class.md)
