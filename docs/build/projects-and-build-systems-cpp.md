---
title: Projekty języka C/C++ i systemów kompilacji w programie Visual Studio
ms.description: Use Visual Studio to compile and build C++ projects for Windows, ARM or Linux based on any project system.
ms.date: 12/08/2018
f1_keywords:
- vcbuilding
- buildingaprogramVC
helpviewer_keywords:
- builds [C++]
- Visual C++ projects, building
- projects [C++], building
- builds [C++], options
- Visual C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.openlocfilehash: 73797f3817338c48e8ff11eaaadff71263374fd0
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124762"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>Projekty języka C/C++ i systemów kompilacji w programie Visual Studio

Visual Studio 2017 służy do edytowania, kompilowania i kompilacji kodu C++ podstawowy z pełną obsługą technologii IntelliSense, bez konieczno ści konwersji kodu do projektu programu Visual Studio lub kompilacji z zestawem narzędzi MSVC. Na przykład można edytować projektu narzędzia CMake dla wielu platform w programie Visual Studio na komputerze Windows następnie skompilować go dla systemu Linux przy użyciu g ++ na komputerze zdalnym z systemem Linux.

## <a name="c-compilation"></a>Kompilacja języka C++

Aby *kompilacji* oznacza program w języku C++ skompilować kod źródłowy z jednego lub więcej plików, a następnie połącz te pliki do pliku wykonywalnego (.exe), obciążenia dynamicznie biblioteka (dll) lub biblioteka statyczna (.lib). 

Podstawowe kompilacji C++ obejmuje trzy główne kroki:

- Preprocesora C++ przekształca wszystkie definicje #directives i makr w każdym pliku źródłowego. Spowoduje to utworzenie *jednostki translacji*.
- Kompilator języka C++ kompiluje każdą jednostkę translacji w plikach obiektowych (.obj), stosując, niezależnie od opcji kompilatora zostały ustawione.
- *Konsolidatora* scala plików obiektów w jednym pliku wykonywalnego, zastosowanie opcji konsolidatora, które zostały ustawione. 

## <a name="the-msvc-toolset"></a>Zestaw narzędzi MSVC

Microsoft C++ kompilatora, konsolidatora, standardowych bibliotek i pokrewne narzędzia obejmują zestaw narzędzi kompilatora MSVC (nazywanych również łańcucha "narzędzia do kompilacji"). Są one wyświetlane w programie Visual Studio. Możesz również pobrać i bezpłatne korzystanie z zestawu narzędzi jako autonomiczny pakiet z [Lokalizacja pobierania narzędzia Build Tools for Visual Studio 2017](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017).

Proste programy można tworzyć za pomocą kompilatora MSVC (cl.exe) bezpośrednio z poziomu wiersza polecenia. Poniższe polecenie akceptuje pojedyncze źródło pliku z kodem i wywołuje cl.exe, aby utworzyć plik wykonywalny o nazwie *hello.exe*: 

```cmd
cl /EHsc hello.cpp
```
Należy pamiętać, że tutaj kompilatora (cl.exe) automatycznie wywołuje preprocesora języka C++ i konsolidator, aby wygenerować plik końcowych danych wyjściowych.  Aby uzyskać więcej informacji, zobacz [tworzenia w wierszu polecenia](building-on-the-command-line.md).

## <a name="build-systems-and-projects"></a>Budowanie systemów i projektów

Większości programów rzeczywistych korzystać z niektórych rodzaju *system kompilacji* zarządzanie złożonością, kompilowanie wiele plików źródłowych w przypadku konfiguracji z wieloma (czyli debugowanie a release), wiele platform (x86, x64, ARM, i tak dalej), niestandardowej kompilacji czynności, a nawet utworzyć wiele plików wykonywalnych, które muszą być skompilowane w określonej kolejności. Wprowadź ustawienia w plikach konfiguracji kompilacji, a system kompilacji akceptuje tego pliku jako dane wejściowe, przed jej wywoływanie kompilatora. Zestaw plików kodu źródłowego i kompilacja pliki konfiguracji niezbędne do utworzenia pliku wykonywalnego jest nazywany *projektu*. 

Na poniższej liście przedstawiono różne opcje dla projektów programu Visual Studio — C++:

- Tworzenie projektu programu Visual Studio przy użyciu programu Visual Studio IDE i skonfiguruj ją za pomocą strony właściwości. Projektów programu Visual Studio generuje programów, które działają na Windows. Aby uzyskać przegląd, zobacz [kompilowanie i tworzenie](/visualstudio/ide/compiling-and-building-in-visual-studio) w dokumentacji programu Visual Studio.

- Otwórz folder, który zawiera plik CMakeLists.txt. Obsługa CMake jest zintegrowana w programie Visual Studio. Edytowanie, testowanie i debugowanie bez modyfikowania pliki CMake w jakikolwiek sposób, można użyć środowiska IDE. Dzięki temu można pracować w tym samym projektu narzędzia CMake jako innym, kto może korzystać z różnymi edytorami. Narzędzie CMake jest zalecane podejście do projektowania na różne platformy. Aby uzyskać więcej informacji, zobacz [projektów CMake](cmake-projects-in-visual-studio.md).
 
- Otwórz luźne folderu plików źródłowych z żadnego pliku projektu. Program Visual Studio będzie używać Algorytm heurystyczny do tworzenia plików. Jest to prosty sposób, aby skompilować i uruchomić aplikacje konsoli małe. Aby uzyskać więcej informacji, zobacz [projektów Otwórz Folder](open-folder-projects-cpp.md).

- Otwórz folder, który zawiera pliku reguł programu make lub dowolnego innego kompilacji system konfiguracji pliku. Można skonfigurować programu Visual Studio do wywołania dowolnych poleceń dowolnego kompilacji przez dodanie plików JSON do folderu. Aby uzyskać więcej informacji, zobacz [projektów Otwórz Folder](open-folder-projects-cpp.md).
 
- Otwórz plik reguł programu make Windows w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [odwołanie NMAKE](reference/nmake-reference.md).

## <a name="msbuild-from-the-command-line"></a>Program MSBuild z wiersza polecenia 

Przekazując plik .vcxproj wraz z opcjami wiersza polecenia, można wywołać program MSBuild z wiersza polecenia. Takie podejście wymaga dobrej znajomości sposobu programu MSBuild i jest zalecane tylko wtedy, gdy jest to absolutnie konieczne. Aby uzyskać więcej informacji, zobacz [MSBuild](msbuild-visual-cpp.md).

## <a name="in-this-section"></a>W tej sekcji

[Projektów programu Visual Studio](creating-and-managing-visual-cpp-projects.md) jak tworzenie, konfigurowanie i tworzenie w języku C++ projektów w programie Visual Studio przy użyciu jego native tworzenie systemu (MSBuild).

[Projekty CMake](cmake-projects-in-visual-studio.md) instrukcje kodu, kompilowania i wdrażania projektów CMake w programie Visual Studio.

[Otwórz Folder projektów](open-folder-projects-cpp.md) jak za pomocą programu Visual Studio code, kompilowania i wdrażania projektów w języku C++ na podstawie dowolnego systemu kompilacji dowolnego lub żaden system kompilacji. W ogóle. 

[Kompilacje wydania](release-builds.md) sposób tworzenia i rozwiązywanie problemów z zoptymalizowane wersji kompilacji do wdrożenia dla użytkowników końcowych.

[Używanie zestawu narzędzi MSVC z poziomu wiersza polecenia](building-on-the-command-line.md)<br/>
W tym artykule omówiono sposób użycia kompilator C/C++ i narzędzia build tools bezpośrednio z poziomu wiersza polecenia, a nie przy użyciu programu Visual Studio IDE.

[Kompilowanie biblioteki dll w programie Visual Studio](dlls-in-visual-cpp.md) jak tworzyć, debugować i wdrażać bibliotek DLL języka C/C++ (biblioteki udostępnione) w programie Visual Studio.

[Przewodnik: Tworzenie i używanie biblioteki statycznej](walkthrough-creating-and-using-a-static-library-cpp.md) sposobu tworzenia pliku binarnego. lib.

[Kompilowanie aplikacji izolowanych C/C++ i zestawów Side-by-side](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md) w tym artykule opisano model wdrażania dla aplikacji Windows Desktop z koncepcję izolowanymi oraz aplikacjami wykonywanymi side-by-side.

[Konfigurowanie projektów w języku C++ x64 64-bitowy, obiekty docelowe](configuring-programs-for-64-bit-visual-cpp.md) jak do obiektu docelowego x64 64-bitowego sprzętu z MSVC narzędzia do kompilacji.

[Konfigurowanie projektów w języku C++ dla procesorów ARM](configuring-programs-for-arm-processors-visual-cpp.md) jak za pomocą narzędzia do kompilacji MSVC sprzętu ARM.

[Optymalizacja kodu](optimizing-your-code.md) sposobu optymalizacji kodu na różne sposoby, w tym program sterowanej optymalizacji.

[Konfigurowanie programów systemu Windows XP](configuring-programs-for-windows-xp.md) jak Windows XP z MSVC narzędzia do kompilacji docelowej.

[Dokumentacja kompilacji w języku C/C++](reference/c-cpp-building-reference.md)<br/>
Zawiera łącza do gama artykułów dotyczących programu, tworzenia w języku C++, opcje kompilatora i konsolidatora i różnych narzędzi do kompilacji.
