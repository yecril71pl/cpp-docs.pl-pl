---
title: Klasa CDockablePaneAdapter | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
dev_langs:
- C++
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5bb0e10490a381784e40167e16d1c7ec4e7e1a19
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdockablepaneadapter-class"></a>Klasa CDockablePaneAdapter
Zapewnia obsługę dokowania `CWnd`-pochodnych okienka.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDockablePaneAdapter : public CDockablePane  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|Zwraca okno opakowana.|  
|[CDockablePaneAdapter::LoadState](#loadstate)|(Przesłania [CDockablePane::LoadState](http://msdn.microsoft.com/en-us/96110136-4f46-4764-8a76-3b4abaf77917).)|  
|[CDockablePaneAdapter::SaveState](#savestate)|(Przesłania [CDockablePane::SaveState](http://msdn.microsoft.com/en-us/c5c24249-8d0d-46cb-96d9-9f5c6dc191db).)|  
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj platformę tworzy obiekty tej klasy, korzystając z [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) lub [CMFCBaseTabCtrl::InsertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) metody.  
  
 Jeśli chcesz dostosować `CDockablePaneAdapter` zachowanie, tylko dziedziczyć nową klasę i ustaw informacje o klasie czasu wykonywania na kartach okna przy użyciu [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxDockablePaneAdapter.h  
  
##  <a name="getwrappedwnd"></a>CDockablePaneAdapter::GetWrappedWnd  
 Zwraca podstawowej okna dokującego okienku karty.  
  
```  
virtual CWnd* GetWrappedWnd() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do okna opakowana.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do okna opakowana.  
  
##  <a name="loadstate"></a>CDockablePaneAdapter::LoadState  
 Ładuje stan okienka z rejestru.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszProfileName`  
 Nazwa profilu.  
  
 [in]`nIndex`  
 Indeks profilu.  
  
 [in]`uiID`  
 Identyfikator okienka.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="savestate"></a>CDockablePaneAdapter::SaveState  
 Zapisuje stan okienka w rejestrze.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszProfileName`  
 Nazwa profilu.  
  
 [in]`nIndex`  
 Indeks profilu (wartość domyślna to identyfikator formantu okna).  
  
 [in]`uiID`  
 Identyfikator okienka.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setwrappedwnd"></a>CDockablePaneAdapter::SetWrappedWnd  
 Ustawia podstawowy okna dokującego okienku karty.  
  
```  
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWnd`  
 Wskaźnik do okna okienku karty do zakodowania.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)
