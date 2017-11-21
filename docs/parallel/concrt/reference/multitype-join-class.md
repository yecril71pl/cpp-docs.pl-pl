---
title: "multitype_join — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- multitype_join
- AGENTS/concurrency::multitype_join
- AGENTS/concurrency::multitype_join::multitype_join
- AGENTS/concurrency::multitype_join::accept
- AGENTS/concurrency::multitype_join::acquire_ref
- AGENTS/concurrency::multitype_join::consume
- AGENTS/concurrency::multitype_join::link_target
- AGENTS/concurrency::multitype_join::release
- AGENTS/concurrency::multitype_join::release_ref
- AGENTS/concurrency::multitype_join::reserve
- AGENTS/concurrency::multitype_join::unlink_target
- AGENTS/concurrency::multitype_join::unlink_targets
dev_langs: C++
helpviewer_keywords: multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a53206c32b59ab5cac9f14d51bed42a4870b94fa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="multitypejoin-class"></a>multitype_join — Klasa
A `multitype_join` bloku komunikatów to wielu źródłach, jednego docelowego blok komunikatów łączy ze sobą wiadomości o różnych typach z każdego z jego źródła i oferuje krotka Scalonej wiadomości do jego elementów docelowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<
    typename T,  
    join_type _Jtype = non_greedy  
>  
class multitype_join: public ISource<typename _Unwrap<T>::type>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 `tuple` Typ ładunku komunikatów przyłączone i propagowane przez bloku.  
  
 `_Jtype`  
 Rodzaj elementu `join` bloku jest, albo `greedy` lub`non_greedy`  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`type`|Alias typu `T`.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[multitype_join —](#ctor)|Przeciążone. Konstruuje `multitype_join` bloku obsługi wiadomości.|  
|[~ multitype_join — destruktor](#dtor)|Niszczy `multitype_join` bloku obsługi wiadomości.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Zaakceptuj](#accept)|Akceptuje wiadomość została przyjęta przez to `multitype_join` bloku przeniesieniem własności do obiektu wywołującego.|  
|[acquire_ref](#acquire_ref)|Uzyskuje liczebności referencyjnej na tym `multitype_join` bloku obsługi wiadomości, aby zapobiec usunięciu.|  
|[korzystać z](#consume)|Wykorzystuje komunikat wcześniej oferowane przez `multitype_join` wiadomości bloku oraz pomyślnie zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.|  
|[link_target](#link_target)|Łącza do tego bloku docelowego `multitype_join` bloku obsługi wiadomości.|  
|[zlecenia](#release)|Zwalnia Poprzednia rezerwacja wiadomości powiodło się.|  
|[release_ref](#release_ref)|Zwalnia liczebności referencyjnej na tym `multiple_join` bloku obsługi wiadomości.|  
|[rezerwowa](#reserve)|Rezerwuje komunikat wcześniej oferowane przez to `multitype_join` bloku obsługi wiadomości.|  
|[unlink_target](#unlink_target)|Odłączenie od tego bloku docelowego `multitype_join` bloku obsługi wiadomości.|  
|[unlink_targets](#unlink_targets)|Wstrzymuje wszystkie elementy docelowe tego `multitype_join` bloku obsługi wiadomości. (Przesłania [ISource::unlink_targets](isource-class.md#unlink_targets).)|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [Isource —](isource-class.md)  
  
 `multitype_join`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="accept"></a>Zaakceptuj 

 Akceptuje wiadomość została przyjęta przez to `multitype_join` bloku przeniesieniem własności do obiektu wywołującego.  
  
```  
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z oferowany `message` obiektu.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który wywołuje `accept` metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do wywołującego ma teraz własność komunikat.  
  
##  <a name="acquire_ref"></a>acquire_ref 

 Uzyskuje liczebności referencyjnej na tym `multitype_join` bloku obsługi wiadomości, aby zapobiec usunięciu.  
  
```  
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który jest wywołaniem tej metody.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez `ITarget` obiekt, który jest połączone z tym źródłem podczas `link_target` metody.  
  
##  <a name="consume"></a>korzystać z 

 Wykorzystuje komunikat wcześniej oferowane przez `multitype_join` wiadomości bloku oraz pomyślnie zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.  
  
```  
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z zarezerwowanego `message` obiektu.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który wywołuje `consume` metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `message` obiekt, aby wywołującego ma teraz własności.  
  
### <a name="remarks"></a>Uwagi  
 `consume` Metoda jest podobna do `accept`, ale zawsze musi być poprzedzony przez wywołanie do `reserve` zwróconą `true`.  
  
##  <a name="link_target"></a>link_target 

 Łącza do tego bloku docelowego `multitype_join` bloku obsługi wiadomości.  
  
```  
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do `ITarget` bloku, aby połączyć się z: `multitype_join` bloku obsługi wiadomości.  
  
##  <a name="ctor"></a>multitype_join — 

 Konstruuje `multitype_join` bloku obsługi wiadomości.  
  
```  
explicit multitype_join(
    T _Tuple);

 
multitype_join(
    Scheduler& _PScheduler,  
    T _Tuple);

 
multitype_join(
    ScheduleGroup& _PScheduleGroup,  
    T _Tuple);

 
multitype_join(
    multitype_join&& _Join);
```  
  
### <a name="parameters"></a>Parametry  
 `_Tuple`  
 A `tuple` źródeł dla tego `multitype_join` bloku obsługi wiadomości.  
  
 `_PScheduler`  
 `Scheduler` Obiektu, w którym zadanie propagacji `multitype_join` zaplanowano bloku obsługi wiadomości.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Obiektu, w którym zadanie propagacji `multitype_join` zaplanowano bloku obsługi wiadomości. `Scheduler` Technicznego obiekt używany przez grupę harmonogramu.  
  
 `_Join`  
 A `multitype_join` bloku komunikatów do skopiowania. Należy pamiętać, że jest oddzielona oryginalny obiekt, co to Konstruktor przenoszenia.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.  
  
 Konstrukcja przenoszenia nie jest wykonywane w obszarze blokady, co oznacza, że zależy użytkownika, aby transmitowane w czasie przenoszenia nie ma żadnych zadań lekki. W przeciwnym razie wiele szczepy mogą wystąpić, co może prowadzić do wyjątków lub niespójny stan.  
  
##  <a name="dtor"></a>~ multitype_join — 

 Niszczy `multitype_join` bloku obsługi wiadomości.  
  
```  
~multitype_join();
```  
  
##  <a name="release"></a>zlecenia 

 Zwalnia Poprzednia rezerwacja wiadomości powiodło się.  
  
```  
virtual void release(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiekt został wydany.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który wywołuje `release` metody.  
  
##  <a name="release_ref"></a>release_ref 

 Zwalnia liczebności referencyjnej na tym `multiple_join` bloku obsługi wiadomości.  
  
```  
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który jest wywołaniem tej metody.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez `ITarget` obiekt, który jest jest rozłączony z tego źródła. Blok źródła może zwolnić wszystkie zasoby zarezerwowane dla blok docelowy.  
  
##  <a name="reserve"></a>rezerwowa 

 Rezerwuje komunikat wcześniej oferowane przez to `multitype_join` bloku obsługi wiadomości.  
  
```  
virtual bool reserve(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiektu pozostaje zarezerwowane.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który wywołuje `reserve` metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli komunikat został pomyślnie zarezerwowany, `false` inaczej. Zastrzeżenia może zakończyć się niepowodzeniem dla wielu powodów, takich jak: wiadomość już została zastrzeżone lub zaakceptowane przez inny element docelowy, źródła można odmówić zastrzeżenia i tak dalej.  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu metody `reserve`, jeśli próba powiedzie się, należy wywołać albo `consume` lub `release` Aby przejąć lub zrezygnować posiadania wiadomości, odpowiednio.  
  
##  <a name="unlink_target"></a>unlink_target 

 Odłączenie od tego bloku docelowego `multitype_join` bloku obsługi wiadomości.  
  
```  
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do `ITarget` bloku, aby odłączyć od tego `multitype_join` bloku obsługi wiadomości.  
  
##  <a name="unlink_targets"></a>unlink_targets 

 Wstrzymuje wszystkie elementy docelowe tego `multitype_join` bloku obsługi wiadomości.  
  
```  
virtual void unlink_targets();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Klasa wyboru](choice-class.md)   
 [JOIN — klasa](join-class.md)
