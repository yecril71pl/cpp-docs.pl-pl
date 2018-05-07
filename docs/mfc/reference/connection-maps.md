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
ms.openlocfilehash: 475314edba2a11535349991db644a4915e352ae7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="connection-maps"></a>Mapy połączeń
Formanty OLE są możliwe do udostępnienia interfejsy do innych aplikacji. Te interfejsy umożliwiają dostęp z kontenera tylko do tego formantu. Jeśli formant OLE chce uzyskać dostępu do zewnętrznych interfejsów innych obiektów OLE, należy ustanowić punktu połączenia. Punkt połączenia z tym zapewnia kontrolę wychodzący dostęp do mapy wysyłania zewnętrznych, takich jak mapy zdarzeń lub funkcji powiadomień.  
  
 Microsoft Foundation Class Library zapewnia model programowania, który obsługuje punkty połączenia. W tym modelu "połączenia mapuje" służą do wyznaczenia interfejsów lub punkty połączenia OLE formantu. Mapy połączeń zawierać jedno makro dla każdego punktu połączenia. Aby uzyskać więcej informacji na mapy połączeń, zobacz [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) klasy.  
  
 Zwykle formantu zostanie obsługują tylko dwa punkty połączeń: jeden dla zdarzeń i jeden dla właściwości powiadomienia. Są one zaimplementowane przez `COleControl` klasa podstawowa i wymagane żadne dodatkowe czynności przez moduł zapisujący formantu. Wszystkie punkty połączenia dodatkowe, które mają do zaimplementowania w klasie, należy dodać ręcznie. Aby obsługiwać mapy połączeń i punkty, MFC zapewnia następujące makra:  
  
### <a name="connection-map-declaration-and-demarcation"></a>Połączenie mapy deklaracja i odgraniczenie  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_PART —](#begin_connection_part)|Deklaruje osadzonych klasy, która implementuje punkt połączenia dodatkowe (należy użyć w deklaracji klasy).|  
|[END_CONNECTION_PART —](#end_connection_part)|Kończy się deklarację punktu połączenia (należy użyć w deklaracji klasy).|  
|[CONNECTION_IID —](#connection_iid)|Określa identyfikator interfejsu punktu połączenia formantu.|  
|[DECLARE_CONNECTION_MAP —](#declare_connection_map)|Deklaruje, że mapa połączenia będą używane w klasie (należy użyć w deklaracji klasy).|  
|[BEGIN_CONNECTION_MAP —](#begin_connection_map)|Rozpoczyna się definicję planu połączenia (musi być zastosowany w implementacji klasy).|  
|[END_CONNECTION_MAP —](#end_connection_map)|Kończy definicję planu połączenia (musi być zastosowany w implementacji klasy).|  
|[CONNECTION_PART —](#connection_part)|Określa punkt połączenia w mapie połączenia formantu.|  
  
 Następujące funkcje pomagają zbiorniku ustanawiania i rozłączanie połączenia przy użyciu punkty połączeń:  
  
### <a name="initializationtermination-of-connection-points"></a>Inicjowanie/Zakończenie punktów połączenia  
  
|||  
|-|-|  
|[Afxconnectionadvise —](#afxconnectionadvise)|Ustanawia połączenie między źródłem i odbioru.|  
|[Afxconnectionunadvise —](#afxconnectionunadvise)|Przerywa połączenie między źródłem i odbioru.|  
  
##  <a name="begin_connection_part"></a>  BEGIN_CONNECTION_PART —  
 Użyj `BEGIN_CONNECTION_PART` makra, aby rozpocząć definicji punkty połączenia dodatkowych poza punkty połączenia powiadomień zdarzeń i właściwości.  
  
```   
BEGIN_CONNECTION_PART(theClass, localClass)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Określa, że nazwa klasy formantu, którego połączenie punktu to jest.  
  
 *localClass*  
 Określa nazwę klasy lokalnej, która implementuje punkt połączenia.  
  
### <a name="remarks"></a>Uwagi  
 W pliku deklaracji (.h), który definiuje funkcje Członkowskie dla klasy, należy uruchomić punkt połączenia z `BEGIN_CONNECTION_PART` makra, następnie dodać `CONNECTION_IID` makro i innych funkcji elementów członkowskich, chcesz wdrożyć, a następnie wykonaj mapy punktu połączenia z `END_CONNECTION_PART` makra.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="end_connection_part"></a>  END_CONNECTION_PART —  
 Kończy się deklaracja punktu połączenia.  
  
```   
END_CONNECTION_PART(localClass)   
```  
  
### <a name="parameters"></a>Parametry  
 *localClass*  
 Określa nazwę klasy lokalnej, która implementuje punkt połączenia.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="connection_iid"></a>  CONNECTION_IID —  
 Użyj między `BEGIN_CONNECTION_PART` i `END_CONNECTION_PART` makra, aby zdefiniować identyfikator interfejsu punktu połączenia obsługiwane przez formant OLE.  
  
```   
CONNECTION_IID(iid)   
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 Identyfikator interfejsu interfejsu wywoływane przez punkt połączenia.  
  
### <a name="remarks"></a>Uwagi  
 `iid` Argument jest interfejsem identyfikator używany do identyfikowania interfejs, który punkt połączenia będzie zwracać się o jego połączonych obiektach sink. Na przykład:  
  
 [!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]  
  
 Określa punkt połączenia, który wywołuje `ISinkInterface` interfejsu.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="declare_connection_map"></a>  DECLARE_CONNECTION_MAP —  
 Każdy `COleControl`-klasy pochodnej w programie zapewniają Mapa połączenia podaj punkty połączenia dodatkowe, które obsługuje formantu.  
  
```   
DECLARE_CONNECTION_MAP() 
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli formantu obsługuje dodatkowe punkty, użyj `DECLARE_CONNECTION_MAP` makro końca z deklaracji klasy. Następnie, w pliku .cpp, który definiuje funkcji elementów członkowskich klasy, należy użyć `BEGIN_CONNECTION_MAP` makra `CONNECTION_PART` makra dla każdego z punktów połączenia formantu i `END_CONNECTION_MAP` makra, aby zadeklarować koniec mapy połączenia.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="begin_connection_map"></a>  BEGIN_CONNECTION_MAP —  
 Każdy `COleControl`-klasy pochodnej w programie zapewniają mapy połączenia w celu określenia punktów połączenia, które będą obsługiwać formantu.  
  
```   
BEGIN_CONNECTION_MAP(theClass, theBase)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Określa nazwę klasy formantu, którego połączenie mapowania.  
  
 *theBase*  
 Określa nazwę klasy podstawowej `theClass`.  
  
### <a name="remarks"></a>Uwagi  
 W implementacji (. Pliku CPP), który definiuje funkcje Członkowskie dla klasy, uruchom Mapa połączenia z `BEGIN_CONNECTION_MAP` makra, następnie dodaj makro wpisy dla wszystkich punktów połączenia przy użyciu [connection_part —](#connection_part) makra. Na koniec Ukończ Mapa połączenia z [end_connection_map —](#end_connection_map) makra.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="end_connection_map"></a>  END_CONNECTION_MAP —  
 Kończy definicję mapy połączenia.  
  
```   
END_CONNECTION_MAP()  
```  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="connection_part"></a>  CONNECTION_PART —  
 Mapuje punktu połączenia dla formantu OLE na identyfikator określonego interfejsu.  
  
```   
CONNECTION_PART(theClass, iid, localClass)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Określa, że nazwa klasy formantu, którego połączenie punktu to jest.  
  
 `iid`  
 Identyfikator interfejsu interfejsu wywoływane przez punkt połączenia.  
  
 *localClass*  
 Określa nazwę klasy lokalnej, która implementuje punkt połączenia.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]  
  
 mapy połączenia z punktem połączenia, który wywołuje implementuje `IID_ISinkInterface` interfejsu.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="afxconnectionadvise"></a>  Afxconnectionadvise —  
 Wywołaj tę funkcję, aby nawiązać połączenie między źródłem, określony przez `pUnkSrc`i odbiorczy, określony przez `pUnkSink`.  
  
```   
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc, 
    REFIID iid, 
    LPUNKNOWN pUnkSink, 
    BOOL bRefCount, 
    DWORD FAR* pdwCookie);
```  
  
### <a name="parameters"></a>Parametry  
 `pUnkSrc`  
 Wskaźnik do obiektu, który wywołuje interfejs.  
  
 `pUnkSink`  
 Wskaźnik do obiektu, który implementuje interfejs.  
  
 `iid`  
 Identyfikator interfejsu połączenia.  
  
 `bRefCount`  
 **Wartość TRUE,** wskazuje, że tworzenie połączenie powinno powodować liczebności referencyjnej równej `pUnkSink` do jest zwiększany. **FALSE** wskazuje liczbę odwołań nie powinny być zwiększane.  
  
 `pdwCookie`  
 Wskaźnik do `DWORD` gdy zwracany jest identyfikator połączenia. Ta wartość powinien zostać przekazany jako `dwCookie` parametr `AfxConnectionUnadvise` podczas rozłączanie połączenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli połączenie zostało nawiązane; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxctl.h 

##  <a name="afxconnectionunadvise"></a>  Afxconnectionunadvise —  
 Wywołaj tę funkcję, aby rozłączyć połączenie między źródłem, określony przez `pUnkSrc`i odbiorczy, określony przez `pUnkSink`.  
  
```   
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc, 
    REFIID iid, 
    LPUNKNOWN pUnkSink, 
    BOOL bRefCount, 
    DWORD dwCookie); 
```  
  
### <a name="parameters"></a>Parametry  
 `pUnkSrc`  
 Wskaźnik do obiektu, który wywołuje interfejs.  
  
 `pUnkSink`  
 Wskaźnik do obiektu, który implementuje interfejs.  
  
 `iid`  
 Interfejs identyfikator interfejsu punktu połączenia.  
  
 `bRefCount`  
 **Wartość TRUE,** wskazuje, że rozłączanie połączenia powinno powodować liczebności referencyjnej równej `pUnkSink` być zmniejszany. **FALSE** wskazuje, że liczba odwołań nie powinny być zmniejszany.  
  
 `dwCookie`  
 Identyfikator połączenia zwrócony przez `AfxConnectionAdvise`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli połączenie zostało rozłączone; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxctl.h 

## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
