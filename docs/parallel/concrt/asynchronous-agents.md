---
title: Agenci asynchroniczni
ms.date: 11/19/2018
helpviewer_keywords:
- asynchronous agents
- agents [Concurrency Runtime]
ms.assetid: 6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a
ms.openlocfilehash: ff6fa851519066c3c399a28557fd8f103d0e94be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412817"
---
# <a name="asynchronous-agents"></a>Agenci asynchroniczni

*Agent asynchroniczny* (lub po prostu *agenta*) jest składnik aplikacji asynchronicznie współpracuje z innymi czynnikami, aby rozwiązać bardziej złożone zadania obliczeniowe. Agenta można traktować jako zadanie, które ma ustawiony cykl życia. Na przykład jednego agenta może odczytać danych z urządzenia z systemem wejścia/wyjścia (np. klawiatura, plik na dysku lub połączenia sieciowego) i innego agenta może wykonywać działania na tych danych, po jej udostępnieniu. Pierwszy agent używa przekazywania komunikatów drugi agent poinformować, że dostępnych jest więcej danych. Harmonogram zadań w środowisku uruchomieniowym współbieżności: zapewnia wydajny mechanizm, aby włączyć agentów zablokować i uzyskanie wspólne bez konieczności wywłaszczania mniej wydajne rozwiązanie.

Biblioteka agentów definiuje [concurrency::agent](../../parallel/concrt/reference/agent-class.md) klasy do reprezentowania agent asynchroniczny. `agent` jest klasą abstrakcyjną, która deklaruje metodę wirtualną [concurrency::agent::run](reference/agent-class.md#run). `run` Metoda wykonuje zadanie, które jest wykonywane przez agenta. Ponieważ `run` jest abstrakcyjny, musisz zaimplementować tę metodę w każdej klasy, która pochodzi z `agent`.

## <a name="agent-life-cycle"></a>Cykl życia agenta

Agenci mają ustawiony cykl życia. [Concurrency::agent_status](reference/concurrency-namespace-enums.md#agent_status) wyliczenie definiuje różne stany agenta. Na poniższej ilustracji jest diagram stanu, który pokazuje, jak agentów postępu z jednego stanu do drugiego. Na tej ilustracji linia ciągła reprezentowania metody, które można wywoływać z aplikacji; Wiersze dotted przedstawiają metody, które są wywoływane ze środowiska wykonawczego.

![Diagram stanu agenta](../../parallel/concrt/media/agentstate.png "Diagram stanu agenta")

W poniższej tabeli opisano każdy stan w `agent_status` wyliczenia.

|Stan agenta.|Opis|
|-----------------|-----------------|
|`agent_created`|Agent nie został zaplanowany do wykonania.|
|`agent_runnable`|Środowisko uruchomieniowe jest planowanie agenta do wykonania.|
|`agent_started`|Agent została uruchomiona i działa.|
|`agent_done`|Zakończono agenta.|
|`agent_canceled`|Agent została anulowana przed jej wprowadzeniem `started` stanu.|

`agent_created` jest wstępny stan agenta, `agent_runnable` i `agent_started` są aktywne stany i `agent_done` i `agent_canceled` są Stany terminala.

Użyj [concurrency::agent::status](reference/agent-class.md#status) metodę, która pobierze bieżący stan `agent` obiektu. Mimo że `status` metoda jest bezpieczna pod kątem współbieżności, stan agenta można zmienić do czasu `status` metoda zwraca. Przykładowo agent może być `agent_started` stanu po wywołaniu `status` metody, ale przeniesiony do `agent_done` stanu tuż za `status` metoda zwraca.

## <a name="methods-and-features"></a>Metody i funkcje

W poniższej tabeli przedstawiono niektóre ważne metody, które należą do `agent` klasy. Aby uzyskać więcej informacji na temat wszystkich `agent` metody klasy, zobacz [agent, klasa](../../parallel/concrt/reference/agent-class.md).

|Metoda|Opis|
|------------|-----------------|
|[start](reference/agent-class.md#start)|Harmonogramy `agent` obiektu do wykonania i ustawia ją na `agent_runnable` stanu.|
|[run](reference/agent-class.md#run)|Wykonuje zadanie, które ma być wykonywane przez `agent` obiektu.|
|[Gotowe](reference/agent-class.md#done)|Przenosi agenta pod kątem `agent_done` stanu.|
|[cancel](../../parallel/concrt/cancellation-in-the-ppl.md#cancel)|Jeśli agent nie został uruchomiony, ta metoda powoduje anulowanie wykonywania agenta i ustawia ją na `agent_canceled` stanu.|
|[status](reference/agent-class.md#status)|Pobiera bieżący stan `agent` obiektu.|
|[Czekaj](reference/agent-class.md#wait)|Czeka, aż `agent` obiektu, aby wprowadzić `agent_done` lub `agent_canceled` stanu.|
|[wait_for_all](reference/agent-class.md#wait_for_all)|Czeka, aż wszystkie podane `agent` obiektów, aby wprowadzić `agent_done` lub `agent_canceled` stanu.|
|[wait_for_one](reference/agent-class.md#wait_for_one)|Czeka na co najmniej jednego z dostarczonych `agent` obiektów, aby wprowadzić `agent_done` lub `agent_canceled` stanu.|

Po utworzeniu obiektu agenta należy wywołać [concurrency::agent::start](reference/agent-class.md#start) metodę, aby zaplanować jego wykonywania. Środowisko uruchomieniowe wywołuje `run` metoda po planuje agenta i ustawia ją na `agent_runnable` stanu.

Środowisko wykonawcze nie zarządza wyjątki wyrzucane przez agentów asynchronicznych. Aby uzyskać więcej informacji na temat obsługi wyjątków i agentów, zobacz [wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="example"></a>Przykład

Aby uzyskać przykład pokazujący sposób tworzenia podstawowych aplikacji opartej o agentów, zobacz [instruktażu: Tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md).

## <a name="see-also"></a>Zobacz także

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)
