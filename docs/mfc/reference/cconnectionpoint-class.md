---
title: Klasa CConnectionPoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CConnectionPoint
- AFXDISP/CConnectionPoint
- AFXDISP/CConnectionPoint::CConnectionPoint
- AFXDISP/CConnectionPoint::GetConnections
- AFXDISP/CConnectionPoint::GetContainer
- AFXDISP/CConnectionPoint::GetIID
- AFXDISP/CConnectionPoint::GetMaxConnections
- AFXDISP/CConnectionPoint::GetNextConnection
- AFXDISP/CConnectionPoint::GetStartPosition
- AFXDISP/CConnectionPoint::OnAdvise
- AFXDISP/CConnectionPoint::QuerySinkInterface
dev_langs:
- C++
helpviewer_keywords:
- CConnectionPoint [MFC], CConnectionPoint
- CConnectionPoint [MFC], GetConnections
- CConnectionPoint [MFC], GetContainer
- CConnectionPoint [MFC], GetIID
- CConnectionPoint [MFC], GetMaxConnections
- CConnectionPoint [MFC], GetNextConnection
- CConnectionPoint [MFC], GetStartPosition
- CConnectionPoint [MFC], OnAdvise
- CConnectionPoint [MFC], QuerySinkInterface
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b092c6a097d39c3114193c578bc37c179ca0df7
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336202"
---
# <a name="cconnectionpoint-class"></a>Klasa CConnectionPoint
Definiuje specjalny rodzaj interfejsu używanego do komunikacji z innymi obiektami OLE, o nazwie "punkt połączenia".  
  
## <a name="syntax"></a>Składnia  
  
```  
class CConnectionPoint : public CCmdTarget  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|Konstruuje `CConnectionPoint` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CConnectionPoint::GetConnections](#getconnections)|Pobiera wszystkie punkty połączenia w mapie połączenia.|  
|[CConnectionPoint::GetContainer](#getcontainer)|Pobiera kontener formantu, który jest właścicielem mapy połączeń.|  
|[CConnectionPoint::GetIID](#getiid)|Pobiera identyfikator interfejsu punktu połączenia.|  
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|Pobiera maksymalną liczbę punktów połączenia obsługiwane przez kontrolkę.|  
|[CConnectionPoint::GetNextConnection](#getnextconnection)|Pobiera wskaźnik do elementu połączenia w *pos*.|  
|[CConnectionPoint::GetStartPosition](#getstartposition)|Uruchamia iteracji mapy, zwracając wartość pozycji, które mogą być przekazywane do `GetNextConnection` wywołania.|  
|[CConnectionPoint::OnAdvise](#onadvise)|Metoda wywoływana przez platformę, gdy ustanawianie lub przerwanie połączenia.|  
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|Pobiera wskaźnik do interfejsu żądanego ujścia.|  
  
## <a name="remarks"></a>Uwagi  
 W przeciwieństwie do normalnego interfejsy OLE, które są używane do implementowania rejestracji i udostępniają funkcje kontrolkę OLE, punkt połączenia implementuje interfejsu wychodzącego, która jest w stanie inicjowania działania na inne obiekty, takie jak wyzwalanie zdarzeń i powiadomień o zmianie.  
  
 Połączenie składa się z dwóch części: obiekt wywołujący interfejs o nazwie "źródło", a obiekt implementujący interfejs o nazwie "sink". Dzięki uwidocznieniu działania punktu połączenia, źródłem umożliwia ujścia do nawiązywania połączeń z samym sobą. Za pośrednictwem punktu połączenia mechanizmu obiekt źródłowy uzyskuje wskaźnik do implementacji obiektu sink zestaw elementów członkowskich. Na przykład aby wyzwolić zdarzenie implementowany przez obiekt sink, źródła można wywołać odpowiedniej metody wdrożenia ujścia.  
  
 Domyślnie `COleControl`-klasy pochodnej implementuje dwa punkty połączenia: jeden dla zdarzeń i jeden dla właściwości powiadomienia o zmianie. Te połączenia są używane, odpowiednio, inicjowanie zdarzeń i do powiadamiania ujścia (na przykład, kontrolki kontenera), gdy wartość właściwości została zmieniona. Również obsługiwane dla formantów OLE zaimplementować dodatkowe połączenie punktów. Dla każdego punktu połączenia dodatkowe zaimplementowana w klasie kontrolki należy zadeklarować "część połączenia", który implementuje punkt połączenia. W przypadku zastosowania jednego lub więcej punktów połączenia, należy zadeklarować pojedynczy "map połączenia" w klasie kontrolki.  
  
 W poniższym przykładzie pokazano mapy prostego połączenia i jedno połączenie punkt `Sample` kontrolkę OLE, składający się z dwóch fragmentów kodu: pierwszy fragment deklaruje mapie połączenia, a punkt; drugi implementuje tej mapy i punkt. Pierwszy fragment jest wstawiany do deklaracji klasy kontrolki, w obszarze **chronione** sekcji:  
  
 [!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]  
  
 Makra BEGIN_CONNECTION_PART i END_CONNECTION_PART zadeklarować klasie osadzonej `XSampleConnPt` (pochodną `CConnectionPoint`), który zawiera ten punkt określonego połączenia. Jeśli chcesz przesłonić `CConnectionPoint` funkcji składowych lub Dodaj funkcje Członkowskie samodzielnie, zadeklarować je między te dwa makra. Na przykład zastąpienia CONNECTION_IID — makro `CConnectionPoint::GetIID` funkcja elementu członkowskiego umieszczone między te dwa makra.  
  
 Drugi fragment kodu jest wstawiany do pliku implementacji (. CPP) Twojej klasy kontrolki. Ten kod implementuje Mapa połączenia, która zawiera punkt połączenia dodatkowych, `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]  
  
 Po wstawieniu te fragmenty kodu kontrolki OLE przykładowe uwidacznia punkt połączenia dla `ISampleSink` interfejsu.  
  
 Zwykle punkty połączenia obsługują "multiemisji", który jest możliwość emisji do wielu ujść podłączone do tego samego interfejsu. Poniższy fragment kodu przedstawia sposób wykonania multiemisji, iterując przez każdy obiekt sink dla punktu połączenia:  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
 W tym przykładzie pobiera bieżący zestaw połączeń na `SampleConnPt` punkt połączenia z wywołaniem `CConnectionPoint::GetConnections`. Następnie wykonuje iterację przez połączenia i wywołania `ISampleSink::SinkFunc` dla każdego aktywnego połączenia.  
  
 Aby uzyskać więcej informacji na temat korzystania z `CConnectionPoint`, zapoznaj się z artykułem [punkty połączenia](../../mfc/connection-points.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CConnectionPoint`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
  
##  <a name="cconnectionpoint"></a>  CConnectionPoint::CConnectionPoint  
 Konstruuje `CConnectionPoint` obiektu.  
  
```  
CConnectionPoint();
```  
  
##  <a name="getconnections"></a>  CConnectionPoint::GetConnections  
 Wywołaj tę funkcję, aby pobrać wszystkie aktywne połączenia punktu połączenia.  
  
```  
const CPtrArray* GetConnections();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do tablicy aktywnych połączeń (ujścia). Niektóre wskaźników w tablicy może mieć wartości NULL. Każdy wskaźnik innych niż NULL w tej tablicy można bezpiecznie przekonwertować na wskaźnik do interfejsu ujścia, za pomocą operatora rzutowania.  
  
##  <a name="getcontainer"></a>  CConnectionPoint::GetContainer  
 Wywoływane przez platformę, by pobrać `IConnectionPointContainer` dla punktu połączenia.  
  
```  
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, wskaźnik do kontenera; w przeciwnym razie wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zwykle implementowany przez BEGIN_CONNECTION_PART — makro.  
  
##  <a name="getiid"></a>  CConnectionPoint::GetIID  
 Metoda wywoływana przez platformę, by pobrać identyfikator interfejsu punktu połączenia.  
  
```  
virtual REFIID GetIID() = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do identyfikatora interfejsu punktu połączenia  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, aby zwrócić identyfikator interfejsu dla tego punktu połączenia.  
  
##  <a name="getmaxconnections"></a>  CConnectionPoint::GetMaxConnections  
 Metoda wywoływana przez platformę, by pobrać maksymalną liczbę połączeń obsługiwanych przez punkt połączenia.  
  
```  
virtual int GetMaxConnections();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna liczba połączeń obsługiwanych przez formant lub wartość -1, jeśli brak limitu.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja zwraca -1, bez ograniczeń.  
  
 Należy przesłonić tę funkcję, jeśli chcesz ograniczyć liczbę ujścia, które można nawiązać połączenia z kontrolą.  
  
##  <a name="getnextconnection"></a>  CConnectionPoint::GetNextConnection  
 Pobiera wskaźnik do elementu połączenia w *pos*.  
  
```  
LPUNKNOWN GetNextConnection(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *punktu sprzedaży*  
 Określa odwołanie do wartości pozycji zwrócony przez poprzednie `GetNextConnection` lub [GetStartPosition](#getstartposition) wywołania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do określony przez element połączenia *pos*, lub wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest najbardziej przydatne do iteracji na elementach na mapie połączenia. Podczas iteracji, należy pominąć wszystkie zwrócone w wyniku tej funkcji na wartości null.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
##  <a name="getstartposition"></a>  CConnectionPoint::GetStartPosition  
 Uruchamia iteracji mapy, zwracając wartość pozycji, które mogą być przekazywane do [GetNextConnection](#getnextconnection) wywołania.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, która wskazuje pozycja początkowa które mapy; lub wartość NULL, jeśli mapa jest pusta.  
  
### <a name="remarks"></a>Uwagi  
 Sekwencja iteracji nie jest przewidywalne; Dlatego "pierwszego elementu w mapie" ma specjalnego znaczenia.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CConnectionPoint::GetNextConnection](#getnextconnection).  
  
##  <a name="onadvise"></a>  CConnectionPoint::OnAdvise  
 Metoda wywoływana przez platformę, gdy połączenie jest nawiązano lub zerwano.  
  
```  
virtual void OnAdvise(BOOL bAdvise);
```  
  
### <a name="parameters"></a>Parametry  
 *bAdvise*  
 Wartość TRUE, jeśli połączenie zostanie nawiązane; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja nic nie robi.  
  
 Należy przesłonić tę funkcję, chcąc powiadomień podczas ujść nawiązać lub Odłącz od punktu połączenia.  
  
##  <a name="querysinkinterface"></a>  CConnectionPoint::QuerySinkInterface  
 Pobiera wskaźnik do interfejsu żądanego ujścia.  
  
```  
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,  
    void** ppInterface);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnkSink*  
 Identyfikator interfejs obiektu sink, żądana.  
  
 *ppInterface*  
 Wskaźnik do wskaźnika interfejsu identyfikowane przez *pUnkSink*. Jeśli obiekt nie obsługuje ten interfejs \* *ppInterface* ma wartość NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
## <a name="see-also"></a>Zobacz też  
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)

