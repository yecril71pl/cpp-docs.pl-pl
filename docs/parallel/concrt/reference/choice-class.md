---
title: Klasa wyboru | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- choice
- AGENTS/concurrency::choice
- AGENTS/concurrency::choice::choice
- AGENTS/concurrency::choice::accept
- AGENTS/concurrency::choice::acquire_ref
- AGENTS/concurrency::choice::consume
- AGENTS/concurrency::choice::has_value
- AGENTS/concurrency::choice::index
- AGENTS/concurrency::choice::link_target
- AGENTS/concurrency::choice::release
- AGENTS/concurrency::choice::release_ref
- AGENTS/concurrency::choice::reserve
- AGENTS/concurrency::choice::unlink_target
- AGENTS/concurrency::choice::unlink_targets
- AGENTS/concurrency::choice::value
dev_langs:
- C++
helpviewer_keywords:
- choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 77a02043a3a301760130b568380a0ca5d57994cc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="choice-class"></a>Klasa wyboru
A `choice` bloku komunikatów jest blok wielu źródłach, jednego docelowego reprezentuje przepływ sterowania interakcji z zestawu źródeł. Blokowanie wybór będzie czekać do jednego z wielu źródeł, który zwróci komunikat i rozpropaguje indeksu źródła wytworzonego wiadomości.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<
    class T  
>  
class choice: public ISource<size_t>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 A `tuple`— na podstawie typu reprezentujący ładunki źródeł danych wejściowych.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`type`|Alias typu `T`.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Wybór](#ctor)|Przeciążone. Konstruuje `choice` bloku obsługi wiadomości.|  
|[~ choice — destruktor](#dtor)|Niszczy `choice` bloku obsługi wiadomości.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Zaakceptuj](#accept)|Akceptuje wiadomość została przyjęta przez to `choice` bloku przeniesieniem własności do obiektu wywołującego.|  
|[acquire_ref](#acquire_ref)|Uzyskuje liczebności referencyjnej na tym `choice` bloku obsługi wiadomości, aby zapobiec usunięciu.|  
|[Korzystać z](#consume)|Wykorzystuje komunikat wcześniej oferowane przez to `choice` wiadomości bloku oraz pomyślnie zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.|  
|[has_value](#has_value)|Sprawdza, czy to `choice` bloku komunikatów został zainicjowany z wartością jeszcze.|  
|[index](#index)|Zwraca indeks do `tuple` reprezentujący element wybranych przez `choice` bloku obsługi wiadomości.|  
|[link_target](#link_target)|Łącza do tego bloku docelowego `choice` bloku obsługi wiadomości.|  
|[Zlecenia](#release)|Zwalnia Poprzednia rezerwacja wiadomości powiodło się.|  
|[release_ref](#release_ref)|Zwalnia liczebności referencyjnej na tym `choice` bloku obsługi wiadomości.|  
|[reserve](#reserve)|Rezerwuje komunikat wcześniej oferowane przez to `choice` bloku obsługi wiadomości.|  
|[unlink_target](#unlink_target)|Odłączenie od tego bloku docelowego `choice` bloku obsługi wiadomości.|  
|[unlink_targets](#unlink_targets)|Wstrzymuje wszystkie elementy docelowe tego `choice` bloku obsługi wiadomości. (Przesłania [ISource::unlink_targets](isource-class.md#unlink_targets).)|  
|[value](#value)|Pobiera komunikat, którego indeks wybraną przez `choice` bloku obsługi wiadomości.|  
  
## <a name="remarks"></a>Uwagi  
 Blokowanie wybór zapewnia tylko jeden z komunikatów przychodzących jest używane.  
  
 Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [Isource —](isource-class.md)  
  
 `choice`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="accept">Zaakceptuj</a> 

 Akceptuje wiadomość została przyjęta przez to `choice` bloku przeniesieniem własności do obiektu wywołującego.  
  
```  
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z oferowany `message` obiektu.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który wywołuje `accept` metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do wywołującego ma teraz własność komunikat.  
  
##  <a name="acquire_ref"></a> acquire_ref 

 Uzyskuje liczebności referencyjnej na tym `choice` bloku obsługi wiadomości, aby zapobiec usunięciu.  
  
```  
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który jest wywołaniem tej metody.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez `ITarget` obiekt, który jest połączone z tym źródłem podczas `link_target` metody.  
  
##  <a name="ctor">Wybór</a> 

 Konstruuje `choice` bloku obsługi wiadomości.  
  
```  
explicit choice(
    T _Tuple);

 
choice(
    Scheduler& _PScheduler,  
    T _Tuple);

 
choice(
    ScheduleGroup& _PScheduleGroup,  
    T _Tuple);

 
choice(
    choice&& _Choice);
```  
  
### <a name="parameters"></a>Parametry  
 `_Tuple`  
 A `tuple` źródeł wyboru.  
  
 `_PScheduler`  
 `Scheduler` Obiektu, w którym zadanie propagacji `choice` zaplanowano bloku obsługi wiadomości.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Obiektu, w którym zadanie propagacji `choice` zaplanowano bloku obsługi wiadomości. `Scheduler` Technicznego obiekt używany przez grupę harmonogramu.  
  
 `_Choice`  
 A `choice` bloku komunikatów do skopiowania. Należy pamiętać, że jest oddzielona oryginalny obiekt, co to Konstruktor przenoszenia.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.  
  
 Konstrukcja przenoszenia nie jest wykonywane w obszarze blokady, co oznacza, że zależy użytkownika, aby transmitowane w czasie przenoszenia nie ma żadnych zadań lekki. W przeciwnym razie wiele szczepy mogą wystąpić, co może prowadzić do wyjątków lub niespójny stan.  
  
##  <a name="dtor"></a> ~ choice 

 Niszczy `choice` bloku obsługi wiadomości.  
  
```  
~choice();
```  
  
##  <a name="consume">Korzystać z</a> 

 Wykorzystuje komunikat wcześniej oferowane przez to `choice` wiadomości bloku oraz pomyślnie zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.  
  
```  
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
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
  
##  <a name="has_value"></a> has_value 

 Sprawdza, czy to `choice` bloku komunikatów został zainicjowany z wartością jeszcze.  
  
```  
bool has_value() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli blok otrzymał wartość `false` inaczej.  
  
##  <a name="index"></a> Indeks 

 Zwraca indeks do `tuple` reprezentujący element wybranych przez `choice` bloku obsługi wiadomości.  
  
```  
size_t index();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 Ładunek komunikatu można wyodrębnić przy użyciu `get` metody.  
  
##  <a name="link_target"></a> link_target 

 Łącza do tego bloku docelowego `choice` bloku obsługi wiadomości.  
  
```  
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do `ITarget` bloku, aby połączyć się z: `choice` bloku obsługi wiadomości.  
  
##  <a name="release">Zlecenia</a> 

 Zwalnia Poprzednia rezerwacja wiadomości powiodło się.  
  
```  
virtual void release(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiekt został wydany.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który wywołuje `release` metody.  
  
##  <a name="release_ref"></a> release_ref 

 Zwalnia liczebności referencyjnej na tym `choice` bloku obsługi wiadomości.  
  
```  
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który jest wywołaniem tej metody.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez `ITarget` obiekt, który jest jest rozłączony z tego źródła. Blok źródła może zwolnić wszystkie zasoby zarezerwowane dla blok docelowy.  
  
##  <a name="reserve"></a> rezerwowa 

 Rezerwuje komunikat wcześniej oferowane przez to `choice` bloku obsługi wiadomości.  
  
```  
virtual bool reserve(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` obiektu pozostaje zarezerwowane.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który wywołuje `reserve` metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli komunikat został pomyślnie zarezerwowany, `false` inaczej. Zastrzeżenia może zakończyć się niepowodzeniem dla wielu powodów, takich jak: wiadomość już została zastrzeżone lub zaakceptowane przez inny element docelowy, źródła można odmówić zastrzeżenia i tak dalej.  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu metody `reserve`, jeśli próba powiedzie się, należy wywołać albo `consume` lub `release` Aby przejąć lub zrezygnować posiadania wiadomości, odpowiednio.  
  
##  <a name="unlink_target"></a> unlink_target 

 Odłączenie od tego bloku docelowego `choice` bloku obsługi wiadomości.  
  
```  
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do `ITarget` bloku, aby odłączyć od tego `choice` bloku obsługi wiadomości.  
  
##  <a name="unlink_targets"></a> unlink_targets 

 Wstrzymuje wszystkie elementy docelowe tego `choice` bloku obsługi wiadomości.  
  
```  
virtual void unlink_targets();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda nie musi być wywoływana z destruktor, ponieważ destruktor dla elementu wewnętrznego `single_assignment` bloku będą rozłączyć poprawnie.  
  
##  <a name="value"></a> Wartość 

 Pobiera komunikat, którego indeks wybraną przez `choice` bloku obsługi wiadomości.  
  
```  
template <
    typename _Payload_type  
>  
_Payload_type const& value();
```  
  
### <a name="parameters"></a>Parametry  
 `_Payload_type`  
 Typ ładunek komunikatu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Obciążenie komunikatu.  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ `choice` bloku obsługi wiadomości może zająć danych wejściowych z ładunku różnych typów, należy określić typ ładunku w punkcie odzyskiwania. Można określić typu na podstawie wyniku `index` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [JOIN — klasa](join-class.md)   
 [single_assignment, klasa](single-assignment-class.md)
