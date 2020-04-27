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
ms.openlocfilehash: fd94d0d6fe43d80b45def3f747c7b7d558de31d4
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167880"
---
# <a name="catlpreviewctrlimpl-class"></a>Klasa CAtlPreviewCtrlImpl

Ta klasa jest implementacją ATL okna, która jest umieszczana w oknie hosta dostarczonym przez powłokę dla bogatej wersji zapoznawczej.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl](#dtor)|Destruktory obiektu kontroli wersji zapoznawczej.|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Konstruuje obiekt kontrolki podglądu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl:: Create](#create)|Wywoływane przez zaawansowaną procedurę obsługi podglądu do utworzenia okna systemu Windows.|
|[CAtlPreviewCtrlImpl::D Estroy](#destroy)|Wywoływane przez zaawansowaną procedurę obsługi podglądu, gdy trzeba zniszczyć tę kontrolkę.|
|[CAtlPreviewCtrlImpl:: Focus](#focus)|Ustawia fokus wprowadzania dla tego formantu.|
|[CAtlPreviewCtrlImpl:: OnPaint](#onpaint)|Obsługuje komunikat WM_PAINT.|
|[CAtlPreviewCtrlImpl:: redraw](#redraw)|Informuje tę kontrolkę o ponownym narysowaniu.|
|[CAtlPreviewCtrlImpl:: SetHost](#sethost)|Ustawia nowy element nadrzędny dla tej kontrolki.|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Wywoływana przez zaawansowaną procedurę obsługi podglądu, gdy musi ona ustawiać wizualizacje zawartości bogatej wersji zapoznawczej.|
|[CAtlPreviewCtrlImpl:: SetRect](#setrect)|Ustawia nowy prostokąt ograniczający dla tej kontrolki.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::D oPaint](#dopaint)|Wywoływane przez platformę w celu renderowania wersji zapoznawczej.|

### <a name="protected-constants"></a>Chronione stałe

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl:: m_plf](#m_plf)|Czcionka używana do wyświetlania tekstu w oknie podglądu.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl:: m_clrBack](#m_clrback)|Kolor tła okna podglądu.|
|[CAtlPreviewCtrlImpl:: m_clrText](#m_clrtext)|Kolor tekstu okna podglądu.|

## <a name="remarks"></a>Uwagi

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`TBase`

`ATL::CMessageMap`

`ATL::CWindowImplRoot<TBase>`

`ATL::CWindowImplBaseT<TBase,TWinTraits>`

[ATL:: CWindowImpl\<CAtlPreviewCtrlImpl>](../../atl/reference/cwindowimpl-class.md)

`IPreviewCtrl`

`ATL::CAtlPreviewCtrlImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlpreviewctrlimpl. h

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

Konstruuje obiekt kontrolki podglądu.

```cpp
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="dtor"></a>CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl

Destruktory obiektu kontroli wersji zapoznawczej.

```cpp
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplcreate"></a><a name="create"></a>CAtlPreviewCtrlImpl:: Create

Wywoływane przez zaawansowaną procedurę obsługi podglądu do utworzenia okna systemu Windows.

```cpp
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Dojście do okna hosta dostarczone przez powłokę do rozbudowanej wersji zapoznawczej.

*Republika*<br/>
Określa początkowy rozmiar i położenie okna.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimpldestroy"></a><a name="destroy"></a>CAtlPreviewCtrlImpl::D Estroy

Wywoływane przez zaawansowaną procedurę obsługi podglądu, gdy trzeba zniszczyć tę kontrolkę.

```cpp
virtual void Destroy();
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimpldopaint"></a><a name="dopaint"></a>CAtlPreviewCtrlImpl::D oPaint

Wywoływane przez platformę w celu renderowania wersji zapoznawczej.

```cpp
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>Parametry

*używający HDC*<br/>
Uchwyt do kontekstu urządzenia do malowania.

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplfocus"></a><a name="focus"></a>CAtlPreviewCtrlImpl:: Focus

Ustawia fokus wprowadzania dla tego formantu.

```cpp
virtual void Focus();
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplm_clrback"></a><a name="m_clrback"></a>CAtlPreviewCtrlImpl:: m_clrBack

Kolor tła okna podglądu.

```cpp
COLORREF m_clrBack;
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplm_clrtext"></a><a name="m_clrtext"></a>CAtlPreviewCtrlImpl:: m_clrText

Kolor tekstu okna podglądu.

```cpp
COLORREF m_clrText;
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplm_plf"></a><a name="m_plf"></a>CAtlPreviewCtrlImpl:: m_plf

Czcionka używana do wyświetlania tekstu w oknie podglądu.

```cpp
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplonpaint"></a><a name="onpaint"></a>CAtlPreviewCtrlImpl:: OnPaint

Obsługuje komunikat WM_PAINT.

```cpp
LRESULT OnPaint(
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Ustaw na WM_PAINT.

*wParam*<br/>
Ten parametr nie jest używany.

*lParam*<br/>
Ten parametr nie jest używany.

*bHandled*<br/>
Gdy ta funkcja zwraca, zawiera wartość TRUE.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość 0.

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplredraw"></a><a name="redraw"></a>CAtlPreviewCtrlImpl:: redraw

Informuje tę kontrolkę o ponownym narysowaniu.

```cpp
virtual void Redraw();
```

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplsethost"></a><a name="sethost"></a>CAtlPreviewCtrlImpl:: SetHost

Ustawia nowy element nadrzędny dla tej kontrolki.

```cpp
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Uchwyt do nowego okna nadrzędnego.

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals

Wywoływana przez zaawansowaną procedurę obsługi podglądu, gdy musi ona ustawiać wizualizacje zawartości bogatej wersji zapoznawczej.

```cpp
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>Parametry

*clrBack*<br/>
Kolor tła okna podglądu.

*clrText*<br/>
Kolor tekstu okna podglądu.

*plf*<br/>
Czcionka używana do wyświetlania tekstu w oknie podglądu.

### <a name="remarks"></a>Uwagi

## <a name="catlpreviewctrlimplsetrect"></a><a name="setrect"></a>CAtlPreviewCtrlImpl:: SetRect

Ustawia nowy prostokąt ograniczający dla tej kontrolki.

```cpp
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>Parametry

*Republika*<br/>
Określa nowy rozmiar i położenie kontrolki podglądu.

*bRedraw*<br/>
Określa, czy kontrolka ma być odświeżana.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)
