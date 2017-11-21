---
title: "Krok 1 — Tworzenie projektu C++ aplikacji konsoli | Dokumentacja firmy Microsoft"
description: "Zainstaluj obsługę programu Visual Studio dla programu Visual C++"
ms.custom: mvc
ms.date: 10/17/2017
ms.topic: get-started-article
ms.technology: devlang-C++
ms.devlang: C++
dev_langs: C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f75d8fc6ec744038d57bfb7576547c9be84b7551
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="create-a-c-console-app-project"></a>Utwórz projekt aplikacji konsoli języka C++

Zwykle rozpocząć programisty C++ jest tekst "Hello, world!" aplikacja uruchamiana w wierszu polecenia. To, jakie zostaną utworzone w programie Visual Studio w tym kroku.

## <a name="prerequisites"></a>Wymagania wstępne

- Masz program Visual Studio z tworzenia klasycznych aplikacji z C++ obciążenia zainstalowana i uruchomiona na komputerze. Jeśli nie jest jeszcze zainstalowana, zobacz [krok 0 - zainstalować obsługi języka C++ w programie Visual Studio](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Utwórz projekt aplikacji

Visual Studio będzie korzystać *projekty* organizowania kodu dla aplikacji i *rozwiązań* do organizowania projektów. Projekt zawiera wszystkie opcje, konfiguracji i reguły służące do tworzenia aplikacji i zarządza relacji między plików wszystkich projektów i pliki zewnętrzne. Aby utworzyć aplikację, najpierw należy utworzyć nowego projektu i rozwiązania.

1. W programie Visual Studio Otwórz **pliku** menu i wybierz polecenie **nowy > Projekt** otworzyć **nowy projekt** okna dialogowego.

   ![Otwórz okno dialogowe Nowy projekt](../build/media/vscpp-file-new-project.gif "Otwórz okno dialogowe Nowy projekt")

1. W **nowy projekt** okno dialogowe, wybierz opcję **zainstalowana**, **Visual C++** Jeśli jeszcze nie jest zaznaczone, a następnie wybierz **pusty projekt** szablon. W **nazwa** wprowadź *HelloWorld*. Wybierz **OK** Aby utworzyć projekt.

   ![Nazwy i Utwórz nowy projekt](../build/media/vscpp-concierge-project-name-callouts.png "nazwy i Utwórz nowy projekt")

Visual Studio tworzy nowy, pusty projekt, gotowy do specialize dla rodzaju aplikacji, którą chcesz utworzyć i dodać do plików kodu źródłowego. Należy to zrobić tego dalej.

[Czy wystąpił problem.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Utworzyć projekt aplikacji konsoli

Visual Studio można utworzyć wszelkiego rodzaju aplikacje i składniki systemu Windows i innych platform. **Pusty projekt** szablonu nie jest konkretnym tworzy jakiego rodzaju aplikacji. Aby utworzyć *aplikacji konsoli*, jednego z systemem w konsoli lub w oknie wiersza polecenia, należy wskazać Visual Studio, aby utworzyć aplikację do użycia podsystemu konsoli.

1. W programie Visual Studio Otwórz **projektu** menu i wybierz polecenie **właściwości** otworzyć **strony właściwości HelloWorld** okna dialogowego.

1. W **strony właściwości** okna dialogowego, w obszarze **właściwości konfiguracji**, wybierz pozycję **konsolidatora**, **systemu**, a następnie wybierz obok pola edycji **podsystemu** właściwości. W wyświetlonym menu rozwijanego wybierz **konsoli (/ SUBSYSTEM: CONSOLE)**. Wybierz **OK** Aby zapisać zmiany.

   ![Otwórz okno dialogowe strony właściwości](../build/media/vscpp-properties-linker-subsystem.gif "Otwórz okno dialogowe strony właściwości")

Visual Studio teraz wie, aby skompilować projekt do uruchamiania w oknie konsoli. Następnie będzie dodawanie pliku kodu źródłowego i wprowadź kod aplikacji.

[Czy wystąpił problem.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Dodawanie pliku kodu źródłowego

1. W **Eksploratora rozwiązań**, wybierz projekt HelloWorld. Na pasku menu wybierz **projektu**, **Dodaj nowy element** otworzyć **Dodaj nowy element** okna dialogowego.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **Visual C++** w obszarze **zainstalowana** Jeśli nie została już wybrana. W środkowym okienku wybierz **plik C++ (.cpp)**. Zmień **nazwa** do *HelloWorld.cpp*. Wybierz **Dodaj** aby zamknąć okno dialogowe i utworzyć pliku.

   ![Dodawanie pliku źródłowego dla HelloWorld.cpp](../build/media/vscpp-add-new-item.gif "Dodawanie pliku źródłowego dla HelloWorld.cpp")

Visual studio tworzy plik kodu źródłowego na nowy, pusty i otwarcie go w oknie edytora gotowa do przejścia w kodzie źródłowym.

[Czy wystąpił problem.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Dodaj kod do pliku źródłowego

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

   ![Witaj świecie kodu w edytorze](../build/media/vscpp-hello-world-editor.png "Hello World kodu w edytorze")

Gdy kod wygląda następująco w edytorze, wszystko jest gotowe, przejdź do następnego kroku i tworzenie aplikacji.

[Czy wystąpił problem.](#add-a-source-code-file-issues)

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Krok 2: Tworzenie i uruchamianie projektu C++](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Przewodnik rozwiązywania problemów

Pochodzić tutaj rozwiązania często występujących problemów podczas tworzenia pierwszego projektu C++.

### <a name="create-your-app-project-issues"></a>Tworzenie aplikacji problemy projektu

Jeśli **nowy projekt** nie wyświetla okno dialogowe **Visual C++** wpis w **zainstalowana**, kopii programu Visual Studio, prawdopodobnie nie masz **pulpitu Programowanie w języku C++** obciążenia zainstalowane. Można uruchomić Instalatora z **nowy projekt** okna dialogowego. Wybierz **Otwórz Instalator programu Visual Studio** łącze, aby uruchomić Instalatora ponownie. Jeśli **Kontrola konta użytkownika** okna dialogowego żąda uprawnień, wybierz **tak**. W Instalatorze, upewnij się, **tworzenia klasycznych aplikacji w języku C++** obciążenie jest zaznaczony, a następnie wybierz pozycję **OK** do aktualizacji instalacji programu Visual Studio.

Jeśli inny projekt o tej samej nazwie już istnieje, wybierz inną nazwę dla projektu, lub usuń istniejący projekt i spróbuj ponownie. Aby usunąć istniejący projekt, należy usunąć folder rozwiązania (folder zawierający plik helloworld.sln) w Eksploratorze plików.

[Przejdź wstecz](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>Wprowadź projektu problemy aplikacji konsoli

Jeśli nie widzisz **konsolidatora** kategorii **właściwości konfiguracji**, wybierz **anulować** zamknąć **strony właściwości** okna dialogowego, a następnie Upewnij się, że **HelloWorld** projekt jest wybrany w **Eksploratora rozwiązań**, nie rozwiązania lub inny plik lub folder, przed ponowną próbą.

Formant listy rozwijanej nie jest wyświetlany w **podsystemu** pole edycji właściwości dopiero po wybraniu właściwości. Możesz wybrać je za pomocą wskaźnika lub naciśnij klawisz Tab, aby przechodzić kolejno przez formanty okna dialogowego aż do **podsystemu** zostanie wyróżniona. Wybierz kontrolki rozwijanej lub naciśnij klawisze Alt + Strzałka w dół, aby go otworzyć.

[Przejdź wstecz](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Dodaj problemów z plików kodu źródłowego

Szkodzi, jeśli podać inną nazwę pliku kodu źródłowego. Jednak nie należy dodawać więcej niż jednego pliku kodu źródłowego, który zawiera ten sam kod do projektu.

Jeśli dodano niewłaściwych plików do projektu, na przykład plik nagłówka, usuń go i spróbuj ponownie. Aby usunąć plik, wybierz je w **Eksploratora rozwiązań** i naciśnij klawisz Delete.

[Przejdź wstecz](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>Dodaj kod, aby problemy pliku źródłowego

Jeśli przypadkowo zamknięty okna edytora pliku kodu na źródło, aby otworzyć go ponownie, kliknij dwukrotnie HelloWorld.cpp w **Eksploratora rozwiązań** okna.

Czerwone zygzaki są wyświetlane w obszarze wszystko w edytorze kodu źródłowego, sprawdź, czy kod jest zgodna przykład pisowni, znaki interpunkcyjne i przypadku. Przypadek jest istotna w języku C++ kod.

[Przejdź wstecz](#add-code-to-the-source-file).

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />