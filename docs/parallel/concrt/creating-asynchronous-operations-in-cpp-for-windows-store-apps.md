---
title: Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy uniwersalnej systemu Windows
ms.date: 11/19/2018
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
ms.openlocfilehash: 635a8c95a3801c6e88feff1cefa3ed27727a8f88
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032190"
---
# <a name="creating-asynchronous-operations-in-c-for-uwp-apps"></a>Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy uniwersalnej systemu Windows

W tym dokumencie opisano niektóre kluczowe punkty, o których należy pamiętać podczas korzystania z klasy zadań do tworzenia operacji asynchronicznych opartych na usłudze Windows ThreadPool w aplikacji uniwersalnego środowiska wykonawczego systemu Windows (UWP).

Użycie programowania asynchroniowego jest kluczowym składnikiem modelu aplikacji środowiska wykonawczego systemu Windows, ponieważ umożliwia aplikacjom pozostawać w odpowiedzi na dane wejściowe użytkownika. Można uruchomić długotrwałe zadanie bez blokowania wątku interfejsu użytkownika, a wyniki zadania można uzyskać później. Można również anulować zadania i otrzymywać powiadomienia o postępie, gdy zadania są uruchamiane w tle. Dokument [programowania asynchroniiowego w języku C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) zawiera omówienie wzorca asynchronii, który jest dostępny w języku Visual C++ do tworzenia aplikacji platformy uniwersalnej systemu Windows. Ten dokument uczy, jak zarówno zużywają, jak i tworzą łańcuchy asynchronicznych operacji środowiska wykonawczego systemu Windows. W tej sekcji opisano sposób używania typów w ppltasks.h do tworzenia operacji asynchronicznych, które mogą być używane przez inny składnik środowiska wykonawczego systemu Windows i jak kontrolować sposób wykonywania pracy asynchronicznie. Należy również rozważyć [przeczytanie wzorców programowania Async i wskazówek w Hilo (aplikacje ze Sklepu Windows przy użyciu języka C++ i XAML),](/previous-versions/windows/apps/jj160321(v=win.10)) aby dowiedzieć się, jak użyliśmy klasy zadań do zaimplementowania operacji asynchronicznych w Hilo, aplikacji środowiska wykonawczego systemu Windows przy użyciu języka C++ i XAML.

> [!NOTE]
> Biblioteka [wzorców równoległych](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) i [Biblioteka agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) można użyć w aplikacji platformy uniwersalnej systemu uniwersalnego. Nie można jednak używać Harmonogramu zadań ani Menedżera zasobów. W tym dokumencie opisano dodatkowe funkcje, które udostępnia PPL, które są dostępne tylko dla aplikacji platformy uniwersalnej systemu Windows, a nie dla aplikacji klasycznej.

## <a name="key-points"></a>Kwestie kluczowe

- Użyj [współbieżności::create_async](reference/concurrency-namespace-functions.md#create_async) do tworzenia operacji asynchronicznych, które mogą być używane przez inne składniki (które mogą być napisane w językach innych niż C++).

- Użyj [współbieżności::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) do raportowania powiadomień o postępie do składników, które wywołują operacje asynchroniczne.

- Użyj tokenów anulowania, aby włączyć wewnętrzne operacje asynchroniczne, aby anulować.

- Zachowanie `create_async` funkcji zależy od typu zwracanego funkcji pracy, która jest przekazywana do niego. Funkcja pracy, która zwraca zadanie `task<T>` `task<void>`(albo lub ) działa synchronicznie w kontekście, który o nazwie `create_async`. Funkcja pracy, `T` która `void` zwraca lub działa w dowolnym kontekście.

- Można użyć [współbieżności::task::then](reference/task-class.md#then) metody, aby utworzyć łańcuch zadań, które uruchamiają jeden po drugim. W aplikacji platformy uniwersalnej systemu i platformy uniwersalnej domyślnego kontekstu dla kontynuacji zadania zależy od sposobu skonstruowania tego zadania. Jeśli zadanie zostało utworzone przez przekazanie akcji asynchronicznego do konstruktora zadań lub przez przekazanie wyrażenia lambda, które zwraca akcję asynchronicznego, domyślnym kontekstem dla wszystkich kontynuacji tego zadania jest bieżący kontekst. Jeśli zadanie nie jest skonstruowane z akcji asynchronicznego, a następnie dowolny kontekst jest używany domyślnie dla kontynuacji zadania. Domyślny kontekst można zastąpić klasą [współbieżności::task_continuation_context.](../../parallel/concrt/reference/task-continuation-context-class.md)

## <a name="in-this-document"></a>W tym dokumencie

- [Tworzenie operacji asynchronicznych](#create-async)

- [Przykład: Tworzenie składnika środowiska wykonawczego systemu Windows w języku C++](#example-component)

- [Sterowanie wątkiem wykonania](#exethread)

- [Przykład: Kontrolowanie wykonywania w aplikacji środowiska wykonawczego systemu Windows za pomocą języka C++ i XAML](#example-app)

## <a name="creating-asynchronous-operations"></a><a name="create-async"></a>Tworzenie operacji asynchronicznych

Za pomocą modelu zadań i kontynuacji w bibliotece wzorców równoległych (PPL) można zdefiniować zadania w tle, a także dodatkowe zadania uruchamiane po zakończeniu poprzedniego zadania. Ta funkcja jest dostarczana przez [klasę współbieżności::task.](../../parallel/concrt/reference/task-class.md) Aby uzyskać więcej informacji `task` na temat tego modelu i klasy, zobacz [Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Środowisko wykonawcze systemu Windows to interfejs programowania, którego można używać do tworzenia aplikacji platformy uniwersalnej systemu Windows, które działają tylko w specjalnym środowisku systemu operacyjnego. Takie aplikacje używają autoryzowanych funkcji, typów danych i urządzeń i są dystrybuowane ze sklepu Microsoft Store. Środowisko wykonawcze systemu Windows jest reprezentowane przez *interfejs binarny aplikacji* (ABI). ABI jest podstawowym kontraktem binarnym, który udostępnia interfejsy API środowiska wykonawczego systemu Windows do języków programowania, takich jak Visual C++.

Korzystając ze środowiska wykonawczego systemu Windows, można użyć najlepszych funkcji różnych języków programowania i połączyć je w jedną aplikację. Na przykład można utworzyć interfejs użytkownika w języku JavaScript i wykonać logikę aplikacji intensywnie korzystających z obliczeń w składniku C++. Możliwość wykonywania tych operacji intensywnie korzystających z obliczeń w tle jest kluczowym czynnikiem w utrzymaniu reakcji interfejsu użytkownika. Ponieważ `task` klasa jest specyficzna dla języka C++, należy użyć interfejsu środowiska wykonawczego systemu Windows do komunikowania się z operacjami asynchronicznymi z innymi składnikami (które mogą być zapisywane w językach innych niż C++). Środowisko wykonawcze systemu Windows udostępnia cztery interfejsy, których można używać do reprezentowania operacji asynchronicznych:

[Windows::Fundacja::IAsyncAction](/uwp/api/windows.foundation.iasyncaction)<br/>
Reprezentuje akcję asynchronizacjową.

[Windows::Foundation::IAsyncActionWithProgress\<TProgress>](/uwp/api/windows.foundation.iasyncactionwithprogress-1)<br/>
Reprezentuje akcję asynchronizacjową, która raportuje postęp.

[Windows::Foundation::IAsyncOperation\<TResult>](/uwp/api/windows.foundation.iasyncoperation-1)<br/>
Reprezentuje operację asynchronizacyjną, która zwraca wynik.

[Windows::Foundation::IAsyncOperationWithProgress\<TResult, TProgress>](/uwp/api/windows.foundation.iasyncoperationwithprogress-2)<br/>
Reprezentuje operację asynchroniza, która zwraca wynik i raportuje postęp.

Pojęcie *akcji* oznacza, że zadanie asynchroniczne nie tworzy wartości (pomyśl o `void`funkcji, która zwraca ). Pojęcie *operacji* oznacza, że zadanie asynchroniczne daje wartość. Pojęcie *postępu* oznacza, że zadanie może zgłaszać komunikaty postępu do wywołującego. JavaScript, .NET Framework i Visual C++ każdy udostępnia swój własny sposób tworzenia wystąpień tych interfejsów do użycia w granicach ABI. Dla języka Visual C++, PPL zapewnia [współbieżność::create_async](reference/concurrency-namespace-functions.md#create_async) funkcji. Ta funkcja tworzy asynchronicznego czasu wykonywania systemu Windows akcji lub operacji, która reprezentuje ukończenie zadania. Funkcja `create_async` przyjmuje funkcję pracy (zazwyczaj wyrażenie lambda), wewnętrznie `task` tworzy obiekt i zawija to zadanie w jednym z czterech asynchronicznych interfejsów środowiska wykonawczego systemu Windows.

> [!NOTE]
> Należy `create_async` używać tylko wtedy, gdy trzeba utworzyć funkcje, które można uzyskać dostęp z innego języka lub innego składnika środowiska wykonawczego systemu Windows. Użyj `task` klasy bezpośrednio, gdy wiadomo, że operacja jest zarówno produkowane i używane przez kod C++ w tym samym składniku.

Typ zwracany `create_async` jest określany przez typ jego argumentów. Jeśli na przykład funkcja pracy nie zwraca wartości i nie `create_async` zgłasza `IAsyncAction`postępu, zwraca go. Jeśli funkcja pracy nie zwraca wartości, a `create_async` także `IAsyncActionWithProgress`raportuje postęp, zwraca . Aby zgłosić postęp, [podaj współbieżność::pprogresja_reporter](../../parallel/concrt/reference/progress-reporter-class.md) obiektu jako parametr do funkcji pracy. Możliwość raportowania postępu umożliwia raportowanie, jaka ilość pracy została wykonana i jaka kwota nadal pozostaje (na przykład jako procent). Umożliwia również raportowanie wyników, gdy tylko staną się dostępne.

, `IAsyncAction` `IAsyncActionWithProgress<TProgress>`, `IAsyncOperation<TResult>`i `IAsyncActionOperationWithProgress<TProgress, TProgress>` interfejsy każdy `Cancel` zapewniają metodę, która umożliwia anulowanie operacji asynchroniczne. Klasa `task` działa z tokenami anulowania. Gdy używasz tokenu anulowania, aby anulować pracę, środowisko wykonawcze nie uruchamia nowej pracy, która subskrybuje ten token. Praca, która jest już aktywna, może monitorować jego token anulowania i zatrzymać, gdy może. Mechanizm ten jest opisany bardziej szczegółowo w dokumencie [Anulowanie w PPL](cancellation-in-the-ppl.md). Anulowanie zadań można połączyć`Cancel` z metodami środowiska wykonawczego systemu Windows na dwa sposoby. Po pierwsze można zdefiniować funkcję pracy, do której przechodzisz, aby `create_async` wziąć [współbieżność::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) obiektu. Gdy `Cancel` metoda jest wywoływana, ten token anulowania jest anulowany `task` i normalne `create_async` reguły anulowania stosuje się do obiektu źródłowego, który obsługuje wywołanie. Jeśli obiekt nie `cancellation_token` zostanie podasz, obiekt bazowy `task` definiuje jeden niejawnie. Zdefiniuj `cancellation_token` obiekt, gdy trzeba wspólnie reagować na anulowanie w funkcji roboczej. Przykład [sekcji: Kontrolowanie wykonywania w aplikacji środowiska wykonawczego systemu Windows za pomocą języka C++ i XAML przedstawiono](#example-app) przykład sposobu przeprowadzania anulowania w aplikacji platformy uniwersalnej systemu Windows (UWP) w językach C# i XAML, która używa niestandardowego składnika C++ środowiska wykonawczego systemu Windows.

> [!WARNING]
> W łańcuchu kontynuacji zadań zawsze czyścić stan, a następnie [wywołać współbieżność::cancel_current_task,](reference/concurrency-namespace-functions.md#cancel_current_task) gdy token anulowania zostanie anulowany. Jeśli wrócisz wcześnie zamiast `cancel_current_task`wywoływania, operacja zostanie przesuń do stanu ukończonego zamiast stanu anulowane.

W poniższej tabeli podsumowano kombinacje, których można użyć do zdefiniowania operacji asynchronicznych w aplikacji.

|Aby utworzyć ten interfejs środowiska wykonawczego systemu Windows|Zwracaj ten typ z`create_async`|Przekaż te typy parametrów do funkcji pracy, aby użyć niejawnego tokenu anulowania|Przekaż te typy parametrów do funkcji roboczej, aby użyć jawnego tokenu anulowania|
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|`IAsyncAction`|`void` lub `task<void>`|(brak)|(`cancellation_token`)|
|`IAsyncActionWithProgress<TProgress>`|`void` lub `task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|
|`IAsyncOperation<TResult>`|`T` lub `task<T>`|(brak)|(`cancellation_token`)|
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T` lub `task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|

Można zwrócić wartość lub `task` obiekt z funkcji pracy, `create_async` która jest przekazywalna do funkcji. Te odmiany wytwarzają różne zachowania. Po zwróceniu wartości funkcja pracy jest `task` zawijana w tak, aby można było uruchomić na wątku w tle. Ponadto podstawowej `task` używa tokenu anulowania niejawne. Z drugiej strony, `task` jeśli zwrócisz obiekt, funkcja pracy działa synchronicznie. W związku z tym `task` jeśli zwrócisz obiekt, upewnij się, że wszystkie długie operacje w funkcji pracy również działać jako zadania, aby umożliwić aplikacji pozostają elastyczne. Ponadto podstawowej `task` nie używa tokenu anulowania niejawne. W związku z tym należy zdefiniować `cancellation_token` funkcję pracy, aby wziąć obiekt, `task` jeśli `create_async`wymagana jest obsługa anulowania podczas zwracania obiektu z .

W poniższym przykładzie przedstawiono `IAsyncAction` różne sposoby tworzenia obiektu, który może być zużywany przez inny składnik środowiska wykonawczego systemu Windows.

[!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]

## <a name="example-creating-a-c-windows-runtime-component-and-consuming-it-from-c"></a><a name="example-component"></a>Przykład: Tworzenie składnika środowiska wykonawczego systemu Windows w języku C++ i korzystanie z niego z języka C\#

Należy wziąć pod uwagę aplikację, która używa XAML i C# do definiowania interfejsu użytkownika i składnika środowiska wykonawczego systemu Windows W++ do wykonywania operacji intensywnie korzystających z obliczeń. W tym przykładzie składnik C++ oblicza, które liczby w danym zakresie są prime. Aby zilustrować różnice między czterema asynchroniczną interfejsami zadań środowiska wykonawczego systemu Windows, uruchom w `Primes`programie Visual Studio, tworząc puste **rozwiązanie** i nazywając go . Następnie dodaj do rozwiązania projekt **składnika środowiska** `PrimesLibrary`wykonawczego systemu Windows i nadawanie go . Dodaj następujący kod do wygenerowanego pliku nagłówka Języka C++ (w tym przykładzie zmienia nazwę class1.h na Primes.h). Każda `public` metoda definiuje jeden z czterech interfejsów asynchronicznych. Metody zwracające wartość zwracają [windows::Foundation::Collections::IVector\<int>](/uwp/api/windows.foundation.collections.ivector-1) obiektu. Metody, które raportują postęp, generują `double` wartości definiujące procent ogólnej pracy, która została ukończona.

[!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]

> [!NOTE]
> Zgodnie z konwencją nazwy metod asynchronicznych w czasie wykonywania systemu Windows zazwyczaj kończą się na "Async".

Dodaj następujący kod do wygenerowanego pliku źródłowego języka C++ (w tym przykładzie zmienia nazwę class1.cpp na Primes.cpp). Funkcja `is_prime` określa, czy jego dane wejściowe są doskonałe. Pozostałe metody implementują `Primes` klasę. Każde wywołanie `create_async` używa podpisu, który jest zgodny z metodą, z której jest wywoływana. Na przykład `Primes::ComputePrimesAsync` ponieważ `IAsyncAction`zwraca , funkcja pracy, `create_async` która jest dostarczana do nie `progress_reporter` zwraca wartość i nie przyjmuje obiektu jako parametru.

[!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]

Każda metoda najpierw wykonuje sprawdzanie poprawności, aby upewnić się, że parametry wejściowe są nieujemne. Jeśli wartość wejściowa jest ujemna, metoda zgłasza [Platform::InvalidArgumentException](../../cppcx/platform-invalidargumentexception-class.md). Obsługa błędów jest wyjaśniona w dalszej części tej sekcji.

Aby korzystać z tych metod z aplikacji platformy uniwersalnej systemu Wizjerskiego, użyj szablonu pustej aplikacji języka Visual **C#(XAML),** aby dodać drugi projekt do rozwiązania programu Visual Studio. W tym przykładzie nazwa projektu `Primes`. Następnie z `Primes` projektu dodaj odwołanie do `PrimesLibrary` projektu.

Dodaj następujący kod do pliku MainPage.xaml. Ten kod definiuje interfejsu użytkownika, dzięki czemu można wywołać składnik C++ i wyświetlić wyniki.

[!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]

Dodaj następujący kod `MainPage` do klasy w mainpage.xaml. Ten kod definiuje `Primes` obiekt i programy obsługi zdarzeń przycisku.

[!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]

Metody te `async` używają `await` i słowa kluczowe, aby zaktualizować interfejsu użytkownika po zakończeniu operacji asynchronicznych. Aby uzyskać informacje na temat kodowania asynchroniowego w aplikacjach platformy uniwersalnej systemu Windows, zobacz [Tworzenie wątków i programowanie asynchroniczne](/windows/uwp/threading-async).

Metody `getPrimesCancellation` `cancelGetPrimes` i metody współpracują ze sobą, aby umożliwić użytkownikowi anulowanie operacji. Gdy użytkownik wybierze **przycisk Anuluj,** `cancelGetPrimes` metoda wywołuje [IAsyncOperationWithProgress\<TResult, TProgress>::Anuluj,](/uwp/api/windows.foundation.iasyncinfo.cancel) aby anulować operację. Środowisko uruchomieniowe współbieżności, który zarządza podstawową operacją asynchroniką, zgłasza wewnętrzny typ wyjątku, który jest przechwytyny przez środowisko wykonawcze systemu Windows w celu poinformowania, że anulowanie zostało zakończone. Aby uzyskać więcej informacji na temat modelu anulowania, zobacz [Anulowanie](../../parallel/concrt/cancellation-in-the-ppl.md).

> [!IMPORTANT]
> Aby włączyć PPL poprawnie zgłosić do środowiska wykonawczego systemu Windows, że anulował operację, nie należy przechwytywać tego typu wyjątku wewnętrznego. Oznacza to, że nie należy również`catch (...)`łapać wszystkich wyjątków ( ). Jeśli musisz złapać wszystkie wyjątki, ponownie uruchomić wyjątek, aby upewnić się, że środowisko wykonawcze systemu Windows można ukończyć operację anulowania.

Na poniższej `Primes` ilustracji przedstawiono aplikację po wybraniu każdej opcji.

![Aplikacja Primes środowiska wykonawczego systemu Windows](../../parallel/concrt/media/concrt_windows_primes.png "Aplikacja Primes środowiska wykonawczego systemu Windows")

Aby zapoznać `create_async` się z przykładami, które są używane do tworzenia zadań asynchronicznych, które mogą być używane przez inne języki, zobacz [Używanie języka C++ w przykładzie Optymalizatora podróży map Bing](/previous-versions/windows/apps/hh699891(v=vs.140)) i [operacje asynchroniczne systemu Windows 8 w języku C++ z ppl](https://code.msdn.microsoft.com/windowsapps/windows-8-asynchronous-08009a0d).

## <a name="controlling-the-execution-thread"></a><a name="exethread"></a>Sterowanie wątkiem wykonania

Środowisko wykonawcze systemu Windows używa modelu wątków COM. W tym modelu obiekty są hostowane w różnych mieszkaniach, w zależności od tego, jak obsługują ich synchronizacji. Obiekty bezpieczne dla wątków są hostowane w mieszkaniu wielowątkowym (MTA). Obiekty, do których musi uzyskiwać dostęp pojedynczy wątek, są hostowane w mieszkaniu jednowątkowym (STA).

W aplikacji, która ma interfejs użytkownika, Wątek ASTA (Application STA) jest odpowiedzialny za pompowanie komunikatów okna i jest jedynym wątkiem w procesie, który można zaktualizować sta-hosted formantów interfejsu użytkownika. Ma to dwie konsekwencje. Po pierwsze, aby umożliwić aplikacji pozostają elastyczne, wszystkie operacje intensywnie korzystających z procesora CPU i we/wy nie powinny być uruchamiane w wątku ASTA. Po drugie wyniki, które pochodzą z wątków w tle musi być kierowane z powrotem do ASTA, aby zaktualizować interfejsu użytkownika. W aplikacji platformy uniwersalnej `MainPage` systemu IP języka C++ i innych stronach XAML wszystkie są uruchamiane w atsa. W związku z tym kontynuacje zadań, które są zadeklarowane w ASTA są uruchamiane tam domyślnie, dzięki czemu można zaktualizować formanty bezpośrednio w treści kontynuacji. Jeśli jednak zagnieżdżasz zadanie w innym zadaniu, wszystkie kontynuacje tego zagnieżdżonego zadania są uruchamiane w mta. W związku z tym należy rozważyć, czy jawnie określić w jakim kontekście te kontynuacje są uruchamiane.

Zadanie utworzone na podstawie operacji asynchronicznego, `IAsyncOperation<TResult>`takie jak , używa specjalnej semantyki, która może pomóc w zignorowaniu szczegółów wątkowości. Chociaż operacja może działać w wątku w tle (lub może nie być w ogóle poparta wątkiem), jej kontynuacje są domyślnie gwarantowane do uruchomienia w mieszkaniu, które rozpoczęło operacje kontynuacji (innymi słowy, z mieszkania, które się wywoływał). `task::then` Można użyć [współbieżności::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) klasy do kontrolowania kontekstu wykonywania kontynuacji. Użyj tych statycznych metod `task_continuation_context` pomocnika do tworzenia obiektów:

- Użyj [współbieżności::task_continuation_context::use_arbitrary,](reference/task-continuation-context-class.md#use_arbitrary) aby określić, że kontynuacja jest uruchamiana w wątku w tle.

- Użyj [współbieżności::task_continuation_context::use_current,](reference/task-continuation-context-class.md#use_current) aby określić, że kontynuacja jest uruchamiana w wątku o nazwie `task::then`.

Można przekazać `task_continuation_context` obiekt do [task::then](reference/task-class.md#then) metody jawnie kontrolować kontekst wykonywania kontynuacji lub można przekazać zadanie `task::then` do innego mieszkania, a następnie wywołać metodę niejawnie kontrolować kontekst wykonywania.

> [!IMPORTANT]
> Ponieważ główny wątek interfejsu użytkownika aplikacji platformy uniwersalnej systemu Windows działają w ramach STA, kontynuacje, które można utworzyć na tym STA domyślnie uruchomić na STA. W związku z tym kontynuacje, które można utworzyć w mta uruchomić na MTA.

W poniższej sekcji przedstawiono aplikację, która odczytuje plik z dysku, znajduje najczęściej używane słowa w tym pliku, a następnie pokazuje wyniki w interfejsie użytkownika. Ostateczna operacja, aktualizowanie interfejsu użytkownika, występuje w wątku interfejsu użytkownika.

> [!IMPORTANT]
> To zachowanie jest specyficzne dla aplikacji platformy uniwersalnej systemu Windows. W przypadku aplikacji klasycznych nie należy kontrolować, gdzie są uruchamiane kontynuacje. Zamiast tego harmonogram wybiera wątku procesu roboczego, na którym należy uruchomić każdą kontynuację.

> [!IMPORTANT]
> Nie należy wywoływać [współbieżności::task::wait](reference/task-class.md#wait) w treści kontynuacji, która działa na STA. W przeciwnym razie środowisko uruchomieniowe zgłasza [współbieżność::invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) ponieważ ta metoda blokuje bieżący wątek i może spowodować, że aplikacja przestanie odpowiadać. Można jednak wywołać [metodę współbieżności::task::get,](reference/task-class.md#get) aby otrzymać wynik zadania poprzedzanego w kontynuacji opartej na zadaniu.

## <a name="example-controlling-execution-in-a-windows-runtime-app-with-c-and-xaml"></a><a name="example-app"></a>Przykład: Kontrolowanie wykonywania w aplikacji środowiska wykonawczego systemu Windows za pomocą języka C++ i XAML

Należy wziąć pod uwagę C++ XAML aplikacji, która odczytuje plik z dysku, znajduje najczęściej używane słowa w tym pliku, a następnie pokazuje wyniki w interfejsie użytkownika. Aby utworzyć tę aplikację, uruchom w programie Visual Studio, tworząc projekt **pustej aplikacji (Universal Windows)** i nazywając go `CommonWords`. W manifeście aplikacji określ funkcję **Biblioteki dokumentów,** aby umożliwić aplikacji dostęp do folderu Dokumenty. Dodaj również tekst (txt) typ pliku do sekcji deklaracje manifestu aplikacji. Aby uzyskać więcej informacji na temat możliwości i deklaracji aplikacji, zobacz [Pakowanie, wdrażanie i kwerendy aplikacji systemu Windows](/windows/win32/appxpkg/appx-portal).

Zaktualizuj `Grid` element w pliku MainPage.xaml, `ProgressRing` aby uwzględnić element i `TextBlock` element. Wskazuje, `ProgressRing` że operacja jest w `TextBlock` toku i pokazuje wyniki obliczeń.

[!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]

Dodaj następujące `#include` instrukcje do *pch.h*.

[!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]

Dodaj następujące deklaracje metody `MainPage` do klasy (MainPage.h).

[!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]

Dodaj następujące `using` instrukcje do mainpage.cpp.

[!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]

W mainpage.cpp zaimplementuj `MainPage::MakeWordList`, `MainPage::FindCommonWords`i `MainPage::ShowResults` metody. I `MainPage::MakeWordList` `MainPage::FindCommonWords` wykonać operacje intensywnie korzystających z obliczeń. Metoda `MainPage::ShowResults` wyświetla wynik obliczeń w interfejsie użytkownika.

[!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]

Zmodyfikuj `MainPage` konstruktora, aby utworzyć łańcuch zadań kontynuacji, który wyświetla w interfejsie użytkownika wspólne słowa w książce *Iliad* przez Homera. Pierwsze dwa zadania kontynuacji, które dzielą tekst na poszczególne słowa i znajdują wspólne słowa, mogą być czasochłonne i dlatego są jawnie ustawione na uruchamianie w tle. Zadanie kontynuacji końcowego, który aktualizuje interfejsu użytkownika, określa nie kontekst kontynuacji i dlatego jest zgodne z regułami wątkowości mieszkania.

[!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]

> [!NOTE]
> W tym przykładzie pokazano, jak określić konteksty wykonywania i jak skomponować łańcuch kontynuacji. Przypomnijmy, że domyślnie zadanie utworzone na podstawie operacji asynchronicznego uruchamia `task::then`jego kontynuacje w mieszkaniu, które wywoływane jest . W związku z tym `task_continuation_context::use_arbitrary` w tym przykładzie używa do określenia, że operacje, które nie obejmują interfejsu użytkownika, mogą być wykonywane w wątku w tle.

Na poniższej ilustracji `CommonWords` przedstawiono wyniki aplikacji.

![Aplikacja CommonWords dla środowiska wykonawczego systemu Windows](../../parallel/concrt/media/concrt_windows_common_words.png "Aplikacja CommonWords dla środowiska wykonawczego systemu Windows")

W tym przykładzie jest możliwe do `task` obsługi anulowania, ponieważ obiekty, które obsługują `create_async` używać tokenu anulowania niejawne. Zdefiniuj funkcję `cancellation_token` pracy, aby wziąć obiekt, jeśli zadania muszą odpowiadać na anulowanie w sposób kooperacyjny. Aby uzyskać więcej informacji na temat anulowania w PPL, zobacz [Anulowanie w PPL](cancellation-in-the-ppl.md)

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)
