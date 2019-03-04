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
ms.openlocfilehash: 71c50771889381ad2288637c23930103b5925a2c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283272"
---
# <a name="catlpreviewctrlimpl-class"></a>Klasa CAtlPreviewCtrlImpl

Ta klasa jest implementacją ATL okna, które jest umieszczone na oknie hosta zapewnionym przez powłokę podglądu sformatowanego.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::~CAtlPreviewCtrlImpl](#dtor)|Destructs obiekt formantu (wersja zapoznawcza).|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Tworzy obiekt formantu (wersja zapoznawcza).|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::Create](#create)|Metoda wywoływana przez program obsługi podglądu sformatowanego można utworzyć okna Windows.|
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|Metoda wywoływana przez program obsługi podglądu sformatowanego kiedy zachodzi potrzeba zniszczyć tej kontrolki.|
|[CAtlPreviewCtrlImpl::Focus](#focus)|Zestawy danych wejściowych fokus do tego formantu.|
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|Obsługuje komunikat WM_PAINT.|
|[CAtlPreviewCtrlImpl::Redraw](#redraw)|Zawiera informacje dla tego formantu, aby odświeżyć.|
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|Ustawia nowy element nadrzędny dla tego formantu.|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Metoda wywoływana przez program obsługi podglądu sformatowanego kiedy zachodzi potrzeba ustawić wizualizacje podglądu zawartości.|
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|Ustawia nowy prostokąt otaczający dla tego formantu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|Metoda wywoływana przez platformę, by renderować korzystania z wersji zapoznawczej.|

### <a name="protected-constants"></a>Stałe chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|Czcionka używana do wyświetlania tekstu w oknie podglądu.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|Kolor tła okna podglądu.|
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|Kolor tekstu w oknie podglądu.|

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

##  <a name="catlpreviewctrlimpl"></a>  CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

Tworzy obiekt formantu (wersja zapoznawcza).

```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>Uwagi

##  <a name="dtor"></a>  CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl

Destructs obiekt formantu (wersja zapoznawcza).

```
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>Uwagi

##  <a name="create"></a>  CAtlPreviewCtrlImpl::Create

Metoda wywoływana przez program obsługi podglądu sformatowanego można utworzyć okna Windows.

```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Dojście do okna hosta, dostarczone przez powłokę podglądu sformatowanego.

*Chińska Republika Ludowa*<br/>
Określa początkowy rozmiar i położenie okna.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="destroy"></a>  CAtlPreviewCtrlImpl::Destroy

Metoda wywoływana przez program obsługi podglądu sformatowanego kiedy zachodzi potrzeba zniszczyć tej kontrolki.

```
virtual void Destroy();
```

### <a name="remarks"></a>Uwagi

##  <a name="dopaint"></a>  CAtlPreviewCtrlImpl::DoPaint

Metoda wywoływana przez platformę, by renderować korzystania z wersji zapoznawczej.

```
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>Parametry

*hdc*<br/>
Dojście do kontekstu urządzenia dla malowania.

### <a name="remarks"></a>Uwagi

##  <a name="focus"></a>  CAtlPreviewCtrlImpl::Focus

Zestawy danych wejściowych fokus do tego formantu.

```
virtual void Focus();
```

### <a name="remarks"></a>Uwagi

##  <a name="m_clrback"></a>  CAtlPreviewCtrlImpl::m_clrBack

Kolor tła okna podglądu.

```
COLORREF m_clrBack;
```

### <a name="remarks"></a>Uwagi

##  <a name="m_clrtext"></a>  CAtlPreviewCtrlImpl::m_clrText

Kolor tekstu w oknie podglądu.

```
COLORREF m_clrText;
```

### <a name="remarks"></a>Uwagi

##  <a name="m_plf"></a>  CAtlPreviewCtrlImpl::m_plf

Czcionka używana do wyświetlania tekstu w oknie podglądu.

```
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>Uwagi

##  <a name="onpaint"></a>  CAtlPreviewCtrlImpl::OnPaint

Obsługuje komunikat WM_PAINT.

```
LRESULT OnPaint(
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Ustaw WM_PAINT.

*wParam*<br/>
Ten parametr nie jest używany.

*lParam*<br/>
Ten parametr nie jest używany.

*bHandled*<br/>
Gdy ta funkcja zwróci wartość, zawiera wartość TRUE.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość 0.

### <a name="remarks"></a>Uwagi

##  <a name="redraw"></a>  CAtlPreviewCtrlImpl::Redraw

Zawiera informacje dla tego formantu, aby odświeżyć.

```
virtual void Redraw();
```

### <a name="remarks"></a>Uwagi

##  <a name="sethost"></a>  CAtlPreviewCtrlImpl::SetHost

Ustawia nowy element nadrzędny dla tego formantu.

```
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Dojście do nowego okna nadrzędnego.

### <a name="remarks"></a>Uwagi

##  <a name="setpreviewvisuals"></a>  CAtlPreviewCtrlImpl::SetPreviewVisuals

Metoda wywoływana przez program obsługi podglądu sformatowanego kiedy zachodzi potrzeba ustawić wizualizacje podglądu zawartości.

```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>Parametry

*clrBack*<br/>
Kolor tła okna podglądu.

*clrText*<br/>
Kolor tekstu w oknie podglądu.

*plf*<br/>
Czcionka używana do wyświetlania tekstu w oknie podglądu.

### <a name="remarks"></a>Uwagi

##  <a name="setrect"></a>  CAtlPreviewCtrlImpl::SetRect

Ustawia nowy prostokąt otaczający dla tego formantu.

```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>Parametry

*Chińska Republika Ludowa*<br/>
Określa nowy rozmiar i położenie formantu w wersji zapoznawczej.

*bRedraw*<br/>
Określa, czy formant powinien być narysowany ponownie.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)
