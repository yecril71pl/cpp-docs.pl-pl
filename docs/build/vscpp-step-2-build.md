---
title: Kompilowanie i uruchamianie projektu aplikacji konsoli w języku C++
description: Kompilowanie i uruchamianie aplikacji konsolowej Hello world w programie Visual C++
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

Utworzono projekt aplikacji konsolowej w języku C++ i wprowadzono kod. Teraz można kompilować i uruchamiać je w programie Visual Studio. Następnie uruchom go jako autonomiczną aplikację z poziomu wiersza polecenia.

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio z programowaniem dla komputerów stacjonarnych z zainstalowanym i uruchomionym obciążeniem języka C++. Jeśli nie jest jeszcze zainstalowana, wykonaj kroki opisane w sekcji [Instalowanie obsługi języka C++ w programie Visual Studio](vscpp-step-0-installation.md).

- Tworzenie "Hello, World!" projekt i wprowadź jego kod źródłowy. Jeśli jeszcze tego nie zrobiono, wykonaj kroki opisane w sekcji [Tworzenie projektu aplikacji konsolowej w języku C++](vscpp-step-1-create.md).

Jeśli program Visual Studio wygląda tak, wszystko jest gotowe do skompilowania i uruchomienia aplikacji:

   ![Gotowe do skompilowania nowego projektu](media/vscpp-ready-to-build.png "Gotowe do skompilowania nowego projektu")

## <a name="build-and-run-your-code-in-visual-studio"></a>Kompilowanie i uruchamianie kodu w programie Visual Studio

1. Aby skompilować projekt, wybierz opcję **Kompiluj rozwiązanie** z menu **kompilacja** . W oknie **dane wyjściowe** są wyświetlane wyniki procesu kompilacji.

   ![Kompilowanie projektu](media/vscpp-build-solution.gif "Kompilowanie projektu")

1. Aby uruchomić kod, na pasku menu wybierz **Debuguj**, **Uruchom bez debugowania**.

   ![Rozpoczęcie projektu](media/vscpp-start-without-debugging.gif "Rozpoczęcie projektu")

   Zostanie otwarte okno konsoli, a następnie zostanie uruchomiona aplikacja. Po uruchomieniu aplikacji konsolowej w programie Visual Studio program uruchamia swój kod, a następnie drukuje "naciśnij dowolny klawisz, aby kontynuować. . ." , aby dać Ci szansę zobaczyć dane wyjściowe.

Gratulacje! Utworzono pierwszy "Hello, World!" Aplikacja konsolowa w programie Visual Studio! Naciśnij klawisz, aby odrzucić okno konsoli i powrócić do programu Visual Studio.

[Wystąpił problem.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Uruchamianie kodu w oknie polecenia

Zwykle aplikacje konsolowe można uruchamiać w wierszu polecenia, a nie w programie Visual Studio. Po skompilowaniu aplikacji przez program Visual Studio można uruchomić ją z dowolnego okna poleceń. Oto jak znaleźć i uruchomić nową aplikację w oknie wiersza polecenia.

1. W **Eksplorator rozwiązań**wybierz rozwiązanie HelloWorld (nie projekt HelloWorld), a następnie kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe. Wybierz pozycję **Otwórz folder w Eksploratorze plików** , aby otworzyć okno **Eksploratora plików** w folderze rozwiązania HelloWorld.

1. W oknie **Eksplorator plików** Otwórz folder debugowanie. Ten folder zawiera aplikację, *HelloWorld. exe*i kilka innych plików debugowania. Naciśnij i przytrzymaj klawisz **SHIFT** , a następnie kliknij prawym przyciskiem myszy *plik HelloWorld. exe* , aby otworzyć menu kontekstowe. Wybierz **Kopiuj jako ścieżkę** , aby skopiować ścieżkę do aplikacji do Schowka.

1. Aby otworzyć okno wiersza polecenia, naciśnij klawisze **Windows + R** , aby otworzyć okno dialogowe **uruchamiania** . Wprowadź *cmd. exe* w **otwartym** polu tekstowym, a następnie wybierz **przycisk OK** , aby uruchomić okno wiersza polecenia.

1. W oknie wiersza polecenia kliknij prawym przyciskiem myszy, aby wkleić ścieżkę do aplikacji w wierszu polecenia. Naciśnij klawisz ENTER, aby uruchomić aplikację.

   ![Uruchamianie aplikacji przy użyciu wiersza polecenia](media/vscpp-run-in-cmd.gif "Uruchamianie aplikacji przy użyciu wiersza polecenia")

Gratulacje, udało Ci się utworzyć i uruchomić aplikację konsolową w programie Visual Studio!

[Wystąpił problem.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Następne kroki

Po skompilowaniu i uruchomieniu tej prostej aplikacji wszystko jest gotowe do bardziej złożonych projektów. Aby uzyskać więcej informacji, zobacz [Korzystanie z programu Visual Studio IDE do tworzenia aplikacji klasycznych](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)w języku C++. Zawiera bardziej szczegółowe wskazówki dotyczące możliwości platformy Microsoft C++ w programie Visual Studio.

## <a name="troubleshooting-guide"></a>Przewodnik rozwiązywania problemów

Tutaj można znaleźć rozwiązania typowych problemów podczas tworzenia pierwszego projektu w języku C++.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Kompilowanie i uruchamianie kodu w programie Visual Studio: problemy

Jeśli w edytorze kodu źródłowego pojawiają się czerwone zygzaki, kompilacja może zawierać błędy lub ostrzeżenia. Sprawdź, czy Twój kod pasuje do przykładu w pisowni, interpunkcji i wielkości liter.

[Przejdź wstecz.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Uruchamianie kodu w oknie poleceń: problemy

Jeśli ścieżka pokazywana w Eksploratorze plików zostanie zakończona * \\w\\HelloWorld HelloWorld*, zamiast *rozwiązania*HelloWorld został otwarty *projekt* HelloWorld. Pomylić Cię z folderem debugowania, który nie zawiera Twojej aplikacji. Przejdź do poziomu Eksploratora plików, aby przejść do folderu rozwiązania, pierwszy *HelloWorld* w ścieżce. Ten folder zawiera również folder debugowania, w którym znajdziesz swoją aplikację.

Możesz również przejść do folderu debugowania rozwiązania w wierszu polecenia, aby uruchomić aplikację. Aplikacja nie będzie działać z innych katalogów bez określania ścieżki do aplikacji. Można jednak skopiować aplikację do innego katalogu i uruchomić ją stamtąd. Istnieje również możliwość skopiowania jej do katalogu określonego przez zmienną środowiskową PATH, a następnie uruchomić ją z dowolnego miejsca.

Jeśli nie widzisz **ścieżki Copy As** w menu skrótów, Odrzuć menu, a następnie przytrzymaj klawisz **SHIFT** podczas jego otwierania. To polecenie jest przeznaczone tylko dla wygody. Możesz również skopiować ścieżkę do folderu z paska wyszukiwania Eksploratora plików i wkleić je do okna dialogowego **uruchamiania** , a następnie wprowadzić nazwę pliku wykonywalnego na końcu. Jest to tylko nieco więcej tekstu, ale ma ten sam wynik.

[Przejdź wstecz.](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
