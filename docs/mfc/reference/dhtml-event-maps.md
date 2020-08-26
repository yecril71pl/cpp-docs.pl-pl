---
title: Mapy zdarzeń DHTML
ms.date: 11/04/2016
f1_keywords:
- vc.macros.shared
helpviewer_keywords:
- event map macros [MFC]
- DHTML [MFC], event map macros
- macros [MFC], DHTML event map
- DHTML events [MFC], event map
- DHTML events [MFC]
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
ms.openlocfilehash: 099a08298357d99a3d09ed6fc1209d463f6a4526
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837427"
---
# <a name="dhtml-event-maps"></a>Mapy zdarzeń DHTML

Poniższe makra mogą służyć do obsługi zdarzeń w języku DHTML.

## <a name="dhtml-event-map-macros"></a>Makra mapy zdarzeń DHTML

Następujące makra mogą służyć do obsługi zdarzeń DHTML w klasach pochodnych [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md).

|Nazwa|Opis|
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|Oznacza początek mapy zdarzeń DHTML.|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|Oznacza początek mapy zdarzeń DHTML.|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|Deklaruje mapę zdarzeń DHTML.|
|[DHTML_EVENT](#dhtml_event)|Służy do obsługi zdarzenia na poziomie dokumentu dla pojedynczego elementu HTML.|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|Służy do obsługi zdarzenia wyzwalanego przez kontrolkę ActiveX.|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|Służy do obsługi zdarzenia na poziomie dokumentu dla wszystkich elementów HTML z określoną klasą CSS.|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|Używane do obsługi zdarzenia na poziomie elementu.|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|Używane do obsługi `onafterupdate` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|Używane do obsługi `onbeforeupdate` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|Używane do obsługi `onblur` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|Używane do obsługi `onchange` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|Używane do obsługi `onclick` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|Używane do obsługi `ondataavailable` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|Używane do obsługi `ondatasetchanged` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|Używane do obsługi `ondatasetcomplete` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|Używane do obsługi `ondblclick` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|Używane do obsługi `ondragstart` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|Używane do obsługi `onerrorupdate` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|Używane do obsługi `onfilterchange` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|Używane do obsługi `onfocus` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|Używane do obsługi `onhelp` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|Używane do obsługi `onkeydown` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|Używane do obsługi `onkeypress` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|Używane do obsługi `onkeyup` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|Używane do obsługi `onmousedown` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|Używane do obsługi `onmousemove` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|Używane do obsługi `onmouseout` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|Używane do obsługi `onmouseover` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|Używane do obsługi `onmouseup` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|Używane do obsługi `onresize` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|Używane do obsługi `onrowenter` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|Używane do obsługi `onrowexit` zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|Używane do obsługi `onselectstart` zdarzenia z elementu HTML.|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|Służy do obsługi zdarzenia na poziomie dokumentu dla wszystkich elementów z określonym tagiem HTML.|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|Oznacza koniec mapy zdarzeń DHTML.|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|Oznacza koniec mapy zdarzeń DHTML. |

## <a name="url-event-map-macros"></a>Makra mapy zdarzeń URL

Następujące makra mogą służyć do obsługi zdarzeń DHTML w klasach pochodnych [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md).

|Nazwa|Opis|
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|Oznacza początek wielostronicowej mapy zdarzeń w formacie DHTML i adresem URL.|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|Oznacza początek osadzonej mapy zdarzeń DHTML.|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|Oznacza początek mapy wpisów zdarzeń adresu URL.|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|Deklaruje wielostronicową mapę zdarzeń w formacie DHTML i adresem URL.|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|Oznacza koniec wielostronicowej mapy zdarzeń w formacie DHTML i adresów URL.|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|Oznacza koniec osadzonej mapy zdarzeń DHTML.|
|[END_URL_ENTRIES](#end_url_entries)|Oznacza koniec mapy wpisów zdarzeń adresu URL.|
|[URL_EVENT_ENTRY](#url_event_entry)|Mapuje adres URL lub zasób HTML na stronę w oknie dialogowym wielostronicowym.|

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="begin_dhtml_event_map"></a><a name="begin_dhtml_event_map"></a> BEGIN_DHTML_EVENT_MAP

Oznacza początek mapy zdarzeń DHTML, gdy zostanie umieszczony w pliku źródłowym dla klasy identyfikowanej przez `className` .

```cpp
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>Parametry

*Nazwą*<br/>
Nazwa klasy zawierającej mapę zdarzeń DHTML. Ta klasa powinna dziedziczyć bezpośrednio lub pośrednio z [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) i zawierać makro [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) w ramach definicji klasy.

### <a name="remarks"></a>Uwagi

Dodaj mapę zdarzeń DHTML do klasy, aby podać informacje `CDHtmlDialog` , które mogą być używane do kierowania zdarzeń wyzwalanych przez elementy HTML lub kontrolki ActiveX na stronie sieci Web w celu obsługi funkcji w klasie.

Umieść makro BEGIN_DHTML_EVENT_MAP w pliku implementacji klasy (CPP), a następnie DHTML_EVENT makra dla zdarzeń, które Klasa ma obsłużyć (na przykład DHTML_EVENT_ONMOUSEOVER dla zdarzeń MouseOver). Użyj makra [END_DHTML_EVENT_MAP](#end_dhtml_event_map) , aby oznaczyć koniec mapy zdarzeń. Te makra implementują następującą funkcję:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="begin_dhtml_event_map_inline"></a><a name="begin_dhtml_event_map_inline"></a> BEGIN_DHTML_EVENT_MAP_INLINE

Oznacza początek mapy zdarzeń DHTML w definicji klasy dla *ClassName*.

```cpp
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>Parametry

*Nazwą*<br/>
Nazwa klasy zawierającej mapę zdarzeń DHTML. Ta klasa powinna dziedziczyć bezpośrednio lub pośrednio z [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) i zawierać makro [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) w ramach definicji klasy.

### <a name="remarks"></a>Uwagi

Dodaj mapę zdarzeń DHTML do klasy, aby podać informacje `CDHtmlDialog` , które mogą być używane do kierowania zdarzeń wyzwalanych przez elementy HTML lub kontrolki ActiveX na stronie sieci Web w celu obsługi funkcji w klasie.

Umieść makro BEGIN_DHTML_EVENT_MAP w pliku definicji klasy (h), a następnie DHTML_EVENT makra dla zdarzeń, które Klasa ma obsłużyć (na przykład DHTML_EVENT_ONMOUSEOVER dla zdarzeń MouseOver). Użyj makra [END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline) , aby oznaczyć koniec mapy zdarzeń. Te makra implementują następującą funkcję:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="declare_dhtml_event_map"></a><a name="declare_dhtml_event_map"></a> DECLARE_DHTML_EVENT_MAP

Deklaruje mapę zdarzeń DHTML w definicji klasy.

```cpp
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Uwagi

To makro jest używane w definicji klas pochodnych [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md).

Aby zaimplementować mapę, użyj [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) lub [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline) .

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) deklaruje następującą funkcję:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event"></a><a name="dhtml_event"></a> DHTML_EVENT

Uchwyty (na poziomie dokumentu) zdarzenie identyfikowane przez identyfikator *DISPID* pochodzący z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*DISPID*<br/>
Identyfikator DISPID zdarzenia do obsługi.

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie, lub wartość NULL, aby obsłużyć zdarzenia dokumentu.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_axcontrol"></a><a name="dhtml_event_axcontrol"></a> DHTML_EVENT_AXCONTROL

Obsługuje zdarzenie identyfikowane przez identyfikator *DISPID* uruchamiany przez kontrolkę ActiveX identyfikowaną przez *ControlName*.

```cpp
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*DISPID*<br/>
Identyfikator wysyłania zdarzenia.

*formantname*<br/>
LPCWSTR przechowujący identyfikator HTML kontrolki, która wyzwala zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_class"></a><a name="dhtml_event_class"></a> DHTML_EVENT_CLASS

Uchwyty (na poziomie dokumentu) zdarzenie identyfikowane przez identyfikator *DISPID* pochodzący z dowolnego elementu HTML z klasą CSS identyfikowaną przez *elemName*.

```cpp
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*DISPID*<br/>
Identyfikator wysyłania zdarzenia.

*elemName*<br/>
LPCWSTR przechowujący klasę CSS elementów HTML, które są źródłem zdarzenia.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_element"></a><a name="dhtml_event_element"></a> DHTML_EVENT_ELEMENT

Uchwyty (dla elementu identyfikowanego przez *elemName*) zdarzenie identyfikowane przez *DISPID*.

```cpp
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*DISPID*<br/>
Identyfikator wysyłania zdarzenia.

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

Jeśli to makro jest używane do obsługi zdarzeń niepropagacji, źródłem zdarzenia będzie element identyfikowany przez *elemName*.

Jeśli to makro jest używane do obsługi zdarzeń propagacji, element identyfikowany przez *elemName* może nie być źródłem zdarzenia (źródłem może być każdy element zawarty w *elemName*).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onafterupdate"></a><a name="dhtml_event_onafterupdate"></a> DHTML_EVENT_ONAFTERUPDATE

Uchwyty (na poziomie dokumentu) `onafterupdate` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a> DHTML_EVENT_ONBEFOREUPDATE

Uchwyty (na poziomie dokumentu) `onbeforeupdate` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onblur"></a><a name="dhtml_event_onblur"></a> DHTML_EVENT_ONBLUR

Uchwyty (na poziomie elementu) `onblur` zdarzenia. To jest zdarzenie niepropagacji.

```cpp
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onchange"></a><a name="dhtml_event_onchange"></a> DHTML_EVENT_ONCHANGE

Uchwyty (na poziomie elementu) `onchange` zdarzenia. To jest zdarzenie niepropagacji.

```cpp
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onclick"></a><a name="dhtml_event_onclick"></a> DHTML_EVENT_ONCLICK

Uchwyty (na poziomie dokumentu) `onclick` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_ondataavailable"></a><a name="dhtml_event_ondataavailable"></a> DHTML_EVENT_ONDATAAVAILABLE

Uchwyty (na poziomie dokumentu) `ondataavailable` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_ondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a> DHTML_EVENT_ONDATASETCHANGED

Uchwyty (na poziomie dokumentu) `ondatasetchanged` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_ondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a> DHTML_EVENT_ONDATASETCOMPLETE

Uchwyty (na poziomie dokumentu) `ondatasetcomplete` zdarzenie pochodzące z elementu HTML identyfikowanego przez `elemName` .

```cpp
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_ondblclick"></a><a name="dhtml_event_ondblclick"></a> DHTML_EVENT_ONDBLCLICK

Uchwyty (na poziomie dokumentu) `ondblclick` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_ondragstart"></a><a name="dhtml_event_ondragstart"></a> DHTML_EVENT_ONDRAGSTART

Uchwyty (na poziomie dokumentu) `ondragstart` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a> DHTML_EVENT_ONERRORUPDATE

Uchwyty (na poziomie dokumentu) `onerrorupdate` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onfilterchange"></a><a name="dhtml_event_onfilterchange"></a> DHTML_EVENT_ONFILTERCHANGE

Uchwyty (na poziomie dokumentu) `onfilterchange` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onfocus"></a><a name="dhtml_event_onfocus"></a> DHTML_EVENT_ONFOCUS

Uchwyty (na poziomie elementu) `onfocus` zdarzenia. To jest zdarzenie niepropagacji.

```cpp
DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onhelp"></a><a name="dhtml_event_onhelp"></a> DHTML_EVENT_ONHELP

Uchwyty (na poziomie dokumentu) `onhelp` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onkeydown"></a><a name="dhtml_event_onkeydown"></a> DHTML_EVENT_ONKEYDOWN

Uchwyty (na poziomie dokumentu) `onkeydown` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onkeypress"></a><a name="dhtml_event_onkeypress"></a> DHTML_EVENT_ONKEYPRESS

Uchwyty (na poziomie dokumentu) `onkeypress` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onkeyup"></a><a name="dhtml_event_onkeyup"></a> DHTML_EVENT_ONKEYUP

Uchwyty (na poziomie dokumentu) `onkeyup` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onmousedown"></a><a name="dhtml_event_onmousedown"></a> DHTML_EVENT_ONMOUSEDOWN

Uchwyty (na poziomie dokumentu) `onmousedown` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onmousemove"></a><a name="dhtml_event_onmousemove"></a> DHTML_EVENT_ONMOUSEMOVE

Uchwyty (na poziomie dokumentu) `onmousemove` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onmouseout"></a><a name="dhtml_event_onmouseout"></a> DHTML_EVENT_ONMOUSEOUT

Uchwyty (na poziomie dokumentu) `onmouseout` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onmouseover"></a><a name="dhtml_event_onmouseover"></a> DHTML_EVENT_ONMOUSEOVER

Uchwyty (na poziomie dokumentu) `onmouseover` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onmouseup"></a><a name="dhtml_event_onmouseup"></a> DHTML_EVENT_ONMOUSEUP

Uchwyty (na poziomie dokumentu) `onmouseup` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onresize"></a><a name="dhtml_event_onresize"></a> DHTML_EVENT_ONRESIZE

Uchwyty (na poziomie elementu) `onresize` zdarzenia. To jest zdarzenie niepropagacji.

```cpp
DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onrowenter"></a><a name="dhtml_event_onrowenter"></a> DHTML_EVENT_ONROWENTER

Uchwyty (na poziomie dokumentu) `onrowenter` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onrowexit"></a><a name="dhtml_event_onrowexit"></a> DHTML_EVENT_ONROWEXIT

Uchwyty (na poziomie dokumentu) `onrowexit` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_onselectstart"></a><a name="dhtml_event_onselectstart"></a> DHTML_EVENT_ONSELECTSTART

Uchwyty (na poziomie dokumentu) `onselectstart` zdarzenie pochodzące z elementu HTML identyfikowanego przez *elemName*.

```cpp
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR przechowujący identyfikator elementu HTML, który pozyskuje zdarzenie.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="dhtml_event_tag"></a><a name="dhtml_event_tag"></a> DHTML_EVENT_TAG

Uchwyty (na poziomie dokumentu) zdarzenie identyfikowane przez `dispid` element HTML z TAGIEM HTML identyfikowanym przez *elemName*.

```cpp
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*DISPID*<br/>
Identyfikator wysyłania zdarzenia.

*elemName*<br/>
Tag HTML elementów HTML, które są źródłem zdarzenia.

*memberFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="end_dhtml_event_map"></a><a name="end_dhtml_event_map"></a> END_DHTML_EVENT_MAP

Oznacza koniec mapy zdarzeń DHTML.

```cpp
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Uwagi

Musi być używany w połączeniu z [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="begin_dhtml_url_event_map"></a><a name="begin_dhtml_url_event_map"></a> BEGIN_DHTML_URL_EVENT_MAP

Uruchamia definicję mapy zdarzeń DHTML i URL w oknie dialogowym wielostronicowym.

```cpp
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Uwagi

Umieść BEGIN_DHTML_URL_EVENT_MAP w pliku implementacji klasy pochodnej [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Postępuj zgodnie z [osadzonymi mapami zdarzeń DHTML](#begin_embed_dhtml_event_map) i [wpisami URL](#begin_url_entries), a następnie zamknij je za pomocą [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map). Uwzględnij [DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) makro w definicji klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="begin_embed_dhtml_event_map"></a><a name="begin_embed_dhtml_event_map"></a> BEGIN_EMBED_DHTML_EVENT_MAP

Uruchamia definicję osadzonej mapy zdarzeń DHTML w oknie dialogowym wielostronicowym.

```cpp
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>Parametry

*Nazwą*<br/>
Nazwa klasy zawierającej mapę zdarzeń. Ta klasa powinna dziedziczyć bezpośrednio lub pośrednio z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Osadzona Mapa zdarzeń DHTML musi znajdować się wewnątrz [mapy zdarzeń w formacie DHTML i adresów URL](#begin_dhtml_url_event_map).

*mapName*<br/>
Określa stronę, której mapuje zdarzenia. Jest to zgodne z *mapName* w makrze [URL_EVENT_ENTRY](#url_event_entry) faktycznie definiującym adres URL lub zasób html.

### <a name="remarks"></a>Uwagi

Ponieważ wielostronicowe okno języka DHTML składa się z wielu stron HTML, z których każdy może wywoływać zdarzenia języka DHTML, osadzone mapy zdarzeń są używane do mapowania zdarzeń do obsługi dla poszczególnych stron.

Osadzone mapy zdarzeń w ramach mapy zdarzeń DHTML i adresów URL składają się z makra BEGIN_EMBED_DHTML_EVENT_MAP, po którym następują makra [DHTML_EVENT](#dhtml_event) i makro [END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map) .

Każda osadzona Mapa zdarzeń wymaga wpisu zdarzenia dotyczącego odpowiedniego [adresu URL](#url_event_entry) do mapowania *mapName* (określony w BEGIN_EMBED_DHTML_EVENT_MAP) na adres URL lub zasób html.

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="begin_url_entries"></a><a name="begin_url_entries"></a> BEGIN_URL_ENTRIES

Uruchamia definicję mapy wpisów zdarzeń adresu URL w oknie dialogowym wielostronicowym.

```cpp
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>Parametry

*Nazwą*<br/>
Nazwa klasy zawierającej mapowanie wpisu zdarzenia adresu URL. Ta klasa powinna dziedziczyć bezpośrednio lub pośrednio z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Mapa wpisów zdarzeń adresu URL musi znajdować się wewnątrz [mapy zdarzeń w formacie DHTML i adresów URL](#begin_dhtml_url_event_map).

### <a name="remarks"></a>Uwagi

Ponieważ wielostronicowe okno języka DHTML składa się z wielu stron HTML, wpisy zdarzeń URL są używane do mapowania adresów URL lub zasobów HTML na odpowiednie [osadzone mapy zdarzeń DHTML](#begin_embed_dhtml_event_map). Umieść URL_EVENT_ENTRY makra między makrami BEGIN_URL_ENTRIES i [END_URL_ENTRIES](#end_url_entries) .

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="declare_dhtml_url_event_map"></a><a name="declare_dhtml_url_event_map"></a> DECLARE_DHTML_URL_EVENT_MAP

Deklaruje mapę zdarzeń DHTML i URL w definicji klasy.

```cpp
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Uwagi

To makro jest używane w definicji klas pochodnych [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md).

Mapa zdarzeń DHTML i URL zawiera [osadzone mapy zdarzeń DHTML](#begin_embed_dhtml_event_map) i [wpisy zdarzeń adresów URL](#begin_url_entries) , które umożliwiają mapowanie zdarzeń w formacie DHTML na poszczególne strony. Użyj [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) , aby zaimplementować mapę.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="end_dhtml_url_event_map"></a><a name="end_dhtml_url_event_map"></a> END_DHTML_URL_EVENT_MAP

Oznacza koniec mapy zdarzeń w formacie DHTML i adresów URL.

```cpp
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>Parametry

*Nazwą*<br/>
Nazwa klasy zawierającej mapę zdarzeń. Ta klasa powinna dziedziczyć bezpośrednio lub pośrednio z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Ta wartość powinna być zgodna z *nazwą klasy* w odpowiednim makrze [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) .

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="end_embed_dhtml_event_map"></a><a name="end_embed_dhtml_event_map"></a> END_EMBED_DHTML_EVENT_MAP

Oznacza koniec osadzonej mapy zdarzeń DHTML.

```cpp
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="end_url_entries"></a><a name="end_url_entries"></a> END_URL_ENTRIES

Oznacza koniec mapy wpisów zdarzeń adresu URL.

```cpp
END_URL_ENTRIES()
```

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="url_event_entry"></a><a name="url_event_entry"></a> URL_EVENT_ENTRY

Mapuje adres URL lub zasób HTML na stronę w oknie dialogowym wielostronicowym.

```cpp
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>Parametry

*Nazwą*<br/>
Nazwa klasy zawierającej mapowanie wpisu zdarzenia adresu URL. Ta klasa powinna dziedziczyć bezpośrednio lub pośrednio z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Mapa wpisów zdarzeń adresu URL musi znajdować się wewnątrz [mapy zdarzeń w formacie DHTML i adresów URL](#begin_dhtml_url_event_map).

*adres URL*<br/>
Adres URL lub zasób HTML dla strony.

*mapName*<br/>
Określa stronę, której adres URL jest *adresem URL*. Jest to zgodne z *mapName* w makrze [BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map) , które mapują zdarzenia z tej strony.

### <a name="remarks"></a>Uwagi

Jeśli strona jest zasobem HTML, *adres URL* musi być reprezentacją ciągu o numerze ID zasobu (czyli "123", a nie 123 lub ID_HTMLRES1).

Identyfikator strony, *mapName*, jest dowolnym symbolem służącym do łączenia osadzonych map zdarzeń DHTML z mapowaniami wpisów zdarzeń adresów URL. Jest ona ograniczona do zakresu dla mapy zdarzeń DHTML i adresów URL.

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml. h

## <a name="end_dhtml_event_map_inline"></a><a name="end_dhtml_event_map_inline"></a> END_DHTML_EVENT_MAP_INLINE

Oznacza koniec mapy zdarzeń DHTML.

### <a name="syntax"></a>Składnia

```cpp
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>Uwagi

Musi być używany w połączeniu z [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdhtml. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](mfc-macros-and-globals.md)
