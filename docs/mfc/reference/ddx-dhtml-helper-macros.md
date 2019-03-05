---
title: Makra pomocnika Ddx_dhtml
ms.date: 11/04/2016
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
ms.openlocfilehash: 90c80dbc5c8b6788f3afad3cf77d796139fbd946
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326650"
---
# <a name="ddxdhtml-helper-macros"></a>Makra pomocnika Ddx_dhtml

Makra pomocnika ddx_dhtml umożliwia łatwy dostęp do często używanych właściwości formantów na stronie HTML.

### <a name="data-exchange-macros"></a>Makra wymiany danych

|||
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Ustawia lub pobiera wartość właściwości z wybranej kontrolki.|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Ustawia lub pobiera tekstu między tagiem początkowym i końcowym bieżącego elementu.|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Ustawia lub pobiera kodu HTML między tagiem początkowym i końcowym bieżącego elementu.|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Ustawia lub pobiera docelowy adres URL i punktu kontrolnego.|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Ustawia lub pobiera docelowego okna lub ramki.|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Ustawia lub pobiera nazwę obrazu lub klip wideo w dokumencie.|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Ustawia lub pobiera adres URL skojarzony ramki.|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Ustawia lub pobiera adres URL skojarzony ramki.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdhtml.h

## <a name="ddx_dhtml_anchor_href"></a> DDX_DHtml_Anchor_Href

Ustawia lub pobiera docelowy adres URL i punktu kontrolnego.

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*Nazwa*<br/>
Wartość określona dla parametru Identyfikatora kontrolki HTML.

*var*<br/>
Wartość wymianie.

## <a name="remarks"></a>Uwagi

Wywołuje to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkcji przy użyciu DISPID_IHTMLANCHORELEMENT_HREF wysyłania identyfikatora.

## <a name="ddx_dhtml_anchor_target"></a>  DDX_DHtml_Anchor_Target

Ustawia lub pobiera docelowego okna lub ramki.

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*Nazwa*<br/>
Wartość określona dla parametru Identyfikatora kontrolki HTML.

*var*<br/>
Wartość wymianie.

## <a name="remarks"></a>Uwagi

Wywołuje to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkcji przy użyciu DISPID_IHTMLANCHORELEMENT_TARGET wysyłania identyfikatora.

## <a name="ddx_dhtml_elementinnerhtml"></a>  DDX_DHtml_ElementInnerHtml

Ustawia lub pobiera kodu HTML między tagiem początkowym i końcowym bieżącego elementu.

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*Nazwa*<br/>
Wartość określona dla parametru Identyfikatora kontrolki HTML.

*var*<br/>
Wartość wymianie.

## <a name="remarks"></a>Uwagi

Wywołuje to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkcji przy użyciu DISPID_IHTMLELEMENT_INNERHTML wysyłania identyfikatora.

## <a name="ddx_dhtml_elementinnertext"></a>  DDX_DHtml_ElementInnerText

Ustawia lub pobiera tekstu między tagiem początkowym i końcowym bieżącego elementu.

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*Nazwa*<br/>
Wartość określona dla parametru Identyfikatora kontrolki HTML.

*var*<br/>
Wartość wymianie.

## <a name="remarks"></a>Uwagi

Wywołuje to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkcji przy użyciu DISPID_IHTMLELEMENT_INNERTEXT wysyłania identyfikatora.

## <a name="ddx_dhtml_elementvalue"></a> DDX_DHtml_ElementValue

Ustawia lub pobiera wartość właściwości z wybranej kontrolki.

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*Nazwa*<br/>
Wartość określona dla parametru Identyfikatora kontrolki HTML.

*var*<br/>
Wartość wymianie. Zobacz *wartość* w [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).

## <a name="remarks"></a>Uwagi

To makro powiedzie się tylko po uruchomieniu na formantów, które mają właściwości Value. Formanty, które mają właściwość Value zawierają pola tekstowe, pola listy i pola kombi.

Wywołuje to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkcji przy użyciu DISPID_A_VALUE wysyłania identyfikatora.

## <a name="ddx_dhtml_frame_src"></a> DDX_DHtml_Frame_Src

Ustawia lub pobiera adres URL skojarzony ramki.

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*Nazwa*<br/>
Wartość określona dla parametru Identyfikatora kontrolki HTML.

*var*<br/>
Wartość wymianie.

## <a name="remarks"></a>Uwagi

Wywołuje to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkcji przy użyciu DISPID_IHTMLFRAMEBASE_SRC wysyłania identyfikatora.

## <a name="ddx_dhtml_iframe_src"></a> DDX_DHtml_IFrame_Src

Ustawia lub pobiera adres URL skojarzony ramki.

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*Nazwa*<br/>
Wartość określona dla parametru Identyfikatora kontrolki HTML.

*var*<br/>
Wartość wymianie.

## <a name="remarks"></a>Uwagi

Wywołuje to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkcji przy użyciu DISPID_IHTMLFRAMEBASE_SRC wysyłania identyfikatora.

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src

Pobiera lub pobiera nazwę obrazu lub klip wideo w dokumencie.

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*Nazwa*<br/>
Wartość określona dla parametru Identyfikatora kontrolki HTML.

*var*<br/>
Wartość wymianie.

## <a name="remarks"></a>Uwagi

Pobrać właściwości src elementu obrazu za pomocą makra DDX_DHtml_Img_Src, obiekt obrazu programu Internet Explorer będzie zwracać pełni o zmienionym znaczeniu adres URL źródła obrazu. Na przykład jeśli makro DDX_DHtml_Img_Src jest używany do ustawiania właściwości src elementu obrazu do ciągu "niektóre ciekawe obraz", podczas pobierania tej właściwości program Internet Explorer zwróci ciąg "res://d:\myapplication\myapp.exe/some% 20interesting % 20picture."

Wywołuje to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkcji przy użyciu DISPID_IHTMLIMGELEMENT_SRC wysyłania identyfikatora.

## <a name="see-also"></a>Zobacz także

[Klasa CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)
