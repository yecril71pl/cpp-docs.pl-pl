---
title: Równoległe narzędzia diagnostyczne (współbieżność środowiska wykonawczego)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
ms.openlocfilehash: 34b2421dfc53deeb35dcc659a8d555983e583737
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510498"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>Równoległe narzędzia diagnostyczne (współbieżność środowiska wykonawczego)

Program Visual Studio zapewnia szeroką obsługę debugowania i profilowania aplikacji wielowątkowych.

## <a name="debugging"></a>Debugowanie

Debuger programu Visual Studio zawiera okno **stosów równoległych** , okno **zadań równoległych** i okno **czujki równoległej** . Aby uzyskać więcej informacji, [zobacz Przewodnik: Debugowanie aplikacji](/visualstudio/debugger/walkthrough-debugging-a-parallel-application) równoległej i [instrukcje: Użyj okna](/visualstudio/debugger/how-to-use-the-parallel-watch-window)czujki równoległej.

## <a name="profiling"></a>Profilowanie

Narzędzia profilowania oferują trzy widoki danych, które wyświetlają graficzne, tabelaryczne i liczbowe informacje o sposobie interakcji aplikacji wielowątkowej z innymi programami. Widoki umożliwiają szybkie identyfikowanie obszarów zainteresowania oraz nawigowanie po punktach na graficznej wyświetlaczach, które umożliwiają wywoływanie stosów, wywoływanie witryn i kodu źródłowego. Aby uzyskać więcej informacji, zobacz [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).

## <a name="event-tracing"></a>Śledzenie zdarzeń

Środowisko uruchomieniowe współbieżności używa [śledzenia zdarzeń systemu Windows](/windows/win32/ETW/event-tracing-portal) (ETW) do powiadamiania narzędzi instrumentacji, takich jak program do obsługi plików, gdy wystąpią różne zdarzenia. Te zdarzenia obejmują czas aktywowania lub dezaktywowania harmonogramu, gdy kontekst rozpoczyna się, zatrzymuje, blokuje, odblokowuje lub daje, a kiedy algorytm równoległy zaczyna się lub skończy.

Narzędzia takie jak narzędzie [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer) wykorzystują tę funkcję; w związku z tym zazwyczaj nie trzeba bezpośrednio korzystać z tych zdarzeń. Jednak te zdarzenia są przydatne podczas tworzenia niestandardowego profilera lub korzystania z narzędzi śledzenia zdarzeń, takich jak [Xperf](https://go.microsoft.com/fwlink/p/?linkid=160628).

Środowisko uruchomieniowe współbieżności generuje te zdarzenia tylko wtedy, gdy śledzenie jest włączone. Wywołaj funkcję [concurrency:: EnableTracing —](reference/concurrency-namespace-functions.md#enabletracing) , aby włączyć śledzenie zdarzeń i funkcję [concurrency::D isabletracing](reference/concurrency-namespace-functions.md#disabletracing) w celu wyłączenia śledzenia.

W poniższej tabeli opisano zdarzenia, które wywołuje środowisko uruchomieniowe, gdy włączone jest śledzenie zdarzeń:

|Zdarzenie|Opis|Wartość|
|-----------|-----------------|-----------|
|[concurrency:: ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)|Identyfikator dostawcy ETW dla środowisko uruchomieniowe współbieżności.|`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|
|[concurrency:: ContextEventGuid —](reference/concurrency-namespace-constants1.md#contexteventguid)|Oznacza zdarzenia dotyczące kontekstów.|`5727a00f-50be-4519-8256-f7699871fecb`|
|[współbieżność::P PLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)|Oznacza wejście i wyjście do wywołań algorytmu [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) .|`31c8da6b-6165-4042-8b92-949e315f4d84`|
|[współbieżność::P PLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)|Oznacza wejście i wyjście do wywołań algorytmu [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) .|`5cb7d785-9d66-465d-bae1-4611061b5434`|
|[współbieżność::P PLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|Oznacza wejście i wyjście do wywołań algorytmu [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) .|`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|
|[concurrency:: SchedulerEventGuid —](reference/concurrency-namespace-constants1.md#schedulereventguid)|Oznacza zdarzenia dotyczące [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).|`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|
|[concurrency:: VirtualProcessorEventGuid —](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)|Oznacza zdarzenia związane z procesorami wirtualnymi.|`2f27805f-1676-4ecc-96fa-7eb09d44302f`|

Środowisko uruchomieniowe współbieżności definiuje, ale obecnie nie wywołuje następujących zdarzeń. Środowisko uruchomieniowe rezerwuje te zdarzenia do użytku w przyszłości:

- [concurrency:: ConcRTEventGuid —](reference/concurrency-namespace-constants1.md#concrteventguid)

- [concurrency:: ScheduleGroupEventGuid —](reference/concurrency-namespace-constants1.md#schedulereventguid)

- [concurrency:: ChoreEventGuid —](reference/concurrency-namespace-constants1.md#choreeventguid)

- [concurrency:: LockEventGuid —](reference/concurrency-namespace-constants1.md#lockeventguid)

- [concurrency:: ResourceManagerEventGuid —](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)

Element [concurrency:: ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype) Enumeration określa możliwe operacje śledzone przez zdarzenie. Na przykład w momencie wejścia `parallel_for` algorytmu środowisko uruchomieniowe `PPLParallelForEventGuid` wywołuje zdarzenie i zapewnia `CONCRT_EVENT_START` jako operację. Przed zwróceniem `PPLParallelForEventGuid`algorytmuśrodowisko uruchomieniowe ponownie wywołuje zdarzenie i zapewnia `CONCRT_EVENT_END` jako operację. `parallel_for`

Poniższy przykład ilustruje, jak włączyć śledzenie dla wywołania `parallel_for`. Środowisko uruchomieniowe nie śledzi pierwszego wywołania do `parallel_for` , ponieważ śledzenie nie jest włączone. Wywołanie `EnableTracing` umożliwiające środowisko uruchomieniowe śledzenia drugiego wywołania do `parallel_for`.

[!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]

Środowisko uruchomieniowe śledzi liczbę wywołań `EnableTracing` i. `DisableTracing` W związku z tym, `EnableTracing` Jeśli wywołasz wiele razy, `DisableTracing` należy wywołać tę samą liczbę razy, aby wyłączyć śledzenie.

## <a name="see-also"></a>Zobacz także

[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)
