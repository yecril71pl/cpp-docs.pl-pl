---
title: Klasa CMFCFontInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
dev_langs:
- C++
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9e4c1031ba06eaabe67418a018f95d689f71d1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368296"
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
|[CMFCFontInfo::GetFullName](#getfullname)|Pobiera połączonych nazwy czcionki i jej znak zestawu (skrypt).|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Wartość, która określa zestawu znaków (skrypt) skojarzone z czcionki.|  
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Wartość, która określa gęstość i rodzinę czcionek.|  
|[CMFCFontInfo::m_nType](#m_ntype)|Wartość, która określa typ czcionki.|  
|[CMFCFontInfo::m_strName](#m_strname)|Nazwa czcionki; na przykład **Arial**.|  
|[CMFCFontInfo::m_strScript](#m_strscript)|Nazwa zestawu znaków (skrypt) skojarzone z czcionki.|  
  
## <a name="remarks"></a>Uwagi  
 Możesz dołączyć `CMFCFontInfo` obiektu do elementu [klasy CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) klasy. Wywołanie [CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) metoda pobierania wskaźnik do `CMFCFontInfo` obiektu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych członkami `CMFCFontInfo` klasy. W przykładzie pokazano, jak uzyskać `CMFCFontInfo` obiekt z `CMFCRibbonFontComboBox`oraz sposób uzyskać dostępu do jego zmiennych lokalnych. Ten przykład jest częścią [próbka MSOffice 2007 Demo](../../visual-cpp-samples.md).  
  
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
 [in] `lpszName`  
 Nazwa czcionki. Aby uzyskać więcej informacji, zobacz `lfFaceName` członkiem [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury.  
  
 [in] `lpszScript`  
 Nazwa skryptu (zestaw znaków) czcionki.  
  
 [in] `nCharSet`  
 Wartość, która określa zestaw znaków (skrypt) czcionki. Aby uzyskać więcej informacji, zobacz `lfCharSet` członkiem [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury.  
  
 [in] `nPitchAndFamily`  
 Wartość, która określa gęstość i rodzinę czcionek. Aby uzyskać więcej informacji, zobacz `lfPitchAndFamily` członkiem [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury.  
  
 [in] `nType`  
 Wartość, która określa typ czcionki. Ten parametr może być bitowe połączenie (lub) DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE.  
  
 [in] `src`  
 Istniejące `CMFCFontInfo` obiektu, której członkami są używane do skonstruowania to `CMFCFontInfo` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Ta dokumentacja używa warunki *zestaw znaków* i *skryptu* zamiennie. A *skryptu*, który jest także znana jako system pisma, to zbiór znaków i zasady dotyczące pisania te znaki w co najmniej jeden język. Zbiór znaków obejmuje alfabetu i znaków interpunkcyjnych używane w tym skrypcie. Na przykład alfabetu łacińskiego skryptu jest używany dla języka angielskiego, ponieważ jest on używany w Stanach Zjednoczonych i alfabecie zawiera znaki od A do Z. `lfCharSet` Członkiem [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury określa zestaw znaków. Na przykład wartość `ANSI_CHARSET` Określa [!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)] zestawu znaków, w tym alfabetu łacińskiego skryptu.  
  
##  <a name="getfullname"></a>  CMFCFontInfo::GetFullName  
 Pobiera połączonych nazwy czcionki i jej znak zestawu (skrypt).  
  
```  
CString GetFullName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg zawierający nazwę czcionki i skrypt.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby uzyskać pełną nazwę czcionki. Na przykład, jeśli nazwa czcionki jest `Arial` oraz skrypt czcionki jest `Cyrillic`, ta metoda zwraca wartość "Arial (cyrylica)".  
  
##  <a name="m_ncharset"></a>  CMFCFontInfo::m_nCharSet  
 Wartość, która określa zestawu znaków (skrypt) skojarzone z czcionki.  
  
```  
const BYTE m_nCharSet;  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz `nCharSet` parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktora.  
  
##  <a name="m_npitchandfamily"></a>  CMFCFontInfo::m_nPitchAndFamily  
 Wartość, która określa gęstość (rozmiar czcionki) i rodzinę (na przykład serif, sans-serif i o stałej szerokości) czcionki.  
  
```  
const BYTE m_nPitchAndFamily;  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz `nPitchAndFamily` parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktora.  
  
##  <a name="m_ntype"></a>  CMFCFontInfo::m_nType  
 Wartość, która określa typ czcionki.  
  
```  
const int m_nType;  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz `nType` parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktora.  
  
##  <a name="m_strname"></a>  CMFCFontInfo::m_strName  
 Nazwa czcionki: na przykład **Arial**.  
  
```  
const CString m_strName;  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz `lpszName` parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktora.  
  
##  <a name="m_strscript"></a>  CMFCFontInfo::m_strScript  
 Nazwa zestawu znaków (skrypt) skojarzone z czcionki.  
  
```  
const CString m_strScript;  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz `lpszScript` parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktora.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [Klasa CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
