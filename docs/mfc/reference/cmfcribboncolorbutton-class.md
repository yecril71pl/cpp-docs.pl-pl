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
ms.openlocfilehash: 528b883d75889589c7021f462324dd9dcb71be25
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754846"
---
# <a name="cmfcribboncolorbutton-class"></a>Klasa CMFCRibbonColorButton

Klasa `CMFCRibbonColorButton` implementuje przycisk koloru, który można dodać do paska wstążki. Przycisk koloru wstążki wyświetla menu rozwijane zawierające jedną lub więcej palet kolorów.

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
|[CMFCRibbonColorButton::AddColorsGroup](#addcolorsgroup)|Dodaje grupę kolorów do zwykłego obszaru kolorów.|
|[CMFCRibbonColorButton::EnableAutomaticButton](#enableautomaticbutton)|Określa, czy przycisk **Automatyczny** jest włączony.|
|[CMFCRibbonColorButton::EnableOtherButton](#enableotherbutton)|Włącza przycisk **Inne.**|
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||
|[CMFCRibbonColorButton::GetColor](#getcolor)|Zwraca aktualnie zaznaczony kolor.|
|[CMFCRibbonColorButton::GetColorBoxSize](#getcolorboxsize)|Zwraca rozmiar elementów kolorów wyświetlanych na pasku kolorów.|
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||
|[CMFCRibbonColorButton::GetHighlightedColor](#gethighlightedcolor)|Zwraca kolor aktualnie zaznaczonego elementu w palecie kolorów wyskakujących okienków.|
|[CMFCRibbonColorButton::RemoveAllColorGroups](#removeallcolorgroups)|Usuwa wszystkie grupy kolorów ze zwykłego obszaru kolorów.|
|[CMFCRibbonColorButton::SetColor](#setcolor)|Wybiera kolor ze zwykłego obszaru kolorów.|
|[CMFCRibbonColorButton::SetColorBoxSize](#setcolorboxsize)|Ustawia rozmiar wszystkich elementów kolorów wyświetlanych na pasku kolorów.|
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||
|[CMFCRibbonColorButton::SetDocumentColors](#setdocumentcolors)|Określa listę wartości RGB wyświetlanych w obszarze koloru dokumentu.|
|[CMFCRibbonColorButton::SetPalette](#setpalette)||
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||

## <a name="remarks"></a>Uwagi

Przycisk koloru wstążki wyświetla pasek kolorów, gdy użytkownik go naciśnie. Domyślnie ten pasek kolorów zawiera paletę wyboru kolorów zwaną zwykłym obszarem kolorów. Opcjonalnie na pasku kolorów można wyświetlić przycisk **Automatyczny,** który umożliwia użytkownikowi wybranie domyślnego koloru, oraz przycisk **Inne,** który wyświetla wyskakujących paletę kolorów zawierającą dodatkowe kolory.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCRibbonColorButton` używać różnych metod w klasie. W przykładzie pokazano, `CMFCRibbonColorButton` jak skonstruować obiekt, ustawić duży obraz, włączyć przycisk **Automatyczny,** włączyć przycisk **Inne,** ustawić liczbę kolumn, ustawić rozmiar wszystkich elementów kolorów wyświetlanych na pasku kolorów, dodać grupę kolorów do zwykłego obszaru kolorów i określić listę wartości RGB do wyświetlenia w obszarze koloru dokumentu. Ten fragment kodu jest częścią [próbki Klienta rysowania](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGaleria](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribboncolorbutton.h

## <a name="cmfcribboncolorbuttonaddcolorsgroup"></a><a name="addcolorsgroup"></a>CMFCRibbonColorButton::AddColorsGroup

Dodaje grupę kolorów do zwykłego obszaru kolorów.

```cpp
void AddColorsGroup(
    LPCTSTR lpszName,
    const CList<COLORREF,COLORREF>& lstColors,
    BOOL bContiguousColumns=FALSE);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
[w] Nazwa grupy.

*lstKolory*<br/>
[w] Lista kolorów.

*bKontytowanie*<br/>
[w] Określa sposób wyświetlania elementów kolorów w grupie. Jeśli wartość TRUE, elementy koloru są rysowane bez odstępów pionowych. Jeśli FAŁDa, elementy koloru są rysowane z pionowymi odstępami.

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia wyświetlenie wyskakujące okienka kolorów kilkoma grupami kolorów. Można kontrolować sposób wyświetlania kolorów w grupie.

## <a name="cmfcribboncolorbuttoncmfcribboncolorbutton"></a><a name="cmfcribboncolorbutton"></a>CMFCRibbonColorButton::CMFCRibbonColorButton

Konstruuje `CMFCRibbonColorButton` obiekt.

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

*Nid*<br/>
[w] Określa identyfikator polecenia polecenia do wykonania, gdy użytkownik kliknie przycisk.

*lpszText (tekst)*<br/>
[w] Określa tekst wyświetlany na przycisku.

*nSmallImageIndex*<br/>
[w] Indeks od zera małego obrazu, który ma być wyświetlany na przycisku.

*color*<br/>
[w] Kolor przycisku (domyślnie czarny).

*bProspojbuttonLook*<br/>
[w] Jeśli true, przycisk jest rysowany jako prosty prostokąt.

*nLargeImageIndex*<br/>
[w] Indeks od zera dużego obrazu, który ma być wyświetlany na przycisku.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCRibbonColorButton::EnableAutomaticButton

Określa, czy przycisk **Automatyczny** jest włączony.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE,
    LPCTSTR lpszToolTip=NULL,
    BOOL bOnTop=TRUE,
    BOOL bDrawBorder=FALSE);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
[w] Etykieta przycisku **Automatyczna.**

*kolorAutomatyczny*<br/>
[w] Wartość RGB określająca domyślny kolor przycisku **Automatyczny.**

*bWłaszą*<br/>
[w] PRAWDA, jeśli przycisk **Automatyczny** jest włączony; FAŁSZ, jeśli jest wyłączony.

*lpszToolTip*<br/>
[w] Etykietka narzędzia przycisku **Automatyczne.**

*bOnTop*<br/>
[w] Określa, czy przycisk **Automatyczny** znajduje się u góry, przed paletą kolorów.

*bDrawBorder*<br/>
[w] PRAWDA, jeśli aplikacja rysuje obramowanie wokół paska kolorów na przycisku koloru wstążki. Pasek kolorów wyświetla aktualnie wybrany kolor. FAŁSZ, jeśli aplikacja nie rysuje obramowania

## <a name="cmfcribboncolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCRibbonColorButton::EnableOtherButton

Włącza przycisk **Inne.**

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    LPCTSTR lpszToolTip=NULL);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
Etykieta przycisku.

*lpszToolTip*<br/>
Tekst etykietki narzędzia dla przycisku **Inne.**

### <a name="remarks"></a>Uwagi

**Przycisk Inne** to przycisk wyświetlany poniżej grupy kolorów. Gdy użytkownik kliknie przycisk **Inne,** zostanie wyświetlone okno dialogowe koloru.

## <a name="cmfcribboncolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCRibbonColorButton::GetAutomaticColor

Pobiera bieżący kolor przycisku automatycznego.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość koloru RGB reprezentująca bieżący kolor przycisku automatycznego.

### <a name="remarks"></a>Uwagi

Kolor przycisku automatycznego jest `colorAutomatic` ustawiany `CMFCRibbonColorButton::EnableAutomaticButton` przez parametr przekazany do metody.

## <a name="cmfcribboncolorbuttongetcolor"></a><a name="getcolor"></a>CMFCRibbonColorButton::GetColor

Zwraca aktualnie zaznaczony kolor.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolor wybrany przez kliknięcie przycisku.

## <a name="cmfcribboncolorbuttongetcolorboxsize"></a><a name="getcolorboxsize"></a>CMFCRibbonColorButton::GetColorBoxSize

Zwraca rozmiar elementów kolorów wyświetlanych na pasku kolorów.

```
CSize GetColorBoxSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar przycisków kolorów w rozwijanej palecie kolorów.

## <a name="cmfcribboncolorbuttongetcolumns"></a><a name="getcolumns"></a>CMFCRibbonColorButton::GetColumns

Pobiera liczbę elementów w wierszu wyświetlania galerii przycisku koloru wstążki.

```
int GetColumns() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę ikon w każdym wierszu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncolorbuttongethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFCRibbonColorButton::GetHighlightedColor

Zwraca kolor aktualnie zaznaczonego elementu na wyskakującym palecie kolorów.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolor aktualnie wybranego elementu na wyskakującym palecie kolorów.

## <a name="cmfcribboncolorbuttonremoveallcolorgroups"></a><a name="removeallcolorgroups"></a>CMFCRibbonColorButton::RemoveAllColorGroups

Usuwa wszystkie grupy kolorów ze zwykłego obszaru kolorów.

```cpp
void RemoveAllColorGroups();
```

## <a name="cmfcribboncolorbuttonsetcolor"></a><a name="setcolor"></a>CMFCRibbonColorButton::SetColor

Wybiera kolor ze zwykłego obszaru kolorów.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[w] Kolor do ustawionego.

## <a name="cmfcribboncolorbuttonsetcolorboxsize"></a><a name="setcolorboxsize"></a>CMFCRibbonColorButton::SetColorBoxSize

Ustawia rozmiar wszystkich elementów kolorów wyświetlanych na pasku kolorów.

```cpp
void SetColorBoxSize(CSize sizeBox);
```

### <a name="parameters"></a>Parametry

*sizeBox (skrzynka rozmiar)*<br/>
[w] Nowy rozmiar przycisków kolorów w palecie kolorów.

## <a name="cmfcribboncolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFCRibbonColorButton::SetColorName

Ustawia nową nazwę dla określonego koloru.

```
static void __stdcall SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[w] Wartość RGB koloru.

*nazwa strName*<br/>
[w] Nowa nazwa określonego koloru.

### <a name="remarks"></a>Uwagi

Ponieważ wywołuje, `CMFCColorBar::SetColorName`ta metoda zmienia nazwę określonego `CMFCColorBar` koloru we wszystkich obiektach w aplikacji.

## <a name="cmfcribboncolorbuttonsetcolumns"></a><a name="setcolumns"></a>CMFCRibbonColorButton::SetColumns

Ustawia liczbę kolumn wyświetlanych w tabeli kolorów, która jest prezentowana użytkownikowi podczas procesu wyboru kolorów użytkownika.

```cpp
void SetColumns(int nColumns);
```

### <a name="parameters"></a>Parametry

*nKolumny*<br/>
[w] Liczba ikon kolorów wyświetlanych w każdym wierszu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCRibbonColorButton::SetDocumentColors

Określa listę wartości RGB wyświetlanych w obszarze koloru dokumentu.

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
[w] Tekst, który ma być wyświetlany z kolorami dokumentu.

*lstKolory*<br/>
[w] Odwołanie do listy wartości RGB.

## <a name="cmfcribboncolorbuttonsetpalette"></a><a name="setpalette"></a>CMFCRibbonColorButton::SetPalette

Określa kolory standardowe wyświetlane w tabeli kolorów wyświetlanej przez przycisk koloru.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parametry

*pPalette (ppalette)*<br/>
[w] Wskaźnik do palety kolorów.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFCRibbonColorButton::UpdateColor

Wywoływana przez strukturę, gdy użytkownik wybiera kolor z tabeli kolorów wyświetlanej, gdy użytkownik kliknie przycisk koloru.

```cpp
void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[w] Kolor wybrany przez użytkownika.

### <a name="remarks"></a>Uwagi

Metoda `CMFCRibbonColorButton::UpdateColor` zmienia kolor aktualnie wybranego przycisku i powiadamia jego element nadrzędny, wysyłając wiadomość WM_COMMAND z BN_CLICKED standardowym powiadomieniem. Użyj [CMFCRibbonColorButton::GetColor](#getcolor) metody, aby pobrać wybrany kolor.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)
