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
ms.openlocfilehash: 717e560035d42957c16168097577d0c8c589e3c7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753349"
---
# <a name="cdialogex-class"></a>Klasa CDialogEx

Klasa `CDialogEx` określa kolor tła i obraz tła okna dialogowego.

## <a name="syntax"></a>Składnia

```
class CDialogEx : public CDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDialogEx::CDialogEx](#cdialogex)|Konstruuje `CDialogEx` obiekt.|
|`CDialogEx::~CDialogEx`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDialogEx::SetBackgroundColor](#setbackgroundcolor)|Ustawia kolor tła okna dialogowego.|
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|Ustawia obraz tła okna dialogowego.|

## <a name="remarks"></a>Uwagi

Aby użyć `CDialogEx` klasy, należy wyprowadzić klasę `CDialogEx` okna dialogowego `CDialog` z klasy zamiast klasy.

Obrazy okna dialogowego są przechowywane w pliku zasobów. Struktura automatycznie usuwa dowolny obraz, który jest ładowany z pliku zasobu. Aby programowo usunąć bieżący obraz tła, wywołaj [metodę CDialogEx::SetBackgroundImage](#setbackgroundimage) lub zaimplementuj `OnDestroy` program obsługi zdarzeń. Po wywołaniu [CDialogEx::SetBackgroundImage](#setbackgroundimage) metoda, `HBITMAP` przekazać w parametrze jako dojście obrazu. Obiekt `CDialogEx` przejmie na własność obraz i usunie go, jeśli flaga `m_bAutoDestroyBmp` jest `TRUE`.

Obiekt `CDialogEx` może być elementem nadrzędnym obiektu [CMFCPopupMenu Class.](../../mfc/reference/cmfcpopupmenu-class.md) [Obiekt klasy CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) `CDialogEx::SetActiveMenu` wywołuje metodę po otwarciu obiektu [klasy CMFCPopupMenu.](../../mfc/reference/cmfcpopupmenu-class.md) Następnie `CDialogEx` obiekt obsługuje każde zdarzenie menu, dopóki obiekt [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) nie zostanie zamknięty.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[Cdialogex](../../mfc/reference/cdialogex-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdialogex.h

## <a name="cdialogexcdialogex"></a><a name="cdialogex"></a>CDialogEx::CDialogEx

Konstruuje `CDialogEx` obiekt.

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
[w] Identyfikator zasobu szablonu okna dialogowego.

*lpszTemplateName*<br/>
[w] Nazwa zasobu szablonu okna dialogowego.

*pRoczysz*<br/>
[w] Wskaźnik do okna nadrzędnego. Wartością domyślną jest NULL.

*pParentWnd*<br/>
[w] Wskaźnik do okna nadrzędnego. Wartością domyślną jest NULL.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdialogexsetbackgroundcolor"></a><a name="setbackgroundcolor"></a>CDialogEx::SetBackgroundColor

Ustawia kolor tła okna dialogowego.

```cpp
void SetBackgroundColor(
    COLORREF color,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[w] Wartość koloru RGB.

*bMalusz*<br/>
[w] PRAWDA, aby natychmiast zaktualizować ekran; w przeciwnym razie FALSE. Wartością domyślną jest PRAWDA.

### <a name="remarks"></a>Uwagi

## <a name="cdialogexsetbackgroundimage"></a><a name="setbackgroundimage"></a>CDialogEx::SetBackgroundImage

Ustawia obraz tła okna dialogowego.

```cpp
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

*hBitmapa*<br/>
[w] Uchwyt do obrazu tła.

*interfejs użytkownika uiBmpResId*<br/>
[w] Identyfikator zasobu obrazu tła.

*Lokalizacji*<br/>
[w] Jedna z `CDialogEx::BackgroundLocation` wartości określających lokalizację obrazu. Prawidłowe wartości obejmują BACKGR_TILE, BACKGR_TOPLEFT, BACKGR_TOPRIGHT, BACKGR_BOTTOMLEFT i BACKGR_BOTTOMRIGHT. Wartość domyślna jest BACKGR_TILE.

*bAutoDestroj*<br/>
[w] PRAWDA, aby automatycznie zniszczyć obraz tła; w przeciwnym razie FALSE.

*bMalusz*<br/>
[w] TRUE, aby natychmiast przerysować okno dialogowe; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

W składni przeciążenia drugiej metody, PRAWDA, jeśli metoda jest pomyślna; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Określony obraz nie jest rozciągnięty tak, aby pasował do obszaru klienta okna dialogowego.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)<br/>
[Klasa CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)
