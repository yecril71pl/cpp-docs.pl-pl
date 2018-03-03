---
title: "Typy utworzone dla projektów Visual C++ plików | Dokumentacja firmy Microsoft"
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
- header files [C++], Visual C++ projects
- ActiveX controls [C++], Help files
- def files
- project items [C++], files
- Visual C++ projects, files and directories
- resource files, created by wizard
- files [C++], extensions
- Help files, for ActiveX controls
- Web projects [C++], adding items
- .def files
- licensing ActiveX controls
ms.assetid: 2b0ee2e0-ae81-4185-9bb9-11da3c99a283
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 90d7b1523c8a61405224fc21701b5203e2cfb006
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="file-types-created-for-visual-c-projects"></a>Typy plików utworzonych dla projektów Visual C++
W tym temacie opisano wszystkie typy plików, które są skojarzone z projektów Visual C++ w klasycznej aplikacji klasycznych. Rzeczywiste pliki zawarte w projekcie zależą od opcji wybranych przy użyciu kreatora i typ projektu.  
  
-   [Pliki projektu i rozwiązania](../ide/project-and-solution-files.md)  
  
-   [Projekty CLR](../ide/files-created-for-clr-projects.md)  
  
-   [Program ATL lub źródło kontroli i pliki nagłówkowe](../ide/atl-program-or-control-source-and-header-files.md)  
  
-   [Program MFC lub źródło kontroli i pliki nagłówkowe](../ide/mfc-program-or-control-source-and-header-files.md)  
  
-   [Prekompilowane pliki nagłówka](../ide/precompiled-header-files.md)  
  
-   [Pliki zasobów](../ide/resource-files-cpp.md)  
  
-   [Pliki pomocy (WinHelp)](../ide/help-files-winhelp.md)  
  
-   [Pliki wskazówek](../ide/hint-files.md)  
  
 Gdy użytkownik [utworzyć projekt Visual C++](../ide/creating-desktop-projects-by-using-application-wizards.md), tworzenia nowego rozwiązania lub może być dodaniu projektu do rozwiązania. Aplikacje inne niż trivial często są tworzone z wielu projektów w rozwiązaniu.  
  
 Projekty zazwyczaj powodują pliku EXE lub DLL. Projekty mogą być zależne od siebie; podczas procesu tworzenia środowiska Visual C++ sprawdza zależności w obrębie i między projektami. Każdy projekt ma kod źródłowy core, a w zależności od rodzaju projektu może mieć wiele plików zawierających różne aspekty projektu. Zawartość tych plików jest reprezentowana przez rozszerzenie pliku. Środowisko projektowe Visual Studio używa rozszerzeń plików, aby określić sposób obsługi zawartość pliku podczas kompilacji.  
  
 W poniższej tabeli przedstawiono typowe pliki w projekcie Visual C++ i określa je z ich rozszerzenia pliku.  
  
|Rozszerzenie pliku|Typ|Spis treści|  
|--------------------|----------|--------------|  
|.asmx|Źródło|Plik wdrożenia.|  
|ASP|Źródło|Active Server Page pliku.|  
|.ATP|Projekt|Plik projektu szablonu aplikacji.|  
|BMP, dib, GIF, jpg, jpe, PNG|Zasób|Pliki obrazów ogólne.|  
|.BSC|Trwa kompilowanie...|Przeglądarka plików kodu.|  
|.cpp; .c|Źródło|Pliki kodu źródłowego głównego aplikacji.|  
|.CUR|Zasób|Kursor graficzne plik mapy bitowej.|  
|.DBP|Projekt|Plik projektu bazy danych.|  
|.disco|Źródło|Dynamiczne odnajdowanie pliku dokumentu. Obsługuje odnajdowania usługi XML sieci Web.|  
|.exe, .dll|Projekt|Pliki wykonywalne lub dołączanej biblioteki.|  
|.h|Źródło|Nagłówek (Dołącz) pliku.|  
|htm, HTML, .xsp, .asp, .htc, HTA, .xml|Zasób|Wspólne pliki sieci Web.|  
|. HxC.|Projekt|Plik projektu pomocy.|  
|ICO|Zasób|Ikona graficzne plik mapy bitowej.|  
|.IDB|Trwa kompilowanie...|Plik stanu, zawierający informacje o zależnościach między pliki źródłowe i definicje klas, które mogą być używane przez kompilator podczas minimalna ponowna kompilacja i kompilacji przyrostowej. Użyj [/Fd](../build/reference/fd-program-database-file-name.md) opcję kompilatora, aby określić nazwę pliku .idb. Zobacz [/GM ponowną (Włącz minimalnego odbudować)](../build/reference/gm-enable-minimal-rebuild.md) Aby uzyskać więcej informacji.|  
|.IDL|Trwa kompilowanie...|Plik języka definicji interfejsu. Zobacz [plik definicji interfejsu (IDL)](http://msdn.microsoft.com/library/windows/desktop/aa378712) w zestawie SDK systemu Windows, aby uzyskać więcej informacji.|  
|.ilk|Konsolidacja|Plik konsolidowania przyrostowego. Zobacz [/INCREMENTAL](../build/reference/incremental-link-incrementally.md) Aby uzyskać więcej informacji.|  
|.map|Konsolidacja|Plik tekstowy zawierający informacje o konsolidatora. Użyj [/Fm](../build/reference/fm-name-mapfile.md) — opcja kompilatora nazwę pliku mapy. Zobacz [/MAP](../build/reference/map-generate-mapfile.md) Aby uzyskać więcej informacji.|  
|.mfcribbon ms|Zasób|Plik zasobu, który zawiera kod XML, definiujący przycisków, formantów i atrybutów na Wstążce. Aby uzyskać więcej informacji, zobacz [projektanta wstążki (MFC)](../mfc/ribbon-designer-mfc.md).|  
|.obj, .o||Pliki obiektów, skompilowane, ale nie jest połączona.|  
|.pch —|Debugowanie|Prekompilowany plik nagłówka.|  
|.RC, .rc2|Zasób|[Pliki skryptów zasobów](../windows/working-with-resource-files.md) by wygenerować zasoby.|  
|.SBR|Trwa kompilowanie...|Pośredni plik przeglądarki źródła. Plik wejściowy dla [BSCMAKE](../build/reference/bscmake-options.md).|  
|.sln|Rozwiązanie|[Rozwiązania](http://msdn.microsoft.com/en-us/a45c299d-69f5-4b67-879d-1383417df0a7) pliku.|  
|.suo|Rozwiązanie|Opcje pliku rozwiązania.|  
|.txt|Zasób|Plik tekstowy, zwykle w pliku "readme".|  
|.VAP|Projekt|Plik projektu programu Visual Studio Analyzer.|  
|.vbg|Rozwiązanie|Plik grupy zgodnego projektu.|  
|.vbp, .vip, vbproj|Projekt|Plik projektu w języku Visual Basic.|  
|.vcxitems|Projekt|Udostępniane elementy projektu do udostępniania plików kodu między wiele projektów C++. Zobacz [pliki projektu i pliki reguł programu make](../ide/project-and-solution-files.md) Aby uzyskać więcej informacji.|
|.vcxproj|Projekt|Plik projektu Visual C++. Zobacz [pliki projektu i pliki reguł programu make](../ide/project-and-solution-files.md) Aby uzyskać więcej informacji.|  
|. vcxproj.filters|Projekt|W przypadku Eksploratora rozwiązań aby dodać plik do projektu pliku filtrów definiuje gdzie w widoku drzewa Eksploratora rozwiązań plik zostanie dodany, na podstawie ich rozszerzenia nazwy pliku.|  
|vdproj|Projekt|Plik projektu programu Visual Studio wdrożenia.|  
|vmx|Projekt|Makro pliku projektu.|  
|.vup|Projekt|Narzędzie pliku projektu.|  
  
 Aby uzyskać informacje na inne pliki skojarzone z programem Visual Studio, zobacz [typy plików i rozszerzenia plików w programie Visual Studio .NET](/visualstudio/ide/reference/project-and-solution-file-types).  
  
 Pliki projektu są podzielone na folderów w Eksploratorze rozwiązań. Visual C++ tworzy folder dla plików źródłowych, pliki nagłówkowe i pliki zasobów, ale można zreorganizować tych folderów lub utworzyć nowe. Foldery służą do organizowania jawnie logicznej klastrów plików w hierarchii projektu. Na przykład można tworzyć foldery, które zawierają wszystkie Twoje pliki źródłowe interfejsu użytkownika, lub specyfikacji, dokumentacja lub zestawy testów. Wszystkie nazwy folderu plików powinny być unikatowe.  
  
 Po dodaniu elementu do projektu, należy dodać element do wszystkie konfiguracje dla projektu, niezależnie od tego, czy element jest była kompilowana. Na przykład jeśli masz projektu o nazwie MyProject dodawania elementu dodaje go do obu Debug i Release konfiguracje projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i zarządzanie projektami Visual C++](../ide/creating-and-managing-visual-cpp-projects.md)   
 [Typy projektów Visual C++](../ide/visual-cpp-project-types.md)   
 [Obsługa kreatora dla innych języków](../ide/wizard-support-for-other-languages.md)