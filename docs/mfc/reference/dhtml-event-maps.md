---
title: Mapy zdarzeń DHTML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.macros.shared
dev_langs:
- C++
helpviewer_keywords:
- event map macros [MFC]
- DHTML [MFC], event map macros
- macros [MFC], DHTML event map
- DHTML events [MFC], event map
- DHTML events [MFC]
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8a888cfdf8d83f3628bf4ad80b26db6ac51ad72
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123100"
---
# <a name="dhtml-event-maps"></a>Mapy zdarzeń DHTML
Następujące makra może służyć do obsługi zdarzeń DHTML.  
  
## <a name="dhtml-event-map-macros"></a>Makra mapy zdarzeń DHTML  
 Następujące makra może służyć do obsługi zdarzeń DHTML w [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-klas pochodnych.  
  
|||  
|-|-|  
|[BEGIN_DHTML_EVENT_MAP —](#begin_dhtml_event_map)|Oznacza początek mapy zdarzeń DHTML.|  
|[BEGIN_DHTML_EVENT_MAP_INLINE —](#begin_dhtml_event_map_inline)|Oznacza początek mapy zdarzeń DHTML.|  
|[DECLARE_DHTML_EVENT_MAP —](#declare_dhtml_event_map)|Deklaruje mapy zdarzeń DHTML.|  
|[DHTML_EVENT —](#dhtml_event)|Używane do obsługi zdarzenia na poziomie dokumentu dla pojedynczego elementu HTML.|  
|[DHTML_EVENT_AXCONTROL —](#dhtml_event_axcontrol)|Używane do obsługi zdarzenia wywoływane przez kontrolkę ActiveX.|  
|[DHTML_EVENT_CLASS —](#dhtml_event_class)|Używane do obsługi zdarzenia na poziomie dokumentu dla wszystkich elementów HTML o określonej klasy CSS.|  
|[DHTML_EVENT_ELEMENT —](#dhtml_event_element)|Używane do obsługi zdarzenia na poziomie elementu.|  
|[DHTML_EVENT_ONAFTERUPDATE —](#dhtml_event_onafterupdate)|Używane do obsługi `onafterupdate` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONBEFOREUPDATE —](#dhtml_event_onbeforeupdate)|Używane do obsługi `onbeforeupdate` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONBLUR —](#dhtml_event_onblur)|Używane do obsługi `onblur` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONCHANGE —](#dhtml_event_onchange)|Używane do obsługi `onchange` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONCLICK —](#dhtml_event_onclick)|Używane do obsługi `onclick` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONDATAAVAILABLE —](#dhtml_event_ondataavailable)|Używane do obsługi `ondataavailable` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONDATASETCHANGED —](#dhtml_event_ondatasetchanged)|Używane do obsługi `ondatasetchanged` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONDATASETCOMPLETE —](#dhtml_event_ondatasetcomplete)|Używane do obsługi `ondatasetcomplete` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONDBLCLICK —](#dhtml_event_ondblclick)|Używane do obsługi `ondblclick` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONDRAGSTART —](#dhtml_event_ondragstart)|Używane do obsługi `ondragstart` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONERRORUPDATE —](#dhtml_event_onerrorupdate)|Używane do obsługi `onerrorupdate` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONFILTERCHANGE —](#dhtml_event_onfilterchange)|Używane do obsługi `onfilterchange` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONFOCUS —](#dhtml_event_onfocus)|Używane do obsługi `onfocus` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONHELP —](#dhtml_event_onhelp)|Używane do obsługi `onhelp` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONKEYDOWN —](#dhtml_event_onkeydown)|Używane do obsługi `onkeydown` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONKEYPRESS —](#dhtml_event_onkeypress)|Używane do obsługi `onkeypress` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONKEYUP —](#dhtml_event_onkeyup)|Używane do obsługi `onkeyup` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONMOUSEDOWN —](#dhtml_event_onmousedown)|Używane do obsługi `onmousedown` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONMOUSEMOVE —](#dhtml_event_onmousemove)|Używane do obsługi `onmousemove` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONMOUSEOUT —](#dhtml_event_onmouseout)|Używane do obsługi `onmouseout` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONMOUSEOVER —](#dhtml_event_onmouseover)|Używane do obsługi `onmouseover` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONMOUSEUP —](#dhtml_event_onmouseup)|Używane do obsługi `onmouseup` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONRESIZE —](#dhtml_event_onresize)|Używane do obsługi `onresize` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONROWENTER —](#dhtml_event_onrowenter)|Używane do obsługi `onrowenter` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONROWEXIT —](#dhtml_event_onrowexit)|Używane do obsługi `onrowexit` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_ONSELECTSTART —](#dhtml_event_onselectstart)|Używane do obsługi `onselectstart` zdarzeń z elementu HTML.|  
|[DHTML_EVENT_TAG —](#dhtml_event_tag)|Używane do obsługi zdarzenia na poziomie dokumentu dla wszystkich elementów z określonego tagu HTML.|  
|[END_DHTML_EVENT_MAP —](#end_dhtml_event_map)|Oznacza koniec mapy zdarzeń DHTML.|  
|[END_DHTML_EVENT_MAP_INLINE —](#end_dhtml_event_map_inline)|Oznacza koniec mapy zdarzeń DHTML. |
  
## <a name="url-event-map-macros"></a>Makra mapy zdarzeń adresu URL  
 Następujące makra może służyć do obsługi zdarzeń DHTML w [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-klas pochodnych.  
  
|||  
|-|-|  
|[BEGIN_DHTML_URL_EVENT_MAP —](#begin_dhtml_url_event_map)|Oznacza początek wielostronicowe mapy zdarzeń DHTML i adres URL.|  
|[BEGIN_EMBED_DHTML_EVENT_MAP —](#begin_embed_dhtml_event_map)|Oznacza początek osadzonych mapy zdarzeń DHTML.|  
|[BEGIN_URL_ENTRIES —](#begin_url_entries)|Oznacza początek wpisu mapy zdarzeń adresu URL.|  
|[DECLARE_DHTML_URL_EVENT_MAP —](#declare_dhtml_url_event_map)|Deklaruje wielostronicowe mapy zdarzeń DHTML i adres URL.|  
|[END_DHTML_URL_EVENT_MAP —](#end_dhtml_url_event_map)|Oznacza koniec wielostronicowe mapy zdarzeń DHTML i adres URL.|  
|[END_EMBED_DHTML_EVENT_MAP —](#end_embed_dhtml_event_map)|Oznacza koniec osadzonych mapy zdarzeń DHTML.|  
|[END_URL_ENTRIES —](#end_url_entries)|Oznacza koniec wpisu mapy zdarzeń adresu URL.|  
|[URL_EVENT_ENTRY —](#url_event_entry)|Mapuje zasobu adresu URL lub kod HTML strony w wielostronicowe okna dialogowego.|  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="begin_dhtml_event_map"></a>  BEGIN_DHTML_EVENT_MAP —  
 Oznacza początek mapy zdarzeń DHTML po umieszczeniu w pliku źródłowym dla klasy oznaczona `className`.  
  
```   
BEGIN_DHTML_EVENT_MAP(className)   
```  
  
### <a name="parameters"></a>Parametry  
 *className*  
 Nazwa klasy zawierającej mapy zdarzeń DHTML. Ta klasa powinien pochodzić od bezpośrednio lub pośrednio [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) i obejmują [declare_dhtml_event_map —](#declare_dhtml_event_map) makra w ramach swojej definicji klasy.  
  
### <a name="remarks"></a>Uwagi  
 Dodawanie do swojej klasy, aby zapewnić informacje mapy zdarzeń DHTML `CDHtmlDialog` który może służyć do trasy zdarzenia wywoływane przez elementów HTML lub kontrolki ActiveX na stronie sieci web z funkcjami programu obsługi w klasie.  
  
 Umieść begin_dhtml_event_map — makro w klasy (.cpp) pliku implementacji następuje dhtml_event — makra dla klasy ma obsługę zdarzeń (na przykład dhtml_event_onmouseover — etykietka wskaźnika myszy zdarzeń). Użyj [end_dhtml_event_map —](#end_dhtml_event_map) makra w celu oznaczenia zakończenia Mapa zdarzeń. Te makra zaimplementowania następujących funkcji:  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="begin_dhtml_event_map_inline"></a>  BEGIN_DHTML_EVENT_MAP_INLINE —  
 Oznacza początek Mapa zdarzeń DHTML w definicji klasy dla *className*.  
  
```   
BEGIN_DHTML_EVENT_MAP_INLINE(className)   
```  
  
### <a name="parameters"></a>Parametry  
 *className*  
 Nazwa klasy zawierającej mapy zdarzeń DHTML. Ta klasa powinien pochodzić od bezpośrednio lub pośrednio [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) i obejmują [declare_dhtml_event_map —](#declare_dhtml_event_map) makra w ramach swojej definicji klasy.  
  
### <a name="remarks"></a>Uwagi  
 Dodawanie do swojej klasy, aby zapewnić informacje mapy zdarzeń DHTML `CDHtmlDialog` który może służyć do trasy zdarzenia wywoływane przez elementów HTML lub kontrolki ActiveX na stronie sieci web z funkcjami programu obsługi w klasie.  
  
 Umieść begin_dhtml_event_map — makro w klasy (.h) pliku definicji następuje dhtml_event — makra dla klasy ma obsługę zdarzeń (na przykład dhtml_event_onmouseover — etykietka wskaźnika myszy zdarzeń). Użyj [end_dhtml_event_map_inline —](#end_dhtml_event_map_inline) makra w celu oznaczenia zakończenia Mapa zdarzeń. Te makra zaimplementowania następujących funkcji:  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  

  
##  <a name="declare_dhtml_event_map"></a>  DECLARE_DHTML_EVENT_MAP —  
 Deklaruje mapy zdarzeń DHTML w definicji klasy.  
  
```   
DECLARE_DHTML_EVENT_MAP()   
```  
  
### <a name="remarks"></a>Uwagi  
 To makro ma być używany w definicji [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-klas pochodnych.  
  
 Użyj [begin_dhtml_event_map —](#begin_dhtml_event_map) lub [begin_dhtml_event_map_inline —](#begin_dhtml_event_map_inline) mapę implementacji.  
  
 [Declare_dhtml_event_map —](#declare_dhtml_event_map) deklaruje następujących funkcji:  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event"></a>  DHTML_EVENT —  
 Obsługuje (na poziomie dokumentu) identyfikowany przez zdarzenie *dispid* zainicjowany przez element HTML identyfikowane przez *elemName*.  
  
```   
DHTML_EVENT(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *identyfikator DISPID*  
 Identyfikator DISPID zdarzenia, które mają być obsługiwane.  
  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzeń ani mieć wartości NULL do obsługi zdarzeń dokumentu.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_axcontrol"></a>  DHTML_EVENT_AXCONTROL —  
 Obsługuje zdarzenie identyfikowane przez *dispid* wywoływane przez formant ActiveX identyfikowane przez *formantu*.  
  
```   
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)  
```  
  
### <a name="parameters"></a>Parametry  
 *identyfikator DISPID*  
 Identyfikator wysyłania zdarzeń do obsłużenia.  
  
 *Nazwa formantu*  
 LPCWSTR zawierający HTML Identyfikatora formantu wyzwoleniem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_class"></a>  DHTML_EVENT_CLASS —  
 Obsługuje (na poziomie dokumentu) identyfikowany przez zdarzenie *dispid* zainicjowany przez dowolnego elementu HTML przy użyciu klasy CSS identyfikowane przez *elemName*.  
  
```   
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *identyfikator DISPID*  
 Identyfikator wysyłania zdarzeń do obsłużenia.  
  
 *elemName*  
 LPCWSTR zawierający klasę CSS sourcing zdarzenia elementów HTML.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_element"></a>  DHTML_EVENT_ELEMENT —  
 Obsługuje (w elemencie identyfikowane przez *elemName*) identyfikowany przez zdarzenie *dispid*.  
  
```   
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn) 
```  
  
### <a name="parameters"></a>Parametry  
 *identyfikator DISPID*  
 Identyfikator wysyłania zdarzeń do obsłużenia.  
  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
 Jeśli to makro jest używane do obsługi zdarzeń nonbubbling, źródło zdarzenia będą identyfikowane przez element *elemName*.  
  
 Jeśli to makro jest używane do obsługi zdarzeń propagacji, element identyfikowane przez *elemName* nie może być źródłem zdarzenia (źródło może być dowolny element zawarty w *elemName*).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onafterupdate"></a>  DHTML_EVENT_ONAFTERUPDATE —  
 Obsługuje (na poziomie dokumentu) `onafterupdate` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```   
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onbeforeupdate"></a>  DHTML_EVENT_ONBEFOREUPDATE —  
 Obsługuje (na poziomie dokumentu) `onbeforeupdate` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```   
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onblur"></a>  DHTML_EVENT_ONBLUR —  
 Obsługuje (na poziomie elementu) `onblur` zdarzeń. To jest zdarzenie nonbubbling.  
  
```   
DHTML_EVENT_ONBLUR(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onchange"></a>  DHTML_EVENT_ONCHANGE —  
 Obsługuje (na poziomie elementu) `onchange` zdarzeń. To jest zdarzenie nonbubbling.  
  
```   
DHTML_EVENT_ONCHANGE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onclick"></a>  DHTML_EVENT_ONCLICK —  
 Obsługuje (na poziomie dokumentu) `onclick` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```   
DHTML_EVENT_ONCLICK(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_ondataavailable"></a>  DHTML_EVENT_ONDATAAVAILABLE —  
 Obsługuje (na poziomie dokumentu) `ondataavailable` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```   
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_ondatasetchanged"></a>  DHTML_EVENT_ONDATASETCHANGED —  
 Obsługuje (na poziomie dokumentu) `ondatasetchanged` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```   
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_ondatasetcomplete"></a>  DHTML_EVENT_ONDATASETCOMPLETE —  
 Obsługuje (na poziomie dokumentu) `ondatasetcomplete` pochodzi przez element HTML identyfikowane przez `elemName`.  
  
```   
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn) 
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_ondblclick"></a>  DHTML_EVENT_ONDBLCLICK —  
 Obsługuje (na poziomie dokumentu) `ondblclick` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```   
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_ondragstart"></a>  DHTML_EVENT_ONDRAGSTART —  
 Obsługuje (na poziomie dokumentu) `ondragstart` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```   
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onerrorupdate"></a>  DHTML_EVENT_ONERRORUPDATE —  
 Obsługuje (na poziomie dokumentu) `onerrorupdate` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```   
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onfilterchange"></a>  DHTML_EVENT_ONFILTERCHANGE —  
 Obsługuje (na poziomie dokumentu) `onfilterchange` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```  
 
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onfocus"></a>  DHTML_EVENT_ONFOCUS —  
 Obsługuje (na poziomie elementu) `onfocus` zdarzeń. To jest zdarzenie nonbubbling.  
  
```  
 
DHTML_EVENT_ONFOCUS(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onhelp"></a>  DHTML_EVENT_ONHELP —  
 Obsługuje (na poziomie dokumentu) `onhelp` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```  
 
DHTML_EVENT_ONHELP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onkeydown"></a>  DHTML_EVENT_ONKEYDOWN —  
 Obsługuje (na poziomie dokumentu) `onkeydown` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```  
 
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onkeypress"></a>  DHTML_EVENT_ONKEYPRESS —  
 Obsługuje (na poziomie dokumentu) `onkeypress` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```  
 
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onkeyup"></a>  DHTML_EVENT_ONKEYUP —  
 Obsługuje (na poziomie dokumentu) `onkeyup` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```  
 
DHTML_EVENT_ONKEYUP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onmousedown"></a>  DHTML_EVENT_ONMOUSEDOWN —  
 Obsługuje (na poziomie dokumentu) `onmousedown` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onmousemove"></a>  DHTML_EVENT_ONMOUSEMOVE —  
 Obsługuje (na poziomie dokumentu) `onmousemove` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onmouseout"></a>  DHTML_EVENT_ONMOUSEOUT —  
 Obsługuje (na poziomie dokumentu) `onmouseout` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onmouseover"></a>  DHTML_EVENT_ONMOUSEOVER —  
 Obsługuje (na poziomie dokumentu) `onmouseover` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onmouseup"></a>  DHTML_EVENT_ONMOUSEUP —  
 Obsługuje (na poziomie dokumentu) `onmouseup` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onresize"></a>  DHTML_EVENT_ONRESIZE —  
 Obsługuje (na poziomie elementu) `onresize` zdarzeń. To jest zdarzenie nonbubbling.  
  
```  
 
DHTML_EVENT_ONRESIZE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onrowenter"></a>  DHTML_EVENT_ONROWENTER —  
 Obsługuje (na poziomie dokumentu) `onrowenter` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```  
 
DHTML_EVENT_ONROWENTER(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onrowexit"></a>  DHTML_EVENT_ONROWEXIT —  
 Obsługuje (na poziomie dokumentu) `onrowexit` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```  
 
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_onselectstart"></a>  DHTML_EVENT_ONSELECTSTART —  
 Obsługuje (na poziomie dokumentu) `onselectstart` pochodzi przez element HTML identyfikowane przez *elemName*.  
  
```  
 
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR zawierający identyfikator elementu HTML źródłem zdarzenia.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="dhtml_event_tag"></a>  DHTML_EVENT_TAG —  
 Obsługuje (na poziomie dokumentu) identyfikowany przez zdarzenie `dispid` zainicjowany przez dowolnego elementu HTML przy tagu HTML identyfikowane przez *elemName*.  
  
```   
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *identyfikator DISPID*  
 Identyfikator wysyłania zdarzeń do obsłużenia.  
  
 *elemName*  
 Tag HTML sourcing zdarzenia elementów HTML.  
  
 *memberFxn*  
 Funkcja obsługi dla zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra, aby dodać wpis do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="end_dhtml_event_map"></a>  END_DHTML_EVENT_MAP —  
 Oznacza koniec mapy zdarzeń DHTML.  
  
```   
END_DHTML_EVENT_MAP()   
```  
  
### <a name="remarks"></a>Uwagi  
 Należy używać w połączeniu z [begin_dhtml_event_map —](#begin_dhtml_event_map).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="begin_dhtml_url_event_map"></a>  BEGIN_DHTML_URL_EVENT_MAP —  
 Uruchamia definicji mapy zdarzeń DHTML i adres URL w wielostronicowe okna dialogowego.  
  
```  
BEGIN_DHTML_URL_EVENT_MAP()  
 
```  
  
### <a name="remarks"></a>Uwagi  
 Begin_dhtml_url_event_map — należy umieścić w pliku implementacji dla Twojego [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-klasy. Wykonaj go przy użyciu [osadzone mapy zdarzeń DHTML](#begin_embed_dhtml_event_map) i [wpisy adresu URL](#begin_url_entries), a następnie zamknij go przy użyciu [end_dhtml_url_event_map —](#end_dhtml_url_event_map). Obejmują [declare_dhtml_url_event_map —](#declare_dhtml_url_event_map) makra w definicji klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="begin_embed_dhtml_event_map"></a>  BEGIN_EMBED_DHTML_EVENT_MAP —  
 Uruchamia definicji mapy zdarzeń DHTML osadzonych w wielostronicowe okna dialogowego.  
  
```  
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *className*  
 Nazwa klasy zawierającej Mapa zdarzeń. Ta klasa powinien pochodzić od bezpośrednio lub pośrednio [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Osadzony Mapa zdarzeń DHTML musi znajdować się wewnątrz [mapy zdarzeń DHTML i adres URL](#begin_dhtml_url_event_map)).  
  
 *mapName*  
 Określa, że strona, do którego zdarzenie mapowania jest. Odpowiada *mapName* w [url_event_entry —](#url_event_entry) makro faktycznie Definiowanie zasobu adresu URL lub HTML.  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ wielostronicowe okna dialogowego DHTML obejmuje wiele stron HTML, z których każdy może wywoływać zdarzenia DHTML, mapy zdarzeń osadzonych są używane do mapowania zdarzeń na programy obsługi dla poszczególnych stron.  
  
 Mapy zdarzeń osadzony wewnątrz mapy zdarzeń DHTML i adres URL składa się z begin_embed_dhtml_event_map — makro następuje [dhtml_event —](#dhtml_event) makra i [end_embed_dhtml_event_map —](#end_embed_dhtml_event_map) makra.  
  
 Każdej mapy zdarzeń osadzonych wymaga odpowiedniej [wpis dotyczący zdarzenia adresu URL](#url_event_entry) do mapowania *mapName* (określony w begin_embed_dhtml_event_map —) do zasobu adresu URL lub HTML.  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [begin_dhtml_url_event_map —](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="begin_url_entries"></a>  BEGIN_URL_ENTRIES —  
 Uruchamia definicji wpisu mapy zdarzeń adres URL w wielostronicowe okna dialogowego.  
  
```  
BEGIN_URL_ENTRIES(className)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *className*  
 Nazwa klasy zawierającej wpisu mapy zdarzeń adresu URL. Ta klasa powinien pochodzić od bezpośrednio lub pośrednio [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Adres URL zdarzenia wpisu mapy musi znajdować się wewnątrz [mapy zdarzeń DHTML i adres URL](#begin_dhtml_url_event_map)).  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ wielostronicowe okna dialogowego DHTML zawiera wiele stron HTML, adres URL zdarzenia wpisy są używane do mapowania adresów URL lub HTML zasobów do odpowiadającego [osadzone mapy zdarzeń DHTML](#begin_embed_dhtml_event_map). Umieść url_event_entry — makra między begin_url_entries — i [end_url_entries —](#end_url_entries) makra.  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [begin_dhtml_url_event_map —](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="declare_dhtml_url_event_map"></a>  DECLARE_DHTML_URL_EVENT_MAP —  
 Deklaruje mapy zdarzeń DHTML i adres URL w definicji klasy.  
  
```  
DECLARE_DHTML_URL_EVENT_MAP()  
 
```  
  
### <a name="remarks"></a>Uwagi  
 To makro ma być używany w definicji [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-klas pochodnych.  
  
 Mapa zdarzeń DHTML i adres URL zawiera [osadzone mapy zdarzeń DHTML](#begin_embed_dhtml_event_map) i [adres URL zdarzenia wpisy](#begin_url_entries) do mapy zdarzeń DHTML do programów obsługi na podstawie na stronie. Użyj [begin_dhtml_url_event_map —](#begin_dhtml_url_event_map) mapę implementacji.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="end_dhtml_url_event_map"></a>  END_DHTML_URL_EVENT_MAP —  
 Oznacza koniec mapy zdarzeń DHTML i adres URL.  
  
```  
END_DHTML_URL_EVENT_MAP(className)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *className*  
 Nazwa klasy zawierającej Mapa zdarzeń. Ta klasa powinien pochodzić od bezpośrednio lub pośrednio [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Powinna odpowiadać *className* w odpowiednich [begin_dhtml_url_event_map —](#begin_dhtml_url_event_map) makra.  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [begin_dhtml_url_event_map —](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="end_embed_dhtml_event_map"></a>  END_EMBED_DHTML_EVENT_MAP —  
 Oznacza koniec osadzonych mapy zdarzeń DHTML.  
  
```  
END_EMBED_DHTML_EVENT_MAP()  
 
```  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [begin_dhtml_url_event_map —](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="end_url_entries"></a>  END_URL_ENTRIES —  
 Oznacza koniec wpisu mapy zdarzeń adresu URL.  
  
```  
END_URL_ENTRIES()  
 
```  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [begin_dhtml_url_event_map —](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  
  
##  <a name="url_event_entry"></a>  URL_EVENT_ENTRY —  
 Mapuje zasobu adresu URL lub kod HTML strony w wielostronicowe okna dialogowego.  
  
```  
URL_EVENT_ENTRY(className, url,  mapName)   
```  
  
### <a name="parameters"></a>Parametry  
 *className*  
 Nazwa klasy zawierającej wpisu mapy zdarzeń adresu URL. Ta klasa powinien pochodzić od bezpośrednio lub pośrednio [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Adres URL zdarzenia wpisu mapy musi znajdować się wewnątrz [mapy zdarzeń DHTML i adres URL](#begin_dhtml_url_event_map)).  
  
 *adres URL*  
 Zasób Adres URL lub kod HTML dla strony.  
  
 *mapName*  
 Określa stronę, którego adres URL jest *adres url*. Odpowiada *mapName* w [begin_embed_dhtml_event_map —](#begin_embed_dhtml_event_map) makra, który mapuje zdarzenia z tej strony.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli strona jest zasobem HTML *adres url* musi być reprezentację ciągu identyfikator zasobu (to znaczy "123", nie 123 lub ID_HTMLRES1).  
  
 Identyfikator strony *mapName*, jest symbolem dowolnego używane do łączenia osadzonych mapy zdarzeń DHTML do adresu URL zdarzeń wpisu mapy. Jest ono ograniczone w zakresie do mapy zdarzeń DHTML i adres URL.  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [begin_dhtml_url_event_map —](#begin_dhtml_url_event_map).  

  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdhtml.h  

##  <a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE —
Oznacza koniec mapy zdarzeń DHTML.  
   
### <a name="syntax"></a>Składnia    
```
END_DHTML_EVENT_MAP_INLINE( )    
```  
   
### <a name="remarks"></a>Uwagi  
 Należy używać w połączeniu z [begin_dhtml_event_map_inline —](#begin_dhtml_event_map_inline).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdhtml.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
