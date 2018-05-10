---
title: EventSource — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
dev_langs:
- C++
helpviewer_keywords:
- EventSource class
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b2d466b317927cd8de259637450b68b6aaf13bd5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="eventsource-class"></a>EventSource — Klasa
Reprezentuje-agile zdarzeń. Funkcje Członkowskie EventSource dodawania, usuwania i wywołanie procedury obsługi zdarzeń. Elastyczne zdarzenia, użyj [AgileEventSource](agileeventsource-class.md). 
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename TDelegateInterface>  
class EventSource;  
```  
  
#### <a name="parameters"></a>Parametry  
 `TDelegateInterface`  
 Interfejs do delegata, który reprezentuje program obsługi zdarzeń.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[EventSource::EventSource, konstruktor](../windows/eventsource-eventsource-constructor.md)|Inicjuje nowe wystąpienie klasy EventSource.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[EventSource::Add, metoda](../windows/eventsource-add-method.md)|Dołącza reprezentowany przez interfejs określonego delegata do zestawu obsługi zdarzeń dla bieżącego obiektu EventSource programu obsługi zdarzeń.|  
|[EventSource::GetSize, metoda](../windows/eventsource-getsize-method.md)|Pobiera liczbę programów obsługi zdarzeń skojarzonych z bieżącym obiektem źródła zdarzeń|  
|[EventSource::InvokeAll, metoda](../windows/eventsource-invokeall-method.md)|Wywołuje każdego obsługi zdarzeń skojarzonych z bieżącego obiektu EventSource przy użyciu określone typy argumentów i argumentów.|  
|[EventSource::Remove, metoda](../windows/eventsource-remove-method.md)|Usuwa reprezentowanego przez określone zdarzenie tokenu rejestracji z zestawu programów obsługi zdarzeń skojarzonych z bieżącym obiektem EventSource programu obsługi zdarzeń.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[EventSource::addRemoveLock_, składowa danych](../windows/eventsource-addremovelock-data-member.md)|Synchronizuje dostęp do [targets_ —](../windows/eventsource-targets-data-member.md) tablicy podczas dodawania, usuwania lub wywoływanie programów obsługi zdarzeń.|  
|[EventSource::targets_, składowa danych](../windows/eventsource-targets-data-member.md)|Tablica procedury obsługi zdarzeń.|  
|[EventSource::targetsPointerLock_, składowa danych](../windows/eventsource-targetspointerlock-data-member.md)|Synchronizuje dostępu do elementów członkowskich danych wewnętrznych, nawet wtedy, gdy programy obsługi zdarzeń dla tego elementu EventSource są dodawane, usunięte lub wywołany.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `EventSource`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)
[AgileEventSource — klasa](agileeventsource-class.md)