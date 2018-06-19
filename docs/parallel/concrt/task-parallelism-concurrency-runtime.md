---
title: Zadanie równoległości (współbieżność środowiska wykonawczego) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- structured task groups [Concurrency Runtime]
- structured tasks [Concurrency Runtime]
- task groups [Concurrency Runtime]
- task parallelism
- tasks [Concurrency Runtime]
ms.assetid: 42f05ac3-2098-494a-ba84-737fcdcad077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4f2a1f1a5bd0b4a8ca68f3aa47f6890a11efa11
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695327"
---
# <a name="task-parallelism-concurrency-runtime"></a>Równoległość zadania (współbieżność środowiska wykonawczego)
Współbieżność środowiska wykonawczego *zadań* jest jednostka pracy, który wykonuje określone zadanie i zwykle uruchamia się równolegle z innymi zadaniami. Zadanie może być rozłożone na dodatkowych, bardziej szczegółowych zadań, które są podzielone na *grupy zadań*.  
  
 Zadania można użyć podczas pisania kodu asynchroniczne, a niektóre działania wykonywane po zakończeniu operacji asynchronicznej. Na przykład można użyć zadania asynchronicznie odczytane z pliku, a następnie użyć innego zadania — *zadania kontynuacji*, który znajduje się w dalszej części tego dokumentu — do przetwarzania danych, gdy stanie się dostępny. Z drugiej strony można użyć grup zadań próba dekompozycji pracy równoległej na mniejsze części. Na przykład załóżmy, że masz algorytm cyklicznej, który dzieli Praca pozostała na dwóch partycji. Grupy zadań umożliwia równoczesne uruchamianie tych partycji, a następnie odczekaj podzielony pracy. zakończyć.  
  
> [!TIP]

>  Dotyczą tej samej procedury co element kolekcji równolegle, należy używać algorytmu równoległe, takich jak [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), zamiast zadania lub grupy zadań. Aby uzyskać więcej informacji na temat algorytmy równoległe, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).  

  
## <a name="key-points"></a>Kwestie kluczowe  
  
-   Jeśli zmienne do wyrażenia lambda przez odwołanie, musi zapewniać, że okres istnienia tej zmiennej będzie się powtarzać, zakończenie zadania.  
  
-   Używanie zadań ( [concurrency::task](../../parallel/concrt/reference/task-class.md) klasy) podczas pisania kodu asynchronicznego. Task — klasa korzysta z puli wątków systemu Windows jako jego harmonogramu nie współbieżności środowiska wykonawczego.  
  
-   Użyj grupy zadań ( [concurrency::task_group](reference/task-group-class.md) klasy lub [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytm) kiedy zachodzi potrzeba dekompozycji pracy równoległej na mniejsze części i poczekaj tych mniejszych części, aby zakończyć.  
  
-   Użyj [concurrency::task::then](reference/task-class.md#then) metodę w celu utworzenia kontynuacje. A *kontynuacji* to zadanie, które uruchamia asynchronicznie, po zakończeniu inne zadanie. Można połączyć z dowolną liczbę kontynuacje, aby utworzyć łańcuch asynchroniczne.  
  
-   Kontynuacja opartego na zadaniach zawsze jest zaplanowane do uruchomienia po zakończeniu poprzedzających zadań, nawet gdy poprzedzających zadanie zostało anulowane lub zgłasza wyjątek.  
  
-   Użyj [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) do tworzenie zadania kończonego po zakończeniu każdy element członkowski zestawu zadań. Użyj [concurrency::when_any](reference/concurrency-namespace-functions.md#when_any) do tworzenie zadania kończonego po zakończeniu jednego członka zestawu zadań.  

  
-   Zadania i grupy zadań mogą uczestniczyć w mechanizm anulowania równoległych biblioteki wzorców (PLL). Aby uzyskać więcej informacji, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).  
  
-   Aby dowiedzieć się, jak środowisko uruchomieniowe obsługi wyjątków, które są generowane przez zadania i grupy zadań, zobacz [obsługi wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
## <a name="in-this-document"></a>W tym dokumencie  
  
- [Za pomocą wyrażenia Lambda](#lambdas)  
  
- [Zadanie — klasa](#task-class)  
  
- [Zadań kontynuacji](#continuations)  
  
- [Na podstawie wartości i Kontynuacje opartego na zadaniach](#value-versus-task)  
  
- [Tworzenie zadań](#composing-tasks)  
  
    - [When_all — funkcja](#when-all)  
  
    - [When_any — funkcja](#when-any)  
  
- [Wykonywanie zadań opóźnione](#delayed-tasks)  
  
- [Grupy zadań](#task-groups)  
  
- [Porównywanie task_group do structured_task_group —](#comparing-groups)  
  
- [Przykład](#example)  
  
- [Skuteczne programowanie](#robust)  
  
##  <a name="lambdas"></a> Za pomocą wyrażenia Lambda  
 Ze względu na ich zwięzły składnię wyrażenia lambda są typowe sposób definiowania pracy wykonywanego przez zadania i grupy zadań. Poniżej przedstawiono kilka wskazówek użycia:  
  
-   Ponieważ zadania są zazwyczaj uruchamiane na wątki w tle, należy pamiętać o okres istnienia obiektu podczas przechwytywania zmienne w wyrażeniach lambda. Po przechwyceniu zmiennej przez wartość kopię tej zmiennej jest przeprowadzane w treści lambda. Podczas przechwytywania przez odwołanie, nie jest możliwe kopii. W związku z tym upewnij się, że który okres istnienia żadnych zmiennej przechwytywanie przez odwołanie outlives zadanie, które korzysta z niego.  
  
-   Jeśli wyrażenie lambda do zadania, nie należy przechwytywać zmiennych, które są przydzielane na stosie przez odwołanie.  
  
-   Być jawne o zmiennych przechwytywanych w wyrażeniach lambda, dzięki czemu można zidentyfikować, co możesz jest przechwytywanie według wartości i według odwołania. Z tego powodu zaleca się, że nie używasz `[=]` lub `[&]` opcje dla wyrażeń lambda.  
  
 Wspólnego wzorca jest podczas jednego zadania w łańcuchu kontynuacji przypisuje się do zmiennej, a inne zadanie odczytuje tej zmiennej. Nie można przechwycić przez wartość, ponieważ zawiera kopię innej zmiennej każdego zadania kontynuacji. Przydzielony stos zmiennych, także nie można przechwycić przez odwołanie, ponieważ zmienna może nie być już prawidłowe.  
  
 Aby rozwiązać ten problem, użyj wskaźnika inteligentnego, takiego jak [std::shared_ptr](../../standard-library/shared-ptr-class.md), aby zawijać zmiennej i przekazanie przez wartość wskaźnika inteligentnego. W ten sposób obiektu źródłowego można przypisać do odczytu i będzie outlive zadania, które go używają. Użyj tej metody, nawet wtedy, gdy jest zmienna wskaźnika lub dojścia zliczane odwołania (`^`) do obiektu środowiska wykonawczego systemu Windows. Poniżej przedstawiono prosty przykład:  
  
 [!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]  
  
 Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda](../../cpp/lambda-expressions-in-cpp.md).  
  
##  <a name="task-class"></a> Zadanie — klasa  
 Można użyć [concurrency::task](../../parallel/concrt/reference/task-class.md) klasy utworzenie zadania do zestawu działań zależnych. Ten model kompozycji jest obsługiwana przez pojęcie *kontynuacje*. Kod umożliwia kontynuacji ma być wykonywana po poprzedniej, lub *antecedent*, zadanie zostanie ukończone. Wynik zadania poprzedzających jest przekazywany jako dane wejściowe do jednego lub więcej zadań kontynuacji. Po zakończeniu poprzedzających zadań kontynuacji zadań, które oczekują na nim są zaplanowane do uruchomienia. Każde zadanie kontynuacji wysyłana kopia wyniku poprzedzających zadań. Z kolei tych zadań kontynuacji mogą być również poprzedzających zadania dla innych kontynuacje, tworząc łańcuch zadań. Kontynuacje ułatwiają tworzenie łańcuchów o dowolnej długości zadań, które mają określone zależności między nimi. Ponadto zadania mogą uczestniczyć w anulowania przed zadań uruchamia lub w sposób współpracy, jest uruchomiona. Aby uzyskać więcej informacji na temat tego modelu anulowania, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).  
  
 `task` to klasa szablonu. Parametr typu `T` jest typem wyniku, który jest generowany przez zadanie. Tego typu może być `void` Jeśli zadanie nie zwraca wartości. `T` Nie można użyć `const` modyfikator.  
  
 Podczas tworzenia zadania, należy podać *funkcja pracy* wykonująca treść zadania. Funkcja pracy jest dostarczany w formie funkcja lambda, wskaźnik funkcji lub obiekt funkcji. Aby czekać na zakończenie bez uzyskania wynik zadania, należy wywołać [concurrency::task::wait](reference/task-class.md#wait) metody. `task::wait` Metoda zwraca [concurrency::task_status](reference/concurrency-namespace-enums.md#task_group_status) wartość, która opisuje czy zadanie zostało zakończone lub anulowane. Aby uzyskać wynik zadania, należy wywołać [concurrency::task::get](reference/task-class.md#get) metody. Ta metoda wywołuje `task::wait` do poczekaj na zakończenie, a zatem wykonanie bloki bieżącego wątku zadania wynik jest dostępna.  
  
 Poniższy przykład pokazuje, jak utworzyć zadanie, poczekaj na jego wynik i wyświetlić jej wartość. Przykłady w tej dokumentacji Użyj funkcji lambda, ponieważ udostępniają one bardziej zwięzły składni. Jednak umożliwia także wskaźników funkcji i funkcji obiektów korzystając z zadania.  
  
 [!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]  
  

 Jeśli używasz [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) funkcji, można użyć `auto` słowa kluczowego zamiast deklarowanie typu. Rozważmy na przykład tego kodu, które tworzy i wyświetla macierzą:  

  
 [!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]  
  
 Można użyć `create_task` funkcji równoważne operacji tworzenia.  
  
 [!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]  
  
 Jeśli podczas wykonywania zadania jest zgłaszany wyjątek, środowisko uruchomieniowe marshals ten wyjątek w wywołaniu kolejnych `task::get` lub `task::wait`, lub w celu utrzymania opartego na zadaniach. Aby uzyskać więcej informacji dotyczących zadań mechanizm obsługi wyjątków, zobacz [obsługi wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 Na przykład, który używa `task`, [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), anulowania, zobacz [wskazówki: łączenie za pomocą zadań i żądań XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md). ( `task_completion_event` Klasy opisanego w dalszej części tego dokumentu.)  
  
> [!TIP]
>  Aby uzyskać szczegółowe informacje, które są specyficzne dla zadania w aplikacji platformy uniwersalnej systemu Windows, zobacz [asynchronicznego programowania w języku C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) i [tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).  
  
##  <a name="continuations"></a> Zadań kontynuacji  
 W programowanie asynchroniczne jest często stosowane w jednej operacji asynchronicznej, po zakończeniu, aby wywołać operację drugi i przekazywania danych do niej. Zazwyczaj jest to zrobić za pomocą metody wywołania zwrotnego. Współbieżność środowiska wykonawczego, te same funkcje odbywa się przy *zadań kontynuacji*. Zadania kontynuacji (nazywanego także po prostu utrzymania) jest zadanie asynchroniczne, które jest wywoływane przez inne zadanie, znany jako *antecedent*, po zakończeniu antecedent. Przy użyciu kontynuacje, można:  
  
-   Przekazywanie danych z antecedent do kontynuacji.  
  
-   Określ dokładne warunki, w których kontynuacji jest wywoływane lub nie został wywołany.  
  
-   Anuluj utrzymania przed rozpoczęciem lub wspólnie jest uruchomiona.  
  
-   Zawierają wskazówki dotyczące sposobu powinny zostać zaplanowane kontynuacji. (Dotyczy tylko systemu Windows platformy Uniwersalnej aplikacji. Aby uzyskać więcej informacji, zobacz [tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).)  
  
-   Wywołanie wielu kontynuacje z tym samym antecedent.  
  
-   Wywołania kontynuacji jednego, gdy wszystkie lub niektóre z wielu antecedents ukończenia.  
  
-   Łańcuch kontynuacje jeden po drugim do dowolnej długości.  
  
-   Umożliwia obsługi wyjątków, które są generowane przez antecedent utrzymania.  
  
 Te funkcje umożliwiają wykonywanie jednego lub więcej zadań, po zakończeniu pierwszego zadania. Na przykład można utworzyć kontynuacji, który kompresuje plik po pierwszym zadaniem odczytuje go z dysku.  
  


 Poniższy przykład modyfikuje poprzedniego do użycia [concurrency::task::then](reference/task-class.md#then) metodę, aby zaplanować kontynuacji, który wyświetla wartość poprzedzających zadań, gdy jest ona dostępna.  


  
 [!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]  
  
 Można łańcucha i zagnieździć zadań do dowolnej długości. Zadanie może istnieć wiele kontynuacje. Poniższy przykład przedstawia łańcuch kontynuacji podstawowego, który zwiększa wartość poprzedniego zadania trzy razy.  
  
 [!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]  
  
 Kontynuacja może zwrócić również inne zadanie. Jeśli nie ma żadnych anulowania, to zadanie jest wykonywane przed kolejnych kontynuacji. Ta technika jest nazywany *odkodowywania asynchroniczne*. Asynchroniczne odkodowywania jest przydatne, gdy chcesz wykonać dodatkowe czynności w tle, ale nie ma bieżącego zadania, aby zablokować bieżącego wątku. (To jest typowe w aplikacjach platformy uniwersalnej systemu Windows, gdy kontynuacje można uruchomić w wątku interfejsu użytkownika). W poniższym przykładzie przedstawiono trzy zadania. Pierwszym zadaniem zwraca innego zadania, który jest uruchamiany przed zadania kontynuacji.  
  
 [!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]  
  
> [!IMPORTANT]
>  Podczas kontynuacji zadania zwraca zadania zagnieżdżonego typu `N`, wynikowy zadanie ma typ `N`, a nie `task<N>`, a działanie jest kończone po zakończeniu zadania zagnieżdżonego. Innymi słowy kontynuacji wykonuje odkodowywania zadania zagnieżdżonego.  
  
##  <a name="value-versus-task"></a> Na podstawie wartości i Kontynuacje opartego na zadaniach  
 Podane `task` obiektu, którego typ zwracany jest `T`, można podać wartości typu `T` lub `task<T>` do swoich zadań kontynuacji. Kontynuacja, który przyjmuje typ `T` nosi nazwę *na podstawie wartości kontynuacji*. Kontynuacja na podstawie wartości jest zaplanowane do uruchomienia, gdy poprzedzających zadanie zakończy pracę bez błędów i nie została anulowana. Kontynuacja, który przyjmuje typ `task<T>` jako jego parametr nosi nazwę *opartego na zadaniach kontynuacji*. Kontynuacja opartego na zadaniach zawsze jest zaplanowane do uruchomienia po zakończeniu poprzedzających zadań, nawet gdy poprzedzających zadanie zostało anulowane lub zgłasza wyjątek. Następnie można wywołać `task::get` można pobrać wyniku zadania poprzedzających. Jeśli poprzedzających zadanie zostało anulowane, `task::get` zgłasza [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). Jeśli zadanie poprzedzających zwrócił wyjątek, `task::get` ponownie zgłasza ten wyjątek. Kontynuacja opartego na zadaniach nie jest oznaczony jako anulowane podczas jego poprzedzających zadanie zostało anulowane.  
  
##  <a name="composing-tasks"></a> Tworzenie zadań  
 W tej sekcji opisano [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) i [concurrency::when_any](reference/concurrency-namespace-functions.md#when_all) funkcje, które mogą pomóc utworzenie wielu zadań, aby zaimplementować typowe wzorce.  

  
###  <a name="when-all"></a> When_all — funkcja  
 `when_all` Funkcja tworzy zadania kończonego po zakończeniu zestaw zadań. Ta funkcja zwraca wartość odchylenia::[wektor](../../standard-library/vector-class.md) obiekt zawierający wynik każdego zadania w zestawie. W poniższym przykładzie podstawowe `when_all` można utworzyć zadanie reprezentujące zakończenie trzy innych zadań.  
  
 [!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]  
  
> [!NOTE]
>  Zadania, które są przekazywane do `when_all` muszą być jednolite. Innymi słowy muszą one wszystkich zwracać tego samego typu.  
  
 Można również użyć `&&` składnię, aby tworzyć zadania kończonego po zakończeniu zestawu zadań, jak pokazano w poniższym przykładzie.  
  
 `auto t = t1 && t2; // same as when_all`  
  
 Często używać kontynuacji razem z `when_all` do wykonywania akcji po zakończeniu zestaw zadań. Poniższy przykład modyfikuje poprzedniego sumę trzy zadania drukowania każdego utworzyć `int` wynik.  
  
 [!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]  
  
 W tym przykładzie można również określić `task<vector<int>>` wygenerowało utrzymania opartego na zadaniach.  
  
 Jeśli wszystkie zadania w zestawie zadań została anulowana lub zgłasza wyjątek, `when_all` natychmiast kończy i czeka na zakończenie pozostałych zadań. Jeśli wyjątek środowiska uruchomieniowego ponownie zgłasza wyjątek podczas wywoływania `task::get` lub `task::wait` w zadaniu obiekt `when_all` zwraca. Jeśli więcej niż jedno zadanie zgłasza wyjątek, środowisko uruchomieniowe wybiera jeden z nich. W związku z tym upewnij się, można zaobserwować wszystkie wyjątki po zakończeniu wszystkich zadań; zadania nieobsługiwany wyjątek powoduje, że aplikacja zakończyć.  
  
 W tym miejscu to funkcja narzędzia, która służy do zapewnienia, że program przestrzega wszystkie wyjątki. Dla każdego zadania w zakresie podana `observe_all_exceptions` wyzwala żadnych wyjątek, który wystąpił na zgłoszony, a następnie swallows ten wyjątek.  
  
 [!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]  
  
 Należy wziąć pod uwagę aplikacji platformy uniwersalnej systemu Windows, która korzysta z C++ i języka XAML i zapisuje zestawu plików na dysku. Poniższy przykład przedstawia użycie `when_all` i `observe_all_exceptions` aby upewnić się, że program przestrzega wszystkie wyjątki.  
  
 [!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]  
  
##### <a name="to-run-this-example"></a>Do uruchomienia tego przykładu  
  
1.  W MainPage.xaml, Dodaj `Button` formantu.  
  
 [!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]  
  
2.  W MainPage.xaml.h, Dodaj następujące deklaracje do przodu `private` sekcji `MainPage` deklaracji klasy.  
  
 [!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]  
  
3.  W MainPage.xaml.cpp, należy zaimplementować `Button_Click` obsługi zdarzeń.  
  
 [!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]  
  
4.  W MainPage.xaml.cpp, należy zaimplementować `WriteFilesAsync` jak pokazano w przykładzie.  
  
> [!TIP]

> `when_all` to nieblokujące funkcja, która tworzy `task` wyniku. W odróżnieniu od [task::wait](reference/task-class.md#wait), można bezpiecznie wywołanie tej funkcji w aplikacji platformy uniwersalnej systemu Windows w wątku ASTA (STA aplikacji).  

  
###  <a name="when-any"></a> When_any — funkcja  
 `when_any` Funkcja tworzy zadania kończonego po zakończeniu pierwszego zadania w zestawie zadania. Ta funkcja zwraca [std::pair](../../standard-library/pair-structure.md) obiekt zawierający wynik ukończonego zadania i indeks tego zadania w zestawie.  
  
 `when_any` Funkcja jest szczególnie przydatne w następujących scenariuszach:  
  
-   Operacje nadmiarowe. Należy wziąć pod uwagę algorytm lub operację, które mogą być wykonywane na wiele sposobów. Można użyć `when_any` funkcji wybierz operację, którą najpierw zakończy, a następnie Anuluj pozostałych operacji.  
  
-   Operacje z przeplotem. Można uruchomić wiele operacji musi wszystkie Zakończ i użyj `when_any` funkcji do przetwarzania wyników zakończeniu każdej operacji. Po zakończeniu jednej operacji można uruchomić jedno lub więcej dodatkowych zadań.  
  
-   Operacje ograniczane. Można użyć `when_any` funkcji, aby rozszerzyć w poprzednim scenariuszu przez ograniczenie liczby równoczesnych operacji.  
  
-   Wygasłe operacje. Można użyć `when_any` funkcji, aby wybrać jednego lub więcej zadań i zadań, który zakończy się po upływie określonego czasu.  
  
 Jak `when_all`, często do kontynuacji, który ma używać `when_any` do wykonania akcji po zakończeniu pierwszego zestawu zadań. W poniższym przykładzie podstawowe `when_any` Aby utworzyć zadanie, którego działanie jest kończone po zakończeniu pierwszego trzy inne zadania.  
  
 [!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_15.cpp)]  
  
 W tym przykładzie można również określić `task<pair<int, size_t>>` wygenerowało utrzymania opartego na zadaniach.  
  
> [!NOTE]
>  Jak `when_all`, zadań, które są przekazywane do `when_any` musi zwracać taki sam typ.  
  
 Można również użyć `||` składnię, aby tworzyć zadania kończonego po ukończeniu pierwszego zadania w zestawie zadania, jak pokazano w poniższym przykładzie.  
  
 `auto t = t1 || t2; // same as when_any`  
  
> [!TIP]
>  Jak `when_all`, `when_any` jest nieblokujące i bezpiecznie wywołać w aplikacji platformy uniwersalnej systemu Windows w wątku ASTA.  
  
##  <a name="delayed-tasks"></a> Wykonywanie zadań opóźnione  
 Czasami jest to konieczne, umożliwia opóźnienie wykonania zadania, dopóki spełniony jest warunek lub uruchomić zadanie w odpowiedzi na zdarzenie zewnętrzne. Na przykład w programowanie asynchroniczne, trzeba będzie uruchomić zadanie w odpowiedzi na zdarzenia zakończenia We/Wy.  
  
 To zrobić na dwa sposoby powinny używać utrzymania lub uruchomić zadanie i zaczekać na zdarzenie wewnątrz funkcji pracy zadania. Istnieją jednak przypadki, gdy go nie jest możliwe do korzystania z jednego z poniższych metod. Na przykład aby utworzyć kontynuację, musi mieć poprzedzających zadań. Jednak jeśli nie masz poprzedzających zadań, można utworzyć *zdarzenie ukończenia zadania* i później łańcucha zdarzenie ukończenia poprzedzających zadania po ich udostępnieniu. Ponadto ponieważ zadanie oczekiwania blokuje również wątku, można użyć zdarzenia zakończenia zadań do wykonywania pracy po zakończeniu operacji asynchronicznej i wolny w tym samym wątku.  
  
 [Concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) klasa upraszcza kompozycji takich zadań. Podobnie jak `task` klasy parametr typu `T` jest typem wyniku, który jest generowany przez zadanie. Tego typu może być `void` Jeśli zadanie nie zwraca wartości. `T` Nie można użyć `const` modyfikator. Zazwyczaj `task_completion_event` dostarczonego do wątku lub zadanie, które sygnalizowana go po udostępnieniu wartość dla tego obiektu. W tym samym czasie co najmniej jednego zadania są ustawiane jako odbiorników tego zdarzenia. Gdy zdarzenie jest ustawiona, wykonaj zadania odbiornika, a ich kontynuacje są zaplanowane do uruchomienia.  
  
 Na przykład, który używa `task_completion_event` do wykonania zadania kończonego po opóźnieniu, zobacz [porady: Tworzenie zadania takie zakończeniu po opóźnienie](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md).  
  
##  <a name="task-groups"></a> Grupy zadań  
 A *grupy zadań* organizuje kolekcji zadań. Grupy zadań wypychanie zadań do kolejki kradzież pracy. Planista usuwa zadania z tej kolejki i je wykonuje zasobów obliczeniowych dostępnych na. Dodanie zadania do grupy zadań, można poczekać dla wszystkich zadań zakończyć lub anulować zadania, które nie zostały jeszcze uruchomione.  
  
 Używa PPL [concurrency::task_group](reference/task-group-class.md) i [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) klasy do reprezentowania grupy zadań i [concurrency::task_handle](../../parallel/concrt/reference/task-handle-class.md) — klasa do reprezentowania zadania, które będą uruchamiane w tych grupach. `task_handle` Klasa hermetyzuje kod, który wykonuje pracę. Podobnie jak `task` klasy, funkcja pracy jest dostarczany w formie funkcja lambda, wskaźnik funkcji lub obiekt funkcji. Zwykle nie należy do pracy z `task_handle` obiekty bezpośrednio. Zamiast tego przechodzą funkcji pracy do grupy zadań, a grupy zadań tworzy i którymi zarządza `task_handle` obiektów.  
  
 PPL dzieli grupy zadań na tych dwóch kategorii: *grupy zadań niestrukturalnych* i *strukturalne grupy zadań*. Używa PPL `task_group` klasy do reprezentowania grupy bez struktury zadań i `structured_task_group` klasy do reprezentowania strukturalne grupy zadań.  
  
> [!IMPORTANT]

>  Definiuje również PPL [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytmu, który używa `structured_task_group` klasy do wykonywania zestawu zadań równolegle. Ponieważ `parallel_invoke` algorytm ma więcej zwięzły składnię, zaleca się używania jej zamiast `structured_task_group` klasy, jeśli można wykonywać następujące czynności. Temat [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md) opisuje `parallel_invoke` bardziej szczegółowo.  
  
 Użyj `parallel_invoke` gdy masz kilka zadań niezależne, które ma być wykonane w tym samym czasie, i należy poczekać na zakończenie przed kontynuowaniem wszystkich zadań. Ta metoda jest często określany jako *rozwidlenia i sprzężenia* równoległości. Użyj `task_group` gdy masz kilka zadań niezależne, które ma być wykonane w tym samym czasie, ale chcesz czekać na zakończenie w późniejszym czasie zadań. Na przykład można dodać zadania do `task_group` obiektu i poczekaj na zakończenie innej funkcji lub z innego wątku zadań.  
  
 Grupy zadań obsługuje pojęcie anulowania. Anulowanie umożliwia sygnału wszystkie aktywne zadania chcesz anulować operację ogólną. Anulowanie uniemożliwia również zadania, które nie zostały jeszcze uruchomione uruchamianiu. Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).  
  
 Środowisko uruchomieniowe udostępnia model obsługi wyjątków, który umożliwia Zgłoś wyjątek z zadania i obsługiwać ten wyjątek podczas oczekiwania dla grupy zadań skojarzony zakończyć. Aby uzyskać więcej informacji na temat ten model obsługi wyjątków, zobacz [obsługi wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
##  <a name="comparing-groups"></a> Porównywanie task_group do structured_task_group —  
 Mimo że firma Microsoft zaleca użycie `task_group` lub `parallel_invoke` zamiast `structured_task_group` klasy, istnieją przypadki, w której chcesz użyć `structured_task_group`, na przykład podczas zapisu równoległych algorytmu, który wykonuje zmienną liczbę zadań lub wymaga Obsługa anulowania. W tej sekcji wyjaśniono różnice między `task_group` i `structured_task_group` klasy.  
  
 `task_group` Klasa jest bezpieczne wątkowo. W związku z tym można dodać zadania do `task_group` obiektów z wielu wątków i poczekaj lub Anuluj `task_group` obiektu wiele wątków. Konstrukcja i niszczenie `structured_task_group` obiektu musi występować w tym samym zakresie leksykalne. Ponadto wszystkie operacje na `structured_task_group` obiektu muszą odbywać się na tym samym wątku. Wyjątkiem od tej reguły jest [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) i [concurrency::structured_task_group::is_canceling](reference/structured-task-group-class.md#is_canceling) metody. Zadania podrzędnego można wywołać tych metod, aby anulować nadrzędnej grupy zadań lub Wyszukaj anulowania w dowolnym momencie.  
  
 Dodatkowe zadania można uruchamiać na `task_group` obiektu po wywołaniu metody [concurrency::task_group::wait](reference/task-group-class.md#wait) lub [concurrency::task_group::run_and_wait](reference/task-group-class.md#run_and_wait) metody. Z drugiej strony Jeśli dodatkowe zadania zostanie uruchomiony na `structured_task_group` obiektu po wywołaniu metody [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait) lub [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait) metody , to zachowanie jest niezdefiniowany.  
  
 Ponieważ `structured_task_group` klasy nie synchronizuje się pomiędzy wątkami, ma mniej wykonywania narzut niż `task_group` klasy. Dlatego jeśli problemu nie wymaga, aby zaplanować pracę z wielu wątków i nie można użyć `parallel_invoke` algorytmu, `structured_task_group` klasy pomocnych lepsze wykonywanie kodu.  
  
 Jeśli używany jest jeden `structured_task_group` obiektu wewnątrz innego `structured_task_group` obiektu, obiekt wewnętrzny musi zakończyć i niszczone przed zakończeniem obiektu zewnętrznego. `task_group` Klasa nie wymagają grup zagnieżdżonych zadań przed zakończeniem grupy zewnętrznej.  
  
 Grupy zadań niestrukturalnych strukturalne grupy zadań pracować na dojść do zadań na różne sposoby. Można przekazać bezpośrednio do funkcji pracy `task_group` obiekt; `task_group` obiekt utworzy i zarządzać dojście zadań. `structured_task_group` Klasy wymaga zarządzanie `task_handle` obiekt dla każdego zadania. Każdy `task_handle` obiektu musi ważność w okresie istnienia skojarzone `structured_task_group` obiektu. Użyj [concurrency::make_task](reference/concurrency-namespace-functions.md#make_task) funkcja służąca do tworzenia `task_handle` obiektów, jak pokazano w poniższym przykładzie podstawowe:  
  
 [!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]  
  
 Aby zarządzać zadań uchwyty przypadkach, gdy mają różną liczbą zadań, użyj procedury alokacji stosu takich jak [_malloca —](../../c-runtime-library/reference/malloca.md) lub klasę kontenera, takich jak std::[wektor](../../standard-library/vector-class.md).  
  
 Zarówno `task_group` i `structured_task_group` obsługuje anulowania. Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).  
  
##  <a name="example"></a> Przykład  
 Poniższy przykład podstawowa pokazuje, jak pracować z grupy zadań. W tym przykładzie użyto `parallel_invoke` algorytmu do wykonania dwóch zadań jednocześnie. Każde zadanie dodaje podzadania `task_group` obiektu. Należy pamiętać, że `task_group` klasa umożliwia dla wielu zadań jednocześnie dodać zadania do niego.  
  
 [!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]  
  
 Oto przykładowe dane wyjściowe w tym przykładzie:  
  
```Output  
Message from task: Hello  
Message from task: 3.14  
Message from task: 42  
```  
  
 Ponieważ `parallel_invoke` algorytm uruchamia zadania jednocześnie, kolejność komunikaty wyjściowe może się różnić.  
  
 Pełne przykłady, które pokazują, jak używać `parallel_invoke` algorytmu, zobacz [porady: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) i [porady: Korzystanie z parallel_invoke do przeprowadzania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md). Pełny przykład, który używa `task_group` klasy Implementowanie przyszłych operacji asynchronicznej, zobacz [wskazówki: Wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md).  
  
##  <a name="robust"></a> Skuteczne programowanie  
 Upewnij się, że rozumiesz roli anulowania i obsługi wyjątków, korzystając z zadania, grup zadań i algorytmy równoległe. Na przykład drzewa pracy równoległej, zadania, które zostało anulowane zapobiega zadania podrzędne uruchomiona. Może to powodować problemy, jeśli jedno z zadań podrzędnych wykonuje operację, która jest istotne dla aplikacji, takich jak zwalnianie zasobu. Ponadto jeśli zadania podrzędnego zgłasza wyjątek, ten wyjątek może propagację za pośrednictwem destruktor obiektu i spowodować niezdefiniowane zachowanie aplikacji. Na przykład ilustrujący punkty, zobacz [opis sposobu anulowania i wyjątek obsługi wpływają na zniszczeniem obiektu](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) części dokumentu Biblioteka wzorów równoległych — najlepsze praktyki. Aby uzyskać więcej informacji na temat anulowania i modele obsługi wyjątków w PPL, zobacz [anulowania](../../parallel/concrt/cancellation-in-the-ppl.md) i [obsługi wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Przedstawia sposób użycia `parallel_invoke` algorytmu, aby poprawić wydajność bitonic algorytm sortowania.|  
|[Instrukcje: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Przedstawia sposób użycia `parallel_invoke` algorytmu, aby poprawić wydajność program, który wykonuje wiele operacji na udostępnione źródło danych.|  
|[Instrukcje: tworzenie zadania kończonego po opóźnieniu](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Przedstawia sposób użycia `task`, `cancellation_token_source`, `cancellation_token`, i `task_completion_event` klasy Tworzenie zadania kończonego po opóźnieniu.|  
|[Przewodnik: wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md)|Pokazuje, jak połączyć istniejące funkcje współbieżność środowiska wykonawczego na coś nieistniejącego więcej.|  
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|W tym artykule opisano PPL, które zapewnia model programowania konieczne tworzenie współbieżnych aplikacji.|  
  
## <a name="reference"></a>Tematy pomocy  
 [task, klasa (środowisko uruchomieniowe współbieżności)](../../parallel/concrt/reference/task-class.md)  
  
 [task_completion_event, klasa](../../parallel/concrt/reference/task-completion-event-class.md)  

 [when_all — funkcja](reference/concurrency-namespace-functions.md#when_all)  
  
 [when_any — funkcja](reference/concurrency-namespace-functions.md#when_any)  
  
 [task_group — klasa](reference/task-group-class.md)  
  
 [parallel_invoke — funkcja](reference/concurrency-namespace-functions.md#parallel_invoke)  
  
 [structured_task_group, klasa](../../parallel/concrt/reference/structured-task-group-class.md)
