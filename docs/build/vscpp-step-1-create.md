---
title: Tworzenie projektu aplikacji konsoli w języku C++
description: Utwórz aplikację konsoli Hello World przy użyciu języka Microsoft C++ w programie Visual Studio.
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 07e88da9a8a3712e1d37e319c29fd25aebce8ea7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749311"
---
# <a name="create-a-c-console-app-project"></a>Tworzenie projektu aplikacji konsoli w języku C++

Zwykle punktem wyjścia dla programisty C++ jest "Cześć, świat!" aplikacja, która działa w wierszu polecenia. To, co utworzysz w programie Visual Studio w tym kroku.

## <a name="prerequisites"></a>Wymagania wstępne

- Mieć Visual Studio z pulpitu rozwoju z c++ obciążenia zainstalowanego i uruchomionego na komputerze. Jeśli nie jest jeszcze zainstalowany, zobacz [Instalowanie pomocy technicznej języka C++ w programie Visual Studio](vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Tworzenie projektu aplikacji

Visual Studio używa *projektów* do organizowania kodu dla aplikacji i *rozwiązań* do organizowania projektów. Projekt zawiera wszystkie opcje, konfiguracje i reguły używane do tworzenia aplikacji. Zarządza relacją między wszystkimi plikami projektu a wszelkimi plikami zewnętrznymi. Aby utworzyć aplikację, najpierw utworzysz nowy projekt i rozwiązanie.

::: moniker range=">=vs-2019"

1. W programie Visual Studio otwórz menu **Plik** i wybierz polecenie **Nowy > project,** aby otworzyć okno dialogowe **Utwórz nowy projekt.** Wybierz szablon **aplikacji konsoli,** który ma tagi **C++,** **Windows**i **Konsola,** a następnie wybierz pozycję **Dalej**.

   ![Tworzenie nowego projektu](media/vs2019-choose-console-app.png "Otwieranie okna dialogowego Tworzenie nowego projektu")

1. W oknie dialogowym **Konfigurowanie nowego projektu** wprowadź *helloworld* w polu edycji **nazwy projektu.** Wybierz **pozycję Utwórz,** aby utworzyć projekt.

   ![Nazwij i utwórz nowy projekt](media/vs2019-configure-new-project-hello-world.png "Nazwij i utwórz nowy projekt")

   Visual Studio tworzy nowy projekt. Jest gotowy do dodania i edycji kodu źródłowego. Domyślnie szablon aplikacji konsoli wypełnia kod źródłowy aplikacją "Hello World":

   ![Projekt Hello World w idei](media/vs2019-hello-world-code.png "Projekt Hello World w idei")

   Gdy kod wygląda tak w edytorze, możesz przystąpić do następnego kroku i utworzyć aplikację.

[Wpadłem na problem.](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=vs-2017"

1. W programie Visual Studio otwórz menu **Plik** i wybierz polecenie **Nowy > project,** aby otworzyć okno dialogowe **Nowy projekt.**

   ![Otwieranie okna dialogowego Nowy projekt](media/vscpp-file-new-project.gif "Otwieranie okna dialogowego Nowy projekt")

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **Zainstalowana > visual c++,** jeśli nie jest jeszcze zaznaczona, a następnie wybierz szablon **Pusty projekt.** W polu **Nazwa** wprowadź *helloworld*. Wybierz **przycisk OK,** aby utworzyć projekt.

   ![Nazwij i utwórz nowy projekt](media/vscpp-concierge-project-name-callouts.png "Nazwij i utwórz nowy projekt")

Visual Studio tworzy nowy, pusty projekt. Jest gotowy, aby specjalizować się w rodzaju aplikacji, którą chcesz utworzyć i dodać pliki kodu źródłowego. Zrobisz to w następnym kroku.

[Wpadłem na problem.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Uczynienie projektu aplikacją konsoli

Program Visual Studio może tworzyć wszystkie rodzaje aplikacji i składników dla systemu Windows i innych platform. **Szablon Pusty projekt** nie jest określony w rodzaju tworzonej aplikacji. Aplikacja konsoli to *aplikacja,* która działa w oknie konsoli lub wiersza polecenia. Aby go utworzyć, należy poinformować program Visual Studio, aby utworzyć aplikację, aby korzystać z podsystemu konsoli.

1. W programie Visual Studio otwórz menu **Projekt** i wybierz polecenie **Właściwości,** aby otworzyć okno dialogowe **Strony właściwości HelloWorld.**

1. W oknie dialogowym **Strony właściwości** wybierz pozycję Właściwości konfiguracji **> konsolidator > system**, a następnie wybierz pole edycji obok właściwości **Podsystem.** W wyświetlonym menu rozwijanym wybierz **pozycję Konsola (/SUBSYSTEM:KONSOLA)**. Wybierz **przycisk OK,** aby zapisać zmiany.

   ![Otwieranie okna dialogowego Strony właściwości](media/vscpp-properties-linker-subsystem.gif "Otwieranie okna dialogowego Strony właściwości")

Visual Studio wie teraz, aby utworzyć projekt do uruchomienia w oknie konsoli. Następnie dodasz plik kodu źródłowego i wprowadzisz kod aplikacji.

[Wpadłem na problem.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Dodawanie pliku kodu źródłowego

1. W **Eksploratorze rozwiązań**wybierz projekt HelloWorld. Na pasku menu wybierz pozycję **Projekt**, **Dodaj nowy element,** aby otworzyć okno dialogowe Dodaj nowy **element.**

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Visual **C++** w obszarze **Zainstalowane,** jeśli nie jest jeszcze zaznaczona. W środkowym okienku wybierz **plik C++ (cpp)**. Zmień **nazwę** na *HelloWorld.cpp*. Wybierz **pozycję Dodaj,** aby zamknąć okno dialogowe i utworzyć plik.

   ![Dodawanie pliku źródłowego dla helloworld.cpp](media/vscpp-add-new-item.gif "Dodawanie pliku źródłowego dla helloworld.cpp")

Visual Studio tworzy nowy, pusty plik kodu źródłowego i otwiera go w oknie edytora, gotowy do wprowadzenia kodu źródłowego.

[Wpadłem na problem.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Dodawanie kodu do pliku źródłowego

1. Skopiuj ten kod do okna edytora HelloWorld.cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   Kod powinien wyglądać następująco w oknie edytora:

   ![Hello World kod w edytorze](media/vscpp-hello-world-editor.png "Hello World kod w edytorze")

Gdy kod wygląda tak w edytorze, możesz przystąpić do następnego kroku i utworzyć aplikację.

[Wpadłem na problem.](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Tworzenie i uruchamianie projektu języka C++](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Przewodnik rozwiązywania problemów

Przyjdź tutaj, aby uzyskać rozwiązania typowych problemów podczas tworzenia pierwszego projektu C++.

### <a name="create-your-app-project-issues"></a>Tworzenie projektu aplikacji: problemy

::: moniker range="vs-2019"

W oknie dialogowym **Nowy projekt** powinien być wyświetlany szablon **aplikacji konsoli** zawierający tagi **C++,** **Windows**i **Konsola.** Jeśli go nie widzisz, istnieją dwie możliwe przyczyny. Może być odfiltrowany z listy lub może nie być zainstalowany. Najpierw sprawdź listy rozwijane filtru u góry listy szablonów. Ustaw je na **C++,** **Windows**i **Konsola**. Powinien pojawić się szablon **aplikacji konsoli** Języka C++; w przeciwnym razie **programowy pulpitu z** obciążeniem języka C++ nie jest zainstalowany.

Aby zainstalować **programowanie pulpitu w języku C++**, można uruchomić instalator bezpośrednio z okna dialogowego **Nowy projekt.** Wybierz **łącze Zainstaluj więcej narzędzi i funkcji** u dołu listy szablonów, aby uruchomić instalatora. Jeśli okno dialogowe **Kontrola konta użytkownika** żąda uprawnień, wybierz pozycję **Tak**. W instalatorze upewnij się, że **programowanie pulpitu z** obciążeniem języka C++ jest zaznaczone. Następnie wybierz pozycję **Modyfikuj,** aby zaktualizować instalację programu Visual Studio.

Jeśli inny projekt o tej samej nazwie już istnieje, wybierz inną nazwę dla projektu. Możesz też usunąć istniejący projekt i spróbować ponownie. Aby usunąć istniejący projekt, usuń folder rozwiązania (folder zawierający plik *helloworld.sln)* w Eksploratorze plików.

[Wróć](#create-your-app-project).

::: moniker-end

::: moniker range="vs-2017"

Jeśli **okno** dialogowe Nowy projekt nie pokazuje wpisu **Visual C++** w obszarze **Zainstalowane**, kopia programu Visual Studio prawdopodobnie nie ma zainstalowanego obciążenia pulpitu z zainstalowanym obciążeniem **języka C++.** Instalatora można uruchomić bezpośrednio w oknie dialogowym **Nowy projekt.** Wybierz **łącze Instalatora programu Visual Visual Studio,** aby ponownie uruchomić instalator. Jeśli okno dialogowe **Kontrola konta użytkownika** żąda uprawnień, wybierz pozycję **Tak**. W razie potrzeby zaktualizuj instalatora. W instalatorze upewnij się, że **programowanie pulpitu z** obciążeniem języka C++ jest zaznaczone i wybierz przycisk **OK,** aby zaktualizować instalację programu Visual Studio.

::: moniker-end

::: moniker range="<=vs-2017"

Jeśli inny projekt o tej samej nazwie już istnieje, wybierz inną nazwę dla projektu. Możesz też usunąć istniejący projekt i spróbować ponownie. Aby usunąć istniejący projekt, usuń folder rozwiązania (folder zawierający plik *helloworld.sln)* w Eksploratorze plików.

[Wróć](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>Nadaj projektowi aplikację konsoli: problemy

Jeśli nie widzisz **konsolidatora** na liście **właściwości konfiguracji,** wybierz pozycję **Anuluj,** aby zamknąć okno dialogowe **Strony właściwości.** Upewnij się, że projekt **HelloWorld** jest zaznaczony w **Eksploratorze rozwiązań** przed ponowną próbą. Nie wybieraj rozwiązania **HelloWorld** ani innego elementu w **Eksploratorze rozwiązań**.

Kontrolka rozwijana nie pojawia się w polu edycji właściwości **Podsystem,** dopóki nie wybierzesz właściwości. Kliknij pole edycji, aby je zaznaczyć. Można też nacisnąć klawisz **Tab,** aby przełączać się między formantami okna dialogowego, dopóki **podsystem** nie zostanie wyróżniony. Wybierz kontrolka listy rozwijanej lub naciśnij **klawisze Alt+Down,** aby ją otworzyć.

[Przejdź wstecz](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Dodawanie pliku kodu źródłowego: problemy

Jest w porządku, jeśli nadasz plikowi kodu źródłowego inną nazwę. Jednak nie należy dodawać więcej niż jeden plik, który zawiera ten sam kod do projektu.

Jeśli do projektu dodano niewłaściwy typ pliku, taki jak plik nagłówkowy, usuń go i spróbuj ponownie. Aby usunąć plik, zaznacz go w **Eksploratorze rozwiązań**. Następnie naciśnij klawisz **Delete.**

[Wróć](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>Dodawanie kodu do pliku źródłowego: problemy

Jeśli przypadkowo zamknięto okno edytora plików kodu źródłowego, możesz je łatwo otworzyć ponownie. Aby go otworzyć, kliknij dwukrotnie HelloWorld.cpp w oknie **Eksploratora rozwiązań.**

Jeśli czerwone squiggles pojawiają się pod czymkolwiek w edytorze kodu źródłowego, sprawdź, czy kod pasuje do przykładu w pisowni, znaki interpunkcyjne i sprawy. Przypadek jest istotny w kodzie C++.

[Wróć](#add-code-to-the-source-file).

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
