---
title: Biblioteki agentów asynchronicznych
ms.date: 11/04/2016
helpviewer_keywords:
- Agents Library
- Asynchronous Agents Library
ms.assetid: d2a72a31-8ba6-4220-ad7a-e403a6acaa42
ms.openlocfilehash: 9086734b22523d395022299fb75b7a130a8e7a16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629284"
---
# <a name="asynchronous-agents-library"></a>Biblioteki agentów asynchronicznych

Bibliotekę asynchronicznych agentów (lub po prostu *biblioteki agentów*) zapewnia model programowania, który pozwala zwiększyć niezawodność rozwoju aplikacji z możliwością współbieżności. Biblioteka agentów jest najwyższym model programowania oparty na aktora i komunikatów w trakcie przekazywania dla gruboziarnistych przepływu danych i ich przetwarzanie potokowe zadań Biblioteka szablonów języka C++. Biblioteka agentów opiera się na planowanie i składniki zarządzania w czasie wykonywania współbieżności.

## <a name="programming-model"></a>Model programowania

Biblioteka agentów zawiera alternatywy dla udostępnionego stanu, umożliwiając łączenie izolowane składniki za pomocą modelu komunikacji asynchronicznej, oparty na przepływ danych zamiast przepływu sterowania. *Przepływ danych* odwołuje się do programowania modelu, w których są wykonane obliczeń, gdy wszystkie wymagane dane są dostępne; *przepływ sterowania* odwołuje się do modelu programowania, gdzie obliczenia są wykonywane w określonej kolejności.

Model programowania przepływu danych jest powiązany z koncepcji *przekazywania komunikatów*, gdzie niezależnie od składników programu komunikować się ze sobą, wysyłając komunikaty.

Biblioteka agentów składa się z trzech składników: *agentów asynchronicznych*, *bloki komunikatów asynchronicznych*, i *funkcje przekazywania komunikatów*. Agenci zarządzania stanem i bloki komunikatów i funkcje przekazywania komunikatów mogą komunikować się ze sobą i przy użyciu składników zewnętrznych. Funkcje przekazywania komunikatów umożliwiają agentów, aby wysyłać i odbierać komunikaty z zewnętrznej składników. Bloki komunikatów asynchronicznych przechowywania komunikatów i włączyć agentów do komunikowania się w sposób zsynchronizowane.

Na poniższej ilustracji przedstawiono jak dwóch agentów bloki komunikatów użycia i funkcje przekazywania komunikatów do komunikowania się. Na tej ilustracji `agent1` wysyła komunikat `agent2` przy użyciu [concurrency::send](reference/concurrency-namespace-functions.md#send) funkcji i [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) obiektu. `agent2` używa [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkcję, aby odczytać wiadomość. `agent2` wykorzystuje tę samą metodę można wysłać wiadomości do `agent1`. Kreskowane strzałki przedstawiają przepływ danych między agentami. Stałe strzałki nawiązać bloki komunikatów, które one zapisu lub odczytu z agentów.

![Składniki biblioteki agentów](../../parallel/concrt/media/agent_librarycomp.png "agent_librarycomp")

Przykładowy kod, który implementuje na tej ilustracji przedstawiono w dalszej części tego tematu.

Model programowania agent ma kilka zalet za pośrednictwem innych mechanizmów współbieżność i synchronizacji, na przykład zdarzenia. Jedną z zalet to, czy przy użyciu przekazywania komunikatów do przesłania zmian stanu między obiektami, możesz odizolować dostęp do zasobów udostępnionych i tym samym poprawienia skalowalności. Zaletą przekazywania komunikatów jest wiąże synchronizacji danych zamiast wiązanie go do obiektu zewnętrznego synchronizacji. To ułatwia przesyłanie danych między składnikami i wyeliminować błędy programowania w swoich aplikacjach.

## <a name="when-to-use-the-agents-library"></a>Kiedy należy używać biblioteki agentów

Jeśli masz wiele operacji, które muszą asynchronicznie komunikować się ze sobą, należy używać biblioteki agentów. Bloki komunikatów i funkcje przekazywania komunikatów pozwalają tworzyć aplikacje równoległe bez konieczności mechanizmy synchronizacji, takie jak blokad. Dzięki temu deweloper może skupić się na logice aplikacji.

Model programowania agenta jest często używany do tworzenia *potoków danych* lub *sieci*. Potok danych jest szeregu składników, z których każdy wykonuje określone zadanie, które przyczynia się do ogólnego celu. Każdy składnik w potoku przepływu danych wykonuje pracę, gdy odbiera wiadomości z innego składnika. Wynikiem tej pracy jest przekazywany do innych składników w potoku lub sieci. Składniki funkcji można używać więcej szczegółowych współbieżności z innych bibliotek, na przykład, [biblioteki wzorców równoległych (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

## <a name="example"></a>Przykład

Poniższy przykład implementuje ilustracji przedstawione wcześniej w tym temacie.

[!code-cpp[concrt-basic-agents#1](../../parallel/concrt/codesnippet/cpp/asynchronous-agents-library_1.cpp)]

Ten przykład generuje następujące wyniki:

```Output
agent1: sending request...
agent2: received 'request'.
agent2: sending response...
agent1: received '42'.
```

W poniższych tematach opisano funkcje używane w tym przykładzie.

## <a name="related-topics"></a>Tematy pokrewne

[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)<br/>
W tym artykule opisano rolę agentów asynchronicznych w rozwiązaniu bardziej złożone zadania obliczeniowe.

[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
Zawiera opis różnych typów bloku komunikatu, które są dostarczane przez biblioteki agentów.

[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br/>
W tym artykule opisano różne procedur przekazywanie wiadomości, które są dostarczane przez biblioteki agentów.

[Instrukcje: implementowanie różnych wzorców producent — konsument](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br/>
Opisuje sposób implementacji wzorca producent — konsument w aplikacji.

[Instrukcje: zapewnianie funkcji pracy dla wywoływania oraz klasy transformatora](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br/>
Pokazano kilka sposobów zapewnianie funkcji pracy do [concurrency::call](../../parallel/concrt/reference/call-class.md) i [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) klasy.

[Instrukcje: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
Ilustruje sposób używania [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) klasy w potoku danych.

[Instrukcje: wybieranie spośród zadań wykonanych](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br/>
Ilustruje sposób używania [concurrency::choice](../../parallel/concrt/reference/choice-class.md) i [concurrency::join](../../parallel/concrt/reference/join-class.md) klasy zaznacz pierwsze zadanie do wykonania algorytmu wyszukiwania.

[Instrukcje: wysyłanie komunikatu w regularnych odstępach czasu](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br/>
Ilustruje sposób używania [concurrency::timer](../../parallel/concrt/reference/timer-class.md) klasy do wysyłania komunikatu w regularnych odstępach czasu.

[Instrukcje: korzystanie z filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)<br/>
Pokazuje, jak włączyć blokiem komunikatów asynchronicznych o zaakceptowanie lub odrzucenie wiadomości za pomocą filtru.

[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Opisuje sposób używania różnych równoległych wzorców, takich jak algorytmy równoległe w swoich aplikacjach.

[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)<br/>
W tym artykule opisano środowisko uruchomieniowe współbieżności, upraszczający Programowanie równoległe i zawiera linki do powiązanych tematów.

