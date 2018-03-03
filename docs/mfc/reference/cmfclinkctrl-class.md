---
title: Klasa CMFCLinkCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
dev_langs:
- C++
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fc83e5abf09102af8f27b1ee73fc78ed162b9335
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfclinkctrl-class"></a>Klasa CMFCLinkCtrl
`CMFCLinkCtrl` Klasa przedstawia przycisk jako hiperłącze i wywołuje docelowy łącza, po kliknięciu przycisku.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCLinkCtrl : public CMFCButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCLinkCtrl::SetURL](#seturl)|Określony adres URL będzie wyświetlany jako tekst przycisku.|  
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|Ustawia niejawne protokół (na przykład "http:") adresu URL.|  
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|Zmienia rozmiar przycisku zawierają tekst przycisku lub mapy bitowej.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Wywoływane przez platformę przed narysowaniem prostokąt fokusu przycisku.|  
  
## <a name="remarks"></a>Uwagi  
 Po kliknięciu przycisku, który jest pochodną `CMFCLinkCtrl` klasy, struktury przekazuje adres URL przycisku jako parametr `ShellExecute` metody. Następnie przy użyciu `ShellExecute` metody otwiera obiekt docelowy adresu URL.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób ustawiania rozmiaru `CMFCLinkCtrl` obiektu oraz jak ustawić adres url i etykietki narzędzia w `CMFCLinkCtrl` obiektu. Ten przykład jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxlinkctrl.h  
  
##  <a name="ondrawfocusrect"></a>CMFCLinkCtrl::OnDrawFocusRect  
 Wywoływane przez platformę przed narysowaniem prostokąt fokusu przycisku.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in]`rectClient`  
 Prostokąt zakresem kontrolki łącza.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę metodę, jeśli chcesz użyć własnego kodu do rysowania prostokąt fokusu przycisku.  
  
##  <a name="seturl"></a>CMFCLinkCtrl::SetURL  
 Określony adres URL będzie wyświetlany jako tekst przycisku.  
  
```  
void SetURL(LPCTSTR lpszURL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszURL`  
 Tekst przycisku do wyświetlenia.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="seturlprefix"></a>CMFCLinkCtrl::SetURLPrefix  
 Ustawia niejawne protokół (na przykład "http:") adresu URL.  
  
```  
void SetURLPrefix(LPCTSTR lpszPrefix);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszPrefix`  
 Prefiks adresu URL protokołu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby ustawić prefiksu adresu URL. Prefiks nie jest wyświetlany na przycisku, ale służy do pomocy, przejdź do docelowego adresu URL.  
  
##  <a name="sizetocontent"></a>CMFCLinkCtrl::SizeToContent  
 Zmienia rozmiar przycisku zawierają tekst przycisku lub mapy bitowej.  
  
```  
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,  
    BOOL bHCenter=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bVCenter`  
 `TRUE`Tekst przycisku center i mapy bitowej w pionie między górą a dołem kontroli łączy. w przeciwnym razie `FALSE`. Wartość domyślna to `FALSE`.  
  
 [in]`bHCenter`  
 `TRUE`Aby wyśrodkować tekst przycisku i mapy bitowej poziomo od lewej i prawej stronie formantu łącze; w przeciwnym razie `FALSE`. Wartość domyślna to `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) obiekt, który zawiera nowy rozmiar kontrolki łącza.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CLinkCtrl](../../mfc/reference/clinkctrl-class.md)   
 [Klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md)
