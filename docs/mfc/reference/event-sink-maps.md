---
title: Mapy wychwytywania zdarzeń
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 731ed2403aae3332e81702673d1181e9e52399a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365723"
---
# <a name="event-sink-maps"></a>Mapy wychwytywania zdarzeń

Gdy osadzony formant OLE uruchamia zdarzenie, kontener formantu odbiera zdarzenie przy użyciu mechanizmu, zwanego "mapą ujścia zdarzeń", dostarczonej przez MFC. Ta mapa ujścia zdarzeń wyznacza funkcje obsługi dla każdego określonego zdarzenia, a także parametry tych zdarzeń. Aby uzyskać więcej informacji na temat map ujścia zdarzeń, zobacz artykuł [Kontenery sterowania ActiveX](../../mfc/activex-control-containers.md).

### <a name="event-sink-maps"></a>Mapy wychwytywania zdarzeń

|||
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|Rozpoczyna definicję mapy ujścia zdarzeń.|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|Deklaruje mapę ujścia zdarzeń.|
|[END_EVENTSINK_MAP](#end_eventsink_map)|Kończy definicję mapy ujścia zdarzeń.|
|[ON_EVENT](#on_event)|Definiuje program obsługi zdarzeń dla określonego zdarzenia.|
|[ON_EVENT_RANGE](#on_event_range)|Definiuje program obsługi zdarzeń dla określonego zdarzenia uruchamianego z zestawu formantów OLE.|
|[ON_EVENT_REFLECT](#on_event_reflect)|Odbiera zdarzenia uruchamiane przez formant, zanim są obsługiwane przez kontener formantu.|
|[ON_PROPNOTIFY](#on_propnotify)|Definiuje program obsługi do obsługi powiadomień właściwości z formantu OLE.|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|Definiuje program obsługi do obsługi powiadomień właściwości z zestawu formantów OLE.|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|Odbiera powiadomienia właściwości wysyłane przez formant, zanim są obsługiwane przez kontener formantu.|

## <a name="begin_eventsink_map"></a><a name="begin_eventsink_map"></a>BEGIN_EVENTSINK_MAP

Rozpoczyna definicję mapy ujścia zdarzeń.

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Określa nazwę klasy kontrolnej, której mapa ujścia zdarzeń jest to.

*Baseclass*<br/>
Określa nazwę klasy podstawowej *klasy klasy*.

### <a name="remarks"></a>Uwagi

W pliku implementacji (.cpp), który definiuje funkcje członkowskie dla klasy, uruchom mapę ujścia zdarzeń z BEGIN_EVENTSINK_MAP makra, a następnie dodaj wpisy makr dla każdego zdarzenia, które mają być powiadamiane, i wypełnij mapę ujścia zdarzeń za pomocą END_EVENTSINK_MAP makra.

Aby uzyskać więcej informacji na temat map ujścia zdarzeń i kontenerów sterowania OLE, zobacz artykuł [Kontenery sterowania ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="declare_eventsink_map"></a><a name="declare_eventsink_map"></a>DECLARE_EVENTSINK_MAP

Kontener OLE może dostarczyć mapę ujścia zdarzeń, aby określić zdarzenia, o które zostanie powiadomiony kontener.

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>Uwagi

Użyj makra DECLARE_EVENTSINK_MAP na końcu deklaracji klasy. Następnie, w . Plik CPP, który definiuje funkcje członkowskie dla klasy, użyj BEGIN_EVENTSINK_MAP makra, wpisów makr dla każdego zdarzenia, które mają być powiadamiane, a makro END_EVENTSINK_MAP do zadeklarowania końca listy ułowienia zdarzeń.

Aby uzyskać więcej informacji na temat map ujścia zdarzeń, zobacz artykuł [Kontenery sterowania ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="end_eventsink_map"></a><a name="end_eventsink_map"></a>END_EVENTSINK_MAP

Kończy definicję mapy ujścia zdarzeń.

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="on_event"></a><a name="on_event"></a>ON_EVENT

Użyj makra ON_EVENT, aby zdefiniować funkcję obsługi zdarzeń dla zdarzenia uruchamianego przez kontrolę OLE.

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Klasa, do której należy ta mapa ujścia zdarzenia.

*Identyfikator*<br/>
Identyfikator sterowania formantu OLE.

*Dispid*<br/>
Identyfikator wysyłki zdarzenia wywoływanego przez formant.

*pfnHandler (pfnHandler)*<br/>
Wskaźnik do funkcji elementu członkowskiego, która obsługuje zdarzenie. Ta funkcja powinna mieć typ zwracany BOOL i typy parametrów, które pasują do parametrów zdarzenia (patrz *vtsParams*). Funkcja powinna zwracać wartość TRUE, aby wskazać, że zdarzenie zostało obsłużone; w przeciwnym razie FALSE.

*vtsParams ( vtsParams )*<br/>
Sekwencja **VTS_** stałych, która określa typy parametrów zdarzenia. Są to te same stałe, które są używane we wpisach mapy wysyłki, takich jak DISP_FUNCTION.

### <a name="remarks"></a>Uwagi

*VtsParams* argument jest oddzielona spacja lista wartości od **VTS_** stałych. Jedna lub więcej z tych wartości oddzielonych spacjami (nie przecinkami) określa listę parametrów funkcji. Przykład:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

określa listę zawierającą krótką liczbę całkowitą, po której następuje BOOL.

Aby uzyskać listę **stałych VTS_,** zobacz [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="on_event_range"></a><a name="on_event_range"></a>ON_EVENT_RANGE

Użyj makra ON_EVENT_RANGE, aby zdefiniować funkcję obsługi zdarzeń dla zdarzenia uruchamianego przez dowolny formant OLE o identyfikatorze formantu w ciągłym zakresie identyfikatorów.

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Klasa, do której należy ta mapa ujścia zdarzenia.

*idFirst*<br/>
Identyfikator sterowania pierwszego formantu OLE w zakresie.

*idLast*<br/>
Identyfikator sterowania ostatniego formantu OLE w zakresie.

*Dispid*<br/>
Identyfikator wysyłki zdarzenia wywoływanego przez formant.

*pfnHandler (pfnHandler)*<br/>
Wskaźnik do funkcji elementu członkowskiego, która obsługuje zdarzenie. Ta funkcja powinna mieć typ zwracany BOOL, pierwszy parametr typu UINT (dla identyfikatora formantu) i dodatkowe typy parametrów, które pasują do parametrów zdarzenia (patrz *vtsParams*). Funkcja powinna zwracać wartość TRUE, aby wskazać, że zdarzenie zostało obsłużone; w przeciwnym razie FALSE.

*vtsParams ( vtsParams )*<br/>
Sekwencja **VTS_** stałych, która określa typy parametrów zdarzenia. Pierwsza stała powinna być typu VTS_I4 dla identyfikatora formantu. Są to te same stałe, które są używane we wpisach mapy wysyłki, takich jak DISP_FUNCTION.

### <a name="remarks"></a>Uwagi

*VtsParams* argument jest oddzielona spacja lista wartości od **VTS_** stałych. Jedna lub więcej z tych wartości oddzielonych spacjami (nie przecinkami) określa listę parametrów funkcji. Przykład:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

określa listę zawierającą krótką liczbę całkowitą, po której następuje BOOL.

Aby uzyskać listę **stałych VTS_,** zobacz [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono program obsługi zdarzeń dla MouseDown zdarzenia, zaimplementowane dla trzech formantów ( IDC_MYCTRL1 za pośrednictwem IDC_MYCTRL3). Funkcja obsługi zdarzeń `OnRangeMouseDown`, jest zadeklarowana w pliku `CMyDlg`nagłówka klasy dialogowej ( ) jako:

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

Poniższy kod jest zdefiniowany w pliku implementacji klasy dialogowej.

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="on_event_reflect"></a><a name="on_event_reflect"></a>ON_EVENT_REFLECT

Makro ON_EVENT_REFLECT, gdy jest używane w mapie ujścia zdarzeń klasy otoki formantu OLE, odbiera zdarzenia uruchamiane przez formant, zanim zostaną obsłużone przez kontener formantu.

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Klasa, do której należy ta mapa ujścia zdarzenia.

*Dispid*<br/>
Identyfikator wysyłki zdarzenia wywoływanego przez formant.

*pfnHandler (pfnHandler)*<br/>
Wskaźnik do funkcji elementu członkowskiego, która obsługuje zdarzenie. Ta funkcja powinna mieć typ zwracany BOOL i typy parametrów, które pasują do parametrów zdarzenia (patrz *vtsParams*). Funkcja powinna zwracać wartość TRUE, aby wskazać, że zdarzenie zostało obsłużone; w przeciwnym razie FALSE.

*vtsParams ( vtsParams )*<br/>
Sekwencja **VTS_** stałych, która określa typy parametrów zdarzenia. Są to te same stałe, które są używane we wpisach mapy wysyłki, takich jak DISP_FUNCTION.

### <a name="remarks"></a>Uwagi

*VtsParams* argument jest oddzielona spacja lista wartości od **VTS_** stałych.

Jedna lub więcej z tych wartości oddzielonych spacjami (nie przecinkami) określa listę parametrów funkcji. Przykład:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

określa listę zawierającą krótką liczbę całkowitą, po której następuje BOOL.

Aby uzyskać listę **stałych VTS_,** zobacz [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="on_propnotify"></a><a name="on_propnotify"></a>ON_PROPNOTIFY

Użyj makra ON_PROPNOTIFY, aby zdefiniować wpis mapy ujścia zdarzeń do obsługi powiadomień właściwości z formantu OLE.

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Klasa, do której należy ta mapa ujścia zdarzenia.

*Identyfikator*<br/>
Identyfikator sterowania formantu OLE.

*Dispid*<br/>
Identyfikator wysyłki nieruchomości biorącej udział w powiadomieniu.

*pfnRequest (PfnRequest)*<br/>
Wskaźnik do funkcji elementu członkowskiego, która obsługuje `OnRequestEdit` powiadomienie dla tej właściwości. Ta funkcja powinna mieć typ zwracany BOOL i parametr **BOOL.** <strong>\*</strong> Ta funkcja powinna ustawić parametr na TRUE, aby umożliwić właściwość do zmiany i FALSE nie zezwalać. Funkcja powinna zwracać wartość PRAWDA, aby wskazać, że powiadomienie zostało obsłużone; w przeciwnym razie FALSE.

*pfnZanged*<br/>
Wskaźnik do funkcji elementu członkowskiego, która obsługuje `OnChanged` powiadomienie dla tej właściwości. Funkcja powinna mieć typ zwracany BOOL i parametr UINT. Funkcja powinna zwracać wartość TRUE, aby wskazać, że powiadomienie zostało obsłużone; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

*VtsParams* argument jest oddzielona spacja lista wartości od **VTS_** stałych. Jedna lub więcej z tych wartości oddzielonych spacjami (nie przecinkami) określa listę parametrów funkcji. Przykład:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

określa listę zawierającą krótką liczbę całkowitą, po której następuje BOOL.

Aby uzyskać listę **stałych VTS_,** zobacz [EVENT_CUSTOM](event-maps.md#event_custom).

## <a name="on_propnotify_range"></a><a name="on_propnotify_range"></a>ON_PROPNOTIFY_RANGE

Użyj makra ON_PROPNOTIFY_RANGE, aby zdefiniować wpis mapy ujścia zdarzeń do obsługi powiadomień właściwości z dowolnego formantu OLE o identyfikatorze formantu w ciągłym zakresie identyfikatorów.

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Klasa, do której należy ta mapa ujścia zdarzenia.

*idFirst*<br/>
Identyfikator sterowania pierwszego formantu OLE w zakresie.

*idLast*<br/>
Identyfikator sterowania ostatniego formantu OLE w zakresie.

*Dispid*<br/>
Identyfikator wysyłki nieruchomości biorącej udział w powiadomieniu.

*pfnRequest (PfnRequest)*<br/>
Wskaźnik do funkcji elementu członkowskiego, która obsługuje `OnRequestEdit` powiadomienie dla tej właściwości. Ta funkcja powinna `BOOL` mieć `UINT` typ `BOOL*` zwracany i parametry. Funkcja powinna ustawić parametr na TRUE, aby umożliwić właściwość do zmiany i FALSE nie zezwalać. Funkcja powinna zwracać wartość TRUE, aby wskazać, że powiadomienie zostało obsłużone; w przeciwnym razie FALSE.

*pfnZanged*<br/>
Wskaźnik do funkcji elementu członkowskiego, która obsługuje `OnChanged` powiadomienie dla tej właściwości. Funkcja powinna mieć `BOOL` typ zwracany i `UINT` parametr. Funkcja powinna zwracać wartość TRUE, aby wskazać, że powiadomienie zostało obsłużone; w przeciwnym razie FALSE.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="on_propnotify_reflect"></a><a name="on_propnotify_reflect"></a>ON_PROPNOTIFY_REFLECT

Makro ON_PROPNOTIFY_REFLECT, gdy jest używane w mapie ujścia zdarzeń klasy otoki formantu OLE, odbiera powiadomienia o właściwościach wysyłane przez formant, zanim zostaną obsłużone przez kontener formantu.

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Klasa, do której należy ta mapa ujścia zdarzenia.

*Dispid*<br/>
Identyfikator wysyłki nieruchomości biorącej udział w powiadomieniu.

*pfnRequest (PfnRequest)*<br/>
Wskaźnik do funkcji elementu członkowskiego, która obsługuje `OnRequestEdit` powiadomienie dla tej właściwości. Ta funkcja powinna mieć typ zwracany BOOL i parametr **BOOL.** <strong>\*</strong> Ta funkcja powinna ustawić parametr na TRUE, aby umożliwić właściwość do zmiany i FALSE nie zezwalać. Funkcja powinna zwracać wartość PRAWDA, aby wskazać, że powiadomienie zostało obsłużone; w przeciwnym razie FALSE.

*pfnZanged*<br/>
Wskaźnik do funkcji elementu członkowskiego, która obsługuje `OnChanged` powiadomienie dla tej właściwości. Funkcja powinna mieć typ zwracany BOOL i nie parametry. Funkcja powinna zwracać wartość PRAWDA, aby wskazać, że powiadomienie zostało obsłużone; w przeciwnym razie FALSE.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
