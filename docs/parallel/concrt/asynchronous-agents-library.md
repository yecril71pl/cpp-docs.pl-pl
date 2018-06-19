---
title: Biblioteki agentów asynchronicznych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Agents Library
- Asynchronous Agents Library
ms.assetid: d2a72a31-8ba6-4220-ad7a-e403a6acaa42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8bb1ce7a0c449d5c09e49ad16435e7732ddfcc1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688999"
---
# <a name="asynchronous-agents-library"></a>Biblioteki agentów asynchronicznych
Biblioteki agentów asynchronicznych (lub po prostu *biblioteki agentów*) zapewnia model programowania, który pozwala zwiększyć niezawodność rozwoju aplikacji z obsługą współbieżności. Biblioteki agentów jest Biblioteka szablonów C++, która wspiera aktora na podstawie modelu programowania i komunikatów w trakcie przekazywanie dla coarse-grained przepływu danych i przetwarzanie potokowe zadania. Biblioteki agentów opiera się na planowanie i składniki zarządzania współbieżności środowiska wykonawczego.  
  
## <a name="programming-model"></a>Model programowania  
 Biblioteki agentów zawiera alternatyw do stanu udostępnionego, umożliwiając się izolowane składniki przy użyciu modelu komunikacji asynchronicznej, który jest oparty na przepływ danych zamiast przepływu sterowania. *Biblioteka przepływu danych* odwołuje się do programowania modelu, w których są wykonane obliczenia, gdy wszystkie wymagane dane są dostępne; *sterowania przepływem* odwołuje się do modelu programowania, w których są wykonane obliczenia w określonej kolejności.  
  
 Model programowania przepływu danych jest powiązany z pojęcie *przekazywania komunikatów*, gdzie niezależnych składników programu komunikować się ze sobą przy wysyłaniu wiadomości.  
  
 Biblioteki agentów składa się z trzech składników: *agentów asynchronicznych*, *bloki komunikatów asynchronicznych*, i *funkcje przekazywania komunikatów*. Agenci zarządzania stanem i użyj bloki komunikatów i funkcje przekazywania komunikatów, aby komunikować się ze sobą i składników zewnętrznych. Funkcje przekazywania komunikatów włączyć agentów do wysyłania i odbierania wiadomości do i z składników zewnętrznych. Bloki komunikatów asynchronicznych przechowywania wiadomości i włączyć agentów komunikowanie się w sposób zsynchronizowane.  
  
 Na poniższej ilustracji przedstawiono sposób dwaj agenci, użyj bloki komunikatów i funkcje przekazywania komunikatów do komunikacji. Na tej ilustracji `agent1` wysyła komunikat do `agent2` za pomocą [concurrency::send](reference/concurrency-namespace-functions.md#send) funkcji i [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) obiektu. `agent2` używa [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkcji, aby odczytać wiadomość. `agent2` wysyła komunikat do przy użyciu tej samej metody `agent1`. Strzałki przerywane przedstawiają przepływ danych między agentami. Stałe strzałki nawiązać agenci bloki komunikatów, które zapisu lub odczytu.  
  
 ![Składniki biblioteki agentów](../../parallel/concrt/media/agent_librarycomp.png "agent_librarycomp")  
  
 Przykładowy kod, który implementuje Ta ilustracja przedstawiono w dalszej części tego tematu.  
  
 Model programowania agent ma kilka zalet za pośrednictwem innych mechanizmów współbieżności i synchronizacji, na przykład zdarzenia. Jedną z zalet jest, że za pomocą przekazywanie komunikatów do przesłania zmian stanu między obiektami, można odizolować dostęp do zasobów udostępnionych, a tym samym poprawić skalowalność. Zaletą przekazywania komunikatów jest wiąże synchronizacji danych zamiast wiązanie go na obiekt synchronizacji zewnętrznych. To upraszcza transmisji danych między składnikami i wyeliminować błędy programowania aplikacji.  
  
## <a name="when-to-use-the-agents-library"></a>Kiedy należy używać biblioteki agentów  
 Biblioteki agentów należy użyć, jeśli masz wiele operacji, które muszą asynchronicznie komunikować się ze sobą. Bloki komunikatów i funkcje przekazywania komunikatów można pisać aplikacje równoległe bez konieczności mechanizmów synchronizacji, takie jak blokad. Dzięki temu można skupić się na logiki aplikacji.  
  
 Model programowania agenta jest często używany do tworzenia *potoki danych* lub *sieci*. Potoku danych jest szereg składników, z których każdy wykonuje określone zadanie, która wspiera większy cel. Każdy składnik w potoku przepływu danych wykonuje pracę po otrzymaniu komunikatu z innego składnika. Wynikiem tej pracy jest przekazywany do innych składników w potoku lub sieci. Składniki funkcji można używać więcej szczegółowych współbieżności z innych bibliotek, na przykład, [równoległych biblioteki wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład implementuje ilustracji pokazano wcześniej w tym temacie.  
  
 [!code-cpp[concrt-basic-agents#1](../../parallel/concrt/codesnippet/cpp/asynchronous-agents-library_1.cpp)]  
  
 Ten przykład generuje następujące wyniki:  
  
```Output  
agent1: sending request...  
agent2: received 'request'.  
agent2: sending response...  
agent1: received '42'.  
```  
  
 W poniższych tematach opisano funkcji używanych w tym przykładzie.  
  
## <a name="related-topics"></a>Tematy pokrewne  
 [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)  
 Opisuje rolę agentów asynchronicznych w rozwiązaniu większych zadań.  
  
 [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)  
 W tym artykule opisano różne typy bloku komunikatów, które są udostępniane przez biblioteki agentów.  
  
 [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)  
 Zawiera opis różnych procedur przekazywanie komunikatów, które są udostępniane przez biblioteki agentów.  
  
 [Instrukcje: implementowanie różnych wzorców producent — konsument](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)  
 Opisuje sposób Implementowanie wzorca producent — konsument w aplikacji.  
  
 [Instrukcje: zapewnianie funkcji pracy dla wywoływania oraz klasy transformatora](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)  
 Przedstawiono kilka sposobów zapewnianie funkcji pracy do [concurrency::call](../../parallel/concrt/reference/call-class.md) i [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) klasy.  
  
 [Instrukcje: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)  
 Przedstawia sposób użycia [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) klasy w potoku danych.  
  
 [Instrukcje: wybieranie spośród zadań wykonanych](../../parallel/concrt/how-to-select-among-completed-tasks.md)  
 Przedstawia sposób użycia [concurrency::choice](../../parallel/concrt/reference/choice-class.md) i [concurrency::join](../../parallel/concrt/reference/join-class.md) klasy do wybrania pierwszego zadania do wykonania algorytmu wyszukiwania.  
  
 [Instrukcje: wysyłanie komunikatu w regularnych odstępach czasu](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)  
 Przedstawia sposób użycia [concurrency::timer](../../parallel/concrt/reference/timer-class.md) klasy do wysyłania komunikatu w regularnych odstępach czasu.  
  
 [Instrukcje: korzystanie z filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
 Pokazuje, jak użyć filtru w celu włączenia komunikatów asynchronicznych block o zaakceptowanie lub odrzucenie wiadomości.  
  
 [Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)  
 Informacje dotyczące używania różnych równoległych wzorców, takich jak algorytmy równoległe w aplikacji.  
  
 [Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)  
 W tym artykule opisano współbieżność środowiska wykonawczego, co upraszcza Programowanie równoległe i zawiera linki do powiązanych tematów.

