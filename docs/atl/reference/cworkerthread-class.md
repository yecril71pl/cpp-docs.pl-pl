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
ms.openlocfilehash: f1aa76514b98bbf12f8e516d3d54f68e8ef4dd7d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417720"
---
# <a name="cworkerthread-class"></a>Klasa CWorkerThread

Ta klasa tworzy wątek roboczy lub używa istniejącego obiektu, czeka na co najmniej jeden obiekt jądra, i wykonuje określoną funkcję klienta po zasygnalizowaniu jednego z uchwytów.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>Parametry

*ThreadTraits*<br/>
Klasa dostarczająca funkcję tworzenia wątku, na przykład [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) lub [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).

## <a name="members"></a>Members

### <a name="protected-structures"></a>Struktury chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CWorkerThread::CWorkerThread](#cworkerthread)|Konstruktor dla wątku roboczego.|
|[CWorkerThread:: ~ CWorkerThread](#dtor)|Destruktor wątku roboczego.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CWorkerThread:: AddHandle](#addhandle)|Wywołaj tę metodę, aby dodać uchwyt obiektu oczekującego do listy obsługiwanej przez wątek roboczy.|
|[CWorkerThread:: addtimeer](#addtimer)|Wywołaj tę metodę, aby dodać okresowy czasomierz oczekujący na listę obsługiwaną przez wątek roboczy.|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Wywołaj tę metodę, aby uzyskać uchwyt wątku wątku roboczego.|
|[CWorkerThread::GetThreadId](#getthreadid)|Wywołaj tę metodę, aby uzyskać identyfikator wątku wątku roboczego.|
|[CWorkerThread:: Initialize](#initialize)|Wywołaj tę metodę, aby zainicjować wątek roboczy.|
|[CWorkerThread::RemoveHandle](#removehandle)|Wywołaj tę metodę, aby usunąć dojście z listy obiektów oczekujących.|
|[CWorkerThread:: Shutdown](#shutdown)|Wywołaj tę metodę, aby zamknąć wątek roboczy.|

## <a name="remarks"></a>Uwagi

### <a name="to-use-cworkerthread"></a>Aby użyć CWorkerThread

1. Utwórz wystąpienie tej klasy.

1. Wywołanie [CWorkerThread:: Initialize](#initialize).

1. Wywołaj [CWorkerThread:: AddHandle](#addhandle) z dojściem obiektu jądra i wskaźnikiem do implementacji elementu [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

   \- lub-

   Wywołaj [CWorkerThread:: Addtimeer](#addtimer) ze wskaźnikiem do implementacji elementu [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

1. Zaimplementuj [IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) , aby wykonać jakąś akcję, gdy dojście lub czasomierz są sygnalizowane.

1. Aby usunąć obiekt z listy obiektów oczekujących, wywołaj [CWorkerThread:: RemoveHandle](#removehandle).

1. Aby zakończyć wątek, wywołaj [CWorkerThread:: Shutdown](#shutdown).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil. h

##  <a name="addhandle"></a>CWorkerThread:: AddHandle

Wywołaj tę metodę, aby dodać uchwyt obiektu oczekującego do listy obsługiwanej przez wątek roboczy.

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Uchwyt do obiektu, który można oczekiwać.

*pClient*<br/>
Wskaźnik do interfejsu [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) na obiekcie, który ma być wywoływany po zasygnalizowaniu uchwytu.

*dwParam*<br/>
Parametr, który ma zostać przesłany do [IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) po zasygnalizowaniu uchwytu.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

[IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) zostanie wywołane przez *pClient* , gdy dojście, *hObject*, zostanie zasygnalizowane.

##  <a name="addtimer"></a>CWorkerThread:: addtimeer

Wywołaj tę metodę, aby dodać okresowy czasomierz oczekujący na listę obsługiwaną przez wątek roboczy.

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>Parametry

*dwInterval*<br/>
Określa okres czasomierza (w milisekundach).

*pClient*<br/>
Wskaźnik do interfejsu [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) na obiekcie, który ma być wywoływany po zasygnalizowaniu uchwytu.

*dwParam*<br/>
Parametr, który ma zostać przesłany do [IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) po zasygnalizowaniu uchwytu.

*phTimer*<br/>
określoną Adres zmiennej dojścia, która po powodzeniu odbiera dojście do nowo utworzonego czasomierza.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

[IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) zostanie wywołane przez *pClient* po zasygnalizowaniu czasomierza.

Przekaż uchwyt Timer z *phTimer* do [CWorkerThread:: RemoveHandle](#removehandle) , aby zamknąć czasomierz.

##  <a name="cworkerthread"></a>CWorkerThread::CWorkerThread

Konstruktor.

```
CWorkerThread() throw();
```

##  <a name="dtor"></a>CWorkerThread:: ~ CWorkerThread

Destruktor.

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>Uwagi

Wywołania [CWorkerThread:: Shutdown](#shutdown).

##  <a name="getthreadhandle"></a>CWorkerThread::GetThreadHandle

Wywołaj tę metodę, aby uzyskać uchwyt wątku wątku roboczego.

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca dojście do wątku lub wartość NULL, jeśli wątek roboczy nie został zainicjowany.

##  <a name="getthreadid"></a>CWorkerThread::GetThreadId

Wywołaj tę metodę, aby uzyskać identyfikator wątku wątku roboczego.

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca identyfikator wątku lub wartość NULL, jeśli wątek roboczy nie został zainicjowany.

##  <a name="initialize"></a>CWorkerThread:: Initialize

Wywołaj tę metodę, aby zainicjować wątek roboczy.

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>Parametry

*pThread*<br/>
Istniejący wątek roboczy.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda powinna być wywoływana w celu zainicjowania obiektu po utworzeniu lub po wywołaniu [CWorkerThread:: Shutdown](#shutdown).

Aby dwa lub więcej obiektów `CWorkerThread` używały tego samego wątku roboczego, zainicjuj jeden z nich bez przekazywania jakichkolwiek argumentów, a następnie Przekaż wskaźnik do tego obiektu do `Initialize` metod innych. Obiekty zainicjowane przy użyciu wskaźnika powinny zostać zamknięte przed obiektem użytym do jego zainicjowania.

Zobacz [CWorkerThread:: Shutdown](#shutdown) , aby uzyskać informacje na temat zmiany zachowania tej metody po zainicjowaniu jej przy użyciu wskaźnika do istniejącego obiektu.

##  <a name="removehandle"></a>CWorkerThread::RemoveHandle

Wywołaj tę metodę, aby usunąć dojście z listy obiektów oczekujących.

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Dojście do usunięcia.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Po usunięciu dojścia [IWorkerThreadClient:: funkcja CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) zostanie wywołana dla skojarzonego obiektu, który został przekazano do funkcji [AddHandle](#addhandle). Jeśli to wywołanie zakończy się niepowodzeniem, `CWorkerThread` wywoła funkcję [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) systemu Windows na dojście.

##  <a name="shutdown"></a>CWorkerThread:: Shutdown

Wywołaj tę metodę, aby zamknąć wątek roboczy.

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>Parametry

*dwWait*<br/>
Czas (w milisekundach) oczekiwania na zamknięcie wątku roboczego. ATL_WORKER_THREAD_WAIT wartość domyślna to 10 sekund. W razie potrzeby można zdefiniować własną wartość tego symbolu przed uwzględnieniem atlutil. h.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia, na przykład w przypadku przekroczenia limitu czasu, *dwWait*.

### <a name="remarks"></a>Uwagi

Aby ponownie użyć obiektu, wywołaj [CWorkerThread:: Initialize](#initialize) po wywołaniu tej metody.

Należy zauważyć, że wywołanie `Shutdown` na obiekcie zainicjowanym za pomocą wskaźnika do innego obiektu `CWorkerThread` nie ma żadnego efektu i zawsze zwraca S_OK.

## <a name="see-also"></a>Zobacz też

[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Klasy](../../atl/reference/atl-classes.md)<br/>
[Wielowątkowość: tworzenie wątków roboczych](../../parallel/multithreading-creating-worker-threads.md)<br/>
[Interfejs IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)
