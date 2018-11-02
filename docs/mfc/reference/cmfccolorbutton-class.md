---
title: Klasa CMFCColorButton
ms.date: 11/04/2016
f1_keywords:
- CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::EnableAutomaticButton
- AFXCOLORBUTTON/CMFCColorButton::EnableOtherButton
- AFXCOLORBUTTON/CMFCColorButton::GetAutomaticColor
- AFXCOLORBUTTON/CMFCColorButton::GetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColorName
- AFXCOLORBUTTON/CMFCColorButton::SetColumnsNumber
- AFXCOLORBUTTON/CMFCColorButton::SetDocumentColors
- AFXCOLORBUTTON/CMFCColorButton::SetPalette
- AFXCOLORBUTTON/CMFCColorButton::SizeToContent
- AFXCOLORBUTTON/CMFCColorButton::IsDrawXPTheme
- AFXCOLORBUTTON/CMFCColorButton::OnDraw
- AFXCOLORBUTTON/CMFCColorButton::OnDrawBorder
- AFXCOLORBUTTON/CMFCColorButton::OnDrawFocusRect
- AFXCOLORBUTTON/CMFCColorButton::OnShowColorPopup
- AFXCOLORBUTTON/CMFCColorButton::RebuildPalette
- AFXCOLORBUTTON/CMFCColorButton::UpdateColor
- AFXCOLORBUTTON/CMFCColorButton::m_bEnabledInCustomizeMode
helpviewer_keywords:
- CMFCColorButton [MFC], CMFCColorButton
- CMFCColorButton [MFC], EnableAutomaticButton
- CMFCColorButton [MFC], EnableOtherButton
- CMFCColorButton [MFC], GetAutomaticColor
- CMFCColorButton [MFC], GetColor
- CMFCColorButton [MFC], SetColor
- CMFCColorButton [MFC], SetColorName
- CMFCColorButton [MFC], SetColumnsNumber
- CMFCColorButton [MFC], SetDocumentColors
- CMFCColorButton [MFC], SetPalette
- CMFCColorButton [MFC], SizeToContent
- CMFCColorButton [MFC], IsDrawXPTheme
- CMFCColorButton [MFC], OnDraw
- CMFCColorButton [MFC], OnDrawBorder
- CMFCColorButton [MFC], OnDrawFocusRect
- CMFCColorButton [MFC], OnShowColorPopup
- CMFCColorButton [MFC], RebuildPalette
- CMFCColorButton [MFC], UpdateColor
- CMFCColorButton [MFC], m_bEnabledInCustomizeMode
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
ms.openlocfilehash: 97012e1d8cdc36f080245243c5f099b340225fc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533864"
---
# <a name="cmfccolorbutton-class"></a>Klasa CMFCColorButton

`CMFCColorButton` i [klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) klasy są używane razem w celu wdrożenia kontroli próbnika kolorów.

## <a name="syntax"></a>Składnia

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Tworzy nowy `CMFCColorButton` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Włącza i wyłącza przycisk "Automatyczny", który znajduje się powyżej regularne kolor przycisków. (Przycisk Automatyczny standardowych systemowych jest oznaczona etykietą **automatyczne**.)|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Włącza i wyłącza "other" przycisk, który znajduje się poniżej regularne kolor przycisków. (Standardowy system "other" przycisk ma etykietę **więcej kolorów**.)|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Pobiera bieżący kolor automatyczne.|
|[CMFCColorButton::GetColor](#getcolor)|Pobiera kolor przycisku.|
|[CMFCColorButton::SetColor](#setcolor)|Określa kolor przycisku.|
|[CMFCColorButton::SetColorName](#setcolorname)|Ustawia nazwę koloru.|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Ustawia liczbę kolumn na okno dialogowe próbnika kolorów.|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Określa listę kolorów specyficzne dla dokumentu, które są wyświetlane na okno dialogowe próbnika kolorów.|
|[CMFCColorButton::SetPalette](#setpalette)|Określa paletę kolorów standardowego.|
|[CMFCColorButton::SizeToContent](#sizetocontent)|Zmienia rozmiar kontrolki przycisku w zależności od rozmiaru tekstu i obrazów.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Wskazuje, czy bieżący przycisk koloru jest wyświetlany w stylu wizualnego systemu Windows XP.|
|[CMFCColorButton::OnDraw](#ondraw)|Metoda wywoływana przez platformę, by wyświetlić obrazu przycisku.|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Metoda wywoływana przez platformę, by wyświetlić obramowania przycisku.|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Metoda wywoływana przez platformę, by wyświetlić prostokąta fokusu w przypadku, gdy przycisk ma fokus.|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Wywoływane przez platformę, gdy ma być wyświetlane okno dialogowe próbnika kolorów.|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Inicjuje `m_pPalette` chroniony element członkowski danych palety określona lub domyślna paleta systemu.|
|[CMFCColorButton::UpdateColor](#updatecolor)|Wywoływane przez platformę, gdy użytkownik zaznaczy kolor z palety okno dialogowe próbnika kolorów.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|`m_bAltColorDlg`|Wartość logiczna. W przypadku opcji TRUE ramach Wyświetla [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) okno dialogowe kolorów, kiedy *innych* kliknięto przycisk lub w przypadku wartości FAŁSZ system kolor okno dialogowe. Wartość domyślna to TRUE. Aby uzyskać więcej informacji, zobacz [CMFCColorButton::EnableOtherButton](#enableotherbutton).|
|`m_bAutoSetFocus`|Wartość logiczna. W przypadku opcji TRUE ramach Ustawia fokus na menu Kolor menu wyświetlanym lub w przypadku wartości FAŁSZ nie zmienia się fokus. Wartość domyślna to TRUE.|
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Wskazuje, czy dla przycisku koloru jest włączony tryb dostosowywania.|
|`m_Color`|A [COLORREF](/windows/desktop/gdi/colorref) wartości. Zawiera obecnie wybranego koloru.|
|`m_ColorAutomatic`|A [COLORREF](/windows/desktop/gdi/colorref) wartości. Zawiera aktualnie wybranego domyślny kolor.|
|`m_Colors`|A [CArray](../../mfc/reference/carray-class.md) z [COLORREF](/windows/desktop/gdi/colorref) wartości. Zawiera obecnie dostępnych kolorów.|
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md) z [COLORREF](/windows/desktop/gdi/colorref) wartości. Zawiera kolorów bieżącego dokumentu.|
|`m_nColumns`|Liczba całkowita. Zawiera liczbę kolumn do wyświetlenia w siatce kolorów w menu wyboru kolorów.|
|`m_pPalette`|Wskaźnik do [CPalette](../../mfc/reference/cpalette-class.md). Zawiera kolorów, które są dostępne w bieżącym menu wyboru kolorów.|
|`m_pPopup`|Wskaźnik do [klasa CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md) obiektu. Menu wyboru koloru jest wyświetlany po kliknięciu przycisku koloru.|
|`m_strAutoColorText`|Ciąg. Etykieta przycisku "Automatyczny" w menu wyboru kolorów.|
|`m_strDocColorsText`|Ciąg. Etykieta przycisku w menu wyboru koloru, który wyświetla kolory dokumentu.|
|`m_strOtherText`|Ciąg. Etykieta przycisku "other" w menu wyboru kolorów.|

## <a name="remarks"></a>Uwagi

Domyślnie `CMFCColorButton` klasy zachowuje się jak przycisk polecenia, który otwiera okno dialogowe próbnika kolorów. Okno dialogowe próbnika kolorów zawiera tablicę kolorów przycisków i "other" przycisk, który wyświetla selektor koloru niestandardowego. (Standardowy system "other" przycisk ma etykietę **więcej kolorów**.) Gdy użytkownik wybierze nowy kolor `CMFCColorButton` obiektu odzwierciedla zmianę i wyświetla wybrany kolor.

Tworzenie kontrolki przycisku koloru, bezpośrednio w kodzie lub za pomocą **ClassWizard** narzędzia i szablonu okna dialogowego. Jeśli utworzysz formant przycisku koloru bezpośrednio, należy dodać `CMFCColorButton` zmiennej do aplikacji, a następnie wywołania konstruktora i `Create` metody `CMFCColorButton` obiektu. Jeśli używasz **ClassWizard**, Dodaj `CButton` zmiennej do swojej aplikacji, a następnie zmień typ zmiennej z `CButton` do `CMFCColorButton`.

Okno dialogowe próbnika kolorów ( [klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)) jest wyświetlany [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) struktura wywołuje metodę `OnLButtonDown` programu obsługi zdarzeń. [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) metodę można przesłonić, aby obsługiwać wybór koloru niestandardowego.

`CMFCColorButton` Obiektu powiadamia jego elementu nadrzędnego, który zmienia kolor wysyłając WM_COMMAND | BN_CLICKED — powiadomienie. Element nadrzędny używa [CMFCColorButton::GetColor](#getcolor) metodę, która pobierze bieżący kolor.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak skonfigurować przycisk koloru przy użyciu różnych metod w `CMFCColorButton` klasy. Metody Ustaw kolor przycisku koloru i jego numer kolumny, a następnie włączyć automatyczne i inne przyciski. W tym przykładzie jest częścią [próbka Demo pasek stanu](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcolorbutton.h

##  <a name="cmfccolorbutton"></a>  CMFCColorButton::CMFCColorButton

Tworzy nowy `CMFCColorButton` obiektu.

```
CMFCColorButton();
```

##  <a name="enableautomaticbutton"></a>  CMFCColorButton::EnableAutomaticButton

Włącz lub Wyłącz przycisk "Automatyczny" kontrolki selektora kolorów i ustawić kolor automatyczne (opcja domyślna).

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Określa tekst przycisku automatycznego.

*colorAutomatic*<br/>
[in] Wartości RGB, który określa kolor domyślny przycisk Automatyczny.

*bWłączenie*<br/>
[in] Określa, czy przycisk Automatyczny jest włączone.

### <a name="remarks"></a>Uwagi

##  <a name="enableotherbutton"></a>  CMFCColorButton::EnableOtherButton

Włącza lub wyłącza "other" przycisk, który pojawia się poniżej regularne kolor przycisków.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Określa tekst na przycisku.

*bAltColorDlg*<br/>
[in] Określa, czy [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) okno dialogowe lub okno dialogowe kolorów systemu jest otwierana, gdy użytkownik kliknie przycisk.

*bWłączenie*<br/>
[in] Określa, czy "other" przycisk jest włączony.

### <a name="remarks"></a>Uwagi

Kliknij przycisk "other" Aby wyświetlić okno dialogowe kolorów. Jeśli *bAltColorDlg* parametr ma wartość PRAWDA, [klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) jest wyświetlana; w przeciwnym razie zostanie wyświetlone okno dialogowe kolorów systemu.

##  <a name="getautomaticcolor"></a>  CMFCColorButton::GetAutomaticColor

Pobiera bieżący kolor automatyczne (opcja domyślna).

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość RGB reprezentujący bieżące kolorowi automatycznemu.

### <a name="remarks"></a>Uwagi

Bieżący kolor automatycznego została ustawiona przez [CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton) metody.

##  <a name="getcolor"></a>  CMFCColorButton::GetColor

Pobiera obecnie wybrany kolor.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość RGB.

### <a name="remarks"></a>Uwagi

##  <a name="isdrawxptheme"></a>  CMFCColorButton::IsDrawXPTheme

Wskazuje, czy bieżący przycisk koloru jest wyświetlany w stylu wizualnego systemu Windows XP.

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli style wizualne są obsługiwane i przycisku bieżący kolor jest wyświetlany w stylu wizualnego systemu Windows XP; w przeciwnym razie wartość FALSE.

##  <a name="m_benabledincustomizemode"></a>  CMFCColorButton::m_bEnabledInCustomizeMode

Ustawia tryb dostosowywania przycisk koloru.

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>Uwagi

Jeśli trzeba dodać przycisk koloru do okna dialogowego Dostosowywanie strony (lub Zezwól użytkownikowi Dokonaj innego wyboru koloru podczas dostosowywania), należy włączyć przycisk przez ustawienie `m_bEnabledInCustomizeMode` elementu członkowskiego na wartość TRUE. Domyślnie ten element członkowski ma wartość FALSE.

##  <a name="ondraw"></a>  CMFCColorButton::OnDraw

Metoda wywoływana przez platformę, by renderować obraz przycisku.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskazuje kontekst urządzenia, który jest używany do renderowania obrazu przycisku.

*Rect*<br/>
[in] Prostokąt, który granic przycisku.

*uiState*<br/>
[in] Określa stan wizualny przycisku.

### <a name="remarks"></a>Uwagi

Zastępuje tę metodę w celu dostosowania procesu renderowania.

##  <a name="ondrawborder"></a>  CMFCColorButton::OnDrawBorder

Metoda wywoływana przez platformę, by wyświetlić obramowania przycisku.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskazuje kontekst urządzenia używany do rysowania obramowania.

*rectClient*<br/>
[in] Prostokąt w kontekście urządzenia, który jest określony przez *kontrolera pDC* parametr, który definiuje granice przycisku do narysowania.

*uiState*<br/>
[in] Określa stan wizualny przycisku.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby dostosować wygląd obramowania przycisku koloru.

##  <a name="ondrawfocusrect"></a>  CMFCColorButton::OnDrawFocusRect

Metoda wywoływana przez platformę, by wyświetlić prostokąta fokusu w przypadku, gdy przycisk ma fokus.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskazuje kontekst urządzenia używany do rysowania prostokąt fokusu.

*rectClient*<br/>
[in] Prostokąt w kontekście urządzenia określone przez *kontrolera pDC* parametr, który definiuje granice tego przycisku.

### <a name="remarks"></a>Uwagi

Zastępuje tę metodę, aby dostosować wygląd prostokąt fokusu.

##  <a name="onshowcolorpopup"></a>  CMFCColorButton::OnShowColorPopup

Metoda wywoływana przed wyświetleniem podręczny pasek koloru.

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>Uwagi

##  <a name="rebuildpalette"></a>  CMFCColorButton::RebuildPalette

Inicjuje `m_pPalette` chroniony element członkowski danych palety określona lub domyślna paleta systemu.

```
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pPal*|[in] Wskaźnik do palety logiczne lub wartość NULL. Jeśli ma wartość NULL, jest używana domyślna paleta systemu.|

##  <a name="setcolor"></a>  CMFCColorButton::SetColor

Określa kolor przycisku.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
[in] Wartość RGB.

### <a name="remarks"></a>Uwagi

##  <a name="setcolorname"></a>  CMFCColorButton::SetColorName

Określa nazwę koloru.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
[in] Kolor RGB wartość.

*strName*<br/>
[in] Nazwa koloru.

### <a name="remarks"></a>Uwagi

Lista nazw kolorów jest globalny dla aplikacji. W związku z tym, ta metoda przekazuje parametry [CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).

##  <a name="setcolumnsnumber"></a>  CMFCColorButton::SetColumnsNumber

Określa liczbę kolumn, które są wyświetlane w tabeli kolorów, które są prezentowane użytkownikowi podczas procesu wyboru koloru użytkownika.

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parametry

*nColumns*<br/>
[in] Określa liczbę kolumn.

### <a name="remarks"></a>Uwagi

Użytkownik może wybrać kolor z podręczny pasek koloru, który wyświetla tabelę wstępnie zdefiniowanych kolorów. Ta metoda umożliwia zdefiniowanie liczby kolumn w tabeli.

##  <a name="setdocumentcolors"></a>  CMFCColorButton::SetDocumentColors

Określa zestaw kolorów i nazwy zestawu. Zestaw kolorów jest wyświetlana przy użyciu [klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) obiektu.

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Określa etykietę, która ma być wyświetlany z zestawem kolory dokumentu.

*lstColors*<br/>
[in] Odwołanie do listy wartości RGB.

### <a name="remarks"></a>Uwagi

A `CMFCColorButton` obiekt przechowuje listę wartości RGB, które są przekazywane do [klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) obiektu. Po wyświetleniu paska koloru tych kolorów są wyświetlane w specjalnej sekcji, w której etykietę jest określona przez *lpszLabel* parametru.

##  <a name="setpalette"></a>  CMFCColorButton::SetPalette

Określa kolory standardowe do wyświetlenia w podręcznym pasku koloru.

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parametry

*pPalette*<br/>
[in] Wskaźnik do palety kolorów.

### <a name="remarks"></a>Uwagi

##  <a name="sizetocontent"></a>  CMFCColorButton::SizeToContent

Zmienia rozmiar kontrolki przycisku, aby dopasować jego tekstu i obrazów.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
[in] Jeśli wartość jest niezerowa, nowy rozmiar kontrolki przycisku jest obliczana, ale rzeczywisty rozmiar nie jest zmieniany.

### <a name="return-value"></a>Wartość zwracana

A `CSize` obiekt, który określa nowy rozmiar kontrolki przycisku.

### <a name="remarks"></a>Uwagi

##  <a name="updatecolor"></a>  CMFCColorButton::UpdateColor

Wywoływane przez platformę, gdy użytkownik zaznaczy kolor z paska koloru, w którym są wyświetlane, gdy użytkownik kliknie przycisk koloru.

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
[in] Kolor wybrany przez użytkownika.

### <a name="remarks"></a>Uwagi

`UpdateColor` Funkcji zmienia kolor aktualnie zaznaczonego przycisku i powiadamia o jego obiektu nadrzędnego, wysyłając wiadomość z powiadomieniem do standardowego BN_CLICKED WM_COMMAND. Użyj [CMFCColorButton::GetColor](#getcolor) metoda pobierania wybranego koloru.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md)<br/>
[Klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/desktop/gdi/colorref)<br/>
[Klasa CPalette](../../mfc/reference/cpalette-class.md)<br/>
[Klasa CArray](../../mfc/reference/carray-class.md)<br/>
[Klasa CList](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
