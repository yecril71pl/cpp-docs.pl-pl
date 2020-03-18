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
ms.openlocfilehash: c2a49e3396879e5f1e0864ab5342b57541c6b36c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416761"
---
# <a name="coccmanager-class"></a>Klasa COccManager

Zarządza różnymi lokacjami kontrolek niestandardowych; zaimplementowane przez `COleControlContainer` i `COleControlSite` obiektów.

## <a name="syntax"></a>Składnia

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COccManager:: iscontainerer](#createcontainer)|Tworzy obiekt `COleContainer`.|
|[COccManager::CreateDlgControls](#createdlgcontrols)|Tworzy kontrolki ActiveX hostowane przez skojarzony obiekt `COleContainer`.|
|[COccManager:: issite](#createsite)|Tworzy obiekt `COleClientSite`.|
|[COccManager::GetDefBtnCode](#getdefbtncode)|Pobiera kod przycisku domyślnego.|
|[COccManager::IsDialogMessage](#isdialogmessage)|Określa docelowy komunikat okna dialogowego.|
|[COccManager::IsLabelControl](#islabelcontrol)|Określa, czy określony formant jest formantem etykiety.|
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Określa, czy bieżąca wartość jest zgodna z parametrem określonej kontrolki.|
|[COccManager:: OnEvent](#onevent)|Próbuje obsłużyć określone zdarzenie.|
|[COccManager::P ostCreateDialog](#postcreatedialog)|Zwalnia zasoby przydzieloną podczas tworzenia okna dialogowego.|
|[COccManager::P reCreateDialog](#precreatedialog)|Przetwarza szablon okna dialogowego dla formantów ActiveX.|
|[COccManager::SetDefaultButton](#setdefaultbutton)|Przełącza domyślny stan określonej kontrolki.|
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|Oddziela wszystkie istniejące kontrolki ActiveX z formantów wspólnych w określonym szablonie okna dialogowego.|

## <a name="remarks"></a>Uwagi

Klasa bazowa, `CNoTrackObject`, jest nieudokumentowaną klasą bazową (znajdującą się w AFXTLS. H). Przeznaczone do użycia przez strukturę MFC, klasy pochodne klasy `CNoTrackObject` są wykluczone z wykrywania przecieków pamięci. Nie zaleca się wyprowadzania bezpośrednio z `CNoTrackObject`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxocc. h

##  <a name="createcontainer"></a>COccManager:: iscontainerer

Wywoływane przez platformę w celu utworzenia kontenera kontrolek.

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do obiektu okna skojarzonego z kontenerem lokacji niestandardowej.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do nowo utworzonego kontenera; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tworzenia niestandardowych witryn, zobacz [COleControlContainer:: AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).

##  <a name="createdlgcontrols"></a>COccManager::CreateDlgControls

Wywołaj tę funkcję, aby utworzyć kontrolki ActiveX określone przez parametr *pOccDialogInfo* .

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
Nazwa tworzonego zasobu.

*pOccDialogInfo*<br/>
Wskaźnik do szablonu okna dialogowego służącego do tworzenia obiektu okna dialogowego.

*lpResource*<br/>
Wskaźnik do zasobu.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli formant został utworzony pomyślnie; w przeciwnym razie zero.

##  <a name="createsite"></a>COccManager:: issite

Wywoływane przez platformę, aby utworzyć witrynę kontrolki hostowaną przez kontener wskazywany przez *pCtrlCont*.

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parametry

*pCtrlCont*<br/>
Wskaźnik do kontenera sterowania hostującym nową lokację sterowania.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do nowo utworzonej lokacji sterowania.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję, aby utworzyć niestandardową lokację kontrolną przy użyciu klasy pochodnej [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

Każdy kontener sterowania może obsługiwać wiele lokacji. Utwórz dodatkowe lokacje z wieloma wywołaniami do `CreateSite`.

##  <a name="getdefbtncode"></a>COccManager::GetDefBtnCode

Wywołaj tę funkcję, aby określić, czy formant jest domyślnym przyciskiem wypchnięcia.

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Obiekt window zawierający formant Button.

### <a name="return-value"></a>Wartość zwrócona

Jedna z następujących wartości:

- Formant DLGC_DEFPUSHBUTTON jest domyślnym przyciskiem w oknie dialogowym.

- Formant DLGC_UNDEFPUSHBUTTON nie jest domyślnym przyciskiem w oknie dialogowym.

- **0** kontrolka nie jest przyciskiem.

##  <a name="isdialogmessage"></a>COccManager::IsDialogMessage

Wywoływane przez platformę, aby określić, czy komunikat jest przeznaczony dla określonego okna dialogowego i, jeśli jest, przetwarza komunikat.

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*pWndDlg*<br/>
Wskaźnik do zamierzonego docelowego okna dialogowego komunikatu.

*lpMsg*<br/>
Wskaźnik do struktury `MSG`, która zawiera komunikat, który ma zostać sprawdzony.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli komunikat jest przetwarzany; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Domyślnym zachowaniem `IsDialogMessage` jest wyszukanie komunikatów z klawiatury i przekształcenie ich w wybrane dla odpowiedniego okna dialogowego. Na przykład klawisz TAB, po naciśnięciu, wybiera następną kontrolkę lub grupę kontrolek.

Zastąp tę funkcję, aby zapewnić niestandardowe zachowanie komunikatów wysyłanych do określonego okna dialogowego.

##  <a name="islabelcontrol"></a>COccManager::IsLabelControl

Wywołaj tę funkcję, aby określić, czy określony formant jest formantem etykiety.

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do okna zawierającego kontrolkę.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli formant jest etykietą; w przeciwnym razie zero

### <a name="remarks"></a>Uwagi

Kontrolka etykieta jest taka, która działa jak etykieta dla każdej kontrolki w kolejności.

##  <a name="ismatchingmnemonic"></a>COccManager::IsMatchingMnemonic

Wywołaj tę funkcję, aby określić, czy bieżąca wartość pasuje do reprezentowanej przez formant.

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
Wskaźnik do komunikatu zawierającego element, który ma być zgodny.

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli parametr jest zgodny z kontrolką; w przeciwnym razie zero

### <a name="remarks"></a>Uwagi

##  <a name="onevent"></a>COccManager:: OnEvent

Wywoływane przez platformę, aby obsłużyć określone zdarzenie.

```
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,
    UINT idCtrl,
    AFX_EVENT* pEvent,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parametry

*pCmdTarget*<br/>
Wskaźnik do obiektu `CCmdTarget` próbującego obsłużyć zdarzenie

*idCtrl*<br/>
Identyfikator zasobu formantu.

*pEvent*<br/>
Obsługiwane zdarzenie.

*pHandlerInfo*<br/>
Jeśli nie ma wartości NULL, `OnEvent` wypełnia `pTarget` i `pmf` elementów członkowskich struktury `AFX_CMDHANDLERINFO` zamiast wysyłania polecenia. Zazwyczaj ten parametr powinien mieć wartość NULL.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli zdarzenie zostało obsłużone, w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby dostosować domyślny proces obsługi zdarzeń.

##  <a name="precreatedialog"></a>COccManager::P reCreateDialog

Wywoływane przez platformę, aby przetworzyć szablon okna dialogowego dla formantów ActiveX przed utworzeniem rzeczywistego okna dialogowego.

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
Struktura `_AFX_OCC_DIALOG_INFO` zawierająca informacje o szablonie okna dialogowego i wszystkich kontrolkach ActiveX hostowanych przez okno dialogowe.

*pOrigTemplate*<br/>
Wskaźnik do szablonu okna dialogowego, który ma zostać użyty podczas tworzenia okna dialogowego.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do struktury szablonu okna dialogowego używany do tworzenia okna dialogowego.

### <a name="remarks"></a>Uwagi

Domyślne zachowanie wywołuje `SplitDialogTemplate`, określając, czy istnieją jakiekolwiek kontrolki ActiveX, a następnie zwraca wynikowy szablon okna dialogowego.

Zastąp tę funkcję, aby dostosować proces tworzenia okna dialogowego obsługującego kontrolki ActiveX.

##  <a name="postcreatedialog"></a>COccManager::P ostCreateDialog

Wywoływane przez platformę, aby zwolnić pamięć przydzieloną dla szablonu okna dialogowego.

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
Struktura `_AFX_OCC_DIALOG_INFO` zawierająca informacje o szablonie okna dialogowego i wszystkich kontrolkach ActiveX hostowanych przez okno dialogowe.

### <a name="remarks"></a>Uwagi

Ta pamięć została przypisana przez wywołanie do `SplitDialogTemplate`i została użyta dla wszystkich obsługiwanych formantów ActiveX w oknie dialogowym.

Przesłoń tę funkcję, aby dostosować proces czyszczenia wszystkich zasobów używanych przez obiekt okna dialogowego.

##  <a name="setdefaultbutton"></a>COccManager::SetDefaultButton

Wywołaj tę funkcję, aby ustawić kontrolkę jako przycisk domyślny.

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do okna zawierającego kontrolkę.

*bDefault*<br/>
Różne od zera, jeśli formant powinien stać się przyciskiem domyślnym; w przeciwnym razie zero.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Kontrolka musi mieć ustawiony bit stanu OLEMISC_ACTSLIKEBUTTON. Więcej informacji na temat flag OLEMISC można znaleźć w temacie [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) w Windows SDK.

##  <a name="splitdialogtemplate"></a>COccManager::SplitDialogTemplate

Wywoływane przez platformę, by podzielić kontrolki ActiveX z wspólnych kontrolek dialogowych.

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>Parametry

*pTemplate*<br/>
Wskaźnik do szablonu okna dialogowego, który ma zostać zbadany.

*ppOleDlgItems*<br/>
Lista wskaźników do elementów okna dialogowego, które są kontrolkami ActiveX.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do struktury szablonu okna dialogowego zawierającego tylko kontrolki nieactivex. Jeśli kontrolki ActiveX nie są obecne, zwracana jest wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli zostaną znalezione jakiekolwiek kontrolki ActiveX, szablon zostanie przeanalizowany i zostanie utworzony nowy szablon zawierający tylko kontrolki niebędące kontrolkami ActiveX. Wszystkie kontrolki ActiveX Znalezione w trakcie tego procesu są dodawane do *ppOleDlgItems*.

Jeśli w szablonie nie ma żadnych kontrolek ActiveX, zwracana jest wartość NULL *.*

> [!NOTE]
>  Pamięć przydzieloną dla nowego szablonu jest zwalniana w funkcji `PostCreateDialog`.

Zastąp tę funkcję, aby dostosować ten proces.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleControlSite](../../mfc/reference/colecontrolsite-class.md)<br/>
[Klasa COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)
