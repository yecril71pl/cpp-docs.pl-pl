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
ms.openlocfilehash: 229b8c6803aa7b3817cb3d95474bde0502829f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326450"
---
# <a name="ipointerinactiveimpl-class"></a>Klasa IPointerInactiveImpl

Ta klasa `IUnknown` implementuje i [iPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) metody interfejsu.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IPointerInactiveImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Pobiera bieżące zasady aktywacji obiektu. Implementacja ATL zwraca E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Powiadamia obiekt, że wskaźnik myszy został przeniesiony nad nim, wskazując obiekt może uruchamiać zdarzenia myszy. Implementacja ATL zwraca E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Ustawia wskaźnik myszy dla nieaktywnego obiektu. Implementacja ATL zwraca E_NOTIMPL.|

## <a name="remarks"></a>Uwagi

Obiekt nieaktywny to obiekt, który jest po prostu ładowany lub uruchomiony. W przeciwieństwie do aktywnego obiektu nieaktywny obiekt nie może odbierać komunikatów myszy i klawiatury systemu Windows. W związku z tym nieaktywne obiekty zużywają mniej zasobów i są zazwyczaj bardziej wydajne.

Interfejs [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) umożliwia obiektowi obsługę minimalnego poziomu interakcji myszy, pozostając nieaktywnym. Ta funkcja jest szczególnie przydatna w przypadku formantów.

Klasa `IPointerInactiveImpl` implementuje `IPointerInactive` metody po prostu zwracając E_NOTIMPL. Jednak implementuje, `IUnknown` wysyłając informacje do urządzenia zrzutu w kompilacjach debugowania.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="ipointerinactiveimplgetactivationpolicy"></a><a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy

Pobiera bieżące zasady aktywacji obiektu.

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IPointerInactive::GetActivationPolicy](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) w usłudze Windows SDK.

## <a name="ipointerinactiveimploninactivemousemove"></a><a name="oninactivemousemove"></a>IPointerInactiveImpl::OnInactiveMouseMove

Powiadamia obiekt, że wskaźnik myszy został przeniesiony nad nim, wskazując obiekt może uruchamiać zdarzenia myszy.

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

Zobacz [IPointerInactive::OnInactiveMouseMove](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) w pliku SDK systemu Windows.

## <a name="ipointerinactiveimploninactivesetcursor"></a><a name="oninactivesetcursor"></a>IPointerInactiveImpl::OnInactiveSetCursor

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

Zobacz [IPointerInactive::OnInactiveSetCursor](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
