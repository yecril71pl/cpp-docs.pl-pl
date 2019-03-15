---
title: 'Przewodnik: Praca z projektami i rozwiązaniami (C++)'
ms.date: 09/14/2018
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
ms.openlocfilehash: 9408938b670d8130305f2e1c1258fc6fcb9875bb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820068"
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Przewodnik: Praca z projektami i rozwiązaniami (C++)

Oto jak utworzyć projekt C++ w Visual Studio, dodać kod, a następnie skompilować i uruchomić projekt. Projektem w tym instruktażu jest program, który śledzi, ilu graczy gra w różne gry karciane.

W programie Visual Studio praca jest organizowana w projektach i rozwiązaniach. To rozwiązanie może mieć więcej niż jeden projekt — na przykład biblioteki DLL i plik wykonywalny, który odwołuje się do tej biblioteki DLL. Aby uzyskać więcej informacji, zobacz [rozwiązania i projekty](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="before-you-start"></a>Przed rozpoczęciem

Do przeprowadzenia tego instruktażu, potrzebujesz programu Visual Studio 2017 w wersji 15.3 lub nowszej. Jeśli potrzebujesz kopii, poniżej przedstawiono krótki przewodnik: [Instalowanie obsługi języka C++ w programie Visual Studio](../build/vscpp-step-0-installation.md). Jeśli go jeszcze nie wykonano jeszcze, wykonaj następujące kroki po zakończeniu instalacji przy użyciu samouczka "Hello, World", aby upewnić się, że Visual C++ jest poprawnie zainstalowane i jego wszystkie działania.

Pomaga ono, jeśli można rozumieć podstawy języka C++ i ustalić, jakie kompilatora, konsolidatora i debugera są używane do. W samouczku założono, że znasz Windows i sposobu użycia menu, okna dialogowe,

## <a name="create-a-project"></a>Tworzenie projektu

Aby utworzyć projekt, należy najpierw wybrać szablon typu projektu. Dla każdego typu projektu programu Visual Studio Ustawia ustawienia kompilatora i — w zależności od typu — generuje kod startowy, który można później zmodyfikować.

### <a name="to-create-a-project"></a>Aby utworzyć projekt

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

1. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **zainstalowane** i wybierz **Visual C++**, jeśli nie jest otwarty.

1. Na liście zainstalowanych szablonów w środkowym okienku wybierz **aplikacji konsoli Windows**.

   > [!NOTE]
   > W poprzednich wersjach programu Visual Studio zainstalowanych szablonu jest wywoływana **Aplikacja konsoli Win32**.

1. Wprowadź nazwę dla projektu w **nazwa** pole. W tym przykładzie wprowadź *gry*.

   Można zaakceptować lokalizację domyślną **lokalizacji** listy rozwijanej, wprowadzić inną lokalizację lub wybierz **Przeglądaj** przycisk, aby przejść do katalogu, w którym chcesz zapisać projekt.

   Podczas tworzenia projektu Visual Studio umieszcza projekt w rozwiązaniu. Domyślnie rozwiązanie ma taką samą nazwę jak projekt. Możesz zmienić nazwę w **Nazwa rozwiązania** polu, ale w tym przykładzie zachowamy nazwę domyślną.

1. Wybierz **OK** przycisk, aby utworzyć projekt.

   Visual Studio tworzy nowe rozwiązanie i pliki projektu i zostanie otwarty edytor dla pliku kodu źródłowego Game.cpp, jego wygenerowania.

## <a name="organize-projects-and-files"></a>Organizowanie projektów i plików

Możesz użyć **Eksploratora rozwiązań** do organizowania i zarządzania projektami, plikami i innych zasobów w rozwiązaniu.

Tej części instruktażu pokazano, jak dodać klasę do projektu. Po dodaniu klasy program Visual Studio dodaje odpowiednie pliki .h i .cpp. Można wyświetlić wyniki w **Eksploratora rozwiązań**.

### <a name="to-add-a-class-to-a-project"></a>Aby dodać klasę do projektu

1. Jeśli **Eksploratora rozwiązań** okno nie jest wyświetlane w programie Visual Studio, na pasku menu, wybierz polecenie **widoku** > **Eksploratora rozwiązań**.

1. W **Eksploratora rozwiązań**, wybierz opcję **gry** projektu. Na pasku menu wybierz **projektu** > **Dodaj klasę**.

1. W **Dodaj klasę** okno dialogowe, wprowadź *wartość Cardgame* w **Nazwa klasy** pole. Nie należy modyfikować domyślnych nazw plików i ustawień. Wybierz **OK** przycisku.

   Visual Studio tworzy nowe pliki i dodaje je do projektu. Widać je w **Eksploratora rozwiązań** okna. Pliki Cardgame.h i Cardgame.cpp są otwarte w edytorze.

1. Edytuj plik Cardgame.h i wprowadzić te zmiany:

   - Dodaj dwie prywatne składowe danych po nawiasie klamrowym otwierającym definicję klasy.
     <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Zmodyfikuj domyślnego konstruktora wygenerowanego przez Visual Studio. Po `public:` specyfikatorze dostępu, znajdź wiersz, który wygląda następująco:

      `Cardgame();`

      Zmodyfikuj konstruktora, aby pobierał jeden parametr typu `int`o nazwie *graczy*.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - Po domyślnym destruktorze Dodaj wbudowaną deklarację dla `static int` funkcja elementu członkowskiego o nazwie *GetParticipants* która nie przyjmuje żadnych parametrów i zwraca `totalParticipants` wartość.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   Plik Cardgame.h powinien wyglądać podobnie poniższy kod, po zmianach przypominać:

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

   Wiersz `#pragma once` nakazuje kompilatorowi dołączenie pliku nagłówkowym tylko jeden raz. Aby uzyskać więcej informacji, zobacz [po](../preprocessor/once.md). Aby uzyskać informacje dotyczące innych słów kluczowych języka C++, w pliku nagłówkowym powyżej, zobacz [klasy](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [statyczne](../cpp/storage-classes-cpp.md), i [publicznych](../cpp/public-cpp.md).

1. Wybierz **Cardgame.cpp** kartę w górnej części okienka edycji, aby go otworzyć do edycji.

1. Usuń całą zawartość pliku i Zamień kod:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->

    ```cpp
    #include "pch.h"
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
   > Podczas wprowadzania kodu można użyć funkcji autouzupełniania. Na przykład, jeśli ten kod, za pomocą klawiatury, można wprowadzić *pl* lub *tot* , a następnie naciśnij klawisz **Ctrl**+**spacja**. Automatyczne uzupełnianie wprowadza `players` lub `totalParticipants` dla Ciebie.

## <a name="add-test-code-to-your-main-function"></a>Dodaj kod testowy do funkcji main

Dodawanie kodu do aplikacji, który umożliwia sprawdzenie, nowych funkcji.

### <a name="to-add-test-code-to-the-project"></a>Aby dodać kod testu do projektu

1. W **Game.cpp** okna edytora Zastąp istniejący kod składnią:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->

    ```cpp
    // Game.cpp : Defines the entry point for the console application.
    //

    #include "pch.h"
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

   Ten kod dodaje funkcję testową, `PlayGames`, aby kod źródłowy i wywołania w `main`.

## <a name="build-and-run-your-app-project"></a>Skompiluj i uruchom projekt aplikacji

Następnie skompilować projekt i uruchomić aplikację.

### <a name="to-build-and-run-the-project"></a>Aby skompilować i uruchomić projekt

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

   Dane wyjściowe z kompilacji są wyświetlane w **dane wyjściowe** okna. Jeśli kompilacja zakończy się pomyślnie, dane wyjściowe powinny przypominać:

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>pch.cpp
    1>Cardgame.cpp
    1>Game.cpp
    1>Generating Code...
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

   **Dane wyjściowe** okna może pokazywać różne kroki, w zależności od konfiguracji kompilacji, ale jeśli kompilacja projektu zakończy się pomyślnie, ostatni wiersz powinien być podobny wyświetlone dane wyjściowe.

   Jeśli kompilacja nie powiodła się, porównaj swój kod, aby kod, który jest wyświetlany w poprzednich krokach.

1. Aby uruchomić projekt, na pasku menu, wybierz opcję **debugowania** > **Rozpocznij bez debugowania**. Okno konsoli powinna zostać wyświetlona, a dane wyjściowe powinny przypominać:

    ```Output
    4 players have started a new game.  There are now 4 players in total.
    8 players have started a new game.  There are now 12 players in total.
    1 players have started a new game.  There are now 13 players in total.
    5 players have started a new game.  There are now 18 players in total.
    ```

   Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

Gratulacje, pomyślnie skompilowane rozwiązanie i projekt aplikacji. Nadal przewodnika, aby dowiedzieć się więcej o tym, jak tworzyć projekty kodu C++ w programie Visual Studio.

## <a name="next-steps"></a>Następne kroki

**Poprzednie:** [Projektowanie aplikacji w języku C++ w środowisku Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)<br/>
**Dalej:** [Przewodnik: Tworzenie projektu (C++)](../ide/walkthrough-building-a-project-cpp.md)<br/>

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemów kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
