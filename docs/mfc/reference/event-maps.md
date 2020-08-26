---
title: Mapy zdarzeń
ms.date: 09/07/2019
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: aa11dbe1a0a3dc45893d1a05cda0ef1addb9e665
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837349"
---
# <a name="event-maps"></a>Mapy zdarzeń

Za każdym razem, gdy kontrolka życzy sobie poinformować, że została wykonana jakaś akcja (określona przez dewelopera kontrolki) (na przykład naciśnięcie klawisza, kliknięcie myszą lub zmiana stanu kontrolki), wywołuje funkcję uruchamiania zdarzeń. Ta funkcja powiadamia kontener formantów o wystąpieniu pewnej ważnej akcji przez wyzwolenie powiązanego zdarzenia.

Biblioteka MFC oferuje model programowania zoptymalizowany pod kątem wyzwalania zdarzeń. W tym modelu "mapy zdarzeń" są używane do wyznaczania, które funkcje wyzwalają zdarzenia dla konkretnej kontrolki. Mapy zdarzeń zawierają jedno makro dla każdego zdarzenia. Na przykład mapa zdarzeń, która wyzwala wydarzenie akcji kliknięcia, może wyglądać następująco:

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

`EVENT_STOCK_CLICK`Makro wskazuje, że po wykryciu kliknięcia myszą przez formant będzie wyzwalane zdarzenie kliknięcia. Aby zapoznać się z bardziej szczegółową listą innych zdarzeń giełdowych, zobacz artykuł [formanty ActiveX: zdarzenia](../../mfc/mfc-activex-controls-events.md). Dostępne są również makra wskazujące na zdarzenia niestandardowe.

Mimo że makra mapy zdarzeń są ważne, zazwyczaj nie należy wstawiać ich bezpośrednio. Jest to spowodowane tym, że okno **Właściwości** (w **Widok klasy**) automatycznie tworzy wpisy mapowania zdarzeń w plikach źródłowych, gdy jest on używany do kojarzenia funkcji wyzwalania zdarzeń ze zdarzeniami. Za każdym razem, gdy chcesz edytować lub dodać wpis mapy zdarzeń, możesz użyć okna **Właściwości** .

Aby można było obsługiwać mapy zdarzeń, MFC udostępnia następujące makra:

## <a name="event-map-macros"></a>Makra mapy zdarzeń

### <a name="event-map-declaration-and-demarcation"></a>Deklaracja i rozgraniczanie mapy zdarzeń

|Nazwa|Opis|
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|Deklaruje, że mapa zdarzeń zostanie użyta w klasie do mapowania zdarzeń do funkcji uruchamiania zdarzeń (musi być używana w deklaracji klasy).|
|[BEGIN_EVENT_MAP](#begin_event_map)|Rozpoczyna definicję mapy zdarzeń (należy ją użyć w implementacji klasy).|
|[END_EVENT_MAP](#end_event_map)|Zamyka definicję mapy zdarzeń (musi być używana w implementacji klasy).|

### <a name="event-mapping-macros"></a>Makra mapowania zdarzeń

|Nazwa|Opis|
|-|-|
|[EVENT_CUSTOM](#event_custom)|Wskazuje, która funkcja uruchamiania zdarzeń uruchamia określone zdarzenie.|
|[EVENT_CUSTOM_ID](#event_custom_id)|Wskazuje, która funkcja uruchamiania zdarzeń uruchamia określone zdarzenie z wyznaczonym IDENTYFIKATORem wysyłania.|

### <a name="message-mapping-macros"></a>Makra mapowania komunikatów

|Nazwa|Opis|
|-|-|
|[ON_OLEVERB](#on_oleverb)|Wskazuje niestandardowe zlecenie obsługiwane przez kontrolkę OLE.|
|[ON_STDOLEVERB](#on_stdoleverb)|Zastępuje standardowe mapowanie czasownika kontrolki OLE.|

## <a name="declare_event_map"></a><a name="declare_event_map"></a> DECLARE_EVENT_MAP

Każda `COleControl` Klasa pochodna w programie może zapewnić mapę zdarzeń, aby określić zdarzenia, które będą uruchamiane przez formant.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>Uwagi

Użyj makra DECLARE_EVENT_MAP na końcu deklaracji klasy. Następnie w pliku. cpp, który definiuje funkcje elementu członkowskiego dla klasy, użyj makra BEGIN_EVENT_MAP, wpisów makr dla każdego zdarzenia kontrolki i makra END_EVENT_MAP, aby zadeklarować koniec listy zdarzeń.

Aby uzyskać więcej informacji na temat map zdarzeń, zobacz artykuł [formanty ActiveX: zdarzenia](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Wymagania

**Nagłówek** 'afxctl. h

## <a name="begin_event_map"></a><a name="begin_event_map"></a> BEGIN_EVENT_MAP

Rozpoczyna definicję mapy zdarzeń.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa nazwę klasy kontrolki, której mapowanie zdarzeń to.

*baseClass*<br/>
Określa nazwę klasy bazowej *theClass*.

### <a name="remarks"></a>Uwagi

W pliku implementacji (. cpp), który definiuje funkcje elementów członkowskich klasy, uruchom mapę zdarzeń za pomocą makra BEGIN_EVENT_MAP, a następnie Dodaj wpisy makr dla każdego zdarzenia i Ukończ mapowanie zdarzeń za pomocą makra END_EVENT_MAP.

Aby uzyskać więcej informacji na temat map zdarzeń i makra BEGIN_EVENT_MAP, zobacz artykuł [ActiveX Controls: Events](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Wymagania

**Nagłówek** 'afxctl. h

## <a name="end_event_map"></a><a name="end_event_map"></a> END_EVENT_MAP

Użyj makra END_EVENT_MAP, aby zakończyć definicję mapy zdarzeń.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek** 'afxctl. h

## <a name="event_custom"></a><a name="event_custom"></a> EVENT_CUSTOM

Definiuje wpis mapy zdarzeń dla zdarzenia niestandardowego.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>Parametry

*pszName*<br/>
Nazwa zdarzenia.

*pfnFire*<br/>
Nazwa funkcji wywołującej zdarzenia.

*vtsParams*<br/>
Rozdzielana spacjami lista jednej lub kilku stałych określających listę parametrów funkcji.

### <a name="remarks"></a>Uwagi

*VtsParams* parametr to rozdzielana spacjami lista wartości ze `VTS_` stałych. Co najmniej jedna z tych wartości rozdzielonych spacjami (nie przecinkami) określa listę parametrów funkcji. Na przykład:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

Określa listę zawierającą 32-bitową liczbę całkowitą reprezentującą wartość koloru RGB, a następnie wskaźnik do `IFontDisp` interfejsu obiektu czcionki OLE.

`VTS_`Stałe i ich znaczenie są następujące:

|Symbol|Typ parametru|
|------------|--------------------|
|VTS_I2|**`short`**|
|VTS_I4|**`long`**|
|VTS_R4|**`float`**|
|VTS_R8|**`double`**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|WALUTA|
|VTS_DATE|DATE|
|VTS_BSTR|**`const`**__znak \* __|
|VTS_DISPATCH|LPDISPATCH|
|VTS_FONT|`IFontDispatch*`|
|VTS_HANDLE|UCHWYTY|
|VTS_SCODE|SCODE|
|VTS_BOOL|LOGICZNA|
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
> Dodatkowe stałe wariantowe zostały zdefiniowane dla wszystkich typów wariantów, z wyjątkiem VTS_FONT i VTS_PICTURE, które zapewniają wskaźnik do stałej danych Variant. Te stałe są nazwane przy użyciu `VTS_Pconstantname` Konwencji. Na przykład VTS_PCOLOR jest wskaźnikiem do stałej VTS_COLOR.

### <a name="requirements"></a>Wymagania

**Nagłówek** 'afxctl. h

## <a name="event_custom_id"></a><a name="event_custom_id"></a> EVENT_CUSTOM_ID

Definiuje funkcję do uruchamiania zdarzeń dla zdarzenia niestandardowego należącego do identyfikatora wysyłania określonego przez *DISPID*.

```cpp
EVENT_CUSTOM_ID(
    pszName,
    dispid,
    pfnFire,
    vtsParams)
```

### <a name="parameters"></a>Parametry

*pszName*<br/>
Nazwa zdarzenia.

*DISPID*<br/>
Identyfikator wysyłania używany przez formant podczas wyzwalania zdarzenia.

*pfnFire*<br/>
Nazwa funkcji wywołującej zdarzenia.

*vtsParams*<br/>
Zmienna lista parametrów przenoszona do kontenera kontroli, gdy zdarzenie jest wyzwalane.

### <a name="remarks"></a>Uwagi

Argument *vtsParams* jest rozdzielaną spacją listą wartości ze `VTS_` stałych. Co najmniej jedna z tych wartości oddzielona spacjami, a nie przecinkiem, określa listę parametrów funkcji. Na przykład:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

Określa listę zawierającą 32-bitową liczbę całkowitą reprezentującą wartość koloru RGB, a następnie wskaźnik do `IFontDisp` interfejsu obiektu czcionki OLE.

Aby zapoznać się z listą `VTS_` stałych, zobacz [EVENT_CUSTOM](#event_custom).

### <a name="requirements"></a>Wymagania

**Nagłówek** 'afxctl. h

## <a name="on_oleverb"></a><a name="on_oleverb"></a> ON_OLEVERB

To makro definiuje wpis mapy komunikatów, który mapuje czasownik niestandardowy na określoną funkcję elementu członkowskiego formantu.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*idsVerbName*<br/>
Identyfikator zasobu ciągu nazwy zlecenia.

*memberFxn*<br/>
Funkcja wywoływana przez platformę, gdy zlecenie jest wywoływane.

### <a name="remarks"></a>Uwagi

Edytor zasobów może służyć do tworzenia niestandardowych nazw zleceń, które są dodawane do tabeli ciągów.

Prototyp funkcji dla *memberFxn* jest:

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

Wartości parametrów *lpMsg*, *hWndParent*i *lpRect* są pobierane z odpowiednich parametrów `IOleObject::DoVerb` funkcji składowej.

### <a name="requirements"></a>Wymagania

**Nagłówek** Afxole. h

## <a name="on_stdoleverb"></a><a name="on_stdoleverb"></a> ON_STDOLEVERB

To makro służy do przesłonięcia domyślnego zachowania standardowego czasownika.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Standardowy indeks czasowników dla przesłanianego zlecenia.

*memberFxn*<br/>
Funkcja wywoływana przez platformę, gdy zlecenie jest wywoływane.

### <a name="remarks"></a>Uwagi

Standardowy indeks czasowników ma postać `OLEIVERB_` , a po niej akcja. Przykłady standardowych czasowników OLEIVERB_SHOW, OLEIVERB_HIDE i OLEIVERB_UIACTIVATE.

Zobacz [ON_OLEVERB](#on_oleverb) , aby uzyskać opis prototypu funkcji, który ma być używany jako parametr *memberFxn* .

### <a name="requirements"></a>Wymagania

**Nagłówek** Afxole. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
