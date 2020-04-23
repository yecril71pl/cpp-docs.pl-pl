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
ms.openlocfilehash: dbf28787e0c0f7d89586fbf98632bd9172c12eed
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754155"
---
# <a name="cmfcribbonfontcombobox-class"></a>Klasa CMFCRibbonFontComboBox

Implementuje pole kombi zawierające listę czcionek. Pole kombi należy umieścić na panelu wstążki.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|Destruktora.|

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|Konstruuje i inicjuje `CMFCRibbonFontComboBox` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Wypełnia pole kombi czcionki wstążki czcionką czcionkami o określonym typie czcionki, zestawie znaków oraz wysokości i rodziny.|
|`CMFCRibbonFontComboBox::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|Zwraca określony zestaw znaków.|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|Zwraca typy czcionek do wyświetlenia w polu kombi. Prawidłowe opcje to DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE lub dowolna ich kombinacja bitowa.|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Zwraca wysokość i rodzinę czcionek wyświetlanych w polu kombi.|
|`CMFCRibbonFontComboBox::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Wypełnia pole kombi czcionki wstążki czcionką czcionkami o wcześniej określonym typie czcionki, zestawie znaków oraz wysokości i rodzinie.|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Wybiera określoną czcionkę w polu kombi.|

## <a name="remarks"></a>Uwagi

Po utworzeniu `CMFCRibbonFontComboBox` obiektu dodaj go do panelu wstążki, wywołując [polecenie CMFCRibbonPanel::Dodaj](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[Cmfcribbonedit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonComboBox.h

## <a name="cmfcribbonfontcomboboxbuildfonts"></a><a name="buildfonts"></a>CMFCRibbonFontComboBox::BuildFonts

Wypełnia pole kombi na wstążce czcionkami.

```cpp
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>Parametry

*nFontType (typ nFontType)*<br/>
[w] Określa typ czcionki do dodania.

*nCharSet (Zestaw chybianie)*<br/>
[w] Określa zestaw znaków czcionek do dodania.

*nPitchAndRodzina*<br/>
[w] Określa wysokość i rodzinę czcionek do dodania.

## <a name="cmfcribbonfontcomboboxcmfcribbonfontcombobox"></a><a name="cmfcribbonfontcombobox"></a>CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

Konstruuje i inicjuje [OBIEKT CMFCRibbonFontComboBox.](../../mfc/reference/cmfcribbonfontcombobox-class.md)

```
CMFCRibbonFontComboBox(
    UINT nID,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH,
    int nWidth = -1);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[w] Identyfikator polecenia polecenia, które jest wykonywane, gdy użytkownik wybiera element z pola kombi.

*nFontType (typ nFontType)*<br/>
[w] Określa typy czcionek, które mają być wyświetlane w polu kombi. Prawidłowe opcje to DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE lub dowolna ich kombinacja bitowa.

*nCharSet (Zestaw chybianie)*<br/>
[w] Filtruje czcionki w polu kombi do tych, które należą do określonego zestawu znaków..

*nPitchAndRodzina*<br/>
[w] Określa wysokość i rodzinę czcionek wyświetlanych w polu kombi.

*nWidth (ww.*<br/>
[w] Określa szerokość pola kombi w pikselach.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat możliwych wartości *parametrów nFontType,* zobacz [EnumFontFamProc](/previous-versions/dd162621\(v=vs.85\)) w dokumentacji windows SDK.

Aby uzyskać więcej informacji na temat prawidłowych zestawów znaków, które można przypisać do *nCharSet*i prawidłowych wartości, które można przypisać do *nPitchAndFamily*, zobacz [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) w dokumentacji zestawu Windows SDK.

## <a name="cmfcribbonfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCRibbonFontComboBox::GetFontDesc

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>Parametry

[w] *iIndex*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonfontcomboboxrebuildfonts"></a><a name="rebuildfonts"></a>CMFCRibbonFontComboBox::RebuildFonts

Wypełnia pole kombi na wstążce czcionkami wcześniej określonego typu czcionki, zestawu znaków oraz skoku i rodziny.

```cpp
void RebuildFonts();
```

### <a name="remarks"></a>Uwagi

Można określić typ czcionki, zestaw znaków oraz wysokość i rodzinę czcionek, które mają być uwzględnione w polu kombi czcionki wstążki w [konstruktorze](#cmfcribbonfontcombobox) dla tej klasy, lub wywołując [polecenie CMFCRibbonFontComboBox::BuildFonts](#buildfonts).

## <a name="cmfcribbonfontcomboboxsetfont"></a><a name="setfont"></a>CMFCRibbonFontComboBox::SetFont

Wybiera określoną czcionkę w polu kombi.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>Parametry

'lpszName* Określa nazwę czcionki do wyboru.

*nCharSet (Zestaw chybianie)*<br/>
Określa zestaw znaków dla wybranej czcionki.

*bEkstycznie*<br/>
PRAWDA, aby określić, że zestaw znaków musi być zgodny podczas wybierania czcionki; FAŁSZ, aby określić, że zestaw znaków może być ignorowany podczas wybierania czcionki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli określona czcionka została znaleziona i wybrana; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonfontcomboboxgetcharset"></a><a name="getcharset"></a>CMFCRibbonFontComboBox::GetCharSet

Zwraca określony zestaw znaków.

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>Wartość zwracana

Zestaw znaków (zobacz LOGFONT w dokumentacji zestawu Windows SDK).

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonfontcomboboxgetfonttype"></a><a name="getfonttype"></a>CMFCRibbonFontComboBox::GetFontType

Zwraca typy czcionek do wyświetlenia w polu kombi. Prawidłowe opcje to DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE lub dowolna ich kombinacja bitowa.

```
int GetFontType() const;
```

### <a name="return-value"></a>Wartość zwracana

Typy czcionek (zobacz EnumFontFamProc w dokumentacji sdk systemu Windows).

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonfontcomboboxgetpitchandfamily"></a><a name="getpitchandfamily"></a>CMFCRibbonFontComboBox::GetPitchAndFamily

Zwraca wysokość i rodzinę czcionek wyświetlanych w polu kombi.

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>Wartość zwracana

Pitch i rodziny (zobacz LOGFONT w dokumentacji windows SDK).

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)
