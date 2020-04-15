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
ms.openlocfilehash: 947ec16e91b99cc42cff90abe7df4a5d13576e98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329622"
---
# <a name="iolecontrolimpl-class"></a>Klasa IOleControlImpl

Ta klasa zapewnia domyślną `IOleControl` implementację `IUnknown`interfejsu i implementuje .

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IOleControlImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|Wskazuje, czy kontener ignoruje lub akceptuje zdarzenia z formantu.|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Wypełnia informacje o zachowaniu klawiatury formantu. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleControlImpl::OnAmbientPropertyZmienienie](#onambientpropertychange)|Informuje formant, że jedna lub więcej właściwości otoczenia kontenera uległa zmianie. Implementacja ATL zwraca S_OK.|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informuje formant, że użytkownik nacisnął określone naciśnięcie klawisza. Implementacja ATL zwraca E_NOTIMPL.|

## <a name="remarks"></a>Uwagi

Klasa `IOleControlImpl` zapewnia domyślną implementację interfejsu [IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol) i implementuje, `IUnknown` wysyłając informacje do urządzenia zrzutu w kompilacjach debugowania.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="iolecontrolimplfreezeevents"></a><a name="freezeevents"></a>IOleControlImpl::FreezeEvents

W implementacji ATL `FreezeEvents` zwiększa element członkowski `m_nFreezeEvents` danych klasy `bFreeze` kontrolnej, jeśli `m_nFreezeEvents` jest `bFreeze` TRUE, i zmniejsza, jeśli jest FALSE.

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Uwagi

`FreezeEvents`następnie zwraca S_OK.

Zobacz [IOleControl::FreezeEvents](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) w windows SDK.

## <a name="iolecontrolimplgetcontrolinfo"></a><a name="getcontrolinfo"></a>IOleControlImpl::GetControlInfo

Wypełnia informacje o zachowaniu klawiatury formantu.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleControl:GetControlInfo](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

## <a name="iolecontrolimplonambientpropertychange"></a><a name="onambientpropertychange"></a>IOleControlImpl::OnAmbientPropertyZmienienie

Informuje formant, że jedna lub więcej właściwości otoczenia kontenera uległa zmianie.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IOleControl::OnAmbientPropertyChange](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) w windows SDK.

## <a name="iolecontrolimplonmnemonic"></a><a name="onmnemonic"></a>IOleControlImpl::OnMnemonic

Informuje formant, że użytkownik nacisnął określone naciśnięcie klawisza.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IOleControl::OnMnemonic](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) w windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)<br/>
[Interfejsy sterowania ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
