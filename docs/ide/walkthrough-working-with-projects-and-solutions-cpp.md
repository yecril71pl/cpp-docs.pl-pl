---
title: 'Wskazówki: praca z projektami i rozwiązaniami (C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
ms.openlocfilehash: 36c64a74310c72df38021aebd8abb3ee430da3f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375897"
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Wskazówki: praca z projektami i rozwiązaniami (C++)

Oto jak utworzyć projekt C++ w Visual Studio, dodać kod, a następnie skompilować i uruchomić projekt. Projektem w tym instruktażu jest program, który śledzi, ilu graczy gra w różne gry karciane.

W programie Visual Studio praca jest zorganizowana w projektach i rozwiązaniach. Rozwiązanie może mieć więcej niż jeden projekt — na przykład bibliotekę DLL i plik wykonywalny, który odwołuje się do tej biblioteki DLL. Aby uzyskać więcej informacji, zobacz [Rozwiązania i projekty](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="before-you-start"></a>Przed rozpoczęciem

Aby ukończyć ten instruktaż, potrzebujesz programu Visual Studio 2017 lub nowszego. Jeśli potrzebujesz kopii, oto krótki przewodnik: [Zainstaluj obsługę języka C++ w programie Visual Studio.](../build/vscpp-step-0-installation.md) Jeśli jeszcze tego nie zrobiłeś, wykonaj następne kroki po instalacji za pomocą samouczka "Hello, World", aby upewnić się, że składniki języka C++ są poprawnie zainstalowane i wszystko działa.

Pomaga, jeśli rozumiesz podstawy języka C++ i wiesz, do czego służy kompilator, konsolidator i debuger. W samouczku przyjęto również założenie, że znasz system Windows i jak korzystać z menu, okien dialogowych,

## <a name="create-a-project"></a>Tworzenie projektu

Aby utworzyć projekt, należy najpierw wybrać szablon typu projektu. Dla każdego typu projektu program Visual Studio ustawia ustawienia kompilatora i — w zależności od typu — generuje kod startowy, który można później zmodyfikować. Poniższe kroki różnią się w zależności od używanej wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj formantu selektor **wersji.** Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-a-project-in-visual-studio-2019"></a>Aby utworzyć projekt w programie Visual Studio 2019

1. Z menu głównego wybierz polecenie **Plik** > **nowego** > **projektu,** aby otworzyć okno **dialogowe Tworzenie nowego projektu.**

1. W górnej części okna dialogowego ustaw **język** na **C++,** ustaw **platformę** na **Windows**i ustaw **typ projektu** na **Konsola**.

1. Z filtru listy typów projektów wybierz pozycję **Aplikacja konsoli,** a następnie wybierz pozycję **Dalej**. Na następnej stronie wprowadź *grę* jako nazwę projektu.

   Możesz zaakceptować domyślną lokalizację na liście rozwijanej **Lokalizacja,** wprowadzić inną lokalizację lub wybrać przycisk **Przeglądaj,** aby przejść do katalogu, w którym chcesz zapisać projekt.

   Podczas tworzenia projektu visual studio umieszcza projekt w rozwiązaniu. Domyślnie rozwiązanie ma taką samą nazwę jak projekt. Nazwę można zmienić w polu **Nazwa rozwiązania,** ale w tym przykładzie zachować domyślną nazwę.

1. Wybierz przycisk **Utwórz,** aby utworzyć projekt.

   Visual Studio tworzy nowe rozwiązanie i pliki projektu i otwiera edytor pliku kodu źródłowego Game.cpp, który wygenerował.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017"></a>Aby utworzyć projekt w programie Visual Studio 2017

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

1. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **Zainstalowany** i wybierz pozycję **Visual C++,** jeśli nie jest jeszcze otwarty.

1. Na liście zainstalowanych szablonów w środkowym okienku wybierz pozycję **Aplikacja konsoli systemu Windows**.

1. Wprowadź nazwę projektu w polu **Nazwa.** W tym przykładzie wprowadź *game*.

   Możesz zaakceptować domyślną lokalizację na liście rozwijanej **Lokalizacja,** wprowadzić inną lokalizację lub wybrać przycisk **Przeglądaj,** aby przejść do katalogu, w którym chcesz zapisać projekt.

   Podczas tworzenia projektu visual studio umieszcza projekt w rozwiązaniu. Domyślnie rozwiązanie ma taką samą nazwę jak projekt. Nazwę można zmienić w polu **Nazwa rozwiązania,** ale w tym przykładzie zachować domyślną nazwę.

1. Wybierz przycisk **OK,** aby utworzyć projekt.

   Visual Studio tworzy nowe rozwiązanie i pliki projektu i otwiera edytor pliku kodu źródłowego Game.cpp, który wygenerował.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-project-in-visual-studio-2015"></a>Aby utworzyć projekt w programie Visual Studio 2015

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

1. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **Zainstalowany** i wybierz pozycję **Visual C++,** jeśli nie jest jeszcze otwarty.

1. Na liście zainstalowanych szablonów w środkowym okienku wybierz pozycję **Aplikacja konsoli Win32**.

1. Wprowadź nazwę projektu w polu **Nazwa.** W tym przykładzie wprowadź *game*.

   Możesz zaakceptować domyślną lokalizację na liście rozwijanej **Lokalizacja,** wprowadzić inną lokalizację lub wybrać przycisk **Przeglądaj,** aby przejść do katalogu, w którym chcesz zapisać projekt.

   Podczas tworzenia projektu visual studio umieszcza projekt w rozwiązaniu. Domyślnie rozwiązanie ma taką samą nazwę jak projekt. Nazwę można zmienić w polu **Nazwa rozwiązania,** ale w tym przykładzie zachować domyślną nazwę.

1. Wybierz przycisk **OK,** aby utworzyć projekt.

   Visual Studio tworzy nowe rozwiązanie i pliki projektu i otwiera edytor pliku kodu źródłowego Game.cpp, który wygenerował.

::: moniker-end

## <a name="organize-projects-and-files"></a>Organizowanie projektów i plików

Za pomocą **Eksploratora rozwiązań** można organizować projekty, pliki i inne zasoby w rozwiązaniu oraz zarządzać nimi.

W tej części przewodnika pokazano, jak dodać klasę do projektu. Po dodaniu klasy program Visual Studio dodaje odpowiednie pliki .h i .cpp. Wyniki można zobaczyć w **Eksploratorze rozwiązań**.

### <a name="to-add-a-class-to-a-project"></a>Aby dodać klasę do projektu

1. Jeśli okno **Eksploratora rozwiązań** nie jest wyświetlane w programie Visual Studio, na pasku menu wybierz pozycję **Wyświetl** > **Eksploratora rozwiązań**.

1. W **Eksploratorze rozwiązań**wybierz projekt **Gry.** Na pasku menu wybierz pozycję **Project** > **Add Class**.

1. W oknie dialogowym **Dodawanie klasy** wprowadź grę w *grze cardgame* w polu **Nazwa klasy.** Nie należy modyfikować domyślnych nazw plików i ustawień. Wybierz przycisk **OK.**

   Program Visual Studio tworzy nowe pliki i dodaje je do projektu. Można je zobaczyć w oknie **Eksploratora rozwiązań.** Pliki Cardgame.h i Cardgame.cpp są otwierane w edytorze.

1. Edytuj plik Cardgame.h i wykonuj następujące zmiany:

   - Dodaj dwie prywatne składowe danych po nawiasie klamrowym otwierającym definicję klasy.
     <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Zmodyfikuj domyślnego konstruktora wygenerowanego przez Visual Studio. Po `public:` specyfikatoru dostępu znajdź linię, która wygląda następująco:

      `Cardgame();`

      Zmodyfikuj konstruktora, aby wziąć jeden parametr typu `int`, nazwany *gracz*.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - Po domyślnym destruktorze dodaj deklarację `static int` wbudowaną dla funkcji elementu członkowskiego o nazwie `totalParticipants` *GetParticipants,* która nie przyjmuje żadnych parametrów i zwraca wartość.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   Plik Cardgame.h powinien przypominać poniższy kod po jego zmianie:

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

   Wiersz `#pragma once` mówi kompilatorowi, aby uwzględnił plik nagłówka tylko jeden raz. Aby uzyskać więcej informacji, zobacz [jeden raz](../preprocessor/once.md). Aby uzyskać informacje o innych słowach kluczowych języka C++ w powyższym pliku nagłówka, zobacz [class](../cpp/class-cpp.md), [int,](../cpp/fundamental-types-cpp.md) [static](../cpp/storage-classes-cpp.md)i [public](../cpp/public-cpp.md).

1. Wybierz kartę **Cardgame.cpp** w górnej części okienka edycji, aby otworzyć ją do edycji.

1. Usuń wszystko w pliku i zastąp go kodem:

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
   > Podczas wprowadzania kodu można użyć funkcji autouzupełniania. Na przykład, jeśli wprowadzisz ten kod na klawiaturze, możesz wprowadzić *pl* lub *tot,* a następnie nacisnąć **klawisz Ctrl**+**Spacja**. Automatyczne wypełnianie `players` wchodzi `totalParticipants` lub dla Ciebie.

## <a name="add-test-code-to-your-main-function"></a>Dodawanie kodu testowego do funkcji głównej

Dodaj kod do aplikacji, który testuje nowe funkcje.

### <a name="to-add-test-code-to-the-project"></a>Aby dodać kod testu do projektu

1. W oknie edytora **Game.cpp** zastąp istniejący kod:

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

   Kod dodaje funkcję testową, `PlayGames`do kodu źródłowego `main`i wywołuje ją w .

## <a name="build-and-run-your-app-project"></a>Tworzenie i uruchamianie projektu aplikacji

Następnie skompiluj projekt i uruchom aplikację.

### <a name="to-build-and-run-the-project"></a>Aby skompilować i uruchomić projekt

1. Na pasku menu wybierz pozycję **Build** > **Build Solution**.

   Dane wyjściowe z kompilacji są wyświetlane w oknie **Dane wyjściowe.** Jeśli kompilacja zakończy się pomyślnie, dane wyjściowe powinny przypominać:

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>pch.cpp
    1>Cardgame.cpp
    1>Game.cpp
    1>Generating Code...
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

   Okno **Dane wyjściowe** może wyświetlać różne kroki, w zależności od konfiguracji kompilacji, ale jeśli kompilacja projektu powiedzie się, ostatni wiersz powinien przypominać pokazane dane wyjściowe.

   Jeśli kompilacja nie powiodła się, porównaj kod z kodem, który jest wyświetlany we wcześniejszych krokach.

1. Aby uruchomić projekt, na pasku menu wybierz pozycję **Debugowanie** > **start bez debugowania**. Powinno pojawić się okno konsoli, a dane wyjściowe powinny przypominać:

    ```Output
    4 players have started a new game.  There are now 4 players in total.
    8 players have started a new game.  There are now 12 players in total.
    1 players have started a new game.  There are now 13 players in total.
    5 players have started a new game.  There are now 18 players in total.
    ```

   Naciśnij klawisz, aby odrzucić okno konsoli.

Gratulacje, pomyślnie powstał projekt aplikacji i rozwiązanie. Kontynuuj instruktaż, aby dowiedzieć się więcej o tym, jak tworzyć projekty kodu języka C++ w programie Visual Studio.

## <a name="next-steps"></a>Następne kroki

**Poprzedni:** [Korzystanie z środowiska IDE programu Visual Studio dla programowania pulpitu w języku C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)<br/>
**Dalej:** [Przewodnik: Tworzenie projektu (C++)](../ide/walkthrough-building-a-project-cpp.md)

## <a name="see-also"></a>Zobacz też

[Odwołanie do języka języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
