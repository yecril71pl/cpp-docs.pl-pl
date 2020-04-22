---
title: Kompilowanie i uruchamianie projektu aplikacji konsoli w języku C++
description: Tworzenie i uruchamianie aplikacji konsoli Hello World w języku Visual C++
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: d1e92e598b370312730a7c4e208b935a264010bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749243"
---
# <a name="build-and-run-a-c-console-app-project"></a>Kompilowanie i uruchamianie projektu aplikacji konsoli w języku C++

Utworzono projekt aplikacji konsoli Języka C++ i wprowadzono kod. Teraz można go skompilować i uruchomić w programie Visual Studio. Następnie uruchom go jako aplikację autonomiczną z wiersza polecenia.

## <a name="prerequisites"></a>Wymagania wstępne

- Mieć Visual Studio z pulpitu rozwoju z c++ obciążenia zainstalowanego i uruchomionego na komputerze. Jeśli nie jest jeszcze zainstalowany, wykonaj kroki opisane w [programie Zainstaluj obsługę języka C++ w programie Visual Studio](vscpp-step-0-installation.md).

- Stwórz "Cześć, Świat!" projektu i wprowadź jego kod źródłowy. Jeśli ten krok nie został jeszcze wykonany, wykonaj czynności opisane w programie [Utwórz projekt aplikacji konsoli C++.](vscpp-step-1-create.md)

Jeśli program Visual Studio wygląda następująco, możesz przystąpić do tworzenia i uruchamiania aplikacji:

   ![Gotowy do zbudowania nowego projektu](media/vscpp-ready-to-build.png "Gotowy do zbudowania nowego projektu")

## <a name="build-and-run-your-code-in-visual-studio"></a>Tworzenie i uruchamianie kodu w programie Visual Studio

1. Aby utworzyć projekt, wybierz polecenie **Buduj rozwiązanie** z menu **Kompilacja.** Okno **Dane wyjściowe** pokazuje wyniki procesu kompilacji.

   ![Kompilowanie projektu](media/vscpp-build-solution.gif "Kompilowanie projektu")

1. Aby uruchomić kod, na pasku menu wybierz polecenie **Debug ,** **Start bez debugowania**.

   ![Rozpoczęcie projektu](media/vscpp-start-without-debugging.gif "Rozpoczęcie projektu")

   Zostanie otwarte okno konsoli, a następnie uruchomi aplikację. Po uruchomieniu aplikacji konsoli w programie Visual Studio uruchamia kod, a następnie drukuje "Naciśnij dowolny klawisz, aby kontynuować . . ." aby dać ci szansę zobaczenia wyjścia.

Gratulacje! Stworzyłeś swój pierwszy "Cześć, świat!" aplikacji konsoli w programie Visual Studio! Naciśnij klawisz, aby odrzucić okno konsoli i powrócić do programu Visual Studio.

[Wpadłem na problem.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Uruchamianie kodu w oknie polecenia

Zwykle można uruchomić aplikacje konsoli w wierszu polecenia, a nie w programie Visual Studio. Gdy aplikacja jest szesnasty przez program Visual Studio, można uruchomić go z dowolnego okna polecenia. Poniżej opisano, jak znaleźć i uruchomić nową aplikację w oknie wiersza polecenia.

1. W **Eksploratorze rozwiązań**wybierz rozwiązanie HelloWorld (nie projekt HelloWorld) i kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe. Wybierz **pozycję Otwórz folder w Eksploratorze plików,** aby otworzyć okno **Eksploratora plików** w folderze rozwiązania HelloWorld.

1. W oknie **Eksplorator plików** otwórz folder Debug. Ten folder zawiera aplikację *HelloWorld.exe*i kilka innych plików debugowania. Przytrzymaj klawisz **Shift** i kliknij prawym przyciskiem myszy *HelloWorld.exe,* aby otworzyć menu kontekstowe. Wybierz **pozycję Kopiuj jako ścieżkę,** aby skopiować ścieżkę do aplikacji do schowka.

1. Aby otworzyć okno wiersza polecenia, naciśnij **klawisze Windows+R,** aby otworzyć okno dialogowe **Uruchom.** Wprowadź *plik cmd.exe* w oknie tekstowym **Otwórz,** a następnie wybierz przycisk **OK,** aby uruchomić okno wiersza polecenia.

1. W oknie wiersza polecenia kliknij prawym przyciskiem myszy, aby wkleić ścieżkę do aplikacji do wiersza polecenia. Naciśnij klawisz Enter, aby uruchomić aplikację.

   ![Uruchamianie aplikacji w wierszu polecenia](media/vscpp-run-in-cmd.gif "Uruchamianie aplikacji w wierszu polecenia")

Gratulacje, masz wbudowane i uruchomić aplikację konsoli w programie Visual Studio!

[Wpadłem na problem.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Następne kroki

Po zbudowaniu i uruchomieniu tej prostej aplikacji możesz przygotować się do bardziej złożonych projektów. Aby uzyskać więcej informacji, zobacz [Korzystanie z środowiska IDE programu Visual Studio dla środowiska dewelopera pulpitu w języku C++.](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md) Ma bardziej szczegółowe wskazówki, które eksplorują możliwości programu Microsoft C++ w programie Visual Studio.

## <a name="troubleshooting-guide"></a>Przewodnik rozwiązywania problemów

Przyjdź tutaj, aby uzyskać rozwiązania typowych problemów podczas tworzenia pierwszego projektu C++.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Tworzenie i uruchamianie kodu w programie Visual Studio: problemy

Jeśli czerwone squiggles pojawiają się pod czymkolwiek w edytorze kodu źródłowego, kompilacja może mieć błędy lub ostrzeżenia. Sprawdź, czy kod pasuje do przykładu pisowni, znaków interpunkcyjnych i sprawy.

[Przejdź wstecz.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Uruchamianie kodu w oknie polecenia: problemy

Jeśli ścieżka pokazana w Eksploratorze plików kończy się w * \\HelloWorld\\HelloWorld,* otwarto *projekt* HelloWorld zamiast *rozwiązania*HelloWorld . Będziesz mylić przez folder debugowania, który nie zawiera aplikacji. Przejdź do poziomu w Eksploratorze plików, aby przejść do folderu rozwiązania, pierwszego *HelloWorld* w ścieżce. Ten folder zawiera również folder debugowania, a znajdziesz tam aplikację.

Można również przejść do folderu debugowania rozwiązania w wierszu polecenia, aby uruchomić aplikację. Aplikacja nie będzie uruchamiana z innych katalogów bez określania ścieżki do aplikacji. Można jednak skopiować aplikację do innego katalogu i uruchomić ją stamtąd. Istnieje również możliwość skopiowania go do katalogu określonego przez zmienną środowiskową PATH, a następnie uruchomić go z dowolnego miejsca.

Jeśli w menu skrótów nie widzisz **opcji Kopiuj jako ścieżka,** odrzuć menu, a następnie przytrzymaj klawisz **Shift** podczas ponownego otwierania. To polecenie jest tylko dla wygody. Ścieżkę do folderu można również skopiować z paska wyszukiwania Eksploratora plików i wkleić ją do okna dialogowego **Uruchom,** a następnie wprowadzić nazwę pliku wykonywalnego na końcu. To tylko trochę więcej pisania, ale ma ten sam wynik.

[Przejdź wstecz.](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
