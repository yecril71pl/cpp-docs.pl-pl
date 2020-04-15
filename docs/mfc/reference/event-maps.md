---
title: Mapy zdarzeń
ms.date: 09/07/2019
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: c79d2fb1ac73947ddb13adcbd444ff7b5d50bdb4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365734"
---
# <a name="event-maps"></a>Mapy zdarzeń

Za każdym razem, gdy formant chce powiadomić swój kontener, że niektóre akcje (określone przez dewelopera formantu) miało miejsce (na przykład naciśnięcie klawisza, kliknięcie myszą lub zmiana stanu formantu) wywołuje funkcję wypalania zdarzeń. Ta funkcja powiadamia kontener formantu, że wystąpiła jakaś ważna akcja przez wypalanie powiązanego zdarzenia.

Biblioteka klas Microsoft Foundation oferuje model programowania zoptymalizowany pod kątem wypalania zdarzeń. W tym modelu "mapy zdarzeń" są używane do określania, które funkcje ognia, które zdarzenia dla określonego formantu. Mapy zdarzeń zawierają jedno makro dla każdego zdarzenia. Na przykład mapa zdarzeń, która uruchamia zdarzenie click stock może wyglądać następująco:

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

Makro `EVENT_STOCK_CLICK` wskazuje, że formant będzie uruchamiał zdarzenie kliknięcie za każdym razem, gdy wykryje kliknięcie myszą. Aby uzyskać bardziej szczegółową listę innych zdarzeń giełdowych, zobacz artykuł [ActiveX Controls: Events](../../mfc/mfc-activex-controls-events.md). Makra są również dostępne do wskazywania zdarzeń niestandardowych.

Chociaż makra mapy zdarzeń są ważne, zazwyczaj nie należy ich wstawiać bezpośrednio. Dzieje się tak, ponieważ okno **Właściwości** (w **widoku klasy)** automatycznie tworzy wpisy mapy zdarzeń w plikach źródłowych, gdy jest używane do kojarzenia funkcji wypalania zdarzeń ze zdarzeniami. Za każdym razem, gdy chcesz edytować lub dodać wpis mapy zdarzeń, możesz użyć okna **Właściwości.**

Aby obsługiwać mapy zdarzeń, MFC udostępnia następujące makra:

## <a name="event-map-macros"></a>Makra mapy zdarzeń

### <a name="event-map-declaration-and-demarcation"></a>Deklaracja i rozgraniczenie mapy zdarzeń

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|Deklaruje, że mapa zdarzeń będzie używana w klasie do mapowania zdarzeń do funkcji wypalania zdarzeń (musi być używana w deklaracji klasy).|
|[BEGIN_EVENT_MAP](#begin_event_map)|Rozpoczyna definicję mapy zdarzeń (musi być używana w implementacji klasy).|
|[END_EVENT_MAP](#end_event_map)|Kończy definicję mapy zdarzeń (musi być używana w implementacji klasy).|

### <a name="event-mapping-macros"></a>Makra mapowania zdarzeń

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|Wskazuje, która funkcja wypalania zdarzeń spowoduje wystrzelenie określonego zdarzenia.|
|[EVENT_CUSTOM_ID](#event_custom_id)|Wskazuje, która funkcja wywoływania zdarzeń spowoduje wystrzelenie określonego zdarzenia, z wyznaczonym identyfikatorem wysyłki.|

### <a name="message-mapping-macros"></a>Makra mapowania wiadomości

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|Wskazuje zlecenie niestandardowe obsługiwane przez kontrolkę OLE.|
|[ON_STDOLEVERB](#on_stdoleverb)|Zastępuje standardowe mapowanie zlecenia formantu OLE.|

## <a name="declare_event_map"></a><a name="declare_event_map"></a>DECLARE_EVENT_MAP

Każda `COleControl`klasa pochodna w programie może dostarczyć mapę zdarzeń, aby określić zdarzenia, które zostanie podpalone przez formant.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>Uwagi

Użyj makra DECLARE_EVENT_MAP na końcu deklaracji klasy. Następnie w pliku .cpp, który definiuje funkcje członkowskie dla klasy, użyj BEGIN_EVENT_MAP makra, wpisów makr dla każdego zdarzenia formantu i makra END_EVENT_MAP, aby zadeklarować koniec listy zdarzeń.

Aby uzyskać więcej informacji na temat map zdarzeń, zobacz artykuł [ActiveX Controls: Events](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Wymagania

**Nagłówek** afxctl.h

## <a name="begin_event_map"></a><a name="begin_event_map"></a>BEGIN_EVENT_MAP

Rozpoczyna definicję mapy zdarzeń.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Określa nazwę klasy kontrolnej, której mapa zdarzeń jest to.

*Baseclass*<br/>
Określa nazwę klasy podstawowej *klasy klasy*.

### <a name="remarks"></a>Uwagi

W pliku implementacji (.cpp), który definiuje funkcje członkowskie dla klasy, uruchom mapę zdarzeń BEGIN_EVENT_MAP makra, a następnie dodaj wpisy makr dla każdego zdarzenia i uzupełnij mapę zdarzeń END_EVENT_MAP makra.

Aby uzyskać więcej informacji na temat map zdarzeń i makra BEGIN_EVENT_MAP, zobacz artykuł [ActiveX Controls: Events](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Wymagania

**Nagłówek** afxctl.h

## <a name="end_event_map"></a><a name="end_event_map"></a>END_EVENT_MAP

Użyj makra END_EVENT_MAP, aby zakończyć definicję mapy zdarzeń.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek** afxctl.h

## <a name="event_custom"></a><a name="event_custom"></a>EVENT_CUSTOM

Definiuje wpis mapy zdarzeń dla zdarzenia niestandardowego.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
Nazwa zdarzenia.

*pfnFire (pfnFire)*<br/>
Nazwa funkcji wypalania zdarzenia.

*vtsParams ( vtsParams )*<br/>
Oddzielona spacja lista jednej lub więcej stałych określających listę parametrów funkcji.

### <a name="remarks"></a>Uwagi

Parametr *vtsParams* jest oddzieloną spacją listą `VTS_` wartości ze stałych. Jedna lub więcej z tych wartości oddzielonych spacjami (nie przecinkami) określa listę parametrów funkcji. Przykład:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

określa listę zawierającą 32-bitową liczbę całkowitą reprezentującą wartość koloru RGB, `IFontDisp` po której następuje wskaźnik do interfejsu obiektu czcionek OLE.

Stałe `VTS_` i ich znaczenie są następujące:

|Symbol|Typ parametru|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|WALUTA|
|VTS_DATE|DATE|
|VTS_BSTR|const __char\* __ **(char)**|
|VTS_DISPATCH|LPDISPATCH ( LPDISPATCH )|
|VTS_FONT|`IFontDispatch*`|
|VTS_HANDLE|Obsługi|
|VTS_SCODE|SCODE|
|VTS_BOOL|Bool|
|VTS_VARIANT|`const VARIANT*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_OPTEXCLUSIVE|OLE_OPTEXCLUSIVE|
|VTS_PICTURE|`IPictureDisp*`|
|VTS_TRISTATE|OLE_TRISTATE|
|VTS_XPOS_PIXELS|OLE_XPOS_PIXELS|
|VTS_YPOS_PIXELS|OLE_YPOS_PIXELS|
|VTS_XSIZE_PIXELS|OLE_XSIZE_PIXELS|
|VTS_YSIZE_PIXELS|OLE_YSIZE_PIXELS|
|TS_XPOS_HIMETRIC|OLE_XPOS_HIMETRIC|
|VTS_YPOS_HIMETRIC|OLE_YPOS_HIMETRIC|
|VTS_XSIZE_HIMETRIC|OLE_XSIZE_HIMETRIC|
|VTS_YSIZE_HIMETRIC|OLE_YSIZE_HIMETRIC|

> [!NOTE]
> Dodatkowe stałe wariantu zostały zdefiniowane dla wszystkich typów wariantów, z wyjątkiem VTS_FONT i VTS_PICTURE, które zapewniają wskaźnik do stałej danych wariantu. Te stałe są nazwane przy użyciu `VTS_Pconstantname` konwencji. Na przykład VTS_PCOLOR jest wskaźnikiem do stałej VTS_COLOR.

### <a name="requirements"></a>Wymagania

**Nagłówek** afxctl.h

## <a name="event_custom_id"></a><a name="event_custom_id"></a>EVENT_CUSTOM_ID

Definiuje funkcję wywoływania zdarzeń dla zdarzenia niestandardowego należącego do identyfikatora wysyłki określonego przez *dispid*.

```cpp
EVENT_CUSTOM_ID(
    pszName,
    dispid,
    pfnFire,
    vtsParams)
```

### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
Nazwa zdarzenia.

*Dispid*<br/>
Identyfikator wysyłki używany przez formant podczas wypalania zdarzenia.

*pfnFire (pfnFire)*<br/>
Nazwa funkcji wypalania zdarzenia.

*vtsParams ( vtsParams )*<br/>
Lista zmiennych parametrów przekazanych do kontenera formantu po uruchomieniu zdarzenia.

### <a name="remarks"></a>Uwagi

*VtsParams* argument jest oddzielona spacja lista `VTS_` wartości ze stałych. Jedna lub więcej z tych wartości oddzielonych spacjami, a nie przecinkami, określa listę parametrów funkcji. Przykład:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

określa listę zawierającą 32-bitową liczbę całkowitą reprezentującą wartość koloru RGB, `IFontDisp` po której następuje wskaźnik do interfejsu obiektu czcionek OLE.

Aby uzyskać listę `VTS_` stałych, zobacz [EVENT_CUSTOM](#event_custom).

### <a name="requirements"></a>Wymagania

**Nagłówek** afxctl.h

## <a name="on_oleverb"></a><a name="on_oleverb"></a>ON_OLEVERB

To makro definiuje wpis mapy wiadomości, który mapuje zlecenie niestandardowe na określoną funkcję elementu członkowskiego formantu.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*idsVerbName*<br/>
Identyfikator zasobu ciągu nazwy zlecenia.

*członekFxn*<br/>
Funkcja wywoływana przez strukturę, gdy wywoływany jest zlecenie.

### <a name="remarks"></a>Uwagi

Edytor zasobów może służyć do tworzenia niestandardowych nazw zleceń, które są dodawane do tabeli ciągów.

Prototyp funkcji dla *memberFxn* jest:

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

Wartości *parametrów lpMsg*, *hWndParent*i *lpRect* są pobierane `IOleObject::DoVerb` z odpowiednich parametrów funkcji elementu członkowskiego.

### <a name="requirements"></a>Wymagania

**Nagłówek** afxole.h

## <a name="on_stdoleverb"></a><a name="on_stdoleverb"></a>ON_STDOLEVERB

To makro służy do zastępowania domyślnego zachowania zlecenia standardowego.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Indeks zlecenia standardowego dla zlecenia jest zastępowane.

*członekFxn*<br/>
Funkcja wywoływana przez strukturę, gdy wywoływany jest zlecenie.

### <a name="remarks"></a>Uwagi

Standardowy indeks czasownika `OLEIVERB_`ma formę , po której następuje akcja. OLEIVERB_SHOW, OLEIVERB_HIDE i OLEIVERB_UIACTIVATE są przykładami czasowników standardowych.

Zobacz [ON_OLEVERB](#on_oleverb) opis prototypu funkcji, który ma być używany jako parametr *memberFxn.*

### <a name="requirements"></a>Wymagania

**Nagłówek** afxole.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
