---
title: Kompilowanie i uruchamianie projektu aplikacji konsoli w języku C++ | Dokumentacja firmy Microsoft
description: Kompilowanie i uruchamianie aplikacji konsolowej Hello World w języku Visual C++
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: tutorial
ms.technology:
- cpp-tools
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9c32f6811a18fae00cb2943a9ca97a89cf159a1
ms.sourcegitcommit: 92c568e9466ffd7346a4120c478c9bdea61c8756
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2018
ms.locfileid: "47029596"
---
# <a name="build-and-run-a-c-console-app-project"></a>Kompilowanie i uruchamianie projektu aplikacji konsoli w języku C++

Po utworzeniu projektu aplikacji konsoli w języku C++ i wprowadzić swój kod, kompilacji i uruchom go w programie Visual Studio, a następnie uruchom go jako autonomiczną aplikację z poziomu wiersza polecenia.

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio za pomocą programowanie aplikacji klasycznych, z obciążeniem C++ zainstalowany i uruchomiony na komputerze. Jeśli nie jest jeszcze zainstalowany, wykonaj kroki opisane w [Instalowanie obsługi języka C++ w programie Visual Studio](../build/vscpp-step-0-installation.md).

- Tworzenie "Hello, World!" Projekt, a następnie wprowadź jego kod źródłowy. Jeśli nie masz jeszcze ustanowionego jeszcze, wykonaj kroki opisane w [Tworzenie projektu aplikacji konsoli w języku C++](../build/vscpp-step-1-create.md).

Jeśli program Visual Studio wygląda tak, możesz przystąpić do kompilowania i uruchamiania aplikacji:

   ![Gotowe do kompilowania nowego projektu](../build/media/vscpp-ready-to-build.png "gotowe do kompilowania nowego projektu")

## <a name="build-and-run-your-code-in-visual-studio"></a>Kompilowanie i uruchamianie kodu w programie Visual Studio

1. Aby skompilować projekt, wybierz opcję **Kompiluj rozwiązanie** z **kompilacji** menu. **Dane wyjściowe** okno przedstawia wyniki procesu kompilacji.

   ![Skompiluj projekt](../build/media/vscpp-build-solution.gif "kompilacji projektu")

1. Aby uruchomić kod, na pasku menu, wybierz **debugowania**, **Uruchom bez debugowania**.

   ![Rozpocznij projekt](../build/media/vscpp-start-without-debugging.gif "Rozpocznij projekt")

   Okno konsoli zostanie otwarty, a następnie uruchamia aplikację. Po uruchomieniu aplikacji konsoli w programie Visual Studio działa kod, a następnie drukuje "naciśnij dowolny klawisz, aby kontynuować. . ." daje szansę, aby wyświetlić dane wyjściowe.

Gratulacje! Utworzono pierwszej "Hello, world!" Aplikacja konsoli w programie Visual Studio! Naciśnij dowolny klawisz, aby zamknąć okno konsoli i powrócić do programu Visual Studio.

[Wystąpił problem.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Uruchamianie kodu w oknie polecenia

Normalnie możesz uruchomić aplikacje konsoli w wierszu polecenia, a nie w programie Visual Studio. Po skompilowaniu aplikacji przez program Visual Studio można uruchomić go z dowolnego okna polecenia. Poniżej przedstawiono sposób znaleźć i uruchomienie nowej aplikacji w oknie wiersza polecenia.

1. W **Eksploratora rozwiązań**kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe i wybierz rozwiązanie HelloWorld. Wybierz **Otwórz Folder w Eksploratorze plików** otworzyć **Eksploratora plików** okna w folderze rozwiązania HelloWorld.

1. W **Eksploratora plików** okna, otwórz folder debugowania. Zawiera aplikację, HelloWorld.exe i kilka innych plików debugowania. Wybierz HelloWorld.exe, naciśnij i przytrzymaj klawisz Shift i kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe. Wybierz **Kopiuj jako ścieżka** skopiować ścieżki do aplikacji do Schowka.

1. Aby otworzyć okno wiersza polecenia, naciśnij klawisze Windows-R, aby otworzyć **Uruchom** okna dialogowego. Wprowadź *cmd.exe* w **Otwórz** pola tekstowego, wybierz **OK** Aby uruchomić okno wiersza polecenia.

1. W oknie wiersza polecenia kliknij prawym przyciskiem myszy w celu Wklej ścieżkę do aplikacji w wierszu polecenia. Naciśnij klawisz Enter, aby uruchomić aplikację.

   ![Uruchamianie aplikacji w wierszu polecenia](../build/media/vscpp-run-in-cmd.gif "uruchomienia aplikacji w wierszu polecenia")

Gratulacje, udało skompilowane i uruchomisz aplikację konsoli w programie Visual Studio!

[Wystąpił problem.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Następne kroki

Po zostały skompilowane i uruchomić tej prostej aplikacji, możesz przystąpić do bardziej złożonych projektów. Zobacz [przy użyciu programu Visual Studio IDE dla programowanie aplikacji klasycznych w języku C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md) bardziej szczegółowe wskazówki, zapoznaj się z możliwościami programu Visual C++ w programie Visual Studio.

## <a name="troubleshooting-guide"></a>Przewodnik rozwiązywania problemów

Tu rozwiązania typowych problemów podczas tworzenia pierwszego projektu C++.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Kompilowanie i uruchamianie kodu w problemy dotyczące programu Visual Studio

Czerwone symbole są wyświetlane w obszarze dowolne elementy w edytorze kodu źródłowego, kompilacji może być błędy lub ostrzeżenia. Sprawdź, czy kod jest zgodna w przykładzie w pisowni, znaki interpunkcyjne i wielkości liter.

[Przejdź wstecz.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Uruchamianie kodu w oknie polecenia problemów

Możesz także przejść do folderu rozwiązania debugowania w wierszu polecenia, aby uruchomić aplikację. Nie można uruchomić aplikacji z innych katalogów, bez określania ścieżki do aplikacji. Można jednak kopiowanie aplikację do innego katalogu i uruchom go z tego miejsca.

Jeśli nie widzisz **Kopiuj jako ścieżka** w menu skrótów zamknąć menu, a następnie przytrzymaj naciśnięty klawisz Shift, gdy otworzysz go ponownie. Jest to po prostu dla wygody. Można również skopiować ścieżkę do folderu z paska wyszukiwania Eksploratora plików i wklej go do **Uruchom** okno dialogowe, a następnie wprowadź nazwę plik wykonywalny na końcu. Jest nieco więcej wpisywania, ale ma ona ten sam wynik.

[Przejdź wstecz.](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
