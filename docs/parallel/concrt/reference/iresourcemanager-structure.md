---
title: Iresourcemanager — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d1032b2db7d1552beb40eb724b9953142b9b2ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027417"
---
# <a name="iresourcemanager-structure"></a>IResourceManager — Struktura
Interfejs do Menedżera zasobów Runtime współbieżności. Jest to interfejs, za pomocą którego lotów komunikować się z usługą Resource Manager.  
  
## <a name="syntax"></a>Składnia  
  
```
struct IResourceManager;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-enumerations"></a>Wyliczenia publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Iresourcemanager::OSVersion —](#osversion)|Typ wyliczany reprezentujący wersję systemu operacyjnego.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Iresourcemanager::createnodetopology —](#createnodetopology)|Obecnie tylko podczas debugowania kompilacji środowiska uruchomieniowego, ta metoda jest hook testu, zaprojektowany w celu ułatwienia badania Menedżera zasobów na różnych topologii sprzętu, bez konieczności rzeczywistego sprzętu zgodnego konfiguracji sprzętu. Za pomocą kompilacji detalicznej środowiska uruchomieniowego ta metoda zwróci bez wykonywania żadnych czynności.|  
|[IResourceManager::GetAvailableNodeCount](#getavailablenodecount)|Zwraca liczbę węzłów, które są dostępne do usługi Resource Manager.|  
|[IResourceManager::GetFirstNode](#getfirstnode)|Zwraca pierwszy węzeł w kolejności wyliczenia, zgodnie z definicją przez Menedżera zasobów.|  
|[Iresourcemanager::Reference —](#reference)|Zwiększa liczbę odwołań w wystąpieniu usługi Resource Manager.|  
|[IResourceManager::RegisterScheduler](#registerscheduler)|Rejestruje harmonogramu przy użyciu usługi Resource Manager. Po zarejestrowaniu harmonogram powinien komunikować się przy użyciu usługi Resource Manager `ISchedulerProxy` interfejsu, który jest zwracany.|  
|[Iresourcemanager::Release —](#release)|Dekrementuje liczbę odwołań w wystąpieniu usługi Resource Manager. Menedżer zasobów jest niszczony, kiedy jego licznik odwołań zbliża się do `0`.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj [createresourcemanager —](concurrency-namespace-functions.md) funkcji można uzyskać interfejsu na pojedyncze wystąpienie usługi Resource Manager. Metoda zwiększa licznik odwołań w Menedżerze zasobów i należy wywołać [IResourceManager::Release](#release) metodę, aby zwolnić odwołania, gdy są wykonywane przy użyciu usługi Resource Manager. Zazwyczaj każdego harmonogramu, tworzonych wywołać tę metodę podczas tworzenia i zwolnij odwołanie do usługi Resource Manager, po jego zamknięciu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IResourceManager`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="createnodetopology"></a>  Iresourcemanager::createnodetopology — metoda  
 Obecnie tylko podczas debugowania kompilacji środowiska uruchomieniowego, ta metoda jest hook testu, zaprojektowany w celu ułatwienia badania Menedżera zasobów na różnych topologii sprzętu, bez konieczności rzeczywistego sprzętu zgodnego konfiguracji sprzętu. Za pomocą kompilacji detalicznej środowiska uruchomieniowego ta metoda zwróci bez wykonywania żadnych czynności.  
  
```
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```  
  
### <a name="parameters"></a>Parametry  
*NodeCount*<br/>
Liczba węzłów procesora jest symulowane.  
  
*pCoreCount*<br/>
Tablica, która określa liczbę rdzeni w każdym węźle.  
  
*pNodeDistance*<br/>
Macierzy, określając węzła odległość między dwoma węzłami, wszystkie. Ten parametr może mieć wartość `NULL`.  
  
*pProcessorGroups*<br/>
Tablica, która określa grupę procesora należy każdego węzła.  
  
### <a name="remarks"></a>Uwagi  
 [invalid_argument](../../../standard-library/invalid-argument-class.md) jest generowany, jeśli parametr `nodeCount` ma wartość `0` został przekazany, lub jeśli parametr `pCoreCount` ma wartość `NULL`.  
  
 [invalid_operation](invalid-operation-class.md) jest generowany, jeśli ta metoda jest wywoływana, gdy inne transfery danych istnieje w procesie.  
  
##  <a name="getavailablenodecount"></a>  Iresourcemanager::getavailablenodecount — metoda  
 Zwraca liczbę węzłów, które są dostępne do usługi Resource Manager.  
  
```
virtual unsigned int GetAvailableNodeCount() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba węzłów jest dostępny dla Menedżera zasobów.  
  
##  <a name="getfirstnode"></a>  Iresourcemanager::getfirstnode — metoda  
 Zwraca pierwszy węzeł w kolejności wyliczenia, zgodnie z definicją przez Menedżera zasobów.  
  
```
virtual ITopologyNode* GetFirstNode() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszego węzła w kolejności wyliczenia, zgodnie z definicją przez Menedżera zasobów.  
  
##  <a name="iresourcemanager__osversion"></a>  Iresourcemanager::OSVersion — wyliczenie  
 Typ wyliczany reprezentujący wersję systemu operacyjnego.  
  
```
enum OSVersion;
```  
  
##  <a name="reference"></a>  Iresourcemanager::Reference — metoda  
 Zwiększa liczbę odwołań w wystąpieniu usługi Resource Manager.  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynikowa liczba odwołań.  
  
##  <a name="registerscheduler"></a>  Iresourcemanager::registerscheduler — metoda  
 Rejestruje harmonogramu przy użyciu usługi Resource Manager. Po zarejestrowaniu harmonogram powinien komunikować się przy użyciu usługi Resource Manager `ISchedulerProxy` interfejsu, który jest zwracany.  
  
```
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```  
  
### <a name="parameters"></a>Parametry  
*pScheduler*<br/>
`IScheduler` Interfejs harmonogram, który ma zostać zarejestrowany.  
  
*Wersja*<br/>
Wersja interfejsu komunikacji harmonogram używa do komunikowania się z usługą Resource Manager. Przy użyciu wersji umożliwia rozwój interfejsu komunikacji, zapewniając transfery danych w celu uzyskania dostępu do starszych funkcji Menedżera zasobów. Transfery danych, które chcą korzystać z funkcji usługi Resource Manager w programie Visual Studio 2010 należy użyć wersji `CONCRT_RM_VERSION_1`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `ISchedulerProxy` Interfejsu Menedżera zasobów jest skojarzona z harmonogramu. Harmonogramu, należy używać tego interfejsu, komunikować się z usługą Resource Manager z tego punktu.  
  
### <a name="remarks"></a>Uwagi  
 Metoda ta jest przydatna w celu zainicjowania komunikacji z usługą Resource Manager. Metoda kojarzy `IScheduler` interfejs dla harmonogramu za pomocą `ISchedulerProxy` interfejsu i ręce je z powrotem do Ciebie. Zwrócony interfejs można użyć, aby zażądać wykonania zasobów do użycia przez harmonogramu lub do subskrybowania wątków przy użyciu usługi Resource Manager. Resource Manager będzie używać elementów zasad z zasad harmonogramu zwrócony przez [ischeduler::getpolicy —](ischeduler-structure.md#getpolicy) metodę pozwala ustalić, jaki typ wątki harmonogram będzie konieczne wykonanie pracy. Jeśli Twoje `SchedulerKind` klucz zasad ma wartość `UmsThreadDefault` i wartość jest do odczytu z zasad z wartością `UmsThreadDefault`, `IScheduler` przekazywany do metody interfejsu muszą być `IUMSScheduler` interfejsu.  
  
 Metoda zgłasza `invalid_argument` wyjątek Jeśli parametr `pScheduler` ma wartość `NULL` lub, jeśli parametr `version` nie jest prawidłową wersją interfejsu komunikacji.  
  
##  <a name="release"></a>  Iresourcemanager::Release — metoda  
 Dekrementuje liczbę odwołań w wystąpieniu usługi Resource Manager. Menedżer zasobów jest niszczony, kiedy jego licznik odwołań zbliża się do `0`.  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynikowa liczba odwołań.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Ischedulerproxy — struktura](ischedulerproxy-structure.md)   
 [IScheduler, struktura](ischeduler-structure.md)
