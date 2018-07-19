---
title: Klasa CMFCBaseVisualManager | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7b21651bdab6bf2e4603a8fa012480a6201e34b
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336226"
---
# <a name="cmfcbasevisualmanager-class"></a>Klasa CMFCBaseVisualManager
Warstwa między pochodnej menedżerów wizualnych oraz interfejsu API Windows motywu.  
  
 `CMFCBaseVisualManager` ładuje UxTheme.dll, jeśli jest dostępny i zarządza dostępem do metody interfejsu API programu Windows motywu.  
  
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
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|Rysuje kontrolkę pola wyboru przy użyciu bieżącego motywu Windows.|  
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|Rysuje obramowanie pola kombi, przy użyciu bieżącego motywu Windows.|  
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|Rysuje przycisku rozwijanego pola kombi, przy użyciu bieżącego motywu Windows.|  
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|Rysuje przycisku polecenia przy użyciu bieżącego motywu Windows.|  
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|Rysuje kontrolkę przycisku radiowego za pomocą bieżący motyw Windows.|  
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|Rysuje pasek postępu na formant paska stanu ( [klasa CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)) przy użyciu bieżącego motywu Windows.|  
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|Wypełnia tła formantu paska pomocniczego przy użyciu bieżącego motywu Windows.|  
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Pobiera bieżący motyw Windows.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Wywołania `CloseThemeData` wszystkie dojścia otrzymanego w `UpdateSystemColors`.|  
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Wywołania `OpenThemeData` można uzyskać dojścia do rysowania różnych formantów: systemu windows, paski narzędzi, przycisków i tak dalej.|  
  
## <a name="remarks"></a>Uwagi  
 Nie masz bezpośrednie tworzenie wystąpień obiektów tej klasy.  
  
 Ponieważ klasa bazowa dla wszystkich menedżerów wizualnych, możesz po prostu wywołać [CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance), uzyskiwanie wskaźnika do bieżącego Menedżera wizualizacji i dostęp do metody `CMFCBaseVisualManager` przy użyciu tego wskaźnika. Jednak w przypadku wyświetlania kontrolki przy użyciu bieżącego motywu Windows lepiej jest używać `CMFCVisualManagerWindows` interfejsu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxvisualmanager.h  
  
##  <a name="cleanupthemes"></a>  CMFCBaseVisualManager::CleanUpThemes  
 Wywołania `CloseThemeData` wszystkie dojścia otrzymanego w `UpdateSystemColors`.  
  
```  
void CleanUpThemes();
```  
  
### <a name="remarks"></a>Uwagi  
 Tylko do użytku wewnętrznego.  
  
##  <a name="cmfcbasevisualmanager"></a>  CMFCBaseVisualManager::CMFCBaseVisualManager  
 Tworzy i inicjuje `CMFCBaseVisualManager` obiektu.  
  
```  
CMFCBaseVisualManager();
```  
  
##  <a name="drawcheckbox"></a>  CMFCBaseVisualManager::DrawCheckBox  
 Rysuje kontrolkę pola wyboru przy użyciu bieżącego motywu Windows.  
  
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
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia  
  
 [in] *rect*  
 Prostokąt otaczający pole wyboru.  
  
 [in] *bHighlighted*  
 Określa, czy pole wyboru jest wyróżniona.  
  
 [in] *nInformacje*  
 0 nie jest zaznaczone, 1 dla zaznaczenia normalny  
  
 2-mieszane normalny.  
  
 [in] *bWłączony*  
 Określa, czy pole wyboru jest włączone.  
  
 [in] *bPressed*  
 Określa, czy pole wyboru jest wciśnięty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli motyw interfejsu API jest włączony; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Wartości *nInformacje* odpowiadają poniższym style pól wyboru.  
  
|nInformacje|Pole wyboru stylu|  
|------------|---------------------|  
|0|CBS_UNCHECKEDNORMAL|  
|1|CBS_CHECKEDNORMAL|  
|2|CBS_MIXEDNORMAL|  
  
##  <a name="drawcomboborder"></a>  CMFCBaseVisualManager::DrawComboBorder  
 Rysuje obramowanie pola kombi, przy użyciu bieżącego motywu Windows.  
  
```  
virtual BOOL DrawComboBorder(
    CDC* pDC,   
    CRect rect,   
    BOOL bDisabled,   
    BOOL bIsDropped,   
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *rect*  
 Prostokąt otaczający obramowanie pola kombi.  
  
 [in] *bWyłączone*  
 Określa, czy obramowanie pola kombi jest wyłączona.  
  
 [in] *bIsDropped*  
 Określa, czy obramowanie pola kombi jest rozwijana.  
  
 [in] *bIsHighlighted*  
 Określa, czy obramowanie pola kombi jest wyróżniona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli motyw interfejsu API jest włączony; w przeciwnym razie wartość FALSE.  
  
##  <a name="drawcombodropbutton"></a>  CMFCBaseVisualManager::DrawComboDropButton  
 Rysuje przycisku rozwijanego pola kombi, przy użyciu bieżącego motywu Windows.  
  
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
|[in] *podstawowego kontrolera domeny*|Wskaźnik do kontekstu urządzenia.|  
|[in] *rect*|Prostokąt otaczający przycisku rozwijanego pola kombi.|  
|[in] *bWyłączone*|Określa, czy przycisk listy rozwijanej pola kombi jest wyłączona.|  
|[in] *bIsDropped*|Określa, czy przycisk listy rozwijanej pola kombi jest rozwijana.|  
|[in] *bIsHighlighted*|Określa, czy przycisk listy rozwijanej pola kombi jest wyróżniona.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli motyw interfejsu API jest włączony; w przeciwnym razie wartość FALSE.  
  
##  <a name="drawpushbutton"></a>  CMFCBaseVisualManager::DrawPushButton  
 Rysuje przycisku polecenia przy użyciu bieżącego motywu Windows.  
  
```  
virtual BOOL DrawPushButton(
    CDC* pDC,   
    CRect rect,   
    CMFCButton* pButton,   
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *rect*  
 Prostokąt otaczający przycisku polecenia.  
  
 [in] *pButton*  
 Wskaźnik do [klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md) obiektu do rysowania.  
  
 [in] *uiState*  
 Ignorowane. Stan jest pobierana z *pButton*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli motyw interfejsu API jest włączony; w przeciwnym razie wartość FALSE.  
  
##  <a name="drawradiobutton"></a>  CMFCBaseVisualManager::DrawRadioButton  
 Rysuje kontrolkę przycisku radiowego za pomocą bieżący motyw Windows.  
  
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
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *rect*  
 Prostokąt otaczający przycisku radiowego.  
  
 [in] *bHighlighted*  
 Określa, czy przycisk radiowy zostanie wyróżniona.  
  
 [in] *bChecked*  
 Określa, czy zaznaczono opcję przycisku radiowego.  
  
 [in] *bWłączony*  
 Określa, czy włączono przycisku radiowego.  
  
 [in] *bPressed*  
 Określa, czy naciśnięciu przycisku radiowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli motyw interfejsu API jest włączony; w przeciwnym razie wartość FALSE.  
  
##  <a name="drawstatusbarprogress"></a>  CMFCBaseVisualManager::DrawStatusBarProgress  
 Rysuje pasek postępu w formantu paska stanu ( [klasa CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)) przy użyciu bieżącego motywu Windows.  
  
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
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *pStatusBar*  
 Wskaźnik na pasku stanu. Ta wartość jest ignorowana.  
  
 [in] *rectProgress*  
 Prostokąt otaczający pasek postępu w *kontrolera pDC* współrzędnych.  
  
 [in] *nProgressTotal*  
 Całkowity postęp wartość.  
  
 [in] *nProgressCurr*  
 Bieżąca wartość postępu.  
  
 [in] *clrBar*  
 Kolor początkowy. `CMFCBaseVisualManager` ignoruje to. Klasy pochodne go używać gradientów kolorów.  
  
 [in] *clrProgressBarDest*  
 Kolor końcowy. `CMFCBaseVisualManager` ignoruje to. Klasy pochodne go używać gradientów kolorów.  
  
 [in] *clrProgressText*  
 Kolor tekstu w toku. `CMFCBaseVisualManager` ignoruje to. Kolor tekstu jest definiowany przez `afxGlobalData.clrBtnText`.  
  
 [in] *bProgressText*  
 Określa, czy ma być wyświetlany tekst dotyczący postępu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli motyw interfejsu API jest włączony; w przeciwnym razie wartość FALSE.  
  
##  <a name="fillrebarpane"></a>  CMFCBaseVisualManager::FillReBarPane  
 Wypełnia tła formantu paska pomocniczego przy użyciu bieżącego motywu Windows.  
  
```  
virtual void FillReBarPane(
    CDC* pDC,   
    CBasePane* pBar,   
    CRect rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *pBar*  
 Wskaźnik do okienka, w których tło ma być rysowany.  
  
 [in] *rectClient*  
 Obszar, który ma zostać wypełniony prostokąt otaczający.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli motyw interfejsu API jest włączony; w przeciwnym razie wartość FALSE.  
  
##  <a name="getstandardwindowstheme"></a>  CMFCBaseVisualManager::GetStandardWindowsTheme  
 Pobiera bieżący motyw Windows.  
  
```  
virtual WinXpTheme GetStandardWindowsTheme();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obecnie wybrany kolor motywu Windows. Może to być jeden z poniższych wyliczonych wartości:  
  
- `WinXpTheme_None` — nie ma żadnych motyw włączone.  
  
- `WinXpTheme_NonStandard` -motyw inny niż standardowy jest zaznaczone (tzn. wybrano motyw, ale żaden z poniższej listy).  
  
- `WinXpTheme_Blue` -motyw niebieski (Luna).  
  
- `WinXpTheme_Olive` -oliwek motywu.  
  
- `WinXpTheme_Silver` -silver motywu.  
  
##  <a name="updatesystemcolors"></a>  CMFCBaseVisualManager::UpdateSystemColors  
 Wywołania `OpenThemeData` można uzyskać dojścia do rysowania różnych formantów: systemu windows, paski narzędzi, przycisków i tak dalej.  
  
```  
void UpdateSystemColors();
```  
  
### <a name="remarks"></a>Uwagi  
 Tylko do użytku wewnętrznego.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
