---
title: Klasa CTreeView
ms.date: 11/04/2016
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
ms.openlocfilehash: db899b58c68dabc25e571c390db0575a2d2ebb58
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496347"
---
# <a name="ctreeview-class"></a>Klasa CTreeView

Upraszcza korzystania z formantu drzewa z [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), klasa, która łączy funkcjonalność formantu drzewa z architekturą widoku dokumentu MFC.

## <a name="syntax"></a>Składnia

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTreeView::CTreeView](#ctreeview)|Konstruuje `CTreeView` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTreeView::GetTreeCtrl](#gettreectrl)|Zwraca kontrolkę drzewa skojarzone z tym widokiem.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tej architektury, zobacz Omówienie dla [CView](../../mfc/reference/cview-class.md) klasy i odsyłacze cytowane istnieje.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcview.h

##  <a name="ctreeview"></a>  CTreeView::CTreeView

Konstruuje `CTreeView` obiektu.

```
CTreeView();
```

##  <a name="gettreectrl"></a>  CTreeView::GetTreeCtrl

Zwraca odwołanie do formantu drzewa skojarzone z tym widokiem.

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>Zobacz też

[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Klasa CTreeCtrl](../../mfc/reference/ctreectrl-class.md)
