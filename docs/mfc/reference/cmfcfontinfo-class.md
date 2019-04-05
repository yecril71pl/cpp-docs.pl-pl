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
ms.openlocfilehash: 930aceb4514195f0e844c35d326b52d9cd8d31fa
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781331"
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
|`CMFCFontInfo`|Konstruuje `CMFCFontInfo` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCFontInfo::GetFullName](#getfullname)|Pobiera nazwy połączonych czcionkę i jej znak zestawu (skrypt).|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Wartość, która określa zestaw znaków (skrypt) skojarzony z czcionki.|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Wartość, która określa gęstość i rodzinę czcionek.|
|[CMFCFontInfo::m_nType](#m_ntype)|Wartość, która określa typ czcionki.|
|[CMFCFontInfo::m_strName](#m_strname)|Nazwa czcionki; na przykład **Arial**.|
|[CMFCFontInfo::m_strScript](#m_strscript)|Nazwa zestawu znaków (skrypt) skojarzony z czcionki.|

## <a name="remarks"></a>Uwagi

Możesz dołączyć `CMFCFontInfo` obiektu do elementu [klasa CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) klasy. Wywołaj [CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) metodę, aby pobrać wskaźnika do `CMFCFontInfo` obiektu.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać różnych członków `CMFCFontInfo` klasy. W przykładzie pokazano, jak uzyskać `CMFCFontInfo` obiektu z `CMFCRibbonFontComboBox`i jak uzyskać dostęp do jego zmiennych lokalnych. W tym przykładzie jest częścią [próbka MSOffice 2007 Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbarfontcombobox.h

##  <a name="cmfcfontinfo"></a>  CMFCFontInfo::CMFCFontInfo

Konstruuje `CMFCFontInfo` obiektu.

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
[in] Nazwa czcionki. Aby uzyskać więcej informacji, zobacz `lfFaceName` członkiem [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) struktury.

*lpszScript*<br/>
[in] Nazwa skryptu (zestaw znaków) czcionki.

*nCharSet*<br/>
[in] Wartość, która określa zestaw znaków (skrypt) czcionki. Aby uzyskać więcej informacji, zobacz `lfCharSet` członkiem [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) struktury.

*nPitchAndFamily*<br/>
[in] Wartość, która określa gęstość i rodzinę czcionek. Aby uzyskać więcej informacji, zobacz `lfPitchAndFamily` członkiem [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) struktury.

*nType*<br/>
[in] Wartość, która określa typ czcionki. Ten parametr może być bitowa kombinacja (lub) DEVICE_FONTTYPE RASTER_FONTTYPE i TRUETYPE_FONTTYPE.

*src*<br/>
[in] Istniejące `CMFCFontInfo` obiektu, której członkami są używane do konstruowania to `CMFCFontInfo` obiektu.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Ta dokumentacja używa warunki *zestaw znaków* i *skryptu* zamiennie. A *skryptu*, który jest również nazywany systemem zapisu to zbiór znaków i zasady dotyczące pisania te znaki w co najmniej jeden język. Zbiór znaków obejmują alfabetu i znaków interpunkcyjnych, używany w tym skrypcie. Na przykład łacińskim jest używany w języku angielskim, jak jest używany w Stanach Zjednoczonych, a jego alfabetu zawiera znaki od A do Z. `lfCharSet` Członkiem [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) struktury określa zestaw znaków. Na przykład wartość ANSI_CHARSET określa zestawu znaków ANSI, który zawiera alfabecie łacińskim.

##  <a name="getfullname"></a>  CMFCFontInfo::GetFullName

Pobiera nazwy połączonych czcionkę i jej znak zestawu (skrypt).

```
CString GetFullName() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg, który zawiera nazwę czcionki i skryptów.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby uzyskać pełną nazwę czcionki. Na przykład, jeśli nazwa czcionki **Arial** oraz skrypt czcionka jest **cyrylica**, ta metoda zwraca wartość "Arial (cyrylica)".

##  <a name="m_ncharset"></a>  CMFCFontInfo::m_nCharSet

Wartość, która określa zestaw znaków (skrypt) skojarzony z czcionki.

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz *nCharSet* parametru [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktora.

##  <a name="m_npitchandfamily"></a>  CMFCFontInfo::m_nPitchAndFamily

Wartość, która określa gęstość (w punktach) i rodzinę (na przykład serif, sans-serif i o stałej szerokości) czcionki.

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz *nPitchAndFamily* parametru [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktora.

##  <a name="m_ntype"></a>  CMFCFontInfo::m_nType

Wartość, która określa typ czcionki.

```
const int m_nType;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz *nNie* parametru [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktora.

##  <a name="m_strname"></a>  CMFCFontInfo::m_strName

Nazwa czcionki: na przykład **Arial**.

```
const CString m_strName;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz *lpszName* parametru [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktora.

##  <a name="m_strscript"></a>  CMFCFontInfo::m_strScript

Nazwa zestawu znaków (skrypt) skojarzony z czcionki.

```
const CString m_strScript;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz *lpszScript* parametru [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktora.

## <a name="see-also"></a>Zobacz także

[Diagram hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox Class](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
