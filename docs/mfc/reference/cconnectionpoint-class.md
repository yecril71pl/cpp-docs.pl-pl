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
ms.openlocfilehash: d892ea225e3b1c1089447587eb808e56370bbb69
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952225"
---
# <a name="cconnectionpoint-class"></a>Klasa CConnectionPoint
Definiuje specjalny typ interfejs używany do komunikowania się z innymi obiektami OLE o nazwie "punkt połączenia".  
  
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
|[CConnectionPoint::GetConnections](#getconnections)|Pobiera wszystkie punkty połączenia na mapie połączenia.|  
|[CConnectionPoint::GetContainer](#getcontainer)|Pobiera kontener formantu, który jest właścicielem mapy połączenia.|  
|[CConnectionPoint::GetIID](#getiid)|Pobiera identyfikator interfejsu punktu połączenia.|  
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|Pobiera maksymalną liczbę punktów połączenia obsługiwane przez formant.|  
|[CConnectionPoint::GetNextConnection](#getnextconnection)|Pobiera wskaźnik do elementu połączenia *pos*.|  
|[CConnectionPoint::GetStartPosition](#getstartposition)|Uruchamia iteracji mapy zwracając **pozycji** wartości, które mogą zostać przekazane do `GetNextConnection` wywołania.|  
|[CConnectionPoint::OnAdvise](#onadvise)|Wywoływane przez platformę, gdy ustanawianie lub przerwanie połączenia.|  
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|Pobiera wskaźnik do zbiornika żądanego interfejsu.|  
  
## <a name="remarks"></a>Uwagi  
 W przeciwieństwie do normalnej interfejsy OLE, używanych do wdrożenia i udostępniają funkcje kontrolkę OLE punktu połączenia implementuje interfejs wychodzących, który jest w stanie inicjowania działania na inne obiekty, takie jak wyzwalania zdarzeń i powiadomień o zmianie.  
  
 Połączenie składa się z dwóch części: obiekt wywołujący interfejs o nazwie "source", a obiekt implementujący interfejs o nazwie "sink". W przypadku wystawianego punktu połączenia, źródłem umożliwia wychwytywanie do ustanawiania połączeń do samej siebie. Za pomocą mechanizmu punktu połączenia obiektu źródłowego uzyskuje wskaźnik do implementacji obiektu sink zestawu funkcji elementów członkowskich. Na przykład uruchomienie zaimplementowana przez obiekt sink zdarzenia, źródła można wywołać odpowiedniej metody implementacji obiektu sink.  
  
 Domyślnie `COleControl`— Klasa pochodna implementuje dwoma punktami połączenia: jeden dla zdarzeń i jeden dla właściwości powiadomienia o zmianie. Połączenia te są używane, odpowiednio do uruchamiania zdarzeń i powiadamiania zbiornika (na przykład formantu kontenera) po wartości właściwości została zmieniona. Również obsługiwane dla formantów OLE do zaimplementowania połączenia dodatkowe punkty. Dla każdego punktu połączenia dodatkowych zaimplementowana w klasie formantu należy zadeklarować "części połączenia", który implementuje punkt połączenia. W przypadku zastosowania co najmniej jednego punktu połączenia, należy zadeklarować pojedynczy "mapy połączenia" w Twojej klasy kontrolki.  
  
 W poniższym przykładzie pokazano mapy prostego połączenia i jedno połączenie punkt `Sample` kontrolkę OLE, składające się z dwóch fragmentów kodu: pierwszej części deklaruje mapy połączenia i punkt; druga implementuje ten mapy i punktu. Pierwszego fragmentu są wstawiane do deklaracji klasy formantu w obszarze `protected` sekcji:  
  
 [!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]  
  
 Begin_connection_part — i end_connection_part — makra zadeklarować klasy osadzone, `XSampleConnPt` (pochodną `CConnectionPoint`), który zawiera ten punkt określonego połączenia. Jeśli chcesz przesłonić `CConnectionPoint` funkcji Członkowskich lub dodać funkcje Członkowskie własny, Zadeklaruj je między tych dwóch makr. Na przykład zastąpienia connection_iid — makro `CConnectionPoint::GetIID` funkcji członkowskiej umieszczone między tych dwóch makr.  
  
 Drugi fragmentu kodu zostaną wstawione do pliku implementacji (. CPP) klasy formantu. Ten kod implementuje Mapa połączenia, która zawiera punkt połączenia dodatkowych, `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]  
  
 Po wstawieniu tych fragmentów kodu formantu OLE próbki udostępnia punkt połączenia dla `ISampleSink` interfejsu.  
  
 Zazwyczaj punkty połączenia obsługi "multiemisji", który jest możliwość emisji do wielu wychwytywanie podłączone do tego samego interfejsu. Poniższy fragment kodu przedstawia sposób osiągnąć iteracja każdego zbiornika w punkcie połączenia multiemisji:  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
 W tym przykładzie pobierana bieżącego zestawu połączeń na `SampleConnPt` punkt połączenia z wywołaniem do `CConnectionPoint::GetConnections`. Następnie wykonuje iterację za pośrednictwem połączenia i wywołania `ISampleSink::SinkFunc` dla każdego aktywnego połączenia.  
  
 Aby uzyskać więcej informacji na temat używania `CConnectionPoint`, zapoznaj się z artykułem [punkty połączenia](../../mfc/connection-points.md).  
  
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
 Wywołanie tej funkcji można pobrać wszystkich aktywnych połączeń punktu połączenia.  
  
```  
const CPtrArray* GetConnections();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do tablicy aktywnych połączeń (wychwytywanie). Niektóre wskaźniki w tablicy mogą mieć wartości NULL. Każdy wskaźnik inną niż NULL w tej tablicy można bezpiecznie konwertować na wskaźnik do interfejsu zbiornika przy użyciu operatora rzutowania.  
  
##  <a name="getcontainer"></a>  CConnectionPoint::GetContainer  
 Wywoływane przez platformę, by pobrać **IConnectionPointContainer** punktu połączenia.  
  
```  
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia wskaźnika w kontenerze; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zwykle implementowany przez begin_connection_part — makro.  
  
##  <a name="getiid"></a>  CConnectionPoint::GetIID  
 Wywoływane przez platformę, by pobrać identyfikator interfejsu punktu połączenia.  
  
```  
virtual REFIID GetIID() = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do identyfikatora interfejsu punktu połączenia  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, aby zwrócić identyfikator interfejsu dla tego punktu połączenia.  
  
##  <a name="getmaxconnections"></a>  CConnectionPoint::GetMaxConnections  
 Wywoływane przez platformę, by pobrać maksymalną liczbę połączeń obsługiwaną przez punkt połączenia.  
  
```  
virtual int GetMaxConnections();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna liczba połączeń obsługiwaną przez formant lub wartość -1, jeśli brak limitu.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja zwraca -1, wskazując brak limitu.  
  
 Należy przesłonić tę funkcję, jeśli chcesz ograniczyć liczbę wychwytywanie, które można łączyć z formantu.  
  
##  <a name="getnextconnection"></a>  CConnectionPoint::GetNextConnection  
 Pobiera wskaźnik do elementu połączenia *pos*.  
  
```  
LPUNKNOWN GetNextConnection(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Określa odwołania do **pozycji** wartość zwrócona przez poprzednie `GetNextConnection` lub [GetStartPosition](#getstartposition) wywołania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do elementu połączenia określonego przez *pos*, ani mieć wartości NULL.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest najbardziej przydatny w przypadku iteracja przez wszystkie elementy na mapie połączenia. Podczas wykonywania iteracji, pominąć wszystkie wartości null zwracane z tej funkcji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
##  <a name="getstartposition"></a>  CConnectionPoint::GetStartPosition  
 Uruchamia iteracji mapy zwracając **pozycji** wartości, które mogą zostać przekazane do [GetNextConnection](#getnextconnection) wywołania.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która wskazuje pozycję początkową, które mapy; lub **NULL** Jeśli mapy jest pusta.  
  
### <a name="remarks"></a>Uwagi  
 Sekwencja iteracji nie jest przewidywalne; w związku z tym "pierwszy element w mapie" ma specjalnego znaczenia.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CConnectionPoint::GetNextConnection](#getnextconnection).  
  
##  <a name="onadvise"></a>  CConnectionPoint::OnAdvise  
 Wywoływane przez platformę, gdy połączenie jest nawiązano lub zerwano.  
  
```  
virtual void OnAdvise(BOOL bAdvise);
```  
  
### <a name="parameters"></a>Parametry  
 *bAdvise*  
 **Wartość TRUE,**, jeśli połączenie ma zostać nawiązane, a w przeciwnym **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja nie działa.  
  
 Należy przesłonić tę funkcję, jeśli chcesz powiadomienia, gdy wychwytywanie połączyć lub rozłączyć się z punktu połączenia.  
  
##  <a name="querysinkinterface"></a>  CConnectionPoint::QuerySinkInterface  
 Pobiera wskaźnik do zbiornika żądanego interfejsu.  
  
```  
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,  
    void** ppInterface);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnkSink*  
 Identyfikator żądanego interfejsu ujścia.  
  
 *ppInterface*  
 Wskaźnik do wskaźnika interfejsu identyfikowane przez *pUnkSink*. Jeśli obiekt nie obsługuje ten interfejs \* *ppInterface* ustawiono **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)

