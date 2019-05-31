---
title: Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy uniwersalnej systemu Windows
ms.date: 11/19/2018
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
ms.openlocfilehash: 92226d8db9fa87ce829ae96b4802ad2f45bc3e54
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450187"
---
# <a name="creating-asynchronous-operations-in-c-for-uwp-apps"></a>Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy uniwersalnej systemu Windows

W tym dokumencie opisano niektóre kluczowe punkty, których należy pamiętać, gdy używasz klasy zadania do wygenerowania na podstawie puli wątków Windows operacje asynchroniczne w aplikacji Windows Runtime Uniwersalnej.

Korzystanie z programowania asynchronicznego jest kluczowym elementem w modelu aplikacji środowiska wykonawczego Windows, ponieważ umożliwia aplikacjom ciągle reagować na dane wejściowe użytkownika. Długotrwałe zadania mogą być uruchamiane bez blokowania wątku interfejsu użytkownika, a otrzymasz wyników zadania w dalszej części. Możesz również anulować zadania i otrzymywać powiadomienia o postępie jako zadania uruchomione w tle. Dokument [asynchronicznego programowania w języku C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) zawiera omówienie wzorca asynchronicznego, które są dostępne w programie Visual C++ do tworzenia aplikacji platformy uniwersalnej systemu Windows. Ten dokument omawia jak używanie i tworzenie łańcuchów operacji asynchronicznych środowiska wykonawczego Windows. W tej sekcji opisano sposób użycia typy w ppltasks.h w celu wygenerowania operacji asynchronicznych, które mogą być wykorzystane przez inny składnik środowiska wykonawczego Windows i sposobie kontrolowania sposobu asynchroniczne jest wykonywany. Należy również rozważyć odczytu [programowanie Async wzorców i porady w Hilo (aplikacje Windows Store przy użyciu języków C++ i XAML)](https://msdn.microsoft.com/library/windows/apps/jj160321.aspx) Aby dowiedzieć się, jak użyliśmy klasy zadania do implementowania asynchronicznych operacji w Hilo, aplikacji środowiska wykonawczego Windows, korzystając z C++ i XAML.

> [!NOTE]
>  Możesz użyć [biblioteki wzorców równoległych](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) i [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md) w aplikacji platformy uniwersalnej systemu Windows. Jednak nie możesz użyć harmonogramu zadań ani Menedżera zasobów. W tym dokumencie opisano dodatkowe funkcje, które zapewnia PPL, które są dostępne tylko dla aplikacji platformy uniwersalnej systemu Windows, a nie do aplikacji klasycznej.

## <a name="key-points"></a>Kwestie kluczowe

- Użyj [concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) do utworzenia operacji asynchronicznych, które mogą być używane przez inne składniki (które mogą być napisane w językach innych niż C++).

- Użyj [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) raport postępu powiadomień do składników, które wywołują operacje asynchroniczne.

- Używają tokenów anulowania, aby włączyć wewnętrznej operacji asynchronicznych anulować.

- Zachowanie `create_async` funkcji jest zależny od zwracany typ funkcji pracy, który jest przekazywany do niego. Funkcja pracy, który zwraca klasę task (albo `task<T>` lub `task<void>`) jest uruchamiana synchronicznie w kontekście, który wywołuje `create_async`. Funkcja pracy, która zwraca `T` lub `void` jest uruchamiany w kontekście dowolnego.

- Możesz użyć [CONCURRENCY::Task:: Then](reference/task-class.md#then) metodę, aby utworzyć łańcuch zadań uruchamianych po kolei. W przypadku aplikacji platformy uniwersalnej systemu Windows domyślny kontekst kontynuacji zadań zależy od tego, jak skonstruowano tego zadania. Jeśli zadanie zostało utworzone przez przekazanie akcji asynchronicznych do konstruktora zadania lub przez przekazanie Wyrażenie lambda, która zwraca akcji asynchronicznych, domyślny kontekst dla wszystkich kontynuacji zadania jest bieżący kontekst. Jeśli zadanie nie jest zbudowany z akcji asynchronicznych, dowolnego kontekstu jest używana w domyślne dla kontynuacji zadania podrzędnego. Można zastąpić domyślny kontekst z [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) klasy.

## <a name="in-this-document"></a>W tym dokumencie

- [Tworzenie operacji asynchronicznych](#create-async)

- [Przykład: Tworzenie składnika środowiska wykonawczego Windows C++](#example-component)

- [Kontrolowanie wątku wykonania](#exethread)

- [Przykład: Sterowanie wykonywaniem w aplikacji Windows Runtime z C++ i XAML](#example-app)

##  <a name="create-async"></a> Tworzenie operacji asynchronicznych

Można użyć modelu zadania i kontynuacji w równoległych Biblioteka wzorców (PPL) do definiowania zadań w tle, a także dodatkowe zadania, które są uruchamiane po zakończeniu poprzedniego zadania. Ta funkcjonalność jest dostarczana przez [concurrency::task](../../parallel/concrt/reference/task-class.md) klasy. Aby uzyskać więcej informacji na temat tego modelu i `task` klasy, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Środowisko wykonawcze Windows jest interfejsem programowania, który służy do tworzenia aplikacji platformy uniwersalnej systemu Windows, które są uruchamiane tylko w środowisku specjalnych systemu operacyjnego. Takie aplikacje używać funkcji autoryzowanych, typów danych i urządzeń i są dystrybuowane za pomocą usługi Microsoft Store. Środowisko wykonawcze Windows jest reprezentowany przez *interfejsem binarnym aplikacji* (ABI). ABI jest podstawowego kontraktu binarny, który udostępnia interfejsów API środowiska wykonawczego Windows w językach programowania, takich jak Visual C++.

Za pomocą środowiska wykonawczego Windows, możesz korzystać z najlepszych funkcji różnych języków programowania i połączyć je w jednej aplikacji. Na przykład możesz utworzyć interfejs użytkownika w języku JavaScript i wykonania logiki praktyce intensywnie korzystających z aplikacji w składniku C++. Możliwość wykonywania tych praktyce intensywnie korzystających z operacji w tle jest kluczowym czynnikiem w ochronie elastyczny interfejs użytkownika. Ponieważ `task` klasy jest specyficzny dla języka C++, należy użyć interfejsu środowiska wykonawczego Windows do komunikowania się operacji asynchronicznych do innych składników, (które mogą być napisane w językach innych niż C++). Środowisko wykonawcze Windows zawiera cztery interfejsy, które służy do reprezentowania operacji asynchronicznych:

[Windows::Foundation::IAsyncAction](/uwp/api/windows.foundation.iasyncaction)<br/>
Reprezentuje akcję asynchroniczną.

[Windows::Foundation::IAsyncActionWithProgress\<TProgress>](https://msdn.microsoft.com/library/windows/apps/br206581.aspx)<br/>
Reprezentuje akcję asynchroniczną, która zgłasza postępy pracy.

[Windows::Foundation::IAsyncOperation\<TResult>](https://msdn.microsoft.com/library/windows/apps/br206598.aspx)<br/>
Reprezentuje operację asynchroniczną, która zwraca wynik.

[Windows::Foundation::IAsyncOperationWithProgress\<TResult, TProgress>](https://msdn.microsoft.com/library/windows/apps/br206594.aspx)<br/>
Reprezentuje operację asynchroniczną, która zwraca wynik i raporty postęp.

Pojęcie *akcji* oznacza, że zadanie asynchroniczne nie tworzy wartości (reakcji funkcji, która zwraca `void`). Pojęcie *operacji* oznacza, że zadanie asynchroniczne uzyskiwania wartości. Pojęcie *postępu* oznacza, że zadanie może zgłaszać komunikaty o postępie do obiektu wywołującego. JavaScript, .NET Framework i Visual C++ każdy zawiera swój własny sposób tworzenia wystąpień tych interfejsów do użytku przez granicę interfejsu ABI. Dla elementu wizualnego C++, zapewnia PPL [concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) funkcji. Ta funkcja tworzy akcję asynchroniczną środowiska wykonawczego Windows lub operacji, które reprezentuje ukończenie zadania. `create_async` Funkcja przyjmuje funkcja pracy (zwykle Wyrażenie lambda), tworzy wewnętrznie `task` obiektu i zawija, które zadanie w jednej z czterech asynchronicznych interfejsów Windows Runtime.

> [!NOTE]
>  Użyj `create_async` tylko kiedy należy utworzyć funkcje, które są dostępne z innego języka lub inny składnik środowiska wykonawczego Windows. Użyj `task` klasy bezpośrednio po wiadomo, operacja jest zarówno utworzone i używane przez kod języka C++ w jednym składniku.

Zwracany typ `create_async` jest określana przez typ z jej argumentów. Załóżmy, że funkcja pracy nie może zwracać wartości i nie raportowania postępu `create_async` zwraca `IAsyncAction`. Jeśli nie zwraca wartości funkcji pracy, a także raporty postępu, `create_async` zwraca `IAsyncActionWithProgress`. Aby raport postęp, podaj [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) obiekt jako parametr do funkcji pracy. Możliwość raportowania postępu umożliwia raportu ilość pracy, które zostało wykonane i jakie ilość nadal pozostaje (na przykład w procentach). Można również do raportowania wyników w miarę ich udostępniania.

`IAsyncAction`, `IAsyncActionWithProgress<TProgress>`, `IAsyncOperation<TResult>`, I `IAsyncActionOperationWithProgress<TProgress, TProgress>` interfejsy każdego `Cancel` metodę, która pozwala anulować operację asynchroniczną. `task` Klasy współpracuje z tokenów anulowania. Gdy używasz token anulowania do anulowania pracy, środowisko wykonawcze nie można uruchomić nowych prac, które subskrybuje ten token. Pracy, która jest już aktywna, można monitorować jej token anulowania i Zatrzymaj, gdy jest to możliwe. Ten mechanizm jest opisany bardziej szczegółowo w dokumencie [anulowanie w PPL](cancellation-in-the-ppl.md). Anulowanie zadania można połączyć ze środowiskiem uruchomieniowym Windows`Cancel` metod na dwa sposoby. Po pierwsze, można zdefiniować ta funkcja pracy, który jest przekazywany do `create_async` podjęcie [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) obiektu. Gdy `Cancel` metoda jest wywoływana, ten token anulowania, zostanie anulowane i reguły normalne anulowania mają zastosowanie do bazowego `task` obiekt, który obsługuje `create_async` wywołania. Jeśli nie podasz `cancellation_token` obiektu bazowego `task` obiektu definiuje jedną niejawnie. Zdefiniuj `cancellation_token` obiektu, kiedy należy odpowiedzieć wspólne anulowanie w funkcji pracy. Sekcja [przykładu: Sterowanie wykonywaniem w aplikacji Windows Runtime z C++ i XAML](#example-app) przedstawia przykład sposobu wykonywania anulowania w aplikacji platformy uniwersalnej Windows (UWP), za pomocą C# i XAML, który używa niestandardowego składnika środowiska wykonawczego Windows w języku C++.

> [!WARNING]
>  W łańcuchu kontynuacji zadań, zawsze wyczyścić stanu, a następnie wywołać [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) kiedy anulowany jest token anulowania. Jeśli wcześniej zwrócisz zamiast wywołać `cancel_current_task`, operacja, przechodzi do stanu ukończenia, zamiast stanem anulowane.

W poniższej tabeli przedstawiono kombinacje, które służy do definiowania operacji asynchronicznych w swojej aplikacji.

|Aby utworzyć ten interfejs Windows Runtime|Wróć do tego typu przy użyciu `create_async`|Przekaż te typy parametrów do funkcji pracy do użycia tokenu anulowania niejawne|Przekaż te typy parametrów do funkcji pracy do użycia tokenu anulowania jawne|
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|`IAsyncAction`|`void` lub `task<void>`|(Brak)|(`cancellation_token`)|
|`IAsyncActionWithProgress<TProgress>`|`void` lub `task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|
|`IAsyncOperation<TResult>`|`T` lub `task<T>`|(Brak)|(`cancellation_token`)|
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T` lub `task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|

Może zwracać wartość lub `task` obiektu przez funkcję pracy, który jest przekazywany do `create_async` funkcji. Takie zmiany mogą powodować różne zachowania. Po powrocie wartość ta funkcja pracy jest opakowana w `task` , dzięki czemu mogą być uruchamiane w wątku tła. Oprócz podstawowych `task` używa tokenu anulowanie niejawne. Z drugiej strony Jeśli wrócisz `task` obiektu, ta funkcja pracy jest uruchamiana synchronicznie. W związku z tym jeśli wrócisz `task` obiektów, upewnij się, że żadnych długotrwałej operacji w funkcji roboczych również uruchomić jako zadania, aby umożliwić zarządzanie aplikacją na czas reakcji. Oprócz podstawowych `task` nie korzysta z tokenu anulowanie niejawne. W związku z tym, należy zdefiniować funkcję pracy do wykonania `cancellation_token` obiektu, jeśli potrzebujesz pomocy technicznej dotyczącej anulowania, po powrocie `task` obiektu z `create_async`.

Poniższy przykład ilustruje różne sposoby tworzenia `IAsyncAction` obiekt, który może być używany przez inny składnik środowiska wykonawczego Windows.

[!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]

##  <a name="example-component"></a> Przykład: Tworzenie składnika wykonawczego Windows C++ i korzystanie zC#

Należy wziąć pod uwagę aplikację, która używa XAML i C#, aby zdefiniować interfejs użytkownika i składnika środowiska uruchomieniowego C++ Windows do wykonywania operacji obliczeniowych. W tym przykładzie składnika C++ oblicza, które numery w danym zakresie są Północnej. Aby zilustrować różnice między cztery interfejsów zadania asynchronicznego środowiska wykonawczego Windows, uruchamianie, w programie Visual Studio, tworząc **puste rozwiązanie** i nadawania mu nazwy `Primes`. Następnie dodaj do rozwiązania **składnika środowiska wykonawczego Windows** projektu i nadawania mu nazwy `PrimesLibrary`. Dodaj następujący kod do wygenerowanego pliku nagłówka C++ (w tym przykładzie zmienia nazwę Class1.h na Primes.h). Każdy `public` Metoda określa jeden z czterech asynchronicznych interfejsów. Metody, które zwracają wartość zwracają [Windows::Foundation::Collections::IVector\<int >](/uwp/api/Windows.Foundation.Collections.IVector_T_) obiektu. Metody, które raportowania postępu tworzenia `double` wartości, które definiują procent ogólnej pracy, która została zakończona.

[!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]

> [!NOTE]
>  Według Konwencji nazwy metod asynchronicznych środowiska wykonawczego Windows zazwyczaj kończy się "Async".

Dodaj następujący kod do wygenerowanego pliku źródłowego języka C++ (w tym przykładzie zmienia nazwę Class1.cpp na Primes.cpp). `is_prime` Funkcji określa, czy dane wejściowe jest pierwsze. Implementowanie pozostałych metod `Primes` klasy. Każde wywołanie `create_async` używa podpisu, który jest zgodny z metodą, z którego jest wywoływana. Na przykład ponieważ `Primes::ComputePrimesAsync` zwraca `IAsyncAction`, ta funkcja pracy, który został dostarczony do `create_async` nie może zwracać wartości i nie przyjmuje `progress_reporter` obiekt jako parametr.

[!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]

Każda metoda najpierw jest przeprowadzane sprawdzanie poprawności, aby upewnić się, że parametry wejściowe nieujemnej wartości. Jeśli wartość wejściowa jest ujemna, metoda zgłasza [Platform::InvalidArgumentException](https://msdn.microsoft.com/library/windows/apps/hh755794.aspx). Obsługa błędów została wyjaśniona później w tej sekcji.

Korzystanie z tych metod z aplikacji platformy uniwersalnej systemu Windows, należy użyć programu Visual C# **pusta aplikacja (XAML)** szablon, aby dodać drugi projekt do rozwiązania Visual Studio. W tym przykładzie nazwy projektu `Primes`. Następnie w `Primes` projektu, Dodaj odwołanie do `PrimesLibrary` projektu.

Dodaj następujący kod do pliku MainPage.xaml. Ten kod definiuje interfejs użytkownika, dzięki czemu mogą wywołać składników języka C++ i wyświetlić wyniki.

[!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]

Dodaj następujący kod do `MainPage` klasy w pliku MainPage.xaml. Ten kod definiuje `Primes` obiektu i procedury obsługi zdarzeń przycisku.

[!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]

Metody te za pomocą `async` i `await` słów kluczowych, aby zaktualizować interfejs użytkownika, po ukończeniu operacji asynchronicznych. Aby uzyskać informacji na temat programowania asynchronicznego w aplikacjach platformy uniwersalnej systemu Windows, zobacz [wątki i programowanie async](/windows/uwp/threading-async).

`getPrimesCancellation` i `cancelGetPrimes` metody działają razem, aby umożliwić użytkownikowi anulować operację. Kiedy użytkownik naciśnie **anulować** przycisku `cancelGetPrimes` wywołania metody [IAsyncOperationWithProgress\<TResult, TProgress >:: Anuluj](/uwp/api/windows.foundation.iasyncinfo.cancel) anulować operację. Współbieżność środowiska wykonawczego, która zarządza podstawowych operacji asynchronicznej, zgłasza typu wyjątek wewnętrzny, który zostanie przechwycony przez środowisko wykonawcze Windows do komunikowania się, że Zakończono operację anulowania. Aby uzyskać więcej informacji dotyczących anulowania, zobacz [anulowania](../../parallel/concrt/cancellation-in-the-ppl.md).

> [!IMPORTANT]
>  Aby włączyć PPL poprawnie zgłosić do środowiska wykonawczego Windows czy anulował operację, nie Przechwytuj ten typ wyjątku wewnętrznego. Oznacza to, czy też nie należy przechwytywać wszystkie wyjątki (`catch (...)`). Jeśli należy przechwytywać wszystkie wyjątki, zgłoś ponownie wyjątek, aby upewnić się, że środowisko wykonawcze Windows może ukończyć operację anulowania.

Poniższa ilustracja przedstawia `Primes` aplikacji po każdej opcji została wybrana.

![Środowisko uruchomieniowe Windows zapór aplikacji](../../parallel/concrt/media/concrt_windows_primes.png "Windows Runtime blokad aplikacji")

Przykłady, które używają `create_async` do tworzenia zadań asynchronicznych, które mogą być wykorzystane przez innych języków, zobacz [przy użyciu języka C++ w przykładzie optymalizatora podróży w mapach Bing](https://msdn.microsoft.com/library/windows/apps/hh699891.aspx) i [systemu Windows 8 operacji asynchronicznych w języku C++ z PPL](https://code.msdn.microsoft.com/windowsapps/windows-8-asynchronous-08009a0d).

##  <a name="exethread"></a> Kontrolowanie wątku wykonania

Środowisko wykonawcze Windows używa model wątkowości COM. W tym modelu obiektów znajdują się w różnych apartamentach, w zależności od sposobu obsługi ich synchronizacji. Obiekty wątków znajdują się w trybie komórek wielowątkowych (MTA). Obiekty, które muszą być dostępne przez pojedynczy wątek znajdują się w jednowątkowym (przedziale STA).

W aplikacji, która ma interfejs użytkownika wątku ASTA (aplikacja STA) jest odpowiedzialny za przekazywanie komunikatów okien i tylko wątek w procesie, który może aktualizować hostowanych STA kontrolek interfejsu użytkownika. To ma dwa skutki. Po pierwsze umożliwia korzystanie z aplikacji nadal odpowiadać, wszystkie mocy procesora CPU i operacje We/Wy nie można uruchamiać w wątku ASTA. Po drugie wyniki, które pochodzą z wątków w tle musi być organizowany do ASTA, aby zaktualizować interfejs użytkownika. W aplikacji platformy uniwersalnej systemu Windows w języku C++ `MainPage` i innych stron XAML wszystkich systemem ATSA. W związku z tym kontynuacji zadań, które są zadeklarowane na ASTA są uruchamiane istnieje domyślnie, dzięki czemu można zaktualizować kontrolki bezpośrednio w treści kontynuacji. Jednak należy zagnieździć zadania w innym zadaniem, wszelkie kontynuacje dla tego zadania zagnieżdżonego będzie uruchamiać w MTA. W związku z tym należy wziąć pod uwagę, czy należy jawnie określić, jakie kontekstu uruchamiania tych kontynuacji.

Zadanie, które jest tworzony z operacją asynchroniczną, takich jak `IAsyncOperation<TResult>`, używa semantyki specjalne, które mogą pomóc Ci zignorować wątkowości szczegóły. Mimo że operacji mogą być uruchamiane w wątku w tle (lub jej może nie być wspierany przez wątek na wszystkich), jego kontynuacje są domyślną gwarantowane na mieszkania, który uruchomił operacji kontynuacji (innymi słowy, z typu apartment, która wywołała `task::then`). Możesz użyć [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) klasy do kontrolowania Kontekst wykonywania kontynuacji. Umożliwia utworzenie tych metod statycznych Pomocnika `task_continuation_context` obiektów:

- Użyj [concurrency::task_continuation_context::use_arbitrary](reference/task-continuation-context-class.md#use_arbitrary) do określenia, że kontynuacja zostanie uruchomiona w wątku tła.

- Użyj [concurrency::task_continuation_context::use_current](reference/task-continuation-context-class.md#use_current) do określenia, że kontynuacja jest uruchamiany na wątku, który wywołał `task::then`.

Możesz przekazać `task_continuation_context` obiekt [Task::Then —](reference/task-class.md#then) metodę, aby jawnie kontrolować Kontekst wykonywania kontynuację albo można przekazywać zadania do innego typu apartment, a następnie wywołać `task::then` metody kontrolowania niejawnie Kontekst wykonywania.

> [!IMPORTANT]
>  Ponieważ głównego wątku interfejsu użytkownika w aplikacji platformy uniwersalnej systemu Windows uruchamiana STA, kontynuacja, utworzone w tym STA domyślnie uruchamiane w komórce jednowątkowej W związku z tym kontynuacji, które tworzysz na MTA systemem MTA.

W poniższej sekcji pokazano aplikację, która odczytuje plik z dysku, znajduje najbardziej popularne wyrazy w tym pliku, a następnie przedstawia wyniki w interfejsie użytkownika. Ostatniej operacji, aktualizowanie interfejsu użytkownika, występuje w wątku interfejsu użytkownika.

> [!IMPORTANT]
> To zachowanie jest specyficzne dla aplikacji platformy uniwersalnej systemu Windows. Dla aplikacji komputerowych nie kontroli, gdzie kontynuacje uruchomiona. Zamiast tego harmonogramu wybiera wątku roboczego, w którym można uruchomić każdy kontynuacji.

> [!IMPORTANT]
> Nie wywołuj [CONCURRENCY::Task:: wait](reference/task-class.md#wait) w treści kontynuacja, która działa w komórce jednowątkowej W przeciwnym wypadku środowisko wykonawcze zgłasza [concurrency::invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) , ponieważ ta metoda blokują bieżący wątek i może spowodować, że aplikacja przestanie odpowiadać. Jednak można wywoływać [CONCURRENCY::Task:: GET](reference/task-class.md#get) metodę do uzyskania wyniku zadania poprzedzającego w kontynuacji opartej na zadaniach.

##  <a name="example-app"></a> Przykład: Sterowanie wykonywaniem w aplikacji Windows Runtime z C++ i XAML

Należy wziąć pod uwagę aplikacji w języku C++ XAML, który odczytuje plik z dysku, znajduje najbardziej popularne wyrazy w tym pliku, a następnie przedstawia wyniki w interfejsie użytkownika. Aby stworzyć tę aplikację, uruchom, w programie Visual Studio, tworząc **pusta aplikacja (Windows Universal)** projektu i nadawania mu nazwy `CommonWords`. W manifeście aplikacji, należy określić **biblioteki dokumentów** możliwości, aby umożliwić aplikacji dostęp do folderu dokumenty. Typ pliku tekstowego (.txt) można również dodać do sekcji deklaracji w manifeście aplikacji. Aby uzyskać więcej informacji na temat możliwości aplikacji i deklaracji, zobacz [pakiety aplikacji i wdrażania](https://msdn.microsoft.com/library/windows/apps/hh464929.aspx).

Aktualizacja `Grid` elementu w pliku MainPage.xaml, aby uwzględnić `ProgressRing` elementu i `TextBlock` elementu. `ProgressRing` Wskazuje, że operacja jest w toku i `TextBlock` przedstawiono wyniki obliczeń.

[!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]

Dodaj następujący kod `#include` instrukcji pch.h.

[!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]

Dodaj następujące deklaracje metody do `MainPage` klasy (MainPage.h).

[!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]

Dodaj następujący kod `using` instrukcji MainPage.cpp.

[!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]

W pliku MainPage.cpp, zaimplementuj `MainPage::MakeWordList`, `MainPage::FindCommonWords`, i `MainPage::ShowResults` metody. `MainPage::MakeWordList` i `MainPage::FindCommonWords` praktyce intensywnie korzystających z operacji. `MainPage::ShowResults` Metoda wyświetla wynik obliczeń w interfejsie użytkownika.

[!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]

Modyfikowanie `MainPage` konstruktora, aby utworzyć łańcuch połączonych zadań, który wyświetla w interfejsie użytkownika popularne wyrazy w książce *Iliad* przez Homer. Pierwsze zadania kontynuacji dwóch, które Podziel tekst na poszczególnych wyrazów i możesz znaleźć popularne wyrazy, może zająć dużo czasu i w związku z tym są jawnie ustawione na uruchamianie w tle. Zadaniem końcowym kontynuacji, które aktualizacje interfejsu użytkownika, określa brak kontekstu kontynuacji, a w związku z powyższym apartamentu wątkowości reguły.

[!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]

> [!NOTE]
>  W tym przykładzie pokazano, jak określić kontekstami wykonywania i jak tworzyć w łańcuchu kontynuacji. Odwołaj, domyślnie zadanie, które jest tworzony z operacją asynchroniczną działa jego kontynuacji apartament, która wywołała `task::then`. W tym przykładzie użyto `task_continuation_context::use_arbitrary` do określenia, czy w wątku w tle można wykonać operacji, które nie wymagają interfejsu użytkownika.

Na poniższej ilustracji przedstawiono wyniki `CommonWords` aplikacji.

![Aplikacja CommonWords środowiska wykonawczego Windows](../../parallel/concrt/media/concrt_windows_common_words.png "Windows Runtime CommonWords aplikacji")

W tym przykładzie jest to możliwe zapewnić obsługę anulowania, ponieważ `task` obiekty, które obsługują `create_async` Użyj tokenu anulowanie niejawne. Definiowanie funkcji pracy do wykonania `cancellation_token` obiektu, jeśli konieczne reagowanie na operację anulowania w sposób współpracujący zadań. Aby uzyskać więcej informacji na temat anulowanie w PPL, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md)

## <a name="see-also"></a>Zobacz także

[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)
