---
title: CMFCBaseVisualManager Class
ms.date: 11/04/2016
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
ms.openlocfilehash: 0c26c0c9c9026f8312218b2ac15f83a50a67be79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403857"
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager Class

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

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia

*Rect*<br/>
[in] Prostokąt otaczający pole wyboru.

*bHighlighted*<br/>
[in] Określa, czy pole wyboru jest wyróżniona.

*nState*<br/>
[in] 0 nie jest zaznaczone, 1 dla zaznaczenia normalny

2-mieszane normalny.

*bWłączony*<br/>
[in] Określa, czy pole wyboru jest włączone.

*bPressed*<br/>
[in] Określa, czy pole wyboru jest wciśnięty.

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

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[in] Prostokąt otaczający obramowanie pola kombi.

*bWyłączone*<br/>
[in] Określa, czy obramowanie pola kombi jest wyłączona.

*bIsDropped*<br/>
[in] Określa, czy obramowanie pola kombi jest rozwijana.

*bIsHighlighted*<br/>
[in] Określa, czy obramowanie pola kombi jest wyróżniona.

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
|*pDC*|[in] Wskaźnik do kontekstu urządzenia.|
|*Rect*|[in] Prostokąt otaczający przycisku rozwijanego pola kombi.|
|*bWyłączone*|[in] Określa, czy przycisk listy rozwijanej pola kombi jest wyłączona.|
|*bIsDropped*|[in] Określa, czy przycisk listy rozwijanej pola kombi jest rozwijana.|
|*bIsHighlighted*|[in] Określa, czy przycisk listy rozwijanej pola kombi jest wyróżniona.|

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

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[in] Prostokąt otaczający przycisku polecenia.

*pButton*<br/>
[in] Wskaźnik do [klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md) obiektu do rysowania.

*uiState*<br/>
[in] Ignorowane. Stan jest pobierana z *pButton*.

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

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[in] Prostokąt otaczający przycisku radiowego.

*bHighlighted*<br/>
[in] Określa, czy przycisk radiowy zostanie wyróżniona.

*bChecked*<br/>
[in] Określa, czy zaznaczono opcję przycisku radiowego.

*bWłączony*<br/>
[in] Określa, czy włączono przycisku radiowego.

*bPressed*<br/>
[in] Określa, czy naciśnięciu przycisku radiowego.

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

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia.

*pStatusBar*<br/>
[in] Wskaźnik na pasku stanu. Ta wartość jest ignorowana.

*rectProgress*<br/>
[in] Prostokąt otaczający pasek postępu w *kontrolera pDC* współrzędnych.

*nProgressTotal*<br/>
[in] Całkowity postęp wartość.

*nProgressCurr*<br/>
[in] Bieżąca wartość postępu.

*clrBar*<br/>
[in] Kolor początkowy. `CMFCBaseVisualManager` ignoruje to. Klasy pochodne go używać gradientów kolorów.

*clrProgressBarDest*<br/>
[in] Kolor końcowy. `CMFCBaseVisualManager` ignoruje to. Klasy pochodne go używać gradientów kolorów.

*clrProgressText*<br/>
[in] Kolor tekstu w toku. `CMFCBaseVisualManager` ignoruje to. Kolor tekstu jest definiowany przez `afxGlobalData.clrBtnText`.

*bProgressText*<br/>
[in] Określa, czy ma być wyświetlany tekst dotyczący postępu.

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

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia.

*pBar*<br/>
[in] Wskaźnik do okienka, w których tło ma być rysowany.

*rectClient*<br/>
[in] Obszar, który ma zostać wypełniony prostokąt otaczający.

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

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
