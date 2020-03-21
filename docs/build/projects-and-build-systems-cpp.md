---
title: C/C++ projekty i systemy kompilacji w programie Visual Studio
ms.description: Use Visual Studio to compile and build C++ projects for Windows, ARM or Linux based on any project system.
ms.date: 07/17/2019
helpviewer_keywords:
- builds [C++]
- C++ projects, building
- projects [C++], building
- builds [C++], options
- C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.topic: overview
ms.openlocfilehash: 3d82ac4569e06a4472047a79da60032ad2db43ca
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078474"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>C/C++ projekty i systemy kompilacji w programie Visual Studio

Możesz użyć programu Visual Studio do edytowania, kompilowania i kompilowania dowolnego C++ kodu bazowego z pełną obsługą technologii IntelliSense bez konieczności konwertowania tego kodu do projektu programu Visual Studio lub kompilowania przy użyciu zestawu narzędzi MSVC. Na przykład można edytować Międzyplatformowy projekt CMake w programie Visual Studio na komputerze z systemem Windows, a następnie kompilować go dla systemu Linux przy użyciu języka g + + na zdalnym komputerze z systemem Linux.

## <a name="c-compilation"></a>C++kompilowa

C++ Aby *skompilować program, należy* skompilować kod źródłowy z jednego lub większej liczby plików, a następnie połączyć te pliki do pliku wykonywalnego (. exe), biblioteki dynamicznej ładowania (. dll) lub biblioteki statycznej (. lib).

Kompilacja C++ podstawowa obejmuje trzy główne kroki:

- C++ Preprocesor przekształca wszystkie #directives i definicje makr w każdym pliku źródłowym. Spowoduje to utworzenie *jednostki tłumaczenia*.
- C++ Kompilator kompiluje każdą jednostkę tłumaczenia na pliki obiektów (. obj), stosując wszystkie opcje kompilatora, które zostały ustawione.
- *Konsolidator* scala pliki obiektów w jeden plik wykonywalny, stosując ustawione Opcje konsolidatora.

## <a name="the-msvc-toolset"></a>Zestaw narzędzi MSVC

Kompilatory C++ firmy Microsoft, konsolidator, biblioteki standardowe i powiązane narzędzia składają się z zestawu narzędzi kompilatora MSVC (nazywanego również łańcucha narzędzi lub "narzędzia kompilacji"). Są one dołączone do programu Visual Studio. Możesz również pobrać zestaw narzędzi jako pakiet autonomiczny bezpłatnie z [Narzędzia Build Tools for Visual Studio 2019](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019).

Można tworzyć proste programy, wywołując kompilator MSVC (CL. exe) bezpośrednio z wiersza polecenia. Następujące polecenie akceptuje pojedynczy plik kodu źródłowego i wywołuje CL. exe w celu utworzenia pliku wykonywalnego o nazwie *Hello. exe*:

```cmd
cl /EHsc hello.cpp
```

Należy zauważyć, że kompilator (CL. exe) automatycznie wywołuje C++ preprocesor i konsolidator, aby utworzyć końcowy plik wyjściowy.  Aby uzyskać więcej informacji, zobacz [Kompilowanie w wierszu polecenia](building-on-the-command-line.md).

## <a name="build-systems-and-projects"></a>Kompiluj systemy i projekty

Większość programów działających w świecie korzysta z pewnego rodzaju *systemu kompilacji* do zarządzania złożonością kompilowania wielu plików źródłowych w wielu konfiguracjach (tj. debugowanie i wydanie), wielu platform (x86, x64, ARM itd.), niestandardowych kroków kompilacji i nawet wielu plików wykonywalnych, które muszą być kompilowane w określonej kolejności. Należy wprowadzić ustawienia w plikach konfiguracji kompilacji, a system kompilacji akceptuje ten plik jako dane wejściowe przed wywołaniem kompilatora. Zestaw plików kodu źródłowego i pliki konfiguracji kompilacji wymagane do skompilowania pliku wykonywalnego nazywa się *projektem*.

Na poniższej liście przedstawiono różne opcje projektów programu Visual Studio C++:

- Utwórz projekt programu Visual Studio przy użyciu środowiska IDE programu Visual Studio i skonfiguruj go za pomocą stron właściwości. Projekty programu Visual Studio tworzą programy działające w systemie Windows. Aby zapoznać się z omówieniem, zobacz [Kompilowanie i kompilowanie](/visualstudio/ide/compiling-and-building-in-visual-studio) w dokumentacji programu Visual Studio.

- Otwórz folder, który zawiera plik CMakeLists. txt. Obsługa CMake jest zintegrowana z Visual Studio. IDE służy do edytowania, testowania i debugowania bez modyfikowania plików CMake w dowolny sposób. Dzięki temu można działać w tym samym projekcie CMake, co inne osoby, które mogą używać różnych edytorów. CMake to zalecane podejście do tworzenia aplikacji dla wielu platform. Aby uzyskać więcej informacji, zobacz [CMAKE projects](cmake-projects-in-visual-studio.md).

- Otwórz luźny folder plików źródłowych bez pliku projektu. Program Visual Studio będzie używać algorytmów heurystycznych do kompilowania plików. Jest to prosty sposób kompilowania i uruchamiania małych aplikacji konsolowych. Aby uzyskać więcej informacji, zobacz temat [Otwieranie projektów folderów](open-folder-projects-cpp.md).

- Otwórz folder zawierający pliki reguł programu make lub inny plik konfiguracyjny systemu kompilacji. Można skonfigurować program Visual Studio do wywoływania dowolnego polecenia kompilacji, dodając pliki JSON do folderu. Aby uzyskać więcej informacji, zobacz temat [Otwieranie projektów folderów](open-folder-projects-cpp.md).

- Otwórz plik reguł programu make systemu Windows w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [NMAKE Reference](reference/nmake-reference.md).

## <a name="msbuild-from-the-command-line"></a>MSBuild z wiersza polecenia

Można wywołać program MSBuild z poziomu wiersza polecenia, przechodząc do niego plik. vcxproj wraz z opcjami wiersza polecenia. Takie podejście wymaga dobrego poznania programu MSBuild i jest zalecane tylko wtedy, gdy jest to absolutnie konieczne. Aby uzyskać więcej informacji, zobacz [MSBuild](msbuild-visual-cpp.md).

## <a name="in-this-section"></a>W tej sekcji

[Projekty programu Visual Studio](creating-and-managing-visual-cpp-projects.md) Jak tworzyć, konfigurować i kompilować C++ projekty w programie Visual Studio przy użyciu natywnego systemu kompilacji (MSBuild).

[CMAKE projekty](cmake-projects-in-visual-studio.md) Jak zakodować, skompilować i wdrożyć projekty CMake w programie Visual Studio.

[Otwórz projekty folderu](open-folder-projects-cpp.md) Jak używać programu Visual Studio do wykonywania kodu, kompilowania C++ i wdrażania projektów na podstawie dowolnego systemu kompilacji lub bez systemu kompilacji. W ogóle.

[Kompilacje wydania](release-builds.md) Tworzenie i rozwiązywanie problemów z zoptymalizowanymi kompilacjami wydania dla użytkowników końcowych.

[Używanie zestawu narzędzi MSVC z poziomu wiersza polecenia](building-on-the-command-line.md)<br/>
W tym artykule omówiono sposób używania kompilatoraC++ C/i narzędzi do kompilowania bezpośrednio z wiersza polecenia zamiast używania środowiska IDE programu Visual Studio.

[Tworzenie bibliotek DLL w programie Visual Studio](dlls-in-visual-cpp.md) Jak tworzyć, debugować i wdrażać C/C++ dll (biblioteki udostępnione) w programie Visual Studio.

[Przewodnik: Tworzenie i używanie biblioteki statycznej](walkthrough-creating-and-using-a-static-library-cpp.md) Jak utworzyć plik binarny. lib.

[Kompilowanie aplikacjiC++ C/izolowanych i zestawów równoległych](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md) Opisuje model wdrażania aplikacji klasycznych systemu Windows, na podstawie koncepcji izolowanych aplikacji i zestawów równoległych.

[Konfigurowanie C++ projektów dla 64-bitowych, docelowych procesorów x64](configuring-programs-for-64-bit-visual-cpp.md) Jak kierować sprzętem 64-bitowym x64 za pomocą narzędzi kompilacji MSVC.

[Konfigurowanie C++ projektów dla procesorów ARM](configuring-programs-for-arm-processors-visual-cpp.md) Jak używać narzędzi kompilacji MSVC do kierowania sprzętu ARM.

[Optymalizowanie kodu](optimizing-your-code.md) Jak zoptymalizować swój kod na różne sposoby, w tym optymalizacje programu z przewodnikiem.

[Konfigurowanie programów dla systemu Windows XP](configuring-programs-for-windows-xp.md) Jak kierować system Windows XP przy użyciu narzędzi kompilacji MSVC.

[Dokumentacja kompilacji w języku C/C++](reference/c-cpp-building-reference.md)<br/>
Zawiera łącza do artykułów referencyjnych dotyczących tworzenia programów C++w programie, opcji kompilatora i konsolidatora oraz różnych narzędzi do kompilacji.
