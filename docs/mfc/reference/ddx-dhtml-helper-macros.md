---
title: Makra pomocnika DDX_DHtml
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
ms.openlocfilehash: f78a923a498713867c13ccc88e3e30c1f0a23885
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365868"
---
# <a name="ddx_dhtml-helper-macros"></a>Makra pomocnika DDX_DHtml

Makra pomocnika DDX_DHtml umożliwiają łatwy dostęp do powszechnie używanych właściwości formantów na stronie HTML.

### <a name="data-exchange-macros"></a>Makra wymiany danych

|||
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Ustawia lub pobiera Value właściwości z wybranego formantu.|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Ustawia lub pobiera tekst między znacznikami początkowymi i końcowymi bieżącego elementu.|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Ustawia lub pobiera kod HTML między znacznikami początkowymi i końcowymi bieżącego elementu.|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Ustawia lub pobiera docelowy adres URL lub punkt kontrolny.|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Ustawia lub pobiera okno docelowe lub ramkę.|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Ustawia lub pobiera nazwę obrazu lub klipu wideo w dokumencie.|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Ustawia lub pobiera adres URL skojarzonej ramki.|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Ustawia lub pobiera adres URL skojarzonej ramki.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdhtml.h

## <a name="ddx_dhtml_anchor_href"></a><a name="ddx_dhtml_anchor_href"></a>DDX_DHtml_Anchor_Href

Ustawia lub pobiera docelowy adres URL lub punkt kontrolny.

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Nazwa*<br/>
Wartość określona dla parametru identyfikatora formantu HTML.

*var*<br/>
Wartość wymieniana.

## <a name="remarks"></a>Uwagi

To makro wywołuje funkcję [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora DISPID_IHTMLANCHORELEMENT_HREF wysyłki.

## <a name="ddx_dhtml_anchor_target"></a><a name="ddx_dhtml_anchor_target"></a>DDX_DHtml_Anchor_Target

Ustawia lub pobiera okno docelowe lub ramkę.

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Nazwa*<br/>
Wartość określona dla parametru identyfikatora formantu HTML.

*var*<br/>
Wartość wymieniana.

## <a name="remarks"></a>Uwagi

To makro wywołuje funkcję [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora DISPID_IHTMLANCHORELEMENT_TARGET wysyłki.

## <a name="ddx_dhtml_elementinnerhtml"></a><a name="ddx_dhtml_elementinnerhtml"></a>DDX_DHtml_ElementInnerHtml

Ustawia lub pobiera kod HTML między znacznikami początkowymi i końcowymi bieżącego elementu.

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Nazwa*<br/>
Wartość określona dla parametru identyfikatora formantu HTML.

*var*<br/>
Wartość wymieniana.

## <a name="remarks"></a>Uwagi

To makro wywołuje funkcję [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora DISPID_IHTMLELEMENT_INNERHTML wysyłki.

## <a name="ddx_dhtml_elementinnertext"></a><a name="ddx_dhtml_elementinnertext"></a>DDX_DHtml_ElementInnerText

Ustawia lub pobiera tekst między znacznikami początkowymi i końcowymi bieżącego elementu.

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Nazwa*<br/>
Wartość określona dla parametru identyfikatora formantu HTML.

*var*<br/>
Wartość wymieniana.

## <a name="remarks"></a>Uwagi

To makro wywołuje funkcję [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora DISPID_IHTMLELEMENT_INNERTEXT wysyłki.

## <a name="ddx_dhtml_elementvalue"></a><a name="ddx_dhtml_elementvalue"></a>DDX_DHtml_ElementValue

Ustawia lub pobiera Value właściwości z wybranego formantu.

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Nazwa*<br/>
Wartość określona dla parametru identyfikatora formantu HTML.

*var*<br/>
Wartość wymieniana. Zobacz *wartość* w [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).

## <a name="remarks"></a>Uwagi

To makro powiedzie się tylko wtedy, gdy jest uruchamiane na formanty, które mają Value właściwości. Formanty, które mają Value właściwości obejmują pola edycji, pola listy i pola kombi.

To makro wywołuje funkcję [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora DISPID_A_VALUE wysyłki.

## <a name="ddx_dhtml_frame_src"></a><a name="ddx_dhtml_frame_src"></a>DDX_DHtml_Frame_Src

Ustawia lub pobiera adres URL skojarzonej ramki.

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Nazwa*<br/>
Wartość określona dla parametru identyfikatora formantu HTML.

*var*<br/>
Wartość wymieniana.

## <a name="remarks"></a>Uwagi

To makro wywołuje funkcję [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora DISPID_IHTMLFRAMEBASE_SRC wysyłki.

## <a name="ddx_dhtml_iframe_src"></a><a name="ddx_dhtml_iframe_src"></a>DDX_DHtml_IFrame_Src

Ustawia lub pobiera adres URL skojarzonej ramki.

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Nazwa*<br/>
Wartość określona dla parametru identyfikatora formantu HTML.

*var*<br/>
Wartość wymieniana.

## <a name="remarks"></a>Uwagi

To makro wywołuje funkcję [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora DISPID_IHTMLFRAMEBASE_SRC wysyłki.

## <a name="ddx_dhtml_img_src"></a><a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src

Pobiera lub pobiera nazwę obrazu lub klipu wideo w dokumencie.

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Nazwa*<br/>
Wartość określona dla parametru identyfikatora formantu HTML.

*var*<br/>
Wartość wymieniana.

## <a name="remarks"></a>Uwagi

W przypadku korzystania z makra DDX_DHtml_Img_Src do pobrania właściwości src dla elementu IMAGE obiekt obrazu programu Internet Explorer zwróci całkowicie zmieniony adres URL źródła obrazu. Na przykład, jeśli podczas pobierania tej właściwości użyjesz makra DDX_DHtml_Img_Src, aby ustawić właściwość src elementu IMAGE na ciąg "jakiś interesujący obraz", program Internet Explorer zwróci ciąg "res://d:\myapplication\myapp.exe/some%20interesting%20picture".

To makro wywołuje funkcję [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora DISPID_IHTMLIMGELEMENT_SRC wysyłki.

## <a name="see-also"></a>Zobacz też

[Klasa CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)
