---
title: Klasa CThreadPool
ms.date: 11/04/2016
f1_keywords:
- CThreadPool
- ATLUTIL/ATL::CThreadPool
- ATLUTIL/ATL::CThreadPool::CThreadPool
- ATLUTIL/ATL::CThreadPool::AddRef
- ATLUTIL/ATL::CThreadPool::GetNumThreads
- ATLUTIL/ATL::CThreadPool::GetQueueHandle
- ATLUTIL/ATL::CThreadPool::GetSize
- ATLUTIL/ATL::CThreadPool::GetTimeout
- ATLUTIL/ATL::CThreadPool::Initialize
- ATLUTIL/ATL::CThreadPool::QueryInterface
- ATLUTIL/ATL::CThreadPool::QueueRequest
- ATLUTIL/ATL::CThreadPool::Release
- ATLUTIL/ATL::CThreadPool::SetSize
- ATLUTIL/ATL::CThreadPool::SetTimeout
- ATLUTIL/ATL::CThreadPool::Shutdown
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
ms.openlocfilehash: 07fd470a6aeab0575f2733d72650bd695b8e2752
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915685"
---
# <a name="cthreadpool-class"></a>Klasa CThreadPool

Ta klasa udostępnia pulę wątków roboczych, które przetwarzają kolejkę elementów roboczych.

## <a name="syntax"></a>Składnia

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>Parametry

*Odpowiedzialn*<br/>
Klasa zgodna z [archetypeem procesu roboczego](../../atl/reference/worker-archetype.md) dostarczająca kod używany do przetwarzania elementów roboczych w kolejce w puli wątków.

*ThreadTraits*<br/>
Klasa dostarczająca funkcję służącą do tworzenia wątków w puli.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|Konstruktor dla puli wątków.|
|[CThreadPool::~CThreadPool](#dtor)|Destruktor dla puli wątków.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CThreadPool:: AddRef](#addref)|Implementacja programu `IUnknown::AddRef`.|
|[CThreadPool::GetNumThreads](#getnumthreads)|Wywołaj tę metodę, aby uzyskać liczbę wątków w puli.|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Wywołaj tę metodę, aby uzyskać uchwyt portu ukończenia we/wy używanego do kolejkowania elementów roboczych.|
|[CThreadPool::GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać liczbę wątków w puli.|
|[CThreadPool::GetTimeout](#gettimeout)|Wywołaj tę metodę, aby uzyskać maksymalny czas w milisekundach, przez który Pula wątków będzie czekać na zamknięcie wątku.|
|[CThreadPool:: Initialize](#initialize)|Wywołaj tę metodę, aby zainicjować pulę wątków.|
|[CThreadPool:: QueryInterface](#queryinterface)|Implementacja programu `IUnknown::QueryInterface`.|
|[CThreadPool::QueueRequest](#queuerequest)|Wywołaj tę metodę, aby kolejkować element roboczy, który ma być obsługiwany przez wątek w puli.|
|[CThreadPool:: Release](#release)|Implementacja programu `IUnknown::Release`.|
|[CThreadPool::SetSize](#setsize)|Wywołaj tę metodę, aby ustawić liczbę wątków w puli.|
|[CThreadPool::SetTimeout](#settimeout)|Wywołaj tę metodę, aby ustawić maksymalny czas (w milisekundach) oczekiwania puli wątków na zamknięcie wątku.|
|[CThreadPool::Shutdown](#shutdown)|Wywołaj tę metodę, aby zamknąć pulę wątków.|

## <a name="remarks"></a>Uwagi

Wątki w puli są tworzone i niszczone po zainicjowaniu puli, zmianie rozmiaru lub zamknięciu. Wystąpienie *procesu roboczego* klasy zostanie utworzone na stosie każdego wątku roboczego w puli. Każde wystąpienie będzie aktywne przez okres istnienia wątku.

Natychmiast po utworzeniu wątku *proces roboczy*::`Initialize` zostanie wywołany dla obiektu skojarzonego z tym wątkiem. Bezpośrednio przed zniszczeniem wątku *proces roboczy*::`Terminate` zostanie wywołany. Obie metody muszą akceptować argument **void** <strong>\*</strong> . Wartość tego argumentu jest przenoszona do puli wątków za pomocą parametru *PvWorkerParam* [CThreadPool:: Initialize](#initialize).

Gdy istnieją elementy robocze w kolejce i wątki robocze dostępne do pracy, wątek roboczy spowoduje wyciągnięcie elementu z kolejki i wywołanie `Execute` metody obiektu *Worker* dla tego wątku. Trzy elementy są następnie przenoszone do metody: element z kolejki, taki sam `pvWorkerParam` , jak *proces roboczy*:: `Initialize` i *proces roboczy*:: `Terminate`, oraz wskaźnik do [pokrywającej](/windows/desktop/api/minwinbase/ns-minwinbase-overlapped) się struktury używanej dla kolejki portu ukończenia we/wy .

Klasa *Worker* deklaruje typ elementów, które zostaną dodane do kolejki w puli wątków, dostarczając element typedef, *Worker*:: `RequestType`. Ten typ musi być w stanie rzutować do i z ULONG_PTR.

Przykładem klasy *procesu roboczego* jest [Klasa CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil. h

##  <a name="addref"></a>CThreadPool:: AddRef

Implementacja programu `IUnknown::AddRef`.

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca 1.

### <a name="remarks"></a>Uwagi

Ta klasa nie implementuje kontroli okresu istnienia przy użyciu zliczania odwołań.

##  <a name="cthreadpool"></a>CThreadPool::CThreadPool

Konstruktor dla puli wątków.

```
CThreadPool() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje wartość limitu czasu ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. Wartość domyślna to 36 sekund. W razie potrzeby można zdefiniować własną dodatnią wartość całkowitą dla tego symbolu przed uwzględnieniem atlutil. h.

##  <a name="dtor"></a>CThreadPool:: ~ CThreadPool

Destruktor dla puli wątków.

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Uwagi

Wywołania [CThreadPool:: Shutdown](#shutdown).

##  <a name="getnumthreads"></a>CThreadPool::GetNumThreads

Wywołaj tę metodę, aby uzyskać liczbę wątków w puli.

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wątków w puli.

##  <a name="getqueuehandle"></a>CThreadPool::GetQueueHandle

Wywołaj tę metodę, aby uzyskać uchwyt portu ukończenia we/wy używanego do kolejkowania elementów roboczych.

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście kolejki lub wartość NULL, jeśli Pula wątków nie została zainicjowana.

##  <a name="getsize"></a>CThreadPool:: GetSize

Wywołaj tę metodę, aby uzyskać liczbę wątków w puli.

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>Parametry

*pnNumThreads*<br/>
określoną Adres zmiennej, która po powodzeniu odbiera liczbę wątków w puli.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="gettimeout"></a>  CThreadPool::GetTimeout

Wywołaj tę metodę, aby uzyskać maksymalny czas w milisekundach, przez który Pula wątków będzie czekać na zamknięcie wątku.

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>Parametry

*pdwMaxWait*<br/>
określoną Adres zmiennej, która po sukcesie odbiera maksymalny czas w milisekundach, przez który Pula wątków czeka na zamknięcie wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta wartość limitu czasu jest używana przez [CThreadPool:: Shutdown](#shutdown) , jeśli żadna inna wartość nie zostanie dostarczona do tej metody.

##  <a name="initialize"></a>CThreadPool:: Initialize

Wywołaj tę metodę, aby zainicjować pulę wątków.

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>Parametry

*pvWorkerParam*<br/>
Parametr procesu roboczego `Initialize`, który ma zostać przesłany do metody obiektu wątku `Execute`roboczego, `Terminate` i.

*nNumThreads*<br/>
Żądana liczba wątków w puli.

Jeśli *nNumThreads* jest ujemna, jego wartość bezwzględna zostanie pomnożona przez liczbę procesorów w maszynie, aby uzyskać łączną liczbę wątków.

Jeśli *nNumThreads* ma wartość zero, ATLS_DEFAULT_THREADSPERPROC zostanie pomnożona przez liczbę procesorów w maszynie, aby uzyskać łączną liczbę wątków.  Wartość domyślna to 2 wątki na procesor. W razie potrzeby można zdefiniować własną dodatnią wartość całkowitą dla tego symbolu przed uwzględnieniem atlutil. h.

*dwStackSize*<br/>
Rozmiar stosu dla każdego wątku w puli.

*hCompletion*<br/>
Dojście obiektu do skojarzenia z portem ukończenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="queryinterface"></a>CThreadPool:: QueryInterface

Implementacja programu `IUnknown::QueryInterface`.

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Uwagi

Obiekty tej klasy mogą być pomyślnie zapytania dla `IUnknown` interfejsów i [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md) .

##  <a name="queuerequest"></a>CThreadPool::QueueRequest

Wywołaj tę metodę, aby kolejkować element roboczy, który ma być obsługiwany przez wątek w puli.

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>Parametry

*żądając*<br/>
Żądanie do umieszczenia w kolejce.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje element roboczy do kolejki. Wątki w puli wybierają elementy z kolejki w kolejności, w której zostały odebrane.

##  <a name="release"></a>CThreadPool:: Release

Implementacja programu `IUnknown::Release`.

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca 1.

### <a name="remarks"></a>Uwagi

Ta klasa nie implementuje kontroli okresu istnienia przy użyciu zliczania odwołań.

##  <a name="setsize"></a>CThreadPool:: setSize

Wywołaj tę metodę, aby ustawić liczbę wątków w puli.

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>Parametry

*nNumThreads*<br/>
Żądana liczba wątków w puli.

Jeśli *nNumThreads* jest ujemna, jego wartość bezwzględna zostanie pomnożona przez liczbę procesorów w maszynie, aby uzyskać łączną liczbę wątków.

Jeśli *nNumThreads* ma wartość zero, ATLS_DEFAULT_THREADSPERPROC zostanie pomnożona przez liczbę procesorów w maszynie, aby uzyskać łączną liczbę wątków. Wartość domyślna to 2 wątki na procesor. W razie potrzeby można zdefiniować własną dodatnią wartość całkowitą dla tego symbolu przed uwzględnieniem atlutil. h.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Jeśli liczba określonych wątków jest mniejsza niż liczba wątków aktualnie w puli, obiekt umieszcza komunikat zamknięcia w kolejce do pobrania przez wątek oczekujący. Gdy oczekujący wątek ściąga komunikat z kolejki, powiadamia pulę wątków i opuszcza procedurę wątku. Ten proces jest powtarzany, dopóki liczba wątków w puli osiągnie określoną liczbę lub do momentu, gdy żaden wątek nie zakończył się w okresie określonym przez GetTimeout [](#gettimeout)/ setTimeout.[](#settimeout) W tej sytuacji metoda zwróci wartość HRESULT odpowiadającą WAIT_TIMEOUT, a oczekujący komunikat zamknięcia zostanie anulowany.

##  <a name="settimeout"></a>CThreadPool:: setTimeout

Wywołaj tę metodę, aby ustawić maksymalny czas (w milisekundach) oczekiwania puli wątków na zamknięcie wątku.

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>Parametry

*dwMaxWait*<br/>
Żądany maksymalny czas (w milisekundach) oczekiwania puli wątków na zamknięcie wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Limit czasu jest zainicjowany do ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. Wartość domyślna to 36 sekund. W razie potrzeby można zdefiniować własną dodatnią wartość całkowitą dla tego symbolu przed uwzględnieniem atlutil. h.

Należy pamiętać, że *dwMaxWait* to czas oczekiwania puli na zamknięcie jednego wątku. Maksymalny czas, jaki można podjąć w celu usunięcia wielu wątków z puli, może być nieco mniejszy niż *dwMaxWait* pomnożony przez liczbę wątków.

##  <a name="shutdown"></a>CThreadPool:: Shutdown

Wywołaj tę metodę, aby zamknąć pulę wątków.

```
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>Parametry

*dwMaxWait*<br/>
Żądany maksymalny czas (w milisekundach) oczekiwania puli wątków na zamknięcie wątku. Jeśli wartość jest równa 0 lub nie podano wartości, ta metoda będzie używać limitu czasu ustawionego przez [CThreadPool:: setTimeout](#settimeout).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła żądanie zamknięcia do wszystkich wątków w puli. Jeśli limit czasu wygaśnie, ta metoda wywoła [TerminateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-terminatethread) na dowolnym wątku, który nie został zakończony. Ta metoda jest wywoływana automatycznie z destruktora klasy.

## <a name="see-also"></a>Zobacz także

[Interfejs IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Klasy](../../atl/reference/atl-classes.md)
