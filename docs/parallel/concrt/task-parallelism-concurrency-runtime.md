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
ms.openlocfilehash: c9f18dfd1498538ce3700fd73a27ce6f6088ee42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180046"
---
# <a name="task-parallelism-concurrency-runtime"></a>Równoległość zadania (współbieżność środowiska wykonawczego)

W środowisku uruchomieniowym współbieżności *zadań* jest jednostką pracy, który wykonuje określone zlecenie i zazwyczaj działa równolegle z innymi zadaniami. Zadanie może być rozłożone na zadania dodatkowe, bardziej szczegółowymi zasadami, które są zorganizowane w *grupy zadań*.

Zadania są używane podczas pisania kodu asynchronicznego i chcesz niektóre operacje wystąpiły po zakończeniu operacji asynchronicznej. Na przykład można użyć zadania do asynchronicznego odczytania z pliku, a następnie użyć innego zadania — *zadanie kontynuacji*, co jest opisane w dalszej części tego dokumentu — do przetwarzania danych, gdy stanie się dostępny. Z drugiej strony można użyć grup zadań do rozkładu pracy równolegle na mniejsze części. Na przykład załóżmy, że masz algorytm cykliczny, która dzieli pozostałą pracę na dwie partycje. Grupy zadań umożliwia jednoczesne uruchamianie tych partycji, a następnie poczekaj na zakończenie pracy podzielonej.

> [!TIP]
> Jeśli chcesz stosować taką samą procedurę dla każdego elementu kolekcji równolegle, Użyj algorytmu równoległego, takich jak [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), a nie zadania lub grupy zadań. Aby uzyskać więcej informacji dotyczących algorytmów równoległych, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="key-points"></a>Kwestie kluczowe

- Podczas przekazywania zmiennych do wyrażenia lambda przez odniesienie, musisz gwarantować, że okres istnienia tej zmiennej będzie się powtarzał, zakończenie zadania.

- Używanie zadań ( [concurrency::task](../../parallel/concrt/reference/task-class.md) klasy) podczas wpisywania kodu asynchronicznego. Klasa zadania korzysta z puli wątków Windows jako jego harmonogram, a nie w czasie wykonywania współbieżności.

- Użyj grup zadaniowych ( [concurrency::task_group](reference/task-group-class.md) klasy lub [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytmu) kiedy chcesz rozkładać równoległą pracę na mniejsze kawałki i zaczekaj, aż te mniejsze kawałki zakończą.

- Użyj [CONCURRENCY::Task:: Then](reference/task-class.md#then) metody do tworzenia kontynuacji. A *kontynuacji* jest zadaniem uruchamianym asynchronicznie po zakończeniu innego zadania. Możesz połączyć dowolną liczbę kontynuacji w postaci łańcucha zadań asynchronicznych.

- Kontynuacja oparta na zadaniach zawsze jest zaplanowane do uruchomienia po zakończeniu zadania poprzedzającego, nawet gdy zadanie poprzedzające zostało anulowane lub zgłasza wyjątek.

- Użyj [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) do utworzenia zadania, które kończy się po zakończeniu każdy członek zestawu zadań. Użyj [concurrency::when_any](reference/concurrency-namespace-functions.md#when_any) do utworzenia zadania, które kończy się po zakończeniu jednego z członków zestawu zadań.

- Grupy zadań i mogą uczestniczyć w mechanizmie anulowania biblioteki wzorców równoległych (PPL). Aby uzyskać więcej informacji, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).

- Aby dowiedzieć się, jak środowisko wykonawcze obsługuje wyjątki wyrzucane przez grupy zadań i zadania, zobacz [wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="in-this-document"></a>W tym dokumencie

- [Użycie wyrażeń Lambda](#lambdas)

- [Klasa zadania](#task-class)

- [Zadań kontynuacji](#continuations)

- [Na podstawie wartości w stosunku do kontynuacji opartych na zadaniach](#value-versus-task)

- [Tworzenie zadań](#composing-tasks)

    - [When_all — funkcja](#when-all)

    - [When_any — funkcja](#when-any)

- [Wykonanie opóźnionego zadania](#delayed-tasks)

- [Grupy zadań](#task-groups)

- [Porównywanie task_group z structured_task_group](#comparing-groups)

- [Przykład](#example)

- [Skuteczne programowanie](#robust)

##  <a name="lambdas"></a> Użycie wyrażeń Lambda

Ze względu na ich zwięzłą składnię wyrażenia lambda są typowym sposobem definiowania pracy, która jest wykonywana przez grupy zadań i zadania. Poniżej przedstawiono kilka porad o użyciu:

- Ponieważ zadania zazwyczaj są uruchamiane na wątkach w tle, należy pamiętać o okresie istnienia obiektu podczas przechwytywania zmiennych w wyrażeniach lambda. W przypadku przechwytywania zmiennej według wartości, kopia tej zmiennej jest nawiązywane w treści lambda. W przypadku przechwytywania według odniesienia, kopia nie jest wykonywana. W związku z tym upewnij się, że że okres istnienia dowolnej zmiennej przechwytywania według odniesienia outlives zadanie, które korzysta z niego.

- Jeśli przekazujesz Wyrażenie lambda do zadania, nie Przechwytuj zmiennych, które są przydzielane na stosie przez odwołanie.

- Była niejawna przy korzystaniu zmiennych, które przechwytywania w wyrażeniach lambda, dzięki czemu można zidentyfikować, co udało się przechwycić według wartości i według odwołania. Z tego powodu zaleca się, że nie używasz `[=]` lub `[&]` opcje dla wyrażeń lambda.

Typowym wzorcem jest jedno zadanie w łańcuchu kontynuacji jest przypisywany do zmiennej, gdy inne zadanie odczytuje tę zmienną. Nie można przechwycić według wartości, ponieważ każde zadanie kontynuacji będzie przechowywało inną kopię zmiennej. Dla zmiennych przydzielanych ze stosów również nie przechwytywania według odniesienia, ponieważ zmienna może nie być już prawidłowa.

Aby rozwiązać ten problem, Użyj inteligentnego wskaźnika, takiego jak [std::shared_ptr](../../standard-library/shared-ptr-class.md), aby zawinąć zmienną i przekazać inteligentny wskaźnik przez wartość. W ten sposób obiekt źródłowy można przypisać do odczytywać i będzie on nakreślał zadania, które go używają. Użyj tej techniki, nawet wtedy, gdy zmienna jest wskaźnikiem lub zliczanym uchwytem (`^`) do obiektu Windows Runtime. Poniżej przedstawiono prosty przykład:

[!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]

Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../../cpp/lambda-expressions-in-cpp.md).

##  <a name="task-class"></a> Klasa zadania

Możesz użyć [concurrency::task](../../parallel/concrt/reference/task-class.md) klasy do redagowania zadań w zestaw operacji zależnych. Ten model kompozycji jest obsługiwany przez *kontynuacji*. Kontynuacja umożliwia kodu do wykonania, gdy poprzedniego lub *zadania poprzedzającego*, zadanie zostanie ukończone. Wynik zadania poprzedzającego jest przekazywany jako dane wejściowe do jednego lub kilku zadań kontynuacji. Po zakończeniu zadania poprzedzającego, wszelkie zadania kontynuacji, które na czekają są zaplanowane do wykonania. Każde zadanie utrzymania otrzymuje kopię wyników zadania poprzedzającego. Z kolei te zadania kontynuacji mogą być również zadaniami poprzedzającymi dla innych kontynuacji, tworząc w ten sposób łańcuch zadań. Kontynuacji ułatwiają tworzenie łańcuchów dowolnej długości zadań, które mają szczególne współzależności między nimi. Ponadto zadanie może uczestniczyć w anulowaniu albo przed zadania uruchamiania lub w sposób współpracujący, gdy jest on uruchomiony. Aby uzyskać więcej informacji dotyczących metody anulowania, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).

`task` jest klasą szablonu. Parametr typu `T` to typu wyniku, który jest wytwarzany przez zadanie. Ten typ może być `void` Jeśli zadanie nie zwraca wartości. `T` Nie można użyć `const` modyfikator.

Podczas tworzenia zadania, zapewniają *funkcja pracy* która wykonuje treść zadania. Ta funkcja pracy ma postać funkcji lambda, wskaźnika funkcji lub obiektu funkcji. Aby czekać na zakończenie zadania bez uzyskania wyniku, wywołaj [CONCURRENCY::Task:: wait](reference/task-class.md#wait) metody. `task::wait` Metoda zwraca [concurrency::task_status](reference/concurrency-namespace-enums.md#task_group_status) wartość, która opisuje, czy zadanie zostało ukończone lub anulowane. Aby uzyskać wynik zadania, wywołaj [CONCURRENCY::Task:: GET](reference/task-class.md#get) metody. Ta metoda wywołuje `task::wait` oczekiwania na zakończenie i w związku z tym blokuje wykonanie bieżącego wątku zadania momentu udostępnienia wyniku.

Poniższy przykład pokazuje, jak utworzyć zadanie, czekać na jego wynik i wyświetlić jego wartość. Przykłady w niniejszej dokumentacji Użyj funkcji lambda, ponieważ zapewniają one bardziej zwięzłą składnię. Jednak umożliwia także wskaźników funkcji i obiektów funkcji podczas korzystania z zadań.

[!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]

Kiedy używasz [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) funkcji, można użyć `auto` słowa kluczowego zamiast deklarowania typu. Na przykład rozważmy ten kod, który tworzy i drukuje macierz tożsamości:

[!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]

Możesz użyć `create_task` funkcję, aby utworzyć operację równoważną.

[!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]

Jeśli wyjątek zostanie zgłoszony podczas wykonywania zadania, środowisko uruchomieniowe kieruje ten wyjątek w następnym wywołaniu do metody `task::get` lub `task::wait`, lub do kontynuacji opartego na zadaniach. Aby uzyskać więcej informacji na temat zadań mechanizmu obsługi wyjątków, zobacz [wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Aby uzyskać przykład, który używa `task`, [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), anulowania, zobacz [instruktażu: Łączenie za pomocą zadań i żądań XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md). ( `task_completion_event` Klasy jest opisane w dalszej części tego dokumentu.)

> [!TIP]
>  Aby uzyskać szczegółowe informacje, które są specyficzne dla zadań w aplikacjach platformy uniwersalnej systemu Windows, zobacz [asynchronicznego programowania w języku C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) i [tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

##  <a name="continuations"></a> Zadań kontynuacji

W programowaniu asynchronicznych jest częste jedna operacja asynchroniczna po zakończeniu wywołuje drugą operację i przekazuje dane do niej. Tradycyjnie odbywa się przy użyciu metod wywołania zwrotnego. W środowisku uruchomieniowym współbieżności taką samą funkcjonalność świadczą *zadań kontynuacji*. Zadanie kontynuacji (znane również jako kontynuacja) to asynchroniczne zadanie, które jest wywoływane przez inne zadanie, który jest znany jako *zadania poprzedzającego*, po jego zakończeniu. Korzystając z kontynuacji, możesz wykonywać następujące czynności:

- Przekazywanie danych od zadania poprzedzającego do kontynuacji.

- Określ dokładne warunki, na jakich kontynuacja jest lub nie jest wywoływana.

- Anuluj kontynuację albo przed jej rozpoczęciem albo w trakcie jest uruchomiona.

- Dostarczanie wskazówek na temat jak kontynuacja powinna zostać zaplanowana. (Dotyczy to tylko aplikacji uniwersalnych platformy Windows (UWP). Aby uzyskać więcej informacji, zobacz [tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).)

- Wywoływanie wielu kontynuacji z tego samego zadania poprzedzającego.

- Wywołanie jednej kontynuacji po ukończeniu wszystkich lub dowolnego z wielu zadań poprzedzających.

- Kontynuacje łańcucha kolejno jeden po drugim do dowolnej długości.

- Użyj kontynuacji, aby obsłużyć wyjątki wyrzucane przez element poprzedzający.

Te funkcje umożliwiają wykonanie co najmniej jedno zadanie po zakończeniu pierwszego zadania. Na przykład można utworzyć kontynuację, która kompresuje plik, gdy pierwsze zadanie odczyta go z dysku.

Poniższy przykład modyfikuje poprzedni, aby użyć [CONCURRENCY::Task:: Then](reference/task-class.md#then) metodę, aby zaplanować kontynuację, która drukuje wartość zadania poprzedzającego, gdy będzie ona dostępna.

[!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]

Można połączyć i zagnieździć zadania do dowolnej długości. Zadanie może też mieć wiele kontynuacji. Poniższy przykład ilustruje podstawową kontynuację łańcucha, który zwiększa wartość poprzedniego zadania trzy razy.

[!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]

Kontynuacja może również zwracać inne zadanie. Jeśli nie ma żadnego anulowania, to zadanie jest wykonywane przed kolejną kontynuacją. Ta technika jest znana jako *rozpakowanie asynchroniczne*. Rozpakowanie asynchroniczne jest przydatne, gdy chcesz wykonać dodatkową pracę w tle, ale nie ma bieżącego zadania, aby zablokować bieżącego wątku. (To jest typowe w aplikacjach platformy UWP, gdzie kontynuacje można uruchomić na wątku interfejsu użytkownika). Poniższy przykład ukazuje trzy zadania. Pierwsze zadanie zwraca inne zadanie, które jest uruchamiane przed kontynuacją zadania.

[!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]

> [!IMPORTANT]
>  Kiedy kontynuacja zadania zwraca zagnieżdżone zadanie typu `N`, wynikowe zadanie ma typ `N`, a nie `task<N>`i kończy po zakończeniu zadania zagnieżdżonego. Innymi słowy kontynuacja wykonuje rozpakowanie zagnieżdżonego zadania.

##  <a name="value-versus-task"></a> Na podstawie wartości w stosunku do kontynuacji opartych na zadaniach

Biorąc pod uwagę `task` obiektu, którego typem zwracanym jest `T`, należy podać wartość typu `T` lub `task<T>` do jego zadań kontynuacji. Kontynuacja, która ma typ `T` jest znany jako *kontynuacja oparta na wartościach*. Kontynuacja oparta na wartościach jest zaplanowana do wykonania, gdy poprzedzające zadanie zakończy się bez błędów i nie zostało anulowane. Kontynuacja, która ma typ `task<T>` jako parametr, jest znana jako *kontynuację opartą na zadaniach*. Kontynuacja oparta na zadaniach zawsze jest zaplanowane do uruchomienia po zakończeniu zadania poprzedzającego, nawet gdy zadanie poprzedzające zostało anulowane lub zgłasza wyjątek. Następnie możesz wywołać `task::get` Aby uzyskać wynik zadania poprzedzającego. Jeśli zadanie poprzedzające zostało anulowane, `task::get` zgłasza [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). Jeśli zadanie poprzedzające zgłosiło wyjątek, `task::get` ponownie zgłasza ten wyjątek. Kontynuacja oparta na zadaniach nie jest oznaczona jako anulowana po anulowaniu zadania poprzedzającego.

##  <a name="composing-tasks"></a> Tworzenie zadań

W tej sekcji opisano [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) i [concurrency::when_any](reference/concurrency-namespace-functions.md#when_all) funkcji, które mogą pomóc w komponowaniu wielu zadań do realizacji typowych wzorców.

###  <a name="when-all"></a> When_all — funkcja

`when_all` Funkcja tworzy zadanie, które kończy się po wykonaniu zestawu zadań. Ta funkcja zwraca std::[wektor](../../standard-library/vector-class.md) obiektu, który zawiera wynik każdego zadania w zestawie. Poniższy przykład podstawowy używa `when_all` do utworzenia zadania, które reprezentuje ukończenie trzech innych zadań.

[!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]

> [!NOTE]
>  Zadania, które są przekazywane do `when_all` muszą być jednolite. Innymi słowy muszą one wszystkie zwracać ten sam typ.

Można również użyć `&&` Składnia służąca do tworzenia zadania, które kończy się po wykonaniu zestawu zadań, jak pokazano w poniższym przykładzie.

`auto t = t1 && t2; // same as when_all`

Jest często używa się kontynuacji wraz z `when_all` do wykonania akcji po zakończeniu zestawu zadań. Poniższy przykład modyfikuje poprzedni, aby drukować sumę trzech zadań każde produkuje `int` wynik.

[!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]

W tym przykładzie można również określić `task<vector<int>>` do wygenerowania kontynuacji opartej na zadaniach.

Jeśli dowolne zadanie w zestawie zadań zostanie anulowane lub zgłasza wyjątek, `when_all` natychmiast kończy działanie i nie czeka na zakończenie pozostałych zadań. Jeśli wyjątek jest zgłaszany, środowisko uruchomieniowe ponownie zgłasza wyjątek podczas wywoływania `task::get` lub `task::wait` dla obiektu zadania, które `when_all` zwraca. Jeśli więcej niż jedno zadanie zgłasza, środowisko uruchomieniowe wybiera jeden z nich. W związku z tym upewnij się, że przestrzegasz wszystkich wyjątków, po zakończeniu wszystkich zadań; nieobsłużony wyjątek zadania powoduje zakończenie działania aplikacji.

W tym miejscu jest funkcja narzędziowa, której można użyć, aby upewnić się, że program odczytuje wszystkie wyjątki. Dla każdego zadania z podanego zakresu `observe_all_exceptions` wyzwala każdy wyjątek, który wystąpił, jest zgłaszany ponownie, a następnie obiekt.

[!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]

Należy wziąć pod uwagę aplikacji platformy uniwersalnej systemu Windows, która korzysta z C++ i XAML i zapisuje zbiór plików na dysku. Poniższy przykład pokazuje, jak używać `when_all` i `observe_all_exceptions` aby upewnić się, że program rejestruje wszystkie wyjątki.

[!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]

##### <a name="to-run-this-example"></a>Aby uruchomić ten przykład

1. W pliku MainPage.xaml Dodaj `Button` kontroli.

[!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]

1. W pliku MainPage.xaml.h należy dodać te deklaracje przechodzenia do przodu do `private` części `MainPage` deklaracji klasy.

[!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]

1. W pliku MainPage.xaml.cpp zaimplementuj `Button_Click` programu obsługi zdarzeń.

[!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]

1. W pliku MainPage.xaml.cpp zaimplementuj `WriteFilesAsync` jak pokazano w przykładzie.

> [!TIP]
> `when_all` jest funkcją bez blokowania tworzącego `task` jako wynik. W odróżnieniu od [Task::wait —](reference/task-class.md#wait), można bezpiecznie wywołać tę funkcję w aplikacji platformy uniwersalnej systemu Windows w wątku ASTA (aplikacja STA).

###  <a name="when-any"></a> When_any — funkcja

`when_any` Funkcja tworzy zadanie, które kończy się po zakończeniu pierwszego zadania w zestawie zadań. Ta funkcja zwraca [std::pair](../../standard-library/pair-structure.md) obiekt, który zawiera wynik ukończonego zadania i indeks tego zadania w zestawie.

`when_any` Funkcja jest szczególnie użyteczna w następujących scenariuszach:

- Operacje nadmiarowe. Należy wziąć pod uwagę algorytm lub operację, które mogą być wykonywane na wiele sposobów. Możesz użyć `when_any` funkcję, aby wybrać operację, która zakończy się pierwsza, a następnie anulować pozostałe operacje.

- Operacje z przeplotem. Można uruchomić wiele operacji, że muszą się zakończyć i używać `when_any` funkcji do przetwarzania wyników, po zakończeniu każdej operacji. Po zakończeniu jednej operacji można uruchomić jedno lub więcej dodatkowych zadań.

- Operacje ograniczane. Możesz użyć `when_any` funkcję, aby rozszerzyć poprzedni scenariusz poprzez ograniczenie liczby operacji jednoczesnych.

- Wygasłe operacje. Możesz użyć `when_any` funkcję, aby wybrać jedno lub więcej zadań i zadań, który kończy się po określonym czasie.

Podobnie jak w przypadku `when_all`, jest często używa się kontynuacji wraz z obiektem `when_any` do wykonania akcji po zakończeniu pierwszego zestawu zadań. Poniższy przykład podstawowy używa `when_any` Tworzenie zadania kończonego po zakończeniu pierwszego dnia trzech innych zadań.

[!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_15.cpp)]

W tym przykładzie można również określić `task<pair<int, size_t>>` do wygenerowania kontynuacji opartej na zadaniach.

> [!NOTE]
> Podobnie jak w przypadku `when_all`, zadania, które są przekazywane do `when_any` musi zwracać tego samego typu.

Można również użyć `||` Składnia służąca do tworzenia zadania, które kończy się po zakończeniu pierwszego zadania w zestawie zadań, jak pokazano w poniższym przykładzie.

`auto t = t1 || t2; // same as when_any`

> [!TIP]
> Podobnie jak w przypadku `when_all`, `when_any` jest bez blokowania i jest bezpieczny do wywołania w aplikacji platformy uniwersalnej systemu Windows w wątku ASTA.

##  <a name="delayed-tasks"></a> Wykonanie opóźnionego zadania

Czasami konieczne jest opóźnienie wykonania zadania, dopóki nie zostanie spełniony jakiś warunek, lub uruchomić zadanie w odpowiedzi na zdarzenie zewnętrzne. Na przykład w asynchronicznym programowaniu może być konieczne uruchomienie zadania w odpowiedzi na zdarzenie zakończenia operacji We/Wy.

Są dwa sposoby na osiągnięcie tego celu to kontynuacja lub na uruchomienie zadania i Oczekiwanie na zdarzenie wewnątrz funkcji pracy zadania podrzędnego. Jednakże istnieją przypadki, gdy nie jest możliwe użycie jednej z poniższych metod. Na przykład aby utworzyć kontynuację, musi mieć zadanie poprzedzające. Jednakże, jeśli nie masz zadania poprzedzającego, możesz utworzyć *zdarzenie zakończenia zadania* i później połączyć to zdarzenie zakończenia zadania poprzedzającego, gdy stanie się dostępna. Ponadto ponieważ zadanie oczekujące blokuje również wątek, można użyć zdarzeń zakończenia zadania do wykonywania pracy po zakończeniu operacji asynchronicznej, a efekcie zwolnić wątek.

[Concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) klasy pomaga uprościć taki skład zadań. Podobnie jak `task` klasy, parametr typu `T` to typu wyniku, który jest wytwarzany przez zadanie. Ten typ może być `void` Jeśli zadanie nie zwraca wartości. `T` Nie można użyć `const` modyfikator. Zazwyczaj `task_completion_event` obiektu jest udostępniane na wątku lub zadania, które wyda sygnał, gdy wartość dla niego stanie się dostępna. W tym samym czasie co najmniej jednego zadania są ustawiane jako detektory zdarzenia. Gdy zdarzenie jest ustawione, kończą się zadania odbiornika a ich kontynuacje są planowane do uruchomienia.

Aby uzyskać przykład, który używa `task_completion_event` do zaimplementowania zadania kończonego po opóźnieniu, zobacz [jak: Tworzenie zadania kończonego po opóźnieniu](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md).

##  <a name="task-groups"></a> Grupy zadań

A *grupy zadań* organizuje zbiory zadań. Grupy zadań wypychają zadania do kolejki przechwytywania pracy. Harmonogram usuwa zadania z tej kolejki i wykonuje je na dostępnych zasobach komputerowych. Po dodaniu zadań do grupy zadań możesz poczekać, aż wszystkie zadania zakończyć lub anulowania zadania, które nie zostały rozpoczęte.

PPL korzysta [concurrency::task_group](reference/task-group-class.md) i [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) klasy do reprezentowania grup zadań i [concurrency::task_handle](../../parallel/concrt/reference/task-handle-class.md) klasy do reprezentowania zadań uruchamianych w tych grupach. `task_handle` Klasa hermetyzuje kod, który wykonuje pracę. Podobnie jak `task` klasy, ta funkcja pracy ma postać funkcji lambda, wskaźnika funkcji lub obiektu funkcji. Zazwyczaj nie trzeba pracować z `task_handle` obiektów. Zamiast tego funkcje robocze są przekazywane do grupy zadań, a grupa zadań tworzy i którymi zarządza `task_handle` obiektów.

PPL dzieli grupy zadań na dwie kategorie: *grupy zadań bez struktury* i *ze strukturą grup zadań*. PPL korzysta `task_group` klasy do reprezentowania grup zadań bez struktury i `structured_task_group` klasy do reprezentowania grup zadań strukturalnych.

> [!IMPORTANT]
> PPL definiuje również [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytmu, który używa `structured_task_group` klasy do wykonywania zestawu zadań równolegle. Ponieważ `parallel_invoke` algorytm ma bardziej zwięzłą składnię, zaleca się używać go zamiast `structured_task_group` klasy miarę. Temat [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md) opisuje `parallel_invoke` bardziej szczegółowo.

Użyj `parallel_invoke` kiedy masz kilka niezależnych zadań, które mają zostać zrealizowane w tym samym czasie i musisz poczekać na zakończenie przed kontynuowaniem wszystkich zadań. Ta technika jest często nazywany *rozwidlenia i sprzężenia* równoległości. Użyj `task_group` kiedy masz kilka niezależnych zadań, które mają zostać zrealizowane w tym samym czasie, ale chcesz czekać na zadania zakończyć w późniejszym czasie. Na przykład można dodać zadania do `task_group` obiektu i poczekaj na zakończenie innej funkcji lub z innego wątku zadań.

Grupy zadań obsługują koncepcję anulowania. Anulowanie umożliwia zasygnalizowanie wszystkim aktywnym zadaniom, chcesz anulować operację ogólną. Anulowanie zapobiega także zadaniom, które nie zostały rozpoczęte od uruchamiania. Aby uzyskać więcej informacji dotyczących anulowania, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).

Środowisko wykonawcze zapewnia również model obsługi wyjątków, który umożliwia zgłoszenie wyjątku z zadania i obsługę tego wyjątku podczas oczekiwania dla skojarzonej grupy zadań na zakończenie. Aby uzyskać więcej informacji na temat tego modelu obsługi wyjątków, zobacz [wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

##  <a name="comparing-groups"></a> Porównywanie task_group z structured_task_group

Mimo że zaleca się, że używasz `task_group` lub `parallel_invoke` zamiast `structured_task_group` klasy, są przypadki, w której chcesz użyć `structured_task_group`, na przykład podczas wpisywania algorytmu równoległego, który wykonuje liczbę zmiennych zadań lub wymaga Obsługa anulowania. W tej sekcji opisano różnice między `task_group` i `structured_task_group` klasy.

`task_group` Klasa jest metodą o bezpiecznych wątkach. W związku z tym można dodawać zadania do `task_group` obiektów z wielu wątków i czekać lub anulować `task_group` obiektów z wielu wątków. Budowa i niszczenie obiektu `structured_task_group` musi występować w tym samym zakresie leksykalnym. Ponadto wszystkie operacje na `structured_task_group` musi występować w tym samym wątku. Wyjątkiem od tej reguły jest [CONCURRENCY::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) i [CONCURRENCY::structured_task_group:: is_canceling](reference/structured-task-group-class.md#is_canceling) metody. Zadanie podrzędne może wywoływać te metody, aby anulować grupę nadrzędną zadań lub sprawdzić anulowanie w dowolnym momencie.

Możesz przeprowadzić dodatkowe zadania na `task_group` obiektu po wywołaniu metody [CONCURRENCY::task_group:: wait](reference/task-group-class.md#wait) lub [CONCURRENCY::task_group:: run_and_wait](reference/task-group-class.md#run_and_wait) metody. Z drugiej strony po uruchomieniu zadań dodatkowych na `structured_task_group` obiektu po wywołaniu metody [CONCURRENCY::structured_task_group:: wait](reference/structured-task-group-class.md#wait) lub [CONCURRENCY::structured_task_group::](reference/structured-task-group-class.md#run_and_wait) metody , a następnie zachowanie jest niezdefiniowane.

Ponieważ `structured_task_group` klasy nie synchronizuje między wątkami, ma ona mniejsze obciążenie niż `task_group` klasy. W związku z tym, jeśli problem nie wymaga planowania pracy z wielu wątków i nie można użyć `parallel_invoke` algorytm `structured_task_group` klasy mogą ułatwić tworzenie lepiej zachowującego się kodu.

Jeśli używany jest jeden `structured_task_group` obiektu wewnątrz innego `structured_task_group` obiektu, obiekt wewnętrzny zakończyć działanie i zostać zniszczone przed zakończeniem działania obiektu zewnętrznego. `task_group` Klasy nie wymaga zagnieżdżonych grup zadań na zakończenie przed zakończeniem prac przez grupę zewnętrzną.

Grupy zadań bez struktury i zadania strukturalnych pracują z programami do obsługi zadań w różny sposób. Możesz przekazać funkcje pracy bezpośrednio do `task_group` obiektu `task_group` obiektu będzie tworzył i zarządzał obsługi zadań dla Ciebie. `structured_task_group` Klasy, musisz zarządzać `task_handle` obiekt dla każdego zadania. Każdy `task_handle` obiektu musi zachować ważność przez cały okres istnienia związanego z nim `structured_task_group` obiektu. Użyj [concurrency::make_task](reference/concurrency-namespace-functions.md#make_task) funkcji, aby utworzyć `task_handle` obiektu, jak pokazano w poniższym przykładzie podstawowe:

[!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]

Aby zarządzać programami do obsługi zadań dla przypadków, w których mają zmienną liczbę zadań, użyj procedury alokacji stosu takich jak [_malloca](../../c-runtime-library/reference/malloca.md) lub klasy kontenera, takich jak std::[wektor](../../standard-library/vector-class.md).

Zarówno `task_group` i `structured_task_group` obsługują anulowania. Aby uzyskać więcej informacji dotyczących anulowania, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).

##  <a name="example"></a> Przykład

Poniższy przykład podstawowy pokazuje, jak pracować z grupami zadań. W tym przykładzie użyto `parallel_invoke` algorytmu do wykonywania dwóch zadań jednocześnie. Każde zadanie dodaje podzadania `task_group` obiektu. Należy pamiętać, że `task_group` klasa umożliwia dodanie jednocześnie wielu zadań.

[!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]

Poniżej przedstawiono przykładowe dane wyjściowe, w tym przykładzie:

```Output
Message from task: Hello
Message from task: 3.14
Message from task: 42
```

Ponieważ `parallel_invoke` algorytm uruchamia zadania jednocześnie, kolejność komunikatów wyjściowych może być inna.

Aby uzyskać kompletny przykład przedstawiający sposób użycia `parallel_invoke` algorytmu, zobacz [jak: Używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) i [jak: Używanie parallel_invoke do operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md). Aby uzyskać kompletny przykład, który używa `task_group` klasy, aby zaimplementować funkcje asynchroniczne, zobacz [instruktażu: Wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md).

##  <a name="robust"></a> Skuteczne programowanie

Upewnij się, że rozumiesz rolę anulowania i obsługi wyjątków, kiedy używasz zadań, grup zadań i algorytmów równoległych. Na przykład w drzewie równoległej pracy zadanie, które zostało anulowane zapobiega zadań podrzędnych uruchamianiu. Może to powodować problemy, jeśli jedno z zadań podrzędnych wykonuje operację, która jest ważna dla aplikacji, taką jak zwalnianie zasobu. Ponadto jeśli zadanie podrzędne zgłasza wyjątek, ten wyjątek może propagować przez destruktora obiektu i spowodować niezdefiniowane zachowanie w aplikacji. Na przykład, który ilustruje te punkty, zobacz [opis sposobu anulowania i wyjątków obsługi wpływają na zniszczenie obiektu](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) sekcji najlepszych praktykach w dokumencie Biblioteka równoległych wzorców. Aby uzyskać więcej informacji na temat anulowania i modele obsługi wyjątków w PPL, zobacz [anulowania](../../parallel/concrt/cancellation-in-the-ppl.md) i [wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Ilustruje sposób używania `parallel_invoke` algorytmu, aby zwiększyć wydajność algorytmu sortowania bitonicznego.|
|[Instrukcje: wykonywanie operacji równoległych za pomocą elementu Parallel.Invoke](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Ilustruje sposób używania `parallel_invoke` algorytmu, aby zwiększyć wydajność programu, który wykonuje wiele operacji na udostępnione źródło danych.|
|[Instrukcje: tworzenie zadania kończonego po opóźnieniu](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Ilustruje sposób używania `task`, `cancellation_token_source`, `cancellation_token`, i `task_completion_event` klasy, aby tworzenie zadania kończonego po opóźnieniu.|
|[Przewodnik: wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md)|Pokazuje, jak połączyć istniejącą funkcje w środowisku uruchomieniowym współbieżności w coś, ma większe.|
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|W tym artykule opisano PPL, która udostępnia model programowania do tworzenia aplikacji współbieżnych.|

## <a name="reference"></a>Tematy pomocy

[task, klasa (środowisko uruchomieniowe współbieżności)](../../parallel/concrt/reference/task-class.md)

[task_completion_event, klasa](../../parallel/concrt/reference/task-completion-event-class.md)

[when_all — funkcja](reference/concurrency-namespace-functions.md#when_all)

[when_any — funkcja](reference/concurrency-namespace-functions.md#when_any)

[task_group, klasa](reference/task-group-class.md)

[parallel_invoke Function](reference/concurrency-namespace-functions.md#parallel_invoke)

[structured_task_group, klasa](../../parallel/concrt/reference/structured-task-group-class.md)
