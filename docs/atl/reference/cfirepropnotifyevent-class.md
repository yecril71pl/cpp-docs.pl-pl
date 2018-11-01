---
title: Klasa CFirePropNotifyEvent
ms.date: 11/04/2016
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
ms.openlocfilehash: b25fa156c4576783ebc275a160a850e364066f96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621042"
---
# <a name="cfirepropnotifyevent-class"></a>Klasa CFirePropNotifyEvent

Ta klasa dostarcza metody do powiadamiania ujścia kontenera odnośnie do zmian właściwości formantu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CFirePropNotifyEvent
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|(Statyczny) Powiadamia obiekt sink kontenera, które uległy zmianie właściwości formantu.|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|(Statyczny) Powiadamia obiekt sink kontenera, który właściwości kontrolki zostanie zmienione.|

## <a name="remarks"></a>Uwagi

`CFirePropNotifyEvent` oferuje dwie metody, które powiadamiają o ujścia kontenera, który właściwości kontrolki została zmieniona lub ma zostać zmieniona.

Jeśli jest pochodną klasy implementowania kontroli nad `IPropertyNotifySink`, `CFirePropNotifyEvent` metody są wywoływane, gdy wywołujesz `FireOnRequestEdit` lub `FireOnChanged`. Jeśli nie pochodzi od klasy kontrolki `IPropertyNotifySink`, wywołania tych funkcji zwraca S_OK.

Aby uzyskać więcej informacji na temat tworzenia formantów, zobacz [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="fireonchanged"></a>  CFirePropNotifyEvent::FireOnChanged

Powiadamia o wszystkich połączonych [ipropertynotifysink —](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interfejsy (na każdym punkcie połączenia obiektu), które właściwości określonego obiektu został zmieniony.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Wskaźnik do `IUnknown` obiektu wysyłania powiadomienia.

*dispID*<br/>
[in] Identyfikator właściwości, które uległy zmianie.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Ta funkcja jest bezpieczny do wywołania, nawet jeśli formant nie obsługuje punktów połączenia.

##  <a name="fireonrequestedit"></a>  CFirePropNotifyEvent::FireOnRequestEdit

Powiadamia o wszystkich połączonych [ipropertynotifysink —](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interfejsy (na każdym punkcie połączenia obiektu), które właściwości określony obiekt ma zostać zmieniona.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Wskaźnik do `IUnknown` obiektu wysyłania powiadomienia.

*dispID*<br/>
[in] Identyfikator właściwości, które chcesz zmienić.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Ta funkcja jest bezpieczny do wywołania, nawet jeśli formant nie obsługuje punktów połączenia.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
