---
title: stałe przestrzeń nazw współbieżności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- concrt/concurrency::AgentEventGuid
- concrt/concurrency::COOPERATIVE_TIMEOUT_INFINITE
- concrt/concurrency::COOPERATIVE_WAIT_TIMEOUT
- concrt/concurrency::ConcRTEventGuid
- concrt/concurrency::ConcRT_ProviderGuid
- concrt/concurrency::INHERIT_THREAD_PRIORITY
- concrt/concurrency::LockEventGuid
- concrt/concurrency::PPLParallelForEventGuid
- concrt/concurrency::PPLParallelForeachEventGuid
- concrt/concurrency::ResourceManagerEventGuid
- concrt/concurrency::ScheduleGroupEventGuid
- concrt/concurrency::VirtualProcessorEventGuid
dev_langs:
- C++
ms.assetid: 6f81fc4c-b10c-479e-8717-9c292360d5a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3fe1d8fdd1d77751f5663b7b70eeb6fdc65e572
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="concurrency-namespace-constants"></a>stałe przestrzeń nazw współbieżności
||||  
|-|-|-|  
|[Agenteventguid —](#agenteventguid)|[CONCRT_RM_VERSION_1](#concrt_rm_version_1)|[COOPERATIVE_TIMEOUT_INFINITE —](#cooperative_timeout_infinite)|  
|[COOPERATIVE_WAIT_TIMEOUT](#cooperative_wait_timeout)|[Choreeventguid —](#choreeventguid)|[ConcRTEventGuid](#concrteventguid)|  
|[ConcRT_ProviderGuid](#concrt_providerguid)|[Contexteventguid —](#contexteventguid)|[INHERIT_THREAD_PRIORITY](#inherit_thread_priority)|  
|[Lockeventguid —](#lockeventguid)|[MaxExecutionResources](#maxexecutionresources)|[PPLParallelForEventGuid](#pplparallelforeventguid)|  
|[PPLParallelForeachEventGuid](#pplparallelforeacheventguid)|[PPLParallelInvokeEventGuid](#pplparallelinvokeeventguid)|[ResourceManagerEventGuid](#resourcemanagereventguid)|  
|[ScheduleGroupEventGuid](#schedulegroupeventguid)|[SchedulerEventGuid](#schedulereventguid)|[VirtualProcessorEventGuid](#virtualprocessoreventguid)|  
  
##  <a name="agenteventguid"></a>  Agenteventguid —  
 Kategoria zdarzenia ETW opisujący wywoływane przez biblioteki agentów współbieżność środowiska wykonawczego identyfikatora GUID ({B9B5B78C-0713-4898-A21A-C67949DCED07}).  
  
```
const __declspec(selectany) GUID AgentEventGuid = {0xb9b5b78c, 0x713, 0x4898, { 0xa2, 0x1a, 0xc6, 0x79, 0x49, 0xdc, 0xed, 0x7 } };
```  
  
##  <a name="choreeventguid"></a>  Choreeventguid —  
 Kategoria GUID opisujące zdarzenia ETW wywoływane przez współbieżność środowiska wykonawczego, które są bezpośrednio związane z zadań i zadań.  
  
```
const __declspec(selectany) GUID ChoreEventGuid = 
    { 0x7E854EC7, 0xCDC4, 0x405a, { 0xB5, 0xB2, 0xAA, 0xF7, 0xC9, 0xE7, 0xD4, 0x0C } };
```  
  
### <a name="remarks"></a>Uwagi  
 Ta kategoria zdarzenia nie jest obecnie uruchamiany przez współbieżności środowiska wykonawczego.  
  
##  <a name="concrt_providerguid"></a>  Concrt_providerguid —  
 Dostawca ETW identyfikatora GUID dla współbieżności środowiska wykonawczego.  
  
```
const __declspec(selectany) GUID ConcRT_ProviderGuid = 
    { 0xF7B697A3, 0x4DB5, 0x4d3b, { 0xBE, 0x71, 0xC4, 0xD2, 0x84, 0xE6, 0x59, 0x2F } };
```  
  
##  <a name="concrt_rm_version_1"></a>  CONCRT_RM_VERSION_1 —  
 Wskazuje obsługi interfejsu Menedżera zasobów zdefiniowane w programie Visual Studio 2010.  
  
```
const unsigned int CONCRT_RM_VERSION_1 = 0x00010000;
```  
  
##  <a name="concrteventguid"></a>  Concrteventguid —  
 Kategorię GUID opisujące zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które nie zostały opisane bardziej szczegółowo w innej kategorii.  
  
```
const __declspec(selectany) GUID ConcRTEventGuid = 
    { 0x72B14A7D, 0x704C, 0x423e, { 0x92, 0xF8, 0x7E, 0x6D, 0x64, 0xBC, 0xB9, 0x2A } };
```  
  
### <a name="remarks"></a>Uwagi  
 Ta kategoria zdarzenia nie jest obecnie uruchamiany przez współbieżności środowiska wykonawczego.  
  
##  <a name="cooperative_timeout_infinite"></a>  COOPERATIVE_TIMEOUT_INFINITE —  
 Wartość wskazująca, której oczekiwania nigdy nie ma limitu czasu.  
  
```
const unsigned int COOPERATIVE_TIMEOUT_INFINITE = (unsigned int)-1;
```  
  
##  <a name="cooperative_wait_timeout"></a>  COOPERATIVE_WAIT_TIMEOUT —  
 Wartość wskazująca, że oczekiwania upłynął limit czasu.  
  
```
const size_t COOPERATIVE_WAIT_TIMEOUT = SIZE_MAX;
```  
  
##  <a name="contexteventguid"></a>  Contexteventguid —  
 Kategorię GUID opisujące zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z kontekstami.  
  
```
const __declspec(selectany) GUID ContextEventGuid = 
    { 0x5727A00F, 0x50BE, 0x4519, { 0x82, 0x56, 0xF7, 0x69, 0x98, 0x71, 0xFE, 0xCB } };
```  
  
##  <a name="inherit_thread_priority"></a>  INHERIT_THREAD_PRIORITY —  
 Specjalna wartość dla klucza zasad `ContextPriority` wskazującą, czy priorytet wątku wszystkie konteksty w harmonogramie powinna być taka sama jak w wątku, w której został utworzony harmonogram.  
  
```
const unsigned int INHERIT_THREAD_PRIORITY = 0x0000F000;
```  
  
##  <a name="lockeventguid"></a>  Lockeventguid —  
 Kategoria GUID opisujące zdarzenia ETW wywoływane przez współbieżność środowiska wykonawczego, które są bezpośrednio związane z blokad.  
  
```
const __declspec(selectany) GUID LockEventGuid = 
    { 0x79A60DC6, 0x5FC8, 0x4952, { 0xA4, 0x1C, 0x11, 0x63, 0xAE, 0xEC, 0x5E, 0xB8 } };
```  
  
### <a name="remarks"></a>Uwagi  
 Ta kategoria zdarzenia nie jest obecnie uruchamiany przez współbieżności środowiska wykonawczego.  
  
##  <a name="maxexecutionresources"></a>  Maxexecutionresources —  
 Specjalna wartość kluczy zasad `MinConcurrency` i `MaxConcurrency`. Wartość domyślna to liczba wątków sprzętu na komputerze w przypadku braku inne ograniczenia.  
  
```
const unsigned int MaxExecutionResources = 0xFFFFFFFF;
```  
  
##  <a name="pplparallelforeventguid"></a>  Pplparallelforeventguid —  
 Kategorię GUID opisujące zdarzenia ETW wywoływane przez współbieżność środowiska wykonawczego, które są bezpośrednio związane z użycie `parallel_for` funkcji.  
  
```
const __declspec(selectany) GUID PPLParallelForEventGuid = 
    { 0x31c8da6b, 0x6165, 0x4042, { 0x8b, 0x92, 0x94, 0x9e, 0x31, 0x5f, 0x4d, 0x84 } };
```  
  
##  <a name="pplparallelforeacheventguid"></a>  Pplparallelforeacheventguid —  
 Kategorię GUID opisujące zdarzenia ETW wywoływane przez współbieżność środowiska wykonawczego, które są bezpośrednio związane z użycie `parallel_for_each` funkcji.  
  
```
const __declspec(selectany) GUID PPLParallelForeachEventGuid = 
    { 0x5cb7d785, 0x9d66, 0x465d, { 0xba, 0xe1, 0x46, 0x11, 0x6, 0x1b, 0x54, 0x34 } };
```  
  
##  <a name="pplparallelinvokeeventguid"></a>  Pplparallelinvokeeventguid —  
 Kategorię GUID opisujące zdarzenia ETW wywoływane przez współbieżność środowiska wykonawczego, które są bezpośrednio związane z użycie `parallel_invoke` funkcji.  
  
```
const __declspec(selectany) GUID PPLParallelInvokeEventGuid = 
    { 0xd1b5b133, 0xec3d, 0x49f4, { 0x98, 0xa3, 0x46, 0x4d, 0x1a, 0x9e, 0x46, 0x82 } };
```  
  
##  <a name="resourcemanagereventguid"></a>  Resourcemanagereventguid —  
 Kategorię GUID opisujące zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z Menedżera zasobów.  
  
```
const __declspec(selectany) GUID ResourceManagerEventGuid = 
    { 0x2718D25B, 0x5BF5, 0x4479, { 0x8E, 0x88, 0xBA, 0xBC, 0x64, 0xBD, 0xBF, 0xCA } };
```  
  
### <a name="remarks"></a>Uwagi  
 Ta kategoria zdarzenia nie jest obecnie uruchamiany przez współbieżności środowiska wykonawczego.  
  
##  <a name="schedulegroupeventguid"></a>  ScheduleGroupEventGuid  
 Kategorię GUID opisujące zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z grupy harmonogramu.  
  
```
const __declspec(selectany) GUID ScheduleGroupEventGuid = 
    { 0xE8A3BF1F, 0xA86B, 0x4390, { 0x9C, 0x60, 0x53, 0x90, 0xB9, 0x69, 0xD2, 0x2C } };
```  
  
### <a name="remarks"></a>Uwagi  
 Ta kategoria zdarzenia nie jest obecnie uruchamiany przez współbieżności środowiska wykonawczego.  
  
##  <a name="schedulereventguid"></a>  Schedulereventguid —  
 Kategoria GUID opisujące zdarzenia ETW wywoływane przez współbieżność środowiska wykonawczego, które są bezpośrednio związane z działania harmonogramu.  
  
```
const __declspec(selectany) GUID SchedulerEventGuid = 
    { 0xE2091F8A, 0x1E0A, 0x4731, { 0x84, 0xA2, 0x0D, 0xD5, 0x7C, 0x8A, 0x52, 0x61 } };
```  
  
##  <a name="virtualprocessoreventguid"></a>  Virtualprocessoreventguid —  
 Kategoria GUID opisujące zdarzenia ETW wywoływane przez współbieżność środowiska wykonawczego, które są bezpośrednio związane z procesorów wirtualnych.  
  
```
const __declspec(selectany) GUID VirtualProcessorEventGuid = 
    { 0x2f27805f, 0x1676, 0x4ecc, { 0x96, 0xfa, 0x7e, 0xb0, 0x9d, 0x44, 0x30, 0x2f } };
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
