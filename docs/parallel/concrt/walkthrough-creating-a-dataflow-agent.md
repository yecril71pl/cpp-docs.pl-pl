---
title: "Wskazówki: Tworzenie agenta przepływu danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- creating dataflow agents [Concurrency Runtime]
- dataflow agents, creating [Concurrency Runtime]
ms.assetid: 9db5ce3f-c51b-4de1-b79b-9ac2a0cbd130
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b94fb68ad28e45141551b238acf99baedf78ef6a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-creating-a-dataflow-agent"></a>Wskazówki: tworzenie agenta przepływu danych
Ten dokument przedstawia sposób tworzenia aplikacji opartych na agenta, oparte na przepływu danych, zamiast przepływu sterowania.  
  
 *Przepływ kontroli* odwołuje się do kolejność wykonywania działań w programie. Przepływ sterowania jest regulowany za pomocą struktury sterujące, takie jak warunkowe instrukcje, pętli i tak dalej. Alternatywnie *przepływu danych* odwołuje się do modelu programowania, w których obliczenia są wykonane tylko wtedy, gdy wszystkie dane wymagane jest dostępna. Model programowania przepływu danych jest powiązany z koncepcji komunikatu przekazywanie, w którym niezależne składników programu komunikować się ze sobą przy wysyłaniu wiadomości.  
  
 Agenci asynchroniczni obsługuje zarówno przepływu sterowania, jak i modele programowania przepływu danych. Mimo że modelu przepływu sterowania jest odpowiednia w wielu przypadkach, model przepływu danych jest w innych, na przykład, gdy agent odbiera dane i wykonuje akcję, która jest oparta na ładunku danych.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przeczytaj następujące dokumenty przed skorzystaniem z tego przewodnika:  
  
- [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)  
  
- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [Porady: Użyj filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
##  <a name="top"></a>Sekcje  
 Ten przewodnik zawiera następujące sekcje:  
  
- [Tworzenie agenta podstawowy przepływ sterowania](#control-flow)  
  
- [Tworzenie agenta przepływu danych podstawowych](#dataflow)  
  
- [Tworzenie agenta rejestrowania komunikatów](#logging)  
  
##  <a name="control-flow"></a>Tworzenie agenta podstawowy przepływ sterowania  
 Rozważmy następujący przykład, który definiuje `control_flow_agent` klasy. `control_flow_agent` Klasa działa na trzy buforów komunikatów: jeden wejściowy buforu i dwa wyjściowe buforów. `run` Metoda odczytuje z bufora źródłowego komunikat w pętli i używa instrukcji warunkowej przekierować przepływ wykonania programu. Agent zwiększa jeden licznik do zera, ujemnych wartości i zwiększa licznik innej wartości innej niż zero, dodatnią. Gdy agent otrzyma wartownik wartość zero, wysyła wartości liczników do buforów komunikatu wyjściowego. `negatives` i `positives` metody Włącz aplikacji na odczytywanie liczby wartości ujemnych i dodatnich od agenta.  
  
 [!code-cpp[concrt-dataflow-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_1.cpp)]  
  
 Mimo że w tym przykładzie powoduje, że podstawowe wykorzystanie przepływu sterowania agenta, pokazuje serial rodzaj sterowania przepływem na podstawie programowania. Każdy komunikat muszą być przetwarzane sekwencyjnie, mimo że wiele komunikatów mogą zostać udostępnione w buforze komunikatu wejściowego. Model przepływu danych umożliwia obu gałęziach instrukcji warunkowej do oceny jednocześnie. Model przepływu danych pozwala również tworzyć bardziej złożone sieci obsługi komunikatów, które działają w danych po jej udostępnieniu.  
  
 [[Górnej](#top)]  
  
##  <a name="dataflow"></a>Tworzenie agenta przepływu danych podstawowych  
 W tej sekcji przedstawiono sposób konwertowania `control_flow_agent` klasy na potrzeby wykonania tego samego zadania przepływu danych modelu.  
  
 Działa agenta przepływu danych, tworząc sieci buforów komunikatów, z których każdy spełnia określone przeznaczenie. Niektóre bloki komunikatów użyć funkcji filtru, aby zaakceptować lub odrzucić komunikat na podstawie jego ładunku. Funkcja filtru gwarantuje, że blok komunikatów odbiera tylko niektóre wartości.  
  
#### <a name="to-convert-the-control-flow-agent-to-a-dataflow-agent"></a>Aby przekonwertować agenta sterowania przepływem do agenta przepływu danych  
  
1.  Kopiuj treść `control_flow_agent` klasy do innej klasy, na przykład `dataflow_agent`. Alternatywnie można zmienić nazwy `control_flow_agent` klasy.  
  
2.  Usuń treści pętli, które wywołuje `receive` z `run` metody.  
  
 [!code-cpp[concrt-dataflow-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_2.cpp)]  
  
3.  W `run` metody po zainicjowaniu zmienne `negative_count` i `positive_count`, Dodaj `countdown_event` obiekt śledzący liczba aktywnych operacji.  
  
 [!code-cpp[concrt-dataflow-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_3.cpp)]  
  
     `countdown_event` Klasy przedstawiono w dalszej części tego tematu.  
  
4.  Utwórz wiadomość buforu obiektów, które będą uczestniczyć w sieci przepływu danych.  
  
 [!code-cpp[concrt-dataflow-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_4.cpp)]  
  
5.  Łączenie buforów komunikatów do utworzenia sieci.  
  
 [!code-cpp[concrt-dataflow-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_5.cpp)]  
  
6.  Poczekaj, aż `event` i `countdown event` obiektów należy ustawić wartość. Te zdarzenia sygnalizują, który agent otrzymano wartości wartownika i zakończono wszystkie operacje.  
  
 [!code-cpp[concrt-dataflow-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_6.cpp)]  
  
 Na poniższym diagramie przedstawiono sieć ukończenia przepływu danych `dataflow_agent` klasy:  
  
 ![Biblioteka przepływu danych sieci](../../parallel/concrt/media/concrt_dataflow.png "concrt_dataflow")  
  
 W poniższej tabeli opisano elementy członkowskie w sieci.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`increment_active`|A [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) obiekt, który zwiększa licznik zdarzeń aktywnych i przekazuje wartość wejściowa do pozostałej części sieci.|  
|`negatives`, `positives`|[CONCURRENCY::call](../../parallel/concrt/reference/call-class.md) obiektów, które zwiększyć liczbę cyfr i zmniejsza licznik zdarzeń aktywnych. Obiekty każdego Użyj filtru, aby zaakceptować dodatnie albo ujemne.|  
|`sentinel`|A [concurrency::call](../../parallel/concrt/reference/call-class.md) obiektu, który akceptuje tylko wartości wartownika zero i zmniejsza licznik zdarzeń aktywnych.|  
|`connector`|A [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) obiekt, który łączy bufor komunikatów źródłowy do sieci wewnętrznej.|  
  
 Ponieważ `run` metoda jest wywoływana w oddzielnym wątku, inne wątki będą mogły wysyłać wiadomości do sieci przed podłączona sieć. `_source` Elementu członkowskiego danych jest `unbounded_buffer` obiekt, który buforuje wszystkie dane wejściowe, wysyłany z aplikacji do agenta. Aby upewnić się, sieci przetwarza wiadomości wszystkich wejściowych, agenta najpierw łączy wewnętrznych węzłów, sieci i stanowi łącze początek tej sieci `connector`, do `_source` element członkowski danych. Gwarantuje to, że komunikaty nie przetworzenie jako powstaje sieci.  
  
 Ponieważ sieci, w tym przykładzie jest oparta na przepływu danych, zamiast na przepływu sterowania, sieci muszą komunikować się z agentem czy zakończył przetwarzanie każdej wartości wejściowej i otrzymanie w węźle wartownik jej wartość. W tym przykładzie użyto `countdown_event` obiektu, która sygnalizuje, że zostaną przetworzone wszystkie wartości wejściowe i [concurrency::event](../../parallel/concrt/reference/event-class.md) obiekt, aby wskazać otrzymanie w węźle wartownik jej wartość. `countdown_event` Klasy używa `event` obiektu, która sygnalizuje, gdy wartość licznika osiągnie wartość zero. Nagłówek sieci przepływu danych zwiększa licznik za każdym razem, że odbiera wartość. Każdy terminali węzeł zmniejsza sieci licznika po przetwarza wartości wejściowej. Po agenta formularzy sieci przepływu danych, oczekuje na węźle wartownik można ustawić `event` obiektu i `countdown_event` obiektu, która sygnalizuje, że jego licznika osiągnęła wartość zero.  
  
 W poniższym przykładzie przedstawiono `control_flow_agent`, `dataflow_agent`, i `countdown_event` klasy. `wmain` Funkcja tworzy `control_flow_agent` i `dataflow_agent` obiektu i używa `send_values` funkcja do wysyłania serii losowych wartości do agentów.  
  
 [!code-cpp[concrt-dataflow-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_7.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe:  
  
```Output  
Control-flow agent:  
There are 500523 negative numbers.  
There are 499477 positive numbers.  
Dataflow agent:  
There are 500523 negative numbers.  
There are 499477 positive numbers.  
```  
  
### <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `dataflow-agent.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc przepływu danych agent.cpp**  
  
 [[Górnej](#top)]  
  
##  <a name="logging"></a>Tworzenie agenta rejestrowania komunikatów  
 W poniższym przykładzie przedstawiono `log_agent` klasy, która jest podobny `dataflow_agent` klasy. `log_agent` Klasa implementuje agenta rejestrowania asynchroniczne czy zapisuje komunikaty dziennika do pliku i do konsoli. `log_agent` Klasa umożliwia aplikacjom kategoryzowanie wiadomości celów informacyjnych, warning lub error. Umożliwia również aplikacji określić, czy każda kategoria dziennika są zapisywane do pliku i/lub konsoli. W tym przykładzie zapisuje wszystkie komunikaty dziennika do pliku i tylko komunikaty o błędach do konsoli.  
  
 [!code-cpp[concrt-log-filter#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_8.cpp)]  
  
 W tym przykładzie zapisuje następujące dane wyjściowe do konsoli.  
  
```Output  
error: This is a sample error message.  
```  
  
 W tym przykładzie powoduje również plik log.txt, który zawiera następujący tekst.  
  
```Output  
info: ===Logging started.=== 
warning: This is a sample warning message.  
error: This is a sample error message.  
info: ===Logging finished.=== 
```  
  
### <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `log-filter.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc dziennika filter.cpp**  
  
 [[Górnej](#top)]  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność środowiska wykonawczego — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

