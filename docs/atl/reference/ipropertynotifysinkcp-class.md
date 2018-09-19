---
title: Klasa IPropertyNotifySinkCP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13ddd14ad530fa2b7ce2892ce8838b27e307381f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135779"
---
# <a name="ipropertynotifysinkcp-class"></a>Klasa IPropertyNotifySinkCP

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

*KOR*<br/>
Klasa, która zarządza połączeniami między punktem połączenia i jego ujścia. Wartość domyślna to [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), co umożliwia nieograniczone połączenia. Można również użyć [CComUnkArray](../../atl/reference/ccomunkarray-class.md), która określa stałą liczbę połączeń.

## <a name="remarks"></a>Uwagi

`IPropertyNotifySinkCP` dziedziczy wszystkie metody, za pośrednictwem swojej klasy bazowej, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).

[Ipropertynotifysink —](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interfejs umożliwia obiekt sink otrzymywać powiadomienia o zmianie właściwości. Klasa `IPropertyNotifySinkCP` udostępnia ten interfejs jako interfejsu wychodzącego w obiekcie składnika. Klient musi implementować `IPropertyNotifySink` metody na obiekt sink.

Pochodzi z klasy `IPropertyNotifySinkCP` gdy chcesz utworzyć punkt połączenia, który reprezentuje `IPropertyNotifySink` interfejsu.

Aby uzyskać więcej informacji dotyczących używania punktów połączenia w ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="see-also"></a>Zobacz też

[Klasa IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[Klasa IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
