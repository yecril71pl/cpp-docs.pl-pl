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
ms.openlocfilehash: e85de9a07b625030976e6f03c9e965d34c3134d4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220980"
---
# <a name="cancellation-in-the-ppl"></a>Anulowanie w PPL

W tym dokumencie wyjaśniono rolę anulowania w bibliotece równoległych wzorców (PPL), jak anulować pracę równoległą i jak ustalić, kiedy równoległe działanie zostało anulowane.

> [!NOTE]
> Środowisko uruchomieniowe używa obsługi wyjątków w celu zaimplementowania anulowania. Nie należy przechwytywać ani obsługiwać tych wyjątków w kodzie. Ponadto zalecamy napisać kod bezpieczny dla wyjątków w treści funkcji dla zadań podrzędnych. Na przykład można użyć wzorca *pozyskiwania zasobów* (RAII), aby upewnić się, że zasoby są prawidłowo obsługiwane, gdy w treści zadania zostanie zgłoszony wyjątek. Aby zapoznać się z kompletnym przykładem, który używa wzorca RAII do czyszczenia zasobu w zadaniu, zobacz [Przewodnik: usuwanie pracy z wątku interfejsu użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md).

## <a name="key-points"></a>Kwestie kluczowe

- Anulowanie jest wspólne i obejmuje koordynację między kodem, który żąda anulowania, a zadaniem, które reaguje na anulowanie.

- Jeśli to możliwe, użyj tokenów anulowania, aby anulować pracę. Klasa [concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) definiuje token anulowania.

- W przypadku używania tokenów anulowania Użyj metody [concurrency:: cancellation_token_source:: Cancel](reference/cancellation-token-source-class.md#cancel) , aby zainicjować anulowanie i funkcję [concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) , aby odpowiedzieć na anulowanie. Użyj metody [concurrency:: cancellation_token:: is_canceled](reference/cancellation-token-class.md#is_canceled) , aby sprawdzić, czy każde inne zadanie zażądało anulowania.

- Anulowanie nie następuje od razu. Chociaż nie uruchomiono nowego zadania, jeśli zadanie lub grupa zadań została anulowana, aktywna służbowa musi sprawdzić i odpowiedzieć na anulowanie.

- Kontynuacja oparta na wartości dziedziczy token anulowania zadania poprzedzającego. Kontynuacja oparta na zadaniach nigdy nie dziedziczy tokenu zadania poprzedzającego.

- Użyj metody [concurrency:: cancellation_token:: none](reference/cancellation-token-class.md#none) , gdy wywołasz konstruktora lub funkcję, która pobiera `cancellation_token` obiekt, ale nie chcesz, aby operacja nie została anulowana. Ponadto, jeśli token anulowania nie zostanie przekazany do funkcji [concurrency:: Task](../../parallel/concrt/reference/task-class.md) konstruktora lub [concurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) , to zadanie nie zostanie anulowane.

## <a name="in-this-document"></a><a name="top"></a>W tym dokumencie

- [Równoległe drzewa robocze](#trees)

- [Anulowanie zadań równoległych](#tasks)

  - [Anulowanie równoległej pracy przy użyciu tokenu anulowania](#tokens)

  - [Anulowanie pracy równoległej za pomocą metody Cancel](#cancel)

  - [Anulowanie pracy równoległej przy użyciu wyjątków](#exceptions)

- [Anulowanie algorytmów równoległych](#algorithms)

- [Kiedy nie używać anulowania](#when)

## <a name="parallel-work-trees"></a><a name="trees"></a>Równoległe drzewa robocze

PPL używa zadań i grup zadań do zarządzania szczegółowymi zadaniami i obliczeniami. Grupy zadań można zagnieżdżać w celu utworzenia *drzew* pracy równoległej. Na poniższej ilustracji przedstawiono równoległe drzewo robocze. Na tej ilustracji `tg1` i `tg2` reprezentuje grupy zadań,, `t1` , `t2` `t3` `t4` i `t5` reprezentuje prace wykonywane przez grupy zadań.

![Równoległe drzewo robocze](../../parallel/concrt/media/parallelwork_trees.png "Równoległe drzewo robocze")

W poniższym przykładzie przedstawiono kod, który jest wymagany do utworzenia drzewa na ilustracji. W tym przykładzie `tg1` i `tg2` są to [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) Objects,,,, `t1` `t2` `t3` `t4` i `t5` to [concurrency:: task_handle](../../parallel/concrt/reference/task-handle-class.md) Objects.

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

Można również użyć klasy [concurrency:: task_group](reference/task-group-class.md) , aby utworzyć podobne drzewo robocze. Klasa [concurrency:: Task](../../parallel/concrt/reference/task-class.md) obsługuje również koncepcję drzewa pracy. Jednak `task` drzewo jest drzewem zależności. W `task` drzewie praca w przyszłości kończy się po bieżącej pracy. W drzewie grupy zadań zakończenie pracy wewnętrznej przed rozpoczęciem pracy zewnętrznej. Aby uzyskać więcej informacji o różnicach między zadaniami i grupami zadań, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

[[Top](#top)]

## <a name="canceling-parallel-tasks"></a><a name="tasks"></a>Anulowanie zadań równoległych

Istnieje wiele sposobów anulowania równoległych zadań. Preferowanym sposobem jest użycie tokenu anulowania. Grupy zadań obsługują również metodę [concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) oraz metodę [concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) . Końcowym sposobem jest zgłoszenie wyjątku w treści funkcji pracy zadania. Niezależnie od wybranej metody, wyjaśnienie, że anulowanie nie następuje natychmiast. Chociaż nie uruchomiono nowego zadania, jeśli zadanie lub grupa zadań została anulowana, aktywna służbowa musi sprawdzić i odpowiedzieć na anulowanie.

Aby uzyskać więcej przykładów, które anulują zadania równoległe, zobacz Wskazówki [: łączenie za pomocą zadań i żądań HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), [jak: użyć anulowania do przerwania z pętli równoległej](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)i [jak: użyć obsługi wyjątków, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

### <a name="using-a-cancellation-token-to-cancel-parallel-work"></a><a name="tokens"></a>Anulowanie równoległej pracy przy użyciu tokenu anulowania

`task`Klasy, `task_group` i `structured_task_group` obsługują anulowanie przy użyciu tokenów anulowania. PPL definiuje w tym celu klasy [concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) i [concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) . W przypadku anulowania pracy przy użyciu tokenu anulowania środowisko uruchomieniowe nie uruchamia nowej pracy, która subskrybuje ten token. Działa, która jest już aktywna, może używać funkcji składowej [is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) do monitorowania tokenu anulowania i zatrzymania, gdy będzie to możliwe.

Aby zainicjować anulowanie, wywołaj metodę [concurrency:: cancellation_token_source:: Cancel](reference/cancellation-token-source-class.md#cancel) . Możesz odpowiedzieć na anulowanie w następujący sposób:

- W przypadku `task` obiektów Użyj funkcji [concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) . `cancel_current_task`anuluje bieżące zadanie i wszystkie kontynuacje oparte na wartościach. (Nie anuluje *tokenu* anulowania, który jest skojarzony z zadaniem lub jego kontynuacji).

- W przypadku grup zadań i algorytmów równoległych należy użyć funkcji [concurrency:: is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) w celu wykrycia anulowania i powrotu jak najszybciej z treści zadania, gdy ta funkcja zwróci wartość **`true`** . (Nie wywołuj `cancel_current_task` z grupy zadań).

Poniższy przykład pokazuje pierwszy podstawowy wzorzec dla anulowania zadania. Treść zadania sporadycznie sprawdza obecność anulowania wewnątrz pętli.

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

`cancel_current_task`Funkcja zgłasza; w związku z tym nie trzeba jawnie zwracać z bieżącej pętli lub funkcji.

> [!TIP]
> Alternatywnie można wywołać funkcję [concurrency:: interruption_point](reference/concurrency-namespace-functions.md#interruption_point) zamiast `cancel_current_task` .

Ważne jest, aby wywołać, `cancel_current_task` gdy odpowie na anulowanie, ponieważ przechodzi do stanu anulowane. W przypadku powrotu wczesnej zamiast wywołania `cancel_current_task` , operacja przechodzi do stanu ukończenia, a wszystkie kontynuacje oparte na wartości są uruchamiane.

> [!CAUTION]
> Nigdy nie zgłaszaj `task_canceled` kodu. `cancel_current_task`Zamiast niego wywołać.

Gdy zadanie zostanie zakończone w stanie anulowanym, Metoda [concurrency:: Task:: Get](reference/task-class.md#get) zgłasza [współbieżność:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md). (Odwrotnie, [concurrency:: Task:: wait](reference/task-class.md#wait) zwraca [task_status:: anulowane](reference/concurrency-namespace-enums.md#task_group_status) i nie throw). Poniższy przykład ilustruje to zachowanie dla kontynuacji opartej na zadaniach. Kontynuacja oparta na zadaniach jest zawsze wywoływana, nawet gdy zadanie poprzedzające zostało anulowane.

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

Ponieważ kontynuacje oparte na wartości dziedziczą token zadania poprzedzającego, chyba że zostały utworzone za pomocą jawnego tokenu, kontynuacje natychmiast wprowadza stan anulowane nawet wtedy, gdy zadanie poprzedzające jest nadal wykonywane. W związku z tym każdy wyjątek, który jest generowany przez zadanie poprzedzające, po anulowaniu nie jest propagowany do zadań kontynuacji. Anulowanie zawsze zastępuje stan zadania poprzedzającego. Poniższy przykład przypomina poprzedni, ale ilustruje zachowanie dla kontynuacji opartej na wartości.

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> Jeśli nie przekażesz tokenu anulowania do `task` konstruktora lub funkcji [concurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) , to zadanie nie zostanie anulowane. Ponadto należy przekazać ten sam token anulowania do konstruktora wszystkich zadań zagnieżdżonych (czyli zadań, które są tworzone w treści innego zadania), aby anulować wszystkie zadania jednocześnie.

Możesz chcieć uruchomić dowolny kod, gdy token anulowania zostanie anulowany. Na przykład, jeśli użytkownik wybierze przycisk **Anuluj** w interfejsie użytkownika, aby anulować operację, można wyłączyć ten przycisk, dopóki użytkownik nie rozpocznie innej operacji. Poniższy przykład pokazuje, jak używać metody [concurrency:: cancellation_token:: register_callback](reference/cancellation-token-class.md#register_callback) do rejestrowania funkcji wywołania zwrotnego, która jest uruchamiana po anulowaniu tokenu anulowania.

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

W dokumencie [Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md) jest wyjaśnione różnice między kontynuacjami opartymi na wartościach i zadaniach. Jeśli nie podasz `cancellation_token` obiektu do zadania kontynuacji, kontynuacja dziedziczy token anulowania z zadania poprzedzającego w następujący sposób:

- Kontynuacja oparta na wartości zawsze dziedziczy token anulowania zadania poprzedzającego.

- Kontynuacja oparta na zadaniach nigdy nie dziedziczy tokenu anulowania zadania poprzedzającego. Jedynym sposobem, aby możliwe było anulowanie kontynuacji opartej na zadaniach, jest jawne przekazanie tokenu anulowania.

Takie zachowania nie mają wpływ na zadanie o błędach (czyli takie, które zgłasza wyjątek). W takim przypadku kontynuacja oparta na wartości jest anulowana; Kontynuacja oparta na zadaniach nie została anulowana.

> [!CAUTION]
> Zadanie, które jest tworzone w innym zadaniu (innymi słowy, zadanie zagnieżdżone) nie dziedziczy tokenu anulowania zadania nadrzędnego. Tylko kontynuacja oparta na wartości dziedziczy token anulowania zadania poprzedzającego.

> [!TIP]
> Użyj metody [concurrency:: cancellation_token:: none](reference/cancellation-token-class.md#none) , gdy wywołasz konstruktora lub funkcję, która pobiera `cancellation_token` obiekt, i nie chcesz, aby operacja nie została anulowana.

Możesz również dostarczyć token anulowania do konstruktora `task_group` `structured_task_group` obiektu lub. Ważnym aspektem tego jest to, że podrzędne grupy zadań dziedziczą ten token anulowania. Przykład demonstrujący tę koncepcję przy użyciu funkcji [concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) do wywołania `parallel_for` , zobacz [anulowanie algorytmów równoległych](#algorithms) w dalszej części tego dokumentu.

[[Top](#top)]

#### <a name="cancellation-tokens-and-task-composition"></a>Anulowanie tokenów i kompozycji zadania

Funkcje [concurrency:: when_all](reference/concurrency-namespace-functions.md#when_all) i [concurrency:: when_any](reference/concurrency-namespace-functions.md#when_all) mogą pomóc w tworzeniu wielu zadań w celu zaimplementowania wspólnych wzorców. W tej sekcji opisano, jak funkcje te działają z tokenami anulowania.

Po podaniu tokenu anulowania do `when_all` `when_any` funkcji i funkcja ta anuluje działanie tylko wtedy, gdy token anulowania został anulowany lub gdy jedno z zadań uczestników zostanie zakończone w stanie anulowane lub zgłasza wyjątek.

`when_all`Funkcja dziedziczy token anulowania z każdego zadania, które składa się z ogólnej operacji, jeśli nie podasz do niego tokenu anulowania. Zadanie, które jest zwracane z, `when_all` zostało anulowane po anulowaniu któregokolwiek z tych tokenów, a co najmniej jedno zadanie uczestnika nie zostało jeszcze uruchomione lub działa. Podobne zachowanie występuje, gdy jedno z zadań zgłasza wyjątek — zadanie zwracane z `when_all` jest natychmiast anulowane z powodu tego wyjątku.

Środowisko uruchomieniowe wybiera token anulowania zadania, które jest zwracane z `when_any` funkcji po zakończeniu zadania. Jeśli żaden z zadań uczestników nie zakończy się w stanie ukończonym, a co najmniej jedno zadanie zgłosi wyjątek, jedno z zadań, które wygenerowało, jest wybrane do ukończenia `when_any` i jego token jest wybierany jako token dla zadania końcowego. Jeśli więcej niż jedno zadanie zakończy się w stanie ukończenia, zadanie zwrócone z `when_any` zadania zakończy się w stanie ukończone. Środowisko uruchomieniowe próbuje wybrać zakończone zadanie, którego token nie został anulowany w momencie zakończenia, tak że zadanie zwracane z `when_any` nie jest natychmiast anulowane, mimo że inne wykonywane zadania mogą zakończyć się w późniejszym czasie.

[[Top](#top)]

### <a name="using-the-cancel-method-to-cancel-parallel-work"></a><a name="cancel"></a>Anulowanie pracy równoległej za pomocą metody Cancel

[Concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) i [concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) Metoda ustawia grupę zadań na stan anulowane. Po wywołaniu `cancel` , grupa zadań nie uruchamia przyszłych zadań. `cancel`Metody mogą być wywoływane przez wiele zadań podrzędnych. Anulowane zadanie powoduje, że metody [concurrency:: task_group:: wait](reference/task-group-class.md#wait) i [concurrency:: structured_task_group:: wait](reference/structured-task-group-class.md#wait) , aby zwracały [concurrency:: anulowane](reference/concurrency-namespace-enums.md#task_group_status).

Jeśli grupa zadań zostanie anulowana, wywołania z każdego zadania podrzędnego do środowiska uruchomieniowego mogą wyzwolić *punkt przerwania*, co powoduje, że środowisko uruchomieniowe zgłasza i przechwytuje wewnętrzny typ wyjątku, aby anulować aktywne zadania. Środowisko uruchomieniowe współbieżności nie definiuje określonych punktów przerwania; mogą wystąpić w dowolnym wywołaniu środowiska uruchomieniowego. Środowisko uruchomieniowe musi obsłużyć wyjątki, które zgłasza, aby można było wykonać operację anulowania. W związku z tym nie należy obsługiwać nieznanych wyjątków w treści zadania.

Jeśli zadanie podrzędne wykonuje czasochłonną operację i nie wywołuje do środowiska uruchomieniowego, musi okresowo sprawdzać, czy można wycofać i wyjść w sposób terminowy. W poniższym przykładzie pokazano jeden ze sposobów, aby określić, kiedy zadanie zostało anulowane. Zadanie `t4` anuluje nadrzędną grupę zadań po napotkaniu błędu. Zadanie `t5` sporadycznie wywołuje `structured_task_group::is_canceling` metodę w celu sprawdzenia anulowania. Jeśli nadrzędna grupa zadań zostanie anulowana, zadanie `t5` drukuje komunikat i kończy pracę.

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

Ten przykład sprawdza, czy dla<sup>każdej 100 iteracji</sup> pętli zadań jest wykonywane anulowanie. Częstotliwość, z którą jest sprawdzane anulowanie, zależy od ilości pracy wykonywanej przez zadanie oraz szybkości, z jaką zadania mogą reagować na anulowanie.

Jeśli nie masz dostępu do obiektu nadrzędnej grupy zadań, wywołaj funkcję [concurrency:: is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) , aby określić, czy nadrzędna grupa zadań została anulowana.

`cancel`Metoda ma wpływ tylko na zadania podrzędne. Na przykład, jeśli anulujesz grupę zadań `tg1` na ilustracji drzewa pracy równoległej, wszystkie zadania w drzewie ( `t1` , `t2` ,, `t3` `t4` , i `t5` ) są modyfikowane. Jeśli anulujesz zagnieżdżoną grupę zadań, `tg2` dotyczy to tylko zadań podrzędnych `t4` `t5` .

Po wywołaniu `cancel` metody wszystkie podrzędne grupy zadań również są anulowane. Anulowanie nie ma jednak wpływu na wszystkie elementy nadrzędne grupy zadań w równoległym drzewie roboczym. W poniższych przykładach pokazano to przez skompilowanie na ilustracji równoległych drzew roboczych.

Pierwszy z tych przykładów tworzy funkcję służbową dla zadania `t4` , które jest elementem podrzędnym grupy zadań `tg2` . Funkcja Work wywołuje funkcję `work` w pętli. Jeśli dowolne wywołanie `work` zakończy się niepowodzeniem, zadanie anuluje jego nadrzędną grupę zadań. Powoduje to, że grupa zadań `tg2` wprowadza stan anulowany, ale nie anuluje grupy zadań `tg1` .

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

Ten drugi przykład przypomina pierwszy z nich, z tą różnicą, że zadanie anuluje grupę zadań `tg1` . Ma to wpływ na wszystkie zadania w drzewie ( `t1` , `t2` ,, `t3` `t4` i `t5` ).

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

`structured_task_group`Klasa nie jest bezpieczna wątkowo. W związku z tym zadanie podrzędne, które wywołuje metodę jego obiektu nadrzędnego, `structured_task_group` daje nieokreślone zachowanie. Wyjątkami od tej reguły są `structured_task_group::cancel` metody [concurrency:: structured_task_group:: is_canceling](reference/structured-task-group-class.md#is_canceling) . Zadanie podrzędne może wywoływać te metody, aby anulować nadrzędną grupę zadań i wyszukać anulowanie.

> [!CAUTION]
> Chociaż można użyć tokenu anulowania, aby anulować pracę wykonywaną przez grupę zadań działającą jako element podrzędny `task` obiektu, nie można użyć `task_group::cancel` `structured_task_group::cancel` metod lub do anulowania `task` obiektów, które są uruchamiane w grupie zadań.

[[Top](#top)]

### <a name="using-exceptions-to-cancel-parallel-work"></a><a name="exceptions"></a>Anulowanie pracy równoległej przy użyciu wyjątków

Użycie tokenów anulowania i `cancel` metody jest bardziej wydajne niż obsługa wyjątków podczas anulowania równoległego drzewa pracy. Tokeny anulowania i `cancel` Metoda anulują zadanie i zadania podrzędne w sposób w dół. Odwrotnie, obsługa wyjątków działa w sposób dolny i musi anulować każdą podrzędną grupę zadań niezależnie, ponieważ wyjątek jest propagowany w górę. [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) w temacie wyjaśnia, jak środowisko uruchomieniowe współbieżności używa wyjątków do komunikacji z błędami. Jednak nie wszystkie wyjątki wskazują na błąd. Na przykład algorytm wyszukiwania może anulować skojarzone z nim zadanie, gdy odnajdzie wynik. Jednak jak wspomniano wcześniej, obsługa wyjątków jest mniej wydajna niż użycie `cancel` metody do anulowania równoległych zadań.

> [!CAUTION]
> Zalecamy używanie wyjątków do anulowania równoległych zadań tylko wtedy, gdy jest to konieczne. Tokeny anulowania i metody grupy zadań są wydajniejsze `cancel` i mniej podatne na błędy.

W przypadku zgłaszania wyjątku w treści funkcji służbowej przekazanej do grupy zadań środowisko uruchomieniowe zapisuje ten wyjątek i przekazuje wyjątek do kontekstu, który czeka na zakończenie działania grupy zadań. Podobnie jak w przypadku `cancel` metody, środowisko uruchomieniowe odrzuca wszystkie zadania, które nie zostały jeszcze uruchomione i nie akceptuje nowych zadań.

Ten trzeci przykład jest podobny do drugiego, z tą różnicą, że zadanie `t4` zgłasza wyjątek, aby anulować grupę zadań `tg2` . W tym przykładzie używa **`try`** - **`catch`** bloku do sprawdzania anulowania, gdy grupa zadań `tg2` czeka na zakończenie zadań podrzędnych. Podobnie jak w przypadku pierwszego przykładu, to powoduje, że grupa zadań `tg2` wprowadza stan anulowany, ale nie anuluje grupy zadań `tg1` .

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

Ten czwarty przykład używa obsługi wyjątków, aby anulować całe drzewo robocze. Przykład przechwytuje wyjątek, gdy grupa zadań `tg1` czeka na zakończenie zadań podrzędnych, zamiast gdy grupa zadań `tg2` czeka na zadania podrzędne. Podobnie jak w drugim przykładzie powoduje to, że oba zadania są wykonywane w drzewie, `tg1` a w `tg2` celu wprowadzenia stanu anulowane.

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

Ponieważ `task_group::wait` metody i `structured_task_group::wait` generują gdy zadanie podrzędne zgłasza wyjątek, nie otrzymasz od nich wartości zwracanej.

[[Top](#top)]

## <a name="canceling-parallel-algorithms"></a><a name="algorithms"></a>Anulowanie algorytmów równoległych

Algorytmy równoległe w PPL, na przykład, `parallel_for` kompilacja w grupach zadań. W związku z tym można użyć wielu z tych samych technik, aby anulować algorytm równoległy.

Poniższe przykłady ilustrują kilka sposobów anulowania algorytmu równoległego.

Poniższy przykład używa funkcji, `run_with_cancellation_token` Aby wywołać `parallel_for` algorytm. `run_with_cancellation_token`Funkcja przyjmuje token anulowania jako argument i wywołuje podaną funkcję pracy synchronicznie. Ze względu na to, że algorytmy równoległe są tworzone na podstawie zadań, dziedziczą token anulowania zadania nadrzędnego. W związku `parallel_for` z tym może odpowiedzieć na anulowanie.

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

W poniższym przykładzie zastosowano metodę [concurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait) do wywołania `parallel_for` algorytmu. `structured_task_group::run_and_wait`Metoda czeka na zakończenie podanego zadania. `structured_task_group`Obiekt umożliwia funkcji pracy anulowanie zadania.

[!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
The task group status is: canceled.
```

W poniższym przykładzie zastosowano obsługę wyjątków w celu anulowania `parallel_for` pętli. Środowisko uruchomieniowe powoduje kierowanie wyjątku do kontekstu wywołującego.

[!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
Caught 50
```

Poniższy przykład używa flagi logicznej do koordynowania anulowania w `parallel_for` pętli. Każde zadanie jest uruchamiane, ponieważ w tym przykładzie nie jest używana `cancel` Metoda lub obsługa wyjątków w celu anulowania ogólnego zestawu zadań. W związku z tym ta technika może mieć więcej obciążeń obliczeniowych niż mechanizm anulowania.

[!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]

Każda metoda anulowania ma zalety dla innych. Wybierz metodę odpowiadającą konkretnym potrzebom.

[[Top](#top)]

## <a name="when-not-to-use-cancellation"></a><a name="when"></a>Kiedy nie używać anulowania

Użycie anulowania jest odpowiednie, gdy każdy członek grupy powiązanych zadań może wyjść w odpowiednim czasie. Istnieją jednak sytuacje, w których anulowanie może nie być odpowiednie dla Twojej aplikacji. Na przykład ze względu na to, że anulowanie zadania jest wspólne, cały zestaw zadań nie zostanie anulowany, jeśli każde zadanie zostanie zablokowane. Na przykład jeśli jedno zadanie jeszcze nie zostało uruchomione, ale odblokowuje inne aktywne zadanie, nie zostanie ono uruchomione, jeśli grupa zadań zostanie anulowana. Może to spowodować wystąpienie zakleszczenia w aplikacji. Drugi przykład, w którym użycie anulowania może być nieodpowiednie, ma miejsce, gdy zadanie zostało anulowane, ale jego zadanie podrzędne wykonuje ważne operacje, takie jak zwalnianie zasobów. Ponieważ cały zestaw zadań jest anulowany po anulowaniu zadania nadrzędnego, ta operacja nie zostanie wykonana. Przykład, który ilustruje ten punkt, znajduje się w sekcji [zrozumienie, jak anulowanie i obsługa wyjątków wpływają na sekcję niszczenie obiektów](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) w temacie najlepsze rozwiązania w bibliotece równoległych wzorców.

[[Top](#top)]

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Jak użyć anulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Pokazuje, jak za pomocą anulowania zaimplementować algorytm wyszukiwania równoległego.|
|[Instrukcje: korzystanie z obsługi wyjątków, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Pokazuje, w jaki sposób używać `task_group` klasy do pisania algorytmu wyszukiwania dla podstawowej struktury drzewa.|
|[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Opisuje, jak środowisko uruchomieniowe obsługuje wyjątki, które są zgłaszane przez grupy zadań, uproszczone zadania i agenci asynchroniczni oraz jak odpowiadać na wyjątki w aplikacjach.|
|[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Opisuje, w jaki sposób zadania są powiązane z grupami zadań i jak można użyć zadań bez struktury i strukturalnych w aplikacjach.|
|[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)|Opisuje algorytmy równoległe, które jednocześnie wykonują prace nad kolekcjami danych|
|[Biblioteka równoległych wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Zawiera omówienie biblioteki wzorców równoległych.|

## <a name="reference"></a>Dokumentacja

[Task — Klasa (środowisko uruchomieniowe współbieżności)](../../parallel/concrt/reference/task-class.md)

[Klasa cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)

[Klasa cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)

[Klasa task_group](reference/task-group-class.md)

[Klasa structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)

[Funkcja parallel_for](reference/concurrency-namespace-functions.md#parallel_for)
