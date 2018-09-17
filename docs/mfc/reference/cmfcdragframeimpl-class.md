---
title: Klasa CMFCDragFrameImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDragFrameImpl
dev_langs:
- C++
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c8cd05dc5d4cdff535b8e571e94d9033d0220ccf
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710167"
---
# <a name="cmfcdragframeimpl-class"></a>Klasa CMFCDragFrameImpl
`CMFCDragFrameImpl` Klasy rysuje przeciągnij prostokąt, który jest wyświetlany, gdy użytkownik przeciągnie okienko w trybie standardowego dokowania.  
   Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.  
   
## <a name="syntax"></a>Składnia  
  
```  
class CMFCDragFrameImpl  
```  
  
## <a name="remarks"></a>Uwagi  
 Obiekt tej klasy jest osadzony w każdym [klasa CPane](../../mfc/reference/cpane-class.md) obiektu. W związku z tym, każde okienko, który używa `CanFloat` metoda Wyświetla przeciągnij prostokąt, gdy użytkownik przeciągnie go.  
  
 Grubość przeciągnij prostokąt można kontrolować za pomocą [AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat) i [AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdragframeimpl.h  
  
##  <a name="enddrawdragframe"></a>  CMFCDragFrameImpl::EndDrawDragFrame  

  
```  
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bClearInternalRects*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="init"></a>  CMFCDragFrameImpl::Init  

  
```  
void Init(CWnd* pDraggedWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pDraggedWnd*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="movedragframe"></a>  CMFCDragFrameImpl::MoveDragFrame  

  
```  
void MoveDragFrame(BOOL bForceMove = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bForceMove*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="placetabpredocking"></a>  CMFCDragFrameImpl::PlaceTabPreDocking  

  
```  
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,  
    BOOL bFirstTime);  
  
void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```  
  
### <a name="parameters"></a>Parametry  
*pTabbedBar*<br/>
[in] [in] *bFirstTime*  
 [in] *pCBarToPlaceOn*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="removetabpredocking"></a>  CMFCDragFrameImpl::RemoveTabPreDocking  

  
```  
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pOldTargetBar*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="resetstate"></a>  CMFCDragFrameImpl::ResetState  

  
```  
void ResetState();
```  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CPane](../../mfc/reference/cpane-class.md)