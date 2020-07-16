---
title: Wdrażanie, uruchamianie i debugowanie projektu języka C++ w systemie Linux w programie Visual Studio
description: Opisuje sposób kompilowania, wykonywania i debugowania kodu na zdalnym miejscu docelowym z wewnątrz projektu systemu Linux C++ w programie Visual Studio.
ms.date: 06/07/2019
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: df095d5561bea6dac94b9faa139c83c197802bbf
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404414"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Wdrażanie, uruchamianie i debugowanie projektu systemu Linux

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

Po utworzeniu projektu systemu Linux C++ w programie Visual Studio i nawiązaniu połączenia z projektem za pomocą [Menedżera połączeń systemu Linux](connect-to-your-remote-linux-computer.md)można uruchomić i debugować projekt. Kompilowanie, wykonywanie i debugowanie kodu w zdalnym miejscu docelowym.

::: moniker range="vs-2019"

**Visual Studio 2019 w wersji 16,1** W celu debugowania i kompilowania można wskazać różne systemy Linux. Na przykład można przeprowadzić kompilację krzyżową na platformie x64 i wdrożyć ją na urządzeniu ARM w przypadku scenariuszy IoT. Aby uzyskać więcej informacji, zobacz [Określanie różnych maszyn do kompilowania i debugowania](#separate_build_debug) w dalszej części tego artykułu.

::: moniker-end

Istnieje kilka sposobów współtworzenia i debugowania projektu systemu Linux.

- Debuguj przy użyciu tradycyjnych funkcji programu Visual Studio, takich jak punkty przerwania, Oglądaj okna i umieszczaj wskaźnik myszy na zmiennej. Korzystając z tych metod, można debugować jak zwykle dla innych typów projektów.

- Wyświetl dane wyjściowe z komputera docelowego w oknie konsoli systemu Linux. Za pomocą konsoli programu można także wysyłać dane wejściowe do komputera docelowego.

## <a name="debug-your-linux-project"></a>Debugowanie projektu systemu Linux

1. Wybierz opcję Tryb debugowania na stronie właściwości **debugowania** .

   ::: moniker range="vs-2019"

   GDB jest używany do debugowania aplikacji działających w systemie Linux. Podczas debugowania w systemie zdalnym (nie WSL) GDB można uruchomić w dwóch różnych trybach, które można wybrać z opcji **tryb debugowania** na stronie właściwości **debugowania** projektu:

   ![Opcje GDB](media/vs2019-debugger-settings.png)

   ::: moniker-end

   ::: moniker range="vs-2017"

   GDB jest używany do debugowania aplikacji działających w systemie Linux. GDB może działać w dwóch różnych trybach, które można wybrać z opcji **tryb debugowania** na stronie właściwości **debugowania** projektu:

   ![Opcje GDB](media/vs2017-debugger-settings.png)

   ::: moniker-end

   - W trybie **serwera GDBSERVER** GDB jest uruchamiany lokalnie, który łączy się z serwera gdbserver w systemie zdalnym.  Należy zauważyć, że jest to jedyny tryb obsługiwany przez okno konsoli systemu Linux.

   - W trybie **GDB** program Visual Studio debugger Drives GDB w systemie zdalnym. Jest to lepsza opcja, jeśli lokalna wersja programu GDB nie jest zgodna z wersją zainstalowaną na komputerze docelowym. |

   > [!NOTE]
   > Jeśli nie możesz trafiać punktów przerwania w trybie debugowania serwera gdbserver, wypróbuj tryb GDB. GDB musi być [zainstalowany](download-install-and-setup-the-linux-development-workload.md) na zdalnym miejscu docelowym.

1. Wybierz zdalny obiekt docelowy przy użyciu standardowego paska narzędzi **debugowania** w programie Visual Studio.

   Gdy zdalny element docelowy jest dostępny, zostanie wyświetlony na liście według nazwy lub adresu IP.

   ![Zdalne miejsce docelowe](media/remote_target.png)

   Jeśli nie masz jeszcze połączenia ze zdalnym obiektem docelowym, zostanie wyświetlona instrukcja służąca do nawiązywania połączenia ze zdalnym obiektem docelowym przy użyciu [Menedżera połączeń systemu Linux](connect-to-your-remote-linux-computer.md) .

   ![Architektura zdalna](media/architecture.png)

1. Ustaw punkt przerwania, klikając na lewym marginesie jakiś kod, który będzie wykonywany.

   Czerwona kropka pojawia się w wierszu kodu, w którym ustawiono punkt przerwania.

1. Naciśnij klawisz **F5** (lub **Debuguj > Rozpocznij debugowanie**), aby rozpocząć debugowanie.

   Po rozpoczęciu debugowania aplikacja jest kompilowana na zdalnym miejscu docelowym przed uruchomieniem. Wszystkie błędy kompilacji pojawią się w oknie **Lista błędów** .

   Jeśli nie ma żadnych błędów, aplikacja zostanie uruchomiona, a debuger zostanie wstrzymany w punkcie przerwania.

   ![Trafienie punktu przerwania](media/hit_breakpoint.png)

   Teraz możesz korzystać z aplikacji w jej bieżącym stanie, wyświetlać zmienne i przechodzić przez kod, naciskając klawisze poleceń, takie jak **F10** lub **F11**.

1. Jeśli chcesz używać konsoli systemu Linux do korzystania z aplikacji, wybierz pozycję **debuguj > konsoli systemu Linux**.

   ![Menu konsoli systemu Linux](media/consolemenu.png)

   W tej konsoli zostaną wyświetlone wszystkie dane wyjściowe konsoli z komputera docelowego, a także zostaną wprowadzone dane wejściowe i wysłane do komputera docelowego.

   ![Okno konsoli systemu Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options-msbuild-based-projects"></a>Skonfiguruj inne opcje debugowania (projekty oparte na programie MSBuild)

- Argumenty wiersza polecenia mogą być przekazane do pliku wykonywalnego za pomocą elementu **argumenty programu** na stronie właściwości **debugowania** projektu.

   ![Argumenty programu](media/settings_programarguments.png)

- Określone opcje debugera można przekazywać do GDB przy użyciu **dodatkowego wpisu poleceń debugera** .  Na przykład możesz chcieć zignorować sygnały SIGILL (niedozwolone instrukcje).  Aby to osiągnąć, można użyć polecenia **obsługi** , dodając następujący element do **dodatkowego polecenia debugera** , jak pokazano powyżej:

   `handle SIGILL nostop noprint`

## <a name="configure-other-debugging-options-cmake-projects"></a>Skonfiguruj inne opcje debugowania (projekty CMake)

W launch.vs.jspliku można określić dodatkowe argumenty wiersza polecenia dla projektu CMake. Aby uzyskać więcej informacji, zobacz [debugowanie projektu CMAKE](cmake-linux-project.md#debug_cmake_project)

## <a name="debug-with-attach-to-process"></a>Debuguj z dołączaniem do procesu

Strona właściwości [debugowania](prop-pages/debugging-linux.md) dla projektów programu Visual Studio oraz **Launch.vs.jsw** ustawieniach projektów CMAKE mają ustawienia umożliwiające dołączenie do uruchomionego procesu. Jeśli potrzebujesz dodatkowej kontroli poza tym, co jest dostępne w tych ustawieniach, możesz umieścić plik o nazwie `Microsoft.MIEngine.Options.xml` w katalogu głównym rozwiązania lub obszaru roboczego. Oto prosty przykład:

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

**AttachOptionsForConnection** ma większość atrybutów, które mogą być potrzebne. W powyższym przykładzie pokazano, jak określić lokalizację, aby wyszukać dodatkowe biblioteki. Element podrzędny **ServerOptions** umożliwia dołączenie do procesu zdalnego z serwera gdbserver. Aby to zrobić, należy określić lokalnego klienta GDB (jest on wyświetlany w programie Visual Studio 2017 powyżej) i lokalną kopię pliku binarnego z symbolami. Element **SetupCommands** umożliwia przekazywanie poleceń bezpośrednio do GDB. Wszystkie opcje dostępne w [schemacie LaunchOptions. xsd](https://github.com/Microsoft/MIEngine/blob/master/src/MICore/LaunchOptions.xsd) można znaleźć w witrynie GitHub.

::: moniker range="vs-2019"

## <a name="specify-different-machines-for-building-and-debugging"></a><a name="separate_build_debug"></a>Określ różne maszyny do kompilowania i debugowania

W programie Visual Studio 2019 w wersji 16,1 można rozdzielić zdalną maszynę kompilacji ze zdalnego komputera debugowania dla projektów systemu Linux opartych na programie MSBuild i projektów CMake przeznaczonych dla zdalnego komputera z systemem Linux. Można na przykład teraz przeprowadzić kompilację krzyżową na platformie x64 i wdrożyć ją na urządzeniu ARM w przypadku scenariuszy IoT.

### <a name="msbuild-based-projects"></a>Projekty oparte na programie MSBuild

Domyślnie maszyna debugowania zdalnego jest taka sama jak maszyna kompilacji zdalnej (**Właściwości konfiguracji**  >  **ogólna**  >  **maszyna kompilacji**). Aby określić nową maszynę debugowania zdalnego, kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i przejdź do **Właściwości konfiguracji**  >  **debugowanie**  >  **zdalnego debugowania**.  

![Maszyna zdalnego debugowania systemu Linux](media/linux-remote-debug-machine.png)

Menu rozwijane dla **zdalnego komputera debugowania** jest wypełniane wszystkimi ustanowionymi połączeniami zdalnymi. Aby dodać nowe połączenie zdalne, przejdź do opcji **Narzędzia**  >  **Opcje**  >  Menedżer połączeń**międzyplatformowych**  >  **Connection Manager** lub wyszukaj "Menedżer połączeń" w obszarze **szybkiego uruchamiania**. Możesz również określić nowy katalog zdalnego wdrażania na stronach właściwości projektu (**Właściwości konfiguracji**  >  **ogólny**  >  **katalog zdalnego wdrażania**).

Domyślnie tylko pliki niezbędne do debugowania procesu zostaną wdrożone na maszynie zdalnego debugowania. Za pomocą **Eksplorator rozwiązań** można skonfigurować, które pliki źródłowe zostaną wdrożone na maszynie zdalnego debugowania. Po kliknięciu pliku źródłowego zobaczysz podgląd jego właściwości pliku bezpośrednio poniżej Eksplorator rozwiązań.

![Pliki do wdrożenia systemu Linux](media/linux-deployable-content.png)

Właściwość **Content** określa, czy plik zostanie wdrożony na maszynie zdalnego debugowania. Wdrożenie można całkowicie wyłączyć, przechodząc do **stron właściwości**  >  **Configuration Manager** i usuwając zaznaczenie opcji **wdrożenie** w celu pożądanej konfiguracji.

W niektórych przypadkach może być wymagana większa kontrola nad wdrożeniem projektu. Na przykład niektóre pliki, które mają zostać wdrożone, mogą znajdować się poza rozwiązaniem lub chcesz dostosować katalog zdalnego wdrażania dla pliku ordirectory. W takich przypadkach Dołącz następujące bloki kodu do pliku. vcxproj i Zastąp ciąg "example. cpp" rzeczywistymi nazwami plików:

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

W przypadku projektów CMake przeznaczonych dla zdalnego komputera z systemem Linux można określić nową maszynę debugowania zdalnego w launch.vs.jsna. Domyślnie wartość "remoteMachineName" jest synchronizowana z właściwością "remoteMachineName" w CMakeSettings.json, który odnosi się do zdalnej maszyny kompilacji. Te właściwości nie muszą już być zgodne, a wartość "remoteMachineName" w launch.vs.json określa, który komputer zdalny jest używany do wdrażania i debugowania.

![CMake zdalnego debugowania](media/cmake-remote-debug-machine.png)

Funkcja IntelliSense zasugeruje całą listę wszystkich ustanowionych połączeń zdalnych. Nowe połączenie zdalne można dodać, przechodząc do opcji **Narzędzia**  >  **Opcje**  >  Menedżer połączeń**między platformami**  >  **Connection Manager** lub wyszukując pozycję "Menedżer połączeń" w obszarze **Szybki Start**.

Jeśli chcesz uzyskać pełną kontrolę nad wdrożeniem, możesz dołączyć następujące bloki kodu do launch.vs.jspliku. Pamiętaj, aby zastąpić wartości symboli zastępczych wartościami rzeczywistymi:

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

- Aby debugować urządzenia ARM w systemie Linux, zobacz ten wpis w blogu: [debugowanie osadzonego urządzenia ARM w programie Visual Studio](https://devblogs.microsoft.com/cppblog/debugging-an-embedded-arm-device-in-visual-studio/).

## <a name="see-also"></a>Zobacz też

[Właściwości debugowania języka c++ (Linux C++)](prop-pages/debugging-linux.md)
