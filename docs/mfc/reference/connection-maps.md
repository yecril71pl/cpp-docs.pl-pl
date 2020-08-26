---
title: Mapy połączeń
ms.date: 11/04/2016
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 517017e9e60b86e96daa24f7822538e91c609fb4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841418"
---
# <a name="connection-maps"></a>Mapy połączeń

Formanty OLE mogą uwidaczniać interfejsy innym aplikacjom. Te interfejsy zezwalają na dostęp tylko z kontenera do tej kontrolki. Jeśli formant OLE chce uzyskać dostęp do zewnętrznych interfejsów innych obiektów OLE, należy nawiązać punkt połączenia. Ten punkt połączenia umożliwia kontrolowanie dostępu wychodzącego do zewnętrznych map wysyłania, takich jak mapy zdarzeń lub funkcje powiadomień.

Biblioteka MFC oferuje model programowania obsługujący punkty połączenia. W tym modelu "mapy połączeń" są używane do wyznaczania interfejsów lub punktów połączenia dla kontrolki OLE. Mapy połączeń zawierają jedno makro dla każdego punktu połączenia. Aby uzyskać więcej informacji na temat map połączeń, zobacz Klasa [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) .

Zazwyczaj kontrolka będzie obsługiwać tylko dwa punkty połączenia: jeden dla zdarzeń i jeden dla powiadomień o właściwościach. Są one implementowane przez `COleControl` klasę bazową i nie wymagają dodatkowej pracy przez moduł zapisujący kontroli. Wszystkie dodatkowe punkty połączenia, które mają zostać zaimplementowane w klasie, muszą być dodawane ręcznie. Aby można było obsługiwać mapy i punkty połączeń, MFC udostępnia następujące makra:

### <a name="connection-map-declaration-and-demarcation"></a>Deklaracja i rozgraniczanie mapy połączeń

|Nazwa|Opis|
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Deklaruje osadzoną klasę, która implementuje dodatkowy punkt połączenia (musi być użyta w deklaracji klasy).|
|[END_CONNECTION_PART](#end_connection_part)|Zakończenie deklaracji punktu połączenia (musi być używany w deklaracji klasy).|
|[CONNECTION_IID](#connection_iid)|Określa identyfikator interfejsu punktu połączenia kontrolki.|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Deklaruje, że mapa połączenia zostanie użyta w klasie (musi być używana w deklaracji klasy).|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Rozpoczyna definicję mapy połączeń (należy ją użyć w implementacji klasy).|
|[END_CONNECTION_MAP](#end_connection_map)|Zamyka definicję mapy połączeń (musi być używana w implementacji klasy).|
|[CONNECTION_PART](#connection_part)|Określa punkt połączenia w mapie połączeń formantu.|

Poniższe funkcje pomagają ujścia podczas ustanawiania i rozłączania połączenia przy użyciu punktów połączenia:

### <a name="initializationtermination-of-connection-points"></a>Inicjowanie/Kończenie punktów połączenia

|Nazwa|Opis|
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|Ustanawia połączenie między źródłem a obiektem sink.|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|Przerywa połączenie między źródłem a ujściam.|

## <a name="begin_connection_part"></a><a name="begin_connection_part"></a> BEGIN_CONNECTION_PART

Użyj makra BEGIN_CONNECTION_PART, aby rozpocząć definicję dodatkowych punktów połączenia wykraczających poza punkty połączenia powiadomień o zdarzeniu i właściwości.

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa nazwę klasy kontrolki, której punkt połączenia jest to.

*localClass*<br/>
Określa nazwę lokalnej klasy, która implementuje punkt połączenia.

### <a name="remarks"></a>Uwagi

W pliku deklaracji (. h), który definiuje funkcje składowe klasy, należy uruchomić punkt połączenia za pomocą makra BEGIN_CONNECTION_PART, a następnie dodać makro CONNECTION_IID i wszystkie inne funkcje elementów członkowskich, które mają zostać zaimplementowane, i ukończyć mapowanie punktu połączenia za pomocą makra END_CONNECTION_PART.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="end_connection_part"></a><a name="end_connection_part"></a> END_CONNECTION_PART

Zakończenie deklaracji punktu połączenia.

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>Parametry

*localClass*<br/>
Określa nazwę lokalnej klasy, która implementuje punkt połączenia.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="connection_iid"></a><a name="connection_iid"></a> CONNECTION_IID

Użyj między makrami BEGIN_CONNECTION_PART i END_CONNECTION_PART, aby zdefiniować identyfikator interfejsu dla punktu połączenia obsługiwanego przez formant OLE.

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
Identyfikator interfejsu wywoływany przez punkt połączenia.

### <a name="remarks"></a>Uwagi

Argument *IID* jest identyfikatorem interfejsu używanym do identyfikowania interfejsu, który zostanie wywołany przez punkt połączenia w podłączonych obiektach sink. Na przykład:

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

Określa punkt połączenia, który wywołuje `ISinkInterface` interfejs.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="declare_connection_map"></a><a name="declare_connection_map"></a> DECLARE_CONNECTION_MAP

Każda `COleControl` Klasa pochodna w programie może udostępnić mapę połączeń, aby określić dodatkowe punkty połączenia obsługiwane przez formant.

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>Uwagi

Jeśli formant obsługuje dodatkowe punkty, użyj makra DECLARE_CONNECTION_MAP na końcu deklaracji klasy. Następnie w pliku. cpp, który definiuje funkcje elementu członkowskiego dla klasy, użyj makra BEGIN_CONNECTION_MAP, CONNECTION_PART makra dla każdej z punktów połączenia kontrolki i makro END_CONNECTION_MAP, aby zadeklarować koniec mapy połączeń.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="begin_connection_map"></a><a name="begin_connection_map"></a> BEGIN_CONNECTION_MAP

Każda `COleControl` Klasa pochodna w programie może udostępnić mapę połączeń, aby określić punkty połączenia, które będą obsługiwane przez formant.

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa nazwę klasy kontrolki, której jest mapa połączenia.

*theBase*<br/>
Określa nazwę klasy bazowej *theClass*.

### <a name="remarks"></a>Uwagi

W implementacji (. CPP), który definiuje funkcje elementów członkowskich klasy, należy uruchomić mapę połączenia z makrem BEGIN_CONNECTION_MAP, a następnie dodać wpisy makr dla każdego z punktów połączenia przy użyciu makra [CONNECTION_PART](#connection_part) . Na koniec wykonaj mapowanie połączenia za pomocą makra [END_CONNECTION_MAP](#end_connection_map) .

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="end_connection_map"></a><a name="end_connection_map"></a> END_CONNECTION_MAP

Zamyka definicję mapy połączeń.

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="connection_part"></a><a name="connection_part"></a> CONNECTION_PART

Mapuje punkt połączenia dla kontrolki OLE na określony identyfikator interfejsu.

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa nazwę klasy kontrolki, której punkt połączenia jest to.

*IID*<br/>
Identyfikator interfejsu wywoływany przez punkt połączenia.

*localClass*<br/>
Określa nazwę lokalnej klasy, która implementuje punkt połączenia.

### <a name="remarks"></a>Uwagi

Na przykład:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

implementuje mapę połączenia z punktem połączenia, który wywołuje `IID_ISinkInterface` interfejs.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="afxconnectionadvise"></a><a name="afxconnectionadvise"></a> AfxConnectionAdvise

Wywołaj tę funkcję, aby nawiązać połączenie między źródłem, określonym przez *pUnkSrc*i ujściam, określonym przez *pUnkSink*.

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>Parametry

*pUnkSrc*<br/>
Wskaźnik do obiektu, który wywołuje interfejs.

*pUnkSink*<br/>
Wskaźnik do obiektu, który implementuje interfejs.

*IID*<br/>
Identyfikator interfejsu połączenia.

*bRefCount*<br/>
Wartość TRUE wskazuje, że utworzenie połączenia powinno spowodować zwiększenie liczby odwołań *pUnkSink* . Wartość FALSE wskazuje, że liczba odwołań nie powinna być zwiększana.

*pdwCookie*<br/>
Wskaźnik do wartości DWORD, w której zwracany jest identyfikator połączenia. Ta wartość powinna zostać przeniesiona jako parametr *dwCookie* do `AfxConnectionUnadvise` momentu odłączenia połączenia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli połączenie zostało nawiązane; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** 'afxctl. h

## <a name="afxconnectionunadvise"></a><a name="afxconnectionunadvise"></a> AfxConnectionUnadvise

Wywołaj tę funkcję, aby rozłączyć połączenie między źródłem, określonym przez *pUnkSrc*, a ujściam, określonym przez *pUnkSink*.

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*pUnkSrc*<br/>
Wskaźnik do obiektu, który wywołuje interfejs.

*pUnkSink*<br/>
Wskaźnik do obiektu, który implementuje interfejs.

*IID*<br/>
Identyfikator interfejsu interfejsu punktu połączenia.

*bRefCount*<br/>
Wartość TRUE wskazuje, że rozłączenie połączenia powinno spowodować zmniejszenie liczby odwołań *pUnkSink* . Wartość FALSE wskazuje, że liczba odwołań nie powinna być zmniejszana.

*dwCookie*<br/>
Identyfikator połączenia zwrócony przez `AfxConnectionAdvise` .

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli połączenie zostało rozłączone; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** 'afxctl. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
