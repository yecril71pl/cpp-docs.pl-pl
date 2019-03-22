---
title: Omówienie programowania C++ w programie Visual Studio
description: Środowiska IDE programu Visual Studio obsługuje C++, programowanie na Windows, Linux, Android i iOS za pomocą edytora kodu, debuger, środowisk testowych, analizatory statycznych i innych narzędziach programistycznych.
ms.date: 03/08/2019
helpviewer_keywords:
- Visual C++, development tools
ms.openlocfilehash: dfbe98cdbae6df7dacdc2f3076891971ba86927e
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328121"
---
# <a name="overview-of-c-development-in-visual-studio"></a>Omówienie programowania C++ w programie Visual Studio

W ramach programu zintegrowanego rozwoju środowiska (IDE) Visual Studio C++ firmy Microsoft (MSVC) udostępnia wiele systemu windows i narzędzia wspólnych innych języków. Wiele z nich w tym **Eksploratora rozwiązań**, Edytor kodu i debugera, opisano w [środowiska IDE programu Visual Studio](/visualstudio/get-started/visual-studio-ide). Często udostępnione narzędzia lub okno ma nieco inny zestaw funkcji dla języka C++ niż dla języków .NET lub JavaScript. Kilka systemu windows lub narzędzi są dostępne tylko w wersjach programu Visual Studio Professional lub Visual Studio Enterprise.

Oprócz narzędzi udostępnionych w programie Visual Studio IDE MSVC ma kilka narzędzi specjalnie do tworzenie kodu natywnego. Te narzędzia są również wyszczególnione w tym artykule. Aby uzyskać listę narzędzi są dostępne w każdej wersji programu Visual Studio, zobacz [C++ narzędzia i funkcje w wersji programu Visual Studio](ide/visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="create-projects"></a>Tworzenie projektów

A *projektu* zasadniczo jest to zbiór plików kodu źródłowego i zasoby, takie jak obrazy lub dane plików, które są wbudowane w plik wykonywalny.

Program Visual Studio 2017 zapewnia obsługę dla dowolnego systemu kompilacji lub niestandardowych narzędzi kompilacji, które mają być używane z pełnym wsparciem dla funkcji IntelliSense, przeglądanie i debugowania:

- **Program MSBuild** jest natywnym system kompilacji dla programu Visual Studio. Po wybraniu **pliku** > **New** > **projektu** z menu głównego, zobacz wiele rodzajów MSBuild *szablony projektów*  , rozpoczęcie pracy, szybkie tworzenie różnych rodzajów aplikacji w języku C++.

   ![Szablony projektów](media/vs2017-new-project.png "programu Visual Studio 2017 nowego projektu okna dialogowego")

   Ogólnie rzecz biorąc należy używać tych szablonów dla nowych projektów, chyba że masz powód, aby użyć narzędzia CMake lub innego systemu projektu. Niektóre projekty zostały *kreatora* który prowadzi użytkownika krok po kroku przez proces tworzenia nowego projektu. Aby uzyskać więcej informacji, zobacz [tworzenie i zarządzanie projektami opartych na platformie MSBuild](build/creating-and-managing-visual-cpp-projects.md).

- **Narzędzie CMake** to międzyplatformowa kompilacji system, który jest zintegrowana w środowisku IDE programu Visual Studio, po zainstalowaniu programowanie aplikacji klasycznych w języku C++. Aby uzyskać więcej informacji, zobacz [projektów CMake w programie Visual Studio](build/cmake-projects-in-visual-studio.md).
- Wszystkie inne C++ kompilacji systemu, w tym luźne zbiór plików, jest świadczona za pośrednictwem **Otwórz Folder** funkcji. Możesz utworzyć proste pliki w formacie JSON do wywołania programu kompilacji i konfigurowania sesji debugowania. Aby uzyskać więcej informacji, zobacz [Otwórz Folder projektów w języku C++](build/open-folder-projects-cpp.md).

## <a name="add-to-source-control"></a>Dodaj do kontroli źródła

Kontrola źródła umożliwia koordynować pracę między wielu deweloperów, organizowanie pracy w toku z kodu produkcyjnego i utworzyć kopię zapasową kodu źródłowego. Program Visual Studio obsługuje Git i [Team Foundation Version Control \(TFVC\) ](/azure/devops/repos/tfvc/) za pośrednictwem jego **Team Explorer** okna.

![Team Explorer](media/vs2017-team-explorer.png "Visual Studio 2017 Team Explorer")

Aby uzyskać więcej informacji na temat integracji usługi Git z repozytoriami na platformie Azure, zobacz [udostępnić swój kod za pomocą programu Visual Studio 2017 i Azure repozytoriów Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017). Aby uzyskać informacji na temat integracji usługi Git za pomocą usługi GitHub, zobacz [rozszerzeniu GitHub Extension for Visual Studio](https://visualstudio.github.com/).

## <a name="create-user-interfaces-with-designers"></a>Tworzenie interfejsów użytkownika za pomocą projektantów

Jeśli program nie ma interfejsu użytkownika, można użyć projektanta, aby szybko umieścić w nim formantów, takich jak przyciski, pola listy i tak dalej. Podczas przeciągnij formant z okno przybornika i upuść go na powierzchnię projektu, Visual Studio generuje zasoby i kod jest wymagany, aby umożliwić jej pracę. Następnie napisać kod, aby dostosować wygląd i zachowanie.

![Projektant i przybornik](media/vs2017-toolbox-designer.png "projektanta i Visual Studio Toolbox 2017 r.")

Aby uzyskać więcej informacji na temat projektowania interfejsu użytkownika dla aplikacji Universal Windows Platform, zobacz [interfejsu użytkownika i projektowania](https://developer.microsoft.com/windows/design).

Aby uzyskać więcej informacji na temat tworzenia interfejsu użytkownika dla aplikacji MFC, zobacz [aplikacji pulpitu MFC](mfc/mfc-desktop-applications.md). Aby uzyskać informacje na temat programów Win32, Windows, zobacz [aplikacji komputerowych Windows](windows/windows-desktop-applications-cpp.md).

## <a name="write-code"></a>Pisanie kodu

Po utworzeniu projektu, wszystkie pliki projektu są wyświetlane w **Eksploratora rozwiązań** okna. (A *rozwiązania* to logiczny kontener przeznaczony dla jednego lub więcej powiązanych projektów.) Po kliknięciu pliku .h i .cpp w **Eksploratora rozwiązań**, plik zostanie otwarty w edytorze kodu.

![Eksplorator rozwiązań i Edytor kodu](media/vs2017-solution-explorer-code-editor.png "edytora Visual Studio 2017 oknie Solution Explorer i kodu")

Edytor kodu jest wyspecjalizowane edytora tekstu do kodu źródłowego języka C++. Jego color-codes słowa kluczowe języka, metody i nazw zmiennych i innych elementów kodu, aby kod bardziej czytelne i łatwiejsze do zrozumienia.

Aby uzyskać więcej informacji, zobacz [pisanie i Refaktoryzacja kodu](ide/writing-and-refactoring-code-cpp.md).

## <a name="add-and-edit-resources"></a>Dodawanie i edytowanie zasobów

Termin *zasobów* obejmują takie informacje, takie jak okna dialogowe, ikony, obrazy, możliwych do zlokalizowania ciągi, ekrany powitalne, parametry połączenia bazy danych lub dowolne dane, które mają zostać uwzględnione w pliku wykonywalnym.

Aby uzyskać więcej informacji na temat dodawania i edytowania zasobów w natywnych klasycznych projektów C++, zobacz [Praca z plikami zasobów](windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Kompilacja (kompilacji i link)

Wybierz **kompilacji** > **Kompiluj rozwiązanie** menu paska lub wprowadź kombinacji klawiszy Ctrl + Shift + B, skompilować i utworzyć połączenie projektu. Błędy i ostrzeżenia kompilowania są zgłaszane na liście błędów (Ctrl +\\, E). **Dane wyjściowe** okno (Alt + 2) zawiera informacje na temat procesu kompilacji.

![Dane wyjściowe okna i lista błędów](media/vs2017-output-error-list.png "okna programu Visual Studio 2017 w danych wyjściowych i lista błędów") uzyskać więcej informacji o konfiguracjach MSBuild, zobacz [Praca z właściwościami projektu](build/working-with-project-properties.md) i [Projektów i systemów kompilacji](build/projects-and-build-systems-cpp.md).

Można również użyć kompilatora (cl.exe) i wiele innych autonomiczny dotyczące kompilacji narzędzi takich jak NMAKE i LIB bezpośrednio z poziomu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [kodu kompilacji C/C++ w wierszu polecenia](build/building-on-the-command-line.md) i [odwołanie kompilacji C/C++](build/reference/c-cpp-building-reference.md).

## <a name="debug"></a>Debugowanie

Można uruchomić debugowania, naciskając klawisz **F5**. Wstrzymuje wykonywanie żadnych punktów przerwania, które zostały ustawione. Możesz również przejść przez kod jeden wiersz jednocześnie, wyświetlanie wartości zmiennych lub rejestrach, a nawet w niektórych przypadkach należy wprowadzić zmiany w kodzie i Kontynuuj debugowanie bez ponownego kompilowania. Poniższa ilustracja przedstawia sesji debugowania, w którym wykonywanie zostanie zatrzymana w punkcie przerwania. Wartości elementów członkowskich struktury danych są widoczne w **okno czujki**.

![Sesja debugowania](media/vs2017-debug-watch.png "sesji debugowania programu Visual Studio 2017")

Aby uzyskać więcej informacji, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="test"></a>Test

Program Visual Studio obejmuje struktur testów jednostek dla natywnego języka C++ i C + +/ interfejsu wiersza polecenia. Boost.Test platformy Google Test i narzędzia CTest są również obsługiwane. Uruchom testy z **Eksplorator testów** okna:

![Test Explorer](media/cpp-test-explorer-passed.png "Visual Studio 2017 Test Explorer")

Aby uzyskać więcej informacji, zobacz [weryfikowanie kodu przy użyciu testów jednostkowych](/visualstudio/test/unit-test-your-code) i [pisanie testów jednostkowych dla języka C/C++ w programie Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp).

## <a name="analyze"></a>Analiza

Visual Studio zawiera narzędzia do analizy kodu statycznego, które mogą wykrywać potencjalne problemy w kodzie źródłowym. Do tych narzędzi należą implementację [podstawowych wytycznych dotyczących języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) reguł narzędzia do sprawdzania. Aby uzyskać więcej informacji, zobacz [Code analysis for C/C++ — Przegląd](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

## <a name="deploy-completed-applications"></a>Wdrażanie ukończone aplikacje

Tradycyjne aplikacje komputerowe i aplikacje platformy uniwersalnej systemu Windows można wdrożyć w przypadku klientów za pośrednictwem witryny Microsoft Store. Wdrożenie CRT odbywa się automatycznie w tle. Aby uzyskać więcej informacji, zobacz [Windows publikować aplikacje i gry](/windows/uwp/publish/).

Można także wdrożyć macierzystym języku C++ na inny komputer, aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji komputerowych](ide/deploying-native-desktop-applications-visual-cpp.md).

Aby uzyskać więcej informacji o wdrażaniu w języku C + +/ interfejsu wiersza polecenia programu, zobacz [przewodnik wdrażania dla deweloperów](/dotnet/framework/deployment/deployment-guide-for-developers),

## <a name="next-steps"></a>Następne kroki

Zapoznaj się dodatkowo program Visual Studio, wykonując wraz z jednym niniejsze artykuły wprowadzające zawierają:

> [!div class="nextstepaction"]
> [Dowiedz się, jak za pomocą edytora kodu](/visualstudio/get-started/tutorial-editor)

> [!div class="nextstepaction"]
> [Dowiedz się więcej o projekty i rozwiązania](/visualstudio/get-started/tutorial-projects-solutions)
