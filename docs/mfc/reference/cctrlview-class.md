---
title: Klasa CCtrlView
ms.date: 11/04/2016
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
ms.openlocfilehash: f77f1c265920bd160da790647ef754c55e6dbda3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369355"
---
# <a name="cctrlview-class"></a>Klasa CCtrlView

Dostosowuje architekturę widoku dokumentu do typowych formantów obsługiwanych przez systemy Windows 98 i Windows NT w wersji 3.51 lub nowszej.

## <a name="syntax"></a>Składnia

```
class CCtrlView : public CView
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCtrlView::CCtrlView](#cctrlview)|Konstruuje `CCtrlView` obiekt.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CCtrlView::OnDraw](#ondraw)|Wywoływane przez strukturę do rysowania przy użyciu kontekstu określonego urządzenia.|
|[CCtrlView::PreCreateWindow](#precreatewindow)|Wywoływane przed utworzeniem okna systemu `CCtrlView` Windows dołączonego do tego obiektu.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Zawiera domyślny styl klasy widoku.|
|[CCtrlView::m_strClass](#m_strclass)|Zawiera nazwę klasy systemu Windows dla klasy widoku.|

## <a name="remarks"></a>Uwagi

Klasa `CCtrlView` i jej pochodne, [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md)i [CRichEditView](../../mfc/reference/cricheditview-class.md), dostosowują architekturę widoku dokumentu do nowych wspólnych formantów obsługiwanych przez systemy Windows 95/98 i Windows NT w wersjach 3.51 i nowszych. Aby uzyskać więcej informacji na temat architektury widoku dokumentu, zobacz [Architektura dokumentu/widoku](../../mfc/document-view-architecture.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cctrlviewcctrlview"></a><a name="cctrlview"></a>CCtrlView::CCtrlView

Konstruuje `CCtrlView` obiekt.

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*lpszClass (klasa)*<br/>
Nazwa klasy systemu Windows klasy widoku.

*Dwstyle*<br/>
Styl klasy widoku.

### <a name="remarks"></a>Uwagi

Struktura wywołuje konstruktora, gdy zostanie utworzone nowe okno ramki lub okno jest dzielone. Zastąp [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) zainicjować widok po dołączeniu dokumentu. Wywołanie [CWnd::Create](../../mfc/reference/cwnd-class.md#create) lub [CWnd::CreateEx,](../../mfc/reference/cwnd-class.md#createex) aby utworzyć obiekt systemu Windows.

## <a name="cctrlviewm_strclass"></a><a name="m_strclass"></a>CCtrlView::m_strClass

Zawiera nazwę klasy systemu Windows dla klasy widoku.

```
CString m_strClass;
```

## <a name="cctrlviewm_dwdefaultstyle"></a><a name="m_dwdefaultstyle"></a>CCtrlView::m_dwDefaultStyle

Zawiera domyślny styl klasy widoku.

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>Uwagi

Ten styl jest stosowany podczas tworzenia okna.

## <a name="cctrlviewondraw"></a><a name="ondraw"></a>CCtrlView::OnDraw

Wywoływane przez strukturę do `CCtrlView` rysowania zawartości obiektu przy użyciu kontekstu określonego urządzenia.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia, w którym występuje rysunek.

### <a name="remarks"></a>Uwagi

`OnDraw`jest zazwyczaj wywoływana do wyświetlania ekranu, przekazując kontekst urządzenia ekranu określony przez *pDC*.

## <a name="cctrlviewprecreatewindow"></a><a name="precreatewindow"></a>CCtrlView::PreCreateWindow

Wywoływane przed utworzeniem okna systemu `CWnd` Windows dołączonego do tego obiektu.

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parametry

*Cs*<br/>
Struktura [CREATESTRUCT.](/windows/win32/api/winuser/ns-winuser-createstructw)

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli tworzenie okna powinno być kontynuowane; 0, aby wskazać niepowodzenie tworzenia.

### <a name="remarks"></a>Uwagi

Nigdy nie należy wywoływać tej funkcji bezpośrednio.

Domyślna implementacja tej funkcji sprawdza nazwę klasy okna NULL i zastępuje odpowiednią wartość domyślną. Zastąpokaj tę `CREATESTRUCT` funkcję elementu członkowskiego, aby zmodyfikować strukturę przed utworzeniem okna.

Każda klasa pochodząca z `CCtrlView` dodaje własną funkcjonalność do `PreCreateWindow`jego zastąpienia . Zgodnie z projektem `PreCreateWindow` te pochodne nie są udokumentowane. Aby określić style odpowiednie dla każdej klasy i współzależności między stylami, można sprawdzić kod źródłowy MFC dla klasy podstawowej aplikacji. Jeśli zdecydujesz się zastąpić, można określić, czy style używane w klasie podstawowej aplikacji zapewniają funkcje, `PreCreateWindow`których potrzebujesz przy użyciu informacji zebranych z kodu źródłowego MFC.

Aby uzyskać więcej informacji na temat zmieniania stylów okien, zobacz [Zmienianie stylów okna utworzonego przez MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Zobacz też

[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CTreeView](../../mfc/reference/ctreeview-class.md)<br/>
[Klasa CListView](../../mfc/reference/clistview-class.md)<br/>
[Klasa CRichEditView](../../mfc/reference/cricheditview-class.md)
