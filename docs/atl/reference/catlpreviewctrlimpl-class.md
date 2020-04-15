---
title: Klasa CAtlPreviewCtrlImpl
ms.date: 11/04/2016
f1_keywords:
- CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Create
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Destroy
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Focus
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::OnPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Redraw
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetHost
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetPreviewVisuals
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetRect
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::DoPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_plf
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrBack
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrText
helpviewer_keywords:
- CAtlPreviewCtrlImpl class
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
ms.openlocfilehash: 1ccd01bc4d48dc088538f4799b595cce3fb910ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321368"
---
# <a name="catlpreviewctrlimpl-class"></a>Klasa CAtlPreviewCtrlImpl

Ta klasa jest implementacją ATL okna, które jest umieszczane w oknie hosta dostarczonym przez Shell for Rich Preview.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::~CAtlPreviewCtrlImpl](#dtor)|Niszczy obiekt kontrolny podglądu.|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Konstruuje obiekt kontrolny podglądu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::Tworzenie](#create)|Wywoływane przez program obsługi rich preview, aby utworzyć okno systemu Windows.|
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|Wywoływany przez program obsługi rich preview, gdy musi zniszczyć ten formant.|
|[CAtlPreviewCtrlImpl::Focus](#focus)|Ustawia fokus danych wejściowych do tego formantu.|
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|Obsługuje komunikat WM_PAINT.|
|[CAtlPreviewCtrlImpl::Przerysuj](#redraw)|Mówi tej formancie, aby przerysować.|
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|Ustawia nowy element nadrzędny dla tego formantu.|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Wywoływana przez program obsługi rich preview, gdy musi ustawić wizualizacje zawartości rozszerzonego podglądu.|
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|Ustawia nowy prostokąt ograniczający dla tego formantu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|Wywoływane przez strukturę do renderowania wersji zapoznawczej.|

### <a name="protected-constants"></a>Stałe chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|Czcionka używana do wyświetlania tekstu w oknie podglądu.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|Kolor tła okna podglądu.|
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|Kolor tekstu okna podglądu.|

## <a name="remarks"></a>Uwagi

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`TBase`

`ATL::CMessageMap`

`ATL::CWindowImplRoot<TBase>`

`ATL::CWindowImplBaseT<TBase,TWinTraits>`

[ATL::CWindowImpl\<CAtlPreviewCtrlImpl>](../../atl/reference/cwindowimpl-class.md)

`IPreviewCtrl`

`ATL::CAtlPreviewCtrlImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlpreviewctrlimpl.h

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

Konstruuje obiekt kontrolny podglądu.

```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="dtor"></a>CAtlPreviewCtrlImpl::~CAtlPreviewCtrlImpl

Niszczy obiekt kontrolny podglądu.

```
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplcreate"></a><a name="create"></a>CAtlPreviewCtrlImpl::Tworzenie

Wywoływane przez program obsługi rich preview, aby utworzyć okno systemu Windows.

```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>Parametry

*hWndRodziciek*<br/>
Dojście do okna hosta dostarczone przez powłokę dla zaawansowanego podglądu.

*Chrl*<br/>
Określa początkowy rozmiar i położenie okna.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimpldestroy"></a><a name="destroy"></a>CAtlPreviewCtrlImpl::Destroy

Wywoływany przez program obsługi rich preview, gdy musi zniszczyć ten formant.

```
virtual void Destroy();
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimpldopaint"></a><a name="dopaint"></a>CAtlPreviewCtrlImpl::DoPaint

Wywoływane przez strukturę do renderowania wersji zapoznawczej.

```
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>Parametry

*Hdc*<br/>
Dojście do kontekstu urządzenia do malowania.

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplfocus"></a><a name="focus"></a>CAtlPreviewCtrlImpl::Focus

Ustawia fokus danych wejściowych do tego formantu.

```
virtual void Focus();
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplm_clrback"></a><a name="m_clrback"></a>CAtlPreviewCtrlImpl::m_clrBack

Kolor tła okna podglądu.

```
COLORREF m_clrBack;
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplm_clrtext"></a><a name="m_clrtext"></a>CAtlPreviewCtrlImpl::m_clrText

Kolor tekstu okna podglądu.

```
COLORREF m_clrText;
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplm_plf"></a><a name="m_plf"></a>CAtlPreviewCtrlImpl::m_plf

Czcionka używana do wyświetlania tekstu w oknie podglądu.

```
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplonpaint"></a><a name="onpaint"></a>CAtlPreviewCtrlImpl::OnPaint

Obsługuje komunikat WM_PAINT.

```
LRESULT OnPaint(
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*Nmsg*<br/>
Ustaw WM_PAINT.

*Wparam*<br/>
Ten parametr nie jest używany.

*Lparam*<br/>
Ten parametr nie jest używany.

*bHandled (Obj.*<br/>
Gdy ta funkcja zwraca, zawiera wartość PRAWDA.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość 0.

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplredraw"></a><a name="redraw"></a>CAtlPreviewCtrlImpl::Przerysuj

Mówi tej formancie, aby przerysować.

```
virtual void Redraw();
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplsethost"></a><a name="sethost"></a>CAtlPreviewCtrlImpl::SetHost

Ustawia nowy element nadrzędny dla tego formantu.

```
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>Parametry

*hWndRodziciek*<br/>
Dojście do nowego okna nadrzędnego.

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals

Wywoływana przez program obsługi rich preview, gdy musi ustawić wizualizacje zawartości rozszerzonego podglądu.

```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>Parametry

*clrBack (włask*<br/>
Kolor tła okna podglądu.

*clrTekst*<br/>
Kolor tekstu okna podglądu.

*Plf*<br/>
Czcionka używana do wyświetlania tekstu w oknie podglądu.

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplsetrect"></a><a name="setrect"></a>CAtlPreviewCtrlImpl::SetRect

Ustawia nowy prostokąt ograniczający dla tego formantu.

```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>Parametry

*Chrl*<br/>
Określa nowy rozmiar i położenie formantu podglądu.

*bRedraw*<br/>
Określa, czy formant ma zostać ponownie narysowany.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)
