---
title: Klasa CMFCPropertyGridFontProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e7acda3bf3734a325c7d603489c1305cb63bc3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcpropertygridfontproperty-class"></a>Klasa CMFCPropertyGridFontProperty
`CMFCPropertyGridFileProperty` Klasa obsługuje elementu formantu listy właściwości, które umożliwia otwarcie okna dialogowego wyboru czcionki.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|Konstruuje `CMFCPropertyGridFontProperty` obiektu.|  
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCPropertyGridFontProperty::FormatProperty`|Formatuje tekstowa reprezentacja wartości właściwości. (Przesłania [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|  
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Pobiera kolor czcionki, który użytkownik wybiera z czcionki — okno dialogowe.|  
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Pobiera czcionkę, której użytkownik wybiera z czcionki — okno dialogowe.|  
|`CMFCPropertyGridFontProperty::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|`CMFCPropertyGridFontProperty::OnClickButton`|Wywoływane przez platformę, gdy użytkownik kliknie przycisk, który znajduje się we właściwości. (Przesłania [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridfontproperty"></a>  CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty  
 Konstruuje `CMFCPropertyGridFontProperty` obiektu.  
  
```  
CMFCPropertyGridFontProperty(
    const CString& strName,  
    LOGFONT& lf,  
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,  
    LPCTSTR lpszDescr = NULL,  
    DWORD_PTR dwData = 0,  
    COLORREF color = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `strName`  
 Nazwa właściwości.  
  
 [in] `lf`  
 Struktura logiczna czcionki, która określa atrybuty czcionki.  
  
 [in] `dwFontDialogFlags`  
 Style, które są stosowane do czcionki — okno dialogowe wyświetlane po kliknięciu przycisku rozwijanego wartości właściwości. Wartość domyślna to bitowe połączenie (lub) CF_EFFECTS i CF_SCREENFONTS. Aby uzyskać więcej informacji, zobacz `Flags` parametr [struktury CHOOSEFONT](http://msdn.microsoft.com/library/windows/desktop/ms646832).  
  
 [in] `lpszDescr`  
 Opis właściwości czcionki. Wartość domyślna to `NULL`.  
  
 [in] `dwData`  
 Dane specyficzne dla aplikacji, takich jak liczby całkowitej lub wskaźnika do innych danych, która jest skojarzona z właściwością. Wartość domyślna to 0.  
  
 [in] `color`  
 Kolor czcionki. Wartość domyślna to domyślny kolor.  
  
### <a name="remarks"></a>Uwagi  
 A `CMFCPropertyGridFontProperty` obiekt reprezentuje właściwości font w formancie czcionki siatki właściwości.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCPropertyGridFontProperty` klasy. Ten przykład jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]  
  
##  <a name="getcolor"></a>  CMFCPropertyGridFontProperty::GetColor  
 Pobiera kolor czcionki, który użytkownik wybiera z czcionki — okno dialogowe.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość koloru RGB, który reprezentuje kolor wybranej czcionki.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getlogfont"></a>  CMFCPropertyGridFontProperty::GetLogFont  
 Pobiera czcionkę, której użytkownik wybiera z czcionki — okno dialogowe.  
  
```  
LPLOGFONT GetLogFont();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury, która opisuje wybranej czcionki.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [Klasa CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)
