---
title: Klasa CGlobalUtils | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGlobalUtils
- AFXGLOBALUTILS/CGlobalUtils
- AFXGLOBALUTILS/CGlobalUtils::AdjustRectToWorkArea
- AFXGLOBALUTILS/CGlobalUtils::CalcExpectedDockedRect
- AFXGLOBALUTILS/CGlobalUtils::CanBeAttached
- AFXGLOBALUTILS/CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd
- AFXGLOBALUTILS/CGlobalUtils::CheckAlignment
- AFXGLOBALUTILS/CGlobalUtils::CyFromString
- AFXGLOBALUTILS/CGlobalUtils::DecimalFromString
- AFXGLOBALUTILS/CGlobalUtils::FlipRect
- AFXGLOBALUTILS/CGlobalUtils::ForceAdjustLayout
- AFXGLOBALUTILS/CGlobalUtils::GetDockingManager
- AFXGLOBALUTILS/CGlobalUtils::GetOppositeAlignment
- AFXGLOBALUTILS/CGlobalUtils::GetPaneAndAlignFromPoint
- AFXGLOBALUTILS/CGlobalUtils::GetWndIcon
- AFXGLOBALUTILS/CGlobalUtils::SetNewParent
- AFXGLOBALUTILS/CGlobalUtils::StringFromCy
- AFXGLOBALUTILS/CGlobalUtils::StringFromDecimal
dev_langs:
- C++
helpviewer_keywords:
- CGlobalUtils [MFC], AdjustRectToWorkArea
- CGlobalUtils [MFC], CalcExpectedDockedRect
- CGlobalUtils [MFC], CanBeAttached
- CGlobalUtils [MFC], CanPaneBeInFloatingMultiPaneFrameWnd
- CGlobalUtils [MFC], CheckAlignment
- CGlobalUtils [MFC], CyFromString
- CGlobalUtils [MFC], DecimalFromString
- CGlobalUtils [MFC], FlipRect
- CGlobalUtils [MFC], ForceAdjustLayout
- CGlobalUtils [MFC], GetDockingManager
- CGlobalUtils [MFC], GetOppositeAlignment
- CGlobalUtils [MFC], GetPaneAndAlignFromPoint
- CGlobalUtils [MFC], GetWndIcon
- CGlobalUtils [MFC], SetNewParent
- CGlobalUtils [MFC], StringFromCy
- CGlobalUtils [MFC], StringFromDecimal
ms.assetid: 2c5bd1a6-f80c-4e79-a476-b4ceebabfb2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c92ccfe9dbf25fa1355885a5f6dd3570df4884b
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42466250"
---
# <a name="cglobalutils-class"></a>Klasa CGlobalUtils
Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CGlobalUtils  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CGlobalUtils::AdjustRectToWorkArea](#adjustrecttoworkarea)||  
|[CGlobalUtils::CalcExpectedDockedRect](#calcexpecteddockedrect)||  
|[CGlobalUtils::CanBeAttached](#canbeattached)||  
|[CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd](#canpanebeinfloatingmultipaneframewnd)||  
|[CGlobalUtils::CheckAlignment](#checkalignment)||  
|[CGlobalUtils::CyFromString](#cyfromstring)||  
|[CGlobalUtils::DecimalFromString](#decimalfromstring)||  
|[CGlobalUtils::FlipRect](#fliprect)||  
|[CGlobalUtils::ForceAdjustLayout](#forceadjustlayout)||  
|[CGlobalUtils::GetDockingManager](#getdockingmanager)||  
|[CGlobalUtils::GetOppositeAlignment](#getoppositealignment)||  
|[CGlobalUtils::GetPaneAndAlignFromPoint](#getpaneandalignfrompoint)||  
|[CGlobalUtils::GetWndIcon](#getwndicon)||  
|[CGlobalUtils::SetNewParent](#setnewparent)||  
|[CGlobalUtils::StringFromCy](#stringfromcy)||  
|[CGlobalUtils::StringFromDecimal](#stringfromdecimal)||  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CGlobalUtils](../../mfc/reference/cglobalutils-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxglobalutils.h  
  
##  <a name="adjustrecttoworkarea"></a>  CGlobalUtils::AdjustRectToWorkArea  
  
```  
void AdjustRectToworkArea(
    CRect& rect,  
    CRect* pRectDelta = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [out w] *rect*  
 [in] *pRectDelta*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="calcexpecteddockedrect"></a>  CGlobalUtils::CalcExpectedDockedRect  

  
```  
void CalcExpectedDockedRect(
    CPaneContainerManager& barContainerManager,  
    CWnd* pWndTodock,  
    CPoint ptMouse,  
    CRect& rectResult,  
    BOOL& bDrawTab,  
    CDockablePane** ppTargetBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *barContainerManager*  
 [in] *pWndTodock*  
 [in] *ptMouse*  
 [out] *rectResult*  
 [out] *bDrawTab*  
 [out] *ppTargetBar*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="canbeattached"></a>  CGlobalUtils::CanBeAttached  

  
```  
BOOL CanBeAttached(CWnd* pWnd) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pWnd*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="canpanebeinfloatingmultipaneframewnd"></a>  CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd  

  
```  
BOOL CanPaneBeInFloatingMultiPaneFrameWnd(CWnd* pWnd) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pWnd*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="checkalignment"></a>  CGlobalUtils::CheckAlignment  

  
```  
BOOL CheckAlignment(
    CPoint point,  
    CBasePane* pBar,  
    int nSensitivity,  
    const CDockingManager* pDockManager,  
    BOOL bOuterEdge,  
    DWORD& dwAlignment,  
    DWORD dwEnabledDockBars = CBRS_ALIGN_ANY,  
    LPCRECT lpRectBounds = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *punktu*  
 [in] *pBar*  
 [in] *nSensitivity*  
 [in] *pDockManager*  
 [in] *bOuterEdge*  
 [out] *dwAlignment*  
 [in] *dwEnabledDockBars*  
 [in] *lpRectBounds*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="cyfromstring"></a>  CGlobalUtils::CyFromString  

  
```  
BOOL CyFromString(
    CY& cy,  
    LPCTSTR psz);
```  
  
### <a name="parameters"></a>Parametry  
 [out] *cy*  
 [in] *psz*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="decimalfromstring"></a>  CGlobalUtils::DecimalFromString  

  
```  
BOOL DecimalFromString(
    DECIMAL& decimal,  
    LPCTSTR psz);
```  
  
### <a name="parameters"></a>Parametry  
 [out] *dziesiętna*  
 [in] *psz*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="fliprect"></a>  CGlobalUtils::FlipRect  

  
```  
void FlipRect(
    CRect& rect,  
    int nDegrees);
```  
  
### <a name="parameters"></a>Parametry  
 [out w] *rect*  
 [in] *nDegrees*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="forceadjustlayout"></a>  CGlobalUtils::ForceAdjustLayout  

  
```  
void ForceAdjustLayout(
    CDockingManager* pDockManager,  
    BOOL bForce = FALSE,  
    BOOL bForceInvisible = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [out w] *pDockManager*  
 [in] *bForce*  
 [in] *bForceInvisible*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getdockingmanager"></a>  CGlobalUtils::GetDockingManager  

  
```  
CDockingManager* GetDockingManager(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pWnd*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getoppositealignment"></a>  CGlobalUtils::GetOppositeAlignment  

  
```  
DWORD GetOppositeAlignment(DWORD dwAlign);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *dwAlign*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getpaneandalignfrompoint"></a>  CGlobalUtils::GetPaneAndAlignFromPoint  

  
```  
BOOL GetPaneAndAlignFromPoint(
    CPaneContainerManager& barContainerManager,  
    CPoint pt,  
    CDockablePane** ppTargetControlBar,  
    DWORD& dwAlignment,  
    BOOL& bTabArea,  
    BOOL& bCaption);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *barContainerManager*  
 [in] *(czas pacyficzny)*  
 [out] *ppTargetControlBar*  
 [out] *dwAlignment*  
 [out] *bTabArea*  
 [out] *bCaption*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getwndicon"></a>  CGlobalUtils::GetWndIcon  

  
```  
HICON GetWndIcon(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pWnd*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setnewparent"></a>  CGlobalUtils::SetNewParent  

  
```  
void SetNewParent(
    CObList& lstControlBars,  
    CWnd* pNewParent,  
    BOOL bCheckVisibility = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lstControlBars*  
 [in] *pNewParent*  
 [in] *bCheckVisibility*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="stringfromcy"></a>  CGlobalUtils::StringFromCy  

  
```  
BOOL StringFromCy(
    CString& str,  
    CY& cy);
```  
  
### <a name="parameters"></a>Parametry  
 [out] *str*  
 [in] *cy*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="stringfromdecimal"></a>  CGlobalUtils::StringFromDecimal  

  
```  
BOOL StringFromDecimal(
    CString& str,  
    DECIMAL& decimal);
```  
  
### <a name="parameters"></a>Parametry  
 [out] *str*  
 [in] *dziesiętna*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
