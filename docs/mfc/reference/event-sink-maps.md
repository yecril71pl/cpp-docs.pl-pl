---
title: Mapy wychwytywania zdarzeń
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.maps
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 8e33636253b269692f87f99980b9da0cd60867ee
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285584"
---
# <a name="event-sink-maps"></a>Mapy wychwytywania zdarzeń

Gdy osadzonego formantu OLE uruchamia zdarzenie, kontener formantu odbiera zdarzenia przy użyciu mechanizmu o nazwie "sink mapę zdarzeń," dostarczonych przez MFC. Ta mapa obiekt sink zdarzenia wyznacza funkcji obsługi dla każdego określonego zdarzenia, jak również parametry tych zdarzeń. Aby uzyskać więcej informacji na temat mapy wychwytywania zdarzeń, zobacz artykuł [kontenery kontrolek ActiveX](../../mfc/activex-control-containers.md).

### <a name="event-sink-maps"></a>Mapy wychwytywania zdarzeń

|||
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|Uruchamia definicji mapę ujścia zdarzeń.|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|Deklaruje mapę ujścia zdarzeń.|
|[END_EVENTSINK_MAP](#end_eventsink_map)|Kończy definicję mapę ujścia zdarzeń.|
|[ON_EVENT](#on_event)|Określa program obsługi zdarzeń dla określonego zdarzenia.|
|[ON_EVENT_RANGE](#on_event_range)|Określa program obsługi zdarzeń dla określonego zdarzenia wywoływane z zestawu formantów OLE.|
|[ON_EVENT_REFLECT](#on_event_reflect)|Odbiera zdarzenia wywoływane przez formant przed są obsługiwane przez kontener formantu.|
|[ON_PROPNOTIFY](#on_propnotify)|Definiuje procedury obsługi na potrzeby obsługi powiadomień właściwości z formantem OLE.|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|Definiuje procedury obsługi na potrzeby obsługi powiadomień właściwości z zestawem formantów OLE.|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|Odbiera powiadomienia właściwości przed są obsługiwane przez kontener formantu wysłany przez kontrolkę.|

##  <a name="begin_eventsink_map"></a>  BEGIN_EVENTSINK_MAP

Rozpoczyna się definicji mapy obiektu sink zdarzenia.

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa, że nazwa klasy kontrolki, w których obiekt sink zdarzenia Mapuj.

*baseClass*<br/>
Określa nazwę klasy bazowej *theClass*.

### <a name="remarks"></a>Uwagi

W pliku implementacji (.cpp), który definiuje funkcji elementów członkowskich dla swojej klasy rozpoczynać Mapa ujścia zdarzeń BEGIN_EVENTSINK_MAP — makro, a następnie dodać wpisy makra dla każdego zdarzenia otrzymywać powiadomienia o, a następnie ukończ mapy ujścia zdarzeń za pomocą END_EVENTSINK_MAP — makro.

Aby uzyskać więcej informacji o mapy wychwytywania zdarzeń i kontenery kontrolek OLE, zobacz artykuł [kontenery kontrolek ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="declare_eventsink_map"></a>  DECLARE_EVENTSINK_MAP

Kontener OLE zapewniają Mapa ujścia zdarzeń, aby określić zdarzenia, które kontenera zostanie powiadomiony o.

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>Uwagi

Użyj DECLARE_EVENTSINK_MAP — makro na końcu deklaracją klasy. Następnie w. Plik CPP, który definiuje funkcji elementów członkowskich dla tej klasy, użyj BEGIN_EVENTSINK_MAP — makro, wpisy makra dla każdego zdarzenia, aby otrzymywać powiadomienia o i END_EVENTSINK_MAP — makro, aby zadeklarować na końcu listy obiekt sink zdarzenia.

Aby uzyskać więcej informacji na temat mapy wychwytywania zdarzeń, zobacz artykuł [kontenery kontrolek ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

##  <a name="end_eventsink_map"></a>  END_EVENTSINK_MAP

Kończy definicję na mapie obiektu sink zdarzenia.

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="on_event"></a>  ON_EVENT

ON_EVENT — makro umożliwia definiowanie funkcji procedury obsługi zdarzeń dla zdarzenia wywoływane przez kontrolkę OLE.

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasa, do której należy ta mapa obiekt sink zdarzenia.

*id*<br/>
Identyfikator formantu kontrolki OLE.

*dispid*<br/>
Identyfikator wysyłania zdarzenia wywoływane przez formant.

*pfnHandler*<br/>
Wskaźnik do funkcji składowej, która obsługuje zdarzenie. Ta funkcja powinna mieć BOOL, zwracać typ i typy parametrów, zgodnych parametrów zdarzenia (zobacz *vtsParams*). Funkcja powinna zwrócić wartość TRUE, aby wskazać, że zdarzenia został obsłużony; w przeciwnym razie wartość FALSE.

*vtsParams*<br/>
Sekwencja **VTS_** stałych, które określa typy parametrów zdarzenia. Są to ten sam stałych, które są używane w wpisy mapy wysyłania, takich jak DISP_FUNCTION.

### <a name="remarks"></a>Uwagi

*VtsParams* argument jest rozdzielonej spacjami listy wartości z **VTS_** stałe. Co najmniej jeden z tych wartości, rozdzielone spacjami (nie przecinki) określa listę parametrów funkcji. Na przykład:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Określa listę zawierającą krótka liczba całkowita, a następnie typu wartość logiczna.

Aby uzyskać listę **VTS_** stałych, zobacz [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="on_event_range"></a>  ON_EVENT_RANGE

ON_EVENT_RANGE — makro umożliwia definiowanie funkcji procedury obsługi zdarzeń dla zdarzenia wywoływane przez dowolną kontrolkę OLE mających Identyfikator kontrolki, w ramach ciągły zakres identyfikatorów.

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasa, do której należy ta mapa obiekt sink zdarzenia.

*idFirst*<br/>
Identyfikator formantu pierwszą kontrolkę OLE z zakresu.

*idLast*<br/>
Identyfikator formantu ostatnia kontrolka OLE w zakresie.

*dispid*<br/>
Identyfikator wysyłania zdarzenia wywoływane przez formant.

*pfnHandler*<br/>
Wskaźnik do funkcji składowej, która obsługuje zdarzenie. Ta funkcja powinna mieć BOOL, zwraca typ, pierwszy parametr typu UINT (na identyfikator kontrolki) i typy dodatkowych parametrów, zgodnych parametrów zdarzenia (zobacz *vtsParams*). Funkcja powinna zwrócić wartość TRUE, aby wskazać, że zdarzenia został obsłużony; w przeciwnym razie wartość FALSE.

*vtsParams*<br/>
Sekwencja **VTS_** stałych, które określa typy parametrów zdarzenia. Pierwszy — stała powinien być typu VTS_I4, aby uzyskać identyfikator kontrolki. Są to ten sam stałych, które są używane w wpisy mapy wysyłania, takich jak DISP_FUNCTION.

### <a name="remarks"></a>Uwagi

*VtsParams* argument jest rozdzielonej spacjami listy wartości z **VTS_** stałe. Co najmniej jeden z tych wartości, rozdzielone spacjami (nie przecinki) określa listę parametrów funkcji. Na przykład:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Określa listę zawierającą krótka liczba całkowita, a następnie typu wartość logiczna.

Aby uzyskać listę **VTS_** stałych, zobacz [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano program obsługi zdarzeń, zdarzenia MouseDown zaimplementowane dla trzy kontrolki (IDC_MYCTRL1 za pośrednictwem IDC_MYCTRL3). Funkcja obsługi zdarzenia `OnRangeMouseDown`, jest zadeklarowana w pliku nagłówkowym klasy okna dialogowego ( `CMyDlg`) jako:

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

Poniższy kod jest zdefiniowany w pliku implementacji klasy okna dialogowego.

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="on_event_reflect"></a>  ON_EVENT_REFLECT

ON_EVENT_REFLECT — makro, gdy jest używana w przypadku ujścia mapy klasy otoki kontrolkę OLE, odbiera zdarzenia wywoływane przez formant przed są obsługiwane przez kontener formantu.

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasa, do której należy ta mapa obiekt sink zdarzenia.

*dispid*<br/>
Identyfikator wysyłania zdarzenia wywoływane przez formant.

*pfnHandler*<br/>
Wskaźnik do funkcji składowej, która obsługuje zdarzenie. Ta funkcja powinna mieć BOOL, zwracać typ i typy parametrów, zgodnych parametrów zdarzenia (zobacz *vtsParams*). Funkcja powinna zwrócić wartość TRUE, aby wskazać, że zdarzenia został obsłużony; w przeciwnym razie wartość FALSE.

*vtsParams*<br/>
Sekwencja **VTS_** stałych, które określa typy parametrów zdarzenia. Są to ten sam stałych, które są używane w wpisy mapy wysyłania, takich jak DISP_FUNCTION.

### <a name="remarks"></a>Uwagi

*VtsParams* argument jest rozdzielonej spacjami listy wartości z **VTS_** stałe.

Co najmniej jeden z tych wartości, rozdzielone spacjami (nie przecinki) określa listę parametrów funkcji. Na przykład:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Określa listę zawierającą krótka liczba całkowita, a następnie typu wartość logiczna.

Aby uzyskać listę **VTS_** stałych, zobacz [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="on_propnotify"></a>  ON_PROPNOTIFY

ON_PROPNOTIFY — makro umożliwia definiowanie wpisu mapowania obiektu sink zdarzenia do obsługi powiadomień właściwości z formantem OLE.

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasa, do której należy ta mapa obiekt sink zdarzenia.

*id*<br/>
Identyfikator formantu kontrolki OLE.

*dispid*<br/>
Identyfikator wysyłania właściwości, które są zaangażowane w powiadomieniu.

*pfnRequest*<br/>
Wskaźnik do funkcji składowej, która obsługuje `OnRequestEdit` powiadomienia dla tej właściwości. Ta funkcja powinna mieć BOOL, zwracany typ i **BOOL** <strong>\*</strong> parametru. Ta funkcja powinna Ustaw parametr Zezwalaj na zmianę właściwości ma wartość TRUE i FALSE, aby nie zezwalać. Funkcja powinna zwrócić wartość TRUE, aby wskazać, że powiadomienia został obsłużony; w przeciwnym razie wartość FALSE.

*pfnChanged*<br/>
Wskaźnik do funkcji składowej, która obsługuje `OnChanged` powiadomienia dla tej właściwości. Funkcja powinna mieć BOOL, zwracać typ i parametrem UINT. Funkcja powinna zwrócić wartość TRUE, aby wskazać, że powiadomienia został obsłużony; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

*VtsParams* argument jest rozdzielonej spacjami listy wartości z **VTS_** stałe. Co najmniej jeden z tych wartości, rozdzielone spacjami (nie przecinki) określa listę parametrów funkcji. Na przykład:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Określa listę zawierającą krótka liczba całkowita, a następnie typu wartość logiczna.

Aby uzyskać listę **VTS_** stałych, zobacz [EVENT_CUSTOM](event-maps.md#event_custom).

##  <a name="on_propnotify_range"></a>  ON_PROPNOTIFY_RANGE

ON_PROPNOTIFY_RANGE — makro umożliwia definiowanie wpisu mapowania obiektu sink zdarzenia do obsługi powiadomień właściwości z dowolną kontrolkę OLE mających Identyfikator kontrolki, w ramach ciągły zakres identyfikatorów.

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasa, do której należy ta mapa obiekt sink zdarzenia.

*idFirst*<br/>
Identyfikator formantu pierwszą kontrolkę OLE z zakresu.

*idLast*<br/>
Identyfikator formantu ostatnia kontrolka OLE w zakresie.

*dispid*<br/>
Identyfikator wysyłania właściwości, które są zaangażowane w powiadomieniu.

*pfnRequest*<br/>
Wskaźnik do funkcji składowej, która obsługuje `OnRequestEdit` powiadomienia dla tej właściwości. Ta funkcja powinna mieć `BOOL` zwracany typ i `UINT` i `BOOL*` parametrów. Funkcja powinna Ustaw parametr Zezwalaj na zmianę właściwości ma wartość TRUE i FALSE, aby nie zezwalać. Funkcja powinna zwrócić wartość TRUE, aby wskazać, że powiadomienia został obsłużony; w przeciwnym razie wartość FALSE.

*pfnChanged*<br/>
Wskaźnik do funkcji składowej, która obsługuje `OnChanged` powiadomienia dla tej właściwości. Funkcja powinna mieć `BOOL` zwracany typ i `UINT` parametru. Funkcja powinna zwrócić wartość TRUE, aby wskazać, że powiadomienia został obsłużony; w przeciwnym razie wartość FALSE.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="on_propnotify_reflect"></a>  ON_PROPNOTIFY_REFLECT

ON_PROPNOTIFY_REFLECT — makro, gdy jest używana w przypadku ujścia mapy klasy otoki kontrolkę OLE, odbiera powiadomienia właściwości przed są obsługiwane przez kontener formantu wysłany przez kontrolkę.

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasa, do której należy ta mapa obiekt sink zdarzenia.

*dispid*<br/>
Identyfikator wysyłania właściwości, które są zaangażowane w powiadomieniu.

*pfnRequest*<br/>
Wskaźnik do funkcji składowej, która obsługuje `OnRequestEdit` powiadomienia dla tej właściwości. Ta funkcja powinna mieć BOOL, zwracany typ i **BOOL** <strong>\*</strong> parametru. Ta funkcja powinna Ustaw parametr Zezwalaj na zmianę właściwości ma wartość TRUE i FALSE, aby nie zezwalać. Funkcja powinna zwrócić wartość TRUE, aby wskazać, że powiadomienia został obsłużony; w przeciwnym razie wartość FALSE.

*pfnChanged*<br/>
Wskaźnik do funkcji składowej, która obsługuje `OnChanged` powiadomienia dla tej właściwości. Funkcja powinna mieć BOOL, zwracać typ i bez parametrów. Funkcja powinna zwrócić wartość TRUE, aby wskazać, że powiadomienia został obsłużony; w przeciwnym razie wartość FALSE.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
