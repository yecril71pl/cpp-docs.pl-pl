---
title: Omówienie programowania w języku C++ w programie Visual Studio
description: Środowisko IDE programu Visual Studio obsługuje programowanie w języku C++ w systemach Windows, Linux, Android i iOS z edytorem kodu, debugerem, strukturami testów, analizatorami statycznymi i innymi narzędziami programistycznymi.
ms.date: 12/02/2019
helpviewer_keywords:
- Visual C++, development tools
author: corob-msft
ms.author: corob
ms.openlocfilehash: 02364f778cdab3416cbac7cc1462ce79287b1ad9
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684368"
---
# <a name="overview-of-c-development-in-visual-studio"></a>Omówienie programowania w języku C++ w programie Visual Studio

W ramach zintegrowanego środowiska programistycznego (IDE) programu Visual Studio, Microsoft C++ (MSVC) udostępnia wiele okien i narzędzi wspólnych dla innych języków. Wiele z tych elementów, w tym **Eksplorator rozwiązań**, Edytor kodu i debuger, są udokumentowane w obszarze [IDE programu Visual Studio](/visualstudio/get-started/visual-studio-ide). Często udostępnione narzędzie lub okno ma nieco inny zestaw funkcji dla języka C++ niż w przypadku innych języków. Kilka okien lub narzędzi jest dostępnych tylko w wersjach Visual Studio Professional lub Visual Studio Enterprise.

Oprócz udostępnionych narzędzi w środowisku IDE programu Visual Studio MSVC ma kilka narzędzi przeznaczonych do tworzenia kodu natywnego. Te narzędzia są również wymienione w tym artykule. Aby uzyskać listę narzędzi dostępnych w każdej wersji programu Visual Studio, zobacz [Narzędzia i funkcje języka C++ w wersjach programu Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="create-projects"></a>Tworzenie projektów

*Projekt* jest zasadniczo zestawem plików kodu źródłowego i zasobów, takich jak obrazy lub pliki danych, które są wbudowane w program wykonywalny lub biblioteka.

Program Visual Studio zapewnia obsługę dowolnego systemu projektu lub niestandardowych narzędzi do kompilacji, które mają być używane, z pełną obsługą technologii IntelliSense, przeglądanie i debugowanie:

- **MSBuild** to natywny system projektu dla programu Visual Studio. Po wybraniu opcji **plik**  >  **Nowy**  >  **projekt** z menu głównego zobaczysz wiele rodzajów *szablonów projektów programu* MSBuild, które umożliwiają szybkie rozpoczęcie tworzenia różnych rodzajów aplikacji C++.

   ::: moniker range="vs-2019"

   ![Nowe szablony projektów](../build/media/mathclient-project-name-2019.png "Okno dialogowe nowego projektu programu Visual Studio 2019")

   ::: moniker-end

   ::: moniker range="<=vs-2017"

   ![Szablony projektów](media/vs2017-new-project.png "Okno dialogowe nowego projektu programu Visual Studio 2017")

   ::: moniker-end

   Ogólnie rzecz biorąc należy używać tych szablonów dla nowych projektów, chyba że używasz istniejących projektów CMake lub używasz innego systemu projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie projektów opartych na programie MSBuild i zarządzanie nimi](../build/creating-and-managing-visual-cpp-projects.md).

- **CMAKE** to Międzyplatformowy system kompilacji, który jest zintegrowany z programem Visual Studio IDE podczas instalacji tworzenia aplikacji klasycznych przy użyciu obciążenia C++. Szablon projektu CMake można użyć dla nowych projektów lub po prostu otworzyć folder z plikiem CMakeLists.txt. Aby uzyskać więcej informacji, zobacz [CMAKE projects in Visual Studio](../build/cmake-projects-in-visual-studio.md).

- Każdy inny system kompilacji C++, w tym luźny zbiór plików, jest obsługiwany za pośrednictwem funkcji **Otwórz folder** . Tworzysz proste pliki JSON do wywołania programu kompilacji i konfigurowania sesji debugowania. Aby uzyskać więcej informacji, zobacz [Otwieranie projektów folderu dla języka C++](../build/open-folder-projects-cpp.md).

## <a name="add-to-source-control"></a>Dodaj do kontroli źródła

Kontrola źródła umożliwia koordynowanie pracy wśród wielu deweloperów, izolowanie pracy w toku od kodu produkcyjnego i tworzenie kopii zapasowej kodu źródłowego. Program Visual Studio obsługuje narzędzia Git i [Kontrola wersji serwera Team Foundation \( \) TFVC](/azure/devops/repos/tfvc/) za poorednictwem okna **Team Explorer** .

::: moniker range="vs-2019"

![Zrzut ekranu okna Team Explorer w programie Visual Studio 2019.](media/vs2019-team-explorer.png "Team Explorer programu Visual Studio 2017")

::: moniker-end

::: moniker range="<=vs-2017"

![Zrzut ekranu okna Team Explorer w programie Visual Studio 2017.](media/vs2017-team-explorer.png "Team Explorer programu Visual Studio 2017")

::: moniker-end

Aby uzyskać więcej informacji na temat integracji narzędzia Git z repozytoriami na platformie Azure, zobacz [udostępnianie kodu w programie Visual Studio 2017 i Azure Repos git](/azure/devops/repos/git/share-your-code-in-git-vs-2017). Aby uzyskać informacje na temat integracji narzędzia Git z usługą GitHub, zobacz [rozszerzenie GitHub dla programu Visual Studio](https://visualstudio.github.com/).

## <a name="obtain-libraries"></a>Uzyskaj biblioteki

Użyj Menedżera pakietów [vcpkg](../build/vcpkg.md) , aby uzyskać i zainstalować biblioteki innych firm. W wykazie są obecnie dostępne ponad 900 bibliotek Open Source.

## <a name="create-user-interfaces-with-designers"></a>Tworzenie interfejsów użytkownika za pomocą projektantów

Jeśli program ma interfejs użytkownika, można użyć projektanta, aby szybko wypełnić go kontrolkami, takimi jak przyciski, pola listy i tak dalej. Gdy przeciągniesz kontrolkę z okna przybornika i porzucisz ją na powierzchni projektowej, program Visual Studio generuje zasoby i kod wymagany do jego działania. Następnie napiszesz kod, aby dostosować wygląd i zachowanie.

![Projektant i Przybornik](media/vs2017-toolbox-designer.png "Przybornik i projektant programu Visual Studio 2017")

Aby uzyskać więcej informacji na temat projektowania interfejsu użytkownika dla aplikacji platforma uniwersalna systemu Windows, zobacz [projektowanie i interfejs](https://developer.microsoft.com/windows/design)użytkownika.

Aby uzyskać więcej informacji na temat tworzenia interfejsu użytkownika dla aplikacji MFC, zobacz [aplikacje klasyczne MFC](../mfc/mfc-desktop-applications.md). Aby uzyskać informacje na temat programów Win32 systemu Windows, zobacz [aplikacje klasyczne systemu Windows](../windows/windows-desktop-applications-cpp.md).

## <a name="write-code"></a>Pisanie kodu

Po utworzeniu projektu wszystkie pliki projektu są wyświetlane w oknie **Eksplorator rozwiązań** . ( *Rozwiązanie* jest kontenerem logicznym dla co najmniej jednego powiązanego projektu). Po kliknięciu pliku. h lub. cpp w **Eksplorator rozwiązań**, plik zostanie otwarty w edytorze kodu.

![Eksplorator rozwiązań i Edytor kodu](media/vs2017-solution-explorer-code-editor.png "Visual Studio 2017 Eksplorator rozwiązań i Edytor kodu")

Edytor kodu jest wyspecjalizowanym procesorem tekstów dla kodu źródłowego C++. Kod koloru IT języka — słowa kluczowe, metody i nazwy zmiennych oraz inne elementy kodu, aby zwiększyć czytelność kodu i ułatwić jego zrozumienie. Zapewnia także narzędzia do refaktoryzacji kodu, Nawigowanie między różnymi plikami i zrozumienie, jak kod jest strukturalny. Aby uzyskać więcej informacji, zobacz [pisanie i Refaktoryzacja kodu](../ide/writing-and-refactoring-code-cpp.md).

## <a name="add-and-edit-resources"></a>Dodawanie i edytowanie zasobów

Program lub biblioteka DLL systemu Windows zwykle zawiera niektóre *zasoby*, takie jak okna dialogowe, ikony, obrazy, lokalizowalne ciągi, ekrany powitalne, parametry połączenia bazy danych lub dowolne dane. Program Visual Studio zawiera narzędzia umożliwiające dodawanie i edytowanie zasobów. Aby uzyskać więcej informacji, zobacz [Praca z plikami zasobów](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Kompilacja (kompilacja i link)

Wybierz pozycję **Kompiluj**  >  **kompilację rozwiązania** na pasku menu lub wprowadź kombinację **klawiszy Ctrl + Shift + B** , aby skompilować i połączyć projekt. Błędy kompilacji i ostrzeżenia są raportowane w Lista błędów (**Ctrl + \\ , E**). Okno **dane wyjściowe** (**ALT + 2**) pokazuje informacje o procesie kompilacji.

![Okno Dane wyjściowe i Lista błędów](media/vs2017-output-error-list.png "Okno danych wyjściowych programu Visual Studio 2017 i Lista błędów")

Aby uzyskać więcej informacji o konfigurowaniu kompilacji, zobacz [Praca z właściwościami projektu](../build/working-with-project-properties.md) i [projektami i systemami kompilacji](../build/projects-and-build-systems-cpp.md).

Można również użyć kompilatora (cl.exe) i wielu innych autonomicznych narzędzi związanych z kompilacją, takich jak NMAKE i LIB, bezpośrednio z wiersza polecenia. Aby uzyskać więcej informacji, zobacz [kompilowanie kodu C/c++ w wierszu polecenia](../build/building-on-the-command-line.md) i [Dokumentacja konstrukcyjna c/c++](../build/reference/c-cpp-building-reference.md).

## <a name="debug"></a>Debugowanie

Debugowanie można rozpocząć, naciskając klawisz **F5**. Wykonywanie jest wstrzymywane dla wszystkich ustawionych punktów przerwania (przez naciśnięcie klawisza **F9**). Możesz również przejść przez kod jeden wiersz w czasie (**F10**), wyświetlić wartości zmiennych lub rejestrów, a nawet w niektórych przypadkach wprowadzić zmiany w kodzie i kontynuować debugowanie bez ponownego kompilowania. Na poniższej ilustracji przedstawiono sesję debugowania, w której wykonywanie zostało zatrzymane w punkcie przerwania. Wartości elementów członkowskich struktury danych są widoczne w **oknie Czujka**.

![Sesja debugowania](media/vs2017-debug-watch.png "Sesja debugowania programu Visual Studio 2017")

Aby uzyskać więcej informacji, zobacz [debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="test"></a>Testowanie

Program Visual Studio zawiera środowisko testów jednostkowych firmy Microsoft dla języka C++, a także obsługę podwyższania poziomu. test, Google Test i narzędzia ctest. Uruchom testy z okna **Eksploratora testów** :

![Eksplorator testów](media/cpp-test-explorer-passed.png "Eksplorator testów programu Visual Studio 2017")

Aby uzyskać więcej informacji, zobacz [Weryfikowanie kodu przy użyciu testów jednostkowych](/visualstudio/test/unit-test-your-code) i [pisanie testów jednostkowych dla C/C++ w programie Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp).

## <a name="analyze"></a>Analiza

Program Visual Studio zawiera narzędzia do analizy kodu statycznego, które mogą wykrywać potencjalne problemy w kodzie źródłowym. Te narzędzia obejmują implementację elementów sprawdzania reguł [podstawowe wytyczne dotyczące języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) . Aby uzyskać więcej informacji, zobacz [Analiza kodu dla C/C++ — Omówienie](/cpp/code-quality/code-analysis-for-c-cpp-overview).

## <a name="deploy-completed-applications"></a>Wdrażanie ukończonych aplikacji

Za pomocą Microsoft Store można wdrażać zarówno tradycyjne aplikacje klasyczne, jak i aplikacje platformy UWP. Wdrażanie CRT jest obsługiwane automatycznie w tle. Aby uzyskać więcej informacji, zobacz [publikowanie aplikacji i gier systemu Windows](/windows/uwp/publish/).

Możesz również wdrożyć natywny pulpit C++ na innym komputerze. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji klasycznych](../windows/deploying-native-desktop-applications-visual-cpp.md).

Aby uzyskać więcej informacji na temat wdrażania programu C++/CLI, zobacz [Przewodnik wdrażania dla deweloperów](/dotnet/framework/deployment/deployment-guide-for-developers),

## <a name="next-steps"></a>Następne kroki

Poznanie programu Visual Studio w następujący sposób wraz z jednym z następujących artykułów wprowadzających:

> [!div class="nextstepaction"]
> [Dowiedz się, jak używać edytora kodu](/visualstudio/get-started/tutorial-editor)

> [!div class="nextstepaction"]
> [Informacje o projektach i rozwiązaniach](/visualstudio/get-started/tutorial-projects-solutions)
