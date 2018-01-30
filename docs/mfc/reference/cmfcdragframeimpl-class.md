---
title: Klasa CMFCDragFrameImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDragFrameImpl
dev_langs:
- C++
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2fe293a8fa64cb323771db4f0f2929204790d210
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="cmfcdragframeimpl-class"></a>Klasa CMFCDragFrameImpl
`CMFCDragFrameImpl` Klasy rysuje prostokąt przeciągania, który jest wyświetlany, gdy użytkownik przeciąga okienko w trybie standardowe dokowania.  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
   
## <a name="syntax"></a>Składnia  
  
```  
class CMFCDragFrameImpl  
```  
  
## <a name="remarks"></a>Uwagi  
 Obiekt tej klasy jest osadzony w każdym [klasy CPane](../../mfc/reference/cpane-class.md) obiektu. W związku z tym poszczególnych okienkach, która używa `CanFloat` metoda Wyświetla przeciągnij prostokąt podczas przeciągania go przez użytkownika.  
  
 Grubość przeciągnij prostokąt można kontrolować przy użyciu [AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat) i [AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdragframeimpl.h  
  
##  <a name="enddrawdragframe"></a>CMFCDragFrameImpl::EndDrawDragFrame  

  
```  
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bClearInternalRects`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="init"></a>CMFCDragFrameImpl::Init  

  
```  
void Init(CWnd* pDraggedWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDraggedWnd`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="movedragframe"></a>CMFCDragFrameImpl::MoveDragFrame  

  
```  
void MoveDragFrame(BOOL bForceMove = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bForceMove`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="placetabpredocking"></a>CMFCDragFrameImpl::PlaceTabPreDocking  

  
```  
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,  
    BOOL bFirstTime);  
  
void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pTabbedBar`  
 [in]`bFirstTime`  
 [in]`pCBarToPlaceOn`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="removetabpredocking"></a>CMFCDragFrameImpl::RemoveTabPreDocking  

  
```  
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pOldTargetBar`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="resetstate"></a>CMFCDragFrameImpl::ResetState  

  
```  
void ResetState();
```  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CPane](../../mfc/reference/cpane-class.md)