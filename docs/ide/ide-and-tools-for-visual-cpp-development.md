---
title: "IDE i narzędzia do programowania w języku Visual C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, development tools
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c0ae9514736b66be104198c95c3764772a87ef8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="ide-and-tools-for-visual-c-development"></a>IDE i narzędzia do programowania w języku Visual C++

Jako część programu Visual Studio programowanie środowiska IDE (Integrated) programu Microsoft Visual C++ (MSVC) udostępnia wiele systemu windows i narzędzia wspólne z innych języków. Wiele osób, w tym **Eksploratora rozwiązań**, opisano w edytorze kodu i debugera, [programu Visual Studio IDE](/visualstudio/ide/visual-studio-ide). Często udostępnionego narzędzia lub okno ma nieco inny zestaw funkcji dla języka C++ niż dla języków .NET lub Javascript. Niektóre systemu windows lub narzędzia są dostępne tylko w Pro programu Visual Studio lub Visual Studio Enterprise.

Oprócz narzędzi udostępnionych w programie Visual Studio IDE MSVC ma kilka narzędzi specjalnie z myślą o programowanie kodu natywnego. Te narzędzia znajdują się w tym artykule. Aby uzyskać listę narzędzi są dostępne w każdej wersji programu Visual Studio, zobacz [narzędzia Visual C++ i funkcji w programie Visual Studio wersje](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="creating-a-solution-and-projects"></a>Tworzenie rozwiązania i projekty

A *projektu* jest zasadniczo zestaw plików kodu źródłowego i zasobów, takich jak obrazy lub pliki danych, które są wbudowane w pliku wykonywalnego. Visual Studio 2017 może obsługiwać żadnych system kompilacji lub narzędzia niestandardowej kompilacji, które mają być używane z pełną obsługę funkcji Intellisense, przeglądanie i debugowania:

- MSBuild system natywnej kompilacji dla programu Visual Studio oraz jest często najlepszym rozwiązaniem dla aplikacji uniwersalnych platformy systemu Windows (UWP) lub starszej wersji aplikacji klasycznych systemu Windows, które za pomocą MFC lub ATL. Aby uzyskać więcej informacji na temat projektów C++ na podstawie MSBuild zobacz [tworzenie projektów i zarządzanie nimi na podstawie MSBuild](creating-and-managing-visual-cpp-projects.md).
- CMake to system, który jest zintegrowany środowiska IDE programu Visual Studio, po zainstalowaniu tworzenia klasycznych aplikacji z C++ obciążenia kompilacji i platform. Aby uzyskać więcej informacji, zobacz [CMake projekty w programie Visual C++](cmake-tools-for-visual-cpp.md).
- Wszystkie inne C++ kompilacji systemu, w tym luźne Kolekcja plików, jest obsługiwana za pomocą funkcji Otwórz Folder. Można tworzyć proste pliki JSON do wywołania programu kompilacji i konfigurowania sesji debugowania. Aby uzyskać więcej informacji, zobacz [Przełącz kod w języku C++ dla programu Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/04/14/bring-your-cpp-code-to-visual-studio/).

### <a name="project-templates-msbuild"></a>Szablony projektu (MSBuild)

Visual Studio oferuje kilka szablony projektów opartych na MSBuild; te szablony zawierają kod startowy i ustawień wymaganych dla różnych typów podstawowych programu. Zazwyczaj rozpoczyna, wybierając **pliku** > **nowy projekt** Aby utworzyć projekt z szablonu projektu, następnie dodać nowych plików kodu źródłowego do tego projektu lub programować w plikach podane. Aby uzyskać informacje specyficzne dla projektów C++ i kreatorów projektu, zobacz [tworzenie i zarządzanie projekty Visual C++](../ide/creating-and-managing-visual-cpp-projects.md).

### <a name="application-wizards-msbuild"></a>Kreatorzy aplikacji (MSBuild)

Program Visual Studio udostępnia kreatorów dla niektórych typów projektów MSBuild po wybraniu **pliku** > **nowy projekt**. Kreator poprowadzi Cię przez kolejne etapy tworzenia nowego projektu. Jest to przydatne w przypadku typów projektów, które mają wiele opcji i ustawień. Aby uzyskać więcej informacji, zobacz [Tworzenie pulpitu projektów przez za pomocą kreatorów aplikacji](../ide/creating-desktop-projects-by-using-application-wizards.md).

## <a name="creating-user-interfaces-with-designers-msbuild"></a>Tworzenie interfejsów użytkownika z projektantami (MSBuild)

Program ma interfejs użytkownika, jeden z pierwszego zadania jest umieścić w nim formanty, takie jak przyciski, pola listy i tak dalej. Visual Studio zawiera visual powierzchnię i przybornika dla każdej wersji aplikacji C++. Niezależnie od tego, jakiego typu aplikacji, które tworzysz podstawową koncepcją jest taka sama: przeciągnij formant z przybornika okno i upuść ją na powierzchnię projektu w wybranej lokalizacji. W tle Visual Studio generuje zasobów i kod wymagane dokonanie jego pracy. Następnie należy napisać kod, aby wypełnić kontrolki z danymi lub dostosować wygląd i zachowanie.

Aby uzyskać więcej informacji na temat opracowywania interfejsu użytkownika dla aplikacji platformy uniwersalnej systemu Windows, zobacz [projektu i interfejsu użytkownika](https://developer.microsoft.com/en-us/windows/design).

Aby uzyskać więcej informacji o tworzeniu interfejsu użytkownika dla aplikacji MFC, zobacz [aplikacji pulpitu MFC](../mfc/mfc-desktop-applications.md). Informacji o programów Win32 systemu Windows, temacie [aplikacje dla komputerów z systemem Windows](../windows/windows-desktop-applications-cpp.md).

## <a name="writing-and-editing-code"></a>Zapisywanie i Edycja kodu

### <a name="semantic-colorization"></a>Kolorowanie semantyczne

Po utworzeniu projektu, wszystkie pliki projektu są wyświetlane w **Eksploratora rozwiązań** okna. Po kliknięciu pliku .h lub CPP w **Eksploratora rozwiązań**, otwiera plik w edytorze kodu. Edytor kodu jest specjalne Edytor tekstów kodu źródłowego języka C++. Color-codes go słów kluczowych języka, metody i nazw zmiennych i inne elementy swój kod, aby kod bardziej czytelny i łatwiejsze do zrozumienia.

### <a name="intellisense"></a>IntelliSense

Edytor kodu obsługuje również kilka funkcji, które są ze sobą znane jako Intellisense. Możesz umieść kursor nad metody i niektóre podstawowe dokumentacji dla niego. Po wpisaniu nazwy zmiennej klasy i a. lub ->, zostanie wyświetlona lista elementów członkowskich wystąpienia tej klasy. Jeśli wpiszesz nazwę klasy, a następnie::, zostanie wyświetlona lista statycznych elementów członkowskich. Po ponownym uruchomieniu, wpisując nazwę klasy lub metody, edytora kodu oferuje sugestie do wykonania instrukcji. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](/visualstudio/ide/using-intellisense).

### <a name="code-snippets"></a>Wstawki kodu

Wstawki kodu Intellisense służy do generowania najczęściej używanych lub konstrukcje kodu złożonej z klawiszy skrótów. Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).

## <a name="navigating-code"></a>Nawigowanie po kodzie

**Widoku** menu zapewnia dostęp do wielu systemu windows i narzędzia do nawigowania wokół plików kodu. Aby uzyskać szczegółowe informacje dotyczące tych z systemem windows, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).

### <a name="solution-explorer"></a>Eksplorator rozwiązań

We wszystkich wersjach programu Visual Studio, użyj **Eksploratora rozwiązań** okienko, aby przechodzić między pliki w projekcie. Rozwiń .h lub CPP ikonę pliku, aby wyświetlić klasy w pliku. Rozwiń klasę, aby zobaczyć jego elementy członkowskie. Kliknij dwukrotnie w elemencie członkowskim, można przejść do jego definicji lub wykonania w pliku.

### <a name="class-view-and-code-definition-window"></a>Widok klas i okno definicji kodu

Użyj **widoku klasy** okienko, aby zobaczyć obszary nazw i klas we wszystkich plikach, w tym klas częściowych. Można rozwinąć każdej przestrzeni nazw lub klasę, aby zobaczyć jego elementy członkowskie, a następnie kliknij dwukrotnie w elemencie członkowskim, można przejść do tej lokalizacji w pliku źródłowym. Po otwarciu **okno definicji kodu**, można wyświetlić definicji lub implementacja typu został wybrany **widoku klasy**.

### <a name="object-browser"></a>Przeglądarka obiektów

Użyj **przeglądarki obiektów** do eksplorowania informacji o typie składników środowiska wykonawczego systemu Windows (plików winmd), zestawów platformy .NET i COM biblioteki typów. Nie jest używany z biblioteki DLL systemu Win32.

### <a name="go-to-definitiondeclaration"></a>Przejdź do definicji/deklaracji

Naciśnij klawisz F12 w dowolnej zmiennej nazwy lub elementu członkowskiego interfejsu API, aby przejść do jego definicji. Jeśli definicja znajduje się w pliku winmd (dla platformy uniwersalnej systemu Windows lub Windows 8.x aplikacji do sklepu) zostaną wyświetlone informacje o typach w przeglądarce obiektów. Można również wybrać **przejdź do definicji** lub **przejdź do deklaracji** przez kliknięcie prawym przyciskiem myszy nazwę zmiennej lub typ i wybranie opcji z menu kontekstowego.

### <a name="find-all-references"></a>Znajdź wszystkie odwołania

W pliku kodu źródłowego, kliknij prawym przyciskiem myszy umieść kursor myszy nad nazwą typu lub metody lub zmiennej, a następnie wybierz pozycję **Znajdź wszystkie odwołania** aby powrócić do listy każdej lokalizacji w pliku, projektu lub rozwiązania, w którym typ jest używany. **Znajdź wszystkie odwołania** jest inteligentnego i zwraca tylko wystąpienia tej samej zmiennej identyczne, nawet jeśli inne zmienne w zakresie różnych mają taką samą nazwę.

## <a name="add-and-edit-resources--msbuild"></a>Dodawanie i edytowanie zasobów (MSBuild)

Termin *zasobów* w kontekście programu Visual Studio pulpitu projekt zawiera elementy, takie jak okien dialogowych, ikony, Lokalizowalny ciągów, ekrany powitalny, parametry połączenia bazy danych lub dowolne dane, które chcesz uwzględnić w plik wykonywalny.

Aby uzyskać więcej informacji dotyczących dodawania i edytowania zasobów w macierzystym pulpitu projektów C++, zobacz [Praca z plikami zasobów](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Kompilacja (kompilacji i łącze)

Wybierz **kompilacji** > **Kompiluj rozwiązanie** menu paska lub wprowadź kombinację klawiszy Ctrl + Shift + B, aby skompilować i połączyć projekt. Aby utworzyć kodu wykonywalnego, korzysta z programu Visual Studio [MSBuild](/visualstudio/msbuild/msbuild1) lub CMake lub niezależnie od środowisko kompilacji można skonfigurować za pomocą **Otwórz Folder**. Dla projektów MSBuild Ustaw opcje ogólne kompilacji w obszarze **narzędzia** > **opcje** > **projekty i rozwiązania** i można ustawić właściwości dla określonych projektów w obszarze **projektu** > **właściwości**. Błędy kompilacji i ostrzeżenia są zgłaszane na liście błędów (Ctrl +\\, E). Projekty programu MSBuild nie są skonfigurowane z plikami JSON, które możesz utworzyć w Eksploratorze rozwiązań. Niezależnie od systemu, należy użyć kompilacji **dane wyjściowe** okno (Alt + 2) zawiera informacje na temat procesu kompilacji. Aby uzyskać więcej informacji o konfiguracjach MSBuild, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md) i [kompilowania projektów C++ w programie Visual Studio](../ide/building-cpp-projects-in-visual-studio.md).

Można również użyć kompilatora (cl.exe) i wiele innych związanych z kompilacją autonomicznych narzędzi takich jak NMAKE i LIB bezpośrednio z poziomu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [kodu kompilacji C/C++ w wierszu polecenia](../build/building-on-the-command-line.md) i [odwołanie kompilacji C/C++](../build/reference/c-cpp-building-reference.md).

## <a name="test"></a>Test

Visual Studio zawiera frameworka testów jednostkowych natywnego języka C++ i C + +/ CLI. Aby uzyskać więcej informacji, zobacz [weryfikowanie kodu za pomocą testów jednostkowych](/visualstudio/test/unit-test-your-code) i [testów jednostkowych zapisu dla C/C++ Framework testów jednostkowych Microsoft dla języka C++](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)

## <a name="debug"></a>Debugowanie

Program można debugować przez naciśnięcie przycisku **F5** podczas konfiguracji projektu została ustawiona na debugowanie. Podczas debugowania możesz można ustawić punktów przerwania, naciskając klawisz **F9**, kroki do kodu, naciskając klawisz **F10**, wyświetlanie wartości zmiennych określony lub rejestrów, a nawet w niektórych przypadkach należy wprowadzić zmiany w kodzie i Kontynuuj debugowanie bez ponownego kompilowania. Aby uzyskać więcej informacji, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="deploy-completed-applications"></a>Wdrażanie aplikacji ukończone

Wdrażanie aplikacji platformy uniwersalnej systemu Windows dla klientów za pośrednictwem Microsoft Store za pomocą **projektu** > **magazynu** opcji menu. Wdrożenie CRT odbywa się automatycznie w tle. Aby uzyskać więcej informacji, zobacz [sprzedaży aplikacji](http://go.microsoft.com/fwlink/p/?LinkId=262280).

Podczas wdrażania aplikacji natywnej C++ pulpitu na inny komputer, należy zainstalować aplikacji oraz wszelkie pliki biblioteki, które zależy od aplikacji. Istnieją trzy sposoby wdrażania uniwersalnego środowiska uruchomieniowego C++ (Biblioteka UCRT) przy użyciu aplikacji: centralnej wdrożenia, wdrożenia lokalnego lub statycznego łączenia. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji pulpitu](../ide/deploying-native-desktop-applications-visual-cpp.md).

Aby uzyskać więcej informacji o wdrażaniu C + +/ CLI program, zobacz [przewodnik wdrażania dla deweloperów](/dotnet/framework/deployment/deployment-guide-for-developers),

## <a name="related-articles"></a>Powiązane artykuły

|||
|-|-|
|[Narzędzia i funkcje programu Visual C++ w wydaniach programu Visual Studio](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)|Pokazuje, które funkcje są dostępne w różnych wersjach programu Visual Studio.|
|[Tworzenie projektów i zarządzanie nimi na podstawie MSBuild](../ide/creating-and-managing-visual-cpp-projects.md)|Zawiera omówienie projekty oparte na C++ MSBuild w Visual Studio i łącza do innych artykułów, które wyjaśniono, jak utworzyć i zarządzać nimi.|
|[CMake projekty w programie Visual C++](cmake-tools-for-visual-cpp.md).|Zawiera opis sposobu tworzenia CMake lub innych projektów z systemem innym niż MSBuild w programie Visual C++.|
|[Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)|Zawiera opis sposobu tworzenia projektów C++.|
|[Wdrażanie natywnych aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)|Zawiera omówienie wdrożenia dla aplikacji C++ i łącza do innych artykułów opisujących wdrożenia szczegółowo.|
|[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)|Szczegółowe informacje o sposobie uaktualniania aplikacji C++, które zostały utworzone we wcześniejszych wersjach programu Visual Studio i przeprowadzanie migracji aplikacji, które zostały utworzone przy użyciu narzędzia innego niż Visual Studio.|
|[Visual C++](../top/visual-cpp-in-visual-studio.md)|W tym artykule opisano najważniejsze funkcje programu Visual C++ w Visual Studio i łącza do pozostałej części dokumentacji Visual C++.|
