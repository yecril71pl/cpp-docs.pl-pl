---
title: Najlepsze rozwiązania w bibliotece agentów asynchronicznych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e70b4004b24b04470e1fff280869887bbba74cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412746"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>Biblioteka agentów asynchronicznych — Najlepsze praktyki

W tym dokumencie opisano sposób efektywny używać bibliotekę asynchronicznych agentów. Biblioteka agentów promuje model programowania oparty na aktora i komunikatów w trakcie przekazywania dla gruboziarnistych przepływu danych i ich przetwarzanie potokowe zadania.

Aby uzyskać więcej informacji na temat biblioteki agentów, zobacz [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md).

##  <a name="top"></a> Sekcje

Ten dokument zawiera następujące sekcje:

- [Użycie agentów, aby odizolować stan](#isolation)

- [Użyj mechanizmu Dławiącego, aby ograniczyć liczbę komunikatów w potoku danych](#throttling)

- [Nie wykonuj szczegółowych prac w potoku danych](#fine-grained)

- [Nie przekazuj ładunków dużych bloków komunikatów według wartości](#large-payloads)

- [Użyj shared_ptr w danych sieciowych gdy nie określono własności](#ownership)

##  <a name="isolation"></a> Użycie agentów, aby odizolować stan

Biblioteka agentów zawiera alternatywy dla udostępnionego stanu, umożliwiając łączenie izolowane składniki za pomocą mechanizmu przekazywania komunikatów asynchronicznych. Agenci asynchroniczni są najbardziej efektywne, gdy ich izolowanie ich stan wewnętrzny od innych składników. Przez izolowanie stanu, wiele składników zazwyczaj działa we współdzielonych danych. Stan izolacji można włączyć aplikacji do skalowania, ponieważ pozwala uniknąć rywalizacji o pamięć współużytkowaną. Stan izolacji również zmniejsza ryzyko, warunki zakleszczenia i sytuacji wyścigu, ponieważ nie ma składników do synchronizowania dostępu do udostępnionych danych.

Zazwyczaj odizolować stan agenta poprzez posiadanie elementów członkowskich danych w `private` lub `protected` sekcje klasy agenta i przy użyciu buforów komunikatów do komunikowania się zmiany stanu. W poniższym przykładzie przedstawiono `basic_agent` klasy, która jest pochodną [concurrency::agent](../../parallel/concrt/reference/agent-class.md). `basic_agent` Klasa używa dwóch buforów komunikatów do komunikowania się z składników zewnętrznych. Jeden buforu komunikatów przechowuje komunikaty przychodzące; buforu komunikatu zawiera wiadomości wychodzące.

[!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]

Aby uzyskać kompletny przykład o tym, jak zdefiniować i korzystania z agentów, zobacz [wskazówki: tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md) i [wskazówki: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md).

[[Górnej](#top)]

##  <a name="throttling"></a> Użyj mechanizmu Dławiącego, aby ograniczyć liczbę komunikatów w potoku danych

Wiele typów buforu komunikatów, takie jak [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), może zawierać nieograniczoną liczbę komunikatów. Producent komunikatu szybciej, niż odbiorcy mogą przetworzyć te komunikaty wysyła komunikaty do potoku danych, aplikacja może przejść w stan małej ilości pamięci lub braku pamięci. Za pomocą mechanizmu dławiącego, na przykład semafor, aby ograniczyć liczbę wiadomości, które są jednocześnie aktywne w potoku danych.

Poniższy przykład podstawowy pokazuje, jak użyć semafor, aby ograniczyć liczbę komunikatów w potoku danych. Dane potok używa [concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkcję, aby symulować operacji, która zajmuje co najmniej 100 milisekund. Ponieważ nadawca generuje komunikaty szybciej, niż odbiorcy mogą przetworzyć te komunikaty, w tym przykładzie definiuje `semaphore` klasy, aby umożliwić aplikacji ograniczyć liczbę aktywnych komunikatów.

[!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]

`semaphore` Obiektu ogranicza potok przetwarzania co najwyżej dwa komunikaty, w tym samym czasie.

Producent, w tym przykładzie wysyła komunikaty relatywnie mało konsumenta. W związku z tym w tym przykładzie nie przedstawiono tu potencjalnych warunków małej ilości pamięci lub braku pamięci. Jednak ten mechanizm jest przydatne, gdy potoku danych zawiera stosunkowo dużej liczby komunikatów.

Aby uzyskać więcej informacji na temat tworzenia klasę semafora, która jest używana w tym przykładzie, zobacz [porady: Korzystanie z klasy kontekstu do wdrażania semafora Cooperative](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).

[[Górnej](#top)]

##  <a name="fine-grained"></a> Nie wykonuj szczegółowych prac w potoku danych

Biblioteka agentów jest najbardziej użyteczna, gdy pracę wykonywaną przez potok danych jest dość gruboziarnistych. Na przykład jeden składnik aplikacji może odczytywać dane z pliku lub połączenie sieciowe i od czasu do czasu wysyłania danych do innego składnika. Protokół, który używa biblioteki agentów Propagacja komunikatów powoduje, że masz większe obciążenie niż konstrukcje równoległych zadań, które są dostarczane przez mechanizm przekazywania komunikatów [biblioteki wzorców równoległych](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). W związku z tym upewnij się, że pracę wykonywaną przez potok danych jest wystarczająco długi, o które zostanie przesunięte to obciążenie.

Mimo że potoku danych jest najbardziej efektywne, gdy jego zadania podrzędne są gruboziarnistych, każdy etap potoku danych można użyć konstrukcje PPL, takich jak grupy zadań i algorytmów równoległych do wykonywania bardziej szczegółowych prac. Na przykład sieci gruboziarnistych danych, który używa równoległość drobnoziarnistą na każdym etapie przetwarzania zobacz [wskazówki: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Górnej](#top)]

##  <a name="large-payloads"></a> Nie przekazuj ładunków dużych bloków komunikatów według wartości

W niektórych przypadkach środowisko uruchomieniowe tworzy kopię każdego komunikatu przesyłanego z buforu komunikatu do innego buforu komunikatu. Na przykład [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) klasa oferuje kopii każdej wiadomości, które otrzymuje do każdego z jego elementów docelowych. Podczas korzystania z przekazywania komunikatów funkcji takich jak środowisko uruchomieniowe również tworzy kopię danych komunikatu [concurrency::send](reference/concurrency-namespace-functions.md#send) i [concurrency::receive](reference/concurrency-namespace-functions.md#receive) zapisywanie komunikatów i odczytywać komunikaty z komunikatu bufor. Mimo że ten mechanizm, pomaga wyeliminować ryzyko jednocześnie zapisywania udostępnionych danych, gdy ładunek komunikatu jest stosunkowo dużej ilości może prowadzić do pamięci niskiej wydajności.

Można użyć wskaźników lub odwołań do poprawiania wydajności pamięci podczas przekazywania wiadomości ma duże ładunku. W poniższym przykładzie porównano przekazywanie dużych komunikatów według wartości do przekazywania wskaźników do tego samego typu komunikatu. W przykładzie zdefiniowano dwa typy agenta, `producer` i `consumer`, które działają na `message_data` obiektów. W przykładzie porównano czasu, która jest wymagana dla producentów do wysyłania kilka `message_data` obiektów użytkownika do czasu, która jest wymagana dla agenta producenta do wysyłania wielu wskaźników do `message_data` obiekty do konsumenta.

[!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
Using message_data...
took 437ms.
Using message_data*...
took 47ms.
```

Wersja, która używa wskaźników działa lepiej, ponieważ eliminuje potrzebę środowiska uruchomieniowego utworzyć pełną kopię każdego `message_data` obiekt, który przekazuje od producenta do konsumenta.

[[Górnej](#top)]

##  <a name="ownership"></a> Użyj shared_ptr w danych sieciowych gdy nie określono własności

Podczas wysyłania wiadomości przez wskaźnik za pośrednictwem potoku przekazywania komunikatów lub sieci, są zazwyczaj przydzielić pamięci dla każdego komunikatu z przodu sieci i zwolnić pamięć, że na końcu sieci. Mimo że ten mechanizm często działa dobrze, istnieją przypadki, w których jest trudne lub niemożliwe z niego korzystać. Na przykład rozważmy przypadek, w której wiele węzłów końcowych zawiera sieci danych. W tym przypadku jest nie wyczyść lokalizacji, aby zwolnić pamięć dla wiadomości.

Aby rozwiązać ten problem, można użyć mechanizmu, na przykład [std::shared_ptr](../../standard-library/shared-ptr-class.md), umożliwiającej wskaźnika należy do wielu składników. Gdy końcowe `shared_ptr` niszczony jest obiekt, który posiada zasób, zasób zostanie również zwolniony.

Poniższy przykład pokazuje sposób użycia `shared_ptr` udostępnianie wartości wskaźnika wśród wielu buforów komunikatów. W przykładzie nawiązano połączenie [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) obiektu do trzech [concurrency::call](../../parallel/concrt/reference/call-class.md) obiektów. `overwrite_buffer` Klasa oferuje wiadomości do każdego z jego elementów docelowych. Ponieważ istnieje wielu właścicielom danych na końcu sieć danych, w tym przykładzie użyto `shared_ptr` włączyć `call` obiekt do udostępniania uprawnień własności wiadomości.

[!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

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

[Środowisko uruchomieniowe współbieżności — najlepsze praktyki](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Przewodnik: tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
[Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[Biblioteka wzorów równoległych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[Środowisko uruchomieniowe współbieżności — najlepsze praktyki ogólne](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)

