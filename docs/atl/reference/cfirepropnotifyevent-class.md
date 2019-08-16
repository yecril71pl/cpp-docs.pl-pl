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
ms.openlocfilehash: 694127ceccc1d1b55e5da9abca799dff77dcfc60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496940"
---
# <a name="cfirepropnotifyevent-class"></a>Klasa CFirePropNotifyEvent

Ta klasa dostarcza metody powiadamiania ujścia kontenera o zmianach właściwości formantu.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CFirePropNotifyEvent
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|Ruchom Powiadamia ujścia kontenera o zmianie właściwości kontrolki.|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|Ruchom Powiadamia ujścia kontenera, że właściwość kontrolki ma zostać zmieniona.|

## <a name="remarks"></a>Uwagi

`CFirePropNotifyEvent`ma dwie metody, które powiadamiają ujścia kontenera o zmianie właściwości kontrolki lub zmianie.

Jeśli klasa implementująca `IPropertyNotifySink`formant pochodzi od `CFirePropNotifyEvent` , metody są wywoływane po wywołaniu `FireOnRequestEdit` lub `FireOnChanged`. Jeśli Klasa formantu nie pochodzi od `IPropertyNotifySink`, wywołania tych funkcji zwracają S_OK.

Aby uzyskać więcej informacji na temat tworzenia formantów, zobacz [samouczek ATL](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

##  <a name="fireonchanged"></a>CFirePropNotifyEvent::FireOnChanged

Powiadamia wszystkie połączone interfejsy [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) (na każdym punkcie połączenia obiektu) o zmianie określonej właściwości obiektu.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
podczas Wskaźnik do `IUnknown` obiektu wysyłającego powiadomienie.

*dispID*<br/>
podczas Identyfikator właściwości, która została zmieniona.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja jest bezpieczna do wywołania, nawet jeśli formant nie obsługuje punktów połączenia.

##  <a name="fireonrequestedit"></a>CFirePropNotifyEvent::FireOnRequestEdit

Powiadamia wszystkie połączone interfejsy [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) (na każdym punkcie połączenia obiektu), które mają zostać zmienione przez określoną właściwość obiektu.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
podczas Wskaźnik do `IUnknown` obiektu wysyłającego powiadomienie.

*dispID*<br/>
podczas Identyfikator właściwości, która ma zostać zmieniona.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja jest bezpieczna do wywołania, nawet jeśli formant nie obsługuje punktów połączenia.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
