---
title: Konfigurowanie sesji debugowania CMake w programie Visual Studio
description: W tym artykule opisano sposób konfigurowania ustawień debugera CMake za pomocą programu Visual Studio.
ms.date: 04/02/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 8364e5b3dd3316a4ed7e754a104a14373040aa6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328849"
---
# <a name="configure-cmake-debugging-sessions"></a>Konfigurowanie sesji debugowania narzędzia CMake

::: moniker range="vs-2015"

Natywna pomoc techniczna CMake jest dostępna w programie Visual Studio 2017 i nowszych. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end

::: moniker range=">=vs-2017"

Wszystkie obiekty docelowe wykonywalne CMake są wyświetlane w rozwijaniu **elementu startowego** na pasku narzędzi **Ogólne.** Wybierz jedną, aby rozpocząć sesję debugowania i uruchomić debuger.

![CKszt elementu startowego rozwijanego](media/cmake-startup-item-dropdown.png "CKszt elementu startowego rozwijanego")

Można również uruchomić sesję debugowania z Eksploratora rozwiązań. Najpierw przełącz się do **widoku obiektów docelowych CMake** w oknie **Eksploratora rozwiązań.**

![CNakładuj widok cele](media/cmake-targets-view.png  "CNajmów elementy menu Widok obiektów")

Następnie kliknij prawym przyciskiem myszy plik wykonywalny i wybierz opcję **Debug .** To polecenie automatycznie uruchamia debugowanie wybranego obiektu docelowego na podstawie aktywnej konfiguracji.

## <a name="customize-debugger-settings"></a>Dostosowywanie ustawień debugera

Można dostosować ustawienia debugera dla dowolnego pliku wykonywalnego CMake cel w projekcie. Znajdują się one w pliku konfiguracyjnym o nazwie *`.vs`* *launch.vs.json*, znajdującym się w folderze w katalogu głównym projektu. Plik konfiguracji uruchamiania jest przydatne w większości scenariuszy debugowania, ponieważ można skonfigurować i zapisać szczegóły konfiguracji debugowania. Istnieją trzy punkty wejścia do tego pliku:

- **Menu debugowania:** Wybierz z menu głównego **pozycję Debugowanie > debugowania i uruchamiania dla ${activeDebugTarget}** w celu dostosowania konfiguracji debugowania specyficznej dla aktywnego obiektu docelowego debugowania. Jeśli nie wybrano celu debugowania, ta opcja jest wyszarzony.

![Punkt wejścia menu debugowania](media/cmake-debug-menu.png "Punkt wejścia menu debugowania")

- **Widok celów:** Przejdź do **widoku obiektów docelowych** w Eksploratorze rozwiązań. Następnie kliknij prawym przyciskiem myszy cel debugowania i wybierz pozycję **Dodaj konfigurację debugowania,** aby dostosować konfigurację debugowania specyficzną dla wybranego obiektu docelowego.

![Punkt wejścia widoku obiekty docelowe](media/cmake-targets-add-debug-configuration.png "Punkt wejścia widoku obiekty docelowe")

- **Główny plik CMakeLists.txt:** Kliknij prawym przyciskiem myszy główny plik *CMakeLists.txt* i wybierz pozycję **Dodaj konfigurację debugowania,** aby otworzyć okno dialogowe **Wybieranie debugera.** Okno dialogowe umożliwia dodanie *dowolnego* typu konfiguracji debugowania, ale należy ręcznie określić `projectTarget` CMake cel do wywołania za pośrednictwem właściwości.

![Wybieranie okna dialogowego debugera](media/cmake-select-a-debugger.png "Wybieranie okna dialogowego debugera")

Można edytować plik *launch.vs.json,* aby utworzyć konfiguracje debugowania dla dowolnej liczby obiektów docelowych CMake. Po zapisaniu pliku program Visual Studio tworzy wpis dla każdej nowej konfiguracji w pozycji **startowej.**

## <a name="reference-keys-in-cmakesettingsjson"></a>Klucze referencyjne w CMakeSettings.json

Aby odwołać się do dowolnego klucza w pliku *CMakeSettings.json,* należy dołączyć `cmake.` do niego w pliku *launch.vs.json*. W poniższym przykładzie przedstawiono prosty plik *launch.vs.json,* który pobiera wartość `remoteCopySources` klucza w pliku *CMakeSettings.json* dla aktualnie wybranej konfiguracji:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

**Zmienne środowiskowe zdefiniowane** w *pliku CMakeSettings.json* mogą być również używane `${env.VARIABLE_NAME}`w pliku launch.vs.json przy użyciu składni . W programie Visual Studio 2019 w wersji 16.4 i nowszych obiekty docelowe debugowania są uruchamiane automatycznie przy użyciu środowiska określonego w *pliku CMakeSettings.json*. Zmienną środowiskową można odsetić, ustawiając ją na **wartość null**.

## <a name="launchvsjson-reference"></a>Odwołanie do pliku Launch.vs.json

Istnieje wiele *właściwości launch.vs.json* do obsługi wszystkich scenariuszy debugowania. Następujące właściwości są wspólne dla wszystkich konfiguracji debugowania, zarówno zdalnych, jak i lokalnych:

- `projectTarget`: Określa CMake cel do wywołania podczas tworzenia projektu. Program Visual Studio automatycznie wypełnia tę właściwość po wprowadzeniu *pliku launch.vs.json* z **menu debugowania** lub **widoku obiektów docelowych**. Ta wartość musi być zgodna z nazwą istniejącego obiektu docelowego debugowania wymienionego w liście rozwijanej **Element startowy.**

- `env`: Dodatkowe zmienne środowiskowe do dodania przy użyciu składni:

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`: Argumenty wiersza polecenia przekazywane do programu do debugowania.

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>Launch.vs.json — odwołanie do projektów zdalnych i WSL

W programie Visual Studio 2019 w wersji 16.6 `type: cppgdb` dodaliśmy nową konfigurację debugowania, aby uprościć debugowanie w systemach zdalnych i WSL. Stare konfiguracje debugowania `type: cppdbg` są nadal obsługiwane.

### <a name="configuration-type-cppgdb"></a>Typ konfiguracji`cppgdb`

- `name`: Przyjazna nazwa identyfikująca konfigurację z listy rozwijanej **Element startowy.**
- `project`: Określa względną ścieżkę do pliku projektu. Zwykle nie trzeba zmieniać tej ścieżki podczas debugowania projektu CMake.
- `projectTarget`: Określa CMake cel do wywołania podczas tworzenia projektu. Program Visual Studio automatycznie wypełnia tę właściwość po wprowadzeniu *pliku launch.vs.json* z **menu debugowania** lub **widoku obiektów docelowych**. Ta wartość docelowa musi być zgodna z nazwą istniejącego obiektu docelowego debugowania wymienionego w liście rozwijanej **Element startowy.**
- `debuggerConfiguration`: Wskazuje, który zestaw wartości domyślnych debugowania ma być używany. W programie Visual Studio 2019 w wersji 16.6 jedyną prawidłową opcją jest `gdb`. Wcześniejsze wersje `gdbserver`również obsługują .
- `args`: Argumenty wiersza polecenia przekazywane podczas uruchamiania do debugowanego programu.
- `env`: Dodatkowe zmienne środowiskowe przekazywane do debugowanego programu. Na przykład `{"DISPLAY": "0.0"}`.
- `processID`: Identyfikator procesu Linuksa do dołączenia. Używane tylko podczas podłączania do procesu zdalnego. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dołączaniem do procesów przy użyciu GDB](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

#### <a name="additional-options-for-the-gdb-configuration"></a>Dodatkowe opcje `gdb` konfiguracji

- `program`: Domyślnie `"${debugInfo.fullTargetPath}"`wartość . Ścieżka Unix do aplikacji do debugowania. Wymagane tylko wtedy, gdy różni się od docelowego pliku wykonywalnego w lokalizacji kompilacji lub wdrażania.
- `remoteMachineName`: Domyślnie `"${debugInfo.remoteMachineName}"`wartość . Nazwa systemu zdalnego, który obsługuje program do debugowania. Wymagane tylko wtedy, gdy różni się od systemu kompilacji. Musi mieć istniejący wpis w [Menedżerze połączeń](../linux/connect-to-your-remote-linux-computer.md). Naciśnij **klawisze Ctrl+Spacja,** aby wyświetlić listę wszystkich istniejących połączeń zdalnych.
- `cwd`: Domyślnie `"${debugInfo.defaultWorkingDirectory}"`wartość . Ścieżka uniksowa do katalogu w `program` systemie zdalnym, w którym jest uruchamiana. Ten katalog musi istnieć.
- `gdbpath`: Domyślnie `/usr/bin/gdb`wartość . Pełna ścieżka Uniksa `gdb` do używanego do debugowania. Wymagane tylko w przypadku korzystania `gdb`z niestandardowej wersji programu .
- `preDebugCommand`: Polecenie Linux do uruchomienia `gdb`bezpośrednio przed wywołaniem . `gdb`nie uruchamia się, dopóki polecenie nie zostanie ukończone. Można użyć opcji, aby uruchomić skrypt `gdb`przed wykonaniem programu .

#### <a name="deployment-options"></a>Opcje wdrożenia

Użyj następujących opcji, aby oddzielić komputer kompilacji (zdefiniowane w CMakeSettings.json) od zdalnego komputera debugowania.

- `remoteMachineName`: Zdalne urządzenie debugowania. Wymagane tylko wtedy, gdy różni się od maszyny kompilacji. Musi mieć istniejący wpis w [Menedżerze połączeń](../linux/connect-to-your-remote-linux-computer.md). Naciśnij **klawisze Ctrl+Spacja,** aby wyświetlić listę wszystkich istniejących połączeń zdalnych.
- `disableDeploy`: Domyślnie `false`wartość . Wskazuje, czy separacja kompilacji/debugowania jest wyłączona. Gdy `false`ta opcja umożliwia tworzenie i debugowanie występuje na dwóch oddzielnych komputerach.
- `deployDirectory`: Pełna ścieżka Uniksa do `remoteMachineName` katalogu, do który zostanie skopiowany plik wykonywalny.
- `deploy`: Tablica zaawansowanych ustawień wdrażania. Te ustawienia należy skonfigurować tylko wtedy, gdy ma być bardziej szczegółowa kontrola nad procesem wdrażania. Domyślnie tylko pliki niezbędne do debugowania procesu są wdrażane na komputerze zdalnego debugowania.
  - `sourceMachine`: komputer, z którego jest kopiowany plik lub katalog. Naciśnij **klawisze Ctrl+Spacja,** aby wyświetlić listę wszystkich połączeń zdalnych przechowywanych w Menedżerze połączeń. Podczas tworzenia natywnie na WSL ta opcja jest ignorowana.
  - `targetMachine`: komputer, na którym skopiowany jest plik lub katalog. Naciśnij **klawisze Ctrl+Spacja,** aby wyświetlić listę wszystkich połączeń zdalnych przechowywanych w Menedżerze połączeń.
  - `sourcePath`: Lokalizacja pliku lub `sourceMachine`katalogu w programie .
  - `targetPath`: Lokalizacja pliku lub `targetMachine`katalogu w programie .
  - `deploymentType`: Opis typu wdrożenia. `LocalRemote`i `RemoteRemote` są obsługiwane. `LocalRemote`oznacza kopiowanie z lokalnego systemu plików `remoteMachineName` do zdalnego systemu określonego przez *w launch.vs.json*. `RemoteRemote`oznacza kopiowanie z systemu kompilacji zdalnej określonego w *CMakeSettings.json* do innego zdalnego systemu określonego w *launch.vs.json*.
  - `executable`: Wskazuje, czy wdrożony plik jest plikiem wykonywalnym.

### <a name="execute-custom-gdb-commands"></a>Wykonywanie `gdb` poleceń niestandardowych

Visual Studio obsługuje `gdb` wykonywanie poleceń niestandardowych do bezpośredniej interakcji z bazowym debugerem. Aby uzyskać więcej informacji, zobacz [Wykonywanie niestandardowych `gdb` poleceń lldb](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands).

### <a name="enable-logging"></a>Włącz rejestrowanie

Włącz rejestrowanie miengine, aby zobaczyć, `gdb`jakie `gdb` polecenia są wysyłane do , jakie dane wyjściowe zwraca i jak długo trwa każde polecenie. [Dowiedz się więcej](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>Typ konfiguracji`cppdbg`

Następujące opcje mogą być używane podczas debugowania w systemie `cppdbg` zdalnym lub WSL przy użyciu typu konfiguracji. W programie Visual Studio 2019 w wersji 16.6 lub nowszej zalecany jest typ `cppgdb` konfiguracji.

- `name`: Przyjazna nazwa identyfikująca konfigurację z listy rozwijanej **Element startowy.**

- `project`: Określa względną ścieżkę do pliku projektu. Zwykle nie trzeba zmieniać tej wartości podczas debugowania projektu CMake.

- `projectTarget`: Określa CMake cel do wywołania podczas tworzenia projektu. Program Visual Studio automatycznie wypełnia tę właściwość po wprowadzeniu *pliku launch.vs.json* z **menu debugowania** lub **widoku obiektów docelowych**. Ta wartość musi być zgodna z nazwą istniejącego obiektu docelowego debugowania wymienionego w liście rozwijanej **Element startowy.**

- `args`: Argumenty wiersza polecenia przekazywane podczas uruchamiania do debugowanego programu.

- `processID`: Identyfikator procesu Linuksa do dołączenia. Używane tylko podczas podłączania do procesu zdalnego. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dołączaniem do procesów przy użyciu GDB](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

- `program`: Domyślnie `"${debugInfo.fullTargetPath}"`wartość . Ścieżka Unix do aplikacji do debugowania. Wymagane tylko wtedy, gdy różni się od docelowego pliku wykonywalnego w lokalizacji kompilacji lub wdrażania.

- `remoteMachineName`: Domyślnie `"${debugInfo.remoteMachineName}"`wartość . Nazwa systemu zdalnego, który obsługuje program do debugowania. Wymagane tylko wtedy, gdy różni się od systemu kompilacji. Musi mieć istniejący wpis w [Menedżerze połączeń](../linux/connect-to-your-remote-linux-computer.md). Naciśnij **klawisze Ctrl+Spacja,** aby wyświetlić listę wszystkich istniejących połączeń zdalnych.

- `cwd`: Domyślnie `"${debugInfo.defaultWorkingDirectory}"`wartość . Pełna ścieżka Uniksa do katalogu w `program` systemie zdalnym, w którym jest uruchamiana. Ten katalog musi istnieć.

- `environment`: Dodatkowe zmienne środowiskowe przekazywane do debugowanego programu. Na przykład:

  ```json
    "environment": [
        {
          "name": "ENV1",
          "value": "envvalue1"
        },
        {
          "name": "ENV2",
          "value": "envvalue2"
        }
      ]
  ```

- `pipeArgs`: Tablica argumentów wiersza polecenia przekazana do programu potoku w celu skonfigurowania połączenia. Program potoku służy do przekazywania standardowych wejść/danych wyjściowych między programem Visual Studio a programem `gdb`. Większość tej **tablicy nie musi być dostosowywana** podczas debugowania projektów CMake. Wyjątkiem jest `${debuggerCommand}`, który `gdb` uruchamia się w systemie zdalnym. Można go zmodyfikować w:

  - Wyeksportuj wartość zmiennej środowiskowej DISPLAY w systemie Linux. W poniższym przykładzie `:1`ta wartość to .

    ```json
    "pipeArgs": [
        "/s",
        "${debugInfo.remoteMachineId}",
        "/p",
        "${debugInfo.parentProcessId}",
        "/c",
        "export DISPLAY=:1;${debuggerCommand}",
        "--tty=${debugInfo.tty}"
      ],
    ```

  - Uruchom skrypt przed wykonaniem . `gdb` Upewnij się, że uprawnienia do wykonywania są ustawione na skrypcie.

    ```json
    "pipeArgs": [
        "/s",
        "${debugInfo.remoteMachineId}",
        "/p",
        "${debugInfo.parentProcessId}",
        "/c",
        "/path/to/script.sh;${debuggerCommand}",
        "--tty=${debugInfo.tty}"
      ],
    ```

- `stopOnEntry`: wartość logiczna określająca, czy przerwać się natychmiast po uruchomieniu procesu. Wartością domyślną jest false.

- `visualizerFile`: [Plik .natvis](/visualstudio/debugger/create-custom-views-of-native-objects) do użycia podczas debugowania tego procesu. Ta opcja jest `gdb` niezgodna z ładnym drukowaniem. Należy `showDisplayString` również ustawić po ustawieniu tej właściwości.

- `showDisplayString`: wartość logiczna, która włącza `visualizerFile` ciąg wyświetlania po określeniu. Ustawienie tej `true` opcji może spowodować mniejszą wydajność podczas debugowania.

- `setupCommands`: Co `gdb` najmniej jedno polecenie do wykonania, aby skonfigurować debuger bazowy.

- `miDebuggerPath`: Pełna ścieżka `gdb`do . Gdy nie określono, Visual Studio przeszukuje PATH najpierw debugera.

- Na koniec wszystkie opcje wdrażania zdefiniowane dla typu `cppgdb` konfiguracji `cppdbg` mogą być również używane przez typ konfiguracji.

### <a name="debug-using-gdbserver"></a>Debugowanie przy użyciu`gdbserver`

Konfigurację można `cppdbg` skonfigurować do `gdbserver`debugowania za pomocą programu . Więcej szczegółów i przykładową konfigurację uruchamiania można znaleźć w poście blogu Microsoft C++ Team Blog [Debugowanie `gdbserver`projektów CMake Linux za pomocą programu ](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/).

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>Zobacz też

[CZło projektów w programie Visual Studio](cmake-projects-in-visual-studio.md)\
[Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)\
[Połącz się ze zdalnym komputerem z systemem Linux](../linux/connect-to-your-remote-linux-computer.md)\
[Dostosowywanie ustawień kompilacji CMake](customize-cmake-settings.md)\
[Konfigurowanie sesji debugowania CMake](configure-cmake-debugging-sessions.md)\
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[CZrobe wstępnie zdefiniowane odwołanie do konfiguracji](cmake-predefined-configuration-reference.md)

::: moniker-end
