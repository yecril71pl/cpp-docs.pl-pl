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
ms.openlocfilehash: 9838a48b078cbc59a5ae86669ad9f26792d9816e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495624"
---
# <a name="ipropertynotifysinkcp-class"></a>Klasa IPropertyNotifySinkCP

Ta klasa uwidacznia Interfejs [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) jako interfejs wychodzący w obiekcie połączonym.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IPropertyNotifySinkCP`.

*CDV*<br/>
Klasa, która zarządza połączeniami między punktem połączenia a jego ujściam. Wartość domyślna to [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), która umożliwia nieograniczone połączenia. Można również użyć [CComUnkArray](../../atl/reference/ccomunkarray-class.md), który określa stałą liczbę połączeń.

## <a name="remarks"></a>Uwagi

`IPropertyNotifySinkCP`dziedziczy wszystkie metody za poorednictwem klasy bazowej, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).

Interfejs [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) umożliwia obiektowi ujścia otrzymywanie powiadomień o zmianach właściwości. Klasa `IPropertyNotifySinkCP` uwidacznia ten interfejs jako interfejs wychodzący w obiekcie połączonym. Klient musi zaimplementować `IPropertyNotifySink` metody w zlewie.

Utwórz klasę z `IPropertyNotifySinkCP` , gdy chcesz utworzyć punkt połączenia, który `IPropertyNotifySink` reprezentuje interfejs.

Aby uzyskać więcej informacji na temat używania punktów połączenia w ATL, zobacz [punkty połączenia](../../atl/atl-connection-points.md)w artykule.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

## <a name="see-also"></a>Zobacz także

[Klasa IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[Klasa IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
