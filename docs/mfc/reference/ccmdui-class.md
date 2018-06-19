---
title: Klasa CCmdUI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCmdUI
- AFXWIN/CCmdUI
- AFXWIN/CCmdUI::ContinueRouting
- AFXWIN/CCmdUI::Enable
- AFXWIN/CCmdUI::SetCheck
- AFXWIN/CCmdUI::SetRadio
- AFXWIN/CCmdUI::SetText
- AFXWIN/CCmdUI::m_nID
- AFXWIN/CCmdUI::m_nIndex
- AFXWIN/CCmdUI::m_pMenu
- AFXWIN/CCmdUI::m_pOther
- AFXWIN/CCmdUI::m_pSubMenu
dev_langs:
- C++
helpviewer_keywords:
- CCmdUI [MFC], ContinueRouting
- CCmdUI [MFC], Enable
- CCmdUI [MFC], SetCheck
- CCmdUI [MFC], SetRadio
- CCmdUI [MFC], SetText
- CCmdUI [MFC], m_nID
- CCmdUI [MFC], m_nIndex
- CCmdUI [MFC], m_pMenu
- CCmdUI [MFC], m_pOther
- CCmdUI [MFC], m_pSubMenu
ms.assetid: 04eaaaf5-f510-48ab-b425-94665ba24766
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf80f2ebea8fe27596ce1b240cc414cc0db7a8db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356691"
---
# <a name="ccmdui-class"></a>Ccmdui — klasa
Jest używana tylko wewnątrz `ON_UPDATE_COMMAND_UI` obsługi w `CCmdTarget`-klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CCmdUI  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCmdUI::ContinueRouting](#continuerouting)|Określa, że nadal routingu do bieżącej wiadomości w łańcuchu obsługi mechanizmu routing poleceń.|  
|[CCmdUI::Enable](#enable)|Włącza lub wyłącza elementu interfejsu użytkownika dla tego polecenia.|  
|[CCmdUI::SetCheck](#setcheck)|Ustawia stan wyboru elementów interfejsu użytkownika dla tego polecenia.|  
|[CCmdUI::SetRadio](#setradio)|Podobnie jak `SetCheck` funkcji członkowskiej, ale działa na grup przycisków opcji.|  
|[CCmdUI::SetText](#settext)|Ustawia tekst dla elementu interfejsu użytkownika dla tego polecenia.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCmdUI::m_nID](#m_nid)|Identyfikator obiektu interfejsu użytkownika.|  
|[CCmdUI::m_nIndex](#m_nindex)|Indeks obiektu interfejsu użytkownika.|  
|[CCmdUI::m_pMenu](#m_pmenu)|Wskazuje menu reprezentowany przez `CCmdUI` obiektu.|  
|[CCmdUI::m_pOther](#m_pother)|Wskazuje obiekt window, który wysyłane powiadomienia.|  
|[CCmdUI::m_pSubMenu](#m_psubmenu)|Wskazuje zawartych w niej podmenu reprezentowany przez `CCmdUI` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CCmdUI` nie ma klasy podstawowej.  
  
 Gdy użytkownik aplikacji ściąga dół menu, każdego menu elementu musi wiedzieć, czy ma być wyświetlany jako włączona lub wyłączona. Element docelowy polecenia menu udostępnia te informacje zaimplementowanie `ON_UPDATE_COMMAND_UI` obsługi. Dla każdego z obiektów interfejsu użytkownika poleceń w aplikacji umożliwiają utworzenie prototyp wpisu i funkcja mapy komunikatów dla każdej procedury obsługi okna właściwości.  
  
 Gdy menu jest obniżona, platformę wyszukuje i wywołuje każdą `ON_UPDATE_COMMAND_UI` obsługi, każdy program obsługi wywołuje `CCmdUI` takich jak funkcje Członkowskie **włączyć** i **Sprawdź**i następnie framework Wyświetla odpowiednio każdego elementu menu.  
  
 Element menu można zastąpić przycisk pasek sterowania lub innego obiektu interfejsu użytkownika polecenia bez zmiany kodu w ramach `ON_UPDATE_COMMAND_UI` programu obsługi.  
  
 W poniższej tabeli przedstawiono wpływ `CCmdUI`do funkcji Członkowskich mają na różne elementy interfejsu użytkownika poleceń.  
  
|Element interfejsu użytkownika|Włącz|SetCheck|SetRadio|SetText|  
|--------------------------|------------|--------------|--------------|-------------|  
|Element menu|Włącza lub wyłącza|Sprawdza lub usuwa zaznaczenie|Umożliwia sprawdzenie za pomocą pojedynczego znaku kropki|Ustawia element tekstu|  
|Przycisk paska narzędzi|Włącza lub wyłącza|Wybiera, usuwa, lub nieokreślony|Identyczny `SetCheck`|(Nie dotyczy)|  
|W okienku paska stanu|Powoduje, że tekst widoczne lub niewidoczne|Ustawia wyskakującego lub normal obramowania|Identyczny `SetCheck`|Ustawia okienko tekstu|  
|Normalny przycisk w `CDialogBar`|Włącza lub wyłącza|Sprawdza lub usuwa zaznaczenie pola wyboru|Identyczny `SetCheck`|Tekst przycisku zestawów|  
|Normalne sterowania w programie `CDialogBar`|Włącza lub wyłącza|(Nie dotyczy)|(Nie dotyczy)|Ustawia tekst okna|  
  
 Aby uzyskać więcej informacji dotyczących korzystania z tej klasy, zobacz [jak obiekty interfejsu użytkownika aktualizacji](../../mfc/how-to-update-user-interface-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CCmdUI`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="continuerouting"></a>  CCmdUI::ContinueRouting  
 Wywołanie tej funkcji Członkowskich mówić kontynuować routingu do bieżącej wiadomości w łańcuchu obsługi mechanizmu routing poleceń.  
  
```  
void ContinueRouting();
```  
  
### <a name="remarks"></a>Uwagi  
 To jest funkcja Zaawansowane elementu członkowskiego, które mają być używane w połączeniu z `ON_COMMAND_EX` obsługi, która zwraca **FALSE**. Aby uzyskać więcej informacji, zobacz [6 Uwaga techniczna](../../mfc/tn006-message-maps.md).  
  
##  <a name="enable"></a>  CCmdUI::Enable  
 Wywołanie tej funkcji Członkowskich, aby włączyć lub wyłączyć elementu interfejsu użytkownika dla tego polecenia.  
  
```  
virtual void Enable(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bOn`  
 **Wartość TRUE,** Aby włączyć element, **FALSE** je wyłączyć.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]  
  
##  <a name="m_nid"></a>  CCmdUI::m_nID  
 Identyfikator elementu menu, przycisk paska narzędzi lub innych obiektu interfejsu użytkownika reprezentowanego przez `CCmdUI` obiektu.  
  
```  
UINT m_nID;  
```  
  
##  <a name="m_nindex"></a>  CCmdUI::m_nIndex  
 Indeks elementu menu, przycisk paska narzędzi lub innych obiektu interfejsu użytkownika reprezentowanego przez `CCmdUI` obiektu.  
  
```  
UINT m_nIndex;  
```  
  
##  <a name="m_pmenu"></a>  CCmdUI::m_pMenu  
 Wskaźnik (z `CMenu` typu) do menu reprezentowany przez `CCmdUI` obiektu.  
  
```  
CMenu* m_pMenu;  
```  
  
### <a name="remarks"></a>Uwagi  
 **Wartość NULL** Jeśli element nie jest menu.  
  
##  <a name="m_psubmenu"></a>  CCmdUI::m_pSubMenu  
 Wskaźnik (z `CMenu` typu) do zawartych w niej podmenu reprezentowany przez `CCmdUI` obiektu.  
  
```  
CMenu* m_pSubMenu;  
```  
  
### <a name="remarks"></a>Uwagi  
 **Wartość NULL** Jeśli element nie jest menu. Jeśli okno podręczne pod menu `m_nID` zawiera identyfikator pierwszego elementu w menu podręcznym. Aby uzyskać więcej informacji, zobacz [techniczne notatkę 21](../../mfc/tn021-command-and-message-routing.md).  
  
##  <a name="m_pother"></a>  CCmdUI::m_pOther  
 Wskaźnik (typu `CWnd`) do obiektu okna, na przykład narzędzi lub paska stanu, które wysłane powiadomienie.  
  
```  
CWnd* m_pOther;  
```  
  
### <a name="remarks"></a>Uwagi  
 **Wartość NULL** Jeśli element jest menu lub innej `CWnd` obiektu.  
  
##  <a name="setcheck"></a>  CCmdUI::SetCheck  
 Wywołanie tej funkcji Członkowskich ustawioną stan wyboru odpowiedniego elementu interfejsu użytkownika dla tego polecenia.  
  
```  
virtual void SetCheck(int nCheck = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `nCheck`  
 Określa stan wyboru, aby ustawić. Jeśli usuwa zaznaczenie 0; Jeśli 1, sprawdza; i jeśli 2, ustawia nieokreślony.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska działa w przypadku elementów menu i przycisków paska narzędzi. Stan nieokreślony ma zastosowanie tylko do przycisków paska narzędzi.  
  
##  <a name="setradio"></a>  CCmdUI::SetRadio  
 Wywołanie tej funkcji Członkowskich ustawioną stan wyboru odpowiedniego elementu interfejsu użytkownika dla tego polecenia.  
  
```  
virtual void SetRadio(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bOn`  
 **Wartość TRUE,** umożliwiające elementu; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego działa jak `SetCheck`, ale działa na elementy interfejsu użytkownika, działając jako część grupy opcji. Zaznaczenie pola wyboru innych elementów w grupie nie jest automatyczne, chyba że zachowanie grupa opcji Obsługa same elementy.  
  
##  <a name="settext"></a>  CCmdUI::SetText  
 Wywołanie tej funkcji Członkowskich, aby ustawić tekst elementu interfejsu użytkownika dla tego polecenia.  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Wskaźnik do ciągu tekstowego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MDI](../../visual-cpp-samples.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
