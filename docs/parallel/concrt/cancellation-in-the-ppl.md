---
title: Anulowanie w PPL
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms, canceling [Concurrency Runtime]
- canceling parallel algorithms [Concurrency Runtime]
- parallel tasks, canceling [Concurrency Runtime]
- cancellation in the PPL
- parallel work trees [Concurrency Runtime]
- canceling parallel tasks [Concurrency Runtime]
ms.assetid: baaef417-b2f9-470e-b8bd-9ed890725b35
ms.openlocfilehash: 27c0ea3cfcf62060800c1c0b034dde7de6357250
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368491"
---
# <a name="cancellation-in-the-ppl"></a>Anulowanie w PPL

W tym dokumencie wyjaśniono rolę anulowania w bibliotece wzorców równoległych (PPL), jak anulować pracę równoległą i jak określić, kiedy praca równoległa jest anulowana.

> [!NOTE]
> Środowisko wykonawcze używa obsługi wyjątków do implementacji anulowania. Nie należy przechwytyć ani obsługiwać tych wyjątków w kodzie. Ponadto zaleca się pisanie kodu bezpiecznego wyjątku w organach funkcji dla zadań. Na przykład można użyć wzorca *inicjowania pozyskiwania zasobów* (RAII), aby upewnić się, że zasoby są poprawnie obsługiwane, gdy wyjątek jest zgłaszany w treści zadania. Aby uzyskać pełny przykład, który używa wzorca RAII do czyszczenia zasobu w zadaniach anulowanych, zobacz [Przewodnik: Usuwanie pracy z wątku interfejsu użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md).

## <a name="key-points"></a>Kwestie kluczowe

- Anulowanie jest współpraca i obejmuje koordynację między kodem, który żąda anulowania i zadanie, które odpowiada na anulowanie.

- Jeśli to możliwe, użyj tokenów anulowania, aby anulować pracę. [Współbieżność::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) klasa definiuje token anulowania.

- Korzystając z tokenów anulowania, użyj [współbieżności::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) metody do inicjowania anulowania i [współbieżności::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) funkcji, aby odpowiedzieć na anulowanie. Użyj [współbieżności::cancellation_token::is_canceled](reference/cancellation-token-class.md#is_canceled) metody, aby sprawdzić, czy inne zadanie zażądało anulowania.

- Anulowanie nie nastąpi natychmiast. Chociaż nowa praca nie jest uruchomiona, jeśli zadanie lub grupa zadań została anulowana, aktywna praca musi sprawdzić anulowanie i odpowiedzieć na nią.

- Kontynuacja oparta na wartości dziedziczy token anulowania jego zadania poprzedzago. Kontynuacja oparta na zadaniach nigdy nie dziedziczy tokenu swojego zadania poprzedzago.

- Użyj [współbieżności::cancellation_token::none](reference/cancellation-token-class.md#none) metody podczas wywoływania konstruktora lub `cancellation_token` funkcji, która przyjmuje obiekt, ale nie chcesz, aby operacja była anulowana. Ponadto jeśli nie przekażesz tokenu anulowania do konstruktora [współbieżności::task](../../parallel/concrt/reference/task-class.md) lub [funkcji współbieżności::create_task,](reference/concurrency-namespace-functions.md#create_task) to zadanie nie można anulować.

## <a name="in-this-document"></a><a name="top"></a>W niniejszym dokumencie

- [Równoległe drzewa robocze](#trees)

- [Anulowanie zadań równoległych](#tasks)

  - [Używanie tokenu anulowania do anulowania pracy równoległej](#tokens)

  - [Używanie metody anulowania w celu anulowania pracy równoległej](#cancel)

  - [Używanie wyjątków do anulowania pracy równoległej](#exceptions)

- [Anulowanie algorytmów równoległych](#algorithms)

- [Kiedy nie używać anulowania](#when)

## <a name="parallel-work-trees"></a><a name="trees"></a>Równoległe drzewa robocze

PPL używa zadań i grup zadań do zarządzania szczegółowymi zadaniami i obliczeniami. Grupy zadań można zagnieżdżać, tworząc *drzewa* pracy równoległej. Na poniższej ilustracji przedstawiono równoległe drzewo robocze. Na tej `tg1` ilustracji i `tg2` reprezentują grupy zadań; `t1`, `t2` `t3`, `t4`i `t5` reprezentują pracę, którą wykonują grupy zadań.

![Równoległe drzewo robocze](../../parallel/concrt/media/parallelwork_trees.png "Równoległe drzewo robocze")

Poniższy przykład pokazuje kod, który jest wymagany do utworzenia drzewa na ilustracji. W tym `tg1` przykładzie i `tg2` są [współbieżności::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiektów; `t1`, `t2` `t3`, `t4`i `t5` są [współbieżności::task_handle](../../parallel/concrt/reference/task-handle-class.md) obiektów.

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

Można również użyć [współbieżności::task_group](reference/task-group-class.md) klasy, aby utworzyć podobne drzewo robocze. [Współbieżność::klasa zadań](../../parallel/concrt/reference/task-class.md) obsługuje również pojęcie drzewa pracy. Jednak `task` drzewo jest drzewem zależności. W `task` drzewie przyszłe prace kończą się po bieżącej pracy. W drzewie grupy zadań praca wewnętrzna kończy się przed pracą zewnętrzną. Aby uzyskać więcej informacji na temat różnic między zadaniami a grupami zadań, zobacz [Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

[[Góra](#top)]

## <a name="canceling-parallel-tasks"></a><a name="tasks"></a>Anulowanie zadań równoległych

Istnieje wiele sposobów anulowania pracy równoległej. Preferowanym sposobem jest użycie tokenu anulowania. Grupy zadań obsługują również metodę [współbieżności::task_group:cancel](reference/task-group-class.md#cancel) i metodę [współbieżności::structured_task_group::anuluj.](reference/structured-task-group-class.md#cancel) Ostatnim sposobem jest zgłosić wyjątek w treści funkcji pracy zadania. Bez względu na to, którą metodę wybierzesz, zrozum, że anulowanie nie nastąpi natychmiast. Chociaż nowa praca nie jest uruchomiona, jeśli zadanie lub grupa zadań została anulowana, aktywna praca musi sprawdzić anulowanie i odpowiedzieć na nią.

Aby uzyskać więcej przykładów, które anulują zadania równoległe, zobacz [Instruktaż: Łączenie przy użyciu zadań i żądania HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), [Jak: Użyj anulowania do przerwania z pętli równoległej](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)i [Jak: Użyj obsługi wyjątków, aby przerwać z pętli równoległej](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

### <a name="using-a-cancellation-token-to-cancel-parallel-work"></a><a name="tokens"></a>Używanie tokenu anulowania do anulowania pracy równoległej

, `task` `task_group`i `structured_task_group` klasy obsługują anulowanie za pomocą tokenów anulowania. PPL definiuje [współbieżność::cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) i [współbieżności::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) klas w tym celu. Gdy używasz tokenu anulowania, aby anulować pracę, środowisko wykonawcze nie uruchamia nowej pracy, która subskrybuje ten token. Praca, która jest już aktywna, może używać funkcji [is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) element członkowski do monitorowania tokenu anulowania i zatrzymywania się, gdy jest to możliwe.

Aby zainicjować anulowanie, wywołaj metodę [współbieżności::cancellation_token_source::cancel.](reference/cancellation-token-source-class.md#cancel) Odpowiadasz na anulowanie w ten sposób:

- W `task` przypadku obiektów należy użyć funkcji [współbieżności::cancel_current_task.](reference/concurrency-namespace-functions.md#cancel_current_task) `cancel_current_task`anuluje bieżące zadanie i wszelkie jego kontynuacje oparte na wartości. (Nie anuluje *tokenu* anulowania, który jest skojarzony z zadaniem lub jego kontynuacji.)

- W przypadku grup zadań i algorytmów równoległych użyj funkcji [współbieżności::is_current_task_group_canceling,](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) aby wykryć anulowanie i powrócić tak szybko, jak to możliwe z treści zadania, gdy ta funkcja zwraca **wartość true**. (Nie należy `cancel_current_task` wywoływać z grupy zadań).

W poniższym przykładzie przedstawiono pierwszy podstawowy wzorzec anulowania zadania. Treść zadania od czasu do czasu sprawdza anulowanie wewnątrz pętli.

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

Funkcja `cancel_current_task` rzuca; w związku z tym nie trzeba jawnie zwracać z bieżącej pętli lub funkcji.

> [!TIP]
> Alternatywnie można wywołać [współbieżność::interruption_point,](reference/concurrency-namespace-functions.md#interruption_point) a nie `cancel_current_task`.

Ważne jest, `cancel_current_task` aby wywołać podczas odpowiadania na anulowanie, ponieważ przenosi zadanie do stanu anulowane. Jeśli zwrócisz wcześnie zamiast `cancel_current_task`wywoływania, zostaną uruchomione przejścia operacji do stanu ukończonego i wszystkie kontynuacje oparte na wartości.

> [!CAUTION]
> Nigdy `task_canceled` nie wyrzucaj z kodu. Zamiast `cancel_current_task` tego zadzwoń.

Po zakończeniu zadania w stanie anulowania [współbieżność::task::get](reference/task-class.md#get) metoda zgłasza [współbieżność::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). (Z drugiej strony [współbieżność::task::wait](reference/task-class.md#wait) zwraca [task_status::canceled](reference/concurrency-namespace-enums.md#task_group_status) i nie zgłasza.) Poniższy przykład ilustruje to zachowanie dla kontynuacji opartej na zadaniach. Kontynuacja oparta na zadaniach jest zawsze wywoływana, nawet gdy zadanie poprzedzane jest anulowane.

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

Ponieważ kontynuacje oparte na wartości dziedziczą token ich zadania poprzedzającego, chyba że zostały utworzone za pomocą jawnego tokenu, kontynuacje natychmiast wprowadź anulowany stan, nawet jeśli zadanie poprzedzające jest nadal wykonywane. W związku z tym każdy wyjątek, który jest generowany przez zadanie poprzedzając po anulowaniu nie jest propagowany do zadań kontynuacji. Anulowanie zawsze zastępuje stan zadania poprzedzanego. Poniższy przykład przypomina poprzedni, ale ilustruje zachowanie kontynuacji opartej na wartości.

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> Jeśli nie przekażesz tokenu `task` anulowania do konstruktora lub [funkcji współbieżności::create_task,](reference/concurrency-namespace-functions.md#create_task) to zadanie nie można anulować. Ponadto należy przekazać ten sam token anulowania do konstruktora wszystkich zadań zagnieżdżonych (czyli zadań, które są tworzone w treści innego zadania), aby anulować wszystkie zadania jednocześnie.

Można uruchomić dowolny kod, gdy token anulowania zostanie anulowany. Na przykład jeśli użytkownik wybierze przycisk **Anuluj** w interfejsie użytkownika, aby anulować operację, można wyłączyć ten przycisk, dopóki użytkownik nie rozpocznie innej operacji. Poniższy przykład pokazuje, jak używać [współbieżności::cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback) metody do rejestrowania funkcji wywołania zwrotnego, która jest uruchamiana po anulowaniu tokenu anulowania.

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

Równoległość [zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md) dokumentu wyjaśnia różnicę między kontynuacji opartych na wartości i opartych na zadaniach. Jeśli obiekt nie `cancellation_token` zostanie udostępniony do zadania kontynuacji, kontynuacja dziedziczy token anulowania z zadania poprzedzago w następujący sposób:

- Kontynuacja oparta na wartościach zawsze dziedziczy token anulowania zadania poprzedzanego.

- Kontynuacja oparta na zadaniach nigdy nie dziedziczy tokenu anulowania zadania poprzedzanego. Jedynym sposobem, aby można anulować kontynuację opartą na zadaniach, jest jawne przekazanie tokenu anulowania.

Te zachowania nie są zagrożone przez zadanie błędem (oznacza to, że zgłasza wyjątek). W takim przypadku kontynuacja oparta na wartości jest anulowana; kontynuacja oparta na zadaniach nie jest anulowana.

> [!CAUTION]
> Zadanie, które jest tworzone w innym zadaniu (innymi słowy, zagnieżdżone zadanie) nie dziedziczy tokenu anulowania zadania nadrzędnego. Tylko kontynuacja oparta na wartości dziedziczy token anulowania jego zadania poprzedzago.

> [!TIP]
> Użyj [współbieżności::cancellation_token::none](reference/cancellation-token-class.md#none) metody podczas wywoływania konstruktora lub funkcji, która przyjmuje `cancellation_token` obiekt i nie chcesz, aby operacja była anulowana.

Można również podać token anulowania do `task_group` konstruktora lub `structured_task_group` obiektu. Ważnym aspektem jest to, że podrzędne grupy zadań dziedziczą ten token anulowania. Na przykład, który demonstruje tę koncepcję przy użyciu [funkcji współbieżności::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) do uruchomienia do wywołania, `parallel_for`zobacz [Anulowanie algorytmów równoległych](#algorithms) w dalszej części tego dokumentu.

[[Góra](#top)]

#### <a name="cancellation-tokens-and-task-composition"></a>Anulowanie tokenów i kompozycji zadania

[Współbieżność::when_all](reference/concurrency-namespace-functions.md#when_all) i [współbieżność::when_any](reference/concurrency-namespace-functions.md#when_all) funkcje mogą pomóc w komponowaniu wielu zadań w celu zaimplementowania typowych wzorców. W tej sekcji opisano, jak te funkcje działają z tokenami anulowania.

Po podaniu tokenu anulowania `when_all` `when_any` do i funkcji, ta funkcja anuluje tylko wtedy, gdy token anulowania jest anulowany lub gdy jedno z zadań uczestnika kończy się w stanie anulowane lub zgłasza wyjątek.

Funkcja `when_all` dziedziczy token anulowania z każdego zadania, które komponuje ogólną operację, gdy nie podasz tokenu anulowania do niego. Zadanie, które jest `when_all` zwracane z jest anulowane, gdy którykolwiek z tych tokenów są anulowane i co najmniej jedno z zadań uczestnika nie został jeszcze uruchomiony lub jest uruchomiony. Podobne zachowanie występuje, gdy jedno z zadań zgłasza wyjątek `when_all` — zadanie, które jest zwracane z jest natychmiast anulowane z tym wyjątkiem.

Środowisko wykonawcze wybiera token anulowania dla zadania, który jest zwracany z `when_any` funkcji po zakończeniu tego zadania. Jeśli żadne z zadań uczestnika zakończyć w stanie ukończone i co najmniej jedno z zadań zgłasza `when_any` wyjątek, jedno z zadań, które zostały wybrano do wykonania i jego token jest wybierany jako token dla zadania końcowego. Jeśli więcej niż jedno zadanie zakończy się w stanie `when_any` ukończone, zadanie, które jest zwracane z zadania kończy się w stanie ukończone. Środowisko wykonawcze próbuje wybrać ukończone zadanie, którego token nie został anulowany w `when_any` momencie ukończenia, tak aby zadanie, z którego jest zwracane, nie zostało natychmiast anulowane, mimo że inne zadania wykonujące mogą zostać wykonane w późniejszym momencie.

[[Góra](#top)]

### <a name="using-the-cancel-method-to-cancel-parallel-work"></a><a name="cancel"></a>Używanie metody anulowania w celu anulowania pracy równoległej

[Współbieżność::task_group:anuluj](reference/task-group-class.md#cancel) i [współbieżność::structured_task_group::anuluj](reference/structured-task-group-class.md#cancel) metody ustaw grupę zadań na stan anulowany. Po wywołaniu `cancel`grupa zadań nie uruchamia przyszłych zadań. Metody `cancel` mogą być wywoływane przez wiele zadań podrzędnych. Anulowane zadanie powoduje [współbieżność::task_group::wait](reference/task-group-class.md#wait) and [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait) metody [zwrotu współbieżności::anulowane](reference/concurrency-namespace-enums.md#task_group_status).

Jeśli grupa zadań zostanie anulowana, wywołania z każdego zadania podrzędnego do środowiska wykonawczego mogą wyzwolić *punkt przerwania,* co powoduje, że środowisko uruchomieniowe zgłasza i przechwytuje wewnętrzny typ wyjątku w celu anulowania aktywnych zadań. Środowisko uruchomieniowe współbieżności nie definiuje określonych punktów przerwania; mogą wystąpić w dowolnym wywołaniu środowiska wykonawczego. Środowisko wykonawcze musi obsługiwać wyjątki, które zgłasza w celu wykonania anulowania. W związku z tym nie obsłużyć nieznane wyjątki w treści zadania.

Jeśli zadanie podrzędne wykonuje czasochłonną operację i nie powoduje wywołania w czasie wykonywania, musi okresowo sprawdzać, czy anulowanie i wyjście w odpowiednim czasie. W poniższym przykładzie pokazano jeden sposób, aby określić, kiedy praca jest anulowana. Zadanie `t4` anuluje nadrzędną grupę zadań, gdy wystąpi błąd. Zadanie `t5` od czasu `structured_task_group::is_canceling` do czasu wywołuje metodę, aby sprawdzić, czy anulowanie. Jeśli nadrzędna grupa zadań zostanie `t5` anulowana, zadanie drukuje komunikat i kończy działanie.

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

W tym przykładzie sprawdza anulowanie na co 100<sup>th</sup> iteracji pętli zadań. Częstotliwość, z jaką sprawdzasz, czy chcesz anulować, zależy od ilości pracy wykonywanej przez zadanie i od tego, jak szybko trzeba wykonać zadania, aby odpowiedzieć na anulowanie.

Jeśli nie masz dostępu do nadrzędnego obiektu grupy zadań, należy wywołać funkcję [współbieżności::is_current_task_group_canceling,](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) aby ustalić, czy nadrzędna grupa zadań została anulowana.

Metoda `cancel` dotyczy tylko zadań podrzędnych. Na przykład, jeśli anulujesz `tg1` grupę zadań na ilustracji równoległego`t1`drzewa `t2` `t3`roboczego, dotyczy to wszystkich zadań w drzewie ( , , , `t4`, i `t5`). Jeśli anulujesz zagnieżdżoną grupę zadań, `tg2`tylko zadania i `t4` `t5` dotyczy to tylko zadań.

Po wywołaniu `cancel` metody wszystkie podrzędne grupy zadań są również anulowane. Anulowanie nie ma jednak wpływu na żadne rodziców grupy zadań w równoległym drzewie roboczym. Poniższe przykłady pokazują to, tworząc na ilustracji drzewa roboczego równoległego.

Pierwszy z tych przykładów tworzy funkcję `t4`pracy dla zadania, która `tg2`jest elementem podrzędnym grupy zadań . Funkcja pracy wywołuje `work` funkcję w pętli. Jeśli każde `work` wywołanie nie powiedzie się, zadanie anuluje nadrzędną grupę zadań. Powoduje to, `tg2` że grupa zadań wprowadza stan anulowany, `tg1`ale nie anuluje grupy zadań .

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

Ten drugi przykład przypomina pierwszy, z tą różnicą, że zadanie anuluje grupę `tg1`zadań . Dotyczy to wszystkich zadań w`t1` `t2`drzewie `t4`( `t5`, , `t3`, , i ).

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

Klasa `structured_task_group` nie jest bezpieczna dla wątków. W związku z tym zadanie podrzędne, `structured_task_group` które wywołuje metodę jego obiektu nadrzędnego tworzy nieokreślone zachowanie. Wyjątkami od tej reguły są `structured_task_group::cancel` metody [współbieżności::structured_task_group::is_canceling.](reference/structured-task-group-class.md#is_canceling) Zadanie podrzędne można wywołać te metody, aby anulować nadrzędną grupę zadań i sprawdzić, czy anulowanie.

> [!CAUTION]
> Chociaż można użyć tokenu anulowania, aby anulować pracę wykonaną przez `task` grupę zadań, `task_group::cancel` `structured_task_group::cancel` która działa `task` jako podrzędny obiekt, nie można użyć lub metody anulowania obiektów, które są uruchamiane w grupie zadań.

[[Góra](#top)]

### <a name="using-exceptions-to-cancel-parallel-work"></a><a name="exceptions"></a>Używanie wyjątków do anulowania pracy równoległej

Użycie tokenów anulowania `cancel` i metody są bardziej wydajne niż obsługa wyjątków przy anulowaniu równoległego drzewa roboczego. Tokeny anulowania `cancel` i metoda anulować zadanie i wszystkie zadania podrzędne w sposób odgórny. Z drugiej strony obsługa wyjątków działa w sposób oddolny i musi anulować każdą podrzędną grupę zadań niezależnie, ponieważ wyjątek propaguje w górę. W temacie [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) wyjaśniono, jak środowisko uruchomieniowe współbieżności używa wyjątków do przekazywania błędów. Jednak nie wszystkie wyjątki wskazują na błąd. Na przykład algorytm wyszukiwania może anulować skojarzone zadanie po znalezieniu wyniku. Jednak jak wspomniano wcześniej, obsługa wyjątków jest `cancel` mniej wydajne niż przy użyciu metody, aby anulować pracę równoległą.

> [!CAUTION]
> Zaleca się użycie wyjątków, aby anulować pracę równoległą tylko wtedy, gdy jest to konieczne. Tokeny anulowania i `cancel` metody grupy zadań są bardziej wydajne i mniej podatne na błędy.

Po zgłosisz wyjątek w treści funkcji pracy, która jest przekazywalna do grupy zadań, środowisko wykonawcze przechowuje ten wyjątek i organizuje wyjątek od kontekstu, który czeka na zakończenie grupy zadań. Podobnie jak `cancel` w przypadku metody, środowisko wykonawcze odrzuca wszystkie zadania, które nie zostały jeszcze uruchomione i nie akceptuje nowych zadań.

Ten trzeci przykład przypomina drugi, z `t4` tą różnicą, że `tg2`zadanie zgłasza wyjątek, aby anulować grupę zadań . W tym przykładzie `try` - `catch` użyto bloku, aby `tg2` sprawdzić anulowanie, gdy grupa zadań czeka na zakończenie zadań podrzędnych. Podobnie jak w pierwszym przykładzie `tg2` powoduje to, że grupa zadań wprowadza `tg1`stan anulowany, ale nie anuluje grupy zadań .

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

W tym czwartym przykładzie użyto obsługi wyjątków, aby anulować całe drzewo robocze. W przykładzie wychwytuje `tg1` wyjątek, gdy grupa zadań czeka na `tg2` zakończenie zadań podrzędnych, a nie wtedy, gdy grupa zadań czeka na swoje zadania podrzędne. Podobnie jak w drugim przykładzie powoduje to, że obie grupy zadań w drzewie `tg1` i `tg2`, aby wprowadzić stan anulowane.

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

Ponieważ `task_group::wait` i `structured_task_group::wait` metody zgłosić, gdy zadanie podrzędne zgłasza wyjątek, nie otrzymasz wartość zwracaną od nich.

[[Góra](#top)]

## <a name="canceling-parallel-algorithms"></a><a name="algorithms"></a>Anulowanie algorytmów równoległych

Algorytmy równoległe w PPL, `parallel_for`na przykład , opierają się na grupach zadań. W związku z tym można użyć wielu z tych samych technik, aby anulować algorytm równoległy.

Poniższe przykłady ilustrują kilka sposobów anulowania algorytmu równoległego.

W poniższym przykładzie `run_with_cancellation_token` użyto `parallel_for` funkcji do wywołania algorytmu. Funkcja `run_with_cancellation_token` przyjmuje token anulowania jako argument i wywołuje pod warunkiem funkcji pracy synchronicznie. Ponieważ algorytmy równoległe są zbudowane na zadaniach, dziedziczą token anulowania zadania nadrzędnego. W związku `parallel_for` z tym może odpowiedzieć na anulowanie.

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

W poniższym przykładzie użyto [metody współbieżności::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait) do wywołania algorytmu. `parallel_for` Metoda `structured_task_group::run_and_wait` czeka na podane zadanie do zakończenia. Obiekt `structured_task_group` umożliwia funkcji pracy, aby anulować zadanie.

[!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]

W tym przykładzie daje następujące dane wyjściowe.

```Output
The task group status is: canceled.
```

W poniższym przykładzie użyto `parallel_for` obsługi wyjątków, aby anulować pętlę. Środowisko wykonawcze marszałków wyjątek do kontekstu wywołującego.

[!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]

W tym przykładzie daje następujące dane wyjściowe.

```Output
Caught 50
```

W poniższym przykładzie użyto flagi logicznej do koordynowania anulowania w `parallel_for` pętli. Każde zadanie jest uruchamiane, `cancel` ponieważ w tym przykładzie nie używa metody lub obsługi wyjątków, aby anulować ogólny zestaw zadań. W związku z tym ta technika może mieć więcej nakładów obliczeniowych niż mechanizm anulowania.

[!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]

Każda metoda anulowania ma przewagę nad innymi. Wybierz metodę, która pasuje do Twoich konkretnych potrzeb.

[[Góra](#top)]

## <a name="when-not-to-use-cancellation"></a><a name="when"></a>Kiedy nie używać anulowania

Użycie anulowania jest właściwe, gdy każdy członek grupy powiązanych zadań może zakończyć pracę w odpowiednim czasie. Istnieją jednak pewne scenariusze, w których anulowanie może nie być odpowiednie dla aplikacji. Na przykład ponieważ anulowanie zadania jest kooperatywne, ogólny zestaw zadań nie zostanie anulowany, jeśli każde pojedyncze zadanie zostanie zablokowane. Na przykład jeśli jedno zadanie nie zostało jeszcze uruchomione, ale odblokowuje inne aktywne zadanie, nie zostanie uruchomione, jeśli grupa zadań zostanie anulowana. Może to spowodować zakleszczenie występuje w aplikacji. Drugim przykładem, w którym użycie anulowania może nie być odpowiednie, jest anulowanie zadania, ale jego zadanie podrzędne wykonuje ważną operację, taką jak zwalnianie zasobu. Ponieważ ogólny zestaw zadań jest anulowany, gdy zadanie nadrzędne jest anulowane, ta operacja nie zostanie wykonana. Na przykład, który ilustruje ten punkt, zobacz [Zrozumieć, jak anulowanie i obsługa wyjątków wpływają na zniszczenie obiektu](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) sekcji Najlepsze rozwiązania w bibliotece wzorców równoległych tematu.

[[Góra](#top)]

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: używanie anulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Pokazuje, jak używać anulowania do zaimplementowania algorytmu wyszukiwania równoległego.|
|[Instrukcje: używanie obsługi wyjątków, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Pokazuje, jak `task_group` używać klasy do pisania algorytmu wyszukiwania dla podstawowej struktury drzewa.|
|[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|W tym artykule opisano, jak środowisko uruchomieniowe obsługuje wyjątki, które są zgłaszane przez grupy zadań, lekkie zadania i agentów asynchronicznych i jak reagować na wyjątki w aplikacjach.|
|[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|W tym artykule opisano, jak zadania odnoszą się do grup zadań i jak można używać zadań nieustrukturyzowanych i strukturalnych w aplikacjach.|
|[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)|Opisuje algorytmy równoległe, które jednocześnie wykonują pracę nad kolekcjami danych|
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Zawiera omówienie biblioteki wzorców równoległych.|

## <a name="reference"></a>Dokumentacja

[Klasa zadania (środowisko uruchomieniowe współbieżności)](../../parallel/concrt/reference/task-class.md)

[Klasa cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)

[Klasa cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)

[task_group — Klasa](reference/task-group-class.md)

[Klasa structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)

[Funkcja parallel_for](reference/concurrency-namespace-functions.md#parallel_for)
