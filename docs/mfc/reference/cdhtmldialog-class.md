---
title: Klasa CDHtmlDialog
ms.date: 11/04/2016
f1_keywords:
- CDHtmlDialog
- AFXDHTML/CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CanAccessExternal
- AFXDHTML/CDHtmlDialog::CreateControlSite
- AFXDHTML/CDHtmlDialog::DDX_DHtml_AxControl
- AFXDHTML/CDHtmlDialog::DDX_DHtml_CheckBox
- AFXDHTML/CDHtmlDialog::DDX_DHtml_ElementText
- AFXDHTML/CDHtmlDialog::DDX_DHtml_Radio
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectIndex
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectString
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectValue
- AFXDHTML/CDHtmlDialog::DestroyModeless
- AFXDHTML/CDHtmlDialog::EnableModeless
- AFXDHTML/CDHtmlDialog::FilterDataObject
- AFXDHTML/CDHtmlDialog::GetControlDispatch
- AFXDHTML/CDHtmlDialog::GetControlProperty
- AFXDHTML/CDHtmlDialog::GetCurrentUrl
- AFXDHTML/CDHtmlDialog::GetDHtmlDocument
- AFXDHTML/CDHtmlDialog::GetDropTarget
- AFXDHTML/CDHtmlDialog::GetElement
- AFXDHTML/CDHtmlDialog::GetElementHtml
- AFXDHTML/CDHtmlDialog::GetElementInterface
- AFXDHTML/CDHtmlDialog::GetElementProperty
- AFXDHTML/CDHtmlDialog::GetElementText
- AFXDHTML/CDHtmlDialog::GetEvent
- AFXDHTML/CDHtmlDialog::GetExternal
- AFXDHTML/CDHtmlDialog::GetHostInfo
- AFXDHTML/CDHtmlDialog::GetOptionKeyPath
- AFXDHTML/CDHtmlDialog::HideUI
- AFXDHTML/CDHtmlDialog::IsExternalDispatchSafe
- AFXDHTML/CDHtmlDialog::LoadFromResource
- AFXDHTML/CDHtmlDialog::Navigate
- AFXDHTML/CDHtmlDialog::OnBeforeNavigate
- AFXDHTML/CDHtmlDialog::OnDocumentComplete
- AFXDHTML/CDHtmlDialog::OnDocWindowActivate
- AFXDHTML/CDHtmlDialog::OnFrameWindowActivate
- AFXDHTML/CDHtmlDialog::OnInitDialog
- AFXDHTML/CDHtmlDialog::OnNavigateComplete
- AFXDHTML/CDHtmlDialog::ResizeBorder
- AFXDHTML/CDHtmlDialog::SetControlProperty
- AFXDHTML/CDHtmlDialog::SetElementHtml
- AFXDHTML/CDHtmlDialog::SetElementProperty
- AFXDHTML/CDHtmlDialog::SetElementText
- AFXDHTML/CDHtmlDialog::SetExternalDispatch
- AFXDHTML/CDHtmlDialog::SetHostFlags
- AFXDHTML/CDHtmlDialog::ShowContextMenu
- AFXDHTML/CDHtmlDialog::ShowUI
- AFXDHTML/CDHtmlDialog::TranslateAccelerator
- AFXDHTML/CDHtmlDialog::TranslateUrl
- AFXDHTML/CDHtmlDialog::UpdateUI
- AFXDHTML/CDHtmlDialog::m_bUseHtmlTitle
- AFXDHTML/CDHtmlDialog::m_nHtmlResID
- AFXDHTML/CDHtmlDialog::m_pBrowserApp
- AFXDHTML/CDHtmlDialog::m_spHtmlDoc
- AFXDHTML/CDHtmlDialog::m_strCurrentUrl
- AFXDHTML/CDHtmlDialog::m_szHtmlResID
helpviewer_keywords:
- CDHtmlDialog [MFC], CDHtmlDialog
- CDHtmlDialog [MFC], CanAccessExternal
- CDHtmlDialog [MFC], CreateControlSite
- CDHtmlDialog [MFC], DDX_DHtml_AxControl
- CDHtmlDialog [MFC], DDX_DHtml_CheckBox
- CDHtmlDialog [MFC], DDX_DHtml_ElementText
- CDHtmlDialog [MFC], DDX_DHtml_Radio
- CDHtmlDialog [MFC], DDX_DHtml_SelectIndex
- CDHtmlDialog [MFC], DDX_DHtml_SelectString
- CDHtmlDialog [MFC], DDX_DHtml_SelectValue
- CDHtmlDialog [MFC], DestroyModeless
- CDHtmlDialog [MFC], EnableModeless
- CDHtmlDialog [MFC], FilterDataObject
- CDHtmlDialog [MFC], GetControlDispatch
- CDHtmlDialog [MFC], GetControlProperty
- CDHtmlDialog [MFC], GetCurrentUrl
- CDHtmlDialog [MFC], GetDHtmlDocument
- CDHtmlDialog [MFC], GetDropTarget
- CDHtmlDialog [MFC], GetElement
- CDHtmlDialog [MFC], GetElementHtml
- CDHtmlDialog [MFC], GetElementInterface
- CDHtmlDialog [MFC], GetElementProperty
- CDHtmlDialog [MFC], GetElementText
- CDHtmlDialog [MFC], GetEvent
- CDHtmlDialog [MFC], GetExternal
- CDHtmlDialog [MFC], GetHostInfo
- CDHtmlDialog [MFC], GetOptionKeyPath
- CDHtmlDialog [MFC], HideUI
- CDHtmlDialog [MFC], IsExternalDispatchSafe
- CDHtmlDialog [MFC], LoadFromResource
- CDHtmlDialog [MFC], Navigate
- CDHtmlDialog [MFC], OnBeforeNavigate
- CDHtmlDialog [MFC], OnDocumentComplete
- CDHtmlDialog [MFC], OnDocWindowActivate
- CDHtmlDialog [MFC], OnFrameWindowActivate
- CDHtmlDialog [MFC], OnInitDialog
- CDHtmlDialog [MFC], OnNavigateComplete
- CDHtmlDialog [MFC], ResizeBorder
- CDHtmlDialog [MFC], SetControlProperty
- CDHtmlDialog [MFC], SetElementHtml
- CDHtmlDialog [MFC], SetElementProperty
- CDHtmlDialog [MFC], SetElementText
- CDHtmlDialog [MFC], SetExternalDispatch
- CDHtmlDialog [MFC], SetHostFlags
- CDHtmlDialog [MFC], ShowContextMenu
- CDHtmlDialog [MFC], ShowUI
- CDHtmlDialog [MFC], TranslateAccelerator
- CDHtmlDialog [MFC], TranslateUrl
- CDHtmlDialog [MFC], UpdateUI
- CDHtmlDialog [MFC], m_bUseHtmlTitle
- CDHtmlDialog [MFC], m_nHtmlResID
- CDHtmlDialog [MFC], m_pBrowserApp
- CDHtmlDialog [MFC], m_spHtmlDoc
- CDHtmlDialog [MFC], m_strCurrentUrl
- CDHtmlDialog [MFC], m_szHtmlResID
ms.assetid: 3f941c85-87e1-4f0f-9cc5-ffee8498b312
ms.openlocfilehash: 08db42929fb3c6a7feb79abae5110bd88169f11b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594964"
---
# <a name="cdhtmldialog-class"></a>Klasa CDHtmlDialog

Służy do utworzenia okien dialogowych, które korzystają z HTML a nie zasobów dialogowych do implementacji interfejsu użytkownika.

## <a name="syntax"></a>Składnia

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDHtmlDialog::CDHtmlDialog](#cdhtmldialog)|Tworzy obiekt CDHtmlDialog.|
|[CDHtmlDialog:: ~ CDHtmlDialog](#cdhtmldialog__~cdhtmldialog)|Niszczy obiekt CDHtmlDialog.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDHtmlDialog::CanAccessExternal](#canaccessexternal)|Możliwym do zastąpienia o nazwie jako kontroli dostępu, czy obiekty skryptowe na stronie załadować uzyskać dostęp do zewnętrznych wysyłania kontroli lokacji. Sprawdza, czy na pewno wysyłki jest bezpieczny dla skryptów albo bieżącej strefy umożliwia obiektów, które nie są bezpieczne dla skryptów.|
|[CDHtmlDialog::CreateControlSite](#createcontrolsite)|Overridable użyty do utworzenia wystąpienia witryny formantu do hostowania formantu WebBrowser w oknie dialogowym.|
|[CDHtmlDialog::DDX_DHtml_AxControl](#ddx_dhtml_axcontrol)|Wymienia dane między zmiennej składowej, a wartość właściwości kontrolki ActiveX na stronie HTML.|
|[CDHtmlDialog::DDX_DHtml_CheckBox](#ddx_dhtml_checkbox)|Wymiana danych między zmienną członkowską i pola wyboru na stronie HTML.|
|[CDHtmlDialog::DDX_DHtml_ElementText](#ddx_dhtml_elementtext)|Wymiana danych między zmienną członkowską i dowolnej właściwości elementu HTML na stronie HTML.|
|[CDHtmlDialog::DDX_DHtml_Radio](#ddx_dhtml_radio)|Wymiana danych między zmienną członkowską i przycisk radiowy na stronie HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|Pobiera lub ustawia indeks pola listy na stronie HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectString](#ddx_dhtml_selectstring)|Pobiera lub ustawia tekst wyświetlany wpisu pole listy (oparte na bieżący indeks) na stronie HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|Pobiera lub ustawia wartość wpisu pole listy (oparte na bieżący indeks) na stronie HTML.|
|[CDHtmlDialog::DestroyModeless](#destroymodeless)|Niszczy niemodalnego okna dialogowego.|
|[CDHtmlDialog::EnableModeless](#enablemodeless)|Umożliwia Niemodalne okna dialogowe.|
|[CDHtmlDialog::FilterDataObject](#filterdataobject)|Umożliwia okna dialogowego odfiltrować obiekty danych schowka utworzone przez przeglądarki hostowanej.|
|[CDHtmlDialog::GetControlDispatch](#getcontroldispatch)|Pobiera `IDispatch` interfejsu na kontrolce ActiveX osadzony w dokumencie HTML.|
|[CDHtmlDialog::GetControlProperty](#getcontrolproperty)|Pobiera żądanej właściwości określonego formantu ActiveX.|
|[CDHtmlDialog::GetCurrentUrl](#getcurrenturl)|Pobiera Uniform Resource Locator (adres URL) są skojarzone z bieżącym dokumentem.|
|[CDHtmlDialog::GetDHtmlDocument](#getdhtmldocument)|Pobiera interfejs IHTMLDocument2 w aktualnie załadowanych dokumentu HTML.|
|[CDHtmlDialog::GetDropTarget](#getdroptarget)|Wywoływane przez zawarte formantu WebBrowser, gdy jest on używany jako miejsca docelowego zezwalająca na oknie dialogowym, aby podać zamiast [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).|
|[CDHtmlDialog::GetElement](#getelement)|Pobiera interfejs w elemencie HTML.|
|[CDHtmlDialog::GetElementHtml](#getelementhtml)|Pobiera `innerHTML` właściwość elementu HTML.|
|[CDHtmlDialog::GetElementInterface](#getelementinterface)|Pobiera wskaźnik do żądanego interfejsu z elementu HTML.|
|[CDHtmlDialog::GetElementProperty](#getelementproperty)|Pobiera wartość właściwości elementu HTML.|
|[CDHtmlDialog::GetElementText](#getelementtext)|Pobiera `innerText` właściwość elementu HTML.|
|[CDHtmlDialog::GetEvent](#getevent)|Pobiera `IHTMLEventObj` wskaźnik do bieżącego obiektu zdarzenia.|
|[CDHtmlDialog::GetExternal](#getexternal)|Pobiera hosta `IDispatch` interfejsu.|
|[CDHtmlDialog::GetHostInfo](#gethostinfo)|Pobiera funkcje interfejsu użytkownika hosta.|
|[CDHtmlDialog::GetOptionKeyPath](#getoptionkeypath)|Pobiera klucz rejestru, w którym są przechowywane preferencje użytkownika.|
|[CDHtmlDialog::HideUI](#hideui)|Ukrywa hosta w interfejsie użytkownika.|
|[CDHtmlDialog::IsExternalDispatchSafe](#isexternaldispatchsafe)|Wskazuje, czy host `IDispatch` interfejsu jest bezpieczny dla skryptów.|
|[CDHtmlDialog::LoadFromResource](#loadfromresource)|Ładuje określony zasób do formantu WebBrowser.|
|[CDHtmlDialog::Navigate](#navigate)|Powoduje przejście do określonego adresu URL.|
|[CDHtmlDialog::OnBeforeNavigate](#onbeforenavigate)|Metoda wywoływana przez platformę przed jest wyzwalane zdarzenie nawigacji.|
|[CDHtmlDialog::OnDocumentComplete](#ondocumentcomplete)|Metoda wywoływana przez platformę, by powiadomić aplikację, gdy dokument osiąga stan READYSTATE_COMPLETE.|
|[CDHtmlDialog::OnDocWindowActivate](#ondocwindowactivate)|Wywoływane przez platformę, gdy okno dokumentu jest aktywowane lub dezaktywowane.|
|[CDHtmlDialog::OnFrameWindowActivate](#onframewindowactivate)|Wywoływane przez platformę, gdy okno ramowe jest aktywowane lub dezaktywowane.|
|[CDHtmlDialog::OnInitDialog](#oninitdialog)|Wywołany w odpowiedzi na wiadomość / / Złap.|
|[CDHtmlDialog::OnNavigateComplete](#onnavigatecomplete)|Wywoływane przez platformę, po zakończeniu zdarzeń nawigacji.|
|[CDHtmlDialog::ResizeBorder](#resizeborder)|Powiadamia obiekt, który należy ją zmienić rozmiar miejsca jego obramowania.|
|[CDHtmlDialog::SetControlProperty](#setcontrolproperty)|Ustawia właściwość formantu ActiveX na nową wartość.|
|[CDHtmlDialog::SetElementHtml](#setelementhtml)|Zestawy `innerHTML` właściwość elementu HTML.|
|[CDHtmlDialog::SetElementProperty](#setelementproperty)|Ustawia właściwość elementu HTML.|
|[CDHtmlDialog::SetElementText](#setelementtext)|Zestawy `innerText` właściwość elementu HTML.|
|[CDHtmlDialog::SetExternalDispatch](#setexternaldispatch)|Ustawia hosta `IDispatch` interfejsu.|
|[CDHtmlDialog::SetHostFlags](#sethostflags)|Ustawia flagi interfejsu użytkownika hosta.|
|[CDHtmlDialog::ShowContextMenu](#showcontextmenu)|Wywołuje się, gdy menu kontekstowe ma być wyświetlany.|
|[CDHtmlDialog::ShowUI](#showui)|Pokazuje hosta w interfejsie użytkownika.|
|[CDHtmlDialog::TranslateAccelerator](#translateaccelerator)|Wywoływane w celu przetwarzania komunikatów klawisza skrótu menu.|
|[CDHtmlDialog::TranslateUrl](#translateurl)|Wywołuje się, aby zmodyfikować adres URL do załadowania.|
|[CDHtmlDialog::UpdateUI](#updateui)|Wywołuje się, by powiadomić hosta, którego stan polecenia został zmieniony.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDHtmlDialog::m_bUseHtmlTitle](#m_busehtmltitle)|Wskazuje, czy ma być używany tytuł dokumentu HTML jako okna dialogowego podpisu.|
|[CDHtmlDialog::m_nHtmlResID](#m_nhtmlresid)|Zasób identyfikator HTML zasobów do wyświetlenia.|
|[CDHtmlDialog::m_pBrowserApp](#m_pbrowserapp)|Wskaźnik do aplikacji przeglądarki sieci Web.|
|[CDHtmlDialog::m_spHtmlDoc](#m_sphtmldoc)|Wskaźnik do dokumentu HTML.|
|[CDHtmlDialog::m_strCurrentUrl](#m_strcurrenturl)|Bieżący adres URL.|
|[CDHtmlDialog::m_szHtmlResID](#m_szhtmlresid)|Identyfikator zasobu HTML wersję ciągu|

## <a name="remarks"></a>Uwagi

`CDHtmlDialog` można załadować HTML mają być wyświetlane z albo zasobu HTML lub adres URL.

`CDHtmlDialog` można danych programu exchange przy użyciu kontrolek HTML i obsługiwać zdarzenia z kontrolek HTML, takich jak kliknięcie przycisku.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

`CDHtmlDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdhtml.h

##  <a name="ddx_dhtml_helper_macros"></a>  Makra pomocnika Ddx_dhtml

Makra pomocnika ddx_dhtml umożliwia łatwy dostęp do często używanych właściwości formantów na stronie HTML.

### <a name="data-exchange-macros"></a>Makra wymiany danych

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|Ustawia lub pobiera wartość właściwości z wybranej kontrolki.|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|Ustawia lub pobiera tekstu między tagiem początkowym i końcowym bieżącego elementu.|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|Ustawia lub pobiera kodu HTML między tagiem początkowym i końcowym bieżącego elementu.|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|Ustawia lub pobiera docelowy adres URL i punktu kontrolnego.|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|Ustawia lub pobiera docelowego okna lub ramki.|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|Ustawia lub pobiera nazwę obrazu lub klip wideo w dokumencie.|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|Ustawia lub pobiera adres URL skojarzony ramki.|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|Ustawia lub pobiera adres URL skojarzony ramki.|

##  <a name="canaccessexternal"></a>  CDHtmlDialog::CanAccessExternal

Możliwym do zastąpienia o nazwie jako kontroli dostępu, czy obiekty skryptowe na stronie załadować uzyskać dostęp do zewnętrznych wysyłania kontroli lokacji. Sprawdza, czy na pewno wysyłki jest bezpieczny dla skryptów albo bieżącej strefy umożliwia obiektów, które nie są bezpieczne dla skryptów.

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

##  <a name="cdhtmldialog"></a>  CDHtmlDialog::CDHtmlDialog

Tworzy oparte na zasobach dynamicznego HTML okno dialogowe.

```
CDHtmlDialog();

CDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID,
    CWnd *pParentWnd = NULL);

CDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd *pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Ciąg zakończony znakiem null, który nazywa się okno dialogowe zasobu szablon.

*szHtmlResID*<br/>
Ciąg zakończony znakiem null jest nazwą zasobu HTML.

*pParentWnd*<br/>
Wskaźnik do obiektu okna nadrzędnego lub właściciela (typu [CWnd](../../mfc/reference/cwnd-class.md)) do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okna nadrzędnego obiektu okna dialogowego jest ustawiony na okna głównego aplikacji.

*nIDTemplate*<br/>
Zawiera identyfikator zasobu szablon okno dialogowe.

*nHtmlResID*<br/>
Zawiera identyfikator zasobu HTML.

### <a name="remarks"></a>Uwagi

Druga forma Konstruktor zapewnia dostęp do zasobu okna dialogowego za pomocą nazwy szablonu. Trzecia formą Konstruktor zapewnia dostęp do zasobu okna dialogowego za pomocą identyfikator szablonu zasobów. Zazwyczaj identyfikator rozpoczyna się od **IDD_** prefiks.

##  <a name="_dtorcdhtmldialog"></a>  CDHtmlDialog:: ~ CDHtmlDialog

Niszczy obiekt CDHtmlDialog.

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>Uwagi

[CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) funkcja elementu członkowskiego musi być używane do niszczenia Niemodalne okna dialogowe, które są tworzone przez [CDialog::Create](../../mfc/reference/cdialog-class.md#create).

##  <a name="createcontrolsite"></a>  CDHtmlDialog::CreateControlSite

Overridable użyty do utworzenia wystąpienia witryny formantu do hostowania formantu WebBrowser w oknie dialogowym.

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>Parametry

*pContainer*<br/>
Wskaźnik do [COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md) obiektu

*ppSite*<br/>
Wskaźnik do wskaźnika do [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można zastąpić tę funkcję elementu członkowskiego, aby zwrócić wystąpienia klasy lokacji własne kontrolki.

##  <a name="ddx_dhtml_axcontrol"></a>  CDHtmlDialog::DDX_DHtml_AxControl

Wymienia dane między zmiennej składowej, a wartość właściwości kontrolki ActiveX na stronie HTML.

```
void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispid,
    VARIANT& var);

void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    LPCTSTR szPropName,
    VARIANT& var);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*szId*<br/>
Wartość parametru ID tagu obiektu w kodzie źródłowym HTML dla formantu ActiveX.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości, za pomocą którego ma zostać wymiany danych.

*szPropName*<br/>
Nazwa właściwości.

*var*<br/>
Element członkowski danych, typu VARIANT, [COleVariant](../../mfc/reference/colevariant-class.md), lub [CComVariant](../../atl/reference/ccomvariant-class.md), który przechowuje wartość wymieniane przy użyciu właściwości kontrolki ActiveX.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

##  <a name="ddx_dhtml_checkbox"></a>  CDHtmlDialog::DDX_DHtml_CheckBox

Wymiana danych między zmienną członkowską i pola wyboru na stronie HTML.

```
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*szId*<br/>
Wartość określona dla parametru Identyfikatora kontrolki HTML.

*value*<br/>
Wartość wymianie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

##  <a name="ddx_dhtml_elementtext"></a>  CDHtmlDialog::DDX_DHtml_ElementText

Wymiana danych między zmienną członkowską i dowolnej właściwości elementu HTML na stronie HTML.

```
void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispid,
    CString& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispid,
    short& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispid,
    int& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispid,
    long& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispid,
    DWORD& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispid,
    float& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*szId*<br/>
Wartość określona dla parametru Identyfikatora kontrolki HTML.

*identyfikator DISPID*<br/>
Identyfikator wysyłania elementu HTML, z którym chcesz wymiany danych.

*value*<br/>
Wartość wymianie.

##  <a name="ddx_dhtml_radio"></a>  CDHtmlDialog::DDX_DHtml_Radio

Wymiana danych między zmienną członkowską i przycisk radiowy na stronie HTML.

```
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*szId*<br/>
Wartość określona dla parametru Identyfikatora kontrolki HTML.

*value*<br/>
Wartość wymianie.

##  <a name="ddx_dhtml_selectindex"></a>  CDHtmlDialog::DDX_DHtml_SelectIndex

Pobiera lub ustawia indeks pola listy na stronie HTML.

```
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*szId*<br/>
Wartość określona dla parametru identyfikatora kontrolki HTML.

*value*<br/>
Wartość wymianie.

##  <a name="ddx_dhtml_selectstring"></a>  CDHtmlDialog::DDX_DHtml_SelectString

Pobiera lub ustawia tekst wyświetlany wpisu pole listy (oparte na bieżący indeks) na stronie HTML.

```
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*szId*<br/>
Wartość określona dla parametru Identyfikatora kontrolki HTML.

*value*<br/>
Wartość wymianie.

##  <a name="ddx_dhtml_selectvalue"></a>  CDHtmlDialog::DDX_DHtml_SelectValue

Pobiera lub ustawia wartość wpisu pole listy (oparte na bieżący indeks) na stronie HTML.

```
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*szId*<br/>
Wartość określona dla parametru Identyfikatora kontrolki HTML.

*value*<br/>
Wartość wymianie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

##  <a name="destroymodeless"></a>  CDHtmlDialog::DestroyModeless

Odłącza niemodalnego okna dialogowego z `CDHtmlDialog` obiektu i niszczy obiekt.

```
void DestroyModeless();
```

##  <a name="enablemodeless"></a>  CDHtmlDialog::EnableModeless

Umożliwia Niemodalne okna dialogowe.

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>Parametry

*fEnable*<br/>
Zobacz *fEnable* w [IDocHostUIHandler::EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją firmy CDHtmlDialog [IDocHostUIHandler::EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx), zgodnie z opisem w zestawie Windows SDK.

##  <a name="filterdataobject"></a>  CDHtmlDialog::FilterDataObject

Umożliwia okna dialogowego odfiltrować obiekty danych schowka utworzone przez przeglądarki hostowanej.

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>Parametry

*pDO*<br/>
Zobacz *pDO* w [IDocHostUIHandler::FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx) w zestawie Windows SDK.

*ppDORet*<br/>
Zobacz *ppDORet* w `IDocHostUIHandler::FilterDataObject` w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją firmy CDHtmlDialog [IDocHostUIHandler::FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx), zgodnie z opisem w zestawie Windows SDK.

##  <a name="getcontroldispatch"></a>  CDHtmlDialog::GetControlDispatch

Pobiera `IDispatch` interfejsu na kontrolce ActiveX osadzony w dokumencie HTML zwrócony przez [GetDHtmlDocument](#getdhtmldocument).

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>Parametry

*szId*<br/>
Identyfikator HTML formantu ActiveX.

*ppdisp*<br/>
`IDispatch` Interfejsu formantu Jeśli znalezione na stronie sieci Web.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="getcontrolproperty"></a>  CDHtmlDialog::GetControlProperty

Pobiera żądanej właściwości określonego formantu ActiveX.

```
VARIANT GetControlProperty(
    LPCTSTR szId,
    LPCTSTR szPropName);

VARIANT GetControlProperty(
    LPCTSTR szId,
    DISPID dispid);

VARIANT GetControlProperty(
    IDispatch* pdispControl,
    DISPID dispid);
```

### <a name="parameters"></a>Parametry

*szId*<br/>
Identyfikator HTML formantu ActiveX.

*szPropName*<br/>
Nazwa właściwości w domyślnych ustawień regionalnych bieżącego użytkownika.

*pdispControl*<br/>
`IDispatch` Wskaźnika formantu ActiveX.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości.

### <a name="return-value"></a>Wartość zwracana

Typ variant zawierający żądanej właściwości lub pusty wariant, jeśli nie można znaleźć formantu lub właściwości.

### <a name="remarks"></a>Uwagi

Przeciążenia są wyświetlane z co najmniej wydajne u góry do najbardziej efektywny u dołu.

##  <a name="getcurrenturl"></a>  CDHtmlDialog::GetCurrentUrl

Pobiera Uniform Resource Locator (adres URL) są skojarzone z bieżącym dokumentem.

```
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>Parametry

*szUrl*<br/>
A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający adres URL do pobrania.

##  <a name="getdhtmldocument"></a>  CDHtmlDialog::GetDHtmlDocument

Pobiera [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interfejsu w aktualnie załadowanych dokumentu HTML.

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>Parametry

*\*\*pphtmlDoc* wskaźnik na wskaźnik do dokumentu HTML.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT. Zwraca wartość S_OK w przypadku powodzenia.

##  <a name="getdroptarget"></a>  CDHtmlDialog::GetDropTarget

Wywoływane przez zawarte formantu WebBrowser, gdy jest on używany jako miejsca docelowego zezwalająca na oknie dialogowym, aby podać zamiast [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>Parametry

*pDropTarget*<br/>
Zobacz *pDropTarget* w [IDocHostUIHandler::GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx) w zestawie Windows SDK.

*ppDropTarget*<br/>
Zobacz *ppDropTarget* w `IDocHostUIHandler::GetDropTarget` w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją firmy CDHtmlDialog [IDocHostUIHandler::GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx), zgodnie z opisem w zestawie Windows SDK.

##  <a name="getelement"></a>  CDHtmlDialog::GetElement

Zwraca interfejs dla elementu HTML określonego przez *szElementId*.

```
HRESULT GetElement(
    LPCTSTR szElementId,
    IDispatch** ppdisp,
    BOOL* pbCollection = NULL);

HRESULT GetElement(
    LPCTSTR szElementId,
    IHTMLElement** pphtmlElement);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

*ppdisp*<br/>
`IDispatch` Wskaźnik do żądanego elementu lub kolekcję elementów.

*pbCollection*<br/>
Wartość logiczna wskazująca, czy obiekt reprezentowany przez *ppdisp* jest pojedynczy element lub zbiór elementów.

*pphtmlElement*<br/>
`IHTMLElement` Wskaźnik do żądanego elementu.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Użyj pierwszego przeciążenia, jeśli chcesz obsługiwać sytuacje, w których może być więcej niż jeden element o określonym identyfikatorze. Ostatni parametr można użyć, aby dowiedzieć się, czy wskaźnik interfejsu zwrócone do kolekcji lub pojedynczy element. Jeśli wskaźnik interfejsu znajduje się w kolekcji, można wyszukiwać `IHTMLElementCollection` i używać jej `item` właściwości do odwoływania się do elementów przez porządkowym.

Drugie przeciążenie zakończy się niepowodzeniem, jeśli istnieje więcej niż jeden element o tym samym identyfikatorze na stronie.

##  <a name="getelementhtml"></a>  CDHtmlDialog::GetElementHtml

Pobiera `innerHTML` właściwość elementu HTML identyfikowane przez *szElementId*.

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

### <a name="return-value"></a>Wartość zwracana

`innerHTML` Właściwość elementu HTML identyfikowane przez *szElementId* lub wartość NULL, jeśli element nie został odnaleziony.

##  <a name="getelementinterface"></a>  CDHtmlDialog::GetElementInterface

Pobiera wskaźnik do żądanego interfejsu z elementu HTML identyfikowane przez *szElementId*.

```
template <class Q> HRESULT GetElementInterface(
    LPCTSTR szElementId,
    Q** ppvObj);

HRESULT GetElementInterface(
    LPCTSTR szElementId,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

*ppvObj*<br/>
Adres wskaźnika, który zostanie wypełnione przy użyciu wskaźnika żądanego interfejsu, jeśli element zostanie znaleziony i zapytanie zakończy się pomyślnie.

*Parametr riid*<br/>
Interfejs identyfikator (IID) żądanego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

##  <a name="getelementproperty"></a>  CDHtmlDialog::GetElementProperty

Pobiera wartość właściwości identyfikowane przez *dispid* z elementu HTML identyfikowane przez *szElementId*.

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispid);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości.

### <a name="return-value"></a>Wartość zwracana

Wartość właściwości lub pusty wariant, jeśli nie można odnaleźć właściwości lub elementu.

##  <a name="getelementtext"></a>  CDHtmlDialog::GetElementText

Pobiera `innerText` właściwość elementu HTML identyfikowane przez *szElementId*.

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

### <a name="return-value"></a>Wartość zwracana

`innerText` Właściwość elementu HTML identyfikowane przez *szElementId* lub wartość NULL, jeśli właściwość lub element nie został odnaleziony.

##  <a name="getevent"></a>  CDHtmlDialog::GetEvent

Zwraca `IHTMLEventObj` wskaźnik do bieżącego obiektu zdarzenia.

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>Parametry

*ppEventObj*<br/>
Adres wskaźnika, który zostanie wypełniony kolorem `IHTMLEventObj` wskaźnika interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana tylko z w obsługi zdarzeń DHTML.

##  <a name="getexternal"></a>  CDHtmlDialog::GetExternal

Pobiera hosta `IDispatch` interfejsu.

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>Parametry

*ppDispatch*<br/>
Zobacz *ppDispatch* w [IDocHostUIHandler::GetExternal](https://msdn.microsoft.com/library/aa753256.aspx) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK od tego, czy E_NOTIMPL w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją firmy CDHtmlDialog [IDocHostUIHandler::GetExternal](https://msdn.microsoft.com/library/aa753256.aspx), zgodnie z opisem w zestawie Windows SDK.

##  <a name="gethostinfo"></a>  CDHtmlDialog::GetHostInfo

Pobiera funkcje interfejsu użytkownika hosta.

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>Parametry

*pInfo*<br/>
Zobacz *pInfo* w [IDocHostUIHandler::GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją firmy CDHtmlDialog [IDocHostUIHandler::GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx), zgodnie z opisem w zestawie Windows SDK.

##  <a name="getoptionkeypath"></a>  CDHtmlDialog::GetOptionKeyPath

Pobiera klucz rejestru, w którym są przechowywane preferencje użytkownika.

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>Parametry

*pchKey*<br/>
Zobacz *pchKey* w [IDocHostUIHandler::GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx) w zestawie Windows SDK.

*Magazyn danych*<br/>
Zobacz *dw* w `IDocHostUIHandler::GetOptionKeyPath` w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją firmy CDHtmlDialog [IDocHostUIHandler::GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx), zgodnie z opisem w zestawie Windows SDK.

##  <a name="hideui"></a>  CDHtmlDialog::HideUI

Ukrywa hosta w interfejsie użytkownika.

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją firmy CDHtmlDialog [IDocHostUIHandler::HideUI](https://msdn.microsoft.com/library/aa753259.aspx), zgodnie z opisem w zestawie Windows SDK.

##  <a name="isexternaldispatchsafe"></a>  CDHtmlDialog::IsExternalDispatchSafe

Wskazuje, czy host `IDispatch` interfejsu jest bezpieczny dla skryptów.

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość FALSE.

##  <a name="loadfromresource"></a>  CDHtmlDialog::LoadFromResource

Ładuje określony zasób do formantu WebBrowser w oknie dialogowym DHTML.

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>Parametry

*lpszResource*<br/>
Wskaźnik do ciągu zawierającego nazwę zasobu do załadowania.

*nRes*<br/>
Identyfikator zasobu do załadowania.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.

##  <a name="m_busehtmltitle"></a>  CDHtmlDialog::m_bUseHtmlTitle

Wskazuje, czy ma być używany tytuł dokumentu HTML jako okna dialogowego podpisu.

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>Uwagi

Jeśli **m**_ **bUseHtmlTitle** ma wartość PRAWDA, to okno dialogowe jest równe tytuł dokumentu HTML; w przeciwnym razie zostanie użyty podpis w zasobu okna dialogowego.

##  <a name="m_nhtmlresid"></a>  CDHtmlDialog::m_nHtmlResID

Zasób identyfikator HTML zasobów do wyświetlenia.

```
UINT m_nHtmlResID;
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

##  <a name="m_pbrowserapp"></a>  CDHtmlDialog::m_pBrowserApp

Wskaźnik do aplikacji przeglądarki sieci Web.

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

##  <a name="m_sphtmldoc"></a>  CDHtmlDialog::m_spHtmlDoc

Wskaźnik do dokumentu HTML.

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

##  <a name="m_strcurrenturl"></a>  CDHtmlDialog::m_strCurrentUrl

Bieżący adres URL.

```
CString m_strCurrentUrl;
```

##  <a name="m_szhtmlresid"></a>  CDHtmlDialog::m_szHtmlResID

Identyfikator zasobu HTML wersję ciągu

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

##  <a name="navigate"></a>  CDHtmlDialog::Navigate

Powoduje przejście do zasobu wskazywanego przez adres URL, który jest określony przez *lpszURL*.

```
void Navigate(
    LPCTSTR lpszURL,
    DWORD dwFlags = 0,
    LPCTSTR lpszTargetFrameName = NULL,
    LPCTSTR lpszHeaders = NULL,
    LPVOID lpvPostData = NULL,
    DWORD dwPostDataLen = 0);
```

### <a name="parameters"></a>Parametry

*lpszURL*<br/>
Wskaźnik do ciągu zawierającego adres URL, który ma zostać użyty.

*Flagidw*<br/>
Flagi zmiennej, która określa, czy można dodać zasobu do listy historii, czy do pamięci podręcznej odczytu lub zapisu z pamięci podręcznej i czy ma być wyświetlany zasób w nowym oknie. Zmienna może być kombinacją wartości zdefiniowanych przez [BrowserNavConstants](https://msdn.microsoft.com/library/aa768360.aspx) wyliczenia.

*lpszTargetFrameName*<br/>
Wskaźnik na ciąg, który zawiera nazwę ramki, w której do wyświetlenia tego zasobu.

*lpszHeaders*<br/>
Wskaźnik do wartości, który określa nagłówki HTTP do wysłania na serwer. Tych nagłówków są dodawane do domyślne nagłówki programu Internet Explorer. Nagłówki można określić informacje takie czynności serwera typu danych przekazywanych do serwera lub kod stanu. Ten parametr jest ignorowany, jeśli adres URL nie jest adres URL protokołu HTTP.

*lpvPostData*<br/>
Wskaźnik do danych do wysyłania za pomocą transakcji HTTP POST. Na przykład transakcji WPIS jest używany do wysyłania danych zbieranych przez formularza HTML. Jeśli ten parametr nie określono żadnych danych post `Navigate` wystawia transakcja HTTP GET. Ten parametr jest ignorowany, jeśli adres URL nie jest adres URL protokołu HTTP.

*dwPostDataLen*<br/>
Dane do przesłania za pomocą transakcji HTTP POST. Na przykład transakcji WPIS jest używany do wysyłania danych zbieranych przez formularza HTML. Jeśli ten parametr nie określono żadnych danych post `Navigate` wystawia transakcja HTTP GET. Ten parametr jest ignorowany, jeśli adres URL jest adres URL protokołu HTTP.

##  <a name="onbeforenavigate"></a>  CDHtmlDialog::OnBeforeNavigate

Metoda wywoływana przez platformę, by powodować zdarzenia przed wystąpieniem nawigacji.

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Wskaźnik do `IDispatch` obiektu.

*szUrl*<br/>
Wskaźnik do ciągu zawierającego adres URL, aby przejść do.

##  <a name="ondocumentcomplete"></a>  CDHtmlDialog::OnDocumentComplete

Metoda wywoływana przez platformę, by powiadomić aplikację, gdy dokument zdobyła osiąga stan READYSTATE_COMPLETE.

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Wskaźnik do `IDispatch` obiektu.

*szUrl*<br/>
Wskaźnik do ciągu zawierającego adres URL, który został przejście.

##  <a name="ondocwindowactivate"></a>  CDHtmlDialog::OnDocWindowActivate

Wywoływane przez platformę, gdy okno dokumentu jest aktywowane lub dezaktywowane.

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parametry

*fActivate*<br/>
Zobacz *fActivate* w [IDocHostUIHandler::OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacja firmy CDHtmlDialog [IDocHostUIHandler::OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx), zgodnie z opisem w zestawie Windows SDK.

##  <a name="onframewindowactivate"></a>  CDHtmlDialog::OnFrameWindowActivate

Wywoływane przez platformę, gdy okno ramowe jest aktywowane lub dezaktywowane.

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parametry

*fActivate*<br/>
Zobacz *fActivate* w [IDocHostUIHandler::OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją firmy CDHtmlDialog [IDocHostUIHandler::OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx), zgodnie z opisem w zestawie Windows SDK.

##  <a name="oninitdialog"></a>  CDHtmlDialog::OnInitDialog

Wywołany w odpowiedzi na wiadomość / / Złap.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Ten komunikat jest wysyłany do okna dialogowego podczas `Create`, `CreateIndirect`, lub `DoModal` wywołania, które występują, natychmiast, zanim zostanie wyświetlone okno dialogowe.

Ta funkcja elementu członkowskiego należy zastąpić, jeśli trzeba wykonać specjalnego przetwarzania, gdy okno dialogowe jest zainicjowany. W wersji zastąpione, należy najpierw wywołać klasy bazowej `OnInitDialog` , ale nie brać pod uwagę jego zwracanej wartości. Z funkcji zgodnym z przesłoniętą składową, będzie zwykle zwraca wartość TRUE.

Windows wywołuje `OnInitDialog` funkcje za pośrednictwem wspólne dla wszystkich bibliotekę Microsoft Foundation Class oknach dialogowych procedury standardowe globalne — okno dialogowe, a nie za pomocą mapy wiadomości, więc nie trzeba wpis mapy komunikatów dla tej funkcji elementu członkowskiego.

##  <a name="onnavigatecomplete"></a>  CDHtmlDialog::OnNavigateComplete

Wywoływane przez platformę, po zakończeniu nawigacji pod określony adres URL.

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Wskaźnik do `IDispatch` obiektu.

*szUrl*<br/>
Wskaźnik do ciągu zawierającego adres URL, który został przejście.

##  <a name="resizeborder"></a>  CDHtmlDialog::ResizeBorder

Powiadamia obiekt, który należy ją zmienić rozmiar miejsca jego obramowania.

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>Parametry

*prcBorder*<br/>
Zobacz *prcBorder* w [IDocHostUIHandler::ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx) w zestawie Windows SDK.

*pUIWindow*<br/>
Zobacz *pUIWindow* w `IDocHostUIHandler::ResizeBorder` w zestawie Windows SDK.

*fFrameWindow*<br/>
Zobacz *fFrameWindow* w `IDocHostUIHandler::ResizeBorder` w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

##  <a name="setcontrolproperty"></a>  CDHtmlDialog::SetControlProperty

Ustawia właściwość formantu ActiveX na nową wartość.

```
void SetControlProperty(
    LPCTSTR szElementId,
    DISPID dispid,
    VARIANT* pVar);

void SetControlProperty(
    IDispatch* pdispControl,
    DISPID dispid,
    VARIANT* pVar);

void SetControlProperty(
    LPCTSTR szElementId,
    LPCTSTR szPropName,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator HTML formantu ActiveX.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości do ustawienia.

*pVar*<br/>
Wskaźnik na typ VARIANT zawierający nowa wartość właściwości.

*pdispControl*<br/>
Wskaźnik do formantu ActiveX `IDispatch` interfejsu.

*szPropName*<br/>
Ciąg zawierający nazwę właściwości do ustawienia.

##  <a name="setelementhtml"></a>  CDHtmlDialog::SetElementHtml

Zestawy `innerHTML` właściwość elementu HTML.

```
void SetElementHtml(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementHtml(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

*bstrText*<br/>
Nowa wartość `innerHTML` właściwości.

*punkElem*<br/>
`IUnknown` Wskaźnika elementu HTML.

##  <a name="setelementproperty"></a>  CDHtmlDialog::SetElementProperty

Ustawia właściwość elementu HTML.

```
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispid,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości do ustawienia.

*pVar*<br/>
Nowa wartość właściwości.

##  <a name="setelementtext"></a>  CDHtmlDialog::SetElementText

Zestawy `innerText` właściwość elementu HTML.

```
void SetElementText(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementText(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

*bstrText*<br/>
Nowa wartość `innerText` właściwości.

*punkElem*<br/>
`IUnknown` Wskaźnika elementu HTML.

##  <a name="setexternaldispatch"></a>  CDHtmlDialog::SetExternalDispatch

Ustawia hosta `IDispatch` interfejsu.

```
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>Parametry

*pdispExternal*<br/>
Nowy `IDispatch` interfejsu.

##  <a name="sethostflags"></a>  CDHtmlDialog::SetHostFlags

Ustawia host flagi interfejsu użytkownika.

```
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*Flagidw*<br/>
Możliwe wartości, zobacz [DOCHOSTUIFLAG](https://msdn.microsoft.com/library/aa753277.aspx) w zestawie Windows SDK.

##  <a name="showcontextmenu"></a>  CDHtmlDialog::ShowContextMenu

Wywołuje się, gdy menu kontekstowe ma być wyświetlany.

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>Parametry

*dwID*<br/>
Zobacz *dwID* w [IDocHostUIHandler::ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx) w zestawie Windows SDK.

*ppt*<br/>
Zobacz *ppt* w `IDocHostUIHandler::ShowContextMenu` w Windows SDK.

*pcmdtReserved*<br/>
Zobacz *pcmdtReserved* w `IDocHostUIHandler::ShowContextMenu` w zestawie Windows SDK.

*pdispReserved*<br/>
Zobacz *pdispReserved* w `IDocHostUIHandler::ShowContextMenu` w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją firmy CDHtmlDialog [IDocHostUIHandler::ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx), zgodnie z opisem w zestawie Windows SDK.

##  <a name="showui"></a>  CDHtmlDialog::ShowUI

Pokazuje hosta w interfejsie użytkownika.

```
STDMETHOD(ShowUI)(
    DWORD dwID,
    IOleInPlaceActiveObject* pActiveObject,
    IOleCommandTarget* pCommandTarget,
    IOleInPlaceFrame* pFrame,
    IOleInPlaceUIWindow* pDoc);
```

### <a name="parameters"></a>Parametry

*dwID*<br/>
Zobacz *dwID* w [IDocHostUIHandler::ShowUI](https://msdn.microsoft.com/library/aa753265.aspx) w zestawie Windows SDK.

*pActiveObject*<br/>
Zobacz *d pActiveObject* w `IDocHostUIHandler::ShowUI` w zestawie Windows SDK.

*pCommandTarget*<br/>
Zobacz *pCommandTarget* w `IDocHostUIHandler::ShowUI` w zestawie Windows SDK.

*pFrame*<br/>
Zobacz *pFrame* w `IDocHostUIHandler::ShowUI` w zestawie Windows SDK.

*pDoc*<br/>
Zobacz *pDoc* w `IDocHostUIHandler::ShowUI` w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją firmy CDHtmlDialog [IDocHostUIHandler::ShowUI](https://msdn.microsoft.com/library/aa753265.aspx), zgodnie z opisem w zestawie Windows SDK.

##  <a name="translateaccelerator"></a>  CDHtmlDialog::TranslateAccelerator

Wywoływane w celu przetwarzania komunikatów klawisza skrótu menu.

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>Parametry

*lpMsg*<br/>
Zobacz *lpMsg* w [IDocHostUIHandler::TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx) w zestawie Windows SDK.

*pguidCmdGroup*<br/>
Zobacz *pguidCmdGroup* w `IDocHostUIHandler::TranslateAccelerator` w zestawie Windows SDK.

*nCmdID*<br/>
Zobacz *nCmdID* w `IDocHostUIHandler::TranslateAccelerator` w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją firmy CDHtmlDialog [IDocHostUIHandler::TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx), zgodnie z opisem w zestawie Windows SDK.

##  <a name="translateurl"></a>  CDHtmlDialog::TranslateUrl

Wywołuje się, aby zmodyfikować adres URL do załadowania.

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>Parametry

*dwTranslate*<br/>
Zobacz *dwTranslate* w [IDocHostUIHandler::TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx) w zestawie Windows SDK.

*pchURLIn*<br/>
Zobacz *pchURLIn* w `IDocHostUIHandler::TranslateUrl` w zestawie Windows SDK.

*ppchURLOut*<br/>
Zobacz *ppchURLOut* w `IDocHostUIHandler::TranslateUrl` w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją firmy CDHtmlDialog [IDocHostUIHandler::TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx), zgodnie z opisem w zestawie Windows SDK.

##  <a name="updateui"></a>  CDHtmlDialog::UpdateUI

Wywołuje się, by powiadomić hosta, którego stan polecenia został zmieniony.

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją firmy CDHtmlDialog [IDocHostUIHandler::UpdateUI](https://msdn.microsoft.com/library/aa753268.aspx), zgodnie z opisem w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[DHtmlExplore próbki MFC](../../visual-cpp-samples.md)<br/>
[Makra pomocnika DDX_DHtml](#ddx_dhtml_helper_macros)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)

