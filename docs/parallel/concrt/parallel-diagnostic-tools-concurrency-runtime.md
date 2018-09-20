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
ms.openlocfilehash: db0666d3623dbd2e341b6a27c01d78ef22c6cc6b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446059"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>Równoległe narzędzia diagnostyczne (współbieżność środowiska wykonawczego)

Program Visual Studio zapewnia rozbudowaną obsługę debugowania i profilowania aplikacji wielowątkowych.

## <a name="debugging"></a>Debugowanie

Debuger programu Visual Studio zawiera **stosów równoległych** oknie **zadań równoległych** oknie i **równoległego wyrażenia kontrolnego** okna. Aby uzyskać więcej informacji, zobacz [wskazówki: debugowanie aplikacji równoległych](/visualstudio/debugger/walkthrough-debugging-a-parallel-application) i [porady: Użyj okna czujki równoległej](/visualstudio/debugger/how-to-use-the-parallel-watch-window).

## <a name="profiling"></a>Profilowanie

Narzędzia profilowania zapewniają trzy widoki danych, które wyświetlają graficzne, tabelaryczne i numeryczne informacji na temat współdziałania aplikacji wielowątkowych z samym sobą oraz z innymi programami. Widoki umożliwiają szybko zidentyfikować obszary zainteresowania i można przejść z punktów na graficzny Wyświetla wywołać stosów wywołań witryny i kod źródłowy. Aby uzyskać więcej informacji, zobacz [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).

## <a name="event-tracing"></a>Śledzenie zdarzeń

Środowisko uruchomieniowe współbieżności używa [Event Tracing for Windows](/windows/desktop/ETW/event-tracing-portal) (ETW), aby powiadomić narzędzia instrumentacji, takie jak profilerów, po wystąpieniu różnych zdarzeń. Te zdarzenia obejmują podczas harmonogramu jest aktywowane lub dezaktywowane, kontekst zaczyna się, kończy się, blokuje, odblokowuje lub daje i gdy algorytmu równoległego, rozpoczyna się lub kończy.

Narzędzia takie jak [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer) korzystanie z tej funkcji; w związku z tym, zwykle nie trzeba pracować z tych zdarzeń bezpośrednio. Jednak te zdarzenia są przydatne, gdy tworzysz niestandardowy program profilujący lub jeśli używasz narzędzia śledzenia zdarzeń takich jak [Xperf](http://go.microsoft.com/fwlink/p/?linkid=160628).

Środowisko uruchomieniowe współbieżności wywołuje te zdarzenia, tylko wtedy, gdy śledzenie jest włączone. Wywołaj [concurrency::EnableTracing](reference/concurrency-namespace-functions.md#enabletracing) funkcję, aby włączyć śledzenie zdarzeń i [concurrency::DisableTracing](reference/concurrency-namespace-functions.md#disabletracing) funkcję, aby wyłączyć śledzenie.

W poniższej tabeli opisano zdarzenia, które środowisko uruchomieniowe zgłasza po włączeniu funkcji śledzenia zdarzeń:

|Zdarzenie|Opis|Wartość|
|-----------|-----------------|-----------|

|[CONCURRENCY::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)| Identyfikator dostawcy funkcji ETW w czasie wykonywania współbieżności. | `f7b697a3-4db5-4d3b-be71-c4d284e6592f`| | [concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)| Oznacza zdarzenia, które są powiązane z kontekstami. | `5727a00f-50be-4519-8256-f7699871fecb`| | [concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)| Oznacza wejścia i wyjścia do wywołania [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytmu. | `31c8da6b-6165-4042-8b92-949e315f4d84`| | [concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)| Oznacza wejścia i wyjścia do wywołania [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytmu. | `5cb7d785-9d66-465d-bae1-4611061b5434`| | [concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)| Oznacza wejścia i wyjścia do wywołania [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytmu. | `d1b5b133-ec3d-49f4-98a3-464d1a9e4682`| | [concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)| Oznacza zdarzenia, które są powiązane z [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md). | `e2091f8a-1e0a-4731-84a2-0dd57c8a5261`| | [concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)| Oznacza zdarzenia, które są powiązane z procesorami wirtualnymi. |`2f27805f-1676-4ecc-96fa-7eb09d44302f`|

Środowisko uruchomieniowe współbieżności definiuje, ale obecnie zgłaszaj, następujące zdarzenia. Środowisko uruchomieniowe rezerwuje te zdarzenia do użytku w przyszłości:

- [CONCURRENCY::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)

- [CONCURRENCY::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)

- [CONCURRENCY::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)

- [CONCURRENCY::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)

- [CONCURRENCY::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)

[Concurrency::ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype) wyliczenie określa możliwych operacji, które śledzi zdarzenia. Na przykład przy wejściu `parallel_for` algorytmu, środowisko uruchomieniowe zgłasza `PPLParallelForEventGuid` zdarzeń i zapewnia `CONCRT_EVENT_START` jako operacja. Przed `parallel_for` zwraca algorytm, środowisko uruchomieniowe ponownie zgłasza `PPLParallelForEventGuid` zdarzeń i zapewnia `CONCRT_EVENT_END` jako operacja.

W poniższym przykładzie pokazano sposób włączania śledzenia wywołania `parallel_for`. Środowisko wykonawcze nie śledzenia pierwsze wywołanie `parallel_for` ponieważ go nie włączono śledzenie. Wywołanie `EnableTracing` umożliwia śledzenie drugie wywołanie `parallel_for`.

[!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]

Środowisko uruchomieniowe śledzi, ile razy wywołasz `EnableTracing` i `DisableTracing`. W związku z tym jeśli wywołasz `EnableTracing` wielokrotnie, należy wywołać `DisableTracing` taką samą liczbę razy, aby można było wyłączyć śledzenie.

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)

