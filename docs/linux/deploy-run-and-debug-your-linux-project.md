---
title: Wdrażanie, uruchamianie i debugowanie projektu systemu Linux w programie Visual Studio
description: W tym artykule opisano sposób kompilowania, wykonywania i debugowania kodu na zdalnym docelowych z wewnątrz projektu Linux C++ w programie Visual Studio.
ms.date: 06/07/2019
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: e68feab3a71cd5bb3f6b88eee52f0872ef4bb213
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "80077837"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Wdrażanie, uruchamianie i debugowanie projektu systemu Linux

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

Po utworzeniu projektu Linux C++ w programie Visual Studio i nawiązaniu połączenia z projektem za pomocą [Menedżera połączeń systemu Linux](connect-to-your-remote-linux-computer.md)można uruchomić i debugować projekt. Skompilować, wykonać i debugować kod na zdalnym docelowym.

::: moniker range="vs-2019"

**Visual Studio 2019 w wersji 16.1** Można kierować różne systemy Linux do debugowania i tworzenia. Na przykład można skompilować krzyżowo na x64 i wdrożyć na urządzeniu ARM podczas kierowania scenariuszy IoT. Aby uzyskać więcej informacji, zobacz [Określanie różnych maszyn do tworzenia i debugowania](#separate_build_debug) w dalszej części tego artykułu.

::: moniker-end

Istnieje kilka sposobów interakcji z i debugowania projektu systemu Linux.

- Debugowanie przy użyciu tradycyjnych funkcji programu Visual Studio, takich jak punkty przerwania, okna zegarka i najechanie kursorem na zmienną. Za pomocą tych metod można debugować, jak zwykle w przypadku innych typów projektów.

- Wyświetlanie danych wyjściowych z komputera docelowego w oknie konsoli systemu Linux. Za pomocą konsoli można również wysyłać dane wejściowe do komputera docelowego.

## <a name="debug-your-linux-project"></a>Debugowanie projektu systemu Linux

1. Wybierz tryb debugowania na stronie właściwości **Debugowanie.**

   ::: moniker range="vs-2019"

   GDB służy do debugowania aplikacji działających w systemie Linux. Podczas debugowania w systemie zdalnym (nie WSL) GDB można uruchomić w dwóch różnych trybach, które można wybrać z opcji **Tryb debugowania** na stronie właściwości **debugowania** projektu:

   ![Opcje GDB](media/vs2019-debugger-settings.png)

   ::: moniker-end

   ::: moniker range="vs-2017"

   GDB służy do debugowania aplikacji działających w systemie Linux. GDB można uruchomić w dwóch różnych trybach, które można wybrać z opcji **Tryb debugowania** na stronie właściwości **debugowania** projektu:

   ![Opcje GDB](media/vs2017-debugger-settings.png)

   ::: moniker-end

   - W trybie **gdbserver** GDB jest uruchamiany lokalnie, co łączy się z gdbserver w systemie zdalnym.  Należy zauważyć, że jest to jedyny tryb, który obsługuje okno Konsoli systemu Linux.

   - W trybie **gdb** debuger programu Visual Studio dyski GDB w systemie zdalnym. Jest to lepsze rozwiązanie, jeśli lokalna wersja GDB nie jest zgodna z wersją zainstalowaną na komputerze docelowym. |

   > [!NOTE]
   > Jeśli nie możesz trafić punktów przerwania w trybie debugowania gdbservera, wypróbuj tryb gdb. gdb musi być najpierw [zainstalowany](download-install-and-setup-the-linux-development-workload.md) na zdalnym celu.

1. Wybierz zdalny obiekt docelowy przy użyciu standardowego paska narzędzi **debugowania** w programie Visual Studio.

   Gdy zdalny obiekt docelowy jest dostępny, zostanie wyświetlony na liście według nazwy lub adresu IP.

   ![Cel zdalny](media/remote_target.png)

   Jeśli nie masz jeszcze połączenia ze zdalnym obiektem docelowym, zostanie wyświetlone instrukcje dotyczące [używania Menedżera połączeń linuksa](connect-to-your-remote-linux-computer.md) do łączenia się ze zdalnym obiektem docelowym.

   ![Architektura zdalna](media/architecture.png)

1. Ustaw punkt przerwania, klikając w lewym marginesie niektórych kodu, który, jak wiadomo, wykona.

   Czerwona kropka pojawia się w wierszu kodu, w którym można ustawić punkt przerwania.

1. Naciśnij **klawisz F5** (lub **Debugowanie > rozpocznij debugowanie),** aby rozpocząć debugowanie.

   Po uruchomieniu debugowania, aplikacja jest kompilowana na zdalnym docelowych przed jej uruchomieniem. Wszelkie błędy kompilacji pojawią się w oknie **Lista błędów.**

   Jeśli nie ma żadnych błędów, aplikacja zostanie uruchomiony i debuger zostanie wstrzymany w punkcie przerwania.

   ![Trafienie w punkt przerwania](media/hit_breakpoint.png)

   Teraz można wchodzić w interakcje z aplikacją w jej bieżącym stanie, przeglądać zmienne i przechodzić przez kod, naciskając klawisze poleceń, takie jak **F10** lub **F11**.

1. Jeśli chcesz używać Konsoli Linux do interakcji z aplikacją, wybierz **opcję Debugowanie > Konsoli Linux**.

   ![Menu Konsoli systemu Linux](media/consolemenu.png)

   Ta konsola wyświetli wszystkie dane wyjściowe konsoli z komputera docelowego, a także weźmie dane wejściowe i wyśle je do komputera docelowego.

   ![Okno Konsoli systemu Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options-msbuild-based-projects"></a>Konfigurowanie innych opcji debugowania (projekty oparte na msbuild)

- Argumenty wiersza polecenia mogą być przekazywane do pliku wykonywalnego za pomocą elementu **Argumenty programu** na stronie właściwości **debugowanie** projektu.

   ![Argumenty programu](media/settings_programarguments.png)

- Określone opcje debugera mogą być przekazywane do GDB za pomocą **wpisu Polecenia dodatkowego debugera.**  Na przykład można zignorować sygnały SIGILL (instrukcja niezgodna z prawem).  Można użyć polecenia **dojście,** aby to osiągnąć, dodając następujące elementy do **wpisu Polecenia dodatkowego debugera,** jak pokazano powyżej:

   `handle SIGILL nostop noprint`

## <a name="configure-other-debugging-options-cmake-projects"></a>Konfigurowanie innych opcji debugowania (CMake projects)

W pliku launch.vs.json można określić dodatkowe argumenty wiersza polecenia dla projektu CMake. Aby uzyskać więcej informacji, zobacz [Debugowanie projektu CMake](cmake-linux-project.md#debug_cmake_project)

## <a name="debug-with-attach-to-process"></a>Debugowanie z dołączanie do procesu

Strona właściwości [Debugowanie](prop-pages/debugging-linux.md) dla projektów programu Visual Studio i ustawienia **Launch.vs.json** dla projektów CMake mają ustawienia, które umożliwiają dołączanie do uruchomionego procesu. Jeśli wymagana jest dodatkowa kontrola wykraczające poza to, co `Microsoft.MIEngine.Options.xml` znajduje się w tych ustawieniach, można umieścić plik o nazwie w katalogu głównym rozwiązania lub obszaru roboczego. Oto prosty przykład:

```xml
<?xml version="1.0" encoding="utf-8"?>
<SupplementalLaunchOptions>
    <AttachOptions>
      <AttachOptionsForConnection AdditionalSOLibSearchPath="/home/user/solibs">
        <ServerOptions MIDebuggerPath="C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\Common7\IDE\VC\Linux\bin\gdb\7.9\x86_64-linux-gnu-gdb.exe"
ExePath="C:\temp\ConsoleApplication17\ConsoleApplication17\bin\x64\Debug\ConsoleApplication17.out"/>
        <SetupCommands>
          <Command IgnoreFailures="true">-enable-pretty-printing</Command>
        </SetupCommands>
      </AttachOptionsForConnection>
    </AttachOptions>
</SupplementalLaunchOptions>
```

**AttachOptionsForConnection** ma większość atrybutów, które mogą być potrzebne. W powyższym przykładzie pokazano, jak określić lokalizację, aby wyszukać dodatkowe biblioteki .so. Element **podrzędny ServerOptions** umożliwia dołączanie do procesu zdalnego za pomocą gdbserver zamiast. Aby to zrobić, należy określić lokalnego klienta gdb (ten dostarczany w programie Visual Studio 2017 jest pokazany powyżej) i lokalną kopię pliku binarnego z symbolami. **SetupCommands** Element umożliwia przekazywanie poleceń bezpośrednio do gdb. Wszystkie opcje dostępne można znaleźć w [schemacie LaunchOptions.xsd](https://github.com/Microsoft/MIEngine/blob/master/src/MICore/LaunchOptions.xsd) w usłudze GitHub.

::: moniker range="vs-2019"

## <a name="specify-different-machines-for-building-and-debugging"></a><a name="separate_build_debug"></a>Określanie różnych maszyn do tworzenia i debugowania

W programie Visual Studio 2019 w wersji 16.1 można oddzielić komputer kompilacji zdalnej od zdalnego komputera debugowania dla projektów systemu Linux opartych na systemie MSBuild i projektów CMake, które są przeznaczone dla zdalnego komputera z systemem Linux. Na przykład można teraz cross-compile na x64 i wdrożyć na urządzeniu ARM podczas kierowania scenariuszy IoT.

### <a name="msbuild-based-projects"></a>Projekty oparte na MSBuild

Domyślnie zdalna maszyna debugowania jest taka sama jak maszyna kompilacji zdalnej **(Właściwości** > konfiguracji**Ogólne** > **zdalne budowanie komputera).** Aby określić nową zdalną maszynę debugowania, kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i przejdź do **właściwości** > konfiguracji**Debugowanie** > **zdalnego komputera debugowania**.  

![Zdalna maszyna do debugowania linuksa](media/linux-remote-debug-machine.png)

Menu rozwijane **zdalnego komputera debugującego** jest wypełnione wszystkimi nawiązanymi połączeniami zdalnymi. Aby dodać nowe połączenie zdalne, przejdź do > Menedżera połączeń**Międzyplatformowych** > **Connection Manager** **Opcji** >  **narzędzi**lub wyszukaj hasło "Menedżer połączeń" w **obszarze Szybkie uruchamianie**. Można również określić nowy katalog zdalnego wdrażania na stronach właściwości projektu **(Właściwości** > konfiguracji**Ogólne** > **katalog zdalnego wdrażania**).

Domyślnie tylko pliki niezbędne do debugowania procesu zostaną wdrożone na komputerze zdalnego debugowania. Za pomocą **Eksploratora rozwiązań** można skonfigurować, które pliki źródłowe zostaną wdrożone na komputerze zdalnego debugowania. Po kliknięciu pliku źródłowego zostanie wyświetlony podgląd jego właściwości pliku bezpośrednio pod Eksploratorem rozwiązań.

![Pliki z systemem Linux, które można wdrożyć](media/linux-deployable-content.png)

**Właściwość Content** określa, czy plik zostanie wdrożony na komputerze zdalnego debugowania. Wdrożenie można całkowicie wyłączyć, przechodząc do programu **Property Pages** > **Configuration Manager** i odznaczając **wdrażanie** dla żądanej konfiguracji.

W niektórych przypadkach może wymagać większej kontroli nad wdrożeniem projektu. Na przykład niektóre pliki, które chcesz wdrożyć, mogą znajdować się poza rozwiązaniem lub chcesz dostosować katalog zdalnego wdrażania na plik lub katalog. W takich przypadkach należy dołączyć następujące bloki kodu do pliku .vcxproj i zastąpić "example.cpp" rzeczywistymi nazwami plików:

```xml

<ItemGroup>
   <RemoteDeploy Include="__example.cpp">
<!-- This is the source Linux machine, can be empty if DeploymentType is LocalRemote -->
      <SourceMachine>$(RemoteTarget)</SourceMachine>
      <TargetMachine>$(RemoteDebuggingTarget)</TargetMachine>
      <SourcePath>~/example.cpp</SourcePath>
      <TargetPath>~/example.cpp</TargetPath>
<!-- DeploymentType can be LocalRemote, in which case SourceMachine will be empty and SourcePath is a local file on Windows -->
      <DeploymentType>RemoteRemote</DeploymentType>
<!-- Indicates whether the deployment contains executables -->
      <Executable>true</Executable>
   </RemoteDeploy>
</ItemGroup>
```

### <a name="cmake-projects"></a>Projekty platformy CMake

W przypadku projektów CMake przeznaczonych dla zdalnego komputera z systemem Linux można określić nową zdalną maszynę debugowania w pliku launch.vs.json. Domyślnie wartość "remoteMachineName" jest synchronizowana z właściwością "remoteMachineName" w CMakeSettings.json, która odpowiada zdalnemu maszynie kompilacji. Te właściwości nie muszą już być zgodne, a wartość "remoteMachineName" w pliku launch.vs.json będzie dyktować, który komputer zdalny jest używany do wdrażania i debugowania.

![CZamić zdalne urządzenie do debugowania](media/cmake-remote-debug-machine.png)

IntelliSense zasugeruje wszystkie listy wszystkich nawiązanych połączeń zdalnych. Nowe połączenie zdalne można dodać, przechodząc do**Menedżera połączeń** **Options** > **między platformami** >  **Opcje narzędzi** > lub wyszukując "Menedżer połączeń" w **trybie Szybkie uruchamianie**.

Aby uzyskać pełną kontrolę nad wdrożeniem, możesz dołączyć następujące bloki kodu do pliku launch.vs.json. Pamiętaj, aby zastąpić wartości zastępcze wartościami rzeczywistymi:

```json

"disableDeploy": false,
"deployDirectory": "~\foo",
"deploy" : [
   {
      "sourceMachine": "127.0.0.1 (username=example1, port=22, authentication=Password)",
      "targetMachine": "192.0.0.1 (username=example2, port=22, authentication=Password)",
      "sourcePath": "~/example.cpp",
      "targetPath": "~/example.cpp",
      "executable": "false"
   }
]

```

::: moniker-end

## <a name="next-steps"></a>Następne kroki

- Aby debugować urządzenia ARM w systemie Linux, zobacz ten wpis w blogu: [Debugowanie osadzonego urządzenia ARM w programie Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/).

## <a name="see-also"></a>Zobacz też

[Właściwości debugowania języka C++ (Linux C++)](prop-pages/debugging-linux.md)
