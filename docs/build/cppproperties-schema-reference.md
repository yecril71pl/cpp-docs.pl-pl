---
title: Plik CppProperties.json — dokumentacja schematu
ms.date: 03/05/2019
helpviewer_keywords:
- CMake in Visual C++
ms.openlocfilehash: fd655de3313dd95eb3fcefaeba21e703d32e860a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823685"
---
# <a name="cpppropertiesjson-schema-reference"></a>Plik CppProperties.json — dokumentacja schematu

Otwórz projekty Folder, których nie należy używać narzędzia CMake mogą przechowywać ustawienia konfiguracji projektu w `CppProperties.json` pliku. (CMake projektów użyj [CMakeSettings.json](customize-cmake-settings.md) pliku.) Korzysta z programu Visual Studio IDE `CppProperties.json` dla technologii IntelliSense i nawigowanie po kodzie. Konfiguracja składa się z pary nazwa/wartość i definiuje #include ścieżki, przełączniki kompilatora i inne parametry. 


## <a name="default-configurations"></a>Domyślne konfiguracje

Program Visual Studio udostępnia wstępnie zdefiniowane konfiguracje dla x86 x64 Debug i Release. Domyślnie projekt ma konfigurację debugowania x86 `CppProperties.json`. Aby dodać nową konfigurację, kliknij prawym przyciskiem myszy `CppProperties.json` w pliku **Eksploratora rozwiązań** i wybierz polecenie **Dodawanie konfiguracji**:

![Otwórz Folder Dodaj konfigurację](media/open-folder-add-config.png "Otwórz Folder Dodawanie nowej konfiguracji")

Domyślne konfiguracje przedstawiono poniżej:

```json
{
  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86-Release",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "NDEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    },
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Release",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "NDEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```
Dla właściwości, które mają zbiór dopuszczalnych wartości Edytor kodu przedstawia dostępne opcje, po rozpoczęciu wpisywania:

![Otwórz Folder IntelliSense](media/open-folder-intellisense-mode.png "Otwórz Folder w technologii IntelliSense")



## <a name="configuration-properties"></a>Właściwości konfiguracji

Konfiguracja może mieć jedną z następujących właściwości:

|||
|-|-|
|`name`|Nazwa konfiguracji, który pojawia się na liście rozwijanej konfiguracji C++|
|`includePath`|Lista folderów, które powinny być określone w ścieżki dołączania (map do /I większość kompilatorów)|
|`defines`|Lista makr, które powinny być zdefiniowane (map do /D większość kompilatorów)|
|`compilerSwitches`|jeden lub więcej dodatkowych przełączników, które mogą mieć wpływ na zachowanie funkcji IntelliSense|
|`forcedInclude`|Nagłówek, aby automatycznie dołączone każda jednostka kompilacji (mapuje /FI dla MSVC lub - zawierają clang)|
|`undefines`|Lista makr, być niezdefiniowana (mapuje do /U dla MSVC)|
|`intelliSenseMode`|Aparat IntelliSense, która ma być używany. Warianty określonej architektury można określić dla MSVC i kompilatora gcc, Clang:<br/><br/>-msvc-x86 (ustawienie domyślne)<br/>- msvc-x64<br/>- msvc-arm<br/>-windows-clang-x86<br/>- windows-clang-x64<br/>-windows-clang-arm<br/>- Linux-x64<br/>- Linux-x86<br/>Linux-arm<br/>-gccarm|

## <a name="custom-configurations"></a>Konfiguracje niestandardowe


Możliwość dostosowania configuations domyślne w `CppProperties.json`, lub Utwórz nowe konfiguracje. Każdy będą wyświetlane na liście rozwijanej konfiguracji:

```json
{
  "configurations": [
    {
      "name": "Windows",
      ...
    },
    {
      "name": "with EXTERNAL_CODECS",
      ...
    }
  ]
}
```

## <a name="system-environment-variables"></a>Systemowe zmienne środowiskowe 

 `CppProperties.json` rozszerzanie zmiennych środowiskowych systemu obsługuje do obejmują ścieżek i innych właściwości. Składnia jest `${env.FOODIR}` rozwinąć zmiennej środowiskowej `%FOODIR%`. Obsługiwane są również następujące zmienne zdefiniowane przez system:

|Nazwa zmiennej|Opis|
|-----------|-----------------|
|vsdev|Domyślne środowisko Visual Studio|
|msvc_x86|Kompiluj przy użyciu x86 x86 narzędzia|
|msvc_arm|Kompilowanie dla ARM przy użyciu x86 narzędzia|
|msvc_arm64|Kompilacji dla architektury ARM64 przy użyciu x86 narzędzia|
|msvc_x86_x64|Kompilacji dla AMD64 przy użyciu x86 narzędzia|
|msvc_x64_x64|Kompilacji dla AMD64 przy użyciu narzędzi 64-bitowych|
|msvc_arm_x64|Kompilowanie dla ARM przy użyciu narzędzi 64-bitowych|
|msvc_arm64_x64|Kompilacji dla architektury ARM64 przy użyciu narzędzi 64-bitowych|

Po zainstalowaniu obciążenia systemu Linux dla zdalnie przeznaczonych dla systemów Linux i WSL dostępne są następujące środowiska:

|Nazwa zmiennej|Opis|
|-----------|-----------------|
|linux_x86|Wyceluj x86 Linux zdalnie|
|linux_x64|Wyceluj x64 Linux zdalnie|
|linux_arm|Docelowa ARM Linux zdalnie|

## <a name="custom-environment-variables"></a>Niestandardowe zmienne środowiskowe

Można zdefiniować niestandardowe zmienne środowiskowe w `CppProperties.json` albo globalnie lub na konfiguracji. Poniższy przykład pokazuje, jak domyślne i niestandardowe zmienne środowiskowe mogą być zadeklarowane i być używane. Globalna **środowisk** właściwości deklaruje zmienną o nazwie **INCLUDE** które mogą być używane przez żadnej konfiguracji:

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\src\includes"
    }
  ],

  "configurations": [
    {
      "inheritEnvironments": [
        // Inherit the MSVC 32-bit environment and toolchain.
        "msvc_x86"
      ],
      "name": "x86",
      "includePath": [
        // Use the include path defined above.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "msvc-x86"
    },
    {
      "inheritEnvironments": [
        // Inherit the MSVC 64-bit environment and toolchain.
        "msvc_x64"
      ],
      "name": "x64",
      "includePath": [
        // Use the include path defined above.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "msvc-x64"
    }
  ]
}
```
## <a name="per-configuration-environment-variables"></a>Zmienne środowiskowe — Konfiguracja

Można również definiować **środowisk** właściwości w konfiguracji, tak że ma zastosowanie tylko do konfiguracji i zastępuje wszystkie zmienne globalne o takiej samej nazwie. W poniższym przykładzie x64 Konfiguracja definiuje lokalnym **INCLUDE** zmiennej, która zastępuje wartości globalnej:

```json
{
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\src\includes"
    }
  ],

  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86",
      "includePath": [
        // Use the include path defined in the global environments property.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "msvc-x86"
    },
    {
      "environments": [
        {
          // Append 64-bit specific include path to env.INCLUDE.
          "INCLUDE": "${env.INCLUDE};${workspaceRoot}\src\includes64"
        }
      ],

      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64",
      "includePath": [
        // Use the include path defined in the local environments property.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "msvc-x64"
    }
  ]
}
```

Wszystkie niestandardowe i domyślne zmienne środowiskowe są również dostępne w `tasks.vs.json` i `launch.vs.json`.

#### <a name="build-in-macros"></a>Makra kompilacji w

Masz dostęp do następujących wbudowanych makr wewnątrz `CppProperties.json`:

|||
|-|-|
|`${workspaceRoot}`| Pełna ścieżka do folderu obszaru roboczego|
|`${projectRoot}`| Pełna ścieżka do folderu, w którym `CppProperties.json` znajduje się|
|`${vsInstallDir}`| Pełna ścieżka do folderu, w którym zainstalowano uruchomione wystąpienie programu VS 2017|

Na przykład, jeśli projektu folderem include i obejmują również windows.h oraz inne typowe nagłówki z zestawu Windows SDK, możesz zaktualizować swoje `CppProperties.json` zawiera plik konfiguracji z nimi:

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
> `%WindowsSdkDir%` i `%VCToolsInstallDir%` nie są ustawione jako zmienne środowiskowe globalnego dlatego upewnij się, uruchom devenv.exe z "Developer wiersza polecenia dla programu VS 2017" definiujący tych zmiennych.

## <a name="troubleshoot-intellisense-errors"></a>Rozwiązywanie problemów IntelliSense

Rozwiązywania problemów z technologii IntelliSense błędy spowodowane przez brak ścieżki dołączanych plików, otwórz **lista błędów** E1696. kod błędu "nie można otworzyć pliku źródłowego..." i filtrować dane wyjściowe do lokalizacji "Tylko IntelliSense".



