---
title: Klasa CMFCPropertyGridColorProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableAutomaticButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableOtherButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColumnsNumber
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetOriginalValue
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 164e54ccbd9365e7e4fb2c1989f84891e5813c2f
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849176"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>Klasa CMFCPropertyGridColorProperty
`CMFCPropertyGridColorProperty` Klasa obsługuje element formantu listy właściwości, które otwiera okno dialogowe wyboru kolorów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|Konstruuje `CMFCPropertyGridColorProperty` obiektu.|  
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|Włącza *automatyczne* przycisku na okno dialogowe wyboru kolorów. (Standardowa automatyczne przycisk ma etykietę **automatyczne**.)|  
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|Włącza *innych* przycisku na okno dialogowe wyboru kolorów. (Standardowe innych przycisk ma etykietę **więcej kolorów**.)|  
|`CMFCPropertyGridColorProperty::FormatProperty`|Formatuje tekst reprezentujący wartość właściwości. (Przesłania [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|  
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|Pobiera bieżący kolor właściwości.|  
|`CMFCPropertyGridColorProperty::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|  
|`CMFCPropertyGridColorProperty::OnClickButton`|Wywoływane przez platformę, gdy użytkownik kliknie przycisk, który jest zawarty we właściwości. (Przesłania [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|  
|`CMFCPropertyGridColorProperty::OnDrawValue`|Metoda wywoływana przez platformę, by wyświetlić wartość właściwości. (Przesłania [CMFCPropertyGridProperty::OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue).)|  
|`CMFCPropertyGridColorProperty::OnEdit`|Wywoływane przez platformę, gdy użytkownik ma zmodyfikować wartości właściwości. (Przesłania [CMFCPropertyGridProperty::OnEdit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit).)|  
|`CMFCPropertyGridColorProperty::OnUpdateValue`|Wywoływane przez platformę, gdy zmieniono wartość właściwości można edytować. (Przesłania [CMFCPropertyGridProperty::OnUpdateValue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).)|  
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|Ustawia nowy kolor dla właściwości.|  
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|Określa liczbę kolumn w siatce właściwości bieżący kolor.|  
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|Ustawia oryginalnej wartości elementu edytowalnych właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCPropertyGridColorProperty` Klasa obsługuje właściwość color, który można dodać do listy właściwości kontrolki. Aby uzyskać więcej informacji, zobacz [klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCPropertyGridColorProperty` klasy i skonfigurować ten obiekt za pomocą różnych metod `CMFCPropertyGridColorProperty` klasy. Kod wyjaśnia, jak włączyć automatyczne i inne przyciski i jak ustawić kolor i liczba kolumn. W tym przykładzie jest częścią [przykładowe nowych formantów](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridcolorproperty"></a>  CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty  
 Konstruuje `CMFCPropertyGridColorProperty` obiektu.  
  
```  
CMFCPropertyGridColorProperty(
    const CString& strName,  
    const COLORREF& color,  
    CPalette* pPalette = NULL,  
    LPCTSTR lpszDescr = NULL,  
    DWORD_PTR dwData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *strName*  
 Nazwa właściwości.  
  
 [in] *kolorów*  
 Wartość koloru właściwości.  
  
 [in] *pPalette*  
 Wskaźnik do palety kolorów. Wartością domyślną jest NULL.  
  
 [in] *lpszDescr*  
 Opis właściwości. Wartością domyślną jest NULL.  
  
 [in] *dwData*  
 Dane specyficzne dla aplikacji, takich jak liczby całkowitej lub wskaźnika do innych danych, który jest skojarzony z właściwością. Wartość domyślna to 0.  
  
##  <a name="enableautomaticbutton"></a>  CMFCPropertyGridColorProperty::EnableAutomaticButton  
 Włącza *automatyczne* przycisku na okno dialogowe wyboru kolorów. (Standardowa automatyczne przycisk ma etykietę **automatyczne**.)  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszLabel*  
 Tekst etykiety przycisku automatycznego.  
  
 [in] *colorAutomatic*  
 Wartość koloru RGB kolor automatyczne (opcja domyślna).  
  
 [in] *bWłączenie*  
 Wartość TRUE, aby włączyć przycisk Automatyczny; w przeciwnym razie wartość FALSE. Wartość domyślna to TRUE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="enableotherbutton"></a>  CMFCPropertyGridColorProperty::EnableOtherButton  
 Włącza *innych* przycisku na okno dialogowe wyboru kolorów. (Standardowe innych przycisk ma etykietę **więcej kolorów**.)  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg = TRUE,  
    BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszLabel*  
 Tekst etykiety przycisku.  
  
 [in] *bAltColorDlg*  
 Wartość true, ekran `CMFCColorDialog` okno dialogowe; Wartość FALSE, aby wyświetlić okno dialogowe wyboru kolorów standardowych. Wartość domyślna to TRUE.  
  
 [in] *bWłączenie*  
 Wartość TRUE, aby wyświetlić inny przycisk; w przeciwnym razie wartość FALSE.  Wartość domyślna to TRUE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcolor"></a>  CMFCPropertyGridColorProperty::GetColor  
 Pobiera bieżący kolor właściwości.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość koloru RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setcolor"></a>  CMFCPropertyGridColorProperty::SetColor  
 Ustawia nowy kolor dla właściwości.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *kolorów*  
 Wartość koloru RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setcolumnsnumber"></a>  CMFCPropertyGridColorProperty::SetColumnsNumber  
 Określa liczbę kolumn w siatce właściwości bieżący kolor.  
  
```  
void SetColumnsNumber(int nColumnsNumber);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nColumnsNumber*  
 Preferowany liczba kolumn w siatce właściwości color.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ustawia wartość `m_nColumnsNumber` chroniony element członkowski danych.  
  
##  <a name="setoriginalvalue"></a>  CMFCPropertyGridColorProperty::SetOriginalValue  
 Ustawia oryginalnej wartości elementu edytowalnych właściwości.  
  
```  
virtual void SetOriginalValue(const COleVariant& varValue);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *varValue*  
 Wartość.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CMFCPropertyGridProperty::ResetOriginalValue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue) metodę, aby zresetować oryginalnej wartości właściwości edytowanego.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [Klasa CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)
