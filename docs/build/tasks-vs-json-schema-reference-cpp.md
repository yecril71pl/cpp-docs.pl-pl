---
title: Tasks. vs. JSON — odwołanieC++do schematu ()
ms.date: 08/20/2019
helpviewer_keywords:
- tasks.vs.json file [C++]
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: cc6b2983d3cc3d40449357a554df5feee38c21d9
ms.sourcegitcommit: 6c1960089b92d007fc28c32af1e4bef0f85fdf0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556659"
---
# <a name="tasksvsjson-schema-reference-c"></a>Tasks. vs. JSON — odwołanieC++do schematu ()

Aby poinformować program Visual Studio o sposobie tworzenia kodu źródłowego w projekcie otwartego folderu, Dodaj plik *Tasks. vs. JSON* . Możesz zdefiniować dowolne dowolne zadanie w tym miejscu, a następnie wywołać je z menu kontekstowego **Eksplorator rozwiązań** . Projekty CMake nie korzystają z tego pliku, ponieważ wszystkie polecenia kompilacji są określone w pliku *CMakeLists. txt*. W przypadku systemów kompilacji innych niż CMake, *Tasks. vs. JSON* to miejsce, w którym można określić polecenia kompilacji i wywołać skrypty kompilacji. Aby uzyskać ogólne informacje na temat korzystania z *zadań. vs. JSON*, zobacz [Dostosowywanie kompilacji i debugowania dla tworzenia aplikacji "Otwórz folder"](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio).

Zadanie ma właściwość `type`, która może mieć jedną z czterech wartości: `default`, `launch`, `remote`lub `msbuild`. Większość zadań powinna używać `launch`, chyba że jest wymagane połączenie zdalne.

## <a name="default-properties"></a>Właściwości domyślne

Właściwości domyślne są dostępne dla wszystkich typów zadań:

||||
|-|-|-|
|**Property**|**Typ**|**Opis**|
|`taskLabel`|string| (Wymagane). Określa etykietę zadania używaną w interfejsie użytkownika.|
|`appliesTo`|string| (Wymagane). Określa pliki, na których można wykonać polecenie. Obsługiwane jest użycie symboli wieloznacznych, na przykład: " *", "* . cpp", "/*. txt"|
|`contextType`|string| Dozwolone wartości: "Custom", "build", "Clean", "Rebuild". Określa, gdzie w menu kontekstowym zostanie wyświetlone zadanie. Wartość domyślna to "Custom".|
|`output`|string| Określa tag danych wyjściowych zadania.|
|`inheritEnvironments`|tablica| Określa zestaw zmiennych środowiskowych dziedziczonych z wielu źródeł. Można definiować zmienne w plikach, takich jak *pliku cmakesettings. JSON* lub *pliku cppproperties. JSON* , a następnie udostępniać je kontekstowi zadania. **Visual Studio 16,4:** : Określanie zmiennych środowiskowych dla poszczególnych zadań przy użyciu składni `env.VARIABLE_NAME`. Aby cofnąć ustawienie zmiennej, ustaw ją na wartość "null".|
|`passEnvVars`|wartość logiczna| Określa, czy dołączać dodatkowe zmienne środowiskowe do kontekstu zadania. Te zmienne różnią się od tych zdefiniowanych przy użyciu właściwości `envVars`. Wartość domyślna to "true".|

## <a name="launch-properties"></a>Właściwości uruchamiania

Gdy typ zadania to `launch`, te właściwości są dostępne:

||||
|-|-|-|
|**Property**|**Typ**|**Opis**|
|`command`|string| Określa pełną ścieżkę procesu lub skryptu do uruchomienia.|
|`args`|tablica| Określa rozdzielaną przecinkami listę argumentów przekazaną do polecenia.|
|`launchOption`|string| Dozwolone wartości: "none", "ContinueOnError", "IgnoreError". Określa, jak kontynuować polecenie w przypadku wystąpienia błędów.|
|`workingDirectory`|string| Określa katalog, w którym zostanie uruchomione polecenie. Domyślnie jest bieżącym katalogiem roboczym projektu.|
|`customLaunchCommand`|string| Określa globalne dostosowanie zakresu do zastosowania przed wykonaniem polecenia. Przydatne do ustawiania zmiennych środowiskowych, takich jak% PATH%.|
|`customLaunchCommandArgs`|string| Określa argumenty do customLaunchCommand. (Wymaga `customLaunchCommand`.)|
 `env`| Określa listę klucz-wartość niestandardowych zmiennych środowiskowych. Na przykład "myEnv": "myVal"|
|`commands`|tablica| Określa listę poleceń do wywołania w kolejności.|

### <a name="example"></a>Przykład

Następujące zadania wywołują program make *. exe* , gdy plik reguł programu make jest dostępny w folderze, a środowisko `Mingw64` zostało zdefiniowane w *pliku cppproperties. JSON*, jak pokazano w [dokumentacji schematu pliku cppproperties. JSON](cppproperties-schema-reference.md#user_defined_environments):

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

Zadania zdalne są włączane podczas instalowania środowiska wdrażania systemu Linux C++ przy użyciu obciążenia i dodawania połączenia z komputerem zdalnym za pomocą Menedżera połączeń programu Visual Studio. Zadanie zdalne uruchamia polecenia w systemie zdalnym i może również kopiować do niego pliki.

Gdy typ zadania to `remote`, te właściwości są dostępne:

||||
|-|-|-|
|**Property**|**Typ**|**Opis**|
|`remoteMachineName`|string|Nazwa maszyny zdalnej. Musi być zgodna z nazwą komputera w **Menedżerze połączeń**.|
|`command`|string|Polecenie do wysłania do komputera zdalnego. Polecenia domyślne są wykonywane w katalogu $HOME w systemie zdalnym.|
|`remoteWorkingDirectory`|string|Bieżący katalog roboczy na komputerze zdalnym.|
|`localCopyDirectory`|string|Katalog lokalny, który ma zostać skopiowany na komputer zdalny. Domyślnie jest bieżącym katalogiem roboczym.|
|`remoteCopyDirectory`|string|Katalog na komputerze zdalnym, do którego kopiowany jest `localCopyDirectory`.|
|`remoteCopyMethod`|string| Metoda używana do kopiowania. Dozwolone wartości: "none", "SFTP", "rsync". rsync jest zalecane w przypadku dużych projektów.|
|`remoteCopySourcesOutputVerbosity`|string| Dozwolone wartości: "normal", "verbose", "Diagnostic".|
|`rsyncCommandArgs`|string|Wartość domyślna to "-t--Delete".|
|`remoteCopyExclusionList`|tablica|Rozdzielana przecinkami lista plików w `localCopyDirectory`, które mają zostać wykluczone z operacji kopiowania.|

### <a name="example"></a>Przykład

Następujące zadanie zostanie wyświetlone w menu kontekstowym po kliknięciu prawym przyciskiem myszy *Main. cpp* w **Eksplorator rozwiązań**. Jest to zależne od maszyny zdalnej o nazwie `ubuntu` w **Menedżerze połączeń**. Zadanie Kopiuje bieżący otwarty folder w programie Visual Studio do katalogu `sample` na komputerze zdalnym, a następnie wywołuje polecenie g + + w celu skompilowania programu.

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

Gdy typ zadania to `msbuild`, te właściwości są dostępne:

||||
|-|-|-|
|**Property**|**Typ**|**Opis**|
|`verbosity`|string| Określa wartość verbosityAllowed danych wyjściowych kompilacji projektu programu MSBuild: "quiet", "minimalny", "normalny", "szczegółowy", "Diagnostyka".|
|`toolsVersion`|string| Określa wersję zestawu narzędzi do kompilowania projektu, na przykład "2,0", "3,5", "4,0", "Current". Wartość domyślna to "Current".|
|`globalProperties`|Obiekt programu|Określa listę klucz-wartość właściwości globalnych do przekazania do projektu, na przykład "Konfiguracja": "wersja"|
|`properties`|Obiekt programu| Określa listę klucz-wartość dodatkowych właściwości tylko dla projektu.|
|`targets`|tablica| Określa listę elementów docelowych do wywołania, w kolejności, w projekcie. Domyślny element docelowy projektu jest używany, jeśli nie określono żadnego z nich.|
