---
title: Tworzenie projektu aplikacji konsoli w języku C++
description: Tworzenie aplikacji Hello World konsoli i aplikacja Kalkulator w programie Visual C++
ms.custom: mvc
ms.date: 03/25/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: b15bc7551c4bf99b6dd52f99bb5e69064ddb8308
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58867267"
---
# <a name="create-a-c-console-app-project"></a>Tworzenie projektu aplikacji konsoli w języku C++

Zwykle początkowy punkt jest programistą języka C++ "Hello, world!" Aplikacja, która jest uruchamiana w wierszu polecenia. To, co utworzysz w programie Visual Studio w tym artykule, a następnie przejdziemy do coś trudniejsze: aplikacja Kalkulator.

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio za pomocą **programowanie aplikacji klasycznych w języku C++** obciążenia zainstalowana i uruchomiona na komputerze. Jeśli nie jest jeszcze zainstalowany, zobacz [Instalowanie obsługi języka C++ w programie Visual Studio](../../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Utwórz projekt aplikacji

Program Visual Studio używa *projektów* organizowania kodu dla aplikacji, a *rozwiązania* do organizowania projektów. Projekt zawiera wszystkie opcje, konfiguracji i reguły używane do tworzenia aplikacji. Umożliwia także zarządzanie relacji między plików wszystkich projektów i plików zewnętrznych. Aby utworzyć aplikację, najpierw należy utworzyć nowy projekt i rozwiązanie.

1. Na pasku menu w programie Visual Studio wybierz **pliku** > **New** > **projektu**. **Nowy projekt** zostanie otwarte okno.

2. Na lewym pasku bocznym, upewnij się, że **Visual C++** jest zaznaczone. W Centrum, wybierz **aplikacji konsoli Windows**.

3. W **nazwa** Edytuj pole u dołu, nadaj nazwę nowego projektu *CalculatorTutorial*, następnie wybierz **OK**.

   ![Okno dialogowe Nowy projekt](./media/calculator-new-project-dialog.png "okna dialogowego Nowy projekt")

   Zostanie utworzona pusta Aplikacja konsoli Windows w języku C++. Aplikacje konsoli użyj okna konsoli Windows do wyświetlania danych wyjściowych i akceptuje dane wejściowe użytkownika. W programie Visual Studio okno edytora otwiera się i pokazuje wygenerowanego kodu:

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

## <a name="verify-that-your-new-app-builds-and-runs"></a>Sprawdź, czy Twoja nowa aplikacja kompiluje i uruchamia

Szablon dla nowej aplikacji konsoli systemu windows umożliwia utworzenie prostego języka C++ aplikacji "Hello World". W tym momencie widać, jak Visual Studio kompiluje i uruchamia aplikacje, które można tworzyć bezpośrednio z poziomu środowiska IDE.

1. Aby skompilować projekt, wybierz opcję **Kompiluj rozwiązanie** z **kompilacji** menu. **Dane wyjściowe** okno przedstawia wyniki procesu kompilacji.

   ![Skompiluj projekt](./media/calculator-initial-build-output.png "kompilacji projektu")

1. Aby uruchomić kod, na pasku menu, wybierz **debugowania**, **Uruchom bez debugowania**.

   ![Rozpocznij projekt](./media/calculator-hello-world-console.png "Rozpocznij projekt")

   Okno konsoli zostanie otwarty, a następnie uruchamia aplikację. Po uruchomieniu aplikacji konsoli w programie Visual Studio działa kod, a następnie drukuje "naciśnij dowolny klawisz, aby kontynuować. . ." daje szansę, aby wyświetlić dane wyjściowe. Gratulacje! Utworzono pierwszej "Hello, world!" Aplikacja konsoli w programie Visual Studio!

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i powrócić do programu Visual Studio.

Masz teraz narzędzia, aby skompilować i uruchomić aplikację po każdej zmianie, aby sprawdzić, czy kod nadal działa zgodnie z oczekiwaniami. Później pokażemy sposób jej debugowania, w przeciwnym razie.

## <a name="edit-the-code"></a>Edytowanie kodu

Teraz możemy przekształcając kod w tym szablonie aplikacja Kalkulator.

1. W *CalculatorTutorial.cpp* plik, Edytuj kod w celu dopasowania w tym przykładzie:

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

   > Znajomość kodu:
   >
   > - `#include` Instrukcje umożliwiają odwoływać się do kodu w innych plikach. Czasami może zostać wyświetlony nazwa pliku ujęta w nawiasy (**\<\>**); w innych sytuacjach jest ujęta w cudzysłowy (**""**). Ogólnie rzecz biorąc nawiasy są używane podczas odwoływania się do standardowej biblioteki C++, cudzysłowy są używane dla innych plików.
   > - `#include "pch.h"` (Lub w starszych wersjach programu Visual Studio `#include "stdafx.h"`) wiersza odwołuje się coś, co jest znane jako prekompilowanego nagłówka. Te są często używane przez programistów professional do skrócenia czasu kompilacji, ale są one poza zakres tego samouczka.
   > - `using namespace std;` Wiersza informuje kompilator, aby oczekiwać rzeczy ze standardowej biblioteki C++ ma być używany w tym pliku. Bez tego wiersza, każde słowo kluczowe z biblioteki, musi być poprzedzony znakiem `std::`, aby wskazać jej zakresu. Na przykład, bez tego wiersza każdy odwołanie do `cout` , musi być zapisana jako `std::cout`. `using` Instrukcji jest dodawany do kodu wyglądają przejrzyście więcej.
   > - `cout` — Słowo kluczowe jest używany do drukowania do wyjścia standardowego języka C++. **\< \<** Operator informuje kompilator, aby wysłać dowolną jest po prawej stronie go do wyjścia standardowego.
   > - **Endl** — słowo kluczowe przypomina klawisza Enter; zakończenia wiersza i przenosi kursor do następnego wiersza. Lepiej jest umieścić `\n` wewnątrz ciągu (zawarty w ""), aby zrobić to samo, jak `endl` zawsze opróżnia bufor i może obniżyć wydajność programu, ale ponieważ jest to bardzo mała aplikacja `endl` jest używana zamiast tego uzyskać lepszy czytelności.
   > - Wszystkie instrukcje języka C++ musi kończyć się znakami średnika i wszystkich aplikacji w języku C++ musi zawierać `main()` funkcji. Ta funkcja jest program będzie uruchamiany na początku. Cały kod musi być dostępny z `main()` aby możliwe było użycie.

1. Aby zapisać plik, wprowadź **Ctrl + S**, lub wybierz **Zapisz** ikony w górnej części IDE, ikonę dyskietki, na pasku narzędzi poniżej paska menu.

1. Aby uruchomić aplikację, naciśnij klawisz **kombinację klawiszy Ctrl + F5** lub przejdź do **debugowania** menu i wybrać **Rozpocznij bez debugowania**. Jeśli pojawi się okno podręczne, które mówi **ten projekt jest nieaktualny**, można wybrać **nie pokazuj więcej tego okna dialogowego**, a następnie wybierz **tak** do budowania aplikacji. Powinien zostać wyświetlony pojawiają się okna konsoli wyświetlającego tekst określony w kodzie.

   ![Skompilować i uruchomić aplikację](./media/calculator-first-launch.gif "skompilować i uruchomić aplikację")

1. Gdy skończysz, zamknij okno konsoli.

## <a name="add-code-to-do-some-math"></a>Dodaj kod będzie robił talent matematyczny

Nadszedł czas, aby dodać logikę matematyczne.

### <a name="to-add-a-calculator-class"></a>Aby dodać klasę Kalkulator

1. Przejdź do **projektu** menu i wybrać **Dodaj klasę**. W **Nazwa klasy** edytować pole, wprowadź *Kalkulator*. Wybierz **OK**. Poproś o dodanie Cię dwa nowe pliki do projektu. Aby zapisać wszystkie zmienione pliki naraz, naciśnij **Ctrl + Shift + S**. Jest skrót klawiaturowy **pliku** > **Zapisz wszystko**. Dostępna jest również przycisku paska narzędzi dla **Zapisz wszystko**, ikony dwóch dyskietek, znaleziono obok **Zapisz** przycisku. Ogólnie rzecz biorąc, dobrym rozwiązaniem w celu jest **Zapisz wszystko** często, dlatego nie zostały pominięte pliki podczas zapisywania.

   ![Utwórz klasę Kalkulator](./media/calculator-create-class.gif "Utwórz klasę Kalkulator")

   Klasa jest podobna do planu dla obiektu, który wykonuje coś. W tym przypadku definiujemy Kalkulator i jak powinny działać. **Dodaj klasę** kreatora zostały użyte powyżej, utworzyć pliki .h i .cpp, które mają taką samą nazwę jak klasa. Można wyświetlić pełną listę plików projektu w **Eksploratora rozwiązań** okna widoczne po stronie IDE. Jeśli okno nie jest widoczny, możesz go otworzyć, na pasku menu: Wybierz **widoku** > **Eksploratora rozwiązań**.

   ![Eksplorator rozwiązań](./media/calculator-solution-explorer.png "Eksploratora rozwiązań")

   Teraz powinny być otwartych w edytorze trzech kart: *CalculatorTutorial.cpp*, *Calculator.h*, i *Calculator.cpp*. Jeśli przypadkowo zamknięty jeden z nich, możesz uruchomić go, klikając go dwukrotnie **Eksploratora rozwiązań** okna.

1. W **Calculator.h**, Usuń `Calculator();` i `~Calculator();` wierszy, które zostały wygenerowane, ponieważ nie będą potrzebne w tym miejscu. Następnie dodaj następujący wiersz kodu, dzięki czemu pliku wygląda teraz następująco:

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > Znajomość kodu
   >
   > - Wiersz został dodany deklaruje nową funkcję o nazwie `Calculate`, które będą używane do uruchamiania operacji matematycznych na dodawanie, odejmowanie, mnożenie i dzielenie.
   > - Kod języka C++ jest podzielony na *nagłówka* plików (.h) i *źródła* plików (.cpp). Kilka innych rozszerzeń plików są obsługiwane przez różne kompilatory, ale są najważniejsze z nich wiedzieć o. Funkcje i zmienne są zazwyczaj *zadeklarowana*, która jest podanej nazwy i typu, w plikach nagłówkowych i *zaimplementowane*, lub definicję w plikach źródłowych. Aby kod dostępu zdefiniowane w innym pliku, można użyć `#include "filename.h"`, gdzie "filename.h" to nazwa pliku, który deklaruje zmiennych lub funkcji, której chcesz użyć.
   > - Dwa wiersze, możesz usunąć zadeklarowana *Konstruktor* i *destruktor* dla klasy. Proste klasy podobny do tego kompilator utworzy je, a ich wykorzystania wykraczają poza zakres tego samouczka.
   > - Jest dobrą praktyką, aby zorganizować kodu w różnych plikach uzależnione od tak jest, więc można łatwo znaleźć kod, który będzie potrzebna później. W naszym przypadku definiujemy `Calculator` klasy oddzielnie od pliku zawierającego `main()` funkcji, ale firma Microsoft planuje odwołania `Calculator` klasy w `main()`.

1. Zostanie wyświetlony zielony wężyk, są wyświetlane w obszarze `Calculate`. To, że mamy jeszcze nie zdefiniowano `Calculate` funkcji w pliku .cpp. Umieść kursor nad wyraz, kliknij ikonę żarówki, które się pojawi, a następnie wybierz **Tworzenie definicji "Oblicz" w Calculator.cpp**. Okno podręczne pojawi się podglądu zmiany kodu, która została wprowadzona w innym pliku. Ten kod został dodany do *Calculator.cpp*.

   ![Utwórz definicję Calculate](./media/calculator-create-definition.gif "Utwórz definicję Calculate")

   Obecnie tylko zwraca wartość 0,0. Teraz zmienimy. Naciśnij klawisz **Esc** zamknąć to okno.

1. Przełącz się do *Calculator.cpp* pliku w oknie edytora. Usuń `Calculator()` i `~Calculator()` sekcje (tak jak w pliku .h) i Dodaj następujący kod do `Calculate()`:

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

   > Znajomość kodu
   >
   > - Funkcja `Calculate` zużywa wiele, operator i drugą liczbę, a następnie wykonuje żądaną operację dla numerów.
   > - Kontroli instrukcji switch operator, który został podany i tylko wtedy wykonuje przypadek odpowiadający tej operacji. Wartość domyślna: wielkość liter jest rezerwowe w przypadku, gdy użytkownik wpisze operatora, który nie jest akceptowane, dzięki czemu program nie zostanie przerwane. Ogólnie rzecz biorąc zaleca się obsługiwać dane wejściowe użytkownika nieprawidłowe w sposób bardziej elegancki, ale to wykracza poza zakres tego samouczka.
   > - `double` — Słowo kluczowe wskazuje typ numer, który obsługuje liczbę miejsc dziesiętnych. W ten sposób Kalkulator może obsługiwać zarówno matematyczne dziesiętny, jak i matematyki całkowitoliczbowej. `Calculate` Funkcji jest wymagany, aby zawsze zwracać liczbę ze względu na `double` na samym początku kodu (oznacza typ zwracany przez funkcję), dlatego zostanie zwrócona 0.0 nawet w przypadku domyślnej.
   > - Plik .h deklaruje funkcję *prototypu*, który informuje kompilator, ponoszonych z góry kosztów wymagane parametry i jakie zwracany typ można oczekiwać od niego. Plik CPP zawiera wszystkie szczegóły dotyczące implementacji funkcji.

Jeśli skompilować i uruchomić ponownie na tym etapie kod, nadal zakończy działanie po zapytaniu do wykonywania kolejnej operacji. Następnie zmodyfikujesz `main` funkcji do wykonywania niektórych obliczeń.

### <a name="to-call-the-calculator-class-member-functions"></a>Aby wywoływać funkcje składowe klasy Kalkulator

1. Teraz zaktualizujmy `main` działa w programach *CalculatorTutorial.cpp*:

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

   > Znajomość kodu
   >
   > - Ponieważ programy w języku C++ zawsze rozpoczynają się od `main()` funkcji, należy wywołać kodu języka w tym miejscu, więc `#include` instrukcji jest wymagana.
   > - Niektóre wstępne zmienne `x`, `y`, `oper`, i `result` są uznane za przechowywanie pierwsza liczba, druga liczba, operator i wynik końcowy odpowiednio. Zawsze jest dobrą praktyką, aby dać im niektóre wartości początkowe, aby uniknąć niezdefiniowane zachowanie, czyli o tym, co to jest wykonywane tutaj.
   > - `Calculator c;` Wiersz deklaruje obiektu o nazwie "c", ponieważ wystąpienie `Calculator` klasy. Ta sama klasa to po prostu plan dla działania kalkulatory; obiekt jest określone Kalkulator, która wykonuje obliczenia.
   > - `while (true)` Instrukcja jest pętlą. Kod wewnątrz pętli kontynuuje wykonywanie wielokrotnie tak długo, jak warunku wewnątrz `()` prawdziwe. Ponieważ warunek jest po prostu wyświetlane jako `true`, jest zawsze ma wartość true, więc kiedy pętla zostanie uruchomiona w nieskończoność. Aby zamknąć program, użytkownik musi ręcznie zamknąć okno konsoli. W przeciwnym razie program zawsze czeka, aż nowe dane wejściowe.
   > - `cin` Słowo kluczowe jest używane do przyjmowania danych wejściowych od użytkownika. Ten strumień wejściowy pozostaje inteligentnego przetworzył wiersz z tekstem wprowadzonym w oknie konsoli i umieścić go w każdej zmienne wymienione w kolejności, zakładając, że dopasowania danych wejściowych użytkownika wymaganymi specyfikacjami. Można zmodyfikować tego wiersza, aby zaakceptować różnego rodzaju danych wejściowych, na przykład więcej niż dwie liczby, mimo że `Calculate()` funkcji również musi zostać zaktualizowany do obsługi tego.
   > - `c.Calculate(x, oper, y);` Wywołań wyrażeń `Calculate` funkcję wcześniej zdefiniowaną i dostarcza wprowadzone wartości wejściowych. Następnie funkcja zwraca liczbę, która zostaje zapisany w `result`.
   > - Na koniec `result` są drukowane w konsoli, użytkownik zobaczy następujący wynik obliczenia.

### <a name="build-and-test-the-code-again"></a>Tworzenie i testowanie kodu ponownie

Nadszedł czas na przetestowanie program ponownie, aby upewnić się, że wszystko działa prawidłowo.

1. Naciśnij klawisz **kombinację klawiszy Ctrl + F5** Aby ponownie skompilować i uruchomić aplikację.

1. Wprowadź `5 + 5`i naciśnij klawisz **Enter**. Sprawdź, czy wynik jest 10.

   ![Wynik 5 + 5](./media/calculator-five-plus-five.png "wynik 5 + 5")

## <a name="debug-the-app"></a>Debugowanie aplikacji

Ponieważ użytkownik może wpisać cokolwiek w oknie konsoli, upewnij się, że Kalkulator obsługuje dane wejściowe, zgodnie z oczekiwaniami. Zamiast uruchamiania programu, Przyjrzyjmy debugować go zamiast tego, dzięki czemu można sprawdzić, co wykonywanie operacji szczegółowe instrukcje krok po kroku.

### <a name="to-run-the-app-in-the-debugger"></a>Aby uruchomić aplikację w debugerze

1. Ustaw punkt przerwania na `result = c.Calculate(x, oper, y);` wiersz po użytkownik został poproszony o wprowadzenie danych. Aby ustawić punkt przerwania, kliknij obok wiersza w szarym pionowy pasek wzdłuż lewej krawędzi okna edytora. Pojawi się czerwona kropka.

   ![Ustaw punkt przerwania](./media/calculator-set-breakpoint.gif "Ustaw punkt przerwania")

   Teraz gdy mamy zdebugować program, zawsze wstrzymuje wykonywanie w danym wierszu. Mamy już pomysłem przybliżoną, program działa w przypadku prostych przypadkach. Ponieważ nie chcemy zatrzymać wykonywanie każdym razem, gdy, upewnijmy się, punkt przerwania warunkowe.

1. Kliknij prawym przyciskiem myszy czerwoną kropkę, która reprezentuje punkt przerwania, a następnie wybierz **warunki**. W polu edycji dla warunku, wprowadź `(y == 0) && (oper == '/')`. Wybierz **Zamknij** przycisk po wykonaniu tych czynności. Warunek są zapisywane automatycznie.

   ![Ustaw warunkowego punktu przerwania](./media/calculator-conditional-breakpoint.gif "Ustaw warunkowego punktu przerwania")

   Teraz możemy zatrzymać wykonywanie w punkcie przerwania, szczególnie w przypadku, gdy dzielenie przez 0 jest podejmowana próba.

1. Aby zdebugować program, naciśnij klawisz **F5**, lub wybierz **lokalny debuger Windows** przycisku paska narzędzi, który zawiera ikonę zieloną strzałkę. W aplikacji konsoli po wprowadzeniu podobny do "5-0" pracował normalnie program jest uruchomiony. Jednakże jeśli wpiszesz "10 / 0", wstrzymuje w punkcie przerwania. Możesz nawet umieścić dowolną liczbę spacji między operatora i liczbami dodatnimi. `cin` inteligentny, można przeanalizować danych wejściowych, odpowiednio.

   ![Wstrzymaj na warunkowego punktu przerwania](./media/calculator-debug-conditional.gif "wstrzymania na warunkowego punktu przerwania")

### <a name="useful-windows-in-the-debugger"></a>Przydatne systemu windows w debugerze

Zawsze, gdy debugujesz kod, możesz zauważyć, czy są wyświetlane niektóre z nowych oknach. Okna te mogą pomóc środowisko debugowania. Przyjrzyj się **Autos** okna. **Autos** okno zawiera bieżące wartości zmiennych używane co najmniej trzy wiersze przed, jak i do bieżącego wiersza.

   ![Okno zmiennych automatycznych](./media/calculator-autos.png "okno zmiennych automatycznych")

Aby wyświetlić wszystkie zmienne z tej funkcji, przełącz się do **lokalne** okna. Faktycznie można zmodyfikować wartości tych zmiennych podczas debugowania, aby zobaczyć, jaki będzie wpływ, jakie miałby on program. W tym przypadku pozostawimy je samodzielnie.

   ![Okno zmiennych lokalnych](./media/calculator-locals.png "okno zmiennych lokalnych")

Możesz też po prostu umieść kursor nad zmiennych w kodzie, aby zobaczyć ich bieżącymi wartościami, których wykonywania jest obecnie wstrzymana. Upewnij się, że okno edytora jest w trybie koncentracji uwagi, klikając ją najpierw.

   ![Po wskazaniu wskaźnikiem, aby wyświetlić bieżące wartości zmiennych](./media/calculator-hover-tooltip.gif "po wskazaniu wskaźnikiem, aby wyświetlić bieżące wartości zmiennych")

### <a name="to-continue-debugging"></a>Aby kontynuować debugowanie

1. Żółta linia po lewej stronie pokazuje bieżący punkt wykonania. Bieżące połączenia linii `Calculate`, więc naciśnij **F11** do **Step Into** funkcji. Znajdziesz się w treści `Calculate` funkcji. Należy zachować ostrożność **Step Into**; Jeśli zrobisz to zbyt dużo mogą tracić dużo czasu. Usługa zostanie wprowadzona do żadnego kodu, używanego na wiersz, w którym korzystasz, łącznie z funkcjami biblioteki standardowej.

1. Teraz, gdy punkt wykonania jest na początku `Calculate` funkcji, naciśnij klawisz **F10** można przenieść do następnego wiersza, podczas wykonywania programu. **F10** jest także znana jako **Step Over**. Możesz użyć **Step Over** przenieść wiersz po wierszu, bez wcześniejszego zagłębieniem się w szczegóły co się dzieje w każdej części wiersza. Ogólnie rzecz biorąc należy używać **Step Over** zamiast **Step Into**, chyba że chcesz od razu rozpocząć korzystanie w głębiej do kodu, który jest wywoływany z innego miejsca (tak jak nawiązać połączenie treści `Calculate`).

1. Nadal korzystać z **F10** do **Step Over** każdym wierszu, aż powrócisz do `main()` działać w innym pliku i zatrzymania na `cout` wiersza.

   ![Wyjdź z Calculate i sprawdź wynik](./media/calculator-undefined-zero.gif "wychodzenia z Calculate i sprawdź wynik")

   Prawdopodobnie program robi, oczekiwano: Trwa pierwsza liczba i dzieli go przez drugi. Na `cout` wiersz, umieść kursor nad `result` zmiennej lub Przyjrzyj się `result` w **Autos** okna. Zobaczysz, że jego wartość jest wyświetlana na liście "inf", który jest prawdopodobnie nieprawidłowa, więc go naprawić. `cout` Wiersza po prostu dane wyjściowe, niezależnie od wartości są przechowywane w `result`, dlatego w przypadku wkroczenia do przodu jeszcze jeden wiersz, za pomocą **F10**, w oknie konsoli zostaną wyświetlone:

   ![Wynik dzielenia przez zero](./media/calculator-divide-by-zero-fail.png "wynik dzielenia przez zero")

   Ten wynik wynika z faktu, dzielenie przez zero jest niezdefiniowana, więc nie ma wartości liczbowych odpowiedzi do żądanej operacji.

### <a name="to-fix-the-divide-by-zero-error"></a>Aby naprawić błąd "dzielenie przez zero"

Umożliwia dzielenie przez zero bardziej bezpiecznie obsłużyć, dzięki czemu użytkownik może zrozumieć.

1. Wprowadź następujące zmiany w *CalculatorTutorial.cpp*. (Można pozostawić program uruchomiony podczas edycji, dzięki funkcji debugera, o nazwie **Edytuj i Kontynuuj**):

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

1. Teraz naciśnij **F5** po. Wykonanie programu jest kontynuowane aż, dopóki nie można wstrzymać poprosić o dane wejściowe użytkownika. Wprowadź `10 / 0` ponownie. Teraz bardziej użyteczne komunikat jest drukowany. Użytkownik jest monitowany o więcej danych wejściowych, a program kontynuuje wykonywanie w zwykły sposób.

   ![Wynik końcowy po wprowadzeniu zmian](./media/calculator-final-verification.gif "ostateczny wynik po wprowadzeniu zmian")

   > [!Note]
   > Podczas edytowania kodu podczas debugowania w trybie się ryzyko kodu stają się nieaktualne. Dzieje się tak, gdy debuger jest nadal uruchomiona stary kod i nie został jeszcze zaktualizowany go z wprowadzonymi zmianami. Debuger pojawi się okno dialogowe informujące o tym, w takim przypadku. Czasami konieczne może być naciśnij **F5** odświeżyć wykonywany kod. W szczególności w przypadku wprowadzenia zmiany wewnątrz funkcji podczas punkt wykonania znajduje się wewnątrz, funkcji, musisz wychodzenie z funkcji, a następnie z powrotem do ją ponownie, aby uzyskać zaktualizowany kod. Jeśli to nie zadziała, przyczyny i zostanie wyświetlony komunikat o błędzie, możesz zatrzymać debugowanie, klikając czerwony kwadrat na pasku menu w górnej części IDE, a następnie rozpocząć debugowanie ponownie, wprowadzając **F5** lub wybierając na zielony wskaźnik " odtwarzania"strzałka obok przycisku Zatrzymaj, na pasku narzędzi.
   
   > Opis skrótów uruchamiania i debugowania
   >
   > - **F5** (lub **debugowania** > **Rozpocznij debugowanie**) rozpoczyna sesję debugowania, jeśli nie jest już aktywne i uruchamia program, dopóki nie zostanie osiągnięty punkt przerwania lub danych wejściowych programu potrzeb użytkownika. Jeśli dane wejściowe użytkownika nie jest wymagana i nie punkt przerwania jest dostępna dla trafień, program zakończy, a następnie w oknie konsoli zamyka się po zakończeniu program. Jeśli masz podobny do programu "Hello World", aby uruchomić, użyj **kombinację klawiszy Ctrl + F5** lub ustaw punkt przerwania, możesz wprowadzić **F5** do nie zamykaj okna.
   > - **CTRL + F5** (lub **debugowania** > **Rozpocznij bez debugowania**) uruchamia aplikację bez przechodzenia w tryb debugowania. Jest to nieznacznie szybsze niż debugowania, a w oknie konsoli pozostanie otwarte po zakończeniu program, wykonywanie.
   > - **F10** (nazywane **Step Over**) umożliwia iteracyjne przeglądanie kodu, wiersz po wierszu oraz Wizualizuj działanie kodu i wartości zmiennych są w każdym kroku wykonywania.
   > - **F11** (nazywane **Step Into**) działa podobnie jak **Step Over**, z wyjątkiem przechodzi do wszelkie funkcje wywołane w wierszu wykonywania. Na przykład, jeśli wykonywanego wiersza wywołuje funkcję, naciskając klawisz **F11** przesuwa wskaźnik myszy w treści funkcji, aby można było wykonywać kod funkcji, które są uruchamiane przed powrotem do wiersza rozpoczęło się o. Naciśnięcie klawisza **F10** kroki za pośrednictwem wywołania funkcji i po prostu przechodzi do następnego wiersza; wywołania funkcji nadal się dzieje, ale program nie wstrzymać WAM, jakie jest zastosowanie.

### <a name="close-the-app"></a>Zamknij aplikację

1. Jeśli jest nadal uruchomione, zamknij okno konsoli aplikacji kalkulatora.

## <a name="the-finished-app"></a>Gotową aplikację

Gratulacje! Ukończysz kodu dla aplikacji Kalkulator i wbudowane i debugować go w programie Visual Studio.

## <a name="next-steps"></a>Następne kroki

[Dowiedz się więcej o programie Visual Studio dla języka C++](https://blogs.msdn.microsoft.com/vcblog/2017/04/21/getting-started-with-visual-studio-for-c-and-cpp-development/)
