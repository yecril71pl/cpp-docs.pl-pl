---
title: "Wskazówki: Praca z projektami i rozwiązaniami (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
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
ms.openlocfilehash: 6b30cd4885d5fdd65831c8044a088fcb87b52ae3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Wskazówki: praca z projektami i rozwiązaniami (C++)
Oto jak utworzyć projekt C++ w Visual Studio, dodać kod, a następnie skompilować i uruchomić projekt. Projektem w tym instruktażu jest program, który śledzi, ilu graczy gra w różne gry karciane.  
  
 W programie Visual Studio pracy jest zorganizowana w projekty i rozwiązania. Rozwiązanie może zawierać więcej niż jeden projekt — na przykład bibliotekę DLL i plik wykonywalny, który odwołuje się do tej biblioteki DLL. Aby uzyskać więcej informacji, zobacz [rozwiązań i projektów](/visualstudio/ide/solutions-and-projects-in-visual-studio).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   Aby ukończyć ten instruktaż, musisz rozumieć podstawy języka C++.  
  
## <a name="creating-a-project"></a>Tworzenie projektu  
 Aby utworzyć projekt, należy najpierw wybrać szablon typu projektu. Dla każdego typu projektu programu Visual Studio Ustawia ustawienia kompilatora i — w zależności od typu — generuje kod początkowy, który można zmodyfikować później.  
  
#### <a name="to-create-a-project"></a>Aby utworzyć projekt  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  W lewym okienku **nowy projekt** okna dialogowego rozwiń **zainstalowane szablony** węzła, rozwiń węzeł **Visual C++** węzeł, a następnie wybierz **Win32**.  
  
3.  Na liście szablonów zainstalowanych w środkowym okienku wybierz **aplikacji konsoli Win32**.  
  
4.  Wprowadź nazwę projektu w **nazwa** pole. Na przykład wprowadź **gry**.  
  
     Możesz zaakceptować domyślną lokalizację w **lokalizacji** listy rozwijanej, wprowadź inną lokalizację lub wybierz **Przeglądaj** przycisk, aby przejść do katalogu, w którym chcesz zapisać projekt.  
  
     Podczas tworzenia projektu Visual Studio umieszcza projektu w rozwiązaniu. Domyślnie rozwiązanie ma taką samą nazwę jak projekt. Można zmienić nazwę w **Nazwa rozwiązania** polu, ale w tym przykładzie pozostaw nazwę domyślną.  
  
     Wybierz **OK** przycisk, aby uruchomić **Kreator aplikacji Win32**.  
  
5.  Na **omówienie** strony **Kreator aplikacji Win32**, wybierz **dalej** przycisku.  
  
6.  Na **ustawienia aplikacji** w obszarze **typu aplikacji**, wybierz pozycję **aplikacji konsoli**. W obszarze **dodatkowe opcje**, wyczyść **Prekompilowanego nagłówka** ustawienie, a następnie wybierz **pusty projekt** ustawienie. Wybierz **Zakończ** przycisk, aby utworzyć projekt.  
  
     Istnieje już projekt, ale nie zawiera on jeszcze plików kodu źródłowego.  
  
## <a name="organizing-projects-and-files-in-a-solution"></a>Organizowanie projektów i plików w rozwiązaniu  
 Można użyć **Eksploratora rozwiązań** do organizowania i zarządzania nimi projektów, plików i innych zasobów w rozwiązaniu.  
  
 W tej części instruktażu pokazano, jak dodać klasę do projektu. Po dodaniu klasy Visual Studio dodaje odpowiednich .h i .cpp plików. Następnie dodawany jest nowy plik kodu źródłowego dla głównego programu, który testuje klasę.  
  
#### <a name="to-add-a-class-to-a-project"></a>Aby dodać klasę do projektu  
  
1.  Jeśli **Eksploratora rozwiązań** jest niewidoczny, na pasku menu wybierz **widoku**, **Eksploratora rozwiązań**.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów **pliki nagłówkowe** folder, a następnie wybierz **Dodaj**, **klasy**.  
  
     W lewym okienku **Dodaj klasę** okna dialogowego rozwiń **Visual C++** a następnie wybierz węzeł **C++**, a następnie na liście zainstalowanych szablonów w środkowym okienku wybierz  **Klasy C++**. Wybierz **Dodaj** przycisku.  
  
3.  W **ogólnego Kreator klas C++**, wprowadź **Cardgame** w **Nazwa klasy** pole. Nie należy modyfikować domyślnych nazw plików i ustawień. Wybierz **Zakończ** przycisku.  
  
4.  Plik Cardgame.h zostanie otwarty w edytorze. Należy wprowadzić następujące zmiany:  
  
    -   Dodaj dwa prywatne elementy członkowskie danych po nawiasie klamrowym otwierającym definicję klasy.  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)]  
  
    -   Zmodyfikuj domyślnego konstruktora wygenerowanego przez Visual Studio. Po `public:` specyfikator dostępu, znajdź wiersz, który wygląda następująco:  
  
         `Cardgame(void);`  
  
         Zmodyfikować, aby mieć jeden parametr typu `int`nazwanego **odtwarzacze**.  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]  
  
    -   Po destruktor domyślne dodać deklaracja wbudowanego dla funkcji członkowskiej int statycznej o nazwie **GetParticipants** nie przyjmuje żadnych parametrów i zwraca **totalParticipants** wartości.  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]  
  
5.  Plik Cardgame.h powinien po zmianach przypominać:  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]  
  
     Wiersz `#pragma once` informuje kompilator, aby dołączyć plik tylko jeden raz. Aby uzyskać więcej informacji, zobacz [po](../preprocessor/once.md).  
  
     Aby uzyskać informacje o innych słów kluczowych języka C++ w tym pliku nagłówka, zobacz [klasy](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [statycznych](../cpp/storage-classes-cpp.md), i [publicznego](../cpp/public-cpp.md).  
  
6.  Wybierz **Cardgame.cpp** w okienku edycji, aby go otworzyć do edycji.  
  
7.  Usuń całą zawartość pliku i zamień ją przez ten kod:  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]  
  
    > [!NOTE]
    >  Podczas wprowadzania kodu można użyć funkcji autouzupełniania. Na przykład, jeśli zostały wprowadzenie tego kodu, można wprowadzić **pl** lub **tot** i naciśnij klawisze Ctrl + spacja, aby zakończeniu automatycznego uzupełniania wprowadzania `players` lub `totalParticipants` dla Ciebie.  
  
     Aby uzyskać informacje o `#include`, zobacz [#include — dyrektywa (C/C++)](../preprocessor/hash-include-directive-c-cpp.md).  
  
## <a name="adding-a-source-file"></a>Dodawanie pliku źródłowego  
 Dodaj teraz plik kodu źródłowego dla głównego programu, który testuje klasę.  
  
#### <a name="to-add-a-new-source-file"></a>Aby dodać nowy plik źródłowy  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **pliki źródłowe** folder, a następnie wybierz **Dodaj**, **nowy element**.  
  
     W **Dodaj nowy element** okno dialogowe, w lewym okienku rozwiń **zainstalowana** węzła, rozwiń węzeł **Visual C++** węzeł, a następnie wybierz **kod**. W środkowym okienku wybierz **plik C++ (.cpp)**.  
  
2.  Wprowadź **TestGames.cpp** w **nazwa** polu, a następnie wybierz pozycję **Dodaj** przycisku.  
  
3.  W oknie edycji projektu TestGames.cpp wprowadź następujący kod.  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]  
  
## <a name="building-and-running-a-project"></a>Kompilowanie i uruchamianie projektu  
 Skompiluj teraz projekt i uruchom aplikację.  
  
#### <a name="to-build-and-run-the-project"></a>Aby skompilować i uruchomić projekt  
  
1.  Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
    > [!NOTE]
    >  Jeśli używasz wersji Express edition, które nie są wyświetlane **kompilacji** menu na pasku menu wybierz **narzędzia**, **ustawienia**, **ustawienia ekspert**ją włączyć.  
  
     Dane wyjściowe kompilacji jest wyświetlana w **dane wyjściowe** okna. Jeśli kompilacja zakończy się pomyślnie, dane wyjściowe powinny przypominać:  
  
    ```Output  
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------  
    1>  TestGames.cpp  
    1>  Cardgame.cpp  
    1>  Generating Code...  
    1>  Game.vcxproj -> c:\users\username\documents\visual studio\Projects\Game\Debug\Game.exe  
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========  
  
    ```  
  
     **Dane wyjściowe** okna mogą być prezentowane z różnych kroków, w zależności od wersji i konfigurację kompilacji, ale jeśli kompilacja projektu zakończy się pomyślnie, ostatni wiersz powinien wyglądać wyświetlanego.  
  
     Jeśli kompilacja się nie powiedzie, porównaj swój kod z kodem, który znajduje się w poprzednich krokach.  
  
2.  Aby uruchomić projekt, na pasku menu, wybierz **debugowania**, **uruchomić bez debugowania**. Wynik powinien przypominać poniższe:  
  
    ```Output  
    4 players have started a new game.  There are now 4 players in total.  
    8 players have started a new game.  There are now 12 players in total.  
    1 players have started a new game.  There are now 13 players in total.  
    5 players have started a new game.  There are now 18 players in total.  
    ```  
  
## <a name="next-steps"></a>Następne kroki  
 **Poprzedni:** [dla projektowania aplikacji C++ za pomocą programu Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). **Następnie:**[wskazówki: Tworzenie projektu (C++)](../ide/walkthrough-building-a-project-cpp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)