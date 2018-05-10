---
title: Równoległe narzędzia diagnostyczne (współbieżność środowiska wykonawczego) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cd3ce4c86332719e299c11fee3ffbee8b41c14f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>Równoległe narzędzia diagnostyczne (współbieżność środowiska wykonawczego)
[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] obsługuje szeroką gamę debugowanie i profilowania aplikacji wielowątkowych.  
  
## <a name="debugging"></a>Debugowanie  
 Debuger programu Visual Studio zawiera **stosów równoległych** okna, **zadań równoległych** okno i **czujki równoległej** okna. Aby uzyskać więcej informacji, zobacz [wskazówki: debugowanie aplikacji równoległych](/visualstudio/debugger/walkthrough-debugging-a-parallel-application) i [porady: Użyj okna czujki równoległej](/visualstudio/debugger/how-to-use-the-parallel-watch-window).  
  
## <a name="profiling"></a>Profilowanie  
 Narzędzia profilowania zapewniają trzy widoki danych, które wyświetlają graficzny, tabelarycznych i numeryczne informacji na temat współdziałania aplikacji wielowątkowych ze sobą oraz z innych programów. Widoki pozwalają na szybkie identyfikowanie obszarów zainteresowania i można przejść z punktów graficzny Wyświetla wywołać stosy, wywołaj witryny i kod źródłowy. Aby uzyskać więcej informacji, zobacz [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="event-tracing"></a>Śledzenie zdarzeń  
 Współbieżność środowiska wykonawczego używa [śledzenia zdarzeń dla systemu Windows](http://msdn.microsoft.com/library/windows/desktop/bb968803) (ETW), aby powiadomić narzędzia instrumentacji, takie jak profilowania, gdy występują różne zdarzenia. Zdarzenia te obejmują podczas harmonogramu jest aktywowany lub dezaktywowany, kontekst rozpoczyna, kończy się, blokuje, odblokowuje lub daje i podczas równoległego algorytm zaczyna się lub kończy się.  
  
 Narzędzi takich jak [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer) korzystać z tej funkcji; w związku z tym zazwyczaj nie trzeba pracować bezpośrednio z tych zdarzeń. Jednak te zdarzenia są przydatne, gdy tworzysz niestandardowy profilera lub jeśli używasz narzędzia Śledzenie zdarzeń takich jak [narzędzia Xperf](http://go.microsoft.com/fwlink/p/?linkid=160628).  
  
 Współbieżność środowiska wykonawczego informuje o tych zdarzeniach tylko wtedy, gdy śledzenie jest włączone. Wywołanie [concurrency::EnableTracing](reference/concurrency-namespace-functions.md#enabletracing) funkcji, aby włączyć śledzenie zdarzeń i [concurrency::DisableTracing](reference/concurrency-namespace-functions.md#disabletracing) funkcji, aby wyłączyć śledzenie.  
  
 W poniższej tabeli opisano zdarzenia, które wywołuje środowiska uruchomieniowego, gdy włączone jest śledzenie zdarzeń:  
  
|Zdarzenie|Opis|Wartość|  
|-----------|-----------------|-----------|  

|[CONCURRENCY::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)| Identyfikator dostawcy ETW współbieżności środowiska wykonawczego. |`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|  
|[CONCURRENCY::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)| Oznacza zdarzenia, które są związane z kontekstami. |`5727a00f-50be-4519-8256-f7699871fecb`|  
|[CONCURRENCY::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)| Oznacza wejścia i wyjścia do wywołania [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytmu. |`31c8da6b-6165-4042-8b92-949e315f4d84`|  
|[CONCURRENCY::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)| Oznacza wejścia i wyjścia do wywołania [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytmu. |`5cb7d785-9d66-465d-bae1-4611061b5434`|  
|[CONCURRENCY::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)| Oznacza wejścia i wyjścia do wywołania [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytmu. |`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|  
|[CONCURRENCY::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)| Oznacza zdarzenia, które są powiązane z [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md). |`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|  
|[CONCURRENCY::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)| Oznacza zdarzenia, które są powiązane z procesorów wirtualnych. |`2f27805f-1676-4ecc-96fa-7eb09d44302f`|  
  
 Współbieżność środowiska wykonawczego definiuje, ale nie obecnie zgłaszał, następujące zdarzenia. Środowisko uruchomieniowe rezerwuje te zdarzenia do użytku w przyszłości:  
  
-   [CONCURRENCY::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)  
  
-   [CONCURRENCY::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)  
  
-   [CONCURRENCY::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)  
  
-   [CONCURRENCY::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)  
  
-   [CONCURRENCY::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)  
  
 [Concurrency::ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype) wyliczenie określa możliwe operacje, które śledzi zdarzenia. Na przykład przy wejściu `parallel_for` zgłasza środowiska uruchomieniowego algorytmu, `PPLParallelForEventGuid` zdarzeń i zapewnia `CONCRT_EVENT_START` jako wykonać operację. Przed `parallel_for` zwraca algorytmu, środowisko uruchomieniowe ponownie zgłasza `PPLParallelForEventGuid` zdarzeń i zapewnia `CONCRT_EVENT_END` jako wykonać operację.  
  
 Poniższy przykład przedstawia sposób włączania śledzenia wywołania `parallel_for`. Środowisko uruchomieniowe nie śledzi w pierwszym wywołaniu `parallel_for` ponieważ go nie jest włączone śledzenie. Wywołanie `EnableTracing` środowisko uruchomieniowe śledzenia drugie wywołanie `parallel_for`.  
  
 [!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]  
  
 Środowisko uruchomieniowe śledzi liczbę razy, które należy wywołać `EnableTracing` i `DisableTracing`. W związku z tym jeśli wywołujesz `EnableTracing` wielokrotnie, należy wywołać `DisableTracing` taką samą liczbę razy, aby wyłączyć śledzenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)

