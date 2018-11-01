---
title: Klasa CNonStatelessWorker
ms.date: 11/04/2016
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
helpviewer_keywords:
- CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
ms.openlocfilehash: 7aaae3728113cfd91c0655d2eac445cdd4b34246
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619633"
---
# <a name="cnonstatelessworker-class"></a>Klasa CNonStatelessWorker

Odbiera żądania z puli wątków i przekazuje je do obiektu procesu roboczego, który jest tworzona i niszczona przy każdym żądaniu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class Worker>
class CNonStatelessWorker
```

#### <a name="parameters"></a>Parametry

*Proces roboczy*<br/>
Klasa wątek procesu roboczego zgodnych z [archetyp procesu roboczego](../../atl/reference/worker-archetype.md) nadających się do obsługi żądań w kolejce na [CThreadPool](../../atl/reference/cthreadpool-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

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

Ta klasa jest wątku roboczego prosty do użycia z usługą [CThreadPool](../../atl/reference/cthreadpool-class.md). Ta klasa nie zapewnia jakichkolwiek możliwości obsługi żądań własne. Zamiast tego metoda tworzy jedno wystąpienie *procesu roboczego* na żądanie i wykonania jego metod do tego wystąpienia deleguje odpowiednie uprawnienia.

Zaletą tej klasy jest zapewnia wygodny sposób, aby zmienić model stanu dla istniejących klas wątku roboczego. `CThreadPool` spowoduje utworzenie pojedynczego procesu roboczego przez okres istnienia wątku, więc jeśli klasa proces roboczy przechowuje stan, będą przechowywane jego dla wielu żądań. Po prostu opakowując tej klasy w `CNonStatelessWorker` szablon przed jego z użyciem `CThreadPool`, okres istnienia procesu roboczego i stan przechowuje, jest ograniczona do pojedynczego żądania.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

##  <a name="execute"></a>  CNonStatelessWorker::Execute

Implementacja [WorkerArchetype::Execute](worker-archetype.md#execute).

```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>Uwagi

Ta metoda tworzy wystąpienie *procesu roboczego* klasy na stosie i wywołania [zainicjować](worker-archetype.md#initialize) dla tego obiektu. Jeśli inicjowanie zakończy się pomyślnie, ta metoda wywołuje również [Execute](worker-archetype.md#execute) i [Zakończ](worker-archetype.md#terminate) na tym samym obiekcie.

##  <a name="initialize"></a>  CNonStatelessWorker::Initialize

Implementacja [WorkerArchetype::Initialize](worker-archetype.md#initialize).

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Ta klasa nie wykonuje żadnych inicjowania `Initialize`.

##  <a name="requesttype"></a>  CNonStatelessWorker::RequestType

Implementacja [WorkerArchetype::RequestType](worker-archetype.md#requesttype).

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>Uwagi

Ta klasa obsługuje ten sam typ elementu roboczego jako klasa umożliwiający *procesu roboczego* parametru szablonu. Zobacz [Przegląd CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md) Aby uzyskać szczegółowe informacje.

##  <a name="terminate"></a>  CNonStatelessWorker::Terminate

Implementacja [WorkerArchetype::Terminate](worker-archetype.md#terminate).

```
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>Uwagi

Ta klasa wykonanie oczyszczania `Terminate`.

## <a name="see-also"></a>Zobacz też

[Klasa CThreadPool](../../atl/reference/cthreadpool-class.md)<br/>
[Archetyp procesu roboczego](../../atl/reference/worker-archetype.md)<br/>
[Klasy](../../atl/reference/atl-classes.md)
