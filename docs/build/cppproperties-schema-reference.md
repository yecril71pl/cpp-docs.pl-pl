---
title: Odwołanie pliku cppproperties. JSON
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: d59fca412a26d08f88ccbda20a2c0444cf33b1cb
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417370"
---
# <a name="cpppropertiesjson-reference"></a>Odwołanie pliku cppproperties. JSON

Otwarte projekty folderów, które nie używają CMake, mogą przechowywać ustawienia konfiguracji projektu dla IntelliSense w pliku *pliku cppproperties. JSON* . (Projekty CMake używają pliku [pliku cmakesettings. JSON](customize-cmake-settings.md) ). Konfiguracja składa się z par nazwa/wartość i definiuje ścieżki #include, przełączniki kompilatora i inne parametry. Aby uzyskać więcej informacji na temat dodawania konfiguracji w projekcie otwartego folderu, zobacz temat [Otwieranie projektów C++ folderu](open-folder-projects-cpp.md) . Poniższe sekcje zawierają podsumowanie różnych ustawień. Aby uzyskać pełny opis schematu, przejdź do pliku *CppProperties_schema. JSON*, którego Pełna ścieżka jest podawana u góry edytora kodu, gdy *pliku cppproperties. JSON* jest otwarty.

## <a name="configuration-properties"></a>Właściwości konfiguracji

Konfiguracja może mieć jedną z następujących właściwości:

|||
|-|-|
|`inheritEnvironments`| Określa, które środowiska mają zastosowanie do tej konfiguracji.|
|`name`|Nazwa konfiguracji, która zostanie wyświetlona C++ na liście rozwijanej konfiguracji|
|`includePath`|Rozdzielana przecinkami lista folderów, które powinny być określone w ścieżce dołączania (Maps do/I dla większości kompilatorów)|
|`defines`|Lista makr, które powinny być zdefiniowane (mapy do/D dla większości kompilatorów)|
|`compilerSwitches`|Jeden lub więcej dodatkowych przełączników, które mogą wpływać na zachowanie funkcji IntelliSense|
|`forcedInclude`|Nagłówek, który ma być automatycznie dołączany do każdej jednostki kompilacji (Maps do/FI dla MSVC lub-include dla Clang)|
|`undefines`|Lista makr, które mają być niezdefiniowane (mapy do/U dla MSVC)|
|`intelliSenseMode`|Aparat IntelliSense, który ma być używany. Można określić jedną ze wstępnie zdefiniowanych wariantów specyficznych dla architektury dla MSVC, w zatoce lub Clang.|
|`environments`|Zdefiniowane przez użytkownika zestawy zmiennych, które zachowują się jak zmienne środowiskowe w wierszu polecenia i są dostępne za pomocą $ {ENV.<VARIABLE>} makro.|

### <a name="intellisensemode-values"></a>wartości intelliSensemode

W edytorze kodu są wyświetlane dostępne opcje po rozpoczęciu wpisywania:

![Otwórz folder IntelliSense](media/open-folder-intellisense-mode.png "Otwórz folder IntelliSense")

Są to obsługiwane wartości:

- windows-msvc-x86
- windows-msvc-x64
- windows-msvc-arm
- windows-msvc-arm64
- android-clang-x86
- android-clang-x64
- android-clang-arm
- android-clang-arm64
- iOS — Clang — x86
- ios-clang-x64
- iOS — Clang — ARM
- iOS-Clang-arm64
- windows-clang-x86
- windows-clang-x64
- windows-clang-arm
- windows-clang-arm64
- linux-gcc-x86
- linux-gcc-x64
- Linux — Zarząd — ARM

Uwaga: wartości `msvc-x86` i `msvc-x64` są obsługiwane tylko w przypadku starszych przyczyn. Zamiast tego użyj wariantów `windows-msvc-*`.

## <a name="pre-defined-environments"></a>Środowiska wstępnie zdefiniowane

Program Visual Studio udostępnia następujące wstępnie zdefiniowane środowiska dla C++ firmy Microsoft, które mapują do odpowiednich wiersz polecenia dla deweloperów. W przypadku dziedziczenia jednego z tych środowisk można odwołać się do dowolnych zmiennych środowiskowych, używając właściwości globalnej `env` z następującą składnią makra: $ {ENV.\<VARIABLE >}.

|Nazwa zmiennej|Opis|
|-----------|-----------------|
|vsdev|Domyślne środowisko programu Visual Studio|
|msvc_x86|Kompiluj dla architektury x86 przy użyciu narzędzi x86|
|msvc_x64|Kompiluj dla AMD64 przy użyciu 64-bitowych narzędzi|
|msvc_arm|Kompiluj dla ARM przy użyciu narzędzi x86|
|msvc_arm64|Kompiluj do ARM64 przy użyciu narzędzi x86|
|msvc_x86_x64|Kompiluj dla AMD64 przy użyciu narzędzi x86|
|msvc_arm_x64|Kompiluj dla ARM przy użyciu narzędzi 64-bitowych|
|msvc_arm64_x64|Kompiluj do ARM64 przy użyciu narzędzi 64-bitowych|

Po zainstalowaniu obciążenia systemu Linux następujące środowiska są dostępne dla zdalnego określania systemu Linux i WSL:

|Nazwa zmiennej|Opis|
|-----------|-----------------|
|linux_x86|Zdalny system x86 Linux|
|linux_x64|Element docelowy x64 systemu Linux zdalnie|
|linux_arm|Zdalne docelowa ARM Linux|

## <a name="user_defined_environments"></a>Środowiska zdefiniowane przez użytkownika

Opcjonalnie można użyć właściwości `environments` do zdefiniowania zestawów zmiennych w *pliku cppproperties. JSON* w trybie globalnym lub na konfigurację. Zmienne te zachowują się jak zmienne środowiskowe w kontekście projektu otwartego folderu i można uzyskać do nich dostęp przy użyciu składni $ {ENV.\<VARIABLE >} z pliku *Tasks. vs. JSON* i *uruchamiania. vs. JSON* po ich zdefiniowaniu. Jednak nie są one niekoniecznie ustawiane jako rzeczywiste zmienne środowiskowe w dowolnym wierszu polecenia, który program Visual Studio używa wewnętrznie.

**Program Visual Studio 2019 w wersji 16,4 lub nowszej:** Zmienne specyficzne dla konfiguracji zdefiniowane w pliku *pliku cppproperties. JSON* są automatycznie wybierane przez elementy docelowe i zadania debugowania, bez konieczności ustawiania `inheritEnvironments`. Elementy docelowe debugowania są uruchamiane automatycznie przy użyciu środowiska określonego w pliku *pliku cppproperties. JSON*.

**Program Visual Studio 2019 w wersji 16,3 i starszej:** W przypadku korzystania ze środowiska należy określić go we właściwości `inheritsEnvironments`, nawet jeśli środowisko jest zdefiniowane w ramach tej samej konfiguracji; Właściwość `environment` określa nazwę środowiska. W poniższym przykładzie przedstawiono przykładową konfigurację służącą do włączania funkcji IntelliSense dla programu w ramach instalacji MSYS2. Należy zauważyć, jak konfiguracja definiuje i dziedziczy środowisko `mingw_64` oraz sposób, w jaki Właściwość `includePath` może uzyskać dostęp do zmiennej `INCLUDE`.

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

Gdy definiujesz Właściwość Environments wewnątrz konfiguracji, zastępuje ona wszystkie zmienne globalne o tej samej nazwie.

## <a name="built-in-macros"></a>Makra wbudowane

Masz dostęp do następujących wbudowanych makr wewnątrz pliku *pliku cppproperties. JSON*:

|||
|-|-|
|`${workspaceRoot}`| Pełna ścieżka do folderu obszaru roboczego|
|`${projectRoot}`| Pełna ścieżka do folderu, w którym znajduje się plik *pliku cppproperties. JSON*|
|`${env.vsInstallDir}`| Pełna ścieżka do folderu, w którym zainstalowano uruchomione wystąpienie programu Visual Studio|

### <a name="example"></a>Przykład

Jeśli projekt zawiera folder dołączania, a także zawiera *Windows. h* i inne typowe nagłówki z Windows SDK, warto zaktualizować plik konfiguracyjny *pliku cppproperties. JSON* z uwzględnieniem następujących danych:

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
> `%WindowsSdkDir%` i `%VCToolsInstallDir%` nie są ustawione jako globalne zmienne środowiskowe, dlatego należy uruchomić devenv. exe z wiersz polecenia dla deweloperów, który definiuje te zmienne. (Wpisz "Developer" w menu Start systemu Windows).

## <a name="troubleshoot-intellisense-errors"></a>Rozwiązywanie problemów z błędami IntelliSense

Jeśli nie widzisz oczekiwanej technologii IntelliSense, możesz rozwiązać problemy, przechodząc do opcji **Narzędzia** > **Opcje** > **edytorze tekstów** > **C/C++**  > **Zaawansowane** i ustawienie **Włącz rejestrowanie** na **wartość true**. Aby rozpocząć pracę z programem, spróbuj ustawić **poziom rejestrowania** na 5 i **filtry rejestrowania** na 8.

![Rejestrowanie informacji diagnostycznych](media/diagnostic-logging.png)

Dane wyjściowe są przekazywane do **okno dane wyjściowe** i są widoczne po wybraniu opcji **Pokaż dane wyjściowe z: C++ dziennik wizualny**. Dane wyjściowe zawierają między innymi listę rzeczywistych ścieżek dołączania, które próbuje użyć IntelliSense. Jeśli ścieżki nie pasują do tych w pliku *pliku cppproperties. JSON*, spróbuj zamknąć folder i usunąć podfolder *. vs* zawierający buforowane dane przeglądania.

Aby rozwiązać problemy z błędami funkcji IntelliSense spowodowanymi brakującymi ścieżkami dołączanych, Otwórz **Lista błędów** i przefiltruj dane wyjściowe do "IntelliSense Only" i kod błędu E1696 "nie można otworzyć pliku źródłowego...".
