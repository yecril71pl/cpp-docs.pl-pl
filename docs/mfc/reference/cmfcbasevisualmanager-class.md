---
title: Klasa CMFCBaseVisualManager
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
ms.openlocfilehash: 28efe75c3c825c04c88f9f2263a3db2d83d4f3af
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561326"
---
# <a name="cmfcbasevisualmanager-class"></a>Klasa CMFCBaseVisualManager

Warstwa między pochodnymi menedżerami wizualnymi i interfejsem API motywów systemu Windows.

`CMFCBaseVisualManager` ładuje UxTheme.dll, jeśli jest dostępny, i zarządza dostępem do metod interfejsu API kompozycji systemu Windows.

Ta klasa jest używana tylko do użytku wewnętrznego.

## <a name="syntax"></a>Składnia

```
class CMFCBaseVisualManager: public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCBaseVisualManager::CMFCBaseVisualManager](#cmfcbasevisualmanager)|Konstruuje i inicjuje `CMFCBaseVisualManager` obiekt.|
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCBaseVisualManager::D rawCheckBox](#drawcheckbox)|Rysuje kontrolkę pola wyboru przy użyciu bieżącego motywu systemu Windows.|
|[CMFCBaseVisualManager::D rawComboBorder](#drawcomboborder)|Rysuje obramowanie pola kombi przy użyciu bieżącego motywu systemu Windows.|
|[CMFCBaseVisualManager::D rawComboDropButton](#drawcombodropbutton)|Rysuje przycisk listy rozwijanej pola kombi przy użyciu bieżącego motywu systemu Windows.|
|[CMFCBaseVisualManager::D rawPushButton](#drawpushbutton)|Rysuje przycisk push przy użyciu bieżącego motywu systemu Windows.|
|[CMFCBaseVisualManager::D rawRadioButton](#drawradiobutton)|Rysuje kontrolkę przycisku radiowego za pomocą bieżącego motywu systemu Windows.|
|[CMFCBaseVisualManager::D rawStatusBarProgress](#drawstatusbarprogress)|Rysuje pasek postępu na kontrolce pasek stanu ( [Klasa CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)) przy użyciu bieżącego motywu systemu Windows.|
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|Wypełnia tło formantu paska pomocniczego za pomocą bieżącego motywu systemu Windows.|
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Pobiera bieżący motyw systemu Windows.|

### <a name="protected-methods"></a>Metody chronione

|||
|-|-|
|Nazwa|Opis|
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Wywołania `CloseThemeData` wszystkich dojść uzyskanych w `UpdateSystemColors` .|
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Wywołania `OpenThemeData` mające na celu uzyskanie uchwytów do rysowania różnych kontrolek: okna, paski narzędzi, przyciski i tak dalej.|

## <a name="remarks"></a>Uwagi

Nie ma potrzeby bezpośredniego wystąpienia obiektów tej klasy.

Ponieważ jest klasą bazową dla wszystkich menedżerów wizualizacji, można tylko wywołać [CMFCVisualManager:: GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance), uzyskać wskaźnik do bieżącego programu Visual Manager i uzyskać dostęp do metod `CMFCBaseVisualManager` korzystania z tego wskaźnika. Jeśli jednak musisz wyświetlić formant przy użyciu bieżącego motywu systemu Windows, lepiej jest używać `CMFCVisualManagerWindows` interfejsu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxvisualmanager. h

## <a name="cmfcbasevisualmanagercleanupthemes"></a><a name="cleanupthemes"></a> CMFCBaseVisualManager::CleanUpThemes

Wywołania `CloseThemeData` wszystkich dojść uzyskanych w `UpdateSystemColors` .

```cpp
void CleanUpThemes();
```

### <a name="remarks"></a>Uwagi

Tylko do użytku wewnętrznego.

## <a name="cmfcbasevisualmanagercmfcbasevisualmanager"></a><a name="cmfcbasevisualmanager"></a> CMFCBaseVisualManager::CMFCBaseVisualManager

Konstruuje i inicjuje `CMFCBaseVisualManager` obiekt.

```
CMFCBaseVisualManager();
```

## <a name="cmfcbasevisualmanagerdrawcheckbox"></a><a name="drawcheckbox"></a> CMFCBaseVisualManager::D rawCheckBox

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

*Domeny*<br/>
podczas Wskaźnik do kontekstu urządzenia

*cinania*<br/>
podczas Prostokąt ograniczający pola wyboru.

*bHighlighted*<br/>
podczas Określa, czy pole wyboru jest wyróżnione.

*nInformacje*<br/>
[in] 0 dla opcji niezaznaczone, 1 dla opcji sprawdzone normalne,

2 — normalne.

*bEnabled*<br/>
podczas Określa, czy pole wyboru jest włączone.

*bPressed*<br/>
podczas Określa, czy pole wyboru jest naciśnięty.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli jest włączony interfejs API motywu; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wartości *nInformacje* odpowiadają następującym stylom pola wyboru.

|nInformacje|Styl pola wyboru|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

## <a name="cmfcbasevisualmanagerdrawcomboborder"></a><a name="drawcomboborder"></a> CMFCBaseVisualManager::D rawComboBorder

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

*Domeny*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*cinania*<br/>
podczas Prostokąt graniczny obramowania pola kombi.

*Poddany*<br/>
podczas Określa, czy obramowanie pola kombi jest wyłączone.

*bIsDropped*<br/>
podczas Określa, czy obramowanie pola kombi zostało usunięte.

*bIsHighlighted*<br/>
podczas Określa, czy obramowanie pola kombi jest wyróżnione.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli jest włączony interfejs API motywu; w przeciwnym razie FALSE.

## <a name="cmfcbasevisualmanagerdrawcombodropbutton"></a><a name="drawcombodropbutton"></a> CMFCBaseVisualManager::D rawComboDropButton

Rysuje przycisk listy rozwijanej pola kombi przy użyciu bieżącego motywu systemu Windows.

```
virtual BOOL DrawComboDropButton(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parametry

*Domeny*\
podczas Wskaźnik do kontekstu urządzenia.

*cinania*\
podczas Prostokąt ograniczający przycisk listy rozwijanej pola kombi.

*Poddany*\
podczas Określa, czy przycisk listy rozwijanej pola kombi jest wyłączony.

*bIsDropped*\
podczas Określa, czy przycisk listy rozwijanej pola kombi został usunięty.

*bIsHighlighted*\
podczas Określa, czy przycisk listy rozwijanej pola kombi jest wyróżniony.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli jest włączony interfejs API motywu; w przeciwnym razie FALSE.

## <a name="cmfcbasevisualmanagerdrawpushbutton"></a><a name="drawpushbutton"></a> CMFCBaseVisualManager::D rawPushButton

Rysuje przycisk push przy użyciu bieżącego motywu systemu Windows.

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*cinania*<br/>
podczas Prostokąt ograniczający przycisku push.

*pButton*<br/>
podczas Wskaźnik do obiektu [klasy CMFCButton](../../mfc/reference/cmfcbutton-class.md) do narysowania.

*uiState*<br/>
podczas Ignoruj. Stan jest pobierany z *pButton*.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli jest włączony interfejs API motywu; w przeciwnym razie FALSE.

## <a name="cmfcbasevisualmanagerdrawradiobutton"></a><a name="drawradiobutton"></a> CMFCBaseVisualManager::D rawRadioButton

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

*Domeny*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*cinania*<br/>
podczas Prostokąt ograniczający przycisk radiowy.

*bHighlighted*<br/>
podczas Określa, czy przycisk radiowy jest wyróżniony.

*bChecked*<br/>
podczas Określa, czy przycisk radiowy jest zaznaczony.

*bEnabled*<br/>
podczas Określa, czy przycisk radiowy jest włączony.

*bPressed*<br/>
podczas Określa, czy przycisk radiowy został naciśnięty.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli jest włączony interfejs API motywu; w przeciwnym razie FALSE.

## <a name="cmfcbasevisualmanagerdrawstatusbarprogress"></a><a name="drawstatusbarprogress"></a> CMFCBaseVisualManager::D rawStatusBarProgress

Rysuje pasek postępu w kontrolce pasek stanu ( [Klasa CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)) przy użyciu bieżącego motywu systemu Windows.

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

*Domeny*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*pStatusBar*<br/>
podczas Wskaźnik do paska stanu. Ta wartość jest ignorowana.

*rectProgress*<br/>
podczas Prostokąt ograniczający pasek postępu w współrzędnej *PDC* .

*nProgressTotal*<br/>
podczas Łączna wartość postępu.

*nProgressCurr*<br/>
podczas Bieżąca wartość postępu.

*clrBar*<br/>
podczas Kolor początkowy. `CMFCBaseVisualManager` ignoruje ten. Klasy pochodne mogą używać go dla gradientów kolorów.

*clrProgressBarDest*<br/>
podczas Kolor końcowy. `CMFCBaseVisualManager` ignoruje ten. Klasy pochodne mogą używać go dla gradientów kolorów.

*clrProgressText*<br/>
podczas Kolor tekstu postępu. `CMFCBaseVisualManager` ignoruje ten. Kolor tekstu jest definiowany przez `afxGlobalData.clrBtnText` .

*bProgressText*<br/>
podczas Określa, czy ma być wyświetlany tekst postępu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli jest włączony interfejs API motywu; w przeciwnym razie FALSE.

## <a name="cmfcbasevisualmanagerfillrebarpane"></a><a name="fillrebarpane"></a> CMFCBaseVisualManager::FillReBarPane

Wypełnia tło formantu paska pomocniczego za pomocą bieżącego motywu systemu Windows.

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*pBar*<br/>
podczas Wskaźnik do okienka, którego tło powinno zostać narysowane.

*rectClient*<br/>
podczas Prostokąt ograniczający obszar, który ma zostać wypełniony.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli jest włączony interfejs API motywu; w przeciwnym razie FALSE.

## <a name="cmfcbasevisualmanagergetstandardwindowstheme"></a><a name="getstandardwindowstheme"></a> CMFCBaseVisualManager::GetStandardWindowsTheme

Pobiera bieżący motyw systemu Windows.

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>Wartość zwracana

Kolor aktualnie wybranego motywu systemu Windows. Może być jedną z następujących wartości wyliczanych:

- `WinXpTheme_None` — nie włączono motywu.

- `WinXpTheme_NonStandard` -wybrano motyw niestandardowy (oznacza to, że kompozycja jest zaznaczona, ale nie z poniższej listy).

- `WinXpTheme_Blue` -niebieski motyw (Luna).

- `WinXpTheme_Olive` motyw oliwkowy.

- `WinXpTheme_Silver` — motyw Silver.

## <a name="cmfcbasevisualmanagerupdatesystemcolors"></a><a name="updatesystemcolors"></a> CMFCBaseVisualManager::UpdateSystemColors

Wywołania `OpenThemeData` mające na celu uzyskanie uchwytów do rysowania różnych kontrolek: okna, paski narzędzi, przyciski i tak dalej.

```cpp
void UpdateSystemColors();
```

### <a name="remarks"></a>Uwagi

Tylko do użytku wewnętrznego.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
