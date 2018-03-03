---
title: Makra pomocnika DDX_DHtml | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
dev_langs:
- C++
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d5a69e08d06a53dcb2f3a4be58618e9829e8c8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ddxdhtml-helper-macros"></a>Makra pomocnika DDX_DHtml
Zezwalaj na makra pomocnika DDX_DHtml łatwy dostęp do często używanych właściwości formantów na stronie HTML.  
  
### <a name="data-exchange-macros"></a>Makra wymiany danych  
  
|||  
|-|-|  
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Ustawia lub pobiera wartość właściwości z wybranego formantu.|  
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Ustawia lub pobiera tekst między tagiem początkowym i końcowym bieżącego elementu.|  
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Ustawia lub pobiera kod HTML między tagiem początkowym i końcowym bieżącego elementu.|  
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Ustawia lub pobiera docelowy adres URL i punktu kontrolnego.|  
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Ustawia lub pobiera docelowego okna lub ramki.|  
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Ustawia lub pobiera nazwę obrazu lub klipu wideo w dokumencie.|  
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Ustawia lub pobiera adres URL skojarzone ramki.|  
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Ustawia lub pobiera adres URL skojarzone ramki.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdhtml.h  

## <a name="ddx_dhtml_anchor_href"></a>DDX_DHtml_Anchor_Href
Ustawia lub pobiera docelowy adres URL i punktu kontrolnego.  
  
  
  
```  
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu.  
  
 `name`  
 Wartość określona dla parametru Identyfikatora kontrolka HTML.  
  
 `var`  
 Wartość wymianie.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu DISPID_IHTMLANCHORELEMENT_HREF funkcję wysyłania identyfikatora.

## <a name="ddx_dhtml_anchor_target"></a>DDX_DHtml_Anchor_Target
 Ustawia lub pobiera docelowego okna lub ramki.  
    
```  
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu.  
  
 `name`  
 Wartość określona dla parametru Identyfikatora kontrolka HTML.  
  
 `var`  
 Wartość wymianie.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu DISPID_IHTMLANCHORELEMENT_TARGET funkcję wysyłania identyfikatora.  

## <a name="ddx_dhtml_elementinnerhtml"></a>DDX_DHtml_ElementInnerHtml
 Ustawia lub pobiera kod HTML między tagiem początkowym i końcowym bieżącego elementu.  
  
  
  
```  
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu.  
  
 `name`  
 Wartość określona dla parametru Identyfikatora kontrolka HTML.  
  
 `var`  
 Wartość wymianie.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu DISPID_IHTMLELEMENT_INNERHTML funkcję wysyłania identyfikatora.  
  

## <a name="ddx_dhtml_elementinnertext"></a>DDX_DHtml_ElementInnerText
Ustawia lub pobiera tekst między tagiem początkowym i końcowym bieżącego elementu.  
  
  
  
```  
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu.  
  
 `name`  
 Wartość określona dla parametru Identyfikatora kontrolka HTML.  
  
 `var`  
 Wartość wymianie.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu DISPID_IHTMLELEMENT_INNERTEXT funkcję wysyłania identyfikatora. 

## <a name="ddx_dhtml_elementvalue"></a>DDX_DHtml_ElementValue  
Ustawia lub pobiera wartość właściwości z wybranego formantu.  
 
```  
DDX_DHtml_ElementValue(
    CDataExchange* dx,  
    LPCTSTR name,
    var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu.  
  
 `name`  
 Wartość określona dla parametru Identyfikatora kontrolka HTML.  
  
 `var`  
 Wartość wymianie. Zobacz *wartość* w [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).  
  
## <a name="remarks"></a>Uwagi  
 To makro powiedzie się tylko podczas uruchamiania w formantach, które ma wartość właściwości. Formanty, które ma wartość właściwości obejmują pola edycji i pola listy, pola kombi.  
  
 Wymaga to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu DISPID_A_VALUE funkcję wysyłania identyfikatora.  

## <a name="ddx_dhtml_frame_src"></a>DDX_DHtml_Frame_Src
Ustawia lub pobiera adres URL skojarzone ramki.  
  
```  
DDX_DHtml_Frame_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu.  
  
 `name`  
 Wartość określona dla parametru Identyfikatora kontrolka HTML.  
  
 `var`  
 Wartość wymianie.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu DISPID_IHTMLFRAMEBASE_SRC funkcję wysyłania identyfikatora.  

## <a name="ddx_dhtml_iframe_src"></a>DDX_DHtml_IFrame_Src
Ustawia lub pobiera adres URL skojarzone ramki.  
  
  
  
```  
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu.  
  
 `name`  
 Wartość określona dla parametru Identyfikatora kontrolka HTML.  
  
 `var`  
 Wartość wymianie.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu DISPID_IHTMLFRAMEBASE_SRC funkcję wysyłania identyfikatora. 

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src
Pobiera lub pobiera nazwę obrazu lub klipu wideo w dokumencie.  
  
```  
DDX_DHtml_Img_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu.  
  
 `name`  
 Wartość określona dla parametru Identyfikatora kontrolka HTML.  
  
 `var`  
 Wartość wymianie.  
  
## <a name="remarks"></a>Uwagi  
 Korzystając z `DDX_DHtml_Img_Src` makro można pobrać właściwości src elementu obrazu obiektu obrazu programu Internet Explorer będzie zwracać pełni zmienionym adres URL źródła obrazu. Na przykład, jeśli używasz `DDX_DHtml_Img_Src` makro można ustawić właściwości src elementu obrazu do ciągu "niektóre ciekawe obraz," zwraca ciąg "res://d:\myapplication\myapp.exe/some% podczas pobierania właściwości programu Internet Explorer 20interesting % 20picture."  
  
 Wymaga to makro [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) przy użyciu DISPID_IHTMLIMGELEMENT_SRC funkcję wysyłania identyfikatora.  

  
## <a name="see-also"></a>Zobacz też  
 [Klasa CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)
