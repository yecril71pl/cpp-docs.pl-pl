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
ms.openlocfilehash: d7f3b7c43d98c4f2c42d0c27c8e224f33e4b3301
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749129"
---
# <a name="clistview-class"></a>Klasa CListView

Upraszcza użycie formantu listy i [CListCtrl](../../mfc/reference/clistctrl-class.md), klasy, która hermetyzuje funkcje kontroli listy, z architekturą widoku dokumentu MFC.

## <a name="syntax"></a>Składnia

```
class CListView : public CCtrlView
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CListView::CListView](#clistview)|Konstruuje `CListView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CListView::GetListCtrl](#getlistctrl)|Zwraca kontrolka listy skojarzona z widokiem.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CListView::RemoveImageList](#removeimagelist)|Usuwa określoną listę obrazów z widoku listy.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tej architektury, zobacz omówienie [CView](../../mfc/reference/cview-class.md) klasy i odsyłaczy wymienionych tam.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[Cctrlview](../../mfc/reference/cctrlview-class.md)

`CListView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcview.h

## <a name="clistviewclistview"></a><a name="clistview"></a>CListView::CListView

Konstruuje `CListView` obiekt.

```
CListView();
```

## <a name="clistviewgetlistctrl"></a><a name="getlistctrl"></a>CListView::GetListCtrl

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać odwołanie do formantu listy skojarzone z widokiem.

```
CListCtrl& GetListCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do formantu listy skojarzonego z widokiem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]

## <a name="clistviewremoveimagelist"></a><a name="removeimagelist"></a>CListView::RemoveImageList

Usuwa określoną listę obrazów z widoku listy.

```cpp
void RemoveImageList(int nImageList);
```

### <a name="parameters"></a>Parametry

*nImageList (Lista)*<br/>
Indeks od zera obrazu do usunięcia.

## <a name="see-also"></a>Zobacz też

[Przykładowy WIERSZ MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)
