---
title: Tworzenie operacji asynchronicznych C++ w aplikacjach platformy UWP
ms.date: 11/19/2018
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
ms.openlocfilehash: d6a36da79f24d98d162c4ffffff17b4471b2b063
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512250"
---
# <a name="creating-asynchronous-operations-in-c-for-uwp-apps"></a>Tworzenie operacji asynchronicznych C++ w aplikacjach platformy UWP

W tym dokumencie opisano niektóre kluczowe kwestie, które należy wziąć pod uwagę podczas używania klasy Task do tworzenia asynchronicznych operacji opartych na puli wątków systemu Windows w aplikacji uniwersalnej środowisko wykonawcze systemu Windows (platformy UWP).

Korzystanie z programowania asynchronicznego to kluczowy składnik modelu aplikacji środowisko wykonawcze systemu Windows, ponieważ umożliwia aplikacjom pozostawanie odpowiedzi na dane wejściowe użytkownika. Możesz uruchomić długotrwałe zadanie bez blokowania wątku interfejsu użytkownika, a następnie możesz otrzymać wyniki zadania później. Możesz również anulować zadania i odbierać powiadomienia o postępie, gdy zadania są uruchamiane w tle. [Programowanie asynchroniczne dokumentu w programie C++ ](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) zawiera omówienie wzorca asynchronicznego, który jest dostępny w wizualizacji C++ do tworzenia aplikacji platformy UWP. Ten dokument uczy się, jak używać i tworzyć łańcuchy asynchronicznych operacji środowisko wykonawcze systemu Windows. W tej sekcji opisano, jak używać typów w ppltasks. h do tworzenia asynchronicznych operacji, które mogą być używane przez inny składnik środowisko wykonawcze systemu Windows i jak kontrolować sposób wykonywania asynchronicznej pracy. Rozważ również odczytywanie [wzorców programowania asynchronicznego i porad w Hilo (aplikacje ze sklepu C++ Windows przy użyciu i XAML)](/previous-versions/windows/apps/jj160321(v=win.10)) , aby dowiedzieć się, jak używamy klasy Task do implementowania operacji asynchronicznych w Hilo, aplikacji środowisko wykonawcze systemu Windows przy użyciu C++ i języka XAML.

> [!NOTE]
>  Możesz użyć [biblioteki Parallel wzorców Library](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) i [asynchronicznej biblioteki Agents](../../parallel/concrt/asynchronous-agents-library.md) w aplikacji platformy UWP. Nie można jednak używać Harmonogram zadań ani Menedżer zasobów. Ten dokument zawiera opis dodatkowych funkcji udostępnianych przez program PPL, które są dostępne tylko dla aplikacji platformy UWP, a nie do aplikacji klasycznej.

## <a name="key-points"></a>Kwestie kluczowe

- Użyj [concurrency:: create_async](reference/concurrency-namespace-functions.md#create_async) , aby utworzyć operacje asynchroniczne, które mogą być używane przez inne składniki (które mogą być zapisywane w językach C++innych niż).

- Użyj [współbieżności::p rogress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) , aby raportować powiadomienia o postępie do składników wywołujących operacje asynchroniczne.

- Użyj tokenów anulowania, aby umożliwić anulowanie wewnętrznych operacji asynchronicznych.

- Zachowanie `create_async` funkcji zależy od zwracanego typu funkcji pracy, która jest do niego przenoszona. Funkcja robocza zwracająca zadanie ( `task<T>` lub `task<void>`) jest uruchamiana synchronicznie w kontekście, który został `create_async`wywołany. Funkcja służbowa, która `T` zwraca `void` lub działa w dowolnym kontekście.

- Można użyć metody [concurrency:: Task:: then](reference/task-class.md#then) , aby utworzyć łańcuch zadań, które są uruchamiane jeden po drugim. W aplikacji platformy UWP domyślny kontekst dla kontynuacji zadania zależy od tego, jak to zadanie zostało skonstruowane. Jeśli zadanie zostało utworzone przez przekazanie akcji asynchronicznej do konstruktora zadań lub przez przekazanie wyrażenia lambda, które zwraca akcję asynchroniczną, wówczas domyślny kontekst dla wszystkich kontynuacji tego zadania jest bieżącym kontekstem. Jeśli zadanie nie jest zbudowane z akcji asynchronicznej, domyślnie będzie używany dowolny kontekst dla kontynuacji zadania. Można zastąpić domyślny kontekst z klasą [concurrency:: task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) .

## <a name="in-this-document"></a>W tym dokumencie

- [Tworzenie operacji asynchronicznych](#create-async)

- [Przykład: Tworzenie składnika C++ środowisko wykonawcze systemu Windows](#example-component)

- [Kontrolowanie wątku wykonywania](#exethread)

- [Przykład: Kontrolowanie wykonywania w aplikacji środowisko wykonawcze systemu Windows z C++ i XAML](#example-app)

##  <a name="create-async"></a>Tworzenie operacji asynchronicznych

Do definiowania zadań w tle (PPL) można użyć modelu zadania i kontynuacji w bibliotece równoległych wzorców, a także dodatkowych zadań, które są uruchamiane po zakończeniu poprzedniego zadania. Ta funkcja jest udostępniana przez klasę [concurrency:: Task](../../parallel/concrt/reference/task-class.md) . Aby uzyskać więcej informacji na temat tego modelu `task` i klasy, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Środowisko wykonawcze systemu Windows to interfejs programowania, za pomocą którego można tworzyć aplikacje platformy UWP, które działają tylko w specjalnym środowisku systemu operacyjnego. Takie aplikacje korzystają z autoryzowanych funkcji, typów danych i urządzeń i są dystrybuowane z Microsoft Store. Środowisko wykonawcze systemu Windows jest reprezentowany przez *interfejs binarny aplikacji* (ABI). ABI to podstawowy kontrakt binarny, który sprawia, że interfejsy API środowisko wykonawcze systemu Windows są dostępne dla języków C++programowania, takich jak wizualizacja.

Korzystając z środowisko wykonawcze systemu Windows, można użyć najlepszych funkcji różnych języków programowania i połączyć je w jedną aplikację. Można na przykład utworzyć interfejs użytkownika w języku JavaScript i wykonać obliczeniową logikę aplikacji w C++ składniku. Możliwość wykonywania tych operacji intensywnie korzystających z obliczeń w tle jest kluczowym czynnikiem, który zapewnia czas odpowiedzi interfejsu użytkownika. Ponieważ Klasa jest specyficzna dla C++, należy użyć interfejsu środowisko wykonawcze systemu Windows, aby komunikować operacje asynchroniczne z innymi składnikami (które mogą być zapisywane w językach innych niż C++). `task` Środowisko wykonawcze systemu Windows udostępnia cztery interfejsy, których można użyć do reprezentowania operacji asynchronicznych:

[Windows::Foundation::IAsyncAction](/uwp/api/windows.foundation.iasyncaction)<br/>
Reprezentuje akcję asynchroniczną.

[Windows:: Foundation:: IAsyncActionWithProgress\<TProgress >](/uwp/api/Windows.Foundation.IAsyncActionWithProgress_TProgress_)<br/>
Reprezentuje asynchroniczną akcję służącą do raportowania postępu.

[Windows:: Foundation:: IAsyncOperation\<TResult >](/uwp/api/windows.foundation.iasyncoperation_tresult_)<br/>
Reprezentuje operację asynchroniczną, która zwraca wynik.

[Windows:: Foundation:: IAsyncOperationWithProgress\<TResult, TProgress >](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_)<br/>
Reprezentuje operację asynchroniczną zwracającą wynik i raporty postępu.

Pojęcie *akcji* oznacza, że zadanie asynchroniczne nie tworzy wartości (należy traktować funkcję, która zwraca `void`). Pojęcie *operacji* oznacza, że zadanie asynchroniczne wykonuje wartość. Pojęcie *postępu* oznacza, że zadanie może raportować komunikaty o postępie do obiektu wywołującego. Język JavaScript, .NET Framework i wizualizacja C++ każdy zapewnia własny sposób tworzenia wystąpień tych interfejsów do użycia na granicy ABI. Dla wizualizacji C++PPL zapewnia funkcję [concurrency:: create_async](reference/concurrency-namespace-functions.md#create_async) . Ta funkcja tworzy środowisko wykonawcze systemu Windows asynchronicznej akcji lub operacji, która reprezentuje ukończenie zadania. Funkcja przyjmuje funkcję służbową (zwykle wyrażenie lambda), wewnętrznie `task` tworzy obiekt i otacza to zadanie w jednym z czterech interfejsów środowisko wykonawcze systemu Windows asynchronicznej. `create_async`

> [!NOTE]
>  Należy `create_async` używać tylko wtedy, gdy trzeba utworzyć funkcje, do których można uzyskać dostęp za pomocą innego języka lub innego składnika Środowisko wykonawcze systemu Windows. Użyj klasy bezpośrednio, gdy wiesz, że operacja jest zarówno generowana, jak i C++ zużywana przez kod w tym samym składniku. `task`

Zwracany typ `create_async` jest określany przez typ argumentów. Na przykład, jeśli funkcja pracy nie zwraca wartości i nie zgłasza postępu, `create_async` zwraca. `IAsyncAction` Jeśli funkcja pracy nie zwraca wartości, a także raportuje postęp, `create_async` zwraca `IAsyncActionWithProgress`. Aby zgłosić postęp, podaj wartość [concurrency::p rogress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) Object jako parametr do funkcji służbowej. Możliwość raportowania postępu pozwala na zgłaszanie ilości wykonanej pracy i ilości nadal pozostałej (na przykład jako procent). Umożliwia także raportowanie wyników, gdy staną się dostępne.

`IAsyncAction`, ,,`IAsyncOperation<TResult>`I interfejsykażdy`Cancel` zapewniają metodę, która umożliwia anulowanie operacji asynchronicznej. `IAsyncActionOperationWithProgress<TProgress, TProgress>` `IAsyncActionWithProgress<TProgress>` `task` Klasa współpracuje z tokenami anulowania. W przypadku anulowania pracy przy użyciu tokenu anulowania środowisko uruchomieniowe nie uruchamia nowej pracy, która subskrybuje ten token. Działa, która jest już aktywna, może monitorować swój token anulowania i przestać, gdy będzie to możliwe. Ten mechanizm jest bardziej szczegółowo opisany w dokumencie [anulowanie dokumentu w PPL](cancellation-in-the-ppl.md). Anulowanie zadania można połączyć z metodami środowisko wykonawcze systemu Windows`Cancel` na dwa sposoby. Najpierw można zdefiniować funkcję roboczą, która `create_async` ma zostać przekazana, aby wykonać obiekt [concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) . Po wywołaniu `task` `create_async` metody ten token anulowania jest anulowany, a normalne reguły anulowania stosują się do obiektu bazowego, który obsługuje wywołanie. `Cancel` Jeśli nie podasz `cancellation_token` obiektu, obiekt źródłowy `task` definiuje jeden niejawnie. `cancellation_token` Zdefiniuj obiekt, gdy musisz wspólnie reagować na anulowanie w funkcji służbowej. Przykładowa [sekcja: Kontrolowanie wykonywania w aplikacji środowisko wykonawcze systemu Windows with C++ i XAML](#example-app) pokazuje przykład sposobu wykonywania anulowania w aplikacji platforma uniwersalna systemu Windows (platformy UWP) z C# i XAML korzystającej ze składnika niestandardowego środowisko wykonawcze systemu Windows C++ .

> [!WARNING]
>  W łańcuchu kontynuacji zadań zawsze czyści stan, a następnie Wywołaj [współbieżność:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) , gdy token anulowania zostanie anulowany. W przypadku powrotu wczesnej zamiast wywołania `cancel_current_task`, operacja przechodzi do stanu ukończenia, a nie anulowana.

Poniższa tabela zawiera podsumowanie kombinacji, których można użyć do definiowania operacji asynchronicznych w aplikacji.

|Aby utworzyć ten interfejs środowisko wykonawcze systemu Windows|Zwróć ten typ z`create_async`|Przekaż te typy parametrów do funkcji służbowej, aby użyć niejawnego tokenu anulowania|Przekaż te typy parametrów do funkcji służbowej, aby użyć jawnego tokenu anulowania|
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|`IAsyncAction`|`void` lub `task<void>`|dawaj|(`cancellation_token`)|
|`IAsyncActionWithProgress<TProgress>`|`void` lub `task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|
|`IAsyncOperation<TResult>`|`T` lub `task<T>`|dawaj|(`cancellation_token`)|
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T` lub `task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|

Można zwrócić wartość lub `task` obiekt z funkcji służbowej przekazanej `create_async` do funkcji. Te odmiany tworzą różne zachowania. Gdy zwracasz wartość, funkcja robocza jest opakowana w `task` taki sposób, aby można ją było uruchomić w wątku w tle. Ponadto, podstawowy `task` używa niejawnego tokenu anulowania. Z drugiej strony, jeśli zwracasz `task` obiekt, funkcja pracy jest uruchamiana synchronicznie. W związku z tym, jeśli `task` zwracany jest obiekt, należy się upewnić, że wszystkie długie operacje w funkcji służbowej również są uruchamiane jako zadania, aby umożliwić aplikacji pozostały czas odpowiedzi. Ponadto źródłowy `task` nie używa niejawnego tokenu anulowania. W związku z tym należy zdefiniować funkcję służbową, aby zastosować `cancellation_token` obiekt, jeśli wymagana jest obsługa anulowania podczas `task` zwracania obiektu z `create_async`.

W poniższym przykładzie przedstawiono różne sposoby tworzenia `IAsyncAction` obiektu, który może być używany przez inny składnik środowisko wykonawcze systemu Windows.

[!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]

##  <a name="example-component"></a>Przyklad Tworzenie składnika C++ środowisko wykonawcze systemu Windows i używanie go zC#

Rozważ użycie aplikacji używającej języka XAML C# i ZDEFINIOWANIE interfejsu użytkownika i C++ składnika Środowisko wykonawcze systemu Windows w celu wykonania operacji intensywnie korzystających z obliczeń. W tym przykładzie C++ składnik oblicza, które liczby z danego zakresu są podstawowe. Aby zilustrować różnice między czterema środowisko wykonawcze systemu Windows asynchronicznymi interfejsami zadań, Uruchom w programie Visual Studio, tworząc **puste rozwiązanie** i wprowadzając jego `Primes`nazwę. Następnie Dodaj do rozwiązania projekt **składnika Środowisko wykonawcze systemu Windows** i nadaje mu `PrimesLibrary`nazwę. Dodaj następujący kod do wygenerowanego C++ pliku nagłówkowego (ten przykład zmienia nazwę Class1. h na. h). Każda `public` Metoda definiuje jeden z czterech interfejsów asynchronicznych. Metody zwracające wartość zwracają obiekt [Windows:: Foundation:: Collections:: IVector\<int >](/uwp/api/Windows.Foundation.Collections.IVector_T_) . Metody, które zgłaszają postęp `double` , tworzą wartości, które definiują wartość procentową ogólnej pracy, która została ukończona.

[!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]

> [!NOTE]
>  Zgodnie z Konwencją, nazwy metod asynchronicznych w środowisko wykonawcze systemu Windows zwykle kończą się na "Async".

Dodaj następujący kod do wygenerowanego C++ pliku źródłowego (w tym przykładzie zmieniamy nazwę Class1. cpp na sources. cpp). Funkcja `is_prime` określa, czy dane wejściowe są podstawowe. Pozostałe metody implementują `Primes` klasę. Każde wywołanie `create_async` używa sygnatury zgodnej z metodą, z której jest wywoływana. Na przykład, ponieważ `Primes::ComputePrimesAsync` zwraca `IAsyncAction`, `create_async` funkcja robocza, która jest dostarczana, `progress_reporter` nie zwraca wartości i nie przyjmuje obiektu jako parametru.

[!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]

Każda metoda najpierw wykonuje walidację, aby upewnić się, że parametry wejściowe nie są ujemne. Jeśli wartość wejściowa jest ujemna, metoda zgłasza [platformę:: InvalidArgumentException](../../cppcx/platform-invalidargumentexception-class.md). Obsługa błędów została omówiona w dalszej części tej sekcji.

Aby korzystać z tych metod z poziomu aplikacji platformy UWP, użyj szablonu C# Visual **blank App (XAML)** , aby dodać drugi projekt do rozwiązania programu Visual Studio. Ten przykład nazywa projekt `Primes`. Następnie w `Primes` projekcie Dodaj odwołanie `PrimesLibrary` do projektu.

Dodaj następujący kod do MainPage. XAML. Ten kod definiuje interfejs użytkownika, dzięki czemu można wywołać C++ składnik i wyświetlić wyniki.

[!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]

Dodaj następujący kod do `MainPage` klasy w MainPage. XAML. Ten kod definiuje `Primes` obiekt i programy obsługi zdarzeń przycisku.

[!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]

Te metody używają `async` słów kluczowych `await` i do aktualizowania interfejsu użytkownika po zakończeniu operacji asynchronicznych. Aby uzyskać informacje na temat kodowania asynchronicznego w aplikacjach platformy UWP, zobacz [wątkowość i programowanie asynchroniczne](/windows/uwp/threading-async).

Metody `getPrimesCancellation` i`cancelGetPrimes` współpracują ze sobą, aby umożliwić użytkownikowi anulowanie operacji. Gdy użytkownik wybierze przycisk **Anuluj** , `cancelGetPrimes` metoda wywołuje [IAsyncOperationWithProgress\<TResult, TProgress >:: Cancel](/uwp/api/windows.foundation.iasyncinfo.cancel) , aby anulować operację. Środowisko uruchomieniowe współbieżności, która zarządza podstawową operacją asynchroniczną, zgłasza wewnętrzny typ wyjątku, który jest przechwytywany przez środowisko wykonawcze systemu Windows do komunikowania się, że anulowanie zostało zakończone. Aby uzyskać więcej informacji na temat modelu anulowania, zobacz [anulowania](../../parallel/concrt/cancellation-in-the-ppl.md).

> [!IMPORTANT]
>  Aby umożliwić PPL poprawne raportowanie do środowisko wykonawcze systemu Windows, że operacja została anulowana, nie Przechwytuj tego wewnętrznego typu wyjątku. Oznacza to, że nie należy również przechwytywać wszystkich wyjątków`catch (...)`(). Jeśli musisz przechwycić wszystkie wyjątki, ponownie Zgłoś wyjątek, aby upewnić się, że środowisko wykonawcze systemu Windows może ukończyć operację anulowania.

Na poniższej ilustracji przedstawiono `Primes` aplikację po wybraniu każdej opcji.

![Aplikacja podstawowa środowisko wykonawcze systemu Windows](../../parallel/concrt/media/concrt_windows_primes.png "Aplikacja podstawowa środowisko wykonawcze systemu Windows")

Przykłady `create_async` służące do tworzenia zadań asynchronicznych, które mogą być używane przez inne języki, można znaleźć [w temacie using C++ in the Bing Maps-Optymalizator podróży](/previous-versions/windows/apps/hh699891(v=vs.140)) i [operacje C++ asynchroniczne systemu Windows 8 w programie z PPL](https://code.msdn.microsoft.com/windowsapps/windows-8-asynchronous-08009a0d).

##  <a name="exethread"></a>Kontrolowanie wątku wykonywania

Środowisko wykonawcze systemu Windows używa modelu wątkowości COM. W tym modelu obiekty są hostowane w różnych apartamentachach, w zależności od tego, jak obsługują synchronizację. Obiekty bezpieczne wątkowo są hostowane w apartamentach wielowątkowych (MTA). Obiekty, do których musi być dostęp pojedynczy wątek, są hostowane w jednowątkowym apartamentie (STA).

W aplikacji, która ma interfejs użytkownika, wątek ASTA (Application STA) jest odpowiedzialny za komunikaty okna pompowania i jest jedynym wątkiem w procesie, który może aktualizować kontrolki interfejsu użytkownika obsługiwane przez STA. Ma to dwa konsekwencje. Po pierwsze, aby zapewnić, że aplikacja będzie odpowiadać, wszystkie operacje związane z intensywnym procesorem CPU i we/wy nie powinny być uruchamiane w wątku ASTA. Po drugie wyniki pochodzące z wątków w tle muszą być organizowane z powrotem do ASTA w celu zaktualizowania interfejsu użytkownika. W aplikacji C++ `MainPage` platformy UWP oraz inne strony XAML działają w ATSA. W związku z tym, kontynuacje zadań, które są zadeklarowane w ASTA, są domyślnie uruchamiane w tym miejscu, aby można było zaktualizować formanty bezpośrednio w treści kontynuacji. Jeśli jednak zazagnieżdżasz zadanie w innym zadaniu, wszelkie kontynuacje tego zadania zagnieżdżonego zostanie uruchomione w MTA. W związku z tym należy rozważyć, czy jawnie określić kontekst, w którym są uruchamiane te kontynuacje.

Zadanie, które jest tworzone na podstawie operacji asynchronicznej, na `IAsyncOperation<TResult>`przykład używa specjalnej semantyki, która może pomóc zignorować szczegóły wątku. Mimo że operacja może być uruchamiana w wątku w tle (lub może nie być w ogóle nieobsługiwana przez wątek), jego kontynuacje są domyślnie gwarantowane do uruchomienia w apartamentu, który uruchomił operacje kontynuacji (innymi słowy, od apartamentu, który wywołał `task::then`). Można użyć klasy [concurrency:: task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) , aby kontrolować kontekst wykonywania kontynuacji. Użyj tych statycznych metod pomocnika do `task_continuation_context` tworzenia obiektów:

- Użyj [concurrency:: task_continuation_context:: use_arbitrary](reference/task-continuation-context-class.md#use_arbitrary) , aby określić, że kontynuacja jest uruchamiana w wątku w tle.

- Użyj [concurrency:: task_continuation_context:: use_current](reference/task-continuation-context-class.md#use_current) , aby określić, że kontynuacja jest uruchamiana w `task::then`wątku, który został wywołany.

Można przekazać `task_continuation_context` obiekt do [zadania:: then](reference/task-class.md#then) metodę, aby jawnie kontrolować kontekst wykonywania kontynuacji lub przekazać zadanie do innej komórki `task::then` , a następnie wywołać metodę, aby niejawnie kontrolować kontekst wykonywania .

> [!IMPORTANT]
>  Ze względu na to, że główny wątek interfejsu użytkownika aplikacji platformy UWP działa w ramach STA, kontynuacje tworzone w ramach tego STA są domyślnie uruchamiane w STA. W związku z tym kontynuacje tworzone w ramach MTA działa w ramach MTA.

W poniższej sekcji przedstawiono aplikację, która odczytuje plik z dysku, znajduje najbardziej typowe słowa w tym pliku, a następnie wyświetla wyniki w interfejsie użytkownika. Operacja końcowa, która aktualizuje interfejs użytkownika, występuje w wątku interfejsu użytkownika.

> [!IMPORTANT]
> To zachowanie jest specyficzne dla aplikacji platformy UWP. W przypadku aplikacji klasycznych nie kontroluje się, gdzie działają kontynuacje. Zamiast tego harmonogram wybiera wątek roboczy, na którym ma zostać uruchomiona każda kontynuacja.

> [!IMPORTANT]
> Nie wywołuj [concurrency:: Task:: wait](reference/task-class.md#wait) w treści kontynuacji działającej w sta. W przeciwnym razie środowisko uruchomieniowe zgłasza [współbieżność:: invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) , ponieważ ta metoda blokuje bieżący wątek i może spowodować, że aplikacja przestanie odpowiadać. Można jednak wywołać metodę [concurrency:: Task:: Get](reference/task-class.md#get) , aby otrzymać wynik zadania poprzedzającego w kontynuacji opartej na zadaniach.

##  <a name="example-app"></a>Przyklad Kontrolowanie wykonywania w aplikacji środowisko wykonawcze systemu Windows z C++ i XAML

Rozważmy C++ aplikację XAML, która odczytuje plik z dysku, wyszukuje najbardziej typowe słowa w tym pliku, a następnie wyświetla wyniki w interfejsie użytkownika. Aby utworzyć tę aplikację, Uruchom w programie Visual Studio, tworząc pustą **aplikację (uniwersalną systemu Windows)** i nadając jej `CommonWords`nazwę. W manifeście aplikacji Określ możliwości **biblioteki dokumenty** , aby umożliwić aplikacji dostęp do folderu dokumentów. Dodaj także typ pliku tekstowego (. txt) do sekcji deklaracji manifestu aplikacji. Aby uzyskać więcej informacji na temat możliwości i deklaracji aplikacji, zobacz [pakowanie, wdrażanie i wykonywanie zapytań dotyczących aplikacji systemu Windows](/windows/win32/appxpkg/appx-portal).

Zaktualizuj element w MainPage. XAML w celu `ProgressRing` uwzględnienia elementu i `TextBlock` elementu. `Grid` Wskazuje, że operacja jest w toku `TextBlock` i pokazuje wyniki obliczenia. `ProgressRing`

[!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]

Dodaj następujące `#include` instrukcje do PCH. h.

[!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]

Dodaj następujące deklaracje metody do `MainPage` klasy (MainPage. h).

[!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]

Dodaj następujące `using` instrukcje do MainPage. cpp.

[!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]

W MainPage. cpp Zaimplementuj `MainPage::MakeWordList`metody, `MainPage::FindCommonWords`, i. `MainPage::ShowResults` `MainPage::MakeWordList` I`MainPage::FindCommonWords` wykonują operacje obliczeniowe z dużym obciążeniem. `MainPage::ShowResults` Metoda wyświetla wynik obliczeń w interfejsie użytkownika.

[!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]

Zmodyfikuj konstruktora, aby utworzyć łańcuch zadań kontynuacji, które są wyświetlane w interfejsie użytkownika, w którym często występują słowa w książce Iliad przez stronę domową. `MainPage` Pierwsze dwa zadania kontynuacji, które dzielą tekst na poszczególne wyrazy i Znajdź typowe słowa, mogą być czasochłonne i dlatego jawnie ustawione na uruchamianie w tle. Końcowe zadanie kontynuacji, które aktualizuje interfejs użytkownika, określa brak kontekstu kontynuacji i w związku z tym następuje po wątkach reguł.

[!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]

> [!NOTE]
>  W tym przykładzie pokazano, jak określić konteksty wykonywania i jak utworzyć łańcuch kontynuacji. Odwołaj to domyślnie zadanie, które jest tworzone na podstawie operacji asynchronicznej, uruchamia jego kontynuację w Apartament, który `task::then`został wywołany. W związku z tym ten `task_continuation_context::use_arbitrary` przykład służy do określenia, że operacje, które nie obejmują interfejsu użytkownika, są wykonywane w wątku w tle.

Na poniższej ilustracji przedstawiono wyniki `CommonWords` aplikacji.

![Środowisko wykonawcze systemu Windows aplikacji CommonWords](../../parallel/concrt/media/concrt_windows_common_words.png "Środowisko wykonawcze systemu Windows aplikacji CommonWords")

W tym przykładzie można obsługiwać anulowanie, ponieważ `task` obiekty, które obsługują `create_async` użycie niejawnego tokenu anulowania. Zdefiniuj funkcję służbową, aby utworzyć `cancellation_token` obiekt, jeśli zadania muszą odpowiedzieć na anulowanie w sposób współdziałający. Aby uzyskać więcej informacji na temat anulowania w PPL, zobacz [Anulowanie w PPL](cancellation-in-the-ppl.md)

## <a name="see-also"></a>Zobacz także

[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)
