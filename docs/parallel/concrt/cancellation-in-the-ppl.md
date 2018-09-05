---
title: Anulowanie w PPL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 287e540f73b202229c0355aec55aa0d8f5e0421f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690452"
---
# <a name="cancellation-in-the-ppl"></a>Anulowanie w PPL
W tym dokumencie opisano rolę anulowania w Biblioteka równoległych wzorców (PPL), jak anulować czynność równoległą i jak określić, kiedy zostanie anulowane równoległą pracę.  
  
> [!NOTE]
>  Środowisko wykonawcze używa obsługi wyjątków do implementacji anulowania. Catch lub nie obsługiwać tych wyjątków w kodzie. Ponadto firma Microsoft zaleca, pisanie kodu bezpieczne pod względem wyjątków w treści funkcji, dla zadań podrzędnych. Na przykład można użyć *inicjowania jest pozyskiwanie zasobów* wzorca (RAII) w celu zapewnienia zasobów są poprawnie obsługiwania gdy wyjątek jest zgłaszany w treści zadania. Aby uzyskać kompletny przykład używa wzór RAII czyszczenie zasobów w ramach można anulować zadania, zobacz [przewodnik: usuwanie pracy z wątku interfejsu użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md).  
  
## <a name="key-points"></a>Kwestie kluczowe  
  
-   Anulowanie jest wspólne i obejmuje koordynacji między kodem, który żąda anulowania i zadanie, które odpowiada na operację anulowania.  
  
-   Jeśli to możliwe, należy użyć tokenów anulowania do anulowania pracy. [Concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) klasa definiuje token anulowania.  
  

-   W przypadku użycia tokenów anulowania użyć [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) metodę, aby zainicjować anulowanie i [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) funkcję, aby odpowiedzieć anulowanie. Użyj [concurrency::cancellation_token::is_canceled](reference/cancellation-token-class.md#is_canceled) metodę sprawdzania, czy każde inne zadanie zażądał anulowania.
  
-   Unieważnieniu nastąpić z opóźnieniem. Mimo że nowa praca nie została uruchomiona, jeśli zadania lub grupy zadań zostanie anulowane, aktywną pracą należy sprawdzić i reagowanie na operację anulowania.  
  
-   Kontynuacja oparta na wartościach dziedziczy token anulowania zadania poprzedzającego. Kontynuacja oparta na zadaniach nigdy nie dziedziczy token zadania poprzedzającego.  
  
-   Użyj [concurrency::cancellation_token:: none](reference/cancellation-token-class.md#none) metody podczas wywołania konstruktora lub funkcji, która przyjmuje `cancellation_token` obiekt, ale nie chcesz, aby operacja jest możliwe. Ponadto jeśli nie przekażesz token anulowania do [concurrency::task](../../parallel/concrt/reference/task-class.md) konstruktora lub [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) funkcji, to zadanie nie jest możliwe.  


  
##  <a name="top"></a> W tym dokumencie  
  
- [Równoległe drzewka pracy](#trees)  
  
- [Anulowanie zadań równoległych](#tasks)  
  
    - [Korzystając z tokena odwołania, aby anulować czynność równoległą](#tokens)  
  
    - [Korzystając z metody, aby anulować czynność równoległą odwołania](#cancel)  
  
    - [Używanie wyjątków, aby anulować czynność równoległą](#exceptions)  
  
- [Anulowanie algorytmów równoległych](#algorithms)  
  
- [Kiedy nie należy używać odwołania](#when)  
  
##  <a name="trees"></a> Równoległe drzewka pracy  
 PPL korzysta grupy zadań i zarządzanie szczegółowych zadań i obliczeń. Można zagnieżdżać grup zadań do formularza *drzew* równoległej pracy. Poniższa ilustracja przedstawia drzewa pracy równoległej. Na tej ilustracji `tg1` i `tg2` reprezentowania grup zadań; `t1`, `t2`, `t3`, `t4`, i `t5` reprezentowania grup zadań wykonywania pracy.  
  
 ![Drzewa pracy równoległej](../../parallel/concrt/media/parallelwork_trees.png "parallelwork_trees")  
  
 Poniższy przykład pokazuje kod, który jest wymagany, aby utworzyć drzewo na ilustracji. W tym przykładzie `tg1` i `tg2` są [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiekty; `t1`, `t2`, `t3`, `t4`, i `t5` są [concurrency::task_handle](../../parallel/concrt/reference/task-handle-class.md) obiektów.  
  
 [!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]  
  
 Można również użyć [concurrency::task_group](reference/task-group-class.md) klasy w celu utworzenia podobne drzewa pracy. [Concurrency::task](../../parallel/concrt/reference/task-class.md) klasy obsługuje również pojęcie drzewa pracy. Jednak `task` drzewo jest drzewo zależności. W `task` drzewie przyszłe działania kończy się po bieżącą pracę. W drzewie grupy zadań wewnętrzny zakończeniu zanim praca zewnętrznego. Aby uzyskać więcej informacji na temat różnic między grupy zadań i zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 [[Górnej](#top)]  
  
##  <a name="tasks"></a> Anulowanie zadań równoległych  

 Istnieje wiele sposobów, aby anulować czynność równoległą. Jest preferowany sposób użycia tokenu anulowania. Grupy zadań również obsługę [concurrency::task_group::cancel](reference/task-group-class.md#cancel) metody i [CONCURRENCY::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) metody. Końcowe sposób polega na zgłoszenie wyjątku w treści funkcji roboczych zadania. Bez względu na to wybór metody Dowiedz się, że anulowanie nastąpić z opóźnieniem. Mimo że nowa praca nie została uruchomiona, jeśli zadania lub grupy zadań zostanie anulowane, aktywną pracą należy sprawdzić i reagowanie na operację anulowania.  

  
 Więcej przykładów, które anulowanie zadań równoległych, zobacz [wskazówki: łączenie za pomocą zadań i żądań XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), [jak: Użyj anulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md), i [porady: użycie Obsługa aby przerwać pętlę równoległą wyjątków](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).  
  
###  <a name="tokens"></a> Korzystając z tokena odwołania, aby anulować czynność równoległą  
 `task`, `task_group`, I `structured_task_group` klasy obsługują anulowania przy użyciu tokenów anulowania. PPL definiuje [concurrency::cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) i [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) klas w tym celu. Gdy używasz token anulowania do anulowania pracy, środowisko wykonawcze nie można uruchomić nowych prac, które subskrybuje ten token. Pracy, która jest już aktywna, można użyć [is_canceled —](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) funkcja elementu członkowskiego do monitorowania anulowania i Zatrzymaj, gdy jest to możliwe.  
  

 Aby zainicjować anulowanie, należy wywołać [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) metody. Użytkownik odpowie na operację anulowania w następujący sposób:  
  
-   Aby uzyskać `task` obiekty, używają [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) funkcji. `cancel_current_task` Anuluje bieżące zadanie i wszystkich jego kontynuacji na podstawie wartości. (Nie powoduje anulowania anulowania *tokenu* która jest skojarzona z zadaniem lub jego kontynuacji.)  
  
-   Dla grup zadań i algorytmów równoległych, należy użyć [concurrency::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) funkcję, aby wykryć anulowania i jak najszybciej zwrócić z treści zadania, gdy ta funkcja zwraca `true`. (Nie należy wywoływać metody `cancel_current_task` z grupy zadań.)  

  
 Poniższy przykład pokazuje pierwszy podstawowy wzorzec anulowania zadania. Treść zadania okresowo sprawdza, czy anulowania wewnątrz pętli.  
  
 [!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]  
  
 `cancel_current_task` Funkcja zgłasza wyjątek; w związku z tym, nie trzeba jawnie zwrócona przez bieżącą pętlę lub funkcji.  
  
> [!TIP]

>  Ewentualnie możesz wywołać [concurrency::interruption_point](reference/concurrency-namespace-functions.md#interruption_point) zamiast funkcji `cancel_current_task`.  
  
 Ważne jest, aby wywołać `cancel_current_task` po użytkownik reagowanie na operację anulowania ponieważ nastąpi przejście zadania do stanu Anulowano. Jeśli wcześniej zwrócisz zamiast wywołać `cancel_current_task`, operacja przechodzi do stanu ukończenia i wszelkie kontynuacje na podstawie wartości są uruchamiane.  
  
> [!CAUTION]
>  Nigdy nie zgłaszają `task_canceled` w kodzie. Wywołaj `cancel_current_task` zamiast tego.  
  
 Jeśli zadanie zakończy się ze stanem anulowane, [CONCURRENCY::Task](reference/task-class.md#get) metoda zgłasza wyjątek [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). (I odwrotnie, [CONCURRENCY::Task](reference/task-class.md#wait) zwraca [task_status::canceled](reference/concurrency-namespace-enums.md#task_group_status) i nie generuje.) Poniższy przykład ilustruje takie zachowanie dla kontynuacji opartej na zadaniach. Kontynuacja oparta na zadaniach zawsze jest wywoływany, nawet wtedy, gdy zadanie poprzedzające zostało anulowane.  

  
 [!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]  
  
 Ponieważ na podstawie wartości kontynuacji dziedziczyć token swoje zadania poprzedzającego, chyba że zostały utworzone z tokenem jawne, kontynuacji natychmiast wprowadź stanem anulowane, nawet wtedy, gdy zadanie poprzedzające jest nadal wykonywane. W związku z tym każdy wyjątek, który jest generowany przez zadanie poprzedzające po anulowaniu nie są propagowane do zadań kontynuacji. Unieważnieniu zawsze zastępuje stan zadania poprzedzającego. Poniższy przykład jest podobny do poprzedniego, ale przedstawiono zachowania dla kontynuacji na podstawie wartości.  
  
 [!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]  
  
> [!CAUTION]

>  Jeśli nie przekażesz token anulowania do `task` konstruktora lub [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) funkcji, to zadanie nie jest możliwe. Ponadto należy przekazać ten sam token odwołania do konstruktora żadnych zadań zagnieżdżonych (oznacza to, zadania, które są tworzone w treści innego zadania) aby anulować wszystkie zadania jednocześnie.  
  
 Można uruchomić dowolny kod, gdy token anulowania jest anulowane. Na przykład, jeśli użytkownik wybierze **anulować** przycisku w interfejsie użytkownika, aby anulować operację, można wyłączyć ten przycisk, dopóki użytkownik rozpocznie wykonywanie innej operacji. Poniższy przykład pokazuje, jak używać [CONCURRENCY::cancellation_token:: register_callback](reference/cancellation-token-class.md#register_callback) metodę, aby zarejestrować funkcji wywołania zwrotnego, który jest uruchamiany, gdy token anulowania, zostanie anulowane.  

  
 [!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]  
  
 Dokument [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md) wyjaśnia różnicę pomiędzy na podstawie wartości i według zadań kontynuacji. Jeśli nie podasz `cancellation_token` obiektu zadanie kontynuacji, kontynuacja dziedziczy token anulowania zadania poprzedzającego w następujący sposób:  
  
-   Kontynuacja oparta na wartościach zawsze dziedziczy token anulowania zadania poprzedzającego.  
  
-   Kontynuacja oparta na zadaniach nigdy nie dziedziczy token anulowania zadania poprzedzającego. Jedynym sposobem, aby utworzyć kontynuację opartą na zadaniach cancelable jest jawnie przekazać token anulowania.  
  
 Takie zachowanie nie dotyczy uszkodzoną zadania, (oznacza to, że jeden, która zgłosiła wyjątek). W takim przypadku kontynuacja oparta na wartościach zostało anulowane; kontynuacja oparta na zadaniach nie zostało anulowane.  
  
> [!CAUTION]
>  Zadanie, które jest tworzony w innym zadaniu (innymi słowy, zadanie zagnieżdżone) nie dziedziczy token anulowania zadania nadrzędnego. Tylko kontynuacja oparta na wartościach dziedziczy token anulowania zadania poprzedzającego.  
  
> [!TIP]

>  Użyj [concurrency::cancellation_token:: none](reference/cancellation-token-class.md#none) metody podczas wywołania konstruktora lub funkcji, która przyjmuje `cancellation_token` obiektu i chcesz, aby być można anulować, operacja.  
  
 Możesz też podać token anulowania do konstruktora obiektu `task_group` lub `structured_task_group` obiektu. Ważnym aspektem to to, że grupy zadań podrzędnych dziedziczyć ten token anulowania. Na przykład, który pokazuje tę koncepcję przy użyciu [concurrency::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) uruchamianie do wywołania funkcji `parallel_for`, zobacz [anulowanie algorytmów równoległych](#algorithms) później w tym dokument.  
  
 [[Górnej](#top)]  
  
#### <a name="cancellation-tokens-and-task-composition"></a>Anulowanie tokenów i kompozycji zadania  

 [Concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) i [concurrency::when_any](reference/concurrency-namespace-functions.md#when_all) functions może pomóc w komponowaniu wielu zadań do realizacji typowych wzorców. W tej sekcji opisano, jak te funkcje używają tokenów anulowania.  
  
 Kiedy podasz token anulowania do jednej `when_all` i `when_any` funkcji, że funkcja anuluje tylko wtedy, gdy ten token anulowania, zostanie anulowane, lub gdy jeden z uczestnika zadań kończy się na stanem anulowane lub zgłasza wyjątek.  
  
 `when_all` Funkcja dziedziczy każdego zadania, który komponuje całej operacji, jeśli nie podasz token anulowania do niego token anulowania. Zadanie, które jest zwracana z `when_all` anulowany, gdy dowolne tokeny te są anulowane i co najmniej jednego uczestnika zadania nie została jeszcze uruchomiona lub jest uruchomiona. Podobne zachowanie występuje, gdy jedno z zadań zgłasza wyjątek — zadanie, które jest zwracana z `when_all` natychmiast zostało anulowane z tego wyjątku.  
  
 Środowisko wykonawcze wybiera token anulowania zadania, który jest zwracany z `when_any` działać po zakończeniu tego zadania. Jeśli żaden z uczestnika zadania zakończone w stanu ukończenia i zgłasza wyjątek, jeden lub więcej zadań, jest jedno z zadań, które zgłosiło wybierany do ukończenia `when_any` i jego token jest wybierany jako tokenu końcowego zadania. Jeśli więcej niż jedno zadanie zakończy się w ukończonej stanu zadania, który jest zwracany z `when_any` zadanie kończy się w stanie ukończone. Środowisko uruchomieniowe podejmie próbę pobrania ukończonego zadania podrzędnego, którego token nie został anulowany w momencie zakończenia tak, aby zadanie zostało zwrócone w wyniku `when_any` nie jest od razu anulowane, nawet jeśli inne wykonywanie zadania może wykonać w dowolnym momencie.  
  
 [[Górnej](#top)]  
  
###  <a name="cancel"></a> Korzystając z metody, aby anulować czynność równoległą odwołania  

 [Concurrency::task_group::cancel](reference/task-group-class.md#cancel) i [CONCURRENCY::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) metody równa stanem anulowane grupy zadań. Po wywołaniu metody `cancel`, grupy zadań nie można uruchomić zadania w przyszłości. `cancel` Metody mogą być wywoływane przez wiele zadań podrzędnych. Anulowano zadanie sprawia, że [CONCURRENCY::task_group:: wait](reference/task-group-class.md#wait) i [CONCURRENCY::structured_task_group:: wait](reference/structured-task-group-class.md#wait) metody, aby zwrócić [concurrency::canceled](reference/concurrency-namespace-enums.md#task_group_status).  

  
 Jeśli grupa zadań zostanie anulowane, wywołania z każdego zadania podrzędne w czasie wykonywania mogą wyzwalać *punkcie przerwania*, co powoduje, że środowisko uruchomieniowe throw i catch typ wyjątku wewnętrznego Anuluj aktywne zadania. Środowisko uruchomieniowe współbieżności nie definiuje punktów przerwania określone. one może wystąpić w żadnym wywołaniu, do środowiska uruchomieniowego. Środowisko wykonawcze musi obsługiwać wyjątki, które wyniku weryfikacji zgłasza wyjątek w celu anulowania wykonywania. W związku z tym nie obsługują nieznany wyjątków w treści zadania.  
  
 Jeśli zadanie podrzędne wykonuje czasochłonna operacja i nie mogą wywoływać środowiska uruchomieniowego, należy okresowo sprawdzania występowania unieważnienia i zakończyć w odpowiednim czasie. Poniższy przykład przedstawia sposób określenia, kiedy praca została anulowana. Zadanie `t4` anuluje grupę nadrzędną zadań po napotkaniu błędu. Zadanie `t5` od czasu do czasu wywołania `structured_task_group::is_canceling` metody do sprawdzania występowania unieważnienia. Jeśli grupę nadrzędną zadań zostanie anulowane, zadanie `t5` drukuje wiadomość, a następnie kończy działanie.  
  
 [!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]  
  
 W tym przykładzie wyszukuje anulowania na każde 100<sup>th</sup> iteracji pętli zadania. Częstotliwość, z którym sprawdzania występowania unieważnienia zależy od ilości pracy, który wykonuje zadania i jak szybko należy na reagowanie na operację anulowania zadań.  
  
 Jeśli nie masz dostępu do obiektu grupy zadania nadrzędnego, należy wywołać [concurrency::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) funkcję, aby określić, czy grupę nadrzędną zadań zostanie anulowane.  

  
 `cancel` Metoda ma wpływ tylko na zadań podrzędnych. Na przykład, jeśli anulujesz grupy zadań `tg1` na ilustracji drzewa pracy równoległej, wszystkie zadania w drzewie (`t1`, `t2`, `t3`, `t4`, i `t5`) dotyczy problem. Jeśli anulujesz zadanie zagnieżdżone grupy, `tg2`, tylko zadania `t4` i `t5` dotyczy problem.  
  
 Gdy wywołujesz `cancel` metody, wszystkie zadania podrzędnego grupy również zostaną anulowane. Jednak anulowania nie ma wpływu na wszystkie elementy nadrzędne grupy zadań w drzewie równoległej pracy. W poniższych przykładach pokazano to w postaci ilustracji drzewa pracy równoległej.  
  
 Pierwsza z tych przykładów tworzy funkcję pracy zadania `t4`, który jest elementem podrzędnym grupy zadań `tg2`. Ta funkcja pracy wywołuje funkcję `work` w pętli. Jeśli w żadnym wywołaniu, aby `work` zakończy się niepowodzeniem, zadanie anuluje jej nadrzędnej grupy zadań. Powoduje to, że grupa zadań `tg2` wprowadzenia stanem anulowane, ale nie powoduje anulowania zadań — grupa `tg1`.  
  
 [!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]  
  
 Ten drugi przykład jest podobny pierwszą z nich, z tą różnicą, że zadanie anuluje zadań — grupa `tg1`. Ma to wpływ na wszystkie zadania w drzewie (`t1`, `t2`, `t3`, `t4`, i `t5`).  
  
 [!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]  
  
 `structured_task_group` Klasa nie jest metodą o bezpiecznych wątkach. W związku z tym, zadanie podrzędne, wywołuje metodę jego elementu nadrzędnego `structured_task_group` obiektu tworzy nieokreślone zachowanie. Wyjątkiem od tej reguły jest `structured_task_group::cancel` i [CONCURRENCY::structured_task_group:: is_canceling](reference/structured-task-group-class.md#is_canceling) metody. Zadanie podrzędne może wywoływać te metody, aby anulować grupę nadrzędną zadań i sprawdzania występowania unieważnienia.  

 
> [!CAUTION]
>  Chociaż można używać token anulowania do anulowania pracy wykonywanej przez grupy zadań, która działa jako element podrzędny elementu `task` obiektu, nie można użyć `task_group::cancel` lub `structured_task_group::cancel` metody, aby anulować `task` obiekty, które są uruchamiane w grupie zadań.  
  
 [[Górnej](#top)]  
  
###  <a name="exceptions"></a> Używanie wyjątków, aby anulować czynność równoległą  
 Użycie tokenów anulowania i `cancel` metody są bardziej wydajne niż Obsługa na anulowanie drzewa pracy równoległej wyjątków. Anulowanie tokenów i `cancel` metoda anulowanie zadania i wszystkie zadania podrzędne w sposób góra dół. Z drugiej strony Obsługa wyjątków działa w sposób od dołu do góry i musi anulować każda grupa zadań podrzędnych niezależnie jako wyjątek propaguje w górę. Temat [wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) wyjaśnia, jak środowisko uruchomieniowe współbieżności używa wyjątków do komunikowania się błędy. Jednak nie wszystkie wyjątki wskazywać na błąd. Na przykład algorytm wyszukiwania może spowodować anulowanie jego skojarzone zadania, gdy znajdzie wynik. Jak wspomniano wcześniej, obsługa wyjątków jest jednak mniej wydajne niż przy użyciu `cancel` metodę, aby anulować czynność równoległą.  
  
> [!CAUTION]
>  Firma Microsoft zaleca, użyj wyjątków, aby anulować czynność równoległą tylko wtedy, gdy jest to konieczne. Anulowanie tokenów i grupy zadań `cancel` metody są bardziej efektywne i mniej podatne na błędy.  
  
 Gdy zgłoszenie wyjątku w treści funkcji pracy, który jest przekazywany do grupy zadań, środowisko uruchomieniowe przechowuje ten wyjątek i kieruje wyjątku do kontekstu, która czeka, aż grupy zadań zakończyć. Podobnie jak w przypadku `cancel` metody, środowisko uruchomieniowe odrzuca wszystkie zadania, które nie zostały rozpoczęte, a nie przyjmuje nowych zadań.  
  
 Trzeci przykład jest podobny drugi, chyba że to zadanie `t4` zgłasza wyjątek, aby anulować grupę zadań `tg2`. W tym przykładzie użyto `try` - `catch` bloku do sprawdzania występowania unieważnienia podczas grupy zadań `tg2` czeka na zakończenie jego zadań podrzędnych. Podobnie jak w pierwszym przykładzie powoduje to, że grupa zadań `tg2` wprowadzenia stanem anulowane, ale nie powoduje anulowania zadań — grupa `tg1`.  
  
 [!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]  
  
 W tym przykładzie czwarty używa obsługi wyjątków można anulować w drzewie całej pracy. Przykład przechwytuje wyjątek podczas zadania grupy `tg1` czeka na zakończenie zamiast podczas jego zadań podrzędnych zadania grupy `tg2` czeka na jego zadań podrzędnych. Podobnie jak w drugim przykładzie powoduje to, że obie grupy zadań w drzewie `tg1` i `tg2`, aby wprowadzić stanem anulowane.  
  
 [!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]  
  
 Ponieważ `task_group::wait` i `structured_task_group::wait` metody throw, gdy zadanie podrzędne zgłasza wyjątek, wartość zwracana nie jest wyświetlany z nich.  
  
 [[Górnej](#top)]  
  
##  <a name="algorithms"></a> Anulowanie algorytmów równoległych  
 Równoległe algorytmy w PPL, na przykład `parallel_for`, tworzenie grup zadań. W związku z tym służy wiele z tych samych technik do anulowania algorytmu równoległego.  
  
 Poniższe przykłady ilustrują kilka sposobów, aby anulować algorytmu równoległego.  
  
 W poniższym przykładzie użyto `run_with_cancellation_token` funkcji do wywołania `parallel_for` algorytmu. `run_with_cancellation_token` Funkcji Trwa anulowanie token jako argument i wywołuje podana funkcja pracy synchronicznie. Ponieważ algorytmy równoległe są kompilowane na zadania, dziedziczą one token anulowania zadania nadrzędnego. W związku z tym `parallel_for` mogą odpowiadać na operację anulowania.  
  
 [!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]  
  

 W poniższym przykładzie użyto [CONCURRENCY::structured_task_group::](reference/structured-task-group-class.md#run_and_wait) metodę do wywołania `parallel_for` algorytmu. `structured_task_group::run_and_wait` Metoda czeka na zakończenie zadania podane. `structured_task_group` Obiektu włącza funkcję pracy, aby anulować zadania.  
  
 [!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]  
  
 Ten przykład generuje następujące dane wyjściowe.  
  
```Output  
The task group status is: canceled.  
```  
  
 W poniższym przykładzie użyto obsługi wyjątków, aby anulować `parallel_for` pętli. Środowisko uruchomieniowe kieruje wyjątkiem Kontekst wywołania.  
  
 [!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]  
  
 Ten przykład generuje następujące dane wyjściowe.  
  
```Output  
Caught 50  
```  
  
 W poniższym przykładzie Flaga wartości logicznej do koordynowania anulowanie w `parallel_for` pętli. Każde zadanie jest uruchamiane, ponieważ w tym przykładzie nie używa `cancel` metody lub wyjątek obsługi anulowania ogólny zestaw zadań. W związku z tym ta technika może mieć więcej obciążenia niż mechanizm anulowania.  
  
 [!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]  
  
 Każda metoda anulowania ma zalety w porównaniu z innymi. Wybierz metodę, która pasuje do konkretnych potrzeb.  
  
 [[Górnej](#top)]  
  
##  <a name="when"></a> Kiedy nie należy używać odwołania  
 Użyj anulowania jest odpowiednie, jeśli każdy członek grupy powiązanych zadań można zakończyć w odpowiednim czasie. Istnieją jednak sytuacje, w którym anulowania mogą nie być odpowiednie dla twojej aplikacji. Na przykład ponieważ anulowanie zadania jest wspólne, ogólny zestaw zadań nie spowoduje anulowanie, jeśli wszystkie pojedyncze zadanie jest zablokowany. Na przykład jeśli jedno zadanie nie zostało jeszcze uruchomione, ale jej odblokowuje inną aktywnych zadań, go nie zostanie uruchomiona, jeśli grupa zadań zostanie anulowane. Może to spowodować zakleszczenie w aplikacji. Drugi przykład, z którym użytkowania anulowania mogą nie być odpowiednie jest, gdy zadanie jest anulowane, ale jego zadań podrzędnych wykonuje operację ważne, taką jak zwalnianie zasobu. Ponieważ w całym zestawie zadań zostanie anulowane po anulowaniu zadania nadrzędnego, nie będzie wykonywał tej operacji. Na przykład, który ilustruje ten punkt, zobacz [opis sposobu anulowania i wyjątków obsługi wpływają na zniszczenie obiektu](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) sekcji najlepszych rozwiązań w temacie Biblioteka równoległych wzorców.  
  
 [[Górnej](#top)]  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: używanie anulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Pokazuje, jak należy używać odwołania do zaimplementowania algorytmu wyszukiwania równoległego.|  
|[Instrukcje: używanie obsługi wyjątków, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Ilustruje sposób używania `task_group` klasę umożliwiającą zapisanie algorytmu wyszukiwania dla struktury drzewa podstawowe.|  
|[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|W tym artykule opisano, jak środowisko wykonawcze obsługuje wyjątki wyrzucane przez grupy zadań, lekkie zadanie i agentów asynchronicznych i odpowiadania na wyjątki w aplikacjach.|  
|[Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|W tym artykule opisano, jak zadania odnoszą się do grup zadań i jak można użyć zadań bez struktury i ze strukturą w swoich aplikacjach.|  
|[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)|W tym artykule opisano algorytmów równoległych, które jednocześnie wykonują prace na zbiory danych|  
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Omówienie biblioteki wzorców równoległych.|  
  
## <a name="reference"></a>Tematy pomocy  
 [task, klasa (środowisko uruchomieniowe współbieżności)](../../parallel/concrt/reference/task-class.md)  
  
 [cancellation_token_source, klasa](../../parallel/concrt/reference/cancellation-token-source-class.md)  
  
 [cancellation_token, klasa](../../parallel/concrt/reference/cancellation-token-class.md)  
  
 [task_group — klasa](reference/task-group-class.md)  
  
 [structured_task_group, klasa](../../parallel/concrt/reference/structured-task-group-class.md)  

 [parallel_for — funkcja](reference/concurrency-namespace-functions.md#parallel_for)


