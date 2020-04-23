---
title: Klasa COleControlSite
ms.date: 11/04/2016
f1_keywords:
- COleControlSite
- AFXOCC/COleControlSite
- AFXOCC/COleControlSite::COleControlSite
- AFXOCC/COleControlSite::BindDefaultProperty
- AFXOCC/COleControlSite::BindProperty
- AFXOCC/COleControlSite::CreateControl
- AFXOCC/COleControlSite::DestroyControl
- AFXOCC/COleControlSite::DoVerb
- AFXOCC/COleControlSite::EnableDSC
- AFXOCC/COleControlSite::EnableWindow
- AFXOCC/COleControlSite::FreezeEvents
- AFXOCC/COleControlSite::GetDefBtnCode
- AFXOCC/COleControlSite::GetDlgCtrlID
- AFXOCC/COleControlSite::GetEventIID
- AFXOCC/COleControlSite::GetExStyle
- AFXOCC/COleControlSite::GetProperty
- AFXOCC/COleControlSite::GetStyle
- AFXOCC/COleControlSite::GetWindowText
- AFXOCC/COleControlSite::InvokeHelper
- AFXOCC/COleControlSite::InvokeHelperV
- AFXOCC/COleControlSite::IsDefaultButton
- AFXOCC/COleControlSite::IsWindowEnabled
- AFXOCC/COleControlSite::ModifyStyle
- AFXOCC/COleControlSite::ModifyStyleEx
- AFXOCC/COleControlSite::MoveWindow
- AFXOCC/COleControlSite::QuickActivate
- AFXOCC/COleControlSite::SafeSetProperty
- AFXOCC/COleControlSite::SetDefaultButton
- AFXOCC/COleControlSite::SetDlgCtrlID
- AFXOCC/COleControlSite::SetFocus
- AFXOCC/COleControlSite::SetProperty
- AFXOCC/COleControlSite::SetPropertyV
- AFXOCC/COleControlSite::SetWindowPos
- AFXOCC/COleControlSite::SetWindowText
- AFXOCC/COleControlSite::ShowWindow
- AFXOCC/COleControlSite::GetControlInfo
- AFXOCC/COleControlSite::m_bIsWindowless
- AFXOCC/COleControlSite::m_ctlInfo
- AFXOCC/COleControlSite::m_dwEventSink
- AFXOCC/COleControlSite::m_dwMiscStatus
- AFXOCC/COleControlSite::m_dwPropNotifySink
- AFXOCC/COleControlSite::m_dwStyle
- AFXOCC/COleControlSite::m_hWnd
- AFXOCC/COleControlSite::m_iidEvents
- AFXOCC/COleControlSite::m_nID
- AFXOCC/COleControlSite::m_pActiveObject
- AFXOCC/COleControlSite::m_pCtrlCont
- AFXOCC/COleControlSite::m_pInPlaceObject
- AFXOCC/COleControlSite::m_pObject
- AFXOCC/COleControlSite::m_pWindowlessObject
- AFXOCC/COleControlSite::m_pWndCtrl
- AFXOCC/COleControlSite::m_rect
helpviewer_keywords:
- COleControlSite [MFC], COleControlSite
- COleControlSite [MFC], BindDefaultProperty
- COleControlSite [MFC], BindProperty
- COleControlSite [MFC], CreateControl
- COleControlSite [MFC], DestroyControl
- COleControlSite [MFC], DoVerb
- COleControlSite [MFC], EnableDSC
- COleControlSite [MFC], EnableWindow
- COleControlSite [MFC], FreezeEvents
- COleControlSite [MFC], GetDefBtnCode
- COleControlSite [MFC], GetDlgCtrlID
- COleControlSite [MFC], GetEventIID
- COleControlSite [MFC], GetExStyle
- COleControlSite [MFC], GetProperty
- COleControlSite [MFC], GetStyle
- COleControlSite [MFC], GetWindowText
- COleControlSite [MFC], InvokeHelper
- COleControlSite [MFC], InvokeHelperV
- COleControlSite [MFC], IsDefaultButton
- COleControlSite [MFC], IsWindowEnabled
- COleControlSite [MFC], ModifyStyle
- COleControlSite [MFC], ModifyStyleEx
- COleControlSite [MFC], MoveWindow
- COleControlSite [MFC], QuickActivate
- COleControlSite [MFC], SafeSetProperty
- COleControlSite [MFC], SetDefaultButton
- COleControlSite [MFC], SetDlgCtrlID
- COleControlSite [MFC], SetFocus
- COleControlSite [MFC], SetProperty
- COleControlSite [MFC], SetPropertyV
- COleControlSite [MFC], SetWindowPos
- COleControlSite [MFC], SetWindowText
- COleControlSite [MFC], ShowWindow
- COleControlSite [MFC], GetControlInfo
- COleControlSite [MFC], m_bIsWindowless
- COleControlSite [MFC], m_ctlInfo
- COleControlSite [MFC], m_dwEventSink
- COleControlSite [MFC], m_dwMiscStatus
- COleControlSite [MFC], m_dwPropNotifySink
- COleControlSite [MFC], m_dwStyle
- COleControlSite [MFC], m_hWnd
- COleControlSite [MFC], m_iidEvents
- COleControlSite [MFC], m_nID
- COleControlSite [MFC], m_pActiveObject
- COleControlSite [MFC], m_pCtrlCont
- COleControlSite [MFC], m_pInPlaceObject
- COleControlSite [MFC], m_pObject
- COleControlSite [MFC], m_pWindowlessObject
- COleControlSite [MFC], m_pWndCtrl
- COleControlSite [MFC], m_rect
ms.assetid: 43970644-5eab-434a-8ba6-56d144ff1e3f
ms.openlocfilehash: 90c41a1be1a66cdceebb3f045a98167e56b7cf4c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753944"
---
# <a name="colecontrolsite-class"></a>Klasa COleControlSite

Zapewnia obsługę niestandardowych interfejsów sterowania po stronie klienta.

## <a name="syntax"></a>Składnia

```
class COleControlSite : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleControlSite::COleControlSite](#colecontrolsite)|Konstruuje `COleControlSite` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|Wiąże domyślną właściwość hostowanego formantu ze źródłem danych.|
|[COleControlSite::BindProperty](#bindproperty)|Wiąże właściwość hostowanego formantu ze źródłem danych.|
|[COleControlSite::CreateControl](#createcontrol)|Tworzy hostowany formant ActiveX.|
|[COleControlSite: :DestroyControl](#destroycontrol)|Niszczy hostowany formant.|
|[COleControlSite: :DoVerb](#doverb)|Wykonuje określony zlecenie hostowanego formantu.|
|[COleControlSite::EnableDSC](#enabledsc)|Umożliwia pozyskiwanie danych dla witryny kontrolnej.|
|[COleControlSite::EnableWindow](#enablewindow)|Włącza witrynę sterowania.|
|[COleControlSite::FreezeEvents](#freezeevents)|Określa, czy witryna kontrolna akceptuje zdarzenia.|
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|Pobiera domyślny kod przycisku dla hostowanego formantu.|
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|Pobiera identyfikator formantu.|
|[COleControlSite::GetEventiID](#geteventiid)|Pobiera identyfikator interfejsu zdarzenia dla hostowanego formantu.|
|[COleControlSite::GetExStyle](#getexstyle)|Pobiera rozszerzone style witryny kontrolnej.|
|[COleControlSite::GetProperty](#getproperty)|Pobiera określoną właściwość hostowanego formantu.|
|[COleControlSite::GetStyle](#getstyle)|Pobiera style witryny kontrolnej.|
|[COleControlSite::GetWindowTekst](#getwindowtext)|Pobiera tekst hostowanego formantu.|
|[COleControlSite::InvokeHelper](#invokehelper)|Wywołać określoną metodę hostowanego formantu.|
|[COleControlSite::InvokeHelperV](#invokehelperv)|Wywołać określoną metodę hostowanego formantu z listy zmiennych argumentów.|
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|Określa, czy formant jest przyciskiem domyślnym w oknie.|
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|Sprawdza widoczny stan witryny kontrolnej.|
|[COleControlSite::ModifyStyle](#modifystyle)|Modyfikuje bieżące rozszerzone style witryny kontrolnej.|
|[COleControlSite::ModifyStyleEx](#modifystyleex)|Modyfikuje bieżące style witryny kontrolnej.|
|[COleControlSite::MoveWindow](#movewindow)|Zmienia położenie witryny sterowania.|
|[COleControlSite::QuickActivate](#quickactivate)|Szybkie aktywowanie hostowanego formantu.|
|[COleControlSite::SafeSetProperty](#safesetproperty)|Ustawia właściwość lub metodę formantu bez szansy zgłaszania wyjątku.|
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|Ustawia przycisk domyślny w oknie.|
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|Pobiera identyfikator formantu.|
|[COleControlSite::SetFocus](#setfocus)|Ustawia fokus na stronie kontrolnej.|
|[COleControlSite::Właściwości SetProperty](#setproperty)|Ustawia określoną właściwość hostowanego formantu.|
|[COleControlSite::SetPropertyV](#setpropertyv)|Ustawia określoną właściwość hostowanego formantu z listą argumentów zmiennych.|
|[COleControlSite::SetWindowPos](#setwindowpos)|Ustawia położenie witryny sterowania.|
|[COleControlSite::SetWindowText](#setwindowtext)|Ustawia tekst hostowanego formantu.|
|[COleControlSite::ShowWindow](#showwindow)|Pokazuje lub ukrywa witrynę formantu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleControlSite::GetControlInfo](#getcontrolinfo)|Pobiera informacje o klawiaturze i mnemoniki dla hostowanego formantu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|Określa, czy hostowany formant jest formantem bez okien.|
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|Zawiera informacje na temat obsługi klawiatury dla formantu.|
|[COleControlSite::m_dwEventSink](#m_dweventsink)|Plik cookie punktu połączenia formantu.|
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|Różne stany dla hostowanego formantu.|
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|Plik `IPropertyNotifySink` cookie formantu.|
|[COleControlSite::m_dwStyle](#m_dwstyle)|Style hostowanego formantu.|
|[COleControlSite::m_hWnd](#m_hwnd)|Uchwyt witryny sterowania.|
|[COleControlSite::m_iidEvents](#m_iidevents)|Identyfikator interfejsu zdarzenia dla hostowanego formantu.|
|[COleControlSite::m_nID](#m_nid)|Identyfikator hostowanego formantu.|
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|Wskaźnik do `IOleInPlaceActiveObject` obiektu hostowanego formantu.|
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|Kontener hostowanego formantu.|
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|Wskaźnik do `IOleInPlaceObject` obiektu hostowanego formantu.|
|[COleControlSite::m_pObject](#m_pobject)|Wskaźnik do `IOleObjectInterface` interfejsu formantu.|
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|Wskaźnik do `IOleInPlaceObjectWindowless` interfejsu formantu.|
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|Wskaźnik do obiektu okna dla hostowanego formantu.|
|[COleControlSite::m_rect](#m_rect)|Wymiary miejsca kontroli.|

## <a name="remarks"></a>Uwagi

Ta obsługa jest podstawowym środkiem, za pomocą którego osadzony formant ActiveX uzyskuje informacje o lokalizacji i zasięgu swojej witryny wyświetlania, jego monikera, interfejsu użytkownika, jego właściwości otoczenia i innych zasobów dostarczanych przez jego kontener. `COleControlSite`w pełni implementuje [interfejsy IOleControlSite](/windows/win32/api/ocidl/nn-ocidl-iolecontrolsite), [IOleInPlaCeSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite) `INotifyDBEvents`, [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), `IBoundObjectSite`, [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md) interfaces. Ponadto interfejs IDispatch (zapewniając obsługę właściwości otoczenia i pochłaniacze zdarzeń) jest również zaimplementowana.

Aby utworzyć witrynę kontrolną ActiveX przy użyciu `COleControlSite`, wyprowadz klasę z . `COleControlSite` W `CWnd`klasie pochodnej kontenera (na przykład okno dialogowe) `CWnd::CreateControlSite` zastąpić funkcję.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlSite`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxocc.h

## <a name="colecontrolsitebinddefaultproperty"></a><a name="binddefaultproperty"></a>COleControlSite::BindDefaultProperty

Wiąże domyślną właściwość simple bound obiektu wywołującego, oznaczoną w bibliotece typów, z kursorem, który jest zdefiniowany przez właściwości DataSource, UserName, Password i SQL formantu źródła danych.

```
virtual void BindDefaultProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    LPCTSTR szFieldName,
    CWnd* pDSCWnd);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Określa identyfikator DISPID właściwości na formancie powiązanym z danymi, który ma być powiązany z formantem źródła danych.

*vtProp (vtProp)*<br/>
Określa typ właściwości, która ma być powiązana — na przykład VT_BSTR, VT_VARIANT itd.

*szFieldName (Nazwa główna)*<br/>
Określa nazwę kolumny w kursorze dostarczonym przez formant źródła danych, z którą będzie powiązana właściwość.

*pDSCWnd*<br/>
Wskaźnik do `CWnd`obiektu pochodnego, który obsługuje formant źródła danych, do którego będzie powiązana właściwość.

### <a name="remarks"></a>Uwagi

Obiekt, `CWnd` na którym można wywołać tę funkcję, musi być formantem związanym z danymi.

## <a name="colecontrolsitebindproperty"></a><a name="bindproperty"></a>COleControlSite::BindProperty

Wiąże simple bound właściwości obiektu wywołującego, zgodnie z oznaczeniem w bibliotece typów, do podstawowego kursora, który jest zdefiniowany przez DataSource, UserName, Hasło i SQL właściwości kontroli źródła danych.

```
virtual void BindProperty(
    DISPID dwDispId,
    CWnd* pWndDSC);
```

### <a name="parameters"></a>Parametry

*dwDispId*<br/>
Określa identyfikator DISPID właściwości na formancie powiązanym z danymi, który ma być powiązany z formantem źródła danych.

*pWndDSC*<br/>
Wskaźnik do `CWnd`obiektu pochodnego, który obsługuje formant źródła danych, do którego będzie powiązana właściwość.

### <a name="remarks"></a>Uwagi

Obiekt, `CWnd` na którym można wywołać tę funkcję, musi być formantem związanym z danymi.

## <a name="colecontrolsitecolecontrolsite"></a><a name="colecontrolsite"></a>COleControlSite::COleControlSite

Konstruuje `COleControlSite` nowy obiekt.

```
explicit COleControlSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parametry

*pCtrlCont (Kont.*<br/>
Wskaźnik do kontenera formantu (który reprezentuje okno, które obsługuje AtiveX kontroli).

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana przez [funkcję COccManager::CreateContainer.](../../mfc/reference/coccmanager-class.md#createcontainer) Aby uzyskać więcej informacji na temat dostosowywania tworzenia kontenerów, zobacz [COccManager::CreateSite](../../mfc/reference/coccmanager-class.md#createsite).

## <a name="colecontrolsitecreatecontrol"></a><a name="createcontrol"></a>COleControlSite::CreateControl

Tworzy formant ActiveX, obsługiwany `COleControlSite` przez obiekt.

```
virtual HRESULT CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist = NULL,
    BOOL bStorage = FALSE,
    BSTR bstrLicKey = NULL);

virtual HRESULT CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist = NULL,
    BOOL bStorage = FALSE,
    BSTR bstrLicKey = NULL);
```

### <a name="parameters"></a>Parametry

*pWndCtrl (właśc.*<br/>
Wskaźnik do obiektu okna reprezentującego formant.

*Clsid*<br/>
Unikatowy identyfikator klasy formantu.

*lpszWindowName*<br/>
Wskaźnik do tekstu, który ma być wyświetlany w formancie. Ustawia wartość winodw's Caption lub Text właściwości (jeśli istnieje).

*Dwstyle*<br/>
Style systemu Windows. Dostępne style są wymienione w sekcji **Uwagi.**

*Rect*<br/>
Określa rozmiar i położenie formantu. Może to być `CRect` obiekt lub `RECT` struktura.

*Nid*<br/>
Określa identyfikator okna podrzędnego formantu.

*pPersist*<br/>
Wskaźnik do `CFile` zawierającego stan trwały dla formantu. Wartością domyślną jest NULL, co oznacza, że formant inicjuje się bez przywracania jego stanu z dowolnego magazynu trwałego. Jeśli nie NULL, powinien być `CFile`wskaźnikiem do obiektu pochodnego, który zawiera trwałe dane formantu, w postaci strumienia lub magazynu. Te dane mogły zostać zapisane podczas poprzedniej aktywacji klienta. Może `CFile` zawierać inne dane, ale musi mieć ustawiony wskaźnik odczytu i zapisu na pierwszy `CreateControl`bajt danych trwałych w czasie wywołania .

*bSporównania*<br/>
Wskazuje, czy dane w *pPersist* powinny `IStorage` `IStream` być interpretowane jako lub danych. Jeśli dane w *pPersist* jest magazyn, *bSprzeczynienie* powinno być prawda. Jeśli dane w *pPersist* jest strumień, *bSprzeczynienie* powinno być FALSE. Wartością domyślną jest FAŁSZ.

*klawisz bstrLicKey*<br/>
Opcjonalne dane klucza licencyjnego. Te dane są potrzebne tylko do tworzenia formantów, które wymagają klucza licencji w czasie wykonywania. Jeśli formant obsługuje licencjonowanie, należy podać klucz licencji do tworzenia formantu, aby zakończyć się pomyślnie. Wartością domyślną jest NULL.

*Ppt*<br/>
Wskaźnik do `POINT` struktury, która zawiera lewy górny róg formantu. Wielkość formantu zależy od wartości *psize*. *Ppt* i *psize* wartości są opcjonalną metodą określania rozmiaru i położenia opf formantu.

*psize (psize)*<br/>
Wskaźnik do `SIZE` struktury, która zawiera rozmiar formantu. Lewy górny róg jest określany przez wartość *ppt*. *Ppt* i *psize* wartości są opcjonalną metodą określania rozmiaru i położenia opf formantu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Tylko podzbiór flag systemu Windows *dwStyle* są obsługiwane przez: `CreateControl`

- WS_VISIBLE Tworzy okno, które jest początkowo widoczne. Wymagane, jeśli chcesz, aby formant był widoczny natychmiast, jak zwykłe okna.

- WS_DISABLED Tworzy okno, które jest początkowo wyłączone. Wyłączone okno nie może odbierać danych wejściowych od użytkownika. Można ustawić, jeśli formant ma Enabled właściwości.

- WS_BORDER Tworzy okno z cienką linią obramowania. Można ustawić, jeśli formant ma BorderStyle właściwości.

- WS_GROUP Określa pierwszą kontrolę grupy formantów. Użytkownik może zmienić fokus klawiatury z jednego formantu w grupie do następnego za pomocą klawiszy kierunku. Wszystkie formanty zdefiniowane za pomocą stylu WS_GROUP po pierwszym formancie należą do tej samej grupy. Następny formant ze stylem WS_GROUP kończy grupę i rozpoczyna następną grupę.

- WS_TABSTOP Określa formant, który może odbierać fokus klawiatury, gdy użytkownik naciśnie klawisz TAB. Naciśnięcie klawisza TAB powoduje zmianę fokusu klawiatury na następną kontrolkę stylu WS_TABSTOP.

Użyj drugiego przeciążenia, aby utworzyć domyślne formanty o rozmiarze.

## <a name="colecontrolsitedestroycontrol"></a><a name="destroycontrol"></a>COleControlSite: :DestroyControl

Niszczy `COleControlSite` obiekt.

```
virtual BOOL DestroyControl();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po zakończeniu obiekt jest zwalniany z pamięci, a wszystkie wskaźniki do obiektu nie są już prawidłowe.

## <a name="colecontrolsitedoverb"></a><a name="doverb"></a>COleControlSite: :DoVerb

Wykonuje określony zlecenie.

```
virtual HRESULT DoVerb(
    LONG nVerb,
    LPMSG lpMsg = NULL);
```

### <a name="parameters"></a>Parametry

*nWerb*<br/>
Określa zlecenie do wykonania. Może zawierać jedną z następujących czynności:

|Wartość|Znaczenie|Symbol|
|-----------|-------------|------------|
|0|Primary — Zlecenie|OLEIVERB_PRIMARY|
|-1|Czasownik wtórny|(Brak)|
|1|Wyświetla obiekt do edycji.|OLEIVERB_SHOW|
|-2|Edytuje element w osobnym oknie.|OLEIVERB_OPEN|
|-3|Ukrywa obiekt.|OLEIVERB_HIDE|
|-4|Aktywuje formant w miejscu.|OLEIVERB_UIACTIVATE|
|-5|Aktywuje formant w miejscu, bez dodatkowych elementów interfejsu użytkownika.|OLEIVERB_INPLACEACTIVATE|
|-7|Wyświetl właściwości formantu.|OLEIVERB_PROPERTIES|

*lpMsg*<br/>
Wskaźnik do wiadomości, która spowodowała, że element ma być aktywowany.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje bezpośrednio za `IOleObject` pośrednictwem interfejsu formantu, aby wykonać określony zlecenie. Jeśli wyjątek jest zgłaszany w wyniku tego wywołania funkcji, zwracany jest kod błędu HRESULT.

Aby uzyskać więcej informacji, zobacz [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) w windows SDK.

## <a name="colecontrolsiteenabledsc"></a><a name="enabledsc"></a>COleControlSite::EnableDSC

Umożliwia pozyskiwanie danych dla witryny kontrolnej.

```
virtual void EnableDSC();
```

### <a name="remarks"></a>Uwagi

Wywoływane przez platformę, aby włączyć i zainicjować pozyskiwanie danych dla witryny kontroli. Zastąd w tej funkcji należy wykonać niestandardowe zachowanie.

## <a name="colecontrolsiteenablewindow"></a><a name="enablewindow"></a>COleControlSite::EnableWindow

Włącza lub wyłącza wprowadzanie danych wejściowych myszy i klawiatury w witrynie sterowania.

```
virtual BOOL EnableWindow(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
Określa, czy włączyć lub wyłączyć okno: PRAWDA, jeśli wejście okna ma być włączone, w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli okno było wcześniej wyłączone, w przeciwnym razie 0.

## <a name="colecontrolsitefreezeevents"></a><a name="freezeevents"></a>COleControlSite::FreezeEvents

Określa, czy witryna formantu będzie obsługiwać lub ignorować zdarzenia uruchamiane z formantu.

```cpp
void FreezeEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parametry

*bZamk.*<br/>
Określa, czy witryna formantu chce przestać akceptować zdarzenia. Nonzero, jeśli formant nie akceptuje zdarzeń; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Jeśli *bFreeze* jest TRUE, lokacja formantu żąda formantu, aby zatrzymać zdarzenia fring. Jeśli *bFreeze* jest FALSE, lokacja formantu żąda formantu, aby kontynuowaćpalania zdarzeń.

> [!NOTE]
> Formant nie jest wymagane, aby zatrzymać zdarzenia odpalania, jeśli jest to wymagane przez witrynę kontrolną. Może kontynuować wypalania, ale wszystkie kolejne zdarzenia zostaną zignorowane przez witrynę kontrolną.

## <a name="colecontrolsitegetcontrolinfo"></a><a name="getcontrolinfo"></a>COleControlSite::GetControlInfo

Pobiera informacje o mnemoniki klawiatury i zachowanie klawiatury formantu.

```cpp
void GetControlInfo();
```

### <a name="remarks"></a>Uwagi

Informacje są przechowywane w [COleControlSite::m_ctlInfo](#m_ctlinfo).

## <a name="colecontrolsitegetdefbtncode"></a><a name="getdefbtncode"></a>COleControlSite::GetDefBtnCode

Określa, czy formant jest domyślnym przyciskiem.

```
DWORD GetDefBtnCode();
```

### <a name="return-value"></a>Wartość zwracana

Może być jedną z następujących wartości:

- DLGC_DEFPUSHBUTTON Control jest przyciskiem domyślnym w oknie dialogowym.

- DLGC_UNDEFPUSHBUTTON Control nie jest przyciskiem domyślnym w oknie dialogowym.

- **0** Sterowanie nie jest przyciskiem.

## <a name="colecontrolsitegetdlgctrlid"></a><a name="getdlgctrlid"></a>COleControlSite::GetDlgCtrlID

Pobiera identyfikator formantu.

```
virtual int GetDlgCtrlID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator elementu okna dialogowego formantu.

## <a name="colecontrolsitegeteventiid"></a><a name="geteventiid"></a>COleControlSite::GetEventiID

Pobiera wskaźnik do domyślnego interfejsu zdarzenia formantu.

```
BOOL GetEventIID(IID* piid);
```

### <a name="parameters"></a>Parametry

*piid*<br/>
Wskaźnik do identyfikatora interfejsu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie, w przeciwnym razie 0. Jeśli się powiedzie, *piid* zawiera identyfikator interfejsu dla domyślnego interfejsu zdarzenia formantu.

## <a name="colecontrolsitegetexstyle"></a><a name="getexstyle"></a>COleControlSite::GetExStyle

Pobiera rozszerzone style okna.

```
virtual DWORD GetExStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozszerzone style okna sterowania.

### <a name="remarks"></a>Uwagi

Aby pobrać regularne style, zadzwoń [do COleControlSite::GetStyle](#getstyle).

## <a name="colecontrolsitegetproperty"></a><a name="getproperty"></a>COleControlSite::GetProperty

Pobiera właściwość formantu określona przez *dwDispID*.

```
virtual void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identyfikuje identyfikator wysyłki właściwości, znalezione w domyślnym `IDispatch` interfejsie formantu, które mają zostać pobrane.

*vtProp (vtProp)*<br/>
Określa typ właściwości, która ma zostać pobrana. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvProp*<br/>
Adres zmiennej, która otrzyma wartość właściwości. Musi być zgodny z typem określonym przez *vtProp*.

### <a name="remarks"></a>Uwagi

Wartość jest zwracana za pośrednictwem *pvProp*.

## <a name="colecontrolsitegetstyle"></a><a name="getstyle"></a>COleControlSite::GetStyle

Pobiera style witryny kontrolnej.

```
virtual DWORD GetStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Style okna.

### <a name="remarks"></a>Uwagi

Aby uzyskać listę możliwych wartości, zobacz [Style systemu Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles). Aby pobrać rozszerzone style witryny sterowania, zadzwoń do [COleControlSite::GetExStyle](#getexstyle).

## <a name="colecontrolsitegetwindowtext"></a><a name="getwindowtext"></a>COleControlSite::GetWindowTekst

Pobiera bieżący tekst formantu.

```
virtual void GetWindowText(CString& str) const;
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Odwołanie do `CString` obiektu, który zawiera bieżący tekst formantu.

### <a name="remarks"></a>Uwagi

Jeśli formant obsługuje caption stock właściwości, ta wartość jest zwracana. Jeśli caption stock właściwość nie jest obsługiwana, zwracana jest wartość dla Text właściwości.

## <a name="colecontrolsiteinvokehelper"></a><a name="invokehelper"></a>COleControlSite::InvokeHelper

Wywołuje metodę lub właściwość określoną przez *dwDispID*, w kontekście określonym przez *wFlags*.

```
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identyfikuje identyfikator wysyłki właściwości lub metody, znalezione w `IDispatch` interfejsie formantu, do wywołania.

*wFlags*<br/>
Flagi opisujące kontekst wywołania IDispatch::Invoke. Aby uzyskać możliwe wartości *wFlags,* zobacz `IDispatch::Invoke` w windows SDK.

*vtRet ( vtret )*<br/>
Określa typ zwracanej wartości. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvRet*<br/>
Adres zmiennej, która otrzyma wartość właściwości lub wartość zwracaną. Musi być zgodny z typem określonym przez *vtRet*.

*pbParamInfo*<br/>
Wskaźnik do ciągu bajtów zakończonych z wartością null określających typy parametrów następujących po *pbParamInfo*. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Lista zmiennych parametrów, typów określonych w *pbParamInfo*.

### <a name="remarks"></a>Uwagi

Parametr *pbParamInfo* określa typy parametrów przekazanych do metody lub właściwości. Lista zmiennych argumentów jest reprezentowana przez ... w deklaracji składni.

Ta funkcja konwertuje parametry na wartości VARIANTARG, a następnie wywołuje `IDispatch::Invoke` metodę na formancie. Jeśli wywołanie `IDispatch::Invoke` nie powiedzie się, ta funkcja zda wyjątek. Jeśli kod stanu `IDispatch::Invoke` zwrócony przez jest `DISP_E_EXCEPTION` `COleDispatchException` , ta funkcja zgłasza `COleException`obiekt, w przeciwnym razie rzuca .

## <a name="colecontrolsiteinvokehelperv"></a><a name="invokehelperv"></a>COleControlSite::InvokeHelperV

Wywołuje metodę lub właściwość określoną przez *dwDispID*, w kontekście określonym przez *wFlags*.

```
virtual void InvokeHelperV(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo,
    va_list argList);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identyfikuje identyfikator wysyłki właściwości lub metody, znalezione w `IDispatch` interfejsie formantu, do wywołania.

*wFlags*<br/>
Flagi opisujące kontekst wywołania IDispatch::Invoke.

*vtRet ( vtret )*<br/>
Określa typ zwracanej wartości. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvRet*<br/>
Adres zmiennej, która otrzyma wartość właściwości lub wartość zwracaną. Musi być zgodny z typem określonym przez *vtRet*.

*pbParamInfo*<br/>
Wskaźnik do ciągu bajtów zakończonych z wartością null określających typy parametrów następujących po *pbParamInfo*. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*argLista*<br/>
Wskaźnik do listy argumentów zmiennej.

### <a name="remarks"></a>Uwagi

Parametr *pbParamInfo* określa typy parametrów przekazanych do metody lub właściwości. Dodatkowe parametry dla wywoływana metody lub właściwości mogą być przekazywane przy użyciu *parametru va_list.*

Zazwyczaj ta funkcja jest `COleControlSite::InvokeHelper`wywoływana przez .

## <a name="colecontrolsiteisdefaultbutton"></a><a name="isdefaultbutton"></a>COleControlSite::IsDefaultButton

Określa, czy formant jest przyciskiem domyślnym.

```
BOOL IsDefaultButton();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli formant jest domyślny przycisk w oknie, w przeciwnym razie zero.

## <a name="colecontrolsiteiswindowenabled"></a><a name="iswindowenabled"></a>COleControlSite::IsWindowEnabled

Określa, czy witryna sterowania jest włączona.

```
virtual BOOL IsWindowEnabled() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli formant jest włączony, w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Wartość jest pobierana z właściwości włączono magazyn formantu.

## <a name="colecontrolsitem_biswindowless"></a><a name="m_biswindowless"></a>COleControlSite::m_bIsWindowless

Określa, czy obiekt jest formantem bez okien.

```
BOOL m_bIsWindowless;
```

### <a name="remarks"></a>Uwagi

Nonzero, jeśli formant nie ma okna, w przeciwnym razie zero.

## <a name="colecontrolsitem_ctlinfo"></a><a name="m_ctlinfo"></a>COleControlSite::m_ctlInfo

Informacje o sposobie obsługi wprowadzania danych przez klawiaturę przez formant.

```
CONTROLINFO m_ctlInfo;
```

### <a name="remarks"></a>Uwagi

Informacje te są przechowywane w strukturze [CONTROLINFO.](/windows/win32/api/ocidl/ns-ocidl-controlinfo)

## <a name="colecontrolsitem_dweventsink"></a><a name="m_dweventsink"></a>COleControlSite::m_dwEventSink

Zawiera plik cookie punktu połączenia z pochłaniania zdarzeń formantu.

```
DWORD m_dwEventSink;
```

## <a name="colecontrolsitem_dwmiscstatus"></a><a name="m_dwmiscstatus"></a>COleControlSite::m_dwMiscStatus

Zawiera różne informacje o formancie.

```
DWORD m_dwMiscStatus;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)w windows SDK.

## <a name="colecontrolsitem_dwpropnotifysink"></a><a name="m_dwpropnotifysink"></a>COleControlSite::m_dwPropNotifySink

Zawiera plik cookie [IPropertyNotifySink.](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)

```
DWORD m_dwPropNotifySink;
```

## <a name="colecontrolsitem_dwstyle"></a><a name="m_dwstyle"></a>COleControlSite::m_dwStyle

Zawiera style window formantu.

```
DWORD m_dwStyle;
```

## <a name="colecontrolsitem_hwnd"></a><a name="m_hwnd"></a>COleControlSite::m_hWnd

Zawiera HWND formantu lub NULL, jeśli formant jest bez okien.

```
HWND m_hWnd;
```

## <a name="colecontrolsitem_iidevents"></a><a name="m_iidevents"></a>COleControlSite::m_iidEvents

Zawiera identyfikator interfejsu domyślnego interfejsu ujścia zdarzeń formantu.

```
IID m_iidEvents;
```

## <a name="colecontrolsitem_nid"></a><a name="m_nid"></a>COleControlSite::m_nID

Zawiera identyfikator elementu okna dialogowego formantu.

```
UINT m_nID;
```

## <a name="colecontrolsitem_pactiveobject"></a><a name="m_pactiveobject"></a>COleControlSite::m_pActiveObject

Zawiera interfejs [IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) formantu.

```
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;
```

## <a name="colecontrolsitem_pctrlcont"></a><a name="m_pctrlcont"></a>COleControlSite::m_pCtrlCont

Zawiera kontener formantu (reprezentujący formularz).

```
COleControlContainer* m_pCtrlCont;
```

## <a name="colecontrolsitem_pinplaceobject"></a><a name="m_pinplaceobject"></a>COleControlSite::m_pInPlaceObject

`IOleInPlaceObject` Zawiera interfejs [IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) formantu.

```
LPOLEINPLACEOBJECT m_pInPlaceObject;
```

## <a name="colecontrolsitem_pobject"></a><a name="m_pobject"></a>COleControlSite::m_pObject

Zawiera `IOleObjectInterface` interfejs formantu.

```
LPOLEOBJECT m_pObject;
```

## <a name="colecontrolsitem_pwindowlessobject"></a><a name="m_pwindowlessobject"></a>COleControlSite::m_pWindowlessObject

Zawiera [interfejs IOleInPlaCeObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) formantu. `IOleInPlaceObjectWindowless`

```
IOleInPlaceObjectWindowless* m_pWindowlessObject;
```

## <a name="colecontrolsitem_pwndctrl"></a><a name="m_pwndctrl"></a>COleControlSite::m_pWndCtrl

Zawiera wskaźnik do `CWnd` obiektu, który reprezentuje sam formant.

```
CWnd* m_pWndCtrl;
```

## <a name="colecontrolsitem_rect"></a><a name="m_rect"></a>COleControlSite::m_rect

Zawiera granice formantu względem okna kontenera.

```
CRect m_rect;
```

## <a name="colecontrolsitemodifystyle"></a><a name="modifystyle"></a>COleControlSite::ModifyStyle

Modyfikuje style formantu.

```
virtual BOOL ModifyStyle(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*dwUsuł*<br/>
Style, które mają zostać usunięte z bieżących stylów okien.

*dwAdd*<br/>
Style, które mają zostać dodane z bieżących stylów okien.

*nPłgi*<br/>
Flagi pozycjonowania okien. Aby uzyskać listę możliwych wartości, zobacz [Funkcję SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli style są zmieniane, w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Właściwość włączona zostanie zmodyfikowana w celu dopasowania do ustawienia dla WS_DISABLED. Właściwość styl graniczny magazynu formantu zostanie zmodyfikowana w celu dopasowania do żądanego ustawienia dla WS_BORDER. Wszystkie inne style są stosowane bezpośrednio do uchwytu okna formantu, jeśli jeden jest obecny.

Modyfikuje style okna formantu. Style, które mają zostać dodane lub usunięte, można łączyć za pomocą operatora bitowego OR (&#124;). Zobacz [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) funkcji w windows SDK, aby uzyskać informacje na temat dostępnych stylów okien.

Jeśli *nFlags* jest niezerowy, `ModifyStyle` wywołuje `SetWindowPos`funkcję Win32 i ponownie rysuje okno, łącząc *nFlags* z następującymi czterema flagami:

- SWP_NOSIZE Zachowuje bieżący rozmiar.

- SWP_NOMOVE Zachowuje bieżącą pozycję.

- SWP_NOZORDER Zachowuje bieżące zamówienie Z.

- SWP_NOACTIVATE Nie aktywuje okna.

Aby zmodyfikować rozszerzone style okna, należy [wywołać modifyStyleEx](#modifystyleex).

## <a name="colecontrolsitemodifystyleex"></a><a name="modifystyleex"></a>COleControlSite::ModifyStyleEx

Modyfikuje rozszerzone style formantu.

```
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*dwUsuł*<br/>
Rozszerzone style, które mają zostać usunięte z bieżących stylów okien.

*dwAdd*<br/>
Rozszerzone style, które mają zostać dodane z bieżących stylów okien.

*nPłgi*<br/>
Flagi pozycjonowania okien. Aby uzyskać listę możliwych wartości, zobacz [Funkcję SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli style są zmieniane, w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Właściwość Wygląd akcji formantu zostanie zmodyfikowana w celu dopasowania do ustawienia dla WS_EX_CLIENTEDGE. Wszystkie inne style rozszerzonego okna są stosowane bezpośrednio do uchwytu okna formantu, jeśli jeden jest obecny.

Modyfikuje rozszerzone style okna obiektu witryny kontrolnej. Style, które mają zostać dodane lub usunięte, można łączyć za pomocą operatora bitowego OR (&#124;). Zobacz [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) funkcji w windows SDK, aby uzyskać informacje na temat dostępnych stylów okien.

Jeśli *nFlags* jest niezerowy, `ModifyStyleEx` wywołuje `SetWindowPos`funkcję Win32 i ponownie rysuje okno, łącząc *nFlags* z następującymi czterema flagami:

- SWP_NOSIZE Zachowuje bieżący rozmiar.

- SWP_NOMOVE Zachowuje bieżącą pozycję.

- SWP_NOZORDER Zachowuje bieżące zamówienie Z.

- SWP_NOACTIVATE Nie aktywuje okna.

Aby zmodyfikować rozszerzone style okna, należy [wywołać modifystyle](#modifystyle).

## <a name="colecontrolsitemovewindow"></a><a name="movewindow"></a>COleControlSite::MoveWindow

Zmienia położenie formantu.

```
virtual void MoveWindow(
    int x,
    int y,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Nowe położenie lewej strony okna.

*Y*<br/>
Nowa pozycja górnej części okna.

*nWidth (ww.*<br/>
Nowa szerokość okna

*nFeksja*<br/>
Nowa wysokość okna.

## <a name="colecontrolsitequickactivate"></a><a name="quickactivate"></a>COleControlSite::QuickActivate

Szybkie aktywowanie zamkniętego formantu.

```
virtual BOOL QuickActivate();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli witryna kontroli została aktywowana, w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana tylko wtedy, gdy użytkownik zastępuje proces tworzenia formantu.

Metody `IPersist*::Load` `IPersist*::InitNew` i powinny być wywoływane po szybkiej aktywacji występuje. Formant należy ustanowić jego połączenia z pochłaniaczami kontenera podczas szybkiej aktywacji. Jednak te połączenia nie są `IPersist*::Load` `IPersist*::InitNew` aktywne, dopóki nie został wywołany lub został wywołany.

## <a name="colecontrolsitesafesetproperty"></a><a name="safesetproperty"></a>COleControlSite::SafeSetProperty

Ustawia właściwość formantu określoną przez *dwDispID*.

```
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identyfikuje identyfikator wysyłki właściwości lub metody, znalezione w `IDispatch` interfejsie formantu, do zestawu.

*vtProp (vtProp)*<br/>
Określa typ właściwości, która ma zostać ustawiona. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Pojedynczy parametr typu określonego przez *vtProp*.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> W `SetProperty` `SetPropertyV`przeciwieństwie do i , jeśli wystąpi błąd (na przykład próbuje ustawić nieistniejącą właściwość), nie jest zgłaszany wyjątek.

## <a name="colecontrolsitesetdefaultbutton"></a><a name="setdefaultbutton"></a>COleControlSite::SetDefaultButton

Ustawia formant jako przycisk domyślny.

```cpp
void SetDefaultButton(BOOL bDefault);
```

### <a name="parameters"></a>Parametry

*bDefault (Domyślnie)*<br/>
Nonzero, jeśli formant powinien stać się przyciskiem domyślnym; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Formant musi mieć ustawiony bit stanu OLEMISC_ACTSLIKEBUTTON.

## <a name="colecontrolsitesetdlgctrlid"></a><a name="setdlgctrlid"></a>COleControlSite::SetDlgCtrlID

Zmienia wartość identyfikatora elementu okna dialogowego formantu.

```
virtual int SetDlgCtrlID(int nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Nowa wartość identyfikatora.

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, poprzedni identyfikator elementu okna okna; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

## <a name="colecontrolsitesetfocus"></a><a name="setfocus"></a>COleControlSite::SetFocus

Ustawia fokus do formantu.

```
virtual CWnd* SetFocus();
virtual CWnd* SetFocus(LPMSG lpmsg);
```

### <a name="parameters"></a>Parametry

*lpmsg*<br/>
Wskaźnik do [struktury MSG](/windows/win32/api/winuser/ns-winuser-msg). Ta struktura zawiera komunikat systemu `SetFocus` Windows wyzwalający żądanie formantu zawartego w bieżącej witrynie sterowania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna, które wcześniej fokus.

## <a name="colecontrolsitesetproperty"></a><a name="setproperty"></a>COleControlSite::Właściwości SetProperty

Ustawia właściwość formantu określoną przez *dwDispID*.

```
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identyfikuje identyfikator wysyłki właściwości lub metody, znalezione w `IDispatch` interfejsie formantu, do zestawu.

*vtProp (vtProp)*<br/>
Określa typ właściwości, która ma zostać ustawiona. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Pojedynczy parametr typu określonego przez *vtProp*.

### <a name="remarks"></a>Uwagi

Jeśli `SetProperty` wystąpi błąd, zostanie zgłoszony wyjątek.

Typ wyjątku jest określany przez zwracaną wartość próby ustawiania właściwości lub metody. Jeśli zwracana `DISP_E_EXCEPTION`jest `COleDispatchExcpetion` wartość , a jest generowany; w `COleException`przeciwnym razie .

## <a name="colecontrolsitesetpropertyv"></a><a name="setpropertyv"></a>COleControlSite::SetPropertyV

Ustawia właściwość formantu określoną przez *dwDispID*.

```
virtual void SetPropertyV(
    DISPID dwDispID,
    VARTYPE vtProp,
    va_list argList);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identyfikuje identyfikator wysyłki właściwości lub metody, znalezione w `IDispatch` interfejsie formantu, do zestawu.

*vtProp (vtProp)*<br/>
Określa typ właściwości, która ma zostać ustawiona. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*argLista*<br/>
Wskaźnik do listy argumentów.

### <a name="remarks"></a>Uwagi

Dodatkowe parametry dla wywoływana metody lub właściwości mogą być przekazywane przy użyciu *parametru arg_list.* Jeśli `SetProperty` wystąpi błąd, zostanie zgłoszony wyjątek.

Typ wyjątku jest określany przez zwracaną wartość próby ustawiania właściwości lub metody. Jeśli zwracana `DISP_E_EXCEPTION`jest `COleDispatchExcpetion` wartość , a jest generowany; w `COleException`przeciwnym razie .

## <a name="colecontrolsitesetwindowpos"></a><a name="setwindowpos"></a>COleControlSite::SetWindowPos

Ustawia kolejność rozmiaru, położenia i z witryny sterowania.

```
virtual BOOL SetWindowPos(
    const CWnd* pWndInsertAfter,
    int x,
    int y,
    int cx,
    int cy,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*pWndInsertPo*<br/>
Wskaźnik do okna.

*X*<br/>
Nowe położenie lewej strony okna.

*Y*<br/>
Nowa pozycja górnej części okna.

*Cx*<br/>
Nowa szerokość okna

*Cy*<br/>
Nowa wysokość okna.

*nPłgi*<br/>
Określa flagi zmiany rozmiaru i pozycjonowania okien. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli się powiedzie, w przeciwnym razie zero.

## <a name="colecontrolsitesetwindowtext"></a><a name="setwindowtext"></a>COleControlSite::SetWindowText

Ustawia tekst dla witryny kontrolnej.

```
virtual void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*lpszString*<br/>
Wskaźnik do ciągu zakończonego zerem, który ma być używany jako nowy tytuł lub tekst sterujący.

### <a name="remarks"></a>Uwagi

Ta funkcja najpierw próbuje ustawić caption stock właściwości. Jeśli caption stock właściwość nie jest obsługiwana, Text właściwość jest ustawiona zamiast.

## <a name="colecontrolsiteshowwindow"></a><a name="showwindow"></a>COleControlSite::ShowWindow

Ustawia stan pokazu okna.

```
virtual BOOL ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Parametry

*nCmdShow*<br/>
Określa sposób pokazywany lokacji kontrolnej. Musi to być jedna z następujących wartości:

- SW_HIDE Ukrywa to okno i przekazuje aktywację do innego okna.

- SW_MINIMIZE minimalizuje okno i aktywuje okno najwyższego poziomu na liście systemu.

- SW_RESTORE Aktywuje i wyświetla okno. Jeśli okno jest zminimalizowane lub zmaksymalizowane, system Windows przywraca je do pierwotnego rozmiaru i położenia.

- SW_SHOW Aktywuje okno i wyświetla je w bieżącym rozmiarze i położeniu.

- SW_SHOWMAXIMIZED Aktywuje okno i wyświetla je jako zmaksymalizowane okno.

- SW_SHOWMINIMIZED Aktywuje okno i wyświetla je jako ikonę.

- SW_SHOWMINNOACTIVE Wyświetla okno jako ikonę. Okno, które jest aktualnie aktywne, pozostaje aktywne.

- SW_SHOWNA Wyświetla okno w bieżącym stanie. Okno, które jest aktualnie aktywne, pozostaje aktywne.

- SW_SHOWNOACTIVATE Wyświetla okno w najnowszym rozmiarze i położeniu. Okno, które jest aktualnie aktywne, pozostaje aktywne.

- SW_SHOWNORMAL Aktywuje i wyświetla okno. Jeśli okno jest zminimalizowane lub zmaksymalizowane, system Windows przywraca je do pierwotnego rozmiaru i położenia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli okno było wcześniej widoczne; 0, jeśli okno było wcześniej ukryte.

## <a name="see-also"></a>Zobacz też

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)
