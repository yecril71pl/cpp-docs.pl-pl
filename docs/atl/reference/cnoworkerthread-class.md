---
title: Klasa CNoWorkerThread | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords: CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 12cb2f9ab7c69d8c120c1870c5cd97cbc59cf32e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cnoworkerthread-class"></a>Klasa CNoWorkerThread
Klasa jest używana jako argument dla `MonitorClass` parametr szablonu klasy pamięci podręcznej, jeśli chcesz wyłączyć konserwacji dynamiczne pamięci podręcznej.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CNoWorkerThread
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CNoWorkerThread::AddHandle](#addhandle)|Odpowiednik współzależności funkcjonalnych [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|  
|[CNoWorkerThread::AddTimer](#addtimer)|Odpowiednik współzależności funkcjonalnych [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|  
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|Odpowiednik współzależności funkcjonalnych [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|  
|[CNoWorkerThread::GetThreadId](#getthreadid)|Odpowiednik współzależności funkcjonalnych [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|  
|[CNoWorkerThread::Initialize](#initialize)|Odpowiednik współzależności funkcjonalnych [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|  
|[CNoWorkerThread::RemoveHandle](#removehandle)|Odpowiednik współzależności funkcjonalnych [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|  
|[CNoWorkerThread::Shutdown](#shutdown)|Odpowiednik współzależności funkcjonalnych [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa zawiera ten sam interfejs publiczny jako [CWorkerThread](../../atl/reference/cworkerthread-class.md). Ten interfejs powinien zapewniać `MonitorClass` parametr szablonu klasy pamięci podręcznej.  
  
 Metody tej klasy zostaną zaimplementowane nic nie rób. Metody, które zawsze zwracają HRESULT zwracają wartość S_OK i metody, które zwracają identyfikator dojścia lub wątek zawsze zwraca 0.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlutil.h  
  
##  <a name="addhandle"></a>CNoWorkerThread::AddHandle  
 Odpowiednik współzależności funkcjonalnych [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
```
HRESULT AddHandle(HANDLE /* hObject
 */,
    IWorkerThreadClient* /* pClient
 */,
    DWORD_PTR /* dwParam
 */) throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja udostępniane przez tę klasę nie działa.  
  
##  <a name="addtimer"></a>CNoWorkerThread::AddTimer  
 Odpowiednik współzależności funkcjonalnych [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).  
  
```
HRESULT AddTimer(DWORD /* dwInterval
 */,
    IWorkerThreadClient* /* pClient
 */,
    DWORD_PTR /* dwParam
 */,
    HANDLE* /* phTimer
 */) throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja udostępniane przez tę klasę nie działa.  
  
##  <a name="getthreadhandle"></a>CNoWorkerThread::GetThreadHandle  
 Odpowiednik współzależności funkcjonalnych [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja udostępniane przez tę klasę nie działa.  
  
##  <a name="getthreadid"></a>CNoWorkerThread::GetThreadId  
 Odpowiednik współzależności funkcjonalnych [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja udostępniane przez tę klasę nie działa.  
  
##  <a name="initialize"></a>CNoWorkerThread::Initialize  
 Odpowiednik współzależności funkcjonalnych [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).  
  
```
HRESULT Initialize() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja udostępniane przez tę klasę nie działa.  
  
##  <a name="removehandle"></a>CNoWorkerThread::RemoveHandle  
 Odpowiednik współzależności funkcjonalnych [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).  
  
```
HRESULT RemoveHandle(HANDLE /* hObject
 */) throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja udostępniane przez tę klasę nie działa.  
  
##  <a name="shutdown"></a>CNoWorkerThread::Shutdown  
 Odpowiednik współzależności funkcjonalnych [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja udostępniane przez tę klasę nie działa.
