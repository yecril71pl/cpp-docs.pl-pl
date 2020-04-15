---
title: Klasa COleResizeBar
ms.date: 11/04/2016
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
ms.openlocfilehash: beb0c37b6ac23310b7d5c8506fbdaf677dd74d8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376150"
---
# <a name="coleresizebar-class"></a>Klasa COleResizeBar

Typ paska sterowania, który obsługuje zmiany rozmiaru elementów OLE w miejscu.

## <a name="syntax"></a>Składnia

```
class COleResizeBar : public CControlBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleResizeBar::COleResizeBar](#coleresizebar)|Konstruuje `COleResizeBar` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleResizeBar::Utwórz](#create)|Tworzy i inicjuje okno podrzędne systemu `COleResizeBar` Windows i kojarzy je z obiektem.|

## <a name="remarks"></a>Uwagi

`COleResizeBar`obiekty są wyświetlane jako [CRectTracker](../../mfc/reference/crecttracker-class.md) z kreskowanym obramowaniem i zewnętrznymi uchwytami o rozmiarze.

`COleResizeBar`obiekty są zwykle osadzone elementy członkowskie obiektów okna ramki pochodzące z [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) klasy.

Aby uzyskać więcej informacji, zobacz artykuł [Aktywacja](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Ccontrolbar](../../mfc/reference/ccontrolbar-class.md)

`COleResizeBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="coleresizebarcoleresizebar"></a><a name="coleresizebar"></a>COleResizeBar::COleResizeBar

Konstruuje `COleResizeBar` obiekt.

```
COleResizeBar();
```

### <a name="remarks"></a>Uwagi

Wywołanie `Create` utworzenia obiektu paska zmienić rozmiar.

## <a name="coleresizebarcreate"></a><a name="create"></a>COleResizeBar::Utwórz

Tworzy okno podrzędne i kojarzy je z obiektem. `COleResizeBar`

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_RESIZE_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego paska rozmiaru.

*Dwstyle*<br/>
Określa atrybuty [stylu okna.](../../mfc/reference/styles-used-by-mfc.md#window-styles)

*Nid*<br/>
Identyfikator okna podrzędnego paska zmienić rozmiar.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli pasek rozmiaru rozmiaru został utworzony; w przeciwnym razie 0.

## <a name="see-also"></a>Zobacz też

[Próbka MFC SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleServerDoc](../../mfc/reference/coleserverdoc-class.md)
