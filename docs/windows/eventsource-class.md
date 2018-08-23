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
ms.openlocfilehash: 8805547c5803ae665178330063e6b77b1b3c662e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596214"
---
# <a name="eventsource-class"></a>EventSource — Klasa

Reprezentuje zdarzenie agile. **EventSource** elementów członkowskich dodawania, usuwania i wywoływanie programów obsługi zdarzeń. Dla zdarzeń agile, należy użyć [AgileEventSource](agileeventsource-class.md).

## <a name="syntax"></a>Składnia

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*  
Interfejs do delegata, który reprezentuje program obsługi zdarzeń.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[EventSource::EventSource, konstruktor](../windows/eventsource-eventsource-constructor.md)|Inicjuje nowe wystąpienie klasy **EventSource** klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[EventSource::Add, metoda](../windows/eventsource-add-method.md)|Dołącza program obsługi zdarzeń, reprezentowane przez interfejs określonego delegata do zestawu programów obsługi zdarzeń dla bieżącego **EventSource** obiektu.|
|[EventSource::GetSize, metoda](../windows/eventsource-getsize-method.md)|Pobiera liczbę programów obsługi zdarzeń skojarzonych z bieżącym **EventSource** obiektu|
|[EventSource::InvokeAll, metoda](../windows/eventsource-invokeall-method.md)|Wywołuje każdy program obsługi zdarzeń skojarzonych z bieżącym **EventSource** przy użyciu określone typy argumentów i argumenty.|
|[EventSource::Remove, metoda](../windows/eventsource-remove-method.md)|Usuwa program obsługi zdarzeń, reprezentowane przez tokenu rejestracji określonego zdarzenia z zestawu programów obsługi zdarzeń skojarzonych z bieżącym **EventSource** obiektu.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[EventSource::addRemoveLock_, składowa danych](../windows/eventsource-addremovelock-data-member.md)|Synchronizuje dostęp do [targets_ — element](../windows/eventsource-targets-data-member.md) tablicy podczas dodawania, usuwania lub wywoływania procedury obsługi zdarzeń.|
|[EventSource::targets_, składowa danych](../windows/eventsource-targets-data-member.md)|Tablica procedury obsługi zdarzeń.|
|[EventSource::targetsPointerLock_, składowa danych](../windows/eventsource-targetspointerlock-data-member.md)|Synchronizuje dostęp do danych wewnętrznych elementów członkowskich, nawet wtedy, gdy programy obsługi zdarzeń dla tego źródła zdarzeń są dodawane, usuwane lub wywołana.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`EventSource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)  
[AgileEventSource, klasa](agileeventsource-class.md)