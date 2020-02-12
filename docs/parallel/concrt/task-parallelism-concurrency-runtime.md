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
ms.openlocfilehash: 634b4b584e997007a7de72e23c9b16e937a694ae
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143318"
---
# <a name="task-parallelism-concurrency-runtime"></a>Równoległość zadania (współbieżność środowiska wykonawczego)

W środowisko uruchomieniowe współbieżności *zadanie* jest jednostką pracy, która wykonuje określone zadanie i zazwyczaj działa równolegle z innymi zadaniami. Zadanie może być rozłożone na dodatkowe, bardziej szczegółowe zadania, które są zorganizowane w *grupie zadań*.

Podczas pisania kodu asynchronicznego należy używać zadań, które należy wykonać po zakończeniu operacji asynchronicznej. Można na przykład użyć zadania do asynchronicznego odczytu z pliku, a następnie użyć innego zadania — *zadania kontynuacji*, które zostało wyjaśnione w dalszej części tego dokumentu — w celu przetworzenia danych po ich udostępnieniu. Z kolei można użyć grup zadań do rozkładu pracy równoległej na mniejsze części. Załóżmy na przykład, że masz algorytm cykliczny dzielący pozostałą część pracy na dwie partycje. Możesz użyć grup zadań, aby uruchomić te partycje współbieżnie, a następnie poczekać na ukończenie podzielonej pracy.

> [!TIP]
> Aby zastosować tę samą procedurę do każdego elementu kolekcji równolegle, należy użyć algorytmu równoległego, takiego jak [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for), zamiast zadania lub grupy zadań. Aby uzyskać więcej informacji na temat algorytmów równoległych, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="key-points"></a>Kwestie kluczowe

- Gdy zmienne są przekazywane do wyrażenia lambda przez odwołanie, należy zagwarantować, że okres istnienia tej zmiennej będzie trwały do momentu zakończenia zadania.

- Użyj zadań (Klasa [concurrency:: Task](../../parallel/concrt/reference/task-class.md) ), gdy piszesz kod asynchroniczny. Klasa Task używa puli wątków systemu Windows jako harmonogramu, a nie środowisko uruchomieniowe współbieżności.

- Używaj grup zadań (klasy [concurrency:: task_group](reference/task-group-class.md) lub algorytmu [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) ), jeśli chcesz rozłożyć równoległą pracę na mniejsze fragmenty, a następnie poczekaj na ukończenie tych mniejszych fragmentów.

- Użyj metody [concurrency:: Task:: then](reference/task-class.md#then) , aby utworzyć kontynuacje. *Kontynuacja* to zadanie, które jest uruchamiane asynchronicznie po zakończeniu innego zadania. Możesz połączyć dowolną liczbę kontynuacji, aby utworzyć łańcuch pracy asynchronicznej.

- Kontynuacja oparta na zadaniach jest zawsze planowana do wykonania po zakończeniu zadania poprzedzającego, nawet gdy zadanie poprzedzające zostało anulowane lub zgłosi wyjątek.

- Użyj [concurrency:: when_all](reference/concurrency-namespace-functions.md#when_all) , aby utworzyć zadanie, które kończy się po zakończeniu każdego elementu członkowskiego zestawu zadań. Użyj [concurrency:: when_any](reference/concurrency-namespace-functions.md#when_any) , aby utworzyć zadanie, które kończy się po zakończeniu jednego elementu członkowskiego zestawu zadań.

- Zadania i grupy zadań mogą uczestniczyć w mechanizmie anulowania biblioteki równoległych wzorców (PPL). Aby uzyskać więcej informacji, zobacz [anulowania w PPL](cancellation-in-the-ppl.md).

- Aby dowiedzieć się, jak środowisko uruchomieniowe obsługuje wyjątki, które są zgłaszane przez zadania i grupy zadań, zobacz [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="in-this-document"></a>W tym dokumencie

- [Używanie wyrażeń lambda](#lambdas)

- [Klasa zadania](#task-class)

- [Zadania kontynuacji](#continuations)

- [Kontynuacja oparta na wartościach w porównaniu z zadaniami](#value-versus-task)

- [Tworzenie zadań](#composing-tasks)

    - [Funkcja when_all](#when-all)

    - [Funkcja when_any](#when-any)

- [Opóźnione wykonywanie zadania](#delayed-tasks)

- [Grupy zadań](#task-groups)

- [Porównywanie task_group z structured_task_group](#comparing-groups)

- [Przykład](#example)

- [Niezawodne programowanie](#robust)

## <a name="lambdas"></a>Używanie wyrażeń lambda

Ze względu na ich zwięzłą składnię wyrażenia lambda są typowym sposobem definiowania pracy wykonywanej przez zadania i grupy zadań. Poniżej przedstawiono niektóre porady dotyczące użycia:

- Ponieważ zadania są zwykle uruchamiane w wątkach w tle, należy pamiętać o okresie istnienia obiektu podczas przechwytywania zmiennych w wyrażeniach lambda. Podczas przechwytywania zmiennej według wartości, kopia tej zmiennej jest wprowadzana w treści lambda. Gdy przechwytujesz według odwołania, kopia nie jest wykonywana. W związku z tym upewnij się, że okres istnienia każdej zmiennej, która jest przechwytywana przez odwołanie, zawiera zadanie, które go używa.

- Gdy przekazujesz wyrażenie lambda do zadania, nie Przechwytuj zmiennych, które są przydzielone na stosie przez odwołanie.

- Być jawne o zmiennych, które są przechwytywane w wyrażeniach lambda, aby można było zidentyfikować przechwycenie według wartości, a nie przez odwołanie. Z tego powodu zalecamy, aby nie używać opcji `[=]` ani `[&]` dla wyrażeń lambda.

Typowy wzorzec polega na tym, że jedno zadanie w łańcuchu kontynuacji przypisuje do zmiennej, a inne zadanie odczytuje tę zmienną. Nie można przechwycić według wartości, ponieważ każde zadanie kontynuacji będzie przechowywać inną kopię zmiennej. W przypadku zmiennych przypisywanych ze stosu nie można przechwycić przez odwołanie, ponieważ zmienna może nie być już prawidłowa.

Aby rozwiązać ten problem, Użyj inteligentnego wskaźnika, takiego jak [std:: shared_ptr](../../standard-library/shared-ptr-class.md), aby otoczyć zmienną i przekazać inteligentny wskaźnik przez wartość. W ten sposób obiekt źródłowy może zostać przypisany do i odczytany z i będzie zawierać zadania, które go używają. Tej techniki należy używać nawet wtedy, gdy zmienna jest wskaźnikiem lub dojściem do zliczania odwołań (`^`) do obiektu środowisko wykonawcze systemu Windows. Oto podstawowy przykład:

[!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]

Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](../../cpp/lambda-expressions-in-cpp.md).

## <a name="task-class"></a>Klasa zadania

Można użyć klasy [concurrency:: Task](../../parallel/concrt/reference/task-class.md) , aby utworzyć zadania w zestawie operacji zależnych. Ten model kompozycji jest obsługiwany przez pojęcie *kontynuacji*. Kontynuacja umożliwia wykonanie kodu po zakończeniu poprzedniego lub *poprzedzającego*zadania. Wynik zadania poprzedzającego jest przenoszona jako dane wejściowe do co najmniej jednego zadania kontynuacji. Po zakończeniu zadania poprzedzającego zaplanowano wykonanie wszystkich zadań kontynuacji, które czekają na nią. Każde zadanie kontynuacji otrzymuje kopię wyniku zadania poprzedzającego. Z kolei te zadania kontynuacji mogą również być zadaniami poprzedzającymi dla innych kontynuacji, tworząc łańcuch zadań. Kontynuacje ułatwiają tworzenie łańcuchów zadań o dowolnej długości, które mają określone zależności między nimi. Ponadto zadanie może uczestniczyć w anulowaniu przed rozpoczęciem wykonywania zadań lub w trakcie współpracy w trakcie jego działania. Aby uzyskać więcej informacji na temat tego modelu anulowania, zobacz [anulowania w PPL](cancellation-in-the-ppl.md).

`task` jest klasą szablonu. Parametr typu `T` jest typem wyniku, który jest generowany przez zadanie. Ten typ może być `void`, jeśli zadanie nie zwraca wartości. `T` nie może używać modyfikatora `const`.

Podczas tworzenia zadania należy dostarczyć *funkcję roboczą* , która wykonuje treść zadania. Ta funkcja pracy ma postać funkcji lambda, wskaźnika funkcji lub obiektu funkcji. Aby poczekać na zakończenie zadania bez uzyskania wyniku, wywołaj metodę [concurrency:: Task:: wait](reference/task-class.md#wait) . Metoda `task::wait` zwraca wartość [concurrency:: task_status](reference/concurrency-namespace-enums.md#task_group_status) , która opisuje, czy zadanie zostało ukończone lub anulowane. Aby uzyskać wynik zadania, wywołaj metodę [concurrency:: Task:: Get](reference/task-class.md#get) . Ta metoda wywołuje `task::wait`, aby poczekać na zakończenie zadania, i w związku z tym blokuje wykonywanie bieżącego wątku do momentu dostępności wyniku.

Poniższy przykład pokazuje, jak utworzyć zadanie, poczekać na jego wynik i wyświetlić jego wartość. Przykłady w tej dokumentacji używają funkcji lambda, ponieważ zapewniają bardziej zwięzłą składnię. Można jednak używać wskaźników funkcji i obiektów funkcyjnych podczas korzystania z zadań.

[!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]

Używając funkcji [concurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) , można użyć słowa kluczowego `auto` zamiast deklaracji typu. Rozważmy na przykład ten kod, który tworzy i drukuje macierz tożsamości:

[!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]

Za pomocą funkcji `create_task` można utworzyć równoważną operację.

[!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]

Jeśli wyjątek jest zgłaszany podczas wykonywania zadania, środowisko uruchomieniowe będzie organizować ten wyjątek w następnym wywołaniu do `task::get` lub `task::wait`lub do kontynuacji opartej na zadaniach. Aby uzyskać więcej informacji na temat mechanizmu obsługi wyjątków zadań, zobacz [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Aby zapoznać się z przykładem, który używa `task`, [concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), anulowania, zobacz [Przewodnik: Łączenie przy użyciu zadań i żądań HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md). (Klasa `task_completion_event` została opisana w dalszej części tego dokumentu).

> [!TIP]
> Aby dowiedzieć się więcej o szczegółach dotyczących zadań w aplikacjach platformy UWP, zobacz [programowanie C++ asynchroniczne w](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) i [Tworzenie asynchronicznych operacji w programie C++ dla aplikacji platformy UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

## <a name="continuations"></a>Zadania kontynuacji

W programowaniu asynchronicznym jest bardzo powszechna dla jednej operacji asynchronicznej po zakończeniu, aby wywołać drugą operację i przekazać do niej dane. Tradycyjnie jest to realizowane przy użyciu metod wywołania zwrotnego. W środowisko uruchomieniowe współbieżności te same funkcje są udostępniane przez *zadania kontynuacji*. Zadanie kontynuacji (znane również jako kontynuacja) to asynchroniczne zadanie, które jest wywoływane przez inne zadanie, znane jako *poprzedzające*, po ukończeniu poprzedzającego. Korzystając z kontynuacji, można:

- Przekaż dane z Antecedent do kontynuacji.

- Określ dokładne warunki, w których kontynuacja jest wywoływana lub nie została wywołana.

- Anuluj kontynuację albo przed jej rozpoczęciem lub w trakcie jej działania.

- Podaj wskazówki dotyczące sposobu, w jaki kontynuacja powinna zostać zaplanowana. (Dotyczy to tylko aplikacji platforma uniwersalna systemu Windows (platformy UWP). Aby uzyskać więcej informacji, zobacz [Tworzenie operacji asynchronicznych w programie C++ for platformy UWP Apps](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)).

- Wywoływanie wielu kontynuacji z tego samego poprzedzającego.

- Wywołanie jednej kontynuacji po ukończeniu wszystkich lub dowolnego z wielu poprzedników.

- Łańcuch jest kontynuowany jeden po drugim do dowolnej długości.

- Użyj kontynuacji, aby obsłużyć wyjątki, które są generowane przez poprzedzające.

Te funkcje umożliwiają wykonywanie co najmniej jednego zadania, gdy pierwsze zadanie zostało zakończone. Można na przykład utworzyć kontynuację, która kompresuje plik, gdy pierwsze zadanie odczytuje go z dysku.

Poniższy przykład modyfikuje poprzedni, aby użyć metody [concurrency:: Task:: then](reference/task-class.md#then) , aby zaplanować kontynuację, która drukuje wartość zadania poprzedzającego, gdy jest ono dostępne.

[!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]

Zadania można tworzyć łańcuchowo i zagnieżdżać. Zadanie może mieć również wiele kontynuacji. Poniższy przykład ilustruje podstawowy łańcuch kontynuacji, który zwiększa wartość poprzedniego zadania trzykrotnie.

[!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]

Kontynuacja może również zwracać inne zadanie. Jeśli nie ma żadnych anulowania, to zadanie jest wykonywane przed kolejną kontynuacją. Ta technika jest nazywana *asynchronicznym rozwinięciem*. Odpakowanie asynchroniczne jest przydatne, gdy chcesz wykonać dodatkowe prace w tle, ale nie chcesz, aby bieżące zadanie blokowało bieżący wątek. (Jest to typowe w aplikacjach platformy UWP, w których kontynuacje mogą być uruchamiane w wątku interfejsu użytkownika). Poniższy przykład przedstawia trzy zadania. Pierwsze zadanie zwraca kolejne zadanie, które jest uruchamiane przed wykonaniem zadania kontynuacji.

[!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]

> [!IMPORTANT]
> Gdy kontynuacja zadania zwraca zagnieżdżone zadanie typu `N`, wynikowe zadanie ma typ `N`, nie `task<N>`i kończy się po zakończeniu zadania zagnieżdżonego. Innymi słowy kontynuacja wykonuje odpakowanie zadania zagnieżdżonego.

## <a name="value-versus-task"></a>Kontynuacja oparta na wartościach w porównaniu z zadaniami

Mając `task` obiekt, którego typem zwracanym jest `T`, można podać wartość typu `T` lub `task<T>` do swoich zadań kontynuacji. Kontynuacja, która przyjmuje typ `T` jest znana jako *kontynuacja oparta na wartości*. Kontynuacja oparta na wartości jest zaplanowana do wykonania, gdy zadanie poprzedzające zakończy działanie bez błędu i nie zostało anulowane. Kontynuacja, która przyjmuje typ `task<T>`, ponieważ jego parametr jest znany jako *kontynuacja oparta na zadaniach*. Kontynuacja oparta na zadaniach jest zawsze planowana do wykonania po zakończeniu zadania poprzedzającego, nawet gdy zadanie poprzedzające zostało anulowane lub zgłosi wyjątek. Następnie można wywołać `task::get`, aby uzyskać wynik zadania poprzedzającego. Jeśli zadanie poprzedzające zostało anulowane, `task::get` generuje [concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md). Jeśli zadanie poprzedzające wywołało wyjątek, `task::get` ponownie zgłosi ten wyjątek. Kontynuacja oparta na zadaniach nie jest oznaczona jako anulowana, gdy zadanie poprzedzające zostało anulowane.

## <a name="composing-tasks"></a>Tworzenie zadań

W tej sekcji opisano funkcje [concurrency:: when_all](reference/concurrency-namespace-functions.md#when_all) i [concurrency:: when_any](reference/concurrency-namespace-functions.md#when_all) , które mogą pomóc w tworzeniu wielu zadań w celu zaimplementowania wspólnych wzorców.

### <a name="when-all"></a>Funkcja when_all

Funkcja `when_all` generuje zadanie, które kończy się po zakończeniu zestawu zadań. Ta funkcja zwraca obiekt std::[Vector](../../standard-library/vector-class.md) , który zawiera wynik każdego zadania w zestawie. Poniższy przykład podstawowy używa `when_all` do utworzenia zadania, które reprezentuje ukończenie trzech innych zadań.

[!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]

> [!NOTE]
> Zadania przekazane do `when_all` muszą być jednorodne. Innymi słowy, muszą one zwracać ten sam typ.

Możesz również użyć składni `&&`, aby utworzyć zadanie, które kończy się po ukończeniu zestawu zadań, jak pokazano w poniższym przykładzie.

`auto t = t1 && t2; // same as when_all`

Aby wykonać akcję po zakończeniu zestawu zadań, często należy używać kontynuacji razem z `when_all`. Poniższy przykład modyfikuje poprzednią, aby wydrukować sumę trzech zadań, które generują wynik `int`.

[!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]

W tym przykładzie można także określić `task<vector<int>>`, aby utworzyć kontynuację opartą na zadaniach.

Jeśli dowolne zadanie w zestawie zadań zostanie anulowane lub zgłosi wyjątek, `when_all` natychmiastowe zakończenie i nie czeka na zakończenie pozostałych zadań. Jeśli wystąpi wyjątek, środowisko uruchomieniowe ponownie zgłasza wyjątek podczas wywoływania `task::get` lub `task::wait` w obiekcie zadania, który `when_all` zwraca. W przypadku wyrzucania więcej niż jednego zadania środowisko uruchomieniowe wybiera jeden z nich. W związku z tym upewnij się, że wszystkie wyjątki zostały zaobserwuje po zakończeniu wszystkich zadań; nieobsługiwany wyjątek zadania powoduje przerwanie działania aplikacji.

Oto funkcja narzędziowa, której można użyć, aby upewnić się, że program obserwuje wszystkie wyjątki. Dla każdego zadania z podanego zakresu `observe_all_exceptions` wyzwala wszelkie wyjątki, które wystąpiły do ponownej zgłoszenia, a następnie przypadają na ten wyjątek.

[!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]

Rozważ użycie aplikacji platformy UWP, która C++ używa języka XAML i zapisuje zestaw plików na dysku. Poniższy przykład pokazuje, jak używać `when_all` i `observe_all_exceptions`, aby upewnić się, że program obserwuje wszystkie wyjątki.

[!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]

##### <a name="to-run-this-example"></a>Aby uruchomić ten przykład

1. W MainPage. XAML Dodaj formant `Button`.

[!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]

1. W MainPage. XAML. h Dodaj te deklaracje przesyłania dalej do sekcji `private` deklaracji klasy `MainPage`.

[!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]

1. W MainPage. XAML. cpp Zaimplementuj procedurę obsługi zdarzeń `Button_Click`.

[!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]

1. W pliku MainPage. XAML. cpp Zaimplementuj `WriteFilesAsync` jak pokazano w przykładzie.

> [!TIP]
> `when_all` jest funkcją nieblokującą, która generuje `task` jako wynik. W przeciwieństwie do [zadania:: czekaj](reference/task-class.md#wait), można bezpiecznie wywołać tę funkcję w aplikacji platformy UWP w wątku ASTA (Application sta).

### <a name="when-any"></a>Funkcja when_any

Funkcja `when_any` generuje zadanie, które kończy się po zakończeniu pierwszego zadania w zestawie zadań. Ta funkcja zwraca obiekt [powietrza std::p](../../standard-library/pair-structure.md) , który zawiera wynik zadania zakończonego i indeks tego zadania w zestawie.

Funkcja `when_any` jest szczególnie przydatna w następujących scenariuszach:

- Operacje nadmiarowe. Należy wziąć pod uwagę algorytm lub operację, które mogą być wykonywane na wiele sposobów. Można użyć funkcji `when_any`, aby wybrać operację, która zakończy się w pierwszej kolejności, a następnie anulować pozostałe operacje.

- Operacje z przeplotem. Można uruchomić wiele operacji, które wszystkie muszą zakończyć, i użyć funkcji `when_any`, aby przetwarzać wyniki po zakończeniu każdej operacji. Po zakończeniu jednej operacji można uruchomić jedno lub więcej dodatkowych zadań.

- Operacje ograniczane. Można użyć funkcji `when_any`, aby zwiększyć poprzedni scenariusz, ograniczając liczbę współbieżnych operacji.

- Wygasłe operacje. Za pomocą funkcji `when_any` można wybrać jedno lub więcej zadań i zadanie, które zakończy się po określonym czasie.

Podobnie jak w przypadku `when_all`, powszechne jest użycie kontynuacji, która ma `when_any` do wykonania akcji, gdy pierwszy w zestawie zadań zakończy się. Poniższy przykład podstawowy używa `when_any`, aby utworzyć zadanie, które kończy się po wykonaniu pierwszego z trzech innych zadań.

[!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_15.cpp)]

W tym przykładzie można także określić `task<pair<int, size_t>>`, aby utworzyć kontynuację opartą na zadaniach.

> [!NOTE]
> Podobnie jak w przypadku `when_all`, zadania przekazane do `when_any` muszą zwracać ten sam typ.

Możesz również użyć składni `||`, aby utworzyć zadanie, które kończy się po wykonaniu pierwszego zadania w zestawie zadań, jak pokazano w poniższym przykładzie.

`auto t = t1 || t2; // same as when_any`

> [!TIP]
> Podobnie jak w przypadku `when_all`, `when_any` nie jest blokowaniem i jest bezpiecznie do wywołania w aplikacji platformy UWP w wątku ASTA.

## <a name="delayed-tasks"></a>Opóźnione wykonywanie zadania

Czasami trzeba opóźnić wykonywanie zadania do momentu spełnienia warunku lub uruchomić zadanie w odpowiedzi na zdarzenie zewnętrzne. Na przykład w programowaniu asynchronicznym może być konieczne uruchomienie zadania w odpowiedzi na zdarzenie zakończenia operacji we/wy.

Dwa sposoby osiągnięcia tego celu to użycie kontynuacji lub uruchomienie zadania i oczekiwanie na zdarzenie wewnątrz funkcji pracy zadania. Istnieją jednak przypadki, w których nie można użyć jednej z tych technik. Na przykład, aby utworzyć kontynuację, musisz mieć zadanie poprzedzające. Niemniej jednak, jeśli nie masz zadania poprzedzającego, możesz utworzyć *zdarzenie ukończenia zadania* i później łańcucha, który uzupełnia zadanie poprzedzające, gdy stanie się dostępne. Ponadto, ponieważ zadanie oczekujące blokuje także wątek, można użyć zdarzeń ukończenia zadania do wykonywania pracy po zakończeniu operacji asynchronicznej i tym samym Zwolnij wątek.

Klasa [concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) pomaga uprościć takie składanie zadań. Podobnie jak Klasa `task`, parametr typu `T` jest typem wyniku wytwarzanego przez zadanie. Ten typ może być `void`, jeśli zadanie nie zwraca wartości. `T` nie może używać modyfikatora `const`. Zazwyczaj obiekt `task_completion_event` jest dostarczany do wątku lub zadania, które będą sygnalizować, gdy wartość zostanie udostępniona. W tym samym czasie co najmniej jedno zadanie jest ustawione jako detektory tego zdarzenia. Po ustawieniu zdarzenia zadania odbiornika są wykonywane, a ich kontynuacje są zaplanowane do uruchomienia.

Aby zapoznać się z przykładem, który używa `task_completion_event`, aby zaimplementować zadanie, które kończy się po opóźnieniu, zobacz [How to: Create a zadanie, które kończy się po opóźnieniu](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md).

## <a name="task-groups"></a>Grupy zadań

*Grupa zadań* organizuje kolekcję zadań. Grupy zadań wypychania zadań do kolejki kradzieży pracy. Harmonogram usuwa zadania z tej kolejki i wykonuje je na dostępnych zasobach obliczeniowych. Po dodaniu zadań do grupy zadań możesz poczekać na zakończenie wszystkich zadań lub anulować zadania, które nie zostały jeszcze uruchomione.

PPL używa klas [concurrency:: task_group](reference/task-group-class.md) i [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) do reprezentowania grup zadań, a klasa [concurrency:: task_handle](../../parallel/concrt/reference/task-handle-class.md) do reprezentowania zadań, które są uruchamiane w tych grupach. Klasa `task_handle` hermetyzuje kod, który wykonuje prace. Podobnie jak w przypadku klasy `task`, funkcja pracy znajduje się w postaci funkcji lambda, wskaźnika funkcji lub obiektu funkcji. Zazwyczaj nie trzeba bezpośrednio korzystać z obiektów `task_handle`. Zamiast tego należy przekazać funkcje pracy do grupy zadań, a grupa zadań tworzy obiekty `task_handle` i zarządza nimi.

PPL dzieli grupy zadań na te dwie kategorie: *grupy zadań bez struktury* i *strukturalne grupy zadań*. PPL używa klasy `task_group` do reprezentowania grup zadań bez struktury i klasy `structured_task_group` do reprezentowania grup zadań ze strukturą.

> [!IMPORTANT]
> PPL definiuje również algorytm [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) , który używa klasy `structured_task_group` do równoległego wykonywania zestawu zadań. Ponieważ algorytm `parallel_invoke` ma bardziej zwięzłą składnię, zalecamy użycie jej zamiast klasy `structured_task_group`. [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md) opisują `parallel_invoke` bardziej szczegółowo.

Użyj `parallel_invoke`, gdy masz kilka niezależnych zadań, które chcesz wykonać w tym samym czasie, i musisz poczekać na zakończenie wszystkich zadań przed kontynuowaniem. Ta technika jest często określana jako *rozwidlenie i przyłączanie* równoległości. Użyj `task_group`, gdy masz kilka niezależnych zadań, które chcesz wykonać w tym samym czasie, ale chcesz poczekać na zakończenie wykonywania zadań w późniejszym czasie. Na przykład można dodać zadania do obiektu `task_group` i poczekać na zakończenie zadań w innej funkcji lub z innego wątku.

Grupy zadań obsługują koncepcję anulowania. Anulowanie umożliwia zasygnalizowanie wszystkim aktywnym zadaniom, które mają anulować operację ogólną. Anulowanie uniemożliwia również Uruchamianie zadań, które jeszcze nie rozpoczęły się. Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowania w PPL](cancellation-in-the-ppl.md).

Środowisko uruchomieniowe udostępnia również model obsługi wyjątków, który umożliwia zgłoszenie wyjątku z zadania i obsługę tego wyjątku podczas oczekiwania na zakończenie skojarzonej grupy zadań. Aby uzyskać więcej informacji na temat tego modelu obsługi wyjątków, zobacz [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="comparing-groups"></a>Porównywanie task_group z structured_task_group

Chociaż zalecamy używanie `task_group` lub `parallel_invoke` zamiast klasy `structured_task_group`, istnieją przypadki, w których chcesz użyć `structured_task_group`, na przykład podczas pisania algorytmu równoległego, który wykonuje zmienną liczbę zadań lub wymaga obsługi anulowania. W tej sekcji opisano różnice między klasami `task_group` i `structured_task_group`.

Klasa `task_group` jest bezpieczna wątkowo. W związku z tym można dodać zadania do obiektu `task_group` z wielu wątków i zaczekać lub anulować obiekt `task_group` z wielu wątków. Konstrukcja i zniszczenie obiektu `structured_task_group` muszą wystąpić w tym samym zakresie leksykalnym. Ponadto wszystkie operacje na obiekcie `structured_task_group` muszą wystąpić w tym samym wątku. Wyjątkiem od tej reguły jest metoda [concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) i [concurrency:: structured_task_group:: is_canceling](reference/structured-task-group-class.md#is_canceling) . Zadanie podrzędne może wywoływać te metody, aby anulować nadrzędną grupę zadań lub sprawdzić w dowolnym momencie anulowanie.

Po wywołaniu metody [concurrency:: task_group:: wait](reference/task-group-class.md#wait) lub [concurrency:: task_group:: run_and_wait](reference/task-group-class.md#run_and_wait) można uruchomić dodatkowe zadania na obiekcie `task_group`. Natomiast w przypadku uruchamiania dodatkowych zadań na obiekcie `structured_task_group` po wywołaniu metody [concurrency:: structured_task_group:: wait](reference/structured-task-group-class.md#wait) lub [concurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait) , zachowanie jest niezdefiniowane.

Ponieważ Klasa `structured_task_group` nie synchronizuje się między wątkami, ma mniej nakładów wykonywania niż Klasa `task_group`. W związku z tym, jeśli problem nie wymaga zaplanowania pracy z wielu wątków i nie można użyć algorytmu `parallel_invoke`, Klasa `structured_task_group` może pomóc napisać lepszy kod wykonywany.

Jeśli używasz jednego `structured_task_group` obiektu w innym obiekcie `structured_task_group`, obiekt wewnętrzny musi zakończyć się i zostać zniszczony przed zakończeniem zewnętrznego obiektu. Klasa `task_group` nie wymaga, aby zagnieżdżone grupy zadań kończyły się przed zakończeniem grupy zewnętrznej.

Grupy zadań bez struktury i uporządkowane grupy zadań współpracują z uchwytami zadań na różne sposoby. Funkcje pracy można przekazać bezpośrednio do obiektu `task_group`; Obiekt `task_group` będzie tworzyć i zarządzać uchwytem zadania. Klasa `structured_task_group` wymaga zarządzania obiektem `task_handle` dla każdego zadania. Każdy obiekt `task_handle` musi pozostać ważny przez cały okres istnienia skojarzonego obiektu `structured_task_group`. Użyj funkcji [concurrency:: make_task](reference/concurrency-namespace-functions.md#make_task) , aby utworzyć obiekt `task_handle`, jak pokazano w następującym przykładzie podstawowym:

[!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]

Aby zarządzać dojściami zadań w przypadku, gdy masz zmienną liczbę zadań, użyj procedury alokacji stosu, takiej jak [_malloca](../../c-runtime-library/reference/malloca.md) lub klasy kontenera, takiej jak std::[Vector](../../standard-library/vector-class.md).

Zarówno `task_group`, jak i `structured_task_group` obsługa anulowania. Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowania w PPL](cancellation-in-the-ppl.md).

## <a name="example"></a>Przyklad

Poniższy przykład podstawowy przedstawia sposób pracy z grupami zadań. W tym przykładzie zastosowano algorytm `parallel_invoke`, aby wykonać dwa zadania współbieżnie. Każde zadanie dodaje podzadania podrzędne do obiektu `task_group`. Należy zauważyć, że Klasa `task_group` umożliwia wielu zadań, aby jednocześnie dodawać do niej zadania.

[!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]

Poniżej przedstawiono przykładowe dane wyjściowe dla tego przykładu:

```Output
Message from task: Hello
Message from task: 3.14
Message from task: 42
```

Ponieważ algorytm `parallel_invoke` uruchamia zadania współbieżnie, kolejność komunikatów wyjściowych może się różnić.

Aby zapoznać się z kompletnymi przykładami, które pokazują, jak używać algorytmu `parallel_invoke`, zobacz [How to: use parallel_invoke, aby napisać równoległą procedurę sortowania](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) i [instrukcje: używanie Parallel_invoke do wykonywania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md). Aby zapoznać się z kompletnym przykładem, który używa klasy `task_group` do implementowania asynchronicznych operacji futures, zobacz [Przewodnik: implementowanie przyszłych](../../parallel/concrt/walkthrough-implementing-futures.md).

## <a name="robust"></a>Niezawodne programowanie

Upewnij się, że rozumiesz rolę anulowania i obsługi wyjątków podczas korzystania z zadań, grup zadań i algorytmów równoległych. Na przykład w drzewie pracy równoległej zadanie, które zostało anulowane, uniemożliwia uruchomienie zadań podrzędnych. Może to spowodować problemy, jeśli jedno z zadań podrzędnych wykonuje operację, która jest ważna dla aplikacji, na przykład zwalniając zasób. Ponadto, jeśli zadanie podrzędne zgłasza wyjątek, ten wyjątek może być propagowany przez destruktor obiektu i spowodować niezdefiniowane zachowanie w aplikacji. Aby zapoznać się z przykładem, który ilustruje te punkty, zobacz sekcję [Informacje o sposobie anulowania i obsługi wyjątków, które mają wpływ na niszczenie obiektów](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) w najlepszych rozwiązaniach w dokumencie Biblioteka wzorców równoległych. Więcej informacji o modelach anulowania i obsługi wyjątków w PPL można znaleźć w temacie [Anulowanie](../../parallel/concrt/cancellation-in-the-ppl.md) i [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Pokazuje, jak używać algorytmu `parallel_invoke`, aby zwiększyć wydajność algorytmu sortowania bitonicznego.|
|[Instrukcje: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Pokazuje, jak używać algorytmu `parallel_invoke`, aby zwiększyć wydajność programu wykonującego wiele operacji w udostępnionym źródle danych.|
|[Instrukcje: tworzenie zadania kończonego po opóźnieniu](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Pokazuje, w jaki sposób używać klas `task`, `cancellation_token_source`, `cancellation_token`i `task_completion_event` do tworzenia zadania, które kończy się po opóźnieniu.|
|[Przewodnik: wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md)|Pokazuje, w jaki sposób połączyć istniejące funkcje w środowisko uruchomieniowe współbieżności w coś, co robi więcej.|
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Opisuje PPL, który zapewnia bezwzględny model programowania do tworzenia współbieżnych aplikacji.|

## <a name="reference"></a>Dokumentacja

[task, klasa (środowisko uruchomieniowe współbieżności)](../../parallel/concrt/reference/task-class.md)

[task_completion_event, klasa](../../parallel/concrt/reference/task-completion-event-class.md)

[Funkcja when_all](reference/concurrency-namespace-functions.md#when_all)

[Funkcja when_any](reference/concurrency-namespace-functions.md#when_any)

[task_group, klasa](reference/task-group-class.md)

[Funkcja parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)

[structured_task_group, klasa](../../parallel/concrt/reference/structured-task-group-class.md)
