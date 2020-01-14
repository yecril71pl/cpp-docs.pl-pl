---
title: Konfigurowanie sesji debugowania CMake w programie Visual Studio
description: Opisuje sposób używania programu Visual Studio do konfigurowania ustawień debugera CMake
ms.date: 01/13/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: ff1de8241c2489e675f82f469f1cf697a72f5034
ms.sourcegitcommit: 275b71219d2a8bd5d78f87e21dd909e9968c2f44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75946811"
---
# <a name="configure-cmake-debugging-sessions"></a>Konfigurowanie sesji debugowania narzędzia CMake

::: moniker range="vs-2015"

Natywna obsługa CMake jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

Wszystkie elementy wykonywalne CMake są wyświetlane na liście rozwijanej **elementu startowego** na pasku narzędzi **Ogólne** . Aby rozpocząć sesję debugowania, po prostu wybierz jeden z nich i uruchom debuger.

![Lista rozwijana elementu startowego CMake](media/cmake-startup-item-dropdown.png "Lista rozwijana elementu startowego CMake")

Możesz również uruchomić sesję debugowania z poziomu Eksplorator rozwiązań. Najpierw przejdź do **widoku CMAKE targets** w oknie **Eksplorator rozwiązań** .

![Przycisk Widok elementów docelowych CMake](media/cmake-targets-view.png  "Element menu Widok elementów docelowych CMake")

Następnie kliknij prawym przyciskiem myszy dowolny plik wykonywalny i wybierz polecenie **Debuguj** lub **Debuguj i Uruchom ustawienia**. **Debugowanie** automatycznie rozpocznie debugowanie wybranego elementu docelowego na podstawie aktywnej konfiguracji. **Ustawienia debugowania i uruchamiania** otwierają plik *Launch. vs. JSON* i dodaje nową konfigurację debugowania dla wybranego celu.

## <a name="customize-debugger-settings"></a>Dostosuj ustawienia debugera

Możesz dostosować ustawienia debugera dla dowolnego pliku wykonywalnego CMake w projekcie w pliku o nazwie *Launch. vs. JSON*. Istnieją trzy punkty wejścia do tego pliku:

- Wybierz pozycję **debuguj > Debuguj i Uruchom ustawienia dla $ {activeDebugTarget}** z menu głównego, aby edytować konfigurację debugowania specyficzną dla aktywnego elementu docelowego debugowania. Jeśli nie masz wybranego aktywnego elementu docelowego, ta opcja będzie wyszarzona.

- Przejdź do **widoku obiektów docelowych** w Eksplorator rozwiązań. Następnie kliknij prawym przyciskiem myszy element docelowy debugowania i wybierz polecenie **Debuguj i Uruchom ustawienia** , aby edytować konfigurację debugowania specyficzną dla wybranego obiektu docelowego.

- Kliknij prawym przyciskiem myszy główny CMakeLists. txt, a następnie wybierz polecenie **Debuguj i Uruchom ustawienia** , aby otworzyć okno dialogowe **Wybierz debuger** . W oknie dialogowym można dodać dowolną konfigurację debugowania, ale należy ręcznie określić element docelowy CMake, który ma zostać wywołany za pomocą właściwości `projectTarget`.

Aby odwołać się do dowolnego klucza w pliku *pliku cmakesettings. JSON* , należy poprzedzić go `cmake.` w elemencie *Launch. vs. JSON*. W poniższym przykładzie przedstawiono prosty plik *Launch. vs. JSON* , który ściąga wartość klucza `remoteCopySources` w pliku *pliku cmakesettings. JSON* dla aktualnie wybranej konfiguracji:

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

Po zapisaniu pliku *Launch. vs. JSON* program Visual Studio tworzy wpis nowej nazwy na liście rozwijanej **elementu startowego** . Można edytować plik *Launch. vs. JSON* , aby utworzyć wiele konfiguracji debugowania dla dowolnej liczby elementów docelowych CMAKE.

## <a name="launchvsjson-reference"></a>Dokumentacja uruchamiania. vs. JSON

Istnieje wiele właściwości *uruchamiania. vs. JSON* , które obsługują wszystkie scenariusze debugowania. Następujące właściwości są wspólne dla wszystkich konfiguracji debugowania, zarówno zdalnych, jak i lokalnych:

- `projectTarget`: określa element docelowy CMake, który ma zostać wywołany podczas kompilowania projektu. Program Visual Studio automatycznie wypełnia tę właściwość, jeśli wprowadzasz polecenie *Uruchom. vs. JSON* z **debugowania > Debuguj i Uruchom ustawienia dla widoku $ {ActiveDebugTarget}** lub **elementów docelowych**.

- `program`: pełna ścieżka do pliku wykonywalnego programu w systemie zdalnym. Możesz użyć makra `${debugInfo.fullTargetPath}` tym miejscu.

- `args`: argumenty wiersza polecenia przekazane do programu w celu debugowania.

## <a name="launchvsjson-reference-for-remote-linux-projects"></a>Dokumentacja uruchamiania. vs. JSON dla zdalnych projektów systemu Linux

Następujące właściwości są specyficzne dla **konfiguracji debugowania zdalnego**. Możesz również [wysyłać polecenia bezpośrednio do GDB](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands) i [włączać rejestrowanie MIEngine](https://github.com/microsoft/MIEngine/wiki/Logging). Te właściwości pozwalają zobaczyć, jakie polecenia są wysyłane do GDB, jakie wyjściowe GDB zwraca i jak długo trwa każde polecenie.

- `cwd`: bieżący katalog roboczy na potrzeby znajdowania zależności i innych plików na maszynie zdalnej. `${debugInfo.defaultWorkingDirectory}` można użyć makra. Wartość domyślna to zdalny element główny obszaru roboczego, chyba że zostanie zastąpiony w *CMakeLists. txt*. Ta właściwość jest używana tylko w przypadku konfiguracji zdalnych; `currentDir` służy do ustawiania bieżącego katalogu uruchamiania aplikacji dla projektu lokalnego.

- `environment`: dodatkowe zmienne środowiskowe do dodania do środowiska dla programu z następującą składnią:

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

- `pipeArgs`: argumenty wiersza polecenia przekazane do programu potoku w celu skonfigurowania połączenia. Program potoku służy do przekazywania standardowych danych wejściowych/wyjściowych między programem Visual Studio i GDB. Polecenie `${debuggerCommand}` uruchamia GDB w systemie zdalnym i można je zmodyfikować, aby:

  - Wyeksportuj wartość zmiennej środowiskowej WYŚWIETLAnej w systemie Linux. W poniższym przykładzie ta wartość jest `:1`.

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

  - Uruchom skrypt przed wykonaniem GDB. Upewnij się, że w skrypcie są ustawione uprawnienia do wykonywania.

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

- `stopOnEntry`: wartość logiczna określająca, czy ma zostać przerwana, gdy tylko proces zostanie uruchomiony. Wartość domyślna to false.

- `visualizerFile`: [plik. Natvis](/visualstudio/debugger/create-custom-views-of-native-objects) do użycia podczas debugowania tego procesu. Ta opcja jest niezgodna z gdbą drukowaniem. Należy również ustawić `showDisplayString` podczas ustawiania tej właściwości.

- `showDisplayString`: wartość logiczna, która włącza ciąg wyświetlania, gdy określono `visualizerFile`. Ustawienie tej opcji na `true` może spowodować wolniejszą wydajność podczas debugowania.

- `setupCommands`: co najmniej jedno polecenie GDB do wykonania, aby skonfigurować podstawowy debuger.

- `externalConsole`: wartość logiczna określająca, czy konsola jest uruchamiana dla debugowanego obiektu.

- `miDebuggerPath`: pełna ścieżka do GDB. Gdy nie zostanie określony, program Visual Studio szuka najpierw ścieżki dla debugera.

::: moniker-end

::: moniker range="vs-2017"

- `remoteMachineName`: zdalny system Linux, który hostuje GDB i program do debugowania.

::: moniker-end

::: moniker range="vs-2019"

Poniższe właściwości mogą służyć do oddzielenia **zdalnego systemu kompilacji** od **zdalnego systemu debugowania**. Aby uzyskać więcej informacji, zobacz [Określanie różnych maszyn do kompilowania i debugowania](../linux/deploy-run-and-debug-your-linux-project.md#cmake-projects).

- `remoteMachineName`: zdalny system Linux, który hostuje GDB i program do debugowania. Ten wpis nie musi być zgodny z systemem zdalnego systemu Linux używanym do kompilowania określonego w pliku *pliku cmakesettings. JSON*. Naciśnij **klawisze CTRL + SPACJA** , aby wyświetlić listę wszystkich połączeń zdalnych przechowywanych w [Menedżerze połączeń](../linux/connect-to-your-remote-linux-computer.md).

- `disableDeploy`: wskazuje, czy separacja kompilacji/debugowania jest wyłączona. Włączenie tej funkcji umożliwia kompilowanie i debugowanie na dwóch oddzielnych komputerach.

- `deployDirectory`: katalog na zdalnym komputerze debugowania (określony przez `remoteMachineName`), do którego zostanie skopiowany plik wykonywalny.

- `deploy`: tablica zaawansowanych ustawień wdrożenia. Te ustawienia wystarczy skonfigurować tylko wtedy, gdy potrzebujesz bardziej szczegółowej kontroli nad procesem wdrażania. Domyślnie tylko pliki niezbędne do debugowania procesu zostaną wdrożone na maszynie zdalnego debugowania.

  - `sourceMachine`: maszyna, z której zostanie skopiowany plik lub katalog. Naciśnij **klawisze CTRL + SPACJA** , aby wyświetlić listę wszystkich połączeń zdalnych przechowywanych w Menedżerze połączeń.

  - `targetMachine`: komputer, do którego zostanie skopiowany plik lub katalog. Naciśnij **klawisze CTRL + SPACJA** , aby wyświetlić listę wszystkich połączeń zdalnych przechowywanych w Menedżerze połączeń.

  - `sourcePath`: Lokalizacja pliku lub katalogu w `sourceMachine`.

  - `targetPath`: Lokalizacja pliku lub katalogu w `targetMachine`.

  - `deploymentType`: Opis typu wdrożenia. Obsługiwane są `LocalRemote` i `RemoteRemote`. `LocalRemote` oznacza kopiowanie z lokalnego systemu plików do systemu zdalnego określonego przez `remoteMachineName` w pliku *Launch. vs. JSON*. `RemoteRemote` oznacza kopiowanie ze zdalnego systemu kompilacji określonego w pliku *pliku cmakesettings. JSON* do różnych systemów zdalnych określonych w pliku *Launch. vs. JSON*.

  - `executable`: wskazuje, czy wdrożony plik jest plikiem wykonywalnym.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="attach-to-a-remote-process"></a>Dołącz do procesu zdalnego

Możesz dołączyć do procesu uruchomionego w systemie Linux, ustawiając `processId` na identyfikator procesu, aby dołączyć debuger do programu. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dołączaniem do procesów przy użyciu GDB](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

::: moniker-end

::: moniker range="vs-2019"

## <a name="debug-on-linux-using-gdbserver"></a>Debugowanie w systemie Linux przy użyciu serwera gdbserver

Program Visual Studio 2019 w wersji 16,5 Preview 1 lub nowszej obsługuje zdalne debugowanie projektów CMake z serwera gdbserver. Aby uzyskać więcej informacji, zobacz [Debugowanie projektów CMAKE systemu Linux z serwera gdbserver](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/).

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>Zobacz także

[CMAKE projekty w programie Visual Studio](cmake-projects-in-visual-studio.md)\
[Konfigurowanie\ projektu systemu Linux CMAKE](../linux/cmake-linux-project.md)
[Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](../linux/connect-to-your-remote-linux-computer.md)\
[Dostosuj ustawienia kompilacji CMake](customize-cmake-settings.md)\
[Konfigurowanie sesji debugowania CMake](configure-cmake-debugging-sessions.md)\
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake wstępnie zdefiniowanej konfiguracji](cmake-predefined-configuration-reference.md)

::: moniker-end
