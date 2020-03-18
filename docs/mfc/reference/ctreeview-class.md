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
ms.openlocfilehash: fec8379a3944d981672754274f50dd4e60f71b61
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421430"
---
# <a name="ctreeview-class"></a>Klasa CTreeView

Upraszcza korzystanie z formantu drzewa i [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), klasy, która hermetyzuje funkcjonalność kontrolki drzewa, z architekturą widoku dokumentu MFC.

## <a name="syntax"></a>Składnia

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CTreeView:: CTreeView](#ctreeview)|Konstruuje obiekt `CTreeView`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CTreeView:: funkcji GetTreeCtrl](#gettreectrl)|Zwraca kontrolkę drzewa skojarzoną z widokiem.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tej architektury, zobacz Omówienie klasy [CView](../../mfc/reference/cview-class.md) i odsyłaczy w tym miejscu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcview. h

##  <a name="ctreeview"></a>CTreeView:: CTreeView

Konstruuje obiekt `CTreeView`.

```
CTreeView();
```

##  <a name="gettreectrl"></a>CTreeView:: funkcji GetTreeCtrl

Zwraca odwołanie do kontrolki drzewa skojarzonej z widokiem.

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>Zobacz też

[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Klasa CTreeCtrl](../../mfc/reference/ctreectrl-class.md)
