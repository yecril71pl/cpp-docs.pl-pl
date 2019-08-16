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
ms.openlocfilehash: ec424e433dc84bf4188e349eb6450888aeeeb463
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506897"
---
# <a name="cdhtmldialog-class"></a>Klasa CDHtmlDialog

Służy do tworzenia okien dialogowych, które używają języka HTML, a nie zasobów okna dialogowego do implementowania interfejsu użytkownika.

## <a name="syntax"></a>Składnia

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDHtmlDialog:: CDHtmlDialog](#cdhtmldialog)|Konstruuje obiekt CDHtmlDialog.|
|[CDHtmlDialog::~CDHtmlDialog](#_dtorcdhtmldialog)|Niszczy obiekt CDHtmlDialog.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDHtmlDialog:: CanAccessExternal](#canaccessexternal)|Program, który jest wywoływany jako kontrola dostępu, aby sprawdzić, czy obiekty skryptów na załadowanej stronie mogą uzyskać dostęp do zewnętrznej wysyłki lokacji sterowania. Sprawdza, czy wysyłanie jest bezpieczne dla skryptów lub czy Bieżąca strefa zezwala na obiekty, które nie są bezpieczne do obsługi skryptów.|
|[CDHtmlDialog::CreateControlSite](#createcontrolsite)|Wartość zastąpienia użyta do utworzenia wystąpienia lokacji kontrolki do hostowania formantu WebBrowser w oknie dialogowym.|
|[CDHtmlDialog::D DX_DHtml_AxControl](#ddx_dhtml_axcontrol)|Wymienia dane między zmienną członkowską a wartością właściwości kontrolki ActiveX na stronie HTML.|
|[CDHtmlDialog::D DX_DHtml_CheckBox](#ddx_dhtml_checkbox)|Wymienia dane między zmienną członkowską i polem wyboru na stronie HTML.|
|[CDHtmlDialog::D DX_DHtml_ElementText](#ddx_dhtml_elementtext)|Wymienia dane między zmienną członkowską i dowolną właściwością elementu HTML na stronie HTML.|
|[CDHtmlDialog::D DX_DHtml_Radio](#ddx_dhtml_radio)|Wymienia dane między zmienną członkowską i przyciskiem radiowym na stronie HTML.|
|[CDHtmlDialog::D DX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|Pobiera lub ustawia indeks pola listy na stronie HTML.|
|[CDHtmlDialog::D DX_DHtml_SelectString](#ddx_dhtml_selectstring)|Pobiera lub ustawia tekst wyświetlany wpisu pola listy (na podstawie bieżącego indeksu) na stronie HTML.|
|[CDHtmlDialog::D DX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|Pobiera lub ustawia wartość wpisu pola listy (na podstawie bieżącego indeksu) na stronie HTML.|
|[CDHtmlDialog::DestroyModeless](#destroymodeless)|Niszczy niemodalne okno dialogowe.|
|[CDHtmlDialog::EnableModeless](#enablemodeless)|Włącza Niemodalne okna dialogowe.|
|[CDHtmlDialog::FilterDataObject](#filterdataobject)|Umożliwia okno dialogowe Filtrowanie obiektów danych schowka utworzonych przez hostowaną przeglądarkę.|
|[CDHtmlDialog::GetControlDispatch](#getcontroldispatch)|`IDispatch` Pobiera interfejs na kontrolce ActiveX osadzony w dokumencie HTML.|
|[CDHtmlDialog:: GetControlProperty](#getcontrolproperty)|Pobiera żądaną właściwość określonej kontrolki ActiveX.|
|[CDHtmlDialog:: GetCurrentUrl](#getcurrenturl)|Pobiera adres URL (Uniform Resource Locator) skojarzony z bieżącym dokumentem.|
|[CDHtmlDialog:: GetDHtmlDocument](#getdhtmldocument)|Pobiera interfejs IHTMLDocument2 na aktualnie załadowanym dokumencie HTML.|
|[CDHtmlDialog:: GetDropTarget](#getdroptarget)|Wywoływane przez zawartą kontrolkę WebBrowser, gdy jest ona używana jako element docelowy upuszczania, aby zezwolić na dostarczenie przez okno dialogowe alternatywnej [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).|
|[CDHtmlDialog:: GetElement](#getelement)|Pobiera interfejs dla elementu HTML.|
|[CDHtmlDialog:: GetElementHtml](#getelementhtml)|`innerHTML` Pobiera właściwość elementu HTML.|
|[CDHtmlDialog:: GetElementInterface](#getelementinterface)|Pobiera żądany wskaźnik interfejsu z elementu HTML.|
|[CDHtmlDialog:: GetElementProperty](#getelementproperty)|Pobiera wartość właściwości elementu HTML.|
|[CDHtmlDialog:: GetElementText](#getelementtext)|`innerText` Pobiera właściwość elementu HTML.|
|[CDHtmlDialog:: GetEvent](#getevent)|`IHTMLEventObj` Pobiera wskaźnik do bieżącego obiektu zdarzenia.|
|[CDHtmlDialog:: getexternal](#getexternal)|Pobiera `IDispatch` interfejs hosta.|
|[CDHtmlDialog:: GetHostInfo](#gethostinfo)|Pobiera funkcje interfejsu użytkownika hosta.|
|[CDHtmlDialog::GetOptionKeyPath](#getoptionkeypath)|Pobiera klucz rejestru, w którym są przechowywane preferencje użytkownika.|
|[CDHtmlDialog:: HideUI](#hideui)|Ukrywa interfejs użytkownika hosta.|
|[CDHtmlDialog::IsExternalDispatchSafe](#isexternaldispatchsafe)|Wskazuje, czy `IDispatch` interfejs hosta jest bezpieczny dla skryptów.|
|[CDHtmlDialog:: LoadFromResource](#loadfromresource)|Ładuje określony zasób do kontrolki WebBrowser.|
|[CDHtmlDialog:: Nawiguj](#navigate)|Przechodzi do podanego adresu URL.|
|[CDHtmlDialog:: OnBeforeNavigate](#onbeforenavigate)|Wywoływane przez platformę przed uruchomieniem zdarzenia nawigacji.|
|[CDHtmlDialog::OnDocumentComplete](#ondocumentcomplete)|Wywoływane przez platformę, by powiadomić aplikację, gdy dokument osiągnął stan READYSTATE_COMPLETE.|
|[CDHtmlDialog::OnDocWindowActivate](#ondocwindowactivate)|Wywoływane przez platformę, gdy okno dokumentu jest aktywowane lub dezaktywowane.|
|[CDHtmlDialog:: OnFrameWindowActivate](#onframewindowactivate)|Wywoływane przez platformę, gdy okno ramki jest aktywowane lub dezaktywowane.|
|[CDHtmlDialog::OnInitDialog](#oninitdialog)|Wywołuje się w odpowiedzi na komunikat WM_INITDIALOG.|
|[CDHtmlDialog::OnNavigateComplete](#onnavigatecomplete)|Wywoływane przez platformę po zakończeniu zdarzenia nawigacji.|
|[CDHtmlDialog:: ResizeBorder](#resizeborder)|Alarmuje obiekt, którego potrzeba do zmiany rozmiaru obszaru obramowania.|
|[CDHtmlDialog:: SetControlProperty](#setcontrolproperty)|Ustawia właściwość kontrolki ActiveX na nową wartość.|
|[CDHtmlDialog::SetElementHtml](#setelementhtml)|`innerHTML` Ustawia właściwość elementu HTML.|
|[CDHtmlDialog::SetElementProperty](#setelementproperty)|Ustawia właściwość elementu HTML.|
|[CDHtmlDialog::SetElementText](#setelementtext)|`innerText` Ustawia właściwość elementu HTML.|
|[CDHtmlDialog::SetExternalDispatch](#setexternaldispatch)|Ustawia `IDispatch` interfejs hosta.|
|[CDHtmlDialog::SetHostFlags](#sethostflags)|Ustawia flagi interfejsu użytkownika hosta.|
|[CDHtmlDialog:: ShowContextMenu](#showcontextmenu)|Wywoływana, gdy menu kontekstowe ma być wyświetlane.|
|[CDHtmlDialog:: ShowUI](#showui)|Pokazuje interfejs użytkownika hosta.|
|[CDHtmlDialog:: TranslateAccelerator](#translateaccelerator)|Wywołuje się, by przetworzyć komunikaty klawisza skrótu menu.|
|[CDHtmlDialog::TranslateUrl](#translateurl)|Wywołuje się, by zmodyfikować adres URL do załadowania.|
|[CDHtmlDialog:: UpdateUI](#updateui)|Wywołuje się, by powiadomić hosta o zmianie stanu polecenia.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDHtmlDialog::m_bUseHtmlTitle](#m_busehtmltitle)|Wskazuje, czy tytuł dokumentu HTML ma być używany jako podpis okna dialogowego.|
|[CDHtmlDialog::m_nHtmlResID](#m_nhtmlresid)|Identyfikator zasobu dla zasobu HTML do wyświetlenia.|
|[CDHtmlDialog::m_pBrowserApp](#m_pbrowserapp)|Wskaźnik do aplikacji przeglądarki sieci Web.|
|[CDHtmlDialog::m_spHtmlDoc](#m_sphtmldoc)|Wskaźnik do dokumentu HTML.|
|[CDHtmlDialog::m_strCurrentUrl](#m_strcurrenturl)|Bieżący adres URL.|
|[CDHtmlDialog::m_szHtmlResID](#m_szhtmlresid)|Wersja ciągu identyfikatora zasobu HTML.|

## <a name="remarks"></a>Uwagi

`CDHtmlDialog`program może załadować kod HTML, który ma być wyświetlany z zasobu HTML lub adresu URL.

`CDHtmlDialog`może również wykonywać wymianę danych z kontrolkami HTML i obsługiwać zdarzenia z kontrolek HTML, takich jak kliknięcia przycisku.

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

**Nagłówek:** afxdhtml. h

##  <a name="ddx_dhtml_helper_macros"></a>Makra pomocnika DDX_DHtml

Makra pomocnika DDX_DHtml umożliwiają łatwy dostęp do najczęściej używanych właściwości formantów na stronie HTML.

### <a name="data-exchange-macros"></a>Makra wymiany danych

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|Ustawia lub pobiera właściwość Value z wybranej kontrolki.|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|Ustawia lub pobiera tekst między tagami początkowymi i końcowymi bieżącego elementu.|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|Ustawia lub Pobiera kod HTML między tagami początkowymi i końcowymi bieżącego elementu.|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|Ustawia lub pobiera docelowy adres URL lub punkt zakotwiczenia.|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|Ustawia lub pobiera docelowe okno lub ramkę.|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|Ustawia lub pobiera nazwę obrazu lub klipu wideo w dokumencie.|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|Ustawia lub Pobiera adres URL skojarzonej ramki.|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|Ustawia lub Pobiera adres URL skojarzonej ramki.|

##  <a name="canaccessexternal"></a>CDHtmlDialog:: CanAccessExternal

Program, który jest wywoływany jako kontrola dostępu, aby sprawdzić, czy obiekty skryptów na załadowanej stronie mogą uzyskać dostęp do zewnętrznej wysyłki lokacji sterowania. Sprawdza, czy wysyłanie jest bezpieczne dla skryptów lub czy Bieżąca strefa zezwala na obiekty, które nie są bezpieczne do obsługi skryptów.

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

##  <a name="cdhtmldialog"></a>CDHtmlDialog:: CDHtmlDialog

Tworzy okno dialogowe dynamicznego HTML opartego na zasobach.

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
Ciąg zakończony znakiem null, który jest nazwą zasobu szablonu okna dialogowego.

*szHtmlResID*<br/>
Ciąg zakończony znakiem null, który jest nazwą zasobu HTML.

*pParentWnd*<br/>
Wskaźnik do obiektu nadrzędnego lub elementu będącego właścicielem (typu [CWnd](../../mfc/reference/cwnd-class.md)), do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno nadrzędne obiektu okna dialogowego jest ustawione na główne okno aplikacji.

*nIDTemplate*<br/>
Zawiera numer IDENTYFIKACYJNy zasobu szablonu okna dialogowego.

*nHtmlResID*<br/>
Zawiera numer IDENTYFIKACYJNy zasobu HTML.

### <a name="remarks"></a>Uwagi

Druga forma konstruktora zapewnia dostęp do zasobu okna dialogowego za pomocą nazwy szablonu. Trzecia forma konstruktora zapewnia dostęp do zasobu okna dialogowego za pomocą identyfikatora szablonu zasobu. Zazwyczaj identyfikator rozpoczyna się od prefiksu **IDD_** .

##  <a name="_dtorcdhtmldialog"></a>CDHtmlDialog:: ~ CDHtmlDialog

Niszczy obiekt CDHtmlDialog.

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska [CWnd::D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow) musi być używana do niszczenia niemodalnych okien dialogowych, które są tworzone przez [CDialog:: Create](../../mfc/reference/cdialog-class.md#create).

##  <a name="createcontrolsite"></a>CDHtmlDialog:: CreateControlSite

Wartość zastąpienia użyta do utworzenia wystąpienia lokacji kontrolki do hostowania formantu WebBrowser w oknie dialogowym.

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>Parametry

*pContainer*<br/>
Wskaźnik do obiektu [COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)

*ppSite*<br/>
Wskaźnik do wskaźnika do elementu [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można zastąpić tę funkcję elementu członkowskiego, aby zwracała wystąpienie własnej klasy kontrolek.

##  <a name="ddx_dhtml_axcontrol"></a>CDHtmlDialog::D DX_DHtml_AxControl

Wymienia dane między zmienną członkowską a wartością właściwości kontrolki ActiveX na stronie HTML.

```
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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*szId*<br/>
Wartość parametru ID tagu obiektu w źródle HTML dla kontrolki ActiveX.

*dispId*<br/>
Identyfikator wysyłania właściwości, z którą chcesz wymieniać dane.

*szPropName*<br/>
Nazwa właściwości.

*var*<br/>
Element członkowski danych typu VARIANT, [COleVariant](../../mfc/reference/colevariant-class.md)lub [CComVariant](../../atl/reference/ccomvariant-class.md), który zawiera wartość wymienianą z właściwością kontrolki ActiveX.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

##  <a name="ddx_dhtml_checkbox"></a>CDHtmlDialog::D DX_DHtml_CheckBox

Wymienia dane między zmienną członkowską i polem wyboru na stronie HTML.

```
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*szId*<br/>
Wartość określona dla parametru identyfikatora kontrolki HTML.

*value*<br/>
Wartość wymieniana.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

##  <a name="ddx_dhtml_elementtext"></a>CDHtmlDialog::D DX_DHtml_ElementText

Wymienia dane między zmienną członkowską i dowolną właściwością elementu HTML na stronie HTML.

```
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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*szId*<br/>
Wartość określona dla parametru identyfikatora kontrolki HTML.

*dispId*<br/>
Identyfikator wysyłania elementu HTML, z którym chcesz wymienić dane.

*value*<br/>
Wartość wymieniana.

##  <a name="ddx_dhtml_radio"></a>CDHtmlDialog::D DX_DHtml_Radio

Wymienia dane między zmienną członkowską i przyciskiem radiowym na stronie HTML.

```
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*szId*<br/>
Wartość określona dla parametru identyfikatora kontrolki HTML.

*value*<br/>
Wartość wymieniana.

##  <a name="ddx_dhtml_selectindex"></a>CDHtmlDialog::D DX_DHtml_SelectIndex

Pobiera lub ustawia indeks pola listy na stronie HTML.

```
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*szId*<br/>
Wartość określona dla `id` parametru kontrolki HTML.

*value*<br/>
Wartość wymieniana.

##  <a name="ddx_dhtml_selectstring"></a>CDHtmlDialog::D DX_DHtml_SelectString

Pobiera lub ustawia tekst wyświetlany wpisu pola listy (na podstawie bieżącego indeksu) na stronie HTML.

```
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*szId*<br/>
Wartość określona dla parametru identyfikatora kontrolki HTML.

*value*<br/>
Wartość wymieniana.

##  <a name="ddx_dhtml_selectvalue"></a>CDHtmlDialog::D DX_DHtml_SelectValue

Pobiera lub ustawia wartość wpisu pola listy (na podstawie bieżącego indeksu) na stronie HTML.

```
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*szId*<br/>
Wartość określona dla parametru identyfikatora kontrolki HTML.

*value*<br/>
Wartość wymieniana.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

##  <a name="destroymodeless"></a>CDHtmlDialog::D estroyModeless

Odłącza niemodalne okno dialogowe z `CDHtmlDialog` obiektu i niszczy obiekt.

```
void DestroyModeless();
```

##  <a name="enablemodeless"></a>CDHtmlDialog:: EnableModeless

Włącza Niemodalne okna dialogowe.

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>Parametry

*fEnable*<br/>
Zobacz *fEnable* w [IDocHostUIHandler:: EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją CDHtmlDialog [IDocHostUIHandler:: EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)), zgodnie z opisem w Windows SDK.

##  <a name="filterdataobject"></a>CDHtmlDialog:: FilterDataObject

Umożliwia okno dialogowe Filtrowanie obiektów danych schowka utworzonych przez hostowaną przeglądarkę.

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>Parametry

*pDO*<br/>
Zobacz *pDO* w [IDocHostUIHandler:: FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)) w Windows SDK.

*ppDORet*<br/>
Zobacz *ppDORet* w `IDocHostUIHandler::FilterDataObject` programie w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją CDHtmlDialog [IDocHostUIHandler:: FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)), zgodnie z opisem w Windows SDK.

##  <a name="getcontroldispatch"></a>CDHtmlDialog:: GetControlDispatch

Pobiera interfejs na kontrolce ActiveX osadzony w dokumencie HTML zwróconym przez [GetDHtmlDocument.](#getdhtmldocument) `IDispatch`

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>Parametry

*szId*<br/>
Identyfikator HTML kontrolki ActiveX.

*ppdisp*<br/>
`IDispatch` Interfejs kontrolki, jeśli znajduje się na stronie sieci Web.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

##  <a name="getcontrolproperty"></a>CDHtmlDialog:: GetControlProperty

Pobiera żądaną właściwość określonej kontrolki ActiveX.

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

*szId*<br/>
Identyfikator HTML kontrolki ActiveX.

*szPropName*<br/>
Nazwa właściwości w domyślnych ustawieniach regionalnych bieżącego użytkownika.

*pdispControl*<br/>
`IDispatch` Wskaźnik kontrolki ActiveX.

*dispId*<br/>
Identyfikator wysyłania właściwości.

### <a name="return-value"></a>Wartość zwracana

Wariant zawierający żądaną właściwość lub pusty wariant, jeśli nie można znaleźć kontrolki lub właściwości.

### <a name="remarks"></a>Uwagi

Przeciążenia są wyświetlane od najmniej wydajnych u góry do najbardziej wydajnego w dolnej części.

##  <a name="getcurrenturl"></a>CDHtmlDialog:: GetCurrentUrl

Pobiera adres URL (Uniform Resource Locator) skojarzony z bieżącym dokumentem.

```
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>Parametry

*szUrl*<br/>
Obiekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający adres URL do pobrania.

##  <a name="getdhtmldocument"></a>CDHtmlDialog:: GetDHtmlDocument

Pobiera Interfejs [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) na aktualnie załadowanym dokumencie HTML.

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>Parametry

pphtmlDoc wskaźnik do wskaźnika do dokumentu HTML.  *\* \**

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT. Zwraca S_OK, jeśli powodzenie.

##  <a name="getdroptarget"></a>CDHtmlDialog:: GetDropTarget

Wywoływane przez zawartą kontrolkę WebBrowser, gdy jest ona używana jako element docelowy upuszczania, aby zezwolić na dostarczenie przez okno dialogowe alternatywnej [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>Parametry

*pDropTarget*<br/>
Zobacz *pDropTarget* w [IDocHostUIHandler:: GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)) w Windows SDK.

*ppDropTarget*<br/>
Zobacz *ppDropTarget* w `IDocHostUIHandler::GetDropTarget` programie w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją CDHtmlDialog [IDocHostUIHandler:: GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)), zgodnie z opisem w Windows SDK.

##  <a name="getelement"></a>CDHtmlDialog:: GetElement

Zwraca interfejs elementu HTML określony przez *szElementId*.

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
`IDispatch` Wskaźnik do żądanego elementu lub kolekcji elementów.

*pbCollection*<br/>
Wartość logiczna wskazująca, czy obiekt reprezentowany przez *ppdisp* jest pojedynczym elementem, czy kolekcją elementów.

*pphtmlElement*<br/>
`IHTMLElement` Wskaźnik do żądanego elementu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Użyj pierwszego przeciążenia, jeśli chcesz obsłużyć warunki, w których może istnieć więcej niż jeden element o określonym IDENTYFIKATORze. Możesz użyć ostatniego parametru, aby dowiedzieć się, czy zwracany wskaźnik interfejsu jest kolekcją lub pojedynczym elementem. Jeśli wskaźnik interfejsu znajduje się w kolekcji, można wykonać zapytanie dla `IHTMLElementCollection` i użyć jej `item` właściwości, aby odwołać się do elementów według pozycji porządkowej.

Drugie Przeciążenie zakończy się niepowodzeniem, jeśli istnieje więcej niż jeden element o takim samym IDENTYFIKATORze na stronie.

##  <a name="getelementhtml"></a>CDHtmlDialog:: GetElementHtml

Pobiera właściwość elementu HTML identyfikowanego przez szElementId. `innerHTML`

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

### <a name="return-value"></a>Wartość zwracana

Właściwość elementu HTML identyfikowanego przez szElementId lub wartość null, jeśli nie można znaleźć elementu. `innerHTML`

##  <a name="getelementinterface"></a>CDHtmlDialog:: GetElementInterface

Pobiera żądany wskaźnik interfejsu z elementu HTML identyfikowanego przez *szElementId*.

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

*ppvObj*<br/>
Adres wskaźnika, który będzie wypełniony wskaźnikiem żądanego interfejsu, jeśli element zostanie znaleziony, a zapytanie powiodło się.

*refiid*<br/>
Identyfikator interfejsu (IID) żądanego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

##  <a name="getelementproperty"></a>CDHtmlDialog:: GetElementProperty

Pobiera wartość właściwości identyfikowanej przez identyfikator *dispId* z elementu HTML identyfikowanego przez *szElementId*.

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

*dispId*<br/>
Identyfikator wysyłania właściwości.

### <a name="return-value"></a>Wartość zwracana

Wartość właściwości lub pustej wariantu, jeśli nie można odnaleźć właściwości lub elementu.

##  <a name="getelementtext"></a>CDHtmlDialog:: GetElementText

Pobiera właściwość elementu HTML identyfikowanego przez szElementId. `innerText`

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

### <a name="return-value"></a>Wartość zwracana

Właściwość elementu HTML identyfikowanego przez szElementId lub wartość null, jeśli nie można odnaleźć właściwości lub elementu. `innerText`

##  <a name="getevent"></a>CDHtmlDialog:: GetEvent

`IHTMLEventObj` Zwraca wskaźnik do bieżącego obiektu zdarzenia.

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>Parametry

*ppEventObj*<br/>
Adres wskaźnika, który zostanie wypełniony `IHTMLEventObj` wskaźnikiem interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana tylko z poziomu procedury obsługi zdarzeń DHTML.

##  <a name="getexternal"></a>CDHtmlDialog:: getexternal

Pobiera `IDispatch` interfejs hosta.

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>Parametry

*ppDispatch*<br/>
Zobacz *ppDispatch* w [IDocHostUIHandler:: getexternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK w przypadku powodzenia lub E_NOTIMPL w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją CDHtmlDialog [IDocHostUIHandler:: getexternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)), zgodnie z opisem w Windows SDK.

##  <a name="gethostinfo"></a>CDHtmlDialog:: GetHostInfo

Pobiera funkcje interfejsu użytkownika hosta.

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>Parametry

*pInfo*<br/>
Zobacz *pInfo* w [IDocHostUIHandler:: GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją CDHtmlDialog [IDocHostUIHandler:: GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)), zgodnie z opisem w Windows SDK.

##  <a name="getoptionkeypath"></a>CDHtmlDialog:: GetOptionKeyPath

Pobiera klucz rejestru, w którym są przechowywane preferencje użytkownika.

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>Parametry

*pchKey*<br/>
Zobacz *pchKey* w [IDocHostUIHandler:: GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)) w Windows SDK.

*magazynu*<br/>
Zapoznaj się `IDocHostUIHandler::GetOptionKeyPath` z tematem *DW* w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją CDHtmlDialog [IDocHostUIHandler:: GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)), zgodnie z opisem w Windows SDK.

##  <a name="hideui"></a>CDHtmlDialog:: HideUI

Ukrywa interfejs użytkownika hosta.

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją CDHtmlDialog [IDocHostUIHandler:: HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\)), zgodnie z opisem w Windows SDK.

##  <a name="isexternaldispatchsafe"></a>CDHtmlDialog:: IsExternalDispatchSafe

Wskazuje, czy `IDispatch` interfejs hosta jest bezpieczny dla skryptów.

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość FALSE.

##  <a name="loadfromresource"></a>CDHtmlDialog:: LoadFromResource

Ładuje określony zasób do kontrolki WebBrowser w oknie dialogowym DHTML.

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

Wartość TRUE, jeśli powodzenie; w przeciwnym razie FALSE.

##  <a name="m_busehtmltitle"></a>  CDHtmlDialog::m_bUseHtmlTitle

Wskazuje, czy tytuł dokumentu HTML ma być używany jako podpis okna dialogowego.

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>Uwagi

Jeśli **m**_ **bUseHtmlTitle** ma wartość true, podpis okna dialogowego jest USTAWIANY jako tytuł dokumentu HTML; w przeciwnym razie jest używany podpis w zasobie okna dialogowego.

##  <a name="m_nhtmlresid"></a>CDHtmlDialog:: m_nHtmlResID

Identyfikator zasobu dla zasobu HTML do wyświetlenia.

```
UINT m_nHtmlResID;
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

##  <a name="m_pbrowserapp"></a>CDHtmlDialog:: m_pBrowserApp

Wskaźnik do aplikacji przeglądarki sieci Web.

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

##  <a name="m_sphtmldoc"></a>  CDHtmlDialog::m_spHtmlDoc

Wskaźnik do dokumentu HTML.

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

##  <a name="m_strcurrenturl"></a>CDHtmlDialog:: m_strCurrentUrl

Bieżący adres URL.

```
CString m_strCurrentUrl;
```

##  <a name="m_szhtmlresid"></a>  CDHtmlDialog::m_szHtmlResID

Wersja ciągu identyfikatora zasobu HTML.

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

##  <a name="navigate"></a>CDHtmlDialog:: Nawiguj

Przechodzi do zasobu identyfikowanego przez adres URL określony przez *lpszURL*.

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
Wskaźnik do ciągu zawierającego adres URL, który ma być celem.

*flagiDW*<br/>
Flagi zmiennej określającej, czy dodać zasób do listy Historia, czy ma być odczytywany w pamięci podręcznej, czy zapisane w pamięci podręcznej oraz czy zasób ma być wyświetlany w nowym oknie. Zmienna może być kombinacją wartości zdefiniowanych przez Wyliczenie [BrowserNavConstants](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\)) .

*lpszTargetFrameName*<br/>
Wskaźnik do ciągu, który zawiera nazwę ramki, w której ma zostać wyświetlony zasób.

*lpszHeaders*<br/>
Wskaźnik do wartości, która określa nagłówki HTTP do wysłania do serwera. Te nagłówki są dodawane do domyślnych nagłówków programu Internet Explorer. Nagłówki mogą określać takie informacje jak wymagana akcja serwera, typ danych przesyłanych do serwera lub kod stanu. Ten parametr jest ignorowany, jeśli adres URL nie jest adresem URL protokołu HTTP.

*lpvPostData*<br/>
Wskaźnik do danych, które mają zostać wysłane za pomocą transakcji POST protokołu HTTP. Na przykład transakcja POST służy do wysyłania danych zebranych przez formularz HTML. Jeśli ten parametr nie określa żadnych danych post, `Navigate` generuje transakcję HTTP GET. Ten parametr jest ignorowany, jeśli adres URL nie jest adresem URL protokołu HTTP.

*dwPostDataLen*<br/>
Dane do wysłania przy użyciu transakcji HTTP POST. Na przykład transakcja POST służy do wysyłania danych zebranych przez formularz HTML. Jeśli ten parametr nie określa żadnych danych post, `Navigate` generuje transakcję HTTP GET. Ten parametr jest ignorowany, jeśli adres URL nie jest adresem URL protokołu HTTP.

##  <a name="onbeforenavigate"></a>CDHtmlDialog:: OnBeforeNavigate

Wywoływane przez platformę, aby spowodować uruchomienie zdarzenia przed wystąpieniem nawigacji.

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Wskaźnik do `IDispatch` obiektu.

*szUrl*<br/>
Wskaźnik do ciągu zawierającego adres URL, do którego chcesz przejść.

##  <a name="ondocumentcomplete"></a>CDHtmlDialog:: OnDocumentComplete

Wywoływane przez platformę, by powiadomić aplikację, gdy dokument osiągnął stan READYSTATE_COMPLETE.

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Wskaźnik do `IDispatch` obiektu.

*szUrl*<br/>
Wskaźnik do ciągu zawierającego adres URL, do którego nastąpiło przejście.

##  <a name="ondocwindowactivate"></a>CDHtmlDialog:: OnDocWindowActivate

Wywoływane przez platformę, gdy okno dokumentu jest aktywowane lub dezaktywowane.

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parametry

*fActivate*<br/>
Zobacz *fActivate* w [IDocHostUIHandler:: OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją CDHtmlDialog [IDocHostUIHandler:: OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)), zgodnie z opisem w Windows SDK.

##  <a name="onframewindowactivate"></a>CDHtmlDialog:: OnFrameWindowActivate

Wywoływane przez platformę, gdy okno ramki jest aktywowane lub dezaktywowane.

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parametry

*fActivate*<br/>
Zobacz *fActivate* w [IDocHostUIHandler:: OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją CDHtmlDialog [IDocHostUIHandler:: OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)), zgodnie z opisem w Windows SDK.

##  <a name="oninitdialog"></a>CDHtmlDialog:: OnInitDialog

Wywołuje się w odpowiedzi na komunikat WM_INITDIALOG.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Ta wiadomość jest wysyłana do okna dialogowego w trakcie `Create`, `CreateIndirect`, lub `DoModal` wywołania, które występują bezpośrednio przed wyświetleniem okna dialogowego.

Przesłoń tę funkcję elementu członkowskiego, jeśli trzeba przeprowadzić przetwarzanie specjalne po zainicjowaniu okna dialogowego. W zastąpionej wersji, najpierw Wywołaj klasę `OnInitDialog` bazową, ale zignoruj jej wartość zwracaną. Zwykle zwracasz wartość TRUE ze zastąpionej funkcji członkowskiej.

System Windows wywołuje `OnInitDialog` funkcję za pomocą standardowej globalnej procedury okna dialogowego, która jest wspólna dla wszystkich Biblioteka MFC okien dialogowych, a nie za pomocą mapy komunikatów, dlatego nie trzeba wprowadzać wpisów mapy komunikatów dla tej funkcji elementu członkowskiego.

##  <a name="onnavigatecomplete"></a>CDHtmlDialog:: OnNavigateComplete

Wywoływane przez platformę po zakończeniu nawigacji do podanego adresu URL.

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Wskaźnik do `IDispatch` obiektu.

*szUrl*<br/>
Wskaźnik do ciągu zawierającego adres URL, do którego nastąpiło przejście.

##  <a name="resizeborder"></a>CDHtmlDialog:: ResizeBorder

Alarmuje obiekt, którego potrzeba do zmiany rozmiaru obszaru obramowania.

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>Parametry

*prcBorder*<br/>
Zobacz *prcBorder* w [IDocHostUIHandler:: ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\)) w Windows SDK.

*pUIWindow*<br/>
Zobacz *pUIWindow* w `IDocHostUIHandler::ResizeBorder` programie w Windows SDK.

*fFrameWindow*<br/>
Zobacz *fFrameWindow* w `IDocHostUIHandler::ResizeBorder` programie w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

##  <a name="setcontrolproperty"></a>CDHtmlDialog:: SetControlProperty

Ustawia właściwość kontrolki ActiveX na nową wartość.

```
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
Identyfikator HTML kontrolki ActiveX.

*dispId*<br/>
Identyfikator wysyłania właściwości do ustawienia.

*pVar*<br/>
Wskaźnik na element VARIANT zawierający nową wartość właściwości.

*pdispControl*<br/>
Wskaźnik do `IDispatch` interfejsu kontrolki ActiveX.

*szPropName*<br/>
Ciąg zawierający nazwę właściwości do ustawienia.

##  <a name="setelementhtml"></a>CDHtmlDialog:: SetElementHtml

`innerHTML` Ustawia właściwość elementu HTML.

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
`IUnknown` Wskaźnik elementu HTML.

##  <a name="setelementproperty"></a>CDHtmlDialog:: SetElementProperty

Ustawia właściwość elementu HTML.

```
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parametry

*szElementId*<br/>
Identyfikator elementu HTML.

*dispId*<br/>
Identyfikator wysyłania właściwości do ustawienia.

*pVar*<br/>
Nowa wartość właściwości.

##  <a name="setelementtext"></a>CDHtmlDialog:: SetElementText

`innerText` Ustawia właściwość elementu HTML.

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
`IUnknown` Wskaźnik elementu HTML.

##  <a name="setexternaldispatch"></a>CDHtmlDialog:: SetExternalDispatch

Ustawia `IDispatch` interfejs hosta.

```
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>Parametry

*pdispExternal*<br/>
Nowy `IDispatch` interfejs.

##  <a name="sethostflags"></a>CDHtmlDialog:: SetHostFlags

Ustawia flagi interfejsu użytkownika hosta.

```
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*flagiDW*<br/>
Aby uzyskać możliwe wartości, zobacz [DOCHOSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) w Windows SDK.

##  <a name="showcontextmenu"></a>CDHtmlDialog:: ShowContextMenu

Wywoływana, gdy menu kontekstowe ma być wyświetlane.

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>Parametry

*dwID*<br/>
Zobacz *dwID* w [IDocHostUIHandler:: ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)) w Windows SDK.

*formacie*<br/>
Zobacz *PPT* w `IDocHostUIHandler::ShowContextMenu` Windows SDK.

*pcmdtReserved*<br/>
Zobacz *pcmdtReserved* w `IDocHostUIHandler::ShowContextMenu` programie w Windows SDK.

*pdispReserved*<br/>
Zobacz *pdispReserved* w `IDocHostUIHandler::ShowContextMenu` programie w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją CDHtmlDialog [IDocHostUIHandler:: ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)), zgodnie z opisem w Windows SDK.

##  <a name="showui"></a>CDHtmlDialog:: ShowUI

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

*dwID*<br/>
Zobacz *dwID* w [IDocHostUIHandler:: ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)) w Windows SDK.

*pActiveObject*<br/>
Zobacz *d pActiveObject* w `IDocHostUIHandler::ShowUI` Windows SDK.

*pCommandTarget*<br/>
Zobacz *pCommandTarget* w `IDocHostUIHandler::ShowUI` programie w Windows SDK.

*pFrame*<br/>
Zobacz *pFrame* w `IDocHostUIHandler::ShowUI` programie w Windows SDK.

*pDoc*<br/>
Zobacz *PDOC* w `IDocHostUIHandler::ShowUI` programie w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją CDHtmlDialog [IDocHostUIHandler:: ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)), zgodnie z opisem w Windows SDK.

##  <a name="translateaccelerator"></a>CDHtmlDialog:: TranslateAccelerator

Wywołuje się, by przetworzyć komunikaty klawisza skrótu menu.

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>Parametry

*lpMsg*<br/>
Zobacz *lpMsg* w [IDocHostUIHandler:: TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)) w Windows SDK.

*pguidCmdGroup*<br/>
Zobacz *pguidCmdGroup* w `IDocHostUIHandler::TranslateAccelerator` programie w Windows SDK.

*nCmdID*<br/>
Zobacz *nCmdID* w `IDocHostUIHandler::TranslateAccelerator` programie w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją CDHtmlDialog [IDocHostUIHandler:: TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)), zgodnie z opisem w Windows SDK.

##  <a name="translateurl"></a>CDHtmlDialog:: TranslateUrl

Wywołuje się, by zmodyfikować adres URL do załadowania.

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>Parametry

*dwTranslate*<br/>
Zobacz *dwTranslate* w [IDocHostUIHandler:: TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)) w Windows SDK.

*pchURLIn*<br/>
Zobacz *pchURLIn* w `IDocHostUIHandler::TranslateUrl` programie w Windows SDK.

*ppchURLOut*<br/>
Zobacz *ppchURLOut* w `IDocHostUIHandler::TranslateUrl` programie w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją CDHtmlDialog [IDocHostUIHandler:: TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)), zgodnie z opisem w Windows SDK.

##  <a name="updateui"></a>CDHtmlDialog:: UpdateUI

Wywołuje się, by powiadomić hosta o zmianie stanu polecenia.

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest implementacją CDHtmlDialog [IDocHostUIHandler:: UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\)), zgodnie z opisem w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Przykład DHtmlExplore MFC](../../overview/visual-cpp-samples.md)<br/>
[Makra pomocnika DDX_DHtml](#ddx_dhtml_helper_macros)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
