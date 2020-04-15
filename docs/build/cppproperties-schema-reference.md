---
title: Odwołanie do pliku CppProperties.json
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: be6db52e1e62244e9f44db8ac86238242ab50ca0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328716"
---
# <a name="cpppropertiesjson-reference"></a>Odwołanie do pliku CppProperties.json

Otwórz projekty folderów, które nie używają CMake można przechowywać ustawienia konfiguracji projektu dla IntelliSense w pliku *CppProperties.json.* (CMake projektów użyć [pliku CMakeSettings.json.)](customize-cmake-settings.md) Konfiguracja składa się z par nazwy/wartości i definiuje #include ścieżki, przełączniki kompilatora i inne parametry. Aby uzyskać więcej informacji na temat dodawania konfiguracji w projekcie Folderu otwartego, zobacz [Otwieranie projektów folderów dla języka C++.](open-folder-projects-cpp.md) W poniższych sekcjach podsumowano różne ustawienia. Aby uzyskać pełny opis schematu, przejdź do *CppProperties_schema.json*, którego pełna ścieżka jest podana w górnej części edytora kodu, gdy *CppProperties.json* jest otwarty.

## <a name="configuration-properties"></a>Właściwości konfiguracji

Konfiguracja może mieć dowolną z następujących właściwości:

|||
|-|-|
|`inheritEnvironments`| Określa, które środowiska mają zastosowanie do tej konfiguracji.|
|`name`|Nazwa konfiguracji, która pojawi się na menu rozwijanym konfiguracji języka C++|
|`includePath`|Oddzielona przecinkami lista folderów, które powinny być określone w ścieżce dołączania (mapy do /I dla większości kompilatorów)|
|`defines`|Lista makr, które powinny być zdefiniowane (mapy do /D dla większości kompilatorów)|
|`compilerSwitches`|Co najmniej jeden dodatkowy przełącznik, który może wpływać na zachowanie intellisense|
|`forcedInclude`|Nagłówek, który ma być automatycznie uwzględniany w każdej jednostce kompilacji (mapuje na /FI dla MSVC lub -include for clang)|
|`undefines`|Lista makr, które mają być niezdefiniowane (mapuje do /U dla MSVC)|
|`intelliSenseMode`|Silnik IntelliSense do użycia. Można określić jeden ze wstępnie zdefiniowanych wariantów specyficznych dla architektury dla MSVC, gcc lub Clang.|
|`environments`|Zdefiniowane przez użytkownika zestawy zmiennych, które zachowują się jak zmienne środowiskowe w\< wierszu polecenia i są dostępne za pomocą ${env. ZMIENNE>} makr.|

### <a name="intellisensemode-values"></a>intelliSenseMode wartości

Edytor kodu pokazuje dostępne opcje po rozpoczęciu pisania:

![Otwórz folder IntelliSense](media/open-folder-intellisense-mode.png "Otwórz folder IntelliSense")

Są to obsługiwane wartości:

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
- linux-gcc-ramię

Uwaga: Wartości `msvc-x86` `msvc-x64` i są obsługiwane tylko ze względu na starsze wersje. Zamiast `windows-msvc-*` tego użyj wariantów.

## <a name="pre-defined-environments"></a>Wstępnie zdefiniowane środowiska

Program Visual Studio udostępnia następujące wstępnie zdefiniowane środowiska dla programu Microsoft C++, które są mapowane do odpowiedniego wiersza polecenia dewelopera. Po odziedziczeniu jednego z tych środowisk można odwołać się do dowolnej `env` zmiennej środowiskowej przy użyciu właściwości\< globalnej z tą składnią makra: ${env. ZMIENNA>}.

|Nazwa zmiennej|Opis|
|-----------|-----------------|
|vsdev ( vsdev )|Domyślne środowisko programu Visual Studio|
|msvc_x86|Kompilowanie dla x86 przy użyciu narzędzi x86|
|msvc_x64|Kompilowanie dla AMD64 przy użyciu narzędzi 64-bitowych|
|msvc_arm|Kompilowanie dla ARM przy użyciu narzędzi x86|
|msvc_arm64|Kompilowanie dla ARM64 przy użyciu narzędzi x86|
|msvc_x86_x64|Kompilowanie dla AMD64 przy użyciu narzędzi x86|
|msvc_arm_x64|Kompilowanie dla ARM przy użyciu narzędzi 64-bitowych|
|msvc_arm64_x64|Kompilowanie dla ARM64 przy użyciu narzędzi 64-bitowych|

Po zainstalowaniu obciążenia systemu Linux dostępne są następujące środowiska do zdalnego kierowania na linki i wsl:

|Nazwa zmiennej|Opis|
|-----------|-----------------|
|linux_x86|Zdalnie kierować x86 Linux|
|linux_x64|Zdalnie kierować x64 Linux|
|linux_arm|Target ARM Linux zdalnie|

## <a name="user-defined-environments"></a><a name="user_defined_environments"></a>Środowiska zdefiniowane przez użytkownika

Opcjonalnie można użyć `environments` właściwości do definiowania zestawów zmiennych w *CppProperties.json* globalnie lub na konfigurację. Zmienne te zachowują się jak zmienne środowiskowe w kontekście projektu Otwórz folder\< i są dostępne za pomocą ${env. ZMIENNA>} składni z *pliku tasks.vs.json* i *launch.vs.json* po ich zdefiniowaniu w tym miejscu. Jednak nie są one koniecznie ustawione jako rzeczywiste zmienne środowiskowe w wierszu polecenia, który visual studio używa wewnętrznie.

**Visual Studio 2019 w wersji 16.4 i nowszej:** Zmienne specyficzne dla konfiguracji zdefiniowane w *pliku CppProperties.json* są automatycznie pobierane `inheritEnvironments`przez obiekty docelowe i zadania debugowania bez konieczności ustawiania . Obiekty docelowe debugowania są uruchamiane automatycznie w środowisku określonym w *pliku CppProperties.json*.

**Visual Studio 2019 w wersji 16.3 i wcześniejszych:** Gdy zużywają środowisko, następnie należy określić go we `inheritsEnvironments` właściwości, nawet jeśli środowisko jest zdefiniowane jako część tej samej konfiguracji; `environment` właściwość określa nazwę środowiska. W poniższym przykładzie przedstawiono przykładową konfigurację włączania technologii IntelliSense dla GCC w instalacji msys2. Należy zauważyć, jak konfiguracja definiuje `mingw_64` i dziedziczy `includePath` środowisko i `INCLUDE` jak właściwość może uzyskać dostęp do zmiennej.

```json
"configurations": [
    {

      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath ,": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**",
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR};",
          "environment": "mingw_64"
        }
      ]
    }
  ]
```

Podczas definiowania **środowiska** właściwości wewnątrz konfiguracji, zastępuje wszystkie zmienne globalne o tej samej nazwie.

## <a name="built-in-macros"></a>Wbudowane makra

Masz dostęp do następujących wbudowanych makr wewnątrz *CppProperties.json:*

|||
|-|-|
|`${workspaceRoot}`| Pełna ścieżka do folderu obszaru roboczego|
|`${projectRoot}`| Pełna ścieżka do folderu, w którym jest umieszczana plik *CppProperties.json*|
|`${env.vsInstallDir}`| Pełna ścieżka do folderu, w którym jest zainstalowane uruchomione wystąpienie programu Visual Studio|

### <a name="example"></a>Przykład

Jeśli projekt ma folder dołączany i zawiera również *plik windows.h* i inne typowe nagłówki z pakietu Windows SDK, można zaktualizować plik konfiguracyjny *CppProperties.json* o następujące elementy:

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\ucrt",
        "${env.NETFXSDKDir}\include\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\shared",
        "${env.VCToolsInstallDir}\include"
      ]
    }
  ]
}
```

> [!Note]
> `%WindowsSdkDir%`i `%VCToolsInstallDir%` nie są ustawione jako globalne zmienne środowiskowe, więc upewnij się, że uruchomisz devenv.exe z wiersza polecenia dewelopera, który definiuje te zmienne. (Wpisz "deweloper" w menu Start systemu Windows).

## <a name="troubleshoot-intellisense-errors"></a>Rozwiązywanie problemów z błędami intellisense

Jeśli nie widzisz intellisense, że można rozwiązać problem, przechodząc do **Narzędzia** > **Opcje** > **Edytor** > tekstu**C / C ++** > **Zaawansowane** i ustawienie **Włącz rejestrowanie** do **true**. Na początek spróbuj **zniwelować poziom rejestrowania** na 5, a **filtry rejestrowania** na 8.

![Rejestrowanie diagnostyczne](media/diagnostic-logging.png)

Dane wyjściowe są przesyłane potokiem do **okna wyjściowego** i są widoczne po wybraniu opcji **Pokaż wyjście z: Visual C++ Log**. Dane wyjściowe zawiera między innymi listę rzeczywistych ścieżek dołączanych przez intellisense. Jeśli ścieżki nie są zgodne z ścieżkami w *pliku CppProperties.json,* spróbuj zamknąć folder i usunąć podfolder *.vs* zawierający buforowane dane przeglądania.

Aby rozwiązać problemy z błędami IntelliSense spowodowanymi brakiem ścieżek, otwórz **listę błędów** i przefiltruj jej dane wyjściowe do "IntelliSense only" i kod błędu E1696 "nie może otworzyć pliku źródłowego ...".
