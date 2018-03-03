---
title: Anulowanie w PPL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- parallel algorithms, canceling [Concurrency Runtime]
- canceling parallel algorithms [Concurrency Runtime]
- parallel tasks, canceling [Concurrency Runtime]
- cancellation in the PPL
- parallel work trees [Concurrency Runtime]
- canceling parallel tasks [Concurrency Runtime]
ms.assetid: baaef417-b2f9-470e-b8bd-9ed890725b35
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 340942905ce252f7e4a40d8ae5366d5d154755d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cancellation-in-the-ppl"></a>Anulowanie w PPL
W tym dokumencie opisano roli anulowania w Biblioteka równoległych wzorców (PLL), jak anulować równoległych pracy i sposób określania, kiedy pracy równoległej została anulowana.  
  
> [!NOTE]
>  Środowisko uruchomieniowe używa obsługi wyjątków do implementacji anulowania. Nie catch lub obsługę tych wyjątków w kodzie. Ponadto firma Microsoft zaleca zapisu wyjątek bezpieczny kod w treści funkcji dla zadań. Na przykład można użyć *inicjowania jest nabywania zasobów* wzorca (RAII), aby upewnić się, czy zasoby są poprawnie obsłużona podczas wyjątek w treści zadania. Pełny przykład korzysta ze wzorca RAII czyszczenie zasobów można anulować zadania, zobacz [wskazówki: usuwanie pracy z wątku interfejsu użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md).  
  
## <a name="key-points"></a>Kwestie kluczowe  
  
-   Anulowanie jest współpracy i obejmuje koordynację między tymi kod, który żąda anulowania i zadań, która odpowiada na anulowanie.  
  
-   Jeśli to możliwe, należy użyć anulowanie tokenów do anulowania pracy. [Concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) klasa definiuje token anulowania.  
  

-   W przypadku użycia anulowanie tokenów użyć [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) metodę, aby zainicjować anulowanie i [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) funkcja odpowiedzieć anulowanie. Użyj [concurrency::cancellation_token::is_canceled](reference/cancellation-token-class.md#is_canceled) , aby sprawdzić, czy inne zadanie wysłano żądanie anulowania.
  
-   Anulowanie nie występuje od razu. Chociaż nowa praca nie jest uruchomiona, jeśli zadania lub grupy zadań zostało anulowane, aktywną pracą musi sprawdzić i odpowiadanie na anulowanie.  
  
-   Kontynuacja oparte na wartościach dziedziczy token anulowania poprzedzających zadania. Kontynuacja opartego na zadaniach nigdy nie dziedziczy token poprzedzających zadania.  
  
-   Użyj [concurrency::cancellation_token:: Brak](reference/cancellation-token-class.md#none) metody podczas wywołania konstruktora lub funkcję, która przyjmuje `cancellation_token` obiekt, ale nie chcesz, aby operacja jest możliwe. Ponadto jeśli nie są przekazywane token anulowania na potrzeby [concurrency::task](../../parallel/concrt/reference/task-class.md) konstruktora lub [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) funkcji, to zadanie nie jest możliwe.  


  
##  <a name="top"></a>W tym dokumencie  
  
- [Drzewa pracy równoległej](#trees)  
  
- [Anulowanie zadań równoległych](#tasks)  
  
    - [Przy użyciu Token anulowania do anulowania pracy równoległych](#tokens)  
  
    - [Przy użyciu Anuluj metodę, aby anulować pracy równoległych](#cancel)  
  
    - [Używanie wyjątków można anulować pracy równoległych](#exceptions)  
  
- [Anulowanie algorytmów równoległych](#algorithms)  
  
- [Kiedy nie należy używać anulowania](#when)  
  
##  <a name="trees"></a>Drzewa pracy równoległej  
 PPL używa zadań i zadań grup do zarządzania szczegółowych zadań i obliczeń. Grupy zadań do formularza można zagnieżdżać *drzew* pracy równoległych. Na poniższej ilustracji przedstawiono drzewa pracy równoległej. Na tej ilustracji `tg1` i `tg2` reprezentują grupy zadań; `t1`, `t2`, `t3`, `t4`, i `t5` reprezentują pracę, aby wykonać grupy zadań.  
  
 ![Drzewa pracy równoległej](../../parallel/concrt/media/parallelwork_trees.png "parallelwork_trees")  
  
 Poniższy przykład przedstawia kod, który jest wymagany do utworzenia drzewa na ilustracji. W tym przykładzie `tg1` i `tg2` są [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiekty; `t1`, `t2`, `t3`, `t4`, i `t5` są [concurrency::task_handle](../../parallel/concrt/reference/task-handle-class.md) obiektów.  
  
 [!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]  
  
 Można również użyć [concurrency::task_group](reference/task-group-class.md) klasa do tworzenia podobnych drzewa pracy. [Concurrency::task](../../parallel/concrt/reference/task-class.md) klasa obsługuje również pojęcia drzewa pracy. Jednak `task` drzewo jest drzewo zależności. W `task` drzewa, działa przyszłych zakończeniu po bieżących prac. W drzewie grupy zadań wewnętrzny pracy kończy się przed pracy zewnętrznego. Aby uzyskać więcej informacji na temat różnic między zadaniami i grupy zadań, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 [[Górnej](#top)]  
  
##  <a name="tasks"></a>Anulowanie zadań równoległych  

 Istnieje wiele sposobów, aby anulować pracy równoległych. Jest preferowany sposób użycia token anulowania. Grupy zadań również obsługa [concurrency::task_group::cancel](reference/task-group-class.md#cancel) — metoda i [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) metody. Końcowego należy zgłosić wyjątek w treści funkcji pracy zadania. Niezależnie od wybranej metody Dowiedz się, że anulowania nie występuje od razu. Chociaż nowa praca nie jest uruchomiona, jeśli zadania lub grupy zadań zostało anulowane, aktywną pracą musi sprawdzić i odpowiadanie na anulowanie.  

  
 Więcej przykładów, które anulowanie zadań równoległych, zobacz [wskazówki: łączenie za pomocą zadań i żądań XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), [porady: Użyj anulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md), i [porady: użycie Obsługa aby przerwać pętlę równoległą wyjątków](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).  
  
###  <a name="tokens"></a>Przy użyciu Token anulowania do anulowania pracy równoległych  
 `task`, `task_group`, I `structured_task_group` klasy obsługuje anulowania przy użyciu anulowanie tokenów. Definiuje PPL [concurrency::cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) i [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) klas w tym celu. Gdy używasz token anulowania do anulowania pracy środowiska uruchomieniowego nie można uruchomić nowej pracy, które subskrybuje tokenu. Można użyć pracy, który jest już aktywny [is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) funkcji członkowskiej token anulowania i zatrzymywania po może.  
  

 Aby zainicjować anulowanie, należy wywołać [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) metody. Uwzględniał anulowania w następujący sposób:  
  
-   Aby uzyskać `task` obiektów, użyj [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) funkcji. `cancel_current_task`Umożliwia anulowanie bieżącego zadania oraz wszystkie jego kontynuacje na podstawie wartości. (Nie spowoduje anulowania anulowania *tokenu* skojarzonego z zadania lub jej kontynuacje.)  
  
-   Dla grup zadań i algorytmy równoległe, użyj [concurrency::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) funkcji wykrywania anulowania i jak najszybciej zwrócić z treści zadań po powrocie z tej funkcji `true`. (Nie należy wywoływać `cancel_current_task` z grupy zadań.)  

  
 W poniższym przykładzie przedstawiono pierwszy wzorzec podstawowe anulowania zadań. Treść zadania sprawdza od czasu do czasu anulowania wewnątrz pętli.  
  
 [!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]  
  
 `cancel_current_task` Funkcji zgłasza; w związku z tym nie trzeba jawnie zwrócona przez bieżący pętli lub funkcji.  
  
> [!TIP]

>  Alternatywnie możesz wywołać [concurrency::interruption_point](reference/concurrency-namespace-functions.md#interruption_point) funkcji zamiast `cancel_current_task`.  
  
 Ważne jest, aby wywołać `cancel_current_task` po udzieleniu odpowiedzi anulowania ponieważ przechodzi ona na stan Anulowane zadania. Jeśli wcześniej zamiast wywoływać metodę `cancel_current_task`, operacja przejścia do stanu ukończenia i są uruchamiane wszystkie kontynuacje na podstawie wartości.  
  
> [!CAUTION]
>  Nigdy nie zgłaszają `task_canceled` w kodzie. Wywołanie `cancel_current_task` zamiast tego.  
  
 Gdy zadanie kończy się w stanie Anulowane [concurrency::task::get](reference/task-class.md#get) metoda zgłasza [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). (Natomiast [concurrency::task::wait](reference/task-class.md#wait) zwraca [task_status::canceled](reference/concurrency-namespace-enums.md#task_group_status) i nie zgłasza.) Poniższy przykład przedstawia to zachowanie dla utrzymania opartego na zadaniach. Kontynuacja opartego na zadaniach zawsze jest wywoływana, nawet wtedy, gdy poprzedzających zadanie zostało anulowane.  

  
 [!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]  
  
 Ponieważ kontynuacje na podstawie wartości dziedziczą token ich poprzedzających zadań, chyba że zostały utworzone z tokenem jawne, kontynuacje natychmiast wprowadź anulowane stanu, nawet wtedy, gdy nadal jest wykonywane zadanie poprzedzających. W związku z tym wyjątku zgłoszonego przez zadanie poprzedzających po anulowaniu nie są propagowane do zadań kontynuacji. Zawsze anulowania przesłania stan poprzedzających zadania. Poniższy przykład przypomina poprzedni, ale przedstawiono zachowania dla utrzymania na podstawie wartości.  
  
 [!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]  
  
> [!CAUTION]

>  Jeśli nie są przekazywane token anulowania na potrzeby `task` konstruktora lub [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) funkcji, to zadanie nie jest możliwe. Ponadto należy podać ten sam token anulowania do konstruktora jakichkolwiek zadań zagnieżdżonych (to znaczy zadania, które są tworzone w treści innego zadania) aby anulować wszystkie zadania jednocześnie.  
  
 Można uruchomić dowolny kod po anulowaniu token anulowania. Na przykład, jeśli wybierze użytkownika **anulować** przycisk w interfejsie użytkownika, aby anulować operację, można wyłączyć ten przycisk, dopóki użytkownik uruchamia wykonywanie innej operacji. Poniższy przykład przedstawia użycie [concurrency::cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback) metody do rejestrowania funkcji wywołania zwrotnego, która jest uruchamiana, gdy token anulowania zostało anulowane.  

  
 [!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]  
  
 Dokument [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md) objaśniono różnicę między kontynuacje na podstawie wartości i oparty na zadaniach. Jeśli nie podasz `cancellation_token` do zadania kontynuacji obiektu kontynuacji dziedziczy token anulowania zadań poprzedzających w następujący sposób:  
  
-   Na podstawie wartości utrzymania zawsze dziedziczy token anulowania poprzedzających zadania.  
  
-   Kontynuacja opartego na zadaniach nigdy nie dziedziczy token anulowania poprzedzających zadania. Jedynym sposobem, aby utrzymania opartego na zadaniach można anulować jest jawnie Przekaż token anulowania.  
  
 Takie zachowanie nie dotyczy błędnej zadania (to znaczy jedną, która zgłasza wyjątek). W takim przypadku zostało anulowane na podstawie wartości utrzymania; kontynuacja opartego na zadaniach nie została anulowana.  
  
> [!CAUTION]
>  Zadanie, które jest tworzone w innym zadaniu (innymi słowy, zadania zagnieżdżonego) nie dziedziczy token anulowania zadania nadrzędnego. Tylko na podstawie wartości utrzymania dziedziczy token anulowania poprzedzających zadania.  
  
> [!TIP]

>  Użyj [concurrency::cancellation_token:: Brak](reference/cancellation-token-class.md#none) metody podczas wywołania konstruktora lub funkcję, która przyjmuje `cancellation_token` obiektu, a nie chcesz, aby operacja jest możliwe.  
  
 Można też podać token anulowania do konstruktora obiektu `task_group` lub `structured_task_group` obiektu. Ważnym aspektem to jest, że grupy zadań podrzędnych dziedziczy ten token anulowania. Na przykład, która przedstawia tę koncepcję przy użyciu [concurrency::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) funkcji do wywołania `parallel_for`, zobacz [anulowanie algorytmów równoległych](#algorithms) dalszej części tego dokument.  
  
 [[Górnej](#top)]  
  
#### <a name="cancellation-tokens-and-task-composition"></a>Anulowanie tokenów i kompozycji zadania  

 [Współbieżności:: when_all HYPERLINK "http://msdn.microsoft.com/library/system.threading.tasks.task.whenall (v=VS.110).aspx" —](reference/concurrency-namespace-functions.md#when_all) i [concurrency::when_any](reference/concurrency-namespace-functions.md#when_all) funkcje ułatwiają compose wiele zadań do wykonania typowe wzorce. W tej sekcji opisano, jak te funkcje działają z tokenami anulowania.  
  
 Gdy Podaj token anulowania na potrzeby albo `when_all` i `when_any` działanie, że funkcja anuluje tylko w przypadku, gdy token anulowania zostało anulowane lub jednego uczestnika zadań kończy się w stanie anulowane lub zgłasza wyjątek.  
  
 `when_all` Funkcja dziedziczy każdego zadania, które Redaguj ogólną operację, jeśli nie podasz token anulowania do niego token anulowania. Zadanie zwrócone przez `when_all` jest anulowany, gdy dowolne tokeny te są anulowane i co najmniej jednego uczestnika zadań nie została jeszcze uruchomiona lub jest uruchomiony. Podobne zachowanie występuje, gdy jedno z zadań zgłasza wyjątek - zadań, która jest zwracana z `when_all` natychmiast została anulowana z powodu tego wyjątku.  
  
 Środowisko uruchomieniowe wybierze token anulowania dla zadań, która jest zwracana z `when_any` działać po zakończeniu zadania. Jeśli żadne uczestnika zadanie Zakończ w stanie ukończone i co najmniej jednego zadania zgłasza wyjątek, jednego z zadań, które zwrócił jest wybierany do ukończenia `when_any` i jego token jest wybrany jako tokenu końcowego zadania. Jeśli więcej niż jedno zadanie zakończy działanie w ukończonej stanu zadań, która jest zwracana z `when_any` zadań kończy się w stanie ukończone. Środowisko uruchomieniowe podejmie próbę pobrania o zakończeniu zadania, których token nie jest anulowane w chwili zakończenia tak, aby zadanie zostało zwrócone z `when_any` nie jest od razu anulowane, mimo że może zostać ukończone inne zadania wykonywane w późniejszym czasie.  
  
 [[Górnej](#top)]  
  
###  <a name="cancel"></a>Przy użyciu Anuluj metodę, aby anulować pracy równoległych  

 [Concurrency::task_group::cancel](reference/task-group-class.md#cancel) i [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) metody ustawioną anulowane stanu grupy zadań. Po wywołaniu metody `cancel`, grupy zadań nie można uruchomić zadania w przyszłości. `cancel` Metody może być wywoływany przez wielu zadań podrzędnych. Anulowane zadanie sprawia, że [concurrency::task_group::wait](reference/task-group-class.md#wait) i [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait) metod do zwrócenia [concurrency::canceled](reference/concurrency-namespace-enums.md#task_group_status).  

  
 Jeśli grupa zadań została anulowana, wywołania z każdego zadania podrzędne w czasie wykonywania mogą wyzwalać *punktu przerwania*, co powoduje, że środowisko wykonawcze throw i catch typu wyjątek wewnętrzny, aby Anuluj aktywne zadania. Współbieżność środowiska wykonawczego nie definiuje punktów przerwania określonych; mogą one występować w żadnym wywołaniu do środowiska wykonawczego. Środowisko uruchomieniowe musi obsługiwać wyjątki, które zgłasza wyjątek, aby można było wykonać anulowania. W związku z tym nie obsługują nieznany wyjątków w treści zadania.  
  
 Jeśli zadania podrzędnego wykonuje czasochłonna operacja i nie wywołuje w czasie wykonywania, należy okresowo sprawdzaj anulowania i zakończyć w odpowiednim czasie. Poniższy przykład przedstawia sposób określenia, kiedy pracy zostało anulowane. Zadanie `t4` anuluje nadrzędnej grupy zadań, po napotkaniu błędu. Zadanie `t5` od czasu do czasu wywołania `structured_task_group::is_canceling` metodę sprawdzania anulowania. Jeśli grupy nadrzędnej zadanie zostało anulowane, zadanie `t5` drukuje wiadomość i kończy działanie.  
  
 [!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]  
  
 W tym przykładzie sprawdza, czy anulowania na każdym 100<sup>th</sup> iteracji pętli zadań. Częstotliwość, z którym Sprawdź anulowania zależy od ilości pracy, który wykonuje zadania i jak szybko należy na odpowiadanie na anulowanie zadań.  
  
 Jeśli nie masz dostępu do obiektu nadrzędnego grupy zadań, należy wywołać [concurrency::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) funkcji, aby określić, czy grupy nadrzędnej zadanie zostało anulowane.  

  
 `cancel` Metoda ma wpływ tylko na zadania podrzędne. Na przykład, jeśli anulujesz grupy zadań `tg1` na ilustracji drzewa pracy równoległej, wszystkie zadania w drzewie (`t1`, `t2`, `t3`, `t4`, i `t5`) dotyczy problem. Jeśli anulujesz grupy zadania zagnieżdżonego `tg2`, tylko zadania `t4` i `t5` dotyczy problem.  
  
 Podczas wywoływania `cancel` metoda, wszystkie zadania podrzędne grupy również zostały anulowane. Jednak anulowania nie ma wpływu na grupy zadań w formie drzewa pracy równoległej elementów nadrzędnych. W poniższych przykładach pokazano to według budynków na ilustracji drzewa pracy równoległej.  
  
 Pierwsza z tych przykładów tworzy funkcję pracy zadania `t4`, które jest działaniem podrzędnym grupy zadań `tg2`. Funkcja pracy wywołuje funkcję `work` w pętli. Jeśli w żadnym wywołaniu, aby `work` kończy się niepowodzeniem, zadanie anuluje jej nadrzędnej grupy zadań. Powoduje to, że grupy zadań `tg2` wprowadzenia anulowane stanu, ale nie spowoduje anulowania zadań — grupa `tg1`.  
  
 [!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]  
  
 W tym przykładzie drugi podobny pierwsza z nich, z wyjątkiem tego, że zadanie anuluje grupy zadań `tg1`. Ma to wpływ na wszystkie zadania w drzewie (`t1`, `t2`, `t3`, `t4`, i `t5`).  
  
 [!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]  
  
 `structured_task_group` Klasa nie jest bezpieczne wątkowo. W związku z tym zadania podrzędnego która wywołuje metodę nadrzędnego `structured_task_group` obiektu powoduje zachowanie nieokreślony. Wyjątkiem od tej reguły jest `structured_task_group::cancel` i [concurrency::structured_task_group::is_canceling](reference/structured-task-group-class.md#is_canceling) metody. Zadania podrzędnego można wywołać tych metod, aby anulować nadrzędnej grupy zadań i sprawdź, czy anulowania.  

 
> [!CAUTION]
>  Mimo że używasz token anulowania do anulowania pracy, które jest przeprowadzane przez grupy zadań, która działa jako element podrzędny `task` obiektu, nie można użyć `task_group::cancel` lub `structured_task_group::cancel` metod, aby anulować `task` obiektów, które są uruchamiane w grupie zadań.  
  
 [[Górnej](#top)]  
  
###  <a name="exceptions"></a>Używanie wyjątków można anulować pracy równoległych  
 Użycie anulowanie tokenów i `cancel` metody są bardziej wydajne niż obsługi na anulowanie drzewa pracy równoległej wyjątków. Anulowanie tokenów i `cancel` metody anulowanie zadania i wszystkie zadania podrzędne w sposób góra dół. Z drugiej strony Obsługa wyjątków w sposób dołu do góry i musiał zrezygnować z każdej grupy zadań podrzędnych niezależnie jako wyjątek w górę propaguje. Temat [obsługi wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) wyjaśniono, jak współbieżności środowiska wykonawczego używa wyjątków do komunikowania się błędy. Jednak nie wszystkie wyjątki oznaczać błąd. Na przykład algorytmu wyszukiwania może spowodować anulowanie jego skojarzonego zadania, gdy znajdzie wynik. Jak wspomniano wcześniej, obsługa wyjątków jest jednak mniej wydajne niż przy użyciu `cancel` metodę, aby anulować pracy równoległych.  
  
> [!CAUTION]
>  Zalecane jest użycie wyjątków można anulować pracy równoległej tylko wtedy, gdy jest to konieczne. Anulowanie tokenów i grupy zadań `cancel` metody są bardziej wydajne i mniej podatne na błędy.  
  
 W przypadku zgłoszenia wyjątku w treści funkcji pracy, który jest przekazywany do grupy zadań, środowisko uruchomieniowe przechowuje ten wyjątek i marshals wyjątek do kontekstu, która oczekuje na grupy zadań zakończyć. Jak `cancel` metody środowiska uruchomieniowego odrzuca wszystkie zadania, które nie zostały jeszcze uruchomione, a nie przyjmuje nowych zadań.  
  
 W tym przykładzie trzeci podobny drugi, z wyjątkiem tego zadania `t4` zgłasza wyjątek, aby anulować grupy zadań `tg2`. W tym przykładzie użyto `try` - `catch` bloku do sprawdzenia anulowania podczas grupy zadań `tg2` czeka na zakończenie jego zadań podrzędnych. Tak jak w pierwszym przykładzie powoduje grupy zadań `tg2` wprowadzenia anulowane stanu, ale nie spowoduje anulowania zadań — grupa `tg1`.  
  
 [!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]  
  
 W tym przykładzie czwarty wykorzystuje obsługi wyjątków do anulowania pracy całego drzewa. Przykład przechwytuje wyjątek podczas zadań grupy `tg1` czeka na zakończenie zamiast podczas jego zadań podrzędnych zadania grupy `tg2` czeka na jego zadań podrzędnych. Podobnie jak drugi przykład powoduje to, że obie grupy zadań w drzewie `tg1` i `tg2`, aby wprowadzić stan anulowane.  
  
 [!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]  
  
 Ponieważ `task_group::wait` i `structured_task_group::wait` metody throw podczas zadania podrzędnego zgłasza wyjątek, nie mają wartości zwracanej z nich.  
  
 [[Górnej](#top)]  
  
##  <a name="algorithms"></a>Anulowanie algorytmów równoległych  
 Równoległe algorytmów w PPL, na przykład `parallel_for`, tworzenie grup zadań. W związku z tym umożliwia wiele z tych samych metod anulowanie algorytmów równoległych.  
  
 Poniższe przykłady przedstawiają kilka sposobów anulowanie algorytmów równoległych.  
  
 W poniższym przykładzie użyto `run_with_cancellation_token` funkcji do wywołania `parallel_for` algorytmu. `run_with_cancellation_token` Funkcja przyjmuje jako argument token anulowania i wywołuje określona funkcja pracy synchronicznie. Ponieważ algorytmy równoległe są wbudowane w system zadania, dziedziczą token anulowania zadania nadrzędnego. W związku z tym `parallel_for` mogą odpowiadać na anulowanie.  
  
 [!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]  
  

 W poniższym przykładzie użyto [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait) metodę do wywołania `parallel_for` algorytmu. `structured_task_group::run_and_wait` Metody czeka na zakończenie zadania podane. `structured_task_group` Obiektu włącza funkcję pracy można anulować zadania.  
  
 [!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
The task group status is: canceled.  
```  
  
 W poniższym przykładzie użyto obsługi wyjątków, aby anulować `parallel_for` pętli. Środowisko uruchomieniowe marshals wyjątek Kontekst wywołania.  
  
 [!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
Caught 50  
```  
  
 W poniższym przykładzie użyto Flaga wartości logicznej do koordynowania anulowanie w `parallel_for` pętli. Co zadanie jest uruchamiane, ponieważ nie jest używane w tym przykładzie `cancel` metody lub wyjątek Obsługa anulowania ogólną zestawu zadań. W związku z tym ta technika może mieć większe obliczeniową koszty niż mechanizm anulowania.  
  
 [!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]  
  
 Każda metoda anulowania ma zalet w porównaniu z jej innym osobom. Wybierz metodę, która pasuje do określonych potrzeb.  
  
 [[Górnej](#top)]  
  
##  <a name="when"></a>Kiedy nie należy używać anulowania  
 Korzystanie z anulowania jest odpowiednie, gdy każdego członka grupy powiązanych zadań mogą zakończyć się w odpowiednim czasie. Istnieją sytuacje, w którym anulowania nie może być odpowiedni dla twojej aplikacji. Na przykład ponieważ anulowanie zadania jest współpracy, ogólną zestawu zadań nie spowoduje anulowanie zablokowanie poszczególnych zadań. Na przykład jeśli jedno zadanie nie została jeszcze uruchomiona, ale jego odblokowuje inne aktywne zadanie, go nie zostanie uruchomiona Jeśli grupy zadań została anulowana. Może to spowodować zakleszczenie w aplikacji. Drugi przykładem gdzie stosowania anulowania mogą nie być odpowiednie jest zadanie zostało anulowane, ale jego zadań podrzędnych wykonuje operację ważne, takich jak zwalnianie zasobu. Ponieważ ogólną zestawu zadań została anulowana po anulowaniu zadaniem nadrzędnym, ta operacja nie zostanie wykonany. Na przykład, który ilustruje tę sytuację, zobacz [opis sposobu anulowania i wyjątek obsługi wpływają na zniszczeniem obiektu](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) części najlepsze rozwiązania w temacie Biblioteka równoległych wzorców.  
  
 [[Górnej](#top)]  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: używanie anulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Przedstawia sposób użycia anulowania do zaimplementowania algorytmu wyszukiwania równoległego.|  
|[Instrukcje: używanie obsługi wyjątków, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Przedstawia sposób użycia `task_group` klasa umożliwiająca zapisanie algorytmu wyszukiwania dla struktury drzewa podstawowe.|  
|[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Opisuje sposób obsługi wyjątków, które są generowane przez grupy zadań, zadań lekkich i agentów asynchronicznych przez środowisko uruchomieniowe i odpowiadanie na wyjątków w aplikacji.|  
|[Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Opisuje sposób zadania odnoszą się do grup zadań i używania zadań i niestrukturalnych w aplikacji.|  
|[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)|W tym artykule opisano algorytmy równoległe, które jednocześnie wykonywania pracy na zbiory danych|  
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Zawiera omówienie Biblioteka równoległych wzorców.|  
  
## <a name="reference"></a>Tematy pomocy  
 [task, klasa (środowisko uruchomieniowe współbieżności)](../../parallel/concrt/reference/task-class.md)  
  
 [cancellation_token_source, klasa](../../parallel/concrt/reference/cancellation-token-source-class.md)  
  
 [cancellation_token, klasa](../../parallel/concrt/reference/cancellation-token-class.md)  
  
 [task_group — klasa](reference/task-group-class.md)  
  
 [structured_task_group, klasa](../../parallel/concrt/reference/structured-task-group-class.md)  

 [parallel_for — funkcja](reference/concurrency-namespace-functions.md#parallel_for)


