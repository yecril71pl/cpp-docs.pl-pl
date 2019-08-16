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
ms.openlocfilehash: 9b9b68a001acdf4b08d9cfc01cc67c43217d9a57
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504313"
---
# <a name="colecontrolsite-class"></a>Klasa COleControlSite

Zapewnia obsługę niestandardowych interfejsów kontroli po stronie klienta.

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
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|Tworzy powiązanie domyślnej właściwości hostowanej kontrolki ze źródłem danych.|
|[COleControlSite::BindProperty](#bindproperty)|Tworzy powiązanie właściwości hostowanej kontrolki ze źródłem danych.|
|[COleControlSite::CreateControl](#createcontrol)|Tworzy hostowaną kontrolkę ActiveX.|
|[COleControlSite::DestroyControl](#destroycontrol)|Niszczy formant hostowany.|
|[COleControlSite::DoVerb](#doverb)|Wykonuje określone zlecenie kontroli hostowanej.|
|[COleControlSite::EnableDSC](#enabledsc)|Włącza pozyskiwanie danych dla witryny kontrolnej.|
|[COleControlSite::EnableWindow](#enablewindow)|Włącza lokację sterowania.|
|[COleControlSite::FreezeEvents](#freezeevents)|Określa, czy lokacja kontrolki akceptuje zdarzenia.|
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|Pobiera domyślny kod przycisku dla hostowanej kontrolki.|
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|Pobiera identyfikator kontrolki.|
|[COleControlSite::GetEventIID](#geteventiid)|Pobiera identyfikator interfejsu zdarzenia dla kontrolki hostowanej.|
|[COleControlSite::GetExStyle](#getexstyle)|Pobiera rozszerzone style lokacji sterującej.|
|[COleControlSite::GetProperty](#getproperty)|Pobiera określoną właściwość hostowanej kontrolki.|
|[COleControlSite::GetStyle](#getstyle)|Pobiera Style lokacji formantu.|
|[COleControlSite::GetWindowText](#getwindowtext)|Pobiera tekst kontrolki hostowanej.|
|[COleControlSite::InvokeHelper](#invokehelper)|Wywołaj konkretną metodę kontroli hostowanej.|
|[COleControlSite::InvokeHelperV](#invokehelperv)|Wywołaj określoną metodę kontrolki hostowanej z zmienną listą argumentów.|
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|Określa, czy kontrolka jest domyślnym przyciskiem w oknie.|
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|Sprawdza widoczny stan lokacji sterowania.|
|[COleControlSite::ModifyStyle](#modifystyle)|Modyfikuje bieżące rozszerzone style lokacji sterowania.|
|[COleControlSite::ModifyStyleEx](#modifystyleex)|Modyfikuje bieżące style lokacji kontrolki.|
|[COleControlSite::MoveWindow](#movewindow)|Zmienia pozycję lokacji formantu.|
|[COleControlSite::QuickActivate](#quickactivate)|Umożliwia szybkie aktywowanie hostowanej kontrolki.|
|[COleControlSite::SafeSetProperty](#safesetproperty)|Ustawia właściwość lub metodę formantu bez prawdopodobieństwa zgłaszania wyjątku.|
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|Ustawia przycisk domyślny w oknie.|
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|Pobiera identyfikator kontrolki.|
|[COleControlSite::SetFocus](#setfocus)|Ustawia fokus na lokację sterowania.|
|[COleControlSite::SetProperty](#setproperty)|Ustawia konkretną właściwość kontrolki hostowanej.|
|[COleControlSite::SetPropertyV](#setpropertyv)|Ustawia określoną właściwość kontrolki hostowanej z zmienną listą argumentów.|
|[COleControlSite::SetWindowPos](#setwindowpos)|Ustawia pozycję lokacji formantu.|
|[COleControlSite::SetWindowText](#setwindowtext)|Ustawia tekst kontrolki hostowanej.|
|[COleControlSite::ShowWindow](#showwindow)|Pokazuje lub ukrywa lokację sterowania.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleControlSite::GetControlInfo](#getcontrolinfo)|Pobiera informacje o klawiaturze i skróty dla kontrolki hostowanej.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|Określa, czy formant hostowany jest kontrolką bez okien.|
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|Zawiera informacje na temat obsługi klawiatury dla kontrolki.|
|[COleControlSite::m_dwEventSink](#m_dweventsink)|Plik cookie punktu połączenia kontrolki.|
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|Różne stany dla hostowanej kontroli.|
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|`IPropertyNotifySink` Plik cookie formantu.|
|[COleControlSite::m_dwStyle](#m_dwstyle)|Style kontrolki hostowanej.|
|[COleControlSite::m_hWnd](#m_hwnd)|Uchwyt witryny kontrolnej.|
|[COleControlSite::m_iidEvents](#m_iidevents)|Identyfikator interfejsu zdarzenia dla hostowanej kontrolki.|
|[COleControlSite::m_nID](#m_nid)|Identyfikator hostowanej kontrolki.|
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|Wskaźnik do `IOleInPlaceActiveObject` obiektu kontrolki hostowanej.|
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|Kontener hostowanej kontrolki.|
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|Wskaźnik do `IOleInPlaceObject` obiektu kontrolki hostowanej.|
|[COleControlSite::m_pObject](#m_pobject)|Wskaźnik do `IOleObjectInterface` interfejsu formantu.|
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|Wskaźnik do `IOleInPlaceObjectWindowless` interfejsu formantu.|
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|Wskaźnik do obiektu okna dla hostowanej kontrolki.|
|[COleControlSite::m_rect](#m_rect)|Wymiary lokacji sterowania.|

## <a name="remarks"></a>Uwagi

Jest to podstawowy sposób polegający na tym, że osadzony formant ActiveX uzyskuje informacje o lokalizacji i zakresie jego witryny wyświetlania, monikerze, interfejsie użytkownika, jego właściwości otoczenia i innych zasobach udostępnianych przez jego kontener. `COleControlSite`w pełni implementuje interfejsy [IOleControlSite](/windows/win32/api/ocidl/nn-ocidl-iolecontrolsite), [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite), [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), `INotifyDBEvents` `IBoundObjectSite`, i [IRowsetNotify](../../data/oledb/irowsetnotifyimpl-class.md) . Ponadto zaimplementowane są również interfejsy IDispatch (zapewniające obsługę właściwości otoczenia i ujścia zdarzeń).

Aby utworzyć witrynę kontrolki ActiveX przy `COleControlSite`użyciu, należy uzyskać klasę `COleControlSite`z. W klasie pochodnej kontenera (na przykład okno dialogowe) `CWnd::CreateControlSite` przesłania funkcję. `CWnd`

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlSite`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxocc. h

##  <a name="binddefaultproperty"></a>COleControlSite::BindDefaultProperty

Tworzy powiązanie domyślnej prostej powiązanej właściwości obiektu wywołującego, jak oznaczono w bibliotece typów, do podstawowego kursora zdefiniowanego za pomocą właściwości DataSource, UserName, Password i SQL kontroli źródła danych.

```
virtual void BindDefaultProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    LPCTSTR szFieldName,
    CWnd* pDSCWnd);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Określa identyfikator DISPID właściwości w formancie powiązanym z danymi, który ma zostać powiązany z kontrolą źródła danych.

*vtProp*<br/>
Określa typ właściwości, która ma zostać powiązana — na przykład VT_BSTR, VT_VARIANT i tak dalej.

*szFieldName*<br/>
Określa nazwę kolumny w kursorze dostarczonym przez formant źródła danych, do którego zostanie powiązana właściwość.

*pDSCWnd*<br/>
Wskaźnik do `CWnd`obiektu pochodnego, który hostuje kontrolę źródła danych, do której zostanie powiązana właściwość.

### <a name="remarks"></a>Uwagi

`CWnd` Obiekt, na którym wywoływana jest ta funkcja, musi być formantem powiązanym z danymi.

##  <a name="bindproperty"></a>COleControlSite::BindProperty

Tworzy powiązanie prostej powiązanej właściwości obiektu wywołującego, jak oznaczono w bibliotece typów, do podstawowego kursora zdefiniowanego za pomocą właściwości DataSource, UserName, Password i SQL kontroli źródła danych.

```
virtual void BindProperty(
    DISPID dwDispId,
    CWnd* pWndDSC);
```

### <a name="parameters"></a>Parametry

*dwDispId*<br/>
Określa identyfikator DISPID właściwości w formancie powiązanym z danymi, który ma zostać powiązany z kontrolą źródła danych.

*pWndDSC*<br/>
Wskaźnik do `CWnd`obiektu pochodnego, który hostuje kontrolę źródła danych, do której zostanie powiązana właściwość.

### <a name="remarks"></a>Uwagi

`CWnd` Obiekt, na którym wywoływana jest ta funkcja, musi być formantem powiązanym z danymi.

##  <a name="colecontrolsite"></a>COleControlSite::COleControlSite

Tworzy nowy `COleControlSite` obiekt.

```
explicit COleControlSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parametry

*pCtrlCont*<br/>
Wskaźnik do kontenera kontrolki (który reprezentuje okno obsługujące formant AtiveX).

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana przez funkcję [COccManager::](../../mfc/reference/coccmanager-class.md#createcontainer) iscontainerer. Aby uzyskać więcej informacji na temat dostosowywania tworzenia kontenerów, zobacz [COccManager:: issite](../../mfc/reference/coccmanager-class.md#createsite).

##  <a name="createcontrol"></a>COleControlSite:: IsControl

Tworzy kontrolkę ActiveX hostowaną przez `COleControlSite` obiekt.

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

*pWndCtrl*<br/>
Wskaźnik do obiektu okna reprezentującego formant.

*Identyfikator*<br/>
Unikatowy identyfikator klasy formantu.

*lpszWindowName*<br/>
Wskaźnik do tekstu, który ma być wyświetlany w kontrolce. Ustawia wartość właściwości Caption lub text winodw (jeśli istnieje).

*dwStyle*<br/>
Style systemu Windows. Dostępne style są wymienione w sekcji **uwagi** .

*cinania*<br/>
Określa rozmiar i położenie kontrolki. Może to być `CRect` obiekt `RECT` lub struktura.

*nID*<br/>
Określa identyfikator okna podrzędnego kontrolki.

*pPersist*<br/>
Wskaźnik do elementu `CFile` zawierającego trwały stan dla kontrolki. Wartość domyślna to NULL, co oznacza, że kontrolka inicjuje się sama bez przywracania stanu z dowolnego trwałego magazynu. Jeśli wartość nie jest równa null, powinna to być `CFile`wskaźnik do obiektu pochodnego, który zawiera trwałe dane kontrolki w postaci strumienia lub magazynu. Te dane mogły zostać zapisane w poprzedniej aktywacji klienta. Może zawierać inne dane, ale musi mieć ustawiony wskaźnik odczytu i zapisu na pierwszy bajt trwałych danych w czasie wywołania do `CreateControl`. `CFile`

*bStorage*<br/>
Wskazuje, czy dane w *pPersist* powinny być interpretowane `IStorage` jako `IStream` czy dane. Jeśli dane w *pPersist* są magazynem, *bStorage* powinna mieć wartość true. Jeśli dane w *pPersist* jest strumieniem, *bStorage* powinna mieć wartość false. Wartość domyślna to FALSE.

*bstrLicKey*<br/>
Opcjonalne dane klucza licencji. Te dane są potrzebne tylko do tworzenia formantów, które wymagają klucza licencji w czasie wykonywania. Jeśli formant obsługuje Licencjonowanie, należy podać klucz licencji, aby można było utworzyć formant. Wartość domyślna to NULL.

*formacie*<br/>
Wskaźnik do `POINT` struktury zawierającej lewy górny róg kontrolki. Rozmiar kontrolki jest określany na podstawie wartości *psize*. Wartości *PPT* i *psize* są opcjonalną metodą określania rozmiaru i położenia OPF kontrolki.

*psize*<br/>
Wskaźnik do `SIZE` struktury zawierającej rozmiar kontrolki. Lewy górny róg jest określany przez wartość *PPT*. Wartości *PPT* i *psize* są opcjonalną metodą określania rozmiaru i położenia OPF kontrolki.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Tylko podzbiór flag *DwStyle* systemu Windows jest obsługiwany przez `CreateControl`:

- WS_VISIBLE tworzy okno, które jest początkowo widoczne. Wymagane, jeśli formant ma być widoczny natychmiast, na przykład w zwykłych oknach.

- WS_DISABLED tworzy okno, które jest początkowo wyłączone. Wyłączone okno nie może odebrać danych wejściowych od użytkownika. Można ustawić, Jeśli kontrolka ma właściwość Enabled.

- WS_BORDER tworzy okno z obramowaniem cienkim. Można ustawić, Jeśli kontrolka ma właściwość BorderStyle.

- WS_GROUP Określa pierwszą kontrolkę grupy kontrolek. Użytkownik może zmienić fokus klawiatury z jednej kontrolki w grupie na następny przy użyciu klawiszy kierunkowych. Wszystkie kontrolki zdefiniowane przy użyciu stylu WS_GROUP po pierwszej kontrolce należy do tej samej grupy. Następna kontrolka ze stylem WS_GROUP zatrzymuje grupę i rozpoczyna następną grupę.

- WS_TABSTOP określa kontrolkę, która może odbierać fokus klawiatury, gdy użytkownik naciśnie klawisz TAB. Naciśnięcie klawisza TAB powoduje zmianę fokusu klawiatury na następną kontrolkę stylu WS_TABSTOP.

Użyj drugiego przeciążenia, aby utworzyć kontrolki o rozmiarze domyślnym.

##  <a name="destroycontrol"></a>  COleControlSite::DestroyControl

`COleControlSite` Niszczy obiekt.

```
virtual BOOL DestroyControl();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po zakończeniu obiekt zostaje zwolniony z pamięci, a wszystkie wskaźniki do obiektu nie są już prawidłowe.

##  <a name="doverb"></a>COleControlSite::D oVerb

Wykonuje określone zlecenie.

```
virtual HRESULT DoVerb(
    LONG nVerb,
    LPMSG lpMsg = NULL);
```

### <a name="parameters"></a>Parametry

*nVerb*<br/>
Określa zlecenie do wykonania. Może zawierać jedną z następujących czynności:

|Wartość|Znaczenie|Symbol|
|-----------|-------------|------------|
|0|Primary — Zlecenie|OLEIVERB_PRIMARY|
|-1|Zlecenie pomocnicze|Dawaj|
|1|Wyświetla obiekt do edycji.|OLEIVERB_SHOW|
|-2|Edytuje element w osobnym oknie.|OLEIVERB_OPEN|
|-3|Ukrywa obiekt.|OLEIVERB_HIDE|
|-4|Uaktywnia formant w miejscu.|OLEIVERB_UIACTIVATE|
|-5|Aktywuje kontrolkę w miejscu bez dodatkowych elementów interfejsu użytkownika.|OLEIVERB_INPLACEACTIVATE|
|-7|Wyświetl właściwości kontrolki.|OLEIVERB_PROPERTIES|

*lpMsg*<br/>
Wskaźnik na komunikat, który spowodował aktywowanie elementu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja bezpośrednio wywołuje przez `IOleObject` interfejs kontrolki, aby wykonać określone zlecenie. Jeśli wyjątek jest zgłaszany w wyniku wywołania funkcji, zwracany jest kod błędu HRESULT.

Aby uzyskać więcej informacji, zobacz [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) w Windows SDK.

##  <a name="enabledsc"></a>COleControlSite::EnableDSC

Włącza pozyskiwanie danych dla lokacji sterowania.

```
virtual void EnableDSC();
```

### <a name="remarks"></a>Uwagi

Wywoływane przez platformę, aby włączyć i zainicjować pozyskiwanie danych dla lokacji kontroli. Zastąp tę funkcję, aby zapewnić dostosowane zachowanie.

##  <a name="enablewindow"></a>COleControlSite::EnableWindow

Włącza lub wyłącza wprowadzanie danych przez mysz i klawiaturę do lokacji sterowania.

```
virtual BOOL EnableWindow(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Określa, czy okno ma być włączone, czy wyłączone: PRAWDA, jeśli dane wejściowe okna mają być włączone, w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli okno zostało wcześniej wyłączone, w przeciwnym razie 0.

##  <a name="freezeevents"></a>COleControlSite:: FreezeEvents

Określa, czy witryna kontrolki będzie obsługiwać czy ignorować zdarzenia wywoływane przez formant.

```
void FreezeEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parametry

*bFreeze*<br/>
Określa, czy witryna kontrolki chce zatrzymać akceptowanie zdarzeń. Niezerowe, jeśli formant nie akceptuje zdarzeń; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Jeśli *bFreeze* ma wartość true, lokacja kontrolki żąda kontrolki do zatrzymania zdarzeń naruszenia. Jeśli *bFreeze* ma wartość false, lokacja kontrolki żąda kontrolki do kontynuowania uruchamiania zdarzeń.

> [!NOTE]
>  Kontrolka nie jest wymagana do zatrzymania uruchamiania zdarzeń, jeśli żądanie jest wymagane przez lokację kontroli. Może kontynuować proces uruchamiania, ale wszystkie kolejne zdarzenia zostaną zignorowane przez lokację kontroli.

##  <a name="getcontrolinfo"></a>  COleControlSite::GetControlInfo

Pobiera informacje o funkcjach klawiatury i zachowania klawiatury.

```
void GetControlInfo();
```

### <a name="remarks"></a>Uwagi

Informacje są przechowywane w [COleControlSite:: m_ctlInfo](#m_ctlinfo).

##  <a name="getdefbtncode"></a>COleControlSite::GetDefBtnCode

Określa, czy kontrolka jest domyślnym przyciskiem wypchnięcia.

```
DWORD GetDefBtnCode();
```

### <a name="return-value"></a>Wartość zwracana

Może być jedną z następujących wartości:

- Formant DLGC_DEFPUSHBUTTON jest domyślnym przyciskiem w oknie dialogowym.

- Formant DLGC_UNDEFPUSHBUTTON nie jest domyślnym przyciskiem w oknie dialogowym.

- **0** kontrolka nie jest przyciskiem.

##  <a name="getdlgctrlid"></a>COleControlSite::GetDlgCtrlID

Pobiera identyfikator kontrolki.

```
virtual int GetDlgCtrlID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator elementu okna dialogowego formantu.

##  <a name="geteventiid"></a>COleControlSite::GetEventIID

Pobiera wskaźnik do domyślnego interfejsu zdarzeń kontrolki.

```
BOOL GetEventIID(IID* piid);
```

### <a name="parameters"></a>Parametry

*piid*<br/>
Wskaźnik do identyfikatora interfejsu.

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli się powiedzie, w przeciwnym razie 0. Jeśli to się powiedzie, *piid* zawiera identyfikator interfejsu dla domyślnego interfejsu zdarzenia kontrolki.

##  <a name="getexstyle"></a>  COleControlSite::GetExStyle

Pobiera Style rozszerzone okna.

```
virtual DWORD GetExStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Style rozszerzone okna sterowania.

### <a name="remarks"></a>Uwagi

Aby pobrać style regularne, wywołaj metodę [COleControlSite:: GetStyle](#getstyle).

##  <a name="getproperty"></a>COleControlSite:: GetProperty

Pobiera właściwość kontrolki określoną przez *dwDispID*.

```
virtual void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identyfikuje identyfikator wysyłania właściwości, który znajduje się w domyślnym `IDispatch` interfejsie formantu, który ma zostać pobrany.

*vtProp*<br/>
Określa typ właściwości, która ma zostać pobrana. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvProp*<br/>
Adres zmiennej, która będzie odbierać wartość właściwości. Musi być zgodny z typem określonym przez *vtProp*.

### <a name="remarks"></a>Uwagi

Wartość jest zwracana za pomocą *pvProp*.

##  <a name="getstyle"></a>COleControlSite:: GetStyle

Pobiera Style lokacji formantu.

```
virtual DWORD GetStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Style okna.

### <a name="remarks"></a>Uwagi

Aby uzyskać listę możliwych wartości, zobacz [Style systemu Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles). Aby pobrać style rozszerzone witryny sterowania, wywołaj [COleControlSite:: GetExStyle](#getexstyle).

##  <a name="getwindowtext"></a>COleControlSite::GetWindowText

Pobiera bieżący tekst formantu.

```
virtual void GetWindowText(CString& str) const;
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odwołanie do `CString` obiektu, który zawiera bieżący tekst formantu.

### <a name="remarks"></a>Uwagi

Jeśli formant obsługuje Właściwość Caption, ta wartość jest zwracana. Jeśli właściwość Caption nie jest obsługiwana, zwracana jest wartość właściwości text.

##  <a name="invokehelper"></a>COleControlSite:: InvokeHelper

Wywołuje metodę lub właściwość określoną przez *dwDispID*w kontekście określonym przez *wFlags*.

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
Identyfikuje identyfikator wysyłania właściwości lub metody w `IDispatch` interfejsie kontrolki, który ma zostać wywołany.

*wFlags*<br/>
Flagi opisujące kontekst wywołania elementu IDispatch:: Invoke. Aby uzyskać możliwe wartości *wFlags* , `IDispatch::Invoke` Zobacz w Windows SDK.

*vtRet*<br/>
Określa typ zwracanej wartości. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvRet*<br/>
Adres zmiennej, która będzie odbierać wartość właściwości lub wartość zwracaną. Musi być zgodny z typem określonym przez *vtRet*.

*pbParamInfo*<br/>
Wskaźnik na ciąg zakończony znakiem null bajtów określający typy parametrów po *pbParamInfo*. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Zmienna lista parametrów, typów określonych w *pbParamInfo*.

### <a name="remarks"></a>Uwagi

Parametr *pbParamInfo* określa typy parametrów przesłane do metody lub właściwości. Zmienna lista argumentów jest reprezentowana przez... w deklaracji składni.

Ta funkcja konwertuje parametry na wartości VARIANTARG, a następnie wywołuje `IDispatch::Invoke` metodę na kontrolce. Jeśli wywołanie `IDispatch::Invoke` zakończy się niepowodzeniem, ta funkcja zgłosi wyjątek. Jeśli kod `IDispatch::Invoke` stanu zwracany przez is ma `DISP_E_EXCEPTION`wartość `COleDispatchException` , ta funkcja zgłasza obiekt, w przeciwnym razie zgłasza `COleException`.

##  <a name="invokehelperv"></a>COleControlSite::InvokeHelperV

Wywołuje metodę lub właściwość określoną przez *dwDispID*w kontekście określonym przez *wFlags*.

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
Identyfikuje identyfikator wysyłania właściwości lub metody w `IDispatch` interfejsie kontrolki, który ma zostać wywołany.

*wFlags*<br/>
Flagi opisujące kontekst wywołania elementu IDispatch:: Invoke.

*vtRet*<br/>
Określa typ zwracanej wartości. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvRet*<br/>
Adres zmiennej, która będzie odbierać wartość właściwości lub wartość zwracaną. Musi być zgodny z typem określonym przez *vtRet*.

*pbParamInfo*<br/>
Wskaźnik na ciąg zakończony znakiem null bajtów określający typy parametrów po *pbParamInfo*. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*argList*<br/>
Wskaźnik na listę zmiennych argumentów.

### <a name="remarks"></a>Uwagi

Parametr *pbParamInfo* określa typy parametrów przesłane do metody lub właściwości. Dodatkowe parametry wywoływanej metody lub właściwości mogą być przesyłane przy użyciu parametru *va_list* .

Zazwyczaj ta funkcja jest wywoływana przez `COleControlSite::InvokeHelper`.

##  <a name="isdefaultbutton"></a>COleControlSite::IsDefaultButton

Określa, czy formant jest przyciskiem domyślnym.

```
BOOL IsDefaultButton();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, Jeśli kontrolka jest przyciskiem domyślnym w oknie, w przeciwnym razie zero.

##  <a name="iswindowenabled"></a>COleControlSite::IsWindowEnabled

Określa, czy lokacja kontrolki jest włączona.

```
virtual BOOL IsWindowEnabled() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, Jeśli kontrolka jest włączona, w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Wartość jest pobierana z właściwości giełdowy włączonej kontrolki.

##  <a name="m_biswindowless"></a>COleControlSite::m_bIsWindowless

Określa, czy obiekt jest kontrolką bez okien.

```
BOOL m_bIsWindowless;
```

### <a name="remarks"></a>Uwagi

Niezerowe, Jeśli kontrolka nie ma okna, w przeciwnym razie zero.

##  <a name="m_ctlinfo"></a>COleControlSite::m_ctlInfo

Informacje o tym, jak dane wejściowe klawiatury są obsługiwane przez formant.

```
CONTROLINFO m_ctlInfo;
```

### <a name="remarks"></a>Uwagi

Te informacje są przechowywane w strukturze [CONTROLINFO](/windows/win32/api/ocidl/ns-ocidl-controlinfo) .

##  <a name="m_dweventsink"></a>  COleControlSite::m_dwEventSink

Zawiera plik cookie punktu połączenia z ujścia zdarzeń kontrolki.

```
DWORD m_dwEventSink;
```

##  <a name="m_dwmiscstatus"></a>  COleControlSite::m_dwMiscStatus

Zawiera różne informacje o formancie.

```
DWORD m_dwMiscStatus;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)w Windows SDK.

##  <a name="m_dwpropnotifysink"></a>  COleControlSite::m_dwPropNotifySink

Zawiera plik cookie [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) .

```
DWORD m_dwPropNotifySink;
```

##  <a name="m_dwstyle"></a>COleControlSite::m_dwStyle

Zawiera style okna kontrolki.

```
DWORD m_dwStyle;
```

##  <a name="m_hwnd"></a>COleControlSite::m_hWnd

Zawiera właściwość HWND kontrolki lub wartość NULL, jeśli formant jest bezokienkowy.

```
HWND m_hWnd;
```

##  <a name="m_iidevents"></a>COleControlSite::m_iidEvents

Zawiera identyfikator interfejsu domyślnego obiektu ujścia zdarzenia kontrolki.

```
IID m_iidEvents;
```

##  <a name="m_nid"></a>  COleControlSite::m_nID

Zawiera identyfikator elementu okna dialogowego kontrolki.

```
UINT m_nID;
```

##  <a name="m_pactiveobject"></a>  COleControlSite::m_pActiveObject

Zawiera interfejs [IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) formantu.

```
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;
```

##  <a name="m_pctrlcont"></a>  COleControlSite::m_pCtrlCont

Zawiera kontener kontrolki (reprezentujący formularz).

```
COleControlContainer* m_pCtrlCont;
```

##  <a name="m_pinplaceobject"></a>  COleControlSite::m_pInPlaceObject

Zawiera interfejs IOleInPlaceObject formantu. [](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) `IOleInPlaceObject`

```
LPOLEINPLACEOBJECT m_pInPlaceObject;
```

##  <a name="m_pobject"></a>  COleControlSite::m_pObject

`IOleObjectInterface` Zawiera interfejs formantu.

```
LPOLEOBJECT m_pObject;
```

##  <a name="m_pwindowlessobject"></a>  COleControlSite::m_pWindowlessObject

Zawiera interfejs IOleInPlaceObjectWindowless formantu. [](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) `IOleInPlaceObjectWindowless`

```
IOleInPlaceObjectWindowless* m_pWindowlessObject;
```

##  <a name="m_pwndctrl"></a>  COleControlSite::m_pWndCtrl

Zawiera wskaźnik do `CWnd` obiektu, który reprezentuje sam formant.

```
CWnd* m_pWndCtrl;
```

##  <a name="m_rect"></a>COleControlSite::m_rect

Zawiera granice kontrolki względem okna kontenera.

```
CRect m_rect;
```

##  <a name="modifystyle"></a>COleControlSite:: Modify

Modyfikuje style formantu.

```
virtual BOOL ModifyStyle(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*dwRemove*<br/>
Style, które mają zostać usunięte ze stylów bieżącego okna.

*dwAdd*<br/>
Style, które mają zostać dodane ze stylów bieżącego okna.

*nFlags*<br/>
Flagi położenia okna. Aby uzyskać listę możliwych wartości, zobacz funkcję [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli style są zmieniane, w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Właściwość z włączonym magazynem kontrolki zostanie zmodyfikowana w celu dopasowania jej do ustawienia WS_DISABLED. Właściwość stylu obramowania elementu sterującego zostanie zmodyfikowana w celu dopasowania do żądanego ustawienia dla WS_BORDER. Wszystkie inne style są stosowane bezpośrednio do uchwytu okna kontrolki, jeśli taki istnieje.

Modyfikuje style okna kontrolki. Style do dodania lub usunięcia można łączyć za pomocą operatora bitowego lub ( &#124; ). Zobacz funkcja [onwindow](/windows/win32/api/winuser/nf-winuser-createwindoww) w Windows SDK, aby uzyskać informacje o dostępnych stylach okien.

Jeśli *nFlags* ma wartość różną od `ModifyStyle` zera, wywołuje funkcję `SetWindowPos`Win32 i ponownie rysuje okno, łącząc *nFlags* z następującymi czterema flagami:

- SWP_NOSIZE zachowuje bieżący rozmiar.

- SWP_NOMOVE zachowuje bieżącą pozycję.

- SWP_NOZORDER zachowuje bieżącą kolejność Z.

- SWP_NOACTIVATE nie aktywuje okna.

Aby zmodyfikować style rozszerzone okna, wywołaj [ModifyStyleEx](#modifystyleex).

##  <a name="modifystyleex"></a>COleControlSite::ModifyStyleEx

Modyfikuje rozszerzone Style formantu.

```
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*dwRemove*<br/>
Style rozszerzone, które mają zostać usunięte ze stylów bieżącego okna.

*dwAdd*<br/>
Style rozszerzone, które mają zostać dodane ze stylów bieżącego okna.

*nFlags*<br/>
Flagi położenia okna. Aby uzyskać listę możliwych wartości, zobacz funkcję [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli style są zmieniane, w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Właściwość wyglądu akcji kontrolki zostanie zmodyfikowana w celu dopasowania jej do ustawienia WS_EX_CLIENTEDGE. Wszystkie inne style okna rozszerzonego są stosowane bezpośrednio do uchwytu okna kontrolki, jeśli taki istnieje.

Modyfikuje rozszerzone style okna obiektu lokacji sterowania. Style do dodania lub usunięcia można łączyć za pomocą operatora bitowego lub ( &#124; ). Zobacz funkcję [elementu CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) w Windows SDK, aby uzyskać informacje o dostępnych stylach okien.

Jeśli *nFlags* ma wartość różną od `ModifyStyleEx` zera, wywołuje funkcję `SetWindowPos`Win32 i ponownie rysuje okno, łącząc *nFlags* z następującymi czterema flagami:

- SWP_NOSIZE zachowuje bieżący rozmiar.

- SWP_NOMOVE zachowuje bieżącą pozycję.

- SWP_NOZORDER zachowuje bieżącą kolejność Z.

- SWP_NOACTIVATE nie aktywuje okna.

Aby zmodyfikować style rozszerzone okna, wywołaj polecenie [modifyname](#modifystyle).

##  <a name="movewindow"></a>COleControlSite::MoveWindow

Zmienia położenie formantu.

```
virtual void MoveWindow(
    int x,
    int y,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Nowa pozycja lewej strony okna.

*y*<br/>
Nowa pozycja górnej części okna.

*nWidth*<br/>
Nowa szerokość okna

*nHeight*<br/>
Nowa wysokość okna.

##  <a name="quickactivate"></a>COleControlSite::QuickActivate

Umożliwia szybkie aktywowanie zawartej kontrolki.

```
virtual BOOL QuickActivate();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, Jeśli lokacja została aktywowana, w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana tylko wtedy, gdy użytkownik zastępuje proces tworzenia formantu.

Metody `IPersist*::Load` i`IPersist*::InitNew` powinny być wywoływane po wystąpieniu szybkiej aktywacji. Formant powinien nawiązywać połączenia z ujściami kontenera podczas szybkiej aktywacji. Połączenia te nie są jednak aktywne, dopóki `IPersist*::Load` `IPersist*::InitNew` nie zostaną wywołane.

##  <a name="safesetproperty"></a>COleControlSite::SafeSetProperty

Ustawia właściwość kontrolki określoną przez *dwDispID*.

```
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Określa identyfikator wysyłania właściwości lub metody, które mają zostać ustawione w `IDispatch` interfejsie kontrolki.

*vtProp*<br/>
Określa typ właściwości, która ma zostać ustawiona. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Pojedynczy parametr typu określony przez *vtProp*.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  W `SetProperty` przeciwieństwie `SetPropertyV`do i, jeśli wystąpi błąd (np. Próba ustawienia nieistniejącej właściwości), żaden wyjątek nie jest zgłaszany.

##  <a name="setdefaultbutton"></a>COleControlSite::SetDefaultButton

Ustawia kontrolkę jako przycisk domyślny.

```
void SetDefaultButton(BOOL bDefault);
```

### <a name="parameters"></a>Parametry

*bDefault*<br/>
Różne od zera, jeśli formant powinien stać się przyciskiem domyślnym; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Kontrolka musi mieć ustawiony bit stanu OLEMISC_ACTSLIKEBUTTON.

##  <a name="setdlgctrlid"></a>COleControlSite::SetDlgCtrlID

Zmienia wartość identyfikatora elementu okna dialogowego kontrolki.

```
virtual int SetDlgCtrlID(int nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Nowa wartość identyfikatora.

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, poprzedni identyfikator elementu okna dialogowego okna; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

##  <a name="setfocus"></a>COleControlSite:: SetFocus

Ustawia fokus na kontrolkę.

```
virtual CWnd* SetFocus();
virtual CWnd* SetFocus(LPMSG lpmsg);
```

### <a name="parameters"></a>Parametry

*lpmsg*<br/>
Wskaźnik do [struktury MSG](/windows/win32/api/winuser/ns-winuser-msg). Ta struktura zawiera komunikat systemu Windows wyzwalający `SetFocus` żądanie kontroli zawartej w bieżącej lokacji kontroli.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna, które wcześniej miało fokus.

##  <a name="setproperty"></a>COleControlSite:: SetProperty

Ustawia właściwość kontrolki określoną przez *dwDispID*.

```
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Określa identyfikator wysyłania właściwości lub metody, które mają zostać ustawione w `IDispatch` interfejsie kontrolki.

*vtProp*<br/>
Określa typ właściwości, która ma zostać ustawiona. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Pojedynczy parametr typu określony przez *vtProp*.

### <a name="remarks"></a>Uwagi

Jeśli `SetProperty` wystąpi błąd, zgłaszany jest wyjątek.

Typ wyjątku jest określany przez zwracaną wartość próby ustawienia właściwości lub metody. Jeśli zwracana wartość to `DISP_E_EXCEPTION` `COleDispatchExcpetion` , `COleException`jest zgłaszany; w przeciwnym razie.

##  <a name="setpropertyv"></a>COleControlSite::SetPropertyV

Ustawia właściwość kontrolki określoną przez *dwDispID*.

```
virtual void SetPropertyV(
    DISPID dwDispID,
    VARTYPE vtProp,
    va_list argList);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Określa identyfikator wysyłania właściwości lub metody, które mają zostać ustawione w `IDispatch` interfejsie kontrolki.

*vtProp*<br/>
Określa typ właściwości, która ma zostać ustawiona. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver:: InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*argList*<br/>
Wskaźnik na listę argumentów.

### <a name="remarks"></a>Uwagi

Dodatkowe parametry wywoływanej metody lub właściwości można passeed za pomocą parametru *arg_list* . Jeśli `SetProperty` wystąpi błąd, zgłaszany jest wyjątek.

Typ wyjątku jest określany przez zwracaną wartość próby ustawienia właściwości lub metody. Jeśli zwracana wartość to `DISP_E_EXCEPTION` `COleDispatchExcpetion` , `COleException`jest zgłaszany; w przeciwnym razie.

##  <a name="setwindowpos"></a>COleControlSite::SetWindowPos

Ustawia rozmiar, położenie i porządek osi Z witryny sterowania.

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

*pWndInsertAfter*<br/>
Wskaźnik do okna.

*x*<br/>
Nowa pozycja lewej strony okna.

*y*<br/>
Nowa pozycja górnej części okna.

*cx*<br/>
Nowa szerokość okna

*cy*<br/>
Nowa wysokość okna.

*nFlags*<br/>
Określa rozmiar okna i flagi pozycjonowania. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli to się powiedzie, w przeciwnym razie zero.

##  <a name="setwindowtext"></a>COleControlSite::SetWindowText

Ustawia tekst dla witryny sterowania.

```
virtual void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*lpszString*<br/>
Wskaźnik na ciąg zakończony znakiem null, który ma być używany jako nowy tytuł lub tekst kontrolny.

### <a name="remarks"></a>Uwagi

Ta funkcja najpierw próbuje ustawić właściwość webcaption. Jeśli właściwość Caption nie jest obsługiwana, właściwość Text zostanie ustawiona zamiast.

##  <a name="showwindow"></a>COleControlSite:: funkcja ShowWindow

Ustawia stan wyświetlania okna.

```
virtual BOOL ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Parametry

*nCmdShow*<br/>
Określa, w jaki sposób ma być wyświetlana lokacja kontrolki. Musi to być jedna z następujących wartości:

- SW_HIDE ukrywa to okno i przekazuje aktywację do innego okna.

- SW_MINIMIZE minimalizuje okno i uaktywnia okno najwyższego poziomu na liście systemu.

- SW_RESTORE aktywuje i wyświetla okno. Jeśli okno jest zminimalizowane lub zmaksymalizowane, system Windows przywraca jego oryginalny rozmiar i położenie.

- SW_SHOW aktywuje okno i wyświetla go w bieżącym rozmiarze i położeniu.

- SW_SHOWMAXIMIZED aktywuje okno i wyświetla je jako zmaksymalizowane okno.

- SW_SHOWMINIMIZED aktywuje okno i wyświetla go jako ikonę.

- SW_SHOWMINNOACTIVE wyświetla okno jako ikonę. Okno, które jest obecnie aktywne, pozostaje aktywne.

- SW_SHOWNA wyświetla okno w bieżącym stanie. Okno, które jest obecnie aktywne, pozostaje aktywne.

- SW_SHOWNOACTIVATE Wyświetla okno w jego najnowszym rozmiarze i położeniu. Okno, które jest obecnie aktywne, pozostaje aktywne.

- W ramach tego okna jest uaktywniane i wyświetlane okno. Jeśli okno jest zminimalizowane lub zmaksymalizowane, system Windows przywraca jego oryginalny rozmiar i położenie.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli okno było wcześniej widoczne; 0, jeśli okno zostało wcześniej ukryte.

## <a name="see-also"></a>Zobacz także

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)
