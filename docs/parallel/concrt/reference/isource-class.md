---
title: Isource — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
dev_langs:
- C++
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27b1aa57a8c90c2f996aab3b8ee47797f15edd5b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="isource-class"></a>ISource — Klasa
`ISource` Klasa jest interfejsem źródła wszystkie bloki. Bloki źródła propagację wiadomości `ITarget` bloków.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>
class ISource;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych ładunku w komunikaty generowane przez bloku źródłowego.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`source_type`|Alias typu `T`.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[~ ISource — destruktor](#dtor)|Niszczy `ISource` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Zaakceptuj](#accept)|W przypadku przesłonięcia w klasie pochodnej, akceptuje wiadomość została przyjęta przez to `ISource` bloku przeniesieniem własności do obiektu wywołującego.|  
|[acquire_ref](#acquire_ref)|W przypadku przesłonięcia w klasie pochodnej, uzyskuje liczebności referencyjnej na tym `ISource` bloku, aby zapobiec usunięciu.|  
|[Korzystać z](#consume)|W przypadku przesłonięcia w klasie pochodnej, wykorzystuje komunikat wcześniej oferowane przez to `ISource` blokować i pomyślnie zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.|  
|[link_target](#link_target)|W przypadku przesłonięcia w klasie pochodnej, linki bloku docelowego tej `ISource` bloku.|  
|[Zlecenia](#release)|W przypadku przesłonięcia w klasie pochodnej, zwalnia Poprzednia rezerwacja wiadomości powiodło się.|  
|[release_ref](#release_ref)|W przypadku przesłonięcia w klasie pochodnej, zwalnia liczebności referencyjnej na tym `ISource` bloku.|  
|[reserve](#reserve)|W przypadku przesłonięcia w klasie pochodnej, rezerwuje komunikat wcześniej oferowane przez to `ISource` bloku.|  
|[unlink_target](#unlink_target)|W przypadku przesłonięcia w klasie pochodnej, odłączenie od tego bloku docelowego `ISource` zablokować, jeśli znaleziono wcześniej być połączony.|  
|[unlink_targets](#unlink_targets)|W przypadku przesłonięcia w klasie pochodnej, odłączenie wszystkich bloków docelowej tego `ISource` bloku.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ISource`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="accept"></a> Zaakceptuj 

 W przypadku przesłonięcia w klasie pochodnej, akceptuje wiadomość została przyjęta przez to `ISource` bloku przeniesieniem własności do obiektu wywołującego.  
  
```
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z oferowany `message` obiektu.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który wywołuje `accept` metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do wywołującego ma teraz własność komunikat.  
  
### <a name="remarks"></a>Uwagi  
 `accept` Metoda jest wywoływana przez element docelowy, gdy komunikat jest oferowany przez to `ISource` bloku. Wskaźnik komunikat zwrócony mogą być inne niż ten, który został przekazany do `propagate` metody `ITarget` zablokować, jeśli to źródło postanawia kopia wiadomości.  
  
##  <a name="acquire_ref"></a> acquire_ref 

 W przypadku przesłonięcia w klasie pochodnej, uzyskuje liczebności referencyjnej na tym `ISource` bloku, aby zapobiec usunięciu.  
  
```
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który jest wywołaniem tej metody.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez `ITarget` obiekt, który jest połączone z tym źródłem podczas `link_target` metody.  
  
##  <a name="consume"></a> Korzystać z 

 W przypadku przesłonięcia w klasie pochodnej, wykorzystuje komunikat wcześniej oferowane przez to `ISource` blokować i pomyślnie zastrzeżone przez element docelowy przeniesieniem własności do obiektu wywołującego.  
  
```
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
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
  
##  <a name="dtor"></a> ~ Isource — 

 Niszczy `ISource` obiektu.  
  
```
virtual ~ISource();
```  
  
##  <a name="link_target"></a> link_target 

 W przypadku przesłonięcia w klasie pochodnej, linki bloku docelowego tej `ISource` bloku.  
  
```
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do bloku docelowego są połączone z tym `ISource` bloku.  
  
##  <a name="release"></a> Zlecenia 

 W przypadku przesłonięcia w klasie pochodnej, zwalnia Poprzednia rezerwacja wiadomości powiodło się.  
  
```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z zarezerwowanego `message` obiektu.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który wywołuje `release` metody.  
  
##  <a name="release_ref"></a> release_ref 

 W przypadku przesłonięcia w klasie pochodnej, zwalnia liczebności referencyjnej na tym `ISource` bloku.  
  
```
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który jest wywołaniem tej metody.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez `ITarget` obiekt, który jest jest rozłączony z tego źródła. Blok źródła może zwolnić wszystkie zasoby zarezerwowane dla blok docelowy.  
  
##  <a name="reserve"></a> rezerwowa 

 W przypadku przesłonięcia w klasie pochodnej, rezerwuje komunikat wcześniej oferowane przez to `ISource` bloku.  
  
```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z oferowany `message` obiektu.  
  
 `_PTarget`  
 Wskaźnik do bloku docelowego, który wywołuje `reserve` metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli komunikat został pomyślnie zarezerwowany, `false` inaczej. Zastrzeżenia może zakończyć się niepowodzeniem dla wielu powodów, takich jak: wiadomość już została zastrzeżone lub zaakceptowane przez inny element docelowy, źródła można odmówić zastrzeżenia i tak dalej.  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu metody `reserve`, jeśli próba powiedzie się, należy wywołać albo `consume` lub `release` Aby przejąć lub zrezygnować posiadania wiadomości, odpowiednio.  
  
##  <a name="unlink_target"></a> unlink_target 

 W przypadku przesłonięcia w klasie pochodnej, odłączenie od tego bloku docelowego `ISource` zablokować, jeśli znaleziono wcześniej być połączony.  
  
```
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Wskaźnik do bloku docelowego jest rozłączony z tego `ISource` bloku.  
  
##  <a name="unlink_targets"></a> unlink_targets 

 W przypadku przesłonięcia w klasie pochodnej, odłączenie wszystkich bloków docelowej tego `ISource` bloku.  
  
```
virtual void unlink_targets() = 0;
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [ITarget, klasa](itarget-class.md)
