---
title: Klasa CMFCBaseVisualManager | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawCheckBox
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboBorder
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboDropButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawPushButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawRadioButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawStatusBarProgress
- AFXVISUALMANAGER/CMFCBaseVisualManager::FillReBarPane
- AFXVISUALMANAGER/CMFCBaseVisualManager::GetStandardWindowsTheme
- AFXVISUALMANAGER/CMFCBaseVisualManager::CleanUpThemes
- AFXVISUALMANAGER/CMFCBaseVisualManager::UpdateSystemColors
dev_langs:
- C++
helpviewer_keywords:
- CMFCBaseVisualManager [MFC], CMFCBaseVisualManager
- CMFCBaseVisualManager [MFC], DrawCheckBox
- CMFCBaseVisualManager [MFC], DrawComboBorder
- CMFCBaseVisualManager [MFC], DrawComboDropButton
- CMFCBaseVisualManager [MFC], DrawPushButton
- CMFCBaseVisualManager [MFC], DrawRadioButton
- CMFCBaseVisualManager [MFC], DrawStatusBarProgress
- CMFCBaseVisualManager [MFC], FillReBarPane
- CMFCBaseVisualManager [MFC], GetStandardWindowsTheme
- CMFCBaseVisualManager [MFC], CleanUpThemes
- CMFCBaseVisualManager [MFC], UpdateSystemColors
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: edb579cff639da9965c7214c2dd8abce8459d254
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcbasevisualmanager-class"></a>Klasa CMFCBaseVisualManager
Warstwa między menedżerami visual pochodnej i interfejs API kompozycji systemu Windows.  
  
 `CMFCBaseVisualManager`ładuje UxTheme.dll, jeśli jest dostępny i zarządza dostępem do metody interfejsu API kompozycji systemu Windows.  
  
 Ta klasa jest tylko do użytku wewnętrznego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCBaseVisualManager: public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCBaseVisualManager::CMFCBaseVisualManager](#cmfcbasevisualmanager)|Tworzy i inicjuje `CMFCBaseVisualManager` obiektu.|  
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|Rysuje kontrolkę pola wyboru przy użyciu bieżącego motywu systemu Windows.|  
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|Rysuje obramowanie pola kombi, przy użyciu bieżącego motywu systemu Windows.|  
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|Rysuje przycisku rozwijanego pola kombi przy użyciu bieżącego motywu systemu Windows.|  
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|Rysuje przycisku polecenia przy użyciu bieżącego motywu systemu Windows.|  
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|Rysuje kontrolkę przycisku radiowego za pomocą bieżącego motywu systemu Windows.|  
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|Rysuje pasek postępu w formancie paska stanu ( [CMFCStatusBar — klasa](../../mfc/reference/cmfcstatusbar-class.md)) przy użyciu bieżącego motywu systemu Windows.|  
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|Wypełnia tła formantu paska pomocniczego przy użyciu bieżącego motywu systemu Windows.|  
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Pobiera bieżący motyw systemu Windows.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Wywołania `CloseThemeData` wszystkie dojścia otrzymanego w `UpdateSystemColors`.|  
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Wywołania `OpenThemeData` można uzyskać dojścia do rysowania różnych formantów: systemu windows, pasków narzędzi, przycisków i tak dalej.|  
  
## <a name="remarks"></a>Uwagi  
 Nie masz bezpośrednio utworzyć wystąpienia obiektów tej klasy.  
  
 Klasa podstawowa dla wszystkich menedżerów visual, dlatego można po prostu Wywołaj [CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance), uzyskiwanie wskaźnika do bieżącego Menedżera Visual i metody dla dostępu `CMFCBaseVisualManager` przy użyciu tego wskaźnika. Jednak jeśli konieczne wyświetlenie formantu przy użyciu bieżącego motywu systemu Windows, lepiej jest użyć `CMFCVisualManagerWindows` interfejsu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxvisualmanager.h  
  
##  <a name="cleanupthemes"></a>CMFCBaseVisualManager::CleanUpThemes  
 Wywołania `CloseThemeData` wszystkie dojścia otrzymanego w `UpdateSystemColors`.  
  
```  
void CleanUpThemes();
```  
  
### <a name="remarks"></a>Uwagi  
 Tylko do użytku wewnętrznego.  
  
##  <a name="cmfcbasevisualmanager"></a>CMFCBaseVisualManager::CMFCBaseVisualManager  
 Tworzy i inicjuje `CMFCBaseVisualManager` obiektu.  
  
```  
CMFCBaseVisualManager();
```  
  
##  <a name="drawcheckbox"></a>CMFCBaseVisualManager::DrawCheckBox  
 Rysuje kontrolkę pola wyboru przy użyciu bieżącego motywu systemu Windows.  
  
```  
virtual BOOL DrawCheckBox(
    CDC* pDC,   
    CRect rect,   
    BOOL bHighlighted,   
    int nState,   
    BOOL bEnabled,   
    BOOL bPressed);

);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia  
  
 [in]`rect`  
 Prostokąt ograniczający pole wyboru.  
  
 [in]`bHighlighted`  
 Określa, czy pole wyboru zostanie wyróżniona.  
  
 [in]`nState`  
 0 nie jest zaznaczona, 1 dla zaznaczonych normalny  
  
 2-mieszane normalny.  
  
 [in]`bEnabled`  
 Określa, czy pole wyboru jest włączone.  
  
 [in]`bPressed`  
 Określa, czy pole wyboru zostanie naciśnięty.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli włączono interfejs API motywu; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Wartości `nState` odpowiadają następujące style pola wyboru.  
  
|nInformacje|Styl pola wyboru|  
|------------|---------------------|  
|0|CBS_UNCHECKEDNORMAL|  
|1|CBS_CHECKEDNORMAL|  
|2|CBS_MIXEDNORMAL|  
  
##  <a name="drawcomboborder"></a>CMFCBaseVisualManager::DrawComboBorder  
 Rysuje obramowanie pola kombi przy użyciu bieżącego motywu systemu Windows.  
  
```  
virtual BOOL DrawComboBorder(
    CDC* pDC,   
    CRect rect,   
    BOOL bDisabled,   
    BOOL bIsDropped,   
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in]`rect`  
 Prostokąt ograniczający obramowanie pola kombi.  
  
 [in]`bDisabled`  
 Określa, czy obramowanie pola kombi jest wyłączone.  
  
 [in]`bIsDropped`  
 Określa, czy jest rozwijana obramowanie pola kombi.  
  
 [in]`bIsHighlighted`  
 Określa, czy zostanie wyróżniona obramowanie pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli włączono interfejs API motywu; w przeciwnym razie `FALSE`.  
  
##  <a name="drawcombodropbutton"></a>CMFCBaseVisualManager::DrawComboDropButton  
 Rysuje przycisku rozwijanego pola kombi przy użyciu bieżącego motywu systemu Windows.  
  
```  
virtual BOOL DrawComboDropButton(
    CDC* pDC,   
    CRect rect,   
    BOOL bDisabled,   
    BOOL bIsDropped,   
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`pDC`|Wskaźnik do kontekstu urządzenia.|  
|[in]`rect`|Prostokąt ograniczający przycisku rozwijanego pola kombi.|  
|[in]`bDisabled`|Określa, czy przycisk listy rozwijanej pola kombi jest wyłączone.|  
|[in]`bIsDropped`|Określa, czy jest rozwijana przycisku rozwijanego pola kombi.|  
|[in]`bIsHighlighted`|Określa, czy zostanie wyróżniona przycisku rozwijanego pola kombi.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli włączono interfejs API motywu; w przeciwnym razie `FALSE`.  
  
##  <a name="drawpushbutton"></a>CMFCBaseVisualManager::DrawPushButton  
 Rysuje przycisku polecenia przy użyciu bieżącego motywu systemu Windows.  
  
```  
virtual BOOL DrawPushButton(
    CDC* pDC,   
    CRect rect,   
    CMFCButton* pButton,   
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in]`rect`  
 Prostokąt ograniczający przycisku polecenia.  
  
 [in]`pButton`  
 Wskaźnik do [klasy CMFCButton](../../mfc/reference/cmfcbutton-class.md) obiektu do rysowania.  
  
 [in]`uiState`  
 Ignorowane. Stan jest pobierana z `pButton`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli włączono interfejs API motywu; w przeciwnym razie `FALSE`.  
  
##  <a name="drawradiobutton"></a>CMFCBaseVisualManager::DrawRadioButton  
 Rysuje kontrolkę przycisku radiowego za pomocą bieżącego motywu systemu Windows.  
  
```  
virtual BOOL DrawRadioButton(
    CDC* pDC,   
    CRect rect,   
    BOOL bHighlighted,   
    BOOL bChecked,   
    BOOL bEnabled,   
    BOOL bPressed);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in]`rect`  
 Prostokąt ograniczający przycisku radiowego.  
  
 [in]`bHighlighted`  
 Określa, czy przycisk radiowy zostanie wyróżniona.  
  
 [in]`bChecked`  
 Określa, czy przycisk radiowy jest zaznaczony.  
  
 [in]`bEnabled`  
 Określa, czy przycisk radiowy jest włączone.  
  
 [in]`bPressed`  
 Określa, czy zostanie naciśnięty przycisk radiowy.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli włączono interfejs API motywu; w przeciwnym razie `FALSE`.  
  
##  <a name="drawstatusbarprogress"></a>CMFCBaseVisualManager::DrawStatusBarProgress  
 Rysuje pasek postępu w formantu paska stanu ( [CMFCStatusBar — klasa](../../mfc/reference/cmfcstatusbar-class.md)) przy użyciu bieżącego motywu systemu Windows.  
  
```  
virtual BOOL DrawStatusBarProgress(
    CDC* pDC,   
    CMFCStatusBar* pStatusBar,   
    CRect rectProgress,   
    int nProgressTotal,   
    int nProgressCurr,  
    COLORREF clrBar,   
    COLORREF clrProgressBarDest,   
    COLORREF clrProgressText,   
    BOOL bProgressText);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in]`pStatusBar`  
 Wskaźnik do paska stanu. Ta wartość jest ignorowana.  
  
 [in]`rectProgress`  
 Prostokąt ograniczający pasek postępu w `pDC` współrzędnych.  
  
 [in]`nProgressTotal`  
 Wartość całkowita postępu.  
  
 [in]`nProgressCurr`  
 Bieżąca wartość postępu.  
  
 [in]`clrBar`  
 Kolor początkowy. `CMFCBaseVisualManager`ignoruje to. Klasy pochodne może być używany do gradientu koloru.  
  
 [in]`clrProgressBarDest`  
 Kolor końcowy. `CMFCBaseVisualManager`ignoruje to. Klasy pochodne może być używany do gradientu koloru.  
  
 [in]`clrProgressText`  
 Kolor tekstu w toku. `CMFCBaseVisualManager`ignoruje to. Kolor tekstu jest definiowana za pomocą `afxGlobalData.clrBtnText`.  
  
 [in]`bProgressText`  
 Określa, czy do wyświetlania tekstu w toku.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli włączono interfejs API motywu; w przeciwnym razie `FALSE`.  
  
##  <a name="fillrebarpane"></a>CMFCBaseVisualManager::FillReBarPane  
 Wypełnia tła formantu paska pomocniczego przy użyciu bieżącego motywu systemu Windows.  
  
```  
virtual void FillReBarPane(
    CDC* pDC,   
    CBasePane* pBar,   
    CRect rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in]`pBar`  
 Wskaźnik do tła, których ma być rysowany okienka.  
  
 [in]`rectClient`  
 Prostokąt ograniczający do wypełnienia obszaru.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli włączono interfejs API motywu; w przeciwnym razie `FALSE`.  
  
##  <a name="getstandardwindowstheme"></a>CMFCBaseVisualManager::GetStandardWindowsTheme  
 Pobiera bieżący motyw systemu Windows.  
  
```  
virtual WinXpTheme GetStandardWindowsTheme();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Aktualnie wybrany kolor motywu systemu Windows. Może to być jedna z następujących wartości:  
  
- `WinXpTheme_None`-Brak motywu włączone nie istnieje.  
  
- `WinXpTheme_NonStandard`-motyw z systemem innym niż standardowe wybrano (to znaczy motywu jest zaznaczona, ale żaden z poniższej listy).  
  
- `WinXpTheme_Blue`-motywu niebieski (Luna).  
  
- `WinXpTheme_Olive`-oliwek motywu.  
  
- `WinXpTheme_Silver`-motyw srebrny.  
  
##  <a name="updatesystemcolors"></a>CMFCBaseVisualManager::UpdateSystemColors  
 Wywołania `OpenThemeData` można uzyskać dojścia do rysowania różnych formantów: systemu windows, pasków narzędzi, przycisków i tak dalej.  
  
```  
void UpdateSystemColors();
```  
  
### <a name="remarks"></a>Uwagi  
 Tylko do użytku wewnętrznego.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
