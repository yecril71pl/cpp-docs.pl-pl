---
title: "Najlepsze rozwiązania w biblioteki agentów asynchronicznych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8d4b52839675334ab343adf48790bdce390dd5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>Biblioteka agentów asynchronicznych — Najlepsze praktyki
Ten dokument zawiera opis sposobu efektywnie wykorzystać biblioteki agentów asynchronicznych. Biblioteki agentów zamienia aktora na podstawie modelu programowania i komunikatów w trakcie przekazywanie dla coarse-grained przepływu danych i przetwarzanie potokowe zadania.  
  
 Aby uzyskać więcej informacji na temat biblioteki agentów, zobacz [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md).  
  
##  <a name="top"></a>Sekcje  
 Ten dokument zawiera następujące sekcje:  
  
- [Korzystania z agentów do stanu Isolate](#isolation)  
  
- [Użyj mechanizm ograniczania przepustowości, aby ograniczyć liczbę wiadomości w potoku danych](#throttling)  
  
- [Nie wykonuj szczegółowych pracy w potoku danych](#fine-grained)  
  
- [Nie przekazuj ładunków dużych komunikatów przez wartość](#large-payloads)  
  
- [Użyj shared_ptr w danych sieci podczas własność jest niezdefiniowana](#ownership)  
  
##  <a name="isolation"></a>Korzystania z agentów do stanu Isolate  
 Biblioteki agentów zawiera alternatyw do stanu udostępnionego, umożliwiając się izolowane składniki przy użyciu asynchronicznej mechanizm przekazywania komunikatów. Agentów asynchronicznych są najbardziej efektywne, gdy ich izolować ich stan wewnętrzny z innymi składnikami. Przez izolowanie stanu, wiele składników nie zazwyczaj działają na udostępnionych danych. Stan izolacji można włączyć aplikacji do skalowania, ponieważ pozwala uniknąć rywalizacji pamięci współużytkowanej. Stan izolacji zmniejsza ryzyko zakleszczenia i wyścigu warunków, ponieważ składniki nie mają dostępu do udostępnionych danych synchronizacji.  
  
 Zwykle izolować stanu w agencie, przytrzymując elementy członkowskie danych w `private` lub `protected` sekcje klasy agenta i przy użyciu buforów komunikatów do komunikowania się zmiany stanu. W poniższym przykładzie przedstawiono `basic_agent` klasy, która jest pochodną [concurrency::agent](../../parallel/concrt/reference/agent-class.md). `basic_agent` Klasy używa dwóch buforów komunikatów do komunikowania się z składników zewnętrznych. Jeden bufor komunikatów przechowuje komunikaty przychodzące; inne bufor komunikatów przechowuje komunikaty wychodzące.  
  
 [!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]  
  
 Zakończenie przykłady sposobu definiowania i korzystania z agentów można znaleźć [wskazówki: tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md) i [wskazówki: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md).  
  
 [[Górnej](#top)]  
  
##  <a name="throttling"></a>Użyj mechanizm ograniczania przepustowości, aby ograniczyć liczbę wiadomości w potoku danych  
 Wiele typów bufor komunikatów, takie jak [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), może przechowywać nieograniczoną liczbę komunikatów. Jeśli producent komunikatu szybciej niż konsumenta może przetwarzać takie komunikaty wysyła komunikaty do potoku danych, aplikacji mogą przejść w stan ilości pamięci lub braku pamięci. Można użyć mechanizm ograniczania przepustowości, na przykład semafora, aby ograniczyć liczbę wiadomości, które są jednocześnie aktywne w potoku danych.  
  
 W poniższym przykładzie podstawowe pokazano sposób użycia semafora, aby ograniczyć liczbę wiadomości w potoku danych. Dane w potoku używa [concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkcji, aby symulować operacji co najmniej 100 milisekund. Ponieważ nadawca tworzy szybciej niż konsumenta może przetwarzać komunikatów tych wiadomości, w tym przykładzie zdefiniowano `semaphore` klasy można włączyć aplikacji ograniczyć liczbę aktywnych wiadomości.  
  
 [!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]  
  
 `semaphore` Obiektu ogranicza potoku przetwarzania co najwyżej dwa komunikaty w tym samym czasie.  
  
 Producent w tym przykładzie wysyła komunikaty względnie mało do konsumenta. W związku z tym w tym przykładzie nie pokazują potencjalnych warunek ilości pamięci lub braku pamięci. Jednak ten mechanizm jest przydatne, gdy potoku danych zawiera stosunkowo dużej liczby komunikatów.  
  
 Aby uzyskać więcej informacji na temat tworzenia klasa semaforu, który jest używany w tym przykładzie, zobacz [porady: Korzystanie z klasy kontekstu do zaimplementowania semafora wspólnego](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).  
  
 [[Górnej](#top)]  
  
##  <a name="fine-grained"></a>Nie wykonuj szczegółowych pracy w potoku danych  
 Biblioteki agentów jest użyteczna, gdy jest dość coarse-grained pracy, który odbywa się za pośrednictwem potoku danych. Na przykład jeden składnik aplikacji może odczytać danych z pliku lub połączenie sieciowe i czasami wysyłania danych do innego składnika. Protokół, który korzysta z biblioteki agentów propagację wiadomości powoduje, że mają większe obciążenie niż konstrukcje równoległych zadań, udostępnianych przez mechanizm przekazywania komunikatów [Biblioteka równoległych wzorców](../../parallel/concrt/parallel-patterns-library-ppl.md) (PLL). W związku z tym upewnij się, że pracy, który odbywa się za pośrednictwem potoku danych jest wystarczająco długie przesunąć ten narzut.  
  
 Mimo że potoku danych jest najbardziej efektywne, gdy jego zadania są coarse-grained, każdego etapu w potoku danych można użyć konstrukcji PPL, takich jak grup zadań i algorytmy równoległe przeprowadzić bardziej szczegółową pracy. Na przykład sieć coarse-grained danych używa szczegółowych równoległości na każdym etapie przetwarzania zobacz [wskazówki: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 [[Górnej](#top)]  
  
##  <a name="large-payloads"></a>Nie przekazuj ładunków dużych komunikatów przez wartość  

 W niektórych przypadkach środowiska uruchomieniowego tworzy kopię każdej wiadomości przesyłanego z buforu komunikatu do innego buforu komunikatu. Na przykład [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) klasy oferuje kopii każdej wiadomości otrzymanych do każdego z jego elementów docelowych. Środowisko uruchomieniowe również tworzy kopię danych komunikat podczas korzystania z przekazywania wiadomości funkcji takich jak [concurrency::send](reference/concurrency-namespace-functions.md#send) i [concurrency::receive](reference/concurrency-namespace-functions.md#receive) pisanie i odbieranie wiadomości w wiadomości bufor. Chociaż ten mechanizm pozwala wyeliminować ryzyko jednocześnie zapisywania danych udostępnionych, gdy ładunek komunikatu jest stosunkowo dużej może prowadzić do pamięci niską wydajność.  
  
 Możesz użyć wskaźniki lub odwołania do poprawiania wydajności pamięci podczas przekazywania wiadomości, które mają duży ładunek. Poniższy przykład porównuje przekazywanie dużych wiadomości przez wartość do przekazywania wskaźników do tego samego typu komunikatu. W przykładzie zdefiniowano dwa typy agenta, `producer` i `consumer`, które działają na `message_data` obiektów. Przykład porównuje czasu, która jest wymagana dla producenta wysłać kilka `message_data` obiektów użytkownika do czasu, która jest wymagana dla agenta producent wysłać kilka wskaźniki do `message_data` obiekty do użytkownika.  
  
 [!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe:  
  
```Output  
Using message_data...  
took 437ms.  
Using message_data*...  
took 47ms.  
```  
  
 Wersji, która używa wskaźników działa lepiej, ponieważ eliminuje konieczność środowiska wykonawczego utworzyć pełną kopię co `message_data` obiekt, który przekazuje ono od producenta do konsumenta.  
  
 [[Górnej](#top)]  
  
##  <a name="ownership"></a>Użyj shared_ptr w danych sieci podczas własność jest niezdefiniowana  
 Podczas wysyłania wiadomości przez wskaźnik za pośrednictwem potoku przekazywania wiadomości lub sieci, zazwyczaj przydzielić pamięci dla każdego komunikatu z przodu sieci i zwolnić pamięć, że na końcu sieci. Chociaż ten mechanizm często działa dobrze, istnieją przypadki, w których jest trudne lub niemożliwe z niego korzystać. Rozważmy na przykład sytuacji, w której wiele węzłów końcowych zawiera sieci danych. W takim przypadku jest lokalizacja nie Wyczyść, aby zwolnić pamięć dla wiadomości.  
  
 Aby rozwiązać ten problem, można użyć mechanizm, na przykład [std::shared_ptr](../../standard-library/shared-ptr-class.md), umożliwiającej wskaźnik należeć do wielu składników. Gdy ostatecznych `shared_ptr` obiektu, który jest właścicielem zasobu, zasób jest również zwolniony.  
  
 W poniższym przykładzie pokazano sposób użycia `shared_ptr` udostępnianie wartości wskaźnika wśród wielu buforów komunikatów. Przykład łączy [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) obiektu do trzech [concurrency::call](../../parallel/concrt/reference/call-class.md) obiektów. `overwrite_buffer` Klasy oferuje wiadomości do każdego z jego elementów docelowych. Ponieważ istnieje wiele właścicieli danych na końcu sieci danych, w tym przykładzie użyto `shared_ptr` umożliwiające `call` obiekt, aby udostępnić prawa własności wiadomości.  
  
 [!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe:  
  
```Output  
Creating resource 42...  
receiver1: received resource 42  
Creating resource 64...  
receiver2: received resource 42  
receiver1: received resource 64  
Destroying resource 42...  
receiver2: received resource 64  
Destroying resource 64...  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność środowiska wykonawczego — najlepsze praktyki](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)   
 [Wskazówki: Tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)   
 [Wskazówki: Tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)   
 [Wskazówki: Tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [Biblioteka wzorów równoległych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [Środowisko uruchomieniowe współbieżności — najlepsze praktyki ogólne](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)

