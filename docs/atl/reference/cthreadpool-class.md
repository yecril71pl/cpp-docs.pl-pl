---
title: Klasa CThreadPool | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64a165bdffa9f37241991af919d60de2e0dc7a96
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cthreadpool-class"></a>Klasa CThreadPool
Ta klasa udostępnia puli wątków roboczych, które przetwarzają kolejki elementów roboczych.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Worker, class ThreadTraits = DefaultThreadTraits>  
class CThreadPool : public IThreadPoolConfig
```  
  
#### <a name="parameters"></a>Parametry  
 *Proces roboczy*  
 Klasa odpowiadające [archetype procesu roboczego](../../atl/reference/worker-archetype.md) podanie kodu użyty do przetwarzania elementów w kolejce dla puli wątków roboczych.  
  
 `ThreadTraits`  
 Klasa, zapewniając funkcję służącą do Tworzenie wątków w puli.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CThreadPool::CThreadPool](#cthreadpool)|Konstruktor dla puli wątków.|  
|[CThreadPool:: ~ CThreadPool](#dtor)|Destruktor dla puli wątków.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CThreadPool::AddRef](#addref)|Implementacja `IUnknown::AddRef`.|  
|[CThreadPool::GetNumThreads](#getnumthreads)|Wywołaj tę metodę, aby pobrać liczbę wątków w puli.|  
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Wywołaj tę metodę, aby pobrać uchwytu portu zakończenia We/Wy, które są używane do kolejki elementów roboczych.|  
|[CThreadPool::GetSize](#getsize)|Wywołaj tę metodę, aby pobrać liczbę wątków w puli.|  
|[CThreadPool::GetTimeout](#gettimeout)|Wywołanie tej metody, aby uzyskać maksymalny czas (w milisekundach) oczekiwania na wątek zamknięcia puli wątków.|  
|[CThreadPool::Initialize](#initialize)|Wywołaj tę metodę, aby zainicjować puli wątków.|  
|[CThreadPool::QueryInterface](#queryinterface)|Implementacja **IUnknown::QueryInterface**.|  
|[CThreadPool::QueueRequest](#queuerequest)|Wywołanie tej metody można umieścić w kolejce elementu pracy do obsługi przez wątek w puli.|  
|[CThreadPool::Release](#release)|Implementacja `IUnknown::Release`.|  
|[CThreadPool::SetSize](#setsize)|Wywołanie tej metody, aby ustawić liczbę wątków w puli.|  
|[CThreadPool::SetTimeout](#settimeout)|Wywołaj tę metodę, aby ustawić maksymalny czas (w milisekundach) oczekiwania na wątek zamknięcia puli wątków.|  
|[CThreadPool::Shutdown](#shutdown)|Wywołaj tę metodę, aby zamknąć puli wątków.|  
  
## <a name="remarks"></a>Uwagi  
 Wątków w puli są tworzone i niszczone podczas puli jest zainicjowany, rozmiaru lub go zamknąć. Wystąpienie klasy *procesu roboczego* zostanie utworzona na stosie każdy wątek roboczy w puli. Każde wystąpienie będzie funkcjonować przez czas ich istnienia wątku.  
  
 Natychmiast po utworzeniu przez wątek *procesu roboczego*:: `Initialize` zostanie wywołana dla obiektu skojarzone z tym wątku. Bezpośrednio przed zniszczenie wątku *procesu roboczego*:: `Terminate` zostanie wywołana. Obie metody, należy zaakceptować **void\***  argumentu. Wartość tego argumentu jest przekazywana do puli wątków za pośrednictwem `pvWorkerParam` parametr [CThreadPool::Initialize](#initialize).  
  
 Brak dostępnych elementów roboczych w wątkach kolejki i proces roboczy pracy, wątek roboczy będzie pobierać element poza kolejki i wywołanie **Execute** metody *procesu roboczego* obiekt dla tego wątku. Trzy elementy są następnie przekazywane do metody: element z kolejki, taka sama `pvWorkerParam` przekazany do *procesu roboczego*:: `Initialize` i *procesu roboczego*:: `Terminate`i wskaźnika do [OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342) struktura używana dla kolejki portu zakończenia We/Wy.  
  
 *Procesu roboczego* klasy deklaruje typ elementów, które zostaną umieszczone w kolejce dla puli wątków zapewniając typem typedef *procesu roboczego*:: `RequestType`. Ten typ musi być w stanie są rzucane do i z **typu ULONG_PTR**.  
  
 Przykład *procesu roboczego* jest klasa [CNonStatelessWorker klasy](../../atl/reference/cnonstatelessworker-class.md).  
  
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
 Ta klasa nie implementuje okres istnienia formantu przy użyciu liczenie odwołań w.  
  
##  <a name="cthreadpool"></a>  CThreadPool::CThreadPool  
 Konstruktor dla puli wątków.  
  
```
CThreadPool() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje wartość limitu czasu na `ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT`. Czas domyślny to 36 sekund. W razie potrzeby można zdefiniować przed dołączeniem atlutil.h własne dodatnią liczbę całkowitą dla tego symbolu.  
  
##  <a name="dtor"></a>  CThreadPool:: ~ CThreadPool  
 Destruktor dla puli wątków.  
  
```
~CThreadPool() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [CThreadPool::Shutdown](#shutdown).  
  
##  <a name="getnumthreads"></a>  CThreadPool::GetNumThreads  
 Wywołaj tę metodę, aby pobrać liczbę wątków w puli.  
  
```
int GetNumThreads() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę wątków w puli.  
  
##  <a name="getqueuehandle"></a>  CThreadPool::GetQueueHandle  
 Wywołaj tę metodę, aby pobrać uchwytu portu zakończenia We/Wy, które są używane do kolejki elementów roboczych.  
  
```
HANDLE GetQueueHandle() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca uchwyt kolejki lub wartość NULL, jeśli nie została zainicjowana puli wątków.  
  
##  <a name="getsize"></a>  CThreadPool::GetSize  
 Wywołaj tę metodę, aby pobrać liczbę wątków w puli.  
  
```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pnNumThreads`  
 [out] Adres zmiennej, która w przypadku powodzenia otrzymuje to liczba wątków w puli.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="gettimeout"></a>  CThreadPool::GetTimeout  
 Wywołanie tej metody, aby uzyskać maksymalny czas (w milisekundach) oczekiwania na wątek zamknięcia puli wątków.  
  
```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pdwMaxWait`  
 [out] Adres zmiennej, która w przypadku powodzenia otrzymuje maksymalny czas (w milisekundach) oczekiwania na wątek zamknięcia puli wątków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość limitu czasu jest używana przez [CThreadPool::Shutdown](#shutdown) Jeśli żadna inna wartość nie jest dostarczony do tej metody.  
  
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
 `pvWorkerParam`  
 Parametr proces roboczy do przekazania do obiektu wątku roboczego `Initialize`, **Execute**, i `Terminate` metody.  
  
 `nNumThreads`  
 Żądana liczba wątków w puli.  
  
 Jeśli `nNumThreads` jest ujemna, jego wartość bezwzględna zostanie pomnożona przez liczbę procesorów na maszynie, aby uzyskać łączna liczba wątków.  
  
 Jeśli `nNumThreads` wynosi zero, `ATLS_DEFAULT_THREADSPERPROC` zostanie pomnożona przez liczbę procesorów na maszynie, aby uzyskać łączna liczba wątków.  Wartość domyślna to 2 wątków na procesor. W razie potrzeby można zdefiniować przed dołączeniem atlutil.h własne dodatnią liczbę całkowitą dla tego symbolu.
  
 `dwStackSize`  
 Rozmiar stosu dla każdego wątku w puli.  
  
 *hCompletion*  
 Dojście obiektu do skojarzenia z portem ukończenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="queryinterface"></a>  CThreadPool::QueryInterface  
 Implementacja **IUnknown::QueryInterface**.  
  
```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Obiekty z tej klasy można pomyślnie zapytanie dla **IUnknown** i [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md) interfejsów.  
  
##  <a name="queuerequest"></a>  CThreadPool::QueueRequest  
 Wywołanie tej metody można umieścić w kolejce elementu pracy do obsługi przez wątek w puli.  
  
```
BOOL QueueRequest(Worker::RequestType request) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `request`  
 Żądanie do kolejki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda dodaje elementu roboczego do kolejki. Wątki w puli wybierać elementy poza kolejki w kolejności, w którym są odbierane.  
  
##  <a name="release"></a>  CThreadPool::Release  
 Implementacja `IUnknown::Release`.  
  
```
ULONG STDMETHODCALLTYPE Release() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość 1.  
  
### <a name="remarks"></a>Uwagi  
 Ta klasa nie implementuje okres istnienia formantu przy użyciu liczenie odwołań w.  
  
##  <a name="setsize"></a>  CThreadPool::SetSize  
 Wywołanie tej metody, aby ustawić liczbę wątków w puli.  
  
```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nNumThreads`  
 Żądana liczba wątków w puli.  
  
 Jeśli `nNumThreads` jest ujemna, jego wartość bezwzględna zostanie pomnożona przez liczbę procesorów na maszynie, aby uzyskać łączna liczba wątków.  
  
 Jeśli `nNumThreads` wynosi zero, `ATLS_DEFAULT_THREADSPERPROC` zostanie pomnożona przez liczbę procesorów na maszynie, aby uzyskać łączna liczba wątków. Wartość domyślna to 2 wątków na procesor. W razie potrzeby można zdefiniować przed dołączeniem atlutil.h własne dodatnią liczbę całkowitą dla tego symbolu.
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli liczba określonych wątków jest mniejsza niż liczba wątków w puli, obiekt umieszcza komunikatu zamknięcia w kolejce do pobrania przez wątek oczekiwania. Podczas oczekiwania wątku pobiera komunikat poza kolejki, powiadamia puli wątków i kończy procedurę wątku. Ten proces jest powtarzany do momentu liczbę wątków w puli osiągnie określony numer lub wątek nie został zakończony w okresie wskazanym przez [GetTimeout](#gettimeout)/ [SetTimeout](#settimeout). W takiej sytuacji metoda zwróci wartość HRESULT odpowiadający **WAIT_TIMEOUT** i komunikatów oczekujących zamknięcie zostało anulowane.  
  
##  <a name="settimeout"></a>  CThreadPool::SetTimeout  
 Wywołaj tę metodę, aby ustawić maksymalny czas (w milisekundach) oczekiwania na wątek zamknięcia puli wątków.  
  
```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwMaxWait`  
 Żądana maksymalny czas (w milisekundach) oczekiwania na wątek zamknięcia puli wątków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Limit czasu jest ustawiana na `ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT`. Czas domyślny to 36 sekund. W razie potrzeby można zdefiniować przed dołączeniem atlutil.h własne dodatnią liczbę całkowitą dla tego symbolu. 
  
 Należy pamiętać, że `dwMaxWait` to czas oczekiwania puli dla pojedynczego wątku zamknięcia. Maksymalny czas, który można podjąć w celu usunięcia wiele wątków z puli może być nieco mniejsze `dwMaxWait` pomnożona przez liczbę wątków.  
  
##  <a name="shutdown"></a>  CThreadPool::Shutdown  
 Wywołaj tę metodę, aby zamknąć puli wątków.  
  
```
void Shutdown(DWORD dwMaxWait = 0) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwMaxWait`  
 Żądana maksymalny czas (w milisekundach) oczekiwania na wątek zamknięcia puli wątków. Jeśli podano 0 lub brak wartości, ta metoda użyje limit czasu ustawiony [CThreadPool::SetTimeout](#settimeout).  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda generuje żądanie zamknięcia wszystkich wątków w puli. Po przekroczeniu limitu czasu, ta metoda wywoła [funkcji TerminateThread](http://msdn.microsoft.com/library/windows/desktop/ms686717) w którymkolwiek wątku, który nie został zakończony. Ta metoda jest wywoływana automatycznie przez destruktor klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)   
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [Klasy](../../atl/reference/atl-classes.md)
