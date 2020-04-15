---
title: Klasa IPropertyNotifySinkCP
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: c6d98bf5a6dfe5566839eb22bcd2bab2a9c28e4d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329608"
---
# <a name="ipropertynotifysinkcp-class"></a>Klasa IPropertyNotifySinkCP

Ta klasa udostępnia [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) interfejs jako interfejs wychodzący na obiekcie connectable.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IPropertyNotifySinkCP`.

*Cdv*<br/>
Klasa, która zarządza połączeniami między punktem połączenia a jego pochłaniaczami. Wartością domyślną jest [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), która pozwala na nieograniczone połączenia. Można również użyć [CComUnkArray](../../atl/reference/ccomunkarray-class.md), który określa stałą liczbę połączeń.

## <a name="remarks"></a>Uwagi

`IPropertyNotifySinkCP`dziedziczy wszystkie metody za pośrednictwem swojej klasy podstawowej [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).

[Interfejs IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) umożliwia obiektowi ujścia do odbierania powiadomień o zmianach właściwości. Klasa `IPropertyNotifySinkCP` udostępnia ten interfejs jako interfejs wychodzący na obiekcie, który można podłączyć. Klient musi zaimplementować `IPropertyNotifySink` metody na zlewie.

Wywodź `IPropertyNotifySinkCP` klasę z punktu, w którym `IPropertyNotifySink` chcesz utworzyć punkt połączenia reprezentujący interfejs.

Aby uzyskać więcej informacji na temat korzystania z punktów połączenia w atl, zobacz artykuł [Punkty połączenia](../../atl/atl-connection-points.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="see-also"></a>Zobacz też

[Klasa IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[Klasa IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
