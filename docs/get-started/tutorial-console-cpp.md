---
title: Tworzenie projektu aplikacji konsoli w języku C++
description: Tworzenie aplikacji konsoli Hello World i aplikacji kalkulatora w języku Visual C++
ms.custom: mvc
ms.date: 08/19/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 27522a6960546dc935ea3d9bce974eb36789c0aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "80079288"
---
# <a name="create-a-c-console-app-project"></a>Tworzenie projektu aplikacji konsoli w języku C++

::: moniker range=">=vs-2019"

Zwykle punktem wyjścia dla programisty C++ jest "Cześć, świat!" aplikacja, która działa w wierszu polecenia. To, co utworzysz w programie Visual Studio w tym artykule, a następnie przejdziemy do czegoś trudniejszego: aplikacji kalkulatora.

## <a name="prerequisites"></a>Wymagania wstępne

- Mieć Visual Studio z **pulpitu rozwoju z c++** obciążenia zainstalowanego i uruchomionego na komputerze. Jeśli nie jest jeszcze zainstalowany, zobacz [Instalowanie pomocy technicznej języka C++ w programie Visual Studio](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Tworzenie projektu aplikacji

Visual Studio używa *projektów* do organizowania kodu dla aplikacji i *rozwiązań* do organizowania projektów. Projekt zawiera wszystkie opcje, konfiguracje i reguły używane do tworzenia aplikacji. Zarządza również relacją między wszystkimi plikami projektu a wszelkimi plikami zewnętrznymi. Aby utworzyć aplikację, najpierw utworzysz nowy projekt i rozwiązanie.

1. Jeśli właśnie rozpoczęto program Visual Studio, zobaczysz okno dialogowe Visual Studio 2019. Wybierz **pozycję Utwórz nowy projekt,** aby rozpocząć.

   ![Początkowe okno dialogowe programu Visual Studio 2019](./media/calc-vs2019-initial-dialog.png "Początkowe okno dialogowe programu Visual Studio 2019")

   W przeciwnym razie na pasku menu w programie Visual Studio wybierz pozycję **Plik** > **nowego** > **projektu**. Zostanie otwarte okno **Utwórz nowy projekt.**

1. Na liście szablonów projektów wybierz pozycję **Aplikacja konsoli**, a następnie wybierz pozycję **Dalej**.

   ![Wybieranie szablonu aplikacji konsoli](./media/calc-vs2019-choose-console-app.png "Wybieranie szablonu aplikacji konsoli")

   > [!Important]
   > Upewnij się, że wybrałeś wersję c++ szablonu **aplikacji konsoli.** Ma tagi **C++,** **Windows**i **Konsola,** a ikona ma "++" w rogu.

1. W oknie dialogowym **Konfigurowanie nowego projektu** zaznacz pole edycji **nazwy projektu,** nazwij nowy projekt *CalculatorTutorial*, a następnie wybierz pozycję **Utwórz**.

   ![Nadawanie nazwy projektowi w oknie dialogowym Konfigurowanie nowego projektu](./media/calc-vs2019-name-your-project.png "Nadawanie nazwy projektowi w oknie dialogowym Konfigurowanie nowego projektu")

   Zostanie utworzona pusta aplikacja konsoli systemu Windows języka C++. Aplikacje konsoli używają okna konsoli systemu Windows do wyświetlania danych wyjściowych i akceptowania danych wejściowych użytkownika. W programie Visual Studio otwiera się okno edytora i pokazuje wygenerowany kod:

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

## <a name="verify-that-your-new-app-builds-and-runs"></a>Sprawdź, czy nowa aplikacja tworzy i działa

Szablon dla nowej aplikacji konsoli systemu Windows tworzy prostą aplikację C++ "Hello World". W tym momencie można zobaczyć, jak Visual Studio tworzy i uruchamia aplikacje, które tworzysz bezpośrednio z IDE.

1. Aby utworzyć projekt, wybierz polecenie **Buduj rozwiązanie** z menu **Kompilacja.** Okno **Dane wyjściowe** pokazuje wyniki procesu kompilacji.

   ![Kompilowanie projektu](./media/calc-vs2019-build-your-project.png "Kompilowanie projektu")

1. Aby uruchomić kod, na pasku menu wybierz polecenie **Debug ,** **Start bez debugowania**.

   ![Rozpoczęcie projektu](./media/calc-vs2019-hello-world-console.png "Rozpoczęcie projektu")

   Zostanie otwarte okno konsoli, a następnie uruchomi aplikację. Po uruchomieniu aplikacji konsoli w programie Visual Studio uruchamia kod, a następnie drukuje "Naciśnij dowolny klawisz, aby zamknąć to okno . . ." aby dać ci szansę zobaczenia wyjścia. Gratulacje! Stworzyłeś swój pierwszy "Cześć, świat!" aplikacji konsoli w programie Visual Studio!

1. Naciśnij klawisz, aby odrzucić okno konsoli i powrócić do programu Visual Studio.

Teraz masz narzędzia do tworzenia i uruchamiania aplikacji po każdej zmianie, aby sprawdzić, czy kod nadal działa zgodnie z oczekiwaniami. Później pokażemy Ci, jak go debugować, jeśli nie.

## <a name="edit-the-code"></a>Edytowanie kodu

Teraz przekszłomy kod w tym szablonie w aplikację kalkulatora.

1. W pliku *CalculatorTutorial.cpp* edytuj kod, aby dopasować go w tym przykładzie:

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

   > Opis kodu:
   >
   > - Instrukcje `#include` umożliwiają odwoływanie się do kodu znajdującego się w innych plikach. Czasami może pojawić się nazwa pliku otoczona nawiasami kątowymi (**\<**); innym razem jest otoczony cytatami (**" "**). Ogólnie rzecz biorąc nawiasy kątowe są używane podczas odwoływania się do standardowej biblioteki języka C++, podczas gdy cudzysłowy są używane dla innych plików.
   > - Wiersz `using namespace std;` informuje kompilatora oczekiwać rzeczy z biblioteki standardowej języka C++ do użycia w tym pliku. Bez tego wiersza każde słowo kluczowe z biblioteki `std::`musiałoby być poprzedzone , aby oznaczyć jego zakres. Na przykład bez tego wiersza `cout` każde odniesienie musiałoby `std::cout`być zapisane jako . Instrukcja `using` jest dodawana, aby kod wyglądał bardziej czysto.
   > - Słowo `cout` kluczowe służy do drukowania do standardowego wyjścia w języku C++. Operator ** \< ** informuje kompilator, aby wysłać cokolwiek jest po prawej stronie do standardowego wyjścia.
   > - **Endl** słowo kluczowe jest jak Enter klucz; kończy linię i przenosi kursor do następnego wiersza. Jest to lepsza praktyka, `\n` aby umieścić wewnątrz ciąg (zawarte przez ""), `endl` aby zrobić to samo, jak zawsze opróżnia bufor i może zaszkodzić `endl` wydajności programu, ale ponieważ jest to bardzo mała aplikacja, jest używany zamiast dla lepszej czytelności.
   > - Wszystkie instrukcje C++ musi kończyć się średnikami i `main()` wszystkie aplikacje C++ musi zawierać funkcję. Ta funkcja jest to, co program działa na początku. Cały kod musi `main()` być dostępny, aby można było go używać.

1. Aby zapisać plik, wprowadź **klawisze Ctrl+S**lub wybierz ikonę **Zapisz** u góry IDE, ikonę dyskietki na pasku narzędzi pod paskiem menu.

1. Aby uruchomić aplikację, naciśnij **klawisze Ctrl+F5** lub przejdź do menu **Debugowania** i wybierz polecenie **Start Without Debugging**. Powinno zostać wyświetlone okno konsoli, w które wyświetla tekst określony w kodzie.

1. Zamknij okno konsoli po zakończeniu.

## <a name="add-code-to-do-some-math"></a>Dodaj kod, aby wykonać matematykę

Nadszedł czas, aby dodać trochę logiki matematycznej.

### <a name="to-add-a-calculator-class"></a>Aby dodać klasę Kalkulator

1. Przejdź do menu **Projekt** i wybierz polecenie **Dodaj klasę**. W polu **edycji Nazwa klasy** wprowadź pozycję *Kalkulator*. Wybierz pozycję **OK**. Dwa nowe pliki są dodawane do projektu. Aby zapisać wszystkie zmienione pliki jednocześnie, naciśnij **klawisze Ctrl+Shift+S**. Jest to skrót klawiaturowy do **pliku** > **Zapisz wszystko**. Obok przycisku **Zapisz** wszystko znajduje się również przycisk paska narzędzi **Dla wszystkich**, ikona dwóch dyskietek. Ogólnie rzecz biorąc, dobrą praktyką jest częste **zapisywanie wszystkich,** aby nie przegapić żadnych plików podczas zapisywania.

   ![Tworzenie klasy Kalkulator](./media/calc-vs2019-create-calculator-class.png "Tworzenie klasy Kalkulator")

   Klasa jest jak plan dla obiektu, który coś robi. W takim przypadku definiujemy kalkulator i jak powinien działać. Kreator **Dodaj klasę,** który został użyty powyżej, utworzył pliki .h i .cpp, które mają taką samą nazwę jak klasa. Pełną listę plików projektu można wyświetlić w oknie **Eksploratora rozwiązań,** widocznym z boku IDE. Jeśli okno nie jest widoczne, możesz je otworzyć na pasku menu: wybierz pozycję **Wyświetl** > **Eksploratora rozwiązań**.

   ![Eksplorator rozwiązań](./media/calc-vs2019-solution-explorer.png "Eksplorator rozwiązań")

   Teraz powinieneś mieć trzy karty otwarte w edytorze: *CalculatorTutorial.cpp*, *Calculator.h*i *Calculator.cpp*. Jeśli przypadkowo zamkniesz jeden z nich, możesz ponownie otworzyć go, klikając go dwukrotnie w oknie **Eksploratora rozwiązań.**

1. W **Calculator.h**, `Calculator();` `~Calculator();` usuń i linie, które zostały wygenerowane, ponieważ nie będzie ich tutaj potrzebne. Następnie dodaj następujący wiersz kodu, aby plik wyglądał teraz następująco:

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
   > - Dodany wiersz deklaruje nową funkcję `Calculate`o nazwie , która będzie używana do uruchamiania operacji matematycznych do dodawania, odejmowania, mnożenia i dzielenia.
   > - Kod C++ jest zorganizowany w pliki *nagłówka* (.h) i pliki *źródłowe* (.cpp). Kilka innych rozszerzeń plików są obsługiwane przez różne kompilatory, ale są to główne z nich wiedzieć o. Funkcje i zmienne są zwykle *deklarowane*, to znaczy, o nazwie i typie, w plikach nagłówkowych i *implementowane*lub podane definicji, w plikach źródłowych. Aby uzyskać dostęp do kodu zdefiniowanego w innym pliku, można użyć `#include "filename.h"`, gdzie "filename.h" jest nazwą pliku, który deklaruje zmienne lub funkcje, których chcesz użyć.
   > - Dwa usunięte wiersze zadeklarowane *konstruktora* i *destruktora* dla klasy. Dla klasy proste, takie jak ta, kompilator tworzy je dla Ciebie, a ich zastosowania wykraczają poza zakres tego samouczka.
   > - Dobrą praktyką jest organizowanie kodu w różnych plikach na podstawie tego, co robi, więc łatwo jest znaleźć kod, którego potrzebujesz później. W `Calculator` naszym przypadku definiujemy klasę oddzielnie od `main()` pliku zawierającego funkcję, `Calculator` ale `main()`planujemy odwołać się do klasy w .

1. Pod spodem pojawi się zielony `Calculate`squiggle . To dlatego, że nie zdefiniowaliśmy `Calculate` funkcji w pliku .cpp. Umieść wskaźnik myszy na słowie, kliknij żarówkę (w tym przypadku śrubokręt), która wyskakuje, i wybierz pozycję **Utwórz definicję "Oblicz" w pliku Calculator.cpp**.

   ![Tworzenie definicji obliczania](./media/calc-vs2019-create-definition.png "Tworzenie definicji obliczania")

   Pojawi się okno podręczne, które daje wgląd w zmianę kodu, która została wykonydowana w innym pliku. Kod został dodany do *calculator.cpp*.

   ![Wyskakujące okienko z definicją Oblicz](./media/calc-vs2019-pop-up-definition.png "Wyskakujące okienko z definicją Oblicz")

   Obecnie po prostu zwraca 0.0. Zmienimy to teraz. Naciśnij **klawisz Esc,** aby zamknąć okno podręczne.

1. Przełącz się do pliku *Calculator.cpp* w oknie edytora. Usuń `Calculator()` sekcje i `~Calculator()` (tak jak w pliku .h) i `Calculate()`dodaj następujący kod do:

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
   > - Funkcja `Calculate` zużywa liczbę, operator i drugą liczbę, a następnie wykonuje żądaną operację na liczbach.
   > - Instrukcja switch sprawdza, który operator został dostarczony i wykonuje tylko przypadek odpowiadający tej operacji. Wartość domyślna: przypadek jest rezerwowym w przypadku, gdy użytkownik wpisuje operatora, który nie jest akceptowany, więc program nie zostanie przerwany. Ogólnie rzecz biorąc najlepiej jest obsługiwać nieprawidłowe dane wejściowe użytkownika w bardziej elegancki sposób, ale wykracza to poza zakres tego samouczka.
   > - Słowo `double` kluczowe oznacza typ liczby obsługującej miejsca dziesiętne. W ten sposób kalkulator może obsługiwać zarówno matematykę dziesiętną, jak i matematykę całkowitą. Funkcja `Calculate` jest wymagana, aby zawsze zwracać `double` taką liczbę ze względu na sam początek kodu (oznacza to typ zwracany funkcji), dlatego zwracamy 0.0 nawet w przypadku domyślnym.
   > - Plik .h deklaruje *prototyp*funkcji , który informuje kompilator z góry, jakie parametry wymaga i jaki typ zwracany oczekiwać od niego. Plik .cpp zawiera wszystkie szczegóły implementacji funkcji.

Jeśli skompilujesz i uruchomisz kod ponownie w tym momencie, nadal zostanie ono zakończyć pracę po zapytaniu, którą operację wykonać. Następnie zmodyfikujesz `main` funkcję, aby wykonać kilka obliczeń.

### <a name="to-call-the-calculator-class-member-functions"></a>Aby wywołać funkcje członkowskie klasy Kalkulator

1. Teraz zaktualizujmy `main` funkcję w *CalculatorTutorial.cpp*:

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
   > - Ponieważ programy C++ zawsze `main()` zaczynają się od funkcji, musimy wywołać `#include` nasz inny kod stamtąd, więc instrukcja jest potrzebna.
   > - Niektóre zmienne `x` `y`początkowe , `oper`, i `result` są zadeklarowane do przechowywania pierwszej liczby, drugiej liczby, operatora i wyniku końcowego, odpowiednio. Zawsze dobrą praktyką jest nadajnienie im pewnych wartości początkowych, aby uniknąć niezdefiniowanego zachowania, co jest tutaj wykonywane.
   > - Wiersz `Calculator c;` deklaruje obiekt o nazwie "c" jako `Calculator` wystąpienie klasy. Sama klasa jest tylko planem działania kalkulatorów; obiekt jest specyficznym kalkulatorem, który wykonuje matematykę.
   > - Instrukcja `while (true)` jest pętlą. Kod wewnątrz pętli nadal wykonywać w kółko tak długo, jak `()` warunek wewnątrz posiada true. Ponieważ warunek jest po `true`prostu wymieniony jako , to zawsze prawda, więc pętla działa na zawsze. Aby zamknąć program, użytkownik musi ręcznie zamknąć okno konsoli. W przeciwnym razie program zawsze czeka na nowe dane wejściowe.
   > - Słowo `cin` kluczowe służy do akceptowania danych wejściowych od użytkownika. Ten strumień wejściowy jest wystarczająco inteligentny, aby przetworzyć wiersz tekstu wprowadzony w oknie konsoli i umieścić go wewnątrz każdej z wymienionych zmiennych, w kolejności, w kolejności, w której dane wejściowe użytkownika są zgodne z wymaganą specyfikacją. Można zmodyfikować ten wiersz, aby zaakceptować różne typy danych wejściowych, na przykład więcej niż dwie liczby, chociaż `Calculate()` funkcja również musi zostać zaktualizowana, aby obsłużyć tę funkcję.
   > - Wyrażenie `c.Calculate(x, oper, y);` wywołuje `Calculate` funkcję zdefiniowaną wcześniej i dostarcza wprowadzone wartości wejściowe. Następnie funkcja zwraca liczbę, która `result`jest przechowywana w pliku .
   > - Na koniec `result` jest drukowany na konsoli, więc użytkownik widzi wynik obliczeń.

### <a name="build-and-test-the-code-again"></a>Ponownie skompiluj i przetestuj kod

Teraz nadszedł czas, aby przetestować program ponownie, aby upewnić się, że wszystko działa poprawnie.

1. Naciśnij **klawisze Ctrl+F5,** aby odbudować i uruchomić aplikację.

1. Wprowadź `5 + 5`i naciśnij klawisz **Enter**. Sprawdź, czy wynik wynosi 10.

   ![Wynik 5 + 5](./media/calc-vs2019-five-plus-five.png "Wynik 5 + 5")

## <a name="debug-the-app"></a>Debugowanie aplikacji

Ponieważ użytkownik może wpisać cokolwiek w oknie konsoli, upewnijmy się, że kalkulator obsługuje niektóre dane wejściowe zgodnie z oczekiwaniami. Zamiast uruchamiać program, niech debugować go zamiast, dzięki czemu możemy sprawdzić, co robi w szczegółach, krok po kroku.

### <a name="to-run-the-app-in-the-debugger"></a>Aby uruchomić aplikację w debugerze

1. Ustaw punkt przerwania `result = c.Calculate(x, oper, y);` w wierszu, zaraz po tym, jak użytkownik został poproszony o wprowadzenie danych wejściowych. Aby ustawić punkt przerwania, kliknij obok linii na szarym pionowym pasku wzdłuż lewej krawędzi okna edytora. Pojawi się czerwona kropka.

   ![Ustawianie punktu przerwania](./media/calc-vs2019-set-breakpoint.png "Ustawianie punktu przerwania")

   Teraz, gdy debugujemy program, zawsze wstrzymuje wykonanie w tym wierszu. Mamy już przybliżone przekonanie, że program działa w prostych przypadkach. Ponieważ nie chcemy wstrzymać wykonywania za każdym razem, niech się punkt przerwania warunkowe.

1. Kliknij prawym przyciskiem myszy czerwoną kropkę reprezentującą punkt przerwania, a następnie wybierz pozycję **Warunki**. W polu edycji warunku wprowadź . `(y == 0) && (oper == '/')` Po zakończeniu wybierz przycisk **Zamknij.** Warunek zostanie zapisany automatycznie.

   ![Ustawianie warunkowego punktu przerwania](./media/calc-vs2019-conditional-breakpoint.png "Ustawianie warunkowego punktu przerwania")

   Teraz wstrzymujemy wykonywanie w punkcie przerwania, w szczególności, jeśli zostanie podjęta próba podziału przez 0.

1. Aby debugować program, naciśnij **klawisz F5**lub wybierz przycisk **lokalnego paska narzędzi Windows Debugger** z ikoną zielonej strzałki. W aplikacji konsoli, jeśli wprowadzisz coś w rodzaju "5 - 0", program zachowuje się normalnie i działa. Jeśli jednak wpiszesz "10 / 0", zatrzymuje się w punkcie przerwania. Można nawet umieścić dowolną liczbę spacji między `cin` operatorem i numerami: jest wystarczająco inteligentny, aby odpowiednio przeanalizować dane wejściowe.

   ![Pauza w warunkowym punkcie przerwania](./media/calc-vs2019-debug-breakpoint.png "Pauza w warunkowym punkcie przerwania")

### <a name="useful-windows-in-the-debugger"></a>Przydatne okna w debugerze

Za każdym razem, gdy debugujesz kod, można zauważyć, że pojawiają się nowe okna. Te okna mogą pomóc w debugowaniu. Spójrz na okno **Autos.** Okno **Autos** pokazuje bieżące wartości zmiennych używanych co najmniej trzy wiersze przed i do bieżącego wiersza. Aby wyświetlić wszystkie zmienne z tej funkcji, przełącz się do okna **Zmiennych.** Można faktycznie zmodyfikować wartości tych zmiennych podczas debugowania, aby zobaczyć, jaki wpływ będą miały na program. W takim przypadku zostawimy je w spokoju.

   ![Okno Miejscowi](./media/calc-vs2019-debug-locals.png "Okno Miejscowi")

Można również po prostu najechać kursorem na zmienne w samym kodzie, aby zobaczyć ich bieżące wartości, w których wykonanie jest obecnie wstrzymane. Upewnij się, że okno edytora jest w centrum uwagi, klikając go najpierw.

   ![Kursoruj, aby wyświetlić bieżące wartości zmiennych](./media/calc-vs2019-hover-tooltip.png "Kursoruj, aby wyświetlić bieżące wartości zmiennych")

### <a name="to-continue-debugging"></a>Aby kontynuować debugowanie

1. Żółta linia po lewej stronie pokazuje bieżący punkt wykonania. Bieżąca linia `Calculate`wywołuje , więc naciśnij **klawisz F11,** aby **przejść do** funkcji. Znajdziesz się w ciele `Calculate` funkcji. Bądź ostrożny z **Step Into**; jeśli zrobisz to za dużo, możesz tracić dużo czasu. Przechodzi do dowolnego kodu, którego używasz w wierszu, w tym standardowych funkcji biblioteki.

1. Teraz, gdy punkt wykonania znajduje się `Calculate` na początku funkcji, naciśnij **klawisz F10,** aby przejść do następnego wiersza w wykonaniu programu. **F10** jest również znany jako **Step Over**. Krok **można** użyć, aby przejść z linii do wiersza, bez zagłębiania się w szczegóły tego, co dzieje się w każdej części wiersza. Ogólnie rzecz biorąc należy użyć **Step Over** zamiast **Step Into**, chyba że chcesz zanurzyć się głębiej w `Calculate`kod, który jest wywoływany z innego miejsca (jak to miało miejsce, aby dotrzeć do ciała ).

1. Kontynuuj korzystanie **z F10** do **step over** `main()` każdego wiersza, aż wrócisz `cout` do funkcji w innym pliku i zatrzymać się w wierszu.

   Wygląda na to, że program robi to, czego się oczekuje: przyjmuje pierwszą liczbę i dzieli ją przez drugą. W `cout` wierszu umieść `result` wskaźnik myszy na `result` zmiennej lub spójrz w oknie **Autos.** Zobaczysz, że jego wartość jest wyświetlana jako "inf", która nie wygląda dobrze, więc naprawmy to. Linia `cout` po prostu wyprowadza dowolną `result`wartość, więc po wykonaniu jednego kroku do przodu za pomocą **F10**zostanie wyświetlone okno konsoli:

   ![Wynik podziału przez zero](./media/calc-vs2019-divide-by-zero-fail.png "Wynik podziału przez zero")

   Ten wynik dzieje się, ponieważ dzielenie przez zero jest niezdefiniowane, więc program nie ma numerycznej odpowiedzi na żądaną operację.

### <a name="to-fix-the-divide-by-zero-error"></a>Aby naprawić błąd "podziel przez zero"

Obsłużmy dzielenie przez zero bardziej wdzięku, dzięki czemu użytkownik może zrozumieć problem.

1. Wykonuj następujące zmiany w *calculatorTutorial.cpp*. (Możesz pozostawić program uruchomiony podczas edycji, dzięki funkcji debugera o nazwie **Edytuj i Kontynuuj):**

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

1. Teraz naciśnij **klawisz F5** raz. Wykonywanie programu trwa do końca, dopóki nie musi wstrzymać, aby poprosić o dane wejściowe użytkownika. Wprowadź `10 / 0` ponownie. Teraz drukowana jest bardziej pomocna wiadomość. Użytkownik jest proszony o więcej danych wejściowych, a program kontynuuje wykonywanie normalnie.

   ![Ostateczny wynik po zmianach](./media/calc-vs2019-final-verification.png "Ostateczny wynik po zmianach")

   > [!Note]
   > Podczas edycji kodu w trybie debugowania, istnieje ryzyko, że kod staje się przestarzały. Dzieje się tak, gdy debuger jest nadal uruchomiony stary kod i nie został jeszcze zaktualizowany o zmiany. Debuger wyskakuje okno dialogowe, aby poinformować, kiedy to nastąpi. Czasami może być konieczne naciśnięcie **klawisza F5,** aby odświeżyć wykonywany kod. W szczególności jeśli dokonasz zmiany wewnątrz funkcji, podczas gdy punkt wykonania znajduje się wewnątrz tej funkcji, musisz wyjść z funkcji, a następnie z powrotem do niej ponownie, aby uzyskać zaktualizowany kod. Jeśli to nie działa z jakiegoś powodu i pojawi się komunikat o błędzie, możesz zatrzymać debugowanie, klikając czerwony kwadrat na pasku narzędzi w menu w górnej części IDE, a następnie ponownie rozpocząć debugowanie, wprowadzając **klawisz F5** lub wybierając zieloną strzałkę "play" obok przycisku stop na pasku narzędzi.

   > Opis skrótów uruchamiania i debugowania
   >
   > - **F5** (lub **Debug** > **Start Debug Debugging**) rozpoczyna sesję debugowania, jeśli nie jest jeszcze aktywny i uruchamia program, dopóki punkt przerwania nie zostanie trafiony lub program wymaga danych wejściowych użytkownika. Jeśli nie jest potrzebne żadne dane wejściowe użytkownika i nie jest dostępny punkt przerwania, program kończy działanie, a okno konsoli zamyka się po zakończeniu działania programu. Jeśli masz coś takiego jak program "Hello World", użyj **klawiszy Ctrl+F5** lub ustaw punkt przerwania przed wprowadzeniem **F5,** aby okno było otwarte.
   > - **Ctrl +F5** (lub **Debug** > **start bez debugowania)** uruchamia aplikację bez przechodzenia w tryb debugowania. Jest to nieco szybsze niż debugowanie, a okno konsoli pozostaje otwarte po zakończeniu wykonywania programu.
   > - **F10** (znany jako **Step Over)** umożliwia iterację za pomocą kodu, wiersz po wierszu i wizualizacji sposobu uruchamiania kodu i wartości zmiennych na każdym etapie wykonywania.
   > - **F11** (znany jako **Step Into)** działa podobnie do **Step Over**, z tą różnicą, że kroki do wszystkich funkcji wywoływanych w wierszu wykonywania. Na przykład jeśli linia wykonywana wywołuje funkcję, naciśnięcie **klawisza F11** przenosi wskaźnik do treści funkcji, dzięki czemu można wykonać kod funkcji jest uruchamiany przed powrotem do wiersza, który rozpoczął się w. Naciśnięcie **klawisza F10** kroki nad wywołaniem funkcji i po prostu przechodzi do następnego wiersza; wywołanie funkcji nadal się dzieje, ale program nie zatrzymuje się, aby pokazać, co robi.

### <a name="close-the-app"></a>Zamykanie aplikacji

- Jeśli nadal działa, zamknij okno konsoli dla aplikacji kalkulatora.

## <a name="the-finished-app"></a>Ukończona aplikacja

Gratulacje! Kod aplikacji kalkulatora został ukończony, a następnie skupilowany i debugowany w programie Visual Studio.

## <a name="next-steps"></a>Następne kroki

[Dowiedz się więcej o programie Visual Studio dla języka C++](https://blogs.msdn.microsoft.com/vcblog/2017/04/21/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end

::: moniker range="<vs-2019"

Zwykle punktem wyjścia dla programisty C++ jest "Cześć, świat!" aplikacja, która działa w wierszu polecenia. To, co utworzysz w programie Visual Studio w tym artykule, a następnie przejdziemy do czegoś trudniejszego: aplikacji kalkulatora.

## <a name="prerequisites"></a>Wymagania wstępne

- Mieć Visual Studio z **pulpitu rozwoju z c++** obciążenia zainstalowanego i uruchomionego na komputerze. Jeśli nie jest jeszcze zainstalowany, zobacz [Instalowanie pomocy technicznej języka C++ w programie Visual Studio](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Tworzenie projektu aplikacji

Visual Studio używa *projektów* do organizowania kodu dla aplikacji i *rozwiązań* do organizowania projektów. Projekt zawiera wszystkie opcje, konfiguracje i reguły używane do tworzenia aplikacji. Zarządza również relacją między wszystkimi plikami projektu a wszelkimi plikami zewnętrznymi. Aby utworzyć aplikację, najpierw utworzysz nowy projekt i rozwiązanie.

1. Na pasku menu w programie Visual Studio wybierz pozycję **Plik** > **nowego** > **projektu**. Zostanie otwarte okno **Nowy projekt.**

2. Upewnij się, że na lewym pasku bocznym jest zaznaczona opcja **Visual C++.** W centrum wybierz pozycję **Aplikacja konsoli systemu Windows**.

3. W polu Edycja **nazwy** u dołu nazwij nowy projekt *CalculatorTutorial*, a następnie wybierz przycisk **OK**.

   ![Okno dialogowe Nowy projekt](./media/calculator-new-project-dialog.png "Okno dialogowe Nowy projekt")

   Zostanie utworzona pusta aplikacja konsoli systemu Windows języka C++. Aplikacje konsoli używają okna konsoli systemu Windows do wyświetlania danych wyjściowych i akceptowania danych wejściowych użytkownika. W programie Visual Studio otwiera się okno edytora i pokazuje wygenerowany kod:

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

## <a name="verify-that-your-new-app-builds-and-runs"></a>Sprawdź, czy nowa aplikacja tworzy i działa

Szablon dla nowej aplikacji konsoli systemu Windows tworzy prostą aplikację C++ "Hello World". W tym momencie można zobaczyć, jak Visual Studio tworzy i uruchamia aplikacje, które tworzysz bezpośrednio z IDE.

1. Aby utworzyć projekt, wybierz polecenie **Buduj rozwiązanie** z menu **Kompilacja.** Okno **Dane wyjściowe** pokazuje wyniki procesu kompilacji.

   ![Kompilowanie projektu](./media/calculator-initial-build-output.png "Kompilowanie projektu")

1. Aby uruchomić kod, na pasku menu wybierz polecenie **Debug ,** **Start bez debugowania**.

   ![Rozpoczęcie projektu](./media/calculator-hello-world-console.png "Rozpoczęcie projektu")

   Zostanie otwarte okno konsoli, a następnie uruchomi aplikację. Po uruchomieniu aplikacji konsoli w programie Visual Studio uruchamia kod, a następnie drukuje "Naciśnij dowolny klawisz, aby kontynuować . . ." aby dać ci szansę zobaczenia wyjścia. Gratulacje! Stworzyłeś swój pierwszy "Cześć, świat!" aplikacji konsoli w programie Visual Studio!

1. Naciśnij klawisz, aby odrzucić okno konsoli i powrócić do programu Visual Studio.

Teraz masz narzędzia do tworzenia i uruchamiania aplikacji po każdej zmianie, aby sprawdzić, czy kod nadal działa zgodnie z oczekiwaniami. Później pokażemy Ci, jak go debugować, jeśli nie.

## <a name="edit-the-code"></a>Edytowanie kodu

Teraz przekszłomy kod w tym szablonie w aplikację kalkulatora.

1. W pliku *CalculatorTutorial.cpp* edytuj kod, aby dopasować go w tym przykładzie:

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

   > Opis kodu:
   >
   > - Instrukcje `#include` umożliwiają odwoływanie się do kodu znajdującego się w innych plikach. Czasami może pojawić się nazwa pliku otoczona nawiasami kątowymi (**\<**); innym razem jest otoczony cytatami (**" "**). Ogólnie rzecz biorąc nawiasy kątowe są używane podczas odwoływania się do standardowej biblioteki języka C++, podczas gdy cudzysłowy są używane dla innych plików.
   > - Wiersz `#include "pch.h"` (lub w programie Visual Studio 2017 i `#include "stdafx.h"`wcześniejszych) odwołuje się do czegoś znanego jako wstępnie skompilowany nagłówek. Są one często używane przez profesjonalnych programistów w celu poprawy czasu kompilacji, ale wykraczają one poza zakres tego samouczka.
   > - Wiersz `using namespace std;` informuje kompilatora oczekiwać rzeczy z biblioteki standardowej języka C++ do użycia w tym pliku. Bez tego wiersza każde słowo kluczowe z biblioteki `std::`musiałoby być poprzedzone , aby oznaczyć jego zakres. Na przykład bez tego wiersza `cout` każde odniesienie musiałoby `std::cout`być zapisane jako . Instrukcja `using` jest dodawana, aby kod wyglądał bardziej czysto.
   > - Słowo `cout` kluczowe służy do drukowania do standardowego wyjścia w języku C++. Operator ** \< ** informuje kompilator, aby wysłać cokolwiek jest po prawej stronie do standardowego wyjścia.
   > - **Endl** słowo kluczowe jest jak Enter klucz; kończy linię i przenosi kursor do następnego wiersza. Jest to lepsza praktyka, `\n` aby umieścić wewnątrz ciąg (zawarte przez ""), `endl` aby zrobić to samo, jak zawsze opróżnia bufor i może zaszkodzić `endl` wydajności programu, ale ponieważ jest to bardzo mała aplikacja, jest używany zamiast dla lepszej czytelności.
   > - Wszystkie instrukcje C++ musi kończyć się średnikami i `main()` wszystkie aplikacje C++ musi zawierać funkcję. Ta funkcja jest to, co program działa na początku. Cały kod musi `main()` być dostępny, aby można było go używać.

1. Aby zapisać plik, wprowadź **klawisze Ctrl+S**lub wybierz ikonę **Zapisz** u góry IDE, ikonę dyskietki na pasku narzędzi pod paskiem menu.

1. Aby uruchomić aplikację, naciśnij **klawisze Ctrl+F5** lub przejdź do menu **Debugowania** i wybierz polecenie **Start Without Debugging**. Jeśli pojawi się okno podręczne z napisem **Ten projekt jest nieaktualne,** możesz wybrać **opcję Nie pokazuj ponownie tego okna dialogowego,** a następnie wybierz pozycję **Tak,** aby utworzyć aplikację. Powinno zostać wyświetlone okno konsoli, w które wyświetla tekst określony w kodzie.

   ![Tworzenie i uruchamianie aplikacji](./media/calculator-first-launch.gif "Tworzenie i uruchamianie aplikacji")

1. Zamknij okno konsoli po zakończeniu.

## <a name="add-code-to-do-some-math"></a>Dodaj kod, aby wykonać matematykę

Nadszedł czas, aby dodać trochę logiki matematycznej.

### <a name="to-add-a-calculator-class"></a>Aby dodać klasę Kalkulator

1. Przejdź do menu **Projekt** i wybierz polecenie **Dodaj klasę**. W polu **edycji Nazwa klasy** wprowadź pozycję *Kalkulator*. Wybierz pozycję **OK**. Dwa nowe pliki są dodawane do projektu. Aby zapisać wszystkie zmienione pliki jednocześnie, naciśnij **klawisze Ctrl+Shift+S**. Jest to skrót klawiaturowy do **pliku** > **Zapisz wszystko**. Obok przycisku **Zapisz** wszystko znajduje się również przycisk paska narzędzi **Dla wszystkich**, ikona dwóch dyskietek. Ogólnie rzecz biorąc, dobrą praktyką jest częste **zapisywanie wszystkich,** aby nie przegapić żadnych plików podczas zapisywania.

   ![Tworzenie klasy Kalkulator](./media/calculator-create-class.gif "Tworzenie klasy Kalkulator")

   Klasa jest jak plan dla obiektu, który coś robi. W takim przypadku definiujemy kalkulator i jak powinien działać. Kreator **Dodaj klasę,** który został użyty powyżej, utworzył pliki .h i .cpp, które mają taką samą nazwę jak klasa. Pełną listę plików projektu można wyświetlić w oknie **Eksploratora rozwiązań,** widocznym z boku IDE. Jeśli okno nie jest widoczne, możesz je otworzyć na pasku menu: wybierz pozycję **Wyświetl** > **Eksploratora rozwiązań**.

   ![Eksplorator rozwiązań](./media/calculator-solution-explorer.png "Eksplorator rozwiązań")

   Teraz powinieneś mieć trzy karty otwarte w edytorze: *CalculatorTutorial.cpp*, *Calculator.h*i *Calculator.cpp*. Jeśli przypadkowo zamkniesz jeden z nich, możesz ponownie otworzyć go, klikając go dwukrotnie w oknie **Eksploratora rozwiązań.**

1. W **Calculator.h**, `Calculator();` `~Calculator();` usuń i linie, które zostały wygenerowane, ponieważ nie będzie ich tutaj potrzebne. Następnie dodaj następujący wiersz kodu, aby plik wyglądał teraz następująco:

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
   > - Dodany wiersz deklaruje nową funkcję `Calculate`o nazwie , która będzie używana do uruchamiania operacji matematycznych do dodawania, odejmowania, mnożenia i dzielenia.
   > - Kod C++ jest zorganizowany w pliki *nagłówka* (.h) i pliki *źródłowe* (.cpp). Kilka innych rozszerzeń plików są obsługiwane przez różne kompilatory, ale są to główne z nich wiedzieć o. Funkcje i zmienne są zwykle *deklarowane*, to znaczy, o nazwie i typie, w plikach nagłówkowych i *implementowane*lub podane definicji, w plikach źródłowych. Aby uzyskać dostęp do kodu zdefiniowanego w innym pliku, można użyć `#include "filename.h"`, gdzie "filename.h" jest nazwą pliku, który deklaruje zmienne lub funkcje, których chcesz użyć.
   > - Dwa usunięte wiersze zadeklarowane *konstruktora* i *destruktora* dla klasy. Dla klasy proste, takie jak ta, kompilator tworzy je dla Ciebie, a ich zastosowania wykraczają poza zakres tego samouczka.
   > - Dobrą praktyką jest organizowanie kodu w różnych plikach na podstawie tego, co robi, więc łatwo jest znaleźć kod, którego potrzebujesz później. W `Calculator` naszym przypadku definiujemy klasę oddzielnie od `main()` pliku zawierającego funkcję, `Calculator` ale `main()`planujemy odwołać się do klasy w .

1. Pod spodem pojawi się zielony `Calculate`squiggle . To dlatego, że nie zdefiniowaliśmy `Calculate` funkcji w pliku .cpp. Umieść wskaźnik myszy na słowie, kliknij żarówkę, która się pojawi, a następnie wybierz pozycję **Utwórz definicję "Oblicz" w pliku Calculator.cpp**. Pojawi się okno podręczne, które daje wgląd w zmianę kodu, która została wykonydowana w innym pliku. Kod został dodany do *calculator.cpp*.

   ![Tworzenie definicji obliczania](./media/calculator-create-definition.gif "Tworzenie definicji obliczania")

   Obecnie po prostu zwraca 0.0. Zmienimy to teraz. Naciśnij **klawisz Esc,** aby zamknąć okno podręczne.

1. Przełącz się do pliku *Calculator.cpp* w oknie edytora. Usuń `Calculator()` sekcje i `~Calculator()` (tak jak w pliku .h) i `Calculate()`dodaj następujący kod do:

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
   > - Funkcja `Calculate` zużywa liczbę, operator i drugą liczbę, a następnie wykonuje żądaną operację na liczbach.
   > - Instrukcja switch sprawdza, który operator został dostarczony i wykonuje tylko przypadek odpowiadający tej operacji. Wartość domyślna: przypadek jest rezerwowym w przypadku, gdy użytkownik wpisuje operatora, który nie jest akceptowany, więc program nie zostanie przerwany. Ogólnie rzecz biorąc najlepiej jest obsługiwać nieprawidłowe dane wejściowe użytkownika w bardziej elegancki sposób, ale wykracza to poza zakres tego samouczka.
   > - Słowo `double` kluczowe oznacza typ liczby obsługującej miejsca dziesiętne. W ten sposób kalkulator może obsługiwać zarówno matematykę dziesiętną, jak i matematykę całkowitą. Funkcja `Calculate` jest wymagana, aby zawsze zwracać `double` taką liczbę ze względu na sam początek kodu (oznacza to typ zwracany funkcji), dlatego zwracamy 0.0 nawet w przypadku domyślnym.
   > - Plik .h deklaruje *prototyp*funkcji , który informuje kompilator z góry, jakie parametry wymaga i jaki typ zwracany oczekiwać od niego. Plik .cpp zawiera wszystkie szczegóły implementacji funkcji.

Jeśli skompilujesz i uruchomisz kod ponownie w tym momencie, nadal zostanie ono zakończyć pracę po zapytaniu, którą operację wykonać. Następnie zmodyfikujesz `main` funkcję, aby wykonać kilka obliczeń.

### <a name="to-call-the-calculator-class-member-functions"></a>Aby wywołać funkcje członkowskie klasy Kalkulator

1. Teraz zaktualizujmy `main` funkcję w *CalculatorTutorial.cpp*:

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
   > - Ponieważ programy C++ zawsze `main()` zaczynają się od funkcji, musimy wywołać `#include` nasz inny kod stamtąd, więc instrukcja jest potrzebna.
   > - Niektóre zmienne `x` `y`początkowe , `oper`, i `result` są zadeklarowane do przechowywania pierwszej liczby, drugiej liczby, operatora i wyniku końcowego, odpowiednio. Zawsze dobrą praktyką jest nadajnienie im pewnych wartości początkowych, aby uniknąć niezdefiniowanego zachowania, co jest tutaj wykonywane.
   > - Wiersz `Calculator c;` deklaruje obiekt o nazwie "c" jako `Calculator` wystąpienie klasy. Sama klasa jest tylko planem działania kalkulatorów; obiekt jest specyficznym kalkulatorem, który wykonuje matematykę.
   > - Instrukcja `while (true)` jest pętlą. Kod wewnątrz pętli nadal wykonywać w kółko tak długo, jak `()` warunek wewnątrz posiada true. Ponieważ warunek jest po `true`prostu wymieniony jako , to zawsze prawda, więc pętla działa na zawsze. Aby zamknąć program, użytkownik musi ręcznie zamknąć okno konsoli. W przeciwnym razie program zawsze czeka na nowe dane wejściowe.
   > - Słowo `cin` kluczowe służy do akceptowania danych wejściowych od użytkownika. Ten strumień wejściowy jest wystarczająco inteligentny, aby przetworzyć wiersz tekstu wprowadzony w oknie konsoli i umieścić go wewnątrz każdej z wymienionych zmiennych, w kolejności, w kolejności, w której dane wejściowe użytkownika są zgodne z wymaganą specyfikacją. Można zmodyfikować ten wiersz, aby zaakceptować różne typy danych wejściowych, na przykład więcej niż dwie liczby, chociaż `Calculate()` funkcja również musi zostać zaktualizowana, aby obsłużyć tę funkcję.
   > - Wyrażenie `c.Calculate(x, oper, y);` wywołuje `Calculate` funkcję zdefiniowaną wcześniej i dostarcza wprowadzone wartości wejściowe. Następnie funkcja zwraca liczbę, która `result`jest przechowywana w pliku .
   > - Na koniec `result` jest drukowany na konsoli, więc użytkownik widzi wynik obliczeń.

### <a name="build-and-test-the-code-again"></a>Ponownie skompiluj i przetestuj kod

Teraz nadszedł czas, aby przetestować program ponownie, aby upewnić się, że wszystko działa poprawnie.

1. Naciśnij **klawisze Ctrl+F5,** aby odbudować i uruchomić aplikację.

1. Wprowadź `5 + 5`i naciśnij klawisz **Enter**. Sprawdź, czy wynik wynosi 10.

   ![Wynik 5 + 5](./media/calculator-five-plus-five.png "Wynik 5 + 5")

## <a name="debug-the-app"></a>Debugowanie aplikacji

Ponieważ użytkownik może wpisać cokolwiek w oknie konsoli, upewnijmy się, że kalkulator obsługuje niektóre dane wejściowe zgodnie z oczekiwaniami. Zamiast uruchamiać program, niech debugować go zamiast, dzięki czemu możemy sprawdzić, co robi w szczegółach, krok po kroku.

### <a name="to-run-the-app-in-the-debugger"></a>Aby uruchomić aplikację w debugerze

1. Ustaw punkt przerwania `result = c.Calculate(x, oper, y);` w wierszu, zaraz po tym, jak użytkownik został poproszony o wprowadzenie danych wejściowych. Aby ustawić punkt przerwania, kliknij obok linii na szarym pionowym pasku wzdłuż lewej krawędzi okna edytora. Pojawi się czerwona kropka.

   ![Ustawianie punktu przerwania](./media/calculator-set-breakpoint.gif "Ustawianie punktu przerwania")

   Teraz, gdy debugujemy program, zawsze wstrzymuje wykonanie w tym wierszu. Mamy już przybliżone przekonanie, że program działa w prostych przypadkach. Ponieważ nie chcemy wstrzymać wykonywania za każdym razem, niech się punkt przerwania warunkowe.

1. Kliknij prawym przyciskiem myszy czerwoną kropkę reprezentującą punkt przerwania, a następnie wybierz pozycję **Warunki**. W polu edycji warunku wprowadź . `(y == 0) && (oper == '/')` Po zakończeniu wybierz przycisk **Zamknij.** Warunek zostanie zapisany automatycznie.

   ![Ustawianie warunkowego punktu przerwania](./media/calculator-conditional-breakpoint.gif "Ustawianie warunkowego punktu przerwania")

   Teraz wstrzymujemy wykonywanie w punkcie przerwania, w szczególności, jeśli zostanie podjęta próba podziału przez 0.

1. Aby debugować program, naciśnij **klawisz F5**lub wybierz przycisk **lokalnego paska narzędzi Windows Debugger** z ikoną zielonej strzałki. W aplikacji konsoli, jeśli wprowadzisz coś w rodzaju "5 - 0", program zachowuje się normalnie i działa. Jeśli jednak wpiszesz "10 / 0", zatrzymuje się w punkcie przerwania. Można nawet umieścić dowolną liczbę spacji między operatorem a numerami; `cin` jest wystarczająco inteligentny, aby odpowiednio przeanalizować dane wejściowe.

   ![Pauza w warunkowym punkcie przerwania](./media/calculator-debug-conditional.gif "Pauza w warunkowym punkcie przerwania")

### <a name="useful-windows-in-the-debugger"></a>Przydatne okna w debugerze

Za każdym razem, gdy debugujesz kod, można zauważyć, że pojawiają się nowe okna. Te okna mogą pomóc w debugowaniu. Spójrz na okno **Autos.** Okno **Autos** pokazuje bieżące wartości zmiennych używanych co najmniej trzy wiersze przed i do bieżącego wiersza.

   ![Okno Autos](./media/calculator-autos.png "Okno Autos")

Aby wyświetlić wszystkie zmienne z tej funkcji, przełącz się do okna **Zmiennych.** Można faktycznie zmodyfikować wartości tych zmiennych podczas debugowania, aby zobaczyć, jaki wpływ będą miały na program. W takim przypadku zostawimy je w spokoju.

   ![Okno Miejscowi](./media/calculator-locals.png "Okno Miejscowi")

Można również po prostu najechać kursorem na zmienne w samym kodzie, aby zobaczyć ich bieżące wartości, w których wykonanie jest obecnie wstrzymane. Upewnij się, że okno edytora jest w centrum uwagi, klikając go najpierw.

   ![Kursoruj, aby wyświetlić bieżące wartości zmiennych](./media/calculator-hover-tooltip.gif "Kursoruj, aby wyświetlić bieżące wartości zmiennych")

### <a name="to-continue-debugging"></a>Aby kontynuować debugowanie

1. Żółta linia po lewej stronie pokazuje bieżący punkt wykonania. Bieżąca linia `Calculate`wywołuje , więc naciśnij **klawisz F11,** aby **przejść do** funkcji. Znajdziesz się w ciele `Calculate` funkcji. Bądź ostrożny z **Step Into**; jeśli zrobisz to za dużo, możesz tracić dużo czasu. Przechodzi do dowolnego kodu, którego używasz w wierszu, w tym standardowych funkcji biblioteki.

1. Teraz, gdy punkt wykonania znajduje się `Calculate` na początku funkcji, naciśnij **klawisz F10,** aby przejść do następnego wiersza w wykonaniu programu. **F10** jest również znany jako **Step Over**. Krok **można** użyć, aby przejść z linii do wiersza, bez zagłębiania się w szczegóły tego, co dzieje się w każdej części wiersza. Ogólnie rzecz biorąc należy użyć **Step Over** zamiast **Step Into**, chyba że chcesz zanurzyć się głębiej w `Calculate`kod, który jest wywoływany z innego miejsca (jak to miało miejsce, aby dotrzeć do ciała ).

1. Kontynuuj korzystanie **z F10** do **step over** `main()` każdego wiersza, aż wrócisz `cout` do funkcji w innym pliku i zatrzymać się w wierszu.

   ![Wyjdź z obliczania i sprawdź wynik](./media/calculator-undefined-zero.gif "Wyjdź z obliczania i sprawdź wynik")

   Wygląda na to, że program robi to, czego się oczekuje: przyjmuje pierwszą liczbę i dzieli ją przez drugą. W `cout` wierszu umieść `result` wskaźnik myszy na `result` zmiennej lub spójrz w oknie **Autos.** Zobaczysz, że jego wartość jest wyświetlana jako "inf", która nie wygląda dobrze, więc naprawmy to. Linia `cout` po prostu wyprowadza dowolną `result`wartość, więc po wykonaniu jednego kroku do przodu za pomocą **F10**zostanie wyświetlone okno konsoli:

   ![Wynik podziału przez zero](./media/calculator-divide-by-zero-fail.png "Wynik podziału przez zero")

   Ten wynik dzieje się, ponieważ dzielenie przez zero jest niezdefiniowane, więc program nie ma numerycznej odpowiedzi na żądaną operację.

### <a name="to-fix-the-divide-by-zero-error"></a>Aby naprawić błąd "podziel przez zero"

Obsłużmy dzielenie przez zero bardziej wdzięku, dzięki czemu użytkownik może zrozumieć problem.

1. Wykonuj następujące zmiany w *calculatorTutorial.cpp*. (Możesz pozostawić program uruchomiony podczas edycji, dzięki funkcji debugera o nazwie **Edytuj i Kontynuuj):**

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

1. Teraz naciśnij **klawisz F5** raz. Wykonywanie programu trwa do końca, dopóki nie musi wstrzymać, aby poprosić o dane wejściowe użytkownika. Wprowadź `10 / 0` ponownie. Teraz drukowana jest bardziej pomocna wiadomość. Użytkownik jest proszony o więcej danych wejściowych, a program kontynuuje wykonywanie normalnie.

   ![Ostateczny wynik po zmianach](./media/calculator-final-verification.gif "Ostateczny wynik po zmianach")

   > [!Note]
   > Podczas edycji kodu w trybie debugowania, istnieje ryzyko, że kod staje się przestarzały. Dzieje się tak, gdy debuger jest nadal uruchomiony stary kod i nie został jeszcze zaktualizowany o zmiany. Debuger wyskakuje okno dialogowe, aby poinformować, kiedy to nastąpi. Czasami może być konieczne naciśnięcie **klawisza F5,** aby odświeżyć wykonywany kod. W szczególności jeśli dokonasz zmiany wewnątrz funkcji, podczas gdy punkt wykonania znajduje się wewnątrz tej funkcji, musisz wyjść z funkcji, a następnie z powrotem do niej ponownie, aby uzyskać zaktualizowany kod. Jeśli to nie działa z jakiegoś powodu i pojawi się komunikat o błędzie, możesz zatrzymać debugowanie, klikając czerwony kwadrat na pasku narzędzi w menu w górnej części IDE, a następnie ponownie rozpocząć debugowanie, wprowadzając **klawisz F5** lub wybierając zieloną strzałkę "play" obok przycisku stop na pasku narzędzi.

   > Opis skrótów uruchamiania i debugowania
   >
   > - **F5** (lub **Debug** > **Start Debug Debugging**) rozpoczyna sesję debugowania, jeśli nie jest jeszcze aktywny i uruchamia program, dopóki punkt przerwania nie zostanie trafiony lub program wymaga danych wejściowych użytkownika. Jeśli nie jest potrzebne żadne dane wejściowe użytkownika i nie jest dostępny punkt przerwania, program kończy działanie, a okno konsoli zamyka się po zakończeniu działania programu. Jeśli masz coś takiego jak program "Hello World", użyj **klawiszy Ctrl+F5** lub ustaw punkt przerwania przed wprowadzeniem **F5,** aby okno było otwarte.
   > - **Ctrl +F5** (lub **Debug** > **start bez debugowania)** uruchamia aplikację bez przechodzenia w tryb debugowania. Jest to nieco szybsze niż debugowanie, a okno konsoli pozostaje otwarte po zakończeniu wykonywania programu.
   > - **F10** (znany jako **Step Over)** umożliwia iterację za pomocą kodu, wiersz po wierszu i wizualizacji sposobu uruchamiania kodu i wartości zmiennych na każdym etapie wykonywania.
   > - **F11** (znany jako **Step Into)** działa podobnie do **Step Over**, z tą różnicą, że kroki do wszystkich funkcji wywoływanych w wierszu wykonywania. Na przykład jeśli linia wykonywana wywołuje funkcję, naciśnięcie **klawisza F11** przenosi wskaźnik do treści funkcji, dzięki czemu można wykonać kod funkcji jest uruchamiany przed powrotem do wiersza, który rozpoczął się w. Naciśnięcie **klawisza F10** kroki nad wywołaniem funkcji i po prostu przechodzi do następnego wiersza; wywołanie funkcji nadal się dzieje, ale program nie zatrzymuje się, aby pokazać, co robi.

### <a name="close-the-app"></a>Zamykanie aplikacji

- Jeśli nadal działa, zamknij okno konsoli dla aplikacji kalkulatora.

## <a name="the-finished-app"></a>Ukończona aplikacja

Gratulacje! Kod aplikacji kalkulatora został ukończony, a następnie skupilowany i debugowany w programie Visual Studio.

## <a name="next-steps"></a>Następne kroki

[Dowiedz się więcej o programie Visual Studio dla języka C++](https://blogs.msdn.microsoft.com/vcblog/2017/04/21/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end
