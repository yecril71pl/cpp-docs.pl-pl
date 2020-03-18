---
title: Klasa CDialogBar
ms.date: 11/04/2016
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
ms.openlocfilehash: af84c5239a9cb3cbddb1ab4f0230e5b1a3373573
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420478"
---
# <a name="cdialogbar-class"></a>Klasa CDialogBar

Udostępnia funkcje niemodalnego okna dialogowego systemu Windows na pasku sterowania.

## <a name="syntax"></a>Składnia

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDialogBar:: CDialogBar](#cdialogbar)|Konstruuje obiekt `CDialogBar`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDialogBar:: Create](#create)|Tworzy pasek okna dialogowego systemu Windows i dołącza go do obiektu `CDialogBar`.|

## <a name="remarks"></a>Uwagi

Pasek okna dialogowego przypomina okno dialogowe, w którym znajdują się standardowe formanty systemu Windows, które użytkownik może tabulatorować. Kolejną podobieństwem jest to, że tworzysz szablon okna dialogowego do reprezentowania paska dialogowego.

Tworzenie i używanie paska dialogowego jest podobne do tworzenia i używania obiektu `CFormView`. Najpierw użyj [edytora okien dialogowych](../../windows/dialog-editor.md) , aby zdefiniować szablon okna dialogowego z stylem WS_CHILD i bez innych stylów. Szablon nie może mieć WS_VISIBLE stylu. W kodzie aplikacji Wywołaj konstruktora w celu skonstruowania obiektu `CDialogBar`, a następnie Wywołaj `Create`, aby utworzyć okno paska dialogowego i dołączyć je do obiektu `CDialogBar`.

Aby uzyskać więcej informacji na temat `CDialogBar`, zobacz [paski](../../mfc/dialog-bars.md) kontroli artykułów i [Uwaga techniczna 31](../../mfc/tn031-control-bars.md), paski sterowania.

> [!NOTE]
>  W bieżącej wersji obiekt `CDialogBar` nie może hostować formantów Windows Forms. Aby uzyskać więcej informacji na temat formantów Windows Forms C++w wizualizacji, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext. h

##  <a name="cdialogbar"></a>CDialogBar:: CDialogBar

Konstruuje obiekt `CDialogBar`.

```
CDialogBar();
```

##  <a name="create"></a>CDialogBar:: Create

Ładuje szablon zasobów okna dialogowego określony przez `lpszTemplateName` lub `nIDTemplate`, tworzy okno pasek dialogowe, ustawia jego styl i kojarzy go z obiektem `CDialogBar`.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

virtual BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do nadrzędnego obiektu `CWnd`.

*lpszTemplateName*<br/>
Wskaźnik do nazwy szablonu zasobów okna dialogowego obiektu `CDialogBar`.

*nStyle*<br/>
Styl paska narzędzi. Obsługiwane są dodatkowe style paska narzędzi:

- CBRS_TOP pasek sterowania znajduje się u góry okna ramki.

- CBRS_BOTTOM pasek sterowania znajduje się u dołu okna ramki.

- Gdy rozmiar elementu nadrzędnego zostanie zmieniony, CBRS_NOALIGN pasek sterowania nie jest zmieniany.

- Na pasku sterowania CBRS_TOOLTIPS są wyświetlane etykietki narzędzi.

- CBRS_SIZE_DYNAMIC pasek sterowania jest dynamiczny.

- CBRS_SIZE_FIXED pasek sterowania został naprawiony.

- CBRS_FLOATING pasek sterowania jest przestawny.

- Na pasku stanu CBRS_FLYBY są wyświetlane informacje o przycisku.

- CBRS_HIDE_INPLACE pasku sterowania nie jest wyświetlany użytkownikowi.

*nID*<br/>
Identyfikator kontrolki paska dialogowego.

*nIDTemplate*<br/>
Identyfikator zasobu szablonu okna dialogowego obiektu `CDialogBar`.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli określisz styl wyrównania CBRS_TOP lub CBRS_BOTTOM, Szerokość paska dialogowego jest równa rozmiarowi okna ramki, a jego wysokość to zasób określony przez *nIDTemplate*. Jeśli określisz styl wyrównania CBRS_LEFT lub CBRS_RIGHT, Wysokość paska dialogowego jest równa rozmiarowi okna ramki, a jego szerokość jest określana przez zasób określony przez *nIDTemplate*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykład CTRLBARS MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFormView](../../mfc/reference/cformview-class.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)
