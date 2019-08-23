---
title: Uruchom. vs. JSON — odwołanie doC++schematu ()
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: 362a329289107f74cca2f20af62c8a28b4192575
ms.sourcegitcommit: ace42fa67e704d56d03c03745b0b17d2a5afeba4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69978442"
---
# <a name="launchvsjson-schema-reference-c"></a>Uruchom. vs. JSON — odwołanie doC++schematu ()

Aby skonfigurować parametry debugowania, użyj pliku *Launch. vs. JSON* . , Aby utworzyć plik. Kliknij prawym przyciskiem myszy plik wykonywalny w **Eksplorator rozwiązań** i wybierz polecenie **Debuguj i Uruchom ustawienia**. Wybierz opcję, która najlepiej pasuje do Twojego projektu, a następnie użyj następujących właściwości, aby zmodyfikować konfigurację zgodnie z potrzebami:

## <a name="default-properties"></a>Właściwości domyślne

||||
|-|-|-|
|**Property**|**Typ**|**Opis**|
|`name`|string|Określa nazwę wpisu na liście rozwijanej elementu docelowego debugowania.|
|`type`|string|Określa, czy projekt jest biblioteką DLL, czy exe (wartość domyślna to. exe)|
|`project`|string|Określa ścieżkę względną do pliku projektu.|
|`projectTarget`|string|Określa opcjonalny element docelowy wywoływany podczas `project`kompilowania. Ta `projectTarget` nazwa musi już istnieć i być zgodna z nazwą z listy rozwijanej **elementu docelowego debugowania** .|
|`debugType`|string|Określa tryb debugowania zgodnie z typem kodu (natywnym, zarządzanym lub mieszanym). Zostanie ono automatycznie wykryte, chyba że ten parametr jest ustawiony. Dozwolone wartości: "native", "Managed", "Mixed".|
|`inheritEnvironments`|tablica|Określa zestaw zmiennych środowiskowych dziedziczonych z wielu źródeł. Można zdefiniować niektóre zmienne w plikach, takie jak pliku cmakesettings. JSON lub pliku cppproperties. JSON i udostępnić je kontekstowi debugowania|
|`args`|tablica|Określa argumenty wiersza polecenia przekazane do uruchomionego programu.|
|`currentDir`|string|Określa pełną ścieżkę katalogu do celu kompilacji. Zostanie ono automatycznie wykryte, chyba że ten parametr jest ustawiony.|
|`noDebug`|wartość logiczna|Określa, czy ma być debugowany uruchomiony program. Wartość domyślna dla tego parametru jest Jeśli `false` nie została określona.|
|`stopOnEntry`|wartość logiczna|Określa, czy wkrótce ma zostać przerwane, gdy proces zostanie uruchomiony i zostanie dołączony debuger. Wartość domyślna tego parametru to `false`.|
|`remoteMachine`|string|Określa nazwę komputera zdalnego, na którym uruchomiono program.|
|`env`|tablica| Określa listę klucz-wartość niestandardowych zmiennych środowiskowych. env: {"myEnv": "myVal"}.|
|`portName`|string|Określa nazwę portu podczas dołączania do uruchomionego procesu.|
|`buildConfigurations`|tablica| Para klucz-wartość, która określa nazwę trybu kompilacji, aby zastosować konfiguracje. Na przykład `Debug` lub `Release` i konfiguracje, które mają być używane zgodnie z wybranym trybem kompilacji.

## <a name="c-linux-properties"></a>C++Właściwości systemu Linux

||||
|-|-|-|
|**Property**|**Typ**|**Opis**|
|`program`|string|Pełna ścieżka do pliku wykonywalnego programu na maszynie zdalnej. W przypadku korzystania z cmake, `${debugInfo.fullTargetPath}` makro może być używane jako wartość tego pola.|
|`processId`|integer|Opcjonalny identyfikator procesu, do którego ma zostać dołączony debuger.|
|`sourceFileMap`|object|Opcjonalne mapowania plików źródłowych przenoszone do aparatu debugowania. Format: `{ "\<Compiler source location>": "\<Editor source location>" }` lub `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`. Przykład: `{ "/home/user/foo": "C:\\foo" }` lub `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`. Zobacz [Opcje mapy plików źródłowych](#source_file_map_options).|
|`additionalProperties`|string|Jeden z sourceFileMapOptions. (Zobacz poniżej).|
|`MIMode`|string|Wskazuje typ debugera konsolowego z włączoną funkcją MI, z którym będzie się łączyć MIDebugEngine. Dozwolone wartości to "GDB", "LLDB".|
|`args`|tablica|Argumenty wiersza polecenia przekazane do programu.|
|`environment`|tablica|Zmienne środowiskowe do dodania do środowiska programu. Przykład: [{"name": "Squid", "value": "generacja"}].|
|`targetArchitecture`|string|Architektura debugowanego obiektu. Zostanie ono automatycznie wykryte, chyba że ten parametr jest ustawiony. Dozwolone wartości to x86, ARM, arm64, MIPS, x64, amd64, x86_64.|
|`visualizerFile`|string|plik. Natvis, który ma być używany podczas debugowania tego procesu. Ta opcja nie jest zgodna z GDBą drukowaniem. Jeśli korzystasz z tego ustawienia, zobacz "showDisplayString".|
|`showDisplayString`|wartość logiczna|Gdy visualizerFile jest określony, showDisplayString zostanie włączony ciąg wyświetlania. Włączenie tej opcji może spowodować wolniejszą wydajność podczas debugowania.|
|`remoteMachineName`|string|Zdalny komputer z systemem Linux, który obsługuje GDB i program do debugowania. Użyj Menedżera połączeń do dodawania nowych maszyn z systemem Linux. W przypadku korzystania z cmake, `${debugInfo.remoteMachineName}` makro może być używane jako wartość tego pola.|
|`cwd`|string|Katalog roboczy obiektu docelowego na komputerze zdalnym. W przypadku korzystania z cmake, `${debugInfo.defaultWorkingDirectory}` makro może być używane jako wartość tego pola. Wartość domyślna to zdalny katalog główny obszaru roboczego, chyba że zostanie zastąpiony w pliku *CMakeLists. txt* .|
|`miDebuggerPath`|string|Ścieżka do debugera z włączoną funkcją MI (na przykład GDB). Jeśli nie zostanie określony, zostanie wyszukany najpierw ścieżka dla debugera.|
|`miDebuggerServerAddress`|string|Adres sieciowy serwera debugera z włączoną funkcją MI, z którym ma zostać nawiązane połączenie. Przykład: localhost: 1234.|
|`setupCommands`|tablica|Jedno lub więcej poleceń GDB/LLDB do wykonania w celu skonfigurowania podstawowego debugera. Przykład: `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. Zobacz [Uruchamianie poleceń Instalatora](#launch_setup_commands).|
|`customLaunchSetupCommands`|tablica|Jeśli ta wartość jest określona, zastępuje domyślne polecenia używane do uruchamiania obiektu docelowego z innymi poleceniami. Na przykład może to być "-Target-Attach" w celu dołączenia do procesu docelowego. Pusta lista poleceń zastępuje polecenia uruchamiania nie tylko, co może być przydatne, jeśli w debugerze są dostępne opcje uruchamiania jako opcje wiersza polecenia. Przykład: `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|string|Polecenie do wykonania po pełnej konfiguracji debugera, aby można było uruchomić proces docelowy. Dozwolone wartości to "exec-Run", "exec-Continue", "none". Wartość domyślna to "exec-Run".|
|`debugServerPath`|string|Opcjonalna pełna ścieżka do serwera debugowania do uruchomienia. Wartością domyślną jest null.|
|`debugServerArgs`|string|Opcjonalne argumenty serwera debugowania. Wartością domyślną jest null.|
|`filterStderr`|wartość logiczna|Wyszukaj strumień STDERR dla wzorca uruchomionego na serwerze i zdarzeń log stderr, aby debugować dane wyjściowe. Wartość domyślna to `false`.|
|`coreDumpPath`|string|Opcjonalna pełna ścieżka do podstawowego pliku zrzutu dla określonego programu. Wartością domyślną jest null.|
externalConsole|wartość logiczna|W przypadku wartości true konsola jest uruchamiana dla debugowanego obiektu. Jeśli `false`konsola nie zostanie uruchomiona. Wartość domyślna to `false`. KORYGUJĄC Ta opcja jest ignorowana w niektórych przypadkach ze względów technicznych.|
|`pipeTransport`|string|Jeśli jest obecny, oznacza to, że debuger nawiązuje połączenie z komputerem zdalnym przy użyciu innego pliku wykonywalnego jako potoku przekazującego standardowe dane wejściowe/wyjściowe między programem Visual Studio i debugerem z włączoną funkcją MI (na przykład GDB). Dozwolone wartości: co najmniej jedna [Opcja transportu potoku](#pipe_transport_options).|


## <a name="launch_setup_commands"></a>Uruchom polecenia Instalatora

Używane z `setupCommands` właściwością:

||||
|-|-|-|
|`text`|string|Polecenie debugera do wykonania.|
|`description`|string|Opcjonalny opis polecenia.|
|`ignoreFailures`|wartość logiczna|W przypadku wartości true błędy polecenia powinny być ignorowane. Wartość domyślna to `false`.|

## <a name = "pipe_transport_options"></a>Opcje transportu potoku

Używane z `pipeTransport` właściwością:

||||
|-|-|-|
|`pipeCwd`|string|W pełni kwalifikowana ścieżka do katalogu roboczego dla programu potoku.|
|`pipeProgram`|string|W pełni kwalifikowana potoku polecenie do wykonania.|
|`pipeArgs`|tablica|Argumenty wiersza polecenia przekazane do programu potoku w celu skonfigurowania połączenia.|
|`debuggerPath`|string|Pełna ścieżka do debugera na komputerze docelowym, na przykład/usr/bin/GDB.|
|`pipeEnv`|object|Zmienne środowiskowe przechodzą do programu potoku.|
|`quoteArgs`|wartość logiczna|Jeśli poszczególne argumenty zawierają znaki (takie jak spacje lub tabulatory), powinny być ujęte w cudzysłów? Jeśli `false`polecenie debugera nie zostanie już automatycznie ujęte w cudzysłów. Wartość domyślna to `true`.|

## <a name="source_file_map_options"></a>Opcje mapy plików źródłowych

Użyj z `sourceFileMap` właściwością:

||||
|-|-|-|
|`editorPath`|string|Lokalizacja kodu źródłowego dla edytora, który ma zostać zlokalizowany.|
|`useForBreakpoints`|wartość logiczna|Podczas ustawiania punktów przerwania należy użyć tego mapowania źródła. Jeśli `false`do ustawiania punktów przerwania jest używana tylko nazwa pliku i numer wiersza. Jeśli `true`, punkty przerwania zostaną ustawione z pełną ścieżką do pliku i numerem wiersza tylko wtedy, gdy używane jest mapowanie źródłowe. W przeciwnym razie tylko nazwa pliku i numer wiersza będą używane podczas ustawiania punktów przerwania. Wartość domyślna to `true`.|
