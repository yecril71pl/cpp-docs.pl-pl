---
title: Bloki komunikatów asynchronicznych
ms.date: 11/04/2016
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
ms.openlocfilehash: 6697bdd296a3c71f03bc22986efa47dd586d5d9e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217912"
---
# <a name="asynchronous-message-blocks"></a>Bloki komunikatów asynchronicznych

Biblioteka agenci zawiera kilka typów bloków komunikatów, które umożliwiają propagowanie komunikatów między składnikami aplikacji w sposób bezpieczny dla wątków. Te typy bloków komunikatów są często używane z różnymi procedurami przekazywania komunikatów, takimi jak [concurrency:: Send](reference/concurrency-namespace-functions.md#send), [concurrency:: asend](reference/concurrency-namespace-functions.md#asend), [concurrency:: receive](reference/concurrency-namespace-functions.md#receive)i [concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive). Aby uzyskać więcej informacji na temat procedur przekazywania komunikatów, które są zdefiniowane przez bibliotekę agentów, zobacz [funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md).

## <a name="sections"></a><a name="top"></a>Poszczególne

Ten temat zawiera następujące sekcje:

- [Źródła i obiekty docelowe](#sources_and_targets)

- [Propagowanie komunikatów](#propagation)

- [Przegląd typów bloku komunikatów](#overview)

- [Klasa unbounded_buffer](#unbounded_buffer)

- [Klasa overwrite_buffer](#overwrite_buffer)

- [Klasa single_assignment](#single_assignment)

- [Call, Klasa](#call)

- [transformator — Klasa](#transformer)

- [Choice — Klasa](#choice)

- [Klasy Join i multitype_join](#join)

- [Timer — Klasa](#timer)

- [Filtrowanie komunikatów](#filtering)

- [Rezerwacja komunikatów](#reservation)

## <a name="sources-and-targets"></a><a name="sources_and_targets"></a>Źródła i elementy docelowe

Źródła i cele są dwoma ważnymi uczestnikami przesyłania komunikatów. *Źródło* odwołuje się do punktu końcowego komunikacji, która wysyła komunikaty. *Obiekt docelowy* odwołuje się do punktu końcowego komunikacji, który odbiera komunikaty. Źródło można traktować jako punkt końcowy odczytywany z i obiekt docelowy jako punkt końcowy, w którym piszesz. Aplikacje nawiązują połączenie ze źródłami i obiektami docelowymi w celu tworzenia *sieci komunikatów*.

Biblioteka agentów używa dwóch klas abstrakcyjnych do reprezentowania źródeł i elementów docelowych: [concurrency:: ISource](../../parallel/concrt/reference/isource-class.md) i [concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md). Typy bloku komunikatów, które działają jako źródła pochodzą z `ISource` ; typy bloku komunikatów, które działają jako elementy docelowe pochodne `ITarget` . Typy bloku komunikatów, które działają jako źródła i obiekty docelowe, pochodzą z obu `ISource` i `ITarget` .

[[Top](#top)]

## <a name="message-propagation"></a><a name="propagation"></a>Propagowanie komunikatów

*Propagowanie komunikatów* jest aktem wysyłania komunikatu z jednego składnika do drugiego. Gdy w bloku komunikatów jest oferowany komunikat, może on zaakceptować, odrzucić lub odłożyć ten komunikat. Każdy typ bloku komunikatów przechowuje i przesyła komunikaty na różne sposoby. Na przykład `unbounded_buffer` Klasa przechowuje nieograniczoną liczbę komunikatów, `overwrite_buffer` Klasa przechowuje pojedynczą wiadomość w danym momencie, a Klasa transformatora przechowuje zmodyfikowaną wersję poszczególnych komunikatów. Te typy bloków komunikatów są opisane bardziej szczegółowo w dalszej części tego dokumentu.

Gdy blok komunikatów akceptuje komunikat, może opcjonalnie wykonać prace i, jeśli blok komunikatów jest źródłem, przekazać komunikat uzyskany do innego elementu członkowskiego sieci. Blok komunikatów może używać funkcji filtru w celu odrzucania komunikatów, które nie mają być odbierane. Filtry są opisane bardziej szczegółowo w dalszej części tego tematu, w sekcji [filtrowanie komunikatów](#filtering). Blok komunikatów, który opóźnia komunikat, może zarezerwować ten komunikat i użyć go później. Rezerwacja komunikatów została opisana szczegółowo w dalszej części tego tematu w sekcji [rezerwacja komunikatu](#reservation).

Biblioteka agenci umożliwia blokowanie komunikatów asynchronicznie lub synchronicznie. Gdy przekazujesz komunikat synchronicznie do bloku komunikatów, na przykład przy użyciu `send` funkcji, środowisko uruchomieniowe blokuje bieżący kontekst do momentu zaakceptowania lub odrzucenia komunikatu przez blok docelowy. W przypadku przekazywania komunikatu do bloku komunikatów asynchronicznie, na przykład przy użyciu `asend` funkcji, środowisko uruchomieniowe oferuje komunikat do obiektu docelowego, a jeśli obiekt docelowy akceptuje komunikat, środowisko uruchomieniowe planuje asynchroniczne zadanie, które propaguje komunikat do odbiorcy. Środowisko uruchomieniowe używa uproszczonych zadań do propagowania komunikatów w sposób współdziałania. Aby uzyskać więcej informacji na temat uproszczonych zadań, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Aplikacje nawiązują połączenie ze źródłami i obiektami docelowymi w celu tworzenia sieci komunikatów. Zwykle połączenie sieci i wywołanie `send` lub `asend` przekazanie danych do sieci. Aby połączyć blok komunikatów źródłowych z obiektem docelowym, wywołaj metodę [concurrency:: ISource:: link_target](reference/isource-class.md#link_target) . Aby odłączyć blok źródłowy od obiektu docelowego, wywołaj metodę [concurrency:: ISource:: unlink_target](reference/isource-class.md#unlink_target) . Aby odłączyć blok źródłowy ze wszystkich jego obiektów docelowych, wywołaj metodę [concurrency:: ISource:: unlink_targets](reference/isource-class.md#unlink_targets) . Gdy jeden z wstępnie zdefiniowanych typów bloku komunikatów pozostawia zakres lub jest niszczony, automatycznie rozłącza się z dowolnymi blokami docelowymi. Niektóre typy bloku komunikatów ograniczają maksymalną liczbę elementów docelowych, do których mogą pisać. W poniższej sekcji opisano ograniczenia dotyczące wstępnie zdefiniowanych typów bloków komunikatów.

[[Top](#top)]

## <a name="overview-of-message-block-types"></a><a name="overview"></a>Przegląd typów bloku komunikatów

W poniższej tabeli krótko opisano rolę ważnych typów bloków komunikatów.

[unbounded_buffer](#unbounded_buffer)<br/>
Przechowuje kolejkę komunikatów.

[overwrite_buffer](#overwrite_buffer)<br/>
Przechowuje jeden komunikat, który może być zapisywany i odczytywany wiele razy.

[single_assignment](#single_assignment)<br/>
Przechowuje jeden komunikat, który można zapisać w jeden raz i odczytywać wiele razy.

[połączeń](#call)<br/>
Wykonuje działania po odebraniu komunikatu.

[Funkcja](#transformer)<br/>
Wykonuje zadanie po odebraniu danych i wysłaniu wyniku pracy do innego bloku docelowego. `transformer`Klasa może działać na różnych typach danych wejściowych i wyjściowych.

[Rozwiązanie](#choice)<br/>
Wybiera pierwszy dostępny komunikat z zestawu źródeł.

[sprzężenie i sprzężenie wielotypu](#join)<br/>
Poczekaj na odebranie wszystkich komunikatów z zestawu źródeł, a następnie połącz komunikaty w jeden komunikat dla innego bloku komunikatów.

[licz](#timer)<br/>
Wysyła komunikat do bloku docelowego w regularnych odstępach czasu.

Te typy bloków komunikatów mają różne cechy, które sprawiają, że są one przydatne w różnych sytuacjach. Oto niektóre z tych cech:

- *Typ propagacji*: czy blok komunikatów działa jako źródło danych, odbiorca danych lub oba te elementy.

- *Porządkowanie komunikatów*: czy blok komunikatów zachowuje pierwotną kolejność, w której wiadomości są wysyłane lub odbierane. Każdy wstępnie zdefiniowany typ bloku komunikatów zachowuje pierwotną kolejność, w której wysyła lub odbiera komunikaty.

- *Liczba źródeł*: Maksymalna liczba źródeł, z których może odczytywać blok komunikatów.

- *Liczba obiektów docelowych*: Maksymalna liczba elementów docelowych, do których może zapisywać blok komunikatów.

W poniższej tabeli przedstawiono, jak te charakterystyki odnoszą się do różnych typów bloku komunikatów.

|Typ bloku komunikatu|Typ propagacji (Źródło, cel lub oba)|Porządkowanie komunikatów (uporządkowane lub nieuporządkowane)|Liczba źródeł|Liczba elementów docelowych|
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|
|`unbounded_buffer`|Oba|Zamówione|Unbounded|Unbounded|
|`overwrite_buffer`|Oba|Zamówione|Unbounded|Unbounded|
|`single_assignment`|Oba|Zamówione|Unbounded|Unbounded|
|`call`|Cel|Zamówione|Unbounded|Nie dotyczy|
|`transformer`|Oba|Zamówione|Unbounded|1|
|`choice`|Oba|Zamówione|10|1|
|`join`|Oba|Zamówione|Unbounded|1|
|`multitype_join`|Oba|Zamówione|10|1|
|`timer`|Element źródłowy|Nie dotyczy|Nie dotyczy|1|

W poniższych sekcjach opisano typy bloków komunikatów bardziej szczegółowo.

[[Top](#top)]

## <a name="unbounded_buffer-class"></a><a name="unbounded_buffer"></a>Klasa unbounded_buffer

Klasa [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) reprezentuje strukturę asynchronicznej obsługi komunikatów ogólnego przeznaczenia. Ta klasa przechowuje kolejki w pierwszej kolejności (FIFO) komunikatów, które mogą być zapisywane przez wiele źródeł lub odczytywane przez wiele obiektów docelowych. Gdy obiekt docelowy otrzymuje komunikat z `unbounded_buffer` obiektu, ten komunikat zostanie usunięty z kolejki komunikatów. W związku z tym mimo że `unbounded_buffer` obiekt może mieć wiele obiektów docelowych, tylko jeden element docelowy otrzyma każdy komunikat. `unbounded_buffer`Klasa jest przydatna, gdy chcesz przekazać wiele komunikatów do innego składnika, a ten składnik musi odebrać każdy komunikat.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje podstawową strukturę sposobu pracy z `unbounded_buffer` klasą. Ten przykład wysyła trzy wartości do `unbounded_buffer` obiektu, a następnie odczytuje te wartości z powrotem z tego samego obiektu.

[!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]

Ten przykład generuje następujące wyniki:

```Output
334455
```

Aby zapoznać się z kompletnym przykładem, który pokazuje, jak korzystać z `unbounded_buffer` klasy, zobacz [How to: Implementuj różne wzorce producenta i konsumenta](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[[Top](#top)]

## <a name="overwrite_buffer-class"></a><a name="overwrite_buffer"></a>Klasa overwrite_buffer

Klasa [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) jest podobna do `unbounded_buffer` klasy, z tą różnicą, że `overwrite_buffer` obiekt przechowuje tylko jeden komunikat. Ponadto, gdy obiekt docelowy otrzymuje komunikat z `overwrite_buffer` obiektu, ten komunikat nie jest usuwany z bufora. W związku z tym wiele obiektów docelowych otrzymuje kopię wiadomości.

`overwrite_buffer`Klasa jest przydatna, gdy chcesz przekazać wiele komunikatów do innego składnika, ale ten składnik wymaga tylko najnowszej wartości. Ta klasa jest również przydatna, gdy chcesz emitować komunikat do wielu składników.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje podstawową strukturę sposobu pracy z `overwrite_buffer` klasą. Ten przykład wysyła trzy wartości do `overwrite _buffer` obiektu, a następnie odczytuje bieżącą wartość z tego samego obiektu trzykrotnie. Ten przykład jest podobny do przykładu dla `unbounded_buffer` klasy. Jednak `overwrite_buffer` Klasa przechowuje tylko jeden komunikat. Ponadto środowisko uruchomieniowe nie usuwa komunikatu z `overwrite_buffer` obiektu po jego odczytaniu.

[!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]

Ten przykład generuje następujące wyniki:

```Output
555555
```

Aby zapoznać się z kompletnym przykładem, który pokazuje, jak korzystać z `overwrite_buffer` klasy, zobacz [How to: Implementuj różne wzorce producenta i konsumenta](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[[Top](#top)]

## <a name="single_assignment-class"></a><a name="single_assignment"></a>Klasa single_assignment

Klasa [concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) jest podobna do `overwrite_buffer` klasy, z tą różnicą, że `single_assignment` obiekt może być zapisywana tylko raz. Podobnie jak `overwrite_buffer` Klasa, gdy obiekt docelowy otrzymuje komunikat z `single_assignment` obiektu, ten komunikat nie jest usuwany z tego obiektu. W związku z tym wiele obiektów docelowych otrzymuje kopię wiadomości. `single_assignment`Klasa jest przydatna, gdy chcesz emitować jeden komunikat do wielu składników.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje podstawową strukturę sposobu pracy z `single_assignment` klasą. Ten przykład wysyła trzy wartości do `single_assignment` obiektu, a następnie odczytuje bieżącą wartość z tego samego obiektu trzykrotnie. Ten przykład jest podobny do przykładu dla `overwrite_buffer` klasy. Chociaż obie `overwrite_buffer` klasy i `single_assignment` przechowują jeden komunikat, `single_assignment` Klasa może być zapisywana tylko jeden raz.

[!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]

Ten przykład generuje następujące wyniki:

```Output
333333
```

Aby zapoznać się z kompletnym przykładem, który pokazuje, jak używać `single_assignment` klasy, zobacz [Przewodnik: implementowanie przyszłych](../../parallel/concrt/walkthrough-implementing-futures.md).

[[Top](#top)]

## <a name="call-class"></a><a name="call"></a>Call, Klasa

Klasa [concurrency:: Call](../../parallel/concrt/reference/call-class.md) działa jako odbiorca komunikatu, który wykonuje funkcję służbową po odebraniu danych. Ta funkcja robocza może być wyrażeniem lambda, obiektem funkcji lub wskaźnikiem funkcji. `call`Obiekt zachowuje się inaczej niż zwykłe wywołanie funkcji, ponieważ działa równolegle z innymi składnikami, które wysyłają do niego komunikaty. Jeśli `call` obiekt wykonuje działanie, gdy odbierze komunikat, dodaje ten komunikat do kolejki. Każdy `call` obiekt przetwarza wiadomości w kolejce w kolejności, w której zostały odebrane.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje podstawową strukturę sposobu pracy z `call` klasą. Ten przykład tworzy `call` obiekt, który drukuje każdą wartość, którą otrzymuje do konsoli. Przykład wysyła następnie trzy wartości do `call` obiektu. Ponieważ `call` obiekt przetwarza komunikaty w osobnym wątku, w tym przykładzie używa również zmiennej licznika i obiektu [zdarzenia](../../parallel/concrt/reference/event-class.md) , aby upewnić się, że `call` obiekt przetwarza wszystkie komunikaty przed `wmain` zwróceniem przez funkcję.

[!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]

Ten przykład generuje następujące wyniki:

```Output
334455
```

Aby zapoznać się z kompletnym przykładem, który pokazuje, jak używać `call` klasy, zobacz [How to: zapewnianie funkcji pracy dla klas wywołań i transformatorów](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md).

[[Top](#top)]

## <a name="transformer-class"></a><a name="transformer"></a>transformator — Klasa

Klasa [concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) pełni rolę odbiorcy wiadomości i nadawcy wiadomości. `transformer`Klasa jest podobna do `call` klasy, ponieważ wykonuje funkcję roboczą zdefiniowaną przez użytkownika po odebraniu danych. Jednak `transformer` Klasa wysyła również wynik funkcji służbowej do obiektów odbiornika. Podobnie jak w przypadku obiektu `call` , `transformer` obiekt działa równolegle z innymi składnikami, które wysyłają do niego komunikaty. Jeśli `transformer` obiekt wykonuje działanie, gdy odbierze komunikat, dodaje ten komunikat do kolejki. Każdy `transformer` obiekt przetwarza komunikaty w kolejce w kolejności, w której zostały odebrane.

`transformer`Klasa wysyła wiadomość do jednego obiektu docelowego. W przypadku ustawienia `_PTarget` parametru w konstruktorze na `NULL` , można później określić obiekt docelowy przez wywołanie metody [concurrency:: link_target](reference/source-block-class.md#link_target) .

W przeciwieństwie do wszystkich innych typów bloku komunikatów asynchronicznych, które są dostarczane przez bibliotekę agentów, `transformer` Klasa może działać na różnych typach danych wejściowych i wyjściowych. Ta możliwość przekształcania danych z jednego typu na inny powoduje, że `transformer` Klasa jest kluczem składnika w wielu współbieżnych sieciach. Ponadto można dodać bardziej szczegółowe funkcje równoległe w funkcji służbowej `transformer` obiektu.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje podstawową strukturę sposobu pracy z `transformer` klasą. Ten przykład tworzy `transformer` obiekt, który ma wielokrotność każdej wartości wejściowej **`int`** przez 0,33 w celu utworzenia **`double`** wartości jako danych wyjściowych. Następnie przykład otrzymuje przekształcone wartości z tego samego `transformer` obiektu i drukuje je do konsoli.

[!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]

Ten przykład generuje następujące wyniki:

```Output
10.8914.5218.15
```

Aby zapoznać się z kompletnym przykładem, który pokazuje, jak używać `transformer` klasy, zobacz [How to: use Transformer w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

[[Top](#top)]

## <a name="choice-class"></a><a name="choice"></a>Choice — Klasa

Klasa [concurrency:: Choice](../../parallel/concrt/reference/choice-class.md) wybiera pierwszy dostępny komunikat z zestawu źródeł. `choice`Klasa reprezentuje mechanizm przepływu sterowania zamiast mechanizmu przepływu danych (temat [Biblioteka agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) tematu opisuje różnice między przepływu danych i przepływem sterowania).

Odczyt z obiektu Choice przypomina wywoływanie funkcji interfejsu API systemu Windows, `WaitForMultipleObjects` gdy ma `bWaitAll` parametr ustawiony na `FALSE` . Jednak `choice` Klasa wiąże dane ze zdarzeniem, a nie z zewnętrznym obiektem synchronizacji.

Zazwyczaj Klasa jest używana `choice` razem z funkcją [concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) do sterowania przepływem w aplikacji. Użyj `choice` klasy, gdy musisz wybrać bufory komunikatów mające różne typy. Użyj `single_assignment` klasy, gdy musisz wybrać bufory komunikatów, które mają ten sam typ.

Kolejność, w której są łączone źródła do `choice` obiektu jest ważna, ponieważ może ustalić, który komunikat jest wybrany. Rozważmy na przykład przypadek, w którym można połączyć wiele buforów komunikatów, które zawierają już komunikat do `choice` obiektu. `choice`Obiekt wybiera komunikat z pierwszego źródła, z którym jest połączony. Po połączeniu ze wszystkimi źródłami `choice` obiekt zachowuje kolejność, w jakiej każde źródło otrzymuje komunikat.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje podstawową strukturę sposobu pracy z `choice` klasą. Ten przykład używa funkcji [concurrency:: make_choice](reference/concurrency-namespace-functions.md#make_choice) , aby utworzyć `choice` obiekt, który wybiera spośród trzech bloków komunikatów. Przykład następnie oblicza różne liczby Fibonacci i przechowuje każdy wynik w innym bloku komunikatów. Przykład następnie drukuje do konsoli komunikat oparty na operacji, która zakończyła się w pierwszej kolejności.

[!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
fib35 received its value first. Result = 9227465
```

Ponieważ zadanie, które oblicza<sup>liczbę 35 Fibonacci</sup> , nie ma gwarancji na zakończenie, dane wyjściowe tego przykładu mogą się różnić.

W tym przykładzie zastosowano algorytm [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) w celu obliczenia liczby Fibonacci równolegle. Aby uzyskać więcej informacji na temat `parallel_invoke` , zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

Aby zapoznać się z kompletnym przykładem, który pokazuje, jak używać `choice` klasy, zobacz [How to: SELECT in Complete Tasks](../../parallel/concrt/how-to-select-among-completed-tasks.md).

[[Top](#top)]

## <a name="join-and-multitype_join-classes"></a><a name="join"></a>Klasy Join i multitype_join

Klasy [concurrency:: join](../../parallel/concrt/reference/join-class.md) i [concurrency:: multitype_join](../../parallel/concrt/reference/multitype-join-class.md) umożliwiają oczekiwanie na otrzymanie komunikatu dla każdego elementu członkowskiego zestawu źródeł. `join`Klasa działa w obiektach źródłowych, które mają wspólny typ komunikatu. `multitype_join`Klasa działa na obiektach źródłowych, które mogą mieć różne typy komunikatów.

Odczyt z `join` obiektu lub `multitype_join` przypomina wywoływanie funkcji interfejsu API systemu Windows, `WaitForMultipleObjects` gdy ma `bWaitAll` parametr ustawiony na `TRUE` . Jednak podobnie jak w przypadku obiektów `choice` , `join` a `multitype_join` obiekty używają mechanizmu zdarzeń, który wiąże dane ze zdarzeniem, a nie z zewnętrznym obiektem synchronizacji.

Odczyt z `join` obiektu generuje obiekt std::[Vector](../../standard-library/vector-class.md) . Odczyt z `multitype_join` obiektu tworzy obiekt std::[krotek](../../standard-library/tuple-class.md) . Elementy pojawiają się w tych obiektach w takiej samej kolejności, w jakiej odpowiadające im bufory źródłowe są połączone z `join` `multitype_join` obiektem lub. Ponieważ kolejność, w jakiej są połączone bufory źródłowe `join` z `multitype_join` obiektem lub jest skojarzona z kolejnością elementów w wyniku `vector` lub `tuple` , nie zaleca się odłączania istniejącego buforu źródłowego od sprzężenia. Wykonanie tej czynności może skutkować nieokreślonym zachowaniem.

### <a name="greedy-versus-non-greedy-joins"></a>Złączenia zachłanne vs. niezachłanne

`join`Klasy i `multitype_join` obsługują koncepcje sprzężeń zachłanne i innych niż zachłanne. *Zachłanne Join* akceptuje komunikat z każdego z jego źródeł, ponieważ komunikaty stają się dostępne do momentu udostępnienia wszystkich komunikatów. *Sprzężenie inne niż zachłanne* odbiera komunikaty w dwóch fazach. Po pierwsze, sprzężenie inne niż zachłanne czeka na zaoferowanie komunikatów z poszczególnych źródeł. Po drugie, gdy wszystkie komunikaty źródłowe są dostępne, sprzężenie inne niż zachłanne próbuje zarezerwować każdą z tych komunikatów. Jeśli może zarezerwować każdy komunikat, wykorzystuje wszystkie komunikaty i propaguje je do jego obiektu docelowego. W przeciwnym razie zwalnia lub anuluje, rezerwacje komunikatów i ponownie czekają na otrzymanie wiadomości dla każdego źródła.

Sprzężenia zachłanne działają lepiej niż sprzężenia inne niż zachłanne, ponieważ natychmiast akceptują komunikaty. Jednak w rzadkich przypadkach sprzężenia zachłanne mogą prowadzić do zakleszczenia. Użyj sprzężenia innego niż zachłanne, gdy masz wiele sprzężeń zawierających jeden lub więcej udostępnionych obiektów źródłowych.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje podstawową strukturę sposobu pracy z `join` klasą. Ten przykład używa funkcji [concurrency:: make_join](reference/concurrency-namespace-functions.md#make_join) , aby utworzyć `join` obiekt, który odbiera z trzech `single_assignment` obiektów. Ten przykład oblicza różne liczby Fibonacci, przechowuje każdy wynik w innym `single_assignment` obiekcie, a następnie drukuje do konsoli każdego wyniku, gdy obiekt jest `join` przechowywany. Ten przykład jest podobny do przykładu `choice` klasy, z tą różnicą, że `join` Klasa czeka na wszystkie bloki komunikatów źródłowych do odbierania wiadomości.

[!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]

Ten przykład generuje następujące wyniki:

```Output
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008
```

W tym przykładzie zastosowano algorytm [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) w celu obliczenia liczby Fibonacci równolegle. Aby uzyskać więcej informacji na temat `parallel_invoke` , zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

Aby zapoznać się z kompletnymi przykładami, które pokazują, jak korzystać z `join` klasy, zobacz [jak to zrobić: wybieranie spośród ukończonych zadań](../../parallel/concrt/how-to-select-among-completed-tasks.md) i [Przewodnik: Używanie funkcji join w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

[[Top](#top)]

## <a name="timer-class"></a><a name="timer"></a>Timer — Klasa

Klasa concurrency::[Timer](../../parallel/concrt/reference/timer-class.md) działa jako źródło komunikatu. `timer`Obiekt wysyła komunikat do obiektu docelowego po upływie określonego czasu. `timer`Klasa jest przydatna, gdy trzeba opóźnić wysyłanie wiadomości lub wysłać komunikat w regularnych odstępach czasu.

`timer`Klasa wysyła wiadomość do tylko jednego obiektu docelowego. W przypadku ustawienia `_PTarget` parametru w konstruktorze na `NULL` , można później określić obiekt docelowy przez wywołanie metody [concurrency:: ISource:: link_target](reference/source-block-class.md#link_target) .

`timer`Obiekt może być powtarzany lub niepowtarzalny. Aby utworzyć powtarzalny czasomierz, należy przekazać **`true`** `_Repeating` parametr podczas wywoływania konstruktora. W przeciwnym razie Przekaż **`false`** `_Repeating` parametr, aby utworzyć niepowtarzalny czasomierz. Jeśli czasomierz jest powtarzany, wysyła ten sam komunikat do jego celu po każdym interwale.

Biblioteka agenci tworzy `timer` obiekty w stanie nieuruchomionym. Aby uruchomić obiekt Timer, wywołaj metodę [concurrency:: Timer:: Start](reference/timer-class.md#start) . Aby zatrzymać `timer` obiekt, Zniszcz obiekt lub wywołaj metodę [concurrency:: Timer:: Stop](reference/timer-class.md#stop) . Aby wstrzymać powtarzający się czasomierz, wywołaj metodę [concurrency:: Timer::p ause](reference/timer-class.md#pause) .

### <a name="example"></a>Przykład

Poniższy przykład pokazuje podstawową strukturę sposobu pracy z `timer` klasą. W przykładzie są `timer` stosowane `call` obiekty i są raportowane postępy długotrwałej operacji.

[!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
Computing fib(42)..................................................result is 267914296
```

Aby zapoznać się z kompletnym przykładem, który pokazuje, jak używać `timer` klasy, zobacz [How to: Send a Message w regularnych odstępach czasu](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md).

[[Top](#top)]

## <a name="message-filtering"></a><a name="filtering"></a>Filtrowanie komunikatów

Podczas tworzenia obiektu bloku komunikatu można dostarczyć *funkcję filtru* , która określa, czy blok komunikatów akceptuje lub odrzuca komunikat. Funkcja filtru jest użytecznym sposobem zagwarantowania, że blok komunikatów odbiera tylko niektóre wartości.

Poniższy przykład pokazuje, jak utworzyć `unbounded_buffer` obiekt, który używa funkcji filtru, aby akceptować tylko parzyste liczby. `unbounded_buffer`Obiekt odrzuca liczby nieparzyste i w związku z tym nie propaguje liczb nieparzystych do ich bloków docelowych.

[!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]

Ten przykład generuje następujące wyniki:

```Output
0 2 4 6 8
```

Funkcja filtru może być funkcją lambda, wskaźnikiem funkcji lub obiektem funkcji. Każda funkcja filtru przyjmuje jedną z następujących form.

```Output
bool (T)
bool (T const &)
```

Aby wyeliminować niepotrzebne kopiowanie danych, użyj drugiego formularza, gdy masz zagregowany typ, który jest propagowany przez wartość.

Filtrowanie komunikatów obsługuje model programowania *przepływu danych* , w którym składniki wykonują obliczenia po odebraniu danych. Aby zapoznać się z przykładami korzystającymi z funkcji filtrowania do sterowania przepływem danych w sieci przekazującej komunikaty, zobacz [How to: use a Message Filter Block](../../parallel/concrt/how-to-use-a-message-block-filter.md), [Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)i [Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Top](#top)]

## <a name="message-reservation"></a><a name="reservation"></a>Rezerwacja komunikatów

*Rezerwacja komunikatów* umożliwia bloku komunikatów zastrzeganie wiadomości do późniejszego użycia. Zazwyczaj rezerwacja komunikatów nie jest używana bezpośrednio. Jednak zrozumienie rezerwacji komunikatów może pomóc lepiej zrozumieć zachowanie niektórych wstępnie zdefiniowanych typów bloków komunikatów.

Weź pod uwagę sprzężenia inne niż zachłanne i zachłanne. Obie te wartości używają rezerwacji komunikatów do rezerwowania komunikatów do późniejszego użycia. Opisane wcześniej, sprzężenie inne niż zachłanne odbiera komunikaty w dwóch fazach. Podczas pierwszej fazy obiekt inny niż zachłanne czeka, `join` aż każdy ze źródeł otrzyma komunikat. Sprzężenie inne niż zachłanne próbuje zastrzec każdą z tych komunikatów. Jeśli może zarezerwować każdy komunikat, wykorzystuje wszystkie komunikaty i propaguje je do jego obiektu docelowego. W przeciwnym razie zwalnia lub anuluje, rezerwacje komunikatów i ponownie czekają na otrzymanie wiadomości dla każdego źródła.

Zachłanne join, które również odczytuje komunikaty wejściowe z wielu źródeł, używa rezerwacji komunikatów do odczytywania dodatkowych komunikatów podczas oczekiwania na odebranie komunikatu z każdego źródła. Rozważmy na przykład sprzężenie zachłanne, które odbiera wiadomości z bloków komunikatów `A` i `B` . Jeśli zachłanne Join odbiera dwa komunikaty z B, ale nie odebrał jeszcze komunikatu z `A` , zachłanne Join zapisuje unikatowy identyfikator komunikatu dla drugiego komunikatu z `B` . Gdy zachłanne Join odbierze komunikat z `A` i propaguje te komunikaty, użyje zapisanego identyfikatora komunikatu, aby sprawdzić, czy drugi komunikat z `B` jest nadal dostępny.

Można użyć rezerwacji komunikatów podczas implementowania własnych niestandardowych typów bloku komunikatów. Aby zapoznać się z przykładem dotyczącym sposobu tworzenia niestandardowego typu bloku komunikatów, zobacz [Przewodnik: Tworzenie niestandardowego bloku komunikatów](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md).

[[Top](#top)]

## <a name="see-also"></a>Zobacz także

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)
