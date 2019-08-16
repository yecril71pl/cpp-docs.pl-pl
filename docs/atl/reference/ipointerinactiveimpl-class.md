---
title: Klasa IPointerInactiveImpl
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
ms.openlocfilehash: 6fb5d9f2bcbdeda61f32947bf339d134c4924b72
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495657"
---
# <a name="ipointerinactiveimpl-class"></a>Klasa IPointerInactiveImpl

Ta klasa implementuje `IUnknown` metody interfejsu [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) .

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IPointerInactiveImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Pobiera bieżące zasady aktywacji dla obiektu. Implementacja ATL zwraca E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Powiadamia obiekt o przesunięciu wskaźnika myszy nad nim, wskazując, że obiekt może wyzwalać zdarzenia myszy. Implementacja ATL zwraca E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Ustawia wskaźnik myszy dla nieaktywnego obiektu. Implementacja ATL zwraca E_NOTIMPL.|

## <a name="remarks"></a>Uwagi

Obiekt nieaktywny to ten, który jest po prostu ładowany lub uruchomiony. W przeciwieństwie do aktywnego obiektu nieaktywny obiekt nie może odbierać komunikatów myszy i klawiatury systemu Windows. W ten sposób obiekty nieaktywne używają mniejszej ilości zasobów i są zwykle bardziej wydajne.

Interfejs [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) umożliwia obiektowi obsługę minimalnego poziomu interakcji myszy, podczas gdy pozostaje nieaktywna. Ta funkcja jest szczególnie przydatna w przypadku formantów.

`IPointerInactiveImpl` Klasa`IPointerInactive` implementuje metody przez po prostu zwrócenie E_NOTIMPL. Jest to jednak implementowane `IUnknown` przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

**Powiązane artykuły** [Samouczek ATL](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

##  <a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy

Pobiera bieżące zasady aktywacji dla obiektu.

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IPointerInactive:: GetActivationPolicy](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) w Windows SDK.

##  <a name="oninactivemousemove"></a>IPointerInactiveImpl::OnInactiveMouseMove

Powiadamia obiekt o przesunięciu wskaźnika myszy nad nim, wskazując, że obiekt może wyzwalać zdarzenia myszy.

```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IPointerInactive:: OnInactiveMouseMove](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) w Windows SDK.

##  <a name="oninactivesetcursor"></a>IPointerInactiveImpl::OnInactiveSetCursor

Ustawia wskaźnik myszy dla nieaktywnego obiektu.

```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IPointerInactive:: OnInactiveSetCursor](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
