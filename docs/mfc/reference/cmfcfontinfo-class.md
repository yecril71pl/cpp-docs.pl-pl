---
title: Klasa CMFCFontInfo
ms.date: 11/04/2016
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
ms.openlocfilehash: a27606b494b13cd7b50f01b38fa95a918bacc7aa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505278"
---
# <a name="cmfcfontinfo-class"></a>Klasa CMFCFontInfo

`CMFCFontInfo` Klasa opisuje nazwę i inne atrybuty czcionki.

## <a name="syntax"></a>Składnia

```
class CMFCFontInfo : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCFontInfo`|Konstruuje `CMFCFontInfo` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCFontInfo:: getfullname](#getfullname)|Pobiera połączone nazwy czcionki i jej zestawu znaków (skrypt).|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Wartość określająca zestaw znaków (skrypt) skojarzony z czcionką.|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Wartość określająca gęstość i rodzinę czcionki.|
|[CMFCFontInfo::m_nType](#m_ntype)|Wartość, która określa typ czcionki.|
|[CMFCFontInfo::m_strName](#m_strname)|Nazwa czcionki; na przykład **Arial**.|
|[CMFCFontInfo::m_strScript](#m_strscript)|Nazwa zestawu znaków (skrypt) skojarzonego z czcionką.|

## <a name="remarks"></a>Uwagi

Można dołączyć `CMFCFontInfo` obiekt do elementu klasy [klasy CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) . Wywołaj metodę [CMFCToolBarFontComboBox:: GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) , aby pobrać wskaźnik do `CMFCFontInfo` obiektu.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać różnych elementów członkowskich `CMFCFontInfo` klasy. W przykładzie pokazano `CMFCFontInfo` `CMFCRibbonFontComboBox`, jak uzyskać obiekt z i, jak uzyskać dostęp do zmiennych lokalnych. Ten przykład jest częścią przykładu demonstracyjnego na [MSOffice 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbarfontcombobox. h

##  <a name="cmfcfontinfo"></a>CMFCFontInfo::CMFCFontInfo

Konstruuje `CMFCFontInfo` obiekt.

```
CMFCFontInfo(
    LPCTSTR lpszName,
    LPCTSTR lpszScript,
    BYTE nCharSet,
    BYTE nPitchAndFamily,
    int nType);

CMFCFontInfo(const CMFCFontInfo& src);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
podczas Nazwa czcionki. Aby uzyskać więcej informacji, zobacz `lfFaceName` element członkowski struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*lpszScript*<br/>
podczas Nazwa skryptu (zestawu znaków) czcionki.

*nCharSet*<br/>
podczas Wartość określająca zestaw znaków (skrypt) czcionki. Aby uzyskać więcej informacji, zobacz `lfCharSet` element członkowski struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*nPitchAndFamily*<br/>
podczas Wartość określająca gęstość i rodzinę czcionki. Aby uzyskać więcej informacji, zobacz `lfPitchAndFamily` element członkowski struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*Npowiadomienia*<br/>
podczas Wartość, która określa typ czcionki. Ten parametr może być kombinacją bitową (lub) z DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE.

*SRC*<br/>
podczas Istniejący `CMFCFontInfo` obiekt, którego członkowie są używani do konstruowania tego `CMFCFontInfo` obiektu.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

W tej dokumentacji zastosowano *zestaw znaków* terminów i *skrypt* zamiennie. *Skrypt*, który jest również znany jako system pisania, to kolekcja znaków i zasad służących do pisania tych znaków w jednym lub kilku językach. Kolekcja znaków zawiera alfabet i interpunkcję używaną w tym skrypcie. Na przykład skrypt łaciński jest używany w języku angielskim, ponieważ jest mówiony w Stany Zjednoczone, a jego alfabet zawiera znaki od A do Z. Element członkowski struktury LOGFONT określa zestaw znaków. [](/windows/win32/api/wingdi/ns-wingdi-logfontw) `lfCharSet` Na przykład wartość ANSI_CHARSET określa zestaw znaków ANSI, który zawiera alfabet łacińskiego skryptu.

##  <a name="getfullname"></a>CMFCFontInfo:: getfullname

Pobiera połączone nazwy czcionki i jej zestawu znaków (skrypt).

```
CString GetFullName() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg, który zawiera nazwę czcionki i skrypt.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby uzyskać pełną nazwę czcionki. Na przykład jeśli nazwa czcionki jest czcionką **Arial** , a skrypt czcionki to **cyrylica**, Metoda ta zwraca czcionkę Arial (cyrylica).

##  <a name="m_ncharset"></a>CMFCFontInfo::m_nCharSet

Wartość określająca zestaw znaków (skrypt) skojarzony z czcionką.

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz parametr *nCharSet* konstruktora [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_npitchandfamily"></a>CMFCFontInfo::m_nPitchAndFamily

Wartość określająca gęstość (rozmiar punktu) i rodzinę (na przykład szeryfową, sans-serif i znak) czcionki.

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz parametr *nPitchAndFamily* konstruktora [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_ntype"></a>CMFCFontInfo::m_nType

Wartość, która określa typ czcionki.

```
const int m_nType;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz parametr *npowiadomienia* konstruktora [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_strname"></a>CMFCFontInfo::m_strName

Nazwa czcionki: na przykład **Arial**.

```
const CString m_strName;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz parametr *lpszName* konstruktora [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_strscript"></a>CMFCFontInfo::m_strScript

Nazwa zestawu znaków (skrypt) skojarzonego z czcionką.

```
const CString m_strScript;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz parametr *lpszScript* konstruktora [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[Klasa CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
