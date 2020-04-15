---
title: Event, Klasa (WRL)
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Event class
- Microsoft::WRL::Wrappers::Event::Event, constructor
- Microsoft::WRL::Wrappers::Event::operator= operator
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
ms.openlocfilehash: 85b4c2d1f1a27e90a65e47aa749e079f4aa08739
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371523"
---
# <a name="event-class-wrl"></a>Event, Klasa (WRL)

Reprezentuje zdarzenie.

## <a name="syntax"></a>Składnia

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                   | Opis
---------------------- | ------------------------------------------------
[Zdarzenie::Zdarzenie](#event) | Inicjuje nowe wystąpienie klasy `Event`.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                 | Opis
------------------------------------ | ------------------------------------------------------------------------
[Zdarzenie::operator=](#operator-assign) | Przypisuje określone `Event` odwołanie do `Event` bieżącego wystąpienia.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HandleT`

`Event`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki

## <a name="eventevent"></a><a name="event"></a>Zdarzenie::Zdarzenie

Inicjuje nowe wystąpienie klasy `Event`.

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Dojście do zdarzenia. Domyślnie *h* jest inicjowany do `nullptr`.

## <a name="eventoperator"></a><a name="operator-assign"></a>Zdarzenie::operator=

Przypisuje określone `Event` odwołanie do `Event` bieżącego wystąpienia.

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Odwołanie rvalue do `Event` wystąpienia.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bieżącego `Event` wystąpienia.
