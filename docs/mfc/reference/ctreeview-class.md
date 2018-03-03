---
title: "CTreeView — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7530569d5e5313ebfcbdaf92ebd245962b9e443c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cview —](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CTreeView`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcview.h  
  
##  <a name="ctreeview"></a>CTreeView::CTreeView  
 Konstruuje `CTreeView` obiektu.  
  
```  
CTreeView();
```  
  
##  <a name="gettreectrl"></a>CTreeView::GetTreeCtrl  
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
