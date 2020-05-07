---
title: Uruchom. vs. JSON — odwołanie do schematu (C++)
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
# <a name="launchvsjson-schema-reference-c"></a>Uruchom. vs. JSON — odwołanie do schematu (C++)

Aby skonfigurować parametry debugowania, użyj pliku *Launch. vs. JSON* . , Aby utworzyć plik. Kliknij prawym przyciskiem myszy plik wykonywalny w **Eksplorator rozwiązań** i wybierz polecenie **Debuguj i Uruchom ustawienia**. Wybierz opcję, która najlepiej pasuje do Twojego projektu, a następnie użyj następujących właściwości, aby zmodyfikować konfigurację zgodnie z potrzebami. Aby uzyskać więcej informacji na temat debugowania projektów CMake, zobacz [Konfigurowanie CMAKE debugowania sesji](/cpp/build/configure-cmake-debugging-sessions).

## <a name="default-properties"></a>Właściwości domyślne

||||
|-|-|-|
|**Właściwość**|**Typ**|**Opis**|
|`name`|ciąg|Określa nazwę wpisu na liście rozwijanej elementu docelowego debugowania.|
|`type`|ciąg|Określa, czy projekt jest biblioteką DLL, czy exe (wartość domyślna to. exe)|
|`project`|ciąg|Określa ścieżkę względną do pliku projektu.|
|`projectTarget`|ciąg|Określa opcjonalny element docelowy wywoływany podczas `project`kompilowania. Ta `projectTarget` nazwa musi już istnieć i być zgodna z nazwą z listy rozwijanej **elementu docelowego debugowania** .|
|`debugType`|ciąg|Określa tryb debugowania zgodnie z typem kodu (natywnym, zarządzanym lub mieszanym). Zostanie ono automatycznie wykryte, chyba że ten parametr jest ustawiony. Dozwolone wartości: "native", "Managed", "Mixed".|
|`inheritEnvironments`|tablica|Określa zestaw zmiennych środowiskowych dziedziczonych z wielu źródeł. Można zdefiniować niektóre zmienne w plikach, takie jak *pliku cmakesettings. JSON* lub *pliku cppproperties. JSON* i udostępnić je kontekstowi debugowania.  **Visual Studio 16,4:**: Określ zmienne środowiskowe dla poszczególnych elementów docelowych przy użyciu `env.VARIABLE_NAME` składni. Aby cofnąć ustawienie zmiennej, ustaw ją na wartość "null".|
|`args`|tablica|Określa argumenty wiersza polecenia przekazane do uruchomionego programu.|
|`currentDir`|ciąg|Określa pełną ścieżkę katalogu do celu kompilacji. Zostanie ono automatycznie wykryte, chyba że ten parametr jest ustawiony.|
|`noDebug`|wartość logiczna|Określa, czy ma być debugowany uruchomiony program. Wartość domyślna dla tego parametru jest Jeśli `false` nie została określona.|
|`stopOnEntry`|wartość logiczna|Określa, czy wkrótce ma zostać przerwane, gdy proces zostanie uruchomiony i zostanie dołączony debuger. Wartość domyślna tego parametru to `false`.|
|`remoteMachine`|ciąg|Określa nazwę komputera zdalnego, na którym uruchomiono program.|
|`env`|tablica| Określa listę klucz-wartość niestandardowych zmiennych środowiskowych. env: {"myEnv": "myVal"}.|
|`portName`|ciąg|Określa nazwę portu podczas dołączania do uruchomionego procesu.|
|`buildConfigurations`|tablica| Para klucz-wartość, która określa nazwę trybu kompilacji, aby zastosować konfiguracje. Na przykład `Debug` lub `Release` i konfiguracje, które mają być używane zgodnie z wybranym trybem kompilacji.

## <a name="c-linux-properties"></a>Właściwości języka C++ dla systemu Linux

||||
|-|-|-|
|**Właściwość**|**Typ**|**Opis**|
|`program`|ciąg|Pełna ścieżka do pliku wykonywalnego programu na maszynie zdalnej. W przypadku korzystania z CMake, `${debugInfo.fullTargetPath}` makro może być używane jako wartość tego pola.|
|`processId`|liczba całkowita|Opcjonalny identyfikator procesu, do którego ma zostać dołączony debuger.|
|`sourceFileMap`|obiekt|Opcjonalne mapowania plików źródłowych przenoszone do aparatu debugowania. Format: `{ "\<Compiler source location>": "\<Editor source location>" }` lub `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`. Przykład: `{ "/home/user/foo": "C:\\foo" }` lub `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`. Zobacz [Opcje mapy plików źródłowych](#source_file_map_options).|
|`additionalProperties`|ciąg|Jeden z sourceFileMapOptions. (Zobacz poniżej).|
|`MIMode`|ciąg|Wskazuje typ debugera konsolowego z włączoną funkcją MI, z którym będzie się łączyć MIDebugEngine. Dozwolone wartości to "GDB", "LLDB".|
|`args`|tablica|Argumenty wiersza polecenia przekazane do programu.|
|`environment`|tablica|Zmienne środowiskowe do dodania do środowiska programu. Przykład: [{"name": "Squid", "value": "generacja"}].|
|`targetArchitecture`|ciąg|Architektura debugowanego obiektu. Zostanie ono automatycznie wykryte, chyba że ten parametr jest ustawiony. Dozwolone wartości to x86, ARM, arm64, MIPS, x64, amd64, x86_64.|
|`visualizerFile`|ciąg|plik. Natvis, który ma być używany podczas debugowania tego procesu. Ta opcja nie jest zgodna z GDBą drukowaniem. Jeśli korzystasz z tego ustawienia, zobacz "showDisplayString".|
|`showDisplayString`|wartość logiczna|Gdy visualizerFile jest określony, showDisplayString zostanie włączony ciąg wyświetlania. Włączenie tej opcji może spowodować wolniejszą wydajność podczas debugowania.|
|`remoteMachineName`|ciąg|Zdalny komputer z systemem Linux, który obsługuje GDB i program do debugowania. Użyj Menedżera połączeń do dodawania nowych maszyn z systemem Linux. W przypadku korzystania z CMake, `${debugInfo.remoteMachineName}` makro może być używane jako wartość tego pola.|
|`cwd`|ciąg|Katalog roboczy obiektu docelowego na komputerze zdalnym. W przypadku korzystania z CMake, `${debugInfo.defaultWorkingDirectory}` makro może być używane jako wartość tego pola. Wartość domyślna to zdalny katalog główny obszaru roboczego, chyba że zostanie zastąpiony w pliku *CMakeLists. txt* .|
|`miDebuggerPath`|ciąg|Ścieżka do debugera z włączoną funkcją MI (na przykład GDB). Jeśli nie zostanie określony, zostanie wyszukany najpierw ścieżka dla debugera.|
|`miDebuggerServerAddress`|ciąg|Adres sieciowy serwera debugera z włączoną funkcją MI, z którym ma zostać nawiązane połączenie. Przykład: localhost: 1234.|
|`setupCommands`|tablica|Jedno lub więcej poleceń GDB/LLDB do wykonania w celu skonfigurowania podstawowego debugera. Przykład: `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. Zobacz [Uruchamianie poleceń Instalatora](#launch_setup_commands).|
|`customLaunchSetupCommands`|tablica|Jeśli ta wartość jest określona, zastępuje domyślne polecenia używane do uruchamiania obiektu docelowego z innymi poleceniami. Na przykład może to być "-Target-Attach" w celu dołączenia do procesu docelowego. Pusta lista poleceń zastępuje polecenia uruchamiania nie tylko, co może być przydatne, jeśli w debugerze są dostępne opcje uruchamiania jako opcje wiersza polecenia. Przykład: `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|ciąg|Polecenie do wykonania po pełnej konfiguracji debugera, aby można było uruchomić proces docelowy. Dozwolone wartości to "exec-Run", "exec-Continue", "none". Wartość domyślna to "exec-Run".|
|`debugServerPath`|ciąg|Opcjonalna pełna ścieżka do serwera debugowania do uruchomienia. Wartością domyślną jest null.|
|`debugServerArgs`|ciąg|Opcjonalne argumenty serwera debugowania. Wartością domyślną jest null.|
|`filterStderr`|wartość logiczna|Wyszukaj strumień STDERR dla wzorca uruchomionego na serwerze i zdarzeń log stderr, aby debugować dane wyjściowe. Wartość domyślna `false`to.|
|`coreDumpPath`|ciąg|Opcjonalna pełna ścieżka do podstawowego pliku zrzutu dla określonego programu. Wartością domyślną jest null.|
externalConsole|wartość logiczna|W przypadku wartości true konsola jest uruchamiana dla debugowanego obiektu. Jeśli `false`konsola nie zostanie uruchomiona. Wartość domyślna `false`to. Uwaga: Ta opcja jest ignorowana w niektórych przypadkach ze względów technicznych.|
|`pipeTransport`|ciąg|Jeśli jest obecny, oznacza to, że debuger nawiązuje połączenie z komputerem zdalnym przy użyciu innego pliku wykonywalnego jako potoku przekazującego standardowe dane wejściowe/wyjściowe między programem Visual Studio i debugerem z włączoną funkcją MI (na przykład GDB). Dozwolone wartości: co najmniej jedna [Opcja transportu potoku](#pipe_transport_options).|

## <a name="launch-setup-commands"></a><a name="launch_setup_commands"></a>Uruchom polecenia Instalatora

Używane z `setupCommands` właściwością:

||||
|-|-|-|
|`text`|ciąg|Polecenie debugera do wykonania.|
|`description`|ciąg|Opcjonalny opis polecenia.|
|`ignoreFailures`|wartość logiczna|W przypadku wartości true błędy polecenia powinny być ignorowane. Wartość domyślna `false`to.|

## <a name="pipe-transport-options"></a><a name = "pipe_transport_options"></a>Opcje transportu potoku

Używane z `pipeTransport` właściwością:

||||
|-|-|-|
|`pipeCwd`|ciąg|W pełni kwalifikowana ścieżka do katalogu roboczego dla programu potoku.|
|`pipeProgram`|ciąg|W pełni kwalifikowana potoku polecenie do wykonania.|
|`pipeArgs`|tablica|Argumenty wiersza polecenia przekazane do programu potoku w celu skonfigurowania połączenia.|
|`debuggerPath`|ciąg|Pełna ścieżka do debugera na komputerze docelowym, na przykład/usr/bin/GDB.|
|`pipeEnv`|obiekt|Zmienne środowiskowe przechodzą do programu potoku.|
|`quoteArgs`|wartość logiczna|Jeśli poszczególne argumenty zawierają znaki (takie jak spacje lub tabulatory), powinny być ujęte w cudzysłów? Jeśli `false`polecenie debugera nie zostanie już automatycznie ujęte w cudzysłów. Wartość domyślna to `true`.|

## <a name="source-file-map-options"></a><a name="source_file_map_options"></a>Opcje mapy plików źródłowych

Użyj z `sourceFileMap` właściwością:

||||
|-|-|-|
|`editorPath`|ciąg|Lokalizacja kodu źródłowego dla edytora, który ma zostać zlokalizowany.|
|`useForBreakpoints`|wartość logiczna|Podczas ustawiania punktów przerwania należy użyć tego mapowania źródła. Jeśli `false`do ustawiania punktów przerwania jest używana tylko nazwa pliku i numer wiersza. Jeśli `true`, punkty przerwania zostaną ustawione z pełną ścieżką do pliku i numerem wiersza tylko wtedy, gdy używane jest mapowanie źródłowe. W przeciwnym razie tylko nazwa pliku i numer wiersza będą używane podczas ustawiania punktów przerwania. Wartość domyślna to `true`.|
