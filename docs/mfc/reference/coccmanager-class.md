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
ms.openlocfilehash: a83f58b8de2411577d9fc025f7a8f8dc535ea8b3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276653"
---
# <a name="coccmanager-class"></a>Klasa COccManager

Zarządza różnymi witrynami kontrolek niestandardowych; implementowany przez `COleControlContainer` i `COleControlSite` obiektów.

## <a name="syntax"></a>Składnia

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COccManager::CreateContainer](#createcontainer)|Tworzy `COleContainer` obiektu.|
|[COccManager::CreateDlgControls](#createdlgcontrols)|Tworzy kontrolki ActiveX, hostowane przez skojarzony `COleContainer` obiektu.|
|[COccManager::CreateSite](#createsite)|Tworzy `COleClientSite` obiektu.|
|[COccManager::GetDefBtnCode](#getdefbtncode)|Pobiera kod przycisk domyślny.|
|[COccManager::IsDialogMessage](#isdialogmessage)|Określa obiekt docelowy komunikatu dialogu.|
|[COccManager::IsLabelControl](#islabelcontrol)|Określa, czy określony formant kontrolkę typu etykieta.|
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Określa, czy bieżący skrót klawiszowy odpowiada wartość określoną kontrolkę.|
|[COccManager::OnEvent](#onevent)|Próbuje obsłużyć określonego zdarzenia.|
|[COccManager::PostCreateDialog](#postcreatedialog)|Zwalnia zasoby przydzielone podczas tworzenia okna dialogowego.|
|[COccManager::PreCreateDialog](#precreatedialog)|Przetwarza szablonu okna dialogowego dla formantów ActiveX.|
|[COccManager::SetDefaultButton](#setdefaultbutton)|Włącza/wyłącza stan domyślny określoną kontrolkę.|
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|Oddziela żadnych istniejących formantów ActiveX od formantów wspólnych w szablonie określonego okna dialogowego.|

## <a name="remarks"></a>Uwagi

Klasa bazowa `CNoTrackObject`, jest nieudokumentowane klasy bazowej (znajdujący się w AFXTLS. GODZ.). Przeznaczony do użytku przez platformę, MFC, klasy pochodne klasy `CNoTrackObject` klasy są wykluczone z wykrywania przecieków pamięci. Nie zaleca się, że uzyskujesz bezpośrednio z `CNoTrackObject`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxocc.h

##  <a name="createcontainer"></a>  COccManager::CreateContainer

Metoda wywoływana przez strukturę w celu utworzenia kontenera kontrolki.

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do obiektu okna skojarzonych z danym kontenerem niestandardowej witryny.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzony kontener; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tworzenia niestandardowych witryn, zobacz [COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).

##  <a name="createdlgcontrols"></a>  COccManager::CreateDlgControls

Wywołaj tę funkcję w celu tworzenia formantów ActiveX określony przez *pOccDialogInfo* parametru.

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

*pWndParent*<br/>
Wskaźnik do elementu nadrzędnego obiektu okna dialogowego.

*lpszResourceName*<br/>
Nazwa zasobu tworzonego.

*pOccDialogInfo*<br/>
Wskaźnik do szablonu okna dialogowego, użyty do utworzenia obiektu okna dialogowego.

*lpResource*<br/>
Wskaźnik do zasobu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli kontrolka została utworzona pomyślnie; w przeciwnym razie wartość zero.

##  <a name="createsite"></a>  COccManager::CreateSite

Wywoływane przez platformę, aby utworzyć lokację kontroli hostowanych przez kontener, do których prowadzą *pCtrlCont*.

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parametry

*pCtrlCont*<br/>
Wskaźnik do nowej lokacji formantu do hostowania kontenerów kontroli.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do lokacji nowo utworzonego formantu.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby utworzyć formant niestandardowy lokacji, przy użyciu usługi [COleControlSite](../../mfc/reference/colecontrolsite-class.md)-klasy pochodnej.

Każdy kontener formantu może hostować wiele witryn. Utwórz dodatkowe lokacje z wielu wywołań `CreateSite`.

##  <a name="getdefbtncode"></a>  COccManager::GetDefBtnCode

Wywołaj tę funkcję, aby określić, czy kontrolka jest domyślny przycisk.

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Obiekt okna zawierającego formant przycisku.

### <a name="return-value"></a>Wartość zwracana

Jeden z następujących wartości:

- Kontrolka DLGC_DEFPUSHBUTTON jest przycisk domyślny w oknie dialogowym.

- Kontrolka DLGC_UNDEFPUSHBUTTON nie jest przycisk domyślny w oknie dialogowym.

- **0** kontrolki nie jest przyciskiem.

##  <a name="isdialogmessage"></a>  COccManager::IsDialogMessage

Metoda wywoływana przez platformę, aby określić, czy komunikat jest przeznaczony dla określonego okna dialogowego, a jeśli tak jest, przetwarza komunikat.

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*pWndDlg*<br/>
Wskaźnik do okna dialogowego zamierzonym obiektem docelowym wiadomości.

*lpMsg*<br/>
Wskaźnik do `MSG` strukturę, która zawiera komunikat, który ma być zaznaczone.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli komunikat jest przetwarzany; w przeciwnym razie wartość zero.

### <a name="remarks"></a>Uwagi

Domyślne zachowanie `IsDialogMessage` sprawdzenia pod kątem komunikatów klawiatury i przekonwertować je na odpowiednim oknie dialogowym Opcje. Na przykład klawisz TAB, po naciśnięciu klawisza, wybiera następny formant lub grupy formantów.

Należy przesłonić tę funkcję, aby zapewnić zachowanie niestandardowe dla wiadomości wysyłanych do określonego okna dialogowego.

##  <a name="islabelcontrol"></a>  COccManager::IsLabelControl

Wywołaj tę funkcję, aby ustalić, czy określony formant kontrolkę typu etykieta.

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do okna zawierającego kontrolkę.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli kontrolka ma etykietę; w przeciwnym razie wartość zero

### <a name="remarks"></a>Uwagi

Formant etykiety jest taki, który zachowuje się jak etykietę dla dowolnych formant jest dalej w kolejności.

##  <a name="ismatchingmnemonic"></a>  COccManager::IsMatchingMnemonic

Wywołaj tę funkcję, aby określić, jeśli bieżący skrót klawiszowy architekturze i językowi reprezentowana przez kontrolkę.

```
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,
    LPMSG lpMsg);

static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do okna zawierającego kontrolkę.

*lpMsg*<br/>
Wskaźnik do komunikatu zawierającego mnemonik do dopasowania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli mnemonik pasuje do kontroli. w przeciwnym razie wartość zero

### <a name="remarks"></a>Uwagi

##  <a name="onevent"></a>  COccManager::OnEvent

Metoda wywoływana przez platformę, by obsłużyć określonego zdarzenia.

```
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,
    UINT idCtrl,
    AFX_EVENT* pEvent,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parametry

*pCmdTarget*<br/>
Wskaźnik do `CCmdTarget` obiektu próby obsługi zdarzeń

*idCtrl*<br/>
Identyfikator zasobu formantu.

*pEvent*<br/>
Przetwarzanego zdarzenia.

*pHandlerInfo*<br/>
Jeśli nie ma wartość NULL, `OnEvent` wypełnia `pTarget` i `pmf` członkowie `AFX_CMDHANDLERINFO` struktury zamiast wysyłania polecenia. Zazwyczaj ten parametr powinien mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli zdarzenie został obsłużony, w przeciwnym razie wartość zero.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby dostosować domyślny proces obsługi zdarzeń.

##  <a name="precreatedialog"></a>  COccManager::PreCreateDialog

Metoda wywoływana przez platformę, by przetworzyć szablonu okna dialogowego dla formantów ActiveX przed utworzeniem rzeczywistych okno dialogowe.

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
`_AFX_OCC_DIALOG_INFO` Struktura zawierająca informacje na temat szablonu okna dialogowego i żadnych formantów ActiveX hostowanych przez okno dialogowe.

*pOrigTemplate*<br/>
Wskaźnik do szablonu okna dialogowego do użycia podczas tworzenia okna dialogowego.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury szablonu okna dialogowego użyty do utworzenia okna dialogowego.

### <a name="remarks"></a>Uwagi

Domyślne zachowanie wywołuje `SplitDialogTemplate`, określająca, w przypadku dowolnego ActiveX kontroluje obecne, a następnie zwraca szablonu wynikowego okna dialogowego.

Należy przesłonić tę funkcję, aby dostosować proces tworzenia kontrolki hostingu ActiveX okno dialogowe.

##  <a name="postcreatedialog"></a>  COccManager::PostCreateDialog

Metoda wywoływana przez platformę, aby zwolnić pamięć przydzieloną szablonu okna dialogowego.

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
`_AFX_OCC_DIALOG_INFO` Struktura zawierająca informacje na temat szablonu okna dialogowego i żadnych formantów ActiveX hostowanych przez okno dialogowe.

### <a name="remarks"></a>Uwagi

Ta pamięć została przydzielona przez wywołanie `SplitDialogTemplate`i została użyta dla dowolnej hostowanej kontrolek ActiveX w oknie dialogowym.

Należy przesłonić tę funkcję, aby dostosować proces czyszczenia wszelkie zasoby używane przez obiekt okno dialogowe.

##  <a name="setdefaultbutton"></a>  COccManager::SetDefaultButton

Wywołaj tę funkcję, aby ustawić kontroli jako przycisk domyślny.

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do okna zawierającego kontrolkę.

*bPoziom domyślny*<br/>
Wartość różną od zera, jeśli kontrolka powinna stać się przycisk domyślny; w przeciwnym razie wartość zero.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Kontrolka musi mieć OLEMISC_ACTSLIKEBUTTON stan-bitowego zestawu. Aby uzyskać więcej informacji na temat flagi OLEMISC, zobacz [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) tematu w zestawie Windows SDK.

##  <a name="splitdialogtemplate"></a>  COccManager::SplitDialogTemplate

Metoda wywoływana przez platformę, by podziału kontrolki ActiveX ze wspólnych formantów okna dialogowego.

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>Parametry

*pTemplate*<br/>
Wskaźnik do szablonu okna dialogowego do badania.

*ppOleDlgItems*<br/>
Lista wskaźników do okna dialogowego pole elementów, które są formantów ActiveX.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury szablonu okna dialogowego zawierającego tylko formanty ActiveX nie. Jeśli istnieją Brak kontrolek ActiveX, zwracana jest wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli zostaną znalezione wszystkie kontrolki ActiveX, szablon jest analizowany i jest tworzony jest nowy szablon, zawierający tylko formanty ActiveX nie. Wszystkie kontrolki ActiveX w trakcie tego procesu są dodawane do *ppOleDlgItems*.

W przypadku brak kontrolek ActiveX w szablonie, zwracana jest wartość NULL *.*

> [!NOTE]
>  Pamięć przydzielona dla nowego szablonu jest zwalniana w `PostCreateDialog` funkcji.

Należy przesłonić tę funkcję, aby dostosować ten proces.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleControlSite](../../mfc/reference/colecontrolsite-class.md)<br/>
[Klasa COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)
