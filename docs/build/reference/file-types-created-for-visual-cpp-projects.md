---
title: Typy plików utworzonych dla projektów Visual C++
ms.date: 11/04/2016
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
ms.openlocfilehash: c05dd9da5dd17b0e06ace750d34f2c5abcf94380
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823841"
---
# <a name="file-types-created-for-visual-studio-c-projects"></a>Typy plików utworzonych dla projektów języka C++ w programie Visual Studio

W tym temacie opisano wszystkie typy plików, które są skojarzone z projektów programu Visual Studio dla klasycznych aplikacji klasycznych. Rzeczywiste pliki zawarte w projekcie są zależne od typu projektu i opcje wybrane w przypadku korzystania z kreatora.

- [Pliki projektu i rozwiązania]()

- [Projekty CLR](files-created-for-clr-projects.md)

- [Program ATL lub źródło kontroli i pliki nagłówkowe](atl-program-or-control-source-and-header-files.md)

- [Program MFC lub źródło kontroli i pliki nagłówkowe](mfc-program-or-control-source-and-header-files.md)

- [Prekompilowane pliki nagłówka](../creating-precompiled-header-files.md)

- [Pliki zasobów](resource-files-cpp.md)

- [Pliki pomocy (WinHelp)](help-files-winhelp.md)

- [Pliki wskazówek](hint-files.md)

Podczas tworzenia projektu programu Visual Studio, tworzenia nowego rozwiązania, lub może być Dodawanie projektu do rozwiązania. Aplikacje inne niż prosta często są tworzone z użyciem wielu projektów w rozwiązaniu.

Projekty zazwyczaj generuje pliku EXE lub DLL. Projekty mogą być zależne od siebie; podczas procesu kompilacji w środowisku Visual Studio sprawdza zależności w obrębie i między projektami. Każdy projekt ma podstawowe kodu źródłowego, a następnie w zależności od rodzaju projektu, może mieć wiele plików zawierających różne aspekty projektu. Zawartość tych plików są wskazywane przez rozszerzenie pliku. Środowiska programistycznego Visual Studio używa rozszerzeń plików, aby określić sposób obsługi zawartość pliku podczas kompilacji.

Poniższa tabela zawiera wspólne pliki w projekcie programu Visual Studio i identyfikuje ich za pomocą ich rozszerzenia pliku.

|Rozszerzenie pliku|Typ|Spis treści|
|--------------------|----------|--------------|
|asmx|Źródło|Plik wdrożenia.|
|ASP|Źródło|Aktywny plik strony serwera.|
|.ATP|Projekt|Plik projektu szablonu aplikacji.|
|.bmp, .dib, .gif, .jpg, .jpe, .png|Zasób|Pliki obrazów ogólne.|
|.BSC|Kompilowanie|Plik kodu przeglądarki.|
|.cpp; .c|Źródło|Pliki kodu źródłowego główne dla twojej aplikacji.|
|.CUR|Zasób|Plik graficzny mapy bitowej kursora.|
|.dbp|Projekt|Plik projektu bazy danych.|
|.disco|Źródło|Dynamiczne odnajdowanie plik dokumentu. Obsługuje odnajdowania usług XML sieci Web.|
|.exe, .dll|Projekt|Pliki wykonywalne lub dołączanej biblioteki.|
|.h|Źródło|Nagłówek (Dołącz) pliku.|
|htm, HTML, .xsp, .asp, .htc, HTA, .xml|Zasób|Wspólne pliki sieci Web.|
|.HxC|Projekt|Plik projektu pomocy.|
|.ico|Zasób|Plik graficzny mapy bitowej ikony.|
|.idb|Kompilowanie|Plik stanu, zawierający informacje o zależnościach między plikami źródłowymi a definicje klas, które mogą być używane przez kompilator podczas minimalną ponowną kompilację i kompilacji przyrostowej. Użyj [/Fd](fd-program-database-file-name.md) opcję kompilatora, aby określić nazwę pliku .idb. Zobacz [/Gm (Włącz minimalną ponowną kompilację)](gm-enable-minimal-rebuild.md) Aby uzyskać więcej informacji.|
|.IDL|Kompilowanie|Plik języka definicji interfejsu. Zobacz [plik definicji interfejsu (IDL)](/windows/desktop/Rpc/the-interface-definition-language-idl-file) w zestawie Windows SDK, aby uzyskać więcej informacji.|
|.ilk|Konsolidacja|Plik konsolidowania przyrostowego. Zobacz [/INCREMENTAL](incremental-link-incrementally.md) Aby uzyskać więcej informacji.|
|map|Konsolidacja|Plik tekstowy zawierający informacje o konsolidatora. Użyj [/Fm](fm-name-mapfile.md) — opcja kompilatora nazwę pliku mapy. Zobacz [/MAP](map-generate-mapfile.md) Aby uzyskać więcej informacji.|
|.mfcribbon-ms|Zasób|Plik zasobu, który zawiera kod XML, który definiuje przyciskami, formanty i atrybuty na Wstążce. Aby uzyskać więcej informacji, zobacz [Projektant wstążki (MFC)](../../mfc/ribbon-designer-mfc.md).|
|.obj, .o||Pliki obiektów, skompilowany, ale nie jest połączona.|
|.pch|Debugowanie|Prekompilowany plik nagłówkowy.|
|.RC, .rc2|Zasób|[Pliki skryptów zasobów](../../windows/working-with-resource-files.md) by wygenerować zasoby.|
|.sbr|Kompilowanie|Plik pośredni przeglądarki źródeł. Plik wejściowy dla [BSCMAKE](bscmake-options.md).|
|.sln|Rozwiązanie|[Rozwiązania](/visualstudio/ide/solutions-and-projects-in-visual-studio) pliku.|
|.suo|Rozwiązanie|Opcje pliku rozwiązania.|
|.txt|Zasób|Plik tekstowy, zwykle w pliku "readme".|
|.VAP|Projekt|Plik projektu programu Visual Studio Analyzer.|
|.vbg|Rozwiązanie|Plik grupy projektów zgodny.|
|.vbp, .vip, .vbproj|Projekt|Plik projektu języka Visual Basic.|
|.vcxitems|Projekt|Udostępniane elementy projektu do udostępniania plików kodu między wiele projektów w języku C++. Zobacz [plików projektu i plików reguł programu make]() Aby uzyskać więcej informacji.|
|.vcxproj|Projekt|Plik projektu programu Visual Studio. Zobacz [plików projektu i plików reguł programu make]() Aby uzyskać więcej informacji.|
|.vcxproj.filters|Projekt|W przypadku Eksploratora rozwiązań, aby dodać plik do projektu pliku filtrów dla definiuje gdzie w widoku drzewa Eksploratora rozwiązań plik zostanie dodany, oparte na rozszerzenie nazwy pliku.|
|.vdproj|Projekt|Plik projektu wdrożenia programu Visual Studio.|
|.vmx|Projekt|Makro pliku projektu.|
|.vup|Projekt|Narzędzie do pliku projektu.|

Aby uzyskać informacji na temat innych plików skojarzonych z programem Visual Studio, zobacz [typy plików i rozszerzenia plików w programie Visual Studio .NET](/visualstudio/ide/reference/project-and-solution-file-types).

Pliki projektu są zorganizowane w foldery w Eksploratorze rozwiązań. Program Visual Studio tworzy folder dla plików źródłowych, pliki nagłówkowe i pliki zasobów, ale można zreorganizować tych folderów lub utworzyć nowe. Za pomocą folderów do organizowania jawnie logiczne klastrów pliki znajdujące się w hierarchii projektu. Na przykład można tworzyć foldery pomocne zawierają wszystkie swoje pliki źródłowe interfejsu użytkownika, lub specyfikacji, dokumentacja lub zestawów testów. Wszystkie nazwy folderu plików powinny być unikatowe.

Po dodaniu elementu do projektu, należy dodać element do wszystkie konfiguracje dla tego projektu, niezależnie od tego, czy element jest możliwej do skompilowania. Na przykład jeśli masz projekt o nazwie MyProject, dodanie elementu dodaje go do obu Debug i Release konfiguracje projektu.

## <a name="see-also"></a>Zobacz też

[Tworzenie i zarządzanie projektami Visual Studio C++](../creating-and-managing-visual-cpp-projects.md)<br>
[Typy projektów C++ w programie Visual Studio](visual-cpp-project-types.md)<br>