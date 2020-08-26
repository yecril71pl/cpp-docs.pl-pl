---
title: tasks.vs.jsodwołanie do schematu (C++)
ms.date: 08/20/2019
helpviewer_keywords:
- tasks.vs.json file [C++]
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: a2aea1b64d5a6c62604c680bf1a4a26478b7b52a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844993"
---
# <a name="tasksvsjson-schema-reference-c"></a>tasks.vs.jsodwołanie do schematu (C++)

Aby poinformować program Visual Studio o sposobie tworzenia kodu źródłowego w projekcie otwartego folderu, Dodaj *tasks.vs.jsdo* pliku. Możesz zdefiniować dowolne dowolne zadanie w tym miejscu, a następnie wywołać je z menu kontekstowego **Eksplorator rozwiązań** . Projekty CMake nie używają tego pliku, ponieważ wszystkie polecenia kompilacji są określone w *CMakeLists.txt*. W przypadku systemów kompilacji innych niż CMake *tasks.vs.jsna* to miejsce, w którym można określić polecenia kompilacji i wywoływać skrypty kompilacji. Aby uzyskać ogólne informacje na temat używania *tasks.vs.json*, zobacz [Dostosowywanie kompilacji i debugowania zadań dla tworzenia aplikacji "Otwórz folder"](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio).

Zadanie ma `type` Właściwość, która może mieć jedną z czterech wartości: `default` , `launch` , `remote` lub `msbuild` . Większość zadań powinna zostać użyta `launch` , chyba że jest wymagane połączenie zdalne.

## <a name="default-properties"></a>Właściwości domyślne

Właściwości domyślne są dostępne dla wszystkich typów zadań:

|Właściwość|Typ|Opis|
|-|-|-|
|`taskLabel`|ciąg| (Wymagane). Określa etykietę zadania używaną w interfejsie użytkownika.|
|`appliesTo`|ciąg| (Wymagane). Określa pliki, na których można wykonać polecenie. Obsługiwane jest użycie symboli wieloznacznych, na przykład: "*", "*. cpp", "/*. txt"|
|`contextType`|ciąg| Dozwolone wartości: "Custom", "build", "Clean", "Rebuild". Określa, gdzie w menu kontekstowym zostanie wyświetlone zadanie. Wartość domyślna to "Custom".|
|`output`|ciąg| Określa tag danych wyjściowych zadania.|
|`inheritEnvironments`|array| Określa zestaw zmiennych środowiskowych dziedziczonych z wielu źródeł. Można definiować zmienne w plikach, takie jak *CMakeSettings.js* lub *CppProperties.jswłączone* i dostępne dla kontekstu zadania. **Visual Studio 16,4:**: Określanie zmiennych środowiskowych dla poszczególnych zadań przy użyciu `env.VARIABLE_NAME` składni. Aby cofnąć ustawienie zmiennej, ustaw ją na wartość "null".|
|`passEnvVars`|boolean| Określa, czy dołączać dodatkowe zmienne środowiskowe do kontekstu zadania. Te zmienne różnią się od tych, które zostały zdefiniowane przy użyciu `envVars` właściwości. Wartość domyślna to "true".|

## <a name="launch-properties"></a>Właściwości uruchamiania

Gdy typ zadania to `launch` , te właściwości są dostępne:

|Właściwość|Typ|Opis|
|-|-|-|
|`command`|ciąg| Określa pełną ścieżkę procesu lub skryptu do uruchomienia.|
|`args`|array| Określa rozdzielaną przecinkami listę argumentów przekazaną do polecenia.|
|`launchOption`|ciąg| Dozwolone wartości: "none", "ContinueOnError", "IgnoreError". Określa, jak kontynuować polecenie w przypadku wystąpienia błędów.|
|`workingDirectory`|ciąg| Określa katalog, w którym zostanie uruchomione polecenie. Domyślnie jest bieżącym katalogiem roboczym projektu.|
|`customLaunchCommand`|ciąg| Określa globalne dostosowanie zakresu do zastosowania przed wykonaniem polecenia. Przydatne do ustawiania zmiennych środowiskowych, takich jak% PATH%.|
|`customLaunchCommandArgs`|ciąg| Określa argumenty do customLaunchCommand. (Wymagane `customLaunchCommand` ).|
 `env`| Określa listę klucz-wartość niestandardowych zmiennych środowiskowych. Na przykład "myEnv": "myVal"|
|`commands`|array| Określa listę poleceń do wywołania w kolejności.|

### <a name="example"></a>Przykład

Poniższe zadania wywołują *make.exe* , gdy plik reguł programu make jest dostępny w folderze, a `Mingw64` środowisko zostało zdefiniowane w *CppProperties.jsna*, jak pokazano w [CppProperties.jsodwołania do schematu](cppproperties-schema-reference.md#user_defined_environments):

```json
 {
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "gcc make",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make"
    },
    {
      "taskLabel": "gcc clean",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make",
      "args": ["clean"]
    }
  ]
}
```

Te zadania mogą być wywoływane z menu kontekstowego po kliknięciu prawym przyciskiem myszy pliku *. cpp* w **Eksplorator rozwiązań**.

## <a name="remote-properties"></a>Właściwości zdalne

Zadania zdalne są włączane podczas instalowania środowiska wdrażania systemu Linux przy użyciu obciążenia C++ i dodawania połączenia z komputerem zdalnym za pomocą Menedżera połączeń programu Visual Studio. Zadanie zdalne uruchamia polecenia w systemie zdalnym i może również kopiować do niego pliki.

Gdy typ zadania to `remote` , te właściwości są dostępne:

|Właściwość|Typ|Opis|
|-|-|-|
|`remoteMachineName`|ciąg|Nazwa maszyny zdalnej. Musi być zgodna z nazwą komputera w **Menedżerze połączeń**.|
|`command`|ciąg|Polecenie do wysłania do komputera zdalnego. Polecenia domyślne są wykonywane w katalogu $HOME w systemie zdalnym.|
|`remoteWorkingDirectory`|ciąg|Bieżący katalog roboczy na komputerze zdalnym.|
|`localCopyDirectory`|ciąg|Katalog lokalny, który ma zostać skopiowany na komputer zdalny. Domyślnie jest bieżącym katalogiem roboczym.|
|`remoteCopyDirectory`|ciąg|Katalog na komputerze zdalnym, do którego `localCopyDirectory` jest kopiowany.|
|`remoteCopyMethod`|ciąg| Metoda używana do kopiowania. Dozwolone wartości: "none", "SFTP", "rsync". rsync jest zalecane w przypadku dużych projektów.|
|`remoteCopySourcesOutputVerbosity`|ciąg| Dozwolone wartości: "normal", "verbose", "Diagnostic".|
|`rsyncCommandArgs`|ciąg|Wartość domyślna to "-t--Delete".|
|`remoteCopyExclusionList`|array|Rozdzielana przecinkami lista plików w `localCopyDirectory` do wykluczenia z operacji kopiowania.|

### <a name="example"></a>Przykład

Następujące zadanie zostanie wyświetlone w menu kontekstowym po kliknięciu prawym przyciskiem myszy *Main. cpp* w **Eksplorator rozwiązań**. Jest to zależne od maszyny zdalnej wywoływanej `ubuntu` w **Menedżerze połączeń**. Zadanie Kopiuje bieżący otwarty folder w programie Visual Studio do `sample` katalogu na komputerze zdalnym, a następnie wywołuje polecenie g + + w celu skompilowania programu.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Build",
      "appliesTo": "main.cpp",
      "type": "remote",
      "contextType": "build",
      "command": "g++ main.cpp",
      "remoteMachineName": "ubuntu",
      "remoteCopyDirectory": "~/sample",
      "remoteCopyMethod": "sftp",
      "remoteWorkingDirectory": "~/sample/hello",
      "remoteCopySourcesOutputVerbosity": "Verbose"
    }
  ]
}
```

## <a name="msbuild-properties"></a>właściwości programu MSBuild

Gdy typ zadania to `msbuild` , te właściwości są dostępne:

|Właściwość|Typ|Opis|
|-|-|-|
|`verbosity`|ciąg| Określa wartość verbosityAllowed danych wyjściowych kompilacji projektu programu MSBuild: "quiet", "minimalny", "normalny", "szczegółowy", "Diagnostyka".|
|`toolsVersion`|ciąg| Określa wersję zestawu narzędzi do kompilowania projektu, na przykład "2,0", "3,5", "4,0", "Current". Wartość domyślna to "Current".|
|`globalProperties`|object|Określa listę klucz-wartość właściwości globalnych do przekazania do projektu, na przykład "Konfiguracja": "wersja"|
|`properties`|object| Określa listę klucz-wartość dodatkowych właściwości tylko dla projektu.|
|`targets`|array| Określa listę elementów docelowych do wywołania, w kolejności, w projekcie. Domyślny element docelowy projektu jest używany, jeśli nie określono żadnego z nich.|
