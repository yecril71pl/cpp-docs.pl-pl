---
title: IPointerInactiveImpl Class
ms.date: 11/04/2016
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
ms.openlocfilehash: d7d9f048fceb3a569b024d7fe2b87f30a828b68e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266838"
---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl Class

Ta klasa implementuje `IUnknown` i [IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive) metody interfejsu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IPointerInactiveImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Pobiera bieżące zasady aktywacji dla obiektu. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Powiadamia obiekt, który wskaźnik myszy zostanie przesunięty nad, wskazujące obiekt może wyzwalać zdarzeń myszy. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Ustawia kursor nieaktywnym obiektem. Implementacja biblioteki ATL zwraca E_NOTIMPL.|

## <a name="remarks"></a>Uwagi

Nieaktywne obiekt jest taki, który jest po prostu załadowane lub nie działa. W przeciwieństwie do aktywnego obiektu nieaktywnym obiektem nie może odbierać komunikaty myszy i klawiatury Windows. Dlatego obiektów nieaktywnych wykorzystuje mniej zasobów i są zwykle bardziej wydajne.

[IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive) interfejs umożliwia obiektu do obsługi minimalny poziom interakcji z myszą przy pozostałe nieaktywne. Ta funkcja jest szczególnie użyteczna w przypadku kontrolek.

Klasa `IPointerInactiveImpl` implementuje `IPointerInactive` metody powracając po prostu E_NOTIMPL. Jednak implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.

**Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="getactivationpolicy"></a>  IPointerInactiveImpl::GetActivationPolicy

Pobiera bieżące zasady aktywacji dla obiektu.

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>Wartość zwracana

Returns E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IPointerInactive::GetActivationPolicy](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) w Windows SDK.

##  <a name="oninactivemousemove"></a>  IPointerInactiveImpl::OnInactiveMouseMove

Powiadamia obiekt, który wskaźnik myszy zostanie przesunięty nad, wskazujące obiekt może wyzwalać zdarzeń myszy.

```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```

### <a name="return-value"></a>Wartość zwracana

Returns E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IPointerInactive::OnInactiveMouseMove](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) w Windows SDK.

##  <a name="oninactivesetcursor"></a>  IPointerInactiveImpl::OnInactiveSetCursor

Ustawia kursor nieaktywnym obiektem.

```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```

### <a name="return-value"></a>Wartość zwracana

Returns E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IPointerInactive::OnInactiveSetCursor](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
