---
title: "Tworzenie operacji asynchronicznych w języku C++ dla aplikacji Windows 8.x | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
caps.latest.revision: "31"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 95e35564c759a5ede802f3e1377f64df7ccaab67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="creating-asynchronous-operations-in-c-for-windows-8x-apps"></a>Tworzenie operacji asynchronicznych w języku C++ dla aplikacji Windows 8.x
W tym dokumencie opisano niektóre z najważniejszych należy wziąć pod uwagę, gdy klasa zadanie służy do utworzenia puli wątków systemu Windows na podstawie operacji asynchronicznych w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji.  
  
 Korzystanie z programowanie asynchroniczne jest kluczowym czynnikiem [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] modelu aplikacji, ponieważ dzięki aplikacji będzie odbierać dane wejściowe użytkownika. Długotrwałe zadanie można uruchomić bez blokowania wątku interfejsu użytkownika i może odbierać wyniki zadanie później. Możesz również anulować zadania i otrzymywać powiadomienia o postępie jako zadania uruchomione w tle. Dokument [asynchronicznego programowania w języku C++](http://msdn.microsoft.com/library/windows/apps/hh780559.aspx) zawiera omówienie wzorca asynchronicznego, która jest dostępna w programie Visual C++ do tworzenia [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Ten dokument zawiera wskazówki jak korzystać z, a także tworzenie łańcuchów operacji asynchronicznych środowiska wykonawczego systemu Windows. W tej sekcji opisano sposób użycia typów w ppltasks.h do produkcji operacje asynchroniczne, które mogą być używane przez inny składnik środowiska wykonawczego systemu Windows i sterowanie jak zadanie asynchroniczne jest wykonywana. Należy również rozważyć odczytu [programowania asynchronicznego wzorców i porad w Hilo (aplikacje ze Sklepu Windows przy użyciu języka C++ i XAML)](http://msdn.microsoft.com/library/windows/apps/jj160321.aspx) Aby dowiedzieć się, jak użyliśmy klasy zadania do wykonania operacji asynchronicznych w Hilo, [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji przy użyciu języka C++ i języka XAML.  
  
> [!NOTE]
>  Można użyć [Biblioteka równoległych wzorców](../../parallel/concrt/parallel-patterns-library-ppl.md) (PLL) i [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Nie można jednak użyć harmonogramu zadań i Menedżera zasobów. Ten dokument zawiera opis dodatkowe funkcje, które zapewnia PPL, które są dostępne tylko dla [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji, a nie aplikacji komputerowej.  
  
## <a name="key-points"></a>Kwestie kluczowe  

-   Użyj [concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) można utworzyć operacji asynchronicznych, które mogą być używane przez inne składniki (które mogą być napisane w językach innych niż C++).  

  
-   Użyj [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) raportu postęp powiadomień do składników, które wywołanie asynchroniczne operacje.  
  
-   Umożliwia anulowanie tokenów włączyć wewnętrzny asynchronicznych operacji do anulowania.  
  
-   Zachowanie `create_async` funkcji zależy od zwracany typ funkcji pracy, która została przekazana do niej. Funkcja pracy, który zwraca klasę task (albo `task<T>` lub `task<void>`) jest uruchamiana synchronicznie, w tym kontekście, który wywołał `create_async`. Funkcja pracy, która zwraca `T` lub `void` działa w kontekście umownego.  
  
-   Można użyć [concurrency::task::then](reference/task-class.md#then) metodę w celu utworzenia łańcucha zadania uruchamiane jeden po drugim. W [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji, domyślny kontekst dla kontynuacje zadania zależy od sposobu został skonstruowany tego zadania. Jeśli zadania został utworzony przez przekazanie akcja asynchroniczna konstruktora zadań lub przez przekazanie wyrażenia lambda zwracającego akcja asynchroniczna, domyślny kontekst dla wszystkich kontynuacje tego zadania jest bieżącym kontekście. Jeśli zadanie nie jest utworzone na podstawie akcja asynchroniczna, dowolnego kontekst jest używany w domyślnie dla kontynuacje zadania. Można zastąpić domyślny kontekst z [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) klasy.  

  
## <a name="in-this-document"></a>W tym dokumencie  
  
-   [Tworzenie operacji asynchronicznych](#create-async)  
  
-   [Przykład: Tworzenie składnika C++ środowiska wykonawczego systemu Windows](#example-component)  
  
-   [Kontrolowanie wątku wykonawczego](#exethread)  
  
-   [Przykład: Kontrolowanie wykonywania w aplikacji ze Sklepu Windows z C++ i XAML](#example-app)  
  
##  <a name="create-async"></a>Tworzenie operacji asynchronicznych  
 Zadania i kontynuacji model można użyć w równoległych biblioteki wzorców (PLL) do definiowania zadania w tle, a także dodatkowe zadania, które będą uruchamiane po ukończeniu poprzedniego zadania. Ta funkcja jest zapewniana przez [concurrency::task](../../parallel/concrt/reference/task-class.md) klasy. Aby uzyskać więcej informacji na temat tego modelu i `task` , zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 Środowisko wykonawcze systemu Windows jest interfejs programowania, którego można używać do tworzenia [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacje, które są uruchamiane tylko w środowisku specjalne systemu operacyjnego. Takie aplikacje przy użyciu funkcji autoryzowanych, typy danych i urządzeń, a są dystrybuowane za pomocą [!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)]. Środowisko wykonawcze systemu Windows jest reprezentowana przez *binarny interfejsu aplikacji* (ABI). ABI jest podstawowej kontraktu binarny, który udostępnia języków programowania, takich jak Visual C++ interfejsów API środowiska wykonawczego systemu Windows.  
  
 Za pomocą środowiska wykonawczego systemu Windows, można skorzystać z najlepszych funkcji różnych języków programowania i połączyć je w jednej aplikacji. Na przykład możesz utworzyć interfejsu użytkownika w języku JavaScript i wykonywanie logiki aplikacji intensywnie praktyce w składnika C++. Do wykonania tych operacji praktyce intensywnie wykonujących operacje w tle jest kluczowym czynnikiem w zapewnieniu reakcji interfejsu użytkownika. Ponieważ `task` klasy jest specyficzne dla języka C++, należy użyć interfejsu środowiska wykonawczego systemu Windows do komunikowania się operacji asynchronicznych z innymi składnikami (które mogą być napisane w językach innych niż C++). Środowisko wykonawcze systemu Windows udostępnia cztery interfejsy, które służą do reprezentowania operacji asynchronicznych:  
  
 [Windows::Foundation::IAsyncAction](http://msdn.microsoft.com/library/windows/apps/windows.foundation.iasyncaction.aspx)  
 Reprezentuje akcję asynchroniczną.  
  
 [Windows::Foundation::IAsyncActionWithProgress\<TProgress >](http://msdn.microsoft.com/library/windows/apps/br206581.aspx)  
 Reprezentuje akcję asynchroniczną, która zgłasza postępu.  
  
 [Windows::Foundation::IAsyncOperation\<TResult >](http://msdn.microsoft.com/library/windows/apps/br206598.aspx)  
 Reprezentuje operację asynchroniczną, która zwraca wynik.  
  
 [Windows::Foundation::IAsyncOperationWithProgress\<TResult, TProgress >](http://msdn.microsoft.com/library/windows/apps/br206594.aspx)  
 Reprezentuje operację asynchroniczną, która zwraca wartość postępu wynik i raportów.  
  
 Pojęcia *akcji* oznacza, że zadanie asynchroniczne nie tworzy wartości (Pomyśl o funkcji, która zwraca `void`). Pojęcia *operacji* oznacza, że zadanie asynchroniczne uzyskiwania wartości. Pojęcia *postępu* oznacza, że zadanie może raportować komunikaty o postępie do obiektu wywołującego. JavaScript, .NET Framework i Visual C++ każdego zapewnia drodze do tworzenia wystąpień tych interfejsów do użytku w granicy ABI. W języku Visual C++, zapewnia PPL [concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) funkcji. Ta funkcja tworzy akcję asynchroniczną środowiska wykonawczego systemu Windows lub operacja, która reprezentuje wykonania zadania. `create_async` Funkcja przyjmuje funkcję pracy (zazwyczaj Wyrażenie lambda), wewnętrznie tworzy `task` obiekt i zawija, które zadania w jednej z czterech asynchroniczne interfejsy środowiska wykonawczego systemu Windows.  
  
> [!NOTE]
>  Użyj `create_async` tylko kiedy należy utworzyć funkcje, które są dostępne z innego języka lub innego składnika środowiska wykonawczego systemu Windows. Użyj `task` klasy bezpośrednio, gdy wiesz, czy operacji jest tworzone i używane przez kod w języku C++ w tym samym składnikiem.  
  
 Zwracany typ `create_async` jest określana przez typ argumentów. Na przykład, jeśli funkcja pracy nie może zwracać wartości i nie raportu postępu `create_async` zwraca `IAsyncAction`. Jeśli funkcja pracy nie może zwracać wartości i udostępnia również postępu, `create_async` zwraca `IAsyncActionWithProgress`. Aby zgłosić postępu, podaj [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) obiektu jako parametr do funkcji pracy. Możliwość raportowania postępu umożliwia raport jakie ilość pracy zostało wykonane i jakie ilość nadal pozostaje (na przykład w procentach). Można również do raportu dotyczącego wyników, gdy będą one dostępne.  
  
 `IAsyncAction`, `IAsyncActionWithProgress<TProgress>`, `IAsyncOperation<TResult>`, I `IAsyncActionOperationWithProgress<TProgress, TProgress>` Podaj interfejsy każdego `Cancel` metodę, która pozwala anulować operację asynchroniczną. `task` Klasy współpracuje z anulowanie tokenów. Gdy używasz token anulowania do anulowania pracy środowiska uruchomieniowego nie można uruchomić nowej pracy, które subskrybuje tokenu. Pracy, który jest już aktywny można monitorować jego token anulowania i Zatrzymaj, gdy mogą go. Ten mechanizm jest opisany bardziej szczegółowo w dokumencie [anulowanie w PPL](cancellation-in-the-ppl.md). Anulowanie zadania mogą łączyć się z środowiska uruchomieniowego systemu Windows`Cancel` metod na dwa sposoby. Po pierwsze można zdefiniować funkcja pracy, który jest przekazywany do `create_async` podjęcie [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) obiektu. Gdy `Cancel` metoda jest wywoływana, ten token anulowania zostało anulowane i dotyczą podstawowych reguły normalne anulowania `task` obiekt, który obsługuje `create_async` wywołania. Jeśli nie podasz `cancellation_token` obiektu odpowiadającego `task` obiekt definiuje jedną niejawnie. Zdefiniuj `cancellation_token` obiektu, gdy trzeba wspólnie odpowiadanie na anulowanie w funkcji pracy. Sekcja [przykład: kontrolowanie wykonywania w aplikacji ze Sklepu Windows z C++ i XAML](#example-app) przedstawiono przykład sposobu wykonywania anulowanie w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji przy użyciu języka C# i języka XAML, która używa niestandardowych składników C++ środowiska wykonawczego systemu Windows.  
  
> [!WARNING]
>  W łańcuchu kontynuacje zadań, zawsze Wyczyść stan, a następnie wywołać [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) gdy token anulowania zostało anulowane. Jeśli wcześniej zamiast wywoływać metodę `cancel_current_task`, operacji przejścia do stanu ukończenia zamiast stan anulowane.  

  
 W poniższej tabeli przedstawiono kombinacje, które służy do definiowania asynchronicznych operacji w aplikacji.  
  
|Aby utworzyć ten interfejs środowiska uruchomieniowego systemu Windows|Zwraca tego typu z`create_async`|Przekaż te typy parametrów do funkcji z pracy, należy użyć token anulowania niejawne|Przekaż te typy parametrów do funkcji z pracy, należy użyć token anulowania jawne|  
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|  
|`IAsyncAction`|`void`lub`task<void>`|(Brak)|(`cancellation_token`)|  
|`IAsyncActionWithProgress<TProgress>`|`void`lub`task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|  
|`IAsyncOperation<TResult>`|`T`lub`task<T>`|(Brak)|(`cancellation_token`)|  
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T`lub`task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|  
  
 Może zwracać wartość lub `task` obiektu z funkcji pracy, który jest przekazywany do `create_async` funkcji. Różnice te utworzyć różne zachowania. Po powrocie wartość funkcja pracy jest ujęte w `task` , dzięki czemu mogą być uruchamiane w wątku tła. Oprócz podstawowych `task` używa tokenu niejawne anulowania. Z drugiej strony Jeśli `task` obiektu, funkcja pracy uruchamiane synchronicznie. W związku z tym jeśli `task` obiektów, upewnij się, że wszystkie operacje długich w funkcji pracy również uruchomić jako zadania do włączenia aplikacji będzie odpowiadać. Oprócz podstawowych `task` nie korzysta z tokenem anulowania niejawne. W związku z tym należy zdefiniować funkcję Twojej pracy `cancellation_token` obiektu, jeśli wymagana jest obsługa anulowania po powrocie `task` obiekt z `create_async`.  
  
 W poniższym przykładzie przedstawiono różne sposoby tworzenia `IAsyncAction` obiekt, który może być zużyte przez inny składnik środowiska wykonawczego systemu Windows.  
  
 [!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]  
  
##  <a name="example-component"></a>Przykład: Tworzenie składnika C++ środowiska wykonawczego systemu Windows i używania go w języku C#  
 Należy wziąć pod uwagę aplikację, która używa języka XAML i C# w celu zdefiniowania interfejsu użytkownika i składnika C++ środowiska wykonawczego systemu Windows do wykonywania operacji obliczeniowych. W tym przykładzie składnika C++ oblicza, które numery w danym zakresie są pierwsze. Aby zilustrować różnice między cztery interfejsy zadanie asynchroniczne środowiska wykonawczego systemu Windows, uruchom, w programie Visual Studio, tworząc **puste rozwiązanie** i nazw `Primes`. Następnie dodaj do rozwiązania **składnika środowiska wykonawczego systemu Windows** projektu i nazw `PrimesLibrary`. Dodaj następujący kod do wygenerowanego pliku nagłówka C++ (w tym przykładzie zmienia nazwę Class1.h na Primes.h). Każdy `public` Metoda określa jeden z czterech interfejsów asynchronicznego. Metody, które zwracają wartości zwracają [Windows::Foundation::Collections::IVector\<int >](http://msdn.microsoft.com/library/windows/apps/br206631.aspx) obiektu. Utworzyć raportu postępu metody `double` wartości, które definiują procent ogólnej pracy, które zostało zakończone.  
  
 [!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]  
  
> [!NOTE]
>  Według Konwencji nazwy metod asynchronicznych w środowisku wykonawczym systemu Windows jest zwykle kończyć się "Async".  
  
 Dodaj następujący kod do wygenerowanego pliku źródłowego C++ (w tym przykładzie zmienia nazwę Class1.cpp na Primes.cpp). `is_prime` Funkcji określa, czy jego danych wejściowych jest pierwsze. Implementowanie pozostałe metody `Primes` klasy. Każde wywołanie `create_async` używa podpisie, który jest zgodny z metodą, z którego jest wywoływana. Na przykład ponieważ `Primes::ComputePrimesAsync` zwraca `IAsyncAction`, funkcja pracy, który został dostarczony do `create_async` nie może zwracać wartości i nie przyjmuje `progress_reporter` obiektu jako jego parametr.  
  
 [!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]  
  
 Każda metoda najpierw jest przeprowadzane weryfikacji, aby upewnić się, że parametry wejściowe czy nieujemną. Jeśli wartości wejściowej jest ujemna, metoda wygeneruje [Platform::InvalidArgumentException](http://msdn.microsoft.com/library/windows/apps/hh755794\(v=vs.110\).aspx). Obsługa błędów później opisanej w tej sekcji.  
  
 Aby korzystać z tych metod z [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji, użyj programu Visual C# **pusta aplikacja (XAML)** szablonu, aby dodać drugi projektu do rozwiązania Visual Studio. W tym przykładzie nazwy projektu `Primes`. Następnie z `Primes` projekt, Dodaj odwołanie do `PrimesLibrary` projektu.  
  
 Dodaj następujący kod do MainPage.xaml. Ten kod definiuje interfejsu użytkownika, dzięki czemu można wywołać składnika C++ i wyświetlić wyniki.  
  
 [!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]  
  
 Dodaj następujący kod do `MainPage` klasy w MainPage.xaml. Ten kod definiuje `Primes` obiekt i przycisk obsługi zdarzeń.  
  
 [!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]  
  
 Użyj tych metod `async` i `await` słowa kluczowe można zaktualizować interfejsu użytkownika po zakończeniu operacji asynchronicznych. Aby uzyskać informacje o wzorce asynchroniczne, które są dostępne dla C# i Visual Basic, zobacz [wzorców asynchronicznych w aplikacjach Sklepu Windows w języku C#](http://msdn.microsoft.com/library/windows/apps/hh464924.aspx) i [wzorców asynchronicznych w aplikacjach Sklepu Windows z VB](http://msdn.microsoft.com/library/windows/apps/hh464924.aspx).  
  
 `getPrimesCancellation` i `cancelGetPrimes` metody współdziałać, aby umożliwić użytkownikowi anulować operację. Gdy użytkownik wybierze **anulować** przycisku `cancelGetPrimes` wywołania metody [IAsyncOperationWithProgress\<TResult, TProgress >:: anulować](http://msdn.microsoft.com/library/windows/apps/windows.foundation.iasyncinfo.cancel.aspx) Aby anulować operację. Współbieżność środowiska wykonawczego, która zarządza podstawowym operację asynchroniczną, zgłasza typu wewnętrzny wyjątek, który zostanie przechwycony przez środowisko wykonawcze systemu Windows do komunikowania się, że ukończono anulowania. Aby uzyskać więcej informacji na temat modelu anulowania, zobacz [anulowania](../../parallel/concrt/cancellation-in-the-ppl.md).  
  
> [!IMPORTANT]
>  Aby włączyć PPL poprawnie zgłoszenia do środowiska wykonawczego systemu Windows czy anulował operację, nie Przechwytuj ten typ wyjątku wewnętrznego. Oznacza to, czy też nie należy przechwytywać wszystkie wyjątki (`catch (...)`). Jeśli należy przechwytywać wszystkie wyjątki, było ponownie zgłosić wyjątek, aby upewnić się, że środowiska uruchomieniowego systemu Windows może zakończyć operacji anulowania.  
  
 Na poniższej ilustracji pokazano `Primes` aplikacji po każdej opcji została wybrana.  
  
 ![Aplikacja blokad Sklepu Windows](../../parallel/concrt/media/concrt_windows_primes.png "concrt_windows_primes")  
  
 Przykłady, które używają `create_async` można utworzyć zadania asynchroniczne, które mogą być używane przez inne języki, zobacz [przy użyciu języka C++ w przykładowym Optymalizator podróży mapy Bing](http://msdn.microsoft.com/library/windows/apps/hh699891\(v=vs.110\).aspx) i [systemu Windows 8 operacji asynchronicznych w języku C++ z PPL](http://code.msdn.microsoft.com/windowsapps/windows-8-asynchronous-08009a0d).  
  
##  <a name="exethread"></a>Kontrolowanie wątku wykonawczego  
 Środowisko wykonawcze systemu Windows używa modelu COM, model wątkowości. W tym modelu obiektów znajdują się w różnych apartamentach, w zależności od sposobu ich obsługi ich synchronizacji. Obiekty wątkowo znajdują się w wielowątkowej (MTA). Obiekty, które muszą być dostępne przez pojedynczy wątek znajdują się w jednowątkowego apartamentu (STA).  
  
 W aplikacji, która ma interfejsu użytkownika wątek ASTA (STA aplikacji) jest odpowiedzialny za przekazywanie komunikatów okien i tylko wątku w procesie, który umożliwia zaktualizowanie hostowanej STA interfejsu użytkownika. Ma to wpływ dwa. Najpierw aby umożliwić aplikacji będzie odpowiadać, wszystkie operacje We/Wy i użycie Procesora CPU nie powinien być uruchamiany w wątku ASTA. Po drugie wyniki, które pochodzą od wątki w tle musi być organizowany do ASTA można zaktualizować interfejsu użytkownika. W języku C++ [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji, `MainPage` i inne strony XAML wszystkie uruchomione na ATSA. W związku z tym kontynuacje zadań, które są zadeklarowane na ASTA są uruchamiane istnieje domyślnie, możesz zaktualizować formantów bezpośrednio w treści kontynuacji. Zagnieździć zadań w zadaniu innym, wszelkie kontynuacje w tym zadaniu zagnieżdżonych uruchamiać w MTA. W związku z tym należy wziąć pod uwagę, czy jawnie określać, na jakie kontekstu Uruchom te kontynuacje.  
  
 Zadanie, które jest tworzony z operację asynchroniczną, takich jak `IAsyncOperation<TResult>`, używa semantyki specjalne, które mogą pomóc Ci Ignoruj wątkowości szczegóły. Mimo że operacji mogą być uruchamiane w wątku w tle (lub go może nie była obsługiwana przez wątek w ogóle), jego kontynuacje są domyślnie działanie w apartamencie rozpoczęcia operacji kontynuacji (innymi słowy, z typu apartment, który wywołał `task::then`). Można użyć [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) klasy do kontrolowania kontekstu wykonywania utrzymania. Służy do tworzenia tych metod statycznych Pomocnika `task_continuation_context` obiektów:  
  
-   Użyj [concurrency::task_continuation_context::use_arbitrary](reference/task-continuation-context-class.md#use_arbitrary) do określenia, że kontynuowanie zostanie uruchomiona w wątku w tle.  
  
-   Użyj [concurrency::task_continuation_context::use_current](reference/task-continuation-context-class.md#use_current) do określenia, że kontynuowanie zostanie uruchomiona w wątku, który wywołał `task::then`.  

  
 Można przekazać `task_continuation_context` do obiektu [task::then](reference/task-class.md#then) metody kontrolowania jawnie kontekstu wykonywania można również kontynuacji można przekazać zadania do innego typu apartment, a następnie wywołać `task::then` metody kontrolowania niejawnie Kontekst wykonywania.  
  
> [!IMPORTANT]
>  Ponieważ głównym wątku interfejsu użytkownika [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji uruchamiana STA, kontynuacje utworzonych na tym STA domyślnie uruchamiane na pozostaje tryb komórek jednowątkowych W związku z tym kontynuacje utworzonych na MTA Uruchom na MTA.  
  
 W tej części opisano aplikację, która odczytuje plik z dysku, znajduje najbardziej popularnych wyrazów w tym pliku, a następnie przedstawia wyniki w interfejsie użytkownika. Ostatniej operacji aktualizowania interfejsu użytkownika występuje w wątku interfejsu użytkownika.  
  
> [!IMPORTANT]
>  Dotyczy to zachowanie [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Dla aplikacji klasycznych nie kontroli, której kontynuacje jest uruchomiony. Zamiast tego harmonogramu wybiera wątku roboczego uruchomienia każdej kontynuacji.  
  
> [!IMPORTANT]

>  Nie wywołuj [concurrency::task::wait](reference/task-class.md#wait) w treści utrzymania uruchamianego na pozostaje tryb komórek jednowątkowych W przeciwnym razie zwraca środowiska uruchomieniowego [concurrency::invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) , ponieważ ta metoda umożliwia blokowanie bieżącego wątku i może spowodować, że aplikacja przestanie odpowiadać. Jednak możesz wywołać [concurrency::task::get](reference/task-class.md#get) metodę, aby odbierać wynik zadania poprzedzających kontynuację opartego na zadaniach.  
  
##  <a name="example-app"></a>Przykład: Kontrolowanie wykonywania w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji za pomocą języka C++ i XAML  
 Należy wziąć pod uwagę aplikacji C++ XAML, która odczytuje plik z dysku, znajduje najbardziej popularnych wyrazów w tym pliku, a następnie przedstawia wyniki w interfejsie użytkownika. Aby utworzyć tę aplikację, uruchomić, w programie Visual Studio, tworząc [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] **pusta aplikacja (XAML)** projektu i nazw `CommonWords`. W manifeście aplikacji, należy określić **biblioteki dokumentów** możliwości, aby umożliwić aplikacji dostęp do folderu dokumenty. Typ pliku tekstowego (.txt) należy również dodać do sekcji deklaracji w manifeście aplikacji. Aby uzyskać więcej informacji na temat możliwości aplikacji i deklaracje, zobacz [pakietów aplikacji i wdrażania](http://msdn.microsoft.com/library/windows/apps/hh464929.aspx).  
  
 Aktualizacja `Grid` element MainPage.xaml, aby uwzględnić `ProgressRing` elementu i `TextBlock` elementu. `ProgressRing` Wskazuje, że operacja jest w toku i `TextBlock` pokazuje wyniki obliczenia.  
  
 [!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]  
  
 Dodaj następujące `#include` instrukcje pch.h.  
  
 [!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]  
  
 Dodaj następujące deklaracje metody `MainPage` klasy (MainPage.h).  
  
 [!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]  
  
 Dodaj następujące `using` instrukcje MainPage.cpp.  
  
 [!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]  
  
 W MainPage.cpp, należy zaimplementować `MainPage::MakeWordList`, `MainPage::FindCommonWords`, i `MainPage::ShowResults` metody. `MainPage::MakeWordList` i `MainPage::FindCommonWords` praktyce intensywnie operacji. `MainPage::ShowResults` Metoda wyświetla wynik obliczenia w interfejsie użytkownika.  
  
 [!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]  
  
 Modyfikowanie `MainPage` konstruktora, aby utworzyć łańcuch zadań kontynuacji wyświetlana w interfejsie użytkownika popularnych wyrazów w książce *Iliad* przez Homer. Pierwszego zadania kontynuacji dwa, które podział tekstu w poszczególnych wyrazów i znaleźć popularnych wyrazów, może być czasochłonne i w związku z tym są jawnie ustawione na uruchamianie w tle. Zadania kontynuacji końcowego, które aktualizacje interfejsu użytkownika, określa brak kontekstu kontynuacji, a w związku z powyższym wątków reguły.  
  
 [!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]  
  
> [!NOTE]
>  W tym przykładzie przedstawiono sposób określania kontekstów wykonywania oraz utworzenie łańcucha kontynuacje. Odwołaj, że domyślnie jest tworzona na podstawie operacji asynchronicznej uruchomieniu zadania jego kontynuacje na apartamentu, który wywołał `task::then`. W tym przykładzie użyto `task_continuation_context::use_arbitrary` do określenia, czy można wykonać operacji, które nie wymagają interfejsu użytkownika wątku w tle.  
  
 Na poniższej ilustracji przedstawiono wyniki `CommonWords` aplikacji.  
  
 ![Aplikacja CommonWords Sklepu Windows](../../parallel/concrt/media/concrt_windows_common_words.png "concrt_windows_common_words")  
  
 W tym przykładzie, istnieje możliwość anulowania obsługi, ponieważ `task` obiekty obsługujące `create_async` Użyj tokenu niejawne anulowania. Definiowanie funkcji pracy podjęcie `cancellation_token` obiekt zadań muszą odpowiadać na anulowanie w sposób współpracy. Aby uzyskać więcej informacji na temat anulowanie w PPL, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność środowiska wykonawczego](../../parallel/concrt/concurrency-runtime.md)
