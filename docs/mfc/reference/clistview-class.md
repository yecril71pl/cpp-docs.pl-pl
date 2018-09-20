---
title: Klasa CListView | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CListView
- AFXCVIEW/CListView
- AFXCVIEW/CListView::CListView
- AFXCVIEW/CListView::GetListCtrl
- AFXCVIEW/CListView::RemoveImageList
dev_langs:
- C++
helpviewer_keywords:
- CListView [MFC], CListView
- CListView [MFC], GetListCtrl
- CListView [MFC], RemoveImageList
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fbb9561111a75011f934aeb0ce972829132cb87
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423406"
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

## <a name="see-also"></a>Zobacz też

[Próbki MFC ROWLIST](../../visual-cpp-samples.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)
