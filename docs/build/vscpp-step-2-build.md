---
title: Skompilować i uruchomić projekt aplikacji konsoli języka C++ | Dokumentacja firmy Microsoft
description: Tworzenie i uruchamianie aplikacji konsoli Hello World w programie Visual C++
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: tutorial
ms.technology:
- devlang-C++
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa63175e086fcb22552d0b7fd027b380d9766739
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="build-and-run-a-c-console-app-project"></a>Skompilować i uruchomić projekt aplikacji konsoli języka C++

Po utworzeniu projekt aplikacji konsoli języka C++ i wprowadzić swój kod, kompilacji i uruchom go w programie Visual Studio, a następnie uruchom go jako autonomiczną aplikację z poziomu wiersza polecenia.

## <a name="prerequisites"></a>Wymagania wstępne

- Masz program Visual Studio z tworzenia klasycznych aplikacji z C++ obciążenia zainstalowana i uruchomiona na komputerze. Jeśli nie jest jeszcze zainstalowany, postępuj zgodnie z instrukcjami [zainstalować obsługi języka C++ w programie Visual Studio](../build/vscpp-step-0-installation.md).

- Tworzenie "Hello, World!" Projekt, a następnie wprowadź jego kod źródłowy. Jeśli to nie zostało to jeszcze zrobione jeszcze, postępuj zgodnie z instrukcjami [Utwórz projekt aplikacji konsoli C++](../build/vscpp-step-1-create.md).

Jeśli program Visual Studio wygląda tak, możesz przystąpić do tworzenia i uruchamiania aplikacji:

   ![Gotowy do utworzenia nowego projektu](../build/media/vscpp-ready-to-build.png "rozpocząć tworzenie nowego projektu")

## <a name="build-and-run-your-code-in-visual-studio"></a>Tworzenie i uruchamianie kodu w programie Visual Studio

1. Aby utworzyć projekt, wybierz **Kompiluj rozwiązanie** z **kompilacji** menu. **Dane wyjściowe** okna pokazuje wyniki procesu kompilacji.

   ![Skompiluj projekt](../build/media/vscpp-build-solution.gif "kompilacji projektu")

1. Aby uruchomić kod, na pasku menu, wybierz pozycję **debugowania**, **uruchomienie bez debugowania**.

   ![Uruchom projekt](../build/media/vscpp-start-without-debugging.gif "uruchamiania projektu")

    Okno konsoli zostanie otwarty, a następnie uruchomi aplikację. Po uruchomieniu aplikacji konsoli w programie Visual Studio działa kod, a następnie drukuje "naciśnij dowolny klawisz, aby kontynuować. . ." Aby zapewnić możliwość wyświetlone dane wyjściowe.

Gratulacje! Po utworzeniu pierwszego "Hello, world!" aplikacji konsoli w programie Visual Studio! Naciśnij dowolny klawisz, aby zamknąć okno konsoli i powrócić do programu Visual Studio.

[Czy wystąpił problem.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Uruchamianie kodu w oknie polecenia

Normalnie korzystać z aplikacji konsoli, w wierszu polecenia nie w programie Visual Studio. Po utworzeniu aplikacji przez program Visual Studio można go uruchomić w dowolnym oknie polecenia. Oto jak znaleźć i uruchomienie nowej aplikacji w oknie wiersza polecenia.

1. W **Eksploratora rozwiązań**, wybierz rozwiązanie HelloWorld i kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowego. Wybierz **Otwórz Folder w Eksploratorze plików** otworzyć **Eksploratora plików** okna w folderze rozwiązania HelloWorld.

1. W **Eksploratora plików** okna, otwórz folder debugowania. Zawiera aplikację, HelloWorld.exe i kilka innych plików debugowania. Wybierz HelloWorld.exe, naciśnij i przytrzymaj klawisz Shift, a następnie kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowego. Wybierz **Kopiuj jako ścieżka** skopiować ścieżki do aplikacji do Schowka.

1. Aby otworzyć okno wiersza polecenia, naciśnij klawisz systemu Windows-R, aby otworzyć **Uruchom** okna dialogowego. Wprowadź *cmd.exe* w **Otwórz** pola tekstowego, a następnie wybierz **OK** Aby uruchomić okno wiersza polecenia.

1. W oknie wiersza polecenia kliknij prawym przyciskiem myszy w celu Wklej ścieżka do aplikacji w wierszu polecenia. Naciśnij klawisz Enter, aby uruchomić aplikację.

   ![Uruchom aplikację w wierszu polecenia](../build/media/vscpp-run-in-cmd.gif "uruchamianie aplikacji w wierszu polecenia")

Gratulacje, został utworzony i uruchamianie aplikacji konsoli w programie Visual Studio!

[Czy wystąpił problem.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Następne kroki

Po wbudowane i uruchom to prosta aplikacja, możesz przystąpić do bardziej złożonych projektów. Zobacz [za pomocą środowiska IDE programu Visual Studio dla programowania w języku C++ pulpitu](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md) Aby uzyskać szczegółowe wskazówki, które Poznaj możliwości programu Visual C++ w programie Visual Studio.

## <a name="troubleshooting-guide"></a>Przewodnik rozwiązywania problemów

Pochodzić tutaj rozwiązania często występujących problemów podczas tworzenia pierwszego projektu C++.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Tworzenie i uruchamianie kodu w problemy dotyczące programu Visual Studio

Jeśli red zygzaki są wyświetlane w obszarze wszystko w edytorze kodu źródłowego, kompilacja może być błędy lub ostrzeżenia. Sprawdź, czy kod zgodny przykład pisowni, znaki interpunkcyjne i case.

[Przejdź wstecz.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Uruchamianie kodu w oknie polecenia problemów

Można także przechodzić do folderu rozwiązania debugowania w wierszu polecenia do uruchomienia aplikacji. Nie można uruchomić aplikacji z innych katalogów, bez określenia ścieżki do aplikacji. Można jednak skopiować do innego katalogu aplikacji i uruchomić go z.

Jeśli nie widzisz **Kopiuj jako ścieżka** w menu skrótów zamknąć menu, a następnie naciśnij i przytrzymaj klawisz Shift podczas ponownego otwarcia. To jest tylko dla wygody. Można również skopiować ścieżkę do folderu na pasku wyszukiwania w Eksploratorze plików i wklej ją do **Uruchom** okna dialogowego, a następnie wprowadź nazwę pliku wykonywalnego na końcu. Jest niewiele więcej wpisywania, ale ma ten sam rezultat.

[Przejdź wstecz.](#run-your-code-in-a-command-window)


<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
