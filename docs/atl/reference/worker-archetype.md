---
title: Archetyp pracownika
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: b0b32232d7386df0c0f13a1c3af1003369b906e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329347"
---
# <a name="worker-archetype"></a>Archetyp pracownika

Klasy zgodne z archetypem *procesu roboczego* zapewniają kod do przetwarzania elementów pracy w kolejce w puli wątków.

**Wdrażanie**

Aby zaimplementować klasę zgodną z tym archetypem, klasa musi zawierać następujące funkcje:

|Metoda|Opis|
|------------|-----------------|
|[Initialize](#initialize)|Wywoływany w celu zainicjowania obiektu procesu roboczego przed przekazaniem jakichkolwiek żądań do [żądania Execute](#execute).|
|[Realizacja](#execute)|Wywoływana do przetwarzania elementu pracy.|
|[Terminate](#terminate)|Wywoływany do niezainicjowania obiektu procesu roboczego po przekazaniu wszystkich żądań do [execute](#execute).|

|Typedef|Opis|
|-------------|-----------------|
|[RequestType](#requesttype)|Typedef dla typu elementu pracy, który może być przetwarzany przez klasę roboczą.|

Typowa klasa *pracownika* wygląda następująco:

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**Istniejące implementacje**

Klasy te są zgodne z tym archetypem:

|Klasa|Opis|
|-----------|-----------------|
|[CNonStatelessPracownik](../../atl/reference/cnonstatelessworker-class.md)|Odbiera żądania z puli wątków i przekazuje je do obiektu roboczego, który jest tworzony i niszczony dla każdego żądania.|

**Użycie**

Te parametry szablonu oczekują, że klasa będzie zgodna z tym archetypem:

|Nazwa parametru|Używany przez|
|--------------------|-------------|
|*Pracownik*|[Cthreadpool](../../atl/reference/cthreadpool-class.md)|
|*Pracownik*|[CNonStatelessPracownik](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

## <a name="workerarchetypeexecute"></a><a name="execute"></a>Typ roboczy::Wykonaj

Wywoływana do przetwarzania elementu pracy.

```
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>Parametry

*Żądanie*<br/>
Element pracy do przetworzenia. Element roboczy jest tego `RequestType`samego typu co .

*pvPracerParam*<br/>
Parametr niestandardowy zrozumiały dla klasy procesu roboczego. Również przekazywane `WorkerArchetype::Initialize` `Terminate`do i .

*pZamknienie*<br/>
Wskaźnik do [struktury NAKŁADANE](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) używane do tworzenia kolejki, na którym elementy robocze były umieszczane w kolejce.

## <a name="workerarchetypeinitialize"></a><a name="initialize"></a>Typ roboczy::Inicjalizacja

Wywoływany w celu zainicjowania obiektu procesu `WorkerArchetype::Execute`roboczego przed przekazaniem jakichkolwiek żądań do .

```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>Parametry

*pvParam*<br/>
Parametr niestandardowy zrozumiały dla klasy procesu roboczego. Również przekazywane `WorkerArchetype::Terminate` `WorkerArchetype::Execute`do i .

### <a name="return-value"></a>Wartość zwracana

Powrót TRUE na sukces, FALSE na niepowodzenie.

## <a name="workerarchetyperequesttype"></a><a name="requesttype"></a>Typ roboczy::Typ żądania

Typedef dla typu elementu pracy, który może być przetwarzany przez klasę roboczą.

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>Uwagi

Ten typ musi być używany `WorkerArchetype::Execute` jako pierwszy parametr i musi być zdolny do rzutowania do i z ULONG_PTR.

## <a name="workerarchetypeterminate"></a><a name="terminate"></a>Typ roboczy::Zakończenie

Wywoływana w celu niezainicjowania obiektu procesu `WorkerArchetype::Execute`roboczego po przekazaniu wszystkich żądań do ).

```
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>Parametry

*pvParam*<br/>
Parametr niestandardowy zrozumiały dla klasy procesu roboczego. Również przekazywane `WorkerArchetype::Initialize` `WorkerArchetype::Execute`do i .

## <a name="see-also"></a>Zobacz też

[Pojęcia](../../atl/active-template-library-atl-concepts.md)<br/>
[Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)
