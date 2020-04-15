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
ms.openlocfilehash: ce72c156ab31b742a42d2960923fc56afff656c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369429"
---
# <a name="cconnectionpoint-class"></a>Klasa CConnectionPoint

Definiuje specjalny typ interfejsu używanego do komunikowania się z innymi obiektami OLE, nazywany "punktem połączenia".

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
|[CConnectionPoint::GetConnections](#getconnections)|Pobiera wszystkie punkty połączenia na mapie połączenia.|
|[CConnectionPoint::GetContainer](#getcontainer)|Pobiera kontener formantu, który jest właścicielem mapy połączenia.|
|[CConnectionPoint::GetIID](#getiid)|Pobiera identyfikator interfejsu punktu połączenia.|
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|Pobiera maksymalną liczbę punktów połączenia obsługiwanych przez formant.|
|[CConnectionPoint::GetNextConnection](#getnextconnection)|Pobiera wskaźnik do elementu połączenia w *punkcie pos*.|
|[CConnectionPoint::GetStartPosition](#getstartposition)|Rozpoczyna iterację mapy, zwracając wartość POSITION, która może `GetNextConnection` zostać przekazana do wywołania.|
|[CConnectionPoint::OnAdvise](#onadvise)|Wywoływana przez strukturę podczas ustanawiania lub przerywania połączeń.|
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|Pobiera wskaźnik do żądanego interfejsu ujścia.|

## <a name="remarks"></a>Uwagi

W przeciwieństwie do normalnych interfejsów OLE, które są używane do implementacji i uwidaczniania funkcji formantu OLE, punkt połączenia implementuje interfejs wychodzący, który jest w stanie zainicjować akcje na innych obiektach, takich jak wypalanie zdarzeń i powiadomienia o zmianach.

Połączenie składa się z dwóch części: obiektu wywołującego interfejs, zwanego "źródłem" i obiektu implementującego interfejs, zwanego "sink". Przez uwidacznianie punktu połączenia, źródło umożliwia pochłaniacze do ustanowienia połączeń do siebie. Za pośrednictwem mechanizmu punktu połączenia obiekt źródłowy uzyskuje wskaźnik do implementacji ujścia zestawu funkcji członkowskich. Na przykład, aby wywołać zdarzenie zaimplementowane przez zlew, źródło można wywołać odpowiednią metodę implementacji ujścia.

Domyślnie klasa `COleControl`pochodna implementuje dwa punkty połączenia: jeden dla zdarzeń i jeden dla powiadomień o zmianie właściwości. Połączenia te są używane, odpowiednio, do wpalania zdarzeń i powiadamiania o zlewie (na przykład kontenera formantu) po zmianie wartości właściwości. Dostępna jest również pomoc techniczna dla formantów OLE w celu zaimplementowania dodatkowych punktów połączenia. Dla każdego dodatkowego punktu połączenia zaimplementowanego w klasie kontrolnej należy zadeklarować "część połączenia", która implementuje punkt połączenia. Jeśli zaimplementujesz jeden lub więcej punktów połączenia, należy również zadeklarować jedną "mapę połączenia" w klasie kontrolnej.

W poniższym przykładzie pokazano prostą mapę `Sample` połączenia i jeden punkt połączenia dla formantu OLE, składający się z dwóch fragmentów kodu: pierwsza część deklaruje mapę połączenia i punkt; drugi implementuje tę mapę i punkt. Pierwszy fragment jest wstawiany do deklaracji klasy kontrolnej, w sekcji **chronionej:**

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

Makra BEGIN_CONNECTION_PART i END_CONNECTION_PART deklarują klasę osadzoną `XSampleConnPt` (wywodzącą się z `CConnectionPoint`), która implementuje ten określony punkt połączenia. Jeśli chcesz zastąpić wszystkie `CConnectionPoint` funkcje członkowskie lub dodać własne funkcje członkowskie, zadeklaruj je między tymi dwoma makrami. Na przykład makro CONNECTION_IID zastępuje funkcję elementu `CConnectionPoint::GetIID` członkowskiego po umieszczeniu między tymi dwoma makrami.

Drugi fragment kodu jest wstawiany do pliku implementacji (. CPP) klasy kontrolnej. Ten kod implementuje mapę połączenia, która `SampleConnPt`zawiera dodatkowy punkt połączenia:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

Po wstawieniu tych fragmentów kodu, sample OLE kontroli `ISampleSink` udostępnia punkt połączenia dla interfejsu.

Zazwyczaj punkty połączenia obsługują "multiemisji", czyli możliwość emisji do wielu zlewozmywaków podłączonych do tego samego interfejsu. Poniższy fragment kodu pokazuje, jak wykonać multiemisji przez iteracji przez każdego ujścia na punkcie połączenia:

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

W tym przykładzie pobiera bieżący `SampleConnPt` zestaw połączeń w `CConnectionPoint::GetConnections`punkcie połączenia z wywołaniem . Następnie iteruje za pośrednictwem połączeń `ISampleSink::SinkFunc` i wywołuje na każdym aktywnym połączeniu.

Aby uzyskać więcej `CConnectionPoint`informacji na temat korzystania z programu , zobacz artykuł [Punkty połączenia](../../mfc/connection-points.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a>CConnectionPoint::CConnectionPoint

Konstruuje `CConnectionPoint` obiekt.

```
CConnectionPoint();
```

## <a name="cconnectionpointgetconnections"></a><a name="getconnections"></a>CConnectionPoint::GetConnections

Wywołanie tej funkcji, aby pobrać wszystkie aktywne połączenia dla punktu połączenia.

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do tablicy aktywnych połączeń (pochłaniaczy). Niektóre wskaźniki w tablicy może być NULL. Każdy wskaźnik nienajmowy w tej tablicy można bezpiecznie przekonwertować na wskaźnik do interfejsu ujścia za pomocą operatora rzutowania.

## <a name="cconnectionpointgetcontainer"></a><a name="getcontainer"></a>CConnectionPoint::GetContainer

Wywoływane przez strukturę, `IConnectionPointContainer` aby pobrać dla punktu połączenia.

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, wskaźnik do kontenera; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj implementowana przez makro BEGIN_CONNECTION_PART.

## <a name="cconnectionpointgetiid"></a><a name="getiid"></a>CConnectionPoint::GetIID

Wywoływana przez platformę do pobierania identyfikatora interfejsu punktu połączenia.

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do identyfikatora interfejsu punktu połączenia.

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji należy zastąpić tę funkcję, aby zwrócić identyfikator interfejsu dla tego punktu połączenia.

## <a name="cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a>CConnectionPoint::GetMaxConnections

Wywoływana przez platformę do pobierania maksymalnej liczby połączeń obsługiwanych przez punkt połączenia.

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba połączeń obsługiwanych przez formant lub -1, jeśli nie ma limitu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja zwraca wartość -1, wskazując bez limitu.

Zastąd w tej funkcji, jeśli chcesz ograniczyć liczbę pochłaniaczy, które mogą łączyć się z formantem.

## <a name="cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a>CConnectionPoint::GetNextConnection

Pobiera wskaźnik do elementu połączenia w *punkcie pos*.

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Określa odwołanie do wartości POSITION zwróconej `GetNextConnection` przez poprzednie wywołanie [getstartposition.](#getstartposition)

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu połączenia określonego przez *poz*lub NULL.

### <a name="remarks"></a>Uwagi

Ta funkcja jest najbardziej przydatna do iteracji przez wszystkie elementy na mapie połączenia. Podczas iteracji, pominąć wszelkie NULLs zwrócone z tej funkcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

## <a name="cconnectionpointgetstartposition"></a><a name="getstartposition"></a>CConnectionPoint::GetStartPosition

Rozpoczyna iterację mapy, zwracając wartość POSITION, która może zostać przekazana do wywołania [GetNextConnection.](#getnextconnection)

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION wskazująca pozycję początkową dla iteracji mapy; lub NULL, jeśli mapa jest pusta.

### <a name="remarks"></a>Uwagi

Sekwencja iteracji nie jest przewidywalna; w związku z tym "pierwszy element na mapie" nie ma szczególnego znaczenia.

### <a name="example"></a>Przykład

  Zobacz przykład [CConnectionPoint::GetNextConnection](#getnextconnection).

## <a name="cconnectionpointonadvise"></a><a name="onadvise"></a>CConnectionPoint::OnAdvise

Wywoływana przez platformę, gdy połączenie jest ustanawiane lub łamane.

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>Parametry

*bAdvise*<br/>
PRAWDA, jeśli połączenie jest nawiązywane; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Domyślna implementacja nic nie robi.

Zastąd w tej funkcji należy zastąpić powiadomienie, gdy pochłaniacze łączą się z punktem połączenia lub odłączają go od niego.

## <a name="cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a>CConnectionPoint::QuerySinkInterface

Pobiera wskaźnik do żądanego interfejsu ujścia.

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>Parametry

*pUnkSink (własnek)*<br/>
Identyfikator interfejsu ujścia jest wymagane.

*ppInterface (polski)*<br/>
Wskaźnik do wskaźnika interfejsu identyfikowany przez *pUnkSink*. Jeśli obiekt nie obsługuje tego \* interfejsu, *ppInterface* jest ustawiona na WARTOŚĆ NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="see-also"></a>Zobacz też

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
