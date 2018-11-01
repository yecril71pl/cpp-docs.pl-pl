---
title: Klasa CMFCRibbonColorButton
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::AddColorsGroup
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableAutomaticButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableOtherButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetAutomaticColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetHighlightedColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::RemoveAllColorGroups
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorName
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetDocumentColors
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetPalette
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::UpdateColor
helpviewer_keywords:
- CMFCRibbonColorButton [MFC], CMFCRibbonColorButton
- CMFCRibbonColorButton [MFC], AddColorsGroup
- CMFCRibbonColorButton [MFC], EnableAutomaticButton
- CMFCRibbonColorButton [MFC], EnableOtherButton
- CMFCRibbonColorButton [MFC], GetAutomaticColor
- CMFCRibbonColorButton [MFC], GetColor
- CMFCRibbonColorButton [MFC], GetColorBoxSize
- CMFCRibbonColorButton [MFC], GetColumns
- CMFCRibbonColorButton [MFC], GetHighlightedColor
- CMFCRibbonColorButton [MFC], RemoveAllColorGroups
- CMFCRibbonColorButton [MFC], SetColor
- CMFCRibbonColorButton [MFC], SetColorBoxSize
- CMFCRibbonColorButton [MFC], SetColorName
- CMFCRibbonColorButton [MFC], SetColumns
- CMFCRibbonColorButton [MFC], SetDocumentColors
- CMFCRibbonColorButton [MFC], SetPalette
- CMFCRibbonColorButton [MFC], UpdateColor
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
ms.openlocfilehash: f0a55fa9cb431900a0454d481a77efc4e63372ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644837"
---
# <a name="cmfcribboncolorbutton-class"></a>Klasa CMFCRibbonColorButton

`CMFCRibbonColorButton` Klasa implementuje przycisk koloru, który można dodać do paska wstążki. Przycisk koloru wstążki Wyświetla menu rozwijane, który zawiera co najmniej jeden palet kolorów.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonColorButton : public CMFCRibbonGallery
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonColorButton::AddColorsGroup](#addcolorsgroup)|Dodaje grupę kolorów do obszaru regularne kolorów.|
|[CMFCRibbonColorButton::EnableAutomaticButton](#enableautomaticbutton)|Określa, czy **automatyczne** przycisk jest aktywny.|
|[CMFCRibbonColorButton::EnableOtherButton](#enableotherbutton)|Włącza **innych** przycisku.|
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||
|[CMFCRibbonColorButton::GetColor](#getcolor)|Zwraca aktualnie wybranym kolorze.|
|[CMFCRibbonColorButton::GetColorBoxSize](#getcolorboxsize)|Zwraca rozmiar kolorowe elementy, które są wyświetlane na pasku kolorów.|
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||
|[CMFCRibbonColorButton::GetHighlightedColor](#gethighlightedcolor)|Zwraca kolor obecnie wybrany element na palecie kolorów okna podręcznego.|
|[CMFCRibbonColorButton::RemoveAllColorGroups](#removeallcolorgroups)|Usuwa wszystkie grupy kolorów z obszaru regularne kolorów.|
|[CMFCRibbonColorButton::SetColor](#setcolor)|Zaznaczy kolor przy użyciu obszaru regularne kolorów.|
|[CMFCRibbonColorButton::SetColorBoxSize](#setcolorboxsize)|Ustawia rozmiar wszystkich elementów kolorów, które pojawiają się na pasku kolorów.|
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||
|[CMFCRibbonColorButton::SetDocumentColors](#setdocumentcolors)|Określa listę wartości RGB, aby wyświetlić w obszarze kolor dokumentu.|
|[CMFCRibbonColorButton::SetPalette](#setpalette)||
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||

## <a name="remarks"></a>Uwagi

Przycisk koloru wstążki Wyświetla pasek koloru po użytkownik naciska go. Domyślnie ten pasek koloru zawiera paletę kolorów o nazwie obszar regularne koloru. Opcjonalnie wyświetlić pasek koloru **automatyczne** przycisk, który umożliwia użytkownikowi wybranie domyślny kolor, a **innych** przycisk, który wyświetla menu podręczne paletę kolorów, zawierający dodatkowe kolory.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCRibbonColorButton` klasy. W przykładzie pokazano sposób tworzenia `CMFCRibbonColorButton` obiektu, ustawianie duży obraz, Włącz **automatyczne** przycisk, należy włączyć **innych** przycisk, ustaw liczbę kolumn, ustawianie rozmiaru kolorowe elementy są wyświetlane na pasku kolorów, Dodaj grupę kolorów do obszaru regularne kolorów i określ listę wartości RGB, aby wyświetlić w obszarze kolor dokumentu. Ten fragment kodu jest częścią [Rysowanie Client sample](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribboncolorbutton.h

##  <a name="addcolorsgroup"></a>  CMFCRibbonColorButton::AddColorsGroup

Dodaje grupę kolorów do obszaru regularne kolorów.

```
void AddColorsGroup(
    LPCTSTR lpszName,
    const CList<COLORREF,COLORREF>& lstColors,
    BOOL bContiguousColumns=FALSE);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
[in] Nazwa grupy.

*lstColors*<br/>
[in] Lista kolorów.

*bContiguousColumns*<br/>
[in] Określa, jak elementy kolorów są wyświetlane w grupie. W przypadku opcji TRUE elementów kolorów są rysowane bez odstępy w pionie. Jeśli wartość to FALSE, elementy kolorów są rysowane odstępy w pionie.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji, aby kolor wyskakującego wyświetlić kilka grup kolorów. Można kontrolować sposób wyświetlania kolorów w grupie.

##  <a name="cmfcribboncolorbutton"></a>  CMFCRibbonColorButton::CMFCRibbonColorButton

Konstruuje `CMFCRibbonColorButton` obiektu.

```
CMFCRibbonColorButton();

CMFCRibbonColorButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex,
    COLORREF color = RGB(0, 0, 0));

CMFCRibbonColorButton(
    UINT nID,
    LPCTSTR lpszText,
    BOOL bSimpleButtonLook,
    int nSmallImageIndex,
    int nLargeImageIndex,
    COLORREF color = RGB(0, 0, 0));
```

### <a name="parameters"></a>Parametry

*nID*<br/>
[in] Określa identyfikator polecenia polecenie do wykonania, gdy użytkownik kliknie przycisk.

*lpszText*<br/>
[in] Określa tekst wyświetlany na przycisku.

*nSmallImageIndex*<br/>
[in] Liczony od zera indeks mały obraz była wyświetlana na przycisku.

*Kolor*<br/>
[in] Kolor przycisku (domyślnie czarny).

*bSimpleButtonLook*<br/>
[in] W przypadku opcji TRUE przycisku jest rysowana w formie prosty prostokąt.

*nLargeImageIndex*<br/>
[in] Liczony od zera indeks duży obraz, który wyświetlany na przycisku.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="enableautomaticbutton"></a>  CMFCRibbonColorButton::EnableAutomaticButton

Określa, czy **automatyczne** przycisk jest aktywny.

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE,
    LPCTSTR lpszToolTip=NULL,
    BOOL bOnTop=TRUE,
    BOOL bDrawBorder=FALSE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Etykieta dla **automatyczne** przycisku.

*colorAutomatic*<br/>
[in] Wartość RGB, który określa **automatyczne** przycisku domyślny kolor.

*bWłączenie*<br/>
[in] Wartość TRUE, jeśli **automatyczne** przycisk jest włączony; Wartość FALSE, jeśli jest wyłączone.

*lpszToolTip*<br/>
[in] Etykietka narzędzia **automatyczne** przycisku.

*bOnTop*<br/>
[in] Określa, czy **automatyczne** przycisk znajduje się na początku, zanim palety kolorów.

*bDrawBorder*<br/>
[in] Wartość TRUE, jeśli aplikacja rysuje obramowanie wokół pasek koloru na przycisk koloru wstążki. Pasek koloru Wyświetla aktualnie wybranym kolorze. Wartość FALSE, jeśli aplikacja nie narysować obramowanie

##  <a name="enableotherbutton"></a>  CMFCRibbonColorButton::EnableOtherButton

Włącza **innych** przycisku.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    LPCTSTR lpszToolTip=NULL);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
Etykieta przycisku.

*lpszToolTip*<br/>
Tekst etykietki narzędzia dla **innych** przycisku.

### <a name="remarks"></a>Uwagi

**Innych** przycisk to przycisk, który jest wyświetlany poniżej grupy kolorów. Kiedy użytkownik kliknie **innych** przycisku, wyświetla okno dialogowe kolorów.

##  <a name="getautomaticcolor"></a>  CMFCRibbonColorButton::GetAutomaticColor

Pobiera bieżący kolor przycisku automatycznego.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość koloru RGB, który reprezentuje bieżący kolor przycisku automatycznego.

### <a name="remarks"></a>Uwagi

Kolor przycisku automatycznego została ustawiona przez `colorAutomatic` parametr przekazany do `CMFCRibbonColorButton::EnableAutomaticButton` metody.

##  <a name="getcolor"></a>  CMFCRibbonColorButton::GetColor

Zwraca aktualnie wybranym kolorze.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolor wybrany przez kliknięcie przycisku.

##  <a name="getcolorboxsize"></a>  CMFCRibbonColorButton::GetColorBoxSize

Zwraca rozmiar kolorowe elementy, które są wyświetlane na pasku kolorów.

```
CSize GetColorBoxSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar przycisków kolor z palety kolorów listy rozwijanej.

##  <a name="getcolumns"></a>  CMFCRibbonColorButton::GetColumns

Pobiera liczbę elementów w wierszu ekranu galerii przycisk koloru wstążki.

```
int GetColumns() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę ikon w każdym wierszu.

### <a name="remarks"></a>Uwagi

##  <a name="gethighlightedcolor"></a>  CMFCRibbonColorButton::GetHighlightedColor

Zwraca kolor obecnie wybrany element na palecie kolorów wyskakujących.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolor obecnie wybrany element na palecie kolorów wyskakujących.

##  <a name="removeallcolorgroups"></a>  CMFCRibbonColorButton::RemoveAllColorGroups

Usuwa wszystkie grupy kolorów z obszaru regularne kolorów.

```
void RemoveAllColorGroups();
```

##  <a name="setcolor"></a>  CMFCRibbonColorButton::SetColor

Zaznaczy kolor przy użyciu obszaru regularne kolorów.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
[in] Kolor, aby ustawić.

##  <a name="setcolorboxsize"></a>  CMFCRibbonColorButton::SetColorBoxSize

Ustawia rozmiar wszystkich elementów kolorów, które pojawiają się na pasku kolorów.

```
void SetColorBoxSize(CSize sizeBox);
```

### <a name="parameters"></a>Parametry

*sizeBox*<br/>
[in] Nowy rozmiar przycisków kolor z palety kolorów.

##  <a name="setcolorname"></a>  CMFCRibbonColorButton::SetColorName

Określa nową nazwę dla określonego koloru.

```
static void __stdcall SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
[in] Wartość koloru RGB.

*strName*<br/>
[in] Nowa nazwa dla określonego koloru.

### <a name="remarks"></a>Uwagi

Ponieważ wywołuje `CMFCColorBar::SetColorName`, ta metoda zmienia nazwę określonego koloru we wszystkich `CMFCColorBar` obiektów w aplikacji.

##  <a name="setcolumns"></a>  CMFCRibbonColorButton::SetColumns

Ustawia liczbę kolumn wyświetlanych w tabeli kolorów, które są prezentowane użytkownikowi podczas procesu wyboru koloru użytkownika.

```
void SetColumns(int nColumns);
```

### <a name="parameters"></a>Parametry

*nColumns*<br/>
[in] Liczba ikon koloru do wyświetlenia w każdym wierszu.

### <a name="remarks"></a>Uwagi

##  <a name="setdocumentcolors"></a>  CMFCRibbonColorButton::SetDocumentColors

Określa listę wartości RGB, aby wyświetlić w obszarze kolor dokumentu.

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Tekst, który można wyświetlić za pomocą kolorów dokumentu.

*lstColors*<br/>
[in] Odwołanie do listy wartości RGB.

##  <a name="setpalette"></a>  CMFCRibbonColorButton::SetPalette

Określa kolory standardowe do wyświetlenia w tabeli kolorów, która zawiera przycisk koloru.

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parametry

*pPalette*<br/>
[in] Wskaźnik do palety kolorów.

### <a name="remarks"></a>Uwagi

##  <a name="updatecolor"></a>  CMFCRibbonColorButton::UpdateColor

Wywoływane przez platformę, gdy użytkownik zaznaczy kolor z tabeli kolorów wyświetlane, gdy użytkownik kliknie przycisk koloru.

```
void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
[in] Kolor wybrany przez użytkownika.

### <a name="remarks"></a>Uwagi

`CMFCRibbonColorButton::UpdateColor` Metoda zmienia kolor aktualnie zaznaczonego przycisku i powiadamia o jego obiektu nadrzędnego, wysyłając wiadomość z powiadomieniem do standardowego BN_CLICKED WM_COMMAND. Użyj [CMFCRibbonColorButton::GetColor](#getcolor) metoda pobierania wybranego koloru.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)
