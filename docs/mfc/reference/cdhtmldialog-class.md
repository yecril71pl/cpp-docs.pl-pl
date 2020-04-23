---
title: Klasa CDHtmlDialog
ms.date: 03/27/2019
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
ms.openlocfilehash: e2e4306320c52b8276d915848dfa6e460982c92b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753375"
---
# <a name="cdhtmldialog-class"></a>Klasa CDHtmlDialog

Służy do tworzenia okien dialogowych, które używają zasobów HTML zamiast okna dialogowego do zaimplementowania ich interfejsu użytkownika.

## <a name="syntax"></a>Składnia

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDHtmlDialog::CDHtmlDialog](#cdhtmldialog)|Konstruuje obiekt CDHtmlDialog.|
|[CDHtmlDialog::~CDHtmlDialog](#_dtorcdhtmldialog)|Niszczy obiekt CDHtmlDialog.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDHtmlDialog::CanAccessExternal](#canaccessexternal)|Możliwe do zastąpienia, który jest wywoływany jako sprawdzanie dostępu, aby zobaczyć, czy obiekty skryptów na załadowanej stronie mogą uzyskać dostęp do zewnętrznej wysyłki witryny kontrolnej. Sprawdza, czy wysyłka jest bezpieczna dla skryptów lub bieżąca strefa pozwala na obiekty, które nie są bezpieczne dla skryptów.|
|[CDHtmlDialog::CreateControlSite](#createcontrolsite)|Możliwe do zastąpienia używane do tworzenia wystąpienia witryny formantu do obsługi formantu WebBrowser w oknie dialogowym.|
|[CDHtmlDialog::DDX_DHtml_AxControl](#ddx_dhtml_axcontrol)|Wymienia dane między zmienną elementu członkowskiego i wartość właściwości formantu ActiveX na stronie HTML.|
|[CDHtmlDialog::DDX_DHtml_CheckBox](#ddx_dhtml_checkbox)|Wymiana danych między zmienną członkowną a polem wyboru na stronie HTML.|
|[CDHtmlDialog::DDX_DHtml_ElementText](#ddx_dhtml_elementtext)|Wymiana danych między zmienną elementu członkowskiego a dowolną właściwością elementu HTML na stronie HTML.|
|[CDHtmlDialog::DDX_DHtml_Radio](#ddx_dhtml_radio)|Wymiana danych między zmienną członkowną a przyciskiem opcji na stronie HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|Pobiera lub ustawia indeks pola listy na stronie HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectString](#ddx_dhtml_selectstring)|Pobiera lub ustawia tekst wyświetlany wpisu pola listy (na podstawie bieżącego indeksu) na stronie HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|Pobiera lub ustawia wartość wpisu pola listy (na podstawie bieżącego indeksu) na stronie HTML.|
|[CDHtmlDialog::DestroyModeless](#destroymodeless)|Niszczy niemodowe okno dialogowe.|
|[CDHtmlDialog::EnableModeless](#enablemodeless)|Włącza niemodowe okna dialogowe.|
|[CDHtmlDialog::FilterDataObject](#filterdataobject)|Umożliwia okno dialogowe filtrowania obiektów danych schowka utworzonych przez hostującą przeglądarkę.|
|[CDHtmlDialog::GetControlDispatch](#getcontroldispatch)|Pobiera interfejs `IDispatch` na formancie ActiveX osadzonym w dokumencie HTML.|
|[CDHtmlDialog::GetControlProperty](#getcontrolproperty)|Pobiera żądaną właściwość określonego formantu ActiveX.|
|[CDHtmlDialog::GetCurrentUrl](#getcurrenturl)|Pobiera jednolity lokalizator zasobów (URL) skojarzony z bieżącym dokumentem.|
|[CDHtmlDialog::GetDHtmlDocument](#getdhtmldocument)|Pobiera interfejs IHTMLDocument2 w aktualnie załadowanym dokumencie HTML.|
|[CDHtmlDialog::GetDropTarget](#getdroptarget)|Wywoływana przez formant zawierający przeglądarkę Web, gdy jest używana jako miejsce docelowe upuszczania, aby umożliwić okno dialogowe dostarczenie alternatywnego [programu IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).|
|[CDHtmlDialog::GetElement](#getelement)|Pobiera interfejs na element HTML.|
|[CDHtmlDialog::GetElementHtml](#getelementhtml)|Pobiera `innerHTML` właściwość elementu HTML.|
|[CDHtmlDialog::GetElementInterface](#getelementinterface)|Pobiera żądany wskaźnik interfejsu z elementu HTML.|
|[CDHtmlDialog::GetElementWłaściwość](#getelementproperty)|Pobiera wartość właściwości elementu HTML.|
|[CDHtmlDialog::GetElementText](#getelementtext)|Pobiera `innerText` właściwość elementu HTML.|
|[CDHtmlDialog::GetEvent](#getevent)|Pobiera `IHTMLEventObj` wskaźnik do bieżącego obiektu zdarzenia.|
|[CDHtmlDialog::GetExternal](#getexternal)|Pobiera interfejs hosta. `IDispatch`|
|[CDHtmlDialog::GetHostInfo](#gethostinfo)|Pobiera możliwości interfejsu użytkownika hosta.|
|[CDHtmlDialog::GetOptionKeyPath](#getoptionkeypath)|Pobiera klucz rejestru, w którym są przechowywane preferencje użytkownika.|
|[CDHtmlDialog::HideUI](#hideui)|Ukrywa interfejs użytkownika hosta.|
|[CDHtmlDialog::IsExternalDispatchSafe](#isexternaldispatchsafe)|Wskazuje, czy interfejs `IDispatch` hosta jest bezpieczny dla skryptów.|
|[CDHtmlDialog::LoadFromResource](#loadfromresource)|Ładuje określony zasób do formantu WebBrowser.|
|[CDHtmlDialog::Nawigacja](#navigate)|Przechodzi do określonego adresu URL.|
|[CDHtmlDialog::OnBeforeNavigate](#onbeforenavigate)|Wywoływane przez strukturę przed wywołane zdarzenie nawigacji jest uruchamiany.|
|[CDHtmlDialog::OnDocumentComplete](#ondocumentcomplete)|Wywoływane przez ramy do powiadamiania aplikacji, gdy dokument osiągnie stan READYSTATE_COMPLETE.|
|[CDHtmlDialog::OnDocWindowActivate](#ondocwindowactivate)|Wywoływane przez strukturę, gdy okno dokumentu jest aktywowany lub dezaktywowany.|
|[CDHtmlDialog::OnFrameWindowActivate](#onframewindowactivate)|Wywoływana przez strukturę, gdy okno ramki jest aktywowana lub dezaktywowana.|
|[CDHtmlDialog::OnInitDialog](#oninitdialog)|Wywoływana w odpowiedzi na komunikat WM_INITDIALOG.|
|[CDHtmlDialog::OnNavigateComplete](#onnavigatecomplete)|Wywoływane przez strukturę po zakończeniu zdarzenia nawigacji.|
|[CDHtmlDialog::ResizeBorder](#resizeborder)|Alerty obiektu, który musi zmienić jego rozmiar obszaru obramowania.|
|[CDHtmlDialog::SetControlProperty](#setcontrolproperty)|Ustawia właściwość formantu ActiveX na nową wartość.|
|[CDHtmlDialog::SetElementHtml](#setelementhtml)|Ustawia `innerHTML` właściwość elementu HTML.|
|[CDHtmlDialog::SetElementProperty](#setelementproperty)|Ustawia właściwość elementu HTML.|
|[CDHtmlDialog::SetElementText](#setelementtext)|Ustawia `innerText` właściwość elementu HTML.|
|[CDHtmlDialog::SetExternalDispatch](#setexternaldispatch)|Ustawia interfejs hosta. `IDispatch`|
|[CDHtmlDialog::SetHostFlags](#sethostflags)|Ustawia flagi interfejsu użytkownika hosta.|
|[CDHtmlDialog::ShowContextMenu](#showcontextmenu)|Wywoływane, gdy menu kontekstowe ma być wyświetlane.|
|[CDHtmlDialog::ShowUI](#showui)|Pokazuje interfejs użytkownika hosta.|
|[CDHtmlDialog::TranslateAccelerator](#translateaccelerator)|Wywoływana do przetwarzania komunikatów akceleratora menu-klucz.|
|[CDHtmlDialog::TranslateUrl](#translateurl)|Wywołany, aby zmodyfikować adres URL do załadowania.|
|[CDHtmlDialog::UpdateUI](#updateui)|Wywołany, aby powiadomić hosta, że stan polecenia uległ zmianie.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDHtmlDialog::m_bUseHtmlTitle](#m_busehtmltitle)|Wskazuje, czy jako podpis okna dialogowego ma być używany tytuł dokumentu HTML.|
|[CDHtmlDialog::m_nHtmlResID](#m_nhtmlresid)|Identyfikator zasobu HTML, który ma być wyświetlany.|
|[CDHtmlDialog::m_pBrowserApp](#m_pbrowserapp)|Wskaźnik do aplikacji przeglądarki sieci Web.|
|[CDHtmlDialog::m_spHtmlDoc](#m_sphtmldoc)|Wskaźnik do dokumentu HTML.|
|[CDHtmlDialog::m_strCurrentUrl](#m_strcurrenturl)|Bieżący adres URL.|
|[CDHtmlDialog::m_szHtmlResID](#m_szhtmlresid)|Wersja ciągu identyfikatora zasobu HTML.|

## <a name="remarks"></a>Uwagi

`CDHtmlDialog`można załadować kod HTML, który ma być wyświetlany z zasobu HTML lub adresu URL.

`CDHtmlDialog`można również do wymiany danych za pomocą formantów HTML i obsługiwać zdarzenia z formantów HTML, takich jak kliknięcia przycisku.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[Cwnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[Cdialog](../../mfc/reference/cdialog-class.md)

`CDHtmlDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdhtml.h

## <a name="ddx_dhtml-helper-macros"></a><a name="ddx_dhtml_helper_macros"></a>Makra pomocnika DDX_DHtml

Makra pomocnika DDX_DHtml umożliwiają łatwy dostęp do powszechnie używanych właściwości formantów na stronie HTML.

### <a name="data-exchange-macros"></a>Makra wymiany danych

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|Ustawia lub pobiera Value właściwości z wybranego formantu.|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|Ustawia lub pobiera tekst między znacznikami początkowymi i końcowymi bieżącego elementu.|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|Ustawia lub pobiera kod HTML między znacznikami początkowymi i końcowymi bieżącego elementu.|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|Ustawia lub pobiera docelowy adres URL lub punkt kontrolny.|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|Ustawia lub pobiera okno docelowe lub ramkę.|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|Ustawia lub pobiera nazwę obrazu lub klipu wideo w dokumencie.|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|Ustawia lub pobiera adres URL skojarzonej ramki.|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|Ustawia lub pobiera adres URL skojarzonej ramki.|

## <a name="cdhtmldialogcanaccessexternal"></a><a name="canaccessexternal"></a>CDHtmlDialog::CanAccessExternal

Możliwe do zastąpienia, który jest wywoływany jako sprawdzanie dostępu, aby zobaczyć, czy obiekty skryptów na załadowanej stronie mogą uzyskać dostęp do zewnętrznej wysyłki witryny kontrolnej. Sprawdza, czy wysyłka jest bezpieczna dla skryptów lub bieżąca strefa pozwala na obiekty, które nie są bezpieczne dla skryptów.

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

## <a name="cdhtmldialogcdhtmldialog"></a><a name="cdhtmldialog"></a>CDHtmlDialog::CDHtmlDialog

Konstruuje dynamiczne okno dialogowe HTML oparte na zasobach.

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
Ciąg zakończony z wartością null, który jest nazwą zasobu szablonu okna dialogowego.

*SzHtmlResID ( szhtmlResID )*<br/>
Ciąg zakończony z wartością null, który jest nazwą zasobu HTML.

*pParentWnd*<br/>
Wskaźnik do obiektu okna nadrzędnego lub właściciela (typu [CWnd),](../../mfc/reference/cwnd-class.md)do którego należy obiekt okna dialogowego. Jeśli jest null, okno nadrzędne obiektu okna dialogowego jest ustawiona na okno aplikacji głównej.

*nIDTemplate*<br/>
Zawiera numer identyfikatora zasobu szablonu okna dialogowego.

*nHtmlResID (nHtmlResID)*<br/>
Zawiera numer identyfikatora zasobu HTML.

### <a name="remarks"></a>Uwagi

Druga forma konstruktora zapewnia dostęp do zasobu okna dialogowego za pośrednictwem nazwy szablonu. Trzecia forma konstruktora zapewnia dostęp do zasobu okna dialogowego za pośrednictwem identyfikatora szablonu zasobu. Zazwyczaj identyfikator zaczyna się od prefiksu **IDD_.**

## <a name="cdhtmldialogcdhtmldialog"></a><a name="_dtorcdhtmldialog"></a>CDHtmlDialog::~CDHtmlDialog

Niszczy obiekt CDHtmlDialog.

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) musi służyć do niszczenia niemodowych okien dialogowych utworzonych przez [CDialog::Create](../../mfc/reference/cdialog-class.md#create).

## <a name="cdhtmldialogcreatecontrolsite"></a><a name="createcontrolsite"></a>CDHtmlDialog::CreateControlSite

Możliwe do zastąpienia używane do tworzenia wystąpienia witryny formantu do obsługi formantu WebBrowser w oknie dialogowym.

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>Parametry

*pKontener*<br/>
Wskaźnik do obiektu [COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)

*ppSite (polski)*<br/>
Wskaźnik do wskaźnika do [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można zastąpić tę funkcję elementu członkowskiego, aby zwrócić wystąpienie własnej klasy lokacji formantu.

## <a name="cdhtmldialogddx_dhtml_axcontrol"></a><a name="ddx_dhtml_axcontrol"></a>CDHtmlDialog::DDX_DHtml_AxControl

Wymienia dane między zmienną elementu członkowskiego i wartość właściwości formantu ActiveX na stronie HTML.

```cpp
void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    VARIANT& var);

void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    LPCTSTR szPropName,
    VARIANT& var);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId (szId)*<br/>
Wartość parametru Identyfikatora znacznika obiektu w źródle HTML dla formantu ActiveX.

*Dispid*<br/>
Identyfikator wysyłki właściwości, z którą chcesz wymieniać dane.

*szPropName (Nazwa)*<br/>
Nazwa właściwości.

*var*<br/>
Element członkowski danych, typu VARIANT, [COleVariant](../../mfc/reference/colevariant-class.md)lub [CComVariant](../../atl/reference/ccomvariant-class.md), który przechowuje wartość wymienianą z właściwością formantu ActiveX.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

## <a name="cdhtmldialogddx_dhtml_checkbox"></a><a name="ddx_dhtml_checkbox"></a>CDHtmlDialog::DDX_DHtml_CheckBox

Wymiana danych między zmienną członkowną a polem wyboru na stronie HTML.

```cpp
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId (szId)*<br/>
Wartość określona dla parametru identyfikatora formantu HTML.

*value*<br/>
Wartość wymieniana.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

## <a name="cdhtmldialogddx_dhtml_elementtext"></a><a name="ddx_dhtml_elementtext"></a>CDHtmlDialog::DDX_DHtml_ElementText

Wymiana danych między zmienną elementu członkowskiego a dowolną właściwością elementu HTML na stronie HTML.

```cpp
void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    CString& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    short& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    int& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    long& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    DWORD& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    float& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    double& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId (szId)*<br/>
Wartość określona dla parametru identyfikatora formantu HTML.

*Dispid*<br/>
Identyfikator wysyłki elementu HTML, za pomocą którego chcesz wymieniać dane.

*value*<br/>
Wartość wymieniana.

## <a name="cdhtmldialogddx_dhtml_radio"></a><a name="ddx_dhtml_radio"></a>CDHtmlDialog::DDX_DHtml_Radio

Wymiana danych między zmienną członkowną a przyciskiem opcji na stronie HTML.

```cpp
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId (szId)*<br/>
Wartość określona dla parametru identyfikatora formantu HTML.

*value*<br/>
Wartość wymieniana.

## <a name="cdhtmldialogddx_dhtml_selectindex"></a><a name="ddx_dhtml_selectindex"></a>CDHtmlDialog::DDX_DHtml_SelectIndex

Pobiera lub ustawia indeks pola listy na stronie HTML.

```cpp
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId (szId)*<br/>
Wartość określona dla `id` parametru formantu HTML.

*value*<br/>
Wartość wymieniana.

## <a name="cdhtmldialogddx_dhtml_selectstring"></a><a name="ddx_dhtml_selectstring"></a>CDHtmlDialog::DDX_DHtml_SelectString

Pobiera lub ustawia tekst wyświetlany wpisu pola listy (na podstawie bieżącego indeksu) na stronie HTML.

```cpp
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId (szId)*<br/>
Wartość określona dla parametru identyfikatora formantu HTML.

*value*<br/>
Wartość wymieniana.

## <a name="cdhtmldialogddx_dhtml_selectvalue"></a><a name="ddx_dhtml_selectvalue"></a>CDHtmlDialog::DDX_DHtml_SelectValue

Pobiera lub ustawia wartość wpisu pola listy (na podstawie bieżącego indeksu) na stronie HTML.

```cpp
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId (szId)*<br/>
Wartość określona dla parametru identyfikatora formantu HTML.

*value*<br/>
Wartość wymieniana.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

## <a name="cdhtmldialogdestroymodeless"></a><a name="destroymodeless"></a>CDHtmlDialog::DestroyModeless

Odłącza niemodytowe `CDHtmlDialog` okno dialogowe od obiektu i niszczy obiekt.

```cpp
void DestroyModeless();
```

## <a name="cdhtmldialogenablemodeless"></a><a name="enablemodeless"></a>CDHtmlDialog::EnableModeless

Włącza niemodowe okna dialogowe.

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>Parametry

*fJąlem*<br/>
Zobacz *fEnable* w [IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest implementacja CDHtmlDialog [IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)), zgodnie z opisem w windows SDK.

## <a name="cdhtmldialogfilterdataobject"></a><a name="filterdataobject"></a>CDHtmlDialog::FilterDataObject

Umożliwia okno dialogowe filtrowania obiektów danych schowka utworzonych przez hostującą przeglądarkę.

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>Parametry

*Pdo*<br/>
Zobacz *chNP* w [IDocHostUIHandler::FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)) w windows SDK.

*ppDORet (polski)*<br/>
Zobacz *ppDORet* w `IDocHostUIHandler::FilterDataObject` sdk systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest implementacja CDHtmlDialog [IDocHostUIHandler::FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)), zgodnie z opisem w windows SDK.

## <a name="cdhtmldialoggetcontroldispatch"></a><a name="getcontroldispatch"></a>CDHtmlDialog::GetControlDispatch

Pobiera `IDispatch` interfejs na formancie ActiveX osadzonym w dokumencie HTML zwróconym przez [GetDHtmlDocument](#getdhtmldocument).

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>Parametry

*szId (szId)*<br/>
Identyfikator HTML formantu ActiveX.

*ppdisp (polski)*<br/>
Interfejs `IDispatch` formantu, jeśli zostanie znaleziony na stronie sieci Web.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="cdhtmldialoggetcontrolproperty"></a><a name="getcontrolproperty"></a>CDHtmlDialog::GetControlProperty

Pobiera żądaną właściwość określonego formantu ActiveX.

```
VARIANT GetControlProperty(
    LPCTSTR szId,
    LPCTSTR szPropName);

VARIANT GetControlProperty(
    LPCTSTR szId,
    DISPID dispId);

VARIANT GetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId);
```

### <a name="parameters"></a>Parametry

*szId (szId)*<br/>
Identyfikator HTML formantu ActiveX.

*szPropName (Nazwa)*<br/>
Nazwa właściwości w domyślnych ustawieniach regionalnych bieżącego użytkownika.

*pdispKontroluj*<br/>
Wskaźnik `IDispatch` formantu ActiveX.

*Dispid*<br/>
Identyfikator wysyłki właściwości.

### <a name="return-value"></a>Wartość zwracana

Wariant zawierający żądaną właściwość lub pusty wariant, jeśli nie można odnaleźć formantu lub właściwości.

### <a name="remarks"></a>Uwagi

Przeciążenia są wymienione od najmniej wydajnych u góry do najbardziej wydajnych na dole.

## <a name="cdhtmldialoggetcurrenturl"></a><a name="getcurrenturl"></a>CDHtmlDialog::GetCurrentUrl

Pobiera jednolity lokalizator zasobów (URL) skojarzony z bieżącym dokumentem.

```cpp
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>Parametry

*szurl (szurl)*<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający adres URL do pobrania.

## <a name="cdhtmldialoggetdhtmldocument"></a><a name="getdhtmldocument"></a>CDHtmlDialog::GetDHtmlDocument

Pobiera interfejs [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) w aktualnie załadowanym dokumencie HTML.

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>Parametry

* \* \** Wskaźnik do wskaźnika do dokumentu HTML.

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT. Zwraca S_OK, jeśli zakończy się pomyślnie.

## <a name="cdhtmldialoggetdroptarget"></a><a name="getdroptarget"></a>CDHtmlDialog::GetDropTarget

Wywoływana przez formant zawierający przeglądarkę Web, gdy jest używana jako miejsce docelowe upuszczania, aby umożliwić okno dialogowe dostarczenie alternatywnego [programu IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>Parametry

*PDropTarget*<br/>
Zobacz *pDropTarget* w [IDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)) w windows SDK.

*ppDropTarget (polski)*<br/>
Zobacz *ppDropTarget* w `IDocHostUIHandler::GetDropTarget` windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest implementacja CDHtmlDialog [IDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)), zgodnie z opisem w windows SDK.

## <a name="cdhtmldialoggetelement"></a><a name="getelement"></a>CDHtmlDialog::GetElement

Zwraca interfejs na elemencie HTML określonym przez *identyfikator szElementId*.

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

*ppdisp (polski)*<br/>
Wskaźnik `IDispatch` do żądanego elementu lub kolekcji elementów.

*pbCollection (Plasukcja pb)*<br/>
Bool wskazujący, czy obiekt reprezentowany przez *ppdisp* jest pojedynczym elementem, czy kolekcją elementów.

*pphtmlElement (Polski)*<br/>
Wskaźnik `IHTMLElement` do żądanego elementu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Użyj pierwszego przeciążenia, jeśli trzeba obsługiwać warunki, w których może być więcej niż jeden element o określonym identyfikatorze. Można użyć ostatniego parametru, aby dowiedzieć się, czy zwracany wskaźnik interfejsu jest do kolekcji lub pojedynczego elementu. Jeśli wskaźnik interfejsu znajduje się w kolekcji, można zbadać `IHTMLElementCollection` i używać jego `item` właściwości, aby odwołać się do elementów według położenia porządkowego.

Drugie przeciążenie zakończy się niepowodzeniem, jeśli istnieje więcej niż jeden element o tym samym identyfikatorze na stronie.

## <a name="cdhtmldialoggetelementhtml"></a><a name="getelementhtml"></a>CDHtmlDialog::GetElementHtml

Pobiera `innerHTML` właściwość elementu HTML identyfikowanego przez *identyfikator szElementId*.

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

### <a name="return-value"></a>Wartość zwracana

Właściwość `innerHTML` elementu HTML identyfikowana przez *identyfikator szElementId* lub NULL, jeśli nie można odnaleźć elementu.

## <a name="cdhtmldialoggetelementinterface"></a><a name="getelementinterface"></a>CDHtmlDialog::GetElementInterface

Pobiera żądany wskaźnik interfejsu z elementu HTML identyfikowany przez *identyfikator szElementId*.

```
template <class Q> HRESULT GetElementInterface(
    LPCTSTR szElementId,
    Q** ppvObj);

HRESULT GetElementInterface(
    LPCTSTR szElementId,
    REFIID refiid,
    void** ppvObj);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

*ppvObj (polski)*<br/>
Adres wskaźnika, który zostanie wypełniony żądanym wskaźnikiem interfejsu, jeśli element zostanie znaleziony i kwerenda zakończy się pomyślnie.

*refiid*<br/>
Identyfikator interfejsu (IID) żądanego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

## <a name="cdhtmldialoggetelementproperty"></a><a name="getelementproperty"></a>CDHtmlDialog::GetElementWłaściwość

Pobiera wartość właściwości identyfikowanej przez *dispId* z elementu HTML identyfikowanego przez *identyfikator szElementId*.

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

*Dispid*<br/>
Identyfikator wysyłki właściwości.

### <a name="return-value"></a>Wartość zwracana

Wartość właściwości lub pusty wariant, jeśli nie można odnaleźć właściwości lub elementu.

## <a name="cdhtmldialoggetelementtext"></a><a name="getelementtext"></a>CDHtmlDialog::GetElementText

Pobiera `innerText` właściwość elementu HTML identyfikowanego przez *identyfikator szElementId*.

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

### <a name="return-value"></a>Wartość zwracana

Właściwość `innerText` elementu HTML identyfikowana przez *identyfikator szElementId* lub NULL, jeśli nie można odnaleźć właściwości lub elementu.

## <a name="cdhtmldialoggetevent"></a><a name="getevent"></a>CDHtmlDialog::GetEvent

Zwraca `IHTMLEventObj` wskaźnik do bieżącego obiektu zdarzenia.

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>Parametry

*ppEventObj*<br/>
Adres wskaźnika, który zostanie `IHTMLEventObj` wypełniony wskaźnikiem interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana tylko z poziomu programu obsługi zdarzeń DHTML.

## <a name="cdhtmldialoggetexternal"></a><a name="getexternal"></a>CDHtmlDialog::GetExternal

Pobiera interfejs hosta. `IDispatch`

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>Parametry

*ppDispatch (Nierozróżnianie)*<br/>
Zobacz *ppDispatch* w [IDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub E_NOTIMPL na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest implementacja CDHtmlDialog [IDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)), zgodnie z opisem w windows SDK.

## <a name="cdhtmldialoggethostinfo"></a><a name="gethostinfo"></a>CDHtmlDialog::GetHostInfo

Pobiera możliwości interfejsu użytkownika hosta.

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>Parametry

*Pinfo*<br/>
Zobacz *pInfo* w [IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest implementacja CDHtmlDialog [IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)), zgodnie z opisem w windows SDK.

## <a name="cdhtmldialoggetoptionkeypath"></a><a name="getoptionkeypath"></a>CDHtmlDialog::GetOptionKeyPath

Pobiera klucz rejestru, w którym są przechowywane preferencje użytkownika.

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>Parametry

*pchKey (klucz pchKey)*<br/>
Zobacz *pchKey* w [IDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)) w windows SDK.

*Dw*<br/>
Zobacz *dw* dw `IDocHostUIHandler::GetOptionKeyPath` w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest implementacja CDHtmlDialog [IDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)), zgodnie z opisem w windows SDK.

## <a name="cdhtmldialoghideui"></a><a name="hideui"></a>CDHtmlDialog::HideUI

Ukrywa interfejs użytkownika hosta.

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest implementacja CDHtmlDialog [IDocHostUIHandler::HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\)), zgodnie z opisem w windows SDK.

## <a name="cdhtmldialogisexternaldispatchsafe"></a><a name="isexternaldispatchsafe"></a>CDHtmlDialog::IsExternalDispatchSafe

Wskazuje, czy interfejs `IDispatch` hosta jest bezpieczny dla skryptów.

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość FAŁSZ.

## <a name="cdhtmldialogloadfromresource"></a><a name="loadfromresource"></a>CDHtmlDialog::LoadFromResource

Ładuje określony zasób do formantu WebBrowser w oknie dialogowym DHTML.

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>Parametry

*lpszResource*<br/>
Wskaźnik do ciągu zawierającego nazwę zasobu do załadowania.

*nRes (właso)*<br/>
Identyfikator zasobu do załadowania.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE.

## <a name="cdhtmldialogm_busehtmltitle"></a><a name="m_busehtmltitle"></a>CDHtmlDialog::m_bUseHtmlTitle

Wskazuje, czy jako podpis okna dialogowego ma być używany tytuł dokumentu HTML.

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>Uwagi

Jeśli **m**_ **bUseHtmlTitle** ma wartość TRUE, podpis okna dialogowego jest ustawiony na tytuł dokumentu HTML; w przeciwnym razie zostanie użyty podpis w zasobie okna dialogowego.

## <a name="cdhtmldialogm_nhtmlresid"></a><a name="m_nhtmlresid"></a>CDHtmlDialog::m_nHtmlResID

Identyfikator zasobu HTML, który ma być wyświetlany.

```
UINT m_nHtmlResID;
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

## <a name="cdhtmldialogm_pbrowserapp"></a><a name="m_pbrowserapp"></a>CDHtmlDialog::m_pBrowserApp

Wskaźnik do aplikacji przeglądarki sieci Web.

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

## <a name="cdhtmldialogm_sphtmldoc"></a><a name="m_sphtmldoc"></a>CDHtmlDialog::m_spHtmlDoc

Wskaźnik do dokumentu HTML.

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

## <a name="cdhtmldialogm_strcurrenturl"></a><a name="m_strcurrenturl"></a>CDHtmlDialog::m_strCurrentUrl

Bieżący adres URL.

```
CString m_strCurrentUrl;
```

## <a name="cdhtmldialogm_szhtmlresid"></a><a name="m_szhtmlresid"></a>CDHtmlDialog::m_szHtmlResID

Wersja ciągu identyfikatora zasobu HTML.

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

## <a name="cdhtmldialognavigate"></a><a name="navigate"></a>CDHtmlDialog::Nawigacja

Przechodzi do zasobu identyfikowane przez adres URL, który jest określony przez *lpszURL*.

```cpp
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
Wskaźnik do ciągu zawierającego adres URL, który ma być kierowany.

*Dwflags*<br/>
Flagi zmiennej, która określa, czy dodać zasób do listy historii, czy czytać do pamięci podręcznej lub zapisywać z pamięci podręcznej i czy wyświetlić zasób w nowym oknie. Zmienna może być kombinacją wartości zdefiniowanych przez [wyliczenie BrowserNavConstants.](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\))

*lpszTargetFrameName*<br/>
Wskaźnik do ciągu, który zawiera nazwę ramki, w którym ma być wyświetlany zasób.

*lpszHeaders (lpszHeaders)*<br/>
Wskaźnik do wartości określającej nagłówki HTTP do wysłania do serwera. Nagłówki te są dodawane do domyślnych nagłówków programu Internet Explorer. Nagłówki można określić takie informacje, jak akcja wymagana przez serwer, typ danych przekazywanych do serwera lub kod stanu. Ten parametr jest ignorowany, jeśli adres URL nie jest adresem URL HTTP.

*lpvPostData*<br/>
Wskaźnik do danych do wysłania za pomocą transakcji HTTP POST. Na przykład transakcja POST służy do wysyłania danych zebranych przez formularz HTML. Jeśli ten parametr nie określa `Navigate` żadnych danych księgowania, wystawia transakcję HTTP GET. Ten parametr jest ignorowany, jeśli adres URL nie jest adresem URL HTTP.

*dwPostDataLen*<br/>
Dane do wysłania za pomocą transakcji HTTP POST. Na przykład transakcja POST służy do wysyłania danych zebranych przez formularz HTML. Jeśli ten parametr nie określa `Navigate` żadnych danych księgowania, wystawia transakcję HTTP GET. Ten parametr jest ignorowany, jeśli adres URL nie jest adresem URL HTTP.

## <a name="cdhtmldialogonbeforenavigate"></a><a name="onbeforenavigate"></a>CDHtmlDialog::OnBeforeNavigate

Wywoływane przez strukturę spowodować zdarzenie do ognia przed wystąpieniem nawigacji.

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp (Niem.*<br/>
Wskaźnik do `IDispatch` obiektu.

*szurl (szurl)*<br/>
Wskaźnik do ciągu zawierającego adres URL, do który chcesz przejść.

## <a name="cdhtmldialogondocumentcomplete"></a><a name="ondocumentcomplete"></a>CDHtmlDialog::OnDocumentComplete

Wywoływane przez ramy do powiadamiania aplikacji, gdy dokument osiągnął stan READYSTATE_COMPLETE.

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp (Niem.*<br/>
Wskaźnik do `IDispatch` obiektu.

*szurl (szurl)*<br/>
Wskaźnik do ciągu zawierającego adres URL, do który nawigowano.

## <a name="cdhtmldialogondocwindowactivate"></a><a name="ondocwindowactivate"></a>CDHtmlDialog::OnDocWindowActivate

Wywoływane przez strukturę, gdy okno dokumentu jest aktywowany lub dezaktywowany.

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parametry

*fAktywnie*<br/>
Zobacz *fActivate* w [IDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest implementacja CDHtmlDialog [IDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)), zgodnie z opisem w windows SDK.

## <a name="cdhtmldialogonframewindowactivate"></a><a name="onframewindowactivate"></a>CDHtmlDialog::OnFrameWindowActivate

Wywoływana przez strukturę, gdy okno ramki jest aktywowana lub dezaktywowana.

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parametry

*fAktywnie*<br/>
Zobacz *fActivate* w [IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest implementacja CDHtmlDialog [IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)), zgodnie z opisem w windows SDK.

## <a name="cdhtmldialogoninitdialog"></a><a name="oninitdialog"></a>CDHtmlDialog::OnInitDialog

Wywoływana w odpowiedzi na komunikat WM_INITDIALOG.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Ten komunikat jest wysyłany do `Create` `CreateIndirect`okna `DoModal` dialogowego podczas programu , lub połączeń, które występują bezpośrednio przed wyświetleniem okna dialogowego.

Zastąpość tę funkcję elementu członkowskiego, jeśli konieczne jest wykonanie specjalnego przetwarzania podczas inicjowania okna dialogowego. W wersji zastąpione najpierw wywołać `OnInitDialog` klasę podstawową, ale pominąć jego wartość zwracaną. Zwykle zwracasz wartość TRUE z funkcji nadrzędnego elementu członkowskiego.

System Windows `OnInitDialog` wywołuje tę funkcję za pomocą standardowej globalnej procedury okna dialogowego wspólnej dla wszystkich okien dialogowych biblioteki klas programu Microsoft Foundation, a nie za pośrednictwem mapy wiadomości, więc nie jest potrzebny wpis mapy wiadomości dla tej funkcji członkowskiej.

## <a name="cdhtmldialogonnavigatecomplete"></a><a name="onnavigatecomplete"></a>CDHtmlDialog::OnNavigateComplete

Wywoływana przez platformę po zakończeniu nawigacji do określonego adresu URL.

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp (Niem.*<br/>
Wskaźnik do `IDispatch` obiektu.

*szurl (szurl)*<br/>
Wskaźnik do ciągu zawierającego adres URL, do który nawigowano.

## <a name="cdhtmldialogresizeborder"></a><a name="resizeborder"></a>CDHtmlDialog::ResizeBorder

Alerty obiektu, który musi zmienić jego rozmiar obszaru obramowania.

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>Parametry

*prcBorder*<br/>
Zobacz *prcBorder* w [IDocHostUIHandler::ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\)) w windows SDK.

*pUIWindow*<br/>
Zobacz *pUIWindow* w `IDocHostUIHandler::ResizeBorder` windows SDK.

*fFrameWindow*<br/>
Zobacz *fFrameWindow* w `IDocHostUIHandler::ResizeBorder` windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

## <a name="cdhtmldialogsetcontrolproperty"></a><a name="setcontrolproperty"></a>CDHtmlDialog::SetControlProperty

Ustawia właściwość formantu ActiveX na nową wartość.

```cpp
void SetControlProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    LPCTSTR szElementId,
    LPCTSTR szPropName,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator HTML formantu ActiveX.

*Dispid*<br/>
Identyfikator wysyłki właściwości do ustawionego.

*pWart*<br/>
Wskaźnik do VARIANT zawierający nową wartość właściwości.

*pdispKontroluj*<br/>
Wskaźnik do `IDispatch` interfejsu formantu ActiveX.

*szPropName (Nazwa)*<br/>
Ciąg zawierający nazwę właściwości do ustawionego.

## <a name="cdhtmldialogsetelementhtml"></a><a name="setelementhtml"></a>CDHtmlDialog::SetElementHtml

Ustawia `innerHTML` właściwość elementu HTML.

```cpp
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

*tekst bstrText*<br/>
Nowa wartość `innerHTML` właściwości.

*punkElem (polski)*<br/>
Wskaźnik `IUnknown` elementu HTML.

## <a name="cdhtmldialogsetelementproperty"></a><a name="setelementproperty"></a>CDHtmlDialog::SetElementProperty

Ustawia właściwość elementu HTML.

```cpp
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

*Dispid*<br/>
Identyfikator wysyłki właściwości do ustawionego.

*pWart*<br/>
Nowa wartość właściwości.

## <a name="cdhtmldialogsetelementtext"></a><a name="setelementtext"></a>CDHtmlDialog::SetElementText

Ustawia `innerText` właściwość elementu HTML.

```cpp
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

*tekst bstrText*<br/>
Nowa wartość `innerText` właściwości.

*punkElem (polski)*<br/>
Wskaźnik `IUnknown` elementu HTML.

## <a name="cdhtmldialogsetexternaldispatch"></a><a name="setexternaldispatch"></a>CDHtmlDialog::SetExternalDispatch

Ustawia interfejs hosta. `IDispatch`

```cpp
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>Parametry

*pdispNieszciowy*<br/>
Nowy `IDispatch` interfejs.

## <a name="cdhtmldialogsethostflags"></a><a name="sethostflags"></a>CDHtmlDialog::SetHostFlags

Ustawia flagi interfejsu użytkownika hosta.

```cpp
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*Dwflags*<br/>
Aby uzyskać możliwe wartości, zobacz [DOCHOSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) w windows SDK.

## <a name="cdhtmldialogshowcontextmenu"></a><a name="showcontextmenu"></a>CDHtmlDialog::ShowContextMenu

Wywoływane, gdy menu kontekstowe ma być wyświetlane.

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>Parametry

*dwID (dwID)*<br/>
Zobacz *dwID* w [IDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)) w windows SDK.

*Ppt*<br/>
Zobacz *ppt* w `IDocHostUIHandler::ShowContextMenu` windows SDK.

*pcmdtReserved*<br/>
Zobacz *pcmdtReserved* w `IDocHostUIHandler::ShowContextMenu` windows SDK.

*pdispReserved*<br/>
Zobacz *pdispReserved* w `IDocHostUIHandler::ShowContextMenu` windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest implementacja CDHtmlDialog [IDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)), zgodnie z opisem w windows SDK.

## <a name="cdhtmldialogshowui"></a><a name="showui"></a>CDHtmlDialog::ShowUI

Pokazuje interfejs użytkownika hosta.

```
STDMETHOD(ShowUI)(
    DWORD dwID,
    IOleInPlaceActiveObject* pActiveObject,
    IOleCommandTarget* pCommandTarget,
    IOleInPlaceFrame* pFrame,
    IOleInPlaceUIWindow* pDoc);
```

### <a name="parameters"></a>Parametry

*dwID (dwID)*<br/>
Zobacz *dwID* w [IDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)) w windows SDK.

*pAktywnyobek*<br/>
Zobacz *d pActiveObject* w `IDocHostUIHandler::ShowUI` windows SDK.

*pCommandTarget*<br/>
Zobacz *pCommandTarget* w `IDocHostUIHandler::ShowUI` windows SDK.

*pFrame (klatka)*<br/>
Zobacz *pFrame* w `IDocHostUIHandler::ShowUI` windows SDK.

*pDoc*<br/>
Zobacz *pDoc* w `IDocHostUIHandler::ShowUI` windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest implementacja CDHtmlDialog [IDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)), zgodnie z opisem w windows SDK.

## <a name="cdhtmldialogtranslateaccelerator"></a><a name="translateaccelerator"></a>CDHtmlDialog::TranslateAccelerator

Wywoływana do przetwarzania komunikatów akceleratora menu-klucz.

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>Parametry

*lpMsg*<br/>
Zobacz *lpMsg* w [IDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)) w windows SDK.

*pguidCmdGroup (Grupa pguidCmd)*<br/>
Zobacz *pguidCmdGroup* w `IDocHostUIHandler::TranslateAccelerator` windows SDK.

*nCmdID (identyfikator nCmdID)*<br/>
Zobacz *nCmdID* w `IDocHostUIHandler::TranslateAccelerator` windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest implementacja CDHtmlDialog [IDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)), zgodnie z opisem w windows SDK.

## <a name="cdhtmldialogtranslateurl"></a><a name="translateurl"></a>CDHtmlDialog::TranslateUrl

Wywołany, aby zmodyfikować adres URL do załadowania.

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>Parametry

*dwTranslate*<br/>
Zobacz *dwTranslate* w [IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)) w windows SDK.

*pchURLIn (pchURLIn)*<br/>
Zobacz *pchURLIn* w `IDocHostUIHandler::TranslateUrl` w windows SDK.

*ppchURLOut (Polski)*<br/>
Zobacz *ppchURLOut* w `IDocHostUIHandler::TranslateUrl` w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest implementacja CDHtmlDialog [IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)), zgodnie z opisem w windows SDK.

## <a name="cdhtmldialogupdateui"></a><a name="updateui"></a>CDHtmlDialog::UpdateUI

Wywołany, aby powiadomić hosta, że stan polecenia uległ zmianie.

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest implementacja CDHtmlDialog [IDocHostUIHandler::UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\)), zgodnie z opisem w windows SDK.

## <a name="see-also"></a>Zobacz też

[Próbka MFC DHtmlExplore](../../overview/visual-cpp-samples.md)<br/>
[Makra pomocnika DDX_DHtml](#ddx_dhtml_helper_macros)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
