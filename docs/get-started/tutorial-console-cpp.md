---
title: Tworzenie kalkulatora konsoli w C++
description: Tworzenie aplikacji konsolowej Hello world i aplikacji Kalkulator w programie Visual C++
ms.custom: mvc
ms.date: 08/19/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 5f448e68878e211969c89f7c4c750e3231d3a9b7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230587"
---
# <a name="create-a-console-calculator-in-c"></a>Tworzenie kalkulatora konsoli w C++

::: moniker range=">=vs-2019"

Typowym punktem wyjścia dla programisty języka C++ jest "Hello, World!" aplikacja uruchamiana w wierszu polecenia. To właśnie utworzysz w programie Visual Studio w tym artykule, a następnie przejdziemy do bardziej trudnej: aplikacji Kalkulator.

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio z **programowaniem dla komputerów stacjonarnych z** zainstalowanym i uruchomionym obciążeniem języka C++. Jeśli nie jest jeszcze zainstalowana, zobacz [Install C++ Support in Visual Studio](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Tworzenie projektu aplikacji

Program Visual Studio używa *projektów* do organizowania kodu aplikacji oraz *rozwiązań* do organizowania projektów. Projekt zawiera wszystkie opcje, konfiguracje i reguły używane do kompilowania aplikacji. Zarządza również relacją między wszystkimi plikami projektu a wszystkimi plikami zewnętrznymi. Aby utworzyć aplikację, najpierw utworzysz nowy projekt i rozwiązanie.

1. Jeśli właśnie uruchomiono program Visual Studio, zobaczysz okno dialogowe programu Visual Studio 2019. Wybierz pozycję **Utwórz nowy projekt** , aby rozpocząć.

   ![Początkowe okno dialogowe programu Visual Studio 2019](./media/calc-vs2019-initial-dialog.png "Początkowe okno dialogowe programu Visual Studio 2019")

   W przeciwnym razie na pasku menu w programie Visual Studio wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. Zostanie otwarte okno **Utwórz nowy projekt** .

1. Na liście szablonów projektu wybierz pozycję **Aplikacja konsolowa**, a następnie wybierz przycisk **dalej**.

   ![Wybieranie szablonu aplikacji konsolowej](./media/calc-vs2019-choose-console-app.png "Wybieranie szablonu aplikacji konsolowej")

   > [!Important]
   > Upewnij się, że wybrano wersję C++ szablonu **aplikacji konsolowej** . Zawiera Tagi **C++**, **Windows**i **konsoli** , a ikona ma "+ +" w rogu.

1. W oknie dialogowym **Konfigurowanie nowego projektu** wybierz pole edycji **Nazwa projektu** , nazwij nowy projekt *CalculatorTutorial*, a następnie wybierz pozycję **Utwórz**.

   ![Nazwij projekt w oknie dialogowym Konfigurowanie nowego projektu](./media/calc-vs2019-name-your-project.png "Nazwij projekt w oknie dialogowym Konfigurowanie nowego projektu")

   Zostanie utworzona pusta aplikacja konsoli systemu Windows w języku C++. Aplikacje konsolowe korzystają z okna konsoli systemu Windows w celu wyświetlenia danych wyjściowych i zaakceptowania danych wejściowych użytkownika. W programie Visual Studio zostanie otwarte okno edytora zawierające wygenerowany kod:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>

    int main()
    {
        std::cout << "Hello World!\n";
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu

    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

## <a name="verify-that-your-new-app-builds-and-runs"></a>Sprawdź, czy nowa aplikacja została skompilowana i uruchomiona

Szablon nowej aplikacji konsolowej systemu Windows tworzy prostą aplikację w języku C++ "Hello world". W tym momencie można zobaczyć, jak program Visual Studio kompiluje i uruchamia utworzone aplikacje bezpośrednio z poziomu środowiska IDE.

1. Aby skompilować projekt, wybierz opcję **Kompiluj rozwiązanie** z menu **kompilacja** . W oknie **dane wyjściowe** są wyświetlane wyniki procesu kompilacji.

   ![Kompilowanie projektu](./media/calc-vs2019-build-your-project.png "Kompilowanie projektu")

1. Aby uruchomić kod, na pasku menu wybierz **Debuguj**, **Uruchom bez debugowania**.

   ![Uruchamianie projektu](./media/calc-vs2019-hello-world-console.png "Uruchamianie projektu")

   Zostanie otwarte okno konsoli, a następnie zostanie uruchomiona aplikacja. Po uruchomieniu aplikacji konsolowej w programie Visual Studio program uruchamia swój kod, a następnie drukuje polecenie "naciśnij dowolny klawisz, aby zamknąć to okno. . ." , aby dać Ci szansę zobaczyć dane wyjściowe. Gratulacje! Utworzono pierwszy "Hello, World!" Aplikacja konsolowa w programie Visual Studio!

1. Naciśnij klawisz, aby odrzucić okno konsoli i powrócić do programu Visual Studio.

Teraz masz narzędzia do kompilowania i uruchamiania aplikacji po każdej zmianie, aby sprawdzić, czy kod nadal działa zgodnie z oczekiwaniami. W dalszej części przedstawiono sposób debugowania, jeśli nie.

## <a name="edit-the-code"></a>Edytuj kod

Teraz zmień kod w tym szablonie na aplikację Kalkulator.

1. W pliku *CalculatorTutorial. cpp* Edytuj kod, aby dopasować go do tego przykładu:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>

    using namespace std;

    int main()
    {
        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
            << endl;
        return 0;
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu
    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

   > Zrozumienie kodu:
   >
   > - `#include`Instrukcje umożliwiają odwoływanie się do kodu znajdującego się w innych plikach. Czasami może zostać wyświetlona nazwa pliku otoczona nawiasami ostrymi ( **\<\>** ); inne godziny są otoczone cudzysłowem (**""**). Ogólnie rzecz biorąc, nawiasy ostre są używane podczas odwoływania się do standardowej biblioteki języka C++, natomiast cudzysłowy są używane dla innych plików.
   > - `using namespace std;`Linia instruuje kompilator, aby oczekiwał od standardowej biblioteki języka C++, która ma być używana w tym pliku. Bez tego wiersza każde słowo kluczowe z biblioteki musi być poprzedzone znakiem `std::` , aby zauważyć jego zakres. Na przykład bez tego wiersza każde odwołanie `cout` musi być zapisywane jako `std::cout` . **`using`** Instrukcja zostanie dodana, aby kod wyglądał bardziej czysty.
   > - `cout`Słowo kluczowe jest używane do drukowania do wyjścia standardowego w języku C++. **\<\<** Operator instruuje kompilator, aby wysyłał dane z prawej strony do wyjścia standardowego.
   > - Słowo kluczowe **endl** jest podobne do klawisza ENTER; zamyka wiersz i przenosi kursor do następnego wiersza. Lepszym rozwiązaniem jest umieszczenie `\n` wewnątrz ciągu (zawartego w ""), aby wykonać to samo, jak `endl` zawsze opróżnia bufor i może obniżyć wydajność programu, ale ponieważ jest to bardzo mała aplikacja, `endl` jest używana zamiast tego w celu uzyskania lepszej czytelności.
   > - Wszystkie instrukcje C++ muszą kończyć się średnikami, a wszystkie aplikacje C++ muszą zawierać `main()` funkcję. Ta funkcja jest uruchamiana na początku. Cały kod musi być dostępny `main()` , aby można było go użyć.

1. Aby zapisać plik, naciśnij **klawisze CTRL + S**lub wybierz ikonę **Zapisz** znajdującą się w górnej części IDE, ikonę dyskietki na pasku narzędzi pod paskiem menu.

1. Aby uruchomić aplikację, naciśnij **klawisze CTRL + F5** lub przejdź do menu **Debuguj** i wybierz polecenie **Uruchom bez debugowania**. Powinno zostać wyświetlone okno konsoli zawierające tekst określony w kodzie.

1. Po zakończeniu zamknij okno konsoli.

## <a name="add-code-to-do-some-math"></a>Dodaj kod, aby wykonać kilka obliczeń

Czas na dodanie pewnej logiki matematycznej.

### <a name="to-add-a-calculator-class"></a>Aby dodać klasę kalkulatora

1. Przejdź do menu **projekt** i wybierz polecenie **Dodaj klasę**. W polu edycji **Nazwa klasy** wprowadź *Kalkulator*. Wybierz przycisk **OK**. Dwa nowe pliki zostaną dodane do projektu. Aby zapisać wszystkie zmienione pliki jednocześnie, naciśnij **klawisze Ctrl + Shift + S**. Jest to skrót klawiaturowy do **File**  >  **zapisywania wszystkich**plików. Istnieje również przycisk paska narzędzi dla opcji **Zapisz wszystko**— ikona dwóch dyskietek, która znajduje się obok przycisku **Zapisz** . Ogólnie rzecz biorąc, dobrym sposobem jest **zaoszczędzenie wszystkiego** często, więc nie przegap żadnych plików podczas zapisywania.

   ![Utwórz klasę kalkulatora](./media/calc-vs2019-create-calculator-class.png "Utwórz klasę kalkulatora")

   Klasa przypomina plan dla obiektu, który robi coś. W tym przypadku definiujemy Kalkulator i sposób jego działania. Kreator **dodawania klasy** użyty powyżej utworzył pliki. h i. cpp, które mają taką samą nazwę jak Klasa. Pełną listę plików projektu można wyświetlić w oknie **Eksplorator rozwiązań** widocznym po stronie IDE. Jeśli okno nie jest widoczne, możesz otworzyć je na pasku menu: wybierz pozycję **Wyświetl**  >  **Eksplorator rozwiązań**.

   ![Eksplorator rozwiązań](./media/calc-vs2019-solution-explorer.png "Eksplorator rozwiązań")

   Teraz powinno być otwartych trzy karty w edytorze: *CalculatorTutorial. cpp*, *Kalkulator. h*i *Kalkulator. cpp*. Jeśli przypadkowo zamkniesz jedną z nich, możesz otworzyć ją ponownie, klikając ją dwukrotnie w oknie **Eksplorator rozwiązań** .

1. W polu **Kalkulator. h**Usuń `Calculator();` `~Calculator();` wygenerowane wiersze i, ponieważ nie będą one potrzebne w tym miejscu. Następnie Dodaj następujący wiersz kodu, aby plik wyglądał teraz następująco:

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > Omówienie kodu
   >
   > - Dodana linia deklaruje nową funkcję o nazwie `Calculate` , która będzie używana do uruchamiania operacji matematycznych do dodawania, odejmowania, mnożenia i dzielenia.
   > - Kod języka C++ jest zorganizowany w plikach *nagłówkowych* (. h) i *źródłowych* (. cpp). Różne kompilatory obsługują kilka innych rozszerzeń plików, ale są one głównymi. Funkcje i zmienne są zwykle *zadeklarowane*, to oznacza, że dana nazwa i typ, w plikach nagłówkowych i *zaimplementowana*lub dana definicja, w plikach źródłowych. Aby uzyskać dostęp do kodu zdefiniowanego w innym pliku, można użyć `#include "filename.h"` , gdzie "filename. h" jest nazwą pliku, który deklaruje zmienne lub funkcje, których chcesz użyć.
   > - Dwa usunięte wiersze deklarują *Konstruktor* i *destruktor* dla klasy. W przypadku prostej klasy, takiej jak ta, kompilator tworzy je dla Ciebie, a ich zastosowania wykraczają poza zakres tego samouczka.
   > - Dobrym sposobem jest zorganizowanie kodu w różne pliki w oparciu o to, co robi, dzięki czemu możesz łatwo znaleźć kod, którego potrzebujesz później. W naszym przypadku definiujemy `Calculator` klasy niezależnie od pliku zawierającego `main()` funkcję, ale planujemy odwołanie do `Calculator` klasy w `main()` .

1. Zobaczysz zieloną zygzakę w obszarze `Calculate` . Jest to spowodowane tym, że funkcja nie została zdefiniowana `Calculate` w pliku. cpp. Umieść kursor nad słowem, kliknij żarówki (w tym przypadku śrubokręt), który wystawia, a następnie wybierz pozycję **Utwórz definicję elementu "Oblicz" w programie Kalkulator. cpp**.

   ![Utwórz definicję obliczeń](./media/calc-vs2019-create-definition.png "Utwórz definicję obliczeń")

   Zostanie wyświetlone wyskakujące okienko umożliwiające wgląd w zmiany kodu, które zostały wprowadzone w innym pliku. Kod został dodany do programu *Kalkulator. cpp*.

   ![Wyskakujące okienko z definicją obliczeń](./media/calc-vs2019-pop-up-definition.png "Wyskakujące okienko z definicją obliczeń")

   Obecnie tylko zwraca 0,0. Zmieńmy to. Naciśnij klawisz **ESC** , aby zamknąć okno podręczne.

1. Przejdź do pliku *Kalkulator. cpp* w oknie edytora. Usuń `Calculator()` sekcje i `~Calculator()` (jak w pliku h) i Dodaj następujący kod do `Calculate()` :

    ```cpp
    #include "Calculator.h"

    double Calculator::Calculate(double x, char oper, double y)
    {
        switch(oper)
        {
            case '+':
                return x + y;
            case '-':
                return x - y;
            case '*':
                return x * y;
            case '/':
                return x / y;
            default:
                return 0.0;
        }
    }
    ```

   > Omówienie kodu
   >
   > - Funkcja `Calculate` używa liczby, operatora i drugiej liczby, a następnie wykonuje żądaną operację dla liczb.
   > - Instrukcja Switch sprawdza, który operator został dostarczony i wykonuje tylko przypadki odpowiadające tej operacji. Wartość domyślna: przypadek jest rezerwy w przypadku, gdy użytkownik wpisze operator, który nie został zaakceptowany, więc program nie przerywa. Ogólnie rzecz biorąc, najlepiej jest obsługiwać nieprawidłowe dane wprowadzane przez użytkownika w bardziej elegancki sposób, ale wykracza to poza zakres tego samouczka.
   > - **`double`** Słowo kluczowe wskazuje typ liczby, która obsługuje miejsca dziesiętne. Dzięki temu Kalkulator może obsłużyć zarówno dziesiętną matematyczną, jak i liczbę całkowitą. `Calculate`Funkcja jest wymagana, aby zawsze zwracała taką liczbę ze względu na **`double`** bardzo początek kodu (oznacza to, że zwracany typ funkcji), dlatego zwracamy 0,0 nawet w przypadku domyślnego.
   > - Plik. h deklaruje *prototyp*funkcji, który informuje kompilator, jakie parametry wymagają, i jakie zwraca typ od niego oczekiwane. Plik. cpp zawiera wszystkie szczegóły implementacji funkcji.

Jeśli kompilujesz i uruchomisz kod ponownie w tym momencie, nadal będzie on się zamykał po zaproszeniu do wykonania operacji. Następnie zmodyfikujesz `main` funkcję, aby wykonać pewne obliczenia.

### <a name="to-call-the-calculator-class-member-functions"></a>Aby wywołać funkcje elementów członkowskich klasy kalkulatora

1. Teraz zaktualizujmy `main` funkcję w *CalculatorTutorial. cpp*:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
             << endl;

        Calculator c;
        while (true)
        {
            cin >> x >> oper >> y;
            result = c.Calculate(x, oper, y);
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

   > Omówienie kodu
   >
   > - Ponieważ programy C++ są zawsze uruchamiane przy użyciu `main()` funkcji, musimy w tym miejscu wywołać inny kod, więc `#include` konieczne jest wykonanie instrukcji.
   > - Niektóre zmienne początkowe `x` , `y` , `oper` i `result` są zadeklarowane w celu przechowania odpowiednio pierwszej liczby, drugiej liczby, operatora i wyniku końcowego. Zawsze dobrym sposobem jest przyznanie im początkowych wartości, aby uniknąć niezdefiniowanego zachowania, co jest wykonywane w tym miejscu.
   > - `Calculator c;`Wiersz deklaruje obiekt o nazwie "c" jako wystąpienie `Calculator` klasy. Sama klasa jest tylko planem, w jaki działają Kalkulatory. Obiekt jest określonym kalkulatorem, który wykonuje obliczenia matematyczne.
   > - `while (true)`Instrukcja jest pętlą. Kod wewnątrz pętli będzie nadal wykonywany przez cały czas i dłużej, o ile warunek wewnątrz ma `()` wartość true. Ponieważ warunek jest po prostu wyświetlany jako **`true`** , zawsze ma wartość true, więc pętla jest uruchamiana w nieskończoność. Aby zamknąć program, użytkownik musi ręcznie zamknąć okno konsoli. W przeciwnym razie program zawsze czeka na nowe dane wejściowe.
   > - `cin`Słowo kluczowe jest używane do akceptowania danych wejściowych od użytkownika. Ten strumień wejściowy jest wystarczająco inteligentny, aby przetwarzać wiersz tekstu wprowadzony w oknie konsoli i umieścić go wewnątrz każdej z wymienionych zmiennych w kolejności, przy założeniu, że dane wejściowe użytkownika są zgodne z wymaganą specyfikacją. Możesz zmodyfikować ten wiersz, aby akceptować różne typy danych wejściowych, na przykład więcej niż dwie liczby, chociaż `Calculate()` należy również zaktualizować tę funkcję, aby ją obsłużyć.
   > - `c.Calculate(x, oper, y);`Wyrażenie wywołuje `Calculate` wcześniej zdefiniowaną funkcję i dostarcza wprowadzone wartości wejściowe. Funkcja zwraca liczbę, która jest przechowywana w `result` .
   > - Na koniec `result` jest drukowana w konsoli, więc użytkownik zobaczy wynik obliczenia.

### <a name="build-and-test-the-code-again"></a>Kompiluj i Testuj kod ponownie

Teraz czas na ponowne przetestowanie programu w celu upewnienia się, że wszystko działa prawidłowo.

1. Naciśnij **kombinację klawiszy CTRL + F5** , aby skompilować i uruchomić aplikację.

1. Wprowadź `5 + 5` polecenie i naciśnij klawisz **Enter**. Sprawdź, czy wynik wynosi 10.

   ![Wynik 5 + 5](./media/calc-vs2019-five-plus-five.png "Wynik 5 + 5")

## <a name="debug-the-app"></a>Debugowanie aplikacji

Ponieważ użytkownik może wpisywać dowolne elementy w oknie konsoli, należy się upewnić, że Kalkulator obsługuje pewne dane wejściowe zgodnie z oczekiwaniami. Zamiast uruchamiania programu, należy debugować go zamiast tego, aby można było sprawdzić, co jest wykonywane szczegółowo, krok po kroku.

### <a name="to-run-the-app-in-the-debugger"></a>Aby uruchomić aplikację w debugerze

1. Ustaw punkt przerwania w `result = c.Calculate(x, oper, y);` wierszu zaraz po poproszeniu użytkownika o dane wejściowe. Aby ustawić punkt przerwania, kliknij pozycję obok linii na szarym pasku pionowym wzdłuż lewej krawędzi okna edytora. Zostanie wyświetlona czerwona kropka.

   ![Ustawianie punktu przerwania](./media/calc-vs2019-set-breakpoint.png "Ustawianie punktu przerwania")

   Teraz podczas debugowania programu program zawsze wstrzymuje wykonywanie w tym wierszu. Mamy już pomysł, że program działa w przypadku prostych przypadków. Ponieważ nie chcemy wstrzymywać wykonywania za każdym razem, Przypuśćmy, że punkt przerwania.

1. Kliknij prawym przyciskiem myszy czerwoną kropkę reprezentującą punkt przerwania, a następnie wybierz pozycję **warunki**. W polu edycji dla warunku wprowadź `(y == 0) && (oper == '/')` . Po zakończeniu wybierz przycisk **Zamknij** . Warunek jest automatycznie zapisywany.

   ![Ustaw punkt przerwania warunkowego](./media/calc-vs2019-conditional-breakpoint.png "Ustaw punkt przerwania warunkowego")

   Teraz wstrzymamy wykonywanie w punkcie przerwania, w przypadku próby dzielenia przez 0.

1. Aby debugować program, naciśnij klawisz **F5**lub wybierz przycisk paska narzędzi **lokalnego debugera systemu Windows** , który ma ikonę zielonej strzałki. W aplikacji konsolowej, jeśli wprowadzisz coś takiego jak "5-0", program zachowuje się normalnie i nadal działa. Jednak jeśli wpiszesz "10/0", zostanie on wstrzymany w punkcie przerwania. Można nawet umieścić dowolną liczbę spacji między operatorem a liczbami: `cin` jest to inteligentna wartość, aby odpowiednio analizować dane wejściowe.

   ![Wstrzymaj w warunkowym punkcie przerwania](./media/calc-vs2019-debug-breakpoint.png "Wstrzymaj w warunkowym punkcie przerwania")

### <a name="useful-windows-in-the-debugger"></a>Przydatne okna w debugerze

Za każdym razem, gdy debugujesz kod, możesz zauważyć, że pojawiły się niektóre nowe okna. Te okna mogą pomóc w debugowaniu. Zapoznaj się z oknem **Autokorekty** . W oknie **samochody** są wyświetlane bieżące wartości zmiennych używanych co najmniej trzy wiersze przed i do bieżącego wiersza. Aby wyświetlić wszystkie zmienne z tej funkcji, przełącz się do okna **zmiennych lokalnych** . Można faktycznie zmodyfikować wartości tych zmiennych podczas debugowania, aby zobaczyć, jaki wpływ ma w programie. W takim przypadku pozostawimy je samodzielnie.

   ![Okno zmiennych lokalnych](./media/calc-vs2019-debug-locals.png "Okno zmiennych lokalnych")

Możesz również po prostu umieścić kursor nad zmiennymi w kodzie, aby zobaczyć ich bieżące wartości, w przypadku których wykonywanie jest obecnie wstrzymane. Upewnij się, że okno edytora jest fokusem, klikając je najpierw.

   ![Aktywuj, aby wyświetlić bieżące wartości zmiennych](./media/calc-vs2019-hover-tooltip.png "Aktywuj, aby wyświetlić bieżące wartości zmiennych")

### <a name="to-continue-debugging"></a>Aby kontynuować debugowanie

1. Żółty wiersz po lewej stronie pokazuje bieżący punkt wykonania. Bieżące wywołania wiersza `Calculate` , dlatego naciśnij klawisz **F11** , aby **przejść** do funkcji. Znajdziesz Cię w treści `Calculate` funkcji. Należy zachować ostrożność **krok po kroku**. w przypadku zbyt dużej ilości czasu może to spowodować marnowanie. Zawiera kod, który jest używany w wierszu, w którym pracujesz, w tym funkcje biblioteki standardowej.

1. Teraz, gdy punkt wykonywania jest na początku `Calculate` funkcji, naciśnij klawisz **F10** , aby przejść do następnego wiersza w wykonaniu programu. **F10** jest również znany jako **krok powyżej**. Możesz użyć przechodzenia **krok po kroku** , aby przejść od wiersza do wiersza, bez podania do szczegółów co się dzieje w każdej części wiersza. Ogólnie rzecz biorąc, należy użyć przekroczenia **kroku** zamiast **wkroczenia do**, chyba że chcesz szczegółowe bardziej głęboko kod, który jest wywoływany z innego miejsca (jak miało miejsce do uzyskania treści `Calculate` ).

1. Kontynuuj używanie klawisza **F10** , **Aby przekroczyć** każdy wiersz do momentu powrotu do `main()` funkcji w innym pliku, i zatrzymaj ją w `cout` wierszu.

   Wygląda na to, że program wykonuje oczekiwane działania: Pobiera pierwszą liczbę i dzieli go przez drugi. W `cout` wierszu Umieść wskaźnik myszy nad zmienną lub zapoznaj się `result` `result` z oknem **Autokorekty** . Zobaczysz, że wartość zostanie wyświetlona na liście jako "inf", która nie wygląda w prawidłowym stanie, więc naprawimy ją. `cout`Wiersz tylko wyprowadza dane, które są przechowywane w `result` , więc po przekroczeniu kolejnej linii do przodu przy użyciu klawisza **F10**zostanie wyświetlone okno konsoli:

   ![Wynik dzielenia przez zero](./media/calc-vs2019-divide-by-zero-fail.png "Wynik dzielenia przez zero")

   Wynika to z faktu, że dzielenie przez zero jest niezdefiniowane, więc program nie ma numerycznej odpowiedzi na żądaną operację.

### <a name="to-fix-the-divide-by-zero-error"></a>Aby naprawić błąd "dzielenie przez zero"

Przyjrzyjmy się dzielenie przez zero, dzięki czemu użytkownik może zrozumieć problem.

1. Wprowadź następujące zmiany w *CalculatorTutorial. cpp*. (Można pozostawić program uruchomiony podczas edycji, dzięki funkcji debugera o nazwie **Edytuj i Kontynuuj**):

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b" << endl;

        Calculator c;
        while (true)
        {
            cin  >> x  >> oper  >> y;
            if (oper == '/' && y == 0)
            {
                cout << "Division by 0 exception" << endl;
                continue;
            }
            else
            {
                result = c.Calculate(x, oper, y);
            }
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

1. Teraz naciśnij klawisz **F5** . Wykonanie programu jest kontynuowane aż do momentu zaczekania na podanie danych wejściowych użytkownika. Wprowadź `10 / 0` ponownie. Teraz zostanie wydrukowany bardziej przydatny komunikat. Użytkownik jest monitowany o więcej danych wejściowych, a program kontynuuje wykonywanie normalnie.

   ![Wynik końcowy po zmianach](./media/calc-vs2019-final-verification.png "Wynik końcowy po zmianach")

   > [!Note]
   > Gdy edytujesz kod w trybie debugowania, istnieje ryzyko, że kod staje się przestarzały. Dzieje się tak, gdy debuger nadal działa w starym kodzie i nie został jeszcze zaktualizowany ze zmianami. Debuger wyświetli okno dialogowe, aby poinformować użytkownika o tym, kiedy się dzieje. Czasami może być konieczne naciśnięcie klawisza **F5** w celu odświeżenia wykonywanego kodu. W szczególności w przypadku wprowadzenia zmiany wewnątrz funkcji, gdy punkt wykonywania znajduje się wewnątrz tej funkcji, należy wykonać krok poza funkcję, a następnie ponownie w celu uzyskania zaktualizowanego kodu. Jeśli to nie zadziała z jakiegoś powodu, a zobaczysz komunikat o błędzie, możesz zatrzymać debugowanie, klikając czerwony kwadrat na pasku narzędzi w menu u góry IDE, a następnie ponownie Rozpocznij debugowanie, wprowadzając klawisz **F5** lub wybierając zieloną strzałkę "Odtwórz" obok przycisku Zatrzymaj na pasku narzędzi.

   > Informacje o skrótach uruchamiania i debugowania
   >
   > - **F5** (lub **Debuguj**  >  **Rozpocznij debugowanie**) uruchamia sesję debugowania, jeśli jedna nie jest już aktywna, i uruchamia program do momentu trafienia punktu przerwania lub program wymaga wprowadzenia danych przez użytkownika. Jeśli żadne dane wejściowe użytkownika nie są konieczne i punkt przerwania nie jest dostępny do trafienia, program zostanie przerwany, a okno konsoli zostanie zamknięte po zakończeniu działania programu. Jeśli masz coś takiego jak program "Hello world" do uruchomienia, użyj **kombinacji klawiszy CTRL + F5** lub ustaw punkt przerwania, **Aby zachować** otwarte okno.
   > - **Ctrl + F5** (lub **Debuguj**  >  **Uruchom bez debugowania**) uruchamia aplikację bez przechodzenia do trybu debugowania. Jest to nieco szybsze niż debugowanie, a okno konsoli pozostaje otwarte po zakończeniu wykonywania przez program.
   > - **F10** (znany jako **przekroczenie**) umożliwia przechodzenie przez kod, wiersz po wierszu i wizualizację sposobu uruchamiania kodu oraz zmienne wartości w każdym kroku wykonania.
   > - **F11** (znany jako **krok do**) działa podobnie do **przekroczenia, z**wyjątkiem przypadków, w których są wywoływane wszystkie funkcje w wierszu wykonania. Na przykład, jeśli wykonywany wiersz wywołuje funkcję, naciśnięcie klawisza **F11** przenosi wskaźnik do treści funkcji, dzięki czemu można wykonać kod funkcji uruchamianej przed powrotem do wiersza, który został rozpoczęty. Naciskaj kroki **F10** w wywołaniu funkcji i po prostu przesuniesz się do następnego wiersza. Wywołanie funkcji jest nadal wykonywane, ale program nie jest wstrzymany, aby zobaczyć, co robi.

### <a name="close-the-app"></a>Zamknij aplikację

- Jeśli nadal działa, Zamknij okno konsoli dla aplikacji Kalkulator.

## <a name="the-finished-app"></a>Gotowa aplikacja

Gratulacje! Kod aplikacji kalkulatora został ukończony i skompilowany i debugowany w programie Visual Studio.

## <a name="next-steps"></a>Następne kroki

[Dowiedz się więcej o programie Visual Studio dla języka C++](https://devblogs.microsoft.com/cppblog/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end

::: moniker range="<vs-2019"

Typowym punktem wyjścia dla programisty języka C++ jest "Hello, World!" aplikacja uruchamiana w wierszu polecenia. To wszystko, co utworzysz w programie Visual Studio w tym artykule, a następnie przejdziemy do bardziej trudnej: aplikacji Kalkulator.

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio z **programowaniem dla komputerów stacjonarnych z** zainstalowanym i uruchomionym obciążeniem języka C++. Jeśli nie jest jeszcze zainstalowana, zobacz [Install C++ Support in Visual Studio](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Tworzenie projektu aplikacji

Program Visual Studio używa *projektów* do organizowania kodu aplikacji oraz *rozwiązań* do organizowania projektów. Projekt zawiera wszystkie opcje, konfiguracje i reguły używane do kompilowania aplikacji. Zarządza również relacją między wszystkimi plikami projektu a wszystkimi plikami zewnętrznymi. Aby utworzyć aplikację, najpierw utworzysz nowy projekt i rozwiązanie.

1. Na pasku menu programu Visual Studio wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. Zostanie otwarte okno **Nowy projekt** .

2. Na lewym pasku bocznym upewnij się, że **Visual C++** jest zaznaczone. W centrum wybierz pozycję **Aplikacja konsolowa systemu Windows**.

3. W polu **Nazwa** Edytuj w dolnej części Nadaj nazwę nowemu projektowi *CalculatorTutorial*, a następnie wybierz **przycisk OK**.

   ![Okno dialogowe Nowy projekt](./media/calculator-new-project-dialog.png "Okno dialogowe Nowy projekt")

   Zostanie utworzona pusta aplikacja konsoli systemu Windows w języku C++. Aplikacje konsolowe korzystają z okna konsoli systemu Windows w celu wyświetlenia danych wyjściowych i zaakceptowania danych wejściowych użytkownika. W programie Visual Studio zostanie otwarte okno edytora zawierające wygenerowany kod:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    int main()
    {
        std::cout << "Hello World!\n";
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu

    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

## <a name="verify-that-your-new-app-builds-and-runs"></a>Sprawdź, czy nowa aplikacja została skompilowana i uruchomiona

Szablon nowej aplikacji konsolowej systemu Windows tworzy prostą aplikację w języku C++ "Hello world". W tym momencie można zobaczyć, jak program Visual Studio kompiluje i uruchamia utworzone aplikacje bezpośrednio z poziomu środowiska IDE.

1. Aby skompilować projekt, wybierz opcję **Kompiluj rozwiązanie** z menu **kompilacja** . W oknie **dane wyjściowe** są wyświetlane wyniki procesu kompilacji.

   ![Kompilowanie projektu](./media/calculator-initial-build-output.png "Kompilowanie projektu")

1. Aby uruchomić kod, na pasku menu wybierz **Debuguj**, **Uruchom bez debugowania**.

   ![Uruchamianie projektu](./media/calculator-hello-world-console.png "Uruchamianie projektu")

   Zostanie otwarte okno konsoli, a następnie zostanie uruchomiona aplikacja. Po uruchomieniu aplikacji konsolowej w programie Visual Studio program uruchamia swój kod, a następnie drukuje "naciśnij dowolny klawisz, aby kontynuować. . ." , aby dać Ci szansę zobaczyć dane wyjściowe. Gratulacje! Utworzono pierwszy "Hello, World!" Aplikacja konsolowa w programie Visual Studio!

1. Naciśnij klawisz, aby odrzucić okno konsoli i powrócić do programu Visual Studio.

Teraz masz narzędzia do kompilowania i uruchamiania aplikacji po każdej zmianie, aby sprawdzić, czy kod nadal działa zgodnie z oczekiwaniami. W dalszej części przedstawiono sposób debugowania, jeśli nie.

## <a name="edit-the-code"></a>Edytuj kod

Teraz zmień kod w tym szablonie na aplikację Kalkulator.

1. W pliku *CalculatorTutorial. cpp* Edytuj kod, aby dopasować go do tego przykładu:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    using namespace std;

    int main()
    {
        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
            << endl;
        return 0;
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu
    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

   > Zrozumienie kodu:
   >
   > - `#include`Instrukcje umożliwiają odwoływanie się do kodu znajdującego się w innych plikach. Czasami może zostać wyświetlona nazwa pliku otoczona nawiasami ostrymi ( **\<\>** ); inne godziny są otoczone cudzysłowem (**""**). Ogólnie rzecz biorąc, nawiasy ostre są używane podczas odwoływania się do standardowej biblioteki języka C++, natomiast cudzysłowy są używane dla innych plików.
   > - `#include "pch.h"`Wiersz (lub w programie Visual Studio 2017 i starszych `#include "stdafx.h"` ) odwołuje się do elementu znanego jako prekompilowany nagłówek. Są one często używane przez profesjonalne programiści, aby skrócić czasy kompilacji, ale wykraczają poza zakres tego samouczka.
   > - `using namespace std;`Linia instruuje kompilator, aby oczekiwał od standardowej biblioteki języka C++, która ma być używana w tym pliku. Bez tego wiersza każde słowo kluczowe z biblioteki musi być poprzedzone znakiem `std::` , aby zauważyć jego zakres. Na przykład bez tego wiersza każde odwołanie `cout` musi być zapisywane jako `std::cout` . **`using`** Instrukcja zostanie dodana, aby kod wyglądał bardziej czysty.
   > - `cout`Słowo kluczowe jest używane do drukowania do wyjścia standardowego w języku C++. **\<\<** Operator instruuje kompilator, aby wysyłał dane z prawej strony do wyjścia standardowego.
   > - Słowo kluczowe **endl** jest podobne do klawisza ENTER; zamyka wiersz i przenosi kursor do następnego wiersza. Lepszym rozwiązaniem jest umieszczenie `\n` wewnątrz ciągu (zawartego w ""), aby wykonać to samo, jak `endl` zawsze opróżnia bufor i może obniżyć wydajność programu, ale ponieważ jest to bardzo mała aplikacja, `endl` jest używana zamiast tego w celu uzyskania lepszej czytelności.
   > - Wszystkie instrukcje C++ muszą kończyć się średnikami, a wszystkie aplikacje C++ muszą zawierać `main()` funkcję. Ta funkcja jest uruchamiana na początku. Cały kod musi być dostępny `main()` , aby można było go użyć.

1. Aby zapisać plik, naciśnij **klawisze CTRL + S**lub wybierz ikonę **Zapisz** znajdującą się w górnej części IDE, ikonę dyskietki na pasku narzędzi pod paskiem menu.

1. Aby uruchomić aplikację, naciśnij **klawisze CTRL + F5** lub przejdź do menu **Debuguj** i wybierz polecenie **Uruchom bez debugowania**. Jeśli zostanie wyświetlone okno podręczne, które informuje, że **ten projekt jest nieaktualny**, możesz wybrać opcję **nie pokazuj ponownie tego okna dialogowego**, a następnie wybrać opcję **tak** , aby skompilować aplikację. Powinno zostać wyświetlone okno konsoli zawierające tekst określony w kodzie.

   ![Kompilowanie i uruchamianie aplikacji](./media/calculator-first-launch.gif "Kompilowanie i uruchamianie aplikacji")

1. Po zakończeniu zamknij okno konsoli.

## <a name="add-code-to-do-some-math"></a>Dodaj kod, aby wykonać kilka obliczeń

Czas na dodanie pewnej logiki matematycznej.

### <a name="to-add-a-calculator-class"></a>Aby dodać klasę kalkulatora

1. Przejdź do menu **projekt** i wybierz polecenie **Dodaj klasę**. W polu edycji **Nazwa klasy** wprowadź *Kalkulator*. Wybierz przycisk **OK**. Dwa nowe pliki zostaną dodane do projektu. Aby zapisać wszystkie zmienione pliki jednocześnie, naciśnij **klawisze Ctrl + Shift + S**. Jest to skrót klawiaturowy do **File**  >  **zapisywania wszystkich**plików. Istnieje również przycisk paska narzędzi dla opcji **Zapisz wszystko**— ikona dwóch dyskietek, która znajduje się obok przycisku **Zapisz** . Ogólnie rzecz biorąc, dobrym sposobem jest **zaoszczędzenie wszystkiego** często, więc nie przegap żadnych plików podczas zapisywania.

   ![Utwórz klasę kalkulatora](./media/calculator-create-class.gif "Utwórz klasę kalkulatora")

   Klasa przypomina plan dla obiektu, który robi coś. W tym przypadku definiujemy Kalkulator i sposób jego działania. Kreator **dodawania klasy** użyty powyżej utworzył pliki. h i. cpp, które mają taką samą nazwę jak Klasa. Pełną listę plików projektu można wyświetlić w oknie **Eksplorator rozwiązań** widocznym po stronie IDE. Jeśli okno nie jest widoczne, możesz otworzyć je na pasku menu: wybierz pozycję **Wyświetl**  >  **Eksplorator rozwiązań**.

   ![Eksplorator rozwiązań](./media/calculator-solution-explorer.png "Eksplorator rozwiązań")

   Teraz powinno być otwartych trzy karty w edytorze: *CalculatorTutorial. cpp*, *Kalkulator. h*i *Kalkulator. cpp*. Jeśli przypadkowo zamkniesz jedną z nich, możesz otworzyć ją ponownie, klikając ją dwukrotnie w oknie **Eksplorator rozwiązań** .

1. W polu **Kalkulator. h**Usuń `Calculator();` `~Calculator();` wygenerowane wiersze i, ponieważ nie będą one potrzebne w tym miejscu. Następnie Dodaj następujący wiersz kodu, aby plik wyglądał teraz następująco:

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > Omówienie kodu
   >
   > - Dodana linia deklaruje nową funkcję o nazwie `Calculate` , która będzie używana do uruchamiania operacji matematycznych do dodawania, odejmowania, mnożenia i dzielenia.
   > - Kod języka C++ jest zorganizowany w plikach *nagłówkowych* (. h) i *źródłowych* (. cpp). Różne kompilatory obsługują kilka innych rozszerzeń plików, ale są one głównymi. Funkcje i zmienne są zwykle *zadeklarowane*, to oznacza, że dana nazwa i typ, w plikach nagłówkowych i *zaimplementowana*lub dana definicja, w plikach źródłowych. Aby uzyskać dostęp do kodu zdefiniowanego w innym pliku, można użyć `#include "filename.h"` , gdzie "filename. h" jest nazwą pliku, który deklaruje zmienne lub funkcje, których chcesz użyć.
   > - Dwa usunięte wiersze deklarują *Konstruktor* i *destruktor* dla klasy. W przypadku prostej klasy, takiej jak ta, kompilator tworzy je dla Ciebie, a ich zastosowania wykraczają poza zakres tego samouczka.
   > - Dobrym sposobem jest zorganizowanie kodu w różne pliki w oparciu o to, co robi, dzięki czemu możesz łatwo znaleźć kod, którego potrzebujesz później. W naszym przypadku definiujemy `Calculator` klasy niezależnie od pliku zawierającego `main()` funkcję, ale planujemy odwołanie do `Calculator` klasy w `main()` .

1. Zobaczysz zieloną zygzakę w obszarze `Calculate` . Jest to spowodowane tym, że funkcja nie została zdefiniowana `Calculate` w pliku. cpp. Umieść kursor nad słowem, kliknij żarówki, który wystawia, a następnie wybierz pozycję **Utwórz definicję elementu "Oblicz" w programie Kalkulator. cpp**. Zostanie wyświetlone wyskakujące okienko umożliwiające wgląd w zmiany kodu, które zostały wprowadzone w innym pliku. Kod został dodany do programu *Kalkulator. cpp*.

   ![Utwórz definicję obliczeń](./media/calculator-create-definition.gif "Utwórz definicję obliczeń")

   Obecnie tylko zwraca 0,0. Zmieńmy to. Naciśnij klawisz **ESC** , aby zamknąć okno podręczne.

1. Przejdź do pliku *Kalkulator. cpp* w oknie edytora. Usuń `Calculator()` sekcje i `~Calculator()` (jak w pliku h) i Dodaj następujący kod do `Calculate()` :

    ```cpp
    #include "pch.h"
    #include "Calculator.h"

    double Calculator::Calculate(double x, char oper, double y)
    {
        switch(oper)
        {
            case '+':
                return x + y;
            case '-':
                return x - y;
            case '*':
                return x * y;
            case '/':
                return x / y;
            default:
                return 0.0;
        }
    }
    ```

   > Omówienie kodu
   >
   > - Funkcja `Calculate` używa liczby, operatora i drugiej liczby, a następnie wykonuje żądaną operację dla liczb.
   > - Instrukcja Switch sprawdza, który operator został dostarczony i wykonuje tylko przypadki odpowiadające tej operacji. Wartość domyślna: przypadek jest rezerwy w przypadku, gdy użytkownik wpisze operator, który nie został zaakceptowany, więc program nie przerywa. Ogólnie rzecz biorąc, najlepiej jest obsługiwać nieprawidłowe dane wprowadzane przez użytkownika w bardziej elegancki sposób, ale wykracza to poza zakres tego samouczka.
   > - **`double`** Słowo kluczowe wskazuje typ liczby, która obsługuje miejsca dziesiętne. Dzięki temu Kalkulator może obsłużyć zarówno dziesiętną matematyczną, jak i liczbę całkowitą. `Calculate`Funkcja jest wymagana, aby zawsze zwracała taką liczbę ze względu na **`double`** bardzo początek kodu (oznacza to, że zwracany typ funkcji), dlatego zwracamy 0,0 nawet w przypadku domyślnego.
   > - Plik. h deklaruje *prototyp*funkcji, który informuje kompilator, jakie parametry wymagają, i jakie zwraca typ od niego oczekiwane. Plik. cpp zawiera wszystkie szczegóły implementacji funkcji.

Jeśli kompilujesz i uruchomisz kod ponownie w tym momencie, nadal będzie on się zamykał po zaproszeniu do wykonania operacji. Następnie zmodyfikujesz `main` funkcję, aby wykonać pewne obliczenia.

### <a name="to-call-the-calculator-class-member-functions"></a>Aby wywołać funkcje elementów członkowskich klasy kalkulatora

1. Teraz zaktualizujmy `main` funkcję w *CalculatorTutorial. cpp*:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
             << endl;

        Calculator c;
        while (true)
        {
            cin >> x >> oper >> y;
            result = c.Calculate(x, oper, y);
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

   > Omówienie kodu
   >
   > - Ponieważ programy C++ są zawsze uruchamiane przy użyciu `main()` funkcji, musimy w tym miejscu wywołać inny kod, więc `#include` konieczne jest wykonanie instrukcji.
   > - Niektóre zmienne początkowe `x` , `y` , `oper` i `result` są zadeklarowane w celu przechowania odpowiednio pierwszej liczby, drugiej liczby, operatora i wyniku końcowego. Zawsze dobrym sposobem jest przyznanie im początkowych wartości, aby uniknąć niezdefiniowanego zachowania, co jest wykonywane w tym miejscu.
   > - `Calculator c;`Wiersz deklaruje obiekt o nazwie "c" jako wystąpienie `Calculator` klasy. Sama klasa jest tylko planem, w jaki działają Kalkulatory. Obiekt jest określonym kalkulatorem, który wykonuje obliczenia matematyczne.
   > - `while (true)`Instrukcja jest pętlą. Kod wewnątrz pętli będzie nadal wykonywany przez cały czas i dłużej, o ile warunek wewnątrz ma `()` wartość true. Ponieważ warunek jest po prostu wyświetlany jako **`true`** , zawsze ma wartość true, więc pętla jest uruchamiana w nieskończoność. Aby zamknąć program, użytkownik musi ręcznie zamknąć okno konsoli. W przeciwnym razie program zawsze czeka na nowe dane wejściowe.
   > - `cin`Słowo kluczowe jest używane do akceptowania danych wejściowych od użytkownika. Ten strumień wejściowy jest wystarczająco inteligentny, aby przetwarzać wiersz tekstu wprowadzony w oknie konsoli i umieścić go wewnątrz każdej z wymienionych zmiennych w kolejności, przy założeniu, że dane wejściowe użytkownika są zgodne z wymaganą specyfikacją. Możesz zmodyfikować ten wiersz, aby akceptować różne typy danych wejściowych, na przykład więcej niż dwie liczby, chociaż `Calculate()` należy również zaktualizować tę funkcję, aby ją obsłużyć.
   > - `c.Calculate(x, oper, y);`Wyrażenie wywołuje `Calculate` wcześniej zdefiniowaną funkcję i dostarcza wprowadzone wartości wejściowe. Funkcja zwraca liczbę, która jest przechowywana w `result` .
   > - Na koniec `result` jest drukowana w konsoli, więc użytkownik zobaczy wynik obliczenia.

### <a name="build-and-test-the-code-again"></a>Kompiluj i Testuj kod ponownie

Teraz czas na ponowne przetestowanie programu w celu upewnienia się, że wszystko działa prawidłowo.

1. Naciśnij **kombinację klawiszy CTRL + F5** , aby skompilować i uruchomić aplikację.

1. Wprowadź `5 + 5` polecenie i naciśnij klawisz **Enter**. Sprawdź, czy wynik wynosi 10.

   ![Wynik 5 + 5](./media/calculator-five-plus-five.png "Wynik 5 + 5")

## <a name="debug-the-app"></a>Debugowanie aplikacji

Ponieważ użytkownik może wpisywać dowolne elementy w oknie konsoli, należy się upewnić, że Kalkulator obsługuje pewne dane wejściowe zgodnie z oczekiwaniami. Zamiast uruchamiania programu, należy debugować go zamiast tego, aby można było sprawdzić, co jest wykonywane szczegółowo, krok po kroku.

### <a name="to-run-the-app-in-the-debugger"></a>Aby uruchomić aplikację w debugerze

1. Ustaw punkt przerwania w `result = c.Calculate(x, oper, y);` wierszu zaraz po poproszeniu użytkownika o dane wejściowe. Aby ustawić punkt przerwania, kliknij pozycję obok linii na szarym pasku pionowym wzdłuż lewej krawędzi okna edytora. Zostanie wyświetlona czerwona kropka.

   ![Ustawianie punktu przerwania](./media/calculator-set-breakpoint.gif "Ustawianie punktu przerwania")

   Teraz podczas debugowania programu program zawsze wstrzymuje wykonywanie w tym wierszu. Mamy już pomysł, że program działa w przypadku prostych przypadków. Ponieważ nie chcemy wstrzymywać wykonywania za każdym razem, Przypuśćmy, że punkt przerwania.

1. Kliknij prawym przyciskiem myszy czerwoną kropkę reprezentującą punkt przerwania, a następnie wybierz pozycję **warunki**. W polu edycji dla warunku wprowadź `(y == 0) && (oper == '/')` . Po zakończeniu wybierz przycisk **Zamknij** . Warunek jest automatycznie zapisywany.

   ![Ustaw punkt przerwania warunkowego](./media/calculator-conditional-breakpoint.gif "Ustaw punkt przerwania warunkowego")

   Teraz wstrzymamy wykonywanie w punkcie przerwania, w przypadku próby dzielenia przez 0.

1. Aby debugować program, naciśnij klawisz **F5**lub wybierz przycisk paska narzędzi **lokalnego debugera systemu Windows** , który ma ikonę zielonej strzałki. W aplikacji konsolowej, jeśli wprowadzisz coś takiego jak "5-0", program zachowuje się normalnie i nadal działa. Jednak jeśli wpiszesz "10/0", zostanie on wstrzymany w punkcie przerwania. Można nawet umieścić dowolną liczbę spacji między operatorem i liczbami. `cin`jest wystarczająco inteligentny, aby odpowiednio analizować dane wejściowe.

   ![Wstrzymaj w warunkowym punkcie przerwania](./media/calculator-debug-conditional.gif "Wstrzymaj w warunkowym punkcie przerwania")

### <a name="useful-windows-in-the-debugger"></a>Przydatne okna w debugerze

Za każdym razem, gdy debugujesz kod, możesz zauważyć, że pojawiły się niektóre nowe okna. Te okna mogą pomóc w debugowaniu. Zapoznaj się z oknem **Autokorekty** . W oknie **samochody** są wyświetlane bieżące wartości zmiennych używanych co najmniej trzy wiersze przed i do bieżącego wiersza.

   ![Okno Autokorekty](./media/calculator-autos.png "Okno Autokorekty")

Aby wyświetlić wszystkie zmienne z tej funkcji, przełącz się do okna **zmiennych lokalnych** . Można faktycznie zmodyfikować wartości tych zmiennych podczas debugowania, aby zobaczyć, jaki wpływ ma w programie. W takim przypadku pozostawimy je samodzielnie.

   ![Okno zmiennych lokalnych](./media/calculator-locals.png "Okno zmiennych lokalnych")

Możesz również po prostu umieścić kursor nad zmiennymi w kodzie, aby zobaczyć ich bieżące wartości, w przypadku których wykonywanie jest obecnie wstrzymane. Upewnij się, że okno edytora jest fokusem, klikając je najpierw.

   ![Aktywuj, aby wyświetlić bieżące wartości zmiennych](./media/calculator-hover-tooltip.gif "Aktywuj, aby wyświetlić bieżące wartości zmiennych")

### <a name="to-continue-debugging"></a>Aby kontynuować debugowanie

1. Żółty wiersz po lewej stronie pokazuje bieżący punkt wykonania. Bieżące wywołania wiersza `Calculate` , dlatego naciśnij klawisz **F11** , aby **przejść** do funkcji. Znajdziesz Cię w treści `Calculate` funkcji. Należy zachować ostrożność **krok po kroku**. w przypadku zbyt dużej ilości czasu może to spowodować marnowanie. Zawiera kod, który jest używany w wierszu, w którym pracujesz, w tym funkcje biblioteki standardowej.

1. Teraz, gdy punkt wykonywania jest na początku `Calculate` funkcji, naciśnij klawisz **F10** , aby przejść do następnego wiersza w wykonaniu programu. **F10** jest również znany jako **krok powyżej**. Możesz użyć przechodzenia **krok po kroku** , aby przejść od wiersza do wiersza, bez podania do szczegółów co się dzieje w każdej części wiersza. Ogólnie rzecz biorąc, należy użyć przekroczenia **kroku** zamiast **wkroczenia do**, chyba że chcesz szczegółowe bardziej głęboko kod, który jest wywoływany z innego miejsca (jak miało miejsce do uzyskania treści `Calculate` ).

1. Kontynuuj używanie klawisza **F10** , **Aby przekroczyć** każdy wiersz do momentu powrotu do `main()` funkcji w innym pliku, i zatrzymaj ją w `cout` wierszu.

   ![Wyjdź z obliczeń i wyników sprawdzenia](./media/calculator-undefined-zero.gif "Wyjdź z obliczeń i wyników sprawdzenia")

   Wygląda na to, że program wykonuje oczekiwane działania: Pobiera pierwszą liczbę i dzieli go przez drugi. W `cout` wierszu Umieść wskaźnik myszy nad zmienną lub zapoznaj się `result` `result` z oknem **Autokorekty** . Zobaczysz, że wartość zostanie wyświetlona na liście jako "inf", która nie wygląda w prawidłowym stanie, więc naprawimy ją. `cout`Wiersz tylko wyprowadza dane, które są przechowywane w `result` , więc po przekroczeniu kolejnej linii do przodu przy użyciu klawisza **F10**zostanie wyświetlone okno konsoli:

   ![Wynik dzielenia przez zero](./media/calculator-divide-by-zero-fail.png "Wynik dzielenia przez zero")

   Wynika to z faktu, że dzielenie przez zero jest niezdefiniowane, więc program nie ma numerycznej odpowiedzi na żądaną operację.

### <a name="to-fix-the-divide-by-zero-error"></a>Aby naprawić błąd "dzielenie przez zero"

Przyjrzyjmy się dzielenie przez zero, dzięki czemu użytkownik może zrozumieć problem.

1. Wprowadź następujące zmiany w *CalculatorTutorial. cpp*. (Można pozostawić program uruchomiony podczas edycji, dzięki funkcji debugera o nazwie **Edytuj i Kontynuuj**):

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b" << endl;

        Calculator c;
        while (true)
        {
            cin  >> x  >> oper  >> y;
            if (oper == '/' && y == 0)
            {
                cout << "Division by 0 exception" << endl;
                continue;
            }
            else
            {
                result = c.Calculate(x, oper, y);
            }
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

1. Teraz naciśnij klawisz **F5** . Wykonanie programu jest kontynuowane aż do momentu zaczekania na podanie danych wejściowych użytkownika. Wprowadź `10 / 0` ponownie. Teraz zostanie wydrukowany bardziej przydatny komunikat. Użytkownik jest monitowany o więcej danych wejściowych, a program kontynuuje wykonywanie normalnie.

   ![Wynik końcowy po zmianach](./media/calculator-final-verification.gif "Wynik końcowy po zmianach")

   > [!Note]
   > Gdy edytujesz kod w trybie debugowania, istnieje ryzyko, że kod staje się przestarzały. Dzieje się tak, gdy debuger nadal działa w starym kodzie i nie został jeszcze zaktualizowany ze zmianami. Debuger wyświetli okno dialogowe, aby poinformować użytkownika o tym, kiedy się dzieje. Czasami może być konieczne naciśnięcie klawisza **F5** w celu odświeżenia wykonywanego kodu. W szczególności w przypadku wprowadzenia zmiany wewnątrz funkcji, gdy punkt wykonywania znajduje się wewnątrz tej funkcji, należy wykonać krok poza funkcję, a następnie ponownie w celu uzyskania zaktualizowanego kodu. Jeśli to nie zadziała z jakiegoś powodu, a zobaczysz komunikat o błędzie, możesz zatrzymać debugowanie, klikając czerwony kwadrat na pasku narzędzi w menu u góry IDE, a następnie ponownie Rozpocznij debugowanie, wprowadzając klawisz **F5** lub wybierając zieloną strzałkę "Odtwórz" obok przycisku Zatrzymaj na pasku narzędzi.

   > Informacje o skrótach uruchamiania i debugowania
   >
   > - **F5** (lub **Debuguj**  >  **Rozpocznij debugowanie**) uruchamia sesję debugowania, jeśli jedna nie jest już aktywna, i uruchamia program do momentu trafienia punktu przerwania lub program wymaga wprowadzenia danych przez użytkownika. Jeśli żadne dane wejściowe użytkownika nie są konieczne i punkt przerwania nie jest dostępny do trafienia, program zostanie przerwany, a okno konsoli zostanie zamknięte po zakończeniu działania programu. Jeśli masz coś takiego jak program "Hello world" do uruchomienia, użyj **kombinacji klawiszy CTRL + F5** lub ustaw punkt przerwania, **Aby zachować** otwarte okno.
   > - **Ctrl + F5** (lub **Debuguj**  >  **Uruchom bez debugowania**) uruchamia aplikację bez przechodzenia do trybu debugowania. Jest to nieco szybsze niż debugowanie, a okno konsoli pozostaje otwarte po zakończeniu wykonywania przez program.
   > - **F10** (znany jako **przekroczenie**) umożliwia przechodzenie przez kod, wiersz po wierszu i wizualizację sposobu uruchamiania kodu oraz zmienne wartości w każdym kroku wykonania.
   > - **F11** (znany jako **krok do**) działa podobnie do **przekroczenia, z**wyjątkiem przypadków, w których są wywoływane wszystkie funkcje w wierszu wykonania. Na przykład, jeśli wykonywany wiersz wywołuje funkcję, naciśnięcie klawisza **F11** przenosi wskaźnik do treści funkcji, dzięki czemu można wykonać kod funkcji uruchamianej przed powrotem do wiersza, który został rozpoczęty. Naciskaj kroki **F10** w wywołaniu funkcji i po prostu przesuniesz się do następnego wiersza. Wywołanie funkcji jest nadal wykonywane, ale program nie jest wstrzymany, aby zobaczyć, co robi.

### <a name="close-the-app"></a>Zamknij aplikację

- Jeśli nadal działa, Zamknij okno konsoli dla aplikacji Kalkulator.

## <a name="the-finished-app"></a>Gotowa aplikacja

Gratulacje! Kod aplikacji kalkulatora został ukończony i skompilowany i debugowany w programie Visual Studio.

## <a name="next-steps"></a>Następne kroki

[Dowiedz się więcej o programie Visual Studio dla języka C++](https://devblogs.microsoft.com/cppblog/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end
