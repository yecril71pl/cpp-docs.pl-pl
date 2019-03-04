---
title: Klasa CDialogEx
ms.date: 11/04/2016
f1_keywords:
- CDialogEx
- AFXDIALOGEX/CDialogEx
- AFXDIALOGEX/CDialogEx::CDialogEx
- AFXDIALOGEX/CDialogEx::SetBackgroundColor
- AFXDIALOGEX/CDialogEx::SetBackgroundImage
helpviewer_keywords:
- CDialogEx [MFC], CDialogEx
- CDialogEx [MFC], SetBackgroundColor
- CDialogEx [MFC], SetBackgroundImage
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
ms.openlocfilehash: f92058d1aa0dabccf6623d20a248fed8eb99ab26
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266318"
---
# <a name="cdialogex-class"></a>Klasa CDialogEx

`CDialogEx` Klasa określa kolor tła i obraz tła okna dialogowego.

## <a name="syntax"></a>Składnia

```
class CDialogEx : public CDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDialogEx::CDialogEx](#cdialogex)|Konstruuje `CDialogEx` obiektu.|
|`CDialogEx::~CDialogEx`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDialogEx::SetBackgroundColor](#setbackgroundcolor)|Ustawia kolor tła okna dialogowego.|
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|Ustawia obraz tła okna dialogowego.|

## <a name="remarks"></a>Uwagi

Aby użyć `CDialogEx` klasy, pochodzi z klasy okien dialogowych pole z `CDialogEx` klasy zamiast `CDialog` klasy.

Okno dialogowe pola obrazy są przechowywane w pliku zasobów. Struktura automatycznie usuwa dowolny obraz, który jest ładowany z pliku zasobów. Aby programowo usunąć bieżący obraz tła, wywołaj [CDialogEx::SetBackgroundImage](#setbackgroundimage) metody lub zaimplementuj `OnDestroy` programu obsługi zdarzeń. Gdy wywołujesz [CDialogEx::SetBackgroundImage](#setbackgroundimage) metody, Przekaż `HBITMAP` parametru jako uchwyt obrazu. `CDialogEx` Obiekt będzie przejęcie na własność obrazu i usuń go, jeśli `m_bAutoDestroyBmp` flaga jest `TRUE`.

A `CDialogEx` obiekt może być elementem nadrzędnym [klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) obiektu. [Klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) obiektu wywołania `CDialogEx::SetActiveMenu` metody podczas [klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) obiektu zostanie otwarta. W efekcie `CDialogEx` obiektów obsługuje wszystkie zdarzenia menu, aż do [klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) obiekt jest zamknięty.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdialogex.h

##  <a name="cdialogex"></a>  CDialogEx::CDialogEx

Konstruuje `CDialogEx` obiektu.

```
CDialogEx(
    UINT nIDTemplate,
    CWnd* pParent=NULL);

CDialogEx(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd=NULL);
```

### <a name="parameters"></a>Parametry

*nIDTemplate*<br/>
[in] Identyfikator zasobu szablonu okna dialogowego.

*lpszTemplateName*<br/>
[in] Nazwa zasobu szablonu okna dialogowego.

*pParent*<br/>
[in] Wskaźnik do okna nadrzędnego. Wartością domyślną jest NULL.

*pParentWnd*<br/>
[in] Wskaźnik do okna nadrzędnego. Wartością domyślną jest NULL.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="setbackgroundcolor"></a>  CDialogEx::SetBackgroundColor

Ustawia kolor tła okna dialogowego.

```
void SetBackgroundColor(
    COLORREF color,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
[in] Wartość koloru RGB.

*bRepaint*<br/>
[in] Wartość TRUE, aby natychmiast zaktualizować ekran; w przeciwnym razie wartość FALSE. Wartość domyślna to TRUE.

### <a name="remarks"></a>Uwagi

##  <a name="setbackgroundimage"></a>  CDialogEx::SetBackgroundImage

Ustawia obraz tła okna dialogowego.

```
void SetBackgroundImage(
    HBITMAP hBitmap,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bAutoDestroy=TRUE,
    BOOL bRepaint=TRUE);

BOOL SetBackgroundImage(
    UINT uiBmpResId,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
[in] Dojście do obrazu tła.

*uiBmpResId*<br/>
[in] Identyfikator zasobu obrazu tła.

*location*<br/>
[in] Jedną z `CDialogEx::BackgroundLocation` wartości, które określają lokalizację obrazu. Prawidłowe wartości to BACKGR_TILE, BACKGR_TOPLEFT, BACKGR_TOPRIGHT, BACKGR_BOTTOMLEFT i BACKGR_BOTTOMRIGHT. Wartość domyślna to BACKGR_TILE.

*bAutoDestroy*<br/>
[in] Wartość TRUE, aby automatycznie zniszczyć obrazu tła. w przeciwnym razie wartość FALSE.

*bRepaint*<br/>
[in] Wartość TRUE, aby natychmiast odświeżyć okno dialogowe; w przeciwnym razie wartość FALSE.

### <a name="return-value"></a>Wartość zwracana

W drugiej metodzie przeciążenia składni, wartość TRUE jeśli metoda się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Obraz, który określisz nie jest rozciągnięty do rozmiaru obszaru klienckiego okna dialogowego pole.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)<br/>
[Klasa CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)
