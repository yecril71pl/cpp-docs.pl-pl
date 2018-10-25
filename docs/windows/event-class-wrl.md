---
title: Event — klasa (WRL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Event class
- Microsoft::WRL::Wrappers::Event::Event, constructor
- Microsoft::WRL::Wrappers::Event::operator= operator
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7fce42093eb5d5c9eede67699b58124218d924d4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075466"
---
# <a name="event-class-wrl"></a>Event — klasa (WRL)

Przedstawia zdarzenie.

## <a name="syntax"></a>Składnia

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                   | Opis
---------------------- | ------------------------------------------------
[Event::Event](#event) | Inicjuje nowe wystąpienie klasy `Event` klasy.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                 | Opis
------------------------------------ | ------------------------------------------------------------------------
[Event::operator =](#operator-assign) | Przypisuje określonego `Event` referencję do bieżącego `Event` wystąpienia.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HandleT`

`Event`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="event"></a>Event::Event

Inicjuje nowe wystąpienie klasy `Event` klasy.

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Obsłuż to zdarzenie. Domyślnie *h* jest inicjowany do `nullptr`.

## <a name="operator-assign"></a>Event::operator =

Przypisuje określonego `Event` referencję do bieżącego `Event` wystąpienia.

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Odwołania rvalue do `Event` wystąpienia.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bieżącego `Event` wystąpienia.
