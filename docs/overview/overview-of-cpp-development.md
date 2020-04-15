---
title: Omówienie programowania w języku C++ w programie Visual Studio
description: Ide programu Visual Studio obsługuje tworzenie języka C++ w systemach Windows, Linux, Android i iOS za pomocą edytora kodu, debugera, struktur testowych, analizatorów statycznych i innych narzędzi programistycznych.
ms.date: 12/02/2019
helpviewer_keywords:
- Visual C++, development tools
author: corob-msft
ms.author: corob
ms.openlocfilehash: 4e04e189b44fe61759a9422139d856ab8a09f201
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "77415709"
---
# <a name="overview-of-c-development-in-visual-studio"></a>Omówienie programowania w języku C++ w programie Visual Studio

W ramach programu Visual Studio Integrated Development Environment (IDE) program Microsoft C++ (MSVC) udostępnia wiele okien i narzędzi wspólnych z innymi językami. Wiele z nich, w tym **Eksplorator rozwiązań,** edytor kodu i debuger, są dokumentowane w programie [Visual Studio IDE](/visualstudio/get-started/visual-studio-ide). Często udostępnione narzędzie lub okno ma nieco inny zestaw funkcji dla języka C++ niż w innych językach. Kilka okien lub narzędzi jest dostępnych tylko w wersjach programu Visual Studio Professional lub Visual Studio Enterprise.

Oprócz udostępnionych narzędzi w środowisku IDE programu Visual Studio msvc ma kilka narzędzi specjalnie dla rozwoju kodu macierzystego. Narzędzia te są również wymienione w tym artykule. Aby uzyskać listę narzędzi dostępnych w każdej wersji programu Visual Studio, zobacz [Narzędzia i funkcje języka C++ w programach Visual Studio Editions](visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="create-projects"></a>Tworzenie projektów

*Projekt* jest w zasadzie zestawem plików kodu źródłowego i zasobów, takich jak obrazy lub pliki danych, które są wbudowane w program wykonywalny lub bibliotekę.

Visual Studio zapewnia obsługę dowolnego systemu projektu lub niestandardowe narzędzia kompilacji, które chcesz użyć, z pełną obsługą IntelliSense, przeglądania i debugowania:

- **MSBuild** jest macierzystym systemem projektu dla programu Visual Studio. Po **wybraniu opcji Plik** > **nowego** > **projektu** z menu głównego zostanie wyświetlonych wiele rodzajów *szablonów projektów* MSBuild, które szybko rozpoczną tworzenie różnych rodzajów aplikacji w języku C++.

   ::: moniker range="vs-2019"

   ![Nowe szablony projektów](../build/media/mathclient-project-name-2019.png "Okno dialogowe nowego projektu programu Visual Studio 2019")

   ::: moniker-end

   ::: moniker range="<=vs-2017"

   ![Szablony projektów](media/vs2017-new-project.png "Okno dialogowe nowego projektu programu Visual Studio 2017")

   ::: moniker-end

   Ogólnie rzecz biorąc należy użyć tych szablonów dla nowych projektów, chyba że używasz istniejących projektów CMake lub używasz innego systemu projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie projektów opartych na msbuild i zarządzanie nimi](../build/creating-and-managing-visual-cpp-projects.md).

- **CMake** to system kompilacji między platformami, który jest zintegrowany z ideą programu Visual Studio podczas instalowania środowiska dewelopera pulpitu z obciążeniem C++. Szablon projektu CMake można użyć dla nowych projektów lub po prostu otworzyć folder z plikiem CMakeLists.txt. Aby uzyskać więcej informacji, zobacz [CMake projektów w programie Visual Studio](../build/cmake-projects-in-visual-studio.md).

- Każdy inny system kompilacji języka C++, w tym luźna kolekcja plików, jest obsługiwany za pośrednictwem funkcji **Otwórz folder.** Tworzenie prostych plików JSON do wywoływania programu kompilacji i konfigurowania sesji debugowania. Aby uzyskać więcej informacji, zobacz [Otwieranie projektów folderów dla języka C++](../build/open-folder-projects-cpp.md).

## <a name="add-to-source-control"></a>Dodaj do formantu źródła

Kontrola źródła umożliwia koordynowanie pracy między wieloma deweloperami, izolowanie pracy w toku z kodu produkcyjnego i tworzenie kopii zapasowych kodu źródłowego. Visual Studio obsługuje Git i [Team Foundation Version Control \(TFVC\) ](/azure/devops/repos/tfvc/) za pośrednictwem okna **Eksploratora zespołu.**

::: moniker range="vs-2019"

![Eksplorator zespołu](media/vs2019-team-explorer.png "Eksplorator zespołu programu Visual Studio 2017")

::: moniker-end

::: moniker range="<=vs-2017"

![Eksplorator zespołu](media/vs2017-team-explorer.png "Eksplorator zespołu programu Visual Studio 2017")

::: moniker-end

Aby uzyskać więcej informacji na temat integracji git z reponami na platformie Azure, zobacz [Udostępnianie kodu w programie Visual Studio 2017 i usłudze Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017). Aby uzyskać informacje na temat integracji git z gitHub, zobacz [Rozszerzenie GitHub dla programu Visual Studio](https://visualstudio.github.com/).

## <a name="obtain-libraries"></a>Uzyskiwanie bibliotek

Menedżer pakietów [vcpkg służy](../build/vcpkg.md) do uzyskiwania i instalowania bibliotek innych firm. Ponad 900 bibliotek open source jest obecnie dostępnych w katalogu.

## <a name="create-user-interfaces-with-designers"></a>Tworzenie interfejsów użytkownika z projektantami

Jeśli program ma interfejs użytkownika, można użyć projektanta, aby szybko wypełnić go za pomocą formantów, takich jak przyciski, pola listy i tak dalej. Po przeciągnięciu formantu z okna przybornika i upuścić go na powierzchni projektowej, Visual Studio generuje zasoby i kod wymagane do tego, aby wszystko działało. Następnie napisać kod, aby dostosować wygląd i zachowanie.

![Projektant i przybornik](media/vs2017-toolbox-designer.png "Zestaw narzędzi i projektant programu Visual Studio 2017")

Aby uzyskać więcej informacji na temat projektowania interfejsu użytkownika dla aplikacji uniwersalnej platformy systemu Windows, zobacz [Projektowanie i interfejs użytkownika](https://developer.microsoft.com/windows/design).

Aby uzyskać więcej informacji na temat tworzenia interfejsu użytkownika dla aplikacji MFC, zobacz [Aplikacje pulpitu MFC](../mfc/mfc-desktop-applications.md). Aby uzyskać informacje o programach systemu Windows firmy Win32, zobacz [Aplikacje pulpitu systemu Windows](../windows/windows-desktop-applications-cpp.md).

## <a name="write-code"></a>Pisanie kodu

Po utworzeniu projektu wszystkie pliki projektu są wyświetlane w oknie **Eksploratora rozwiązań.** (Rozwiązanie *solution* jest logicznym kontenerem dla jednego lub więcej powiązanych projektów). Po kliknięciu pliku h lub cpp w **Eksploratorze rozwiązań**plik zostanie otwarty w edytorze kodu.

![Eksplorator rozwiązań i edytor kodu](media/vs2017-solution-explorer-code-editor.png "Visual Studio 2017 Eksplorator rozwiązań i edytor kodu")

Edytor kodu jest wyspecjalizowanym edytorem tekstu dla kodu źródłowego języka C++. To kody kolorów słowa kluczowe języka, metody i nazwy zmiennych oraz inne elementy kodu, aby kod bardziej czytelny i łatwiejszy do zrozumienia. Zapewnia również narzędzia do refaktoryzacji kodu, nawigowanie między różnymi plikami i zrozumienie, jak kod jest skonstruowany. Aby uzyskać więcej informacji, zobacz [Pisanie i refaktoryzowanie kodu](../ide/writing-and-refactoring-code-cpp.md).

## <a name="add-and-edit-resources"></a>Dodawanie i edytowanie zasobów

Program systemu Windows lub biblioteka DLL zwykle zawiera pewne *zasoby,* takie jak okna dialogowe, ikony, obrazy, ciągi zlokalizowane, ekrany powitalne, parametry połączenia bazy danych lub dowolne dane. Program Visual Studio zawiera narzędzia do dodawania i edytowania zasobów. Aby uzyskać więcej informacji, zobacz [Praca z plikami zasobów](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Kompilacja (kompilacja i łącze)

Wybierz **pozycję Build** > **Build Solution** na pasku menu lub wprowadź kombinację klawiszy **Ctrl+Shift+B,** aby skompilować i połączyć projekt. Błędy kompilacji i ostrzeżenia są zgłaszane na liście błędów (**Ctrl +\\, E**). Okno **wyjściowe** **(Alt+2**) zawiera informacje o procesie kompilacji.

![Okno wyjściowe i lista błędów](media/vs2017-output-error-list.png "Okno dane wyjściowe programu Visual Studio 2017 i lista błędów")

Aby uzyskać więcej informacji na temat konfigurowania kompilacji, zobacz [Praca z właściwościami projektu](../build/working-with-project-properties.md) i [projektami oraz tworzenie systemów](../build/projects-and-build-systems-cpp.md).

Można również użyć kompilatora (cl.exe) i wielu innych narzędzi autonomicznych związanych z kompilacją, takich jak NMAKE i LIB bezpośrednio z wiersza polecenia. Aby uzyskać więcej informacji, zobacz [Tworzenie kodu C/C++ w wierszu polecenia](../build/building-on-the-command-line.md) i odwołanie do budynku [C/C++.](../build/reference/c-cpp-building-reference.md)

## <a name="debug"></a>Debugowanie

Debugowanie można rozpocząć, naciskając klawisz **F5**. Wykonywanie wstrzymuje wszystkie ustawione punkty przerwania (naciskając **klawisz F9).** Można również krok po kroku kodu jeden wiersz na raz **(F10**), wyświetlić wartości zmiennych lub rejestrów, a nawet w niektórych przypadkach wprowadzić zmiany w kodzie i kontynuować debugowanie bez ponownego kompilowania. Na poniższej ilustracji przedstawiono sesję debugowania, w której wykonanie jest zatrzymane w punkcie przerwania. Wartości elementów członkowskich struktury danych są widoczne w **oknie czujki**.

![Sesja debugowania](media/vs2017-debug-watch.png "Sesja debugowania programu Visual Studio 2017")

Aby uzyskać więcej informacji, zobacz [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="test"></a>Testowanie

Visual Studio zawiera microsoft unit test framework dla języka C++, a także wsparcie dla Boost.Test, Google Test i CTest. Uruchom testy w oknie **Eksploratora testów:**

![Eksplorator testów](media/cpp-test-explorer-passed.png "Eksplorator testów programu Visual Studio 2017")

Aby uzyskać więcej informacji, zobacz [Weryfikowanie kodu przy użyciu testów jednostkowych](/visualstudio/test/unit-test-your-code) i [zapisu testów jednostkowych dla języka C/C++ w programie Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp).

## <a name="analyze"></a>Analiza

Visual Studio zawiera narzędzia do analizy kodu statycznego, które mogą wykryć potencjalne problemy w kodzie źródłowym. Narzędzia te obejmują wdrożenie zasad [podstawowych wytycznych języka C++.](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) Aby uzyskać więcej informacji, zobacz [Analiza kodu dla c/c++ omówienie](/cpp/code-quality/code-analysis-for-c-cpp-overview).

## <a name="deploy-completed-applications"></a>Wdrażanie ukończonych aplikacji

Za pośrednictwem sklepu Microsoft Store można wdrażać zarówno tradycyjne aplikacje klasyczne, jak i aplikacje platformy uniwersalnej systemu Windows dla klientów. Wdrożenie CRT jest obsługiwane automatycznie za kulisami. Aby uzyskać więcej informacji, zobacz [Publikowanie aplikacji i gier systemu Windows](/windows/uwp/publish/).

Można również wdrożyć natywnego pulpitu Języka C++ na innym komputerze. Aby uzyskać więcej informacji, zobacz [Wdrażanie aplikacji klasycznych](../windows/deploying-native-desktop-applications-visual-cpp.md).

Aby uzyskać więcej informacji na temat wdrażania programu C++/CLI, zobacz [Przewodnik wdrażania dla deweloperów](/dotnet/framework/deployment/deployment-guide-for-developers),

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z programem Visual Studio, wykonując następujące czynności wraz z jednym z następujących artykułów wprowadzających:

> [!div class="nextstepaction"]
> [Dowiedz się, jak korzystać z edytora kodu](/visualstudio/get-started/tutorial-editor)

> [!div class="nextstepaction"]
> [Dowiedz się więcej o projektach i rozwiązaniach](/visualstudio/get-started/tutorial-projects-solutions)
