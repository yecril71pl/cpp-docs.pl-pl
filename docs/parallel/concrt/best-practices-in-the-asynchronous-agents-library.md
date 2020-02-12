---
title: Biblioteka agentów asynchronicznych — Najlepsze praktyki
ms.date: 11/04/2016
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
ms.openlocfilehash: 1cd6b54a014d35d17c732ed52f8529b05274585b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142097"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>Biblioteka agentów asynchronicznych — Najlepsze praktyki

W tym dokumencie opisano sposób efektywnego korzystania z biblioteki agentów asynchronicznych. Biblioteka agenci wspiera model programowania oparty na aktorze i przetwarza komunikaty w procesie, które są przekazywane do przepływu danych i zadań potokowych.

Aby uzyskać więcej informacji na temat biblioteki Agents, zobacz [Biblioteka agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md).

## <a name="top"></a>Poszczególne

Ten dokument zawiera następujące sekcje:

- [Użyj agentów do izolowania stanu](#isolation)

- [Użyj mechanizmu ograniczania przepustowości, aby ograniczyć liczbę komunikatów w potoku danych](#throttling)

- [Nie wykonuj szczegółowych prac w potoku danych](#fine-grained)

- [Nie przekazuj dużych ładunków komunikatów według wartości](#large-payloads)

- [Użyj shared_ptr w sieci danych, gdy własność jest niezdefiniowana](#ownership)

## <a name="isolation"></a>Użyj agentów do izolowania stanu

Biblioteka agenci zapewnia alternatywy dla udostępnionego stanu przez umożliwienie łączenia składników izolowanych za pomocą mechanizmu asynchronicznego przekazywania komunikatów. Agenci asynchroniczni są najbardziej efektywni, gdy izolują swój wewnętrzny stan z innych składników. Przez izolację stanu wiele składników zazwyczaj nie działa na danych udostępnionych. Izolacja stanu może umożliwić skalowanie aplikacji, ponieważ zmniejsza rywalizację do pamięci współdzielonej. Izolacja stanu zmniejsza również prawdopodobieństwo zakleszczenia i warunków wyścigu, ponieważ składniki nie muszą synchronizować dostępu do udostępnionych danych.

Zazwyczaj izolowany jest stan w agencie przez utrzymywanie składowych danych w `private` lub `protected` sekcjach klasy agenta oraz przy użyciu buforów komunikatów do przekazywania zmian stanu. Poniższy przykład przedstawia klasę `basic_agent`, która pochodzi od [concurrency:: Agent](../../parallel/concrt/reference/agent-class.md). Klasa `basic_agent` używa dwóch buforów komunikatów do komunikacji ze składnikami zewnętrznymi. Jeden bufor komunikatów zawiera komunikaty przychodzące; drugi bufor komunikatów zawiera komunikaty wychodzące.

[!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]

Aby zapoznać się z kompletnymi przykładami dotyczącymi definiowania agentów i korzystania z nich, zobacz [Przewodnik: Tworzenie aplikacji opartej na agencie](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md) i [Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md).

[[Top](#top)]

## <a name="throttling"></a>Użyj mechanizmu ograniczania przepustowości, aby ograniczyć liczbę komunikatów w potoku danych

Wiele typów buforów komunikatów, takich jak [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md), może zawierać nieograniczoną liczbę komunikatów. Gdy producent komunikatu wysyła komunikaty do potoku danych szybciej niż odbiorca może przetworzyć te komunikaty, aplikacja może wprowadzić stan niskiej lub wolnej pamięci. Można użyć mechanizmu ograniczania przepustowości, na przykład semafora, aby ograniczyć liczbę komunikatów współbieżnie aktywnych w potoku danych.

Poniższy przykład podstawowy pokazuje, jak używać semafora, aby ograniczyć liczbę komunikatów w potoku danych. Potok danych używa funkcji [concurrency:: wait](reference/concurrency-namespace-functions.md#wait) do symulowania operacji, która trwa co najmniej 100 milisekund. Ponieważ nadawca generuje komunikaty szybciej niż odbiorca może przetworzyć te komunikaty, w tym przykładzie zdefiniowano klasę `semaphore`, aby umożliwić aplikacji ograniczenie liczby aktywnych komunikatów.

[!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]

Obiekt `semaphore` ogranicza potok do przetworzenia maksymalnie dwóch komunikatów w tym samym czasie.

Producent w tym przykładzie wysyła stosunkowo kilka komunikatów do konsumenta. W związku z tym ten przykład nie pokazuje potencjalnego stanu niskiej ilości pamięci lub braku pamięci. Jednak ten mechanizm jest przydatny, gdy Potok danych zawiera stosunkowo dużą liczbę komunikatów.

Aby uzyskać więcej informacji na temat sposobu tworzenia klasy semaforów, która jest używana w tym przykładzie, zobacz [How to: Use the Context Class to Implement The Spółdzielczy semafor](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).

[[Top](#top)]

## <a name="fine-grained"></a>Nie wykonuj szczegółowych prac w potoku danych

Biblioteka agentów jest najbardziej użyteczna, gdy prace wykonywane przez potok danych są dość duże. Na przykład jeden składnik aplikacji może odczytywać dane z pliku lub połączenia sieciowego i okazjonalnie wysyłać je do innego składnika. Protokół, który jest wykorzystywany przez bibliotekę agentów do propagowania komunikatów, sprawia, że mechanizm przekazywania komunikatów jest bardziej narzutem niż konstrukcje równoległe zadań, które są dostarczane przez [bibliotekę wzorców równoległych](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). W związku z tym upewnij się, że prace wykonywane przez potok danych są wystarczająco długie, aby można było przesunąć to obciążenie.

Mimo że Potok danych jest najbardziej skuteczny, gdy jego zadania są bardzo duże, każdy etap potoku danych może używać konstrukcji PPL, takich jak grupy zadań i algorytmy równoległe, aby wykonywać bardziej szczegółowe zadania. Aby zapoznać się z przykładem wieloskładnikowej sieci danych, która korzysta z precyzyjnej równoległości na każdym etapie przetwarzania, zobacz [Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Top](#top)]

## <a name="large-payloads"></a>Nie przekazuj dużych ładunków komunikatów według wartości

W niektórych przypadkach środowisko uruchomieniowe tworzy kopię wszystkich komunikatów przesyłanych z jednego buforu komunikatów do innego buforu komunikatów. Na przykład Klasa [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) zawiera kopię każdego komunikatu, który otrzymuje do każdego z jego obiektów docelowych. Środowisko uruchomieniowe tworzy również kopię danych komunikatów w przypadku korzystania z funkcji przekazywania komunikatów, takich jak [concurrency:: Send](reference/concurrency-namespace-functions.md#send) i [concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) do zapisu komunikatów w buforze komunikatów i odczytywania komunikatów. Mimo że ten mechanizm pozwala wyeliminować ryzyko współbieżnego zapisu danych udostępnionych, może to doprowadzić do niskiej wydajności pamięci, gdy ładunek wiadomości jest stosunkowo duży.

Możesz użyć wskaźników lub odwołań, aby zwiększyć wydajność pamięci podczas przekazywania wiadomości z dużym ładunkiem. Poniższy przykład porównuje przekazywanie dużych komunikatów przez wartość, aby przekazywać wskaźniki do tego samego typu wiadomości. W przykładzie zdefiniowano dwa typy agentów, `producer` i `consumer`, które działają na `message_data` obiektów. Przykład porównuje czas wymagany przez producenta do wysłania kilku `message_data` obiektów do konsumenta do czasu wymaganego przez agenta produkcyjnego do wysłania kilku wskaźników do `message_data` obiektów do konsumenta.

[!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
Using message_data...
took 437ms.
Using message_data*...
took 47ms.
```

Wersja, która korzysta ze wskaźników, jest lepsza, ponieważ eliminuje wymagania dla środowiska uruchomieniowego, aby utworzyć pełną kopię każdego obiektu `message_data`, który przekazuje od producenta do konsumenta.

[[Top](#top)]

## <a name="ownership"></a>Użyj shared_ptr w sieci danych, gdy własność jest niezdefiniowana

Po wysłaniu komunikatów przez wskaźnik przez potok przekazywania komunikatów lub sieć zazwyczaj przydzielana jest pamięć dla każdej wiadomości na początku sieci i wolna pamięć na końcu sieci. Chociaż ten mechanizm często działa prawidłowo, istnieją przypadki, w których jest trudne lub niemożliwe do użycia. Rozważmy na przykład przypadek, w którym sieć danych zawiera wiele węzłów końcowych. W takim przypadku nie istnieje czyszczenie lokalizacji do zwolnienia pamięci dla komunikatów.

Aby rozwiązać ten problem, można użyć mechanizmu, na przykład [std:: shared_ptr](../../standard-library/shared-ptr-class.md), który umożliwia przeznaczenie wskaźnika przez wiele składników. Gdy końcowy obiekt `shared_ptr`, który jest właścicielem zasobu, jest również zwolniony.

W poniższym przykładzie pokazano, jak używać `shared_ptr` do udostępniania wartości wskaźników między wieloma buforami komunikatów. Przykład łączy obiekt [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) do trzech obiektów [concurrency:: Call](../../parallel/concrt/reference/call-class.md) . Klasa `overwrite_buffer` oferuje komunikaty do każdego z jego obiektów docelowych. Ponieważ istnieje wielu właścicieli danych znajdujących się na końcu sieci danych, w tym przykładzie używa `shared_ptr`, aby umożliwić każdemu obiektowi `call` udostępnianie własności komunikatów.

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
