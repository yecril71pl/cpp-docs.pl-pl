---
title: Klasa CWorkerThread | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords: CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: be7a000e48cb044a67f7eee120206f46ecaef2ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cworkerthread-class"></a>Klasa CWorkerThread
Ta klasa tworzy wątku roboczego lub korzysta z jednego z istniejących, czeka na jeden lub więcej dojść obiektu jądra i wykonuje funkcję określonego klienta, gdy jeden z uchwytów zostanie zasygnalizowane.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class ThreadTraits = DefaultThreadTraits>  
class CWorkerThread
```  
  
#### <a name="parameters"></a>Parametry  
 `ThreadTraits`  
 Klasa podania funkcji tworzenia wątku, takich jak [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) lub [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-structures"></a>Struktury chronionych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`WorkerClientEntry`||  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWorkerThread::CWorkerThread](#cworkerthread)|Konstruktor dla wątku roboczego.|  
|[CWorkerThread:: ~ CWorkerThread](#dtor)|Destruktor dla wątku roboczego.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWorkerThread::AddHandle](#addhandle)|Wywołaj tę metodę, aby dodać obiekt waitable uchwyt do listy przez wątek roboczy.|  
|[CWorkerThread::AddTimer](#addtimer)|Wywołanie tej metody można dodać do listy przez wątek roboczy okresowe czasomierza waitable.|  
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Wywołanie tej metody można pobrać uchwytu wątku dla wątku roboczego.|  
|[CWorkerThread::GetThreadId](#getthreadid)|Wywołanie tej metody można uzyskać Identyfikatora wątku dla wątku roboczego.|  
|[CWorkerThread::Initialize](#initialize)|Wywołaj tę metodę, aby zainicjować wątku roboczego.|  
|[CWorkerThread::RemoveHandle](#removehandle)|Wywołaj tę metodę, aby usunąć z listy obiektów waitable dojścia.|  
|[CWorkerThread::Shutdown](#shutdown)|Wywołaj tę metodę, aby zamknąć wątku roboczego.|  
  
## <a name="remarks"></a>Uwagi  
  
### <a name="to-use-cworkerthread"></a>Aby użyć CWorkerThread  
  
1.  Utwórz wystąpienie tej klasy.  
  
2.  Wywołanie [CWorkerThread::Initialize](#initialize).  
  
3.  Wywołanie [CWorkerThread::AddHandle](#addhandle) z dojściem obiektu jądra i wskaźnika do wykonania [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).  
  
     - lub -  
  
     Wywołanie [CWorkerThread::AddTimer](#addtimer) za pomocą wskaźnika do stosowania [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).  
  
4.  Implementowanie [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) to podjąć akcję, gdy zostanie zasygnalizowane dojścia lub czasomierza.  
  
5.  Aby usunąć obiekt z listy obiektów waitable, należy wywołać [CWorkerThread::RemoveHandle](#removehandle).  
  
6.  Zakończenie wątku, wywołaj [CWorkerThread::Shutdown](#shutdown).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlutil.h  
  
##  <a name="addhandle"></a>CWorkerThread::AddHandle  
 Wywołaj tę metodę, aby dodać obiekt waitable uchwyt do listy przez wątek roboczy.  
  
```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Dojście do obiektu waitable.  
  
 `pClient`  
 Wskaźnik do [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) interfejsu na obiekt wywoływany, gdy zostanie zasygnalizowane dojście.  
  
 `dwParam`  
 Parametr do przekazania do [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) kiedy zostanie zasygnalizowane dojście.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) zostanie wywołana za pomocą `pClient` podczas uchwytu `hObject`, zostanie zasygnalizowane.  
  
##  <a name="addtimer"></a>CWorkerThread::AddTimer  
 Wywołanie tej metody można dodać do listy przez wątek roboczy okresowe czasomierza waitable.  
  
```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *dwInterval*  
 Określa okres czasomierza w milisekundach.  
  
 `pClient`  
 Wskaźnik do [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) interfejsu na obiekt wywoływany, gdy zostanie zasygnalizowane dojście.  
  
 `dwParam`  
 Parametr do przekazania do [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) kiedy zostanie zasygnalizowane dojście.  
  
 `phTimer`  
 [out] Adres dojście do zmiennej, w przypadku powodzenia otrzymuje dojścia do nowo utworzonej czasomierza.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) zostanie wywołana za pomocą `pClient` kiedy zostanie zasygnalizowane czasomierza.  
  
 Przekaż dojście czasomierza z `phTimer` do [CWorkerThread::RemoveHandle](#removehandle) zamknąć czasomierza.  
  
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
 Wywołania [CWorkerThread::Shutdown](#shutdown).  
  
##  <a name="getthreadhandle"></a>CWorkerThread::GetThreadHandle  
 Wywołanie tej metody można pobrać uchwytu wątku dla wątku roboczego.  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście wątku lub wartość NULL, jeśli wątek roboczy nie został zainicjowany.  
  
##  <a name="getthreadid"></a>CWorkerThread::GetThreadId  
 Wywołanie tej metody można uzyskać Identyfikatora wątku dla wątku roboczego.  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca identyfikator wątku lub wartość NULL, jeśli wątek roboczy nie został zainicjowany.  
  
##  <a name="initialize"></a>CWorkerThread::Initialize  
 Wywołaj tę metodę, aby zainicjować wątku roboczego.  
  
```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pThread`  
 Istniejące wątku roboczego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Tę metodę należy wywoływać do inicjalizacji obiektu po utworzeniu lub po wywołaniu [CWorkerThread::Shutdown](#shutdown).  
  
 Aby mieć co najmniej dwóch `CWorkerThread` obiektów, użyj tego samego wątku roboczego, zainicjować jednego z nich bez żadnych argumentów przekazuj wskaźnik do obiektu w celu przekazania `Initialize` innych metod. Obiekty zainicjowana przy użyciu wskaźnika należy zamknąć przed obiekt używany do ich inicjowania.  
  
 Zobacz [CWorkerThread::Shutdown](#shutdown) Aby uzyskać informacje dotyczące sposobu zachowanie tej metody zmienia się po zainicjowaniu przy użyciu wskaźnika do istniejącego obiektu.  
  
##  <a name="removehandle"></a>CWorkerThread::RemoveHandle  
 Wywołaj tę metodę, aby usunąć z listy obiektów waitable dojścia.  
  
```
HRESULT RemoveHandle(HANDLE hObject) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Dojście do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Po usunięciu dojście [IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) wywołano skojarzonego obiektu, który został przekazany do [AddHandle](#addhandle). Jeśli to wywołanie nie powiodło się, `CWorkerThread` wywoła systemu Windows [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211) funkcja na uchwycie.  
  
##  <a name="shutdown"></a>CWorkerThread::Shutdown  
 Wywołaj tę metodę, aby zamknąć wątku roboczego.  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwWait`  
 Czas w milisekundach czas oczekiwania na wątek roboczy zamknąć. ATL_WORKER_THREAD_WAIT wartość domyślna to 10 sekund. W razie potrzeby, przed dołączeniem atlutil.h można określić wartość dla tego symbolu. 
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK na powodzenie lub błąd HRESULT na uszkodzenia, np. Jeśli wartość limitu czasu `dwWait`, został przekroczony.  
  
### <a name="remarks"></a>Uwagi  
 Aby ponownie użyć obiektu, należy wywołać [CWorkerThread::Initialize](#initialize) po wywołaniu tej metody.  
  
 Należy pamiętać, że wywołania **zamknięcia** zainicjowana za pomocą wskaźnika do innego obiektu `CWorkerThread` obiekt nie ma wpływu i zawsze zwraca wartość S_OK.  
  
## <a name="see-also"></a>Zobacz też  
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [Klasy](../../atl/reference/atl-classes.md)   
 [Wielowątkowość: Tworzenie wątków roboczych](../../parallel/multithreading-creating-worker-threads.md)   
 [Interfejs IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)
