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
ms.openlocfilehash: 7abe37969799d7fcd78d525a5ec1c6faa9d876ee
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561001"
---
# <a name="cmfccolorbutton-class"></a>Klasa CMFCColorButton

`CMFCColorButton`Klasy i klasy [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) są używane razem w celu zaimplementowania kontrolki selektora kolorów.

## <a name="syntax"></a>Składnia

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Tworzy nowy `CMFCColorButton` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Włącza i wyłącza przycisk "automatyczny" umieszczony powyżej przycisków zwykłych kolorów. (Standardowy przycisk systemowy jest **automatycznie**oznaczony etykietą).|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Włącza i wyłącza przycisk "inne", który jest umieszczony poniżej zwykłych przycisków kolorów. (Standardowy przycisk "inny" ma etykietę **więcej kolorów**).|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Pobiera bieżący automatyczny kolor.|
|[CMFCColorButton:: GetColor](#getcolor)|Pobiera kolor przycisku.|
|[CMFCColorButton:: SetColor](#setcolor)|Ustawia kolor przycisku.|
|[CMFCColorButton:: SetColorName](#setcolorname)|Ustawia nazwę koloru.|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Ustawia liczbę kolumn w oknie dialogowym selektora kolorów.|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Określa listę kolorów specyficznych dla dokumentu, które są wyświetlane w oknie dialogowym selektora kolorów.|
|[CMFCColorButton:: setpaleta](#setpalette)|Określa paletę standardowych kolorów wyświetlania.|
|[CMFCColorButton::SizeToContent](#sizetocontent)|Zmienia rozmiar kontrolki przycisku w zależności od jego tekstu i rozmiaru obrazu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Wskazuje, czy bieżący przycisk koloru jest wyświetlany w stylu wizualnym systemu Windows XP.|
|[CMFCColorButton:: OnDraw](#ondraw)|Wywoływane przez platformę, aby wyświetlić obraz przycisku.|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Wywoływane przez platformę, aby wyświetlić obramowanie przycisku.|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Wywoływane przez platformę, aby wyświetlić prostokąt fokusu, gdy przycisk ma fokus.|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Wywoływane przez platformę, gdy zostanie wyświetlone okno dialogowe selektora kolorów.|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Inicjuje `m_pPalette` element członkowski danych chronionych do określonej palety lub domyślnej palety systemowej.|
|[CMFCColorButton::UpdateColor](#updatecolor)|Wywoływane przez platformę, gdy użytkownik wybierze kolor z palety okna dialogowego selektora kolorów.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|`m_bAltColorDlg`|Wartość logiczna. Jeśli wartość jest równa TRUE, struktura wyświetla okno dialogowe Kolor [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) po kliknięciu *drugiego* przycisku lub w przypadku wartości false okna dialogowego kolor systemu. Wartość domyślna to TRUE. Aby uzyskać więcej informacji, zobacz [CMFCColorButton:: EnableOtherButton](#enableotherbutton).|
|`m_bAutoSetFocus`|Wartość logiczna. Jeśli wartość jest równa TRUE, struktura ustawia fokus w menu kolor, gdy menu jest wyświetlane lub wartość FALSE, nie zmienia fokusu. Wartość domyślna to TRUE.|
|[CMFCColorButton:: m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Wskazuje, czy dla przycisku Color włączono tryb dostosowywania.|
|`m_Color`|Wartość [COLORREF](/windows/win32/gdi/colorref) . Zawiera aktualnie wybrany kolor.|
|`m_ColorAutomatic`|Wartość [COLORREF](/windows/win32/gdi/colorref) . Zawiera aktualnie wybrany kolor domyślny.|
|`m_Colors`|[CArray](../../mfc/reference/carray-class.md) wartości [COLORREF](/windows/win32/gdi/colorref) . Zawiera aktualnie dostępne kolory.|
|`m_lstDocColors`|[CList](../../mfc/reference/clist-class.md) wartości [COLORREF](/windows/win32/gdi/colorref) . Zawiera kolory bieżącego dokumentu.|
|`m_nColumns`|Liczba całkowita. Zawiera liczbę kolumn do wyświetlenia w siatce kolorów w menu wyboru kolorów.|
|`m_pPalette`|Wskaźnik do elementu [CPalette](../../mfc/reference/cpalette-class.md). Zawiera kolory dostępne w bieżącym menu wyboru kolorów.|
|`m_pPopup`|Wskaźnik do obiektu [klasy CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md) . Menu wyboru koloru, które jest wyświetlane po kliknięciu przycisku koloru.|
|`m_strAutoColorText`|Ciąg. Etykieta przycisku "automatyczny" w menu wyboru kolorów.|
|`m_strDocColorsText`|Ciąg. Etykieta przycisku w menu wyboru koloru, które wyświetla kolory dokumentu.|
|`m_strOtherText`|Ciąg. Etykieta przycisku "inne" w menu wyboru kolorów.|

## <a name="remarks"></a>Uwagi

Domyślnie `CMFCColorButton` Klasa zachowuje się jako przycisk wypychania, który otwiera okno dialogowe selektora kolorów. Okno dialogowe selektora kolorów zawiera tablicę przycisków o małym kolorze i przycisk "inne", który wyświetla niestandardowy selektor kolorów. (Standardowy przycisk "inny" ma etykietę **więcej kolorów**). Gdy użytkownik wybierze nowy kolor, `CMFCColorButton` obiekt odzwierciedla zmianę i wyświetla wybrany kolor.

Utwórz kontrolkę przycisku koloru bezpośrednio w kodzie lub przy użyciu narzędzia **ClassWizard** i szablonu okna dialogowego. Jeśli utworzysz kontrolkę przycisk koloru bezpośrednio, Dodaj `CMFCColorButton` zmienną do aplikacji, a następnie Wywołaj konstruktora i `Create` metody `CMFCColorButton` obiektu. Jeśli używasz **ClassWizard**, Dodaj `CButton` zmienną do aplikacji, a następnie zmień typ zmiennej z `CButton` na `CMFCColorButton` .

Okno dialogowe selektora kolorów ( [Klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)) jest wyświetlane przez metodę [CMFCColorButton:: OnShowColorPopup](#onshowcolorpopup) , gdy struktura wywołuje `OnLButtonDown` program obsługi zdarzeń. Metodę [CMFCColorButton:: OnShowColorPopup](#onshowcolorpopup) można zastąpić, aby obsługiwała wybór koloru niestandardowego.

`CMFCColorButton`Obiekt powiadamia jego element nadrzędny o zmianie koloru, wysyłając go WM_COMMAND | BN_CLICKED powiadomienia. Element nadrzędny używa metody [CMFCColorButton:: GetColor](#getcolor) , aby pobrać bieżący kolor.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak skonfigurować przycisk koloru przy użyciu różnych metod w `CMFCColorButton` klasie. Metody ustawiają kolor przycisku koloru i jego liczbę kolumn oraz włączają automatyczne i inne przyciski. Ten przykład jest częścią [przykładu pokazu paska stanu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcolorbutton. h

## <a name="cmfccolorbuttoncmfccolorbutton"></a><a name="cmfccolorbutton"></a> CMFCColorButton::CMFCColorButton

Tworzy nowy `CMFCColorButton` obiekt.

```
CMFCColorButton();
```

## <a name="cmfccolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a> CMFCColorButton::EnableAutomaticButton

Włącz lub Wyłącz przycisk "automatyczny" kontrolki selektora kolorów i ustaw automatyczny kolor (domyślny).

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
podczas Określa tekst przycisku automatycznego.

*colorAutomatic*<br/>
podczas Wartość RGB określająca domyślny kolor przycisku automatycznego.

*bEnable*<br/>
podczas Określa, czy przycisk Automatyczny jest włączony, czy wyłączony.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a> CMFCColorButton::EnableOtherButton

Włącz lub Wyłącz przycisk "inne", który jest wyświetlany poniżej zwykłych przycisków kolorów.

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
podczas Określa tekst przycisku.

*bAltColorDlg*<br/>
podczas Określa, czy okno dialogowe [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) lub okno dialogowe Kolor systemu jest otwierane po kliknięciu przycisku przez użytkownika.

*bEnable*<br/>
podczas Określa, czy przycisk "inne" jest włączony, czy wyłączony.

### <a name="remarks"></a>Uwagi

Kliknij przycisk "inne", aby wyświetlić okno dialogowe koloru. Jeśli parametr *bAltColorDlg* ma wartość true, zostanie wyświetlona [Klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) ; w przeciwnym razie zostanie wyświetlone okno dialogowe Kolor systemu.

## <a name="cmfccolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a> CMFCColorButton::GetAutomaticColor

Pobiera bieżący automatyczny kolor (domyślny).

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość RGB reprezentująca bieżący kolor automatyczny.

### <a name="remarks"></a>Uwagi

Bieżący kolor automatyczny jest ustawiany przez metodę [CMFCColorButton:: EnableAutomaticButton](#enableautomaticbutton) .

## <a name="cmfccolorbuttongetcolor"></a><a name="getcolor"></a> CMFCColorButton:: GetColor

Pobiera aktualnie wybrany kolor.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość RGB.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbuttonisdrawxptheme"></a><a name="isdrawxptheme"></a> CMFCColorButton::IsDrawXPTheme

Wskazuje, czy bieżący przycisk koloru jest wyświetlany w stylu wizualnym systemu Windows XP.

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli style wizualizacji są obsługiwane i przycisk bieżący kolor jest wyświetlany w stylu wizualnym systemu Windows XP; w przeciwnym razie FALSE.

## <a name="cmfccolorbuttonm_benabledincustomizemode"></a><a name="m_benabledincustomizemode"></a> CMFCColorButton:: m_bEnabledInCustomizeMode

Ustawia przycisk koloru na tryb dostosowywania.

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>Uwagi

Jeśli musisz dodać przycisk koloru do strony okna dialogowego dostosowywania (lub zezwolić użytkownikowi na wybranie innego koloru podczas dostosowywania), włącz przycisk, ustawiając `m_bEnabledInCustomizeMode` element członkowski na wartość true. Domyślnie ten element członkowski jest ustawiony na wartość FALSE.

## <a name="cmfccolorbuttonondraw"></a><a name="ondraw"></a> CMFCColorButton:: OnDraw

Wywoływane przez platformę w celu renderowania obrazu przycisku.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskazuje kontekst urządzenia, który jest używany do renderowania obrazu przycisku.

*cinania*<br/>
podczas Prostokąt, który jest powiązany z przyciskiem.

*uiState*<br/>
podczas Określa stan wizualizacji przycisku.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby dostosować proces renderowania.

## <a name="cmfccolorbuttonondrawborder"></a><a name="ondrawborder"></a> CMFCColorButton::OnDrawBorder

Wywoływane przez platformę, aby wyświetlić obramowanie przycisku.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskazuje kontekst urządzenia używany do rysowania obramowania.

*rectClient*<br/>
podczas Prostokąt w kontekście urządzenia, który jest określony przez parametr *podstawowego kontrolera domeny* , który definiuje granice przycisku do narysowania.

*uiState*<br/>
podczas Określa stan wizualizacji przycisku.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby dostosować wygląd obramowania przycisku Color.

## <a name="cmfccolorbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a> CMFCColorButton::OnDrawFocusRect

Wywoływane przez platformę, aby wyświetlić prostokąt fokusu, gdy przycisk ma fokus.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskazuje kontekst urządzenia używany do rysowania prostokąta fokusu.

*rectClient*<br/>
podczas Prostokąt w kontekście urządzenia określony przez parametr *podstawowego kontrolera domeny* , który definiuje granice przycisku.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby dostosować wygląd prostokąta fokusu.

## <a name="cmfccolorbuttononshowcolorpopup"></a><a name="onshowcolorpopup"></a> CMFCColorButton::OnShowColorPopup

Wywoływana przed wyświetleniem paska koloru podręcznego.

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbuttonrebuildpalette"></a><a name="rebuildpalette"></a> CMFCColorButton::RebuildPalette

Inicjuje `m_pPalette` element członkowski danych chronionych do określonej palety lub domyślnej palety systemowej.

```cpp
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>Parametry

*pPal*\
podczas Wskaźnik do logicznej palety lub wartości NULL. Jeśli wartość jest równa NULL, używana jest domyślna paleta systemowa.

## <a name="cmfccolorbuttonsetcolor"></a><a name="setcolor"></a> CMFCColorButton:: SetColor

Określa kolor przycisku.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
podczas Wartość RGB.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbuttonsetcolorname"></a><a name="setcolorname"></a> CMFCColorButton:: SetColorName

Określa nazwę koloru.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
podczas Wartość RGB koloru.

*strName*<br/>
podczas Nazwa koloru.

### <a name="remarks"></a>Uwagi

Lista nazw kolorów jest globalna dla każdej aplikacji. W związku z tym ta metoda przesyła parametry do [CMFCColorBar:: SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).

## <a name="cmfccolorbuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a> CMFCColorButton::SetColumnsNumber

Definiuje liczbę kolumn wyświetlanych w tabeli kolorów prezentowanych użytkownikowi podczas procesu wyboru koloru użytkownika.

```cpp
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parametry

*nColumns*<br/>
podczas Określa liczbę kolumn.

### <a name="remarks"></a>Uwagi

Użytkownik może wybrać kolor z podręczny pasek koloru, który wyświetla tabelę wstępnie zdefiniowanych kolorów. Użyj tej metody, aby zdefiniować liczbę kolumn w tabeli.

## <a name="cmfccolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a> CMFCColorButton::SetDocumentColors

Określa zestaw kolorów i nazwę zestawu. Zestaw kolorów jest wyświetlany przy użyciu obiektu [klasy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) .

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
podczas Określa etykietę, która ma być wyświetlana z zestawem kolorów dokumentu.

*lstColors*<br/>
podczas Odwołanie do listy wartości RGB.

### <a name="remarks"></a>Uwagi

`CMFCColorButton`Obiekt zachowuje listę wartości RGB, które są przesyłane do obiektu [klasy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) . Po wyświetleniu paska kolorów te kolory są wyświetlane w specjalnej sekcji, której etykieta jest określona przez parametr *lpszLabel* .

## <a name="cmfccolorbuttonsetpalette"></a><a name="setpalette"></a> CMFCColorButton:: setpaleta

Określa kolory standardowe, które mają być wyświetlane na pasku koloru podręcznego.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parametry

*pPalette*<br/>
podczas Wskaźnik do palety kolorów.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbuttonsizetocontent"></a><a name="sizetocontent"></a> CMFCColorButton::SizeToContent

Zmienia rozmiar kontrolki przycisku w celu dopasowania jej do tekstu i obrazu.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
podczas Jeśli wartość jest różna od zera, nowy rozmiar kontrolki przycisk jest obliczany, ale rzeczywisty rozmiar nie jest zmieniany.

### <a name="return-value"></a>Wartość zwracana

`CSize`Obiekt, który określa nowy rozmiar formantu przycisku.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbuttonupdatecolor"></a><a name="updatecolor"></a> CMFCColorButton::UpdateColor

Wywoływane przez platformę, gdy użytkownik wybierze kolor z paska kolorów, który jest wyświetlany, gdy użytkownik kliknie przycisk koloru.

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
podczas Kolor wybrany przez użytkownika.

### <a name="remarks"></a>Uwagi

`UpdateColor`Funkcja zmienia kolor aktualnie wybranego przycisku i powiadamia jego element nadrzędny przez wysłanie komunikatu WM_COMMAND za pomocą BN_CLICKED standardowego powiadomienia. Użyj metody [CMFCColorButton:: GetColor](#getcolor) , aby pobrać wybrany kolor.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md)<br/>
[Klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[Klasa CPalette](../../mfc/reference/cpalette-class.md)<br/>
[Klasa CArray](../../mfc/reference/carray-class.md)<br/>
[Klasa CList](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
