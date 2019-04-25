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
ms.openlocfilehash: 643e2a519c6d96c1070990dd86d571c5b7c09f95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237028"
---
# <a name="cmfcribbonfontcombobox-class"></a>Klasa CMFCRibbonFontComboBox

Implementuje pole kombi, która zawiera listę czcionek. Pole kombi jest umieścić na panelu wstążki.

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
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|Tworzy i inicjuje `CMFCRibbonFontComboBox` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Wypełnia wstążki pole kombi czcionki przy użyciu czcionki o określonej czcionki, zestaw znaków, a gęstość i rodzinę.|
|`CMFCRibbonFontComboBox::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|Zwraca wartość określonego zestawu znaków.|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|Zwraca typy czcionek, które do wyświetlenia w polu kombi. Prawidłowe opcje to DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE lub dowolne bitowe.|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Zwraca gęstość i rodzinę czcionek, które są wyświetlane w polu kombi.|
|`CMFCRibbonFontComboBox::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Wypełnia wstążki pole kombi czcionki przy użyciu czcionki o typ wcześniej określonej czcionki, zestaw znaków, a gęstość i rodzinę.|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Wybiera czcionkę określony w polu kombi.|

## <a name="remarks"></a>Uwagi

Po utworzeniu `CMFCRibbonFontComboBox` obiektu, dodaj go do panelu wstążki, wywołując [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonComboBox.h

##  <a name="buildfonts"></a>  CMFCRibbonFontComboBox::BuildFonts

Wypełnia pola kombi na Wstążce czcionek.

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>Parametry

*nFontType*<br/>
[in] Określa krój czcionki, aby dodać.

*nCharSet*<br/>
[in] Określa zestaw znaków czcionek, które można dodać.

*nPitchAndFamily*<br/>
[in] Określa gęstość i rodzinę czcionek, które można dodać.

##  <a name="cmfcribbonfontcombobox"></a>  CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

Tworzy i inicjuje [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md) obiektu.

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
[in] Identyfikator polecenia polecenia, który jest wykonywany, gdy użytkownik wybierze element z pola kombi.

*nFontType*<br/>
[in] Określa, które czcionki typów do wyświetlenia w polu kombi. Prawidłowe opcje to DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE lub dowolne bitowe.

*nCharSet*<br/>
[in] Filtry czcionek w polu kombi do tych, które należą do określonego zestawu znaków...

*nPitchAndFamily*<br/>
[in] Określa gęstość i rodzinę czcionek, które są wyświetlane w polu kombi.

*nWidth*<br/>
[in] Określa szerokość w pikselach, pola kombi.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o możliwych *nFontType* wartości parametrów, zobacz [EnumFontFamProc](https://msdn.microsoft.com/library/windows/desktop/dd162621) w dokumentacji zestawu Windows SDK.

Aby uzyskać więcej informacji na temat zestawów prawidłowych znaków, które mogą być przypisane do *nCharSet*i prawidłowe wartości, które mogą być przypisane do *nPitchAndFamily*, zobacz [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) w Dokumentacja zestawu Windows SDK.

##  <a name="getfontdesc"></a>  CMFCRibbonFontComboBox::GetFontDesc

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>Parametry

[in] *iIndex*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="rebuildfonts"></a>  CMFCRibbonFontComboBox::RebuildFonts

Wypełnia pole kombi na Wstążce czcionek typu wcześniej określonej czcionki, zestaw znaków, a gęstość i rodzinę.

```
void RebuildFonts();
```

### <a name="remarks"></a>Uwagi

Można określić typ czcionki, zestaw znaków, a gęstość i rodzinę czcionek, które mają zostać objęte kombi czcionki wstążki pole w [Konstruktor](#cmfcribbonfontcombobox) dla tej klasy lub przez wywołanie [CMFCRibbonFontComboBox::BuildFonts](#buildfonts).

##  <a name="setfont"></a>  CMFCRibbonFontComboBox::SetFont

Wybiera czcionkę określony w polu kombi.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>Parametry

"lpszName * Określa nazwę czcionki, aby wybrać.

*nCharSet*<br/>
Określa zestaw znaków dla wybranej czcionki.

*bExact*<br/>
Wartość TRUE, aby określić, że zestaw znaków musi odpowiadać podczas wybierania czcionek; Wartość FALSE, aby określić, że zestaw znaków, można zignorować, podczas wybierania czcionki.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli określona czcionka zostało znalezione i wybrano; w przeciwnym razie, wartość zero.

### <a name="remarks"></a>Uwagi

##  <a name="getcharset"></a>  CMFCRibbonFontComboBox::GetCharSet

Zwraca wartość określonego zestawu znaków.

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>Wartość zwracana

Zestaw znaków (zobacz LOGFONT w dokumentacji zestawu Windows SDK).

### <a name="remarks"></a>Uwagi

##  <a name="getfonttype"></a>  CMFCRibbonFontComboBox::GetFontType

Zwraca typy czcionek, które do wyświetlenia w polu kombi. Prawidłowe opcje to DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE lub dowolne bitowe.

```
int GetFontType() const;
```

### <a name="return-value"></a>Wartość zwracana

Typy czcionek (zobacz EnumFontFamProc w dokumentacji zestawu Windows SDK).

### <a name="remarks"></a>Uwagi

##  <a name="getpitchandfamily"></a>  CMFCRibbonFontComboBox::GetPitchAndFamily

Zwraca gęstość i rodzinę czcionek, które są wyświetlane w polu kombi.

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>Wartość zwracana

Gęstość i rodzinę (zobacz LOGFONT w dokumentacji zestawu Windows SDK).

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)
