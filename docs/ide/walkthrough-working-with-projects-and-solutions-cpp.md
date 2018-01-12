---
title: "Wskazówki: Praca z projektami i rozwiązaniami (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a20c0ee933d49465a841b638a8260181d7175ac5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Wskazówki: praca z projektami i rozwiązaniami (C++)

Oto jak utworzyć projekt C++ w Visual Studio, dodać kod, a następnie skompilować i uruchomić projekt. Projektem w tym instruktażu jest program, który śledzi, ilu graczy gra w różne gry karciane.

W programie Visual Studio pracy jest zorganizowana w projekty i rozwiązania. Rozwiązanie może zawierać więcej niż jeden projekt — na przykład bibliotekę DLL i plik wykonywalny, który odwołuje się do tej biblioteki DLL. Aby uzyskać więcej informacji, zobacz [rozwiązań i projektów](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="before-you-start"></a>Przed rozpoczęciem

W tym przewodniku, potrzebujesz programu Visual Studio 2017 wersji 15.3 lub nowszej. Jeśli potrzebujesz kopii, poniżej przedstawiono krótki przewodnik: [zainstalować obsługi języka C++ w programie Visual Studio](../build/vscpp-step-0-installation.md). Jeśli nie zostało to jeszcze zrobione go jeszcze, wykonaj następujące kroki po zakończeniu instalacji za pośrednictwem samouczek "Hello, World", aby upewnić się, że Visual C++ jest poprawnie zainstalowana i jego wszystkie działania.

Pomaga, jeśli informacje podstawowe informacje na temat języka C++ i wiedzieć, jaki kompilatora, konsolidatora i debuger służą do. W tym samouczku założono, że znasz systemu Windows i sposobu użycia menu i okien dialogowych,

## <a name="create-a-project"></a>Tworzenie projektu

Aby utworzyć projekt, należy najpierw wybrać szablon typu projektu. Dla każdego typu projektu programu Visual Studio Ustawia ustawienia kompilatora i — w zależności od typu — generuje kod początkowy, który można zmodyfikować później.

### <a name="to-create-a-project"></a>Aby utworzyć projekt

1. Na pasku menu wybierz **Plik > Nowy > Projekt**.

1. W lewym okienku **nowy projekt** okna dialogowego rozwiń **zainstalowana** i wybierz **Visual C++**, jeśli nie jest otwarty już.

1. Na liście szablonów zainstalowanych w środkowym okienku wybierz **aplikacji konsoli systemu Windows**.

1. Wprowadź nazwę projektu w **nazwa** pole. Na przykład wprowadź **gry**.

   Możesz zaakceptować domyślną lokalizację w **lokalizacji** listy rozwijanej, wprowadź inną lokalizację lub wybierz **Przeglądaj** przycisk, aby przejść do katalogu, w którym chcesz zapisać projekt.

   Podczas tworzenia projektu Visual Studio umieszcza projektu w rozwiązaniu. Domyślnie rozwiązanie ma taką samą nazwę jak projekt. Można zmienić nazwę w **Nazwa rozwiązania** polu, ale w tym przykładzie pozostaw nazwę domyślną.

1. Wybierz **OK** przycisk, aby utworzyć projekt.

   Visual Studio tworzy nowe rozwiązanie i pliki projektu i otwiera edytor dla pliku kodu źródłowego Game.cpp go wygenerować.

## <a name="organize-projects-and-files"></a>Organizowanie projektów i plików

Można użyć **Eksploratora rozwiązań** do organizowania i zarządzania nimi projektów, plików i innych zasobów w rozwiązaniu.

W tej części instruktażu pokazano, jak dodać klasę do projektu. Po dodaniu klasy Visual Studio dodaje odpowiednich .h i .cpp plików. Można wyświetlić wyniki w **Eksploratora rozwiązań**.

### <a name="to-add-a-class-to-a-project"></a>Aby dodać klasę do projektu

1. Jeśli **Eksploratora rozwiązań** okno nie jest wyświetlany w programie Visual Studio na pasku menu, wybierz **Widok > Eksploratora rozwiązań**.

1. W **Eksploratora rozwiązań**, wybierz pozycję **gry** projektu. Na pasku menu wybierz **projektu > Dodaj klasę**.

1. W **Dodaj klasę** okna dialogowego, wprowadź *Cardgame* w **Nazwa klasy** pole. Nie należy modyfikować domyślnych nazw plików i ustawień. Wybierz **OK** przycisku.

   Visual Studio tworzy nowe pliki i dodaje je do projektu. Można wyświetlić je w **Eksploratora rozwiązań** okna. Pliki Cardgame.h i Cardgame.cpp są otwarte w edytorze.

1. Edytuj plik Cardgame.h i wprowadzić te zmiany:

   - Dodaj dwie prywatne składowe danych po nawiasie klamrowym otwierającym definicję klasy.
      <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Zmodyfikuj domyślnego konstruktora wygenerowanego przez Visual Studio. Po `public:` specyfikator dostępu, znajdź wiersz, który wygląda następująco:

      `Cardgame();`

      Modyfikowanie tego konstruktora, aby mieć jeden parametr typu `int`nazwanego *odtwarzacze*.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - Po destruktor domyślne dodać deklaracja wbudowanego `static int` funkcję elementu członkowskiego o nazwie *GetParticipants* nie przyjmuje żadnych parametrów i zwraca `totalParticipants` wartość.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   Plik Cardgame.h powinien po zmianach przypominać:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->
   ```cpp
   #pragma once
   class Cardgame
   {
       int players;
       static int totalParticipants;
   public:
       Cardgame(int players);
       ~Cardgame(void);
       static int GetParticipants() { return totalParticipants; }
   };
   ```

   Wiersz `#pragma once` informuje kompilator, aby uwzględnić plik nagłówka tylko jeden raz. Aby uzyskać więcej informacji, zobacz [po](../preprocessor/once.md). Aby uzyskać informacje o innych słów kluczowych języka C++ w tym pliku nagłówka, zobacz [klasy](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [statycznych](../cpp/storage-classes-cpp.md), i [publicznego](../cpp/public-cpp.md).

1. Wybierz **Cardgame.cpp** kartę w górnej części okienka edycji, aby otworzyć do edycji.

1. Usuń całą zawartość pliku i zamień ją przez ten kod:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->
   ```cpp
   #include "stdafx.h"
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
   > Podczas wprowadzania kodu można użyć funkcji autouzupełniania. Na przykład, jeśli ten kod za pomocą klawiatury, możesz wprowadzić *pl* lub *tot* , a następnie naciśnij klawisze Ctrl + spacja. Wprowadza automatycznego uzupełniania `players` lub `totalParticipants` dla Ciebie.

## <a name="add-test-code-to-your-main-function"></a>Dodaj kod testu do funkcji main

Dodawanie kodu do aplikacji sprawdzający nowych funkcji.

### <a name="to-add-test-code-to-the-project"></a>Aby dodać kod testu do projektu

1. W oknie edytora Game.cpp Zastąp istniejący kod, to:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->
   ```cpp
   // Game.cpp : Defines the entry point for the console application.
   //

   #include "stdafx.h"
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
Ten kod dodaje funkcję testu `PlayGames`, aby kod źródłowy i wywołania w `main`. 

## <a name="build-and-run-your-app-project"></a>Tworzenie i uruchamianie projektu aplikacji

Następnie należy skompilować projekt i uruchomić aplikację.

### <a name="to-build-and-run-the-project"></a>Aby skompilować i uruchomić projekt

1. Na pasku menu wybierz **kompilacji > Kompiluj rozwiązanie**.

   Dane wyjściowe kompilacji jest wyświetlana w **dane wyjściowe** okna. Jeśli kompilacja zakończy się pomyślnie, dane wyjściowe powinny przypominać:

   ```Output
   1>------ Build started: Project: Game, Configuration: Debug Win32 ------
   1>  stdafx.cpp
   1>  Game.cpp
   1>  Cardgame.cpp
   1>  Generating Code...
   1>  Game.vcxproj -> C:\Users\username\Source\Repos\Game\Debug\Game.exe
   ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
   ```

   **Dane wyjściowe** okna mogą być prezentowane z różnych kroków, w zależności od konfiguracji kompilacji, ale jeśli kompilacja projektu zakończy się pomyślnie, ostatni wiersz powinien wyglądać wyświetlanego.

   Jeżeli kompilacji nie powiodła się, porównać Twój kod do kodu, który jest wyświetlany w poprzednich krokach.

1. Aby uruchomić projekt, na pasku menu, wybierz **Debuguj > Uruchom bez debugowania**. Okno konsoli powinna zostać wyświetlona, a dane wyjściowe powinny wyglądać następująco:

   ```Output
   4 players have started a new game.  There are now 4 players in total.
   8 players have started a new game.  There are now 12 players in total.
   1 players have started a new game.  There are now 13 players in total.
   5 players have started a new game.  There are now 18 players in total.
   ```
Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

Gratulacje, pomyślnie skompilowany projekt aplikacji i rozwiązań. Nadal przewodnika, aby dowiedzieć się więcej na temat sposobu tworzenia projektów kodu C++ w programie Visual Studio.

## <a name="next-steps"></a>Następne kroki

**Poprzedni:** [dla projektowania aplikacji C++ za pomocą programu Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
**Następnie:** [wskazówki: Tworzenie projektu (C++)](../ide/walkthrough-building-a-project-cpp.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)  
[Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)