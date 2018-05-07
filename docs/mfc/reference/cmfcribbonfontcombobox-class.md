---
title: Klasa CMFCRibbonFontComboBox | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86a46614cdb61e39af1016e496b12518b87f59ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcribbonfontcombobox-class"></a>Klasa CMFCRibbonFontComboBox
Implementuje pola kombi, który zawiera listę czcionek. Umieszcza pole kombi na panelu wstążki.  
  
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
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Wypełnia wstążki pole kombi czcionki z czcionek z określonej czcionki, zestaw znaków i gęstość i rodzinę.|  
|`CMFCRibbonFontComboBox::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|Zwraca określonego zestawu znaków.|  
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||  
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|Zwraca typów czcionek, które mają być wyświetlane w polu kombi. Prawidłowe opcje to DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE lub dowolną ich kombinację bitowe.|  
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Zwraca gęstość i rodzinę czcionek, które są wyświetlane w polu kombi.|  
|`CMFCRibbonFontComboBox::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Wypełnia wstążki pole kombi czcionki z czcionek z wcześniej określonej czcionki, zestaw znaków i gęstość i rodzinę.|  
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Wybiera czcionkę określonej w polu kombi.|  
  
## <a name="remarks"></a>Uwagi  
 Po utworzeniu `CMFCRibbonFontComboBox` obiektów, dodaj go do panelu wstążki przez wywołanie metody [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
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
 Wypełnienie pola kombi na Wstążce z czcionkami.  
  
```  
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nFontType`  
 Określa krój czcionki do dodania.  
  
 [in] `nCharSet`  
 Określa zestaw znaków czcionki do dodania.  
  
 [in] `nPitchAndFamily`  
 Określa gęstość i rodzinę czcionek do dodania.  
  
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
 [in] `nID`  
 Identyfikator polecenia polecenie, które wykonuje się, gdy użytkownik wybiera element w polu kombi.  
  
 [in] `nFontType`  
 Określa typy czcionki, która mają być wyświetlane w polu kombi. Prawidłowe opcje to **DEVICE_FONTTYPE**, **RASTER_FONTTYPE**, i **TRUETYPE_FONTTYPE**, lub dowolną ich kombinację bitowe.  
  
 [in] `nCharSet`  
 Filtry czcionki w polu kombi do tych, które należą do określonego zestawu znaków.  
  
 [in] `nPitchAndFamily`  
 Określa gęstość i rodzinę czcionek, które są wyświetlane w polu kombi.  
  
 [in] `nWidth`  
 Określa szerokość w pikselach, pola kombi.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat możliwości `nFontType` wartości parametrów, zobacz [EnumFontFamProc](http://msdn.microsoft.com/library/windows/desktop/dd162621) w dokumentacji zestawu SDK systemu Windows.  
  
 Aby uzyskać więcej informacji na temat zestawów prawidłowych znaków, które można przypisać do `nCharSet`i prawidłowe wartości, które można przypisać do `nPitchAndFamily`, zobacz [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) w dokumentacji zestawu SDK systemu Windows.  
  
##  <a name="getfontdesc"></a>  CMFCRibbonFontComboBox::GetFontDesc  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] `iIndex`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="rebuildfonts"></a>  CMFCRibbonFontComboBox::RebuildFonts  
 Wypełnia pole kombi na Wstążce z czcionkami wcześniej określonej czcionki, zestaw znaków i gęstość i rodzinę.  
  
```  
void RebuildFonts();
```  
  
### <a name="remarks"></a>Uwagi  
 Można określić typ czcionki, zestaw znaków i gęstość i rodzinę czcionek, aby uwzględnić w pole kombi czcionki wstążki pole [Konstruktor](#cmfcribbonfontcombobox) dla tej klasy lub poprzez wywołanie [CMFCRibbonFontComboBox::BuildFonts](#buildfonts).  
  
##  <a name="setfont"></a>  CMFCRibbonFontComboBox::SetFont  
 Wybiera czcionkę określonej w polu kombi.  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BOOL bExact = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Określa nazwę czcionki, aby wybrać.  
  
 `nCharSet`  
 Określa zestaw znaków dla wybranej czcionki.  
  
 `bExact`  
 `TRUE` Aby określić, że zestaw znaków muszą być zgodne, wybierając czcionki; `FALSE` do określenia, czy zestaw znaków, można zignorować, wybierając czcionki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli znaleziono określonej czcionki i wybrać; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcharset"></a>  CMFCRibbonFontComboBox::GetCharSet  
 Zwraca określonego zestawu znaków.  
  
```  
BYTE GetCharSet() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zestaw znaków (zobacz LOGFONT w dokumentacji zestawu SDK systemu Windows).  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getfonttype"></a>  CMFCRibbonFontComboBox::GetFontType  
 Zwraca typów czcionek, które mają być wyświetlane w polu kombi. Prawidłowe opcje to DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE lub dowolną ich kombinację bitowe.  
  
```  
int GetFontType() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Typy czcionek (zobacz EnumFontFamProc w dokumentacji zestawu SDK systemu Windows).  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getpitchandfamily"></a>  CMFCRibbonFontComboBox::GetPitchAndFamily  
 Zwraca gęstość i rodzinę czcionek, które są wyświetlane w polu kombi.  
  
```  
BYTE GetPitchAndFamily() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Gęstość i rodzinę (zobacz LOGFONT w dokumentacji zestawu SDK systemu Windows).  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)
