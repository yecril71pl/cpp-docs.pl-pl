---
title: 'Wskazówki: tworzenie agenta przepływu danych'
ms.date: 04/25/2019
helpviewer_keywords:
- creating dataflow agents [Concurrency Runtime]
- dataflow agents, creating [Concurrency Runtime]
ms.assetid: 9db5ce3f-c51b-4de1-b79b-9ac2a0cbd130
ms.openlocfilehash: fa19d965a35909dfefc5f586c772bc9b4565e814
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142974"
---
# <a name="walkthrough-creating-a-dataflow-agent"></a>Wskazówki: tworzenie agenta przepływu danych

W tym dokumencie przedstawiono sposób tworzenia aplikacji opartych na agencie, które są oparte na przepływu danych zamiast przepływu sterowania.

*Przepływ sterowania* odnosi się do kolejności wykonywania operacji w programie. Przepływ sterowania jest regulowany przy użyciu struktur kontroli, takich jak instrukcje warunkowe, pętle i tak dalej. Alternatywnie, *przepływu danych* odnosi się do modelu programowania, w którym obliczenia są wykonywane tylko wtedy, gdy wszystkie wymagane dane są dostępne. Model programowania przepływu danych jest powiązany z koncepcją przekazywania komunikatów, w którym niezależne składniki programu komunikują się ze sobą przez wysyłanie komunikatów.

Agenci asynchroniczni obsługują zarówno model sterujący Flow, jak i modele programowania przepływu danych. Chociaż model przepływu sterowania jest odpowiedni w wielu przypadkach, model przepływu danych jest odpowiedni dla innych, na przykład gdy Agent odbiera dane i wykonuje akcję opartą na ładunku tych danych.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu zapoznaj się z następującymi dokumentami:

- [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Instrukcje: korzystanie z filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)

## <a name="top"></a>Poszczególne

Ten Instruktaż zawiera następujące sekcje:

- [Tworzenie podstawowego agenta sterowania przepływem](#control-flow)

- [Tworzenie podstawowego agenta przepływu danych](#dataflow)

- [Tworzenie agenta rejestrowania komunikatów](#logging)

## <a name="control-flow"></a>Tworzenie podstawowego agenta sterowania przepływem

Rozważmy poniższy przykład, który definiuje klasę `control_flow_agent`. Klasa `control_flow_agent` działa na trzech buforach komunikatów: jeden bufor wejściowy i dwa bufory wyjściowe. Metoda `run` odczytuje z bufora komunikatów źródłowych w pętli i używa instrukcji warunkowej, aby skierować przepływ wykonywania programu. Agent zwiększa jeden licznik dla wartości niezerowych i zwiększa inny licznik dla wartości innych niż zero. Gdy Agent otrzyma wartość wskaźnikową zero, wysyła wartości liczników do buforów komunikatów wyjściowych. Metody `negatives` i `positives` umożliwiają aplikacji odczytywanie liczb ujemnych i dodatnich wartości z agenta.

[!code-cpp[concrt-dataflow-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_1.cpp)]

Chociaż w tym przykładzie podstawowe użycie przepływu sterowania w agencie, pokazuje szeregowy charakter programowania opartego na przepływie sterowania. Każdy komunikat musi być przetwarzany sekwencyjnie, mimo że w buforze komunikatów wejściowych może być dostępnych wiele komunikatów. Model przepływu danych umożliwia równoczesne oszacowanie obu gałęzi instrukcji warunkowej. Model przepływu danych umożliwia również tworzenie bardziej złożonych sieci komunikatów, które działają na danych w miarę ich udostępniania.

[[Top](#top)]

## <a name="dataflow"></a>Tworzenie podstawowego agenta przepływu danych

W tej sekcji przedstawiono sposób konwersji klasy `control_flow_agent`, aby użyć modelu przepływu danych do wykonania tego samego zadania.

Agent przepływu danych działa przez utworzenie sieci buforów komunikatów, z których każdy służy do określonego celu. Niektóre bloki komunikatów używają funkcji filtru, aby akceptować lub odrzucać komunikat na podstawie jego ładunku. Funkcja filtru zapewnia, że blok komunikatów odbiera tylko niektóre wartości.

#### <a name="to-convert-the-control-flow-agent-to-a-dataflow-agent"></a>Aby przekonwertować agenta sterowania przepływem do agenta przepływu danych

1. Skopiuj treść klasy `control_flow_agent` do innej klasy, na przykład `dataflow_agent`. Alternatywnie można zmienić nazwę klasy `control_flow_agent`.

1. Usuń treść pętli, która wywołuje `receive` z metody `run`.

[!code-cpp[concrt-dataflow-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_2.cpp)]

1. W metodzie `run` po zainicjowaniu zmiennych `negative_count` i `positive_count`Dodaj obiekt `countdown_event`, który śledzi liczbę aktywnych operacji.

[!code-cpp[concrt-dataflow-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_3.cpp)]

   Klasa `countdown_event` jest pokazana w dalszej części tego tematu.

1. Utwórz obiekty buforu komunikatów, które będą uczestniczyć w sieci przepływu danych.

[!code-cpp[concrt-dataflow-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_4.cpp)]

1. Podłącz bufory komunikatów w celu utworzenia sieci.

[!code-cpp[concrt-dataflow-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_5.cpp)]

1. Poczekaj, aż obiekty `event` i `countdown event` mają być ustawione. Te zdarzenia sygnalizują, że agent otrzymał wartość wskaźnikową i że wszystkie operacje zostały zakończone.

[!code-cpp[concrt-dataflow-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_6.cpp)]

Na poniższym diagramie przedstawiono kompletną sieć przepływu danych dla klasy `dataflow_agent`:

![Sieć przepływu danych](../../parallel/concrt/media/concrt_dataflow.png "Sieć przepływu danych")

W poniższej tabeli opisano elementy członkowskie sieci.

|Członek|Opis|
|------------|-----------------|
|`increment_active`|Obiekt [concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) , który zwiększa aktywny licznik zdarzeń i przekazuje wartość wejściową do pozostałej części sieci.|
|`negatives`, `positives`|[concurrency:: Call](../../parallel/concrt/reference/call-class.md) obiekty, które zwiększają liczbę liczb i zmniejszają aktywny licznik zdarzeń. Wszystkie obiekty używają filtru, aby akceptować liczby ujemne lub liczby dodatnie.|
|`sentinel`|Obiekt [concurrency:: Call](../../parallel/concrt/reference/call-class.md) , który akceptuje tylko wartość wskaźnikową zero i zmniejsza aktywny licznik zdarzeń.|
|`connector`|Obiekt [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) , który łączy źródłowy bufor komunikatów z siecią wewnętrzną.|

Ponieważ metoda `run` jest wywoływana w osobnym wątku, inne wątki mogą wysyłać komunikaty do sieci przed całkowitym połączeniem sieci. Element członkowski danych `_source` jest obiektem `unbounded_buffer`, który buforuje wszystkie dane wejściowe wysyłane z aplikacji do agenta. Aby upewnić się, że sieć przetwarza wszystkie komunikaty wejściowe, Agent najpierw łączy wewnętrzne węzły sieci, a następnie łączy początek tej sieci, `connector`, z elementem członkowskim danych `_source`. Gwarantuje to, że komunikaty nie są przetwarzane w miarę tworzenia sieci.

Ponieważ sieć w tym przykładzie jest oparta na przepływu danych, a nie w przepływie sterowania, Sieć musi komunikować się z agentem, że zakończył przetwarzanie każdej wartości wejściowej i że węzeł wskaźnikowy otrzymał jego wartość. W tym przykładzie użyto obiektu `countdown_event`, aby sygnalizować, że wszystkie wartości wejściowe zostały przetworzone i obiekt [concurrency:: Event](../../parallel/concrt/reference/event-class.md) , aby wskazać, że węzeł wskaźnikowy otrzymał jego wartość. Klasa `countdown_event` używa obiektu `event` do sygnalizowania, gdy wartość licznika osiągnie zero. Kierownik sieci przepływu danych zwiększa licznik za każdym razem, gdy otrzymuje wartość. Każdy węzeł terminalu w sieci zmniejsza licznik po przetworzeniu wartości wejściowej. Gdy Agent tworzy sieć przepływu danych, czeka, aż węzeł wskaźnikowy ustawi obiekt `event` i dla obiektu `countdown_event`, aby sygnalizować, że jego licznik osiągnął wartość zerową.

W poniższym przykładzie przedstawiono klasy `control_flow_agent`, `dataflow_agent`i `countdown_event`. Funkcja `wmain` tworzy obiekt `control_flow_agent` i `dataflow_agent` i używa funkcji `send_values` do wysyłania serii losowych wartości do agentów.

[!code-cpp[concrt-dataflow-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_7.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
Control-flow agent:
There are 500523 negative numbers.
There are 499477 positive numbers.
Dataflow agent:
There are 500523 negative numbers.
There are 499477 positive numbers.
```

### <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `dataflow-agent.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**CL. exe/EHsc Dataflow-Agent. cpp**

[[Top](#top)]

## <a name="logging"></a>Tworzenie agenta rejestrowania komunikatów

W poniższym przykładzie pokazano klasę `log_agent`, która jest podobna do klasy `dataflow_agent`. Klasa `log_agent` implementuje Asynchroniczny Agent rejestrowania, który zapisuje komunikaty dziennika do pliku i konsoli programu. Klasa `log_agent` umożliwia aplikacji kategoryzowanie komunikatów jako informacyjnych, ostrzeżeń lub błędów. Umożliwia również aplikacji określenie, czy każda kategoria dziennika jest zapisywana w pliku, w konsoli programu czy w obu tych przypadkach. Ten przykład zapisuje wszystkie komunikaty dziennika do pliku i tylko komunikaty o błędach do konsoli.

[!code-cpp[concrt-log-filter#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_8.cpp)]

Ten przykład zapisuje następujące dane wyjściowe w konsoli programu.

```Output
error: This is a sample error message.
```

Ten przykład tworzy również plik log. txt, który zawiera poniższy tekst.

```Output
info: ===Logging started.===
warning: This is a sample warning message.
error: This is a sample error message.
info: ===Logging finished.===
```

### <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `log-filter.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**CL. exe/EHsc log-Filter. cpp**

[[Top](#top)]

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
