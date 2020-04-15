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
ms.openlocfilehash: 21d05fd8e805467f1a7a77d20c81d5ba0401455e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367735"
---
# <a name="cmfccolorbutton-class"></a>Klasa CMFCColorButton

Klasy `CMFCColorButton` [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) są używane razem do implementowania formantu selektora kolorów.

## <a name="syntax"></a>Składnia

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Konstruuje `CMFCColorButton` nowy obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Włącza i wyłącza przycisk "automatyczny", który znajduje się nad zwykłymi przyciskami kolorów. (Standardowy automatyczny przycisk systemu jest oznaczony jako **Automatyczny).**|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Włącza i wyłącza przycisk "inne", który znajduje się poniżej zwykłych przycisków kolorów. (Standardowy systemowy przycisk "inne" jest oznaczony jako **Więcej kolorów.)**|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Pobiera bieżący kolor automatyczny.|
|[CMFCColorButton::GetColor](#getcolor)|Pobiera kolor przycisku.|
|[CMFCColorButton::SetColor](#setcolor)|Ustawia kolor przycisku.|
|[CMFCColorButton::SetColorName](#setcolorname)|Ustawia nazwę koloru.|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Ustawia liczbę kolumn w oknie dialogowym selektora kolorów.|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Określa listę kolorów specyficznych dla dokumentu wyświetlanych w oknie dialogowym selektora kolorów.|
|[CMFCColorButton::SetPalette](#setpalette)|Określa paletę standardowych kolorów wyświetlania.|
|[CMFCColorButton::SizeToContent](#sizetocontent)|Zmienia rozmiar formantu przycisku w zależności od jego tekstu i rozmiaru obrazu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Wskazuje, czy bieżący przycisk koloru jest wyświetlany w stylu wizualnym systemu Windows XP.|
|[CMFCColorButton::OnDraw](#ondraw)|Wywoływana przez strukturę, aby wyświetlić obraz przycisku.|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Wywoływana przez strukturę, aby wyświetlić obramowanie przycisku.|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Wywoływane przez strukturę, aby wyświetlić prostokąt fokus, gdy przycisk ma fokus.|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Wywoływana przez strukturę, gdy okno dialogowe selektora kolorów ma być wyświetlane.|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Inicjuje `m_pPalette` chroniony element członkowski danych do określonej palety lub domyślnej palety systemowej.|
|[CMFCColorButton::UpdateColor](#updatecolor)|Wywoływana przez strukturę, gdy użytkownik wybiera kolor z palety okna dialogowego selektora kolorów.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|`m_bAltColorDlg`|Wartość logiczna. Jeśli TRUE, ramach wyświetla [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) kolor okna dialogowego po kliknięciu *innego* przycisku lub jeśli FALSE, okno dialogowe kolor systemu. Wartością domyślną jest PRAWDA. Aby uzyskać więcej informacji, zobacz [CMFCColorButton::EnableOtherButton](#enableotherbutton).|
|`m_bAutoSetFocus`|Wartość logiczna. Jeśli true, struktura ustawia fokus na menu kolorów, gdy menu jest wyświetlany lub jeśli FALSE, nie zmienia fokusu. Wartością domyślną jest PRAWDA.|
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Wskazuje, czy dla przycisku koloru jest włączony tryb dostosowywania.|
|`m_Color`|Wartość [COLORREF.](/windows/win32/gdi/colorref) Zawiera aktualnie zaznaczony kolor.|
|`m_ColorAutomatic`|Wartość [COLORREF.](/windows/win32/gdi/colorref) Zawiera aktualnie wybrany kolor domyślny.|
|`m_Colors`|[CArray](../../mfc/reference/carray-class.md) wartości [COLORREF.](/windows/win32/gdi/colorref) Zawiera aktualnie dostępne kolory.|
|`m_lstDocColors`|Lista [C wartości](../../mfc/reference/clist-class.md) [COLORREF.](/windows/win32/gdi/colorref) Zawiera bieżące kolory dokumentu.|
|`m_nColumns`|Liczba całkowita. Zawiera liczbę kolumn wyświetlanych w siatce kolorów w menu wyboru kolorów.|
|`m_pPalette`|Wskaźnik do [CPalette](../../mfc/reference/cpalette-class.md). Zawiera kolory dostępne w bieżącym menu wyboru kolorów.|
|`m_pPopup`|Wskaźnik do [cmfccolorpopupmenu klasy](../../mfc/reference/cmfccolorpopupmenu-class.md) obiektu. Menu wyboru kolorów wyświetlane po kliknięciu przycisku koloru.|
|`m_strAutoColorText`|Ciąg. Etykieta przycisku "automatyczny" w menu wyboru koloru.|
|`m_strDocColorsText`|Ciąg. Etykieta przycisku w menu wyboru kolorów, która wyświetla kolory dokumentu.|
|`m_strOtherText`|Ciąg. Etykieta przycisku "inne" w menu wyboru koloru.|

## <a name="remarks"></a>Uwagi

Domyślnie `CMFCColorButton` klasa zachowuje się jak przycisk, który otwiera okno dialogowe selektora kolorów. Okno dialogowe selektora kolorów zawiera tablicę małych przycisków kolorów i przycisk "inne", który wyświetla niestandardowy selektor kolorów. (Standardowy systemowy przycisk "inne" jest oznaczony jako **Więcej kolorów.)** Gdy użytkownik wybierze nowy kolor, `CMFCColorButton` obiekt odzwierciedla zmianę i wyświetla wybrany kolor.

Utwórz kontrolkę przycisku koloru bezpośrednio w kodzie lub za pomocą narzędzia **ClassWizard** i szablonu okna dialogowego. Jeśli tworzysz formant przycisku koloru `CMFCColorButton` bezpośrednio, dodaj zmienną do aplikacji, a następnie wywołaj konstruktor i `Create` metody `CMFCColorButton` obiektu. Jeśli używasz **ClassWizard**, `CButton` dodaj zmienną do aplikacji, a następnie `CButton` `CMFCColorButton`zmień typ zmiennej z .

Okno dialogowe selektora kolorów [(CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)) jest wyświetlane przez [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) metody, gdy struktura wywołuje program obsługi `OnLButtonDown` zdarzeń. [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) metoda może zostać zastąpiona do obsługi niestandardowego wyboru kolorów.

Obiekt `CMFCColorButton` powiadamia rodzica, że kolor zmienia się, wysyłając go WM_COMMAND | BN_CLICKED powiadomienie. Element nadrzędny używa [CMFCColorButton::GetColor](#getcolor) metody do pobierania bieżącego koloru.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonfigurować przycisk `CMFCColorButton` koloru przy użyciu różnych metod w klasie. Metody ustawiają kolor przycisku koloru i jego liczbę kolumn oraz włączają automatyczne i inne przyciski. W tym przykładzie jest częścią [przykładu demo paska stanu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcolorbutton.h

## <a name="cmfccolorbuttoncmfccolorbutton"></a><a name="cmfccolorbutton"></a>CMFCColorButton::CMFCColorButton

Konstruuje `CMFCColorButton` nowy obiekt.

```
CMFCColorButton();
```

## <a name="cmfccolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorButton::EnableAutomaticButton

Włącz lub wyłącz przycisk "automatyczny" formantu selektora kolorów i ustaw automatyczny (domyślny) kolor.

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
[w] Określa tekst przycisku automatycznego.

*kolorAutomatyczny*<br/>
[w] Wartość RGB określająca domyślny kolor przycisku automatycznego.

*bWłaszą*<br/>
[w] Określa, czy przycisk automatyczny jest włączony, czy wyłączony.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorButton::EnableOtherButton

Włącz lub wyłącz przycisk "inne", który pojawia się poniżej zwykłych przycisków kolorów.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
[w] Określa tekst przycisku.

*bAltColorDlg*<br/>
[w] Określa, czy okno dialogowe [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) lub okno dialogowe kolor systemu jest otwierane, gdy użytkownik kliknie przycisk.

*bWłaszą*<br/>
[w] Określa, czy przycisk "inne" jest włączony czy wyłączony.

### <a name="remarks"></a>Uwagi

Kliknij przycisk "inne", aby wyświetlić kolorowe okno dialogowe. Jeśli parametr *bAltColorDlg* ma wartość TRUE, wyświetlana jest [klasa CMFCColorDialog;](../../mfc/reference/cmfccolordialog-class.md) w przeciwnym razie zostanie wyświetlone okno dialogowe kolor systemu.

## <a name="cmfccolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCColorButton::GetAutomaticColor

Pobiera bieżący kolor automatyczny (domyślny).

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość RGB reprezentująca bieżący kolor automatyczny.

### <a name="remarks"></a>Uwagi

Bieżący kolor automatyczny jest ustawiany przez [CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton) metody.

## <a name="cmfccolorbuttongetcolor"></a><a name="getcolor"></a>CMFCColorButton::GetColor

Pobiera aktualnie zaznaczony kolor.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość RGB.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbuttonisdrawxptheme"></a><a name="isdrawxptheme"></a>CMFCColorButton::IsDrawXPTheme

Wskazuje, czy bieżący przycisk koloru jest wyświetlany w stylu wizualnym systemu Windows XP.

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli obsługiwane są style wizualne, a bieżący przycisk koloru jest wyświetlany w stylu wizualnym systemu Windows XP; w przeciwnym razie FALSE.

## <a name="cmfccolorbuttonm_benabledincustomizemode"></a><a name="m_benabledincustomizemode"></a>CMFCColorButton::m_bEnabledInCustomizeMode

Ustawia kolorowy przycisk do trybu dostosowywania.

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>Uwagi

Jeśli chcesz dodać przycisk koloru do strony okna dialogowego dostosowywania (lub zezwolić użytkownikowi na dokonanie innego `m_bEnabledInCustomizeMode` wyboru koloru podczas dostosowywania), włącz przycisk, ustawiając element członkowski na TRUE. Domyślnie ten element członkowski jest ustawiony na FAŁSZ.

## <a name="cmfccolorbuttonondraw"></a><a name="ondraw"></a>CMFCColorButton::OnDraw

Wywoływana przez strukturę do renderowania obrazu przycisku.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskazuje kontekst urządzenia, który jest używany do renderowania obrazu przycisku.

*Rect*<br/>
[w] Prostokąt, który ogranicza przycisk.

*uiStan*<br/>
[w] Określa stan wizualny przycisku.

### <a name="remarks"></a>Uwagi

Zastąd w tej metodzie należy dostosować proces renderowania.

## <a name="cmfccolorbuttonondrawborder"></a><a name="ondrawborder"></a>CMFCColorButton::OnDrawBorder

Wywoływana przez strukturę, aby wyświetlić obramowanie przycisku.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskazuje kontekst urządzenia używany do rysowania obramowania.

*rectClient*<br/>
[w] Prostokąt w kontekście urządzenia określony przez parametr *pDC* definiujący granice przycisku, który ma zostać narysowany.

*uiStan*<br/>
[w] Określa stan wizualny przycisku.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby dostosować wygląd obramowania przycisku koloru.

## <a name="cmfccolorbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCColorButton::OnDrawFocusRect

Wywoływane przez strukturę, aby wyświetlić prostokąt fokus, gdy przycisk ma fokus.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskazuje kontekst urządzenia używany do rysowania prostokąta fokusu.

*rectClient*<br/>
[w] Prostokąt w kontekście urządzenia określony przez parametr *pDC,* który definiuje granice przycisku.

### <a name="remarks"></a>Uwagi

Zastąpaj tę metodę, aby dostosować wygląd prostokąta fokusu.

## <a name="cmfccolorbuttononshowcolorpopup"></a><a name="onshowcolorpopup"></a>CMFCColorButton::OnShowColorPopup

Wywoływana przed wyświetleniem paska kolorów wyskakujących okienka.

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbuttonrebuildpalette"></a><a name="rebuildpalette"></a>CMFCColorButton::RebuildPalette

Inicjuje `m_pPalette` chroniony element członkowski danych do określonej palety lub domyślnej palety systemowej.

```
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pPal (pPal)*|[w] Wskaźnik do palety logicznej lub null. Jeśli null, używana jest domyślna paleta systemowa.|

## <a name="cmfccolorbuttonsetcolor"></a><a name="setcolor"></a>CMFCColorButton::SetColor

Określa kolor przycisku.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[w] Wartość RGB.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFCColorButton::SetColorName

Określa nazwę koloru.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[w] Wartość RGB koloru.

*nazwa strName*<br/>
[w] Nazwa koloru.

### <a name="remarks"></a>Uwagi

Lista nazw kolorów jest globalna dla aplikacji. W związku z tym ta metoda przenosi swoje parametry do [CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).

## <a name="cmfccolorbuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCColorButton::SetColumnsNumber

Określa liczbę kolumn wyświetlanych w tabeli kolorów, która jest prezentowana użytkownikowi podczas procesu wyboru kolorów użytkownika.

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parametry

*nKolumny*<br/>
[w] Określa liczbę kolumn.

### <a name="remarks"></a>Uwagi

Użytkownik może wybrać kolor z paska kolorów podręcznego, na który wyświetlana jest tabela wstępnie zdefiniowanych kolorów. Ta metoda służy do definiowania liczby kolumn w tabeli.

## <a name="cmfccolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCColorButton::SetDocumentColors

Określa zestaw kolorów i nazwę zestawu. Zestaw kolorów jest wyświetlany przy użyciu [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md) obiektu.

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
[w] Określa etykietę, która ma być wyświetlana wraz z zestawem kolorów dokumentu.

*lstKolory*<br/>
[w] Odwołanie do listy wartości RGB.

### <a name="remarks"></a>Uwagi

Obiekt `CMFCColorButton` przechowuje listę wartości RGB, które są przenoszone do [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md) obiektu. Gdy wyświetlany jest pasek kolorów, kolory te są wyświetlane w specjalnej sekcji, której etykieta jest określona przez parametr *lpszLabel.*

## <a name="cmfccolorbuttonsetpalette"></a><a name="setpalette"></a>CMFCColorButton::SetPalette

Określa kolory standardowe wyświetlane na pasku kolorów wyskakujących okienka.

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parametry

*pPalette (ppalette)*<br/>
[w] Wskaźnik do palety kolorów.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCColorButton::SizeToContent

Rozmiar kontrolki przycisku powoduje zmienić jego rozmiar, aby dopasować go do tekstu i obrazu.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
[w] Jeśli niezerowe, nowy rozmiar formantu przycisku jest obliczany, ale rzeczywisty rozmiar nie ulega zmianie.

### <a name="return-value"></a>Wartość zwracana

Obiekt, `CSize` który określa nowy rozmiar formantu przycisku.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFCColorButton::UpdateColor

Wywoływana przez strukturę, gdy użytkownik wybiera kolor z paska kolorów, który jest wyświetlany, gdy użytkownik kliknie przycisk koloru.

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[w] Kolor wybrany przez użytkownika.

### <a name="remarks"></a>Uwagi

Funkcja `UpdateColor` zmienia kolor aktualnie wybranego przycisku i powiadamia jego element nadrzędny, wysyłając wiadomość WM_COMMAND z BN_CLICKED standardowym powiadomieniem. Użyj [CMFCColorButton::GetColor](#getcolor) metody, aby pobrać wybrany kolor.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md)<br/>
[Klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[Colorref](/windows/win32/gdi/colorref)<br/>
[Klasa CPalette](../../mfc/reference/cpalette-class.md)<br/>
[Klasa CArray](../../mfc/reference/carray-class.md)<br/>
[Klasa CList](../../mfc/reference/clist-class.md)<br/>
[Cstring](../../atl-mfc-shared/reference/cstringt-class.md)
