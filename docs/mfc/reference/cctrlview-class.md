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
ms.openlocfilehash: 334f139b81afeb06d57cbd128abe9e413b1fd0e7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507147"
---
# <a name="cctrlview-class"></a>Klasa CCtrlView

Dostosowuje architekturę widoku dokumentu do wspólnych kontrolek obsługiwanych przez systemy Windows 98 i Windows NT w wersji 3,51 i nowszych.

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
|[CCtrlView:: OnDraw](#ondraw)|Wywoływane przez platformę do rysowania przy użyciu określonego kontekstu urządzenia.|
|[CCtrlView::P reCreateWindow](#precreatewindow)|Wywołuje się przed utworzeniem okna systemu Windows dołączonego do tego `CCtrlView` obiektu.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Zawiera domyślny styl klasy widoku.|
|[CCtrlView::m_strClass](#m_strclass)|Zawiera nazwę klasy systemu Windows dla klasy widoku.|

## <a name="remarks"></a>Uwagi

Klasa `CCtrlView` i jej pochodne, [elementu CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md)i [CRichEditView](../../mfc/reference/cricheditview-class.md)dostosowują architekturę widoku dokumentu do nowych wspólnych formantów obsługiwanych przez systemy Windows 95/98 i Windows NT w wersji 3,51 i nowszych. Aby uzyskać więcej informacji na temat architektury widoku dokumentu, zobacz temat [Architektura dokumentu/widoku](../../mfc/document-view-architecture.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="cctrlview"></a>CCtrlView::CCtrlView

Konstruuje `CCtrlView` obiekt.

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*lpszClass*<br/>
Nazwa klasy systemu Windows klasy widoku.

*dwStyle*<br/>
Styl klasy widoku.

### <a name="remarks"></a>Uwagi

Struktura wywołuje konstruktora po utworzeniu nowego okna ramki lub poddzieleniu okna. Przesłoń [CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) , aby zainicjować widok po dołączeniu dokumentu. Wywołanie [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) lub [CWnd:: CreateEx](../../mfc/reference/cwnd-class.md#createex) w celu utworzenia obiektu systemu Windows.

##  <a name="m_strclass"></a>CCtrlView::m_strClass

Zawiera nazwę klasy systemu Windows dla klasy widoku.

```
CString m_strClass;
```

##  <a name="m_dwdefaultstyle"></a>CCtrlView::m_dwDefaultStyle

Zawiera domyślny styl klasy widoku.

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>Uwagi

Ten styl jest stosowany podczas tworzenia okna.

##  <a name="ondraw"></a>CCtrlView:: OnDraw

Wywoływane przez platformę, by narysować zawartość `CCtrlView` obiektu przy użyciu określonego kontekstu urządzenia.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do kontekstu urządzenia, w którym występuje Rysowanie.

### <a name="remarks"></a>Uwagi

`OnDraw`jest zazwyczaj wywoływana do wyświetlania ekranu, przekazując kontekst urządzenia ekranu określony przez *PDC*.

##  <a name="precreatewindow"></a>CCtrlView::P reCreateWindow

Wywołuje się przed utworzeniem okna systemu Windows dołączonego do tego `CWnd` obiektu.

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parametry

*Rejestr*<br/>
Struktura [](/windows/win32/api/winuser/ns-winuser-createstructw) elementu.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli Tworzenie okna powinno być kontynuowane; 0, aby wskazać błąd tworzenia.

### <a name="remarks"></a>Uwagi

Nigdy nie wywołuj tej funkcji bezpośrednio.

Domyślna implementacja tej funkcji sprawdza nazwę klasy okna o wartości NULL i zastępuje odpowiednią wartość domyślną. Przesłoń tę funkcję elementu członkowskiego `CREATESTRUCT` , aby zmodyfikować strukturę przed utworzeniem okna.

Każda klasa, która `CCtrlView` dziedziczy z, dodaje własną funkcjonalność do `PreCreateWindow`zastąpienia. Zgodnie z `PreCreateWindow` projektem te pochodne nie są udokumentowane. Aby określić style odpowiednie dla każdej klasy i współzależności między stylami, można sprawdzić kod źródłowy MFC dla klasy podstawowej aplikacji. Jeśli zdecydujesz się przesłonić `PreCreateWindow`, możesz określić, czy style używane w klasie bazowej aplikacji zapewniają potrzebne funkcje, korzystając z informacji zebranych na podstawie kodu źródłowego MFC.

Aby uzyskać więcej informacji na temat zmieniania stylów okna, zobacz [Zmiana stylów okna utworzonego przez MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Zobacz także

[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CTreeView](../../mfc/reference/ctreeview-class.md)<br/>
[Klasa CListView](../../mfc/reference/clistview-class.md)<br/>
[Klasa CRichEditView](../../mfc/reference/cricheditview-class.md)
