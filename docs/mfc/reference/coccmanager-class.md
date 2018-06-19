---
title: Klasa COccManager | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COccManager
- AFXOCC/COccManager
- AFXOCC/COccManager::CreateContainer
- AFXOCC/COccManager::CreateDlgControls
- AFXOCC/COccManager::CreateSite
- AFXOCC/COccManager::GetDefBtnCode
- AFXOCC/COccManager::IsDialogMessage
- AFXOCC/COccManager::IsLabelControl
- AFXOCC/COccManager::IsMatchingMnemonic
- AFXOCC/COccManager::OnEvent
- AFXOCC/COccManager::PostCreateDialog
- AFXOCC/COccManager::PreCreateDialog
- AFXOCC/COccManager::SetDefaultButton
- AFXOCC/COccManager::SplitDialogTemplate
dev_langs:
- C++
helpviewer_keywords:
- COccManager [MFC], CreateContainer
- COccManager [MFC], CreateDlgControls
- COccManager [MFC], CreateSite
- COccManager [MFC], GetDefBtnCode
- COccManager [MFC], IsDialogMessage
- COccManager [MFC], IsLabelControl
- COccManager [MFC], IsMatchingMnemonic
- COccManager [MFC], OnEvent
- COccManager [MFC], PostCreateDialog
- COccManager [MFC], PreCreateDialog
- COccManager [MFC], SetDefaultButton
- COccManager [MFC], SplitDialogTemplate
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b292196eb6ac8178ba43f0e66bd4814368c916fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376115"
---
# <a name="coccmanager-class"></a>Klasa COccManager
Zarządza różnych witryn kontrolki niestandardowej. implementowany przez `COleControlContainer` i `COleControlSite` obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COccManager : public CNoTrackObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COccManager::CreateContainer](#createcontainer)|Tworzy **COleContainer** obiektu.|  
|[COccManager::CreateDlgControls](#createdlgcontrols)|Tworzy formantów ActiveX, obsługiwanych przez skojarzony `COleContainer` obiektu.|  
|[COccManager::CreateSite](#createsite)|Tworzy `COleClientSite` obiektu.|  
|[COccManager::GetDefBtnCode](#getdefbtncode)|Pobiera kod przycisk domyślny.|  
|[COccManager::IsDialogMessage](#isdialogmessage)|Określa docelowy komunikatu dialogu.|  
|[COccManager::IsLabelControl](#islabelcontrol)|Określa, czy określony formant jest formantu etykiety.|  
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Określa, czy bieżąca wartość zgodne mnemonik określonego formantu.|  
|[COccManager::OnEvent](#onevent)|Próbuje obsługi określonego zdarzenia.|  
|[COccManager::PostCreateDialog](#postcreatedialog)|Zwalnia zasoby przydzielone podczas tworzenia okna dialogowego.|  
|[COccManager::PreCreateDialog](#precreatedialog)|Przetwarza szablonu okna dialogowego dla formantów ActiveX.|  
|[COccManager::SetDefaultButton](#setdefaultbutton)|Włącza/wyłącza domyślnego stanu określonego formantu.|  
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|Oddziela żadnych istniejących formantów ActiveX od formantów wspólnych w szablonie określonego okna dialogowego.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa podstawowa **CNoTrackObject**, jest nieudokumentowanej klasy podstawowej (znajdujący się w AFXTLS. H). Przeznaczony do użytku przez platformę MFC, klasy wyprowadzone z **CNoTrackObject** klasy są wykluczone z wykrywanie przecieków pamięci. Nie zaleca się, że pochodzi bezpośrednio z **CNoTrackObject**.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CNoTrackObject`  
  
 `COccManager`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxocc.h  
  
##  <a name="createcontainer"></a>  COccManager::CreateContainer  
 Wywoływane przez platformę, by utworzyć kontener formantu.  
  
```  
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskaźnik do obiektu okna skojarzony z kontenerem niestandardowej witryny.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo utworzonej kontenera; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat tworzenia niestandardowych witryn, zobacz [COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).  
  
##  <a name="createdlgcontrols"></a>  COccManager::CreateDlgControls  
 Wywołanie tej funkcji do tworzenia kontrolek ActiveX określony przez `pOccDialogInfo` parametru.  
  
```  
virtual BOOL CreateDlgControls(
    CWnd* pWndParent,  
    LPCTSTR lpszResourceName,  
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);

 
virtual BOOL CreateDlgControls(
    CWnd* pWndParent,  
    void* lpResource,  
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndParent*  
 Wskaźnik do elementu nadrzędnego obiektu okna dialogowego.  
  
 `lpszResourceName`  
 Nazwa zasobu tworzonego.  
  
 `pOccDialogInfo`  
 Wskaźnik do szablonu okna dialogowego użyty do utworzenia obiektu okna dialogowego.  
  
 `lpResource`  
 Wskaźnik do zasobu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli formant został utworzony pomyślnie; w przeciwnym razie wartość zero.  
  
##  <a name="createsite"></a>  COccManager::CreateSite  
 Wywoływane przez platformę, aby utworzyć lokację kontroli hostowanych przez kontener wskazywana przez `pCtrlCont`.  
  
```  
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>Parametry  
 `pCtrlCont`  
 Wskaźnik do nowej lokacji formantu kontenera kontroli.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo utworzonej kontroli lokacji.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję można utworzyć niestandardowego formantu lokacji za pomocą programu [COleControlSite](../../mfc/reference/colecontrolsite-class.md)-klasy.  
  
 Kontener każdego formantu można obsługiwać wiele witryn. Utwórz dodatkowe lokacje z wielu wywołań `CreateSite`.  
  
##  <a name="getdefbtncode"></a>  COccManager::GetDefBtnCode  
 Wywołanie tej funkcji, aby określić, czy formant jest domyślny przycisk.  
  
```  
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Obiekt okna zawierającego formantu przycisku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jedna z następujących wartości:  
  
- **DLGC_DEFPUSHBUTTON** formant jest przycisk domyślny w oknie dialogowym.  
  
- **DLGC_UNDEFPUSHBUTTON** formant nie jest przycisk domyślny w oknie dialogowym.  
  
- **0** formant nie jest przycisk.  
  
##  <a name="isdialogmessage"></a>  COccManager::IsDialogMessage  
 Wywoływane przez platformę, by określić, czy wiadomość jest przeznaczony dla określonego okna dialogowego i jeśli tak jest, przetwarza wiadomości.  
  
```  
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndDlg*  
 Wskaźnik do okna dialogowego docelową wiadomości.  
  
 `lpMsg`  
 Wskaźnik do `MSG` struktury, która zawiera komunikat, który ma być sprawdzane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli komunikat jest przetwarzany; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Domyślne zachowanie `IsDialogMessage` Sprawdź, czy komunikaty klawiatury i przekonwertować je na ustawienia w odpowiednim oknie dialogowym. Na przykład klawisz TAB, po naciśnięciu wybiera następny formant lub grupę formantów.  
  
 Zastąpienie tej funkcji do zapewnienia zachowania niestandardowego komunikaty wysyłane do określonego okna dialogowego.  
  
##  <a name="islabelcontrol"></a>  COccManager::IsLabelControl  
 Wywołanie tej funkcji, aby określić, czy określony formant jest formant etykiety.  
  
```  
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);  
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskaźnik do okna zawierającego ten formant.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli formant jest etykieta; w przeciwnym razie zero  
  
### <a name="remarks"></a>Uwagi  
 Etykieta to taki, który działa jak etykietę dla dowolnego formant jest dalej w kolejności.  
  
##  <a name="ismatchingmnemonic"></a>  COccManager::IsMatchingMnemonic  
 Wywołanie tej funkcji, aby określić, czy bieżąca wartość jest zgodna z wersją reprezentowany przez formant.  
  
```  
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,  
    LPMSG lpMsg);

 
static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskaźnik do okna zawierającego ten formant.  
  
 `lpMsg`  
 Wskaźnik do komunikat zawierający mnemonik do dopasowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli mnemonik pasuje do formantu; w przeciwnym razie zero  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onevent"></a>  COccManager::OnEvent  
 Wywoływane przez platformę, by obsłużyć określone zdarzenie.  
  
```  
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,  
    UINT idCtrl,  
    AFX_EVENT* pEvent,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *pCmdTarget*  
 Wskaźnik do `CCmdTarget` obiektu, próby zdarzenie  
  
 `idCtrl`  
 Identyfikator zasobu formantu.  
  
 `pEvent`  
 Zdarzenie jest obsługiwane.  
  
 `pHandlerInfo`  
 Jeśli nie **NULL**, `OnEvent` wypełnia **pTarget** i **pmf** członkami **AFX_CMDHANDLERINFO** struktury zamiast wysyła polecenie. Zazwyczaj ten parametr powinien być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zdarzenie został obsłużony, w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, aby dostosować domyślny proces obsługi zdarzeń.  
  
##  <a name="precreatedialog"></a>  COccManager::PreCreateDialog  
 Wywoływane przez platformę, by przetworzyć przed utworzeniem okna dialogowego rzeczywiste szablonu okna dialogowego dla formantów ActiveX.  
  
```  
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,  
    const DLGTEMPLATE* pOrigTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 `pOccDialogInfo`  
 **_AFX_OCC_DIALOG_INFO** struktury zawierające informacje dotyczące szablonu okna dialogowego i wszelkich formantów ActiveX hostowanej za pomocą okna dialogowego.  
  
 *pOrigTemplate*  
 Wskaźnik do szablonu okna dialogowego, które ma być używany podczas tworzenia okna dialogowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do struktury szablonu okna dialogowego używany do tworzenia okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Domyślne zachowanie nawiązuje połączenie `SplitDialogTemplate`, określania, jeśli ma żadnych ActiveX kontroluje obecne, a następnie zwraca szablonu wynikowe okna dialogowego.  
  
 Zastąpienie tej funkcji w celu dostosowania procesu tworzenia okno dialogowe kontrole hostingu ActiveX.  
  
##  <a name="postcreatedialog"></a>  COccManager::PostCreateDialog  
 Wywoływane przez platformę, aby zwolnić pamięć przydzielona dla szablonu okna dialogowego.  
  
```  
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>Parametry  
 `pOccDialogInfo`  
 **_AFX_OCC_DIALOG_INFO** struktury zawierające informacje dotyczące szablonu okna dialogowego i wszelkich formantów ActiveX hostowanej za pomocą okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Ta pamięć została przydzielona przez wywołanie do `SplitDialogTemplate`i została użyta dla wszystkich obsługiwanych formantów ActiveX w oknie dialogowym.  
  
 Zastąpienie tej funkcji w celu dostosowania procesu oczyszczania zasoby używane przez obiekt — okno dialogowe.  
  
##  <a name="setdefaultbutton"></a>  COccManager::SetDefaultButton  
 Wywołanie tej funkcji, aby ustawić formant jako przycisk domyślny.  
  
```  
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,  
    BOOL bDefault);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskaźnik do okna zawierającego ten formant.  
  
 `bDefault`  
 Różna od zera, jeśli formant powinien być przycisk domyślny; w przeciwnym razie wartość zero.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Kontrolka musi mieć **OLEMISC_ACTSLIKEBUTTON** bitu stanu. Aby uzyskać więcej informacji na temat **OLEMISC** flagi, zobacz [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) tematu w zestawie Windows SDK.  
  
##  <a name="splitdialogtemplate"></a>  COccManager::SplitDialogTemplate  
 Wywoływane przez platformę, by podzielić kontrolki ActiveX z typowych formantów okna dialogowego.  
  
```  
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,  
    DLGITEMTEMPLATE** ppOleDlgItems);
```  
  
### <a name="parameters"></a>Parametry  
 `pTemplate`  
 Wskaźnik do szablonu okna dialogowego należy zbadać.  
  
 `ppOleDlgItems`  
 Lista wskaźników do elementów okno dialogowe, które są formantów ActiveX.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do struktury szablonu okna dialogowego, zawierający tylko formanty ActiveX nie. Jeśli podano żadnych formantów ActiveX **NULL** jest zwracany.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku znalezienia żadnych formantów ActiveX szablonu są analizowane i jest tworzony jest nowy szablon, zawierający tylko formanty ActiveX nie. Wszystkie kontrolki ActiveX w trakcie tego procesu są dodawane do `ppOleDlgItems`.  
  
 Jeśli w szablonie nie nie formantów ActiveX **NULL** jest zwracany *.*  
  
> [!NOTE]
>  Pamięć przydzielona dla nowego szablonu zostanie zwolniona w `PostCreateDialog` funkcji.  
  
 Należy przesłonić tę funkcję, aby dostosować ten proces.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleControlSite](../../mfc/reference/colecontrolsite-class.md)   
 [Klasa COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)
