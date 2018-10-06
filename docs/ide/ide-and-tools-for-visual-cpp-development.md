---
title: Narzędzia projektowe Visual C++ i środowisko IDE | Dokumentacja firmy Microsoft
description: Środowiska IDE programu Visual Studio obsługuje C++, programowanie na Windows, Linux, Android i iOS za pomocą edytora kodu, debuger, środowisk testowych, analizatory statycznych i innych narzędziach programistycznych.
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, development tools
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 310dc9b8e31f72fbd04c620987d9857932f7a0a1
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821154"
---
# <a name="ide-and-compiler-tools-for-visual-c-development"></a>Kompilator narzędzia projektowe Visual C++ i środowisko IDE

W ramach programu zintegrowanego rozwoju środowiska (IDE) Visual Studio programu Microsoft Visual C++ (MSVC) udostępnia wiele systemu windows i narzędzia wspólnych innych języków. Wiele z nich w tym **Eksploratora rozwiązań**, Edytor kodu i debugera, opisano w [środowiska IDE programu Visual Studio](/visualstudio/ide/visual-studio-ide). Często udostępnione narzędzia lub okno ma nieco inny zestaw funkcji dla języka C++ niż dla języków .NET lub JavaScript. Kilka systemu windows lub narzędzi są dostępne tylko w wersjach programu Visual Studio Professional lub Visual Studio Enterprise.

Oprócz narzędzi udostępnionych w programie Visual Studio IDE MSVC ma kilka narzędzi specjalnie do tworzenie kodu natywnego. Te narzędzia są również wyszczególnione w tym artykule. Aby uzyskać listę narzędzi są dostępne w każdej wersji programu Visual Studio, zobacz [Visual C++ Tools i funkcje w wersji programu Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="create-projects"></a>Tworzenie projektów

A *projektu* zasadniczo jest to zbiór plików kodu źródłowego i zasoby, takie jak obrazy lub dane plików, które są wbudowane w plik wykonywalny. 

Program Visual Studio 2015 udostępnia obsługę projektów programu MSBuild. Możesz pobrać rozszerzenia programu Visual Studio dla innych systemów kompilacji, takie jak Qt lub narzędzia CMake.

Program Visual Studio 2017 zapewnia obsługę dla dowolnego systemu kompilacji lub niestandardowych narzędzi kompilacji, które mają być używane z pełnym wsparciem dla funkcji IntelliSense, przeglądanie i debugowania:

- **Program MSBuild** jest natywnym system kompilacji dla programu Visual Studio. Po wybraniu **pliku** > **New** > **projektu** z menu głównego, zobacz wiele rodzajów MSBuild *szablony projektów*  , rozpoczęcie pracy, szybkie tworzenie różnych rodzajów aplikacji w języku C++.

   ![Szablony projektów](media/vs2017-new-project.png "programu Visual Studio 2017 nowego projektu okna dialogowego")

   Ogólnie rzecz biorąc należy używać tych szablonów dla nowych projektów, chyba że masz powód, aby użyć narzędzia CMake lub innego systemu projektu. Niektóre projekty zostały *kreatora* który prowadzi użytkownika krok po kroku przez proces tworzenia nowego projektu. Aby uzyskać więcej informacji, zobacz [tworzenie i zarządzanie projektami opartych na platformie MSBuild](creating-and-managing-visual-cpp-projects.md).

- **Narzędzie CMake** to międzyplatformowa kompilacji system, który jest zintegrowana w środowisku IDE programu Visual Studio, po zainstalowaniu programowanie aplikacji klasycznych w języku C++. Aby uzyskać więcej informacji, zobacz [projektów CMake w programie Visual C++](cmake-tools-for-visual-cpp.md).
- Wszystkie inne C++ kompilacji systemu, w tym luźne zbiór plików, jest świadczona za pośrednictwem **Otwórz Folder** funkcji. Możesz utworzyć proste pliki w formacie JSON do wywołania programu kompilacji i konfigurowania sesji debugowania. Aby uzyskać więcej informacji, zobacz [projekty Otwórz Folder w programie Visual C++](non-msbuild-projects.md).

## <a name="add-to-source-control"></a>Dodaj do kontroli źródła

Kontrola źródła umożliwia koordynować pracę między wielu deweloperów, organizowanie pracy w toku z kodu produkcyjnego i utworzyć kopię zapasową kodu źródłowego. Program Visual Studio obsługuje Git i [Team Foundation Version Control \(TFVC\) ](/azure/devops/repos/tfvc/) za pośrednictwem jego **Team Explorer** okna.

![Team Explorer](media/vs2017-team-explorer.png "Visual Studio 2017 Team Explorer")

Aby uzyskać więcej informacji na temat integracji usługi Git z repozytoriami na platformie Azure, zobacz [udostępnić swój kod za pomocą programu Visual Studio 2017 i Azure repozytoriów Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017). Aby uzyskać informacje na temat informacji na temat integracji usługi Git za pomocą usługi GitHub, zobacz [rozszerzeniu GitHub Extension for Visual Studio](https://visualstudio.github.com/).

## <a name="create-user-interfaces-with-designers"></a>Tworzenie interfejsów użytkownika za pomocą projektantów

Jeśli program nie ma interfejsu użytkownika, można użyć projektanta, aby szybko umieścić w nim formantów, takich jak przyciski, pola listy i tak dalej. Podczas przeciągnij formant z okno przybornika i upuść go na powierzchnię projektu, Visual Studio generuje zasoby i kod jest wymagany, aby umożliwić jej pracę. Następnie napisać kod, aby dostosować wygląd i zachowanie.

![Projektant i przybornik](media/vs2017-toolbox-designer.png "projektanta i Visual Studio Toolbox 2017 r.")

Aby uzyskać więcej informacji na temat projektowania interfejsu użytkownika dla aplikacji Universal Windows Platform, zobacz [interfejsu użytkownika i projektowania](https://developer.microsoft.com/en-us/windows/design).

Aby uzyskać więcej informacji na temat tworzenia interfejsu użytkownika dla aplikacji MFC, zobacz [aplikacji pulpitu MFC](../mfc/mfc-desktop-applications.md). Aby uzyskać informacje na temat programów Win32, Windows, zobacz [aplikacji komputerowych Windows](../windows/windows-desktop-applications-cpp.md).

## <a name="write-code"></a>Pisanie kodu

Po utworzeniu projektu, wszystkie pliki projektu są wyświetlane w **Eksploratora rozwiązań** okna. (A *rozwiązania* to logiczny kontener przeznaczony dla jednego lub więcej powiązanych projektów.) Po kliknięciu pliku .h i .cpp w **Eksploratora rozwiązań**, plik zostanie otwarty w edytorze kodu. 

![Eksplorator rozwiązań i Edytor kodu](media/vs2017-solution-explorer-code-editor.png "edytora Visual Studio 2017 oknie Solution Explorer i kodu")

Edytor kodu jest wyspecjalizowane edytora tekstu do kodu źródłowego języka C++. Jego color-codes słowa kluczowe języka, metody i nazw zmiennych i innych elementów kodu, aby kod bardziej czytelne i łatwiejsze do zrozumienia.

Aby uzyskać więcej informacji, zobacz [pisanie i Refaktoryzacja kodu](writing-and-refactoring-code-cpp.md).

## <a name="add-and-edit-resources"></a>Dodawanie i edytowanie zasobów

Termin *zasobów* obejmują takie informacje, takie jak okna dialogowe, ikony, obrazy, możliwych do zlokalizowania ciągi, ekrany powitalne, parametry połączenia bazy danych lub dowolne dane, które mają zostać uwzględnione w pliku wykonywalnym.

Aby uzyskać więcej informacji na temat dodawania i edytowania zasobów w natywnych klasycznych projektów C++, zobacz [Praca z plikami zasobów](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Kompilacja (kompilacji i link)

Wybierz **kompilacji** > **Kompiluj rozwiązanie** menu paska lub wprowadź kombinacji klawiszy Ctrl + Shift + B, skompilować i utworzyć połączenie projektu. Błędy i ostrzeżenia kompilowania są zgłaszane na liście błędów (Ctrl +\\, E). **Dane wyjściowe** okno (Alt + 2) zawiera informacje na temat procesu kompilacji.

![Dane wyjściowe okna i lista błędów](media/vs2017-output-error-list.png "okna programu Visual Studio 2017 w danych wyjściowych i lista błędów") uzyskać więcej informacji o konfiguracjach MSBuild, zobacz [Praca z właściwościami projektu](working-with-project-properties.md) i [Kompilowanie projektów C++ w programie Visual Studio](building-cpp-projects-in-visual-studio.md).

Można również użyć kompilatora (cl.exe) i wiele innych autonomiczny dotyczące kompilacji narzędzi takich jak NMAKE i LIB bezpośrednio z poziomu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [kodu kompilacji C/C++ w wierszu polecenia](../build/building-on-the-command-line.md) i [odwołanie kompilacji C/C++](../build/reference/c-cpp-building-reference.md).

## <a name="debug"></a>Debugowanie

Można uruchomić debugowania, naciskając klawisz **F5**. Wstrzymuje wykonywanie żadnych punktów przerwania, które zostały ustawione. Możesz również przejść przez kod jeden wiersz jednocześnie, wyświetlanie wartości zmiennych lub rejestrach, a nawet w niektórych przypadkach należy wprowadzić zmiany w kodzie i Kontynuuj debugowanie bez ponownego kompilowania. Poniższa ilustracja przedstawia sesji debugowania, w którym wykonywanie zostanie zatrzymana w punkcie przerwania. Wartości elementów członkowskich struktury danych są widoczne w **okno czujki**.

![Sesja debugowania](media/vs2017-debug-watch.png "sesji debugowania programu Visual Studio 2017")

Aby uzyskać więcej informacji, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="test"></a>Test

Program Visual Studio obejmuje struktur testów jednostek dla natywnego języka C++ i C + +/ interfejsu wiersza polecenia. Boost.Test platformy Google Test i narzędzia CTest są również obsługiwane. Uruchom testy z **Eksplorator testów** okna:

![Eksplorator testów](media/cpp-test-explorer-passed.png "Visual Studio 2017 Test Explorer")

Aby uzyskać więcej informacji, zobacz [weryfikowanie kodu przy użyciu testów jednostkowych](/visualstudio/test/unit-test-your-code) i [pisanie testów jednostkowych dla języka C/C++ w programie Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp).

## <a name="analyze"></a>Analiza

Visual Studio zawiera narzędzia do analizy kodu statycznego, które mogą wykrywać potencjalne problemy w kodzie źródłowym. Do tych narzędzi należą implementację [podstawowych wytycznych dotyczących języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) reguł narzędzia do sprawdzania. Aby uzyskać więcej informacji, zobacz [Code analysis for C/C++ — Przegląd](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

## <a name="deploy-completed-applications"></a>Wdrażanie ukończone aplikacje

Tradycyjne aplikacje komputerowe i aplikacje platformy uniwersalnej systemu Windows można wdrożyć w przypadku klientów za pośrednictwem witryny Microsoft Store. Wdrożenie CRT odbywa się automatycznie w tle. Aby uzyskać więcej informacji, zobacz [Windows publikować aplikacje i gry](/windows/uwp/publish/).

Można także wdrożyć macierzystym języku C++ na inny komputer, aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji komputerowych](deploying-native-desktop-applications-visual-cpp.md).

Aby uzyskać więcej informacji o wdrażaniu w języku C + +/ interfejsu wiersza polecenia programu, zobacz [przewodnik wdrażania dla deweloperów](/dotnet/framework/deployment/deployment-guide-for-developers),

## <a name="related-articles"></a>Powiązane artykuły

|||
|-|-|
|[Narzędzia i funkcje programu Visual C++ w wydaniach programu Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)|Pokazuje, które funkcje są dostępne w różnych wersjach programu Visual Studio.|
|[Tworzenie i zarządzanie projektami opartych na platformie MSBuild](creating-and-managing-visual-cpp-projects.md)|Zawiera omówienie projektach C++ MSBuild w Visual Studio i łącza do innych artykułów, które wyjaśniają, jak tworzyć i zarządzać nimi.|
|[Projekty CMake w programie Visual C++](cmake-tools-for-visual-cpp.md).|W tym artykule opisano sposób tworzenia, narzędzia CMake lub w innych projektach niekorzystających z programu MSBuild w programie Visual C++.|
|[Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)|W tym artykule opisano sposób tworzenia projektów w języku C++.|
|[Wdrażanie aplikacji komputerowych](deploying-native-desktop-applications-visual-cpp.md)|Zawiera omówienie wdrożenia dla aplikacji C++ i łącza do innych artykułów, które opisują wdrożenia szczegółowo.|
|[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)|Szczegółowe informacje o sposobie uaktualniania aplikacji w języku C++, które zostały utworzone we wcześniejszych wersjach programu Visual Studio, a także jak przeprowadzić migrację aplikacji, które zostały utworzone przy użyciu narzędzi innych niż program Visual Studio.|
|[Visual C++](../visual-cpp-in-visual-studio.md)|W tym artykule opisano kluczowe funkcje programu Visual C++ w Visual Studio i łącza do pozostałej części dokumentacji języka Visual C++.|
