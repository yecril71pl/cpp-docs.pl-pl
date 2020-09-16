---
title: Tworzenie projektu aplikacji konsoli w języku C++
description: Utwórz aplikację konsolową Hello world przy użyciu języka Microsoft C++ w programie Visual Studio.
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 333bb6ce1f3ea0db6b07d70ddd60d4a4be337abd
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686512"
---
# <a name="create-a-c-console-app-project"></a>Tworzenie projektu aplikacji konsoli w języku C++

Typowym punktem wyjścia dla programisty języka C++ jest "Hello, World!" aplikacja uruchamiana w wierszu polecenia. To wszystko, co zostanie utworzone w programie Visual Studio w tym kroku.

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio z programowaniem dla komputerów stacjonarnych z zainstalowanym i uruchomionym obciążeniem języka C++. Jeśli nie jest jeszcze zainstalowana, zobacz [Install C++ Support in Visual Studio](vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Tworzenie projektu aplikacji

Program Visual Studio używa *projektów* do organizowania kodu aplikacji oraz *rozwiązań* do organizowania projektów. Projekt zawiera wszystkie opcje, konfiguracje i reguły używane do kompilowania aplikacji. Zarządza relacją między wszystkimi plikami projektu i wszystkimi plikami zewnętrznymi. Aby utworzyć aplikację, najpierw utworzysz nowy projekt i rozwiązanie.

::: moniker range=">=vs-2019"

1. W programie Visual Studio Otwórz menu **plik** i wybierz polecenie **Nowy > projekt** , aby otworzyć okno dialogowe **Tworzenie nowego projektu** . Wybierz szablon **aplikacji konsolowej** zawierający Tagi **C++**, **Windows**i **konsole** , a następnie wybierz przycisk **dalej**.

   ![Tworzenie nowego projektu](media/vs2019-choose-console-app.png "Otwórz okno dialogowe Tworzenie nowego projektu")

1. W oknie dialogowym **Konfigurowanie nowego projektu** wprowadź *HelloWorld* w polu Edycja **nazwy projektu** . Wybierz pozycję **Utwórz** , aby utworzyć projekt.

   ![Zrzut ekranu przedstawiający okno dialogowe Konfigurowanie nowego projektu z Hello world wpisanych w polu tekstowym Nazwa projektu.](media/vs2019-configure-new-project-hello-world.png "Nadaj nazwę i Utwórz nowy projekt")

   Program Visual Studio tworzy nowy projekt. Wszystko jest gotowe do dodawania i edytowania kodu źródłowego. Domyślnie szablon aplikacji konsoli wypełnia kod źródłowy przy użyciu aplikacji "Hello world":

   ![Hello world projekt w IDE](media/vs2019-hello-world-code.png "Hello world projekt w IDE")

   Gdy kod będzie wyglądać następująco w edytorze, możesz przejść do następnego kroku i skompilować aplikację.

[Wystąpił problem.](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=vs-2017"

1. W programie Visual Studio Otwórz menu **plik** i wybierz polecenie **Nowy > projekt** , aby otworzyć okno dialogowe **Nowy projekt** .

   ![Otwórz okno dialogowe Nowy projekt](media/vscpp-file-new-project.gif "Otwórz okno dialogowe Nowy projekt")

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **zainstalowane > Visual C++** , jeśli nie została jeszcze wybrana, a następnie wybierz szablon **pusty projekt** . W polu **Nazwa** wprowadź wartość *HelloWorld*. Wybierz **przycisk OK** , aby utworzyć projekt.

   ![Zrzut ekranu okna dialogowego Nowy projekt z zainstalowanym > Visual C plus plus zaznaczone i nazwane, opcja pustego projektu o nazwie out i Hellow World typeing w polu tekstowym Nazwa.](media/vscpp-concierge-project-name-callouts.png "Nadaj nazwę i Utwórz nowy projekt")

Program Visual Studio tworzy nowy, pusty projekt. Jest to gotowe do specjalizacji dla rodzaju aplikacji, którą chcesz utworzyć, i dodania plików kodu źródłowego. Zrobisz to w następnej kolejności.

[Wystąpił problem.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Tworzenie projektu jako aplikacji konsolowej

Program Visual Studio może tworzyć wszelkiego rodzaju aplikacje i składniki dla systemu Windows i innych platform. **Pusty szablon projektu** nie jest specyficzny dla rodzaju tworzonego przez niego aplikacji. *Aplikacja konsolowa* jest taka, która jest uruchamiana w konsoli lub w oknie wiersza polecenia. Aby go utworzyć, musisz powiedzieć programowi Visual Studio, aby skompilować aplikację w celu korzystania z podsystemu konsoli.

1. W programie Visual Studio Otwórz menu **projekt** i wybierz polecenie **Właściwości** , aby otworzyć okno dialogowe **strony właściwości HelloWorld** .

1. W oknie dialogowym **strony właściwości** wybierz pozycję **Właściwości konfiguracji > konsolidator > system**, a następnie wybierz pole edycji obok właściwości **podsystem** . W wyświetlonym menu rozwijanym wybierz pozycję **konsola (/SUBSYSTEM: Console)**. Wybierz **przycisk OK** , aby zapisać zmiany.

   ![Otwórz okno dialogowe strony właściwości](media/vscpp-properties-linker-subsystem.gif "Otwórz okno dialogowe strony właściwości")

Program Visual Studio wie teraz, aby skompilować projekt do uruchamiania w oknie konsoli. Następnie dodasz plik kodu źródłowego i wprowadzisz kod aplikacji.

[Wystąpił problem.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Dodaj plik kodu źródłowego

1. W **Eksplorator rozwiązań**wybierz projekt HelloWorld. Na pasku menu wybierz **projekt**, **Dodaj nowy element** , aby otworzyć okno dialogowe **Dodaj nowy element** .

1. W oknie dialogowym **Dodaj nowy element** wybierz opcję **Visual C++** w obszarze **zainstalowane** , jeśli nie została jeszcze wybrana. W środkowym okienku wybierz opcję **plik C++ (. cpp)**. Zmień **nazwę** na *HelloWorld. cpp*. Wybierz pozycję **Dodaj** , aby zamknąć okno dialogowe i utworzyć plik.

   ![Dodaj plik źródłowy dla HelloWorld. cpp](media/vscpp-add-new-item.gif "Dodaj plik źródłowy dla HelloWorld. cpp")

Program Visual Studio tworzy nowy, pusty plik kodu źródłowego i otwiera go w oknie edytora, gotowe do wprowadzenia kodu źródłowego.

[Wystąpił problem.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Dodawanie kodu do pliku źródłowego

1. Skopiuj ten kod do okna edytora HelloWorld. cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   Kod powinien wyglądać następująco w oknie edytora:

   ![Kod Hello world w edytorze](media/vscpp-hello-world-editor.png "Kod Hello world w edytorze")

Gdy kod będzie wyglądać następująco w edytorze, możesz przejść do następnego kroku i skompilować aplikację.

[Wystąpił problem.](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Kompilowanie i uruchamianie projektu C++](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Przewodnik rozwiązywania problemów

Tutaj można znaleźć rozwiązania typowych problemów podczas tworzenia pierwszego projektu w języku C++.

### <a name="create-your-app-project-issues"></a>Utwórz projekt aplikacji: problemy

::: moniker range="vs-2019"

W oknie dialogowym **Nowy projekt** powinien zostać wyświetlony szablon **aplikacji konsoli** z tagami **C++**, **Windows**i **konsolą** . Jeśli nie widzisz go, istnieją dwie możliwe przyczyny. Może zostać odfiltrowany z listy lub może nie być zainstalowany. Najpierw sprawdź listę rozwijaną filtrów w górnej części listy szablonów. Ustaw je na **C++**, **Windows**i **Console**. Powinien zostać wyświetlony szablon **aplikacji konsoli** języka C++; w przeciwnym razie **Programowanie aplikacji klasycznych w języku C++** nie jest zainstalowane.

Aby zainstalować **Programowanie aplikacji klasycznych w języku C++**, można uruchomić Instalatora bezpośrednio z okna dialogowego **Nowy projekt** . Wybierz link **Zainstaluj więcej narzędzi i funkcji** u dołu listy szablonów, aby uruchomić Instalatora. Jeśli okno dialogowe **Kontrola konta użytkownika** żąda uprawnień, wybierz pozycję **tak**. W instalatorze upewnij się, że jest zaznaczone pole **Programowanie aplikacji klasycznych w języku C++** . Następnie wybierz pozycję **Modyfikuj** , aby zaktualizować instalację programu Visual Studio.

Jeśli istnieje już inny projekt o takiej samej nazwie, wybierz inną nazwę dla projektu. Lub usuń istniejący projekt i spróbuj ponownie. Aby usunąć istniejący projekt, Usuń folder rozwiązania (folder zawierający plik *HelloWorld. sln* ) w Eksploratorze plików.

[Wróć](#create-your-app-project).

::: moniker-end

::: moniker range="vs-2017"

Jeśli w oknie dialogowym **Nowy projekt** nie jest wyświetlany wpis **Visual C++** w obszarze **zainstalowane**, kopia programu Visual Studio prawdopodobnie nie ma zainstalowanego **środowiska programistycznego z** zainstalowanym obciążeniem języka C++. Można uruchomić Instalatora bezpośrednio z okna dialogowego **Nowy projekt** . Wybierz łącze **otwórz Instalator programu Visual Studio** , aby ponownie uruchomić Instalatora. Jeśli okno dialogowe **Kontrola konta użytkownika** żąda uprawnień, wybierz pozycję **tak**. W razie potrzeby zaktualizuj Instalatora. W instalatorze upewnij się, że jest zaznaczone pole wyboru **Programowanie aplikacji klasycznych w języku C++** , a następnie wybierz **przycisk OK** , aby zaktualizować instalację programu Visual Studio.

::: moniker-end

::: moniker range="<=vs-2017"

Jeśli istnieje już inny projekt o takiej samej nazwie, wybierz inną nazwę dla projektu. Lub usuń istniejący projekt i spróbuj ponownie. Aby usunąć istniejący projekt, Usuń folder rozwiązania (folder zawierający plik *HelloWorld. sln* ) w Eksploratorze plików.

[Wróć](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>Tworzenie projektu aplikacji konsolowej: problemy

Jeśli nie widzisz **konsolidatora** na liście **Właściwości konfiguracji**, wybierz pozycję **Anuluj** , aby zamknąć okno dialogowe **strony właściwości** . Przed ponowną próbą upewnij się, że projekt **HelloWorld** został wybrany w **Eksplorator rozwiązań** . Nie wybieraj rozwiązania **HelloWorld** ani innego elementu w **Eksplorator rozwiązań**.

Formant menu rozwijanego nie pojawia się w polu właściwości **podsystemu** do momentu wybrania właściwości. Kliknij w polu edycji, aby go zaznaczyć. Możesz też nacisnąć klawisz **Tab** , aby przechodzić przez kontrolki okna dialogowego do momentu, gdy **podsystem** zostanie wyróżniony. Wybierz kontrolkę lista rozwijana lub naciśnij **kombinację klawiszy Alt + Strzałka w dół** , aby ją otworzyć.

[Wstecz](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Dodaj plik kodu źródłowego: problemy

Jeśli nadajesz plikowi kodu źródłowego inną nazwę, zgadzasz się. Jednak nie należy dodawać więcej niż jednego pliku, który zawiera ten sam kod do projektu.

Jeśli do projektu został dodany nieprawidłowy typ pliku, na przykład plik nagłówka, usuń go i spróbuj ponownie. Aby usunąć plik, wybierz go w **Eksplorator rozwiązań**. Następnie naciśnij klawisz **delete** .

[Wróć](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>Dodaj kod do pliku źródłowego: problemy

Jeśli przypadkowo zamknięto okno Edytor plików kodu źródłowego, można je łatwo otworzyć. Aby go otworzyć, kliknij dwukrotnie plik HelloWorld. cpp w oknie **Eksplorator rozwiązań** .

Jeśli w edytorze kodu źródłowego pojawia się czerwona zygzakowata, sprawdź, czy Twój kod pasuje do przykładu w pisowni, interpunkcji i przypadku. Przypadek jest istotny w kodzie C++.

[Wróć](#add-code-to-the-source-file).

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
