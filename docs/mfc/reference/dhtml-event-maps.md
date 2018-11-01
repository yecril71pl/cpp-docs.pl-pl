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
ms.openlocfilehash: 329b4176ad4d24651a41b5321c26318cf2af30e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547202"
---
# <a name="dhtml-event-maps"></a>Mapy zdarzeń DHTML

Następujące makra może służyć do obsługi zdarzeń DHTML.

## <a name="dhtml-event-map-macros"></a>Makra mapy zdarzeń DHTML

Następujące makra może służyć do obsługi zdarzeń DHTML w [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-klas pochodnych.

|||
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|Oznacza początek Mapa zdarzeń DHTML.|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|Oznacza początek Mapa zdarzeń DHTML.|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|Deklaruje Mapa zdarzeń DHTML.|
|[DHTML_EVENT](#dhtml_event)|Używane do obsługi zdarzenia na poziomie dokumentu dla pojedynczego elementu HTML.|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|Używane do obsługi zdarzenia wywoływane przez formant ActiveX.|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|Używane do obsługi zdarzenia na poziomie dokumentu dla wszystkich elementów kodu HTML z określoną klasę CSS.|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|Używane do obsługi zdarzenia na poziomie elementu.|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|Używane do obsługi `onafterupdate` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|Używane do obsługi `onbeforeupdate` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|Używane do obsługi `onblur` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|Używane do obsługi `onchange` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|Używane do obsługi `onclick` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|Używane do obsługi `ondataavailable` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|Używane do obsługi `ondatasetchanged` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|Używane do obsługi `ondatasetcomplete` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|Używane do obsługi `ondblclick` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|Używane do obsługi `ondragstart` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|Używane do obsługi `onerrorupdate` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|Używane do obsługi `onfilterchange` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|Używane do obsługi `onfocus` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|Używane do obsługi `onhelp` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|Używane do obsługi `onkeydown` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|Używane do obsługi `onkeypress` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|Używane do obsługi `onkeyup` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|Używane do obsługi `onmousedown` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|Używane do obsługi `onmousemove` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|Używane do obsługi `onmouseout` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|Używane do obsługi `onmouseover` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|Używane do obsługi `onmouseup` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|Używane do obsługi `onresize` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|Używane do obsługi `onrowenter` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|Używane do obsługi `onrowexit` zdarzeń z elementu HTML.|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|Używane do obsługi `onselectstart` zdarzeń z elementu HTML.|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|Używane do obsługi zdarzenia na poziomie dokumentu dla wszystkich elementów z określonego tagu HTML.|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|Oznacza koniec Mapa zdarzeń DHTML.|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|Oznacza koniec Mapa zdarzeń DHTML. |

## <a name="url-event-map-macros"></a>Makra mapy zdarzeń adresu URL

Następujące makra może służyć do obsługi zdarzeń DHTML w [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-klas pochodnych.

|||
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|Oznacza początek wielostronicowe mapy zdarzeń DHTML i adres URL.|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|Oznacza początek osadzone Mapa zdarzeń DHTML.|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|Oznacza początek wpisu mapy zdarzeń adresu URL.|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|Deklaruje wielostronicowe mapy zdarzeń DHTML i adres URL.|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|Oznacza koniec wielostronicowe mapy zdarzeń DHTML i adres URL.|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|Oznacza koniec osadzone Mapa zdarzeń DHTML.|
|[END_URL_ENTRIES](#end_url_entries)|Oznacza koniec wpisu mapy zdarzeń adresu URL.|
|[URL_EVENT_ENTRY](#url_event_entry)|Mapuje zasób adresu URL lub HTML strony w okno wielostronicowe kolejno.|

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="begin_dhtml_event_map"></a>  BEGIN_DHTML_EVENT_MAP

Oznacza początek Mapa zdarzeń DHTML po umieszczeniu w pliku źródłowym dla klasy identyfikowane przez `className`.

```
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>Parametry

*className*<br/>
Nazwa klasy zawierającej Mapa zdarzeń DHTML. Ta klasa powinna pochodzić bezpośrednio lub pośrednio od [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) i obejmują [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) makra w ramach swojej definicji klasy.

### <a name="remarks"></a>Uwagi

Dodawanie mapy zdarzeń DHTML do swojej klasy, aby zapewnić informacje `CDHtmlDialog` który może służyć do trasy zdarzenia wywoływane przez elementy HTML lub formantów ActiveX na stronie sieci web do obsługi funkcji w klasie.

Umieścić BEGIN_DHTML_EVENT_MAP — makro w klasy implementacji (.cpp) pliku następuje DHTML_EVENT makra dla zdarzeń, które klasa jest do obsługi (na przykład DHTML_EVENT_ONMOUSEOVER mouseover zdarzeń). Użyj [END_DHTML_EVENT_MAP](#end_dhtml_event_map) makra, aby zaznaczyć koniec Mapa zdarzeń. Te makra zaimplementować następującą funkcję:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="begin_dhtml_event_map_inline"></a>  BEGIN_DHTML_EVENT_MAP_INLINE

Oznacza początek Mapa zdarzeń DHTML w ramach definicji klasy dla *className*.

```
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>Parametry

*className*<br/>
Nazwa klasy zawierającej Mapa zdarzeń DHTML. Ta klasa powinna pochodzić bezpośrednio lub pośrednio od [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) i obejmują [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) makra w ramach swojej definicji klasy.

### <a name="remarks"></a>Uwagi

Dodawanie mapy zdarzeń DHTML do swojej klasy, aby zapewnić informacje `CDHtmlDialog` który może służyć do trasy zdarzenia wywoływane przez elementy HTML lub formantów ActiveX na stronie sieci web do obsługi funkcji w klasie.

Umieść BEGIN_DHTML_EVENT_MAP — makro klasy (.h) plik definicji następuje DHTML_EVENT makra dla zdarzeń, które klasa jest do obsługi (na przykład DHTML_EVENT_ONMOUSEOVER mouseover zdarzeń). Użyj [END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline) makra, aby zaznaczyć koniec Mapa zdarzeń. Te makra zaimplementować następującą funkcję:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="declare_dhtml_event_map"></a>  DECLARE_DHTML_EVENT_MAP

Deklaruje mapy zdarzeń DHTML w definicji klasy.

```
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Uwagi

To makro, które ma być używane w definicji [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-klas pochodnych.

Użyj [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) lub [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline) do zaimplementowania mapy.

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) oświadcza, używając następującej funkcji:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event"></a>  DHTML_EVENT

Obsługuje (na poziomie dokumentu) identyfikowany przez zdarzenie *dispid* zainicjowany przez element HTML identyfikowane przez *elemName*.

```
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*identyfikator DISPID*<br/>
Identyfikator DISPID zdarzenia, które mają być obsługiwane.

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń, ani mieć wartości NULL do obsługi zdarzeń dokumentu.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_axcontrol"></a>  DHTML_EVENT_AXCONTROL

Obsługuje zdarzenie identyfikowane przez *dispid* wywoływane przez formant ActiveX, identyfikowane przez *formantu*.

```
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*identyfikator DISPID*<br/>
Identyfikator wysyłania zdarzeń do obsłużenia.

*Nazwa formantu*<br/>
LPCWSTR zawierający identyfikator HTML formantu wyzwoleniem zdarzenia.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_class"></a>  DHTML_EVENT_CLASS

Obsługuje (na poziomie dokumentu) identyfikowany przez zdarzenie *dispid* zainicjowany przez dowolnego elementu HTML przy użyciu klasy CSS, identyfikowane przez *elemName*.

```
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*identyfikator DISPID*<br/>
Identyfikator wysyłania zdarzeń do obsłużenia.

*elemName*<br/>
LPCWSTR zawierający klasę CSS z określania źródła zdarzeń elementów HTML.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_element"></a>  DHTML_EVENT_ELEMENT

Obsługuje (na element identyfikowane przez *elemName*) identyfikowany przez zdarzenie *dispid*.

```
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*identyfikator DISPID*<br/>
Identyfikator wysyłania zdarzeń do obsłużenia.

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

Jeśli to makro jest używane do obsługi zdarzeń nonbubbling, źródło zdarzenia będą element identyfikowane przez *elemName*.

W przypadku to makro jest używane do obsługi zdarzeń propagacji, element identyfikowany przez *elemName* może nie być źródło zdarzenia (źródło może być dowolny element zawarty w *elemName*).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onafterupdate"></a>  DHTML_EVENT_ONAFTERUPDATE

Obsługuje (na poziomie dokumentu) `onafterupdate` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onbeforeupdate"></a>  DHTML_EVENT_ONBEFOREUPDATE

Obsługuje (na poziomie dokumentu) `onbeforeupdate` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onblur"></a>  DHTML_EVENT_ONBLUR

Obsługuje (na poziomie elementu) `onblur` zdarzeń. Jest to nonbubbling zdarzenie.

```
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onchange"></a>  DHTML_EVENT_ONCHANGE

Obsługuje (na poziomie elementu) `onchange` zdarzeń. Jest to nonbubbling zdarzenie.

```
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onclick"></a>  DHTML_EVENT_ONCLICK

Obsługuje (na poziomie dokumentu) `onclick` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_ondataavailable"></a>  DHTML_EVENT_ONDATAAVAILABLE

Obsługuje (na poziomie dokumentu) `ondataavailable` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_ondatasetchanged"></a>  DHTML_EVENT_ONDATASETCHANGED

Obsługuje (na poziomie dokumentu) `ondatasetchanged` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_ondatasetcomplete"></a>  DHTML_EVENT_ONDATASETCOMPLETE

Obsługuje (na poziomie dokumentu) `ondatasetcomplete` pochodzi zdarzenie przez element HTML identyfikowane przez `elemName`.

```
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_ondblclick"></a>  DHTML_EVENT_ONDBLCLICK

Obsługuje (na poziomie dokumentu) `ondblclick` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_ondragstart"></a>  DHTML_EVENT_ONDRAGSTART

Obsługuje (na poziomie dokumentu) `ondragstart` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onerrorupdate"></a>  DHTML_EVENT_ONERRORUPDATE

Obsługuje (na poziomie dokumentu) `onerrorupdate` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onfilterchange"></a>  DHTML_EVENT_ONFILTERCHANGE

Obsługuje (na poziomie dokumentu) `onfilterchange` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```

DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onfocus"></a>  DHTML_EVENT_ONFOCUS

Obsługuje (na poziomie elementu) `onfocus` zdarzeń. Jest to nonbubbling zdarzenie.

```

DHTML_EVENT_ONFOCUS(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onhelp"></a>  DHTML_EVENT_ONHELP

Obsługuje (na poziomie dokumentu) `onhelp` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```

DHTML_EVENT_ONHELP(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onkeydown"></a>  DHTML_EVENT_ONKEYDOWN

Obsługuje (na poziomie dokumentu) `onkeydown` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```

DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onkeypress"></a>  DHTML_EVENT_ONKEYPRESS

Obsługuje (na poziomie dokumentu) `onkeypress` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```

DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onkeyup"></a>  DHTML_EVENT_ONKEYUP

Obsługuje (na poziomie dokumentu) `onkeyup` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```

DHTML_EVENT_ONKEYUP(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onmousedown"></a>  DHTML_EVENT_ONMOUSEDOWN

Obsługuje (na poziomie dokumentu) `onmousedown` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```

DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onmousemove"></a>  DHTML_EVENT_ONMOUSEMOVE

Obsługuje (na poziomie dokumentu) `onmousemove` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```

DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onmouseout"></a>  DHTML_EVENT_ONMOUSEOUT

Obsługuje (na poziomie dokumentu) `onmouseout` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```

DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onmouseover"></a>  DHTML_EVENT_ONMOUSEOVER

Obsługuje (na poziomie dokumentu) `onmouseover` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```

DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onmouseup"></a>  DHTML_EVENT_ONMOUSEUP

Obsługuje (na poziomie dokumentu) `onmouseup` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```

DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onresize"></a>  DHTML_EVENT_ONRESIZE

Obsługuje (na poziomie elementu) `onresize` zdarzeń. Jest to nonbubbling zdarzenie.

```

DHTML_EVENT_ONRESIZE(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onrowenter"></a>  DHTML_EVENT_ONROWENTER

Obsługuje (na poziomie dokumentu) `onrowenter` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```

DHTML_EVENT_ONROWENTER(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onrowexit"></a>  DHTML_EVENT_ONROWEXIT

Obsługuje (na poziomie dokumentu) `onrowexit` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```

DHTML_EVENT_ONROWEXIT(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_onselectstart"></a>  DHTML_EVENT_ONSELECTSTART

Obsługuje (na poziomie dokumentu) `onselectstart` pochodzi zdarzenie przez element HTML identyfikowane przez *elemName*.

```

DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR zawierający identyfikator elementu HTML określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="dhtml_event_tag"></a>  DHTML_EVENT_TAG

Obsługuje (na poziomie dokumentu) identyfikowany przez zdarzenie `dispid` zainicjowany przez dowolnego elementu HTML przy użyciu tagu HTML identyfikowane przez *elemName*.

```
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*identyfikator DISPID*<br/>
Identyfikator wysyłania zdarzeń do obsłużenia.

*elemName*<br/>
Tag HTML elementów kodu HTML, określania źródła zdarzeń.

*memberFxn*<br/>
Funkcja obsługi zdarzenia.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby dodać wpis do [Mapa zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="end_dhtml_event_map"></a>  END_DHTML_EVENT_MAP

Oznacza koniec Mapa zdarzeń DHTML.

```
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Uwagi

Należy używać w połączeniu z [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="begin_dhtml_url_event_map"></a>  BEGIN_DHTML_URL_EVENT_MAP

Uruchamia definicji mapy zdarzeń DHTML i adres URL w okno wielostronicowe kolejno.

```
BEGIN_DHTML_URL_EVENT_MAP()

```

### <a name="remarks"></a>Uwagi

Umieść BEGIN_DHTML_URL_EVENT_MAP w pliku implementacji usługi [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-klasy pochodnej. Postępuj zgodnie z [osadzone mapy zdarzeń DHTML](#begin_embed_dhtml_event_map) i [adresu URL wpisy](#begin_url_entries), a następnie zamknij go za pomocą [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map). Obejmują [DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) makra w ramach definicji klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="begin_embed_dhtml_event_map"></a>  BEGIN_EMBED_DHTML_EVENT_MAP

Uruchamia definicji osadzone mapy zdarzeń DHTML w okno wielostronicowe kolejno.

```
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)

```

### <a name="parameters"></a>Parametry

*className*<br/>
Nazwa klasy zawierającej Mapa zdarzeń. Ta klasa powinna pochodzić bezpośrednio lub pośrednio od [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Osadzony Mapa zdarzeń DHTML musi znajdować się wewnątrz [mapy zdarzeń DHTML i adres URL](#begin_dhtml_url_event_map)).

*mapName*<br/>
Określa, że strona, do którego zdarzenie Mapuj jest. Odpowiada to *mapName* w [URL_EVENT_ENTRY](#url_event_entry) — makro faktycznie Definiowanie zasobów adresu URL lub HTML.

### <a name="remarks"></a>Uwagi

Ponieważ okno wielostronicowe kolejno DHTML obejmuje wiele stron HTML, z których każdy może wywoływać zdarzenia DHTML, mapy osadzone zdarzeń są używane do mapowania zdarzeń z programami obsługi na podstawie na stronie.

Mapy zdarzeń osadzone wewnątrz mapy zdarzeń DHTML i adresu URL składają się z BEGIN_EMBED_DHTML_EVENT_MAP — makro, a następnie [DHTML_EVENT](#dhtml_event) makr i [END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map) makra.

Każdego Mapa osadzone zdarzeń wymaga odpowiednią [wpis dotyczący zdarzenia adresu URL](#url_event_entry) do mapowania *mapName* (określony w BEGIN_EMBED_DHTML_EVENT_MAP) do zasobu adresu URL lub HTML.

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="begin_url_entries"></a>  BEGIN_URL_ENTRIES

Uruchamia definicji mapy zapis zdarzenia adresu URL w okno wielostronicowe kolejno.

```
BEGIN_URL_ENTRIES(className)

```

### <a name="parameters"></a>Parametry

*className*<br/>
Nazwa klasy zawierającej adres URL zdarzenia wpis mapy. Ta klasa powinna pochodzić bezpośrednio lub pośrednio od [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Adres URL zdarzenia wpis mapy musi znajdować się wewnątrz [mapy zdarzeń DHTML i adres URL](#begin_dhtml_url_event_map)).

### <a name="remarks"></a>Uwagi

Ponieważ okno wielostronicowe kolejno DHTML zawiera wiele stron HTML, adres URL zdarzenia wpisy są używane do mapowania adresów URL lub HTML zasobów do odpowiadającego [osadzone mapy zdarzeń DHTML](#begin_embed_dhtml_event_map). Umieść makra URL_EVENT_ENTRY między BEGIN_URL_ENTRIES i [END_URL_ENTRIES](#end_url_entries) makra.

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="declare_dhtml_url_event_map"></a>  DECLARE_DHTML_URL_EVENT_MAP

Deklaruje mapy zdarzeń DHTML i adres URL w definicji klasy.

```
DECLARE_DHTML_URL_EVENT_MAP()

```

### <a name="remarks"></a>Uwagi

To makro, które ma być używane w definicji [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-klas pochodnych.

Mapa zdarzeń DHTML i adres URL zawiera [osadzone mapy zdarzeń DHTML](#begin_embed_dhtml_event_map) i [adresu URL wpisy zdarzeń](#begin_url_entries) do mapy zdarzeń DHTML do obsługi na podstawie poszczególnych stron. Użyj [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) do zaimplementowania mapy.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="end_dhtml_url_event_map"></a>  END_DHTML_URL_EVENT_MAP

Oznacza koniec mapy zdarzeń DHTML i adres URL.

```
END_DHTML_URL_EVENT_MAP(className)

```

### <a name="parameters"></a>Parametry

*className*<br/>
Nazwa klasy zawierającej Mapa zdarzeń. Ta klasa powinna pochodzić bezpośrednio lub pośrednio od [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Powinien on odpowiadać *className* w odpowiednich [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) makra.

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="end_embed_dhtml_event_map"></a>  END_EMBED_DHTML_EVENT_MAP

Oznacza koniec osadzone Mapa zdarzeń DHTML.

```
END_EMBED_DHTML_EVENT_MAP()

```

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="end_url_entries"></a>  END_URL_ENTRIES

Oznacza koniec wpisu mapy zdarzeń adresu URL.

```
END_URL_ENTRIES()

```

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="url_event_entry"></a>  URL_EVENT_ENTRY

Mapuje zasób adresu URL lub HTML strony w okno wielostronicowe kolejno.

```
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>Parametry

*className*<br/>
Nazwa klasy zawierającej adres URL zdarzenia wpis mapy. Ta klasa powinna pochodzić bezpośrednio lub pośrednio od [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Adres URL zdarzenia wpis mapy musi znajdować się wewnątrz [mapy zdarzeń DHTML i adres URL](#begin_dhtml_url_event_map)).

*adres URL*<br/>
Zasób adresu URL lub kod HTML dla strony.

*mapName*<br/>
Określa stronę o adresie URL *adresu url*. Odpowiada to *mapName* w [BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map) makro, które mapuje zdarzenia na tej stronie.

### <a name="remarks"></a>Uwagi

Jeśli strona jest zasobem HTML *adresu url* musi być ciąg reprezentujący numer Identyfikatora zasobu (czyli "123" 123 nie lub ID_HTMLRES1).

Identyfikator strony *mapName*, jest dowolny symbol używane do łączenia osadzonych mapy zdarzeń DHTML do mapy zapis zdarzenia adresów URL. Jest ograniczony zakres do mapy zdarzeń DHTML i adres URL.

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

##  <a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE

Oznacza koniec Mapa zdarzeń DHTML.

### <a name="syntax"></a>Składnia

```
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>Uwagi

Należy używać w połączeniu z [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdhtml.h

### <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](mfc-macros-and-globals.md)
