---
title: Klasa CMFCRibbonFontComboBox
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
ms.openlocfilehash: 186c4bc3e1b26529ed0e000d2893e1b2d81c4304
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504959"
---
# <a name="cmfcribbonfontcombobox-class"></a>Klasa CMFCRibbonFontComboBox

Implementuje pole kombi, które zawiera listę czcionek. Pole kombi jest umieszczane na panelu wstążki.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|Destruktor.|

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|Konstruuje i inicjuje `CMFCRibbonFontComboBox` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Wypełnia pole kombi czcionki wstążki przy użyciu czcionek o określonym typie czcionki, zestawie znaków oraz skoku i rodziny.|
|`CMFCRibbonFontComboBox::CreateObject`|Używane przez platformę do tworzenia wystąpienia dynamicznego tego typu klasy.|
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|Zwraca określony zestaw znaków.|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox:: getfonttype](#getfonttype)|Zwraca typy czcionek, które mają być wyświetlane w polu kombi. Prawidłowe opcje to DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE lub ich kombinacji bitowe.|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Zwraca gęstość i rodzinę czcionek, które są wyświetlane w polu kombi.|
|`CMFCRibbonFontComboBox::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Wypełnia pole kombi czcionki wstążki przy użyciu czcionek poprzednio określonego typu czcionki, zestawu znaków oraz skoku i rodziny.|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Wybiera określoną czcionkę w polu kombi.|

## <a name="remarks"></a>Uwagi

Po utworzeniu `CMFCRibbonFontComboBox` obiektu Dodaj go do panelu wstążki przez wywołanie [CMFCRibbonPanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribboncombobox. h

##  <a name="buildfonts"></a>  CMFCRibbonFontComboBox::BuildFonts

Wypełnia pole kombi na Wstążce przy użyciu czcionek.

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>Parametry

*nFontType*<br/>
podczas Określa typ czcionki do dodania.

*nCharSet*<br/>
podczas Określa zestaw znaków czcionek do dodania.

*nPitchAndFamily*<br/>
podczas Określa gęstość i rodzinę czcionek do dodania.

##  <a name="cmfcribbonfontcombobox"></a>CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

Tworzy i inicjuje obiekt [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md) .

```
CMFCRibbonFontComboBox(
    UINT nID,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH,
    int nWidth = -1);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
podczas Identyfikator polecenia polecenia, które jest wykonywane, gdy użytkownik wybierze element z pola kombi.

*nFontType*<br/>
podczas Określa typy czcionek, które mają być wyświetlane w polu kombi. Prawidłowe opcje to DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE lub ich kombinacji bitowe.

*nCharSet*<br/>
podczas Filtruje czcionki w polu kombi do tych, które należą do określonego zestawu znaków..

*nPitchAndFamily*<br/>
podczas Określa gęstość i rodzinę czcionek, które są wyświetlane w polu kombi.

*nWidth*<br/>
podczas Określa szerokość pola kombi (w pikselach).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat możliwych wartości parametrów *nFontType* , zobacz [EnumFontFamProc](/previous-versions/dd162621\(v=vs.85\)) w dokumentacji Windows SDK.

Aby uzyskać więcej informacji na temat prawidłowych zestawów znaków, które można przypisać do *nCharSet*i prawidłowych wartości, które można przypisać do *NPitchAndFamily*, zobacz [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) w dokumentacji Windows SDK.

##  <a name="getfontdesc"></a>CMFCRibbonFontComboBox::GetFontDesc

Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>Parametry

podczas *IIndex*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="rebuildfonts"></a>CMFCRibbonFontComboBox::RebuildFonts

Wypełnia pole kombi na Wstążce przy użyciu czcionek poprzednio określonego typu czcionki, zestawu znaków oraz skoku i rodziny.

```
void RebuildFonts();
```

### <a name="remarks"></a>Uwagi

Można określić typ czcionki, zestaw znaków oraz gęstość i rodzinę czcionek do uwzględnienia w polu kombi czcionki wstążki w konstruktorze dla tej klasy [](#cmfcribbonfontcombobox) lub przez wywołanie [CMFCRibbonFontComboBox:: BuildFonts](#buildfonts).

##  <a name="setfont"></a>CMFCRibbonFontComboBox:: SetFont

Wybiera określoną czcionkę w polu kombi.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>Parametry

"lpszName *" określa nazwę czcionki do wybrania.

*nCharSet*<br/>
Określa zestaw znaków dla wybranej czcionki.

*bExact*<br/>
PRAWDA, aby określić, że zestaw znaków musi być zgodny podczas wybierania czcionki; Wartość FALSE, aby określić, że zestaw znaków może być ignorowany podczas wybierania czcionki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli określona Czcionka została znaleziona i wybrana; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

##  <a name="getcharset"></a>CMFCRibbonFontComboBox:: getcharset

Zwraca określony zestaw znaków.

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>Wartość zwracana

Zestaw znaków (zobacz LOGFONT w dokumentacji Windows SDK).

### <a name="remarks"></a>Uwagi

##  <a name="getfonttype"></a>CMFCRibbonFontComboBox:: getfonttype

Zwraca typy czcionek, które mają być wyświetlane w polu kombi. Prawidłowe opcje to DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE lub ich kombinacji bitowe.

```
int GetFontType() const;
```

### <a name="return-value"></a>Wartość zwracana

Typy czcionek (zobacz EnumFontFamProc w dokumentacji Windows SDK).

### <a name="remarks"></a>Uwagi

##  <a name="getpitchandfamily"></a>CMFCRibbonFontComboBox::GetPitchAndFamily

Zwraca gęstość i rodzinę czcionek, które są wyświetlane w polu kombi.

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>Wartość zwracana

Gęstość i rodzina (zobacz LOGFONT w dokumentacji Windows SDK).

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)
