---
title: Tworzenie projektu aplikacji konsoli w języku C++
description: Tworzenie aplikacji konsolowej Hello World w języku Visual C++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 739da0b6e5400117c0b09a3d4c3335bd44529a25
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314951"
---
# <a name="create-a-c-console-app-project"></a>Tworzenie projektu aplikacji konsoli w języku C++

Zwykle początkowy punkt jest programistą języka C++ "Hello, world!" Aplikacja, która jest uruchamiana w wierszu polecenia. To, co utworzysz w programie Visual Studio w tym kroku.

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio za pomocą programowanie aplikacji klasycznych, z obciążeniem C++ zainstalowany i uruchomiony na komputerze. Jeśli nie jest jeszcze zainstalowany, zobacz [Instalowanie obsługi języka C++ w programie Visual Studio](vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Utwórz projekt aplikacji

Program Visual Studio używa *projektów* organizowania kodu dla aplikacji, a *rozwiązania* do organizowania projektów. Projekt zawiera wszystkie opcje, konfiguracji i reguły używane do tworzenia aplikacji i zarządza relacji między plików wszystkich projektów i plików zewnętrznych. Aby utworzyć aplikację, najpierw należy utworzyć nowy projekt i rozwiązanie.

::: moniker range=">=vs-2019"

1. W programie Visual Studio, otwórz **pliku** menu i wybierz polecenie **New** > **projektu** otworzyć **Utwórz nowy projekt** okna dialogowego. Wybierz **aplikacja Konsolowa** szablonu, a następnie wybierz **dalej**.

   ![Utwórz nowy projekt](media/vs2019-choose-console-app.png "otworzyć tworzenia okna dialogowego Nowy projekt")

1. W **konfigurowania nowego projektu** okno dialogowe, wprowadź *HelloWorld* w **Nazwa projektu** pole edycji. Wybierz **Utwórz** do tworzenia projektu.

   ![Nazwy i Utwórz nowy projekt](media/vs2019-configure-new-project-hello-world.png "nazwy i Utwórz nowy projekt")

   Program Visual Studio tworzy nowy projekt, gotowy do dodawania oraz edytowania kodu źródłowego. Domyślnie szablon Aplikacja konsoli wypełnia kodu źródłowego za pomocą aplikacji "Hello World":

   ![Witaj świecie projektu w IDE](media/vs2019-hello-world-code.png "projektu Hello World w środowisku IDE")

   Gdy kod wygląda to w edytorze, wszystko będzie gotowe, przejdź do następnego kroku i skompiluj aplikację.

::: moniker-end

::: moniker range="<=vs-2017"

1. W programie Visual Studio, otwórz **pliku** menu i wybierz polecenie **nowy > Projekt** otworzyć **nowy projekt** okna dialogowego.

   ![Otwórz okno dialogowe Nowy projekt](media/vscpp-file-new-project.gif "otwarcie okna dialogowego Nowy projekt")

1. W **nowy projekt** okno dialogowe, wybierz opcję **zainstalowane**, **Visual C++** Jeśli jeszcze nie jest zaznaczone, a następnie wybierz **pusty projekt** szablon. W **nazwa** wprowadź *HelloWorld*. Wybierz **OK** do tworzenia projektu.

   ![Nazwy i Utwórz nowy projekt](media/vscpp-concierge-project-name-callouts.png "nazwy i Utwórz nowy projekt")

Program Visual Studio tworzy nowy, pusty projekt, gotowe do specialize dla rodzaju aplikacji, którą chcesz utworzyć i dodać pliki kodu źródłowego. Należy to zrobić to w następnym kroku.

[Wystąpił problem.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Utworzyć projekt aplikacji konsoli

Program Visual Studio można utworzyć wszelkiego rodzaju aplikacje i składniki dla Windows i innych platform. **Pusty projekt** szablon nie ma informacji na temat tworzy jakiego rodzaju aplikacji. Aby utworzyć *aplikacja konsolowa*, jednego, które jest uruchamiane w konsoli lub w oknie wiersza polecenia, musisz poinformować programu Visual Studio do kompilowania aplikacji do użycia podsystemu konsoli.

1. W programie Visual Studio, otwórz **projektu** menu i wybierz polecenie **właściwości** otworzyć **stron właściwości HelloWorld** okna dialogowego.

1. W **stron właściwości** okna dialogowego, w obszarze **właściwości konfiguracji**, wybierz opcję **konsolidatora**, **systemu**, a następnie wybierz pole edycji obok pozycji **podsystemu** właściwości. W wyświetlonym menu rozwijanym wybierz **Konsola (/ SUBSYSTEM: CONSOLE)**. Wybierz **OK** Aby zapisać zmiany.

   ![Otwórz okno dialogowe strony właściwości](media/vscpp-properties-linker-subsystem.gif "Otwórz okno dialogowe strony właściwości")

Program Visual Studio teraz wie, aby skompilować projekt, aby uruchomić w oknie konsoli. Następnie dodasz plik kodu źródłowego i wprowadź kod dla aplikacji.

[Wystąpił problem.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Dodaj plik kodu źródłowego

1. W **Eksploratora rozwiązań**, wybierz projekt HelloWorld. Na pasku menu wybierz **projektu**, **Dodaj nowy element** otworzyć **Dodaj nowy element** okna dialogowego.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **Visual C++** w obszarze **zainstalowane** Jeśli nie została jeszcze wybrana. W środkowym okienku wybierz **plik C++ (.cpp)**. Zmiana **nazwa** do *HelloWorld.cpp*. Wybierz **Dodaj** aby zamknąć okno dialogowe, a następnie utwórz plik.

   ![Dodawanie pliku źródłowego dla HelloWorld.cpp](media/vscpp-add-new-item.gif "dodać plik źródłowy dla HelloWorld.cpp")

Visual studio tworzy plik kodu źródłowego na nowy, pusty i otwiera go w oknie edytora gotowa do przejścia w kodzie źródłowym.

[Wystąpił problem.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Dodaj kod do pliku źródłowego

1. Skopiuj ten kod w oknie edytora HelloWorld.cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   Kod powinien wyglądać następująco w oknie edytora:

   ![Witaj, świecie kodu w edytorze](media/vscpp-hello-world-editor.png "kodu Witaj, świecie w edytorze")

Gdy kod wygląda to w edytorze, wszystko będzie gotowe, przejdź do następnego kroku i skompiluj aplikację.

[Wystąpił problem.](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Kompilowanie i uruchamianie projektu w języku C++](vscpp-step-2-build.md)

::: moniker range="<=vs-2017"

## <a name="troubleshooting-guide"></a>Przewodnik rozwiązywania problemów

Tu rozwiązania typowych problemów podczas tworzenia pierwszego projektu C++.

### <a name="create-your-app-project-issues"></a>Tworzenie aplikacji problemy projektu

Jeśli **nowy projekt** nie wyświetla okno dialogowe **Visual C++** wpis w **zainstalowane**, Twoja kopia programu Visual Studio, prawdopodobnie nie masz **pulpitu Programowanie w języku C++** zainstalowanym obciążeniem. Można uruchomić Instalatora z **nowy projekt** okna dialogowego. Wybierz **Otwórz Instalator programu Visual Studio** łącze, aby uruchomić Instalatora ponownie. Jeśli **Kontrola konta użytkownika** okna dialogowego żąda uprawnień, wybierz polecenie **tak**. W oknie Instalatora upewnij się, że **programowanie aplikacji klasycznych w języku C++** obciążenie jest zaznaczone, a następnie wybierz **OK** można zaktualizować instalację programu Visual Studio.

Jeśli inny projekt o takiej samej nazwie już istnieje, wybierz inną nazwę dla projektu, lub usuń istniejący projekt i spróbuj ponownie. Aby usunąć istniejący projekt, należy usunąć folder rozwiązania (folder, który zawiera plik helloworld.sln) w Eksploratorze plików.

[Przejdź wstecz](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>Wprowadź projektu problemów aplikacji konsoli

Jeśli nie widzisz **konsolidatora** obszarze **właściwości konfiguracji**, wybierz **anulować** zamknąć **strony właściwości** okna dialogowego a następnie Upewnij się, że **HelloWorld** projekt jest wybrany w **Eksploratora rozwiązań**, nie rozwiązania lub innego pliku lub folderu, przed ponowną próbą.

Kontrolka dropdown nie jest wyświetlana w **podsystemu** właściwość pole edycji, dopóki nie wybierzesz właściwości. Możesz wybrać go za pomocą wskaźnika lub możesz nacisnąć klawisz Tab, aby przechodzić między formantów okna dialogowego aż do **podsystemu** zostanie wyróżniona. Wybierz formant listy rozwijanej lub naciśnij klawisze Alt + Strzałka w dół, aby go otworzyć.

[Przejdź wstecz](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Dodaj problemy z plików kodu źródłowego

Szkodzi, jeśli podać inną nazwę pliku z kodem źródłowym. Jednak nie należy dodawać więcej niż jednego pliku kodu źródłowego, który zawiera ten sam kod do projektu.

Jeśli typ pliku jest dodawany do projektu, na przykład plik nagłówka, usuń go i spróbuj ponownie. Aby usunąć plik, wybierz go w **Eksploratora rozwiązań** i naciśnij klawisz Delete.

[Przejdź wstecz](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>Dodaj kod do problemów z plików źródłowych

Jeśli przypadkowo zamknięty źródło pliku okna edytora kodu, aby otworzyć go ponownie, kliknij dwukrotnie HelloWorld.cpp w **Eksploratora rozwiązań** okna.

Czerwone symbole są wyświetlane w obszarze dowolne elementy w edytorze kodu źródłowego, sprawdź, czy kod jest zgodna w przykładzie w pisowni, znaki interpunkcyjne i wielkości liter. Sprawa jest istotne w przypadku kodu C++.

[Przejdź wstecz](#add-code-to-the-source-file).

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
