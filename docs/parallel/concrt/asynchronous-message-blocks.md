---
title: Bloki komunikatów asynchronicznych
ms.date: 11/04/2016
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
ms.openlocfilehash: b78b4db4dda33e0a94da3624ea1ffd8748a601f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586124"
---
# <a name="asynchronous-message-blocks"></a>Bloki komunikatów asynchronicznych

Biblioteka agentów zawiera kilka typów bloków komunikatów, które umożliwiają Propagacja komunikatów między składnikami aplikacji w sposób bezpieczny dla wątków. Te typy bloków komunikatów są często używane przy użyciu różnych procedur przekazywania komunikatów, takie jak [concurrency::send](reference/concurrency-namespace-functions.md#send), [concurrency::asend](reference/concurrency-namespace-functions.md#asend), [concurrency::receive](reference/concurrency-namespace-functions.md#receive), i [concurrency::try_receive](reference/concurrency-namespace-functions.md#try_receive). Aby uzyskać więcej informacji na temat przekazywania procedur, które są zdefiniowane przez bibliotekę agentów komunikatów, zobacz [funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md).

##  <a name="top"></a> Sekcje

Ten temat zawiera następujące sekcje:

- [Źródła i obiekty docelowe](#sources_and_targets)

- [Propagacja komunikatów](#propagation)

- [Omówienie typów bloku komunikatu](#overview)

- [Klasa unbounded_buffer](#unbounded_buffer)

- [overwrite_buffer, klasa](#overwrite_buffer)

- [single_assignment, klasa](#single_assignment)

- [call, klasa](#call)

- [transformer, klasa](#transformer)

- [choice, klasa](#choice)

- [Klasy sprzężenia oraz łączy typu multitype_join](#join)

- [timer, klasa](#timer)

- [Filtrowanie komunikatów](#filtering)

- [Zastrzeżenie komunikatu](#reservation)

##  <a name="sources_and_targets"></a> Źródła i obiekty docelowe

Źródła i obiekty docelowe są dwie ważne uczestnikami przekazywania komunikatów. A *źródła* oznacza punkt końcowy komunikacji, który wysyła wiadomości. A *docelowej* oznacza punkt końcowy komunikacji, która odbiera komunikaty. Można potraktować źródła jako punkt końcowy, który umożliwia odczyt z oraz stanowią obiekty docelowe jako punkt końcowy, który można zapisać do. Aplikacje źródła i obiekty docelowe razem połączyć się z formularza *sieciami wiadomości*.

Biblioteka agentów używa dwóch klas abstrakcyjnych, który reprezentuje źródła i obiekty docelowe: [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) i [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md). Typy bloków wiadomości które działają jako wywodzą się z `ISource`; typy bloków wiadomości które działają jako obiekty docelowe wywodzą się z `ITarget`. Typy bloków wiadomości, które działają jako źródła i obiekty docelowe wywodzą się z obu `ISource` i `ITarget`.

[[Górnej](#top)]

##  <a name="propagation"></a> Propagacja komunikatów

*Propagację wiadomości* polega na wysyłaniu wiadomości od jednego elementu do innego. Gdy blok komunikatów jest oferowana wiadomość, go zaakceptować, odrzucenia lub odroczyć tę wiadomość. Każdy typ bloku komunikatu przechowuje i przesyła wiadomości na różne sposoby. Na przykład `unbounded_buffer` klasa przechowuje nieograniczoną liczbę wiadomości, `overwrite_buffer` klasa przechowuje pojedynczej wiadomości w czasie, a klasy transformatora przechowuje zmienionego wersję każdego komunikatu. Tych typów bloku komunikatu są opisane bardziej szczegółowo w dalszej części tego dokumentu.

Gdy blok komunikatów zaakceptuje wiadomość, może opcjonalnie wykonywania pracy i, jeśli blok komunikatów jest źródłem, należy przekazać komunikat wynikowy do innego członka sieci. Blok komunikatów można użyć funkcji filtru, aby odrzucić wiadomości, które chcesz otrzymywać. Filtry są opisane bardziej szczegółowo w dalszej części tego tematu, w sekcji [filtrowanie komunikatów](#filtering). Blok komunikatów, który odłoży komunikat może zarezerwować ten komunikat i pobrać go później. Zastrzeżenie komunikatu jest opisany bardziej szczegółowo w dalszej części tego tematu, w sekcji [zastrzeżenie komunikatu](#reservation).

Biblioteka agentów umożliwiają blokadom asynchronicznie lub synchronicznie przekazywania wiadomości. Podczas przekazywania wiadomości do bloku komunikatów synchronicznie, na przykład za pomocą `send` funkcji, środowisko uruchomieniowe blokuje bieżący kontekst do momentu blok docelowy może zaakceptować lub odrzuca komunikat. Podczas przekazywania wiadomości do bloku komunikatów asynchronicznie, na przykład za pomocą `asend` funkcji, środowisko wykonawcze zapewnia komunikat, który ma element docelowy, a jeśli docelowych zaakceptuje wiadomość, środowisko uruchomieniowe planuje zadanie asynchroniczne, które propaguje komunikat do odbiorcy. Zadania lekkie środowisko uruchomieniowe Propagacja komunikatów w sposób współpracujący. Aby uzyskać więcej informacji na temat zadań lekkich zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Aplikacje źródła i obiekty docelowe ze sobą połączyć się z sieciami wiadomości formularza. Zwykle, możesz połączyć sieć i wywołania `send` lub `asend` do przekazywania danych do sieci. Aby połączyć z bloku komunikatu źródłowego do obiektu docelowego, należy wywołać [concurrency::ISource::link_target](reference/isource-class.md#link_target) metody. Aby odłączyć blok źródłowy od obiektu docelowego, należy wywołać [concurrency::ISource::unlink_target](reference/isource-class.md#unlink_target) metody. Aby odłączyć blok źródłowy wszystkie jego obiekty docelowe, należy wywołać [concurrency::ISource::unlink_targets](reference/isource-class.md#unlink_targets) metody. Gdy jeden z typów bloku komunikatu wstępnie zdefiniowanych pozostawia zakres lub jest niszczony, jego automatycznie rozłącza sam wszelkich bloków docelowych. Niektórych typów bloku komunikatu ograniczać maksymalną liczbę elementów docelowych, które można zapisać. W poniższej sekcji opisano ograniczenia, które są stosowane do typów bloku komunikatu wstępnie zdefiniowane.

[[Górnej](#top)]

##  <a name="overview"></a> Omówienie typów bloku komunikatu

W poniższej tabeli opisano skrótowo roli typy ważne blok komunikatów.

[unbounded_buffer](#unbounded_buffer)<br/>
Przechowuje kolejki komunikatów.

[overwrite_buffer](#overwrite_buffer)<br/>
Przechowuje jeden komunikat, który może być zapisany i odczytywanie wiele razy.

[single_assignment](#single_assignment)<br/>
Przechowuje jeden komunikat, który może być zapisywane jeden raz i odczytywanie wiele razy.

[Wywołania](#call)<br/>
Wykonuje pracę, po odebraniu komunikatu.

[transformer](#transformer)<br/>
Wykonuje pracę, gdy odbiera dane i wysyła wynikiem tej pracy do innego bloku docelowego. `transformer` Klasy może działać na różne dane wejściowe i typów danych wyjściowych.

[Wybór](#choice)<br/>
Wybiera pierwszy komunikat dostępne z zestawu źródeł.

[sprzężenia i multitype sprzężenia](#join)<br/>
Poczekaj, aż wszystkie komunikaty można odbierać dane z zestawu źródeł i następnie połączyć komunikaty w jednej wiadomości dla innego bloku komunikatu.

[Czasomierz](#timer)<br/>
Wysyła komunikat do bloku docelowego w regularnych odstępach czasu.

Tych typów bloku komunikatu mają różne cechy, które były przydatne w przypadku różnych sytuacjach. Oto niektóre właściwości:

- *Typ propagacji*: czy blok komunikatów działa jako źródło danych i/lub odbiorcy danych.

- *Kolejność komunikatów*: czy blok komunikatów przechowuje oryginalnej kolejności, w której wiadomości są wysyłane lub odbierane. Każdy typ bloku komunikatu wstępnie zdefiniowanych zachowuje kolejności, w którym wysyła i odbiera komunikaty.

- *Liczba źródłowych*: Maksymalna liczba źródeł, które może odczytywać blok komunikatów.

- *Docelowa liczba*: Maksymalna liczba elementów docelowych, które może zapisać blok komunikatów.

W poniższej tabeli przedstawiono, jak te cechy odnoszą się do różnych typów bloku komunikatu.

|Typ bloku komunikatu|Typ propagacji (źródłowy, docelowy lub oba)|Komunikat szeregowania (zamówione lub Unordered)|Liczbę źródeł|Docelowa liczba|
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|
|`unbounded_buffer`|Oba|Uporządkowane|niepowiązane|niepowiązane|
|`overwrite_buffer`|Oba|Uporządkowane|niepowiązane|niepowiązane|
|`single_assignment`|Oba|Uporządkowane|niepowiązane|niepowiązane|
|`call`|Docelowy|Uporządkowane|niepowiązane|Nie dotyczy|
|`transformer`|Oba|Uporządkowane|niepowiązane|1|
|`choice`|Oba|Uporządkowane|10|1|
|`join`|Oba|Uporządkowane|niepowiązane|1|
|`multitype_join`|Oba|Uporządkowane|10|1|
|`timer`|Źródło|Nie dotyczy|Nie dotyczy|1|

W poniższych sekcjach opisano typy blok komunikatów, które bardziej szczegółowo.

[[Górnej](#top)]

##  <a name="unbounded_buffer"></a> Klasa unbounded_buffer

[Concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) klasa reprezentuje strukturę ogólnego przeznaczenia komunikatów asynchronicznych. Ta klasa przechowuje imię w pierwszej FIFO kolejki komunikatów, które mogą być zapisywane przez wiele źródeł lub odczytywać przez wiele elementów docelowych. Gdy obiekt docelowy otrzymuje komunikat z `unbounded_buffer` obiektu, ten komunikat zostanie usunięty z kolejki komunikatów. W związku z tym mimo że `unbounded_buffer` obiekt może mieć wiele elementów docelowych, tylko jeden element docelowy będzie otrzymywać każdego komunikatu. `unbounded_buffer` Klasy jest przydatne w przypadku, gdy chcesz przekazać wiele wiadomości do innego składnika i ten składnik musi otrzymać bit każdego komunikatu.

### <a name="example"></a>Przykład

Poniższy kod przedstawia podstawowe struktury jak pracować z `unbounded_buffer` klasy. W tym przykładzie wysyła trzech wartości celu `unbounded_buffer` obiektu, a następnie odczytuje wartości z kopii tego samego obiektu.

[!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]

Ten przykład generuje następujące wyniki:

```Output
334455
```

Pełny przykład, który pokazuje, jak używać `unbounded_buffer` klasy, zobacz [porady: Implementowanie różnych wzorców producent — konsument](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[[Górnej](#top)]

##  <a name="overwrite_buffer"></a> overwrite_buffer, klasa

[Concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) klasa przypomina `unbounded_buffer` klasy, chyba że `overwrite_buffer` obiekt przechowuje tylko jedną wiadomość. Ponadto, kiedy obiekt docelowy otrzyma komunikat z `overwrite_buffer` obiektu, ten komunikat nie zostanie usunięty z buforu. W związku z tym wiele elementów docelowych otrzymać kopię wiadomości.

`overwrite_buffer` Klasy jest przydatne w przypadku, gdy chcesz przekazać wiele wiadomości do innego składnika, ale ten składnik wymaga tylko najnowszą wartość. Ta klasa jest również przydatne, jeśli chcesz wysyłać komunikat do wielu składników.

### <a name="example"></a>Przykład

Poniższy kod przedstawia podstawowe struktury jak pracować z `overwrite_buffer` klasy. W tym przykładzie wysyła trzech wartości celu `overwrite _buffer` obiektu, a następnie trzykrotnie odczytuje z tego samego obiektu bieżącą wartość. Ten przykład jest podobny do przykład `unbounded_buffer` klasy. Jednak `overwrite_buffer` klasa przechowuje tylko jedną wiadomość. Ponadto środowisko wykonawcze nie powoduje usunięcia komunikatu z `overwrite_buffer` obiektem jest do odczytu.

[!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]

Ten przykład generuje następujące wyniki:

```Output
555555
```

Pełny przykład, który pokazuje, jak używać `overwrite_buffer` klasy, zobacz [porady: Implementowanie różnych wzorców producent — konsument](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[[Górnej](#top)]

##  <a name="single_assignment"></a> single_assignment, klasa

[Concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) klasa przypomina `overwrite_buffer` klasy, chyba że `single_assignment` obiektów mogą być zapisywane tylko raz. Podobnie jak `overwrite_buffer` klasy, gdy obiekt docelowy odbiera wiadomości z `single_assignment` obiektu, ten komunikat nie zostanie usunięta z tego obiektu. W związku z tym wiele elementów docelowych otrzymać kopię wiadomości. `single_assignment` Klasy jest przydatne w przypadku, gdy chcesz wysyłać jedną wiadomość do wielu składników.

### <a name="example"></a>Przykład

Poniższy kod przedstawia podstawowe struktury jak pracować z `single_assignment` klasy. W tym przykładzie wysyła trzech wartości celu `single_assignment` obiektu, a następnie trzykrotnie odczytuje z tego samego obiektu bieżącą wartość. Ten przykład jest podobny do przykład `overwrite_buffer` klasy. Mimo że zarówno `overwrite_buffer` i `single_assignment` klasy przechowywania jeden komunikat o `single_assignment` klasy mogą być zapisywane tylko raz.

[!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]

Ten przykład generuje następujące wyniki:

```Output
333333
```

Pełny przykład, który pokazuje, jak używać `single_assignment` klasy, zobacz [wskazówki: Wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md).

[[Górnej](#top)]

##  <a name="call"></a> wywołanie klasy

[Concurrency::call](../../parallel/concrt/reference/call-class.md) klasa działa jako odbiorcom wiadomości, która wykonuje funkcję pracy po odebraniu danych. Ta funkcja pracy może być wyrażenie lambda, obiekt funkcji lub wskaźnik funkcji. Element `call` obiektu zachowuje się inaczej niż wywołania zwykłej funkcji, ponieważ działa równolegle z innymi składnikami, które wysyłają komunikaty do niego. Jeśli `call` obiekt wykonuje pracę po odebraniu wiadomości, dodaje ten komunikat do kolejki. Każdy `call` procesy obiektu w kolejce wiadomości w kolejności, w której zostały odebrane.

### <a name="example"></a>Przykład

Poniższy kod przedstawia podstawowe struktury jak pracować z `call` klasy. Ten przykład tworzy `call` obiekt, który drukuje każdej wartości, która odbierze do konsoli. Przykład wysyła następnie trzech wartości celu `call` obiektu. Ponieważ `call` obiektu przetwarza wiadomości w oddzielnym wątku, w tym przykładzie również użyto zmiennej licznika i [zdarzeń](../../parallel/concrt/reference/event-class.md) obiekt, aby upewnić się, że `call` obiektów są przetwarzane wszystkie komunikaty przed `wmain` funkcja zwraca.

[!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]

Ten przykład generuje następujące wyniki:

```Output
334455
```

Pełny przykład, który pokazuje, jak używać `call` klasy, zobacz [jak: Podaj funkcji pracy do wywoływania oraz klasy transformatora](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md).

[[Górnej](#top)]

##  <a name="transformer"></a> Transformer, klasa

[Concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) klasa działa jako odbiornik komunikatów i nadawcy wiadomości. `transformer` Klasa przypomina `call` klasy, ponieważ wykonuje funkcji roboczych zdefiniowanej przez użytkownika, po odebraniu danych. Jednak `transformer` klasy wysyła również wynik funkcji pracy z obiektami odbiorcy. Podobnie jak `call` obiektu `transformer` obiektu działa równolegle z innymi składnikami, które wysyłają komunikaty do niego. Jeśli `transformer` obiekt wykonuje pracę po odebraniu wiadomości, dodaje ten komunikat do kolejki. Każdy `transformer` obiektu przetwarza jego wiadomości w kolejce w kolejności, w której zostały odebrane.

`transformer` Klasy wysyła komunikat do jednego obiektu docelowego. Jeśli ustawisz `_PTarget` parametr w Konstruktorze w `NULL`, później możesz określić obiektu docelowego przez wywołanie metody [concurrency::link_target](reference/source-block-class.md#link_target) metody.

W odróżnieniu od wszystkich innych asynchronicznego typów bloku komunikatu, które są dostarczane przez biblioteki agentów `transformer` klasy może działać na różne dane wejściowe i typów danych wyjściowych. Ta możliwość przekształcania danych z jednego typu, powoduje, że inny `transformer` klasy kluczowym czynnikiem wiele równoczesnych sieci. Ponadto można dodać więcej szczegółowych funkcji równoległe w funkcji roboczych `transformer` obiektu.

### <a name="example"></a>Przykład

Poniższy kod przedstawia podstawowe struktury jak pracować z `transformer` klasy. Ten przykład tworzy `transformer` obiektu, że dane wejściowe wielokrotności każdego `int` wartość przez 0,33 w celu utworzenia `double` wartość jako dane wyjściowe. Przykład odbiera przekształcone wartości z tej samej `transformer` obiektów i ich drukuje do konsoli.

[!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]

Ten przykład generuje następujące wyniki:

```Output
10.8914.5218.15
```

Pełny przykład, który pokazuje, jak używać `transformer` klasy, zobacz [porady: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

[[Górnej](#top)]

##  <a name="choice"></a> choice, klasa

[Concurrency::choice](../../parallel/concrt/reference/choice-class.md) klasy wybiera pierwszy komunikat dostępne z zestawu źródeł. `choice` Klasa reprezentuje mechanizm przepływu sterowania zamiast mechanizmu przepływu danych (temat [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md) opisano różnice między przepływu danych i przepływ sterowania).

Czytanie z obiektów wybór przypomina wywoływanie funkcji Windows API `WaitForMultipleObjects` kiedy ma `bWaitAll` parametr `FALSE`. Jednak `choice` klasy tworzy powiązanie danych z elementu zdarzeń do obiektu zewnętrznego synchronizacji.

Zazwyczaj można użyć `choice` klasy wraz z [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkcję, aby dysk przepływ sterowania w aplikacji. Użyj `choice` klasy, jeśli masz do wyboru spośród buforów komunikatów, które mają różne typy. Użyj `single_assignment` klasy, gdy trzeba wybrać pomiędzy buforów komunikatów, które mają tego samego typu.

Kolejność, w którym możesz połączyć źródeł `choice` obiekt jest ważny, ponieważ można określić, której wiadomość jest zaznaczone. Na przykład, rozważmy przypadek, gdzie możesz połączyć wiele buforów komunikatów, które już zawierają komunikatów `choice` obiektu. `choice` Obiektu wybierana jest opcja komunikatu pierwszego źródła, która jest połączona. Po połączeniu wszystkich źródeł `choice` obiektu zachowuje kolejności, w którym każde źródło odbiera komunikat.

### <a name="example"></a>Przykład

Poniższy kod przedstawia podstawowe struktury jak pracować z `choice` klasy. W tym przykładzie użyto [concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice) funkcji, aby utworzyć `choice` obiekt, który wybiera między trzy bloków komunikatów. Przykład następnie różne numery Fibonacci oblicza i przechowuje wynik w bloku inny komunikat. Przykład następnie drukuje do konsoli komunikat, który jest oparty na operację, która zostanie ukończone jako pierwsze.

[!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
fib35 received its value first. Result = 9227465
```

Ponieważ zadanie, które oblicza 35<sup>th</sup> numer Fibonacci nie jest gwarantowana zakończy pierwsza, w tym przykładzie dane wyjściowe mogą się różnić.

W tym przykładzie użyto [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytm obliczania liczb Fibonacci równolegle. Aby uzyskać więcej informacji na temat `parallel_invoke`, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

Pełny przykład, który pokazuje, jak używać `choice` klasy, zobacz [jak: Wybierz spośród ukończone zadania](../../parallel/concrt/how-to-select-among-completed-tasks.md).

[[Górnej](#top)]

##  <a name="join"></a> Klasy sprzężenia oraz łączy typu multitype_join

[Concurrency::join](../../parallel/concrt/reference/join-class.md) i [concurrency::multitype_join](../../parallel/concrt/reference/multitype-join-class.md) klasy umożliwiają oczekiwanie dla każdego elementu członkowskiego zestawu źródeł komunikat o błędzie. `join` Klasa działa na obiekty źródła, które mają wspólny typ komunikatu. `multitype_join` Klasa działa na obiekty źródła, które mogą mieć różne rodzaje komunikatów.

Odczytywanie z `join` lub `multitype_join` obiektu przypomina wywoływanie funkcji Windows API `WaitForMultipleObjects` kiedy ma `bWaitAll` parametr `TRUE`. Jednakże, podobnie jak w przypadku `choice` obiektu `join` i `multitype_join` obiekty używają mechanizm zdarzeń, który tworzy powiązanie danych z elementu zdarzeń do obiektu zewnętrznego synchronizacji.

Odczytywanie z `join` obiektu tworzy std::[wektor](../../standard-library/vector-class.md) obiektu. Odczytywanie z `multitype_join` obiektu tworzy std::[krotki](../../standard-library/tuple-class.md) obiektu. Elementy są wyświetlane w tych obiektów w tej samej kolejności, zgodnie z ich odpowiednich bufory źródła są połączone z `join` lub `multitype_join` obiektu. Ponieważ kolejność, w którym połączenia źródła buforów do `join` lub `multitype_join` obiekt jest skojarzony z kolejność elementów w wynikowym `vector` lub `tuple` obiektu, zaleca się nie odłączenie istniejących bufor źródłowy z Dołącz do. To może doprowadzić do nieokreślone zachowanie.

### <a name="greedy-versus-non-greedy-joins"></a>Złączenia zachłanne vs. niezachłanne

`join` i `multitype_join` klasy obsługuje pojęcie zachłanne i niezachłanne sprzężenia. A *zachłanne złączenia* akceptuje wiadomość z każdej z jej źródeł, jak komunikaty stają się dostępne, dopóki wszystkie wiadomości są dostępne. A *niezachłanne złączenia* odbiera komunikaty w dwóch fazach. Po pierwsze niezachłanne złączenia czeka, aż komunikat jest dostępna z każdego z jej źródła. Po drugie po wszystkich wiadomości źródła są dostępne, niezachłanne złączenia próbuje zarezerwować te wiadomości. Jeśli można ją zarezerwować każdy komunikat, wykorzystuje wszystkie komunikaty i propaguje je do jego element docelowy. W przeciwnym razie zwalnia, ani anuluje rezerwacje wiadomość i ponownie czeka na każde źródło do odbierania wiadomości.

Zachłanne sprzężeń mają lepszą wydajność niż niezachłanne, ponieważ ich akceptować komunikaty od razu. Jednak w rzadkich przypadkach zachłanne sprzężeń może prowadzić do zakleszczenia. Niezachłanne złączenia należy użyć w przypadku wielu sprzężeń, które zawierają co najmniej jeden obiekt źródłowy udostępniony.

### <a name="example"></a>Przykład

Poniższy kod przedstawia podstawowe struktury jak pracować z `join` klasy. W tym przykładzie użyto [concurrency::make_join](reference/concurrency-namespace-functions.md#make_join) funkcji, aby utworzyć `join` obiekt, który odbiera z trzech `single_assignment` obiektów. W tym przykładzie oblicza różne numery Fibonacci, zapisuje każdy wynik w innym `single_assignment` obiektu, a następnie drukuje do konsoli każdy powoduje, że `join` obiektu blokad. Ten przykład jest podobny do przykład `choice` klasy, chyba że `join` klasy czeka, aż wszystkie bloki komunikatów źródła na komunikat o błędzie.

[!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]

Ten przykład generuje następujące wyniki:

```Output
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008
```

W tym przykładzie użyto [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytm obliczania liczb Fibonacci równolegle. Aby uzyskać więcej informacji na temat `parallel_invoke`, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

Kompletne przykłady pokazujące, jak używać `join` klasy, zobacz [jak: Wybierz spośród ukończone zadania](../../parallel/concrt/how-to-select-among-completed-tasks.md) i [Instruktaż: za pomocą, aby zapobiec zakleszczeniu](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

[[Górnej](#top)]

##  <a name="timer"></a> Timer, klasa

Współbieżność::[timer, klasa](../../parallel/concrt/reference/timer-class.md) działa jako źródło komunikatu. Element `timer` obiektu wysyła komunikat do obiektu docelowego, po upływie okresu czasu. `timer` Klasy jest przydatne w przypadku, gdy należy opóźnić wysyłanie wiadomości lub chcesz wysyłanie komunikatu w regularnych odstępach czasu.

`timer` Klasy wysyła komunikat do tylko jednego obiektu docelowego. Jeśli ustawisz `_PTarget` parametr w Konstruktorze w `NULL`, później możesz określić obiektu docelowego przez wywołanie metody [concurrency::ISource::link_target](reference/source-block-class.md#link_target) metody.

A `timer` obiektów, które mogą być powtarzające się lub niepowtarzający. Aby utworzyć powtarzające się czasomierz, należy przekazać **true** dla `_Repeating` parametru podczas wywoływania konstruktora. W przeciwnym razie przekazania **false** dla `_Repeating` parametr w celu utworzenia niepowtarzający czasomierz. Jeśli powtarza czasomierz wysyła tę samą wiadomość do jego element docelowy po każdym interwale.

Tworzy biblioteki agentów `timer` obiekty w stanie-started. Aby rozpocząć obiektu timer, należy wywołać [concurrency::timer::start](reference/timer-class.md#start) metody. Aby zatrzymać `timer` obiektów, zniszczenie obiektu lub wywołanie [concurrency::timer::stop](reference/timer-class.md#stop) metody. Aby wstrzymać czasomierza powtarzające się, należy wywołać [concurrency::timer::pause](reference/timer-class.md#pause) metody.

### <a name="example"></a>Przykład

Poniższy kod przedstawia podstawowe struktury jak pracować z `timer` klasy. W przykładzie użyto `timer` i `call` obiekty do raportowania postępu długotrwałej operacji.

[!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
Computing fib(42)..................................................result is 267914296
```

Pełny przykład, który pokazuje, jak używać `timer` klasy, zobacz [porady: wysyłanie komunikatu w regularnych odstępach czasu](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md).

[[Górnej](#top)]

##  <a name="filtering"></a> Filtrowanie komunikatów

Podczas tworzenia obiektu Blok komunikatów, możesz podać *funkcja filtrowania* określający, czy blok komunikatów akceptuje lub odrzuca komunikat. Funkcję filtru jest to wygodny sposób, aby zagwarantować, że blok komunikatów odbiera tylko niektóre wartości.

Poniższy przykład pokazuje, jak utworzyć `unbounded_buffer` obiektu, który używa funkcji filtru, aby zaakceptować tylko liczby parzyste z zakresu. `unbounded_buffer` Obiektu odrzuca liczby nieparzyste i dlatego nie propaguje liczby nieparzyste do bloków jego miejsca docelowego.

[!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]

Ten przykład generuje następujące wyniki:

```Output
0 2 4 6 8
```

Funkcja filtru może być funkcji lambda, wskaźnika funkcji lub obiektu funkcji. Każdej funkcji filtru ma jedną z następujących form.

```Output
bool (T)
bool (T const &)
```

Aby wyeliminować niepotrzebnego kopiowania danych, użyj drugiego formularza, jeśli masz typ agregacji, który jest propagowany przez wartość.

Obsługuje filtrowanie komunikatów *przepływu danych* modelu programowania, w którym składniki wykonują obliczenia, po otrzymaniu danych. Przykłady, korzystających z funkcji filtru do sterowania przepływem danych w sieci, przekazywanie wiadomości, zobacz [porady: Korzystanie z filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md), [wskazówki: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md), i [ Wskazówki: Tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Górnej](#top)]

##  <a name="reservation"></a> Zastrzeżenie komunikatu

*Zastrzeżenie komunikatu* umożliwia blokowi komunikatu zarezerwować komunikat do późniejszego użytku. Zazwyczaj zastrzeżenie komunikatu nie jest używana bezpośrednio. Jednak zrozumienie wiadomości rezerwacji może pomóc lepiej zrozumieć zachowanie niektórych typów bloku komunikatu wstępnie zdefiniowane.

Należy wziąć pod uwagę niezachłanne i zachłanne sprzężenia. Zastrzeżenie komunikatu oba te służy do rezerwowania wiadomości do późniejszego użycia. Opisany wcześniej niezachłanne złączenia odbiera komunikaty w dwóch fazach. W pierwszej fazie niezachłanne `join` obiektu czeka na każdy z jej źródeł do komunikat o błędzie. Niezachłanne złączenia podejmuje próbę zarezerwować te wiadomości. Jeśli można ją zarezerwować każdy komunikat, wykorzystuje wszystkie komunikaty i propaguje je do jego element docelowy. W przeciwnym razie zwalnia, ani anuluje rezerwacje wiadomość i ponownie czeka na każde źródło do odbierania wiadomości.

Zachłanne złączenia również odczytuje komunikaty wejściowe z wielu źródeł, używa zastrzeżenie komunikatu można odczytać dodatkowych komunikatów podczas oczekiwania na komunikat z każdego źródła. Na przykład, należy wziąć pod uwagę zachłanne złączenia, która odbiera komunikaty z bloków komunikatów `A` i `B`. Jeśli zachłanne złączenia otrzymuje dwa komunikaty z B, ale jeszcze nie otrzymał komunikat z `A`, zachłanne złączenia zapisuje komunikat Unikatowy identyfikator drugi komunikat z `B`. Po zachłanne złączenia otrzymuje komunikat z `A` i propaguje tych wiadomości, używa ona identyfikator zapisanego komunikatu Aby sprawdzić, czy drugi komunikat z `B` jest nadal dostępna.

Zastrzeżenie komunikatu można użyć podczas implementowania swój własny typ bloku komunikatów niestandardowych. Aby uzyskać przykład sposobu tworzenia komunikatów niestandardowy typ bloku, zobacz [wskazówki: Tworzenie niestandardowego bloku komunikatów](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md).

[[Górnej](#top)]

## <a name="see-also"></a>Zobacz też

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)

