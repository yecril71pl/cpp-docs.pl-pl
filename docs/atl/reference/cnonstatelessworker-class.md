---
title: Klasa CNonStatelessWorker | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
dev_langs: C++
helpviewer_keywords: CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 565324b4853880f8dcfafd83f9ba03439b4a7efa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cnonstatelessworker-class"></a>Klasa CNonStatelessWorker
Odbiera żądania z puli wątków i przekazuje je do obiektu procesu roboczego, który zostanie utworzona i zniszczona na każdym żądaniu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Worker>  
class CNonStatelessWorker
```  
  
#### <a name="parameters"></a>Parametry  
 *Proces roboczy*  
 Klasy wątku roboczego odpowiadające [archetype procesu roboczego](../../atl/reference/worker-archetype.md) nadających się do obsługi żądań w kolejce na [CThreadPool](../../atl/reference/cthreadpool-class.md).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CNonStatelessWorker::RequestType](#requesttype)|Implementacja [WorkerArchetype::RequestType](worker-archetype.md#requesttype).|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CNonStatelessWorker::Execute](#execute)|Implementacja [WorkerArchetype::Execute](worker-archetype.md#execute).|  
|[CNonStatelessWorker::Initialize](#initialize)|Implementacja [WorkerArchetype::Initialize](worker-archetype.md#initialize).|  
|[CNonStatelessWorker::Terminate](#terminate)|Implementacja [WorkerArchetype::Terminate](worker-archetype.md#terminate).|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa jest wątku roboczego prostego do użycia z [CThreadPool](../../atl/reference/cthreadpool-class.md). Ta klasa nie zapewnia żadnych możliwości obsługi żądań własnych. Zamiast tego tworzy wystąpienie jednego wystąpienia *procesu roboczego* na żądanie i deleguje implementacji metody wystąpienia.  
  
 Zaletą tej klasy jest to wygodny sposób zmień model stanu istniejące klasy wątku roboczego. `CThreadPool`spowoduje utworzenie pojedynczego procesu roboczego przez czas ich istnienia wątku, więc jeśli klasa procesu roboczego przechowuje stan, będą przechowywane go użytek wielu żądań. Po prostu zawijania tej klasy w `CNonStatelessWorker` szablon przed jego z użyciem `CThreadPool`, okres istnienia elementu roboczego i stan przechowuje, jest ograniczona do pojedynczego żądania.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlutil.h  
  
##  <a name="execute"></a>CNonStatelessWorker::Execute  
 Implementacja [WorkerArchetype::Execute](worker-archetype.md#execute).  

  
```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda tworzy wystąpienie *procesu roboczego* klasy na stosie i wywołania [zainicjować](worker-archetype.md#initialize) dla tego obiektu. Jeśli inicjowanie zakończy się pomyślnie, ta metoda wywołuje również [Execute](worker-archetype.md#execute) i [przerwania](worker-archetype.md#terminate) na tym samym obiekcie.  

  
##  <a name="initialize"></a>CNonStatelessWorker::Initialize  
 Implementacja [WorkerArchetype::Initialize](worker-archetype.md#initialize).  
  
```
BOOL Initialize(void* /* pvParam */) throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość PRAWDA.  
  
### <a name="remarks"></a>Uwagi  
 Ta klasa nie robi inicjowanie `Initialize`.  
  
##  <a name="requesttype"></a>CNonStatelessWorker::RequestType  
 Implementacja [WorkerArchetype::RequestType](worker-archetype.md#requesttype).  
  
```
typedef Worker::RequestType RequestType;
```  
  
### <a name="remarks"></a>Uwagi  
 Ta klasa obsługuje tego samego typu elementu roboczego jako klasa służy do *procesu roboczego* parametru szablonu. Zobacz [omówienie CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md) szczegółowe informacje.  
  
##  <a name="terminate"></a>CNonStatelessWorker::Terminate  
 Implementacja [WorkerArchetype::Terminate](worker-archetype.md#terminate).  
  
```
void Terminate(void* /* pvParam */) throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta klasa wykonanie oczyszczania `Terminate`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CThreadPool](../../atl/reference/cthreadpool-class.md)   
 [Archetype procesu roboczego](../../atl/reference/worker-archetype.md)   
 [Klasy](../../atl/reference/atl-classes.md)
