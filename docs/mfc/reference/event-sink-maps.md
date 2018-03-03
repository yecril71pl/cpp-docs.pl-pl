---
title: Obiekt Sink zdarzenia mapy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 309474220f081a0eca67d0f83ead21c59eb649e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="event-sink-maps"></a>Mapy wychwytywania zdarzeń
Gdy osadzonego formantu OLE wyzwala zdarzenie, formantu kontenera odbiera zdarzenia przy użyciu mechanizmu, nazywany "sink mapę zdarzeń," dostarczonych przez MFC. Ta mapa obiekt sink zdarzenia Określa funkcje programu obsługi dla każdego konkretnego zdarzenia, a także parametry tych zdarzeń. Aby uzyskać więcej informacji dotyczących mapy wychwytywania zdarzeń, zobacz artykuł [kontenery formantów ActiveX](../../mfc/activex-control-containers.md).  
  
### <a name="event-sink-maps"></a>Mapy wychwytywania zdarzeń  
  
|||  
|-|-|  
|[BEGIN_EVENTSINK_MAP —](#begin_eventsink_map)|Uruchamia definicję planu obiekt sink zdarzenia.|  
|[DECLARE_EVENTSINK_MAP —](#declare_eventsink_map)|Deklaruje mapy obiekt sink zdarzenia.|  
|[END_EVENTSINK_MAP —](#end_eventsink_map)|Kończy definicję planu obiekt sink zdarzenia.|  
|[ON_EVENT —](#on_event)|Określa program obsługi zdarzeń dla określonego zdarzenia.|  
|[ON_EVENT_RANGE —](#on_event_range)|Określa program obsługi zdarzeń dla określonego zdarzenia wywoływane z zestawu formantów OLE.|  
|[ON_EVENT_REFLECT —](#on_event_reflect)|Odbiera zdarzenia wywoływane przez formant przed są obsługiwane przy użyciu formantu kontenera.|  
|[ON_PROPNOTIFY —](#on_propnotify)|Określa program obsługi do obsługi powiadomień właściwość z formantem OLE.|  
|[ON_PROPNOTIFY_RANGE —](#on_propnotify_range)|Określa obsługę obsługiwanie właściwości powiadomień z zestawu formantów OLE.|  
|[ON_PROPNOTIFY_REFLECT —](#on_propnotify_reflect)|Odbiera powiadomienia właściwości przed są obsługiwane przy użyciu formantu kontenera wysłany przez formant.|  
  
##  <a name="begin_eventsink_map"></a>BEGIN_EVENTSINK_MAP —  
 Rozpoczyna się definicję planu obiekt sink zdarzenia.  
  
```   
BEGIN_EVENTSINK_MAP(theClass, baseClass)  
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Określa, że nazwa klasy formantu, której obiekt sink zdarzenia mapowania.  
  
 `baseClass`  
 Określa nazwę klasy podstawowej `theClass`.  
  
### <a name="remarks"></a>Uwagi  
 W pliku implementacji (.cpp), który definiuje funkcje Członkowskie dla klasy, należy uruchomić Mapa obiekt sink zdarzenia z `BEGIN_EVENTSINK_MAP` makra, Dodaj makro wpisy dla każdego zdarzenia, które ma być powiadamiany o i ukończyć Mapa obiekt sink zdarzenia z `END_EVENTSINK_MAP` makra.  
  
 Aby uzyskać więcej informacji o mapy wychwytywania zdarzeń i kontenery formantów OLE, zobacz artykuł [kontenery formantów ActiveX](../../mfc/activex-control-containers.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="declare_eventsink_map"></a>DECLARE_EVENTSINK_MAP —  
 Kontener OLE zapewniają mapy obiekt sink zdarzenia określone zdarzenia, które z kontenera zostanie powiadomiony o.  
  
```   
DECLARE_EVENTSINK_MAP()   
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj `DECLARE_EVENTSINK_MAP` makro końca z deklaracji klasy. Następnie w. Funkcje pliku CPP, który definiuje element członkowski klasy, należy użyć `BEGIN_EVENTSINK_MAP` makra, makro wpisy dla każdego zdarzenia, które ma być powiadamiany o i `END_EVENTSINK_MAP` makra, aby zadeklarować na końcu listy obiekt sink zdarzenia.  
  
 Aby uzyskać więcej informacji dotyczących mapy wychwytywania zdarzeń, zobacz artykuł [kontenery formantów ActiveX](../../mfc/activex-control-containers.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  
  
##  <a name="end_eventsink_map"></a>END_EVENTSINK_MAP —  
 Kończy definicję planu obiekt sink zdarzenia.  
  
```   
END_EVENTSINK_MAP()   
```  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="on_event"></a>ON_EVENT —  
 Użyj `ON_EVENT` makra, aby zdefiniować funkcję obsługi zdarzeń dla zdarzenia wywoływane przez kontrolkę OLE.  
  
```   
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams) 
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Klasy, do którego należy ta mapa obiekt sink zdarzenia.  
  
 `id`  
 Identyfikator formantu formantu OLE.  
  
 `dispid`  
 Identyfikator wysyłania zdarzenia wywoływane przez formant.  
  
 `pfnHandler`  
 Wskaźnik do funkcji członkowskiej, która obsługuje zdarzenie. Ta funkcja ma **BOOL** zwracany typ i typy parametrów, zgodnych parametrów zdarzenia (zobacz `vtsParams`). Funkcja powinna zwrócić **TRUE** wskazująca zdarzenia został obsłużony, a w przeciwnym razie **FALSE**.  
  
 `vtsParams`  
 Sekwencja **VTS_** stałe, które określa typy parametrów zdarzenia. Są to stałe tej samej, które są używane w wpisy mapy wysyłania, takich jak `DISP_FUNCTION`.  
  
### <a name="remarks"></a>Uwagi  
 `vtsParams` Argument jest rozdzielonej spacjami listy wartości z **VTS_** stałe. Co najmniej jeden z tych wartości, rozdzielając je spacjami (nie przecinkami) określa listę parametrów funkcji. Na przykład:  
  
 [!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Określa listę zawierającą krótka liczba całkowita, a następnie **BOOL**.  
  
 Aby uzyskać listę **VTS_** stałe, zobacz [event_custom —](event-maps.md#event_custom).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="on_event_range"></a>ON_EVENT_RANGE —  
 Użyj `ON_EVENT_RANGE` makra, aby zdefiniować funkcję obsługi zdarzeń dla zdarzenia wywoływane przez żadnego formantu OLE o identyfikator formantu znajdującego się ciągły zakres identyfikatorów.  
  
```   
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Klasy, do którego należy ta mapa obiekt sink zdarzenia.  
  
 `idFirst`  
 Identyfikator formantu pierwszą kontrolkę OLE z zakresu.  
  
 `idLast`  
 Identyfikator formantu ostatni formant OLE w zakresie.  
  
 `dispid`  
 Identyfikator wysyłania zdarzenia wywoływane przez formant.  
  
 `pfnHandler`  
 Wskaźnik do funkcji członkowskiej, która obsługuje zdarzenie. Ta funkcja ma **BOOL** zwracany typ, pierwszy parametr typu **UINT** (dla Identyfikatora formantu) i typy dodatkowych parametrów, zgodnych parametrów zdarzenia (zobacz `vtsParams`). Funkcja powinna zwrócić **TRUE** wskazująca zdarzenia został obsłużony, a w przeciwnym razie **FALSE**.  
  
 `vtsParams`  
 Sekwencja **VTS_** stałe, które określa typy parametrów zdarzenia. Stała pierwszy powinien być typu **VTS_I4**, identyfikatora formantu. Są to stałe tej samej, które są używane w wpisy mapy wysyłania, takich jak `DISP_FUNCTION`.  
  
### <a name="remarks"></a>Uwagi  
 `vtsParams` Argument jest rozdzielonej spacjami listy wartości z **VTS_** stałe. Co najmniej jeden z tych wartości, rozdzielając je spacjami (nie przecinkami) określa listę parametrów funkcji. Na przykład:  
  
 [!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Określa listę zawierającą krótka liczba całkowita, a następnie **BOOL**.  
  
 Aby uzyskać listę **VTS_** stałe, zobacz [event_custom —](event-maps.md#event_custom).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano program obsługi zdarzeń dla zdarzenia MouseDown zaimplementowano trzy formantów ( `IDC_MYCTRL1` za pośrednictwem `IDC_MYCTRL3`). Do funkcji obsługi zdarzeń `OnRangeMouseDown`, jest zadeklarowany w pliku nagłówka klasy okien dialogowych ( `CMyDlg`) jako:  
  
 [!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]  
  
 Poniższy kod jest zdefiniowany w pliku implementacji klasy okna dialogowego.  
  
 [!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="on_event_reflect"></a>ON_EVENT_REFLECT —  
 `ON_EVENT_REFLECT` Makra, gdy jest używany w przypadku mapy zbiornika klasy otoki formantu OLE odbiera zdarzenia wywoływane przez formant przed są obsługiwane przy użyciu formantu kontenera.  
  
```   
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams) 
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Klasy, do którego należy ta mapa obiekt sink zdarzenia.  
  
 identyfikator DISPID  
 Identyfikator wysyłania zdarzenia wywoływane przez formant.  
  
 `pfnHandler`  
 Wskaźnik do funkcji członkowskiej, która obsługuje zdarzenie. Ta funkcja ma **BOOL** zwracany typ i typy parametrów, zgodnych parametrów zdarzenia (zobacz `vtsParams`). Funkcja powinna zwrócić **TRUE** wskazująca zdarzenia został obsłużony, a w przeciwnym razie **FALSE**.  
  
 `vtsParams`  
 Sekwencja **VTS_** stałe, które określa typy parametrów zdarzenia. Są to stałe tej samej, które są używane w wpisy mapy wysyłania, takich jak `DISP_FUNCTION`.  
  
### <a name="remarks"></a>Uwagi  
 `vtsParams` Argument jest rozdzielonej spacjami listy wartości z **VTS_** stałe.  
  
 Co najmniej jeden z tych wartości, rozdzielając je spacjami (nie przecinkami) określa listę parametrów funkcji. Na przykład:  
  
 [!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Określa listę zawierającą krótka liczba całkowita, a następnie **BOOL**.  
  
 Aby uzyskać listę **VTS_** stałe, zobacz [event_custom —](event-maps.md#event_custom).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="on_propnotify"></a>ON_PROPNOTIFY —  
 Użyj `ON_PROPNOTIFY` makro do definiowania wpisu mapy obiekt sink zdarzenia do obsługi powiadomień właściwość z formantem OLE.  
  
```   
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Klasy, do którego należy ta mapa obiekt sink zdarzenia.  
  
 `id`  
 Identyfikator formantu formantu OLE.  
  
 `dispid`  
 Identyfikator wysyłania właściwości objętego powiadomienia.  
  
 `pfnRequest`  
 Wskaźnik do funkcji członkowskiej, która obsługuje **OnRequestEdit** powiadomienia dla tej właściwości. Ta funkcja ma **BOOL** zwracany typ i **BOOL\***  parametru. Tej funkcji należy ustawić dla parametru **TRUE** umożliwia właściwości do zmiany i **FALSE** do odrzucenia. Funkcja powinna zwrócić **TRUE** wskazująca powiadomienia został obsłużony, a w przeciwnym razie **FALSE**.  
  
 `pfnChanged`  
 Wskaźnik do funkcji członkowskiej, która obsługuje **OnChanged** powiadomienia dla tej właściwości. Funkcja powinna mieć **BOOL** zwracany typ i **UINT** parametru. Funkcja powinna zwrócić **TRUE** aby wskazać, że powiadomienia jest obsługiwany, a w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 `vtsParams` Argument jest rozdzielonej spacjami listy wartości z **VTS_** stałe. Co najmniej jeden z tych wartości, rozdzielając je spacjami (nie przecinkami) określa listę parametrów funkcji. Na przykład:  
  
 [!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Określa listę zawierającą krótka liczba całkowita, a następnie **BOOL**.  
  
 Aby uzyskać listę **VTS_** stałe, zobacz [event_custom —](event-maps.md#event_custom).  
  
##  <a name="on_propnotify_range"></a>ON_PROPNOTIFY_RANGE —  
 Użyj `ON_PROPNOTIFY_RANGE` makro do definiowania wpisu mapy obiekt sink zdarzenia do obsługi powiadomień właściwości z żadnym formantem OLE o identyfikator formantu znajdującego się ciągły zakres identyfikatorów.  
  
```  
 
ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Klasy, do którego należy ta mapa obiekt sink zdarzenia.  
  
 `idFirst`  
 Identyfikator formantu pierwszą kontrolkę OLE z zakresu.  
  
 `idLast`  
 Identyfikator formantu ostatni formant OLE w zakresie.  
  
 `dispid`  
 Identyfikator wysyłania właściwości objętego powiadomienia.  
  
 `pfnRequest`  
 Wskaźnik do funkcji członkowskiej, która obsługuje **OnRequestEdit** powiadomienia dla tej właściwości. Ta funkcja ma **BOOL** zwracany typ i **UINT** i **BOOL\***  parametrów. Funkcja należy ustawić dla parametru **TRUE** umożliwia właściwości do zmiany i **FALSE** nie zezwala na. Funkcja powinna zwrócić **TRUE** aby wskazać, że powiadomienia jest obsługiwany, a w przeciwnym razie **FALSE**.  
  
 `pfnChanged`  
 Wskaźnik do funkcji członkowskiej, która obsługuje **OnChanged** powiadomienia dla tej właściwości. Funkcja powinna mieć **BOOL** zwracany typ i **UINT** parametru. Funkcja powinna zwrócić **TRUE** aby wskazać, że powiadomienia jest obsługiwany, a w przeciwnym razie **FALSE**.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="on_propnotify_reflect"></a>ON_PROPNOTIFY_REFLECT —  
 `ON_PROPNOTIFY_REFLECT` Makra, gdy jest używany w przypadku mapy zbiornika klasy otoki formantu OLE, otrzymuje powiadomienia właściwości przed są obsługiwane przy użyciu formantu kontenera wysłany przez formant.  
  
```  
 
ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Klasy, do którego należy ta mapa obiekt sink zdarzenia.  
  
 `dispid`  
 Identyfikator wysyłania właściwości objętego powiadomienia.  
  
 `pfnRequest`  
 Wskaźnik do funkcji członkowskiej, która obsługuje **OnRequestEdit** powiadomienia dla tej właściwości. Ta funkcja ma **BOOL** zwracany typ i **BOOL\***  parametru. Tej funkcji należy ustawić dla parametru **TRUE** umożliwia właściwości do zmiany i **FALSE** do odrzucenia. Funkcja powinna zwrócić **TRUE** wskazująca powiadomienia został obsłużony, a w przeciwnym razie **FALSE**.  
  
 `pfnChanged`  
 Wskaźnik do funkcji członkowskiej, która obsługuje **OnChanged** powiadomienia dla tej właściwości. Funkcja powinna mieć **BOOL** zwracany typ i bez parametrów. Funkcja powinna zwrócić **TRUE** wskazująca powiadomienia został obsłużony, a w przeciwnym razie **FALSE**.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
    
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
