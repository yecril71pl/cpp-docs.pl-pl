---
title: Klasa CMFCColorMenuButton
ms.date: 11/04/2016
f1_keywords:
- CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableAutomaticButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableDocumentColors
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableOtherButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableTearOff
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetAutomaticColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnChangeParentWnd
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OpenColorDialog
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorName
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColumnsNumber
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CopyFrom
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CreatePopupMenu
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::IsEmptyMenuAllowed
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDraw
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDrawOnCustomizeList
helpviewer_keywords:
- CMFCColorMenuButton [MFC], CMFCColorMenuButton
- CMFCColorMenuButton [MFC], EnableAutomaticButton
- CMFCColorMenuButton [MFC], EnableDocumentColors
- CMFCColorMenuButton [MFC], EnableOtherButton
- CMFCColorMenuButton [MFC], EnableTearOff
- CMFCColorMenuButton [MFC], GetAutomaticColor
- CMFCColorMenuButton [MFC], GetColor
- CMFCColorMenuButton [MFC], GetColorByCmdID
- CMFCColorMenuButton [MFC], OnChangeParentWnd
- CMFCColorMenuButton [MFC], OpenColorDialog
- CMFCColorMenuButton [MFC], SetColor
- CMFCColorMenuButton [MFC], SetColorByCmdID
- CMFCColorMenuButton [MFC], SetColorName
- CMFCColorMenuButton [MFC], SetColumnsNumber
- CMFCColorMenuButton [MFC], CopyFrom
- CMFCColorMenuButton [MFC], CreatePopupMenu
- CMFCColorMenuButton [MFC], IsEmptyMenuAllowed
- CMFCColorMenuButton [MFC], OnDraw
- CMFCColorMenuButton [MFC], OnDrawOnCustomizeList
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
ms.openlocfilehash: 9c895573c626a890facfef689fce4b516aff5115
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752519"
---
# <a name="cmfccolormenubutton-class"></a>Klasa CMFCColorMenuButton

Klasa `CMFCColorMenuButton` obsługuje polecenie menu lub przycisk paska narzędzi, który uruchamia okno dialogowe selektora kolorów.

## <a name="syntax"></a>Składnia

```
class CMFCColorMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|Konstruuje `CMFCColorMenuButton` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|Włącza i wyłącza przycisk "automatyczny", który znajduje się nad zwykłymi przyciskami kolorów. (Standardowy automatyczny przycisk systemu jest oznaczony jako **Automatyczny).**|
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|Umożliwia wyświetlanie kolorów specyficznych dla dokumentu zamiast kolorów systemowych.|
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|Włącza i wyłącza przycisk "inne", który znajduje się poniżej zwykłych przycisków kolorów. (Standardowy systemowy przycisk "inne" jest oznaczony jako **Więcej kolorów.)**|
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|Umożliwia oderwanie okienka kolorów.|
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|Pobiera bieżący kolor automatyczny.|
|[CMFCColorMenuButton::GetColor](#getcolor)|Pobiera kolor bieżącego przycisku.|
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|Pobiera kolor odpowiadający określonemu identyfikatorowi polecenia.|
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Wywoływane przez strukturę, gdy zmienia się okno nadrzędne.|
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|Otwiera okno dialogowe wyboru kolorów.|
|[CMFCColorMenuButton::SetColor](#setcolor)|Ustawia kolor bieżącego przycisku koloru.|
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|Ustawia kolor określonego przycisku menu kolorów.|
|[CMFCColorMenuButton::SetColorName](#setcolorname)|Ustawia nową nazwę dla określonego koloru.|
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|Ustawia liczbę kolumn wyświetlanych przez `CMFCColorBar` obiekt.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|Kopiuje inny przycisk paska narzędzi do bieżącego przycisku.|
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|Tworzy okno dialogowe selektora kolorów.|
|[CMFCColorMenuButton::IsEmptyMenuallowed](#isemptymenuallowed)|Wskazuje, czy puste menu są obsługiwane.|
|[CMFCColorMenuButton::OnDraw](#ondraw)|Wywoływana przez strukturę, aby wyświetlić obraz na przycisku.|
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Wywoływane przez strukturę, `CMFCColorMenuButton` zanim obiekt jest wyświetlany na liście okna dialogowego dostosowywania paska narzędzi.|

## <a name="remarks"></a>Uwagi

Aby zastąpić oryginalne polecenie menu lub `CMFCColorMenuButton` przycisk paska `CMFCColorMenuButton` narzędzi obiektem, utwórz obiekt, ustaw odpowiednie `ReplaceButton` style [klasy CMFCColorBar,](../../mfc/reference/cmfccolorbar-class.md) a następnie wywołaj metodę klasy [CMFCToolBar Class.](../../mfc/reference/cmfctoolbar-class.md) Jeśli dostosujesz pasek narzędzi, wywołaj [METODĘ CMFCToolBarsCustomizeDialog::ReplaceButton.](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton)

Okno dialogowe selektora kolorów jest tworzone podczas przetwarzania programu obsługi zdarzeń [CMFCColorMenuButton::CreatePopupMenu.](#createpopupmenu) Program obsługi zdarzeń powiadamia ramkę nadrzędną za pomocą komunikatu WM_COMMAND. Obiekt `CMFCColorMenuButton` wysyła identyfikator formantu przypisany do oryginalnego polecenia menu lub przycisku paska narzędzi.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak utworzyć i skonfigurować przycisk `CMFCColorMenuButton` menu kolorów przy użyciu różnych metod w klasie. W przykładzie `CPalette` obiekt jest najpierw tworzony, a następnie `CMFCColorMenuButton` używany do konstruowania obiektu klasy. Obiekt `CMFCColorMenuButton` jest następnie konfigurowany przez włączenie jego automatycznych i innych przycisków oraz ustawienie jego koloru i liczby kolumn. Ten kod jest częścią [przykładu Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cmfctoolbarbutton](../../mfc/reference/cmfctoolbarbutton-class.md)

[Cmfctoolbarmenubutton](../../mfc/reference/cmfctoolbarmenubutton-class.md)

[Cmfccolormenubutton](../../mfc/reference/cmfccolormenubutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcolormenubutton.h

## <a name="cmfccolormenubuttoncmfccolormenubutton"></a><a name="cmfccolormenubutton"></a>CMFCColorMenuButton::CMFCColorMenuButton

Konstruuje `CMFCColorMenuButton` obiekt.

```
CMFCColorMenuButton();

CMFCColorMenuButton(
    UINT uiCmdID,
    LPCTSTR lpszText,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>Parametry

*identyfikator uiCmdID*<br/>
[w] Identyfikator polecenia przycisku.

*lpszText (tekst)*<br/>
[w] Tekst przycisku.

*pPalette (ppalette)*<br/>
[w] Wskaźnik do palety kolorów przycisku.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor jest konstruktorem domyślnym. Bieżący kolor i kolor automatyczny obiektu są inicjowane na czarny (RGB(0, 0, 0)).

Drugi konstruktor inicjuje przycisk do koloru odpowiadającego określonemu identyfikatorowi polecenia.

## <a name="cmfccolormenubuttoncopyfrom"></a><a name="copyfrom"></a>CMFCColorMenuButton::CopyFrom

Kopiuje jeden [obiekt cmfctoolbarmenubutton klasy](../../mfc/reference/cmfctoolbarmenubutton-class.md)pochodnej do innego.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[w] Przycisk Źródła do skopiowania.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę, aby skopiować `CMFCColorMenuButton` obiekty, które są pochodną obiektu.

## <a name="cmfccolormenubuttoncreatepopupmenu"></a><a name="createpopupmenu"></a>CMFCColorMenuButton::CreatePopupMenu

Tworzy okno dialogowe selektora kolorów.

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt reprezentujący okno dialogowe selektora kolorów.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy użytkownik naciśnie przycisk menu kolorów.

## <a name="cmfccolormenubuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorMenuButton::EnableAutomaticButton

Włącza i wyłącza przycisk "automatyczny", który znajduje się nad zwykłymi przyciskami kolorów. (Standardowy automatyczny przycisk systemu jest oznaczony jako **Automatyczny).**

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
[w] Określa tekst przycisku wyświetlany, gdy przycisk staje się automatyczny.

*kolorAutomatyczny*<br/>
[w] Określa nowy kolor automatyczny.

*bWłaszą*<br/>
[w] Określa, czy przycisk jest automatyczny, czy nie.

### <a name="remarks"></a>Uwagi

Przycisk automatyczny powoduje zastosowanie bieżącego koloru domyślnego.

## <a name="cmfccolormenubuttonenabledocumentcolors"></a><a name="enabledocumentcolors"></a>CMFCColorMenuButton::EnableDocumentColors

Umożliwia wyświetlanie kolorów specyficznych dla dokumentu zamiast kolorów systemowych.

```cpp
void EnableDocumentColors(
    LPCTSTR lpszLabel,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
[w] Określa tekst przycisku.

*bWłaszą*<br/>
[w] TRUE, aby wyświetlić kolory specyficzne dla dokumentu lub FAŁSZ, aby wyświetlić kolory systemowe.

### <a name="remarks"></a>Uwagi

Ta metoda służy do wyświetlania bieżących kolorów dokumentu lub kolorów palety systemowej, gdy użytkownik kliknie przycisk menu kolorów.

## <a name="cmfccolormenubuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorMenuButton::EnableOtherButton

Włącza i wyłącza przycisk "inne", który znajduje się poniżej zwykłych przycisków kolorów. (Standardowy systemowy przycisk "inne" jest oznaczony jako **Więcej kolorów.)**

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
[w] Określa tekst przycisku.

*bAltColorDlg*<br/>
[w] Określ wartość `CMFCColorDialog` TRUE, aby wyświetlić okno dialogowe, lub FAŁSZ, aby wyświetlić okno dialogowe standardowy kolor systemu.

*bWłaszą*<br/>
[w] Określ wartość PRAWDA, aby wyświetlić przycisk "inne"; w przeciwnym razie FALSE. Wartość domyślna to PRAWDA.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolormenubuttonenabletearoff"></a><a name="enabletearoff"></a>CMFCColorMenuButton::EnableTearOff

Umożliwia oderwanie okienka kolorów.

```cpp
void EnableTearOff(
    UINT uiID,
    int nVertDockColumns=-1,
    int nHorzDockRows=-1);
```

### <a name="parameters"></a>Parametry

*Uiid*<br/>
[w] Określa identyfikator okienka odrywnika.

*nVertDockKolumny*<br/>
[w] Określa liczbę kolumn w okienku kolorów zadokowanych pionowo w stanie odrywu.

*nHorzDockRows*<br/>
[w] Określa liczbę wierszy dla poziomo zadokowanego okienka kolorów w stanie odrywu.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby włączyć funkcję "odrywać" dla okienka kolorów, które pojawia się po naciśnięciu przycisku. `CMFCColorMenuButton`

## <a name="cmfccolormenubuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCColorMenuButton::GetAutomaticColor

Pobiera bieżący kolor automatyczny.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość koloru RGB reprezentująca bieżący kolor automatyczny.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby uzyskać kolor automatyczny, który jest ustawiony przez [CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton).

## <a name="cmfccolormenubuttongetcolor"></a><a name="getcolor"></a>CMFCColorMenuButton::GetColor

Pobiera kolor bieżącego przycisku.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolor przycisku.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolormenubuttongetcolorbycmdid"></a><a name="getcolorbycmdid"></a>CMFCColorMenuButton::GetColorByCmdID

Pobiera kolor odpowiadający określonemu identyfikatorowi polecenia.

```
static COLORREF GetColorByCmdID(UINT uiCmdID);
```

### <a name="parameters"></a>Parametry

*identyfikator uiCmdID*<br/>
[w] Identyfikator polecenia.

### <a name="return-value"></a>Wartość zwracana

Kolor odpowiadający określonemu identyfikatorowi polecenia.

### <a name="remarks"></a>Uwagi

Tej metody należy używać, gdy w aplikacji jest kilka przycisków kolorów. Gdy użytkownik kliknie przycisk koloru, przycisk wysyła jego identyfikator polecenia w WM_COMMAND wiadomości do jego nadrzędnego. Metoda `GetColorByCmdID` używa identyfikatora polecenia do pobrania odpowiedniego koloru.

## <a name="cmfccolormenubuttonisemptymenuallowed"></a><a name="isemptymenuallowed"></a>CMFCColorMenuButton::IsEmptyMenuallowed

Wskazuje, czy puste menu są obsługiwane.

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli puste menu są dozwolone; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Puste menu są domyślnie obsługiwane. Zastąpi tę metodę, aby zmienić to zachowanie w klasie pochodnej.

## <a name="cmfccolormenubuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCColorMenuButton::OnChangeParentWnd

Wywoływane przez strukturę, gdy zmienia się okno nadrzędne.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Wskaźnik do nowego okna nadrzędnego.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolormenubuttonondraw"></a><a name="ondraw"></a>CMFCColorMenuButton::OnDraw

Wywoływana przez strukturę, aby wyświetlić obraz na przycisku.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz=TRUE,
    BOOL bCustomizeMode=FALSE,
    BOOL bHighlight=FALSE,
    BOOL bDrawBorder=TRUE,
    BOOL bGrayDisabledButtons=TRUE);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[w] Prostokąt, który ogranicza obszar do ponownego narysowania.

*pImages (Zdjęcia)*<br/>
[w] Wskazuje listę obrazów paska narzędzi.

*Bhorz*<br/>
[w] PRAWDA, aby określić, że pasek narzędzi jest w stanie zadokowanym poziomo; w przeciwnym razie FALSE. Wartość domyślna to PRAWDA.

*b Tryb dokuczowania*<br/>
[w] PRAWDA, aby określić, że aplikacja jest w trybie dostosowywania; w przeciwnym razie FALSE. Wartość domyślna to FALSE.

*bWyświetlenie*<br/>
[w] PRAWDA, aby określić, że przycisk jest wyróżniony; w przeciwnym razie FALSE. Wartość domyślna to FALSE.

*bDrawBorder*<br/>
[w] PRAWDA, aby określić, że jest wyświetlana obramowanie przycisku; w przeciwnym razie FALSE. Wartość domyślna to PRAWDA.

*bGrayDisabledButtons*<br/>
[w] PRAWDA, aby określić, że wyłączone przyciski są wyszarzone (wyszarzone) w przeciwnym razie FALSE. Wartość domyślna to PRAWDA.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolormenubuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCColorMenuButton::OnDrawOnCustomizeList

Wywoływane przez strukturę, `CMFCColorMenuButton` zanim obiekt jest wyświetlany na liście okna dialogowego dostosowywania paska narzędzi.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[w] Prostokąt, który ogranicza przycisk do narysowania.

*bWybrany*<br/>
[w] WARTOŚĆ TRUE określa, że przycisk jest w wybranym stanie; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Szerokość przycisku.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana `CMFCColorMenuButton` przez platformę, gdy obiekt jest wyświetlany w polu listy podczas procesu dostosowywania paska narzędzi.

## <a name="cmfccolormenubuttonopencolordialog"></a><a name="opencolordialog"></a>CMFCColorMenuButton::OpenColorDialog

Otwiera okno dialogowe wyboru kolorów.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parametry

*colorDefault (Domyślny kolor)*<br/>
[w] Kolor domyślny wybrany w oknie dialogowym kolor.

*colorRes*<br/>
[na zewnątrz] Zwraca kolor wybrany przez użytkownika z okna dialogowego kolor.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli użytkownik wybierze nowy kolor; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Po kliknięciu przycisku menu wywołaj tę metodę, aby otworzyć kolorowe okno dialogowe. Jeśli zwracana wartość jest niezerowa, kolor wybrany przez użytkownika jest przechowywany w parametrze *colorRes.* Użyj [CMFCColorMenuButton::EnableOtherButton](#enableotherbutton) metody, aby przełączyć się między standardowym kolorowym oknie dialogowym i [CMFCColorDialog klasy](../../mfc/reference/cmfccolordialog-class.md) okna dialogowego.

## <a name="cmfccolormenubuttonsetcolor"></a><a name="setcolor"></a>CMFCColorMenuButton::SetColor

Ustawia kolor bieżącego przycisku koloru.

```
virtual void SetColor(
    COLORREF clr,
    BOOL bNotify=TRUE);
```

### <a name="parameters"></a>Parametry

*Clr*<br/>
[w] Wartość koloru RGB.

*bNotuj*<br/>
[w] PRAWDA, aby zastosować kolor parametru *clr* do dowolnego powiązanego przycisku menu lub przycisku paska narzędzi; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby zmienić kolor bieżącego przycisku koloru. Jeśli parametr *bNotify* jest niezerowy, kolor odpowiedniego przycisku w dowolnym skojarzonym menu podręcznym lub pasku narzędzi zostanie zmieniony na kolor określony przez parametr *clr.*

## <a name="cmfccolormenubuttonsetcolorbycmdid"></a><a name="setcolorbycmdid"></a>CMFCColorMenuButton::SetColorByCmdID

Ustawia kolor określonego przycisku menu kolorów.

```
static void SetColorByCmdID(
    UINT uiCmdID,
    COLORREF color);
```

### <a name="parameters"></a>Parametry

*identyfikator uiCmdID*<br/>
[w] Identyfikator zasobu przycisku menu kolorów.

*color*<br/>
[w] Wartość koloru RGB.

## <a name="cmfccolormenubuttonsetcolorname"></a><a name="setcolorname"></a>CMFCColorMenuButton::SetColorName

Ustawia nową nazwę dla określonego koloru.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[w] Wartość RGB koloru, którego nazwa się zmienia.

*nazwa strName*<br/>
[w] Nowa nazwa koloru.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolormenubuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCColorMenuButton::SetColumnsNumber

Ustawia liczbę kolumn wyświetlanych w formancie wyboru kolorów ( [CMFCColorBar).](../../mfc/reference/cmfccolorbar-class.md)

```cpp
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parametry

*nKolumny*<br/>
[w] Liczba kolumn do wyświetlenia.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Klasa CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)<br/>
[Klasa CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)
