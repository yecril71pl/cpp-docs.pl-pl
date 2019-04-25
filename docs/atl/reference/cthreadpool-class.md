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
ms.openlocfilehash: 7d363de0d787ecc5015093005b39a379acd82e71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277401"
---
# <a name="cthreadpool-class"></a>Klasa CThreadPool

Ta klasa dostarcza puli wątków roboczych, które przetwarzają kolejki elementów roboczych.

## <a name="syntax"></a>Składnia

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>Parametry

*Proces roboczy*<br/>
Klasa odpowiadające [archetyp procesu roboczego](../../atl/reference/worker-archetype.md) dostarczanie kodu używani do przetwarzania elementów w kolejce w puli wątków roboczych.

*ThreadTraits*<br/>
Klasa, zapewniając funkcja używana do tworzenia wątków w puli.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|Konstruktor dla puli wątków.|
|[CThreadPool::~CThreadPool](#dtor)|Destruktor dla puli wątków.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CThreadPool::AddRef](#addref)|Implementacja `IUnknown::AddRef`.|
|[CThreadPool::GetNumThreads](#getnumthreads)|Wywołaj tę metodę, aby uzyskać liczbę wątków w puli.|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Wywołaj tę metodę można pobrać uchwytu portu zakończenia We/Wy używany do kolejki elementów roboczych.|
|[CThreadPool::GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać liczbę wątków w puli.|
|[CThreadPool::GetTimeout](#gettimeout)|Wywołaj tę metodę, aby uzyskać maksymalny czas (w milisekundach) oczekiwania na wątek zamknąć puli wątków.|
|[CThreadPool::Initialize](#initialize)|Wywołaj tę metodę, aby zainicjować puli wątków.|
|[CThreadPool::QueryInterface](#queryinterface)|Implementacja `IUnknown::QueryInterface`.|
|[CThreadPool::QueueRequest](#queuerequest)|Wywołaj tę metodę w kolejce elementu roboczego do obsłużenia wątków w puli.|
|[CThreadPool::Release](#release)|Implementacja `IUnknown::Release`.|
|[CThreadPool::SetSize](#setsize)|Wywołaj tę metodę, aby ustawić liczbę wątków w puli.|
|[CThreadPool::SetTimeout](#settimeout)|Wywołaj tę metodę, aby ustawić maksymalny czas (w milisekundach) oczekiwania na wątek zamknąć puli wątków.|
|[CThreadPool::Shutdown](#shutdown)|Wywołaj tę metodę, aby zamknąć puli wątków.|

## <a name="remarks"></a>Uwagi

Wątków w puli są tworzone i niszczone zainicjowany, rozmiaru lub zamknąć puli. Wystąpienie klasy *procesu roboczego* zostanie utworzony na stosie każdego wątku roboczego w puli. Każde wystąpienie będzie funkcjonować przez okres istnienia wątku.

Natychmiast po utworzeniu wątku *procesu roboczego*::`Initialize` będzie wywoływana dla obiektu skojarzonego z tym wątkiem. Tuż przed niszczenie wątków *procesu roboczego*::`Terminate` zostanie wywołana. Musisz zaakceptować obie metody **void** <strong>\*</strong> argumentu. Wartość tego argumentu jest przekazywany do puli wątków za pośrednictwem *pvWorkerParam* parametru [CThreadPool::Initialize](#initialize).

Gdy brak dostępnych elementów roboczych w wątkach kolejkę i proces roboczy do pracy, wątek roboczy będzie pobierać element kolejki i wywołania `Execute` metody *procesu roboczego* obiektu dla tego wątku. Trzy elementy są następnie przekazywane do metody: element w kolejce takie same `pvWorkerParam` przekazany do *procesu roboczego*:: `Initialize` i *procesu roboczego*:: `Terminate`i wskaźnik [OVERLAPPED](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) strukturą używaną dla kolejki portu zakończenia We/Wy.

*Procesu roboczego* klasa deklaruje typ elementów, które zostaną umieszczone w kolejce w puli wątków, zapewniając element typedef *procesu roboczego*:: `RequestType`. Ten typ musi być w stanie rzutowany do i z typu ULONG_PTR.

Przykładem *procesu roboczego* klasa jest [klasa CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

##  <a name="addref"></a>  CThreadPool::AddRef

Implementacja `IUnknown::AddRef`.

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość 1.

### <a name="remarks"></a>Uwagi

Ta klasa nie implementuje formant okresu istnienia przy użyciu zliczanie odwołań.

##  <a name="cthreadpool"></a>  CThreadPool::CThreadPool

Konstruktor dla puli wątków.

```
CThreadPool() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT wartość limitu czasu. Domyślny czas to 36 sekund. Jeśli to konieczne, można zdefiniować własne dodatnią liczbą całkowitą dla tego symbolu, przed dołączeniem atlutil.h.

##  <a name="dtor"></a>  CThreadPool::~CThreadPool

Destruktor dla puli wątków.

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Uwagi

Wywołania [CThreadPool::Shutdown](#shutdown).

##  <a name="getnumthreads"></a>  CThreadPool::GetNumThreads

Wywołaj tę metodę, aby uzyskać liczbę wątków w puli.

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wątków w puli.

##  <a name="getqueuehandle"></a>  CThreadPool::GetQueueHandle

Wywołaj tę metodę można pobrać uchwytu portu zakończenia We/Wy używany do kolejki elementów roboczych.

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt kolejki lub wartość NULL, jeśli nie została zainicjowana puli wątków.

##  <a name="getsize"></a>  CThreadPool::GetSize

Wywołaj tę metodę, aby uzyskać liczbę wątków w puli.

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>Parametry

*pnNumThreads*<br/>
[out] Adres zmiennej, która w przypadku powodzenia, otrzyma liczbę wątków w puli.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="gettimeout"></a>  CThreadPool::GetTimeout

Wywołaj tę metodę, aby uzyskać maksymalny czas (w milisekundach) oczekiwania na wątek zamknąć puli wątków.

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>Parametry

*pdwMaxWait*<br/>
[out] Adres zmiennej, która w przypadku powodzenia odbiera maksymalny czas (w milisekundach) oczekiwania na wątek zamknąć puli wątków.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta wartość limitu czasu jest używana przez [CThreadPool::Shutdown](#shutdown) Jeśli nie dostarczono żadnych innych wartości do tej metody.

##  <a name="initialize"></a>  CThreadPool::Initialize

Wywołaj tę metodę, aby zainicjować puli wątków.

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>Parametry

*pvWorkerParam*<br/>
Parametr procesu roboczego do przekazania do obiektu wątku roboczego `Initialize`, `Execute`, i `Terminate` metody.

*nNumThreads*<br/>
Żądana liczba wątków w puli.

Jeśli *nNumThreads* jest ujemna, jego wartość bezwzględna będzie pomnożona przez liczbę procesorów w komputerze, aby uzyskać łączna liczba wątków.

Jeśli *nNumThreads* wynosi zero, ATLS_DEFAULT_THREADSPERPROC zostanie pomnożona przez liczbę procesorów w komputerze, aby uzyskać łączna liczba wątków.  Wartość domyślna to 2 wątków na procesor. Jeśli to konieczne, można zdefiniować własne dodatnią liczbą całkowitą dla tego symbolu, przed dołączeniem atlutil.h.

*dwStackSize*<br/>
Rozmiar stosu dla każdego wątku w puli.

*hCompletion*<br/>
Uchwyt obiektu do skojarzenia z portu zakończenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="queryinterface"></a>  CThreadPool::QueryInterface

Implementacja `IUnknown::QueryInterface`.

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Uwagi

Obiekty tej klasy może być kwerenda `IUnknown` i [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md) interfejsów.

##  <a name="queuerequest"></a>  CThreadPool::QueueRequest

Wywołaj tę metodę w kolejce elementu roboczego do obsłużenia wątków w puli.

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>Parametry

*request*<br/>
Żądanie do umieszczone w kolejce.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje element roboczy do kolejki. Wątków w puli pobierania elementów w kolejce w kolejności, w której zostały odebrane.

##  <a name="release"></a>  CThreadPool::Release

Implementacja `IUnknown::Release`.

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość 1.

### <a name="remarks"></a>Uwagi

Ta klasa nie implementuje formant okresu istnienia przy użyciu zliczanie odwołań.

##  <a name="setsize"></a>  CThreadPool::SetSize

Wywołaj tę metodę, aby ustawić liczbę wątków w puli.

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>Parametry

*nNumThreads*<br/>
Żądana liczba wątków w puli.

Jeśli *nNumThreads* jest ujemna, jego wartość bezwzględna będzie pomnożona przez liczbę procesorów w komputerze, aby uzyskać łączna liczba wątków.

Jeśli *nNumThreads* wynosi zero, ATLS_DEFAULT_THREADSPERPROC zostanie pomnożona przez liczbę procesorów w komputerze, aby uzyskać łączna liczba wątków. Wartość domyślna to 2 wątków na procesor. Jeśli to konieczne, można zdefiniować własne dodatnią liczbą całkowitą dla tego symbolu, przed dołączeniem atlutil.h.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Jeśli liczba określonych wątków jest mniejsza od liczby wątków obecnie w puli, obiekt umieszcza komunikat zamknięcia w kolejce do pobrania przez wątek oczekiwania. Podczas oczekiwania na wątek ściąga wiadomości w kolejce, powiadamia puli wątków i kończy procedurę wątku. Ten proces jest powtarzany do momentu liczba wątków w puli osiąga określoną liczbę lub żaden wątek został zakończony przed upływem określonego przez [GetTimeout](#gettimeout)/ [SetTimeout](#settimeout). W takiej sytuacji metoda zwróci wartość HRESULT odpowiadający WAIT_TIMEOUT oraz komunikatów oczekujących zamknięcie zostało anulowane.

##  <a name="settimeout"></a>  CThreadPool::SetTimeout

Wywołaj tę metodę, aby ustawić maksymalny czas (w milisekundach) oczekiwania na wątek zamknąć puli wątków.

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>Parametry

*dwMaxWait*<br/>
Żądany maksymalny czas (w milisekundach) oczekiwania na wątek zamknąć puli wątków.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Limit czasu jest ustawiana na ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. Domyślny czas to 36 sekund. Jeśli to konieczne, można zdefiniować własne dodatnią liczbą całkowitą dla tego symbolu, przed dołączeniem atlutil.h.

Należy pamiętać, że *dwMaxWait* to czas, który puli będzie czekać na jednym wątkiem zamknąć. Maksymalny czas, który można podjąć w celu usunięcia wielu wątków z puli może być nieco mniej niż *dwMaxWait* pomnożona przez liczbę wątków.

##  <a name="shutdown"></a>  CThreadPool::Shutdown

Wywołaj tę metodę, aby zamknąć puli wątków.

```
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>Parametry

*dwMaxWait*<br/>
Żądany maksymalny czas (w milisekundach) oczekiwania na wątek zamknąć puli wątków. Jeśli 0 lub wartość nie zostanie podany, ta metoda użyje limit czasu ustawiony [CThreadPool::SetTimeout](#settimeout).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła żądanie zamknięcia do wszystkich wątków w puli. Jeśli upłynie limit czasu, Metoda ta będzie wywoływać [TerminateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-terminatethread) dotyczące dowolnego wątku, który nie został zakończony. Ta metoda jest wywoływana automatycznie przez destruktor klasy.

## <a name="see-also"></a>Zobacz także

[Interfejs IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Klasy](../../atl/reference/atl-classes.md)
