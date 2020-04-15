---
title: Odwołanie do schematu CMakeSettings.json
ms.date: 11/22/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: f9c864b66df86165090b7d6d6fc9c4fc51d65a5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328894"
---
# <a name="cmakesettingsjson-schema-reference"></a>Odwołanie do schematu CMakeSettings.json

::: moniker range="vs-2015"

CMake projekty są obsługiwane w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

Plik **CMakeSettings.json** zawiera informacje używane przez program Visual Studio dla programu IntelliSense i tworzenie argumentów wiersza polecenia, które przekazuje do pliku cmake.exe dla określonego środowiska *konfiguracji* i kompilatora . *environment* Konfiguracja określa właściwości, które mają zastosowanie do określonej platformy `x86-Debug` `Linux-Release`i typu kompilacji, na przykład lub . Każda konfiguracja określa środowisko, które hermetyzuje informacje o zestawie narzędzi kompilatora, na przykład MSVC, GCC lub Clang. CMake używa argumentów wiersza polecenia do ponownego wygenerowania głównego pliku *CMakeCache.txt* i innych plików projektu dla projektu. Wartości można zastąpić w plikach *CMakeLists.txt.*

Można dodać lub usunąć konfiguracje w IDE, a następnie edytować je bezpośrednio w pliku JSON lub użyć **edytora ustawień CMake** (Visual Studio 2019 i nowsze). Można łatwo przełączać się między konfiguracjami w IDE do generowania różnych plików projektu. Aby uzyskać więcej [informacji, zobacz Dostosowywanie ustawień kompilacji CMake w programie Visual Studio.](customize-cmake-settings.md)

## <a name="configurations"></a>Konfiguracje

Tablica `configurations` zawiera wszystkie konfiguracje dla projektu CMake. Aby uzyskać więcej informacji na temat wstępnie zdefiniowanych konfiguracji, [zobacz CMake wstępnie zdefiniowane odwołanie do konfiguracji.](cmake-predefined-configuration-reference.md) Do pliku można dodać dowolną liczbę wstępnie zdefiniowanych lub niestandardowych konfiguracji.

A `configuration` ma następujące właściwości:

- `addressSanitizerEnabled`: `true` jeśli kompiluje program z Address Sanitizer (Experimental on Windows). W systemie Linux skompiluj z poziomem optymalizacji -fno-omit-frame-pointer i kompilatorem -Os lub -Oo, aby uzyskać najlepsze wyniki.
- `addressSanitizerRuntimeFlags`: flagi środowiska uruchomieniowego przekazywane do AddressSanitizer za pośrednictwem zmiennej środowiskowej ASAN_OPTIONS. Format: flag1=value:flag2=value2.
- `buildCommandArgs`: określa natywne przełączniki kompilacji przekazywane do CMake po --build --. Na przykład przekazywanie -v podczas korzystania z generatora Ninja zmusza Ninja do wyprowadzania linii poleceń. Zobacz [argumenty wiersza polecenia Ninja, aby](#ninja) uzyskać więcej informacji na temat poleceń Ninja.
- `buildRoot`: określa katalog, w którym CMake generuje skrypty kompilacji dla wybranego generatora.  Mapuje przełącznik **-DCMAKE_BINARY_DIR** i określa, gdzie zostanie utworzony *plik CMakeCache.txt.* Jeśli folder nie istnieje, zostanie utworzony. Obsługiwane makra `${workspaceRoot}`obejmują `${workspaceHash}` `${projectFile}`, `${projectDir}` `${thisFile}`, `${thisFileDir}` `${name}`, `${generator}` `${env.VARIABLE}`, , , , .
- `cacheGenerationCommand`: określa narzędzie wiersza polecenia i argumenty, na przykład *debugowanie gencache.bat* do generowania pamięci podręcznej. Polecenie jest uruchamiane z powłoki w określonym środowisku dla konfiguracji, gdy użytkownik jawnie żąda regeneracji lub plik CMakeLists.txt lub CMakeSettings.json zostanie zmodyfikowany.
- `cacheRoot`: określa ścieżkę do pamięci podręcznej CMake. Ten katalog powinien zawierać istniejący plik *CMakeCache.txt.*
- `clangTidyChecks`: oddzielona przecinkami lista ostrzeżeń, które zostaną przekazane do clang-tidy; symbole wieloznaczne są dozwolone, a prefiks "-" usunie czeki.
- `cmakeCommandArgs`: określa dodatkowe opcje wiersza polecenia przekazywane do CMake po wywołaniu w celu wygenerowania plików projektu.
- `cmakeToolchain`: określa plik o pęku narzędzi. To jest przekazywane do CMake za pomocą -DCMAKE_TOOLCHAIN_FILE."
- `codeAnalysisRuleset`: określa plan reguł, który ma być używany podczas uruchamiania analizy kodu. Może to być pełna ścieżka lub nazwa pliku pliku zawierającego reguły zainstalowanego przez program Visual Studio.
- `configurationType`: określa konfigurację typu kompilacji dla wybranego generatora. Może być jednym z:

  - Debugowanie
  - Release
  - MinSizeRel (MinSizeRel)
  - RelWithDebInfo
  
- `ctestCommandArgs`: określa dodatkowe opcje wiersza polecenia przekazywane do CTest podczas uruchamiania testów."
- `description`: opis tej konfiguracji, która pojawi się w menu.
- `enableClangTidyCodeAnalysis`: użyj Clang-Tidy do analizy kodu.
- `enableMicrosoftCodeAnalysis`: użyj narzędzi do analizy kodu firmy Microsoft do analizy kodu.
- `generator`: określa generator CMake do użycia w tej konfiguracji. Może być jednym z:
  
  **Tylko program Visual Studio 2019:**
  - Visual Studio 16 2019
  - Visual Studio 16 2019 Win64
  - Visual Studio 16 2019 ARM

  **Visual Studio 2017 i nowsze:**
  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - Pliki uniksowe
  - Ninja

Ponieważ Ninja jest przeznaczony do szybkiego budowania prędkości zamiast elastyczności i funkcji, jest ustawiony jako domyślny. Jednak niektóre projekty CMake mogą nie być w stanie poprawnie zbudować przy użyciu Ninja. W takim przypadku można poinstruować CMake do generowania projektów programu Visual Studio zamiast.

Aby określić generator programu Visual Studio w programie Visual Studio 2017, otwórz go z menu głównego, wybierając **CMake | Zmień ustawienia CMake**. Usuń "Ninja" i wpisz "V". To aktywuje IntelliSense, który pozwala wybrać generator, który chcesz.

Aby określić generator programu Visual Studio w programie Visual Studio 2019, kliknij prawym przyciskiem myszy plik *CMakeLists.txt* w **Eksploratorze rozwiązań** i wybierz pozycję **CMake Settings for project** > **Show Advanced Settings** > **CMake Generator**.

Gdy aktywna konfiguracja określa generator programu Visual Studio, domyślnie msBuild.exe jest wywoływany z `-m -v:minimal` argumentami. Aby dostosować kompilację, wewnątrz pliku *CMakeSettings.json* można określić dodatkowe [argumenty wiersza polecenia MSBuild,](../build/reference/msbuild-visual-cpp-overview.md) które mają być przekazywane do systemu kompilacji za pośrednictwem `buildCommandArgs` właściwości:

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `installRoot`: określa katalog, w którym CMake generuje cele instalacji dla wybranego generatora. Obsługiwane makra `${workspaceRoot}`obejmują `${workspaceHash}` `${projectFile}`, `${projectDir}` `${thisFile}`, `${thisFileDir}` `${name}`, `${generator}` `${env.VARIABLE}`, , , , .
- `inheritEnvironments`: określa co najmniej jedno środowisko kompilatora, od których zależy ta konfiguracja. Może to być dowolne środowisko niestandardowe lub jedno ze wstępnie zdefiniowanych środowisk. Aby uzyskać więcej informacji, zobacz [Środowiska](#environments).
- `intelliSenseMode`: określa tryb używany do obliczania informacji intellisense". Może być jednym z:

  - windows-msvc-x86
  - windows-msvc-x64
  - windows-msvc-ramię
  - windows-msvc-arm64
  - android-clang-x86
  - android-clang-x64
  - android-clang-arm
  - android-clang-arm64
  - ios-clang-x86
  - ios-clang-x64
  - ios-clang-ramię
  - ios-clang-arm64
  - windows-clang-x86
  - windows-clang-x64
  - windows-clang-arm
  - windows-clang-arm64
  - linux-gcc-x86
  - linux-gcc-x64
  - linux-gcc-arm"

- `name`: nazwy konfiguracji.  Aby uzyskać więcej informacji na temat wstępnie zdefiniowanych konfiguracji, [zobacz CMake wstępnie zdefiniowane odwołanie do konfiguracji.](cmake-predefined-configuration-reference.md)
- `wslPath`: ścieżka do uruchomienia instancji podsystemu Windows dla systemu Linux.

### <a name="additional-settings-for-cmake-linux-projects"></a>Dodatkowe ustawienia dla projektów CMake Linux

- `remoteMachineName`: określa nazwę zdalnego komputera z systemem Linux, na którym znajduje się CMake, kompilacje i debuger. Użyj Menedżera połączeń do dodawania nowych maszyn z systemem Linux. Obsługiwane makra `${defaultRemoteMachineName}`obejmują .
- `remoteCopySourcesOutputVerbosity`: określa poziom szczegółowości operacji kopiowania źródłowego na komputerze zdalnym. Może być jednym z ""Normalny", "Pełny" lub "Diagnostyczny".
- `remoteCopySourcesConcurrentCopies`: określa liczbę równoczesnych kopii używanych podczas synchronizacji źródeł z komputerem zdalnym (tylko sftp).
- `remoteCopySourcesMethod`: określa metodę kopiowania plików na komputer zdalny. Może to być "rsync" lub "sftp".
- `remoteCMakeListsRoot`: określa katalog na komputerze zdalnym, który zawiera projekt CMake. Obsługiwane makra `${workspaceRoot}`obejmują `${workspaceHash}` `${projectFile}`, `${projectDir}` `${thisFile}`, `${thisFileDir}` `${name}`, `${generator}` `${env.VARIABLE}`, , , , .
- `remoteBuildRoot`: określa katalog na komputerze zdalnym, w którym CMake generuje skrypty kompilacji dla wybranego generatora. Obsługiwane makra `${workspaceRoot}`obejmują `${workspaceHash}` `${projectFile}`, `${projectDir}` `${thisFile}`, `${thisFileDir}` `${name}`, `${generator}` `${env.VARIABLE}`, , , , .
- `remoteInstallRoot`: określa katalog na komputerze zdalnym, w którym CMake generuje cele instalacji dla wybranego generatora. Obsługiwane makra `${workspaceRoot}`obejmują `${workspaceHash}` `${projectFile}`, `${projectDir}` `${thisFile}`, `${thisFileDir}` `${name}`, `${generator}`, `${env.VARIABLE}` `VARIABLE` , , i gdzie jest zmienna środowiskowa, która została zdefiniowana na poziomie systemu, użytkownika lub sesji.
- `remoteCopySources`: `boolean` A, który określa, czy visual studio należy skopiować pliki źródłowe na komputerze zdalnym. Wartość domyślna jest true. Ustaw wartość false, jeśli samodzielnie zarządzasz synchronizacją plików.
- `remoteCopyBuildOutput`: `boolean` A, który określa, czy chcesz skopiować dane wyjściowe kompilacji z systemu zdalnego.
- `remoteCopyAdditionalIncludeDirectories`: Dodatkowe katalogi dołączane do skopiowania z komputera zdalnego w celu obsługi technologii IntelliSense. Formatuj jako "/path1;/path2...".
- `remoteCopyExcludeDirectories`: Dołącz katalogi NOT do kopiowania z komputera zdalnego. Formatuj jako "/path1;/path2...".
- `remoteCopyUseCompilerDefaults`: Określa, czy kompilator ma używać domyślnychdefinicji i dołączania ścieżek dla intellisense. Powinny być false tylko wtedy, gdy kompilatory w użyciu, aby nie obsługiwać argumenty stylu gcc.
- `rsyncCommandArgs`: określa zestaw dodatkowych opcji wiersza polecenia przekazanych do rsync.
- `remoteCopySourcesExclusionList`: `array` A, który określa listę ścieżek, które mają być wykluczone podczas kopiowania plików źródłowych:ścieżka może być nazwą pliku/katalogu lub ścieżką względem katalogu głównego kopii. Symbole \\ \" * \\ \" wieloznaczne i \\ \"? \\ może być używany do dopasowywania wzorów \" glob.
- `cmakeExecutable`: określa pełną ścieżkę do pliku wykonywalnego programu CMake, w tym nazwę pliku i rozszerzenie.
- `remotePreGenerateCommand`: określa polecenie do uruchomienia przed uruchomieniem CMake do analizy pliku *CMakeLists.txt.*
- `remotePrebuildCommand`: określa polecenie do uruchomienia na komputerze zdalnym przed budynkiem.
- `remotePostbuildCommand`: określa polecenie do uruchomienia na komputerze zdalnym po zbudowaniu.
- `variables`: zawiera parę nazwa-wartość zmiennych CMake, które zostaną przekazane jako wartość * _-D name_=* do CMake. **-D** Jeśli instrukcje kompilacji projektu CMake określić dodanie wszelkich zmiennych bezpośrednio do pliku *CMakeCache.txt,* zaleca się, aby dodać je tutaj zamiast. W poniższym przykładzie pokazano, jak określić pary nazwa-wartość dla zestawu narzędzi MSVC 14.14.26428:

```json
"variables": [
    {
      "name": "CMAKE_CXX_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe",
      "type": "FILEPATH"
    },
    {
      "name": "CMAKE_C_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe",
      "type": "FILEPATH"
    }
  ]
```

Należy zauważyć, że jeśli `"type"`nie `"STRING"` zdefiniujesz , typ zostanie przyjęty domyślnie.

- `remoteCopyOptimizations`: **Właściwości programu Visual Studio 2019 w wersji 16.5 lub nowszej** w celu kontrolowania kopii źródłowej do zdalnego obiektu docelowego. Optymalizacje są domyślnie włączone. Zawiera `remoteCopyUseOptimizations` `rsyncSingleDirectoryCommandArgs`, `remoteCopySourcesMaxSmallChange`i .

## <a name="environments"></a><a name="environments"></a>Środowiskach

*Środowisko* hermetyzuje zmienne środowiskowe, które są ustawione w procesie używanym przez program Visual Studio do wywoływania pliku cmake.exe. W przypadku projektów MSVC zmienne są te, które są ustawione w [wierszu polecenia dewelopera](building-on-the-command-line.md) dla określonej platformy. Na przykład `msvc_x64_x64` środowisko jest takie samo jak **uruchamianie wiersza polecenia dewelopera dla programu VS 2017** lub **wiersza polecenia dewelopera dla programu VS 2019** z argumentami **-arch=amd64 -host_arch=amd64.** Można użyć `env.{<variable_name>}` składni w *CMakeSettings.json* do odwoływania się do poszczególnych zmiennych środowiskowych, na przykład do konstruowania ścieżek do folderów.  Dostępne są następujące wstępnie zdefiniowane środowiska:

- linux_arm: Zdalnie kierować system ARM Linux.
- linux_x64: Zdalnie kierować x64 Linux.
- linux_x86: Zdalnie kierować x86 Linux.
- msvc_arm: Docelowy system ARM Windows z kompilatorem MSVC.
- msvc_arm_x64: Docelowy system ARM Windows z 64-bitowym kompilatorem MSVC.
- msvc_arm64: Docelowy system ARM64 Windows z kompilatorem MSVC.
- msvc_arm64_x64: Docelowy system ARM64 Windows z 64-bitowym kompilatorem MSVC.
- msvc_x64: Docelowy system Windows x64 z kompilatorem MSVC.
- msvc_x64_x64: Docelowy system Windows x64 z 64-bitowym kompilatorem MSVC.
- msvc_x86: Docelowy system x86 Windows z kompilatorem MSVC.
- msvc_x86_x64: Docelowy system x86 Windows z 64-bitowym kompilatorem MSVC.

### <a name="accessing-environment-variables-from-cmakeliststxt"></a>Uzyskiwanie dostępu do zmiennych środowiskowych z pliku CMakeLists.txt

Z pliku CMakeLists.txt wszystkie zmienne środowiskowe są przywołyty przez składnię `$ENV{variable_name}`. Aby wyświetlić dostępne zmienne dla środowiska, otwórz `SET`odpowiedni wiersz polecenia i wpisz . Niektóre informacje w zmiennych środowiskowych jest również dostępny za pośrednictwem CMake zmiennych introspekcji systemu, ale może okazać się bardziej wygodne do korzystania ze zmiennej środowiskowej. Na przykład wersja kompilatora MSVC lub wersja zestawu Windows SDK są łatwo pobierane za pośrednictwem zmiennych środowiskowych.

### <a name="custom-environment-variables"></a>Niestandardowe zmienne środowiskowe

W `CMakeSettings.json`programie można definiować niestandardowe zmienne `environments` środowiskowe globalnie lub na konfigurację w tablicy. Środowisko niestandardowe to wygodny sposób grupowanie zestawu właściwości, których można używać zamiast wstępnie zdefiniowanego środowiska, lub rozszerzanie lub modyfikowanie wstępnie zdefiniowanego środowiska. Każdy element `environments` w tablicy składa się z:

- `namespace`: nazywa środowisko tak, aby jego zmienne mogły się `namespace.variable`odwoływać z konfiguracji w formularzu . Wywoływany `env` jest domyślny obiekt środowiska i jest `%USERPROFILE%`wypełniany określonymi zmiennymi środowiska systemowego, w tym .
- `environment`: jednoznacznie identyfikuje tę grupę zmiennych. Umożliwia dziedziczenie grupy w późniejszym `inheritEnvironments` miejscu wpisu.
- `groupPriority`: Liczba całkowita określająca priorytet tych zmiennych podczas ich oceny. Najpierw oceniane są wyższe pozycje liczbowe.
- `inheritEnvironments`: Tablica wartości określających zestaw środowisk, które są dziedziczone przez tę grupę. Ta funkcja umożliwia dziedziczenie środowisk domyślnych i tworzenie niestandardowych zmiennych środowiskowych, które są przekazywane do CMake.exe po uruchomieniu.

**Visual Studio 2019 w wersji 16.4 i nowszej:** Obiekty docelowe debugowania są uruchamiane automatycznie w środowisku określonym w *pliku CMakeSettings.json*. Zmienne środowiskowe dla obiektu docelowego lub dla zadań można zastąpić lub dodać w zależności od celu lub zadania w pliku [launch.vs.json](launch-vs-schema-reference-cpp.md) i [tasks.vs.json](tasks-vs-json-schema-reference-cpp.md).

Poniższy przykład definiuje jedną zmienną **globalną, BuildDir**, która jest dziedziczona w konfiguracjach debugowania x86 i x64-Debug. Każda konfiguracja używa zmiennej, aby określić wartość właściwości **buildRoot** dla tej konfiguracji. Należy również zauważyć, jak każda konfiguracja używa **inheritEnvironments** właściwość, aby określić zmienną, która ma zastosowanie tylko do tej konfiguracji.

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x86 compiler.
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.BuildDir}\\${name}"    },
    {
      "name": "x64-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x64 compiler.
      "inheritEnvironments": [ "msvc_x64" ],
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

W następnym przykładzie konfiguracja debugowania x86 definiuje własną wartość właściwości **BuildDir.** Ta wartość zastępuje wartość ustawioną przez globalną właściwość **BuildDir,** dzięki czemu **funkcja BuildRoot** jest oceniana na `D:\custom-builddir\x86-Debug`wartość .

```json
{
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",

      // The syntax for this property is the same as the global one above.
      "environments": [
        {
          // Replace the global property entirely.
          "BuildDir": "D:\\custom-builddir"
          // This environment does not specify a namespace, hence by default "env" will be assumed.
          // "namespace" : "name" would require that this variable be referenced with "${name.BuildDir}".
        }
      ],

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      // Evaluates to "D:\custom-builddir\x86-Debug"
      "buildRoot": "${env.BuildDir}\\${name}"
    },
    {
      "name": "x64-Debug",

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x64" ],
      // Since this configuration doesn't modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="macros"></a>Makra

W *pliku CMakeSettings.json*można użyć następujących makr:

- `${workspaceRoot}`– pełna ścieżka folderu obszaru roboczego
- `${workspaceHash}`– skrót lokalizacji obszaru roboczego; przydatne do tworzenia unikatowego identyfikatora dla bieżącego obszaru roboczego (na przykład do użycia w ścieżkach folderów)
- `${projectFile}`– pełna ścieżka głównego pliku CMakeLists.txt
- `${projectDir}`– pełna ścieżka folderu głównego pliku CMakeLists.txt
- `${thisFile}`– pełna ścieżka `CMakeSettings.json` pliku
- `${name}`– nazwa konfiguracji
- `${generator}`– nazwa generatora CMake użytego w tej konfiguracji

Wszystkie odwołania do makr i zmiennych środowiskowych w *pliku CMakeSettings.json* są rozszerzane przed przekazaniem ich do wiersza polecenia cmake.exe.

## <a name="ninja-command-line-arguments"></a><a name="ninja"></a>Argumenty wiersza polecenia Ninja

Jeśli obiekty docelowe są nieokreślone, tworzy "domyślny" cel.

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|Opcja|Opis|
|--------------|------------|
| --wersja  | wersja drukowana ninja ("1.7.1")|
|   -C DIR   | zmienić DIR przed zrobieniem czegokolwiek innego|
|   -f PLIK  | określ wejściowy plik kompilacji (default=build.ninja)|
|   -j N     | uruchamianie zadań N równolegle (domyślnie=14, pochodzące z dostępnych procesorów)|
|   -k N     | kontynuuj pracę, dopóki zadania N nie powiodą się (domyślnie=1)|
|   -l N     | nie uruchamiaj nowych zadań, jeśli średnia obciążenia jest większa niż N|
|   -n       | dry run (nie uruchamiaj poleceń, ale działaj tak, jak się udało)|
|   -v       | pokaż wszystkie wiersze polecenia podczas budowania|
|   -d TRYB  | włącz debugowanie (użyj listy -d do listy trybów)|
|   -t NARZĘDZIE  | uruchom podwładne (użyj listy -t, aby wyświetlić listę podwładnych). kończy opcje najwyższego poziomu; kolejne flagi są przekazywane do narzędzia|
|   -w FLAGA  | dopasowywanie ostrzeżeń (użyj listy -w, aby wyświetlić listę ostrzeżeń)|

::: moniker-end
