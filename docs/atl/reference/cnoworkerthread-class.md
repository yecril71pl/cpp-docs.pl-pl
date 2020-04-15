---
title: Klasa CNoWorkerThread
ms.date: 11/04/2016
f1_keywords:
- CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread::AddHandle
- ATLUTIL/ATL::CNoWorkerThread::AddTimer
- ATLUTIL/ATL::CNoWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CNoWorkerThread::GetThreadId
- ATLUTIL/ATL::CNoWorkerThread::Initialize
- ATLUTIL/ATL::CNoWorkerThread::RemoveHandle
- ATLUTIL/ATL::CNoWorkerThread::Shutdown
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
ms.openlocfilehash: 90056e648a53218ac06083d43ca34870e1ca72fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326706"
---
# <a name="cnoworkerthread-class"></a>Klasa CNoWorkerThread

Użyj tej klasy jako `MonitorClass` argument dla parametru szablonu do buforowania klas, jeśli chcesz wyłączyć dynamiczną konserwację pamięci podręcznej.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CNoWorkerThread
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CNoWorkerThread::AddHandle](#addhandle)|Niesercowy odpowiednik [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|
|[CNoWorkerThread::AddTimer](#addtimer)|Niespożywczy odpowiednik [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|Niesercowe odpowiednik [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|
|[CNoWorkerThread::GetThreadId](#getthreadid)|Niesercowe odpowiednik [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|
|[CNoWorkerThread::Inicjalizuj](#initialize)|Niefunkcjonalne odpowiednik [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|
|[CNoWorkerThread::RemoveHandle](#removehandle)|Nieskładkowych odpowiednik [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|
|[CNoWorkerThread::Zamknięcie](#shutdown)|Nieskowny odpowiednik [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|

## <a name="remarks"></a>Uwagi

Ta klasa zapewnia ten sam interfejs publiczny co [CWorkerThread](../../atl/reference/cworkerthread-class.md). Oczekuje się, że ten `MonitorClass` interfejs zostanie dostarczony przez parametr szablonu do klas pamięci podręcznej.

Metody w tej klasie są implementowane, aby nic nie robić. Metody, które zwracają HRESULT zawsze zwraca S_OK, a metody, które zwracają HANDLE lub identyfikator wątku zawsze zwracają 0.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

## <a name="cnoworkerthreadaddhandle"></a><a name="addhandle"></a>CNoWorkerThread::AddHandle

Niesercowy odpowiednik [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca S_OK.

### <a name="remarks"></a>Uwagi

Implementacja przewidziana przez tę klasę nic nie robi.

## <a name="cnoworkerthreadaddtimer"></a><a name="addtimer"></a>CNoWorkerThread::AddTimer

Niespożywczy odpowiednik [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca S_OK.

### <a name="remarks"></a>Uwagi

Implementacja przewidziana przez tę klasę nic nie robi.

## <a name="cnoworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CNoWorkerThread::GetThreadHandle

Niesercowe odpowiednik [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

Implementacja przewidziana przez tę klasę nic nie robi.

## <a name="cnoworkerthreadgetthreadid"></a><a name="getthreadid"></a>CNoWorkerThread::GetThreadId

Niesercowe odpowiednik [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość 0.

### <a name="remarks"></a>Uwagi

Implementacja przewidziana przez tę klasę nic nie robi.

## <a name="cnoworkerthreadinitialize"></a><a name="initialize"></a>CNoWorkerThread::Inicjalizuj

Niefunkcjonalne odpowiednik [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca S_OK.

### <a name="remarks"></a>Uwagi

Implementacja przewidziana przez tę klasę nic nie robi.

## <a name="cnoworkerthreadremovehandle"></a><a name="removehandle"></a>CNoWorkerThread::RemoveHandle

Nieskładkowych odpowiednik [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca S_OK.

### <a name="remarks"></a>Uwagi

Implementacja przewidziana przez tę klasę nic nie robi.

## <a name="cnoworkerthreadshutdown"></a><a name="shutdown"></a>CNoWorkerThread::Zamknięcie

Nieskowny odpowiednik [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca S_OK.

### <a name="remarks"></a>Uwagi

Implementacja przewidziana przez tę klasę nic nie robi.
