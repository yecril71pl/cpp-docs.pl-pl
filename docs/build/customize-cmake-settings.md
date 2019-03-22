---
title: Dostosowywanie ustawień kompilacji CMake w programie Visual Studio
ms.date: 03/05/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: dd34fbefcbc89c7c4aa93105ae5bad31ae4d5f01
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328301"
---
# <a name="customize-cmake-build-settings"></a>Dostosowywanie ustawień kompilacji CMake

Visual Studio zawiera kilka konfiguracji narzędzia CMake, które definiują, jak CMake.exe jest wywoływana w celu utworzenia pamięci podręcznej narzędzia CMake dla danego projektu. Aby dodać nową konfigurację, kliknij pozycję Konfiguracja, z listy rozwijanej na pasku narzędzi, a następnie wybierz **Zarządzanie konfiguracjami**:

   ![Narzędzie CMake Zarządzanie konfiguracjami](media/cmake-manage-configurations.png)

Można wybrać z listy wstępnie zdefiniowanych konfiguracji:

   ![Narzędzie CMake wstępnie zdefiniowane konfiguracje](media/cmake-configurations.png)

Po raz pierwszy, wybierz konfigurację, program Visual Studio tworzy `CMakeSettings.json` pliku w folderze głównym projektu. Ten plik jest używany ponowne tworzenie pliku pamięci podręcznej narzędzia CMake, na przykład po **czysty** operacji. 

Aby dodać dodatkową konfigurację, kliknij prawym przyciskiem myszy `CMakeSettings.json` i wybierz polecenie **Dodawanie konfiguracji**. 

   ![Dodawanie CMake konfiguracji](media/cmake-add-configuration.png "Dodawanie konfiguracji narzędzia CMake")

JSON technologia IntelliSense pomaga edytować `CMakeSettings.json` pliku:

   ![IntelliSense CMake JSON](media/cmake-json-intellisense.png "IntelliSense JSON narzędzia CMake")

Można również edytować plik przy użyciu **edytora ustawienia narzędzia CMake**. Kliknij prawym przyciskiem myszy `CMakeSettings.json` w **Eksploratora rozwiązań** i wybierz polecenie **Edytuj ustawienia narzędzia CMake**. Lub wybierz **Zarządzanie konfiguracjami** z konfiguracji listy rozwijanej w górnej części okna edytora. 

Można także bezpośrednio edytować `CMakeSettings.json` pokazuje Przykładowa konfiguracja, którego można użyć jako punktu wyjścia, aby utworzyć niestandardowe konfiguracje w poniższym przykładzie:

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },

```

- **Nazwa**: Nazwa wyświetlana na liście rozwijanej konfiguracji C++. `${name}` Makra pozwala na użycie tej wartości podczas redagowania wartości innych właściwości, takich jak ścieżki. Aby uzyskać przykład, zobacz **wybrany element buildRoot** definicji w `CMakeSettings.json`.

- **Generator**: mapuje do narzędzia CMake **- G** przełącznika i określa generator, który ma być używany. Ta właściwość może również służyć jako makra, `${generator}`, tworząc wartości innych właściwości. Program Visual Studio obsługuje obecnie następujące generatory CMake:

  - "Ninja"
  - "Visual Studio 14 2015"
  - "Visual Studio 14 2015 ARM"
  - "Visual Studio 14 2015 Win64"
  - "Visual Studio 15 2017"
  - "Visual Studio 15 2017 ARM"
  - "Visual Studio 15 2017 Win64"

  Ponieważ Ninja jest przeznaczona dla szybkości szybkie kompilacji zamiast elastyczności i funkcji, jest ustawiona jako domyślna. Jednak niektóre projekty narzędzia CMake, może być nie można poprawnie tworzyć zawartość przy użyciu Ninja. W takiej sytuacji można nakazać narzędzia CMake w celu wygenerowania projektu programu Visual Studio, zamiast tego.

  Aby określić generator programu Visual Studio, otwórz `CMakeSettings.json` z menu głównego, wybierając **CMake | Zmień ustawienia narzędzia CMake**. Usuń "Ninja", a następnie wpisz "V". Aktywuje funkcję IntelliSense, która pozwala na dokonanie wyboru generator, który ma.

  Podczas aktywnej konfiguracji określa generator programu Visual Studio, domyślnie MSBuild.exe jest wywoływana z `-m -v:minimal` argumentów. Dostosowywanie kompilacji, wewnątrz `CMakeSettings.json` plików, można określić dodatkowe [argumenty wiersza polecenia programu MSBuild](../build/reference/msbuild-visual-cpp-overview.md) mają być przekazane do systemu kompilacji, za pośrednictwem `buildCommandArgs` właściwości:
    
    ```json
    "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
    ```

- **wybrany element buildRoot**: mapuje **-DCMAKE_BINARY_DIR** Przełącz i określa, w którym zostanie utworzona pamięci podręcznej narzędzia CMake. Jeśli folder nie istnieje, zostanie utworzony.

- **zmienne**: zawiera pary nazwa wartość, zmienne narzędzia CMake, które będą przekazywane jako **-D** *_nazwa_=_wartość_* do narzędzia CMake. Instrukcje kompilacji projektu narzędzia CMake określić dodanie wszelkie zmienne bezpośrednio do pliku pamięci podręcznej narzędzia CMake, zaleca się dodanie ich w tym miejscu zamiast tego. Poniższy przykład pokazuje, jak określić pary nazwa wartość dla 14.14.26428 zestaw narzędzi MSVC:

```json
"variables": [
    {
      "name": "CMAKE_CXX_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe"
    },
    {
      "name": "CMAKE_C_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe"
    }
  ]
```

- **cmakeCommandArgs**: określa żadnych dodatkowych przełączników, które mają być przekazane do CMake.exe.

- **Typ konfiguracji**: Określa typ konfiguracji kompilacji dla wybranego generatora. Obecnie obsługiwane wartości to "Debug", "MinSizeRel", "Wersja" i "RelWithDebInfo".

- **ctestCommandArgs**: Określa dodatkowe przełączniki do przekazania do narzędzia CTest podczas uruchamiania testów.

- **buildCommandArgs**: Określa dodatkowe przełączniki do przekazania do bazowego systemu kompilacji. Na przykład przekazując - v, gdy przy użyciu generatora Ninja wymusza Ninja w danych wyjściowych wiersze polecenia.

Dodatkowe ustawienia są dostępne dla projektów CMake systemu Linux. Zobacz [Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md).

## <a name="environment-variables"></a>Zmienne środowiskowe

 `CMakeSettings.json` obsługuje również konsumencki zmiennych środowiskowych w dowolnej właściwości wymienionych powyżej. Składnia służąca do użycia jest `${env.FOO}` rozwinąć zmiennej środowiskowej % FOO %.
Masz także dostęp do wbudowanych makr, w tym pliku:

- `${workspaceRoot}` — zapewnia pełną ścieżkę folderu obszaru roboczego
- `${workspaceHash}` — Skrót lokalizacji obszaru roboczego. przydatne podczas tworzenia Unikatowy identyfikator dla bieżącego obszaru roboczego (na przykład do użycia w ścieżkach folderów)
- `${projectFile}` — Pełna ścieżka pliku CMakeLists.txt głównego
- `${projectDir}` — Pełna ścieżka do folderu głównego pliku CMakeLists.txt
- `${thisFile}` — Pełna ścieżka `CMakeSettings.json` pliku
- `${name}` — Nazwa konfiguracji
- `${generator}` — Nazwa generatora narzędzia CMake, używany w tej konfiguracji

## <a name="ninja-command-line-arguments"></a>Ninja argumenty wiersza polecenia

W przypadku nieokreślonego obiekty docelowe kompilacji docelowej "default" (zobacz ręczne).

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

## <a name="inherited-environments"></a>Dziedziczonych środowisk

 `CMakeSettings.json` obsługuje dziedziczonych środowisk. Ta funkcja umożliwia (1) dziedziczą środowiska domyślnego i (2) Utwórz niestandardowe zmienne środowiskowe, które są przekazywane do CMake.exe po jego uruchomieniu.

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

W powyższym przykładzie jest taka sama jak działa **wiersz polecenia programisty dla programu VS 2017** z **-arch = amd64-host_arch = amd64** argumentów.

W poniższej tabeli przedstawiono wartości domyślne:

|Nazwa kontekstu|Opis|
|-----------|-----------------|
|vsdev|Domyślne środowisko Visual Studio|
|msvc_x86|Kompiluj przy użyciu x86 x86 narzędzia|
|msvc_arm| Kompilowanie dla ARM przy użyciu x86 narzędzia|
|msvc_arm64|Kompilacji dla architektury ARM64 przy użyciu x86 narzędzia|
|msvc_x86_x64|Kompilacji dla AMD64 przy użyciu x86 narzędzia|
|msvc_x64_x64|Kompilacji dla AMD64 przy użyciu narzędzi 64-bitowych|
|msvc_arm_x64|Kompilowanie dla ARM przy użyciu narzędzi 64-bitowych|
|msvc_arm64_x64|Kompilacji dla architektury ARM64 przy użyciu narzędzi 64-bitowych|

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
          "BuildDir": "D:\\custom-builddir",
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

## <a name="see-also"></a>Zobacz też

[Projekty CMake w programie Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)<br/>
[Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Konfigurowanie sesji debugowania narzędzia CMake](configure-cmake-debugging-sessions.md)<br/>
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Informacje o konfiguracji narzędzia CMake wstępnie zdefiniowane](cmake-predefined-configuration-reference.md)<br/>
