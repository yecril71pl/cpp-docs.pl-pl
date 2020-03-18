---
title: Tworzenie operacji asynchronicznych C++ w aplikacjach platformy UWP
ms.date: 11/19/2018
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
ms.openlocfilehash: 2ceb22afa5e6d071c1cb8dae79327eaaf08e3ee1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445108"
---
# <a name="creating-asynchronous-operations-in-c-for-uwp-apps"></a>Tworzenie operacji asynchronicznych C++ w aplikacjach platformy UWP

W tym dokumencie opisano niektóre kluczowe kwestie, które należy wziąć pod uwagę podczas używania klasy Task do tworzenia asynchronicznych operacji opartych na puli wątków systemu Windows w aplikacji uniwersalnej środowisko wykonawcze systemu Windows (platformy UWP).

Korzystanie z programowania asynchronicznego to kluczowy składnik modelu aplikacji środowisko wykonawcze systemu Windows, ponieważ umożliwia aplikacjom pozostawanie odpowiedzi na dane wejściowe użytkownika. Możesz uruchomić długotrwałe zadanie bez blokowania wątku interfejsu użytkownika, a następnie możesz otrzymać wyniki zadania później. Możesz również anulować zadania i odbierać powiadomienia o postępie, gdy zadania są uruchamiane w tle. [Programowanie asynchroniczne dokumentu w programie C++ ](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) zawiera omówienie wzorca asynchronicznego, który jest dostępny w wizualizacji C++ do tworzenia aplikacji platformy UWP. Ten dokument uczy się, jak używać i tworzyć łańcuchy asynchronicznych operacji środowisko wykonawcze systemu Windows. W tej sekcji opisano, jak używać typów w ppltasks. h do tworzenia asynchronicznych operacji, które mogą być używane przez inny składnik środowisko wykonawcze systemu Windows i jak kontrolować sposób wykonywania asynchronicznej pracy. Rozważ również odczytywanie [wzorców programowania asynchronicznego i porad w Hilo (aplikacje ze sklepu C++ Windows przy użyciu i XAML)](/previous-versions/windows/apps/jj160321(v=win.10)) , aby dowiedzieć się, jak używamy klasy Task do implementowania operacji asynchronicznych w Hilo, aplikacji środowisko wykonawcze systemu Windows przy użyciu C++ i języka XAML.

> [!NOTE]
> Możesz użyć [biblioteki Parallel wzorców Library](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) i [asynchronicznej biblioteki Agents](../../parallel/concrt/asynchronous-agents-library.md) w aplikacji platformy UWP. Nie można jednak używać Harmonogram zadań ani Menedżer zasobów. Ten dokument zawiera opis dodatkowych funkcji udostępnianych przez program PPL, które są dostępne tylko dla aplikacji platformy UWP, a nie do aplikacji klasycznej.

## <a name="key-points"></a>Kwestie kluczowe

- Użyj [concurrency:: create_async](reference/concurrency-namespace-functions.md#create_async) , aby utworzyć operacje asynchroniczne, które mogą być używane przez inne składniki (które mogą być zapisywane w językach C++innych niż).

- Użyj [współbieżności::p rogress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) , aby zgłosić powiadomienia o postępie do składników wywołujących operacje asynchroniczne.

- Użyj tokenów anulowania, aby umożliwić anulowanie wewnętrznych operacji asynchronicznych.

- Zachowanie funkcji `create_async` zależy od zwracanego typu funkcji pracy, która jest do niego przenoszona. Funkcja robocza zwracająca zadanie (`task<T>` lub `task<void>`) przebiega synchronicznie w kontekście, który wywołał `create_async`. Funkcja robocza zwracająca `T` lub `void` uruchamiana w dowolnym kontekście.

- Można użyć metody [concurrency:: Task:: then](reference/task-class.md#then) , aby utworzyć łańcuch zadań, które są uruchamiane jeden po drugim. W aplikacji platformy UWP domyślny kontekst dla kontynuacji zadania zależy od tego, jak to zadanie zostało skonstruowane. Jeśli zadanie zostało utworzone przez przekazanie akcji asynchronicznej do konstruktora zadań lub przez przekazanie wyrażenia lambda, które zwraca akcję asynchroniczną, wówczas domyślny kontekst dla wszystkich kontynuacji tego zadania jest bieżącym kontekstem. Jeśli zadanie nie jest zbudowane z akcji asynchronicznej, domyślnie będzie używany dowolny kontekst dla kontynuacji zadania. Domyślny kontekst można zastąpić za pomocą klasy [concurrency:: task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) .

## <a name="in-this-document"></a>W tym dokumencie

- [Tworzenie operacji asynchronicznych](#create-async)

- [Przykład: Tworzenie składnika C++ środowisko wykonawcze systemu Windows](#example-component)

- [Kontrolowanie wątku wykonywania](#exethread)

- [Przykład: kontrolowanie wykonywania w aplikacji środowisko wykonawcze systemu Windows z C++ i XAML](#example-app)

## <a name="create-async"></a>Tworzenie operacji asynchronicznych

Do definiowania zadań w tle (PPL) można użyć modelu zadania i kontynuacji w bibliotece równoległych wzorców, a także dodatkowych zadań, które są uruchamiane po zakończeniu poprzedniego zadania. Ta funkcja jest udostępniana przez klasę [concurrency:: Task](../../parallel/concrt/reference/task-class.md) . Aby uzyskać więcej informacji na temat tego modelu i klasy `task`, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Środowisko wykonawcze systemu Windows to interfejs programowania, za pomocą którego można tworzyć aplikacje platformy UWP, które działają tylko w specjalnym środowisku systemu operacyjnego. Takie aplikacje korzystają z autoryzowanych funkcji, typów danych i urządzeń i są dystrybuowane z Microsoft Store. Środowisko wykonawcze systemu Windows jest reprezentowany przez *interfejs binarny aplikacji* (ABI). ABI to podstawowy kontrakt binarny, który sprawia, że interfejsy API środowisko wykonawcze systemu Windows są dostępne dla języków C++programowania, takich jak wizualizacja.

Korzystając z środowisko wykonawcze systemu Windows, można użyć najlepszych funkcji różnych języków programowania i połączyć je w jedną aplikację. Można na przykład utworzyć interfejs użytkownika w języku JavaScript i wykonać obliczeniową logikę aplikacji w C++ składniku. Możliwość wykonywania tych operacji intensywnie korzystających z obliczeń w tle jest kluczowym czynnikiem, który zapewnia czas odpowiedzi interfejsu użytkownika. Ponieważ Klasa `task` jest specyficzna dla C++programu, należy użyć interfejsu środowisko wykonawcze systemu Windows, aby komunikować operacje asynchroniczne z innymi składnikami (które mogą być zapisywane w językach innych C++niż). Środowisko wykonawcze systemu Windows udostępnia cztery interfejsy, których można użyć do reprezentowania operacji asynchronicznych:

[Windows:: Foundation:: IAsyncAction](/uwp/api/windows.foundation.iasyncaction)<br/>
Reprezentuje akcję asynchroniczną.

[Windows:: Foundation:: IAsyncActionWithProgress\<TProgress >](/uwp/api/Windows.Foundation.IAsyncActionWithProgress_TProgress_)<br/>
Reprezentuje asynchroniczną akcję służącą do raportowania postępu.

[Windows:: Foundation:: IAsyncOperation\<TResult >](/uwp/api/windows.foundation.iasyncoperation_tresult_)<br/>
Reprezentuje operację asynchroniczną, która zwraca wynik.

[Windows:: Foundation:: IAsyncOperationWithProgress\<TResult, TProgress >](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_)<br/>
Reprezentuje operację asynchroniczną zwracającą wynik i raporty postępu.

Pojęcie *akcji* oznacza, że zadanie asynchroniczne nie produkuje wartości (należy traktować funkcję, która zwraca `void`). Pojęcie *operacji* oznacza, że zadanie asynchroniczne wykonuje wartość. Pojęcie *postępu* oznacza, że zadanie może raportować komunikaty o postępie do obiektu wywołującego. Język JavaScript, .NET Framework i wizualizacja C++ każdy zapewnia własny sposób tworzenia wystąpień tych interfejsów do użycia na granicy ABI. Dla wizualizacji C++PPL zapewnia funkcję [concurrency:: create_async](reference/concurrency-namespace-functions.md#create_async) . Ta funkcja tworzy środowisko wykonawcze systemu Windows asynchronicznej akcji lub operacji, która reprezentuje ukończenie zadania. Funkcja `create_async` przyjmuje funkcję roboczą (zazwyczaj wyrażenie lambda), wewnętrznie tworzy obiekt `task` i otacza to zadanie w jednym z czterech interfejsów środowisko wykonawcze systemu Windows asynchronicznych.

> [!NOTE]
> `create_async` należy używać tylko wtedy, gdy trzeba utworzyć funkcje, do których można uzyskać dostęp za pomocą innego języka lub innego składnika środowisko wykonawcze systemu Windows. Klasy `task` należy używać bezpośrednio, gdy wiadomo, że operacja jest generowana i zużywana C++ przez kod w tym samym składniku.

Zwracany typ `create_async` jest określany przez typ argumentów. Jeśli na przykład funkcja robocza nie zwróci wartości i nie zgłasza postępu, `create_async` zwraca `IAsyncAction`. Jeśli funkcja pracy nie zwraca wartości, a także raportuje postęp, `create_async` zwraca `IAsyncActionWithProgress`. Aby raportować postęp, podaj obiekt [concurrency::p rogress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) jako parametr do funkcji służbowej. Możliwość raportowania postępu pozwala na zgłaszanie ilości wykonanej pracy i ilości nadal pozostałej (na przykład jako procent). Umożliwia także raportowanie wyników, gdy staną się dostępne.

Interfejsy `IAsyncAction`, `IAsyncActionWithProgress<TProgress>`, `IAsyncOperation<TResult>`i `IAsyncActionOperationWithProgress<TProgress, TProgress>` zapewniają metodę `Cancel`, która umożliwia anulowanie operacji asynchronicznej. Klasa `task` współpracuje z tokenami anulowania. W przypadku anulowania pracy przy użyciu tokenu anulowania środowisko uruchomieniowe nie uruchamia nowej pracy, która subskrybuje ten token. Działa, która jest już aktywna, może monitorować swój token anulowania i przestać, gdy będzie to możliwe. Ten mechanizm jest bardziej szczegółowo opisany w dokumencie [anulowanie dokumentu w PPL](cancellation-in-the-ppl.md). Anulowanie zadania można połączyć z metodami`Cancel` środowisko wykonawcze systemu Windows na dwa sposoby. Najpierw można zdefiniować funkcję roboczą, która została przekazana do `create_async` w celu wykonania obiektu [concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) . Po wywołaniu metody `Cancel` ten token anulowania jest anulowany, a normalne reguły anulowania stosują się do bazowego obiektu `task`, który obsługuje wywołanie `create_async`. Jeśli nie podasz obiektu `cancellation_token`, źródłowy obiekt `task` definiuje jeden niejawnie. Zdefiniuj obiekt `cancellation_token`, gdy musisz wspólnie reagować na anulowanie w funkcji służbowej. Przykład sekcji [: kontrolowanie wykonywania w aplikacji środowisko wykonawcze systemu Windows z C++ i XAML](#example-app) pokazuje przykład sposobu wykonywania anulowania w aplikacji platforma uniwersalna systemu Windows (platformy UWP) z C# i xaml korzystającej ze składnika niestandardowego środowisko wykonawcze systemu Windows C++ .

> [!WARNING]
> W łańcuchu kontynuacji zadań zawsze czyści stan, a następnie Wywołaj [współbieżność:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) , gdy token anulowania zostanie anulowany. W przypadku wcześniejszego zwrócenia zamiast wywołania `cancel_current_task`, operacja przechodzi do stanu ukończenia, a nie anulowana.

Poniższa tabela zawiera podsumowanie kombinacji, których można użyć do definiowania operacji asynchronicznych w aplikacji.

|Aby utworzyć ten interfejs środowisko wykonawcze systemu Windows|Zwróć ten typ z `create_async`|Przekaż te typy parametrów do funkcji służbowej, aby użyć niejawnego tokenu anulowania|Przekaż te typy parametrów do funkcji służbowej, aby użyć jawnego tokenu anulowania|
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|`IAsyncAction`|`void` lub `task<void>`|dawaj|(`cancellation_token`)|
|`IAsyncActionWithProgress<TProgress>`|`void` lub `task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|
|`IAsyncOperation<TResult>`|`T` lub `task<T>`|dawaj|(`cancellation_token`)|
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T` lub `task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|

Można zwrócić wartość lub obiekt `task` z funkcji służbowej przekazanej do funkcji `create_async`. Te odmiany tworzą różne zachowania. Gdy zwracasz wartość, funkcja robocza jest opakowana w `task`, aby można ją było uruchomić w wątku w tle. Ponadto bazowe `task` używa niejawnego tokenu anulowania. Z drugiej strony, jeśli zwracasz obiekt `task`, funkcja robocza jest uruchamiana synchronicznie. W związku z tym, Jeśli zwracany jest obiekt `task`, należy się upewnić, że wszystkie długotrwałe operacje w funkcji służbowej również są uruchamiane jako zadania, aby zapewnić, że aplikacja pozostanie niezależna. Ponadto bazowe `task` nie używa niejawnego tokenu anulowania. W związku z tym należy zdefiniować funkcję służbową, aby zastosować obiekt `cancellation_token`, jeśli wymagana jest obsługa anulowania podczas zwracania obiektu `task` z `create_async`.

W poniższym przykładzie przedstawiono różne sposoby tworzenia obiektu `IAsyncAction`, które mogą być używane przez inny składnik środowisko wykonawcze systemu Windows.

[!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]

## <a name="example-component"></a>Przykład: Tworzenie składnika C++ środowisko wykonawcze systemu Windows i używanie go z poziomu języka C\#

Rozważ użycie aplikacji używającej języka XAML C# i ZDEFINIOWANIE interfejsu użytkownika i C++ składnika Środowisko wykonawcze systemu Windows w celu wykonania operacji intensywnie korzystających z obliczeń. W tym przykładzie C++ składnik oblicza, które liczby z danego zakresu są podstawowe. Aby zilustrować różnice między czterema środowisko wykonawcze systemu Windows asynchronicznymi interfejsami zadań, Uruchom w programie Visual Studio, tworząc **puste rozwiązanie** i wprowadzając nazwę `Primes`. Następnie Dodaj do rozwiązania środowisko wykonawcze systemu Windows projektu **składnika** i nadawanie mu nazwy `PrimesLibrary`. Dodaj następujący kod do wygenerowanego C++ pliku nagłówkowego (ten przykład zmienia nazwę Class1. h na. h). Każda metoda `public` definiuje jeden z czterech interfejsów asynchronicznych. Metody zwracające wartość zwracają obiekt [Windows:: Foundation:: Collections:: IVector\<int >](/uwp/api/Windows.Foundation.Collections.IVector_T_) . Metody raportujące postęp generują `double` wartości, które definiują wartość procentową ogólnej pracy, która została ukończona.

[!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]

> [!NOTE]
> Zgodnie z Konwencją, nazwy metod asynchronicznych w środowisko wykonawcze systemu Windows zwykle kończą się na "Async".

Dodaj następujący kod do wygenerowanego C++ pliku źródłowego (w tym przykładzie zmieniamy nazwę Class1. cpp na sources. cpp). Funkcja `is_prime` określa, czy dane wejściowe są podstawowe. Pozostałe metody implementują klasę `Primes`. Każde wywołanie `create_async` używa sygnatury zgodnej z metodą, z której jest wywoływana. Na przykład, ponieważ `Primes::ComputePrimesAsync` zwraca `IAsyncAction`, funkcja robocza, która jest dostarczana do `create_async` nie zwraca wartości i nie przyjmuje obiektu `progress_reporter` jako parametru.

[!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]

Każda metoda najpierw wykonuje walidację, aby upewnić się, że parametry wejściowe nie są ujemne. Jeśli wartość wejściowa jest ujemna, metoda zgłasza [platformę:: InvalidArgumentException](../../cppcx/platform-invalidargumentexception-class.md). Obsługa błędów została omówiona w dalszej części tej sekcji.

Aby korzystać z tych metod z poziomu aplikacji platformy UWP, użyj szablonu C# Visual **blank App (XAML)** , aby dodać drugi projekt do rozwiązania programu Visual Studio. Ten przykład nazywa `Primes`projektu. Następnie w projekcie `Primes` Dodaj odwołanie do projektu `PrimesLibrary`.

Dodaj następujący kod do MainPage. XAML. Ten kod definiuje interfejs użytkownika, dzięki czemu można wywołać C++ składnik i wyświetlić wyniki.

[!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]

Dodaj następujący kod do klasy `MainPage` w MainPage. XAML. Ten kod definiuje obiekt `Primes` i programy obsługi zdarzeń przycisku.

[!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]

Te metody używają słów kluczowych `async` i `await` do aktualizowania interfejsu użytkownika po zakończeniu operacji asynchronicznych. Aby uzyskać informacje na temat kodowania asynchronicznego w aplikacjach platformy UWP, zobacz [wątkowość i programowanie asynchroniczne](/windows/uwp/threading-async).

Metody `getPrimesCancellation` i `cancelGetPrimes` współpracują ze sobą, aby umożliwić użytkownikowi anulowanie operacji. Gdy użytkownik wybierze przycisk **Anuluj** , Metoda `cancelGetPrimes` wywołuje [IAsyncOperationWithProgress\<TResult, TProgress >:: Cancel](/uwp/api/windows.foundation.iasyncinfo.cancel) , aby anulować operację. Środowisko uruchomieniowe współbieżności, która zarządza podstawową operacją asynchroniczną, zgłasza wewnętrzny typ wyjątku, który jest przechwytywany przez środowisko wykonawcze systemu Windows do komunikowania się, że anulowanie zostało zakończone. Aby uzyskać więcej informacji na temat modelu anulowania, zobacz [anulowania](../../parallel/concrt/cancellation-in-the-ppl.md).

> [!IMPORTANT]
> Aby umożliwić PPL poprawne raportowanie do środowisko wykonawcze systemu Windows, że operacja została anulowana, nie Przechwytuj tego wewnętrznego typu wyjątku. Oznacza to, że nie należy również przechwytywać wszystkich wyjątków (`catch (...)`). Jeśli musisz przechwycić wszystkie wyjątki, ponownie Zgłoś wyjątek, aby upewnić się, że środowisko wykonawcze systemu Windows może ukończyć operację anulowania.

Na poniższej ilustracji przedstawiono aplikację `Primes` po wybraniu każdej opcji.

![Aplikacja podstawowa środowisko wykonawcze systemu Windows](../../parallel/concrt/media/concrt_windows_primes.png "Aplikacja podstawowa środowisko wykonawcze systemu Windows")

Przykłady, które używają `create_async` do tworzenia zadań asynchronicznych, które mogą być używane przez inne języki, można znaleźć [w temacie using C++ in the Bing Maps-Optymalizator podróży](/previous-versions/windows/apps/hh699891(v=vs.140)) i [operacje asynchroniczne systemu Windows 8 w programie C++ z PPL](https://code.msdn.microsoft.com/windowsapps/windows-8-asynchronous-08009a0d).

## <a name="exethread"></a>Kontrolowanie wątku wykonywania

Środowisko wykonawcze systemu Windows używa modelu wątkowości COM. W tym modelu obiekty są hostowane w różnych apartamentachach, w zależności od tego, jak obsługują synchronizację. Obiekty bezpieczne wątkowo są hostowane w apartamentach wielowątkowych (MTA). Obiekty, do których musi być dostęp pojedynczy wątek, są hostowane w jednowątkowym apartamentie (STA).

W aplikacji, która ma interfejs użytkownika, wątek ASTA (Application STA) jest odpowiedzialny za komunikaty okna pompowania i jest jedynym wątkiem w procesie, który może aktualizować kontrolki interfejsu użytkownika obsługiwane przez STA. Ma to dwa konsekwencje. Po pierwsze, aby zapewnić, że aplikacja będzie odpowiadać, wszystkie operacje związane z intensywnym procesorem CPU i we/wy nie powinny być uruchamiane w wątku ASTA. Po drugie wyniki pochodzące z wątków w tle muszą być organizowane z powrotem do ASTA w celu zaktualizowania interfejsu użytkownika. W aplikacji C++ platformy UWP `MainPage` i inne strony XAML działają w ATSA. W związku z tym, kontynuacje zadań, które są zadeklarowane w ASTA, są domyślnie uruchamiane w tym miejscu, aby można było zaktualizować formanty bezpośrednio w treści kontynuacji. Jeśli jednak zazagnieżdżasz zadanie w innym zadaniu, wszelkie kontynuacje tego zadania zagnieżdżonego zostanie uruchomione w MTA. W związku z tym należy rozważyć, czy jawnie określić kontekst, w którym są uruchamiane te kontynuacje.

Zadanie, które jest tworzone na podstawie operacji asynchronicznej, takiej jak `IAsyncOperation<TResult>`, używa specjalnej semantyki, która może pomóc zignorować szczegóły wątku. Mimo że operacja może być uruchamiana w wątku w tle (lub może nie być w ogóle nieobsługiwana przez wątek), jego kontynuacje są domyślnie gwarantowane do uruchomienia w apartamentu, który uruchomił operacje kontynuacji (innymi słowy, od apartamentu o nazwie `task::then`). Można użyć klasy [concurrency:: task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) , aby kontrolować kontekst wykonywania kontynuacji. Te statyczne metody pomocnika służą do tworzenia `task_continuation_context` obiektów:

- Użyj [concurrency:: task_continuation_context:: use_arbitrary](reference/task-continuation-context-class.md#use_arbitrary) , aby określić, że kontynuacja jest uruchamiana w wątku w tle.

- Użyj [concurrency:: task_continuation_context:: use_current](reference/task-continuation-context-class.md#use_current) , aby określić, że kontynuacja jest uruchamiana w wątku, który wywołał `task::then`.

Obiekt `task_continuation_context` można przekazać do [zadania:: then](reference/task-class.md#then) metodę, aby jawnie kontrolować kontekst wykonywania kontynuacji lub przekazać zadanie do innej komórki, a następnie wywołać metodę `task::then`, aby niejawnie kontrolować kontekst wykonywania.

> [!IMPORTANT]
> Ze względu na to, że główny wątek interfejsu użytkownika aplikacji platformy UWP działa w ramach STA, kontynuacje tworzone w ramach tego STA są domyślnie uruchamiane w STA. W związku z tym kontynuacje tworzone w ramach MTA działa w ramach MTA.

W poniższej sekcji przedstawiono aplikację, która odczytuje plik z dysku, znajduje najbardziej typowe słowa w tym pliku, a następnie wyświetla wyniki w interfejsie użytkownika. Operacja końcowa, która aktualizuje interfejs użytkownika, występuje w wątku interfejsu użytkownika.

> [!IMPORTANT]
> To zachowanie jest specyficzne dla aplikacji platformy UWP. W przypadku aplikacji klasycznych nie kontroluje się, gdzie działają kontynuacje. Zamiast tego harmonogram wybiera wątek roboczy, na którym ma zostać uruchomiona każda kontynuacja.

> [!IMPORTANT]
> Nie wywołuj [concurrency:: Task:: wait](reference/task-class.md#wait) w treści kontynuacji działającej w sta. W przeciwnym razie środowisko uruchomieniowe zgłasza [współbieżność:: invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) , ponieważ ta metoda blokuje bieżący wątek i może spowodować, że aplikacja przestanie odpowiadać. Można jednak wywołać metodę [concurrency:: Task:: Get](reference/task-class.md#get) , aby otrzymać wynik zadania poprzedzającego w kontynuacji opartej na zadaniach.

## <a name="example-app"></a>Przykład: kontrolowanie wykonywania w aplikacji środowisko wykonawcze systemu Windows z C++ i XAML

Rozważmy C++ aplikację XAML, która odczytuje plik z dysku, wyszukuje najbardziej typowe słowa w tym pliku, a następnie wyświetla wyniki w interfejsie użytkownika. Aby utworzyć tę aplikację, Uruchom w programie Visual Studio, tworząc **pustą aplikację (uniwersalną systemu Windows)** i nadając jej nazwę `CommonWords`. W manifeście aplikacji Określ możliwości **biblioteki dokumenty** , aby umożliwić aplikacji dostęp do folderu dokumentów. Dodaj także typ pliku tekstowego (. txt) do sekcji deklaracji manifestu aplikacji. Aby uzyskać więcej informacji na temat możliwości i deklaracji aplikacji, zobacz [pakowanie, wdrażanie i wykonywanie zapytań dotyczących aplikacji systemu Windows](/windows/win32/appxpkg/appx-portal).

Zaktualizuj element `Grid` w MainPage. XAML w celu uwzględnienia elementu `ProgressRing` i elementu `TextBlock`. `ProgressRing` wskazuje, że operacja jest w toku, a `TextBlock` pokazuje wyniki obliczenia.

[!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]

Dodaj następujące instrukcje `#include` do *PCH. h*.

[!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]

Dodaj następujące deklaracje metody do klasy `MainPage` (MainPage. h).

[!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]

Dodaj następujące instrukcje `using` do MainPage. cpp.

[!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]

W MainPage. cpp Zaimplementuj metody `MainPage::MakeWordList`, `MainPage::FindCommonWords`i `MainPage::ShowResults`. `MainPage::MakeWordList` i `MainPage::FindCommonWords` wykonują operacje obliczeniowe z dużym obciążeniem. Metoda `MainPage::ShowResults` wyświetla wynik obliczeń w interfejsie użytkownika.

[!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]

Zmodyfikuj konstruktora `MainPage`, aby utworzyć łańcuch zadań kontynuacji, które są wyświetlane w interfejsie użytkownika, w którym często występują słowa w książce *Iliad* przez stronę domową. Pierwsze dwa zadania kontynuacji, które dzielą tekst na poszczególne wyrazy i Znajdź typowe słowa, mogą być czasochłonne i dlatego jawnie ustawione na uruchamianie w tle. Końcowe zadanie kontynuacji, które aktualizuje interfejs użytkownika, określa brak kontekstu kontynuacji i w związku z tym następuje po wątkach reguł.

[!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]

> [!NOTE]
> W tym przykładzie pokazano, jak określić konteksty wykonywania i jak utworzyć łańcuch kontynuacji. Odwołaj to domyślnie zadanie, które jest tworzone na podstawie operacji asynchronicznej, uruchamia jego kontynuację w apartamentie o nazwie `task::then`. W związku z tym w tym przykładzie używa się `task_continuation_context::use_arbitrary`, aby określić, że operacje, które nie obejmują interfejsu użytkownika, są wykonywane w wątku w tle.

Na poniższej ilustracji przedstawiono wyniki aplikacji `CommonWords`.

![środowisko wykonawcze systemu Windows aplikacji CommonWords](../../parallel/concrt/media/concrt_windows_common_words.png "środowisko wykonawcze systemu Windows aplikacji CommonWords")

W tym przykładzie można obsługiwać anulowanie, ponieważ `task` obiekty obsługujące `create_async` używają niejawnego tokenu anulowania. Zdefiniuj funkcję roboczą, aby mieć obiekt `cancellation_token`, jeśli zadania muszą odpowiedzieć na anulowanie w sposób współdziałania. Aby uzyskać więcej informacji na temat anulowania w PPL, zobacz [Anulowanie w PPL](cancellation-in-the-ppl.md)

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)
