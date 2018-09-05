---
title: Klasa CNoWorkerThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e602b3493269924e7b80b52b70b34397fcc7dd71
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753929"
---
# <a name="cnoworkerthread-class"></a>Klasa CNoWorkerThread

Klasa jest używana jako argument dla `MonitorClass` parametr szablonu klasy pamięci podręcznej, jeśli chcesz wyłączyć obsługi dynamicznej pamięci podręcznej.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CNoWorkerThread
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CNoWorkerThread::AddHandle](#addhandle)|Wielokrotność nie funkcjonalne [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|
|[CNoWorkerThread::AddTimer](#addtimer)|Wielokrotność nie funkcjonalne [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|Wielokrotność nie funkcjonalne [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|
|[CNoWorkerThread::GetThreadId](#getthreadid)|Wielokrotność nie funkcjonalne [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|
|[CNoWorkerThread::Initialize](#initialize)|Wielokrotność nie funkcjonalne [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|
|[CNoWorkerThread::RemoveHandle](#removehandle)|Wielokrotność nie funkcjonalne [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|
|[CNoWorkerThread::Shutdown](#shutdown)|Wielokrotność nie funkcjonalne [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia ten sam interfejs publiczny co [CWorkerThread](../../atl/reference/cworkerthread-class.md). Ten interfejs powinien być dostarczona przez `MonitorClass` parametr szablonu klasy pamięci podręcznej.

Metody tej klasy są implementowane na nic nie rób. Metody, które zwracają HRESULT zawsze zwracają S_OK i metody, które zwraca identyfikator dojścia lub wątku zawsze zwracają 0.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

##  <a name="addhandle"></a>  CNoWorkerThread::AddHandle

Wielokrotność nie funkcjonalne [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Implementacja dostarczane przez tę klasę nic nie robi.

##  <a name="addtimer"></a>  CNoWorkerThread::AddTimer

Wielokrotność nie funkcjonalne [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Implementacja dostarczane przez tę klasę nic nie robi.

##  <a name="getthreadhandle"></a>  CNoWorkerThread::GetThreadHandle

Wielokrotność nie funkcjonalne [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

Implementacja dostarczane przez tę klasę nic nie robi.

##  <a name="getthreadid"></a>  CNoWorkerThread::GetThreadId

Wielokrotność nie funkcjonalne [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość 0.

### <a name="remarks"></a>Uwagi

Implementacja dostarczane przez tę klasę nic nie robi.

##  <a name="initialize"></a>  CNoWorkerThread::Initialize

Wielokrotność nie funkcjonalne [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Implementacja dostarczane przez tę klasę nic nie robi.

##  <a name="removehandle"></a>  CNoWorkerThread::RemoveHandle

Wielokrotność nie funkcjonalne [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Implementacja dostarczane przez tę klasę nic nie robi.

##  <a name="shutdown"></a>  CNoWorkerThread::Shutdown

Wielokrotność nie funkcjonalne [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Implementacja dostarczane przez tę klasę nic nie robi.
