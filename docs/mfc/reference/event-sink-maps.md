---
title: Mapy wychwytywania zdarzeń
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 2cbfbc70ae14ccda95c377cb1587bf9d2a1ad3e6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837267"
---
# <a name="event-sink-maps"></a>Mapy wychwytywania zdarzeń

Gdy osadzony formant OLE wyzwala zdarzenie, kontener kontrolki otrzymuje zdarzenie przy użyciu mechanizmu zwanego "mapą ujścia zdarzeń" dostarczonym przez MFC. Ta mapa ujścia zdarzeń wyznacza funkcje obsługi dla każdego konkretnego zdarzenia, a także parametry tych zdarzeń. Aby uzyskać więcej informacji na temat map ujścia zdarzeń, zobacz artykuł dotyczący [kontenerów formantów ActiveX](../../mfc/activex-control-containers.md).

### <a name="event-sink-maps"></a>Mapy wychwytywania zdarzeń

|Nazwa|Opis|
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|Uruchamia definicję mapy ujścia zdarzeń.|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|Deklaruje mapę ujścia zdarzeń.|
|[END_EVENTSINK_MAP](#end_eventsink_map)|Zamyka definicję mapy ujścia zdarzeń.|
|[ON_EVENT](#on_event)|Definiuje procedurę obsługi zdarzeń dla określonego zdarzenia.|
|[ON_EVENT_RANGE](#on_event_range)|Definiuje procedurę obsługi zdarzeń dla określonego zdarzenia wywoływanego z zestawu kontrolek OLE.|
|[ON_EVENT_REFLECT](#on_event_reflect)|Odbiera zdarzenia wywoływane przez formant przed ich obsługą przez kontener formantu.|
|[ON_PROPNOTIFY](#on_propnotify)|Definiuje procedurę obsługi powiadomień o właściwościach z formantu OLE.|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|Definiuje procedurę obsługi powiadomień o właściwościach z zestawu kontrolek OLE.|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|Odbiera powiadomienia o właściwościach wysyłane przez formant przed ich obsługą przez kontener formantu.|

## <a name="begin_eventsink_map"></a><a name="begin_eventsink_map"></a> BEGIN_EVENTSINK_MAP

Rozpoczyna definicję mapy obiektu ujścia zdarzeń.

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa nazwę klasy kontrolki, której obiekt sink zdarzenia mapuje.

*baseClass*<br/>
Określa nazwę klasy bazowej *theClass*.

### <a name="remarks"></a>Uwagi

W pliku implementacji (. cpp), który definiuje funkcje elementu członkowskiego dla klasy, uruchom mapę ujścia zdarzeń za pomocą makra BEGIN_EVENTSINK_MAP, a następnie Dodaj wpisy makr dla każdego zdarzenia, które ma zostać powiadomione, i wypełnij mapę ujścia zdarzeń za pomocą makra END_EVENTSINK_MAP.

Aby uzyskać więcej informacji na temat map ujścia zdarzeń i kontenerów formantów OLE, zobacz artykuł dotyczący [kontenerów formantów ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="declare_eventsink_map"></a><a name="declare_eventsink_map"></a> DECLARE_EVENTSINK_MAP

Kontener OLE może zapewnić mapę ujścia zdarzeń, aby określić zdarzenia, które będą powiadamiane o kontenerze.

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>Uwagi

Użyj makra DECLARE_EVENTSINK_MAP na końcu deklaracji klasy. Następnie w. Plik CPP, który definiuje funkcje elementu członkowskiego dla klasy, użyj makra BEGIN_EVENTSINK_MAP, wpisów makr dla każdego zdarzenia, które ma zostać powiadomione, i makro END_EVENTSINK_MAP, aby zadeklarować koniec listy obiektów ujścia zdarzeń.

Aby uzyskać więcej informacji na temat map ujścia zdarzeń, zobacz artykuł dotyczący [kontenerów formantów ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="end_eventsink_map"></a><a name="end_eventsink_map"></a> END_EVENTSINK_MAP

Zamyka definicję mapy ujścia zdarzeń.

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="on_event"></a><a name="on_event"></a> ON_EVENT

Użyj makra ON_EVENT, aby zdefiniować funkcję obsługi zdarzeń dla zdarzenia wywoływanego przez formant OLE.

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasa, do której należy ta mapa ujścia zdarzeń.

*id*<br/>
Identyfikator kontrolki formantu OLE.

*DISPID*<br/>
Identyfikator wysyłania zdarzenia wywoływanego przez formant.

*pfnHandler*<br/>
Wskaźnik do funkcji składowej, która obsługuje zdarzenie. Ta funkcja powinna mieć typ zwracany BOOL i typy parametrów, które pasują do parametrów zdarzenia (zobacz *vtsParams*). Funkcja powinna zwrócić wartość TRUE, aby wskazać, że zdarzenie zostało obsłużone; w przeciwnym razie FALSE.

*vtsParams*<br/>
Sekwencja **VTS_** stałych, która określa typy parametrów dla zdarzenia. Są to te same stałe, które są używane w wpisach mapy wysyłania, takich jak DISP_FUNCTION.

### <a name="remarks"></a>Uwagi

Argument *vtsParams* jest rozdzieloną spacjami listą wartości ze stałych **VTS_** . Co najmniej jedna z tych wartości rozdzielonych spacjami (nie przecinkami) określa listę parametrów funkcji. Na przykład:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Określa listę zawierającą krótką liczbę całkowitą, a po niej wartość logiczną.

Aby uzyskać listę stałych **VTS_** , zobacz [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="on_event_range"></a><a name="on_event_range"></a> ON_EVENT_RANGE

Użyj makra ON_EVENT_RANGE, aby zdefiniować funkcję obsługi zdarzeń dla zdarzenia wywoływanego przez dowolny formant OLE o IDENTYFIKATORze kontrolki w ramach ciągłego zakresu identyfikatorów.

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasa, do której należy ta mapa ujścia zdarzeń.

*idFirst*<br/>
Identyfikator formantu pierwszego formantu OLE w zakresie.

*idLast*<br/>
Identyfikator formantu ostatniej kontrolki OLE w zakresie.

*DISPID*<br/>
Identyfikator wysyłania zdarzenia wywoływanego przez formant.

*pfnHandler*<br/>
Wskaźnik do funkcji składowej, która obsługuje zdarzenie. Ta funkcja powinna mieć typ zwracany BOOL, pierwszy parametr typu UINT (dla identyfikatora kontrolki) i dodatkowe typy parametrów, które pasują do parametrów zdarzenia (zobacz *vtsParams*). Funkcja powinna zwrócić wartość TRUE, aby wskazać, że zdarzenie zostało obsłużone; w przeciwnym razie FALSE.

*vtsParams*<br/>
Sekwencja **VTS_** stałych, która określa typy parametrów dla zdarzenia. Pierwsza stała powinna być typu VTS_I4, dla identyfikatora formantu. Są to te same stałe, które są używane w wpisach mapy wysyłania, takich jak DISP_FUNCTION.

### <a name="remarks"></a>Uwagi

Argument *vtsParams* jest rozdzieloną spacjami listą wartości ze stałych **VTS_** . Co najmniej jedna z tych wartości rozdzielonych spacjami (nie przecinkami) określa listę parametrów funkcji. Na przykład:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Określa listę zawierającą krótką liczbę całkowitą, a po niej wartość logiczną.

Aby uzyskać listę stałych **VTS_** , zobacz [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="example"></a>Przykład

Poniższy przykład ilustruje procedurę obsługi zdarzeń dla zdarzenia MouseDown, zaimplementowane dla trzech formantów (IDC_MYCTRL1 do IDC_MYCTRL3). Funkcja obsługi zdarzeń, `OnRangeMouseDown` , jest zadeklarowana w pliku nagłówkowym klasy okna dialogowego ( `CMyDlg` ) jako:

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

Poniższy kod jest zdefiniowany w pliku implementacji klasy okna dialogowego.

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="on_event_reflect"></a><a name="on_event_reflect"></a> ON_EVENT_REFLECT

ON_EVENT_REFLECT makro, gdy jest używany w mapie ujścia zdarzeń klasy otoki formantu OLE, odbiera zdarzenia wywoływane przez formant, zanim zostaną one obsłużone przez kontener kontrolki.

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasa, do której należy ta mapa ujścia zdarzeń.

*DISPID*<br/>
Identyfikator wysyłania zdarzenia wywoływanego przez formant.

*pfnHandler*<br/>
Wskaźnik do funkcji składowej, która obsługuje zdarzenie. Ta funkcja powinna mieć typ zwracany i typy parametrów, które pasują do parametrów zdarzenia (zobacz *vtsParams*). Funkcja powinna zwrócić wartość TRUE, aby wskazać, że zdarzenie zostało obsłużone; w przeciwnym razie FALSE.

*vtsParams*<br/>
Sekwencja **VTS_** stałych, która określa typy parametrów dla zdarzenia. Są to te same stałe, które są używane w wpisach mapy wysyłania, takich jak DISP_FUNCTION.

### <a name="remarks"></a>Uwagi

Argument *vtsParams* jest rozdzieloną spacjami listą wartości ze stałych **VTS_** .

Co najmniej jedna z tych wartości rozdzielonych spacjami (nie przecinkami) określa listę parametrów funkcji. Na przykład:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Określa listę zawierającą krótką liczbę całkowitą, a po niej wartość logiczną.

Aby uzyskać listę stałych **VTS_** , zobacz [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="on_propnotify"></a><a name="on_propnotify"></a> ON_PROPNOTIFY

Użyj makra ON_PROPNOTIFY, aby zdefiniować wpis mapy ujścia zdarzeń do obsługi powiadomień o właściwościach z formantu OLE.

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasa, do której należy ta mapa ujścia zdarzeń.

*id*<br/>
Identyfikator kontrolki formantu OLE.

*DISPID*<br/>
Identyfikator wysyłki właściwości uwzględnionej w powiadomieniu.

*pfnRequest*<br/>
Wskaźnik do funkcji składowej, która obsługuje `OnRequestEdit` powiadomienie dla tej właściwości. Ta funkcja powinna mieć typ zwracany BOOL i parametr **bool** <strong>\*</strong> . Ta funkcja powinna ustawić parametr na wartość TRUE, aby zezwolić na zmianę właściwości, i FAŁSZ, aby nie zezwalać. Funkcja powinna zwrócić wartość TRUE, aby wskazać, że powiadomienie zostało obsłużone; w przeciwnym razie FALSE.

*pfnChanged*<br/>
Wskaźnik do funkcji składowej, która obsługuje `OnChanged` powiadomienie dla tej właściwości. Funkcja powinna mieć typ zwracany BOOL i parametr UINT. Funkcja powinna zwrócić wartość TRUE, aby wskazać, że powiadomienie zostało obsłużone; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Argument *vtsParams* jest rozdzieloną spacjami listą wartości ze stałych **VTS_** . Co najmniej jedna z tych wartości rozdzielonych spacjami (nie przecinkami) określa listę parametrów funkcji. Na przykład:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Określa listę zawierającą krótką liczbę całkowitą, a po niej wartość logiczną.

Aby uzyskać listę stałych **VTS_** , zobacz [EVENT_CUSTOM](event-maps.md#event_custom).

## <a name="on_propnotify_range"></a><a name="on_propnotify_range"></a> ON_PROPNOTIFY_RANGE

Za pomocą makra ON_PROPNOTIFY_RANGE Zdefiniuj wpis mapy ujścia zdarzeń do obsługi powiadomień o właściwościach z dowolnych kontrolek OLE o IDENTYFIKATORze kontrolki w ramach ciągłego zakresu identyfikatorów.

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasa, do której należy ta mapa ujścia zdarzeń.

*idFirst*<br/>
Identyfikator formantu pierwszego formantu OLE w zakresie.

*idLast*<br/>
Identyfikator formantu ostatniej kontrolki OLE w zakresie.

*DISPID*<br/>
Identyfikator wysyłki właściwości uwzględnionej w powiadomieniu.

*pfnRequest*<br/>
Wskaźnik do funkcji składowej, która obsługuje `OnRequestEdit` powiadomienie dla tej właściwości. Ta funkcja powinna mieć `BOOL` zwracany typ i `UINT` `BOOL*` parametry. Funkcja powinna ustawić parametr na wartość TRUE, aby zezwolić na zmianę właściwości i FAŁSZ, aby nie zezwalać. Funkcja powinna zwrócić wartość TRUE, aby wskazać, że powiadomienie zostało obsłużone; w przeciwnym razie FALSE.

*pfnChanged*<br/>
Wskaźnik do funkcji składowej, która obsługuje `OnChanged` powiadomienie dla tej właściwości. Funkcja powinna mieć `BOOL` zwracany typ i `UINT` parametr. Funkcja powinna zwrócić wartość TRUE, aby wskazać, że powiadomienie zostało obsłużone; w przeciwnym razie FALSE.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="on_propnotify_reflect"></a><a name="on_propnotify_reflect"></a> ON_PROPNOTIFY_REFLECT

Makro ON_PROPNOTIFY_REFLECT, które jest używane w mapie ujścia zdarzeń klasy otoki formantu OLE, odbiera powiadomienia o właściwościach wysyłane przez formant, zanim będą obsługiwane przez kontener kontrolki.

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasa, do której należy ta mapa ujścia zdarzeń.

*DISPID*<br/>
Identyfikator wysyłki właściwości uwzględnionej w powiadomieniu.

*pfnRequest*<br/>
Wskaźnik do funkcji składowej, która obsługuje `OnRequestEdit` powiadomienie dla tej właściwości. Ta funkcja powinna mieć typ zwracany BOOL i parametr **bool** <strong>\*</strong> . Ta funkcja powinna ustawić parametr na wartość TRUE, aby zezwolić na zmianę właściwości, i FAŁSZ, aby nie zezwalać. Funkcja powinna zwrócić wartość TRUE, aby wskazać, że powiadomienie zostało obsłużone; w przeciwnym razie FALSE.

*pfnChanged*<br/>
Wskaźnik do funkcji składowej, która obsługuje `OnChanged` powiadomienie dla tej właściwości. Funkcja powinna mieć typ zwracany BOOL i nie ma parametrów. Funkcja powinna zwrócić wartość TRUE, aby wskazać, że powiadomienie zostało obsłużone; w przeciwnym razie FALSE.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
