---
title: 'Przewodnik: Tworzenie agenta przepływu danych'
ms.date: 04/25/2019
helpviewer_keywords:
- creating dataflow agents [Concurrency Runtime]
- dataflow agents, creating [Concurrency Runtime]
ms.assetid: 9db5ce3f-c51b-4de1-b79b-9ac2a0cbd130
ms.openlocfilehash: bba72404b1c39ef1835b0c96883154b385181b6a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378288"
---
# <a name="walkthrough-creating-a-dataflow-agent"></a>Przewodnik: Tworzenie agenta przepływu danych

W tym dokumencie pokazano, jak tworzyć aplikacje oparte na agentach, oparte na przepływ danych zamiast przepływu sterowania.

*Przepływ sterowania* dotyczy kolejności wykonywania operacji w programie. Przepływ sterowania jest regulowany przy użyciu struktury sterujące, takie jak instrukcji warunkowej, pętli i tak dalej. Alternatywnie *przepływu danych* odwołuje się do modelu programowania, w których obliczenia są wykonane tylko wtedy, gdy wszystkie dane wymagane jest dostępna. Model programowania przepływu danych jest powiązane z pojęcie przekazywania, komunikatów, w którym niezależnie od składników programu komunikować się ze sobą, wysyłając komunikaty.

Agenci asynchroniczni obsługuje przepływu sterowania i przepływu danych modeli programowania. Mimo że przepływ sterowania model jest odpowiednie w wielu przypadkach, model przepływu danych jest właściwy dla innych osób, na przykład, gdy agent odbiera dane i wykonuje akcję, która opiera się na ładunku danych.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu, przeczytaj następujące dokumenty:

- [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Instrukcje: korzystanie z filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)

##  <a name="top"></a> Sekcje

Ten przewodnik zawiera następujące sekcje:

- [Tworzenie agenta przepływu sterowania podstawowe](#control-flow)

- [Tworzenie podstawowego agenta przepływ danych](#dataflow)

- [Tworzenie agenta logowania komunikatów](#logging)

##  <a name="control-flow"></a> Tworzenie agenta przepływu sterowania podstawowe

Rozważmy następujący przykład, który definiuje `control_flow_agent` klasy. `control_flow_agent` Klasa działa w trzech buforów komunikatów: jeden buforu i dwa wyjściowych buforów. `run` Metoda odczytuje dane ze źródła buforu komunikatu w pętli i przy użyciu instrukcji warunkowej kieruje przepływem wykonania programu. Agent zwiększa jeden licznik różna od zera, ujemnych wartości i zwiększa inny licznik dla wartości różna od zera, dodatnią. Gdy agent otrzyma wartość wartownik zero, wysyła wartości liczników do buforów komunikatów, który danych wyjściowych. `negatives` i `positives` metody umożliwiają aplikacji na odczytywanie liczb ujemny i dodatni wartości od agenta.

[!code-cpp[concrt-dataflow-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_1.cpp)]

Mimo że w tym przykładzie sprawia, że podstawowe zastosowanie przepływ sterowania w agencie, pokazuje serial charakter Programowanie oparte na przepływie sterowania. Każdy komunikat muszą zostać przetworzone po kolei, nawet jeśli wiele wiadomości mogą być dostępne w buforze komunikat wejściowy. Model przepływu danych umożliwia obu gałęzi instrukcji warunkowej, można obliczyć wartości jednocześnie. Model przepływu danych pozwala również tworzyć bardziej złożone sieci obsługi komunikatów, które działania na danych, po jej udostępnieniu.

[[Górnej](#top)]

##  <a name="dataflow"></a> Tworzenie podstawowego agenta przepływ danych

W tej sekcji pokazano, jak konwertować `control_flow_agent` klasy w celu wykonania tego samego zadania przy użyciu modelu przepływu danych.

Agenta przepływu danych polega na tworzeniu sieci buforów komunikatów, z których każdy pełni określonego celu. Niektóre bloki komunikatów należy użyć funkcji filtrowania akceptowanie lub odrzucanie wiadomość na podstawie ładunku. Funkcję filtru gwarantuje, że blok komunikatów odbiera tylko niektóre wartości.

#### <a name="to-convert-the-control-flow-agent-to-a-dataflow-agent"></a>Aby przekonwertować agenta sterowania przepływem do agenta przepływu danych

1. Kopiuj treść `control_flow_agent` klasy do innej klasy, na przykład `dataflow_agent`. Alternatywnie, możesz zmienić nazwę `control_flow_agent` klasy.

1. Usuń treść pętli, która wywołuje `receive` z `run` metody.

[!code-cpp[concrt-dataflow-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_2.cpp)]

1. W `run` metoda po zainicjowaniu zmienne `negative_count` i `positive_count`, Dodaj `countdown_event` obiektu, który śledzi liczbę aktywnymi operacjami.

[!code-cpp[concrt-dataflow-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_3.cpp)]

   `countdown_event` Klasy jest przedstawiony w dalszej części tego tematu.

1. Utwórz wiadomość obiektów buforu, które będą uczestniczyć w sieci przepływu danych.

[!code-cpp[concrt-dataflow-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_4.cpp)]

1. Łączenie buforów komunikatów w celu utworzenia sieci.

[!code-cpp[concrt-dataflow-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_5.cpp)]

1. Poczekaj, aż `event` i `countdown event` obiektów należy ustawić. Te zdarzenia sygnalizują, że agent odebrał wartość wartownik i ukończeniu wszystkich działań.

[!code-cpp[concrt-dataflow-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_6.cpp)]

Na poniższym diagramie przedstawiono sieć pełne przepływu danych dla `dataflow_agent` klasy:

![Sieć przepływu danych](../../parallel/concrt/media/concrt_dataflow.png "sieci przepływu danych")

W poniższej tabeli opisano elementy członkowskie w sieci.

|Element członkowski|Opis|
|------------|-----------------|
|`increment_active`|A [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) obiekt, który zwiększa licznik zdarzeń aktywnych i przekazuje wartość wejściowa do pozostałej części sieci.|
|`negatives`, `positives`|[CONCURRENCY::call](../../parallel/concrt/reference/call-class.md) obiektów, które zwiększyć liczbę liczb i zmniejsza Licznik aktywnych zdarzeń. Obiekty każdego Użyj filtru w celu akceptowania liczb ujemnych ani liczb dodatnich.|
|`sentinel`|A [concurrency::call](../../parallel/concrt/reference/call-class.md) obiektu, który akceptuje tylko wartość wartownik zero i zmniejsza Licznik aktywnych zdarzeń.|
|`connector`|A [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) obiekt, który buforu komunikatu źródła nawiązanie połączenia z siecią wewnętrzną.|

Ponieważ `run` metoda jest wywoływana w oddzielnym wątku, inne wątki mogą wysyłać wiadomości do sieci, przed podłączona sieci. `_source` Element członkowski danych jest `unbounded_buffer` obiekt, który buforuje wszystkich danych wejściowych, które są wysyłane z aplikacji do agenta. Aby upewnić się, sieci przetwarza komunikaty wszystkich danych wejściowych, agent najpierw łączy wewnętrznych węzłów sieci, a następnie początek tej sieci `connector`, `_source` element członkowski danych. Gwarantuje to, że komunikaty nie są przetwarzane jako powstaje sieci.

Ponieważ sieci, w tym przykładzie jest oparta na przepływ danych, zamiast na przepływ sterowania sieci muszą komunikować się z agentem czy zakończył przetwarzanie każdej wartości wejściowej i że węzeł wartownik otrzymał jego wartość. W tym przykładzie użyto `countdown_event` obiekt do sygnalizowania, że zostaną przetworzone wszystkie wartości wejściowe i [concurrency::event](../../parallel/concrt/reference/event-class.md) obiektu, aby wskazać, że węzeł wartownik otrzymał jego wartość. `countdown_event` Klasy używa `event` obiekt do sygnalizowania, gdy wartość licznika osiągnie zero. Nagłówek sieci przepływu danych zwiększa licznik za każdym razem, gdy jej otrzymuje wartość. Każdy terminalu węzeł zmniejsza sieci licznika po przetwarza wartości wejściowej. Po agent tworzy sieci przepływu danych, czeka węzeł wartownik, aby ustawić `event` obiektu i `countdown_event` obiekt do sygnalizowania, że jego licznik osiągnęła wartość zero.

W poniższym przykładzie przedstawiono `control_flow_agent`, `dataflow_agent`, i `countdown_event` klasy. `wmain` Funkcja tworzy `control_flow_agent` i `dataflow_agent` obiektu i zastosowań  `send_values` /funkcja do wysyłania szereg wartości losowych do agentów.

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

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `dataflow-agent.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc przepływu danych agent.cpp**

[[Górnej](#top)]

##  <a name="logging"></a> Tworzenie agenta logowania komunikatów

W poniższym przykładzie przedstawiono `log_agent` klasy, która przypomina `dataflow_agent` klasy. `log_agent` Klasa implementuje agenta rejestrowania asynchronicznego zapisu rejestrowania komunikatów, do pliku i do konsoli. `log_agent` Klasa umożliwia aplikacji do kategoryzowania wiadomości informacyjny, ostrzeżenia lub błędu. Umożliwia również aplikacji określić, czy każda kategoria dziennika są zapisywane w pliku i/lub konsoli. Ten przykład zapisuje wszystkie komunikaty dziennika do pliku i tylko komunikaty o błędach do konsoli.

[!code-cpp[concrt-log-filter#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_8.cpp)]

Ten przykład zapisuje następujące dane wyjściowe do konsoli.

```Output
error: This is a sample error message.
```

Ten przykład również generuje plik log.txt, który zawiera poniższy tekst.

```Output
info: ===Logging started.===
warning: This is a sample warning message.
error: This is a sample error message.
info: ===Logging finished.===
```

### <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `log-filter.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc log-filter.cpp**

[[Górnej](#top)]

## <a name="see-also"></a>Zobacz także

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
