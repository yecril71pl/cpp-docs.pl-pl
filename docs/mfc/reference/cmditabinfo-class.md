---
title: Klasa CMDITabInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo::Serialize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bAutoColor
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bDocumentMenu
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bEnableTabSwap
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bFlatFrame
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCloseButton
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCustomTooltips
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabIcons
- AFXMDICLIENTAREAWND/CMDITabInfo::m_nTabBorderSize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_style
- AFXMDICLIENTAREAWND/CMDITabInfo::m_tabLocation
dev_langs:
- C++
helpviewer_keywords:
- CMDITabInfo [MFC], Serialize
- CMDITabInfo [MFC], m_bAutoColor
- CMDITabInfo [MFC], m_bDocumentMenu
- CMDITabInfo [MFC], m_bEnableTabSwap
- CMDITabInfo [MFC], m_bFlatFrame
- CMDITabInfo [MFC], m_bTabCloseButton
- CMDITabInfo [MFC], m_bTabCustomTooltips
- CMDITabInfo [MFC], m_bTabIcons
- CMDITabInfo [MFC], m_nTabBorderSize
- CMDITabInfo [MFC], m_style
- CMDITabInfo [MFC], m_tabLocation
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b670b26855f5edcfb955d3dd0f8150a999f3a8e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmditabinfo-class"></a>Klasa CMDITabInfo
`CMDITabInfo` Klasa jest używana do przekazania parametrów do [CMDIFrameWndEx::EnableMDITabbedGroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) metody. Grupy z kartami zestaw elementów członkowskich tej klasy, do sterowania zachowaniem MDI.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMDITabInfo   
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMDITabInfo::CMDITabInfo`|Domyślny konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMDITabInfo::Serialize](#serialize)|Odczytuje i zapisuje ten obiekt z lub do archiwum.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMDITabInfo::m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|Określa, czy **Zamknij** przycisk jest wyświetlany na etykiecie aktywnej karty.|  
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|Określa, czy kolor na kartach MDI.|  
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|Określa, czy grupa kart Wyświetla menu podręcznego, która umożliwia wyświetlenie listy otwartych dokumentów lub wyświetla przyciski przewijania.|  
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|Określa, czy użytkownika można wymienić przez przeciągnięcie pozycji kart.|  
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|Określa, czy karty mają płaskiej ramki.|  
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|Określa, czy każda etykieta kartę Wyświetla **Zamknij** przycisku.|  
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|Określa, czy włączono niestandardowych etykietek narzędzi.|  
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|Określa, czy mają być wyświetlane ikony na kartach MDI.|  
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|Określa rozmiar obramowania okna każdej karty.|  
|[CMDITabInfo::m_style](#m_style)|Określa styl etykiet kartę.|  
|[CMDITabInfo::m_tabLocation](#m_tablocation)|Określa, czy etykiety karty znajdują się u góry lub u dołu strony.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa określa parametry tworzonych w ramach grup kart MDI.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób ustawiania wartości poszczególnych zmiennych w `CMDITabInfo` klasy.  
  
 [!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmdiclientareawnd.h  
  
##  <a name="m_bactivetabclosebutton_"></a>CMDITabInfo::m_bActiveTabCloseButton;  
 Określa, czy **Zamknij** przycisk jest wyświetlany na etykiecie aktywnej karty.  
  
```  
BOOL m_bActiveTabCloseButton;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `TRUE`, zostanie wyświetlona etykieta karcie active **Zamknij** przycisku. **Zamknij** przycisk zostanie usunięty z prawym górnym rogu obszaru karty. W przeciwnym razie nie będą wyświetlane etykiety karcie active **Zamknij** przycisku. **Zamknij** przycisk pojawi się w prawym górnym rogu obszaru karty.  
  
##  <a name="m_bautocolor"></a>CMDITabInfo::m_bAutoColor  
 Określa, czy każdej karcie MDI ma własną kolorów.  
  
```  
BOOL m_bAutoColor;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `TRUE`, każda karta ma własną kolorów. Zestaw kolorów jest zarządzana przez biblioteki MFC. W przeciwnym razie będą wyświetlane w biały. Wartość domyślna to `FALSE`.  
  
##  <a name="m_bdocumentmenu"></a>CMDITabInfo::m_bDocumentMenu  
 Określa, czy poszczególne karty wyświetla menu podręczne, który zawiera listę otwartych dokumentów na prawej krawędzi obszaru karty.  
  
```  
BOOL m_bDocumentMenu;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `TRUE`, system windows każdej karcie Wyświetla menu podręcznego zawierający listę otwartych dokumentów na prawej krawędzi obszaru karty; W przeciwnym razie okno karty są wyświetlane przyciski przewijania w prawej krawędzi obszaru karty. Wartość domyślna to `FALSE`.  
  
##  <a name="m_benabletabswap"></a>CMDITabInfo::m_bEnableTabSwap  
 Określa, czy użytkownika można wymienić przez przeciągnięcie pozycji kart.  
  
```  
BOOL m_bEnableTabSwap;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `TRUE`, użytkownik może zmienić położenie karty przez przeciągnięcie karty. W przeciwnym razie użytkownik nie można zmienić położenia karty. Wartość domyślna to `TRUE`.  
  
##  <a name="m_bflatframe"></a>CMDITabInfo::m_bFlatFrame  
 Określa, czy każde okno karta ma prosty ramki.  
  
```  
BOOL m_bFlatFrame;  
```  
  
##  <a name="m_btabclosebutton"></a>CMDITabInfo::m_bTabCloseButton  
 Określa, czy każde okno kartę Wyświetla **Zamknij** przycisku.  
  
```  
BOOL m_bTabCloseButton;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `TRUE`, wyświetla okna każdej karcie **Zamknij** przycisk na prawej krawędzi karty. W przeciwnym razie **Zamknij** nie jest wyświetlany przycisk. Wartość domyślna to `TRUE`.  
  
##  <a name="m_btabcustomtooltips"></a>CMDITabInfo::m_bTabCustomTooltips  
 Określa, czy karty wyświetlać elementy ToolTip.  
  
```  
BOOL m_bTabCustomTooltips;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `TRUE`, wysyła aplikacji `AFX_WM_ON_GET_TAB_TOOLTIP` komunikat do ramki głównej. Ten komunikat można obsługiwać przy użyciu `ON_REGISTERED_MESSAGE` makra.  
  
##  <a name="m_btabicons"></a>CMDITabInfo::m_bTabIcons  
 Określa, czy mają być wyświetlane ikony na kartach MDI.  
  
```  
BOOL m_bTabIcons;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `TRUE`, ikony są wyświetlane na każdej karcie MDI. W przeciwnym razie ikony nie są wyświetlane na kartach. Wartość domyślna to `FALSE`.  
  
##  <a name="m_ntabbordersize"></a>CMDITabInfo::m_nTabBorderSize  
 Określa rozmiar obramowania okna w pikselach, każdej karty.  
  
```  
int m_nTabBorderSize;  
```  
  
### <a name="remarks"></a>Uwagi  
 [CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) zwraca wartość domyślną.  
  
##  <a name="m_style"></a>CMDITabInfo::m_style  
 Określa styl etykiet kartę.  
  
```  
CMFCTabCtrl::Style m_style  
```  
  
### <a name="remarks"></a>Uwagi  
 Określ jedną z następujących stylów dla etykiet karty:  
  
 `STYLE_3D`  
 Styl 3W.  
  
 `STYLE_3D_ONENOTE`  
 Styl programu Microsoft OneNote.  
  
 `STYLE_3D_VS2005`  
 Styl Microsoft Visual Studio 2005.  
  
 `STYLE_3D_SCROLLED`  
 Styl 3W z etykietami kartę prostokąta.  
  
 `STYLE_FLAT_SHARED_HORZ_SCROLL`  
 Płaski z udostępnionego poziomy pasek przewijania.  
  
 `STYLE_3D_ROUNDED_SCROLL`  
 Styl 3W z etykietami round kartę.  
  
##  <a name="m_tablocation"></a>CMDITabInfo::m_tabLocation  
 Określa, czy etykiety karty znajdują się u góry lub u dołu strony.  
  
```  
CMFCTabCtrl::Location m_tabLocation;  
```  
  
### <a name="remarks"></a>Uwagi  
 Zastosowanie do karty jeden z następujących flag lokalizacji:  
  
-   LOCATION_BOTTOM: etykiety karty znajdują się w dolnej części strony.  
  
-   LOCATION_TOP: etykiety karty znajdują się w górnej części strony  
  
##  <a name="serialize"></a>CMDITabInfo::Serialize  
 Odczytuje i zapisuje ten obiekt z archiwum lub do archiwum.  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`ar`  
 A [CArchive — klasa](../../mfc/reference/carchive-class.md) obiektu do zserializowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)   
 [Grupy z kartami MDI](../../mfc/mdi-tabbed-groups.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
