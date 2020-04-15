---
title: Klasa CWorkerThread
ms.date: 11/04/2016
f1_keywords:
- CWorkerThread
- ATLUTIL/ATL::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::AddHandle
- ATLUTIL/ATL::CWorkerThread::AddTimer
- ATLUTIL/ATL::CWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CWorkerThread::GetThreadId
- ATLUTIL/ATL::CWorkerThread::Initialize
- ATLUTIL/ATL::CWorkerThread::RemoveHandle
- ATLUTIL/ATL::CWorkerThread::Shutdown
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
ms.openlocfilehash: 05e6b432d44927fa7e276792643e29c80c42d822
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330221"
---
# <a name="cworkerthread-class"></a>Klasa CWorkerThread

Ta klasa tworzy wątek roboczy lub używa istniejącego, czeka na jeden lub więcej uchwytów obiektu jądra i wykonuje określoną funkcję klienta, gdy jeden z uchwytów jest sygnalizowany.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>Parametry

*ThreadTraits (ThreadTraits)*<br/>
Klasa zapewniająca funkcję tworzenia wątku, taką jak [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) lub [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="protected-structures"></a>Konstrukcje chronione

|Nazwa|Opis|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWorkerThread::CWorkerThread](#cworkerthread)|Konstruktor wątku roboczego.|
|[CWorkerThread::~CWorkerThread](#dtor)|Destruktor wątku roboczego.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWorkerThread::AddHandle](#addhandle)|Wywołanie tej metody, aby dodać dojście do obiektu oczekujących do listy obsługiwanej przez wątek roboczy.|
|[CWorkerThread::AddTimer](#addtimer)|Wywołanie tej metody, aby dodać okresowy czasomierz oczekujący do listy obsługiwanej przez wątek roboczy.|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Wywołanie tej metody, aby uzyskać uchwyt wątku wątku roboczego.|
|[CWorkerThread::GetThreadId](#getthreadid)|Wywołanie tej metody, aby uzyskać identyfikator wątku wątku roboczego.|
|[CWorkerThread::Inicjalizuj](#initialize)|Wywołanie tej metody, aby zainicjować wątek roboczy.|
|[CWorkerThread::RemoveHandle](#removehandle)|Wywołanie tej metody, aby usunąć dojście z listy obiektów oczekujących.|
|[CWorkerThread::Zamknięcie](#shutdown)|Wywołanie tej metody, aby zamknąć wątek roboczy.|

## <a name="remarks"></a>Uwagi

### <a name="to-use-cworkerthread"></a>Aby użyć CWorkerThread

1. Utwórz wystąpienie tej klasy.

1. Wywołanie [CWorkerThread::Initialize](#initialize).

1. Wywołanie [CWorkerThread::AddHandle](#addhandle) z uchwytem obiektu jądra i wskaźnikiem do implementacji [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

   \-lub -

   Wywołanie [CWorkerThread::AddTimer](#addtimer) ze wskaźnikiem do implementacji [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

1. Zaimplementuj [iWorkerThreadClient::Execute,](../../atl/reference/iworkerthreadclient-interface.md#execute) aby wykonać jakąś akcję, gdy dojście lub czasomierz jest sygnalizowany.

1. Aby usunąć obiekt z listy obiektów oczekujących, zadzwoń [do CWorkerThread::RemoveHandle](#removehandle).

1. Aby zakończyć wątek, zadzwoń [CWorkerThread::Shutdown](#shutdown).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

## <a name="cworkerthreadaddhandle"></a><a name="addhandle"></a>CWorkerThread::AddHandle

Wywołanie tej metody, aby dodać dojście do obiektu oczekujących do listy obsługiwanej przez wątek roboczy.

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>Parametry

*hObiekt*<br/>
Dojście do obiektu możliwego oczekiwania.

*pClient (właswoić)*<br/>
Wskaźnik do interfejsu [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) na obiekcie, który ma być wywoływany, gdy dojście jest sygnalizowane.

*dwParam (polski)*<br/>
Parametr, który ma być przekazany do [IWorkerThreadClient::Execute,](../../atl/reference/iworkerthreadclient-interface.md#execute) gdy dojście jest sygnalizowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) zostanie wywołana przez *pClient,* gdy uchwyt, *hObject*, jest sygnalizowany.

## <a name="cworkerthreadaddtimer"></a><a name="addtimer"></a>CWorkerThread::AddTimer

Wywołanie tej metody, aby dodać okresowy czasomierz oczekujący do listy obsługiwanej przez wątek roboczy.

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>Parametry

*dwInterval*<br/>
Określa okres czasomierza w milisekundach.

*pClient (właswoić)*<br/>
Wskaźnik do interfejsu [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) na obiekcie, który ma być wywoływany, gdy dojście jest sygnalizowane.

*dwParam (polski)*<br/>
Parametr, który ma być przekazany do [IWorkerThreadClient::Execute,](../../atl/reference/iworkerthreadclient-interface.md#execute) gdy dojście jest sygnalizowane.

*phTimer*<br/>
[na zewnątrz] Adres do handle zmiennej, która po powodzenie odbiera dojście do nowo utworzonego czasomierza.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) zostanie wywołana za pośrednictwem *pClient,* gdy czasomierz jest sygnalizowany.

Przekaż uchwyt czasomierza z *phTimer* do [CWorkerThread::RemoveHandle,](#removehandle) aby zamknąć czasomierz.

## <a name="cworkerthreadcworkerthread"></a><a name="cworkerthread"></a>CWorkerThread::CWorkerThread

Konstruktor.

```
CWorkerThread() throw();
```

## <a name="cworkerthreadcworkerthread"></a><a name="dtor"></a>CWorkerThread::~CWorkerThread

Destruktor.

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>Uwagi

Wywołuje [CWorkerThread::Shutdown](#shutdown).

## <a name="cworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CWorkerThread::GetThreadHandle

Wywołanie tej metody, aby uzyskać uchwyt wątku wątku roboczego.

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście wątku lub wartość NULL, jeśli wątek roboczy nie został zainicjowany.

## <a name="cworkerthreadgetthreadid"></a><a name="getthreadid"></a>CWorkerThread::GetThreadId

Wywołanie tej metody, aby uzyskać identyfikator wątku wątku roboczego.

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca identyfikator wątku lub wartość NULL, jeśli wątek roboczy nie został zainicjowany.

## <a name="cworkerthreadinitialize"></a><a name="initialize"></a>CWorkerThread::Inicjalizuj

Wywołanie tej metody, aby zainicjować wątek roboczy.

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>Parametry

*p Wt wątkiem*<br/>
Istniejący wątek roboczy.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta metoda powinna być wywoływana w celu zainicjowania obiektu po utworzeniu lub po wywołaniu [CWorkerThread::Shutdown](#shutdown).

Aby mieć dwa `CWorkerThread` lub więcej obiektów użyć tego samego wątku roboczego, zainicjować jeden `Initialize` z nich bez przekazywania żadnych argumentów następnie przekazać wskaźnik do tego obiektu do metod innych. Obiekty zainicjowane za pomocą wskaźnika powinny zostać zamknięte przed zainicjowaniem obiektu.

Zobacz [CWorkerThread::Shutdown, aby](#shutdown) uzyskać informacje na temat tego, jak zmienia się zachowanie tej metody podczas inicjowania przy użyciu wskaźnika do istniejącego obiektu.

## <a name="cworkerthreadremovehandle"></a><a name="removehandle"></a>CWorkerThread::RemoveHandle

Wywołanie tej metody, aby usunąć dojście z listy obiektów oczekujących.

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>Parametry

*hObiekt*<br/>
Uchwyt do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Po usunięciu uchwytu [IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) zostanie wywołana na skojarzonym obiekcie, który został przekazany do [AddHandle](#addhandle). Jeśli to wywołanie nie powiedzie się, `CWorkerThread` wywoła funkcję Zamknięcia [Usługi](/windows/win32/api/handleapi/nf-handleapi-closehandle) systemu Windows na dojście.

## <a name="cworkerthreadshutdown"></a><a name="shutdown"></a>CWorkerThread::Zamknięcie

Wywołanie tej metody, aby zamknąć wątek roboczy.

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>Parametry

*dwWait (Niem.*<br/>
Czas w milisekundach oczekiwania na zamknięcie wątku roboczego. ATL_WORKER_THREAD_WAIT domyślnie 10 sekund. W razie potrzeby można zdefiniować własną wartość dla tego symbolu przed włączeniem pliku atlutil.h.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT w przypadku awarii, na przykład jeśli wartość limitu czasu, *dwWait*, jest przekroczona.

### <a name="remarks"></a>Uwagi

Aby ponownie użyć obiektu, wywołaj [CWorkerThread::Initialize](#initialize) po wywołaniu tej metody.

Należy zauważyć, że wywołanie `Shutdown` obiektu zainicjowanego wskaźnikiem do innego `CWorkerThread` obiektu nie ma wpływu i zawsze zwraca S_OK.

## <a name="see-also"></a>Zobacz też

[DefaultThreadTraits (DefaultThreadTraits)](atl-typedefs.md#defaultthreadtraits)<br/>
[Klasy](../../atl/reference/atl-classes.md)<br/>
[Wielowątkowość: tworzenie wątków roboczych](../../parallel/multithreading-creating-worker-threads.md)<br/>
[Interfejs IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)
