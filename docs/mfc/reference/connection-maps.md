---
title: Mapy połączeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1af235a597b70ac736ccd11de429d99e184d37b6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399642"
---
# <a name="connection-maps"></a>Mapy połączeń

Formanty OLE będą mogli uwidacznia interfejsów do innych aplikacji. Te interfejsy zezwalanie na dostęp tylko z kontenera do tego formantu. Jeśli kontrolkę OLE chce uzyskać dostęp zewnętrzne interfejsy innymi obiektami OLE, należy ustanowić punktu połączenia. Punkt połączenia z tym umożliwia wychodzący dostęp do mapy wysyłania zewnętrznych, takich jak mapy zdarzeń lub funkcje powiadomień formantu.

Biblioteki klas Microsoft Foundation udostępnia model programowania, który obsługuje punkty połączenia. W tym modelu "połączenia mapuje" są używane do wyznaczenia interfejsy lub punkty połączenia do sterowania OLE. Mapy połączeń zawierają jeden makra dla każdego punktu połączenia. Aby uzyskać więcej informacji na temat mapy połączeń, zobacz [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) klasy.

Zazwyczaj formant będzie obsługiwać tylko dwa punkty połączeń: jeden dla zdarzeń i jeden dla właściwości powiadomień. Są one zaimplementowane przez `COleControl` klasy bazowej i wymagane żadne dodatkowe czynności przez moduł zapisujący kontroli. Potrzebne do zaimplementowania w klasie punkty dodatkowych połączeń, należy dodać ręcznie. Aby zapewnić obsługę mapy połączeń i punktów, biblioteka MFC zawiera następujące makra:

### <a name="connection-map-declaration-and-demarcation"></a>Połączenie mapy deklaracja i odgraniczenie

|||
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Deklaruje osadzone klasę, która implementuje punkt połączenia dodatkowe (muszą być używane w deklaracji klasy).|
|[END_CONNECTION_PART](#end_connection_part)|Kończy się deklarację punktu połączenia (muszą być używane w deklaracji klasy).|
|[CONNECTION_IID](#connection_iid)|Określa identyfikator interfejsu punktu połączenia formantu.|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Deklaruje, że mapę połączenia będą używane w klasie (muszą być używane w deklaracji klasy).|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Rozpoczyna się definicji mapy połączeń (muszą być używane w implementacji klasy).|
|[END_CONNECTION_MAP](#end_connection_map)|Kończy definicję mapy połączeń (muszą być używane w implementacji klasy).|
|[CONNECTION_PART](#connection_part)|Określa punkt połączenia w mapie połączenia formantu.|

Następujące funkcje pomagają obiekt sink w tworzeniu i rozłączanie połączenia za pomocą punktów połączenia:

### <a name="initializationtermination-of-connection-points"></a>Inicjowanie/zakończeniem punktów połączenia

|||
|-|-|
|[Afxconnectionadvise —](#afxconnectionadvise)|Ustanawia połączenie między źródłem i ujścia.|
|[Afxconnectionunadvise —](#afxconnectionunadvise)|Przerywa połączenie między źródła i ujścia.|

##  <a name="begin_connection_part"></a>  BEGIN_CONNECTION_PART

Aby rozpocząć definicji punktów dodatkowego połączenia po przekroczeniu punkty połączenia powiadomień zdarzeń i właściwości, należy użyć BEGIN_CONNECTION_PART — makro.

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa, że nazwa klasy kontrolki, którego połączenie punktu to.

*localClass*<br/>
Określa nazwę klasy lokalnej, która implementuje punkt połączenia.

### <a name="remarks"></a>Uwagi

W pliku deklaracji (.h), który definiuje funkcji elementów członkowskich dla swojej klasy Uruchom punkt połączenia z BEGIN_CONNECTION_PART — makro, a następnie dodaj CONNECTION_IID — makro i innych funkcji Członkowskich, które chcesz wdrożyć i zakończyć połączenie z punkt mapy za pomocą END_CONNECTION_PART — makro.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="end_connection_part"></a>  END_CONNECTION_PART

Kończy się deklarację punktu połączenia.

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>Parametry

*localClass*<br/>
Określa nazwę klasy lokalnej, która implementuje punkt połączenia.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="connection_iid"></a>  CONNECTION_IID

Aby korzystać z między BEGIN_CONNECTION_PART i END_CONNECTION_PART makra zdefiniować identyfikator interfejsu punktu połączenia obsługiwane przez Twoją kontrolą OLE.

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
Identyfikator interfejsu interfejs o nazwie przez punkt połączenia.

### <a name="remarks"></a>Uwagi

*Iid* argument jest interfejsem identyfikator używany do identyfikowania interfejsu, który punkt połączenia będzie wybierany na swoich połączonych ujścia. Na przykład:

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

Określa punkt połączenia, który wywołuje `ISinkInterface` interfejsu.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="declare_connection_map"></a>  DECLARE_CONNECTION_MAP

Każdy `COleControl`-klasy pochodnej w programie może zapewnić mapy połączenia w celu określenia punktów dodatkowe połączenie, które obsługuje formant.

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>Uwagi

Jeśli formant obsługuje dodatkowe punkty, należy użyć DECLARE_CONNECTION_MAP — makro na końcu deklaracją klasy. Następnie plik .cpp, w którym zdefiniowano funkcji elementów członkowskich klasy, użyj BEGIN_CONNECTION_MAP — makro, CONNECTION_PART makra dla każdego formantu punkty połączenia i END_CONNECTION_MAP — makro do deklarowania koniec mapy połączeń.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="begin_connection_map"></a>  BEGIN_CONNECTION_MAP

Każdy `COleControl`-klasy pochodnej w programie może zapewnić mapę połączenia, aby określić punkty połączenia obsługiwane przez kontrolkę.

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa, że nazwa klasy kontrolki Mapuj którego połączenie.

*theBase*<br/>
Określa nazwę klasy bazowej *theClass*.

### <a name="remarks"></a>Uwagi

W implementacji (. Plik CPP), który definiuje składową funkcje dla swojej klasy, rozpoczynać mapy połączeń BEGIN_CONNECTION_MAP — makro, a następnie dodać wpisy makra dla każdego z punktów połączenia przy użyciu [CONNECTION_PART](#connection_part) makra. Na koniec Ukończ mapy połączenia za pomocą [END_CONNECTION_MAP](#end_connection_map) makra.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="end_connection_map"></a>  END_CONNECTION_MAP

Kończy definicję mapy połączeń.

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="connection_part"></a>  CONNECTION_PART

Mapowany punkt połączenia dla kontrolki OLE identyfikatora dla określonego interfejsu.

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa, że nazwa klasy kontrolki, którego połączenie punktu to.

*IID*<br/>
Identyfikator interfejsu interfejs o nazwie przez punkt połączenia.

*localClass*<br/>
Określa nazwę klasy lokalnej, która implementuje punkt połączenia.

### <a name="remarks"></a>Uwagi

Na przykład:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

implementuje mapę połączenia z punktem połączenia, który wywołuje `IID_ISinkInterface` interfejsu.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="afxconnectionadvise"></a>  Afxconnectionadvise —

Wywołaj tę funkcję, aby nawiązać połączenie między źródłem określony przez *pUnkSrc*, jak i ujście, określony przez *pUnkSink*.

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
Wartość TRUE wskazuje, czy tworzy się połączenie powinno spowodować, że licznik odwołań *pUnkSink* rośnie. Wartość FALSE wskazuje, że licznik odwołań nie powinien być zwiększane.

*pdwCookie*<br/>
Wskaźnik do DWORD, gdy zwracany jest identyfikator połączenia. Ta wartość ma być przekazywany jako *dwCookie* parametr `AfxConnectionUnadvise` podczas rozłączania połączenia.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli połączenie zostało nawiązane; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

##  <a name="afxconnectionunadvise"></a>  Afxconnectionunadvise —

Wywołaj tę funkcję, aby rozłączyć połączenie między źródłem określony przez *pUnkSrc*, jak i ujście, określony przez *pUnkSink*.

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
Interfejs identyfikator interfejsu punktu połączenia.

*bRefCount*<br/>
Wartość TRUE wskazuje, że rozłączanie połączenia powinno spowodować, że licznik odwołań *pUnkSink* do zmniejszenia. Wartość FALSE wskazuje, że licznik odwołań nie powinny być zmniejszony.

*dwCookie*<br/>
Identyfikator połączenia, zwracany przez `AfxConnectionAdvise`.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli połączenie zostało rozłączone; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
