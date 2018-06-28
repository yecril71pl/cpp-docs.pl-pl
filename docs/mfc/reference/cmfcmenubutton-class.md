---
title: Klasa CMFCMenuButton | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::PreTranslateMessage
- AFXMENUBUTTON/CMFCMenuButton::SizeToContent
- AFXMENUBUTTON/CMFCMenuButton::m_bOSMenu
- AFXMENUBUTTON/CMFCMenuButton::m_bRightArrow
- AFXMENUBUTTON/CMFCMenuButton::m_bStayPressed
- AFXMENUBUTTON/CMFCMenuButton::m_hMenu
- AFXMENUBUTTON/CMFCMenuButton::m_nMenuResult
dev_langs:
- C++
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09d68cd7c0e4796b3368e1167888d703d37a8cf8
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040171"
---
# <a name="cmfcmenubutton-class"></a>Klasa CMFCMenuButton
Przycisk menu podręcznego i raporty w opcji menu użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCMenuButton : public CMFCButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|Konstruuje `CMFCMenuButton` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Wywoływane przez platformę, by tłumaczenie komunikaty okna przed ich wysłaniem. (Przesłania `CMFCButton::PreTranslateMessage`.)|  
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Zmienia rozmiar przycisku w zależności od rozmiaru tekstu i obrazów.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Określa, czy do wyświetlenia menu podręcznego systemu domyślne [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|  
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Określa, czy menu podręczne pojawi się poniżej lub po prawej stronie przycisku.|  
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Określa, czy przycisk menu zmiany stanu po użytkownik zwolni przycisk.|  
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Dojście do podłączonego menu systemu Windows.|  
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|Identyfikator, który wskazuje, który element użytkownik wybrał z menu podręcznego.|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCMenuButton` Jest pochodną klasy [klasy CMFCButton](../../mfc/reference/cmfcbutton-class.md) który z kolei pochodną [CButton klasy](../../mfc/reference/cbutton-class.md). W związku z tym można użyć `CMFCMenuButton` w taki sam sposób, należy użyć kodu `CButton`.  
  
 Po utworzeniu `CMFCMenuButton`, trzeba przekazać w dojścia do skojarzonego menu podręczne. Następnie wywołaj funkcję `CMFCMenuButton::SizeToContent`. `CMFCMenuButton::SizeToContent` sprawdza, czy rozmiar przycisku jest wystarczająca do uwzględnienia strzałkę, która wskazuje lokalizację, gdzie okno podręczne pojawi się — to znaczy, poniżej lub po prawej stronie przycisku.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak ustawić dojście dołączone do przycisku menu, Zmień rozmiar przycisku zgodnie z jego tekstu i rozmiaru obrazka i ustaw menu podręczne jest wyświetlany przez platformę. Następujący fragment kodu jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmenubutton.h  
  
##  <a name="cmfcmenubutton"></a>  CMFCMenuButton::CMFCMenuButton  
 Tworzy nowy [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md) obiektu.  
  
```  
CMFCMenuButton();
```  
  
##  <a name="m_bosmenu"></a>  CMFCMenuButton::m_bOSMenu  
 Wyświetla platformę zmienną członkowską logiczna, która wskazuje, które menu podręczne.  
  
```  
BOOL m_bOSMenu;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `m_bOSMenu` jest `TRUE`, struktura wywołuje dziedziczonego `TrackPopupMenu` metody dla tego obiektu. W przeciwnym razie struktura wywołuje [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).  
  
##  <a name="m_brightarrow"></a>  CMFCMenuButton::m_bRightArrow  
 Zmiennej członkowskiej Boolean, który wskazuje lokalizację, w menu podręcznym.  
  
```  
BOOL m_bRightArrow;  
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik naciśnie przycisk menu, aplikacja zawiera menu podręczne. Platformę będą wyświetlane po kliknięciu przycisku lub po prawej stronie przycisku menu podręcznym. Przycisk ma również małą strzałkę, która wskazuje, gdzie będą wyświetlane menu podręczne. Jeśli `m_bRightArrow` jest `TRUE`, platformę Wyświetla menu podręczne po prawej stronie przycisku. W przeciwnym razie on Wyświetla menu podręczne po kliknięciu przycisku.  
  
##  <a name="m_bstaypressed"></a>  CMFCMenuButton::m_bStayPressed  
 Zmiennej członkowskiej Boolean wskazującą, czy jest wyświetlany przycisk menu naciśnięciu, gdy użytkownik nie wybrał wybór z menu podręcznego.  
  
```  
BOOL m_bStayPressed;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `m_bStayPressed` element członkowski jest `FALSE`, menu nie staną się przycisku kiedy użytkownik kliknie przycisk. W takim przypadku platformę Wyświetla menu podręczne.  
  
 Jeśli `m_bStayPressed` element członkowski jest `TRUE`, staje się naciśnięty przycisk menu, gdy użytkownik kliknie przycisk. Pozostaje on objęty naciśniętego dopiero po zamknięciu menu podręcznego Zaznaczanie lub anulowanie przez użytkownika.  
  
##  <a name="m_hmenu"></a>  CMFCMenuButton::m_hMenu  
 Dojście do menu dołączone.  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="remarks"></a>Uwagi  
 Platformę Wyświetla menu wskazywanym przez tej zmiennej członkowskiej, gdy użytkownik kliknie przycisk menu.  
  
##  <a name="m_nmenuresult"></a>  CMFCMenuButton::m_nMenuResult  
 Liczba całkowita, która wskazuje, który element użytkownik wybiera z menu podręcznego.  
  
```  
int m_nMenuResult;  
```  
  
### <a name="remarks"></a>Uwagi  
 Wartość tej zmiennej elementu członkowskiego wynosi zero, jeśli użytkownik anuluje menu bez dokonywania wyboru lub w przypadku wystąpienia błędu.  
  
##  <a name="pretranslatemessage"></a>  CMFCMenuButton::PreTranslateMessage  
 Wywoływane przez platformę, by tłumaczenie komunikaty okna przed ich wysłaniem.  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pMsg*  
 Wskazuje [MSG](../../mfc/reference/msg-structure1.md) strukturę, która zawiera komunikat do przetworzenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli komunikat przetłumaczony i nie powinien być wysyłany; 0, jeśli wiadomość nie została przekonwertowana i powinien zostać wysłane.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="sizetocontent"></a>  CMFCMenuButton::SizeToContent  
 Zmienia rozmiar przycisku zgodnie z jego rozmiaru tekstu i rozmiaru obrazu.  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bCalcOnly*  
 Parametrów typu Boolean wskazującą, czy ta metoda zmienia rozmiar przycisku.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) obiekt, który określa nowy rozmiar dla przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wywołanie tej funkcji i *bCalcOnly* jest `TRUE`, `SizeToContent` oblicza nowy rozmiar przycisku.  
  
 Nowy rozmiar przycisku jest obliczana spełniających tekst przycisku, obrazu i strzałki. Platformę oferuje również wstępnie zdefiniowane marginesy 10 pikseli poziome Edge i 5 pikseli pionowy Edge.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md)
