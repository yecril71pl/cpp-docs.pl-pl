---
title: 'Przewodnik: Praca z projektami i rozwiązaniamiC++()'
ms.date: 05/14/2019
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
ms.openlocfilehash: 6d9ee71e2608c2ed4935e7a5a3c54af45921e5d2
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108397"
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Przewodnik: Praca z projektami i rozwiązaniamiC++()

Oto jak utworzyć projekt C++ w Visual Studio, dodać kod, a następnie skompilować i uruchomić projekt. Projektem w tym instruktażu jest program, który śledzi, ilu graczy gra w różne gry karciane.

W programie Visual Studio prace są zorganizowane w projekty i rozwiązania. Rozwiązanie może mieć więcej niż jeden projekt — na przykład bibliotekę DLL i plik wykonywalny, który odwołuje się do tej biblioteki DLL. Aby uzyskać więcej informacji, zobacz [rozwiązania i projekty](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="before-you-start"></a>Przed rozpoczęciem

Aby ukończyć ten przewodnik, musisz mieć program Visual Studio 2017 lub nowszy. Jeśli potrzebujesz kopii, Oto krótki przewodnik: [Zainstaluj C++ obsługę w programie Visual Studio](../build/vscpp-step-0-installation.md). Jeśli jeszcze tego nie zrobiono, wykonaj następujące czynności po zakończeniu instalacji w samouczku "Hello, World", aby upewnić C++ się, że składniki są poprawnie zainstalowane i wszystkie działają.

Pozwala ona na zapoznanie się z podstawą C++ języka i wiedzą, w jaki sposób jest używany kompilator, konsolidator i debuger. W tym samouczku założono również, że znasz system Windows i jak używać menu, okien dialogowych,

## <a name="create-a-project"></a>Tworzenie projektu

Aby utworzyć projekt, należy najpierw wybrać szablon typu projektu. Dla każdego typu projektu program Visual Studio ustawia ustawienia kompilatora i — w zależności od typu — generuje kod początkowy, który można później zmodyfikować. Poniższe kroki różnią się w zależności od używanej wersji programu Visual Studio. Upewnij się, że selektor wersji w lewym górnym rogu tej strony ma ustawioną poprawną wersję.

::: moniker range="vs-2019"

### <a name="to-create-a-project-in-visual-studio-2019"></a>Aby utworzyć projekt w programie Visual Studio 2019

1. Z menu głównego wybierz pozycję **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Tworzenie nowego projektu** .

1. W górnej części okna dialogowego Ustaw **Język** na **C++** , ustaw platformę na **system Windows**i ustaw **Typ projektu** na **Console**.

1. Z listy filtrowane typy projektów wybierz pozycję **Aplikacja konsolowa** , a następnie wybierz przycisk **dalej**. Na następnej stronie wprowadź *grę* jako nazwę dla projektu.

   Można zaakceptować lokalizację domyślną na liście rozwijanej **Lokalizacja** , wprowadzić inną lokalizację lub wybrać przycisk **Przeglądaj** , aby przejść do katalogu, w którym ma zostać zapisany projekt.

   Podczas tworzenia projektu program Visual Studio umieszcza projekt w rozwiązaniu. Domyślnie rozwiązanie ma taką samą nazwę jak projekt. Można zmienić nazwę w polu **Nazwa rozwiązania** , ale w tym przykładzie należy zachować nazwę domyślną.

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt.

   Program Visual Studio tworzy nowe rozwiązanie i pliki projektu, a następnie otwiera edytor dla wygenerowanego pliku kodu źródłowego Game. cpp.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017"></a>Aby utworzyć projekt w programie Visual Studio 2017

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **zainstalowane** i wybierz pozycję Wizualizacja **C++** , jeśli nie jest jeszcze otwarty.

1. Na liście zainstalowanych szablonów w środkowym okienku wybierz pozycję **Aplikacja konsolowa systemu Windows**.

1. Wprowadź nazwę projektu w polu **Nazwa** . Na potrzeby tego przykładu wpisz *Game*.

   Można zaakceptować lokalizację domyślną na liście rozwijanej **Lokalizacja** , wprowadzić inną lokalizację lub wybrać przycisk **Przeglądaj** , aby przejść do katalogu, w którym ma zostać zapisany projekt.

   Podczas tworzenia projektu program Visual Studio umieszcza projekt w rozwiązaniu. Domyślnie rozwiązanie ma taką samą nazwę jak projekt. Można zmienić nazwę w polu **Nazwa rozwiązania** , ale w tym przykładzie należy zachować nazwę domyślną.

1. Wybierz przycisk **OK** , aby utworzyć projekt.

   Program Visual Studio tworzy nowe rozwiązanie i pliki projektu, a następnie otwiera edytor dla wygenerowanego pliku kodu źródłowego Game. cpp.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-project-in-visual-studio-2015"></a>Aby utworzyć projekt w programie Visual Studio 2015

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **zainstalowane** i wybierz pozycję Wizualizacja **C++** , jeśli nie jest jeszcze otwarty.

1. Na liście zainstalowanych szablonów w środkowym okienku wybierz pozycję **aplikacja konsoli Win32**.

1. Wprowadź nazwę projektu w polu **Nazwa** . Na potrzeby tego przykładu wpisz *Game*.

   Można zaakceptować lokalizację domyślną na liście rozwijanej **Lokalizacja** , wprowadzić inną lokalizację lub wybrać przycisk **Przeglądaj** , aby przejść do katalogu, w którym ma zostać zapisany projekt.

   Podczas tworzenia projektu program Visual Studio umieszcza projekt w rozwiązaniu. Domyślnie rozwiązanie ma taką samą nazwę jak projekt. Można zmienić nazwę w polu **Nazwa rozwiązania** , ale w tym przykładzie należy zachować nazwę domyślną.

1. Wybierz przycisk **OK** , aby utworzyć projekt.

   Program Visual Studio tworzy nowe rozwiązanie i pliki projektu, a następnie otwiera edytor dla wygenerowanego pliku kodu źródłowego Game. cpp.

::: moniker-end

## <a name="organize-projects-and-files"></a>Organizuj projekty i pliki

Za pomocą **Eksplorator rozwiązań** można organizować i zarządzać projektami, plikami i innymi zasobami w rozwiązaniu.

W tej części przewodnika pokazano, jak dodać klasę do projektu. Po dodaniu klasy program Visual Studio dodaje odpowiednie pliki. h i. cpp. Wyniki można zobaczyć w **Eksplorator rozwiązań**.

### <a name="to-add-a-class-to-a-project"></a>Aby dodać klasę do projektu

1. Jeśli okno **Eksplorator rozwiązań** nie jest wyświetlane w programie Visual Studio, na pasku menu wybierz polecenie **Wyświetl** > **Eksplorator rozwiązań**.

1. W **Eksplorator rozwiązań**wybierz projekt **gry** . Na pasku menu wybierz **projekt** > **Dodaj klasę**.

1. W oknie dialogowym **Dodawanie klasy** wprowadź *plik Cardgame* w polu **Nazwa klasy** . Nie należy modyfikować domyślnych nazw plików i ustawień. Wybierz **OK** przycisku.

   Program Visual Studio tworzy nowe pliki i dodaje je do projektu. Można je wyświetlić w oknie **Eksplorator rozwiązań** . Pliki plik Cardgame. h i plik Cardgame. cpp są otwierane w edytorze.

1. Edytuj plik plik Cardgame. h i wprowadź następujące zmiany:

   - Dodaj dwie prywatne składowe danych po nawiasie klamrowym otwierającym definicję klasy.
     <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Zmodyfikuj domyślnego konstruktora wygenerowanego przez Visual Studio. Po specyfikatorze `public:` dostępu Znajdź wiersz, który wygląda następująco:

      `Cardgame();`

      Zmodyfikuj konstruktora, aby przyjmować jeden parametr typu `int`o nazwie *Players*.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - Po domyślnym destruktorze Dodaj wbudowaną deklarację dla `static int` funkcji składowej o nazwie getuczestnicy, która nie przyjmuje `totalParticipants` parametrów i zwraca wartość.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   Plik plik Cardgame. h powinien wyglądać podobnie do poniższego kodu:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->

    ```cpp
    #pragma once
    class Cardgame
    {
        int players;
        static int totalParticipants;
    public:
        Cardgame(int players);
        ~Cardgame();
        static int GetParticipants() { return totalParticipants; }
    };
    ```

   Wiersz `#pragma once` nakazuje kompilatorowi dołączenie pliku nagłówka tylko jeden raz. Aby uzyskać więcej informacji, zobacz [jeden raz](../preprocessor/once.md). Aby uzyskać informacje dotyczące C++ innych słów kluczowych w pliku nagłówkowym, zobacz [klasy](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [static](../cpp/storage-classes-cpp.md)i [Public](../cpp/public-cpp.md).

1. Wybierz kartę **plik Cardgame. cpp** w górnej części okienka Edycja, aby otworzyć ją do edycji.

1. Usuń wszystko z pliku i zastąp je kodem:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->

    ```cpp
    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    int Cardgame::totalParticipants = 0;

    Cardgame::Cardgame(int players)
        : players(players)
    {
        totalParticipants += players;
        cout << players << " players have started a new game.  There are now "
             << totalParticipants << " players in total." << endl;
    }

    Cardgame::~Cardgame()
    {
    }
    ```

   > [!NOTE]
   > Podczas wprowadzania kodu można użyć funkcji autouzupełniania. Na przykład, jeśli wprowadzisz ten kod na klawiaturze, możesz wprowadzić wartość *pl* lub *tot* , a następnie nacisnąć klawisz **Ctrl**+**spacja**. Autouzupełnianie wprowadza `players` lub `totalParticipants` dla Ciebie.

## <a name="add-test-code-to-your-main-function"></a>Dodawanie kodu testowego do funkcji Main

Dodaj do aplikacji kod, który testuje nowe funkcje.

### <a name="to-add-test-code-to-the-project"></a>Aby dodać kod testowy do projektu

1. W oknie Edytor **gier. cpp** Zastąp istniejący kod:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->

    ```cpp
    // Game.cpp : Defines the entry point for the console application.
    //

    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    void PlayGames()
    {
        Cardgame bridge(4);
        Cardgame blackjack(8);
        Cardgame solitaire(1);
        Cardgame poker(5);
    }

    int main()
    {
        PlayGames();
        return 0;
    }
    ```

   Kod dodaje funkcję `PlayGames`testową,, do kodu źródłowego i wywołuje ją w `main`.

## <a name="build-and-run-your-app-project"></a>Kompilowanie i uruchamianie projektu aplikacji

Następnie Skompiluj projekt i uruchom aplikację.

### <a name="to-build-and-run-the-project"></a>Aby skompilować i uruchomić projekt

1. Na pasku menu wybierz polecenie **Kompiluj** > **kompilację rozwiązania**.

   Dane wyjściowe z kompilacji są wyświetlane w oknie **danych wyjściowych** . Jeśli kompilacja zakończy się pomyślnie, dane wyjściowe powinny wyglądać następująco:

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>pch.cpp
    1>Cardgame.cpp
    1>Game.cpp
    1>Generating Code...
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

   Okno **dane wyjściowe** może pokazywać różne kroki, w zależności od konfiguracji kompilacji, ale jeśli kompilacja projektu zakończy się powodzeniem, ostatni wiersz powinien wyglądać podobnie do przedstawionego w danych wyjściowych.

   Jeśli kompilacja nie powiodła się, porównaj kod z kodem, który jest przedstawiony w poprzednich krokach.

1. Aby uruchomić projekt, na pasku menu wybierz **Debuguj** > **Uruchom bez debugowania**. Powinien pojawić się okno konsoli, a dane wyjściowe powinny wyglądać następująco:

    ```Output
    4 players have started a new game.  There are now 4 players in total.
    8 players have started a new game.  There are now 12 players in total.
    1 players have started a new game.  There are now 13 players in total.
    5 players have started a new game.  There are now 18 players in total.
    ```

   Naciśnij klawisz, aby odrzucić okno konsoli.

Gratulacje, projekt aplikacji i rozwiązanie zostały pomyślnie skompilowane. Przejdź do przewodnika, aby dowiedzieć się więcej C++ na temat tworzenia projektów kodu w programie Visual Studio.

## <a name="next-steps"></a>Następne kroki

**Ubiegł** [Projektowanie aplikacji w języku C++ w środowisku Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)<br/>
**Ponown** [Przewodnik: Tworzenie projektu (C++)](../ide/walkthrough-building-a-project-cpp.md)

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
