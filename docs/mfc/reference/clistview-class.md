---
title: Klasa CListView
ms.date: 11/04/2016
f1_keywords:
- CListView
- AFXCVIEW/CListView
- AFXCVIEW/CListView::CListView
- AFXCVIEW/CListView::GetListCtrl
- AFXCVIEW/CListView::RemoveImageList
helpviewer_keywords:
- CListView [MFC], CListView
- CListView [MFC], GetListCtrl
- CListView [MFC], RemoveImageList
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
ms.openlocfilehash: 698e37b2853a2ca3698ee0a426c8ded688c99c58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296660"
---
# <a name="clistview-class"></a>Klasa CListView

Upraszcza korzystania z formantu listy z [CListCtrl](../../mfc/reference/clistctrl-class.md), klasa, która łączy funkcjonalność formantu listy z architekturą widoku dokumentu MFC.

## <a name="syntax"></a>Składnia

```
class CListView : public CCtrlView
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CListView::CListView](#clistview)|Konstruuje `CListView` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CListView::GetListCtrl](#getlistctrl)|Zwraca kontrolkę listy skojarzony z widokiem.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CListView::RemoveImageList](#removeimagelist)|Usuwa określony obraz listy z widoku listy.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tej architektury, zobacz Omówienie dla [CView](../../mfc/reference/cview-class.md) klasy i odsyłacze cytowane istnieje.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CListView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcview.h

##  <a name="clistview"></a>  CListView::CListView

Konstruuje `CListView` obiektu.

```
CListView();
```

##  <a name="getlistctrl"></a>  CListView::GetListCtrl

Wywołaj tę funkcję elementu członkowskiego, aby pobrać odwołanie do formantu listy skojarzony z widokiem.

```
CListCtrl& GetListCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do formantu listy skojarzony z widokiem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]

##  <a name="removeimagelist"></a>  CListView::RemoveImageList

Usuwa określony obraz listy z widoku listy.

```
void RemoveImageList(int nImageList);
```

### <a name="parameters"></a>Parametry

*nImageList*<br/>
Liczony od zera indeks obrazu do usunięcia.

## <a name="see-also"></a>Zobacz także

[Próbki MFC ROWLIST](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)
