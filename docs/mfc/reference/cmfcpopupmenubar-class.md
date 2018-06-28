---
title: Klasa CMFCPopupMenuBar | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::AdjustSizeImmediate
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::BuildOrigItems
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::CloseDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ExportToMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::FindDestintationToolBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetCurrentMenuImageSize
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetDefaultMenuId
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetLastCommandIndex
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ImportFromMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsDropDownListMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsPaletteMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanel
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanelInRegularMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::LoadFromHash
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::RestoreDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetButtonStyle
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::StartPopupMenuTimer
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::m_bDisableSideBarInXPMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCPopupMenuBar [MFC], AdjustSizeImmediate
- CMFCPopupMenuBar [MFC], BuildOrigItems
- CMFCPopupMenuBar [MFC], CloseDelayedSubMenu
- CMFCPopupMenuBar [MFC], ExportToMenu
- CMFCPopupMenuBar [MFC], FindDestintationToolBar
- CMFCPopupMenuBar [MFC], GetCurrentMenuImageSize
- CMFCPopupMenuBar [MFC], GetDefaultMenuId
- CMFCPopupMenuBar [MFC], GetLastCommandIndex
- CMFCPopupMenuBar [MFC], GetOffset
- CMFCPopupMenuBar [MFC], ImportFromMenu
- CMFCPopupMenuBar [MFC], IsDropDownListMode
- CMFCPopupMenuBar [MFC], IsPaletteMode
- CMFCPopupMenuBar [MFC], IsRibbonPanel
- CMFCPopupMenuBar [MFC], IsRibbonPanelInRegularMode
- CMFCPopupMenuBar [MFC], LoadFromHash
- CMFCPopupMenuBar [MFC], RestoreDelayedSubMenu
- CMFCPopupMenuBar [MFC], SetButtonStyle
- CMFCPopupMenuBar [MFC], SetOffset
- CMFCPopupMenuBar [MFC], StartPopupMenuTimer
- CMFCPopupMenuBar [MFC], m_bDisableSideBarInXPMode
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aede6e3224149bd237ca2bb830370718105e1f83
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037762"
---
# <a name="cmfcpopupmenubar-class"></a>Klasa CMFCPopupMenuBar
Pasek menu osadzone w menu podręczne.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCPopupMenuBar : public CMFCToolBar  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|Natychmiast ponownie oblicza układ okienka. (Przesłania [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).)|  
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|Ładuje elementów menu podręcznego z menu określonego zasobu.|  
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|Zamyka przycisk menu podręcznego opóźnione.|  
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|Tworzy menu z przycisków menu podręczne.|  
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|Lokalizuje pasku narzędzi, gdzie znajduje się określony punkt.|  
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|Określa rozmiar obrazów przycisk menu.|  
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|Zwraca identyfikator domyślny element menu.|  
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|Pobiera indeks najbardziej ostatnio wywołanej polecenia menu.|  
|[CMFCPopupMenuBar::GetOffset](#getoffset)|Pobiera przesunięcia wiersza paska menu podręcznego.|  
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|Importuje przycisków menu podręcznego z określonym menu.|  
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|Wskazuje, czy pasek menu podręczne jest w trybie listy rozwijanej w dół.|  
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|Wskazuje, czy pasek menu podręczne jest w trybie palety.|  
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|Wskazuje, czy jest panelu wstążki ( `FALSE` domyślnie).|  
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|Wskazuje, czy panel wstążki jest w trybie regularne ( `FALSE` domyślnie).|  
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|Ładuje menu zarchiwizowane.|  
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|Przywraca przycisk menu opóźnione zamknięcie paska menu podręcznego.|  
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|Ustawia styl przycisku paska narzędzi pod danym indeksem. (Przesłania [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)|  
|[CMFCPopupMenuBar::SetOffset](#setoffset)|Ustawia przesunięcie wiersza paska menu podręcznego.|  
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|Uruchamia czasomierz dla określonego okna podręcznego opóźnione przycisku menu.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|Określa, czy będzie wyświetlana szarego paska bocznego, gdy aplikacja ma wygląd systemu Windows XP.|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCPopupMenuBar` Jest tworzony w tym samym czasie jako [klasy CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) i osadzone wewnątrz niej. `CMFCPopupMenuBar` Obejmuje obszaru klienckiego cały `CMFCPopupMenu` obiektu. Obsługuje ona klawiatury i myszy. Także komunikacji, który wejście do `CMFCPopupMenu` i okna ramowego najwyższego poziomu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak zainicjować `CMFCPopupMenuBar` obiekt z `CMFCPopupMenu` obiektu. Następujący fragment kodu jest częścią [rysowania klienta — przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpopupmenubar.h  
  
##  <a name="adjustsizeimmediate"></a>  CMFCPopupMenuBar::AdjustSizeImmediate  
 Natychmiast ponownie oblicza układ okienku paska menu podręcznego. (Przesłania [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).  
  
```  
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bRecalcLayout*  
 `TRUE` Aby automatycznie ponownie Oblicz układ okienku paska menu podręcznego. w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="buildorigitems"></a>  CMFCPopupMenuBar::BuildOrigItems  
 Ładuje elementów menu podręcznego z menu określonego zasobu.  
  
```  
BOOL BuildOrigItems(UINT uiMenuResID);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *uiMenuResID*  
 Określa identyfikator menu zasobów menu do załadowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` w przypadku powodzenia lub `FALSE` , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="closedelayedsubmenu"></a>  CMFCPopupMenuBar::CloseDelayedSubMenu  
 Zamyka przycisk menu podręcznego opóźnione.  
  
```  
virtual void CloseDelayedSubMenu();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="exporttomenu"></a>  CMFCPopupMenuBar::ExportToMenu  
 Tworzy menu z przycisków menu podręcznego.  
  
```  
virtual HMENU ExportToMenu() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście do nowego menu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="finddestintationtoolbar"></a>  CMFCPopupMenuBar::FindDestintationToolBar  
 Lokalizuje pasku narzędzi, gdzie znajduje się określony punkt.  
  
```  
CMFCToolBar* FindDestintationToolBar(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *punktu*  
 Punkt na ekranie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście do paska narzędzi gdzie znajduje się punkt, jeśli therei, lub `NULL` , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcurrentmenuimagesize"></a>  CMFCPopupMenuBar::GetCurrentMenuImageSize  
 Określa rozmiar obrazów przycisk menu.  
  
```  
virtual CSize GetCurrentMenuImageSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca rozmiar obrazów przycisk menu na pasku narzędzi.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getdefaultmenuid"></a>  CMFCPopupMenuBar::GetDefaultMenuId  
 Zwraca identyfikator domyślny element menu.  
  
```  
UINT GetDefaultMenuId() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca identyfikator domyślny element menu na pasku menu podręcznego.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getlastcommandindex"></a>  CMFCPopupMenuBar::GetLastCommandIndex  
 Pobiera indeks najbardziej ostatnio wywołanej polecenia menu.  
  
```  
static int __stdcall GetLastCommandIndex();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca indeks ostatnie polecenie menu, która została wywołana.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getoffset"></a>  CMFCPopupMenuBar::GetOffset  
 Pobiera przesunięcia wiersza paska menu podręcznego.  
  
```  
int GetOffset() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca przesunięcie wiersza na pasku menu podręcznego.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość jest ustawiana za pomocą [CMFCPopupMenuBar::SetOffset](#setoffset).  
  
##  <a name="importfrommenu"></a>  CMFCPopupMenuBar::ImportFromMenu  
 Importuje przycisków menu podręcznego z określonym menu.  
  
```  
virtual BOOL ImportFromMenu(
    HMENU hMenu,  
    BOOL bShowAllCommands = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *hMenu*  
 Menu, z którego będą importowane przycisków menu podręcznego.  
  
 [in] *bShowAllCommands*  
 `TRUE` w przypadku wszystkich poleceń menu do zaimportowania, lub `FALSE` Jeśli rzadko używane te mogą być ukryte.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` Jeśli przycisków menu zostały pomyślnie zaimportowane z menu lub `FALSE` , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isdropdownlistmode"></a>  CMFCPopupMenuBar::IsDropDownListMode  
 Wskazuje, czy pasek menu podręczne jest w trybie listy rozwijanej w dół.  
  
```  
BOOL IsDropDownListMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` Jeśli paska menu podręczne jest w trybie listy rozwijanej w dół, lub `FALSE` , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ispalettemode"></a>  CMFCPopupMenuBar::IsPaletteMode  
 Wskazuje, czy pasek menu podręczne jest w trybie palety.  
  
```  
BOOL IsPaletteMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` Jeśli włączony jest tryb palety, lub `FALSE` , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 Gdy na pasku menu jest ustawiona na tryb palety, elementy menu pojawiają się na wiele kolumn i ograniczonej liczby wierszy.  
  
##  <a name="isribbonpanel"></a>  CMFCPopupMenuBar::IsRibbonPanel  
 Wskazuje, czy jest panelu wstążki ( `FALSE` domyślnie).  
  
```  
virtual BOOL IsRibbonPanel() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `FALSE` domyślnie wskazujący, że nie jest panelu wstążki.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isribbonpanelinregularmode"></a>  CMFCPopupMenuBar::IsRibbonPanelInRegularMode  
 Wskazuje, czy panel wstążki jest w trybie regularne ( `FALSE` domyślnie).  
  
```  
virtual BOOL IsRibbonPanelInRegularMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `FALSE` domyślnie wskazujący, że nie jest panelu wstążki w trybie regularne.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="loadfromhash"></a>  CMFCPopupMenuBar::LoadFromHash  
 Ładuje menu zarchiwizowane.  
  
```  
BOOL LoadFromHash(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *hMenu*  
 Dojście do menu zarchiwizowane załadować.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` Jeśli menu został załadowany pomyślnie, lub `FALSE` , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_bdisablesidebarinxpmode"></a>  CMFCPopupMenuBar::m_bDisableSideBarInXPMode  
 Parametrów typu Boolean wskazującą, czy aplikacja ma wygląd systemu Windows XP, ma szarego paska bocznego.  
  
```  
BOOL m_bDisableSideBarInXPMode;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ustawiono tę zmienną elementu członkowskiego `FALSE` i aplikacja ma wygląd systemu Windows XP, platformę rysuje szarego paska bocznego w aplikacji.  
  
 Wartość domyślna to `FALSE`.  
  
##  <a name="restoredelayedsubmenu"></a>  CMFCPopupMenuBar::RestoreDelayedSubMenu  
 Przywraca przycisk menu opóźnione zamknięcie paska menu podręcznego.  
  
```  
virtual void RestoreDelayedSubMenu();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setbuttonstyle"></a>  CMFCPopupMenuBar::SetButtonStyle  
 Ustawia styl przycisku paska narzędzi pod danym indeksem. (Przesłania [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)  
  
```  
virtual void SetButtonStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nIndex*  
 Liczony od zera indeks przycisku paska narzędzi, którego styl ma być utworzony.  
  
 [in] *nStyle*  
 Styl przycisku. Zobacz [style formantu ToolBar](../../mfc/reference/toolbar-control-styles.md) listę dostępnych narzędzi style przycisku.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setoffset"></a>  CMFCPopupMenuBar::SetOffset  
 Ustawia przesunięcie wiersza paska menu podręcznego.  
  
```  
void SetOffset(int iOffset);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iOffset*  
 Liczba wierszy na pasku menu podręcznego powinien przesunięcia.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="startpopupmenutimer"></a>  CMFCPopupMenuBar::StartPopupMenuTimer  
 Uruchamia czasomierz dla określonego okna podręcznego opóźnione przycisku menu.  
  
```  
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,  
    int nDelayFactor = 1);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pMenuButton*  
 Wskaźnik do przycisku menu, do których chcesz ustawić czasomierza opóźnienia.  
  
 [in] *nDelayFactor*  
 Współczynnik opóźnienie równa co najmniej jeden, aby pomnożyć przez czas opóźnienia standardowe menu (zazwyczaj między pół sekundy i 5 sekund).  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)   
 [Klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)
