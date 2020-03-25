---
title: Typy plików utworzone dla projektów programu C++ Visual Studio
ms.date: 04/08/2019
helpviewer_keywords:
- header files [C++], Visual Studio projects
- ActiveX controls [C++], Help files
- def files
- project items [C++], files
- Visual Studio C++ projects, files and directories
- resource files, created by wizard
- files [C++], extensions
- Help files, for ActiveX controls
- Web projects [C++], adding items
- .def files
- licensing ActiveX controls
ms.assetid: 2b0ee2e0-ae81-4185-9bb9-11da3c99a283
ms.openlocfilehash: 27e15f8dec693c6b7e70f3e03f274dcbc4f04677
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169022"
---
# <a name="file-types-created-for-visual-studio-c-projects"></a>Typy plików utworzone dla projektów programu C++ Visual Studio

Wiele typów plików jest skojarzonych z projektami programu Visual Studio dla klasycznej aplikacji klasycznych. Rzeczywiste pliki zawarte w projekcie zależą od typu projektu i opcji wybranych podczas korzystania z kreatora.

- [Pliki projektu i rozwiązania](project-and-solution-files.md)

- [Projekty CLR](files-created-for-clr-projects.md)

- [Program ATL lub źródło kontroli i pliki nagłówkowe](atl-program-or-control-source-and-header-files.md)

- [Program MFC lub źródło kontroli i pliki nagłówkowe](mfc-program-or-control-source-and-header-files.md)

- [Prekompilowane pliki nagłówka](../creating-precompiled-header-files.md)

- [Pliki zasobów](resource-files-cpp.md)

- [Pliki pomocy (WinHelp)](help-files-winhelp.md)

- [Pliki wskazówek](hint-files.md)

Podczas tworzenia projektu programu Visual Studio można go utworzyć w nowym rozwiązaniu lub dodać projekt do istniejącego rozwiązania. Aplikacje inne niż proste są zwykle opracowywane z wieloma projektami w rozwiązaniu.

Projekty zwykle tworzą plik EXE lub DLL. Projekty mogą być od siebie zależne. w trakcie procesu kompilacji środowisko programu Visual Studio sprawdza zależności zarówno wewnątrz, jak i między projektami. Każdy projekt ma zwykle podstawowy kod źródłowy. W zależności od rodzaju projektu może istnieć wiele innych plików zawierających różne aspekty projektu. Zawartość tych plików jest wskazywana przez rozszerzenie pliku. Środowisko programistyczne programu Visual Studio używa rozszerzeń plików, aby określić, jak obsłużyć zawartość pliku podczas kompilacji.

W poniższej tabeli przedstawiono typowe pliki w projekcie programu Visual Studio i są one identyfikowane przy użyciu rozszerzenia pliku.

|Rozszerzenie pliku|Typ|Zawartość|
|--------------------|----------|--------------|
|. asmx|Element źródłowy|Plik wdrożenia.|
|. ASP|Element źródłowy|Plik stronicowania Active Server.|
|. ATP|Project|Plik projektu szablonu aplikacji.|
|BMP, DIB, GIF, jpg,. jpe,. png|Zasób|Ogólne pliki obrazów.|
|. bsc|Tworzenie|Plik kodu przeglądarki.|
|. cpp,. c|Element źródłowy|Główne pliki kodu źródłowego aplikacji.|
|. CUR|Zasób|Plik graficzny kursora mapy bitowej.|
|.dbp|Project|Plik projektu bazy danych.|
|.disco|Element źródłowy|Plik dokumentu odnajdywania dynamicznego. Obsługuje odnajdywanie usług sieci Web XML.|
|.exe, .dll|Project|Pliki bibliotek wykonywalnych lub dynamicznych.|
|. h|Element źródłowy|Plik nagłówka (include).|
|. htm,. html,. XSP,. ASP,. HTC,. hta,. XML|Zasób|Wspólne pliki sieci Web.|
|.HxC|Project|Plik projektu pomocy.|
|.ico|Zasób|Plik graficzny mapy bitowej ikony.|
|. IDB|Tworzenie|Plik stanu zawierający informacje o zależnościach między plikami źródłowymi i definicjami klas. Może być używany przez kompilator podczas kompilacji przyrostowej. Użyj opcji kompilatora [/FD](fd-program-database-file-name.md) , aby określić nazwę pliku. IDB.|
|. idl|Tworzenie|Plik języka definicji interfejsu. Aby uzyskać więcej informacji, zobacz [plik definicji interfejsu (IDL)](/windows/win32/Rpc/the-interface-definition-language-idl-file) w Windows SDK.|
|. ilk|Konsolidacja|Przyrostowy plik linku. Aby uzyskać więcej informacji, zobacz [/Incremental](incremental-link-incrementally.md).|
|. map|Konsolidacja|Plik tekstowy zawierający informacje konsolidatora. Użyj opcji kompilatora [/FM](fm-name-mapfile.md) , aby nazwać plik mapy. Aby uzyskać więcej informacji, zobacz [/map](map-generate-mapfile.md).|
|.mfcribbon-ms|Zasób|Plik zasobów zawierający kod XML, który definiuje przyciski MFC, kontrolki i atrybuty na Wstążce. Aby uzyskać więcej informacji, zobacz [Projektant wstążki](../../mfc/ribbon-designer-mfc.md).|
|. obj,. o||Pliki obiektów, skompilowane, ale niepołączone.|
|. PCH|Debugowanie|Prekompilowany plik nagłówkowy.|
|. RC,. RC2|Zasób|[Pliki skryptów zasobów](../../windows/working-with-resource-files.md) do generowania zasobów.|
|.sbr|Tworzenie|Plik pośredni przeglądarki źródłowej. Plik wejściowy dla [BSCMAKE](bscmake-options.md).|
|.sln|Rozwiązanie|Plik [rozwiązania](/visualstudio/ide/solutions-and-projects-in-visual-studio) .|
|.suo|Rozwiązanie|Plik opcji rozwiązania.|
|. txt|Zasób|Plik tekstowy, zazwyczaj plik Readme.|
|.vap|Project|Plik projektu Analizator programu Visual Studio.|
|.vbg|Rozwiązanie|Zgodny plik grupy projektu.|
|. VBP,. VIP,. vbproj|Project|Plik projektu Visual Basic.|
|. vcxitems|Project|Projekt elementów udostępnionych do udostępniania plików kodu między wieloma C++ projektami. Aby uzyskać więcej informacji, zobacz [pliki projektu i rozwiązania](project-and-solution-files.md).|
|. vcxproj|Project|Plik projektu programu Visual Studio. Aby uzyskać więcej informacji, zobacz [pliki projektu i rozwiązania](project-and-solution-files.md).|
|. vcxproj. filters|Project|Używany do dodawania pliku do projektu przy użyciu Eksplorator rozwiązań. Plik filtrów definiuje, gdzie w widoku drzewa Eksplorator rozwiązań dodać plik, na podstawie jego rozszerzenia nazwy pliku.|
|.vdproj|Project|Plik projektu wdrożenia programu Visual Studio.|
|. vmx|Project|Plik projektu makra.|
|.vup|Project|Plik projektu narzędzia.|

Aby uzyskać informacje dotyczące innych plików skojarzonych z programem Visual Studio, zobacz [typy plików i rozszerzenia plików w programie Visual Studio .NET](/visualstudio/ide/reference/project-and-solution-file-types).

Pliki projektu są zorganizowane w foldery w Eksplorator rozwiązań. Program Visual Studio tworzy folder dla plików źródłowych, plików nagłówkowe i plików zasobów, ale można zreorganizować te foldery lub utworzyć nowe. Folderów można używać do organizowania jawnie logicznych klastrów plików w hierarchii projektu. Można na przykład utworzyć foldery zawierające wszystkie pliki źródłowe interfejsu użytkownika. Lub foldery specyfikacji, dokumentacji lub zestawów testów. Wszystkie nazwy folderów plików powinny być unikatowe.

Po dodaniu elementu do projektu, Dodaj element do wszystkich konfiguracji dla tego projektu. Element jest dodawany niezależnie od tego, czy jest możliwe do skompilowania. Na przykład jeśli masz projekt o nazwie Moje projekty, dodanie elementu powoduje dodanie go do konfiguracji projektu Debug i Release.

## <a name="see-also"></a>Zobacz też

[Tworzenie projektów programu Visual Studio C++ i zarządzanie nimi](../creating-and-managing-visual-cpp-projects.md)<br>
[Typy projektów C++ programu Visual Studio](visual-cpp-project-types.md)<br>
