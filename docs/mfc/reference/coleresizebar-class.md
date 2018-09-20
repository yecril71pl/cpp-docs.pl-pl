---
title: Klasa COleResizeBar | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
dev_langs:
- C++
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf1e2b447b4cfe0e2f503d2263354f3537bbb849
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391387"
---
# <a name="coleresizebar-class"></a>Klasa COleResizeBar

Typ formantu paska, który obsługuje zmiany wielkości elementów OLE w miejscu.

## <a name="syntax"></a>Składnia

```
class COleResizeBar : public CControlBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleResizeBar::COleResizeBar](#coleresizebar)|Konstruuje `COleResizeBar` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleResizeBar::Create](#create)|Tworzy i inicjuje okno podrzędne Windows i kojarzy ją do `COleResizeBar` obiektu.|

## <a name="remarks"></a>Uwagi

`COleResizeBar` obiekty są wyświetlane jako [CRectTracker](../../mfc/reference/crecttracker-class.md) uchwyty zmiany rozmiaru z kreskowanym obramowaniem i zewnętrznych.

`COleResizeBar` obiekty są zazwyczaj osadzone elementy członkowskie obiektów okien ramowych pochodzących od [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) klasy.

Aby uzyskać więcej informacji, zobacz artykuł [aktywacji](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`COleResizeBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

##  <a name="coleresizebar"></a>  COleResizeBar::COleResizeBar

Konstruuje `COleResizeBar` obiektu.

```
COleResizeBar();
```

### <a name="remarks"></a>Uwagi

Wywołaj `Create` można utworzyć obiektu pasek zmiany rozmiaru.

##  <a name="create"></a>  COleResizeBar::Create

Tworzy okno podrzędne i kojarzy ją z `COleResizeBar` obiektu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_RESIZE_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okno nadrzędne paska zmiany rozmiaru.

*dwStyle*<br/>
Określa [styl okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) atrybutów.

*nID*<br/>
Pasek zmiany rozmiaru okna podrzędnego identyfikatora.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli utworzono pasek; w przeciwnym razie 0.

## <a name="see-also"></a>Zobacz też

[Próbki MFC SUPERPAD](../../visual-cpp-samples.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleServerDoc](../../mfc/reference/coleserverdoc-class.md)
