---
title: CMFCPreviewCtrlImpl Class
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
ms.openlocfilehash: f66ed8478023bd42e185da4f21740d1de2536140
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295750"
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl Class

Ta klasa implementuje okno, które jest umieszczone na oknie hosta zapewnionym przez powłokę podglądu sformatowanego.

## <a name="syntax"></a>Składnia

```
class CMFCPreviewCtrlImpl : public CWnd;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::~CMFCPreviewCtrlImpl](#dtor)|Destructs obiekt formantu (wersja zapoznawcza).|
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|Tworzy obiekt formantu (wersja zapoznawcza).|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::Create](#create)|Przeciążone. Metoda wywoływana przez program obsługi podglądu sformatowanego można utworzyć okna Windows.|
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|Metoda wywoływana przez program obsługi podglądu sformatowanego kiedy zachodzi potrzeba zniszczyć tej kontrolki.|
|[CMFCPreviewCtrlImpl::Focus](#focus)|Zestawy danych wejściowych fokus do tego formantu.|
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|Zwraca dokument podłączone do tego formantu (wersja zapoznawcza).|
|[CMFCPreviewCtrlImpl::Redraw](#redraw)|Zawiera informacje dla tego formantu, aby odświeżyć.|
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|Metoda wywoływana przez program obsługi (wersja zapoznawcza) można utworzyć relacji między implementacji dokumentu i kontrola wersji zapoznawczej.|
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|Ustawia nowy element nadrzędny dla tego formantu.|
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Metoda wywoływana przez program obsługi podglądu sformatowanego kiedy zachodzi potrzeba ustawić wizualizacje podglądu zawartości.|
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|Ustawia nowy prostokąt otaczający dla tego formantu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|Metoda wywoływana przez platformę, by renderować korzystania z wersji zapoznawczej.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|Kolor tła okna podglądu.|
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|Kolor tekstu w oknie podglądu.|
|[CMFCPreviewCtrlImpl::m_font](#m_font)|Czcionka używana do wyświetlania tekstu w oknie podglądu.|
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|Wskaźnik do dokumentu, w których zawartość jest przeglądany w formancie.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimpl"></a> CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl

Tworzy obiekt formantu (wersja zapoznawcza).

### <a name="syntax"></a>Składnia

CMFCPreviewCtrlImpl();

## <a name="create"></a> CMFCPreviewCtrlImpl::Create

Przeciążone. Metoda wywoływana przez program obsługi podglądu sformatowanego można utworzyć okna Windows.

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

*hWndParent*<br/>
Dojście do okna hosta, dostarczone przez powłokę podglądu sformatowanego.

*Chińska Republika Ludowa*<br/>
Określa początkowy rozmiar i położenie okna.

*pContext*<br/>
Wskaźnik do tworzenia kontekstu.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli tworzenie powiodło się; w przeciwnym razie wartość FALSE.

## <a name="destroy"></a> CMFCPreviewCtrlImpl::Destroy

Metoda wywoływana przez program obsługi podglądu sformatowanego kiedy zachodzi potrzeba zniszczyć tej kontrolki.

### <a name="syntax"></a>Składnia

```
virtual void Destroy();
```

## <a name="dopaint"></a> CMFCPreviewCtrlImpl::DoPaint

Metoda wywoływana przez platformę, by renderować korzystania z wersji zapoznawczej.

### <a name="syntax"></a>Składnia

```
virtual void DoPaint(
   CPaintDC* pDC
);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do kontekstu urządzenia dla malowania.

## <a name="focus"></a> CMFCPreviewCtrlImpl::Focus

Zestawy danych wejściowych fokus do tego formantu.

### <a name="syntax"></a>Składnia

```
virtual void Focus();
```

## <a name="getdocument"></a> CMFCPreviewCtrlImpl::GetDocument

Zwraca dokument podłączone do tego formantu (wersja zapoznawcza).

### <a name="syntax"></a>Składnia

```
ATL::IDocument* GetDocument();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do dokumentu, w których zawartość jest przeglądany w formancie.

## <a name="m_clrbackcolor"></a> CMFCPreviewCtrlImpl::m_clrBackColor

Kolor tła okna podglądu.

### <a name="syntax"></a>Składnia

```
COLORREF m_clrBackColor;
```

## <a name="m_clrtextcolor"></a> CMFCPreviewCtrlImpl::m_clrTextColor

Kolor tekstu w oknie podglądu.

### <a name="syntax"></a>Składnia

```
COLORREF m_clrTextColor;
```

## <a name="m_font"></a> Czcionka CMFCPreviewCtrlImpl::m_font wykorzystywany do wyświetlania tekstu w oknie podglądu.

### <a name="syntax"></a>Składnia

```
CFont m_font;
```

## <a name="m_pdocument"></a> CMFCPreviewCtrlImpl::m_pDocument

Wskaźnik do dokumentu, w których zawartość jest przeglądany w formancie.

### <a name="syntax"></a>Składnia

```
ATL::IDocument* m_pDocument;
```

## <a name="redraw"></a> CMFCPreviewCtrlImpl::Redraw

Zawiera informacje dla tego formantu, aby odświeżyć.

### <a name="syntax"></a>Składnia

```
virtual void Redraw();
```

## <a name="setdocument"></a> CMFCPreviewCtrlImpl::SetDocument

Metoda wywoływana przez program obsługi (wersja zapoznawcza) można utworzyć relacji między implementacji dokumentu i kontrola wersji zapoznawczej.

### <a name="syntax"></a>Składnia

```
void SetDocument(
   IDocument* pDocument
);
```

### <a name="parameters"></a>Parametry

*pDocument*<br/>
Wskaźnik do implementacji dokumentu.

## <a name="sethost"></a> CMFCPreviewCtrlImpl::SetHost

Ustawia nowy element nadrzędny dla tego formantu.

### <a name="syntax"></a>Składnia

```
virtual void SetHost(
   HWND hWndParent
);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Dojście do nowego okna nadrzędnego.

## <a name="setpreviewvisuals"></a> CMFCPreviewCtrlImpl::SetPreviewVisuals

Metoda wywoływana przez program obsługi podglądu sformatowanego kiedy zachodzi potrzeba ustawić wizualizacje podglądu zawartości.

### <a name="syntax"></a>Składnia

```
virtual void SetPreviewVisuals(
   COLORREF clrBack,
   COLORREF clrText,
   const LOGFONTW *plf
);
```

### <a name="parameters"></a>Parametry

*clrBack*<br/>
Kolor tła okna podglądu.

*clrText*<br/>
Kolor tekstu w oknie podglądu.

*plf*<br/>
Czcionka używana do wyświetlania tekstu w oknie podglądu.

##  <a name="setrect"></a> CMFCPreviewCtrlImpl::SetRect

Ustawia nowy prostokąt otaczający dla tego formantu.

### <a name="syntax"></a>Składnia

```
virtual void SetRect(
   const RECT* prc,
   BOOL bRedraw
);
```

### <a name="parameters"></a>Parametry

*Chińska Republika Ludowa*<br/>
Określa nowy rozmiar i położenie formantu w wersji zapoznawczej.

*bRedraw*<br/>
Określa, czy formant powinien być narysowany ponownie.

### <a name="remarks"></a>Uwagi

Zazwyczaj nowy prostokąt otaczający jest ustawiona, gdy zmieni się rozmiar kontrolki hosta.

## <a name="dtor"></a> CMFCPreviewCtrlImpl::~CMFCPreviewCtrlImpl

Destructs obiekt formantu (wersja zapoznawcza).

### <a name="syntax"></a>Składnia

```
virtual ~CMFCPreviewCtrlImpl();
```
