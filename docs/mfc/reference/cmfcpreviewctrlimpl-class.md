---
title: Klasa CMFCPreviewCtrlImpl
ms.date: 11/04/2016
f1_keywords:
- CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::Create
- AFXWIN/CMFCPreviewCtrlImpl::Destroy
- AFXWIN/CMFCPreviewCtrlImpl::Focus
- AFXWIN/CMFCPreviewCtrlImpl::GetDocument
- AFXWIN/CMFCPreviewCtrlImpl::Redraw
- AFXWIN/CMFCPreviewCtrlImpl::SetDocument
- AFXWIN/CMFCPreviewCtrlImpl::SetHost
- AFXWIN/CMFCPreviewCtrlImpl::SetPreviewVisuals
- AFXWIN/CMFCPreviewCtrlImpl::SetRect
- AFXWIN/CMFCPreviewCtrlImpl::DoPaint
- AFXWIN/CMFCPreviewCtrlImpl::m_clrBackColor
- AFXWIN/CMFCPreviewCtrlImpl::m_clrTextColor
- AFXWIN/CMFCPreviewCtrlImpl::m_font
- AFXWIN/CMFCPreviewCtrlImpl::m_pDocument
helpviewer_keywords:
- CMFCPreviewCtrlImpl [MFC], CMFCPreviewCtrlImpl
- CMFCPreviewCtrlImpl [MFC], Create
- CMFCPreviewCtrlImpl [MFC], Destroy
- CMFCPreviewCtrlImpl [MFC], Focus
- CMFCPreviewCtrlImpl [MFC], GetDocument
- CMFCPreviewCtrlImpl [MFC], Redraw
- CMFCPreviewCtrlImpl [MFC], SetDocument
- CMFCPreviewCtrlImpl [MFC], SetHost
- CMFCPreviewCtrlImpl [MFC], SetPreviewVisuals
- CMFCPreviewCtrlImpl [MFC], SetRect
- CMFCPreviewCtrlImpl [MFC], DoPaint
- CMFCPreviewCtrlImpl [MFC], m_clrBackColor
- CMFCPreviewCtrlImpl [MFC], m_clrTextColor
- CMFCPreviewCtrlImpl [MFC], m_font
- CMFCPreviewCtrlImpl [MFC], m_pDocument
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
ms.openlocfilehash: 0c0a594a84b45ce7bf6f2c2fa5d1a547fa10eaa6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751846"
---
# <a name="cmfcpreviewctrlimpl-class"></a>Klasa CMFCPreviewCtrlImpl

Ta klasa implementuje okno, które jest umieszczane w oknie hosta dostarczonym przez Powłokę dla zaawansowanego podglądu.

## <a name="syntax"></a>Składnia

```
class CMFCPreviewCtrlImpl : public CWnd;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::~CMFCPreviewCtrlImpl](#dtor)|Niszczy obiekt kontrolny podglądu.|
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|Konstruuje obiekt kontrolny podglądu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::Tworzenie](#create)|Przeciążone. Wywoływane przez program obsługi rich preview, aby utworzyć okno systemu Windows.|
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|Wywoływany przez program obsługi rich preview, gdy musi zniszczyć ten formant.|
|[CMFCPreviewCtrlImpl::Focus](#focus)|Ustawia fokus danych wejściowych do tego formantu.|
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|Zwraca dokument połączony z tym kontrolką podglądu.|
|[CMFCPreviewCtrlImpl::Przerysuj](#redraw)|Mówi tej formancie, aby przerysować.|
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|Wywoływane przez program obsługi podglądu, aby utworzyć relację między implementacją dokumentu a formantem w wersji zapoznawczej.|
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|Ustawia nowy element nadrzędny dla tego formantu.|
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Wywoływana przez program obsługi rich preview, gdy musi ustawić wizualizacje zawartości rozszerzonego podglądu.|
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|Ustawia nowy prostokąt ograniczający dla tego formantu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|Wywoływane przez strukturę do renderowania wersji zapoznawczej.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|Kolor tła okna podglądu.|
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|Kolor tekstu okna podglądu.|
|[CMFCPreviewCtrlImpl::m_font](#m_font)|Czcionka używana do wyświetlania tekstu w oknie podglądu.|
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|Wskaźnik do dokumentu, którego zawartość jest podgląd w formancie.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="cmfcpreviewctrlimpl"></a>CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl

Konstruuje obiekt kontrolny podglądu.

### <a name="syntax"></a>Składnia

CMFCPreviewCtrlImpl();

## <a name="cmfcpreviewctrlimplcreate"></a><a name="create"></a>CMFCPreviewCtrlImpl::Tworzenie

Przeciążone. Wywoływane przez program obsługi rich preview, aby utworzyć okno systemu Windows.

### <a name="syntax"></a>Składnia

```
virtual BOOL Create(
   HWND hWndParent,
   const RECT* prc
);
virtual BOOL Create(
   HWND hWndParent,
   const RECT* prc,
   CCreateContext* pContext
);
```

### <a name="parameters"></a>Parametry

*hWndRodziciek*<br/>
Dojście do okna hosta dostarczone przez powłokę dla zaawansowanego podglądu.

*Chrl*<br/>
Określa początkowy rozmiar i położenie okna.

*Pcontext*<br/>
Wskaźnik do kontekstu tworzenia.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli utworzenie zakończyło się pomyślnie; w przeciwnym razie FALSE.

## <a name="cmfcpreviewctrlimpldestroy"></a><a name="destroy"></a>CMFCPreviewCtrlImpl::Destroy

Wywoływany przez program obsługi rich preview, gdy musi zniszczyć ten formant.

### <a name="syntax"></a>Składnia

```
virtual void Destroy();
```

## <a name="cmfcpreviewctrlimpldopaint"></a><a name="dopaint"></a>CMFCPreviewCtrlImpl::DoPaint

Wywoływane przez strukturę do renderowania wersji zapoznawczej.

### <a name="syntax"></a>Składnia

```
virtual void DoPaint(
   CPaintDC* pDC
);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia do malowania.

## <a name="cmfcpreviewctrlimplfocus"></a><a name="focus"></a>CMFCPreviewCtrlImpl::Focus

Ustawia fokus danych wejściowych do tego formantu.

### <a name="syntax"></a>Składnia

```
virtual void Focus();
```

## <a name="cmfcpreviewctrlimplgetdocument"></a><a name="getdocument"></a>CMFCPreviewCtrlImpl::GetDocument

Zwraca dokument połączony z tym kontrolką podglądu.

### <a name="syntax"></a>Składnia

```
ATL::IDocument* GetDocument();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do dokumentu, którego zawartość jest podgląd w formancie.

## <a name="cmfcpreviewctrlimplm_clrbackcolor"></a><a name="m_clrbackcolor"></a>CMFCPreviewCtrlImpl::m_clrBackColor

Kolor tła okna podglądu.

### <a name="syntax"></a>Składnia

```
COLORREF m_clrBackColor;
```

## <a name="cmfcpreviewctrlimplm_clrtextcolor"></a><a name="m_clrtextcolor"></a>CMFCPreviewCtrlImpl::m_clrTextColor

Kolor tekstu okna podglądu.

### <a name="syntax"></a>Składnia

```
COLORREF m_clrTextColor;
```

## <a name="cmfcpreviewctrlimplm_font--font-used-to-display-text-in-the-preview-window"></a><a name="m_font"></a>CMFCPreviewCtrlImpl::m_font Czcionka używana do wyświetlania tekstu w oknie podglądu.

### <a name="syntax"></a>Składnia

```
CFont m_font;
```

## <a name="cmfcpreviewctrlimplm_pdocument"></a><a name="m_pdocument"></a>CMFCPreviewCtrlImpl::m_pDocument

Wskaźnik do dokumentu, którego zawartość jest podgląd w formancie.

### <a name="syntax"></a>Składnia

```
ATL::IDocument* m_pDocument;
```

## <a name="cmfcpreviewctrlimplredraw"></a><a name="redraw"></a>CMFCPreviewCtrlImpl::Przerysuj

Mówi tej formancie, aby przerysować.

### <a name="syntax"></a>Składnia

```
virtual void Redraw();
```

## <a name="cmfcpreviewctrlimplsetdocument"></a><a name="setdocument"></a>CMFCPreviewCtrlImpl::SetDocument

Wywoływane przez program obsługi podglądu, aby utworzyć relację między implementacją dokumentu a formantem w wersji zapoznawczej.

### <a name="syntax"></a>Składnia

```cpp
void SetDocument(
   IDocument* pDocument
);
```

### <a name="parameters"></a>Parametry

*Pdocument*<br/>
Wskaźnik do implementacji dokumentu.

## <a name="cmfcpreviewctrlimplsethost"></a><a name="sethost"></a>CMFCPreviewCtrlImpl::SetHost

Ustawia nowy element nadrzędny dla tego formantu.

### <a name="syntax"></a>Składnia

```
virtual void SetHost(
   HWND hWndParent
);
```

### <a name="parameters"></a>Parametry

*hWndRodziciek*<br/>
Dojście do nowego okna nadrzędnego.

## <a name="cmfcpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CMFCPreviewCtrlImpl::SetPreviewVisuals

Wywoływana przez program obsługi rich preview, gdy musi ustawić wizualizacje zawartości rozszerzonego podglądu.

### <a name="syntax"></a>Składnia

```
virtual void SetPreviewVisuals(
   COLORREF clrBack,
   COLORREF clrText,
   const LOGFONTW *plf
);
```

### <a name="parameters"></a>Parametry

*clrBack (włask*<br/>
Kolor tła okna podglądu.

*clrTekst*<br/>
Kolor tekstu okna podglądu.

*Plf*<br/>
Czcionka używana do wyświetlania tekstu w oknie podglądu.

## <a name="cmfcpreviewctrlimplsetrect"></a><a name="setrect"></a>CMFCPreviewCtrlImpl::SetRect

Ustawia nowy prostokąt ograniczający dla tego formantu.

### <a name="syntax"></a>Składnia

```
virtual void SetRect(
   const RECT* prc,
   BOOL bRedraw
);
```

### <a name="parameters"></a>Parametry

*Chrl*<br/>
Określa nowy rozmiar i położenie formantu podglądu.

*bRedraw*<br/>
Określa, czy formant ma zostać ponownie narysowany.

### <a name="remarks"></a>Uwagi

Zazwyczaj nowy prostokąt ograniczający jest ustawiany po przesaniu kontrolki hosta.

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="dtor"></a>CMFCPreviewCtrlImpl::~CMFCPreviewCtrlImpl

Niszczy obiekt kontrolny podglądu.

### <a name="syntax"></a>Składnia

```
virtual ~CMFCPreviewCtrlImpl();
```
