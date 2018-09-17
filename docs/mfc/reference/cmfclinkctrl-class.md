---
title: Klasa CMFCLinkCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6bed16f338c5ee3333529613189fe03ad7e3ec3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709556"
---
# <a name="cmfclinkctrl-class"></a>Klasa CMFCLinkCtrl
`CMFCLinkCtrl` Klasy Wyświetla przycisk jako hiperłącze i wywołuje cel łącza po kliknięciu przycisku.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCLinkCtrl : public CMFCButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCLinkCtrl::SetURL](#seturl)|Wyświetla wybrany adres URL w postaci tekstu przycisku.|  
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|Ustawia protokół niejawne (na przykład "http:") adresu URL.|  
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|Zmienia rozmiar przycisku, które zawierają tekst przycisku lub mapy bitowej.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Wywoływane przez platformę przed narysowaniem prostokąt fokusu przycisku.|  
  
## <a name="remarks"></a>Uwagi  
 Po kliknięciu przycisku, który jest tworzony na podstawie `CMFCLinkCtrl` klasa, struktura przekazanie adresu URL przycisku jako parametr do `ShellExecute` metody. A następnie `ShellExecute` metoda zostanie otwarty obiekt docelowy adresu URL.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak ustawić rozmiar `CMFCLinkCtrl` obiektu i jak ustawić adres url i etykietka narzędzia w `CMFCLinkCtrl` obiektu. W tym przykładzie jest częścią [przykładowe nowych formantów](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxlinkctrl.h  
  
##  <a name="ondrawfocusrect"></a>  CMFCLinkCtrl::OnDrawFocusRect  
 Wywoływane przez platformę przed narysowaniem prostokąt fokusu przycisku.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia.  
  
*rectClient*<br/>
[in] Prostokąt, który granic kontrolki łącza.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę metodę, jeśli chcesz użyć własnego kodu, aby narysować prostokąt fokusu na przycisku.  
  
##  <a name="seturl"></a>  CMFCLinkCtrl::SetURL  
 Wyświetla wybrany adres URL w postaci tekstu przycisku.  
  
```  
void SetURL(LPCTSTR lpszURL);
```  
  
### <a name="parameters"></a>Parametry  
*lpszURL*<br/>
[in] Tekst przycisku do wyświetlenia.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="seturlprefix"></a>  CMFCLinkCtrl::SetURLPrefix  
 Ustawia protokół niejawne (na przykład "http:") adresu URL.  
  
```  
void SetURLPrefix(LPCTSTR lpszPrefix);
```  
  
### <a name="parameters"></a>Parametry  
*lpszPrefix*<br/>
[in] Prefiks Protokół adresu URL.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody można ustawić prefiks adresu URL. Prefiks nie jest wyświetlany na powierzchni przycisku, ale służy do pomocy, przejdź do docelowego adresu URL.  
  
##  <a name="sizetocontent"></a>  CMFCLinkCtrl::SizeToContent  
 Zmienia rozmiar przycisku, które zawierają tekst przycisku lub mapy bitowej.  
  
```  
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,  
    BOOL bHCenter=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
*bVCenter*<br/>
[in] Wartość TRUE, aby wyśrodkować przycisku tekstu i mapy bitowej w pionie między górą a dołem kontroli łącza. w przeciwnym razie wartość FALSE. Wartość domyślna to FALSE.  
  
*bHCenter*<br/>
[in] Wartość TRUE, aby wyśrodkować przycisku tekstu i mapy bitowej w poziomie od lewej i prawej stronie kontroli łącza. w przeciwnym razie wartość FALSE. Wartość domyślna to FALSE.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) obiekt, który zawiera nowy rozmiar kontrolki łącza.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CLinkCtrl](../../mfc/reference/clinkctrl-class.md)   
 [Klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md)
