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
ms.openlocfilehash: 30c755b2901374cffab3ce91d0683811ef6624b6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365808"
---
# <a name="dhtml-event-maps"></a>Mapy zdarzeń DHTML

Do obsługi zdarzeń DHTML można używać następujących makr.

## <a name="dhtml-event-map-macros"></a>Makra mapy zdarzeń DHTML

Następujące makra mogą być używane do obsługi zdarzeń DHTML w klasach pochodnych [CDHtmlDialog.](../../mfc/reference/cdhtmldialog-class.md)

|||
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|Oznacza początek mapy zdarzeń DHTML.|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|Oznacza początek mapy zdarzeń DHTML.|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|Deklaruje mapę zdarzeń DHTML.|
|[DHTML_EVENT](#dhtml_event)|Służy do obsługi zdarzenia na poziomie dokumentu dla pojedynczego elementu HTML.|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|Służy do obsługi zdarzenia uruchamianego przez formant ActiveX.|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|Służy do obsługi zdarzenia na poziomie dokumentu dla wszystkich elementów HTML z określoną klasą CSS.|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|Służy do obsługi zdarzenia na poziomie elementu.|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|Służy do `onafterupdate` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|Służy do `onbeforeupdate` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|Służy do `onblur` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|Służy do `onchange` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|Służy do `onclick` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|Służy do `ondataavailable` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|Służy do `ondatasetchanged` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|Służy do `ondatasetcomplete` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|Służy do `ondblclick` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|Służy do `ondragstart` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|Służy do `onerrorupdate` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|Służy do `onfilterchange` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|Służy do `onfocus` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|Służy do `onhelp` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|Służy do `onkeydown` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|Służy do `onkeypress` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|Służy do `onkeyup` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|Służy do `onmousedown` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|Służy do `onmousemove` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|Służy do `onmouseout` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|Służy do `onmouseover` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|Służy do `onmouseup` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|Służy do `onresize` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|Służy do `onrowenter` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|Służy do `onrowexit` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|Służy do `onselectstart` obsługi zdarzenia z elementu HTML.|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|Służy do obsługi zdarzenia na poziomie dokumentu dla wszystkich elementów z określonym tagiem HTML.|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|Oznacza koniec mapy zdarzeń DHTML.|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|Oznacza koniec mapy zdarzeń DHTML. |

## <a name="url-event-map-macros"></a>Makra mapy zdarzeń url

Następujące makra mogą być używane do obsługi zdarzeń DHTML w klasach pochodnych [CMultiPageDHtmlDialog.](../../mfc/reference/cmultipagedhtmldialog-class.md)

|||
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|Oznacza początek wielostronicowej mapy zdarzeń DHTML i adresu URL.|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|Oznacza początek osadzonej mapy zdarzeń DHTML.|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|Oznacza początek mapy wpisu zdarzenia adresu URL.|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|Deklaruje wielostronicową mapę zdarzeń DHTML i URL.|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|Oznacza koniec wielostronicowej mapy zdarzeń DHTML i adresu URL.|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|Oznacza koniec osadzonej mapy zdarzeń DHTML.|
|[END_URL_ENTRIES](#end_url_entries)|Oznacza koniec mapy wpisu zdarzenia adresu URL.|
|[URL_EVENT_ENTRY](#url_event_entry)|Mapuje adres URL lub zasób HTML na stronę w wielostronicowym oknie dialogowym.|

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="begin_dhtml_event_map"></a><a name="begin_dhtml_event_map"></a>BEGIN_DHTML_EVENT_MAP

Oznacza początek mapy zdarzeń DHTML po umieszczeniu w pliku źródłowym dla klasy identyfikowanej przez `className`program .

```cpp
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Nazwa klasy zawierającej mapę zdarzeń DHTML. Ta klasa powinna pochodzić bezpośrednio lub pośrednio z [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) i zawierać [makro DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) w jego definicji klasy.

### <a name="remarks"></a>Uwagi

Dodaj mapę zdarzeń DHTML do klasy, aby `CDHtmlDialog` zapewnić informacje, które mogą służyć do kierowania zdarzeń uruchamianych przez elementy HTML lub formanty ActiveX na stronie sieci web do funkcji obsługi w klasie.

Umieść makro BEGIN_DHTML_EVENT_MAP w pliku implementacji klasy (.cpp), a następnie DHTML_EVENT makra dla zdarzeń, które klasa ma obsłużyć (na przykład DHTML_EVENT_ONMOUSEOVER zdarzeń najechaniu myszą). Użyj [makra END_DHTML_EVENT_MAP,](#end_dhtml_event_map) aby oznaczyć koniec mapy zdarzeń. Te makra implementują następującą funkcję:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="begin_dhtml_event_map_inline"></a><a name="begin_dhtml_event_map_inline"></a>BEGIN_DHTML_EVENT_MAP_INLINE

Oznacza początek mapy zdarzeń DHTML w definicji klasy dla *className*.

```cpp
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Nazwa klasy zawierającej mapę zdarzeń DHTML. Ta klasa powinna pochodzić bezpośrednio lub pośrednio z [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) i zawierać [makro DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) w jego definicji klasy.

### <a name="remarks"></a>Uwagi

Dodaj mapę zdarzeń DHTML do klasy, aby `CDHtmlDialog` zapewnić informacje, które mogą służyć do kierowania zdarzeń uruchamianych przez elementy HTML lub formanty ActiveX na stronie sieci web do funkcji obsługi w klasie.

Umieść makro BEGIN_DHTML_EVENT_MAP w pliku definicji klasy (.h), po którym następuje DHTML_EVENT makra dla zdarzeń, które klasa ma obsłużyć (na przykład DHTML_EVENT_ONMOUSEOVER zdarzeń najechaniu myszą). Użyj [makra END_DHTML_EVENT_MAP_INLINE,](#end_dhtml_event_map_inline) aby oznaczyć koniec mapy zdarzeń. Te makra implementują następującą funkcję:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="declare_dhtml_event_map"></a><a name="declare_dhtml_event_map"></a>DECLARE_DHTML_EVENT_MAP

Deklaruje mapę zdarzeń DHTML w definicji klasy.

```cpp
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Uwagi

To makro ma być używane w definicji [klas pochodnych CDHtmlDialog.](../../mfc/reference/cdhtmldialog-class.md)

Zaimplementuj mapę za pomocą [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) lub [BEGIN_DHTML_EVENT_MAP_INLINE.](#begin_dhtml_event_map_inline)

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) deklaruje następującą funkcję:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event"></a><a name="dhtml_event"></a>DHTML_EVENT

Obsługuje (na poziomie dokumentu) zdarzenie zidentyfikowane przez *dispid* pochodzi od elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
Dispid zdarzenia, które mają być obsługiwane.

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie lub NULL do obsługi zdarzeń dokumentu.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_axcontrol"></a><a name="dhtml_event_axcontrol"></a>DHTML_EVENT_AXCONTROL

Obsługuje zdarzenie zidentyfikowane przez *dispid* opalanych przez activex kontroli identyfikowane przez *controlName*.

```cpp
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
Identyfikator wysyłki zdarzenia, które ma być obsługiwane.

*nazwa sterowania*<br/>
LPCWSTR zawierający identyfikator HTML formantu wypalania zdarzenia.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_class"></a><a name="dhtml_event_class"></a>DHTML_EVENT_CLASS

Obsługuje (na poziomie dokumentu) zdarzenie identyfikowane przez *dispid* pochodzi od dowolnego elementu HTML z klasy CSS identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
Identyfikator wysyłki zdarzenia, które ma być obsługiwane.

*nazwa elem*<br/>
LPCWSTR gospodarstwa klasy CSS elementów HTML pozyskiwania zdarzenia.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_element"></a><a name="dhtml_event_element"></a>DHTML_EVENT_ELEMENT

Uchwyty (w *elemName)* zdarzenie zidentyfikowane przez *dispid*.

```cpp
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
Identyfikator wysyłki zdarzenia, które ma być obsługiwane.

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

Jeśli to makro jest używane do obsługi zdarzeń niebubbling, źródłem zdarzenia będzie element identyfikowany przez *elemName*.

Jeśli to makro jest używane do obsługi zdarzeń propagacji, element identyfikowany przez *elemName* może nie być źródłem zdarzenia (źródłem może być dowolny element zawarty przez *elemName*).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onafterupdate"></a><a name="dhtml_event_onafterupdate"></a>DHTML_EVENT_ONAFTERUPDATE

Obsługuje (na poziomie dokumentu) `onafterupdate` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a>DHTML_EVENT_ONBEFOREUPDATE

Obsługuje (na poziomie dokumentu) `onbeforeupdate` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onblur"></a><a name="dhtml_event_onblur"></a>DHTML_EVENT_ONBLUR

Obsługuje (na poziomie elementu) `onblur` zdarzenie. Jest to zdarzenie nonbubbling.

```cpp
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onchange"></a><a name="dhtml_event_onchange"></a>DHTML_EVENT_ONCHANGE

Obsługuje (na poziomie elementu) `onchange` zdarzenie. Jest to zdarzenie nonbubbling.

```cpp
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onclick"></a><a name="dhtml_event_onclick"></a>DHTML_EVENT_ONCLICK

Obsługuje (na poziomie dokumentu) `onclick` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_ondataavailable"></a><a name="dhtml_event_ondataavailable"></a>DHTML_EVENT_ONDATAAVAILABLE

Obsługuje (na poziomie dokumentu) `ondataavailable` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_ondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a>DHTML_EVENT_ONDATASETCHANGED

Obsługuje (na poziomie dokumentu) `ondatasetchanged` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_ondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a>DHTML_EVENT_ONDATASETCOMPLETE

Obsługuje (na poziomie dokumentu) `ondatasetcomplete` zdarzenie pochodzące z elementu `elemName`HTML identyfikowane przez .

```cpp
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_ondblclick"></a><a name="dhtml_event_ondblclick"></a>DHTML_EVENT_ONDBLCLICK

Obsługuje (na poziomie dokumentu) `ondblclick` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_ondragstart"></a><a name="dhtml_event_ondragstart"></a>DHTML_EVENT_ONDRAGSTART

Obsługuje (na poziomie dokumentu) `ondragstart` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a>DHTML_EVENT_ONERRORUPDATE

Obsługuje (na poziomie dokumentu) `onerrorupdate` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onfilterchange"></a><a name="dhtml_event_onfilterchange"></a>DHTML_EVENT_ONFILTERCHANGE

Obsługuje (na poziomie dokumentu) `onfilterchange` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onfocus"></a><a name="dhtml_event_onfocus"></a>DHTML_EVENT_ONFOCUS

Obsługuje (na poziomie elementu) `onfocus` zdarzenie. Jest to zdarzenie nonbubbling.

```cpp
DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onhelp"></a><a name="dhtml_event_onhelp"></a>DHTML_EVENT_ONHELP

Obsługuje (na poziomie dokumentu) `onhelp` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onkeydown"></a><a name="dhtml_event_onkeydown"></a>DHTML_EVENT_ONKEYDOWN

Obsługuje (na poziomie dokumentu) `onkeydown` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onkeypress"></a><a name="dhtml_event_onkeypress"></a>DHTML_EVENT_ONKEYPRESS

Obsługuje (na poziomie dokumentu) `onkeypress` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onkeyup"></a><a name="dhtml_event_onkeyup"></a>DHTML_EVENT_ONKEYUP

Obsługuje (na poziomie dokumentu) `onkeyup` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onmousedown"></a><a name="dhtml_event_onmousedown"></a>DHTML_EVENT_ONMOUSEDOWN

Obsługuje (na poziomie dokumentu) `onmousedown` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onmousemove"></a><a name="dhtml_event_onmousemove"></a>DHTML_EVENT_ONMOUSEMOVE

Obsługuje (na poziomie dokumentu) `onmousemove` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onmouseout"></a><a name="dhtml_event_onmouseout"></a>DHTML_EVENT_ONMOUSEOUT

Obsługuje (na poziomie dokumentu) `onmouseout` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onmouseover"></a><a name="dhtml_event_onmouseover"></a>DHTML_EVENT_ONMOUSEOVER

Obsługuje (na poziomie dokumentu) `onmouseover` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onmouseup"></a><a name="dhtml_event_onmouseup"></a>DHTML_EVENT_ONMOUSEUP

Obsługuje (na poziomie dokumentu) `onmouseup` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onresize"></a><a name="dhtml_event_onresize"></a>DHTML_EVENT_ONRESIZE

Obsługuje (na poziomie elementu) `onresize` zdarzenie. Jest to zdarzenie nonbubbling.

```cpp
DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onrowenter"></a><a name="dhtml_event_onrowenter"></a>DHTML_EVENT_ONROWENTER

Obsługuje (na poziomie dokumentu) `onrowenter` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onrowexit"></a><a name="dhtml_event_onrowexit"></a>DHTML_EVENT_ONROWEXIT

Obsługuje (na poziomie dokumentu) `onrowexit` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_onselectstart"></a><a name="dhtml_event_onselectstart"></a>DHTML_EVENT_ONSELECTSTART

Obsługuje (na poziomie dokumentu) `onselectstart` zdarzenie pochodzące z elementu HTML identyfikowane przez *elemName*.

```cpp
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*nazwa elem*<br/>
LPCWSTR zawierający identyfikator elementu HTML zaopatrującego się w zdarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="dhtml_event_tag"></a><a name="dhtml_event_tag"></a>DHTML_EVENT_TAG

Obsługuje (na poziomie dokumentu) zdarzenie zidentyfikowane `dispid` przez pochodzący z dowolnego elementu HTML z tagiem HTML identyfikowanym przez *elemName*.

```cpp
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
Identyfikator wysyłki zdarzenia, które ma być obsługiwane.

*nazwa elem*<br/>
Tag HTML elementów HTML zaopatrujących się w wydarzenie.

*członekFxn*<br/>
Funkcja obsługi dla zdarzenia.

### <a name="remarks"></a>Uwagi

To makro służy do dodawania wpisu do [mapy zdarzeń DHTML](#begin_dhtml_event_map_inline) w klasie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="end_dhtml_event_map"></a><a name="end_dhtml_event_map"></a>END_DHTML_EVENT_MAP

Oznacza koniec mapy zdarzeń DHTML.

```cpp
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Uwagi

Musi być używany w połączeniu z [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="begin_dhtml_url_event_map"></a><a name="begin_dhtml_url_event_map"></a>BEGIN_DHTML_URL_EVENT_MAP

Rozpoczyna definicję mapy zdarzeń DHTML i ADRESU URL w wielostronicowym oknie dialogowym.

```cpp
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Uwagi

Umieść BEGIN_DHTML_URL_EVENT_MAP w pliku implementacji klasy [CMultiPageDHtmlDialog.](../../mfc/reference/cmultipagedhtmldialog-class.md) Postępuj zgodnie z [osadzonymi mapami zdarzeń DHTML](#begin_embed_dhtml_event_map) i [wpisami adresów URL,](#begin_url_entries)a następnie zamknij go [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map). Uwzględnij [makro DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) w definicji klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="begin_embed_dhtml_event_map"></a><a name="begin_embed_dhtml_event_map"></a>BEGIN_EMBED_DHTML_EVENT_MAP

Rozpoczyna definicję osadzonej mapy zdarzeń DHTML w wielostronicowym oknie dialogowym.

```cpp
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Nazwa klasy zawierającej mapę zdarzeń. Ta klasa powinna pochodzić bezpośrednio lub pośrednio z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Osadzona mapa zdarzeń DHTML musi znajdować się wewnątrz [mapy zdarzeń DHTML i ADRESU URL](#begin_dhtml_url_event_map)).

*nazwa mapy*<br/>
Określa stronę, której mapa zdarzeń jest to. To pasuje *do nazwy map* w [URL_EVENT_ENTRY](#url_event_entry) makro definiujące adres URL lub zasób HTML.

### <a name="remarks"></a>Uwagi

Ponieważ wielostronicowe okno dialogowe DHTML składa się z wielu stron HTML, z których każda może podnosić zdarzenia DHTML, osadzone mapy zdarzeń są używane do mapowania zdarzeń do obsługi na podstawie poszczególnych stron.

Osadzone mapy zdarzeń w mapce zdarzeń DHTML i URL składają się z makra BEGIN_EMBED_DHTML_EVENT_MAP, po którym następuje [DHTML_EVENT](#dhtml_event) makra i makro [END_EMBED_DHTML_EVENT_MAP.](#end_embed_dhtml_event_map)

Każda osadzona mapa zdarzeń wymaga odpowiedniego [wpisu zdarzenia adresu URL](#url_event_entry) do *mapowania nazwy mapy* (określonej w BEGIN_EMBED_DHTML_EVENT_MAP) do adresu URL lub zasobu HTML.

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="begin_url_entries"></a><a name="begin_url_entries"></a>BEGIN_URL_ENTRIES

Rozpoczyna definicję mapy wpisu zdarzenia adresu URL w wielostronicowym oknie dialogowym.

```cpp
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Nazwa klasy zawierającej mapę wpisu zdarzenia adresu URL. Ta klasa powinna pochodzić bezpośrednio lub pośrednio z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Mapa wpisu zdarzenia adresu URL musi znajdować się wewnątrz [mapy zdarzeń DHTML i ADRESU URL](#begin_dhtml_url_event_map)).

### <a name="remarks"></a>Uwagi

Ponieważ wielostronicowe okno dialogowe DHTML składa się z wielu stron HTML, wpisy zdarzeń adresu URL są używane do mapowania adresów URL lub zasobów HTML na odpowiednie [osadzone mapy zdarzeń DHTML](#begin_embed_dhtml_event_map). Umieszczanie makr URL_EVENT_ENTRY między makrami BEGIN_URL_ENTRIES i [END_URL_ENTRIES.](#end_url_entries)

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="declare_dhtml_url_event_map"></a><a name="declare_dhtml_url_event_map"></a>DECLARE_DHTML_URL_EVENT_MAP

Deklaruje mapę zdarzeń DHTML i URL w definicji klasy.

```cpp
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Uwagi

To makro ma być używane w definicji [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-derived klas.

Mapa zdarzeń DHTML i URL zawiera [osadzone mapy zdarzeń DHTML](#begin_embed_dhtml_event_map) i [wpisy zdarzeń adresu URL](#begin_url_entries) do mapowania zdarzeń DHTML do programów obsługi na podstawie strony. Użyj [BEGIN_DHTML_URL_EVENT_MAP,](#begin_dhtml_url_event_map) aby zaimplementować mapę.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="end_dhtml_url_event_map"></a><a name="end_dhtml_url_event_map"></a>END_DHTML_URL_EVENT_MAP

Oznacza koniec mapy zdarzeń DHTML i ADRESU URL.

```cpp
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Nazwa klasy zawierającej mapę zdarzeń. Ta klasa powinna pochodzić bezpośrednio lub pośrednio z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Powinno to odpowiadać *className* w odpowiednim [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) makra.

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="end_embed_dhtml_event_map"></a><a name="end_embed_dhtml_event_map"></a>END_EMBED_DHTML_EVENT_MAP

Oznacza koniec osadzonej mapy zdarzeń DHTML.

```cpp
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="end_url_entries"></a><a name="end_url_entries"></a>END_URL_ENTRIES

Oznacza koniec mapy wpisu zdarzenia adresu URL.

```cpp
END_URL_ENTRIES()
```

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="url_event_entry"></a><a name="url_event_entry"></a>URL_EVENT_ENTRY

Mapuje adres URL lub zasób HTML na stronę w wielostronicowym oknie dialogowym.

```cpp
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Nazwa klasy zawierającej mapę wpisu zdarzenia adresu URL. Ta klasa powinna pochodzić bezpośrednio lub pośrednio z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Mapa wpisu zdarzenia adresu URL musi znajdować się wewnątrz [mapy zdarzeń DHTML i ADRESU URL](#begin_dhtml_url_event_map)).

*Adres url*<br/>
Adres URL lub zasób HTML strony.

*nazwa mapy*<br/>
Określa stronę, której adres URL jest *adresem URL*. To pasuje *do nazwy map w* [BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map) makra mapowego, które mapuje zdarzenia z tej strony.

### <a name="remarks"></a>Uwagi

Jeśli strona jest zasobem HTML, *adres URL* musi być reprezentacją ciągu numeru identyfikatora zasobu (czyli "123", a nie 123 lub ID_HTMLRES1).

Identyfikator strony, *mapName*, jest dowolnym symbolem używanym do łączenia osadzonych map zdarzeń DHTML z mapami wpisów zdarzeń URL. Jest ograniczona zakresem do mapy zdarzeń DHTML i adresu URL.

### <a name="example"></a>Przykład

Zobacz przykład w [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdhtml.h

## <a name="end_dhtml_event_map_inline"></a><a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE

Oznacza koniec mapy zdarzeń DHTML.

### <a name="syntax"></a>Składnia

```cpp
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>Uwagi

Musi być używany w połączeniu z [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdhtml.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](mfc-macros-and-globals.md)
