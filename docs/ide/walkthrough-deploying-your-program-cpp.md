---
title: 'Wskazówki: wdrażanie Twojego programu (C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
ms.openlocfilehash: eacbcef82f240589e71b59f80d8e19602ceda869
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365006"
---
# <a name="walkthrough-deploying-your-program-c"></a>Wskazówki: wdrażanie Twojego programu (C++)

Teraz, gdy aplikacja została utworzona przez ukończenie wcześniejszych powiązanych instruktajni, ostatnim krokiem jest utworzenie instalatora, aby inni użytkownicy mogli zainstalować program na swoich komputerach. W przypadku instalatora dodasz nowy projekt do istniejącego rozwiązania. Dane wyjściowe tego nowego projektu to plik setup.exe, który zainstaluje aplikację na innym komputerze.

W przewodniku pokazano, jak wdrożyć aplikację za pomocą Instalatora Windows. Można również użyć ClickOnce do wdrożenia aplikacji. Aby uzyskać więcej informacji, zobacz [ClickOnce Deployment for Visual C++ Applications](../windows/clickonce-deployment-for-visual-cpp-applications.md). Aby uzyskać więcej informacji na temat wdrażania w ogóle, zobacz [Wdrażanie aplikacji, usług i składników](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="prerequisites"></a>Wymagania wstępne

- W przewodniku przyjęto założenie, że rozumiesz podstawy języka C++.

- Przyjęto również założenie, że zostały ukończone wcześniejsze powiązane wskazówki, które są wymienione w [using visual studio IDE for C++ Desktop Development](using-the-visual-studio-ide-for-cpp-desktop-development.md).

- Instruktażu nie można ukończyć w wersjach ekspresowych programu Visual Studio.

## <a name="install-the-visual-studio-setup-and-deployment-project-template"></a>Instalowanie szablonu projektu konfiguracji i wdrażania programu Visual Studio

Kroki opisane w tej sekcji różnią się w zależności od zainstalowanej wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj formantu selektor **wersji.** Znajduje się w górnej części spisu treści na tej stronie.

<!-- markdownlint-disable MD034 -->

::: moniker range="vs-2019"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2019"></a>Aby zainstalować szablon projektu instalacji i wdrażania programu Visual Studio 2019

1. Jeśli jeszcze tego nie zrobiono, pobierz rozszerzenie Microsoft Visual Studio Installer Projects. Rozszerzenie jest bezpłatne dla deweloperów programu Visual Studio i dodaje funkcje szablonów projektu instalacji i wdrażania do programu Visual Studio. Po nawiązaniu połączenia z Internetem w programie Visual Studio wybierz pozycję **Zarządzanie rozszerzeniami rozszerzeń** > **Manage Extensions**. W oknie dialogowym **Rozszerzenia i aktualizacje** wybierz kartę **Online** i wpisz w polu wyszukiwania pozycję *Projekty instalatora programu Microsoft Visual Studio.* Naciśnij **pozycję Enter**, wybierz pozycję Microsoft Visual Studio ** \<version> Installer Projects**i kliknij przycisk **Pobierz**. Wybierz, aby uruchomić i zainstalować rozszerzenie, a następnie uruchom ponownie program Visual Studio.

1. Na pasku menu programu Visual Studio wybierz pozycję **File** > **Recent Projects and Solutions**, a następnie wybierz opcję ponownego otwarcia projektu.

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu,** aby otworzyć okno dialogowe Tworzenie nowego **projektu.** W polu wyszukiwania wpisz "Ustawienia", a z listy wyników wybierz pozycję **Setup Project**.

1. Wprowadź nazwę projektu instalacji w polu **Nazwa.** Z listy rozwijanej **Rozwiązanie** wybierz pozycję **Dodaj do rozwiązania**. Wybierz przycisk **OK,** aby utworzyć projekt instalacji. W oknie edytora zostanie otwarta karta **Asystent plików (ProjectName).**

1. Kliknij prawym przyciskiem myszy węzeł **Folder aplikacji** i wybierz polecenie **Dodaj** > **dane wyjściowe projektu,** aby otworzyć okno dialogowe **Dodawanie grupy wyjściowej projektu.**

1. W oknie dialogowym wybierz pozycję **Wyjście główne** i kliknij przycisk **OK**. Zostanie wyświetlony nowy element o nazwie **Podstawowe dane wyjściowe z gry (aktywne).**

1. Wybierz element **Wyjście podstawowe z gry (aktywny),** kliknij prawym przyciskiem myszy i wybierz polecenie **Utwórz skrót do podstawowego wyjścia z gry (Aktywny).** Zostanie wyświetlony nowy element o nazwie **Skrót do podstawowego wyjścia z gry (aktywny).**

1. Zmień nazwę elementu skrótu na *Gra,* a następnie przeciągnij i upuść element do **węzła Menu programy użytkownika** po lewej stronie okna.

1. W **Eksploratorze rozwiązań**wybierz projekt **Instalatora gier** i wybierz polecenie **Wyświetl** > **okno Właściwości** lub naciśnij **klawisz F4,** aby otworzyć okno **Właściwości.**

1. Określ dodatkowe szczegóły, tak jak chcesz, aby były wyświetlane w instalatorze.  Na przykład użyj *contoso* dla **producenta,** *Instalatora gier* dla **nazwy produktu**i *https\://www.contoso.com* dla **SupportUrl**.

1. Na pasku menu wybierz pozycję **Build** > **Configuration Manager**. W tabeli **Projekt** w kolumnie **Kompilacja** zaznacz pole wyboru **Instalator gry**. Kliknij przycisk **Zamknij**.

1. Na pasku menu wybierz pozycję Build Build Solution to build the Game project and the Game Installer project .On the menu bar, choose **Build** > **Build Solution** to build the Game project and the Game Installer project.

1. W folderze rozwiązania znajdź program setup.exe utworzony z projektu Instalatora gier, a następnie uruchom go, aby zainstalować aplikację Gra na komputerze. Możesz skopiować ten plik (i GameInstaller.msi), aby zainstalować aplikację i jej wymagane pliki biblioteki na innym komputerze.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2017-and-earlier"></a>Aby zainstalować szablon projektu instalacji i wdrażania dla programu Visual Studio 2017 i wcześniejszych

1. Po nawiązaniu połączenia z Internetem w programie Visual Studio wybierz pozycję **Rozszerzenia i aktualizacje** **narzędzi** > .

1. W obszarze **Rozszerzenia i aktualizacje**wybierz kartę **Online** i wpisz w polu wyszukiwania pozycję *Projekty instalatora programu Microsoft Visual Studio.* Naciśnij **pozycję Enter**, wybierz pozycję Microsoft Visual Studio ** \<version> Installer Projects**i kliknij przycisk **Pobierz**.

1. Wybierz, aby zainstalować rozszerzenie, a następnie uruchom ponownie program Visual Studio.

1. Na pasku menu wybierz **pozycję File** > **Recent Projects and Solutions**, a następnie wybierz rozwiązanie **Gry,** aby je ponownie otworzyć.

### <a name="to-create-a-setup-project-and-install-your-program"></a>Aby utworzyć projekt instalacji i zainstalować program

1. Zmień konfigurację aktywnego rozwiązania na Zwolnij. Na pasku menu wybierz pozycję **Build** > **Configuration Manager**. W oknie **dialogowym Menedżer konfiguracji** na liście rozwijanej **Konfiguracja rozwiązania Active** wybierz pozycję **Zwolnij**. Wybierz przycisk **Zamknij,** aby zapisać konfigurację.

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu,** aby otworzyć okno dialogowe **Nowy projekt.**

1. W lewym okienku okna dialogowego rozwiń węzły **Zainstalowane** > **inne typy projektów,** a następnie wybierz pozycję **Instalator programu Visual Studio**. W środkowym okienku wybierz pozycję **Projekt instalacji**.

1. Wprowadź nazwę projektu instalacji w polu **Nazwa.** W tym przykładzie wprowadź *program Game Installer*. Z listy rozwijanej **Rozwiązanie** wybierz pozycję **Dodaj do rozwiązania**. Wybierz przycisk **OK,** aby utworzyć projekt instalacji. W oknie edytora zostanie otwarta karta **Asystent plików (Instalator gier).**

1. Kliknij prawym przyciskiem myszy węzeł **Folder aplikacji** i wybierz polecenie **Dodaj** > **dane wyjściowe projektu,** aby otworzyć okno dialogowe **Dodawanie grupy wyjściowej projektu.**

1. W oknie dialogowym wybierz pozycję **Wyjście główne** i kliknij przycisk **OK**. Zostanie wyświetlony nowy element o nazwie **Podstawowe dane wyjściowe z gry (aktywne).**

1. Wybierz element **Wyjście podstawowe z gry (aktywny),** kliknij prawym przyciskiem myszy i wybierz polecenie **Utwórz skrót do podstawowego wyjścia z gry (Aktywny).** Zostanie wyświetlony nowy element o nazwie **Skrót do podstawowego wyjścia z gry (aktywny).**

1. Zmień nazwę elementu skrótu na *Gra,* a następnie przeciągnij i upuść element do **węzła Menu programy użytkownika** po lewej stronie okna.

1. W **Eksploratorze rozwiązań**wybierz projekt **Instalatora gier** i wybierz polecenie **Wyświetl** > **okno Właściwości** lub naciśnij **klawisz F4,** aby otworzyć okno **Właściwości.**

1. Określ dodatkowe szczegóły, tak jak chcesz, aby były wyświetlane w instalatorze.  Na przykład użyj *contoso* dla **producenta,** *Instalatora gier* dla **nazwy produktu**i *https\://www.contoso.com* dla **SupportUrl**.

1. Na pasku menu wybierz pozycję **Build** > **Configuration Manager**. W tabeli **Projekt** w kolumnie **Kompilacja** zaznacz pole wyboru **Instalator gry**. Kliknij przycisk **Zamknij**.

1. Na pasku menu wybierz pozycję Build Build Solution to build the Game project and the Game Installer project .On the menu bar, choose **Build** > **Build Solution** to build the Game project and the Game Installer project.

1. W folderze rozwiązania znajdź program setup.exe utworzony z projektu Instalatora gier, a następnie uruchom go, aby zainstalować aplikację Gra na komputerze. Możesz skopiować ten plik (i GameInstaller.msi), aby zainstalować aplikację i jej wymagane pliki biblioteki na innym komputerze.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

**Poprzedni:** [Instruktaż: Debugowanie projektu (C++)](walkthrough-debugging-a-project-cpp.md)

## <a name="see-also"></a>Zobacz też

[Odwołanie do języka języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
[Wdrażanie aplikacji klasycznych](../windows/deploying-native-desktop-applications-visual-cpp.md)<br/>
