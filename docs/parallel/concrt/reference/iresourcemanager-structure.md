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
ms.openlocfilehash: 15e27a586fc039791255c01a053f6a1109183f90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368188"
---
# <a name="iresourcemanager-structure"></a>IResourceManager — Struktura

Interfejs menedżera zasobów środowiska wykonawczego współbieżności. Jest to interfejs, za pomocą którego harmonogramy komunikują się z Menedżerem zasobów.

## <a name="syntax"></a>Składnia

```cpp
struct IResourceManager;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-enumerations"></a>Wyliczenia publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IResourceManager::OSVersion](#osversion)|Typ wyliczany reprezentujący wersję systemu operacyjnego.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IResourceManager::CreateNodeTopology](#createnodetopology)|Obecna tylko w kompilacjach debugowania środowiska wykonawczego, ta metoda jest hak testowy zaprojektowany w celu ułatwienia testowania Menedżera zasobów na różnych topologii sprzętu, bez konieczności rzeczywistego sprzętu pasujące do konfiguracji. W przypadku kompilacji sieci sprzedaży środowiska wykonawczego ta metoda zostanie zwracana bez wykonywania żadnych akcji.|
|[IResourceManager::GetAvailableNodeCount](#getavailablenodecount)|Zwraca liczbę węzłów dostępnych dla Menedżera zasobów.|
|[IResourceManager::GetFirstNode](#getfirstnode)|Zwraca pierwszy węzeł w kolejności wyliczenia zdefiniowanej przez Menedżera zasobów.|
|[IResourceManager::Odwołanie](#reference)|Zwiększa liczbę odwołań w wystąpieniu Menedżera zasobów.|
|[IResourceManager::RegisterScheduler](#registerscheduler)|Rejestruje harmonogram w Menedżerze zasobów. Po zarejestrowaniu harmonogramu powinien komunikować się z `ISchedulerProxy` Menedżerem zasobów przy użyciu interfejsu, który jest zwracany.|
|[IResourceManager::Release](#release)|Zmniejsza liczbę odwołań w wystąpieniu Menedżera zasobów. Menedżer zasobów jest niszczony, gdy `0`jego liczba odwołań przechodzi do .|

## <a name="remarks"></a>Uwagi

Funkcja [CreateResourceManager](concurrency-namespace-functions.md) umożliwia uzyskanie interfejsu do wystąpienia Menedżera zasobów singleton. Metoda zwiększa liczbę odwołań na Menedżerze zasobów i należy wywołać [IResourceManager::Release](#release) metody, aby zwolnić odwołanie po zakończeniu z Menedżerem zasobów. Zazwyczaj każdy harmonogram, który tworzysz wywoła tę metodę podczas tworzenia i zwolnić odwołanie do Menedżera zasobów po zamknięciu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IResourceManager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Przestrzeń nazw:** współbieżność

## <a name="iresourcemanagercreatenodetopology-method"></a><a name="createnodetopology"></a>IResourceManager::CreateNodeTopology Metoda

Obecna tylko w kompilacjach debugowania środowiska wykonawczego, ta metoda jest hak testowy zaprojektowany w celu ułatwienia testowania Menedżera zasobów na różnych topologii sprzętu, bez konieczności rzeczywistego sprzętu pasujące do konfiguracji. W przypadku kompilacji sieci sprzedaży środowiska wykonawczego ta metoda zostanie zwracana bez wykonywania żadnych akcji.

```cpp
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>Parametry

*węzełCount*<br/>
Liczba symulowanych węzłów procesora.

*pCoreCount (Licznik pCoreCount)*<br/>
Tablica określająca liczbę rdzeni w każdym węźle.

*pNodeDistance*<br/>
Macierz określająca odległość węzła między dowolnymi dwoma węzłami. Ten parametr może `NULL`mieć wartość .

*pProcessorGrupy*<br/>
Tablica określająca grupę procesorów, do której należy każdy węzeł.

### <a name="remarks"></a>Uwagi

[invalid_argument](../../../standard-library/invalid-argument-class.md) jest zgłaszany, `nodeCount` jeśli parametr `0` ma wartość została przekazana `pCoreCount` w `NULL`lub jeśli parametr ma wartość .

[invalid_operation](invalid-operation-class.md) jest zgłaszany, jeśli ta metoda jest wywoływana, podczas gdy inne harmonogramy istnieją w procesie.

## <a name="iresourcemanagergetavailablenodecount-method"></a><a name="getavailablenodecount"></a>IResourceManager::GetAvailableNodeCount Metoda

Zwraca liczbę węzłów dostępnych dla Menedżera zasobów.

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Liczba węzłów dostępnych dla Menedżera zasobów.

## <a name="iresourcemanagergetfirstnode-method"></a><a name="getfirstnode"></a>IResourceManager::Metoda GetFirstNode

Zwraca pierwszy węzeł w kolejności wyliczenia zdefiniowanej przez Menedżera zasobów.

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy węzeł w kolejności wyliczenia zdefiniowanej przez Menedżera zasobów.

## <a name="iresourcemanagerosversion-enumeration"></a><a name="osversion"></a>IResourceManager::Wyliczenie OSVersion

Typ wyliczany reprezentujący wersję systemu operacyjnego.

```cpp
enum OSVersion;
```

## <a name="iresourcemanagerreference-method"></a><a name="reference"></a>IResourceManager::Metoda referencyjna

Zwiększa liczbę odwołań w wystąpieniu Menedżera zasobów.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Wynikowe liczby odwołań.

## <a name="iresourcemanagerregisterscheduler-method"></a><a name="registerscheduler"></a>IResourceManager::RegisterScheduler Metoda

Rejestruje harmonogram w Menedżerze zasobów. Po zarejestrowaniu harmonogramu powinien komunikować się z `ISchedulerProxy` Menedżerem zasobów przy użyciu interfejsu, który jest zwracany.

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>Parametry

*pScheduler ( pScheduler )*<br/>
Interfejs `IScheduler` do harmonogramu, który ma być zarejestrowany.

*Wersja*<br/>
Wersja interfejsu komunikacyjnego, z drugiej strony, do komunikowania się z Menedżerem zasobów. Za pomocą wersji umożliwia Menedżer zasobów do ewolucji interfejsu komunikacyjnego, umożliwiając jednocześnie harmonogramów, aby uzyskać dostęp do starszych funkcji. Harmonogramy, które chcą korzystać z funkcji Menedżera zasobów obecnych w `CONCRT_RM_VERSION_1`programie Visual Studio 2010, powinny używać wersji .

### <a name="return-value"></a>Wartość zwracana

Interfejs, `ISchedulerProxy` który Menedżer zasobów skojarzył z harmonogramem. Harmonogram powinien używać tego interfejsu do komunikowania się z Menedżerem zasobów od tego momentu.

### <a name="remarks"></a>Uwagi

Ta metoda służy do inicjowania komunikacji z Menedżerem zasobów. Metoda kojarzy `IScheduler` interfejs dla harmonogramu `ISchedulerProxy` z interfejsem i przekazuje go z powrotem do Ciebie. Za pomocą zwróconego interfejsu można zażądać zasobów wykonania do użycia przez harmonogram lub subskrybować wątki za pomocą Menedżera zasobów. Menedżer zasobów użyje elementów zasad z zasad [harmonogramu zwróconych przez metodę IScheduler::GetPolicy,](ischeduler-structure.md#getpolicy) aby określić, jakiego typu wątki harmonogram będzie musiał wykonać pracę. Jeśli `SchedulerKind` klucz zasad ma `UmsThreadDefault` wartość, a wartość jest odczytywana `UmsThreadDefault`z `IScheduler` zasad jako wartość, `IUMSScheduler` interfejs przekazany do metody musi być interfejsem.

Metoda zgłasza `invalid_argument` wyjątek, jeśli `pScheduler` parametr `NULL` ma wartość `version` lub jeśli parametr nie jest prawidłową wersją interfejsu komunikacyjnego.

## <a name="iresourcemanagerrelease-method"></a><a name="release"></a>IResourceManager::Release Metoda

Zmniejsza liczbę odwołań w wystąpieniu Menedżera zasobów. Menedżer zasobów jest niszczony, gdy `0`jego liczba odwołań przechodzi do .

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Wynikowe liczby odwołań.

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)<br/>
[ISchedulerProxy, struktura](ischedulerproxy-structure.md)<br/>
[IScheduler, struktura](ischeduler-structure.md)
