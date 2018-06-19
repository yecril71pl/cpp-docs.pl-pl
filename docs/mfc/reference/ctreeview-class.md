---
title: CTreeView — klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 8d19d4958de2f7909f2072b2ae2f59c00e63d65a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373628"
---
# <a name="ctreeview-class"></a>CTreeView — klasa
Użycie formantu drzewa, upraszcza [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), klasy, która hermetyzuje funkcjonalność kontrolki drzewa, o architekturze dokument widok MFC.  
  
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
|[CTreeView::GetTreeCtrl](#gettreectrl)|Zwraca drzewie skojarzone z tym widokiem.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji dotyczących tej architektury, zobacz Omówienie dla [CView](../../mfc/reference/cview-class.md) klasy i odsyłacze cytowane.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cview —](../../mfc/reference/cview-class.md)  
  
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
 [Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cview — klasa](../../mfc/reference/cview-class.md)   
 [Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)   
 [Klasa CTreeCtrl](../../mfc/reference/ctreectrl-class.md)
