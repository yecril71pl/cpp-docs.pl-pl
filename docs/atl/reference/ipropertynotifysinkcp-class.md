---
title: IPropertyNotifySinkCP Class
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: b96e5345923d04de74dace173a80b8c4d3ee917f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197893"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP Class

Ta klasa udostępnia [ipropertynotifysink —](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interfejs jako interfejsu wychodzącego w obiekcie składnika.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IPropertyNotifySinkCP`.

*CDV*<br/>
Klasa, która zarządza połączeniami między punktem połączenia i jego ujścia. Wartość domyślna to [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), co umożliwia nieograniczone połączenia. Można również użyć [CComUnkArray](../../atl/reference/ccomunkarray-class.md), która określa stałą liczbę połączeń.

## <a name="remarks"></a>Uwagi

`IPropertyNotifySinkCP` dziedziczy wszystkie metody, za pośrednictwem swojej klasy bazowej, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).

[Ipropertynotifysink —](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interfejs umożliwia obiekt sink otrzymywać powiadomienia o zmianie właściwości. Klasa `IPropertyNotifySinkCP` udostępnia ten interfejs jako interfejsu wychodzącego w obiekcie składnika. Klient musi implementować `IPropertyNotifySink` metody na obiekt sink.

Pochodzi z klasy `IPropertyNotifySinkCP` gdy chcesz utworzyć punkt połączenia, który reprezentuje `IPropertyNotifySink` interfejsu.

Aby uzyskać więcej informacji dotyczących używania punktów połączenia w ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="see-also"></a>Zobacz także

[Klasa IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[Klasa IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
