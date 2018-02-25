---
title: "Iresourcemanager — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d309e057a8f829b11cc97ad60f3f5d56ff7ecaff
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="iresourcemanager-structure"></a>IResourceManager — Struktura
Interfejs do współbieżności środowiska wykonawczego Resource Manager. Jest to interfejs, za pomocą którego komunikują się z Menedżerem zasobów transfery danych.  
  
## <a name="syntax"></a>Składnia  
  
```
struct IResourceManager;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-enumerations"></a>Wyliczenia publiczny  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Iresourcemanager::OSVersion —](#osversion)|Typ wyliczany reprezentujący wersję systemu operacyjnego.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IResourceManager::CreateNodeTopology](#createnodetopology)|Tworzy się tylko w przypadku debugowania środowiska uruchomieniowego, ta metoda jest haku testu, zaprojektowany w celu ułatwienia testowania Resource Manager na różne topologie sprzętu, bez konieczności sprzętem dopasowania konfiguracji. Z kompilacjami detalicznej środowiska uruchomieniowego ta metoda zwróci bez wykonywania żadnych czynności.|  
|[IResourceManager::GetAvailableNodeCount](#getavailablenodecount)|Zwraca liczbę węzłów, które są dostępne do Menedżera zasobów.|  
|[IResourceManager::GetFirstNode](#getfirstnode)|Zwraca pierwszy węzeł w kolejności wyliczenia zdefiniowanych przez Menedżera zasobów.|  
|[IResourceManager::Reference](#reference)|Zwiększa liczbę odwołania do wystąpienia menedżera zasobów.|  
|[IResourceManager::RegisterScheduler](#registerscheduler)|Rejestruje harmonogramu przy użyciu Menedżera zasobów. Po zarejestrowaniu planista powinien komunikacji przy użyciu usługi Resource Manager `ISchedulerProxy` interfejs, który jest zwracany.|  
|[IResourceManager::Release](#release)|Zmniejsza liczba odwołania do wystąpienia menedżera zasobów. Menedżer zasobów zostanie zniszczony podczas jego liczebności referencyjnej przechodzi do `0`.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj [createresourcemanager —](concurrency-namespace-functions.md) funkcji można uzyskać interfejsu do pojedyncze wystąpienie Menedżera zasobów. Metoda zwiększa liczbę odwołań w usłudze Resource Manager i powinna wywołać [IResourceManager::Release](#release) metodę, aby zwolnić odwołania, gdy wszystko będzie gotowe za pomocą Menedżera zasobów. Zazwyczaj każdego harmonogramu tworzonych wywołania tej metody podczas tworzenia i zwolnij odwołanie do Menedżera zasobów, po jego zamknięciu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IResourceManager`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="createnodetopology"></a>  IResourceManager::CreateNodeTopology — metoda  
 Tworzy się tylko w przypadku debugowania środowiska uruchomieniowego, ta metoda jest haku testu, zaprojektowany w celu ułatwienia testowania Resource Manager na różne topologie sprzętu, bez konieczności sprzętem dopasowania konfiguracji. Z kompilacjami detalicznej środowiska uruchomieniowego ta metoda zwróci bez wykonywania żadnych czynności.  
  
```
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `nodeCount`  
 Liczba węzłów procesora jest symulowane.  
  
 `pCoreCount`  
 Tablica, która określa liczbę rdzeni na każdym węźle.  
  
 `pNodeDistance`  
 Macierz, określając węzła odległość między dwa węzły. Ten parametr może mieć wartość `NULL`.  
  
 `pProcessorGroups`  
 Tablica, która określa grupę procesora należy każdego węzła.  
  
### <a name="remarks"></a>Uwagi  
 [invalid_argument —](../../../standard-library/invalid-argument-class.md) jest generowany, jeśli parametr `nodeCount` ma wartość `0` został przekazany, lub, jeśli parametr `pCoreCount` ma wartość `NULL`.  
  
 [invalid_operation —](invalid-operation-class.md) jest generowany, jeśli ta metoda jest wywoływana, gdy istnieją inne transfery danych w procesie.  
  
##  <a name="getavailablenodecount"></a>  IResourceManager::GetAvailableNodeCount — metoda  
 Zwraca liczbę węzłów, które są dostępne do Menedżera zasobów.  
  
```
virtual unsigned int GetAvailableNodeCount() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba węzłów dostępny dla Menedżera zasobów.  
  
##  <a name="getfirstnode"></a>  IResourceManager::GetFirstNode — metoda  
 Zwraca pierwszy węzeł w kolejności wyliczenia zdefiniowanych przez Menedżera zasobów.  
  
```
virtual ITopologyNode* GetFirstNode() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy węzeł w kolejności wyliczenia zdefiniowanych przez Menedżera zasobów.  
  
##  <a name="iresourcemanager__osversion"></a>  Iresourcemanager::OSVersion — wyliczenie  
 Typ wyliczany reprezentujący wersję systemu operacyjnego.  
  
```
enum OSVersion;
```  
  
##  <a name="reference"></a>  IResourceManager::Reference — metoda  
 Zwiększa liczbę odwołania do wystąpienia menedżera zasobów.  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynikowa liczba odwołań.  
  
##  <a name="registerscheduler"></a>  IResourceManager::RegisterScheduler — metoda  
 Rejestruje harmonogramu przy użyciu Menedżera zasobów. Po zarejestrowaniu planista powinien komunikacji przy użyciu usługi Resource Manager `ISchedulerProxy` interfejs, który jest zwracany.  
  
```
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pScheduler`  
 `IScheduler` Interfejs do harmonogramu, który ma zostać zarejestrowany.  
  
 `version`  
 Wersja interfejsu komunikacji harmonogram używa do komunikowania się z Menedżerem zasobów. Przy użyciu wersji umożliwia podlegać ewolucji interfejs komunikacyjny, umożliwiając transfery danych w celu uzyskania dostępu do starszych funkcje Menedżera zasobów. Planiści, które chcą korzystać z funkcji Menedżera zasobów w programie Visual Studio 2010 należy używać wersji `CONCRT_RM_VERSION_1`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `ISchedulerProxy` Interfejsu Menedżera zasobów jest skojarzona z Twojego harmonogramu. Twoje harmonogramu należy używać tego interfejsu do komunikacji z usługą Resource Manager z tego punktu w.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia nawiązywanie komunikacji z Menedżerem zasobów. Metoda kojarzy `IScheduler` interfejs użytkownika harmonogramu z `ISchedulerProxy` interfejsu i go z powrotem do możesz ręce. Można użyć interfejsu zwrócone, aby zażądać wykonania zasobów do użycia przez użytkownika harmonogramu lub do subskrybowania wątków przy użyciu Menedżera zasobów. Resource Manager będzie używać elementów zasad z zasad harmonogramu zwrócony przez [IScheduler::GetPolicy](ischeduler-structure.md#getpolicy) metodę, aby określić typ wątków planista należy do wykonywania pracy. Jeśli Twoje `SchedulerKind` zasad klucz ma wartość `UmsThreadDefault` i wartość jest do odczytu wstecz poza zasad jako wartość `UmsThreadDefault`, `IScheduler` musi być przekazywany do metody interfejsu `IUMSScheduler` interfejsu.  
  
 Metoda zgłasza `invalid_argument` wyjątek Jeśli parametr `pScheduler` ma wartość `NULL` lub, jeśli parametr `version` nie jest prawidłową wersją interfejs komunikacyjny.  
  
##  <a name="release"></a>  IResourceManager::Release — metoda  
 Zmniejsza liczba odwołania do wystąpienia menedżera zasobów. Menedżer zasobów zostanie zniszczony podczas jego liczebności referencyjnej przechodzi do `0`.  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynikowa liczba odwołań.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [ISchedulerProxy Structure](ischedulerproxy-structure.md)   
 [IScheduler, struktura](ischeduler-structure.md)
