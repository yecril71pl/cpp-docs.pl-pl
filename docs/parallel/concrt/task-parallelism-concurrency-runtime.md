---
title: Równoległość zadania (współbieżność środowiska wykonawczego)
ms.date: 11/04/2016
helpviewer_keywords:
- structured task groups [Concurrency Runtime]
- structured tasks [Concurrency Runtime]
- task groups [Concurrency Runtime]
- task parallelism
- tasks [Concurrency Runtime]
ms.assetid: 42f05ac3-2098-494a-ba84-737fcdcad077
ms.openlocfilehash: f65521771db3eb0fe19dc863b1b49e9627fc60e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368590"
---
# <a name="task-parallelism-concurrency-runtime"></a>Równoległość zadania (współbieżność środowiska wykonawczego)

W czasie wykonywania współbieżności *zadanie* jest jednostką pracy, która wykonuje określone zadanie i zazwyczaj działa równolegle z innymi zadaniami. Zadanie można rozłożyć na dodatkowe, bardziej szczegółowe zadania, które są zorganizowane w *grupę zadań*.

Zadania są używane podczas pisania kodu asynchroniowego i chcesz, aby niektóre operacji występuje po zakończeniu operacji asynchroniczne. Na przykład można użyć zadania do asynchronicznego odczytu z pliku, a następnie użyć innego zadania — *zadania kontynuacji,* które zostało wyjaśnione w dalszej części tego dokumentu — do przetwarzania danych po ich udostępnieniu. Z drugiej strony można użyć grup zadań do rozkładu pracy równoległej na mniejsze kawałki. Załóżmy na przykład, że masz algorytm cykliczny, który dzieli pozostałą pracę na dwie partycje. Grup zadań można używać do jednoczesnego uruchamiania tych partycji, a następnie oczekiwania na zakończenie podzielonej pracy.

> [!TIP]
> Jeśli chcesz zastosować tę samą procedurę do każdego elementu kolekcji równolegle, należy użyć algorytmu równoległego, takiego jak [współbieżność::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), zamiast zadania lub grupy zadań. Aby uzyskać więcej informacji na temat algorytmów równoległych, zobacz [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="key-points"></a>Kwestie kluczowe

- Po przedawaniu zmiennych do wyrażenia lambda przez odwołanie, należy zagwarantować, że okres istnienia tej zmiennej będzie się powtarzał do momentu zakończenia zadania.

- Użyj zadań [(współbieżności::klasa zadań)](../../parallel/concrt/reference/task-class.md) podczas pisania kodu asynchronicznego. Klasa zadań używa usługi Windows ThreadPool jako harmonogramu, a nie środowiska wykonawczego współbieżności.

- Użyj grup zadań [(współbieżności::task_group](reference/task-group-class.md) klasy lub [współbieżności::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytmu), gdy chcesz rozkładać pracę równoległą na mniejsze kawałki, a następnie czekać na te mniejsze kawałki, aby zakończyć.

- Użyj [współbieżności::task::then](reference/task-class.md#then) metody do tworzenia kontynuacji. *Kontynuacja* jest zadaniem, które jest uruchamiane asynchronicznie po zakończeniu innego zadania. Można połączyć dowolną liczbę kontynuacji, tworząc łańcuch pracy asynchroniczowej.

- Kontynuacja oparta na zadaniach jest zawsze zaplanowana do wykonania po zakończeniu zadania poprzedzacza, nawet wtedy, gdy zadanie poprzedzane jest anulowane lub zgłasza wyjątek.

- Użyj [współbieżności::when_all,](reference/concurrency-namespace-functions.md#when_all) aby utworzyć zadanie, które kończy się po zakończeniu każdego członka zestawu zadań. Użyj [współbieżności::when_any,](reference/concurrency-namespace-functions.md#when_any) aby utworzyć zadanie, które kończy się po zakończeniu jednego członka zestawu zadań.

- Zadania i grupy zadań mogą uczestniczyć w mechanizmie anulowania biblioteki wzorców równoległych (PPL). Aby uzyskać więcej informacji, zobacz [Anulowanie w PPL](cancellation-in-the-ppl.md).

- Aby dowiedzieć się, jak środowisko uruchomieniowe obsługuje wyjątki, które są generowane przez zadania i grupy zadań, zobacz [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="in-this-document"></a>W tym dokumencie

- [Korzystając z wyrażenia Lambda](#lambdas)

- [Klasa zadań](#task-class)

- [Zadania kontynuacji](#continuations)

- [Kontynuacje oparte na wartościach i zadaniach](#value-versus-task)

- [Tworzenie zadań](#composing-tasks)

  - [Funkcja when_all](#when-all)

  - [Funkcja when_any](#when-any)

- [Opóźnione wykonanie zadania](#delayed-tasks)

- [Grupy zadań](#task-groups)

- [Porównywanie task_group z structured_task_group](#comparing-groups)

- [Przykład](#example)

- [Niezawodne programowanie](#robust)

## <a name="using-lambda-expressions"></a><a name="lambdas"></a>Używanie wyrażeń Lambda

Ze względu na ich zwięzłą składnię wyrażenia lambda są typowym sposobem definiowania pracy wykonywanej przez zadania i grupy zadań. Oto kilka wskazówek dotyczących użytkowania:

- Ponieważ zadania zazwyczaj są uruchamiane w wątkach w tle, należy pamiętać o okresie istnienia obiektu podczas przechwytywania zmiennych w wyrażeniach lambda. Podczas przechwytywania zmiennej przez wartość, kopia tej zmiennej jest w treści lambda. Podczas przechwytywania przez odwołanie, kopia nie jest wykonana. W związku z tym upewnij się, że okres istnienia dowolnej zmiennej, które można przechwycić przez odwołanie przeżyje zadanie, które go używa.

- Po przedaniu wyrażenia lambda do zadania, nie przechwytuj zmienne, które są przydzielane na stosie przez odwołanie.

- Być jawne o zmiennych przechwytywania w wyrażeniach lambda, dzięki czemu można zidentyfikować, co są przechwytywania przez wartość w porównaniu przez odwołanie. Z tego powodu zaleca się, `[=]` aby `[&]` nie używać lub opcje dla wyrażeń lambda.

Typowy wzorzec jest, gdy jedno zadanie w łańcuchu kontynuacji przypisuje do zmiennej, a inne zadanie odczytuje tę zmienną. Nie można przechwycić według wartości, ponieważ każde zadanie kontynuacji będzie zawierać inną kopię zmiennej. W przypadku zmiennych przydzielonych do stosu nie można również przechwycić przez odwołanie, ponieważ zmienna może nie być już prawidłowa.

Aby rozwiązać ten problem, użyj inteligentnego wskaźnika, takiego jak [std::shared_ptr](../../standard-library/shared-ptr-class.md), aby zawinąć zmienną i przekazać inteligentny wskaźnik według wartości. W ten sposób podstawowy obiekt może być przypisany i odczytać z i przetrwa zadania, które go używają. Tej techniki należy używać nawet wtedy, gdy zmienna`^`jest wskaźnikiem lub uchwytem zliczanym odwołaniem ( ) do obiektu środowiska wykonawczego systemu Windows. Poniżej przedstawiono prosty przykład:

[!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]

Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [Wyrażenia Lambda](../../cpp/lambda-expressions-in-cpp.md).

## <a name="the-task-class"></a><a name="task-class"></a>Klasa zadań

Klasy [współbieżności::task](../../parallel/concrt/reference/task-class.md) można używać do tworzenia zadań w zestawie operacji zależnych. Ten model kompozycji jest wspierany przez pojęcie *kontynuacji*. Kontynuacja umożliwia wykonanie kodu po zakończeniu poprzedniego lub *poprzedzanego*zadania. Wynik zadania poprzedzago jest przekazywany jako dane wejściowe do jednego lub więcej zadań kontynuacji. Po zakończeniu zadania poprzedzago wszystkie zadania kontynuacji, które czekają na niego są zaplanowane do wykonania. Każde zadanie kontynuacji otrzymuje kopię wyniku zadania poprzedzanego. Z kolei te zadania kontynuacji mogą być również zadaniami poprzednio dla innych kontynuacji, tworząc w ten sposób łańcuch zadań. Kontynuacje ułatwiają tworzenie łańcuchów o dowolnej długości zadań, które mają określone zależności między nimi. Ponadto zadanie może uczestniczyć w anulowaniu przed rozpoczęciem zadania lub w sposób kooperacyjny, gdy jest uruchomione. Aby uzyskać więcej informacji na temat tego modelu anulowania, zobacz [Anulowanie w PPL](cancellation-in-the-ppl.md).

`task`jest klasą szablonu. Parametr type `T` jest typem wyniku, który jest wytwarzany przez zadanie. Ten typ `void` może być, jeśli zadanie nie zwraca wartości. `T`nie można `const` użyć modyfikatora.

Podczas tworzenia zadania należy podać *funkcję pracy,* która wykonuje treść zadania. Ta funkcja pracy jest w postaci funkcji lambda, wskaźnik funkcji lub obiektu funkcji. Aby poczekać na zakończenie zadania bez uzyskiwania wyniku, [wywołaj metodę współbieżności::task::wait.](reference/task-class.md#wait) Metoda `task::wait` zwraca [wartość współbieżności::task_status,](reference/concurrency-namespace-enums.md#task_group_status) która opisuje, czy zadanie zostało ukończone, czy anulowane. Aby uzyskać wynik zadania, wywołaj [metodę współbieżności::task::get.](reference/task-class.md#get) Ta metoda `task::wait` wywołuje czekać na zakończenie zadania i w związku z tym blokuje wykonywanie bieżącego wątku, dopóki wynik jest dostępny.

W poniższym przykładzie pokazano, jak utworzyć zadanie, czekać na jego wynik i wyświetlić jego wartość. Przykłady w tej dokumentacji używać funkcji lambda, ponieważ zapewniają one bardziej zwięzłe składni. Jednak można również używać wskaźników funkcji i obiektów funkcji podczas korzystania z zadań.

[!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]

Korzystając z funkcji [współbieżności::create_task,](reference/concurrency-namespace-functions.md#create_task) można użyć `auto` słowa kluczowego zamiast deklarowania typu. Rozważmy na przykład ten kod, który tworzy i drukuje macierz tożsamości:

[!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]

Za pomocą `create_task` tej funkcji można utworzyć równoważną operację.

[!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]

Jeśli wyjątek zostanie zgłoszony podczas wykonywania zadania, środowisko wykonawcze organizuje ten `task::get` `task::wait`wyjątek w kolejnym wywołaniu lub lub kontynuacji opartej na zadaniu. Aby uzyskać więcej informacji na temat mechanizmu obsługi wyjątków zadań, zobacz [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Na przykład użycia `task`argumentów [współbieżności::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), anulowania, zobacz [Przewodnik: Łączenie przy użyciu zadań i żądania HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md). (Klasa `task_completion_event` jest opisana w dalszej części tego dokumentu.

> [!TIP]
> Aby poznać szczegóły specyficzne dla zadań w aplikacjach platformy uniwersalnej systemu Windows, zobacz [Programowanie asynchroniczne w języku C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) i [Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy uniwersalnej systemu Windows.](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)

## <a name="continuation-tasks"></a><a name="continuations"></a>Zadania kontynuacji

W programowaniu asynchroniiowym jest bardzo często dla jednej operacji asynchroniiowej, po zakończeniu, aby wywołać drugą operację i przekazać dane do niego. Tradycyjnie odbywa się to przy użyciu metod wywołania zwrotnego. W czasie wykonywania współbieżności te same funkcje są dostarczane przez *zadania kontynuacji*. Zadanie kontynuacji (znane również jako kontynuacja) jest zadaniem asynchronicznego wywoływanym przez inne zadanie, które jest znane jako *poprzednik,* po zakończeniu antecedent. Za pomocą kontynuacji, można:

- Przekaż dane z poprzednika do kontynuacji.

- Określ dokładne warunki, w których kontynuacja jest wywoływana lub nie wywoływana.

- Anuluj kontynuację przed jej rozpoczęciem lub wspólnie, gdy jest uruchomiona.

- Podaj wskazówki dotyczące sposobu planowania kontynuacji. (Dotyczy to tylko aplikacji platformy uniwersalnej systemu Windows (UWP). Aby uzyskać więcej informacji, zobacz [Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy uniwersalnej systemu Windows.)](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)

- Wywołaj wiele kontynuacji z tego samego poprzednika.

- Wywołaj jedną kontynuację po zakończeniu wszystkich lub dowolnych z wielu poprzedników.

- Kontynuacja łańcucha jeden po drugim na dowolną długość.

- Użyj kontynuacji do obsługi wyjątków, które są generowane przez poprzednika.

Te funkcje umożliwiają wykonanie jednego lub więcej zadań po zakończeniu pierwszego zadania. Na przykład można utworzyć kontynuację, która kompresuje plik po pierwszym zadaniu odczytuje go z dysku.

Poniższy przykład modyfikuje poprzedni, aby użyć [współbieżności::task::then](reference/task-class.md#then) metoda zaplanować kontynuację, która drukuje wartość zadania poprzedzające, gdy jest on dostępny.

[!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]

Zadania można łańcuchować i zagnieżdżać do dowolnej długości. Zadanie może mieć również wiele kontynuacji. Poniższy przykład ilustruje podstawowy łańcuch kontynuacji, który zwiększa wartość poprzedniego zadania trzy razy.

[!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]

Kontynuacja może również zwrócić inne zadanie. Jeśli nie ma anulowania, to zadanie jest wykonywane przed kolejną kontynuacją. Technika ta jest znana jako *asynchroniczne rozpakowanie*. Rozpakowanie asynchroniczne jest przydatne, gdy chcesz wykonać dodatkową pracę w tle, ale nie chcesz, aby bieżące zadanie blokować bieżący wątek. (Jest to typowe w aplikacjach platformy uniwersalnej systemu Windows, gdzie kontynuacje można uruchomić w wątku interfejsu użytkownika). W poniższym przykładzie przedstawiono trzy zadania. Pierwsze zadanie zwraca inne zadanie, które jest uruchamiane przed zadaniem kontynuacji.

[!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]

> [!IMPORTANT]
> Gdy kontynuacja zadania zwraca zagnieżdżone zadanie typu, `N` `N`wynikowe `task<N>`zadanie ma typ , nie i kończy się po zakończeniu zadania zagnieżdżonego. Innymi słowy kontynuacja wykonuje rozpakowywanie zagnieżdżonego zadania.

## <a name="value-based-versus-task-based-continuations"></a><a name="value-versus-task"></a>Kontynuacje oparte na wartościach i zadaniach

Biorąc `task` pod uwagę obiekt, którego typem zwracanym jest `T`, można podać wartość typu `T` lub `task<T>` jego zadań kontynuacji. Kontynuacja, która `T` przyjmuje typ jest znana jako *kontynuacja oparta na wartościach.* Kontynuacja oparta na wartościach jest zaplanowana do wykonania, gdy zadanie poprzedzane zostanie ukończone bez błędu i nie zostanie anulowane. Kontynuacja, która `task<T>` przyjmuje typ jako jego parametr jest znany jako *kontynuacji opartej na zadaniach.* Kontynuacja oparta na zadaniach jest zawsze zaplanowana do wykonania po zakończeniu zadania poprzedzacza, nawet wtedy, gdy zadanie poprzedzane jest anulowane lub zgłasza wyjątek. Następnie można `task::get` wywołać, aby uzyskać wynik zadania poprzedzago. Jeśli zadanie poprzedzacza zostało anulowane, `task::get` odrzuca [współbieżność::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). Jeśli zadanie poprzedzacze zgłosił wyjątek, `task::get` ponownie wydwoje ten wyjątek. Kontynuacja oparta na zadaniach nie jest oznaczona jako anulowana, gdy jej zadanie poprzedzane zostanie anulowane.

## <a name="composing-tasks"></a><a name="composing-tasks"></a>Tworzenie zadań

W tej sekcji opisano [współbieżność::when_all](reference/concurrency-namespace-functions.md#when_all) i [współbieżności::when_any](reference/concurrency-namespace-functions.md#when_all) funkcji, które mogą pomóc w komponowaniu wielu zadań w celu zaimplementowania typowych wzorców.

### <a name="the-when_all-function"></a><a name="when-all"></a>Funkcja when_all

Funkcja `when_all` tworzy zadanie, które kończy się po zakończeniu zestawu zadań. Ta funkcja zwraca obiekt std::[wektorowy,](../../standard-library/vector-class.md) który zawiera wynik każdego zadania w zestawie. Poniższy przykład podstawowy `when_all` używa do utworzenia zadania, które reprezentuje ukończenie trzech innych zadań.

[!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]

> [!NOTE]
> Zadania, które przechodzą `when_all` do muszą być jednolite. Innymi słowy, wszystkie muszą zwracać tego samego typu.

Można również użyć `&&` składni do utworzenia zadania, które kończy się po zakończeniu zestawu zadań, jak pokazano w poniższym przykładzie.

`auto t = t1 && t2; // same as when_all`

Często używa się kontynuacji `when_all` wraz z do wykonywania akcji po zakończeniu zestawu zadań. Poniższy przykład modyfikuje poprzedni, aby wydrukować sumę `int` trzech zadań, z których każde daje wynik.

[!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]

W tym przykładzie można `task<vector<int>>` również określić, aby utworzyć kontynuację opartą na zadaniach.

Jeśli dowolne zadanie w zestawie zadań zostanie anulowane lub zgłosić wyjątek, `when_all` natychmiast kończy i nie czeka na zakończenie pozostałych zadań. Jeśli wyjątek, środowisko uruchomieniowe ponownie uruchamia wyjątek `task::get` `task::wait` podczas wywoływania `when_all` lub na obiekt zadania, który zwraca. Jeśli więcej niż jedno zadanie zostanie uruchomione, środowisko wykonawcze wybierze jeden z nich. W związku z tym upewnij się, że przestrzegasz wszystkich wyjątków po wykonaniu wszystkich zadań; nieobsługiwał wyjątek zadania powoduje, że aplikacja do zakończenia.

Oto funkcja narzędzia, której można użyć, aby upewnić się, że program przestrzega wszystkich wyjątków. Dla każdego zadania w `observe_all_exceptions` podanym zakresie wyzwala dowolny wyjątek, który wystąpił do rethrown, a następnie połyka ten wyjątek.

[!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]

Należy wziąć pod uwagę aplikację platformy uniwersalnej systemu uniwersalnego, która używa języka C++ i XAML i zapisuje zestaw plików na dysku. W poniższym przykładzie `when_all` `observe_all_exceptions` pokazano, jak używać i upewnić się, że program przestrzega wszystkich wyjątków.

[!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]

##### <a name="to-run-this-example"></a>Aby uruchomić ten przykład

1. W pliku MainPage.xaml `Button` dodaj formant.

[!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]

1. W MainPage.xaml.h dodaj te deklaracje `private` do `MainPage` przodu do sekcji deklaracji klasy.

[!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]

1. W mainpage.xaml.cpp zaimplementuj `Button_Click` program obsługi zdarzeń.

[!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]

1. W mainpage.xaml.cpp, `WriteFilesAsync` zaimplementuj jak pokazano w przykładzie.

> [!TIP]
> `when_all`jest funkcją nieblokujną, która daje `task` jako jej wynik. W przeciwieństwie do [zadania::wait](reference/task-class.md#wait), można bezpiecznie wywołać tę funkcję w aplikacji platformy uniwersalnej systemu uniwersalnego w wątku ASTA (Application STA).

### <a name="the-when_any-function"></a><a name="when-any"></a>Funkcja when_any

Funkcja `when_any` tworzy zadanie, które kończy się po zakończeniu pierwszego zadania w zestawie zadań. Ta funkcja zwraca obiekt [std::pair,](../../standard-library/pair-structure.md) który zawiera wynik ukończonego zadania i indeks tego zadania w zestawie.

Funkcja `when_any` jest szczególnie przydatna w następujących scenariuszach:

- Operacje nadmiarowe. Należy wziąć pod uwagę algorytm lub operację, które mogą być wykonywane na wiele sposobów. Za pomocą `when_any` tej funkcji można wybrać operację, która kończy się najpierw, a następnie anulować pozostałe operacje.

- Operacje z przeplotem. Można uruchomić wiele operacji, które muszą `when_any` zakończyć wszystkie i używać funkcji do przetwarzania wyników po zakończeniu każdej operacji. Po zakończeniu jednej operacji można uruchomić jedno lub więcej dodatkowych zadań.

- Operacje ograniczane. Za pomocą `when_any` funkcji można rozszerzyć poprzedni scenariusz, ograniczając liczbę równoczesnych operacji.

- Wygasłe operacje. Za pomocą `when_any` tej funkcji można wybrać jedno lub więcej zadań do zadania, które kończy się po określonym czasie.

Podobnie `when_all`jak w przypadku , jest `when_any` często używać kontynuacji, która musi wykonać akcję po zakończeniu pierwszego w zestawie zadań. Poniższy przykład podstawowy `when_any` używa do utworzenia zadania, które kończy się po zakończeniu pierwszego z trzech innych zadań.

[!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_15.cpp)]

W tym przykładzie można `task<pair<int, size_t>>` również określić, aby utworzyć kontynuację opartą na zadaniach.

> [!NOTE]
> Podobnie `when_all`jak w tym, `when_any` zadania, które przekazujesz, muszą zwracać ten sam typ.

Można również użyć `||` składni do utworzenia zadania, które kończy się po pierwszym zadaniu w zestawie zadań, jak pokazano w poniższym przykładzie.

`auto t = t1 || t2; // same as when_any`

> [!TIP]
> Podobnie `when_all`jak `when_any` w przypadku , nie blokuje się i można bezpiecznie wywołać w aplikacji platformy uniwersalnej systemu i platformy uniwersalnej systemu w wątku ASTA.

## <a name="delayed-task-execution"></a><a name="delayed-tasks"></a>Opóźnione wykonanie zadania

Czasami konieczne jest opóźnienie wykonania zadania, dopóki warunek nie zostanie spełniony, lub uruchomienie zadania w odpowiedzi na zdarzenie zewnętrzne. Na przykład w programowaniu asynchronicznego może być trzeba uruchomić zadanie w odpowiedzi na zdarzenie ukończenia we/wy.

Dwa sposoby, aby to osiągnąć, to użycie kontynuacji lub rozpoczęcia zadania i odczekania zdarzenia wewnątrz funkcji pracy zadania. Istnieją jednak przypadki, w których nie można użyć jednej z tych technik. Na przykład, aby utworzyć kontynuację, musisz mieć zadanie poprzedzane. Jeśli jednak nie masz zadania poprzedzago, możesz utworzyć *zdarzenie ukończenia zadania,* a później utworzyć to zdarzenie ukończenia do zadania poprzedzanego, gdy stanie się dostępne. Ponadto ponieważ zadanie oczekiwania blokuje również wątek, można użyć zdarzeń ukończenia zadania do wykonywania pracy po zakończeniu operacji asynchronicznego, a tym samym zwolnić wątek.

[Współbieżność::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) klasa pomaga uprościć taki skład zadań. Podobnie `task` jak klasa, `T` parametr type jest typem wyniku, który jest produkowany przez zadanie. Ten typ `void` może być, jeśli zadanie nie zwraca wartości. `T`nie można `const` użyć modyfikatora. Zazwyczaj `task_completion_event` obiekt jest dostarczany do wątku lub zadania, które będą sygnalizować go, gdy wartość dla niego staje się dostępna. W tym samym czasie co najmniej jedno zadanie są ustawiane jako detektory tego zdarzenia. Po ustawieniu zdarzenia zadania odbiornika ukończone i ich kontynuacje są zaplanowane do uruchomienia.

Na przykład, który `task_completion_event` używa do zaimplementowania zadania, które kończy się po opóźnieniu, zobacz [Jak: Tworzenie zadania, które kończy się po opóźnieniu](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md).

## <a name="task-groups"></a><a name="task-groups"></a>Grupy zadań

*Grupa zadań* organizuje zbiór zadań. Grupy zadań wypychają zadania do kolejki kradnącej pracę. Harmonogram usuwa zadania z tej kolejki i wykonuje je na dostępnych zasobach obliczeniowych. Po dodaniu zadań do grupy zadań można poczekać na zakończenie wszystkich zadań lub anulowanie zadań, które jeszcze się nie rozpoczęły.

PPL używa [współbieżności::task_group](reference/task-group-class.md) i [współbieżności::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) klas do reprezentowania grup zadań i [współbieżności::task_handle](../../parallel/concrt/reference/task-handle-class.md) klasy do reprezentowania zadań, które są uruchamiane w tych grupach. Klasa `task_handle` hermetyzuje kod, który wykonuje pracę. Podobnie `task` jak klasa, funkcja pracy jest w postaci funkcji lambda, wskaźnik funkcji lub obiektu funkcji. Zazwyczaj nie trzeba pracować z `task_handle` obiektami bezpośrednio. Zamiast tego należy przekazać funkcje pracy do grupy zadań, a `task_handle` grupa zadań tworzy obiekty i zarządza nimi.

PPL dzieli grupy zadań na dwie kategorie: *nieustrukturyzowane grupy zadań* i *zorganizowane grupy zadań*. PPL używa `task_group` klasy do reprezentowania grup zadań nieustrukturyzowanych i `structured_task_group` klasy do reprezentowania grup zadań strukturalnych.

> [!IMPORTANT]
> PPL definiuje również [współbieżność::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytm, który używa `structured_task_group` klasy do wykonywania zestawu zadań równolegle. Ponieważ `parallel_invoke` algorytm ma bardziej zwięzłą składnię, zaleca się, aby używać go zamiast klasy, `structured_task_group` gdy można. W temacie [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md) opisano `parallel_invoke` bardziej szczegółowo.

Użyj, `parallel_invoke` gdy masz kilka niezależnych zadań, które chcesz wykonać w tym samym czasie i należy poczekać na zakończenie wszystkich zadań przed kontynuowaniem. Technika ta jest często określana jako *rozwidla i łączyć* równoległości. Użyj, `task_group` gdy masz kilka niezależnych zadań, które chcesz wykonać w tym samym czasie, ale chcesz poczekać na zakończenie zadań w późniejszym czasie. Na przykład można dodać zadania `task_group` do obiektu i czekać na zakończenie zadań w innej funkcji lub z innego wątku.

Grupy zadań obsługują koncepcję anulowania. Anulowanie umożliwia sygnalizowanie wszystkich aktywnych zadań, które chcesz anulować ogólną operację. Anulowanie zapobiega również uruchamianiu zadań, które jeszcze się nie rozpoczęły. Aby uzyskać więcej informacji na temat anulowania, zobacz [Anulowanie w PPL](cancellation-in-the-ppl.md).

Środowisko wykonawcze udostępnia również model obsługi wyjątków, który umożliwia zgłaszanie wyjątku z zadania i obsługę tego wyjątku po oczekiwaniu na zakończenie skojarzonej grupy zadań. Aby uzyskać więcej informacji na temat tego modelu obsługi wyjątków, zobacz [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="comparing-task_group-to-structured_task_group"></a><a name="comparing-groups"></a>Porównywanie task_group z structured_task_group

Mimo że zaleca `task_group` się `parallel_invoke` użycie lub `structured_task_group` zamiast klasy, istnieją przypadki, `structured_task_group`w których chcesz użyć , na przykład podczas pisania algorytmu równoległego, który wykonuje zmienną liczbę zadań lub wymaga wsparcia anulowania. W tej sekcji wyjaśniono `task_group` `structured_task_group` różnice między klasami i.

Klasa `task_group` jest bezpieczna dla wątków. W związku z tym `task_group` można dodać zadania do obiektu z `task_group` wielu wątków i czekać na lub anulować obiekt z wielu wątków. Budowa i zniszczenie `structured_task_group` obiektu musi odbywać się w tym samym zakresie leksykalne. Ponadto wszystkie operacje na `structured_task_group` obiekcie musi wystąpić w tym samym wątku. Wyjątkiem od tej reguły jest [współbieżność::structured_task_group::anuluj](reference/structured-task-group-class.md#cancel) i [współbieżność::structured_task_group::is_canceling](reference/structured-task-group-class.md#is_canceling) metody. Zadanie podrzędne może wywołać te metody, aby anulować nadrzędną grupę zadań lub sprawdzić, czy anulowanie zostanie anulowane w dowolnym momencie.

Dodatkowe zadania w `task_group` obiekcie można uruchomić po wywołaniu [współbieżności::task_group::wait](reference/task-group-class.md#wait) lub [współbieżności::task_group::run_and_wait](reference/task-group-class.md#run_and_wait) metody. Z drugiej strony, jeśli po `structured_task_group` wywołaniu [współbieżności::structured_task_group::wait](reference/structured-task-group-class.md#wait) lub [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait) metody, zachowanie jest niezdefiniowane.

Ponieważ `structured_task_group` klasa nie synchronizuje między wątkami, ma mniej `task_group` obciążenia wykonania niż klasa. W związku z tym jeśli problem nie wymaga planowania pracy z `parallel_invoke` wielu wątków i nie można użyć algorytmu, `structured_task_group` klasa może pomóc napisać kod lepiej działające.

Jeśli używasz `structured_task_group` jednego `structured_task_group` obiektu wewnątrz innego obiektu, obiekt wewnętrzny musi zakończyć się i zostać zniszczony przed zakończeniem obiektu zewnętrznego. Klasa `task_group` nie wymaga, aby zagnieżdżone grupy zadań kończyły się przed zakończeniem grupy zewnętrznej.

Nieustrukturyzowane grupy zadań i ustrukturyzowane grupy zadań pracują z uchwytami zadań na różne sposoby. Funkcje pracy można przekazać `task_group` bezpośrednio do obiektu; `task_group` obiekt utworzy uchwyt zadania i będzie nim zarządzać. Klasa `structured_task_group` wymaga zarządzania `task_handle` obiektem dla każdego zadania. Każdy `task_handle` obiekt musi pozostać prawidłowy przez `structured_task_group` cały okres istnienia skojarzonego obiektu. Użyj [funkcji współbieżności::make_task,](reference/concurrency-namespace-functions.md#make_task) aby utworzyć `task_handle` obiekt, jak pokazano w poniższym przykładzie podstawowym:

[!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]

Aby zarządzać dojściami zadań w przypadkach, w których masz zmienną liczbę zadań, należy użyć procedury alokacji stosu, takiej jak [_malloca](../../c-runtime-library/reference/malloca.md) lub klasy kontenera, takiej jak std::[vector](../../standard-library/vector-class.md).

Zarówno `task_group` `structured_task_group` i anulowania pomocy technicznej. Aby uzyskać więcej informacji na temat anulowania, zobacz [Anulowanie w PPL](cancellation-in-the-ppl.md).

## <a name="example"></a><a name="example"></a>Przykład

W poniższym przykładzie podstawowym pokazano, jak pracować z grupami zadań. W tym przykładzie używa algorytmu `parallel_invoke` do wykonywania dwóch zadań jednocześnie. Każde zadanie dodaje podzadań do `task_group` obiektu. Należy zauważyć, że `task_group` klasa umożliwia wiele zadań, aby dodać zadania do niego jednocześnie.

[!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]

Oto przykładowe dane wyjściowe w tym przykładzie:

```Output
Message from task: Hello
Message from task: 3.14
Message from task: 42
```

Ponieważ `parallel_invoke` algorytm uruchamia zadania jednocześnie, kolejność komunikatów wyjściowych może się różnić.

Aby uzyskać pełne przykłady, `parallel_invoke` które pokazują, jak korzystać z algorytmu, zobacz [Jak: Użyj parallel_invoke do zapisu procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) i [jak: Użyj parallel_invoke do wykonywania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md). Aby uzyskać pełny przykład, `task_group` który używa klasy do zaimplementowania asynchronicznych futures, zobacz [Instruktaż: Implementowanie futures](../../parallel/concrt/walkthrough-implementing-futures.md).

## <a name="robust-programming"></a><a name="robust"></a>Solidne programowanie

Upewnij się, że rozumiesz rolę anulowania i obsługi wyjątków podczas korzystania z zadań, grup zadań i algorytmów równoległych. Na przykład w drzewie pracy równoległej zadanie, które jest anulowane uniemożliwia uruchamianie zadań podrzędnych. Może to spowodować problemy, jeśli jedno z zadań podrzędnych wykonuje operację, która jest ważna dla aplikacji, takich jak zwalnianie zasobu. Ponadto jeśli zadanie podrzędne zgłasza wyjątek, wyjątek ten może propagować za pośrednictwem destruktora obiektu i powodować niezdefiniowane zachowanie w aplikacji. Na przykład, który ilustruje te punkty, zobacz [Zrozumieć, jak anulowanie i obsługa wyjątków wpływają na zniszczenie obiektu](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) sekcji Najlepsze rozwiązania w dokumencie biblioteki wzorców równoległych. Aby uzyskać więcej informacji na temat modeli anulowania i obsługi wyjątków w PPL, zobacz [anulowanie](../../parallel/concrt/cancellation-in-the-ppl.md) i [obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Porady: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Pokazuje, jak `parallel_invoke` używać algorytmu, aby poprawić wydajność algorytmu sortowania bitonic.|
|[Jak: Użyj parallel_invoke do wykonywania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Pokazuje, jak `parallel_invoke` użyć algorytmu, aby zwiększyć wydajność programu, który wykonuje wiele operacji na udostępnionym źródle danych.|
|[Instrukcje: tworzenie zadania kończonego po opóźnieniu](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Pokazuje, jak `task`używać `cancellation_token_source` `cancellation_token`programu `task_completion_event` , i klas do tworzenia zadania, które kończy się po opóźnieniu.|
|[Przewodnik: wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md)|Pokazuje, jak połączyć istniejące funkcje w środowiskou runtime współbieżności w coś, co robi więcej.|
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|W tym artykule opisano PPL, który zapewnia imperatywne model programowania do tworzenia równoczesnych aplikacji.|

## <a name="reference"></a>Dokumentacja

[Klasa zadania (środowisko uruchomieniowe współbieżności)](../../parallel/concrt/reference/task-class.md)

[Klasa task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)

[Funkcja when_all](reference/concurrency-namespace-functions.md#when_all)

[Funkcja when_any](reference/concurrency-namespace-functions.md#when_any)

[task_group — Klasa](reference/task-group-class.md)

[Funkcja parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)

[Klasa structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)
