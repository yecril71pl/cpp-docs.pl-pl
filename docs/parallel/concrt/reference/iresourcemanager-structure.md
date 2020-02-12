---
title: IResourceManager — Struktura
ms.date: 03/27/2019
f1_keywords:
- IResourceManager
- CONCRTRM/concurrency::IResourceManager
- CONCRTRM/concurrency::IResourceManager::IResourceManager::OSVersion
- CONCRTRM/concurrency::IResourceManager::IResourceManager::CreateNodeTopology
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetAvailableNodeCount
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetFirstNode
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Reference
- CONCRTRM/concurrency::IResourceManager::IResourceManager::RegisterScheduler
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Release
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
ms.openlocfilehash: 7ce5b07f5eb4272db1b00b7f0105b790ddbb28fe
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142985"
---
# <a name="iresourcemanager-structure"></a>IResourceManager — Struktura

Interfejs Menedżer zasobów środowisko uruchomieniowe współbieżności. Jest to interfejs, za pomocą którego harmonogramy komunikują się z Menedżer zasobów.

## <a name="syntax"></a>Składnia

```cpp
struct IResourceManager;
```

## <a name="members"></a>Members

### <a name="public-enumerations"></a>Wyliczenia publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[IResourceManager:: OSVersion](#osversion)|Typ wyliczany reprezentujący wersję systemu operacyjnego.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[IResourceManager:: CreateNodeTopology —](#createnodetopology)|Ta metoda jest dostępna tylko w kompilacjach debugowania środowiska uruchomieniowego, ponieważ jest to punkt zaczepienia testu zaprojektowany w celu ułatwienia testowania Menedżer zasobów w różnych topologiach sprzętowych, bez konieczności faktycznego sprzętu zgodnego z konfiguracją. W przypadku kompilacji detalicznych środowiska uruchomieniowego ta metoda zwróci wartość bez wykonywania żadnej akcji.|
|[IResourceManager:: GetAvailableNodeCount —](#getavailablenodecount)|Zwraca liczbę węzłów dostępnych dla Menedżer zasobów.|
|[IResourceManager:: GetFirstNode —](#getfirstnode)|Zwraca pierwszy węzeł w kolejności wyliczania zgodnie z definicją Menedżer zasobów.|
|[IResourceManager:: Reference](#reference)|Zwiększa liczbę odwołań w wystąpieniu Menedżer zasobów.|
|[IResourceManager:: RegisterScheduler —](#registerscheduler)|Rejestruje harmonogram z Menedżer zasobów. Po zarejestrowaniu harmonogramu powinien on komunikować się z Menedżer zasobów przy użyciu zwróconego interfejsu `ISchedulerProxy`.|
|[IResourceManager:: Release](#release)|Zmniejsza liczbę odwołań w wystąpieniu Menedżer zasobów. Menedżer zasobów jest niszczona, gdy jej liczba odwołań przejdzie do `0`.|

## <a name="remarks"></a>Uwagi

Użyj funkcji [Serviceresourcemanager](concurrency-namespace-functions.md) , aby uzyskać interfejs do wystąpienia pojedynczego Menedżer zasobów. Metoda zwiększa liczbę odwołań na Menedżer zasobów i należy wywołać metodę [IResourceManager:: Release](#release) , aby zwolnić odwołanie po zakończeniu z Menedżer zasobów. Zazwyczaj każdy utworzony harmonogram wywoła tę metodę podczas tworzenia i zwolni odwołanie do Menedżer zasobów po jego zamknięciu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IResourceManager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="createnodetopology"></a>IResourceManager:: CreateNodeTopology —, Metoda

Ta metoda jest dostępna tylko w kompilacjach debugowania środowiska uruchomieniowego, ponieważ jest to punkt zaczepienia testu zaprojektowany w celu ułatwienia testowania Menedżer zasobów w różnych topologiach sprzętowych, bez konieczności faktycznego sprzętu zgodnego z konfiguracją. W przypadku kompilacji detalicznych środowiska uruchomieniowego ta metoda zwróci wartość bez wykonywania żadnej akcji.

```cpp
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>Parametry

*nodeCount*<br/>
Liczba symulowanych węzłów procesora.

*pCoreCount*<br/>
Tablica, która określa liczbę rdzeni w każdym węźle.

*pNodeDistance*<br/>
Macierz określająca odległość między dwoma węzłami. Ten parametr może mieć wartość `NULL`.

*pProcessorGroups*<br/>
Tablica, która określa grupę procesorów, do której należy każdy węzeł.

### <a name="remarks"></a>Uwagi

[invalid_argument](../../../standard-library/invalid-argument-class.md) jest generowany, jeśli parametr `nodeCount` ma wartość, `0` została przeniesiona, lub jeśli parametr `pCoreCount` ma wartość `NULL`.

[invalid_operation](invalid-operation-class.md) jest generowany, jeśli ta metoda jest wywoływana, gdy istnieją inne harmonogramy w procesie.

## <a name="getavailablenodecount"></a>IResourceManager:: GetAvailableNodeCount —, Metoda

Zwraca liczbę węzłów dostępnych dla Menedżer zasobów.

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Liczba węzłów dostępnych dla Menedżer zasobów.

## <a name="getfirstnode"></a>IResourceManager:: GetFirstNode —, Metoda

Zwraca pierwszy węzeł w kolejności wyliczania zgodnie z definicją Menedżer zasobów.

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Pierwszy węzeł w kolejności wyliczania zgodnie z definicją Menedżer zasobów.

## <a name="osversion"></a>IResourceManager:: OSVersion, Wyliczenie

Typ wyliczany reprezentujący wersję systemu operacyjnego.

```cpp
enum OSVersion;
```

## <a name="reference"></a>IResourceManager:: Reference — Metoda

Zwiększa liczbę odwołań w wystąpieniu Menedżer zasobów.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Wynikowy licznik odwołań.

## <a name="registerscheduler"></a>IResourceManager:: RegisterScheduler —, Metoda

Rejestruje harmonogram z Menedżer zasobów. Po zarejestrowaniu harmonogramu powinien on komunikować się z Menedżer zasobów przy użyciu zwróconego interfejsu `ISchedulerProxy`.

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>Parametry

*pScheduler*<br/>
`IScheduler` interfejs do harmonogramu do zarejestrowania.

*version*<br/>
Wersja interfejsu komunikacyjnego, która jest używana przez harmonogram do komunikowania się z Menedżer zasobów. Użycie wersji pozwala Menedżer zasobów na rozwijanie interfejsu komunikacyjnego, umożliwiając programom Scheduler uzyskanie dostępu do starszych funkcji. Harmonogramy, którzy chcą korzystać z funkcji Menedżer zasobów dostępnych w programie Visual Studio 2010, powinny używać `CONCRT_RM_VERSION_1`wersji.

### <a name="return-value"></a>Wartość zwrócona

`ISchedulerProxy` interfejs Menedżer zasobów powiązany z harmonogramem. Harmonogram powinien używać tego interfejsu, aby komunikować się z Menedżer zasobów od tego momentu.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby zainicjować komunikację z Menedżer zasobów. Metoda kojarzy interfejs `IScheduler` dla harmonogramu z interfejsem `ISchedulerProxy` i przekazuje go z powrotem do użytkownika. Możesz użyć zwróconego interfejsu, aby zażądać zasobów wykonawczych do użycia przez harmonogram lub subskrybować wątki przy użyciu Menedżer zasobów. Menedżer zasobów będzie używać elementów zasad z zasad usługi Scheduler zwracanych przez metodę [IScheduler:: GetPolicy](ischeduler-structure.md#getpolicy) , aby określić, jaki typ wątków ma być wykonywany przez harmonogram. Jeśli klucz zasad `SchedulerKind` ma wartość `UmsThreadDefault` i wartość zostanie odczytana z zasad jako `UmsThreadDefault`wartość, interfejs `IScheduler` przeszedł do metody musi być interfejsem `IUMSScheduler`.

Metoda zgłasza wyjątek `invalid_argument`, jeśli parametr `pScheduler` ma wartość `NULL` lub jeśli parametr `version` nie jest prawidłową wersją interfejsu komunikacyjnego.

## <a name="release"></a>IResourceManager:: Release — Metoda

Zmniejsza liczbę odwołań w wystąpieniu Menedżer zasobów. Menedżer zasobów jest niszczona, gdy jej liczba odwołań przejdzie do `0`.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Wynikowy licznik odwołań.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[ISchedulerProxy, struktura](ischedulerproxy-structure.md)<br/>
[IScheduler, struktura](ischeduler-structure.md)
