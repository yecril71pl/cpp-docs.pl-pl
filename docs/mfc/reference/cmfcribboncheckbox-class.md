---
title: Klasa CMFCRibbonCheckBox | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bc46d934c99e24b63ef314ef1f63402893c6bb18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribboncheckbox-class"></a>Klasa CMFCRibbonCheckBox
`CMFCRibbonCheckBox` Klasa implementuje pole wyboru, które można dodać do menu panelu, pasek narzędzi Szybki dostęp lub okna podręcznego wstążki.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonCheckBox : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(Przesłania [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|  
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(Przesłania [CMFCRibbonButton::GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|  
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(Przesłania [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|  
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Przesłania `CMFCRibbonButton::IsDrawTooltipImage`.)|  
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(Przesłania [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|  
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Przesłania [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|  
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Przesłania `CMFCRibbonButton::OnDrawOnList`.)|  
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(Przesłania [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|  
  
## <a name="remarks"></a>Uwagi  
 Aby użyć `CMFCRibbonCheckBox` w aplikacji, Dodaj następujący Konstruktor do kodu:  
  
```  
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)  
```  
gdzie `nID` jest identyfikator polecenia pole wyboru i `lpszText` jest etykieta tekstowa pola wyboru.  
  
 Można dodać pola wyboru do panelu wstążki za pomocą [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxribboncheckbox.h  
  
##  <a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox  
 Konstruktor obiektu pole wyboru wstążki  
  
```  
CMFCRibbonCheckBox(
    UINT nID,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nID`  
 Określa identyfikator polecenia.  
  
 [in]`lpszText`  
 Określa tekst etykiety.  
  
### <a name="return-value"></a>Wartość zwracana  
 Tworzy obiekt pole wyboru wstążki.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCRibbonCheckBox` klasy.  
  
 [!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]  
  
##  <a name="getcompactsize"></a>CMFCRibbonCheckBox::GetCompactSize  
 W przypadku przesłonięcia pobiera compact rozmiar pola wyboru.  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do `CDC` skojarzone z wyboru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `CSize` obiekt, który zawiera compact rozmiar pola wyboru.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie została zastąpiona, zwraca pośredniego rozmiar pola wyboru.  
  
##  <a name="getintermediatesize"></a>CMFCRibbonCheckBox::GetIntermediateSize  
 Pobiera pośredniego rozmiar pola wyboru.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do `CDC` skojarzone z tego pola wyboru.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CSize` obiektu zawierającego pośrednich rozmiar pola wyboru.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie została zastąpiona, oblicza rozmiar pośredniego jako domyślny rozmiar pola wyboru ( `AFX_CHECK_BOX_DEFAULT_SIZE`) oraz rozmiar tekstu, a także marginesów.  
  
##  <a name="getregularsize"></a>CMFCRibbonCheckBox::GetRegularSize  
 Pobiera zwykły rozmiar pola wyboru.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do `CDC` obiekt skojarzony z tego pola wyboru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `CSize` obiekt, który zawiera zwykły rozmiar pola wyboru.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie została zastąpiona, zwraca pośredniego rozmiar pola wyboru.  
  
##  <a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage  
 Wskazuje, czy obraz etykietki narzędzia, skojarzone z wyboru.  
  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` w przypadku obrazu etykietka narzędzia, skojarzone z pole wyboru lub `FALSE` , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ondraw"></a>CMFCRibbonCheckBox::OnDraw  
 Wywoływane przez platformę, by narysować pole wyboru przy użyciu kontekstu określonego urządzenia.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do `CDC` do rysowania pole wyboru.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage  
 Wywoływane przez platformę, by narysować obraz menu pola wyboru.  
  
```  
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`CDC*`  
 Wskaźnik do `CDC` skojarzone z wyboru.  
  
 [in]`CRect`  
 A `CRect` obiektu Określanie prostokąt do rysowania obrazu menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` Jeśli narysowaniu obrazu, lub `FALSE` , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie została zastąpiona, zwraca `FALSE`.  
  
##  <a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList  
 Wywoływane przez platformę, by narysować pole wyboru w polu listy poleceń.  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia do rysowania pole wyboru.  
  
 [in]`strText`  
 Wyświetlany tekst.  
  
 [in]`nTextOffset`  
 Odległość w pikselach, po lewej stronie pola listy do wyświetlania tekstu.  
  
 [in]`rect`  
 Prostokątny obszar wyświetlania pola wyboru.  
  
 [in]`bIsSelected`  
 `TRUE`Jeśli pole wyboru jest zaznaczone, lub `FALSE` , jeśli nie.  
  
 [in]`bHighlighted`  
 `TRUE`Jeśli pole wyboru jest podświetlona, lub `FALSE` , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setaccdata"></a>CMFCRibbonCheckBox::SetACCData  
 Ustawia dane ułatwień dostępu dla pola wyboru.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 `pParent`  
 Okno nadrzędne pola wyboru.  
  
 `data`  
 Dane dostępności pola wyboru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda ustawia dane ułatwień dostępu dla pola wyboru i zawsze zwraca `TRUE`. Zastępuje tę metodę, aby ustawić dostępność danych i zwracają wartość wskazuje powodzenie lub niepowodzenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)
