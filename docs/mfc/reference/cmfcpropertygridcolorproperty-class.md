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
ms.openlocfilehash: de336692a821ba374996fac9ee7d282d2990bd08
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcpropertygridcolorproperty-class"></a>Klasa CMFCPropertyGridColorProperty
`CMFCPropertyGridColorProperty` Klasa obsługuje elementu formantu listy właściwości, które otwiera okno dialogowe Wybieranie koloru.  
  
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
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|Umożliwia *automatyczne* przycisk w oknie dialogowym Wybieranie koloru. (Etykietą standardowe przycisk Automatyczny **automatyczne**.)|  
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|Umożliwia *innych* przycisk w oknie dialogowym Wybieranie koloru. (Standardowy etykietą inny przycisk **więcej kolorów**.)|  
|`CMFCPropertyGridColorProperty::FormatProperty`|Formatuje tekstowa reprezentacja wartości właściwości. (Przesłania [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|  
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|Pobiera bieżący kolor właściwości.|  
|`CMFCPropertyGridColorProperty::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|`CMFCPropertyGridColorProperty::OnClickButton`|Wywoływane przez platformę, gdy użytkownik kliknie przycisk, który znajduje się we właściwości. (Przesłania [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|  
|`CMFCPropertyGridColorProperty::OnDrawValue`|Wywoływane przez platformę, by wyświetlić wartość właściwości. (Przesłania [CMFCPropertyGridProperty::OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue).)|  
|`CMFCPropertyGridColorProperty::OnEdit`|Wywoływane przez platformę, gdy użytkownik ma zmodyfikować wartości właściwości. (Przesłania [CMFCPropertyGridProperty::OnEdit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit).)|  
|`CMFCPropertyGridColorProperty::OnUpdateValue`|Wywoływane przez platformę, gdy zmieniono wartość właściwości można edytować. (Przesłania [CMFCPropertyGridProperty::OnUpdateValue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).)|  
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|Określa kolor nowej właściwości.|  
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|Określa liczbę kolumn w siatce właściwości bieżący kolor.|  
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|Ustawia oryginalnej wartości właściwości można edytować.|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCPropertyGridColorProperty` Klasa obsługuje właściwości kolor, który można dodać do listy właściwości kontrolki. Aby uzyskać więcej informacji, zobacz [CMFCPropertyGridCtrl klasy](../../mfc/reference/cmfcpropertygridctrl-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCPropertyGridColorProperty` klasy, a następnie skonfigurować ten obiekt przy użyciu różnych metod `CMFCPropertyGridColorProperty` klasy. Kod wyjaśniono, jak włączyć automatyczne i innych przycisków i jak ustawić kolor i liczba kolumn. Ten przykład jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
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
 [in] `strName`  
 Nazwa właściwości.  
  
 [in] `color`  
 Wartość koloru właściwości.  
  
 [in] `pPalette`  
 Wskaźnik do palety kolorów. Wartość domyślna to `NULL`.  
  
 [in] `lpszDescr`  
 Opis właściwości. Wartość domyślna to `NULL`.  
  
 [in] `dwData`  
 Dane specyficzne dla aplikacji, takich jak liczby całkowitej lub wskaźnika do innych danych, która jest skojarzona z właściwością. Wartość domyślna to 0.  
  
##  <a name="enableautomaticbutton"></a>  CMFCPropertyGridColorProperty::EnableAutomaticButton  
 Umożliwia *automatyczne* przycisk w oknie dialogowym Wybieranie koloru. (Etykietą standardowe przycisk Automatyczny **automatyczne**.)  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszLabel`  
 Tekst etykiety przycisk Automatyczny.  
  
 [in] `colorAutomatic`  
 Wartości kolorów RGB koloru automatyczne (ustawienie domyślne).  
  
 [in] `bEnable`  
 `TRUE` Aby włączyć automatyczne przycisk; w przeciwnym razie `FALSE`. Wartość domyślna to `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="enableotherbutton"></a>  CMFCPropertyGridColorProperty::EnableOtherButton  
 Umożliwia *innych* przycisk w oknie dialogowym Wybieranie koloru. (Standardowy etykietą inny przycisk **więcej kolorów**.)  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg = TRUE,  
    BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszLabel`  
 Tekst etykiety inny przycisk.  
  
 [in] `bAltColorDlg`  
 `TRUE` Aby wyświetlić `CMFCColorDialog` okno dialogowe; `FALSE` do wyświetlenia okna dialogowego wyboru Kolor standardowy. Wartość domyślna to `TRUE`.  
  
 [in] `bEnable`  
 `TRUE` Aby wyświetlić przycisk; w przeciwnym razie `FALSE`.  Wartość domyślna to `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcolor"></a>  CMFCPropertyGridColorProperty::GetColor  
 Pobiera bieżący kolor właściwości.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartości kolorów RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setcolor"></a>  CMFCPropertyGridColorProperty::SetColor  
 Określa kolor nowej właściwości.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `color`  
 Wartości kolorów RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setcolumnsnumber"></a>  CMFCPropertyGridColorProperty::SetColumnsNumber  
 Określa liczbę kolumn w siatce właściwości bieżący kolor.  
  
```  
void SetColumnsNumber(int nColumnsNumber);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nColumnsNumber`  
 Preferowaną liczbę kolumn w siatce właściwości kolorów.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ustawia wartość `m_nColumnsNumber` chroniony element członkowski danych.  
  
##  <a name="setoriginalvalue"></a>  CMFCPropertyGridColorProperty::SetOriginalValue  
 Ustawia oryginalnej wartości właściwości można edytować.  
  
```  
virtual void SetOriginalValue(const COleVariant& varValue);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `varValue`  
 Wartość.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CMFCPropertyGridProperty::ResetOriginalValue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue) metoda oryginalnej wartości właściwości edytowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [Klasa CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)
