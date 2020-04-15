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
ms.openlocfilehash: 6e87971e2afefc9cf1574abe951920c254dcd2ae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367483"
---
# <a name="cmfcfontinfo-class"></a>Klasa CMFCFontInfo

Klasa `CMFCFontInfo` opisuje nazwę i inne atrybuty czcionki.

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
|[CMFCFontInfo::GetFullName](#getfullname)|Pobiera połączone nazwy czcionki i jej zestaw znaków (skrypt).|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Wartość określająca zestaw znaków (skrypt) skojarzony z czcionką.|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Wartość określająca wysokość i rodzinę czcionki.|
|[CMFCFontInfo::m_nType](#m_ntype)|Wartość określająca typ czcionki.|
|[CMFCFontInfo::m_strName](#m_strname)|Nazwa czcionki; na przykład **Arial**.|
|[CMFCFontInfo::m_strScript](#m_strscript)|Nazwa zestawu znaków (skryptu) skojarzonego z czcionką.|

## <a name="remarks"></a>Uwagi

Obiekt można `CMFCFontInfo` dołączyć do elementu klasy [CMFCToolBarFontComboBox.](../../mfc/reference/cmfctoolbarfontcombobox-class.md) Wywołanie [CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) metody, aby pobrać `CMFCFontInfo` wskaźnik do obiektu.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCFontInfo` używać różnych członków klasy. W przykładzie pokazano, `CMFCFontInfo` jak uzyskać `CMFCRibbonFontComboBox`obiekt z programu i jak uzyskać dostęp do jego zmiennych lokalnych. W tym przykładzie jest częścią [msoffice 2007 Demo próbki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbarfontcombobox.h

## <a name="cmfcfontinfocmfcfontinfo"></a><a name="cmfcfontinfo"></a>CMFCFontInfo::CMFCFontInfo

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

*Lpszname*<br/>
[w] Nazwa czcionki. Aby uzyskać więcej `lfFaceName` informacji, zobacz element członkowski struktury [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*lpszScript*<br/>
[w] Nazwa skryptu (zestawu znaków) czcionki.

*nCharSet (Zestaw chybianie)*<br/>
[w] Wartość określająca zestaw znaków (skrypt) czcionki. Aby uzyskać więcej `lfCharSet` informacji, zobacz element członkowski struktury [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*nPitchAndRodzina*<br/>
[w] Wartość określająca wysokość i rodzinę czcionki. Aby uzyskać więcej `lfPitchAndFamily` informacji, zobacz element członkowski struktury [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*nTyp*<br/>
[w] Wartość określająca typ czcionki. Ten parametr może być kombinacją bitową (OR) DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE.

*src*<br/>
[w] Istniejący `CMFCFontInfo` obiekt, którego elementy `CMFCFontInfo` członkowskie są używane do konstruowania tego obiektu.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

W tej dokumentacji użyto *terminów zestaw znaków* i *skrypt* zamiennie. Skrypt *script*, który jest również znany jako system pisania, jest zbiorem znaków i reguł pisania tych znaków w jednym lub kilku językach. Kolekcja znaków zawiera alfabet i znaki interpunkcyjne używane w tym skrypcie. Na przykład skrypt łaciński jest używany w języku angielskim, ponieważ jest używany w Stanach Zjednoczonych, a jego alfabet zawiera znaki od A do Z. Element `lfCharSet` członkowski struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) określa zestaw znaków. Na przykład wartość ANSI_CHARSET określa zestaw znaków ANSI, który zawiera alfabet skryptu łacińskiego.

## <a name="cmfcfontinfogetfullname"></a><a name="getfullname"></a>CMFCFontInfo::GetFullName

Pobiera połączone nazwy czcionki i jej zestaw znaków (skrypt).

```
CString GetFullName() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg zawierający nazwę czcionki i skrypt.

### <a name="remarks"></a>Uwagi

Ta metoda służy do uzyskania pełnej nazwy czcionki. Na przykład, jeśli nazwa czcionki to **Arial,** a skrypt czcionki jest **cyrylicą,** ta metoda zwraca "Arial (cyrylica)".

## <a name="cmfcfontinfom_ncharset"></a><a name="m_ncharset"></a>CMFCFontInfo::m_nCharSet

Wartość określająca zestaw znaków (skrypt) skojarzony z czcionką.

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz *parametr nCharSet* konstruktora [CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="cmfcfontinfom_npitchandfamily"></a><a name="m_npitchandfamily"></a>CMFCFontInfo::m_nPitchAndFamily

Wartość określająca wysokość (rozmiar punktu) i rodzinę (na przykład szeryfową, bezszeryfową i monoprzestrzeń) czcionki.

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz *nPitchAndFamily* parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktora.

## <a name="cmfcfontinfom_ntype"></a><a name="m_ntype"></a>CMFCFontInfo::m_nType

Wartość określająca typ czcionki.

```
const int m_nType;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz *parametr nType* konstruktora [CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="cmfcfontinfom_strname"></a><a name="m_strname"></a>CMFCFontInfo::m_strName

Nazwa czcionki: na przykład **Arial**.

```
const CString m_strName;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz *parametr lpszName* konstruktora [CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="cmfcfontinfom_strscript"></a><a name="m_strscript"></a>CMFCFontInfo::m_strScript

Nazwa zestawu znaków (skryptu) skojarzonego z czcionką.

```
const CString m_strScript;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz parametr *lpszScript* konstruktora [CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[Klasa CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
