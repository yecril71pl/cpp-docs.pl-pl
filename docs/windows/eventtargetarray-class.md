---
title: "Eventtargetarray — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::EventTargetArray
dev_langs: C++
helpviewer_keywords: EventTargetArray class
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ac591a1d27792d3b825336ed46e38fa5d002fa73
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="eventtargetarray-class"></a>EventTargetArray — Klasa
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
class EventTargetArray : public Microsoft::WRL::RuntimeClass<Microsoft::WRL::RuntimeClassFlags<ClassicCom>, IUnknown>;  
```  
  
## <a name="remarks"></a>Uwagi  
 Reprezentuje tablicę procedury obsługi zdarzeń.  
  
 Programy obsługi zdarzeń, które są skojarzone z [EventSource](../windows/eventsource-class.md) obiektu są przechowywane w chroniony element członkowski danych eventtargetarray —.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[EventTargetArray::EventTargetArray, konstruktor](../windows/eventtargetarray-eventtargetarray-constructor.md)|Inicjuje nowe wystąpienie klasy eventtargetarray —.|  
|[EventTargetArray::~EventTargetArray, destruktor](../windows/eventtargetarray-tilde-eventtargetarray-destructor.md)|Deinitializes bieżącego eventtargetarray — klasa.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[EventTargetArray::AddTail, metoda](../windows/eventtargetarray-addtail-method.md)|Dołącza określona procedura obsługi zdarzeń do końca tablicy wewnętrznej procedury obsługi zdarzeń.|  
|[EventTargetArray::Begin, metoda](../windows/eventtargetarray-begin-method.md)|Pobiera adres pierwszego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.|  
|[EventTargetArray::End, metoda](../windows/eventtargetarray-end-method.md)|Pobiera adres ostatniego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.|  
|[EventTargetArray::Length, metoda](../windows/eventtargetarray-length-method.md)|Pobiera bieżącą liczbę elementów w tablicy wewnętrznej procedury obsługi zdarzeń.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `EventTargetArray`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)