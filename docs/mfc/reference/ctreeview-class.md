---
title: Klasa CTreeView | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
dev_langs:
- C++
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a760e567718ad7a485ebe469903c7cbd566daccc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375401"
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
