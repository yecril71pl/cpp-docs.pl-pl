---
title: Narzędzia projektowe Visual C++ i środowisko IDE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/02/2018
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
ms.openlocfilehash: d4e7742afd3fecc4dd115624da0c1650dc662004
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412525"
---
# <a name="ide-and-tools-for-visual-c-development"></a>Narzędzia projektowe Visual C++ i środowisko IDE

W ramach programu zintegrowanego rozwoju środowiska (IDE) Visual Studio programu Microsoft Visual C++ (MSVC) udostępnia wiele systemu windows i narzędzia wspólnych innych języków. Wiele z nich w tym **Eksploratora rozwiązań**, Edytor kodu i debugera, opisano w [środowiska IDE programu Visual Studio](/visualstudio/ide/visual-studio-ide). Często udostępnione narzędzia lub okno ma nieco inny zestaw funkcji dla języka C++ niż dla języków .NET lub Javascript. Niektóre okna lub narzędzia są dostępne tylko w Visual Studio Pro lub Visual Studio Enterprise.

Oprócz narzędzi udostępnionych w programie Visual Studio IDE MSVC ma kilka narzędzi specjalnie do tworzenie kodu natywnego. Te narzędzia są również wyszczególnione w tym artykule. Aby uzyskać listę narzędzi są dostępne w każdej wersji programu Visual Studio, zobacz [Visual C++ Tools i funkcje w wersji programu Visual Studio](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="creating-a-solution-and-projects"></a>Tworzenie rozwiązań i projektów

A *projektu* zasadniczo jest to zbiór plików kodu źródłowego i zasoby, takie jak obrazy lub dane plików, które są wbudowane w plik wykonywalny.

Program Visual Studio 2015 udostępnia obsługę projektów programu MSBuild. Możesz pobrać rozszerzenia programu Visual Studio dla innych systemów kompilacji, takie jak Qt lub narzędzia CMake.

Program Visual Studio 2017 zapewnia obsługę dla dowolnego systemu kompilacji lub niestandardowych narzędzi kompilacji, które mają być używane z pełnym wsparciem dla funkcji IntelliSense, przeglądanie i debugowania:

- Program MSBuild jest systemem kompilacji natywnej dla programu Visual Studio i jest często najlepszym wyborem dla aplikacji uniwersalnych platformy Windows (UWP) lub starsze aplikacje pulpitu Windows, które używają kontenera MFC ani ATL. Aby uzyskać więcej informacji na temat projektów C++ opartych na platformie MSBuild, zobacz [tworzenie i zarządzanie projektami opartych na platformie MSBuild](creating-and-managing-visual-cpp-projects.md).
- Narzędzie CMake jest dla wielu platform, tworzenie system, który jest zintegrowana w środowisku IDE programu Visual Studio, po zainstalowaniu programowanie aplikacji klasycznych w języku C++. Aby uzyskać więcej informacji, zobacz [projektów CMake w programie Visual C++](cmake-tools-for-visual-cpp.md).
- Wszystkie inne C++ kompilacji systemu, w tym luźne zbiór plików, jest obsługiwane za pośrednictwem funkcji Otwórz Folder. Możesz utworzyć proste pliki w formacie JSON do wywołania programu kompilacji i konfigurowania sesji debugowania. Aby uzyskać więcej informacji, zobacz [przenieść kod C++ do Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/04/14/bring-your-cpp-code-to-visual-studio/).

### <a name="project-templates-msbuild"></a>Szablony projektu (MSBuild)

Program Visual Studio zawiera kilka szablonów dla projektów opartych na platformie MSBuild; te szablony zawierają kod startowy i ustawienia wymagane dla różnych typów podstawowych programów. Zazwyczaj należy rozpocząć od wybrania **pliku** > **nowy projekt** Aby utworzyć projekt z szablonu projektu, następnie dodaj nowe pliki kodu źródłowego do tego projektu lub Rozpocznij kodowanie w plikach, pod warunkiem. Aby uzyskać informacje specyficzne dla projektów w języku C++ i kreatorów projektu, zobacz [tworzenie i zarządzanie projekty języka Visual C++](../ide/creating-and-managing-visual-cpp-projects.md).

### <a name="application-wizards-msbuild"></a>Kreatorzy aplikacji (MSBuild)

Program Visual Studio zapewnia kreatory niektórych typach projektów programu MSBuild, po wybraniu **pliku** > **nowy projekt**. Kreator prowadzi użytkownika krok po kroku przez proces tworzenia nowego projektu. Jest to przydatne dla typów projektów, które mają wiele opcji i ustawień. Aby uzyskać więcej informacji, zobacz [tworzenia pulpitu projektów, za pomocą kreatorów aplikacji](../ide/creating-desktop-projects-by-using-application-wizards.md).

## <a name="creating-user-interfaces-with-designers-msbuild"></a>Tworzenie interfejsów użytkownika za pomocą projektantów (MSBuild)

Jeśli program nie ma interfejsu użytkownika, jest jedno z zadań pierwszego wypełniania kontrolki, takie jak przyciski, pola listy i tak dalej. Program Visual Studio obejmuje powierzchni projektowej i przybornika dla każdej wersji aplikacji C++. Niezależnie od tego, jakiego typu aplikacji, które tworzysz wygląda to w taki sam: przeciągnij formant z okno przybornika i upuść je na powierzchni projektowej w żądanej lokalizacji. W tle programu Visual Studio generuje zasoby i kod jest wymagany, aby umożliwić jej pracę. Następnie należy napisać kod do wypełnienia kontrolki z danymi lub dostosowywanie ich wyglądu i działania.

Aby uzyskać więcej informacji na temat projektowania interfejsu użytkownika dla aplikacji Universal Windows Platform, zobacz [interfejsu użytkownika i projektowania](https://developer.microsoft.com/en-us/windows/design).

Aby uzyskać więcej informacji na temat tworzenia interfejsu użytkownika dla aplikacji MFC, zobacz [aplikacji pulpitu MFC](../mfc/mfc-desktop-applications.md). Aby uzyskać informacje na temat programów Win32, Windows, zobacz [aplikacji komputerowych Windows](../windows/windows-desktop-applications-cpp.md).

## <a name="writing-and-editing-code"></a>Zapisywanie i Edycja kodu

### <a name="semantic-colorization"></a>Kolorowanie semantyczne

Po utworzeniu projektu, wszystkie pliki projektu są wyświetlane w **Eksploratora rozwiązań** okna. Po kliknięciu pliku .h i .cpp w **Eksploratora rozwiązań**, plik zostanie otwarty w edytorze kodu. Edytor kodu jest wyspecjalizowane edytora tekstu do kodu źródłowego języka C++. Jego color-codes słowa kluczowe języka, metody i nazw zmiennych i innych elementów kodu, aby kod bardziej czytelne i łatwiejsze do zrozumienia.

### <a name="intellisense"></a>IntelliSense

Edytor kodu obsługuje również kilka funkcji, które ze sobą, są znane jako funkcja IntelliSense. Można umieść kursor nad metodą i niektóre podstawowe dokumentacji dla niego. Po wpisaniu nazwy zmiennej klasy, a co. lub ->, zostanie wyświetlona lista składowych wystąpienia tej klasy. Jeśli zostanie wpisana nazwa klasy a następnie::, zostanie wyświetlona lista statyczne elementy członkowskie. Po uruchomieniu, wpisując nazwę klasy lub metody, Edytor kodu oferuje sugestie do wykonania instrukcji. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](/visualstudio/ide/using-intellisense).

### <a name="code-snippets"></a>Fragmenty kodu

Fragmenty kodu IntelliSense można użyć do wygenerowania często używane lub skomplikowanego kodu tworzy się za pomocą klawiszy skrótów. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).

## <a name="navigating-code"></a>Nawigowanie po kodzie

**Widoku** menu zapewnia dostęp do wielu systemów windows i narzędzia do nawigowania między wokół w plikach kodu. Aby uzyskać szczegółowe informacje dotyczące tych okien, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).

### <a name="solution-explorer"></a>Eksplorator rozwiązań

We wszystkich wersjach programu Visual Studio, należy użyć **Eksploratora rozwiązań** okienko, aby przechodzić między pliki w projekcie. Rozwiń .h i .cpp ikonę pliku, aby wyświetlić klasy w pliku. Rozwiń klasę, aby wyświetlić jego członków. Kliknij dwukrotnie członka, aby przejść do swojej definicji lub implementacji w pliku.

### <a name="class-view-and-code-definition-window"></a>Widok klasy i okno definicji kodu

Użyj **Widok klas** okienku, aby zobaczyć obszary nazw i klas we wszystkich plikach, w tym klasy częściowe. Można rozwinąć każdej przestrzeni nazw lub klasy, aby zobaczyć jej elementów członkowskich i kliknij dwukrotnie element członkowski, aby przejść do tej lokalizacji w pliku źródłowym. Jeśli otworzysz **okno definicji kodu**, można zobaczyć, definicja lub implementacji typu możesz wybrać **Widok klas**.

### <a name="object-browser"></a>Przeglądarka obiektów

Użyj **przeglądarki obiektów** do eksplorowania o typie w składników środowiska wykonawczego Windows (winmd), zestawy .NET i COM biblioteki typów. Nie jest używana z bibliotek Win32 dll.

### <a name="go-to-definitiondeclaration"></a>Przejdź do deklaracji/definicji

Naciśnij klawisz F12 w dowolnej zmiennej nazwy lub elementu członkowskiego interfejsu API, aby przejść do jego definicji. Jeśli definicja znajduje się w pliku winmd (dla platformy uniwersalnej systemu Windows lub Windows 8.x Store aplikacji), a następnie zostaną wyświetlone informacje dotyczące typu w przeglądarce obiektów. Można również wybrać **przejdź do definicji** lub **przejdź do deklaracji** , kliknij prawym przyciskiem myszy nazwę zmiennej lub typu i wybierając opcję z menu kontekstowego.

### <a name="find-all-references"></a>Znajdź wszystkie odwołania

W pliku kodu źródłowego, kliknij prawym przyciskiem myszy umieść kursor myszy nad nazwą typu lub metody lub zmiennej, a następnie wybierz **Znajdź wszystkie odwołania** aby powrócić do listy każdej lokalizacji w pliku, projekt lub rozwiązanie, w którym typ jest używany. **Znajdź wszystkie odwołania** jest inteligentne i zwraca tylko wystąpienia tej samej zmiennej identyczny, nawet jeśli inne zmienne w zakresie różnych mają taką samą nazwę.

## <a name="add-and-edit-resources--msbuild"></a>Dodawanie i edytowanie zasobów (MSBuild)

Termin *zasobów* w kontekście programu Visual Studio projekt aplikacji klasycznej kwestie, takie jak okna dialogowe, ikony, możliwych do zlokalizowania ciągi, ekrany powitalne, parametry połączenia bazy danych lub dowolne dane, które mają zostać uwzględnione w plik wykonywalny.

Aby uzyskać więcej informacji na temat dodawania i edytowania zasobów w natywnych klasycznych projektów C++, zobacz [Praca z plikami zasobów](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Kompilacja (kompilacji i link)

Wybierz **kompilacji** > **Kompiluj rozwiązanie** menu paska lub wprowadź kombinacji klawiszy Ctrl + Shift + B, skompilować i utworzyć połączenie projektu. Aby utworzyć kod wykonywalny, program Visual Studio używa [MSBuild](/visualstudio/msbuild/msbuild1) lub narzędzia CMake lub dowolne środowisko kompilacji można skonfigurować za pomocą **Otwórz Folder**. Dla projektów programu MSBuild, ustaw opcje ogólne kompilacji w ramach **narzędzia** > **opcje** > **projekty i rozwiązania** i można ustawić właściwości dla konkretnych projektów, w obszarze **projektu** > **właściwości**. Błędy i ostrzeżenia kompilowania są zgłaszane na liście błędów (Ctrl +\\, E). Projekty inne niż MSBuild są skonfigurowane przy użyciu pliki w formacie JSON, które tworzysz w Eksploratorze rozwiązań. Niezależnie od systemu, możesz użyć do kompilacji **dane wyjściowe** okno (Alt + 2) zawiera informacje na temat procesu kompilacji. Aby uzyskać więcej informacji o konfiguracjach MSBuild, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md) i [kompilowanie projektów C++ w programie Visual Studio](../ide/building-cpp-projects-in-visual-studio.md).

Można również użyć kompilatora (cl.exe) i wiele innych autonomiczny dotyczące kompilacji narzędzi takich jak NMAKE i LIB bezpośrednio z poziomu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [kodu kompilacji C/C++ w wierszu polecenia](../build/building-on-the-command-line.md) i [odwołanie kompilacji C/C++](../build/reference/c-cpp-building-reference.md).

## <a name="test"></a>Test

Program Visual Studio zawiera strukturę testów jednostek zarówno dla natywnych języka C++ i C + +/ interfejsu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [weryfikowanie kodu przy użyciu testów jednostkowych](/visualstudio/test/unit-test-your-code) i [testów jednostkowych zapisu dla języka C/C++ za pomocą Frameworka testów jednostkowych firmy Microsoft dla języka C++](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)

## <a name="analyze"></a>Analiza

Program Visual Studio zawiera narzędzia do analizy kodu statycznego dla języka C++, włącznie z implementacją [podstawowych wytycznych dotyczących języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) reguł narzędzia do sprawdzania. Aby uzyskać więcej informacji, zobacz [Code analysis for C/C++ — Przegląd](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

## <a name="debug"></a>Debugowanie

Program można debugować, naciskając klawisz **F5** kiedy konfigurację projektu jest ustawiona na debugowanie. Podczas debugowania, możesz ustawić punkty przerwania, naciskając klawisz **F9**, Przechodź przez kod, naciskając klawisz **F10**, wyświetlanie wartości zmiennych określonego lub rejestrach, a nawet w niektórych przypadkach należy wprowadzić zmiany w kodzie i Kontynuuj debugowanie bez ponownego kompilowania. Aby uzyskać więcej informacji, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="deploy-completed-applications"></a>Wdrażanie ukończone aplikacje

Wdrażanie aplikacji platformy uniwersalnej systemu Windows do klientów za pośrednictwem witryny Microsoft Store przy użyciu **projektu** > **Store** opcji menu. Wdrożenie CRT odbywa się automatycznie w tle. Aby uzyskać więcej informacji, zobacz [Windows publikować aplikacje i gry](/windows/uwp/publish/).

Podczas wdrażania natywnych aplikacji pulpitu języka C++ na innym komputerze, należy zainstalować samej aplikacji i plików biblioteki, od których zależy aplikacja. Istnieją trzy sposoby wdrożenia uniwersalne środowisko uruchomieniowe C++ (UCRT) z aplikacją: wdrożenie centralne, wdrożenie lokalne lub łączenia statycznego. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md).

Aby uzyskać więcej informacji o wdrażaniu w języku C + +/ interfejsu wiersza polecenia programu, zobacz [przewodnik wdrażania dla deweloperów](/dotnet/framework/deployment/deployment-guide-for-developers),

## <a name="related-articles"></a>Powiązane artykuły

|||
|-|-|
|[Narzędzia i funkcje programu Visual C++ w wydaniach programu Visual Studio](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)|Pokazuje, które funkcje są dostępne w różnych wersjach programu Visual Studio.|
|[Tworzenie i zarządzanie projektami opartych na platformie MSBuild](../ide/creating-and-managing-visual-cpp-projects.md)|Zawiera omówienie projektach C++ MSBuild w Visual Studio i łącza do innych artykułów, które wyjaśniają, jak tworzyć i zarządzać nimi.|
|[Projekty CMake w programie Visual C++](cmake-tools-for-visual-cpp.md).|W tym artykule opisano sposób tworzenia, narzędzia CMake lub w innych projektach niekorzystających z programu MSBuild w programie Visual C++.|
|[Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)|W tym artykule opisano sposób tworzenia projektów w języku C++.|
|[Wdrażanie aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)|Zawiera omówienie wdrożenia dla aplikacji C++ i łącza do innych artykułów, które opisują wdrożenia szczegółowo.|
|[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)|Szczegółowe informacje o sposobie uaktualniania aplikacji w języku C++, które zostały utworzone we wcześniejszych wersjach programu Visual Studio, a także jak przeprowadzić migrację aplikacji, które zostały utworzone przy użyciu narzędzi innych niż program Visual Studio.|
|[Visual C++](../visual-cpp-in-visual-studio.md)|W tym artykule opisano kluczowe funkcje programu Visual C++ w Visual Studio i łącza do pozostałej części dokumentacji języka Visual C++.|
