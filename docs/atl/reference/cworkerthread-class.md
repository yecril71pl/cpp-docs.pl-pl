---
title: Klasa CWorkerThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78d846db4080c780bfa72fca52b7c9f6868edc2f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195345"
---
# <a name="cworkerthread-class"></a>Klasa CWorkerThread
Ta klasa tworzy wątek roboczy lub korzysta z istniejącą grupę, czeka na co najmniej jeden uchwytów obiektu jądra i wykonuje funkcję określonego klienta, gdy jeden z uchwytów, jest sygnalizowane.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class ThreadTraits = DefaultThreadTraits>  
class CWorkerThread
```  
  
#### <a name="parameters"></a>Parametry  
 *ThreadTraits*  
 Klasa dostarczanie funkcji tworzenia wątku, takich jak [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) lub [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-structures"></a>Chronione struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`WorkerClientEntry`||  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWorkerThread::CWorkerThread](#cworkerthread)|Konstruktor wątku roboczego.|  
|[CWorkerThread:: ~ CWorkerThread](#dtor)|Destruktor wątku roboczego.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWorkerThread::AddHandle](#addhandle)|Wywołaj tę metodę, aby dodać obiekt oczekujący uchwyt do listy utrzymywane przez wątek roboczy.|  
|[CWorkerThread::AddTimer](#addtimer)|Wywołaj tę metodę, aby dodać okresowe czasomierz oczekujący na liście prowadzonej przez wątek roboczy.|  
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Wywołaj tę metodę można pobrać uchwytu wątku wątku roboczego.|  
|[CWorkerThread::GetThreadId](#getthreadid)|Wywołaj tę metodę, aby uzyskać identyfikator wątku w wątku roboczego.|  
|[CWorkerThread::Initialize](#initialize)|Wywołaj tę metodę, aby zainicjować wątku roboczego.|  
|[CWorkerThread::RemoveHandle](#removehandle)|Wywołaj tę metodę, aby usunąć uchwyt z listy obiektów oczekujący.|  
|[CWorkerThread::Shutdown](#shutdown)|Wywołaj tę metodę, aby zamknąć wątku roboczego.|  
  
## <a name="remarks"></a>Uwagi  
  
### <a name="to-use-cworkerthread"></a>Aby użyć CWorkerThread  
  
1.  Utwórz wystąpienie tej klasy.  
  
2.  Wywołaj [CWorkerThread::Initialize](#initialize).  
  
3.  Wywołaj [CWorkerThread::AddHandle](#addhandle) z dojściem obiektu jądra i wskaźnik do implementacji [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).  
  
     - lub —  
  
     Wywołaj [CWorkerThread::AddTimer](#addtimer) za pomocą wskaźnika do implementacji [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).  
  
4.  Implementowanie [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) wykonania określonego działania, gdy zasygnalizowania dojścia lub czasomierza.  
  
5.  Aby usunąć obiekt z listy obiektów oczekujący, należy wywołać [CWorkerThread::RemoveHandle](#removehandle).  
  
6.  Aby zakończyć wątek, wywołaj [CWorkerThread::Shutdown](#shutdown).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlutil.h  
  
##  <a name="addhandle"></a>  CWorkerThread::AddHandle  
 Wywołaj tę metodę, aby dodać obiekt oczekujący uchwyt do listy utrzymywane przez wątek roboczy.  
  
```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *hObject*  
 Dojście do obiektu oczekujący.  
  
 *pClient*  
 Wskaźnik do [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) interfejsu na obiekt wywoływany, gdy jest sygnalizowane uchwytu.  
  
 *dwParam*  
 Parametr do przekazania do [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) po zasygnalizowania uchwytu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) zostanie wywołana przez *pClient* podczas uchwyt, *hObject*, jest sygnalizowane.  
  
##  <a name="addtimer"></a>  CWorkerThread::AddTimer  
 Wywołaj tę metodę, aby dodać okresowe czasomierz oczekujący na liście prowadzonej przez wątek roboczy.  
  
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
  
 *pClient*  
 Wskaźnik do [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) interfejsu na obiekt wywoływany, gdy jest sygnalizowane uchwytu.  
  
 *dwParam*  
 Parametr do przekazania do [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) po zasygnalizowania uchwytu.  
  
 *phTimer*  
 [out] Adres dojście do zmiennej, w przypadku powodzenia odbiera uchwyt do nowo utworzonego czasomierza.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) zostanie wywołana przez *pClient* po zasygnalizowania czasomierza.  
  
 Przekaż uchwyt czasomierza z *phTimer* do [CWorkerThread::RemoveHandle](#removehandle) zamknąć czasomierza.  
  
##  <a name="cworkerthread"></a>  CWorkerThread::CWorkerThread  
 Konstruktor.  
  
```
CWorkerThread() throw();
```  
  
##  <a name="dtor"></a>  CWorkerThread:: ~ CWorkerThread  
 Destruktor.  
  
```
~CWorkerThread() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [CWorkerThread::Shutdown](#shutdown).  
  
##  <a name="getthreadhandle"></a>  CWorkerThread::GetThreadHandle  
 Wywołaj tę metodę można pobrać uchwytu wątku wątku roboczego.  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście wątku lub wartość NULL, jeśli wątek roboczy nie został zainicjowany.  
  
##  <a name="getthreadid"></a>  CWorkerThread::GetThreadId  
 Wywołaj tę metodę, aby uzyskać identyfikator wątku w wątku roboczego.  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca identyfikator wątku lub wartość NULL, jeśli wątek roboczy nie został zainicjowany.  
  
##  <a name="initialize"></a>  CWorkerThread::Initialize  
 Wywołaj tę metodę, aby zainicjować wątku roboczego.  
  
```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pThread*  
 Istniejącego wątku roboczego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Tę metodę należy wywoływać do inicjalizacji obiektu po utworzeniu lub po wywołaniu [CWorkerThread::Shutdown](#shutdown).  
  
 Mieć co najmniej dwóch `CWorkerThread` obiekty, użyj tego samego wątku roboczego, inicjować jedno z nich bez żadnych argumentów należy przekazać wskaźnik do obiektu w celu przekazywania `Initialize` innych metod. Obiekty inicjowane za pomocą wskaźnika należy zamknąć przed obiekt używany do ich inicjowania.  
  
 Zobacz [CWorkerThread::Shutdown](#shutdown) uzyskać informacji na temat jak zachowanie tej metody zmienia się po zainicjowaniu za pomocą wskaźnika do istniejącego obiektu.  
  
##  <a name="removehandle"></a>  CWorkerThread::RemoveHandle  
 Wywołaj tę metodę, aby usunąć uchwyt z listy obiektów oczekujący.  
  
```
HRESULT RemoveHandle(HANDLE hObject) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *hObject*  
 Dojście do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Po usunięciu uchwytu [IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) będzie wywoływana dla skojarzonego obiektu, który został przekazany do [AddHandle](#addhandle). Jeśli to wywołanie nie powiedzie się, `CWorkerThread` wywoła Windows [funkcja CloseHandle](https://msdn.microsoft.com/library/windows/desktop/ms724211) funkcji na dojście.  
  
##  <a name="shutdown"></a>  CWorkerThread::Shutdown  
 Wywołaj tę metodę, aby zamknąć wątku roboczego.  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *dwWait*  
 Czas w milisekundach czas oczekiwania, aż wątek procesu roboczego zamknąć. ATL_WORKER_THREAD_WAIT wartość domyślna to 10 sekund. Jeśli to konieczne, można zdefiniować własne wartości dla tego symbolu, przed dołączeniem atlutil.h. 
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK na powodzenie lub błąd HRESULT w przypadku awarii, np. Jeśli wartość limitu czasu *dwWait*, zostanie przekroczony.  
  
### <a name="remarks"></a>Uwagi  
 Aby ponownie użyć obiektu, wywołaj [CWorkerThread::Initialize](#initialize) po wywołaniu tej metody.  
  
 Należy pamiętać, że wywołanie `Shutdown` inicjowane za pomocą wskaźnika do innego obiektu `CWorkerThread` obiekt nie ma wpływu i zawsze zwraca wartość S_OK.  
  
## <a name="see-also"></a>Zobacz też  
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [Klasy](../../atl/reference/atl-classes.md)   
 [Wielowątkowość: Tworzenie wątków roboczych](../../parallel/multithreading-creating-worker-threads.md)   
 [Interfejs IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)
