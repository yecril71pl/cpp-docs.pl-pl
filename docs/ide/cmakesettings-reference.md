---
title: Odwołanie do schematu pliku CMakeSettings.json
ms.date: 03/05/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: d80829b1475e8718e1c4188ff4fb7d42a1d4b3b9
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/07/2019
ms.locfileid: "57566890"
---
# <a name="cmakesettingsjson-schema-reference"></a>Odwołanie do schematu pliku CMakeSettings.json

`cmakesettings.json` Plik zawiera informacje określające, jak Visual Studio powinny wchodzić w interakcje za pomocą narzędzia CMake w celu utworzenia projektu dla określonej platformy. Użyj tego pliku do przechowywania informacji takich jak zmienne środowiskowe lub argumentów dla środowiska cmake.exe.

## <a name="environments"></a>Środowiska

`environments` Tablica zawiera listę `items` typu `object` definiującą "environment". Środowiska mogą służyć do zastosowania zestawem używanych zmiennych `configuration`. Każdy element na `environments` składa się tablicy:

- `namespace`: zmienne mogą być przywoływane z konfiguracją w postaci nazwy środowiska `namespace.variable`. Domyślny obiekt środowisku jest nazywany `env` i jest wypełniana przy użyciu pewne zmienne środowiskowe systemu, w tym `%USERPROFILE%`.
- `environment`: unikatowo identyfikuje tej grupy zmiennych. Umożliwia grupie dziedziczenie później w `inheritEnvironments` wpisu.
- `groupPriority`: Liczba całkowita określająca priorytet tych zmiennych podczas ich obliczania. Ustawienie większej liczby elementy są obliczane jako pierwsze.
- `inheritEnvironments`: Tablica wartości, które określają zestaw środowisk, które są dziedziczone przez tę grupę. Można użyć dowolnego środowiska niestandardowego lub następujących wstępnie zdefiniowanych środowisk:
 
  - linux_arm: Celem ARM Linux zdalnie.
  - linux_x64: Wyceluj x64 Linux zdalnie.
  - linux_x86: Wyceluj x86 Linux zdalnie.
  - msvc_arm: Docelowy ARM Windows za pomocą kompilatora MSVC.
  - msvc_arm_x64: Docelowy ARM Windows za pomocą 64-bitowego kompilatora MSVC.
  - msvc_arm64: Docelowy ARM64 Windows za pomocą kompilatora MSVC.
  - msvc_arm64_x64: Docelowy ARM64 Windows za pomocą 64-bitowego kompilatora MSVC.
  - msvc_x64: Docelowy x64 Windows za pomocą kompilatora MSVC.
  - msvc_x64_x64: Docelowy x64 Windows za pomocą 64-bitowego kompilatora MSVC.
  - msvc_x86: Docelowy x86 Windows za pomocą kompilatora MSVC.
  - msvc_x86_x64: Docelowy x86 Windows za pomocą 64-bitowego kompilatora MSVC.

## <a name="configurations"></a>Konfiguracje

`configurations` Tablicy składa się z obiektami, które reprezentują konfiguracji narzędzia CMake dotyczących pliku CMakeLists.txt w tym samym folderze. Te obiekty można użyć do definiowania wielu konfiguracjach kompilacji i łatwo przełączać się między nimi w środowisku IDE. 

Element `configuration` ma następujące właściwości:
- `name`: nazwy konfiguracji.
- `description`: opis tej konfiguracji, który będzie wyświetlany w menu.
- `generator`: Określa generatora CMake do użycia dla tej konfiguracji. Może to być jeden z:

  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - UNIX pliki reguł programu make
  - Ninja

- `configurationType`: Określa konfigurację typu kompilacji dla wybranego generatora. Może to być jeden z:
 
  - Debugowanie
  - Wydanie
  - MinSizeRel
  - RelWithDebInfo
 
- `inheritEnvironments`: Określa jedną lub więcej środowisk, od których zależy ta konfiguracja. Może być dowolnego środowiska niestandardowego lub jedno z tych wstępnie zdefiniowanych środowisk.
- `buildRoot`: specifiesThe katalogu, w którym narzędzie CMake generuje kompilacji skrypty dla wybranego generatora. Obsługiwane makra to: `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`. "
- `installRoot`: Określa katalog, w którym narzędzie CMake generuje elementy docelowe instalacji, dla wybranego generatora. Obsługiwane makra to: `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`. "
- `cmakeCommandArgs`: Określa dodatkowe opcje wiersza polecenia przekazywane do narzędzia CMake po wywołaniu do generowania pamięci podręcznej. "
- `cmakeToolchain`: Określa plik łańcucha narzędzi. Te informacje są przekazywane do narzędzia CMake za pomocą parametru-DCMAKE_TOOLCHAIN_FILE. "
- `buildCommandArgs`: Określa przełączniki kompilacji natywnej przekazywane do narzędzia CMake po--build--. "
- `ctestCommandArgs`: Określa dodatkowe opcje wiersza polecenia przekazywane do narzędzia CTest podczas uruchamiania testów. "
- `codeAnalysisRuleset`: Określa zestaw reguł do użycia podczas przeprowadzania analizy kodu. Może to być pełną ścieżką lub nazwą pliku zestawu reguł zainstalowanego przez program Visual Studio."
- `intelliSenseMode`: Określa tryb używany do przetwarzania informacji intellisense ". Może to być jeden z:
 
  - windows-msvc-x86
  - windows-msvc-x64
  - windows-msvc-arm
  - windows-msvc-arm64
  - android-clang-x86
  - android-clang-x64
  - android-clang-arm
  - android-clang-arm64
  - ios-clang-x86
  - ios-clang-x64
  - ios-clang-arm
  - ios-clang-arm64
  - windows-clang-x86
  - windows-clang-x64
  - windows-clang-arm
  - windows-clang-arm64
  - linux-gcc-x86
  - linux-gcc-x64
  - linux-gcc-arm"

- `cacheRoot`: Określa ścieżkę do pamięci podręcznej narzędzia CMake. Ten katalog powinien zawierać istniejący plik CMakeCache.txt.
- `remoteMachineName`: Określa nazwę komputera zdalnego systemu Linux, który hostuje narzędzie CMake, kompilacje i debugera. Korzystanie z Menedżera połączeń, aby dodać nowe maszyny z systemem Linux. Obsługiwane makra to: `${defaultRemoteMachineName}`.
- `remoteCopySourcesOutputVerbosity`: Określa poziom szczegółowości dla operacji kopiowania komputera zdalnego źródła. Może być jedną z "" Normal","Pełne"lub"Diagnostyczne".
- `remoteCopySourcesConcurrentCopies`: Określa liczbę równoczesnych operacji kopiowania używanych podczas synchronizowania źródeł na maszynie zdalnej.
- `remoteCopySourcesMethod`: Określa metodę, aby skopiować pliki do maszyny zdalnej. Może to być "rsync" lub "sftp".
- `remoteCMakeListsRoot`: Określa katalog na maszynie zdalnej zawierający projekt narzędzia CMake. Obsługiwane makra to: `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `remoteBuildRoot`: Określa katalog na komputerze zdalnym, w którym narzędzie CMake generuje skrypty kompilacji dla wybranego generatora. Obsługiwane makra to: `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `remoteInstallRoot`: Określa katalog na komputerze zdalnym, w którym narzędzie CMake generuje elementy docelowe instalacji, dla wybranego generatora. Obsługiwane makra to: `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, i `${env.VARIABLE}` gdzie `VARIABLE` jest zmienną środowiskową, która ma została zdefiniowana na poziomie systemu, użytkownika lub sesję.
- `remoteCopySources`: A `boolean` określająca, czy program Visual Studio należy skopiować pliki źródłowe do maszyny zdalnej. Wartość domyślna to true. Ustawienie wartości false, jeśli zarządzasz synchronizacją plików samodzielnie.
- `remoteCopyBuildOutput`: A `boolean` określająca, czy mają być kopiowane dane wyjściowe kompilacji z systemu zdalnego.
- `rsyncCommandArgs`: Określa zestaw dodatkowych opcji wiersza polecenia przekazywane do polecenia rsync.
- `remoteCopySourcesExclusionList`: Element `array` , który określa listy ścieżek, które mają być wykluczone podczas kopiowania plików źródłowych: ścieżka może być nazwa pliku lub katalogu lub ścieżka względem katalogu głównego kopii. Symbole wieloznaczne \\ \" * \\ \" i \\ \"?\\ \" może służyć do globalizowania dopasowywania do wzorca.
- `cmakeExecutable`: Określa pełną ścieżkę do pliku wykonywalnego programu CMake, w tym nazwę pliku i rozszerzenie.
- `remotePreGenerateCommand`: Określa polecenie do uruchomienia przed uruchomieniem narzędzia CMake można przeanalizować pliku CMakeLists.txt.
- `remotePrebuildCommand`: Określa polecenie do uruchomienia na maszynie zdalnej przed kompilacją.
- `remotePostbuildCommand`: Określa polecenie do uruchomienia na maszynie zdalnej po kompilacji.
- `variables`: Element `array` , który określa zmienne, które są przekazywane do narzędzia CMake w postaci - dnazwa1 = wartość1-dnazwa2 = wartość2 itd. 


