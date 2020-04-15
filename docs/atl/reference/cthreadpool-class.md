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
ms.openlocfilehash: 0b970915aa07fe2d1af2b3a07345d5b19826be69
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330565"
---
# <a name="cthreadpool-class"></a>Klasa CThreadPool

Ta klasa udostępnia pulę wątków roboczych, które przetwarzają kolejkę elementów roboczych.

## <a name="syntax"></a>Składnia

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>Parametry

*Pracownik*<br/>
Klasa zgodna z [archetypem procesu roboczego](../../atl/reference/worker-archetype.md) dostarczającym kod używany do przetwarzania elementów roboczych w kolejce w puli wątków.

*ThreadTraits (ThreadTraits)*<br/>
Klasa zapewniająca funkcję używaną do tworzenia wątków w puli.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|Konstruktor puli wątków.|
|[CThreadPool::~CThreadPool](#dtor)|Destruktor puli wątków.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CThreadPool::AddRef](#addref)|Wdrożenie `IUnknown::AddRef`programu .|
|[CThreadPool::GetNumThreads](#getnumthreads)|Wywołanie tej metody, aby uzyskać liczbę wątków w puli.|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Wywołanie tej metody, aby uzyskać dojście portu zakończenia we/wy używane do kolejkowania elementów roboczych.|
|[CThreadPool::GetSize](#getsize)|Wywołanie tej metody, aby uzyskać liczbę wątków w puli.|
|[CThreadPool::GetTimeout](#gettimeout)|Wywołanie tej metody, aby uzyskać maksymalny czas w milisekundach, że pula wątku będzie czekać na wątek do zamknięcia.|
|[CThreadPool::Inicjalizuj](#initialize)|Wywołanie tej metody, aby zainicjować puli wątków.|
|[CThreadPool::QueryInterface](#queryinterface)|Wdrożenie `IUnknown::QueryInterface`programu .|
|[CThreadPool::QueueRequest](#queuerequest)|Wywołanie tej metody do kolejki elementu pracy, które mają być obsługiwane przez wątek w puli.|
|[CThreadPool::Zwolnij](#release)|Wdrożenie `IUnknown::Release`programu .|
|[CThreadPool::SetSize](#setsize)|Wywołanie tej metody, aby ustawić liczbę wątków w puli.|
|[CThreadPool::SetTimeout](#settimeout)|Wywołanie tej metody, aby ustawić maksymalny czas w milisekundach, że pula wątku będzie czekać na wątek do zamknięcia.|
|[CThreadPool::Zamknięcie](#shutdown)|Wywołanie tej metody, aby zamknąć pulę wątków.|

## <a name="remarks"></a>Uwagi

Wątki w puli są tworzone i niszczone, gdy pula jest inicjowana, zmieniana lub zamykana. Wystąpienie klasy *Worker* zostanie utworzony na stosie każdego wątku roboczego w puli. Każde wystąpienie będzie żyć przez cały okres istnienia wątku.

Natychmiast po utworzeniu *wątku, Pracownik*::`Initialize` zostanie wywołany na obiekt skojarzony z tym wątku. Bezpośrednio przed zniszczeniem *Worker*wątku,`Terminate` Pracownik :: zostanie wywołany. Obie metody muszą zaakceptować **argument void.** <strong>\*</strong> Wartość tego argumentu jest przekazywana do puli wątków za pośrednictwem parametru *pvWorkerParam* [cThreadPool::Initialize](#initialize).

Gdy istnieją elementy robocze w kolejce i wątków roboczych dostępnych do pracy, wątek roboczy będzie pobierać element z kolejki i `Execute` wywołać metodę *Worker* obiektu dla tego wątku. Trzy elementy są następnie przekazywane do metody: element `pvWorkerParam` z kolejki, `Initialize` ten sam przekazany do *pracownika*:: i *Pracownik*:: `Terminate`i wskaźnik do struktury [nakładane nakładane](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) używane dla kolejki portu zakończenia we/wy.

*Worker* Klasa deklaruje typ elementów, które będą umieszczane w kolejce w puli `RequestType`wątków, zapewniając typedef, *Worker*:: . Ten typ musi być zdolny do rzutu do i z ULONG_PTR.

Przykładem *Worker* klasy jest [CNonStatelessWorker Class](../../atl/reference/cnonstatelessworker-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

## <a name="cthreadpooladdref"></a><a name="addref"></a>CThreadPool::AddRef

Wdrożenie `IUnknown::AddRef`programu .

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca 1.

### <a name="remarks"></a>Uwagi

Ta klasa nie implementuje kontroli okresu istnienia przy użyciu zliczania odwołań.

## <a name="cthreadpoolcthreadpool"></a><a name="cthreadpool"></a>CThreadPool::CThreadPool

Konstruktor puli wątków.

```
CThreadPool() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje wartość limitu czasu do ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. Domyślny czas to 36 sekund. W razie potrzeby można zdefiniować własną dodatnią wartość całkowitą dla tego symbolu przed włączeniem pliku atlutil.h.

## <a name="cthreadpoolcthreadpool"></a><a name="dtor"></a>CThreadPool::~CThreadPool

Destruktor puli wątków.

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Uwagi

Wywołuje [CThreadPool::Shutdown](#shutdown).

## <a name="cthreadpoolgetnumthreads"></a><a name="getnumthreads"></a>CThreadPool::GetNumThreads

Wywołanie tej metody, aby uzyskać liczbę wątków w puli.

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wątków w puli.

## <a name="cthreadpoolgetqueuehandle"></a><a name="getqueuehandle"></a>CThreadPool::GetQueueHandle

Wywołanie tej metody, aby uzyskać dojście portu zakończenia we/wy używane do kolejkowania elementów roboczych.

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście kolejki lub wartość NULL, jeśli pula wątków nie została zainicjowana.

## <a name="cthreadpoolgetsize"></a><a name="getsize"></a>CThreadPool::GetSize

Wywołanie tej metody, aby uzyskać liczbę wątków w puli.

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>Parametry

*pnNumCięty*<br/>
[na zewnątrz] Adres zmiennej, która po sukcesie odbiera liczbę wątków w puli.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cthreadpoolgettimeout"></a><a name="gettimeout"></a>CThreadPool::GetTimeout

Wywołanie tej metody, aby uzyskać maksymalny czas w milisekundach, że pula wątku będzie czekać na wątek do zamknięcia.

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>Parametry

*pdwMaxWait*<br/>
[na zewnątrz] Adres zmiennej, która po powodzenie otrzymuje maksymalny czas w milisekundach, który pula wątków będzie czekać na zamknięcie wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta wartość limitu czasu jest używana przez [CThreadPool::Shutdown,](#shutdown) jeśli do tej metody nie zostanie dostarczona żadna inna wartość.

## <a name="cthreadpoolinitialize"></a><a name="initialize"></a>CThreadPool::Inicjalizuj

Wywołanie tej metody, aby zainicjować puli wątków.

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>Parametry

*pvPracerParam*<br/>
Parametr roboczy, który ma być przekazywany do obiektu wątku roboczego `Initialize`i `Execute` `Terminate` metod.

*nNumThreads (Wyd.*<br/>
Żądana liczba wątków w puli.

Jeśli *nNumThreads jest ujemna,* jego wartość bezwzględna zostanie pomnożona przez liczbę procesorów w komputerze, aby uzyskać całkowitą liczbę wątków.

Jeśli *nNumThreads* wynosi zero, ATLS_DEFAULT_THREADSPERPROC zostanie pomnożona przez liczbę procesorów w komputerze, aby uzyskać całkowitą liczbę wątków.  Wartość domyślna to 2 wątki na procesor. W razie potrzeby można zdefiniować własną dodatnią wartość całkowitą dla tego symbolu przed włączeniem pliku atlutil.h.

*rozmiar dwStackSize*<br/>
Rozmiar stosu dla każdego wątku w puli.

*hUzupełnienie*<br/>
Dojście obiektu do skojarzenia z portem zakończenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cthreadpoolqueryinterface"></a><a name="queryinterface"></a>CThreadPool::QueryInterface

Wdrożenie `IUnknown::QueryInterface`programu .

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Uwagi

Obiekty tej klasy można pomyślnie zbadać `IUnknown` dla interfejsów i [IThreadPoolConfig.](../../atl/reference/ithreadpoolconfig-interface.md)

## <a name="cthreadpoolqueuerequest"></a><a name="queuerequest"></a>CThreadPool::QueueRequest

Wywołanie tej metody do kolejki elementu pracy, które mają być obsługiwane przez wątek w puli.

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>Parametry

*Żądanie*<br/>
Żądanie, które ma zostać umieszczone w kolejce.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje element pracy do kolejki. Wątki w puli odebrać elementy z kolejki w kolejności, w jakiej są odbierane.

## <a name="cthreadpoolrelease"></a><a name="release"></a>CThreadPool::Zwolnij

Wdrożenie `IUnknown::Release`programu .

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca 1.

### <a name="remarks"></a>Uwagi

Ta klasa nie implementuje kontroli okresu istnienia przy użyciu zliczania odwołań.

## <a name="cthreadpoolsetsize"></a><a name="setsize"></a>CThreadPool::SetSize

Wywołanie tej metody, aby ustawić liczbę wątków w puli.

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>Parametry

*nNumThreads (Wyd.*<br/>
Żądana liczba wątków w puli.

Jeśli *nNumThreads jest ujemna,* jego wartość bezwzględna zostanie pomnożona przez liczbę procesorów w komputerze, aby uzyskać całkowitą liczbę wątków.

Jeśli *nNumThreads* wynosi zero, ATLS_DEFAULT_THREADSPERPROC zostanie pomnożona przez liczbę procesorów w komputerze, aby uzyskać całkowitą liczbę wątków. Wartość domyślna to 2 wątki na procesor. W razie potrzeby można zdefiniować własną dodatnią wartość całkowitą dla tego symbolu przed włączeniem pliku atlutil.h.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Jeśli określona liczba wątków jest mniejsza niż liczba wątków aktualnie w puli, obiekt umieszcza komunikat zamknięcia w kolejce do odebrania przez wątek oczekujący. Gdy oczekiwany wątek ściąga wiadomość z kolejki, powiadamia pulę wątków i kończy procedurę wątku. Ten proces jest powtarzany, dopóki liczba wątków w puli nie osiągnie określonej liczby lub dopóki żaden wątek nie zostanie zakończony w okresie określonym przez [GetTimeout](#gettimeout)/ [SetTimeout](#settimeout). W tej sytuacji metoda zwróci HRESULT odpowiadające WAIT_TIMEOUT i oczekujący komunikat zamknięcia zostanie anulowany.

## <a name="cthreadpoolsettimeout"></a><a name="settimeout"></a>CThreadPool::SetTimeout

Wywołanie tej metody, aby ustawić maksymalny czas w milisekundach, że pula wątku będzie czekać na wątek do zamknięcia.

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>Parametry

*dwMaxWait (Polski)*<br/>
Żądana maksymalna ilość czasu w milisekundach, że pula wątków będzie czekać na zamknięcie wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Limit czasu jest inicjowany, aby ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. Domyślny czas to 36 sekund. W razie potrzeby można zdefiniować własną dodatnią wartość całkowitą dla tego symbolu przed włączeniem pliku atlutil.h.

Należy zauważyć, że *dwMaxWait* jest czas, że pula będzie czekać na jeden wątek, aby zamknąć. Maksymalny czas, który można podjąć, aby usunąć wiele wątków z puli może być nieco mniejsza niż *dwMaxWait* pomnożone przez liczbę wątków.

## <a name="cthreadpoolshutdown"></a><a name="shutdown"></a>CThreadPool::Zamknięcie

Wywołanie tej metody, aby zamknąć pulę wątków.

```
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>Parametry

*dwMaxWait (Polski)*<br/>
Żądana maksymalna ilość czasu w milisekundach, że pula wątków będzie czekać na zamknięcie wątku. Jeśli podano wartość 0 lub nie podano żadnej wartości, ta metoda użyje limitu czasu ustawionego przez [CThreadPool::SetTimeout](#settimeout).

### <a name="remarks"></a>Uwagi

Ta metoda księguje żądanie zamknięcia do wszystkich wątków w puli. Jeśli limit czasu wygaśnie, ta metoda wywoła [TerminateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-terminatethread) w dowolnym wątku, który nie został zakończony. Ta metoda jest wywoływana automatycznie z destruktora klasy.

## <a name="see-also"></a>Zobacz też

[Interfejs IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[DefaultThreadTraits (DefaultThreadTraits)](atl-typedefs.md#defaultthreadtraits)<br/>
[Klasy](../../atl/reference/atl-classes.md)
