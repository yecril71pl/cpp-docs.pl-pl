---
title: Otwórz Folder projektów w języku Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/01/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4444e70ec158d7afa35c3955bbef9af4bfa12f2
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131326"
---
# <a name="open-folder-projects-in-visual-c"></a>Otwórz Folder projektów w języku Visual C++

W programie Visual Studio 2017 i nowszych funkcji "Otwórz Folder" umożliwia otwieranie folderu plików źródłowych i od razu Rozpocznij kodowanie dzięki obsłudze technologii IntelliSense, przeglądanie, refaktoryzację, debugowanie i tak dalej. Nie pliku SLN lub .vcxproj pliki są ładowane; Jeśli to konieczne, niestandardowe zadania można określić także twórz i uruchamiaj parametrów za pomocą plików prostych JSON. Obsługiwane przez Otwórz Folder, Visual C++ może teraz obsługiwać nie tylko luźne kolekcje plików, ale również praktycznie dowolnej kompilacji systemu, w tym CMake, Ninja, QMake (dla projektów Qt), gyp, SCons, Gradle, Buck, markę i nie tylko. 

Aby użyć Otwórz Folder, w menu głównym wybierz *pliku | Otwórz | Folder* lub naciśnij *Ctrl + Shift + Alt + O*. Eksplorator rozwiązań natychmiast wyświetla wszystkie pliki w folderze. Możesz kliknąć dowolny plik, aby rozpocząć jego edycji. W tle programu Visual Studio uruchamia indeksowanie plików, aby włączyć funkcję IntelliSense, nawigowanie i funkcje refaktoryzacji. Jak edytowanie, tworzenie, przenieść lub usunąć pliki programu Visual Studio automatycznie śledzi zmiany i stale aktualizuje jego indeksu funkcji IntelliSense. 
  
## <a name="cmake-projects"></a>Projekty narzędzia CMake
Narzędzie CMake jest zintegrowana w środowisku IDE programu Visual Studio jako narzędzia CMake w języku Visual C++, składnik obciążeniu C++ dla komputerów stacjonarnych. Aby uzyskać więcej informacji, zobacz [narzędzia CMake w języku Visual C++](cmake-tools-for-visual-cpp.md).
 
## <a name="qmake-projects-that-target-the-qt-framework"></a>Projekty QMake, których platformą docelową platformę Qt
Można użyć narzędzia CMake w języku Visual C++ pod kątem Qt do tworzenia projektów Qt lub można użyć [rozszerzenie programu Visual Studio Qt](https://download.qt.io/development_releases/vsaddin/) dla programu Visual Studio 2015 lub Visual Studio 2017.

## <a name="gyp-cons-scons-buck-etc"></a>gyp, Cons, SCons, Buck, etc
Możesz użyć dowolnego systemu kompilacji w programie Visual C++ i nadal korzystaj z zalet środowiska IDE programu Visual C++ i debugera. Po otwarciu folderu głównego projektu, Visual C++ używa heurystyki do indeksowania plików źródłowych dla technologii IntelliSense i przeglądania. Za dostarczanie wskazówek na temat strukturę kodu przez edycję pliku CppProperties.json. W podobny sposób można skonfigurować program kompilacji, edytując plik launch.vs.json. 

## <a name="configuring-open-folder-projects"></a>Konfigurowanie projektów Otwórz Folder
Otwórz Folder projektu można dostosować za pomocą trzech plików JSON:
|||
|-|-|
|CppProperties.json|Określ informacje o konfiguracji niestandardowej do przeglądania. Ten plik, należy utworzyć, jeśli to konieczne, w folderze głównym projektu.|
|launch.vs.json|Określ argumenty wiersza polecenia. Udostępnianych za pośrednictwem **Eksploratora rozwiązań** element menu kontekstowego **ustawienia debugowania i uruchamiania**.|
|tasks.vs.json|Określenie niestandardowych poleceń kompilacji i przełączniki kompilatora. Udostępnianych za pośrednictwem **Eksploratora rozwiązań** element menu kontekstowego **skonfigurować zadania**.|

### <a name="configure-intellisense-with-cpppropertiesjson"></a>Konfigurowanie funkcji IntelliSense przy użyciu CppProperties.json
Funkcja IntelliSense i przeglądanie częściowo zachowanie zależy od aktywną konfigurację kompilacji, który definiuje #include ścieżki, przełączniki kompilatora i inne parametry. Domyślnie program Visual Studio zawiera konfiguracje Debug i Release. Dla niektórych projektów może być konieczne utworzenie konfiguracji niestandardowej w kolejności dla technologii IntelliSense i przeglądania funkcji w pełni zrozumienie kodu. Aby zdefiniować nową konfigurację, Utwórz plik o nazwie CppProperties.json w folderze głównym. Oto przykład:

```json
{
  "configurations": [
    {
      "name": "Windows x64",
      "includePath": [ "include" ],
      "defines": [ "_DEBUG" ],
      "compilerSwitches": "/std:c++17",
      "intelliSenseMode": "msvc-x64",
      "forcedInclude": [ "pch.h" ],
      "undefines": []
    }
  ]
}
```
Konfiguracja może mieć jedną z następujących właściwości:

|||  
|-|-| 
|`name`|Nazwa konfiguracji, który pojawia się na liście rozwijanej konfiguracji C++|
|`includePath`|Lista folderów, które powinny być określone w ścieżki dołączania (map do /I większość kompilatorów)|
|`defines`|Lista makr, które powinny być zdefiniowane (map do /D większość kompilatorów)|
|`compilerSwitches`|jeden lub więcej dodatkowych przełączników, które mogą mieć wpływ na zachowanie funkcji IntelliSense|
|`forcedInclude`|Nagłówek, aby automatycznie dołączone każda jednostka kompilacji (mapuje /FI dla MSVC lub - zawierają clang)|
|`undefines`|Lista makr, być niezdefiniowana (mapuje do /U dla MSVC)|
|`intelliSenseMode`|Aparat IntelliSense, która ma być używany. Warianty określonej architektury można określić dla MSVC i kompilatora gcc, Clang:
- msvc-x86 (ustawienie domyślne)
- msvc-x64
- msvc-arm
- windows-clang-x86
- windows-clang-x64
- windows-clang-arm
- Linux-x64
- Linux-x86
- Linux-arm
- gccarm

#### <a name="environment-variables"></a>Zmienne środowiskowe
Plik CppProperties.json obsługuje system rozszerzanie zmiennych środowiskowych dla obejmują ścieżek i innych właściwości. Składnia jest `${env.FOODIR}` rozwinąć zmiennej środowiskowej `%FOODIR%`. Obsługiwane są również następujące zmienne zdefiniowane przez system:

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

Można zdefiniować niestandardowe zmienne środowiskowe w CppProperties.json albo globalnie lub na konfiguracji. Poniższy przykład pokazuje, jak domyślne i niestandardowe zmienne środowiskowe mogą być zadeklarowane i być używane. Globalna **środowisk** właściwości deklaruje zmienną o nazwie **INCLUDE** które mogą być używane przez żadnej konfiguracji:

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\\src\\includes"
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
Można również definiować **środowisk** właściwości w konfiguracji, tak że ma zastosowanie tylko do konfiguracji i zastępuje wszystkie zmienne globalne o takiej samej nazwie. W poniższym przykładzie x64 Konfiguracja definiuje lokalnym **INCLUDE** zmiennej, która zastępuje wartości globalnej:

```json
{
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\\src\\includes"
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
          "INCLUDE": "${env.INCLUDE};${workspaceRoot}\\src\\includes64"
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

Wszystkie niestandardowe i domyślne zmienne środowiskowe są również dostępne w pliku tasks.vs.json i pliku launch.vs.json.

#### <a name="macros"></a>Makra
Masz dostęp do następujących wbudowanych makr wewnątrz CppProperties.json:
|||
|-|-|
|`${workspaceRoot}`| Pełna ścieżka do folderu obszaru roboczego|
|`${projectRoot}`| Pełna ścieżka do folderu, w którym znajduje się plik CppProperties.json|
|`${vsInstallDir}`| Pełna ścieżka do folderu, w którym zainstalowano uruchomione wystąpienie programu VS 2017|

Na przykład jeśli projekt folderem include, obejmuje także windows.h oraz inne typowe nagłówki z zestawu Windows SDK można zaktualizować swoje CppProperties.json zawiera plik konfiguracji z tych:

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\ucrt",
        "${env.NETFXSDKDir}\\include\\um",
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\um",
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\shared",
        "${env.VCToolsInstallDir}include"
      ]
    }
  ]
}
```

**Uwaga:** `%WindowsSdkDir%` i `%VCToolsInstallDir%` nie są ustawione jako zmienne środowiskowe globalnego dlatego upewnij się, uruchom devenv.exe z "Developer wiersza polecenia dla programu VS 2017" definiujący tych zmiennych.

Rozwiązywania problemów z technologii IntelliSense błędy spowodowane przez brak ścieżki dołączanych plików, otwórz **lista błędów** E1696. kod błędu "nie można otworzyć pliku źródłowego..." i filtrować dane wyjściowe do lokalizacji "Tylko IntelliSense". 

Można utworzyć dowolną liczbę konfiguracji w CppProperties.json. Każdy będą wyświetlane na liście rozwijanej konfiguracji:

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
### <a name="define-tasks-with-tasksvsjson"></a>Definiowanie zadań za pomocą pliku tasks.vs.json
Można zautomatyzować skrypty kompilacji lub innych zewnętrznych operacji na plikach, znajdującym się w bieżącym obszarze roboczym, uruchamiając je jako zadania bezpośrednio w środowisku IDE. Można skonfigurować nowe zadanie, kliknij prawym przyciskiem myszy pliku lub folderu i wybierając **skonfigurować zadania**. 

![Otwórz Folder skonfigurować zadania](media/open-folder-config-tasks.png)

Tworzy (lub zostanie otwarty) `tasks.vs.json` pliku w folderze .vs, który program Visual Studio tworzy w folderze głównym projektu. Można zdefiniować wszystkie dowolnego zadania w tym pliku, a następnie wywołaj ją z **Eksploratora rozwiązań** menu kontekstowego. Poniższy przykład pokazuje plik pliku tasks.vs.json, który definiuje jedno zadanie. `taskName` Określa nazwę, która jest wyświetlana w menu kontekstowym. `appliesTo` Określa pliki, które można wykonać polecenia na. `command` Właściwość odwołuje się do zmiennej środowiskowej COMSPEC, który określa ścieżkę do konsoli (cmd.exe na Windows). Możesz też przywołać zmienne środowiskowe, które są zadeklarowane w CppProperties.json lub w pliku CMakeSettings.json. `args` Właściwość określa wiersz polecenia do wywołania. `${file}` — Makro pobiera wybranego pliku w **Eksploratora rozwiązań**. Poniższy przykład spowoduje wyświetlenie nazwy pliku .cpp zaznaczony.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```
Po zapisaniu pliku tasks.vs.json, kliknij prawym przyciskiem myszy dowolny plik .cpp, w tym folderze, wybierz polecenie **Echo, nazwa_pliku** z menu kontekstowego i zobacz, nazwa pliku jest wyświetlany w oknie danych wyjściowych.



#### <a name="appliesto"></a>AppliesTo
Można utworzyć zadania dla dowolnego pliku lub folderu, określając jej nazwę w `appliesTo` pole, na przykład `"appliesTo" : "hello.cpp"`. Następujące maski plików mogą być używane jako wartości:
|||
|-|-|
|`"*"`| zadanie jest dostępne dla wszystkich plików i folderów w obszarze roboczym|
|`"*/"`| zadanie jest dostępne dla wszystkich folderów w obszarze roboczym|
|`"*.cpp"`| zadanie jest dostępny dla wszystkich plików z rozszerzeniem .cpp w obszarze roboczym|
|`"/*.cpp"`| zadanie jest dostępny dla wszystkich plików z .cpp rozszerzenia w katalogu głównym obszaru roboczego|
|`"src/*/"`| zadanie jest dostępne dla wszystkich podfolderów folderu "src"|
|`"makefile"`| zadanie jest dostępny dla wszystkich plików w pliku reguł programu make w obszarze roboczym|
|`"/makefile"`| zadanie jest dostępna tylko dla pliku reguł programu make w katalogu głównym obszaru roboczego|

#### <a name="output"></a>dane wyjściowe
Użyj `output` właściwości w celu określenia pliku wykonywalnego, który zostanie uruchomiony po naciśnięciu klawisza **F5**. Na przykład:

```json
      "output": "${workspaceRoot}\\bin\\hellomake.exe" 
```

#### <a name="macros-for-tasksvsjson"></a>Makra dla tasks.vs.json

|||
|-|-|
|`${env.<VARIABLE>}`| Określa wszystkie zmienne środowiskowe (np. ${env. PATH}, ${env.COMSPEC} i tak dalej) który jest skonfigurowany dla wiersza polecenia dla deweloperów. Aby uzyskać więcej informacji, zobacz [wiersz polecenia programisty dla programu Visual Studio](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Pełna ścieżka do folderu obszaru roboczego (na przykład "C:\sources\hello")|
|`${file}`| Pełna ścieżka pliku lub folderu wybrana do uruchomienia tego zadania względem (na przykład "C:\sources\hello\src\hello.cpp")|
|`${relativeFile}`| względna ścieżka do pliku lub folderu (na przykład "src\hello.cpp")|
|`${fileBasename}`| Nazwa pliku bez ścieżki i rozszerzenia (na przykład "hello")|
|`${fileDirname}`| Pełna ścieżka do pliku, z wyjątkiem nazwy pliku (na przykład "C:\sources\hello\src")|
|`${fileExtname}`| rozszerzenie wybranego pliku (na przykład, "CPP")|

#### <a name="custom-macros"></a>Niestandardowe makra
Aby zdefiniować niestandardowy — makro w pliku tasks.vs.json, Dodaj parę nazwa: wartość przed bloków zadań. W poniższym przykładzie zdefiniowano makro o nazwie `outDir` który jest używany w `args` właściwości:

```json
{
"version": "0.2.1",
  "outDir": "${workspaceRoot}\\bin",
  "tasks": [
    {
      "taskName": "List outputs",
      "*",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": [
        "dir ${outDir}"
      ]
    }
  ]
```

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Konfiguruj parametry debugowania za pomocą pliku launch.vs.json
Aby dostosować argumenty wiersza polecenia programu, kliknij prawym przyciskiem myszy plik wykonywalny w **Eksploratora rozwiązań** i wybierz **ustawienia debugowania i uruchamiania**. Spowoduje to otwarcie istniejącego `launch.vs.json` pliku, lub jeśli żaden nie istnieje, zostanie utworzony nowy plik wstępnie wypełnione informacjami o programie wybrano. 

Aby określić dodatkowe argumenty, wystarczy dodać ich w `args` tablicę JSON, jak pokazano w poniższym przykładzie:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CPP\\7zip\\Bundles\\Alone\\O\\7za.exe",
      "name": "7za.exe list content of helloworld.zip",
      "args": [ "l", "d:\\sources\\helloworld.zip" ]
    }
  ]
}
```

Po zapisaniu tego pliku, nowa konfiguracja zostanie wyświetlona w menu rozwijanym Debuguj element docelowy i możesz wybrać go, aby uruchomić debuger. Można utworzyć wiele konfiguracji debugowania, jak chcesz, dla dowolnej liczby plików wykonywalnych. Jeśli użytkownik naciśnie klawisz **F5** teraz uruchomić i trafiony punkt przerwania, wszelkie może już zostały ustawione przez debuger. Obecnie są dostępne wszystkie znajomego debugera systemu windows i ich funkcje.

## <a name="see-also"></a>Zobacz też
[Zintegrowane środowisko projektowe i narzędzia projektowe Visual C++](ide-and-tools-for-visual-cpp-development.md)

