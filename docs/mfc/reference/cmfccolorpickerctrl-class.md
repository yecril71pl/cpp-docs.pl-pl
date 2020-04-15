---
title: Klasa CMFCColorPickerCtrl
ms.date: 11/19/2018
f1_keywords:
- CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SelectCellHexagon
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminanceBarWidth
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetOriginalColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetPalette
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetType
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::DrawCursor
helpviewer_keywords:
- CMFCColorPickerCtrl [MFC], CMFCColorPickerCtrl
- CMFCColorPickerCtrl [MFC], GetColor
- CMFCColorPickerCtrl [MFC], GetHLS
- CMFCColorPickerCtrl [MFC], GetHue
- CMFCColorPickerCtrl [MFC], GetLuminance
- CMFCColorPickerCtrl [MFC], GetSaturation
- CMFCColorPickerCtrl [MFC], SelectCellHexagon
- CMFCColorPickerCtrl [MFC], SetColor
- CMFCColorPickerCtrl [MFC], SetHLS
- CMFCColorPickerCtrl [MFC], SetHue
- CMFCColorPickerCtrl [MFC], SetLuminance
- CMFCColorPickerCtrl [MFC], SetLuminanceBarWidth
- CMFCColorPickerCtrl [MFC], SetOriginalColor
- CMFCColorPickerCtrl [MFC], SetPalette
- CMFCColorPickerCtrl [MFC], SetSaturation
- CMFCColorPickerCtrl [MFC], SetType
- CMFCColorPickerCtrl [MFC], DrawCursor
ms.assetid: b9bbd03c-beb0-4b55-9765-9985fd05e5dc
ms.openlocfilehash: c3c11db448ab31324367b7f314cd6bfe44c2e96d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367687"
---
# <a name="cmfccolorpickerctrl-class"></a>Klasa CMFCColorPickerCtrl

Klasa `CMFCColorPickerCtrl` zapewnia funkcjonalność formantu, który jest używany do wybierania kolorów.

## <a name="syntax"></a>Składnia

```
class CMFCColorPickerCtrl : public CButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](#cmfccolorpickerctrl)|Konstruuje `CMFCColorPickerCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorPickerCtrl::GetColor](#getcolor)|Pobiera kolor, który użytkownik wybierze.|
|[CMFCColorPickerCtrl::GetHLS](#gethls)|Pobiera wartości barwy, luminancji i nasycenia koloru wybranego przez użytkownika.|
|[CMFCColorPickerCtrl::GetHue](#gethue)|Pobiera składnik barwy koloru, który wybiera użytkownik.|
|[CMFCColorPickerCtrl::GetLuminance](#getluminance)|Pobiera składnik luminancji koloru, który użytkownik wybierze.|
|[CMFCColorPickerCtrl::GetSaturation](#getsaturation)|Pobiera składnik nasycenia koloru, który wybiera użytkownik.|
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|Ustawia bieżący kolor na kolor zdefiniowany przez określone składniki koloru RGB lub określony sześciokąt komórki.|
|[CMFCColorPickerCtrl::SetColor](#setcolor)|Ustawia bieżący kolor na określoną wartość koloru RGB.|
|[CMFCColorPickerCtrl::SetHLS](#sethls)|Ustawia bieżący kolor na określoną wartość koloru HLS.|
|[CMFCColorPickerCtrl::SetHue](#sethue)|Zmienia składnik barwy aktualnie wybranego koloru.|
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|Zmienia komponent luminancji aktualnie wybranego koloru.|
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|Ustawia szerokość paska luminancji w formancie selektora kolorów.|
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|Ustawia początkowy wybrany kolor.|
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|Ustawia bieżącą paletę kolorów.|
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|Zmienia składnik nasycenia aktualnie wybranego koloru.|
|[CMFCColorPickerCtrl::SetType](#settype)|Ustawia typ formantu selektora kolorów do wyświetlenia.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|Wywoływana przez strukturę przed kursorem, który wskazuje wybrany kolor jest wyświetlany.|

## <a name="remarks"></a>Uwagi

Kolory standardowe są wybierane z sześciokątnej palety kolorów, a kolory niestandardowe są wybierane z paska luminancji, gdzie kolory są określane za pomocą notacji czerwonej/zielonej/niebieskiej lub notacji barwy/satuaration/luminancji.

Poniższa ilustracja `CMFCColorPickerCtrl` przedstawia kilka obiektów.

![Okno dialogowe CMFCColorPickerCtrl](../../mfc/reference/media/colorpicker.png "Okno dialogowe CMFCColorPickerCtrl")

Obsługuje `CMFCColorPickerCtrl` dwie pary stylów. Style HEX i HEX_GREYSCALE są odpowiednie dla standardowego wyboru kolorów. Style PICKER i LUMINANCE są odpowiednie do niestandardowego wyboru kolorów.

Wykonaj następujące czynności, aby `CMFCColorPickerCtrl` włączyć formant do okna dialogowego:

1. Jeśli używasz **ClassWizard**, wstawić nowy kontrolka przycisku do szablonu okna dialogowego (ponieważ `CMFCColorPickerCtrl` klasa jest dziedziczona z `CButton` klasy).

1. Wstaw zmienną elementu członkowskiego skojarzoną z nowym kontrolką przycisku do klasy okna dialogowego. Następnie zmień typ `CButton` zmiennej z na `CMFCColorPickerCtrl`.

1. Wstaw `WM_INITDIALOG` program obsługi wiadomości dla klasy okna dialogowego. W programie obsługi ustaw typ, paletę i początkowy `CMFCColorPickerCtrl` wybrany kolor formantu.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, `CMFCColorPickerCtrl` jak skonfigurować obiekt `CMFCColorPickerCtrl` przy użyciu różnych metod w klasie. W przykładzie pokazano, jak ustawić typ formantu selektora i jak ustawić jego kolor, odcień, luminancję i nasycenie. Przykład jest częścią [próbki Nowe formanty](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cbutton](../../mfc/reference/cbutton-class.md)

[Cmfccolorpickerctrl](../../mfc/reference/cmfccolorpickerctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcolorpickerctrl.h

## <a name="cmfccolorpickerctrlcmfccolorpickerctrl"></a><a name="cmfccolorpickerctrl"></a>CMFCColorPickerCtrl::CMFCColorPickerCtrl

Konstruuje `CMFCColorPickerCtrl` obiekt.

```
CMFCColorPickerCtrl();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorpickerctrldrawcursor"></a><a name="drawcursor"></a>CMFCColorPickerCtrl::DrawCursor

Wywoływana przez strukturę przed kursorem, który wskazuje wybrany kolor jest wyświetlany.

```
virtual void DrawCursor(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[w] Określa prostokątny obszar wokół wybranego koloru.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, gdy trzeba zmienić kształt kursora, który wskazuje zaznaczony kolor.

## <a name="cmfccolorpickerctrlgetcolor"></a><a name="getcolor"></a>CMFCColorPickerCtrl::GetColor

Pobiera kolor, który użytkownik wybierze.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość RGB wybranego koloru.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorpickerctrlgethls"></a><a name="gethls"></a>CMFCColorPickerCtrl::GetHLS

Pobiera wartości barwy, luminancji i nasycenia koloru wybranego przez użytkownika.

```
void GetHLS(
    double* hue,
    double* luminance,
    double* saturation);
```

### <a name="parameters"></a>Parametry

*Hue*<br/>
[na zewnątrz] Wskaźnik do zmiennej typu dwukrotnie, która odbiera informacje o odcieniu.

*Luminancji*<br/>
[na zewnątrz] Wskaźnik do zmiennej typu dwukrotnie, która odbiera informacje o luminancji.

*Nasycenie*<br/>
[na zewnątrz] Wskaźnik do zmiennej typu dwukrotnie, która odbiera informacje o nasyceniu.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorpickerctrlgethue"></a><a name="gethue"></a>CMFCColorPickerCtrl::GetHue

Pobiera składnik barwy koloru, który wybiera użytkownik.

```
double GetHue() const;
```

### <a name="return-value"></a>Wartość zwracana

Składnik barwy wybranego koloru.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorpickerctrlgetluminance"></a><a name="getluminance"></a>CMFCColorPickerCtrl::GetLuminance

Pobiera składnik luminancji koloru, który użytkownik wybierze.

```
double GetLuminance() const;
```

### <a name="return-value"></a>Wartość zwracana

Komponent luminancji wybranego koloru.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorpickerctrlgetsaturation"></a><a name="getsaturation"></a>CMFCColorPickerCtrl::GetSaturation

Pobiera wartość nasycenia koloru wybranego przez użytkownika.

```
double GetSaturation() const;
```

### <a name="return-value"></a>Wartość zwracana

Składnik nasycenia wybranego koloru.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorpickerctrlselectcellhexagon"></a><a name="selectcellhexagon"></a>CMFCColorPickerCtrl::SelectCellHexagon

Ustawia bieżący kolor na kolor zdefiniowany przez określone składniki koloru RGB lub określony sześciokąt komórki.

```
void SelectCellHexagon(
    BYTE R,
    BYTE G,
    BYTE B);

BOOL SelectCellHexagon(
    int x,
    int y);
```

### <a name="parameters"></a>Parametry

*R*<br/>
[w] Komponent koloru czerwonego.

*G*<br/>
[w] Składnik koloru zielonego.

*B*<br/>
[w] Składnik koloru niebieskiego.

*X*<br/>
[w] Współrzędna x kursora, która wskazuje sześciokąt komórki.

*Y*<br/>
[w] Współrzędna y kursora, która wskazuje sześciokąt komórki.

### <a name="return-value"></a>Wartość zwracana

Drugie przeciążenie tej metody zawsze zwraca WARTOŚĆ FAŁSZ.

### <a name="remarks"></a>Uwagi

Pierwsze przeciążenie tej metody ustawia bieżący kolor na kolor odpowiadający określonym składnikom koloru czerwony, zielony i niebieski.

Drugie przeciążenie tej metody ustawia bieżący kolor na kolor sześciokąta komórki, który jest wskazyny przez określoną lokalizację kursora.

## <a name="cmfccolorpickerctrlsetcolor"></a><a name="setcolor"></a>CMFCColorPickerCtrl::SetColor

Ustawia bieżący kolor na określoną wartość koloru RGB.

```
void SetColor(COLORREF Color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
[w] Wartość koloru RGB.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorpickerctrlsethls"></a><a name="sethls"></a>CMFCColorPickerCtrl::SetHLS

Ustawia bieżący kolor na określoną wartość koloru HLS.

```
void SetHLS(
    double hue,
    double luminance,
    double saturation,
    BOOL bInvalidate=TRUE);
```

### <a name="parameters"></a>Parametry

*Hue*<br/>
[w] Wartość odcienia.

*Luminancji*<br/>
[w] Wartość luminancji.

*Nasycenie*<br/>
[w] Wartość nasycenia.

*bInvalidate*<br/>
[w] PRAWDA, aby wymusić aktualizację okna do nowego koloru; w przeciwnym razie FALSE. Wartość domyślna to PRAWDA.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorpickerctrlsethue"></a><a name="sethue"></a>CMFCColorPickerCtrl::SetHue

Zmienia barwę aktualnie wybranego koloru.

```
void SetHue(double Hue);
```

### <a name="parameters"></a>Parametry

*Hue*<br/>
[w] Wartość odcienia.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorpickerctrlsetluminance"></a><a name="setluminance"></a>CMFCColorPickerCtrl::SetLuminance

Zmienia luminancję aktualnie wybranego koloru.

```
void SetLuminance(double Luminance);
```

### <a name="parameters"></a>Parametry

*Luminancji*<br/>
[w] Wartość luminancji.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorpickerctrlsetluminancebarwidth"></a><a name="setluminancebarwidth"></a>CMFCColorPickerCtrl::SetLuminanceBarWidth

Ustawia szerokość paska luminancji w formancie selektora kolorów.

```
void SetLuminanceBarWidth(int w);
```

### <a name="parameters"></a>Parametry

*W*<br/>
[w] Szerokość paska luminancji mierzona w pikselach.

### <a name="remarks"></a>Uwagi

Ta metoda służy do zmieniania rozmiaru paska luminancji, który znajduje się na karcie **Niestandardowe** formantu selektora kolorów. Parametr *w* określa nową szerokość paska luminancji. Wartość szerokości jest ignorowana, jeśli przekracza trzy czwarte szerokości obszaru klienta.

## <a name="cmfccolorpickerctrlsetoriginalcolor"></a><a name="setoriginalcolor"></a>CMFCColorPickerCtrl::SetOriginalColor

Ustawia początkowy wybrany kolor.

```
void SetOriginalColor(COLORREF ref);
```

### <a name="parameters"></a>Parametry

*ref*<br/>
[w] Wartość koloru RGB.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, gdy formant selektora kolorów jest inicjowany.

## <a name="cmfccolorpickerctrlsetpalette"></a><a name="setpalette"></a>CMFCColorPickerCtrl::SetPalette

Ustawia bieżącą paletę kolorów.

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parametry

*pPalette (ppalette)*<br/>
[w] Wskaźnik do palety kolorów.

### <a name="remarks"></a>Uwagi

Paleta kolorów definiuje tablicę kolorów przedstawioną w formancie selektora kolorów.

## <a name="cmfccolorpickerctrlsetsaturation"></a><a name="setsaturation"></a>CMFCColorPickerCtrl::SetSaturation

Zmienia nasycenie aktualnie zaznaczonego koloru.

```
void SetSaturation(double Saturation);
```

### <a name="parameters"></a>Parametry

*Nasycenie*<br/>
[w] Wartość nasycenia.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorpickerctrlsettype"></a><a name="settype"></a>CMFCColorPickerCtrl::SetType

Ustawia typ formantu selektora kolorów do wyświetlenia.

```
void SetType(COLORTYPE colorType);
```

### <a name="parameters"></a>Parametry

*typ koloru*<br/>
[w] Typ formantu selektora kolorów.

Typy są definiowane przez wyliczenie. `CMFCColorPickerCtrl::COLORTYPE` Możliwe typy to LUMINANCE, PICKER, HEX i HEX_GREYSCALE. Domyślnym typem jest SELEKTOR.

### <a name="remarks"></a>Uwagi

Aby określić typ formantu selektora kolorów, należy wywołać tę metodę przed utworzeniem formantu systemu Windows.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)
