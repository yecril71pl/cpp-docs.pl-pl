---
title: Klasa COccManager
ms.date: 11/04/2016
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
ms.openlocfilehash: 5637a4709e90bb14caff3fe4e396487e62e213e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360360"
---
# <a name="coccmanager-class"></a>Klasa COccManager

Zarządza różnymi niestandardowymi witrynami kontroli; implementowane `COleControlContainer` przez `COleControlSite` obiekty i obiekty.

## <a name="syntax"></a>Składnia

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Menedżer COcc::CreateContainer](#createcontainer)|Tworzy obiekt `COleContainer`.|
|[Menedżer COcc::CreateDlgControls](#createdlgcontrols)|Tworzy formanty ActiveX, hostowane przez skojarzony `COleContainer` obiekt.|
|[Menedżer COcc::CreateSite](#createsite)|Tworzy obiekt `COleClientSite`.|
|[Menedżer COcc::GetDefBtnCode](#getdefbtncode)|Pobiera kod przycisku domyślnego.|
|[Menedżer COcc::IsDialogMessage](#isdialogmessage)|Określa miejsce docelowe komunikatu okna dialogowego.|
|[Menedżer COcc::IsLabelControl](#islabelcontrol)|Określa, czy określony formant jest formantem etykiety.|
|[Menedżer COcc::IsMatchingMnemonic](#ismatchingmnemonic)|Określa, czy bieżąca mnemonic pasuje do mnemonic określonego formantu.|
|[Menedżer COcc::OnEvent](#onevent)|Próbuje obsłużyć określone zdarzenie.|
|[Menedżer COcc::PostTworzeniedialog](#postcreatedialog)|Zwalnia zasoby przydzielone podczas tworzenia okna dialogowego.|
|[COccManager::PreCreateDialog](#precreatedialog)|Przetwarza szablon okna dialogowego dla formantów ActiveX.|
|[Menedżer COcc::SetDefaultButton](#setdefaultbutton)|Przełącza domyślny stan określonego formantu.|
|[Menedżer COcc::SplitDialogTemplate](#splitdialogtemplate)|Oddziela wszystkie istniejące formanty ActiveX od typowych formantów w określonym szablonie okna dialogowego.|

## <a name="remarks"></a>Uwagi

Klasa podstawowa `CNoTrackObject`, jest nieudokumentowaną klasą podstawową (znajdującą się w AFXTLS. H). Przeznaczone do użytku przez platformę MFC, `CNoTrackObject` klasy pochodzące z klasy są zwolnione z wykrywania przecieków pamięci. Nie zaleca się, aby pochodzić `CNoTrackObject`bezpośrednio z .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxocc.h

## <a name="coccmanagercreatecontainer"></a><a name="createcontainer"></a>Menedżer COcc::CreateContainer

Wywoływana przez strukturę do tworzenia kontenera formantu.

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do obiektu okna skojarzonego z kontenerem witryny niestandardowej.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego kontenera; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tworzenia witryn niestandardowych, zobacz [COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).

## <a name="coccmanagercreatedlgcontrols"></a><a name="createdlgcontrols"></a>Menedżer COcc::CreateDlgControls

Wywołanie tej funkcji, aby utworzyć formanty ActiveX określone przez parametr *pOccDialogInfo.*

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

*pWndRodziciela*<br/>
Wskaźnik do obiektu nadrzędnego obiektu okna dialogowego.

*lpszResourceName*<br/>
Nazwa tworzonego zasobu.

*pOccDialogInfo*<br/>
Wskaźnik do szablonu okna dialogowego użytego do utworzenia obiektu okna dialogowego.

*lpResource*<br/>
Wskaźnik do zasobu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli formant został utworzony pomyślnie; w przeciwnym razie zero.

## <a name="coccmanagercreatesite"></a><a name="createsite"></a>Menedżer COcc::CreateSite

Wywoływana przez strukturę do tworzenia witryny kontrolnej, hostowana przez kontener wskazany przez *pCtrlCont*.

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parametry

*pCtrlCont (Kont.*<br/>
Wskaźnik do kontenera formantu obsługującego nową witrynę sterowania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonej witryny sterowania.

### <a name="remarks"></a>Uwagi

Zastąpić tę funkcję, aby utworzyć witrynę kontroli niestandardowej, przy użyciu [COleControlSite](../../mfc/reference/colecontrolsite-class.md)klasy pochodnej.

Każdy kontener formantu może obsługiwać wiele lokacji. Tworzenie dodatkowych witryn z `CreateSite`wieloma połączeniami do .

## <a name="coccmanagergetdefbtncode"></a><a name="getdefbtncode"></a>Menedżer COcc::GetDefBtnCode

Wywołanie tej funkcji, aby ustalić, czy formant jest domyślnym przyciskiem.

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Obiekt okna zawierający kontrolka przycisku.

### <a name="return-value"></a>Wartość zwracana

Jedna z następujących wartości:

- DLGC_DEFPUSHBUTTON Control jest przyciskiem domyślnym w oknie dialogowym.

- DLGC_UNDEFPUSHBUTTON Control nie jest przyciskiem domyślnym w oknie dialogowym.

- **0** Sterowanie nie jest przyciskiem.

## <a name="coccmanagerisdialogmessage"></a><a name="isdialogmessage"></a>Menedżer COcc::IsDialogMessage

Wywoływane przez strukturę, aby ustalić, czy wiadomość jest przeznaczona dla określonego okna dialogowego i, jeśli tak jest, przetwarza komunikat.

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*pWndDlg (ps.*<br/>
Wskaźnik do zamierzonego docelowego okna dialogowego wiadomości.

*lpMsg*<br/>
Wskaźnik do `MSG` struktury, która zawiera wiadomość do sprawdzenia.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wiadomość jest przetwarzana; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Domyślnym zachowaniem jest sprawdzenie komunikatów `IsDialogMessage` klawiaturowych i przekonwertowanie ich na wybrane dla odpowiedniego okna dialogowego. Na przykład klawisz TAB po naciśnięciu wybiera następny formant lub grupę formantów.

Zastąd w tej funkcji należy zastąpić zachowanie niestandardowe dla wiadomości wysyłanych do określonego okna dialogowego.

## <a name="coccmanagerislabelcontrol"></a><a name="islabelcontrol"></a>Menedżer COcc::IsLabelControl

Wywołanie tej funkcji, aby ustalić, czy określony formant jest formantem etykiety.

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do okna zawierającego formant.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli formant jest etykietą; w przeciwnym razie zero

### <a name="remarks"></a>Uwagi

Formant etykiety jest taki, który działa jak etykieta dla niezależnie od kontroli jest następny w kolejności.

## <a name="coccmanagerismatchingmnemonic"></a><a name="ismatchingmnemonic"></a>Menedżer COcc::IsMatchingMnemonic

Wywołanie tej funkcji, aby ustalić, czy bieżące mnemonic pasuje, które są reprezentowane przez formant.

```
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,
    LPMSG lpMsg);

static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do okna zawierającego formant.

*lpMsg*<br/>
Wskaźnik do wiadomości zawierającej mnemonic do dopasowania.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli mnemonic pasuje do kontroli; w przeciwnym razie zero

### <a name="remarks"></a>Uwagi

## <a name="coccmanageronevent"></a><a name="onevent"></a>Menedżer COcc::OnEvent

Wywoływana przez strukturę do obsługi określonego zdarzenia.

```
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,
    UINT idCtrl,
    AFX_EVENT* pEvent,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parametry

*pCmdTarget (pCmdTarget)*<br/>
Wskaźnik do `CCmdTarget` obiektu próbującego obsłużyć zdarzenie

*idCtrl ( idCtrl )*<br/>
Identyfikator zasobu formantu.

*pEvent (właso)*<br/>
Zdarzenie obsługiwane.

*pHandlerInfo*<br/>
Jeśli nie `OnEvent` null, wypełnia `pTarget` `pmf` i członków `AFX_CMDHANDLERINFO` struktury zamiast wysyłania polecenia. Zazwyczaj ten parametr powinien mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli zdarzenie zostało obsłużonych, w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Zastądnie tej funkcji, aby dostosować domyślny proces obsługi zdarzeń.

## <a name="coccmanagerprecreatedialog"></a><a name="precreatedialog"></a>COccManager::PreCreateDialog

Wywoływane przez strukturę do przetwarzania szablonu okna dialogowego dla formantów ActiveX przed utworzeniem rzeczywistego okna dialogowego.

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
Struktura `_AFX_OCC_DIALOG_INFO` zawierająca informacje o szablonie okna dialogowego i dowolnych formantach ActiveX obsługiwanych przez okno dialogowe.

*pOrigTemplate*<br/>
Wskaźnik do szablonu okna dialogowego, który ma być używany do tworzenia okna dialogowego.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury szablonu okna dialogowego używany do tworzenia okna dialogowego.

### <a name="remarks"></a>Uwagi

Domyślne zachowanie wywołuje `SplitDialogTemplate`, określając, czy istnieją jakieś formanty ActiveX obecne, a następnie zwraca wynikowy szablon okna dialogowego.

Zastąd w tej funkcji należy dostosować proces tworzenia okna dialogowego zawierającego formanty ActiveX.

## <a name="coccmanagerpostcreatedialog"></a><a name="postcreatedialog"></a>Menedżer COcc::PostTworzeniedialog

Wywoływane przez strukturę, aby zwolnić pamięć przydzieloną dla szablonu okna dialogowego.

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
Struktura `_AFX_OCC_DIALOG_INFO` zawierająca informacje o szablonie okna dialogowego i dowolnych formantach ActiveX obsługiwanych przez okno dialogowe.

### <a name="remarks"></a>Uwagi

Ta pamięć została przydzielona `SplitDialogTemplate`przez wywołanie do programu i była używana dla wszystkich hostowanych formantów ActiveX w oknie dialogowym.

Zastąd w tej funkcji należy dostosować proces czyszczenia zasobów używanych przez obiekt okna dialogowego.

## <a name="coccmanagersetdefaultbutton"></a><a name="setdefaultbutton"></a>Menedżer COcc::SetDefaultButton

Wywołanie tej funkcji, aby ustawić formant jako przycisk domyślny.

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do okna zawierającego formant.

*bDefault (Domyślnie)*<br/>
Nonzero, jeśli formant powinien stać się przyciskiem domyślnym; w przeciwnym razie zero.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Formant musi mieć ustawiony bit stanu OLEMISC_ACTSLIKEBUTTON. Aby uzyskać więcej informacji na temat flag OLEMISC, zobacz temat [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) w windows SDK.

## <a name="coccmanagersplitdialogtemplate"></a><a name="splitdialogtemplate"></a>Menedżer COcc::SplitDialogTemplate

Wywoływane przez strukturę do dzielenia formantów ActiveX od typowych formantów okna dialogowego.

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>Parametry

*pTemplate*<br/>
Wskaźnik do szablonu okna dialogowego, który ma zostać zbadany.

*ppOleDlgItems*<br/>
Lista wskaźników do elementów okna dialogowego, które są formantami ActiveX.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury szablonu okna dialogowego zawierający tylko formanty inne niż ActiveX. Jeśli nie ma żadnych formantów ActiveX, zwracana jest wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli zostaną znalezione jakieś formanty ActiveX, szablon jest analizowany i tworzony jest nowy szablon zawierający tylko formanty inne niż ActiveX. Wszystkie formanty ActiveX znalezione podczas tego procesu są dodawane do *ppOleDlgItems*.

Jeśli w szablonie nie ma żadnych formantów ActiveX, zwracana jest wartość NULL *.*

> [!NOTE]
> Pamięć przydzielona dla nowego szablonu jest zwalniana w `PostCreateDialog` funkcji.

Zastąd w tej funkcji należy dostosować tę funkcję.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleControlSite](../../mfc/reference/colecontrolsite-class.md)<br/>
[Klasa COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)
