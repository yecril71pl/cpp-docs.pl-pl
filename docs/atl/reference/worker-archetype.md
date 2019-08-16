---
title: Archetype procesu roboczego
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: 7f28b9e64c88a5be440417dd9d22f129ee7d6edf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495268"
---
# <a name="worker-archetype"></a>Archetype procesu roboczego

Klasy, które są zgodne z archetypeem roboczym, udostępniają kod do przetwarzania elementów roboczych w kolejce w puli wątków.

**Implementacja**

Aby zaimplementować klasę, która jest zgodna z tym Archetype, Klasa musi udostępniać następujące funkcje:

|Metoda|Opis|
|------------|-----------------|
|[Initialize](#initialize)|Wywołuje się, by zainicjować obiekt Worker przed przekazaniem żądań do [wykonania](#execute).|
|[Execute](#execute)|Wywołuje się, by przetworzyć element roboczy.|
|[Terminate](#terminate)|Wywołuje się, by zainicjować obiekt roboczy po przekazaniu wszystkich żądań do [wykonania](#execute).|

|Własne|Opis|
|-------------|-----------------|
|[RequestType](#requesttype)|Element typedef dla typu elementu roboczego, który może być przetwarzany przez klasę Worker.|

Typowa Klasa *procesu roboczego* wygląda następująco:

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**Istniejące implementacje**

Te klasy są zgodne z tym Archetype:

|Class|Opis|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Odbiera żądania z puli wątków i przekazuje je do obiektu procesu roboczego, który jest tworzony i niszczony dla każdego żądania.|

**Korzystanie**

Te parametry szablonu oczekują, aby Klasa była zgodna z tą Archetype:

|Nazwa parametru|Używane przez|
|--------------------|-------------|
|*Odpowiedzialn*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*Odpowiedzialn*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil. h

## <a name="execute"></a>WorkerArchetype:: Execute

Wywołuje się, by przetworzyć element roboczy.

```
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>Parametry

*żądając*<br/>
Element roboczy, który ma zostać przetworzony. Element roboczy jest tego samego typu co `RequestType`.

*pvWorkerParam*<br/>
Niestandardowy parametr zrozumiały dla klasy Worker. Przeszedł również `WorkerArchetype::Initialize` do `Terminate`i.

*pOverlapped*<br/>
Wskaźnik do nakładającego się struktury użytego do utworzenia kolejki, w której elementy robocze zostały umieszczone w kolejce. [](/windows/win32/api/minwinbase/ns-minwinbase-overlapped)

## <a name="initialize"></a>WorkerArchetype:: Initialize

Wywołuje się, by zainicjować obiekt Worker przed przekazaniem żądań `WorkerArchetype::Execute`do.
```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>Parametry

*pvParam*<br/>
Niestandardowy parametr zrozumiały dla klasy Worker. Przeszedł również `WorkerArchetype::Terminate` do `WorkerArchetype::Execute`i.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

## <a name="requesttype"></a>WorkerArchetype:: RequestType

Element typedef dla typu elementu roboczego, który może być przetwarzany przez klasę Worker.

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>Uwagi

Ten typ musi być używany jako pierwszy parametr `WorkerArchetype::Execute` i musi być w stanie rzutować do i z ULONG_PTR.

## <a name="terminate"></a>WorkerArchetype:: Przerwij

Wywołuje się, by zainicjować obiekt roboczy po przekazaniu wszystkich żądań do `WorkerArchetype::Execute`).

```
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>Parametry

*pvParam*<br/>
Niestandardowy parametr zrozumiały dla klasy Worker. Przeszedł również `WorkerArchetype::Initialize` do `WorkerArchetype::Execute`i.

## <a name="see-also"></a>Zobacz także

[Pojęcia](../../atl/active-template-library-atl-concepts.md)<br/>
[Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)
