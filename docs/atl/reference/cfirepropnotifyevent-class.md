---
title: CFirePropNotifyEvent Klasa
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
ms.openlocfilehash: 1dfce42176341d74ffc7d9b42f856e71b17bf4f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326966"
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent Klasa

Ta klasa zawiera metody powiadamiania kontenera ujścia dotyczące zmian właściwości kontroli.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CFirePropNotifyEvent
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|(Statyczne) Powiadamia ujście kontenera, że właściwość formantu została zmieniona.|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|(Statyczne) Powiadamia ujście kontenera, że właściwość formantu ma się zmienić.|

## <a name="remarks"></a>Uwagi

`CFirePropNotifyEvent`ma dwie metody, które powiadamiają ujście kontenera, że właściwość formantu została zmieniona lub ma się zmienić.

Jeśli klasa implementująca formant `IPropertyNotifySink`jest `CFirePropNotifyEvent` pochodną , metody `FireOnRequestEdit` są `FireOnChanged`wywoływane podczas wywoływania lub . Jeśli klasa kontroli nie jest `IPropertyNotifySink`pochodną , wywołania tych funkcji zwracają S_OK.

Aby uzyskać więcej informacji na temat tworzenia formantów, zobacz [samouczek ATL](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="cfirepropnotifyeventfireonchanged"></a><a name="fireonchanged"></a>CFirePropNotifyEvent::FireOnChanged

Powiadamia wszystkie podłączone [interfejsy IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) (w każdym punkcie połączenia obiektu), które zostały zmienione przez właściwość określonego obiektu.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[w] Wskaźnik do `IUnknown` obiektu wysyłającego powiadomienie.

*Dispid*<br/>
[w] Identyfikator właściwości, która uległa zmianie.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja jest bezpieczna do wywołania, nawet jeśli formant nie obsługuje punktów połączenia.

## <a name="cfirepropnotifyeventfireonrequestedit"></a><a name="fireonrequestedit"></a>CFirePropNotifyEvent::FireOnRequestEdit

Powiadamia wszystkie podłączone [interfejsy IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) (w każdym punkcie połączenia obiektu), które ma się zmienić właściwość określonego obiektu.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[w] Wskaźnik do `IUnknown` obiektu wysyłającego powiadomienie.

*Dispid*<br/>
[w] Identyfikator właściwości, która ma ulec zmianie.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja jest bezpieczna do wywołania, nawet jeśli formant nie obsługuje punktów połączenia.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
