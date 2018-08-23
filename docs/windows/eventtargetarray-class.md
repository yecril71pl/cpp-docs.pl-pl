---
title: Eventtargetarray — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray class
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3be91f85838ceb557edd5def7d7984aaf8904ea5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575668"
---
# <a name="eventtargetarray-class"></a>EventTargetArray — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
class EventTargetArray : public Microsoft::WRL::RuntimeClass<Microsoft::WRL::RuntimeClassFlags<ClassicCom>, IUnknown>;
```

## <a name="remarks"></a>Uwagi

Reprezentuje tablicę procedury obsługi zdarzeń.

Programy obsługi zdarzeń, które są skojarzone z [EventSource](../windows/eventsource-class.md) obiektu są przechowywane w chronionym **EventTargetArray** element członkowski danych.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[EventTargetArray::EventTargetArray, konstruktor](../windows/eventtargetarray-eventtargetarray-constructor.md)|Inicjuje nowe wystąpienie klasy **EventTargetArray** klasy.|
|[EventTargetArray::~EventTargetArray, destruktor](../windows/eventtargetarray-tilde-eventtargetarray-destructor.md)|Deinicjuje bieżące **EventTargetArray** klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[EventTargetArray::AddTail, metoda](../windows/eventtargetarray-addtail-method.md)|Dołącza określona procedura obsługi zdarzeń do końca tablicy wewnętrzne programów obsługi zdarzeń.|
|[EventTargetArray::Begin, metoda](../windows/eventtargetarray-begin-method.md)|Pobiera adres pierwszego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.|
|[EventTargetArray::End, metoda](../windows/eventtargetarray-end-method.md)|Pobiera adres ostatniego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.|
|[EventTargetArray::Length, metoda](../windows/eventtargetarray-length-method.md)|Pobiera aktualną liczbę elementów w tablicy wewnętrznej procedury obsługi zdarzeń.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`EventTargetArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)