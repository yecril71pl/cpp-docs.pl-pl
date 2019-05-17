---
title: Odwołanie do schematu pliku CMakeSettings.json
ms.date: 05/16/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 018a755aa4f3acde44fe1dbb33b07b49c8d1c223
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837255"
---
# <a name="cmakesettingsjson-schema-reference"></a>Odwołanie do schematu pliku CMakeSettings.json

**Cmakesettings.json**"plik zawiera informacje określające, jak Visual Studio powinny wchodzić w interakcje za pomocą narzędzia CMake w celu utworzenia projektu dla określonej platformy. Plik przechowuje informacje takie jak zmienne środowiskowe lub argumentów dla środowiska cmake.exe. Można edytować bezpośrednio lub użyć **edytora ustawienia narzędzia CMake** (Visual Studio 2019 i nowsze). Zobacz [ustawień w programie Visual Studio kompilacji CMake dostosować](customize-cmake-settings.md) Aby uzyskać więcej informacji na temat edytora.

## <a name="environments"></a>Środowiska

`environments` Tablica zawiera listę `items` typu `object` definiującą zestaw narzędzi kompilatora "environment". Środowiska mogą służyć do zastosowania zestawem używanych zmiennych `configuration`. Każdy element na `environments` składa się tablicy:

- `namespace`: zmienne mogą być przywoływane z konfiguracją w postaci nazwy środowiska `namespace.variable`. Domyślny obiekt środowisku jest nazywany `env` i jest wypełniana przy użyciu pewne zmienne środowiskowe systemu, w tym `%USERPROFILE%`.
- `environment`: unikatowo identyfikuje tej grupy zmiennych. Umożliwia grupie dziedziczenie później w `inheritEnvironments` wpisu.
- `groupPriority`: Liczba całkowita określająca priorytet tych zmiennych podczas ich obliczania. Ustawienie większej liczby elementy są obliczane jako pierwsze.
- `inheritEnvironments`: Tablica wartości, które określają zestaw środowisk, które są dziedziczone przez tę grupę. Ta funkcja umożliwia dziedziczą środowiska domyślnego i utworzyć niestandardowe zmienne środowiskowe, które są przekazywane do CMake.exe po jego uruchomieniu.

   ```json
   "inheritEnvironments": [ "msvc_x64_x64" ]
   ```

   W powyższym przykładzie jest taka sama jak działa **wiersz polecenia programisty dla programu VS 2017** lub **wiersz polecenia programisty dla programu VS 2019** z **-arch = amd64-host_arch = amd64** argumenty. Można użyć dowolnego środowiska niestandardowego lub następujących wstępnie zdefiniowanych środowisk:
 
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
  
  **Visual Studio 2019 r tylko:**
  - Visual Studio 16 2019
  - Visual Studio 16 2019 Win64
  - Visual Studio 16 2019 ARM

  **Visual Studio 2017 i nowszym:**
  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - UNIX pliki reguł programu make
  - Ninja

Ponieważ Ninja jest przeznaczona dla szybkości szybkie kompilacji zamiast elastyczności i funkcji, jest ustawiona jako domyślna. Jednak niektóre projekty narzędzia CMake, może być nie można poprawnie tworzyć zawartość przy użyciu Ninja. W takiej sytuacji można nakazać narzędzia CMake w celu wygenerowania projektu programu Visual Studio, zamiast tego.

Aby określić generator programu Visual Studio w programie Visual Studio 2017, otwórz `CMakeSettings.json` z menu głównego, wybierając **CMake | Zmień ustawienia narzędzia CMake**. Usuń "Ninja", a następnie wpisz "V". Aktywuje funkcję IntelliSense, która pozwala na dokonanie wyboru generator, który ma.

Aby określić generator programu Visual Studio w Visual Studio 2019 r, kliknij prawym przyciskiem myszy pliku CMakeLists.txt w **Eksploratora rozwiązań** i wybierz polecenie **ustawienia narzędzia CMake dla projektu** > **Pokaż Zaawansowane ustawienia** > **generatora CMake**.

Podczas aktywnej konfiguracji określa generator programu Visual Studio, domyślnie MSBuild.exe jest wywoływana z `-m -v:minimal` argumentów. Dostosowywanie kompilacji, wewnątrz `CMakeSettings.json` plików, można określić dodatkowe [argumenty wiersza polecenia programu MSBuild](../build/reference/msbuild-visual-cpp-overview.md) mają być przekazane do systemu kompilacji, za pośrednictwem `buildCommandArgs` właściwości:

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `configurationType`: Określa konfigurację typu kompilacji dla wybranego generatora. Może to być jeden z:
 
  - Debugowanie
  - Wydanie
  - MinSizeRel
  - RelWithDebInfo
 
- `inheritEnvironments`: Określa jedną lub więcej środowiska kompilatora, od których zależy ta konfiguracja. Może być dowolnego środowiska niestandardowego lub jedno z tych wstępnie zdefiniowanych środowisk.
- `buildRoot`: Określa katalog, w którym narzędzie CMake generuje skrypty kompilacji dla wybranego generatora.  Mapuje **-DCMAKE_BINARY_DIR** Przełącz i określa, w którym zostanie utworzona pamięci podręcznej narzędzia CMake. Jeśli folder nie istnieje, zostanie utworzony. Obsługiwane makra to: `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `installRoot`: Określa katalog, w którym narzędzie CMake generuje elementy docelowe instalacji, dla wybranego generatora. Obsługiwane makra to: `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `cmakeCommandArgs`: Określa dodatkowe opcje wiersza polecenia przekazywane do narzędzia CMake po wywołaniu do generowania pamięci podręcznej.
- `cmakeToolchain`: Określa plik łańcucha narzędzi. Te informacje są przekazywane do narzędzia CMake za pomocą parametru-DCMAKE_TOOLCHAIN_FILE. "
- `buildCommandArgs`: Określa przełączniki kompilacji natywnej przekazywane do narzędzia CMake po--build--. Na przykład przekazując - v, gdy przy użyciu generatora Ninja wymusza Ninja w danych wyjściowych wiersze polecenia. Zobacz [argumenty wiersza polecenia Ninja](#ninja) Aby uzyskać więcej informacji na temat Ninja poleceń.
- `ctestCommandArgs`: Określa dodatkowe opcje wiersza polecenia przekazywane do narzędzia CTest podczas uruchamiania testów. "
- `codeAnalysisRuleset`: Określa zestaw reguł do użycia podczas przeprowadzania analizy kodu. Może to być pełną ścieżką lub nazwą pliku zestawu reguł zainstalowanego przez program Visual Studio.
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

### <a name="additional-settings-for-cmake-linux-projects"></a>Dodatkowe ustawienia dla projektów CMake systemu Linux. 

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
- `variables`: zawiera pary nazwa wartość, zmienne narzędzia CMake, które będą przekazywane jako **-D** *_nazwa_=_wartość_* do narzędzia CMake. Instrukcje kompilacji projektu narzędzia CMake określić dodanie wszelkie zmienne bezpośrednio do pliku pamięci podręcznej narzędzia CMake, zaleca się dodanie ich w tym miejscu zamiast tego. Poniższy przykład pokazuje, jak określić pary nazwa wartość dla 14.14.26428 zestaw narzędzi MSVC:

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

Należy pamiętać, że jeżeli nie zdefiniujesz `"type"`, zostanie przyjęta wartość domyślna typu "STRING".

## <a name="environment-variables"></a>Zmienne środowiskowe

`CMakeSettings.json` obsługuje również konsumencki zmiennych środowiskowych w jednym z jego właściwości w wymienionych powyżej. Składnia służąca do użycia jest `${env.FOO}` rozwinąć zmiennej środowiskowej % FOO %.

Masz także dostęp do wbudowanych makr, w tym pliku:

- `${workspaceRoot}` — zapewnia pełną ścieżkę folderu obszaru roboczego
- `${workspaceHash}` — Skrót lokalizacji obszaru roboczego. przydatne podczas tworzenia Unikatowy identyfikator dla bieżącego obszaru roboczego (na przykład do użycia w ścieżkach folderów)
- `${projectFile}` — Pełna ścieżka pliku CMakeLists.txt głównego
- `${projectDir}` — Pełna ścieżka do folderu głównego pliku CMakeLists.txt
- `${thisFile}` — Pełna ścieżka `CMakeSettings.json` pliku
- `${name}` — Nazwa konfiguracji
- `${generator}` — Nazwa generatora narzędzia CMake, używany w tej konfiguracji


### <a name="custom-environment-variables"></a>Niestandardowe zmienne środowiskowe

W `CMakeSettings.json`, niestandardowe zmienne środowiskowe można zdefiniować globalnie lub na konfiguracji w **środowisk** właściwości. W poniższym przykładzie zdefiniowano jednej zmiennej globalnej, **BuildDir**, która jest dziedziczona przez konfiguracje debugowania x86 i x64 debugowania. Każda konfiguracja używa zmiennej, aby określić wartość dla **wybrany element buildRoot** właściwości dla tej konfiguracji. Należy zauważyć, jak korzysta z konfiguracjami **inheritEnvironments** właściwość, aby określić zmienną, która ma zastosowanie tylko do tej konfiguracji.

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

W następnym przykładzie konfiguracja debugowania x86 definiuje wartość dla **BuildDir** właściwości. Ta wartość zastępuje wartość ustawioną przy użyciu globalnego **BuildDir** właściwość tak, aby **wybrany element BuildRoot** daje w wyniku `D:\custom-builddir\x86-Debug`.

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
      // Since this configuration doesn’t modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="ninja"></a> Ninja argumenty wiersza polecenia

W przypadku nieokreślonego obiekty docelowe kompilacji docelowej "default".

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|Opcja|Opis|
|--------------|------------|
| --version  | Drukuj ninja wersji ("1.7.1")|
|   -C DIR   | Zmień na katalog, przed wykonaniem jakichkolwiek innych czynności|
|   -f pliku  | Określ plik wejściowy kompilacji (default=build.ninja)|
|   -j N     | równoległe wykonywanie zadań N (domyślny = 14, pochodzące z procesorów dostępnych)|
|   -k N     | Kontynuuj, dopóki N zadanie zakończy się niepowodzeniem (domyślny = 1)|
|   -l N     | Nie uruchamiaj nowe zadania, jeśli średnia obciążenia jest większa niż N|
|   -n       | Wysuszyć Uruchom (nie uruchamiać polecenia, ale działają tak, jak one powiodło się)|
|   -v       | Pokaż wszystkie wiersze polecenia podczas tworzenia|
|   -d tryb  | Włącz debugowanie (tryby listy do użycia -d)|
|   t - narzędzie  | Uruchom subtool (Użyj -t listy do narzędzi niższego poziomu). kończy najwyższego poziomu opcje; Dodatkowo flagi są przekazywane do narzędzia|
|   -w flagi  | Dostosuj ostrzeżenia (Użyj -w listy do ostrzeżenia)|




