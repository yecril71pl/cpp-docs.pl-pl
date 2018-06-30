---
title: Klasa CTooltipManager | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
dev_langs:
- C++
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 01d0cb0774af7c1c900f31b4e83bb03dba8bd255
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121089"
---
# <a name="ctooltipmanager-class"></a>Klasa CTooltipManager
Przechowuje informacje środowiska wykonawczego o etykietek narzędzi. `CTooltipManager` Klasa jest skonkretyzowanym jeden raz w każdej aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CTooltipManager : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTooltipManager::CreateToolTip](#createtooltip)|Tworzy kontrolkę tooltip dla typów sterowania systemu Windows.|  
|[CTooltipManager::DeleteToolTip](#deletetooltip)|Usuwa formantu tooltip.|  
|[CTooltipManager::SetTooltipParams](#settooltipparams)|Dostosowuje wygląd formantu tooltip dla typów sterowania systemu Windows.|  
|[CTooltipManager::SetTooltipText](#settooltiptext)|Ustawia tekst i opis dla formantu tooltip.|  
|[CTooltipManager::UpdateTooltips](#updatetooltips)||  
  
## <a name="remarks"></a>Uwagi  
 Użyj [klasy CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, i `CTooltipManager` ze sobą w celu wdrożenia dostosowane etykietki narzędzi w aplikacji. Na przykład dotyczące używania tych klas tooltip zobacz [klasy CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md) tematu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtooltipmanager.h  
  
##  <a name="createtooltip"></a>  CTooltipManager::CreateToolTip  
 Tworzy formantu tooltip.  
  
```  
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,  
    CWnd* pWndParent,  
    UINT nType);
```  
  
### <a name="parameters"></a>Parametry  
 [out] *pToolTip*  
 Odwołanie do wskaźnika etykietka narzędzia. Wskaż nowo utworzony etykietka narzędzia, gdy funkcja zwraca wartość jest ustawiona.  
  
 [in] *pWndParent*  
 Element nadrzędny elementu tooltip.  
  
 [in] *Npowiadomienia*  
 Typ elementu tooltip.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli etykietka narzędzia został pomyślnie utworzony.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [CTooltipManager::DeleteToolTip](#deletetooltip) można usunąć formantu tooltip, który jest przekazywany z powrotem w *pToolTip*.  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) ustawia parametry wyświetlania każdego tooltip tworzy oparte na elemencie tooltip typie *Npowiadomienia* określa. Aby zmienić parametry dla co najmniej jeden typ etykietka narzędzia, należy wywołać [CTooltipManager::SetTooltipParams](#settooltipparams).  
  
 Etykietka narzędzia prawidłowe typy są wymienione w poniższej tabeli:  
  
|ToolTip — typ|Kategoria formantu|Przykład typów|  
|------------------|----------------------|-------------------|  
|AFX_TOOLTIP_TYPE_BUTTON|Przycisk.|CMFCButton|  
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Pasek tytułu.|CMFCCaptionBar|  
|AFX_TOOLTIP_TYPE_DEFAULT|Formant, który nie mieści się inną kategorię.|Brak.|  
|AFX_TOOLTIP_TYPE_DOCKBAR|Okienko dokującego.|CDockablePane|  
|AFX_TOOLTIP_TYPE_EDIT|Pole tekstowe.|Brak.|  
|AFX_TOOLTIP_TYPE_MINIFRAME|Mini.|CPaneFrameWnd|  
|AFX_TOOLTIP_TYPE_PLANNER|Planista.|Brak.|  
|AFX_TOOLTIP_TYPE_RIBBON|Pasek wstążki.|CMFCRibbonBar, cmfcribbonpanelmenubar —|  
|AFX_TOOLTIP_TYPE_TAB|Formant karty.|CMFCTabCtrl|  
|AFX_TOOLTIP_TYPE_TOOLBAR|Pasek narzędzi.|CMFCToolBar, CMFCPopupMenuBar|  
|AFX_TOOLTIP_TYPE_TOOLBOX|Przybornika.|Brak.|  
  
##  <a name="deletetooltip"></a>  CTooltipManager::DeleteToolTip  
 Usuwa formantu tooltip.  
  
```  
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```  
  
### <a name="parameters"></a>Parametry  
 [w, out] *pToolTip*  
 Odwołanie do wskaźnika do etykietkę narzędzia do zniszczenia.  
  
### <a name="remarks"></a>Uwagi  
 Tę metodę można wywołać dla każdego [CToolTipCtrl — klasa](../../mfc/reference/ctooltipctrl-class.md) utworzony przez [CTooltipManager::CreateToolTip](#createtooltip). Kontrolki nadrzędnej powinny wywoływać tej metody z jego `OnDestroy` obsługi. Jest to wymagane do poprawnego usunięcia etykietki narzędzia w ramach. Ta metoda ustawia *pToolTip* null przed zwróceniem.  
  
##  <a name="settooltipparams"></a>  CTooltipManager::SetTooltipParams  
 Dostosowuje wygląd formantu etykietki narzędzia dla określonych typów sterowania systemu Windows.  
  
```  
void SetTooltipParams(
    UINT nTypes,  
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),  
    CMFCToolTipInfo* pParams=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nTypes*  
 Określa typy formantów.  
  
 [in] *pRTC*  
 Klasa środowiska uruchomieniowego etykietka narzędzia niestandardowego.  
  
 [in] *pParams*  
 Parametry etykietka narzędzia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zestawów środowiska uruchomieniowego klasy i parametrów początkowych [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) używa podczas tworzenia etykietek narzędzi. Gdy formant wymaga [CTooltipManager::CreateToolTip](#createtooltip) i przebiegów w etykietce narzędzia typ jednego z typów wskazywanym przez *nTypes*, Menedżer tooltip tworzy formantu tooltip, który jest wystąpieniem środowisko uruchomieniowe klasą określoną przez *pRTC* i przekazuje parametry określone przez *pParams* do nowego etykietki narzędzia.  
  
 Gdy ta metoda jest wywoływana, wszystkich istniejących właścicieli etykietki narzędzia wyświetlany komunikat AFX_WM_UPDATETOOLTIPS i etykietki należy ponownie utworzyć przy użyciu [CTooltipManager::CreateToolTip](#createtooltip).  
  
 *nTypes* może być dowolną kombinację tooltip prawidłowe typy, które [CTooltipManager::CreateToolTip](#createtooltip) używa lub może być AFX_TOOLTIP_TYPE_ALL. Przekazujesz AFX_TOOLTIP_TYPE_ALL dotyczy wszystkich typów etykietka narzędzia.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `SetTooltipParams` metody `CTooltipManager` klasy. Następujący fragment kodu jest częścią [rysowania klienta — przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]  
  
##  <a name="settooltiptext"></a>  CTooltipManager::SetTooltipText  
 Ustawia tekst i opis etykietka narzędzia.  
  
```  
static void SetTooltipText(
    TOOLINFO* pTI,  
    CToolTipCtrl* pToolTip,  
    UINT nType,  
    const CString strText,  
    LPCTSTR lpszDescr=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pTI*  
 Wskaźnik do obiektu TOOLINFO.  
  
 [w, out] *pToolTip*  
 Wskaźnik do formantu tooltip, do których chcesz ustawić tekst i opis.  
  
 [in] *Npowiadomienia*  
 Określa typ formantu, z którą skojarzony jest ten etykietka narzędzia.  
  
 [in] *strText*  
 Tekst, który ma być ustawiony jako tekst etykietki narzędzia.  
  
 [in] *lpszDescr*  
 Wskaźnik do opisu etykietka narzędzia. Może mieć wartości NULL.  
  
### <a name="remarks"></a>Uwagi  
 Wartość *Npowiadomienia* musi mieć taką samą wartość jak *Npowiadomienia* parametr [CTooltipManager::CreateToolTip](#createtooltip) utworzenia etykietka narzędzia.  
  
##  <a name="updatetooltips"></a>  CTooltipManager::UpdateTooltips  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void UpdateTooltips();
```  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)   
 [Klasa CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)
