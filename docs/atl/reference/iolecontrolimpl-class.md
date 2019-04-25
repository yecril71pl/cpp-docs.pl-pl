---
title: Klasa IOleControlImpl
ms.date: 11/04/2016
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
ms.openlocfilehash: 50119d21b041f37f03ca416a9a56ca9e29ae3344
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276799"
---
# <a name="iolecontrolimpl-class"></a>Klasa IOleControlImpl

Ta klasa udostępnia domyślną implementację elementu `IOleControl` interfejsu i implementuje `IUnknown`.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IOleControlImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|Wskazuje, czy kontener ignoruje lub akceptuje zdarzeń formantu.|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Kopiuje informacje o zachowanie klawiatury formantu. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informuje o kontrolce przynajmniej jedna z właściwości otoczenia kontenera został zmieniony. Implementacja biblioteki ATL, zwraca wartość S_OK.|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informuje o kontrolki użytkownik naciśnie określony naciśnięcia klawisza. Implementacja biblioteki ATL zwraca E_NOTIMPL.|

## <a name="remarks"></a>Uwagi

Klasa `IOleControlImpl` udostępnia domyślną implementację elementu [IOleControl](/windows/desktop/api/ocidl/nn-ocidl-iolecontrol) interfejsu i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.

**Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="freezeevents"></a>  IOleControlImpl::FreezeEvents

W implementacji ATL `FreezeEvents` zwiększa Twojej klasy kontrolki `m_nFreezeEvents` element członkowski danych Jeśli `bFreeze` jest PRAWDA, a także zmniejsza `m_nFreezeEvents` Jeśli `bFreeze` ma wartość FALSE.

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Uwagi

`FreezeEvents` następnie zwraca wartość S_OK.

Zobacz [IOleControl::FreezeEvents](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-freezeevents) w Windows SDK.

##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo

Kopiuje informacje o zachowanie klawiatury formantu.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleControl:GetControlInfo](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Returns E_NOTIMPL.

##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange

Informuje o kontrolce przynajmniej jedna z właściwości otoczenia kontenera został zmieniony.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IOleControl::OnAmbientPropertyChange](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) w Windows SDK.

##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic

Informuje o kontrolki użytkownik naciśnie określony naciśnięcia klawisza.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Wartość zwracana

Returns E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IOleControl::OnMnemonic](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)<br/>
[Interfejsy kontrolki ActiveX](/windows/desktop/com/activex-controls-interfaces)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
