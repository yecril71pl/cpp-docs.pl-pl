---
title: "Clistview — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d9d90df0ac3d91f58c1e9592e65ce84ac900f6e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="clistview-class"></a>Clistview — klasa
Użycie formantu listy, upraszcza [CListCtrl](../../mfc/reference/clistctrl-class.md), klasy, która hermetyzuje funkcjonalność formant listy, o architekturze dokument widok MFC.  
  
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
|[CListView::GetListCtrl](#getlistctrl)|Zwraca kontrolki listy skojarzone z tym widokiem.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CListView::RemoveImageList](#removeimagelist)|Usuwa określony obraz listy z widoku listy.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji dotyczących tej architektury, zobacz Omówienie dla [CView](../../mfc/reference/cview-class.md) klasy i odsyłacze cytowane.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cview —](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CListView`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcview.h  
  
##  <a name="clistview"></a>CListView::CListView  
 Konstruuje `CListView` obiektu.  
  
```  
CListView();
```  
  
##  <a name="getlistctrl"></a>CListView::GetListCtrl  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać odwołanie do formantu listy skojarzone z tym widokiem.  
  
```  
CListCtrl& GetListCtrl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do formantu listy skojarzone z tym widokiem.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]  
  
##  <a name="removeimagelist"></a>CListView::RemoveImageList  
 Usuwa określony obraz listy z widoku listy.  
  
```  
void RemoveImageList(int nImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `nImageList`  
 Liczony od zera indeks obrazu do usunięcia.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC ROWLIST](../../visual-cpp-samples.md)   
 [Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)
