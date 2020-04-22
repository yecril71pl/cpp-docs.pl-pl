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
ms.openlocfilehash: 6264bb6bc9070b5ce170b294f9db0d371e7b6b71
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747668"
---
# <a name="cnonstatelessworker-class"></a>Klasa CNonStatelessWorker

Odbiera żądania z puli wątków i przekazuje je do obiektu roboczego, który jest tworzony i niszczony na każde żądanie.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class Worker>
class CNonStatelessWorker
```

#### <a name="parameters"></a>Parametry

*Pracownik*<br/>
Klasa wątku roboczego zgodna z [archetypem procesu roboczego](../../atl/reference/worker-archetype.md) odpowiednia do obsługi żądań w kolejce na [CThreadPool](../../atl/reference/cthreadpool-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CNonStatelessWorker::Typ żądania](#requesttype)|Implementacja [WorkerArchetype::RequestType](worker-archetype.md#requesttype).|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CNonStatelessWorker::Wykonaj](#execute)|Implementacja [WorkerArchetype::Execute](worker-archetype.md#execute).|
|[CNonStatelessWorker::Inicjalizuj](#initialize)|Implementacja [WorkerArchetype::Initialize](worker-archetype.md#initialize).|
|[CNonStatelessWorker::Zakończ](#terminate)|Implementacja [WorkerArchetype::Terminate](worker-archetype.md#terminate).|

## <a name="remarks"></a>Uwagi

Ta klasa jest prostym wątkiem roboczym do użytku z [CThreadPool](../../atl/reference/cthreadpool-class.md). Ta klasa nie zapewnia żadnych możliwości obsługi żądań własnych. Zamiast tego wystąpienia jednego wystąpienia *worker* na żądanie i deleguje implementacji jego metod do tego wystąpienia.

Zaletą tej klasy jest to, że zapewnia wygodny sposób, aby zmienić model stanu dla istniejących klas wątku roboczego. `CThreadPool`utworzy pojedynczy proces roboczy przez cały okres istnienia wątku, więc jeśli klasa robocza przechowuje stan, będzie go przechowywać w wielu żądaniach. Po prostu zawijania `CNonStatelessWorker` tej klasy w `CThreadPool`szablonie przed użyciem go z , okres istnienia pracownika i stan posiada jest ograniczona do pojedynczego żądania.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

## <a name="cnonstatelessworkerexecute"></a><a name="execute"></a>CNonStatelessWorker::Wykonaj

Implementacja [WorkerArchetype::Execute](worker-archetype.md#execute).

```cpp
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>Uwagi

Ta metoda tworzy wystąpienie *Worker* klasy na stosie i wywołuje [initialize](worker-archetype.md#initialize) na tym obiekcie. Jeśli inicjowanie zakończy się pomyślnie, ta metoda wywołuje również [Execute](worker-archetype.md#execute) i [Terminate](worker-archetype.md#terminate) na tym samym obiekcie.

## <a name="cnonstatelessworkerinitialize"></a><a name="initialize"></a>CNonStatelessWorker::Inicjalizuj

Implementacja [WorkerArchetype::Initialize](worker-archetype.md#initialize).

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Ta klasa nie wykonuje inicjowania w . `Initialize`

## <a name="cnonstatelessworkerrequesttype"></a><a name="requesttype"></a>CNonStatelessWorker::Typ żądania

Implementacja [WorkerArchetype::RequestType](worker-archetype.md#requesttype).

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>Uwagi

Ta klasa obsługuje ten sam typ elementu pracy, co klasa używana dla *parametru* Szablon procesu roboczego. Zobacz [CNonStatelessWorker Omówienie,](../../atl/reference/cnonstatelessworker-class.md) aby uzyskać szczegółowe informacje.

## <a name="cnonstatelessworkerterminate"></a><a name="terminate"></a>CNonStatelessWorker::Zakończ

Implementacja [WorkerArchetype::Terminate](worker-archetype.md#terminate).

```cpp
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>Uwagi

Ta klasa nie wykonuje żadnych `Terminate`oczyszczania w .

## <a name="see-also"></a>Zobacz też

[Klasa CThreadPool](../../atl/reference/cthreadpool-class.md)<br/>
[Archetyp pracownika](../../atl/reference/worker-archetype.md)<br/>
[Klasy](../../atl/reference/atl-classes.md)
