---
title: Klasa CCtrlView | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
dev_langs:
- C++
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84261c2f5b2c913d2096d2b8878886125f6c0243
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380135"
---
# <a name="cctrlview-class"></a>Klasa CCtrlView

Dostosowuje architekturę widoku dokumentu do typowych kontrolek obsługiwanych przez wersje Windows 98 i Windows NT 3.51 lub nowszej.

## <a name="syntax"></a>Składnia

```
class CCtrlView : public CView
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCtrlView::CCtrlView](#cctrlview)|Konstruuje `CCtrlView` obiektu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CCtrlView::OnDraw](#ondraw)|Metoda wywoływana przez platformę, by narysować w kontekście określonego urządzenia.|
|[CCtrlView::PreCreateWindow](#precreatewindow)|Wywołuje się przed tworzeniem okna Windows dołączona do tego `CCtrlView` obiektu.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Zawiera domyślnego stylu dla klasy widoku.|
|[CCtrlView::m_strClass](#m_strclass)|Zawiera nazwę klasy Windows dla klasy widoku.|

## <a name="remarks"></a>Uwagi

Klasa `CCtrlView` i jego pochodne [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md), i [CRichEditView](../../mfc/reference/cricheditview-class.md), dostosowania architektury dokumentu widoku, aby nowe formanty wspólne obsługiwane przez Windows 95/98 i Windows NT w wersji 3.51 lub nowszej. Aby uzyskać więcej informacji na temat architektury dokumentu widoku, zobacz [architektury dokument/widok](../../mfc/document-view-architecture.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="cctrlview"></a>  CCtrlView::CCtrlView

Konstruuje `CCtrlView` obiektu.

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*lpszClass*<br/>
Nazwa klasy Windows widoku klasy.

*dwStyle*<br/>
Styl widoku klasy.

### <a name="remarks"></a>Uwagi

Struktura wywołuje konstruktora, gdy stworzono nowe okno ramowe lub okno zostanie podzielona. Zastąp [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) zainicjować widoku po dołączeniu dokumentu. Wywołaj [CWnd::Create](../../mfc/reference/cwnd-class.md#create) lub [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex) można utworzyć obiektu Windows.

##  <a name="m_strclass"></a>  CCtrlView::m_strClass

Zawiera nazwę klasy Windows dla klasy widoku.

```
CString m_strClass;
```

##  <a name="m_dwdefaultstyle"></a>  CCtrlView::m_dwDefaultStyle

Zawiera domyślnego stylu dla klasy widoku.

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>Uwagi

Ten styl jest stosowana, gdy okno zostanie utworzony.

##  <a name="ondraw"></a>  CCtrlView::OnDraw

Wywoływane przez platformę, by narysować zawartość `CCtrlView` obiekt w kontekście określonego urządzenia.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Wskaźnik do kontekstu urządzenia, w której występuje rysunku.

### <a name="remarks"></a>Uwagi

`OnDraw` jest zwykle nazywany do wyświetlania na ekranie, przekazując kontekst urządzenia ekranu, określony przez *kontrolera pDC*.

##  <a name="precreatewindow"></a>  CCtrlView::PreCreateWindow

Wywołuje się przed tworzeniem okna Windows dołączona do tego `CWnd` obiektu.

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parametry

*CS*<br/>
A [CREATESTRUCT](https://msdn.microsoft.com/library/windows/desktop/ms632603) struktury.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli tworzenie okien powinno być kontynuowane; 0, aby wskazać błąd podczas tworzenia.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, nigdy nie bezpośrednio.

Domyślna implementacja ta funkcja sprawdza, czy nazwa klasy window o wartości NULL i zastępuje odpowiednią wartość domyślną. Zastąpienie tej funkcji elementu członkowskiego, aby zmodyfikować `CREATESTRUCT` struktury przed utworzeniem okna.

Każda klasa jest pochodną `CCtrlView` dodaje swoje własne funkcje do jego zastępowania metody `PreCreateWindow`. Zgodnie z projektem, te pochodne z `PreCreateWindow` nie są udokumentowane. Aby ustalić, style, które są odpowiednie dla każdej klasy i wzajemnych zależności między style, można sprawdzić MFC kod źródłowy dla klasy podstawowej aplikacji. Jeśli chcesz przesłonić `PreCreateWindow`, można określić, czy stylów używanych w klasie bazowej aplikacji zapewniają funkcje, korzystając z informacji zebranych w kodzie źródłowym MFC.

Aby uzyskać więcej informacji na temat Zmienianie stylów okna, zobacz [Zmienianie stylów okna utworzonego przez MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Zobacz też

[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CTreeView](../../mfc/reference/ctreeview-class.md)<br/>
[Klasa CListView](../../mfc/reference/clistview-class.md)<br/>
[Klasa CRichEditView](../../mfc/reference/cricheditview-class.md)
