---
title: Wielowątkowość z językiem C i podsystemem Win32
ms.date: 08/09/2019
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
ms.openlocfilehash: 1764561e0b2b43b8a89d8a1eb2e85d84ce33c4fc
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141967"
---
# <a name="multithreading-with-c-and-win32"></a>Wielowątkowość z językiem C i podsystemem Win32

Kompilator Microsoft C/C++ COMPILER (MSVC) zapewnia obsługę tworzenia aplikacji wielowątkowej. Rozważ użycie więcej niż jednego wątku, jeśli aplikacja wymaga wykonywania kosztownych operacji, które mogłyby spowodować, że interfejs użytkownika przestanie odpowiadać.

W programie MSVC istnieje kilka sposobów programowania z wieloma wątkami: można użyć C++/WinRT i biblioteki środowisko wykonawcze systemu Windows, biblioteki Microsoft Foundation Class (MFC), C++/CLI i środowiska uruchomieniowego platformy .NET albo biblioteki wykonawczej C i Win32 API. Ten artykuł dotyczy wielowątkowości w języku C. Na przykład kod, zobacz [Przykładowy program wielowątkowej w języku C](sample-multithread-c-program.md).

## <a name="multithread-programs"></a>Programy wielowątkowe

Wątek jest w zasadzie ścieżką wykonania za pomocą programu. Jest to również najmniejsza jednostka wykonywania, która ma harmonogram Win32. Wątek składa się ze stosu, stanu rejestrów procesora i wpisu na liście wykonywania harmonogramu systemu. Każdy wątek udostępnia wszystkie zasoby tego procesu.

Proces składa się z co najmniej jednego wątku oraz kodu, danych i innych zasobów programu w pamięci. Typowe zasoby programu to otwarte pliki, semafory i dynamicznie przydzieloną pamięć. Program jest wykonywany, gdy harmonogram systemu udostępnia jedną z formantów wykonywania wątków. Harmonogram określa, które wątki powinny być uruchamiane i kiedy powinny być uruchamiane. Wątki o niższym priorytecie mogą wymagać oczekiwania na ukończenie zadań przez wątki o wyższym priorytecie. Na maszynach wieloprocesorowych harmonogram może przenosić poszczególne wątki do różnych procesorów, aby zrównoważyć obciążenie procesora CPU.

Każdy wątek w procesie działa niezależnie. O ile nie zostaną one widoczne dla siebie, wątki są wykonywane pojedynczo i nie wiedzą o innych wątkach w procesie. Wątki udostępniające wspólne zasoby, jednak muszą koordynować swoją służbę przy użyciu semaforów lub innej metody komunikacji międzyprocesowej. Aby uzyskać więcej informacji na temat synchronizowania wątków, zobacz [pisanie wielowątkowego programu Win32](#writing-a-multithreaded-win32-program).

## <a name="library-support-for-multithreading"></a>Obsługa bibliotek na potrzeby wielowątkowości

Wszystkie wersje CRT obsługują teraz wielowątkowość, z wyjątkiem wersji bez blokowania niektórych funkcji. Aby uzyskać więcej informacji, zobacz temat [wydajność bibliotek wielowątkowych](../c-runtime-library/multithreaded-libraries-performance.md). Aby uzyskać informacje o wersjach platformy CRT dostępnych do łączenia z kodem, zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md).

## <a name="include-files-for-multithreading"></a>Uwzględnianie plików na potrzeby wielowątkowości

Standardowe pliki dołączone do CRT deklarują funkcje biblioteki wykonawczej C, które są implementowane w bibliotekach. Jeśli opcje kompilatora określają [__fastcall lub __vectorcall](../build/reference/gd-gr-gv-gz-calling-convention.md) konwencji wywoływania, kompilator zakłada, że wszystkie funkcje powinny być wywoływane przy użyciu konwencji wywoływania rejestru. Funkcje biblioteki wykonawczej używają konwencji wywoływania języka C, a deklaracje w standardowych plikach dołączanych informują kompilator, aby generował poprawne odwołania zewnętrzne do tych funkcji.

## <a name="crt-functions-for-thread-control"></a>Funkcje CRT dla kontrolki wątku

Wszystkie programy Win32 mają co najmniej jeden wątek. Dowolny wątek może tworzyć dodatkowe wątki. Wątek może szybko zakończyć pracę, a następnie zakończyć działanie lub może pozostać aktywny przez cały czas trwania programu.

Biblioteki CRT udostępniają następujące funkcje tworzenia i kończenia wątków: [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md), [_endthread i _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md).

Funkcje `_beginthread` i `_beginthreadex` tworzą nowy wątek i zwracają identyfikator wątku, jeśli operacja zakończyła się pomyślnie. Wątek kończy się automatycznie po zakończeniu wykonywania. Może też kończyć się wywołaniem do `_endthread` lub `_endthreadex`.

> [!NOTE]
> Jeśli wywołasz procedury czasu wykonywania języka C z programu skompilowanego za pomocą libcmt. lib, musisz uruchomić wątki z funkcją `_beginthread` lub `_beginthreadex`. Nie należy używać funkcji Win32 `ExitThread` i `CreateThread`. Używanie `SuspendThread` może prowadzić do zakleszczenia, gdy więcej niż jeden wątek zostanie zablokowany, czekając na ukończenie zawieszonego wątku, aby zakończyć dostęp do struktury danych w czasie wykonywania C.

### <a name="_core_the__beginthread_function"></a>Funkcje _beginthread i _beginthreadex

Funkcje `_beginthread` i `_beginthreadex` tworzą nowy wątek. Wątek współużytkuje kod i segmenty danych procesu z innymi wątkami w procesie, ale ma własne unikatowe wartości rejestru, przestrzeń stosu i bieżący adres instrukcji. System przekazuje czas procesora CPU do każdego wątku, dzięki czemu wszystkie wątki w procesie mogą być wykonywane współbieżnie.

`_beginthread` i `_beginthreadex` są podobne [do funkcji myFunction w Win32 API, ale](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) zawierają następujące różnice:

- Inicjują pewne zmienne biblioteki wykonawczej C. Jest to istotne tylko w przypadku używania biblioteki wykonawczej C w wątkach.

- `CreateThread` pomaga zapewnić kontrolę nad atrybutami zabezpieczeń. Za pomocą tej funkcji można uruchomić wątek w stanie wstrzymania.

`_beginthread` i `_beginthreadex` zwracać dojście do nowego wątku, jeśli wystąpił błąd lub kod błędu.

### <a name="_core_the__endthread_function"></a>Funkcje _endthread i _endthreadex

Funkcja [_endthread](../c-runtime-library/reference/endthread-endthreadex.md) przerywa wątek utworzony przez `_beginthread` (i podobnie `_endthreadex` kończy wątek utworzony przez `_beginthreadex`). Wątki kończą się automatycznie po zakończeniu. `_endthread` i `_endthreadex` są przydatne dla warunkowego zakończenia z poziomu wątku. Wątek przeznaczony do przetwarzania komunikacji, na przykład, może zakończyć się, jeśli nie jest w stanie uzyskać kontroli nad portem komunikacyjnym.

## <a name="writing-a-multithreaded-win32-program"></a>Pisanie wielowątkowego programu Win32

Podczas pisania programu z wieloma wątkami należy koordynować zachowanie i [korzystać z zasobów programu](#_core_sharing_common_resources_between_threads). Upewnij się również, że każdy wątek otrzymuje [swój własny stos](#_core_thread_stacks).

### <a name="_core_sharing_common_resources_between_threads"></a>Udostępnianie wspólnych zasobów między wątkami

> [!NOTE]
> Aby poznać podobną dyskusję z punktu widzenia MFC, zobacz [wielowątkowość: porady dotyczące programowania](multithreading-programming-tips.md) i [wielowątkowość: Kiedy używać klas synchronizacji](multithreading-when-to-use-the-synchronization-classes.md).

Każdy wątek ma własny stos i własną kopię rejestrów procesora. Inne zasoby, takie jak pliki, dane statyczne i pamięć sterty, są współużytkowane przez wszystkie wątki w procesie. Wątki korzystające z tych typowych zasobów muszą być zsynchronizowane. Win32 oferuje kilka sposobów synchronizowania zasobów, w tym semaforów, sekcji krytycznych, zdarzeń i muteksów.

Gdy wiele wątków uzyskuje dostęp do danych statycznych, program musi zapewnić potencjalne konflikty zasobów. Weź pod uwagę program, w którym jeden wątek aktualizuje statyczną strukturę danych zawierającą współrzędne *x*,*y* dla elementów, które mają być wyświetlane przez inny wątek. Jeśli wątek aktualizacji modyfikuje współrzędną *x* i jest zastępują przed zmianą współrzędną *y* , wątek wyświetlania może być zaplanowany przed aktualizacją współrzędną *y* . Element będzie wyświetlany w niewłaściwej lokalizacji. Można uniknąć tego problemu, korzystając z semaforów do kontrolowania dostępu do struktury.

Element mutex (Short for *Mut*rejestrowania dostępu użytkowników *ex*clusion) jest sposobem komunikacji między wątkami lub procesami, które są wykonywane asynchronicznie. Ta komunikacja może służyć do koordynowania działań wielu wątków lub procesów, zwykle przez kontrolowanie dostępu do udostępnionego zasobu przez zablokowanie i odblokowanie zasobu. Aby rozwiązać ten problem z aktualizacją współrzędnej *x* *,, wątek* aktualizacji ustawia element mutex wskazujący, że struktura danych jest używana przed wykonaniem aktualizacji. Spowoduje to wyczyszczenie obiektu mutex po przetworzeniu obu współrzędnych. Wątek wyświetlania musi czekać na wyczyszczenie obiektu mutex przed zaktualizowaniem ekranu. Ten proces czekania na element mutex jest często nazywany *blokowaniem* obiektu mutex, ponieważ proces jest zablokowany i nie można kontynuować do momentu wyczyszczenia elementu mutex.

Program odbijający. c przedstawiony w [przykładowym programie wielowątkowej c](sample-multithread-c-program.md) używa obiektu mutex o nazwie `ScreenMutex` do koordynowania aktualizacji ekranu. Za każdym razem, gdy jeden z wątków wyświetlania jest gotowy do zapisu na ekranie, wywołuje `WaitForSingleObject` z dojściem, aby `ScreenMutex` i stała NIESKOŃCZONość, aby wskazać, że wywołanie `WaitForSingleObject` powinno blokować element mutex i nie przekroczyć limitu czasu. Jeśli `ScreenMutex` jest jasne, funkcja oczekiwania ustawia element mutex, tak aby inne wątki nie zakłócają wyświetlania i kontynuują wykonywanie wątku. W przeciwnym razie bloki wątku do momentu wyczyszczenia elementu mutex. Gdy wątek ukończy aktualizację wyświetlania, zwalnia mutex, wywołując `ReleaseMutex`.

Wyświetla ekran i dane statyczne są tylko dwa zasoby wymagające dokładnego zarządzania. Na przykład program może mieć wiele wątków uzyskujących dostęp do tego samego pliku. Ponieważ inny wątek mógł przenieść wskaźnik pliku, każdy wątek musi zresetować wskaźnik pliku przed odczytem lub zapisem. Ponadto każdy wątek musi upewnić się, że nie jest zastępujący między czasem umieszcza wskaźnik i czas, w którym uzyskuje dostęp do pliku. Te wątki powinny używać semafora, aby koordynować dostęp do pliku przez przenawiasy klamrowe każdego dostępu do pliku przy użyciu `WaitForSingleObject` i `ReleaseMutex` wywołań. Poniższy przykład kodu ilustruje tę technikę:

```C
HANDLE    hIOMutex = CreateMutex (NULL, FALSE, NULL);

WaitForSingleObject( hIOMutex, INFINITE );
fseek( fp, desired_position, 0L );
fwrite( data, sizeof( data ), 1, fp );
ReleaseMutex( hIOMutex);
```

### <a name="_core_thread_stacks"></a>Stosy wątków

Cała domyślna przestrzeń stosu aplikacji jest przypisana do pierwszego wątku wykonywania, który jest znany jako wątek 1. W związku z tym należy określić ilość pamięci do przydzielenia dla oddzielnego stosu dla każdego dodatkowego wątku wymaganego przez program. System operacyjny przydziela dodatkową przestrzeń stosu dla wątku, w razie potrzeby, ale należy określić wartość domyślną.

Pierwszy argument w wywołaniu `_beginthread` jest wskaźnikiem do funkcji `BounceProc`, która wykonuje wątki. Drugi argument określa domyślny rozmiar stosu dla wątku. Ostatni argument jest numerem identyfikatora, który jest przesyłany do `BounceProc`. `BounceProc` używa numeru IDENTYFIKACYJNego do wypełniania generatora liczb losowych i wybierania atrybutu koloru wątku oraz znaku wyświetlania.

Wątki, które tworzą wywołania do biblioteki wykonawczej C lub do Win32 API muszą zezwalać na wystarczającą ilość miejsca na stosie wywoływanych przez funkcje biblioteki i interfejsu API. Funkcja C `printf` wymaga więcej niż 500 bajtów przestrzeni stosu, a podczas wywoływania procedur Win32 API powinny być dostępne 2Ke bajty przestrzeni stosu.

Ponieważ każdy wątek ma swój własny stos, można uniknąć potencjalnych kolizji dla elementów danych przy użyciu możliwie najmniejszej ilości danych statycznych. Zaprojektuj program do używania automatycznych zmiennych stosu dla wszystkich danych, które mogą być prywatne w wątku. Jedyne zmienne globalne w programie odbijania. c są to muteksy lub zmienne, które nigdy nie zmieniają się po zainicjowaniu.

Win32 udostępnia również magazyn wątków lokalnych (TLS) do przechowywania danych dla każdego wątku. Aby uzyskać więcej informacji, zobacz [lokalny magazyn wątków (TLS)](thread-local-storage-tls.md).

## <a name="avoiding-problem-areas-with-multithread-programs"></a>Unikanie obszarów problemów z programami wielowątkowymi

Istnieje kilka problemów, które mogą wystąpić podczas tworzenia, łączenia lub wykonywania programu wielowątkowej języka C. Niektóre z tych typowych problemów opisano w poniższej tabeli. (W przypadku podobnej dyskusji z punktu widzenia MFC zobacz [wielowątkowość: porady dotyczące programowania](multithreading-programming-tips.md)).

|Problem|Prawdopodobna przyczyna|
|-------------|--------------------|
|Zostanie wyświetlone okno komunikatu z informacją, że program spowodował naruszenie ochrony.|Wiele błędów programowania Win32 powoduje naruszenia ochrony. Typową przyczyną naruszeń ochrony jest pośrednie przypisanie danych do wskaźników o wartości null. Ze względu na to, że program próbuje uzyskać dostęp do pamięci, która nie należy do niej, zostanie wygenerowane naruszenie ochrony.<br /><br /> Łatwym sposobem wykrywania przyczyn naruszenia ochrony jest skompilowanie programu z informacjami o debugowaniu, a następnie uruchomienie go za pomocą debugera w środowisku programu Visual Studio. Po wystąpieniu błędu ochrony system Windows przesyła sterowanie do debugera, a kursor jest umieszczony w wierszu, który spowodował problem.|
|Program generuje liczne błędy kompilacji i łącza.|Aby wyeliminować wiele potencjalnych problemów, należy ustawić poziom ostrzeżeń kompilatora na jedną z największych wartości i Heeding komunikaty ostrzegawcze. Korzystając z opcji poziomu ostrzeżeń poziomu 3 lub 4, można wykryć niezamierzone konwersje danych, brakujące prototypy funkcji i korzystać z funkcji innych niż ANSI.|

## <a name="see-also"></a>Zobacz też

[Obsługa wielowątkowości dla starszego kodu (wizualizacja C++)](multithreading-support-for-older-code-visual-cpp.md)\
[Przykładowy program wielowątkowej w języku C](sample-multithread-c-program.md)\
\ [lokalnego magazynu wątków](thread-local-storage-tls.md)
[Operacje współbieżności i asynchroniczności C++z/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency)\
[Wielowątkowość z C++ i MFC](multithreading-with-cpp-and-mfc.md)
