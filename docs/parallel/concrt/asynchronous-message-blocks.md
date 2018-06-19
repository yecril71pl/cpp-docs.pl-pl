---
title: Bloki komunikatów asynchronicznych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5de4a9ed20e20c03f44f8b8d421a628f220099f7
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695034"
---
# <a name="asynchronous-message-blocks"></a>Bloki komunikatów asynchronicznych

Biblioteki agentów zawiera kilka typów bloku komunikatów, które umożliwiają propagację wiadomości między składnikami aplikacji w sposób wątkowo. Te typy bloku komunikatów są często używane z różnymi procedury przekazywania wiadomości, takie jak [concurrency::send](reference/concurrency-namespace-functions.md#send), [concurrency::asend](reference/concurrency-namespace-functions.md#asend), [concurrency::receive](reference/concurrency-namespace-functions.md#receive), i [concurrency::try_receive](reference/concurrency-namespace-functions.md#try_receive). Aby uzyskać więcej informacji o komunikacie przekazywanie procedur, które są zdefiniowane przez bibliotekę agentów, zobacz [funkcji przekazywania wiadomości](../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="top"></a> Sekcje  
 Ten temat zawiera następujące sekcje:  
  
- [Źródła i obiekty docelowe](#sources_and_targets)  
  
- [Propagacja komunikatów](#propagation)  
  
- [Przegląd typów bloku komunikatów](#overview)  
  
- [Klasa unbounded_buffer](#unbounded_buffer)  
  
- [overwrite_buffer, klasa](#overwrite_buffer)  
  
- [single_assignment, klasa](#single_assignment)  
  
- [call, klasa](#call)  
  
- [transformer, klasa](#transformer)  
  
- [choice, klasa](#choice)  
  
- [sprzężenia i multitype_join — klasy](#join)  
  
- [timer, klasa](#timer)  
  
- [Filtrowanie wiadomości](#filtering)  
  
- [Zastrzeżenie wiadomości](#reservation)  
  
##  <a name="sources_and_targets"></a> Źródła i obiekty docelowe  
 Źródła i obiekty docelowe są dwie ważne uczestnikami przekazywania komunikatów. A *źródła* oznacza punkt końcowy komunikacji, który wysyła wiadomości. A *docelowej* oznacza punkt końcowy komunikacji, który odbiera komunikaty. Można potraktować źródła jako punktu końcowego, który można odczytywać i obiekt docelowy jako punktu końcowego, który można zapisać. Aplikacje źródeł i obiektów docelowych jednocześnie połączyć się z formularza *sieciami wiadomości*.  
  
 Biblioteki agentów używa dwóch klas abstrakcyjnych do reprezentowania źródeł i elementy docelowe: [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) i [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md). Blok komunikatów typy tej czynności, jak źródeł pochodzi od `ISource`; bloku komunikatów typy tej czynności jako obiekty docelowe pochodzi od `ITarget`. Blok komunikatów typów tej czynności jako źródła, a elementy docelowe pochodzi z obu `ISource` i `ITarget`.  
  
 [[Górnej](#top)]  
  
##  <a name="propagation"></a> Propagacja komunikatów  
 *Komunikat propagacji* polega na wysyłanie wiadomości z jednego elementu na inny. Po bloku komunikatów wiadomości, go zaakceptować, odrzucić lub odroczyć tę wiadomość. Każdy typ bloku komunikatów przechowuje i przesyła wiadomości na różne sposoby. Na przykład `unbounded_buffer` klasy przechowuje nieograniczoną liczbę wiadomości, `overwrite_buffer` klasy przechowuje pojedynczej wiadomości w czasie, a klasy transformatora przechowuje zmienionych wersji każdego komunikatu. Te typy bloku komunikatów są opisane bardziej szczegółowo w dalszej części tego dokumentu.  
  
 Kiedy blok komunikatów akceptuje wiadomości, umożliwia opcjonalnie wykonywania pracy i, jeśli blok komunikatów jest źródłem, przekazać komunikat wynikowy do innego członka sieci. Blok komunikatów można użyć funkcji filtru, aby odrzucić wiadomości, które chcesz otrzymywać. Filtry są opisane bardziej szczegółowo w dalszej części tego tematu, w sekcji [filtrowania wiadomości](#filtering). Blok komunikatów, który odłoży wiadomość można zarezerwować tej wiadomości i pobrać go później. Zastrzeżenie wiadomości jest opisany bardziej szczegółowo w dalszej części tego tematu, w sekcji [rezerwacji komunikat](#reservation).  
  
 Biblioteki agentów włącza bloki komunikatów, aby asynchronicznie lub synchronicznie przekazywania wiadomości. Gdy przekazujesz komunikat dla bloku komunikatów synchronicznie, na przykład za pomocą `send` funkcji środowiska uruchomieniowego blokuje bieżącego kontekstu do momentu blok docelowy akceptuje lub odrzuca komunikat. Gdy przekazujesz komunikat dla bloku komunikatów asynchronicznie, na przykład za pomocą `asend` funkcji środowiska uruchomieniowego oferty komunikatów do obiektu docelowego, a jeśli element docelowy akceptuje wiadomości, środowisko uruchomieniowe planuje zadanie asynchroniczne, który rozprzestrzenia się komunikat odbiorcy. Za pomocą zadania lekkie środowisko uruchomieniowe propaguje wiadomości w sposób współpracy. Aby uzyskać więcej informacji na temat zadań lekkich, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  

 Aplikacje łączenia źródeł i obiekty docelowe do formularza sieci do obsługi komunikatów. Zazwyczaj połączyć sieci i wywołanie `send` lub `asend` do przekazywania danych do sieci. Aby połączyć źródła bloku komunikatów do obiektu docelowego, należy wywołać [concurrency::ISource::link_target](reference/isource-class.md#link_target) metody. Aby odłączyć bloku źródłowego z obiektu docelowego, należy wywołać [concurrency::ISource::unlink_target](reference/isource-class.md#unlink_target) metody. Aby odłączyć bloku źródłowego wszystkie elementy docelowe, należy wywołać [concurrency::ISource::unlink_targets](reference/isource-class.md#unlink_targets) metody. Gdy jeden z typów bloku komunikatów wstępnie zdefiniowanych pozostawia zakresu lub zostanie zniszczony automatycznego wyłączania się z bloków docelowej. Niektóre typy bloku komunikatów Ogranicz maksymalną liczbę elementów docelowych, które można zapisać. W poniższej sekcji opisano ograniczenia, które dotyczą typów bloku komunikatów wstępnie zdefiniowane.  
  
 [[Górnej](#top)]  
  
##  <a name="overview"></a> Przegląd typów bloku komunikatów  
 W poniższej tabeli opisano krótko roli typów ważne bloku komunikatów.  
  
 [unbounded_buffer](#unbounded_buffer)  
 Przechowuje kolejki wiadomości.  
  
 [overwrite_buffer](#overwrite_buffer)  
 Przechowuje jeden komunikat, który można zapisywać i odczytywać wiele razy.  
  
 [single_assignment](#single_assignment)  
 Przechowuje jeden komunikat, który może zapisywać jeden raz i odczytywać wiele razy.  
  
 [Wywołania](#call)  
 Wykonuje pracę po otrzymaniu komunikatu.  
  
 [transformer](#transformer)  
 Wykonuje pracę, gdy odbiera dane i wysyła wynikiem tej pracy do innego bloku docelowego. `transformer` Klasa może działać na różnych danych wejściowych i typy danych wyjściowych.  
  
 [Wybór](#choice)  
 Wybiera pierwszy komunikat dostępne z zestawu źródeł.  
  
 [sprzężenia i multitype sprzężenia](#join)  
 Poczekaj, aż wszystkie komunikaty odebrania z zestawu źródeł, a następnie połączenie komunikaty w jednej wiadomości dla innego bloku komunikatów.  
  
 [Czasomierz](#timer)  
 Wysyła komunikat do bloku docelowego w regularnych odstępach czasu.  
  
 Te typy bloku komunikatów charakteryzują się innymi cechami, które były przydatne w różnych sytuacjach. Poniżej przedstawiono czynniki:  
  
- *Typ propagacji*: Określa, czy blok komunikatów działa jako źródło danych i/lub odbiornika danych.  
  
- *Porządkowanie wiadomości*: Określa, czy blok komunikatów przechowuje kolejności, w którym są wysyłane lub odbierane wiadomości. Każdy typ bloku komunikatów wstępnie zdefiniowanych przechowuje kolejności, w którym wysyła i odbiera komunikaty.  
  
- *Liczba źródła*: Maksymalna liczba źródeł, które mogą odczytywać bloku komunikatów.  
  
- *Docelowa liczba*: Maksymalna liczba elementów docelowych, które można zapisać bloku komunikatów.  
  
 W poniższej tabeli przedstawiono, jak te cechy odnoszą się do różnych typów bloku komunikatów.  
  
|Typ bloku komunikatów|Typ propagacji (źródłowego, docelowego lub obu)|Komunikat porządkowanie (zamówione lub Unordered)|Licznik źródłowego|Docelowa liczba|  
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|  
|`unbounded_buffer`|Zarówno|uporządkowane|bez ograniczeń|bez ograniczeń|  
|`overwrite_buffer`|Zarówno|uporządkowane|bez ograniczeń|bez ograniczeń|  
|`single_assignment`|Zarówno|uporządkowane|bez ograniczeń|bez ograniczeń|  
|`call`|docelowy|uporządkowane|bez ograniczeń|Nie dotyczy|  
|`transformer`|Zarówno|uporządkowane|bez ograniczeń|1|  
|`choice`|Zarówno|uporządkowane|10|1|  
|`join`|Zarówno|uporządkowane|bez ograniczeń|1|  
|`multitype_join`|Zarówno|uporządkowane|10|1|  
|`timer`|Źródło|Nie dotyczy|Nie dotyczy|1|  
  
 W poniższych sekcjach opisano typy bloku komunikatów bardziej szczegółowo.  
  
 [[Górnej](#top)]  
  
##  <a name="unbounded_buffer"></a> Klasa unbounded_buffer  
 [Concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) klasa reprezentuje ogólnego przeznaczenia asynchroniczne struktury obsługi wiadomości. Ta klasa przechowuje pierwszy w pierwszej FIFO kolejki komunikatów, które mogą być zapisywane wiele źródeł lub odczytywane przez wiele obiektów docelowych. Jeśli element docelowy odbiera komunikat z `unbounded_buffer` obiektu, że wiadomość zostanie usunięta z kolejki wiadomości. W związku z tym mimo że `unbounded_buffer` obiekt może mieć wielu elementów docelowych, tylko jeden obiekt docelowy będzie otrzymywać każdego komunikatu. `unbounded_buffer` Klasy jest przydatne, gdy chcesz przekazać wiele komunikatów do innego składnika i składnik ten musi otrzymać każdy komunikat.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób pracy z podstawowej struktury `unbounded_buffer` klasy. W tym przykładzie wysyła trzy wartości `unbounded_buffer` obiektów i odczytuje wartości z kopii tego samego obiektu.  
  
 [!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]  
  
 Ten przykład generuje następujące wyniki:  
  
```Output  
334455  
```  
  
 Pełny przykład przedstawiający sposób użycia `unbounded_buffer` , zobacz [porady: Implementowanie różnych wzorców producent — konsument](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).  
  
 [[Górnej](#top)]  
  
##  <a name="overwrite_buffer"></a> Klasa overwrite_buffer  
 [Concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) podobny klasy `unbounded_buffer` klasy, z wyjątkiem `overwrite_buffer` obiekt przechowuje tylko jeden komunikat. Ponadto, gdy element docelowy odbiera komunikat z `overwrite_buffer` obiekt ten komunikat nie zostanie usunięta z buforu. W związku z tym wiele elementów docelowych odbierać kopia wiadomości.  
  
 `overwrite_buffer` Klasy jest przydatne, gdy chcesz przekazać wiele komunikatów do innego składnika, ale ten składnik wymaga tylko najnowsze wartość. Ta klasa jest również przydatne, gdy chcesz wysyłać wiadomości do wielu składników.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób pracy z podstawowej struktury `overwrite_buffer` klasy. W tym przykładzie wysyła trzy wartości `overwrite _buffer` obiektów i odczytuje bieżącą wartość z tego samego obiektu trzy razy. W tym przykładzie jest podobny do przykład `unbounded_buffer` klasy. Jednak `overwrite_buffer` klasy przechowuje tylko jeden komunikat. Ponadto środowisko uruchomieniowe nie usuwa komunikat z `overwrite_buffer` obiektu po jest do odczytu.  
  
 [!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]  
  
 Ten przykład generuje następujące wyniki:  
  
```Output  
555555  
```  
  
 Pełny przykład przedstawiający sposób użycia `overwrite_buffer` , zobacz [porady: Implementowanie różnych wzorców producent — konsument](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).  
  
 [[Górnej](#top)]  
  
##  <a name="single_assignment"></a> Klasa single_assignment  
 [Concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) podobny klasy `overwrite_buffer` klasy, z wyjątkiem `single_assignment` obiektu można zapisać tylko raz. Podobnie jak `overwrite_buffer` klasy, gdy element docelowy otrzyma komunikat z `single_assignment` obiekt ten komunikat nie zostanie usunięty z tego obiektu. W związku z tym wiele elementów docelowych odbierać kopia wiadomości. `single_assignment` Klasy jest przydatne, gdy chcesz wysyłać wiadomości jeden do wielu składników.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób pracy z podstawowej struktury `single_assignment` klasy. W tym przykładzie wysyła trzy wartości `single_assignment` obiektów i odczytuje bieżącą wartość z tego samego obiektu trzy razy. W tym przykładzie jest podobny do przykład `overwrite_buffer` klasy. Mimo że zarówno `overwrite_buffer` i `single_assignment` klasy przechowywane w pojedynczym komunikacie `single_assignment` klasy można zapisać tylko raz.  
  
 [!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]  
  
 Ten przykład generuje następujące wyniki:  
  
```Output  
333333  
```  
  
 Pełny przykład przedstawiający sposób użycia `single_assignment` , zobacz [wskazówki: Wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md).  
  
 [[Górnej](#top)]  
  
##  <a name="call"></a> Call — klasa  
 [Concurrency::call](../../parallel/concrt/reference/call-class.md) klasa działa jako odbiornik komunikat, który wykonuje funkcje pracy po odebraniu danych. Ta funkcja pracy może być wyrażenie lambda, obiekt funkcji lub wskaźnik funkcji. A `call` obiektu zachowuje się inaczej niż wywołanie zwykłej funkcji, ponieważ działa równolegle z innymi składnikami, które wysyłają do niego wiadomości. Jeśli `call` obiekt wykonuje pracę po odebraniu wiadomości, dodaje tej wiadomości do kolejki. Każdy `call` obiektu procesów w kolejce wiadomości w kolejności, w którym są odbierane.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób pracy z podstawowej struktury `call` klasy. Ten przykład tworzy `call` obiekt, który wyświetla wartości do konsoli. Przykład wysyła następnie trzy wartości `call` obiektu. Ponieważ `call` obiektu przetwarza wiadomości w oddzielnym wątku, w tym przykładzie użyto również zmienną licznika i [zdarzeń](../../parallel/concrt/reference/event-class.md) obiekt, aby upewnić się, że `call` obiektu przetwarza wszystkie komunikaty przed `wmain` Funkcja.  
  
 [!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]  
  
 Ten przykład generuje następujące wyniki:  
  
```Output  
334455  
```  
  
 Pełny przykład przedstawiający sposób użycia `call` , zobacz [porady: Podaj funkcji pracy do wywoływania oraz klasy transformatora](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md).  
  
 [[Górnej](#top)]  
  
##  <a name="transformer"></a> Klasa transformatora  
 [Concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) klasa działa jako odbiornik komunikat, a nadawcy wiadomości. `transformer` Podobny klasy `call` klasy, ponieważ wykonuje funkcji zdefiniowanej przez użytkownika pracy po odebraniu danych. Jednak `transformer` klasy wysyła również wynik funkcji pracy z obiektami odbiornika. Podobnie jak `call` obiektu, `transformer` obiektu działa równolegle z innymi składnikami, które wysyłają do niego wiadomości. Jeśli `transformer` obiekt wykonuje pracę po odebraniu wiadomości, dodaje tej wiadomości do kolejki. Każdy `transformer` obiektu przetwarza jego wiadomości w kolejce w kolejności, w którym są odbierane.  
  
 `transformer` Klasy wysyła komunikatu do jednego obiektu docelowego. Jeśli ustawisz `_PTarget` parametru w Konstruktorze do `NULL`, można później Określ cel, wywołując [concurrency::link_target](reference/source-block-class.md#link_target) metody.  
  
 W przeciwieństwie do wszystkich innych komunikatów asynchronicznych block typów udostępnianych przez biblioteki agentów `transformer` klasy może działać na różnych danych wejściowych i typy danych wyjściowych. Ta możliwość przekształcania danych z jednego typu, powoduje, że inny `transformer` klasy głównym składnikiem wiele równoczesnych sieci. Ponadto można dodać więcej szczegółowych funkcji równoległe w funkcji pracy `transformer` obiektu.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób pracy z podstawowej struktury `transformer` klasy. Ten przykład tworzy `transformer` obiekt, czy dane wejściowe wielokrotności każdego `int` wartości przez 0,33, aby można było utworzyć `double` wartość jako dane wyjściowe. Przykład otrzyma przekształcone wartości z tej samej `transformer` obiektu i wyświetla je w konsoli.  
  
 [!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]  
  
 Ten przykład generuje następujące wyniki:  
  
```Output  
10.8914.5218.15  
```  
  
 Pełny przykład przedstawiający sposób użycia `transformer` , zobacz [porady: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).  
  
 [[Górnej](#top)]  
  
##  <a name="choice"></a> Klasa wyboru  
 [Concurrency::choice](../../parallel/concrt/reference/choice-class.md) klasy wybiera pierwszą wiadomością dostępne z zestawu źródeł. `choice` Klasa reprezentuje mechanizm przepływu sterowania zamiast mechanizm przepływu danych (temat [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) opisano różnice między przepływu danych i przepływu sterowania).  
  
 Odczyt z obiektu wybór podobny do wywoływania funkcji Windows API `WaitForMultipleObjects` po ma `bWaitAll` ustawiona `FALSE`. Jednak `choice` klasy wiąże danych sam zamiast zdarzeń do obiektu zewnętrznego synchronizacji.  
  

 Zazwyczaj `choice` klasy razem z [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkcji do kierowania przepływu sterowania w aplikacji. Użyj `choice` klasy, gdy trzeba wybrać między buforów komunikatów, które mają różne typy. Użyj `single_assignment` klasy, gdy trzeba wybrać między buforów komunikatów, które mają ten sam typ.  

  
 Kolejność, w którym możesz połączyć źródła `choice` obiektu jest ważne, ponieważ można określić, jaki komunikat jest zaznaczone. Na przykład rozważmy przypadek, gdzie można połączyć wielu buforów komunikatów, które już zawierają komunikat do `choice` obiektu. `choice` Obiektu wybiera wiadomości z pierwszego źródła, która jest połączona. Po dołączeniu wszystkich źródeł `choice` obiektu zachowuje kolejności, w której każde źródło odbiera komunikat.  
  
### <a name="example"></a>Przykład  

 W poniższym przykładzie pokazano sposób pracy z podstawowej struktury `choice` klasy. W tym przykładzie użyto [concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice) funkcja służąca do tworzenia `choice` obiekt, który wybiera spośród trzech bloki komunikatów. Przykład następnie oblicza różne numery Fibonacci i przechowuje każdy wynik w bloku inny komunikat. Przykład następnie drukuje do konsoli komunikat, który jest oparta na operację, która najpierw zostało zakończone.  

  
 [!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe:  
  
```Output  
fib35 received its value first. Result = 9227465  
```  
  
 Ponieważ zadania, które oblicza 35<sup>th</sup> numer Fibonacci nie jest gwarantowana zakończy pierwsza, może różnić się w tym przykładzie danych wyjściowych.  
  

 W tym przykładzie użyto [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytm obliczania numerów Fibonacci równolegle. Aby uzyskać więcej informacji na temat `parallel_invoke`, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).  
  
 Pełny przykład przedstawiający sposób użycia `choice` , zobacz [jak: Wybieranie między zadania wykonane](../../parallel/concrt/how-to-select-among-completed-tasks.md).  
  
 [[Górnej](#top)]  
  
##  <a name="join"></a> sprzężenia i multitype_join — klasy  
 [Concurrency::join](../../parallel/concrt/reference/join-class.md) i [concurrency::multitype_join](../../parallel/concrt/reference/multitype-join-class.md) klasy pozwalają oczekiwania dla każdego elementu członkowskiego zestawu źródeł otrzymywać wiadomość. `join` Klasa działa na obiekty źródła, które mają wspólny typ komunikatu. `multitype_join` Klasa działa na obiekty źródła, które mogą mieć różne rodzaje komunikatów.  
  
 Odczytywanie z `join` lub `multitype_join` obiektu podobny do wywoływania funkcji Windows API `WaitForMultipleObjects` po ma `bWaitAll` ustawiona `TRUE`. Jednakże, podobnie jak `choice` obiektu `join` i `multitype_join` obiektów używany mechanizm zdarzeń, który wiąże danych sam zamiast zdarzeń do obiektu zewnętrznego synchronizacji.  
  
 Odczytywanie z `join` obiektu tworzy std::[wektor](../../standard-library/vector-class.md) obiektu. Odczytywanie z `multitype_join` obiektu tworzy std::[krotki](../../standard-library/tuple-class.md) obiektu. Elementy wyświetlane w tych obiektów w tej samej kolejności, w ich odpowiednich bufory źródła są połączone z `join` lub `multitype_join` obiektu. Ponieważ kolejność, w którym możesz połączyć źródła buforów do `join` lub `multitype_join` obiekt jest skojarzony z kolejność elementów w wynikowym `vector` lub `tuple` obiektu, zaleca się nie odłączenie istniejących bufor źródłowy z sprzężenia. W ten sposób może spowodować zachowanie nieokreślony.  
  
### <a name="greedy-versus-non-greedy-joins"></a>Złączenia zachłanne vs. niezachłanne  
 `join` i `multitype_join` klasy obsługuje pojęcie intensywnie i niezachłanne sprzężenia. A *zachłanne złączenia* akceptuje wiadomość z każdego z jego źródła jako wiadomości staną się dostępne, dopóki wszystkie wiadomości są dostępne. A *niezachłanne złączenia* odbiera komunikaty w dwóch fazach. Po pierwsze niezachłanne złączenia oczekuje, aż jej jest oferowany komunikat z każdej z jej źródeł. Drugie gdy wszystkie komunikaty źródła są dostępne, niezachłanne złączenia spróbuje zarezerwować te wiadomości. Jeśli można go zarezerwować każdy komunikat, wykorzystuje wszystkie komunikaty i propaguje je do jego obiektu docelowego. W przeciwnym razie zwalnia, ani anuluje rezerwacji wiadomość i ponownie czeka na każdym źródle w celu komunikat o błędzie.  
  
 Zachłanne sprzężenia wykonać lepszą wydajność niż złączenia niezachłanne, ponieważ akceptują wiadomości natychmiast. Jednak w rzadkich przypadkach intensywnie sprzężeń może prowadzić do zakleszczenia. Użyj niezachłanne złączenia, jeśli masz wiele sprzężenia, zawierające co najmniej jeden obiekt udostępnionego źródła.  
  
### <a name="example"></a>Przykład  

 W poniższym przykładzie pokazano sposób pracy z podstawowej struktury `join` klasy. W tym przykładzie użyto [concurrency::make_join](reference/concurrency-namespace-functions.md#make_join) funkcja służąca do tworzenia `join` obiekt, który odbiera z trzech `single_assignment` obiektów. W tym przykładzie oblicza różne numery Fibonacci, przechowuje każdy wynik w innej `single_assignment` obiektu, a następnie drukuje do konsoli każdego powoduje, że `join` obiekt blokad. W tym przykładzie jest podobny do przykład `choice` klasy, z wyjątkiem `join` klasy czeka na wszystkie bloki komunikatów źródła można odebrać wiadomości.  
  
 [!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]  
  
 Ten przykład generuje następujące wyniki:  
  
```Output  
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008  
```  

 W tym przykładzie użyto [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytm obliczania numerów Fibonacci równolegle. Aby uzyskać więcej informacji na temat `parallel_invoke`, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).  
  
 Zakończenie przykłady, które pokazują, jak używać `join` , zobacz [porady: Wybierz między zadania wykonane](../../parallel/concrt/how-to-select-among-completed-tasks.md) i [wskazówki: przy użyciu w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).  
  
 [[Górnej](#top)]  
  
##  <a name="timer"></a> Klasa czasomierza  
 Współbieżność::[klasa czasomierza](../../parallel/concrt/reference/timer-class.md) działa jako źródło komunikatu. A `timer` obiekt wysyła komunikat do obiektu docelowego, po upływie określonego czasu. `timer` Klasy jest przydatne, gdy musi opóźnienie wysyłania komunikatu lub chcesz wysłać komunikatu w regularnych odstępach czasu.  
  

 `timer` Klasy wysyła komunikatu do tylko jeden element docelowy. Jeśli ustawisz `_PTarget` parametru w Konstruktorze do `NULL`, można później Określ cel, wywołując [concurrency::ISource::link_target](reference/source-block-class.md#link_target) metody.  

  
 A `timer` obiektu można powtórzyć lub niepowtarzającymi. Aby utworzyć identycznych czasomierza, należy przekazać `true` dla `_Repeating` parametr podczas wywoływania konstruktora. W przeciwnym razie przekazania `false` dla `_Repeating` parametr w celu utworzenia niepowtarzającymi czasomierza. Jeśli czasomierz jest powtarzane, wysyła tę samą wiadomość do jego obiektu docelowego po każdym interwale.  
  
 Biblioteki agentów tworzy `timer` obiektów w stanie-started. Aby uruchomić obiekt czasomierza, należy wywołać [concurrency::timer::start](reference/timer-class.md#start) metody. Aby zatrzymać `timer` obiektów, zniszczenie obiektu lub wywołanie [concurrency::timer::stop](reference/timer-class.md#stop) metody. Aby wstrzymać identycznych czasomierza, należy wywołać [concurrency::timer::pause](reference/timer-class.md#pause) metody.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób pracy z podstawowej struktury `timer` klasy. W przykładzie użyto `timer` i `call` obiektów do raportu postępu długotrwałej operacji.  
  
 [!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe:  
  
```Output  
Computing fib(42)..................................................result is 267914296  
```  
  
 Pełny przykład przedstawiający sposób użycia `timer` , zobacz [porady: wysyłanie komunikatu w regularnych odstępach czasu](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md).  
  
 [[Górnej](#top)]  
  
##  <a name="filtering"></a> Filtrowanie wiadomości  
 Podczas tworzenia obiektu bloku komunikatów, możesz podać *funkcja filtrowania* Określa, czy blok komunikatów akceptuje lub odrzuca komunikat. Funkcja filtru jest to wygodny sposób, aby zagwarantować, że blok komunikatów odbiera tylko niektóre wartości.  
  
 Poniższy przykład przedstawia sposób tworzenia `unbounded_buffer` obiekt, który korzysta z funkcji filtr do akceptowania tylko liczby parzyste. `unbounded_buffer` Obiektu odrzuca nieparzystej liczby i dlatego nie propaguje nieparzystej liczby jego bloków docelowej.  
  
 [!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]  
  
 Ten przykład generuje następujące wyniki:  
  
```Output  
0 2 4 6 8  
```  
  
 Funkcja filtru może być funkcją lambda, wskaźnik funkcji lub obiekt funkcji. Każda funkcja filtru przyjmuje jeden z następujących form.  
  
```Output  
bool (T)  
bool (T const &)  
```  
  
 Aby usunąć niepotrzebne kopiowanie danych, należy użyć drugiej formy w przypadku typu agregacji, które są propagowane przez wartość.  
  
 Komunikat filtrowania obsługuje *przepływu danych* modelu programowania, w którym składniki wykonać obliczenia po odebraniu danych. Przykłady używające funkcji filtr do sterowania przepływem danych w sieci przekazywanie komunikatów, zobacz [porady: Użyj filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md), [wskazówki: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md), i [ Wskazówki: Tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 [[Górnej](#top)]  
  
##  <a name="reservation"></a> Zastrzeżenie wiadomości  
 *Komunikat rezerwacji* umożliwia bloku komunikatów do zarezerwowania komunikat do późniejszego użycia. Zazwyczaj rezerwacji komunikat nie jest używana bezpośrednio. Jednak wiadomości opis zastrzeżenia może ułatwić lepsze zrozumienie zachowania niektórych typów bloku komunikatów wstępnie zdefiniowane.  
  
 Należy wziąć pod uwagę niezachłanne i intensywnie sprzężenia. Oba te Użyj rezerwacji komunikat do zarezerwowania wiadomości do późniejszego użycia. Opisane wcześniej, niezachłanne złączenia odbiera komunikaty w dwóch fazach. W pierwszej fazie niezachłanne `join` oczekuje obiektu dla każdego z jego źródła można odebrać wiadomości. Niezachłanne złączenia podejmuje próbę zarezerwować te wiadomości. Jeśli można go zarezerwować każdy komunikat, wykorzystuje wszystkie komunikaty i propaguje je do jego obiektu docelowego. W przeciwnym razie zwalnia, ani anuluje rezerwacji wiadomość i ponownie czeka na każdym źródle w celu komunikat o błędzie.  
  
 Zachłanne złączenia również odczytuje komunikaty wejściowe z różnych źródeł, używa rezerwacji komunikat do odczytu dodatkowych komunikatów podczas oczekiwania na komunikat z każdego źródła. Rozważmy na przykład zachłanne złączenia, który odbiera komunikaty z bloki komunikatów `A` i `B`. Jeśli zachłanne złączenia otrzymuje dwa komunikaty z B, ale jeszcze nie otrzymał komunikat z `A`, zachłanne złączenia zapisuje komunikat Unikatowy identyfikator to drugi komunikat z `B`. Gdy zachłanne złączenia otrzyma komunikat z `A` i propaguje tych wiadomości, używa identyfikator zapisanego komunikatu czy drugi komunikat z `B` jest nadal dostępny.  
  
 Podczas implementowania własnych typów bloku niestandardowy komunikat, można użyć rezerwacji wiadomości. Na przykład o sposobach tworzenia komunikat niestandardowy typ bloku, zobacz [wskazówki: Tworzenie niestandardowego bloku komunikatów](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md).  
  
 [[Górnej](#top)]  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)

