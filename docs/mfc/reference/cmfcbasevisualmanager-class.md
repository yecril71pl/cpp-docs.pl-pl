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
ms.openlocfilehash: ac64a3feac5d124c2bfa67fc857dad5045c2dd28
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754889"
---
# <a name="cmfcbasevisualmanager-class"></a>Klasa CMFCBaseVisualManager

Warstwa między pochodnymi menedżerami wizualnymi a interfejsem API motywu systemu Windows.

`CMFCBaseVisualManager`ładuje UxTheme.dll, jeśli jest dostępny, i zarządza dostępem do metod interfejsu API motywu systemu Windows.

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
|[CMFCBaseVisualManager::CMFCBaseVisualManager](#cmfcbasevisualmanager)|Konstruuje i inicjuje `CMFCBaseVisualManager` obiekt.|
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|Rysuje formant pola wyboru przy użyciu bieżącego motywu systemu Windows.|
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|Rysuje obramowanie pola kombi przy użyciu bieżącej kompozycji systemu Windows.|
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|Rysuje przycisk rozwijany pola kombi przy użyciu bieżącej kompozycji systemu Windows.|
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|Rysuje przycisk przy użyciu bieżącej kompozycji systemu Windows.|
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|Rysuje kontrolkę przycisku opcji przy użyciu bieżącej kompozycji systemu Windows.|
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|Rysuje pasek postępu na formancie paska stanu [(CMFCStatusBar Class)](../../mfc/reference/cmfcstatusbar-class.md)przy użyciu bieżącej kompozycji systemu Windows.|
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|Wypełnia tło formantu prętów zbrojeniowych przy użyciu bieżącej kompozycji systemu Windows.|
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Pobiera bieżącą kompozycję systemu Windows.|

### <a name="protected-methods"></a>Metody chronione

|||
|-|-|
|Nazwa|Opis|
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Wywołania `CloseThemeData` wszystkich uchwytów `UpdateSystemColors`uzyskanych w pliku .|
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Wywołania, `OpenThemeData` aby uzyskać uchwyty do rysowania różnych formantów: okna, paski narzędzi, przyciski i tak dalej.|

## <a name="remarks"></a>Uwagi

Nie trzeba bezpośrednio utworzyć wystąpienia obiektów tej klasy.

Ponieważ jest to klasa podstawowa dla wszystkich menedżerów wizualnych, można po prostu wywołać [CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance), uzyskać wskaźnik do bieżącego Menedżera wizualnego i uzyskać dostęp do metod `CMFCBaseVisualManager` przy użyciu tego wskaźnika. Jeśli jednak musisz wyświetlić formant przy użyciu bieżącej kompozycji `CMFCVisualManagerWindows` systemu Windows, lepiej jest użyć interfejsu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxvisualmanager.h

## <a name="cmfcbasevisualmanagercleanupthemes"></a><a name="cleanupthemes"></a>CMFCBaseVisualManager::CleanUpThemes

Wywołania `CloseThemeData` wszystkich uchwytów `UpdateSystemColors`uzyskanych w pliku .

```cpp
void CleanUpThemes();
```

### <a name="remarks"></a>Uwagi

Tylko do użytku wewnętrznego.

## <a name="cmfcbasevisualmanagercmfcbasevisualmanager"></a><a name="cmfcbasevisualmanager"></a>CMFCBaseVisualManager::CMFCBaseVisualManager

Konstruuje i inicjuje `CMFCBaseVisualManager` obiekt.

```
CMFCBaseVisualManager();
```

## <a name="cmfcbasevisualmanagerdrawcheckbox"></a><a name="drawcheckbox"></a>CMFCBaseVisualManager::DrawCheckBox

Rysuje formant pola wyboru przy użyciu bieżącego motywu systemu Windows.

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

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia

*Rect*<br/>
[w] Prostokąt ograniczający pola wyboru.

*bWyświetlony*<br/>
[w] Określa, czy pole wyboru jest wyróżnione.

*nPaństwo*<br/>
[in] 0 dla niezaznaczonych, 1 dla

2 dla normalnie mieszanej.

*bWłach*<br/>
[w] Określa, czy pole wyboru jest włączone.

*bPressed (Wciskany)*<br/>
[w] Określa, czy pole wyboru jest naciśnięte.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli interfejs API motywu jest włączony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wartości *nState* odpowiadają następującym stylom pola wyboru.

|nPaństwo|Styl pola wyboru|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

## <a name="cmfcbasevisualmanagerdrawcomboborder"></a><a name="drawcomboborder"></a>CMFCBaseVisualManager::DrawComboBorder

Rysuje obramowanie pola kombi przy użyciu bieżącej kompozycji systemu Windows.

```
virtual BOOL DrawComboBorder(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[w] Prostokąt ograniczający obramowania pola kombi.

*bWydaj*<br/>
[w] Określa, czy obramowanie pola kombi jest wyłączone.

*bIsDropped (Niezmierzony)*<br/>
[w] Określa, czy obramowanie pola kombi jest odrzucane.

*bIsSwyżkowany*<br/>
[w] Określa, czy obramowanie pola kombi jest wyróżnione.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli interfejs API motywu jest włączony; w przeciwnym razie FALSE.

## <a name="cmfcbasevisualmanagerdrawcombodropbutton"></a><a name="drawcombodropbutton"></a>CMFCBaseVisualManager::DrawComboDropButton

Rysuje przycisk rozwijany pola kombi przy użyciu bieżącej kompozycji systemu Windows.

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
|*Pdc*|[w] Wskaźnik do kontekstu urządzenia.|
|*Rect*|[w] Prostokąt ograniczający przycisk rozwijany pola kombi.|
|*bWydaj*|[w] Określa, czy przycisk rozwijany pola kombi jest wyłączony.|
|*bIsDropped (Niezmierzony)*|[w] Określa, czy przycisk rozwijany pola kombi jest porzucony.|
|*bIsSwyżkowany*|[w] Określa, czy wyróżniony jest przycisk rozwijany pola kombi.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli interfejs API motywu jest włączony; w przeciwnym razie FALSE.

## <a name="cmfcbasevisualmanagerdrawpushbutton"></a><a name="drawpushbutton"></a>CMFCBaseVisualManager::DrawPushButton

Rysuje przycisk przy użyciu bieżącej kompozycji systemu Windows.

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[w] Prostokąt ograniczający przycisku.

*pButton (przycisk)*<br/>
[w] Wskaźnik do [CMFCButton Class](../../mfc/reference/cmfcbutton-class.md) obiektu do rysowania.

*uiStan*<br/>
[w] Ignorowane. Stan jest pobierany z *pButton*.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli interfejs API motywu jest włączony; w przeciwnym razie FALSE.

## <a name="cmfcbasevisualmanagerdrawradiobutton"></a><a name="drawradiobutton"></a>CMFCBaseVisualManager::DrawRadioButton

Rysuje kontrolkę przycisku opcji przy użyciu bieżącej kompozycji systemu Windows.

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

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[w] Prostokąt ograniczający przycisku radiowego.

*bWyświetlony*<br/>
[w] Określa, czy podświetlony jest przycisk radiowy.

*bSprawiona*<br/>
[w] Określa, czy przycisk radiowy jest zaznaczony.

*bWłach*<br/>
[w] Określa, czy przycisk radiowy jest włączony.

*bPressed (Wciskany)*<br/>
[w] Określa, czy przycisk radiowy jest naciśnięty.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli interfejs API motywu jest włączony; w przeciwnym razie FALSE.

## <a name="cmfcbasevisualmanagerdrawstatusbarprogress"></a><a name="drawstatusbarprogress"></a>CMFCBaseVisualManager::DrawStatusBarProgress

Rysuje pasek postępu na pasku stanu [(CMFCStatusBar Class)](../../mfc/reference/cmfcstatusbar-class.md)przy użyciu bieżącego motywu systemu Windows.

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

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*pStatusBar (pStatusBar)*<br/>
[w] Wskaźnik do paska stanu. Ta wartość jest ignorowana.

*spectProgress (proces spectProgress)*<br/>
[w] Prostokąt ograniczający paska postępu we współrzędnych *pDC.*

*nProgressTotal*<br/>
[w] Całkowita wartość postępu.

*nProgressCurr*<br/>
[w] Bieżąca wartość postępu.

*clrBar (clrBar)*<br/>
[w] Kolor początkowy. `CMFCBaseVisualManager`ignoruje to. Klasy pochodne mogą go używać do gradientów kolorów.

*clrProgressBarDest*<br/>
[w] Kolor końcowy. `CMFCBaseVisualManager`ignoruje to. Klasy pochodne mogą go używać do gradientów kolorów.

*clrProgressTeker*<br/>
[w] Kolor tekstu postępu. `CMFCBaseVisualManager`ignoruje to. Kolor tekstu jest `afxGlobalData.clrBtnText`definiowany przez program .

*bProgresstext (Tekst)*<br/>
[w] Określa, czy tekst postępu ma być wyświetlany.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli interfejs API motywu jest włączony; w przeciwnym razie FALSE.

## <a name="cmfcbasevisualmanagerfillrebarpane"></a><a name="fillrebarpane"></a>CMFCBaseVisualManager::FillReBarPane

Wypełnia tło formantu prętów zbrojeniowych przy użyciu bieżącej kompozycji systemu Windows.

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*pBar*<br/>
[w] Wskaźnik do okienka, którego tło powinno zostać narysowane.

*rectClient*<br/>
[w] Prostokąt ograniczający obszaru, który ma zostać wypełniony.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli interfejs API motywu jest włączony; w przeciwnym razie FALSE.

## <a name="cmfcbasevisualmanagergetstandardwindowstheme"></a><a name="getstandardwindowstheme"></a>CMFCBaseVisualManager::GetStandardWindowsTheme

Pobiera bieżącą kompozycję systemu Windows.

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>Wartość zwracana

Aktualnie wybrany kolor motywu systemu Windows. Może być jedną z następujących wartości wyliczonych:

- `WinXpTheme_None`- nie ma włączonego tematu.

- `WinXpTheme_NonStandard`- wybrano niestandardowy motyw (co oznacza, że wybrano motyw, ale żaden z poniższej listy).

- `WinXpTheme_Blue`- niebieski motyw (Luna).

- `WinXpTheme_Olive`- temat oliwy.

- `WinXpTheme_Silver`- srebrny motyw.

## <a name="cmfcbasevisualmanagerupdatesystemcolors"></a><a name="updatesystemcolors"></a>CMFCBaseVisualManager::UpdateSystemColors

Wywołania, `OpenThemeData` aby uzyskać uchwyty do rysowania różnych formantów: okna, paski narzędzi, przyciski i tak dalej.

```cpp
void UpdateSystemColors();
```

### <a name="remarks"></a>Uwagi

Tylko do użytku wewnętrznego.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
