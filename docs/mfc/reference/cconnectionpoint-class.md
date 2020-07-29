---
title: Klasa CConnectionPoint
ms.date: 11/04/2016
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
ms.openlocfilehash: f428ec597e0e4a56788fae2455eff80b286fda39
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87183087"
---
# <a name="cconnectionpoint-class"></a>Klasa CConnectionPoint

Definiuje specjalny typ interfejsu używany do komunikowania się z innymi obiektami OLE o nazwie "punkt połączenia".

## <a name="syntax"></a>Składnia

```
class CConnectionPoint : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|Konstruuje `CConnectionPoint` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CConnectionPoint:: GetConnections](#getconnections)|Pobiera wszystkie punkty połączenia z mapy połączeń.|
|[CConnectionPoint:: getcontainerer](#getcontainer)|Pobiera kontener formantu, który jest właścicielem mapy połączeń.|
|[CConnectionPoint::GetIID](#getiid)|Pobiera identyfikator interfejsu punktu połączenia.|
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|Pobiera maksymalną liczbę punktów połączenia obsługiwanych przez formant.|
|[CConnectionPoint::GetNextConnection](#getnextconnection)|Pobiera wskaźnik do elementu Connection w *punkcie sprzedaży*.|
|[CConnectionPoint::GetStartPosition](#getstartposition)|Uruchamia iterację mapy przez zwrócenie wartości pozycji, która może zostać przeniesiona do `GetNextConnection` wywołania.|
|[CConnectionPoint:: onadvise](#onadvise)|Wywoływane przez platformę podczas ustanawiania lub przerywania połączeń.|
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|Pobiera wskaźnik do żądanego interfejsu ujścia.|

## <a name="remarks"></a>Uwagi

W przeciwieństwie do normalnych interfejsów OLE, które są używane do implementowania i uwidaczniania funkcjonalności formantu OLE, punkt połączenia implementuje interfejs wychodzący, który może inicjować akcje na innych obiektach, takich jak Wyzwalanie zdarzeń i powiadomienia o zmianach.

Połączenie składa się z dwóch części: obiektu wywołującego interfejs, nazywany "źródłem" i obiekt implementujący interfejs, nazywany "ujścia". Udostępnienie punktu połączenia umożliwia ujściam nawiązywanie połączeń z samym sobą. Za pomocą mechanizmu punktu połączenia obiekt źródłowy uzyskuje wskaźnik do implementacji ujścia zestawu funkcji Członkowskich. Na przykład aby uruchomić zdarzenie zaimplementowane przez ujścia, źródło może wywołać odpowiednią metodę implementacji ujścia.

Domyślnie `COleControl` Klasa pochodna implementuje dwa punkty połączenia: jeden dla zdarzeń i jeden dla powiadomień o zmianach właściwości. Te połączenia są używane odpowiednio do uruchamiania zdarzeń i powiadamiania ujścia (na przykład kontenera kontrolki) w przypadku zmiany wartości właściwości. Dostępna jest również obsługa formantów OLE do implementowania dodatkowych punktów połączenia. Dla każdego dodatkowego punktu połączenia zaimplementowanego w klasie formantów należy zadeklarować "część połączenia", która implementuje punkt połączenia. W przypadku zaimplementowania co najmniej jednego punktu połączenia należy również zadeklarować pojedyncze "mapowanie połączeń" w klasie kontrolki.

W poniższym przykładzie pokazano prostą mapę połączeń i jeden punkt połączenia dla `Sample` kontrolki OLE, składający się z dwóch fragmentów kodu: Pierwsza część deklaruje mapę połączenia i punkt, drugi implementuje tę mapę i punkt. Pierwszy fragment jest wstawiany do deklaracji klasy kontrolki, pod **`protected`** sekcją:

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

Makra BEGIN_CONNECTION_PART i END_CONNECTION_PART deklarują klasę osadzoną `XSampleConnPt` (pochodną od `CConnectionPoint` ) implementującą ten konkretny punkt połączenia. Jeśli chcesz przesłonić dowolne `CConnectionPoint` funkcje Członkowskie lub dodać własne funkcje członkowskie, zadeklaruj je między tymi dwoma makrami. Na przykład makro CONNECTION_IID przesłania `CConnectionPoint::GetIID` funkcję członkowską po umieszczeniu między tymi dwoma makrami.

Drugi fragment kodu zostanie wstawiony do pliku implementacji (. CPP) klasy kontrolki. Ten kod implementuje mapę połączeń, która obejmuje dodatkowy punkt połączenia `SampleConnPt` :

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

Po wstawieniu tych fragmentów kodu Przykładowa kontrolka OLE uwidacznia punkt połączenia dla `ISampleSink` interfejsu.

Zazwyczaj punkty połączenia obsługują funkcję "Multiemisja", która umożliwia emitowanie do wielu zlewów połączonych z tym samym interfejsem. Poniższy fragment kodu ilustruje sposób wykonywania multiemisji przez iterację każdego ujścia w punkcie połączenia:

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

Ten przykład pobiera bieżący zestaw połączeń w `SampleConnPt` punkcie połączenia z wywołaniem do `CConnectionPoint::GetConnections` . Następnie wykonuje iterację połączeń i wywołań `ISampleSink::SinkFunc` na każdym aktywnym połączeniu.

Aby uzyskać więcej informacji na temat korzystania z programu `CConnectionPoint` , zobacz [punkty połączenia](../../mfc/connection-points.md)w artykule.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a>CConnectionPoint::CConnectionPoint

Konstruuje `CConnectionPoint` obiekt.

```
CConnectionPoint();
```

## <a name="cconnectionpointgetconnections"></a><a name="getconnections"></a>CConnectionPoint:: GetConnections

Wywołaj tę funkcję, aby pobrać wszystkie aktywne połączenia dla punktu połączenia.

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do tablicy aktywnych połączeń (ujścia). Niektóre wskaźniki w tablicy mogą mieć wartość NULL. Każdy wskaźnik o wartości innej niż NULL w tej tablicy może być bezpiecznie konwertowany na wskaźnik do interfejsu ujścia przy użyciu operatora rzutowania.

## <a name="cconnectionpointgetcontainer"></a><a name="getcontainer"></a>CConnectionPoint:: getcontainerer

Wywoływane przez platformę, by pobrać `IConnectionPointContainer` dla punktu połączenia.

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, wskaźnik do kontenera; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle implementowana przez makro BEGIN_CONNECTION_PART.

## <a name="cconnectionpointgetiid"></a><a name="getiid"></a>CConnectionPoint::GetIID

Wywoływane przez platformę, by pobrać identyfikator interfejsu punktu połączenia.

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do identyfikatora interfejsu punktu połączenia.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję, aby zwrócić identyfikator interfejsu dla tego punktu połączenia.

## <a name="cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a>CConnectionPoint::GetMaxConnections

Wywoływane przez platformę, by pobrać maksymalną liczbę połączeń obsługiwaną przez punkt połączenia.

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba połączeń obsługiwanych przez formant lub-1, jeśli nie ma żadnego limitu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja zwraca-1, co oznacza brak limitu.

Zastąp tę funkcję, jeśli chcesz ograniczyć liczbę zlewów, które mogą łączyć się z kontrolką.

## <a name="cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a>CConnectionPoint::GetNextConnection

Pobiera wskaźnik do elementu Connection w *punkcie sprzedaży*.

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Określa odwołanie do wartości pozycji zwróconej przez poprzednie `GetNextConnection` lub [GetStartPosition](#getstartposition) wywołanie.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu Connection określonego przez *pos*lub null.

### <a name="remarks"></a>Uwagi

Ta funkcja jest najbardziej przydatna do iterowania przez wszystkie elementy na mapie połączeń. Podczas iteracji Pomiń wszystkie wartości NULL zwracane przez tę funkcję.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

## <a name="cconnectionpointgetstartposition"></a><a name="getstartposition"></a>CConnectionPoint::GetStartPosition

Uruchamia iterację mapy przez zwrócenie wartości pozycji, która może zostać przeniesiona do wywołania [GetNextConnection](#getnextconnection) .

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji wskazująca na pozycję początkową dla iteracji mapy; lub wartość NULL, jeśli mapa jest pusta.

### <a name="remarks"></a>Uwagi

Sekwencja iteracji nie jest przewidywalna; w związku z tym "pierwszy element w mapie" nie ma specjalnego znaczenia.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CConnectionPoint:: GetNextConnection](#getnextconnection).

## <a name="cconnectionpointonadvise"></a><a name="onadvise"></a>CConnectionPoint:: onadvise

Wywoływane przez platformę, gdy połączenie jest ustanawiane lub zerwane.

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>Parametry

*bAdvise*<br/>
PRAWDA, jeśli nawiązywane jest połączenie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Domyślna implementacja nie robi nic.

Zastąp tę funkcję, jeśli chcesz, aby powiadomienie, gdy ujścia lub odłączą się od punktu połączenia.

## <a name="cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a>CConnectionPoint::QuerySinkInterface

Pobiera wskaźnik do żądanego interfejsu ujścia.

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>Parametry

*pUnkSink*<br/>
Identyfikator żądanego interfejsu ujścia.

*ppInterface*<br/>
Wskaźnik do wskaźnika interfejsu identyfikowanego przez *pUnkSink*. Jeśli obiekt nie obsługuje tego interfejsu, \* *ppInterface* ma wartość null.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="see-also"></a>Zobacz także

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
