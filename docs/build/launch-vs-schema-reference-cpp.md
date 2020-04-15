---
title: odwołanie do schematu launch.vs.json (C++)
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: ff4713642ab95a9bbc31f1a06236de459e53f9c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323052"
---
# <a name="launchvsjson-schema-reference-c"></a>odwołanie do schematu launch.vs.json (C++)

Użyj pliku *launch.vs.json,* aby skonfigurować parametry debugowania. Aby utworzyć plik. kliknij prawym przyciskiem myszy plik wykonywalny w **Eksploratorze rozwiązań** i wybierz polecenie **Debugowanie i uruchamianie ustawień**. Wybierz opcję, która najbardziej pasuje do projektu, a następnie użyj następujących właściwości, aby zmodyfikować konfigurację w razie potrzeby. Aby uzyskać więcej informacji na temat debugowania projektów CMake, zobacz [Konfigurowanie sesji debugowania CMake](/cpp/build/configure-cmake-debugging-sessions).

## <a name="default-properties"></a>Właściwości domyślne

||||
|-|-|-|
|**Właściwość**|**Typ**|**Opis**|
|`name`|ciąg|Określa nazwę wpisu z listy rozwijanej Debug target.|
|`type`|ciąg|Określa, czy projekt jest biblioteką DLL, czy programem .exe (Domyślne dla programu .exe)|
|`project`|ciąg|Określa względną ścieżkę do pliku projektu.|
|`projectTarget`|ciąg|Określa opcjonalny obiekt docelowy `project`wywoływany podczas tworzenia . To `projectTarget` musi już istnieć i dopasować nazwę w **debugowania docelowego** listy rozwijanej.|
|`debugType`|ciąg|Określa tryb debugowania zgodnie z typem kodu (natywnego, zarządzanego lub mieszanego). Zostanie to wykryte automatycznie, chyba że ten parametr jest ustawiony. Dozwolone wartości: "native", "managed", "mixed".|
|`inheritEnvironments`|tablica|Określa zestaw zmiennych środowiskowych dziedziczonych z wielu źródeł. Można zdefiniować niektóre zmienne w plikach, takich jak *CMakeSettings.json* lub *CppProperties.json* i udostępnić je do debugowania kontekstu.  **Visual Studio 16.4:**: Określ zmienne środowiskowe `env.VARIABLE_NAME` na podstawie na cel przy użyciu składni. Aby odstawić zmienną, ustaw ją na "null".|
|`args`|tablica|Określa argumenty wiersza polecenia przekazywane do uruchomionego programu.|
|`currentDir`|ciąg|Określa pełną ścieżkę katalogu do obiektu docelowego kompilacji. Zostanie to wykryte automatycznie, chyba że ten parametr jest ustawiony.|
|`noDebug`|wartość logiczna|Określa, czy debugować uruchomiony program. Wartość domyślna dla `false` tego parametru jest, jeśli nie jest określona.|
|`stopOnEntry`|wartość logiczna|Określa, czy przerwać proces natychmiast po uruchomieniu i dołączyć debuger. Wartością domyślną dla `false`tego parametru jest .|
|`remoteMachine`|ciąg|Określa nazwę komputera zdalnego, na którym program jest uruchamiany.|
|`env`|tablica| Określa listę klucz-wartość niestandardowych zmiennych środowiskowych. env:{"myEnv":"myVal"}.|
|`portName`|ciąg|Określa nazwę portu podczas dołączania do uruchomionego procesu.|
|`buildConfigurations`|tablica| Para klucz-wartość, która określa nazwę trybu kompilacji, aby zastosować konfiguracje. Na przykład `Debug` `Release` lub i konfiguracje do użycia zgodnie z wybranym trybem kompilacji.

## <a name="c-linux-properties"></a>Właściwości systemu Linux w języku C++

||||
|-|-|-|
|**Właściwość**|**Typ**|**Opis**|
|`program`|ciąg|Pełna ścieżka do programu wykonywalnego na komputerze zdalnym. W przypadku korzystania z `${debugInfo.fullTargetPath}` CMake makro może służyć jako wartość tego pola.|
|`processId`|liczba całkowita|Opcjonalny identyfikator procesu, do aby dołączyć debugera do.|
|`sourceFileMap`|obiekt|Opcjonalne mapowania plików źródłowych przekazywane do aparatu debugowania. Format: `{ "\<Compiler source location>": "\<Editor source location>" }` `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`lub . Przykład: `{ "/home/user/foo": "C:\\foo" }` lub `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`. Zobacz [Opcje mapy plików źródłowych](#source_file_map_options).|
|`additionalProperties`|ciąg|Jeden ze źródełFileMapOptions. (Patrz poniżej).|
|`MIMode`|ciąg|Wskazuje typ debugera konsoli z włączoną funkcją MI, z którą połączy się midebugengine. Dozwolone wartości to "gdb", "lldb".|
|`args`|tablica|Argumenty wiersza polecenia przekazywane do programu.|
|`environment`|tablica|Zmienne środowiskowe, aby dodać do środowiska dla programu. Przykład: [ { "name": "kałamarnica", "wartość": "clam" } ].|
|`targetArchitecture`|ciąg|Architektura debuggee. Zostanie to wykryte automatycznie, chyba że ten parametr jest ustawiony. Dozwolone wartości to x86, arm, arm64, mips, x64, amd64, x86_64.|
|`visualizerFile`|ciąg|.natvis plik do użycia podczas debugowania tego procesu. Ta opcja nie jest zgodna z gdb ładne drukowanie. Zobacz "showDisplayString", jeśli używasz tego ustawienia.|
|`showDisplayString`|wartość logiczna|Po określeniu pliku wizualizatora showDisplayString włączy ciąg wyświetlania. Włączenie tej opcji może spowodować mniejszą wydajność podczas debugowania.|
|`remoteMachineName`|ciąg|Zdalna maszyna Linux, która obsługuje gdb i program do debugowania. Użyj Menedżera połączeń do dodawania nowych maszyn z systemem Linux. W przypadku korzystania z `${debugInfo.remoteMachineName}` CMake makro może służyć jako wartość tego pola.|
|`cwd`|ciąg|Katalog roboczy obiektu docelowego na komputerze zdalnym. W przypadku korzystania z `${debugInfo.defaultWorkingDirectory}` CMake makro może służyć jako wartość tego pola. Wartością domyślną jest katalog główny zdalnego obszaru roboczego, chyba że zostanie zastąpiony w pliku *CMakeLists.txt.*|
|`miDebuggerPath`|ciąg|Ścieżka do debugera z włączoną funkcją MI (na przykład gdb). Gdy nie określono, będzie najpierw przeszukiwać PATH dla debugera.|
|`miDebuggerServerAddress`|ciąg|Adres sieciowy serwera debugera z włączoną funkcją MI, z który ma się połączyć. Przykład: localhost:1234.|
|`setupCommands`|tablica|Co najmniej jedno polecenie GDB/LLDB do wykonania w celu skonfigurowania debugera bazowego. Przykład: `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. Zobacz [Uruchamianie poleceń konfiguracji](#launch_setup_commands).|
|`customLaunchSetupCommands`|tablica|Jeśli to możliwe, zastępuje to domyślne polecenia używane do uruchamiania obiektu docelowego innymi poleceniami. Na przykład może to być "-target-attach" w celu dołączenia do procesu docelowego. Pusta lista poleceń zastępuje polecenia uruchamiania niczym, co może być przydatne, jeśli debuger jest udostępniany jako opcje wiersza polecenia. Przykład: `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|ciąg|Polecenie do wykonania po debuger jest w pełni skonfigurowany, aby spowodować uruchomienie procesu docelowego. Dozwolone wartości to "exec-run", "exec-continue", "None". Wartością domyślną jest "exec-run".|
|`debugServerPath`|ciąg|Opcjonalna pełna ścieżka do serwera debugowania do uruchomienia. Wartość domyślna ma wartość null.|
|`debugServerArgs`|ciąg|Opcjonalne argumenty serwera debugowania. Wartość domyślna ma wartość null.|
|`filterStderr`|wartość logiczna|Szukaj strumienia stderr dla wzorca uruchomionego na serwerze i log stderr do debugowania danych wyjściowych. Wartość domyślna to `false`.|
|`coreDumpPath`|ciąg|Opcjonalna pełna ścieżka do pliku zrzutu podstawowego dla określonego programu. Wartość domyślna ma wartość null.|
zewnętrznaSpoda|wartość logiczna|Jeśli true, konsola jest uruchamiany dla debuggee. Jeśli `false`nie zostanie uruchomiona żadna konsola. Wartość domyślna to `false`. UWAGA: Ta opcja jest ignorowana w niektórych przypadkach ze względów technicznych.|
|`pipeTransport`|ciąg|W chwili obecnej informuje debugera, aby połączyć się z komputerem zdalnym przy użyciu innego pliku wykonywalnego jako potoku, który będzie przekazywania standardowych wejściów/danych wyjściowych między programem Visual Studio i debugerem z włączoną funkcją MI (na przykład gdb). Dozwolone wartości: jedna lub więcej [opcji transportu rur](#pipe_transport_options).|

## <a name="launch-setup-commands"></a><a name="launch_setup_commands"></a>Uruchamianie poleceń konfiguracji

Używany z `setupCommands` właściwością:

||||
|-|-|-|
|`text`|ciąg|Polecenie debugera do wykonania.|
|`description`|ciąg|Opcjonalny opis polecenia.|
|`ignoreFailures`|wartość logiczna|Jeśli true, błędy z polecenia powinny być ignorowane. Wartość domyślna to `false`.|

## <a name="pipe-transport-options"></a><a name = "pipe_transport_options"></a>Opcje transportu rur

Używany z `pipeTransport` właściwością:

||||
|-|-|-|
|`pipeCwd`|ciąg|W pełni kwalifikowana ścieżka do katalogu roboczego dla programu potokowego.|
|`pipeProgram`|ciąg|W pełni kwalifikowane polecenie potoku do wykonania.|
|`pipeArgs`|tablica|Argumenty wiersza polecenia przekazywane do programu potoku w celu skonfigurowania połączenia.|
|`debuggerPath`|ciąg|Pełna ścieżka do debugera na komputerze docelowym, na przykład /usr/bin/gdb.|
|`pipeEnv`|obiekt|Zmienne środowiskowe przekazywane do programu potoku.|
|`quoteArgs`|wartość logiczna|Jeśli poszczególne argumenty zawierają znaki (takie jak spacje lub karty), należy je cytowało? Jeśli `false`polecenie debugera nie będzie już automatycznie cytowane. Wartość domyślna to `true`.|

## <a name="source-file-map-options"></a><a name="source_file_map_options"></a>Opcje mapy plików źródłowych

Użyj z `sourceFileMap` właściwością:

||||
|-|-|-|
|`editorPath`|ciąg|Lokalizacja kodu źródłowego dla edytora, aby zlokalizować.|
|`useForBreakpoints`|wartość logiczna|Podczas ustawiania punktów przerwania, to mapowanie źródła powinny być używane. Jeśli `false`do ustawiania punktów przerwania używana jest tylko nazwa pliku i numer wiersza. Jeśli `true`punkty przerwania zostaną ustawione z pełną ścieżką do pliku i numeru wiersza tylko wtedy, gdy używane jest to mapowanie źródłowe. W przeciwnym razie tylko nazwa pliku i numer wiersza będą używane podczas ustawiania punktów przerwania. Wartość domyślna to `true`.|
