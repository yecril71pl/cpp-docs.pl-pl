---
title: DDX_DHtml makra pomocnika
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
ms.openlocfilehash: 6158bffceda7ac83b79b6ff8bd7fce0378759819
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837466"
---
# <a name="ddx_dhtml-helper-macros"></a>DDX_DHtml makra pomocnika

Makra pomocnika DDX_DHtml umożliwiają łatwy dostęp do najczęściej używanych właściwości formantów na stronie HTML.

### <a name="data-exchange-macros"></a>Makra wymiany danych

|Nazwa|Opis|
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Ustawia lub pobiera właściwość Value z wybranej kontrolki.|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Ustawia lub pobiera tekst między tagami początkowymi i końcowymi bieżącego elementu.|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Ustawia lub Pobiera kod HTML między tagami początkowymi i końcowymi bieżącego elementu.|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Ustawia lub pobiera docelowy adres URL lub punkt zakotwiczenia.|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Ustawia lub pobiera docelowe okno lub ramkę.|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Ustawia lub pobiera nazwę obrazu lub klipu wideo w dokumencie.|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Ustawia lub Pobiera adres URL skojarzonej ramki.|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Ustawia lub Pobiera adres URL skojarzonej ramki.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdhtml. h

## <a name="ddx_dhtml_anchor_href"></a><a name="ddx_dhtml_anchor_href"></a> DDX_DHtml_Anchor_Href

Ustawia lub pobiera docelowy adres URL lub punkt zakotwiczenia.

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*Nazwij*<br/>
Wartość określona dla parametru identyfikatora kontrolki HTML.

*funkcję*<br/>
Wartość wymieniana.

## <a name="remarks"></a>Uwagi

To makro wywołuje funkcję [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora wysyłania DISPID_IHTMLANCHORELEMENT_HREF.

## <a name="ddx_dhtml_anchor_target"></a><a name="ddx_dhtml_anchor_target"></a> DDX_DHtml_Anchor_Target

Ustawia lub pobiera docelowe okno lub ramkę.

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*Nazwij*<br/>
Wartość określona dla parametru identyfikatora kontrolki HTML.

*funkcję*<br/>
Wartość wymieniana.

## <a name="remarks"></a>Uwagi

To makro wywołuje funkcję [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora wysyłania DISPID_IHTMLANCHORELEMENT_TARGET.

## <a name="ddx_dhtml_elementinnerhtml"></a><a name="ddx_dhtml_elementinnerhtml"></a> DDX_DHtml_ElementInnerHtml

Ustawia lub Pobiera kod HTML między tagami początkowymi i końcowymi bieżącego elementu.

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*Nazwij*<br/>
Wartość określona dla parametru identyfikatora kontrolki HTML.

*funkcję*<br/>
Wartość wymieniana.

## <a name="remarks"></a>Uwagi

To makro wywołuje funkcję [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora wysyłania DISPID_IHTMLELEMENT_INNERHTML.

## <a name="ddx_dhtml_elementinnertext"></a><a name="ddx_dhtml_elementinnertext"></a> DDX_DHtml_ElementInnerText

Ustawia lub pobiera tekst między tagami początkowymi i końcowymi bieżącego elementu.

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*Nazwij*<br/>
Wartość określona dla parametru identyfikatora kontrolki HTML.

*funkcję*<br/>
Wartość wymieniana.

## <a name="remarks"></a>Uwagi

To makro wywołuje funkcję [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora wysyłania DISPID_IHTMLELEMENT_INNERTEXT.

## <a name="ddx_dhtml_elementvalue"></a><a name="ddx_dhtml_elementvalue"></a> DDX_DHtml_ElementValue

Ustawia lub pobiera właściwość Value z wybranej kontrolki.

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*Nazwij*<br/>
Wartość określona dla parametru identyfikatora kontrolki HTML.

*funkcję*<br/>
Wartość wymieniana. Zobacz *wartość* w [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).

## <a name="remarks"></a>Uwagi

To makro powiedzie się tylko po uruchomieniu formantów mających Właściwość Value. Kontrolki, które mają właściwość Value, obejmują pola edycji, pola listy i pola kombi.

To makro wywołuje funkcję [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora wysyłania DISPID_A_VALUE.

## <a name="ddx_dhtml_frame_src"></a><a name="ddx_dhtml_frame_src"></a> DDX_DHtml_Frame_Src

Ustawia lub Pobiera adres URL skojarzonej ramki.

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*Nazwij*<br/>
Wartość określona dla parametru identyfikatora kontrolki HTML.

*funkcję*<br/>
Wartość wymieniana.

## <a name="remarks"></a>Uwagi

To makro wywołuje funkcję [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora wysyłania DISPID_IHTMLFRAMEBASE_SRC.

## <a name="ddx_dhtml_iframe_src"></a><a name="ddx_dhtml_iframe_src"></a> DDX_DHtml_IFrame_Src

Ustawia lub Pobiera adres URL skojarzonej ramki.

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*Nazwij*<br/>
Wartość określona dla parametru identyfikatora kontrolki HTML.

*funkcję*<br/>
Wartość wymieniana.

## <a name="remarks"></a>Uwagi

To makro wywołuje funkcję [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora wysyłania DISPID_IHTMLFRAMEBASE_SRC.

## <a name="ddx_dhtml_img_src"></a><a name="ddx_dhtml_img_src"></a> DDX_DHtml_Img_Src

Pobiera lub pobiera nazwę obrazu lub klipu wideo w dokumencie.

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*Nazwij*<br/>
Wartość określona dla parametru identyfikatora kontrolki HTML.

*funkcję*<br/>
Wartość wymieniana.

## <a name="remarks"></a>Uwagi

Przy użyciu makra DDX_DHtml_Img_Src do pobrania właściwości src dla elementu obrazu, obiekt obrazu programu Internet Explorer zwróci w pełni zmieniony adres URL dla źródła obrazu. Jeśli na przykład użyjesz makra DDX_DHtml_Img_Src, aby ustawić właściwość src elementu obrazu na ciąg "jakiś interesujący obraz", po pobraniu tej właściwości program Internet Explorer zwróci ciąg "res://d:\myapplication\myapp.exe/some%20interesting%20picture."

To makro wywołuje funkcję [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu identyfikatora wysyłania DISPID_IHTMLIMGELEMENT_SRC.

## <a name="see-also"></a>Zobacz też

[Klasa CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)
