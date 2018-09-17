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
ms.openlocfilehash: 02806f26f623b2f4ad7f19cd67216018da984e42
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713703"
---
# <a name="cmfcpopupmenubar-class"></a>Klasa CMFCPopupMenuBar
Pasek menu wbudowany w menu podręcznym.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCPopupMenuBar : public CMFCToolBar  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|Od razu ponownie oblicza układ w okienku. (Przesłania [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).)|  
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|Ładuje elementów menu podręcznego z menu określonego zasobu.|  
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|Zamyka przycisk menu podręcznego opóźnione.|  
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|Tworzy menu, przyciski menu podręcznego.|  
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|Lokalizuje pasek narzędzi, gdzie znajduje się określony punkt.|  
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|Określa rozmiar obrazów przycisku menu.|  
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|Zwraca identyfikator domyślny element menu.|  
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|Pobiera indeks najbardziej niedawno wywoływane polecenie menu.|  
|[CMFCPopupMenuBar::GetOffset](#getoffset)|Pobiera przesunięcie wiersza z paska menu podręcznego.|  
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|Importuje przycisków menu podręcznym menu określony.|  
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|Wskazuje, czy pasek menu podręczne jest w trybie listy rozwijanej w dół.|  
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|Wskazuje, czy pasek menu podręczne jest w trybie palety.|  
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|Wskazuje, czy jest panelu wstążki (FALSE domyślnie).|  
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|Wskazuje, czy jest panelu wstążki w regularnym trybie (FALSE domyślnie).|  
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|Ładuje zarchiwizowane menu.|  
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|Przywraca przycisk menu opóźnione zamknięcie paska menu podręcznego.|  
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|Ustawia styl przycisku na pasku narzędzi pod danym indeksem. (Przesłania [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)|  
|[CMFCPopupMenuBar::SetOffset](#setoffset)|Ustawia przesunięcie wiersza z paska menu podręcznego.|  
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|Uruchamia czasomierz dla przycisku menu opóźnione określonej w menu podręczne.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|Określa, czy szarym pasku bocznym, będą wyświetlane, gdy aplikacja ma wygląd Windows XP.|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCPopupMenuBar` Jest tworzony w tym samym czasie jako [klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) i osadzone wewnątrz niego. `CMFCPopupMenuBar` Dotyczy całego obszaru klienta z `CMFCPopupMenu` obiektu. Obsługuje ona klawiatury i myszy. Również komunikuje się ona dane wejściowe, aby `CMFCPopupMenu` i okno ramek najwyższego poziomu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zainicjować `CMFCPopupMenuBar` obiektu z `CMFCPopupMenu` obiektu. Ten fragment kodu jest częścią [Rysowanie Client sample](../../visual-cpp-samples.md).  
  
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
 Od razu ponownie oblicza układ w okienku paska menu podręcznego. (Przesłania [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).  
  
```  
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```  
  
### <a name="parameters"></a>Parametry  
*bRecalcLayout*<br/>
[in] Wartość TRUE, aby automatycznie ponownie Oblicz układ w okienku paska menu podręcznego; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="buildorigitems"></a>  CMFCPopupMenuBar::BuildOrigItems  
 Ładuje elementów menu podręcznego z menu określonego zasobu.  
  
```  
BOOL BuildOrigItems(UINT uiMenuResID);
```  
  
### <a name="parameters"></a>Parametry  
*uiMenuResID*<br/>
[in] Określa identyfikator menu zasób menu do załadowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE, jeśli to się powiedzie, lub FAŁSZ, jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="closedelayedsubmenu"></a>  CMFCPopupMenuBar::CloseDelayedSubMenu  
 Zamyka przycisk menu podręcznego, który został opóźniony.  
  
```  
virtual void CloseDelayedSubMenu();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="exporttomenu"></a>  CMFCPopupMenuBar::ExportToMenu  
 Tworzy menu, przyciski menu podręcznego.  
  
```  
virtual HMENU ExportToMenu() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca uchwyt do nowego menu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="finddestintationtoolbar"></a>  CMFCPopupMenuBar::FindDestintationToolBar  
 Lokalizuje pasek narzędzi, gdzie znajduje się określony punkt.  
  
```  
CMFCToolBar* FindDestintationToolBar(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
*Punkt*<br/>
[in] Punkt na ekranie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca uchwyt do paska narzędzi gdzie znajduje się punkt, jeśli istnieje, lub wartość NULL, jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcurrentmenuimagesize"></a>  CMFCPopupMenuBar::GetCurrentMenuImageSize  
 Określa rozmiar obrazów przycisku menu.  
  
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
 Pobiera indeks najbardziej niedawno wywoływane polecenie menu.  
  
```  
static int __stdcall GetLastCommandIndex();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca indeks ostatniego polecenia menu, która została wywołana.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getoffset"></a>  CMFCPopupMenuBar::GetOffset  
 Pobiera przesunięcie wiersza z paska menu podręcznego.  
  
```  
int GetOffset() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca przesunięcie wiersza z paska menu podręcznego.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość jest ustawiana za pomocą [CMFCPopupMenuBar::SetOffset](#setoffset).  
  
##  <a name="importfrommenu"></a>  CMFCPopupMenuBar::ImportFromMenu  
 Importuje przycisków menu podręcznym menu określony.  
  
```  
virtual BOOL ImportFromMenu(
    HMENU hMenu,  
    BOOL bShowAllCommands = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
*hMenu*<br/>
[in] Menu, z którego chcesz zaimportować przycisków menu podręcznego.  
  
*bShowAllCommands*<br/>
[in] Wartość TRUE, jeśli wszystkie polecenia w menu są importowane lub wartość FALSE, jeśli może być ukryta rzadko używane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli przycisków menu zostały pomyślnie zaimportowane z menu, lub FAŁSZ, jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isdropdownlistmode"></a>  CMFCPopupMenuBar::IsDropDownListMode  
 Wskazuje, czy pasek menu podręczne jest w trybie listy rozwijanej w dół.  
  
```  
BOOL IsDropDownListMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli pasek menu podręcznego nie jest w trybie listy rozwijanej w dół lub jeśli wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ispalettemode"></a>  CMFCPopupMenuBar::IsPaletteMode  
 Wskazuje, czy pasek menu podręczne jest w trybie palety.  
  
```  
BOOL IsPaletteMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE, jeśli jest włączony tryb palety, lub FAŁSZ, jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 Gdy pasek menu jest ustawiany w trybie palety, elementy menu są widoczne na wiele kolumn i ograniczoną liczbę wierszy.  
  
##  <a name="isribbonpanel"></a>  CMFCPopupMenuBar::IsRibbonPanel  
 Wskazuje, czy jest panelu wstążki (FALSE domyślnie).  
  
```  
virtual BOOL IsRibbonPanel() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość FALSE, domyślnie, co oznacza, że nie jest panelu wstążki.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isribbonpanelinregularmode"></a>  CMFCPopupMenuBar::IsRibbonPanelInRegularMode  
 Wskazuje, czy jest panelu wstążki w regularnym trybie (FALSE domyślnie).  
  
```  
virtual BOOL IsRibbonPanelInRegularMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość FALSE, domyślnie wskazujący, że to nie jest panelu wstążki do trybu normalnego.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="loadfromhash"></a>  CMFCPopupMenuBar::LoadFromHash  
 Ładuje zarchiwizowane menu.  
  
```  
BOOL LoadFromHash(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
*hMenu*<br/>
[in] Dojście do menu zarchiwizowane do załadowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli menu jest załadowany pomyślnie, lub FAŁSZ, jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_bdisablesidebarinxpmode"></a>  CMFCPopupMenuBar::m_bDisableSideBarInXPMode  
 Parametr logiczny, który wskazuje, czy aplikacja ma szarym pasku bocznym, gdy ma ona wygląd Windows XP.  
  
```  
BOOL m_bDisableSideBarInXPMode;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta zmienna członka jest ustawiona na wartość FALSE, a Twoja aplikacja ma wygląd Windows XP, struktura rysuje szarego paska bocznego w aplikacji.  
  
 Wartość domyślna to FALSE.  
  
##  <a name="restoredelayedsubmenu"></a>  CMFCPopupMenuBar::RestoreDelayedSubMenu  
 Przywraca przycisk menu opóźnione zamknięcie paska menu podręcznego.  
  
```  
virtual void RestoreDelayedSubMenu();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setbuttonstyle"></a>  CMFCPopupMenuBar::SetButtonStyle  
 Ustawia styl przycisku na pasku narzędzi pod danym indeksem. (Przesłania [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)  
  
```  
virtual void SetButtonStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
*nIndex*<br/>
[in] Liczony od zera indeks przycisku paska narzędzi, którego styl ma być utworzony.  
  
*nStyle*<br/>
[in] Styl przycisku. Zobacz [style formantu ToolBar](../../mfc/reference/toolbar-control-styles.md) listę narzędzi dostępnych stylów przycisków.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setoffset"></a>  CMFCPopupMenuBar::SetOffset  
 Ustawia przesunięcie wiersza z paska menu podręcznego.  
  
```  
void SetOffset(int iOffset);
```  
  
### <a name="parameters"></a>Parametry  
*iOffset*<br/>
[in] Liczba wierszy, przesunięcia paska menu podręcznego.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="startpopupmenutimer"></a>  CMFCPopupMenuBar::StartPopupMenuTimer  
 Uruchamia czasomierz dla przycisku menu opóźnione określonej w menu podręczne.  
  
```  
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,  
    int nDelayFactor = 1);
```  
  
### <a name="parameters"></a>Parametry  
*pMenuButton*<br/>
[in] Wskaźnik na przycisku menu, do których chcesz skonfigurować czasomierz opóźnienia.  
  
*nDelayFactor*<br/>
[in] Współczynnik opóźnienie równe co najmniej jeden do pomnożenia przez czas opóźnienia standardowe menu (zwykle od pół sekundy i pięć sekund).  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)   
 [Klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)
