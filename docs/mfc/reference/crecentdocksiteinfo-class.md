---
title: Klasa CRecentDockSiteInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRecentDockSiteInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::CleanUp
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDefaultPaneDivider
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDockedPercent
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDockedRect
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentListOfPanes
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentPaneContainer
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentTabContainer
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::Init
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::IsRecentLeftPane
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::SaveListOfRecentPanes
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::SetInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::StoreDockInfo
dev_langs:
- C++
helpviewer_keywords:
- CRecentDockSiteInfo [MFC], CleanUp
- CRecentDockSiteInfo [MFC], GetRecentDefaultPaneDivider
- CRecentDockSiteInfo [MFC], GetRecentDockedPercent
- CRecentDockSiteInfo [MFC], GetRecentDockedRect
- CRecentDockSiteInfo [MFC], GetRecentListOfPanes
- CRecentDockSiteInfo [MFC], GetRecentPaneContainer
- CRecentDockSiteInfo [MFC], GetRecentTabContainer
- CRecentDockSiteInfo [MFC], Init
- CRecentDockSiteInfo [MFC], IsRecentLeftPane
- CRecentDockSiteInfo [MFC], SaveListOfRecentPanes
- CRecentDockSiteInfo [MFC], SetInfo
- CRecentDockSiteInfo [MFC], StoreDockInfo
ms.assetid: 2dd14f95-d5a2-4461-a7a5-2c6c36a3a165
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42fd0c5df1731ded5e48bda74cb280b282e6b0cb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702614"
---
# <a name="crecentdocksiteinfo-class"></a>Klasa CRecentDockSiteInfo
`CRecentDockSiteInfo` Klasy to klasa pomocnika przechowująca ostatnie informacje o stanie dla [klasa CPane](../../mfc/reference/cpane-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CRecentDockSiteInfo : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CRecentDockSiteInfo::CRecentDockSiteInfo`|Domyślny konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRecentDockSiteInfo::CleanUp](#cleanup)||  
|[CRecentDockSiteInfo::GetRecentDefaultPaneDivider](#getrecentdefaultpanedivider)||  
|[CRecentDockSiteInfo::GetRecentDockedPercent](#getrecentdockedpercent)||  
|[CRecentDockSiteInfo::GetRecentDockedRect](#getrecentdockedrect)||  
|[CRecentDockSiteInfo::GetRecentListOfPanes](#getrecentlistofpanes)||  
|[CRecentDockSiteInfo::GetRecentPaneContainer](#getrecentpanecontainer)||  
|[CRecentDockSiteInfo::GetRecentTabContainer](#getrecenttabcontainer)||  
|[CRecentDockSiteInfo::Init](#init)||  
|[CRecentDockSiteInfo::IsRecentLeftPane](#isrecentleftpane)||  
|[CRecentDockSiteInfo::operator =](#operator_eq)||  
|[CRecentDockSiteInfo::SaveListOfRecentPanes](#savelistofrecentpanes)||  
|[CRecentDockSiteInfo::SetInfo](#setinfo)||  
|[CRecentDockSiteInfo::StoreDockInfo](#storedockinfo)||  
  
## <a name="remarks"></a>Uwagi  
 `CRecentDockSiteInfo` Klasa jest klasą danych zarządzania. Śledzi stan ostatniego `CPane` jako przechodzi między są zadokowane i przestawne. Po kliknięciu dwukrotnie unoszącego dokowalne, staje się zadokowany. Dwukrotne kliknięcie zadokowanego okienka zwraca go do poprzedniej lokalizacji, rozmiaru i stanu. Podobnie po ponownym zadokowanego okienka zwraca do poprzedniej lokalizacji dokowania. Ta klasa danych to, co sprawia, że, to możliwe. Ponieważ elementy członkowskie tej klasy są przechowywane informacje o stanie dla zadokowanego okienka, ich powinna nie można zmodyfikować bezpośrednio przez aplikację.  
  
 A `CRecentDockSiteInfo` co godzina utworzenia okienko jest tworzony jest obiekt. Każdy `CPane` obiekt ma zmienną członkowską [CPane::m_recentDockInfo](../../mfc/reference/cpane-class.md#m_recentdockinfo), do przechowywania tych informacji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrecentDockSiteInfo.h  
  
##  <a name="cleanup"></a>  CRecentDockSiteInfo::CleanUp  

  
```  
void CleanUp();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="crecentdocksiteinfo"></a>  CRecentDockSiteInfo::CRecentDockSiteInfo  

  
```  
CRecentDockSiteInfo(CPane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pBar*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getrecentdefaultpanedivider"></a>  CRecentDockSiteInfo::GetRecentDefaultPaneDivider  

  
```  
CPaneDivider* GetRecentDefaultPaneDivider();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getrecentdockedpercent"></a>  CRecentDockSiteInfo::GetRecentDockedPercent  

  
```  
int GetRecentDockedPercent(BOOL bForSlider);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bForSlider*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getrecentdockedrect"></a>  CRecentDockSiteInfo::GetRecentDockedRect  

  
```  
CRect& GetRecentDockedRect(BOOL bForSlider);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bForSlider*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getrecentlistofpanes"></a>  CRecentDockSiteInfo::GetRecentListOfPanes  

  
```  
CList<HWND, HWND>& GetRecentListOfPanes(BOOL bForSlider);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bForSlider*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getrecentpanecontainer"></a>  CRecentDockSiteInfo::GetRecentPaneContainer  

  
```  
CPaneContainer* GetRecentPaneContainer(BOOL bForSlider);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bForSlider*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getrecenttabcontainer"></a>  CRecentDockSiteInfo::GetRecentTabContainer  

  
```  
CPaneContainer* GetRecentTabContainer(BOOL bForSlider);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bForSlider*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="init"></a>  CRecentDockSiteInfo::Init  

  
```  
void Init();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isrecentleftpane"></a>  CRecentDockSiteInfo::IsRecentLeftPane  

  
```  
BOOL IsRecentLeftPane(BOOL bForSlider);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bForSlider*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="operator_eq"></a>  CRecentDockSiteInfo::operator =  

  
```  
CRecentDockSiteInfo& operator=(CRecentDockSiteInfo& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *src*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="savelistofrecentpanes"></a>  CRecentDockSiteInfo::SaveListOfRecentPanes  

  
```  
void SaveListOfRecentPanes(CList<HWND,  
    HWND>& lstOrg,  
    BOOL bForSlider);
```  
  
### <a name="parameters"></a>Parametry  
*CList < HWND*<br/>
[in] [in] *lstOrg*  
 [in] *bForSlider*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setinfo"></a>  CRecentDockSiteInfo::SetInfo  

  
```  
virtual void SetInfo(
    BOOL bForSlider,  
    CRecentDockSiteInfo& srcInfo);
```  
  
### <a name="parameters"></a>Parametry  
*bForSlider*<br/>
[in] [in] *srcInfo*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="storedockinfo"></a>  CRecentDockSiteInfo::StoreDockInfo  

  
```  
virtual void StoreDockInfo(
    CPaneContainer* pRecentContainer,  
    CDockablePane* pTabbedBar = NULL);
```  
  
### <a name="parameters"></a>Parametry  
*pRecentContainer*<br/>
[in] [in] *pTabbedBar*  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CDockSite](../../mfc/reference/cdocksite-class.md)
