---
title: Wdrażanie, uruchamianie i debugowanie projektu systemu Linux w języku C++ w programie Visual Studio
description: Opisuje sposób kompilowania, wykonywania i debugowania kodu zdalnego docelową z wewnątrz projektu języka Linux C++ w programie Visual Studio.
ms.date: 06/07/2019
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: 70770385bde859d47532b130463a1cc54e32a570
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042765"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Wdrażanie, uruchamianie i debugowanie projektu systemu Linux

::: moniker range="vs-2015"

Pomoc techniczna Linux support jest dostępne w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

Po utworzeniu projektu języka Linux C++ w programie Visual Studio i łączysz się przy użyciu projektu [Menedżera połączeń systemu Linux](connect-to-your-remote-linux-computer.md), można uruchamiać i debugować projektu. Skompilować, wykonywanie i możliwe jest debugowanie kodu w zdalnym elemencie docelowym.

::: moniker range="vs-2019"

**Visual Studio 2019 wersji 16.1** można wskazać różnych systemów Linux, debugowania i tworzenia. Na przykład można cross kompilacji na x64 i wdrażać na urządzeniu usługi ARM przy przeznaczeniu scenariuszy IoT. Aby uzyskać więcej informacji, zobacz [określić różnych maszyn na potrzeby kompilowania i debugowania](#separate_build_debug) w dalszej części tego artykułu.

::: moniker-end

Istnieje kilka sposobów interakcji z i debugowanie projektu systemu Linux.

- Debugowanie przy użyciu tradycyjnych funkcje programu Visual Studio, takich jak punkty przerwania, okna czujki i przenosząc kursor myszy nad zmienną. Przy użyciu tych metod, może debugować tak jak zwykle dla innych typów projektów.

- Widok danych wyjściowych z komputera docelowego, w oknie konsoli systemu Linux. Umożliwia także konsolę do wysyłania danych wejściowych do komputera docelowego.

## <a name="debug-your-linux-project"></a>Debugowanie projektu systemu Linux

1. Wybierz tryb debugowania w **debugowanie** stronę właściwości.
   
   ::: moniker range="vs-2019"

   GDB jest używana do debugowania aplikacji działającej w systemie Linux. Podczas debugowania w systemie zdalnym (nie WSL) GDB można uruchomić w dwóch różnych trybach, które można wybierać z **tryb debugowania** opcja w projekcie **debugowanie** strona właściwości:

   ![Opcje GDB](media/vs2019-debugger-settings.png)

   ::: moniker-end

   ::: moniker range="vs-2017"

   GDB jest używana do debugowania aplikacji działającej w systemie Linux. GDB można uruchomić w dwóch różnych trybach, które można wybierać z **tryb debugowania** opcja w projekcie **debugowanie** strona właściwości:

   ![Opcje GDB](media/vs2017-debugger-settings.png)

   ::: moniker-end


   - W **serwera gdbserver** trybie GDB jest uruchamiany lokalnie, która łączy się serwera gdbserver w systemie zdalnym.  Należy zauważyć, że to tylko tryb, który obsługuje okno konsoli systemu Linux.

   - W **gdb** trybie debugera programu Visual Studio dyski GDB w systemie zdalnym. Jest lepszym rozwiązaniem, jeśli lokalna wersja GDB nie jest zgodny z wersją zainstalowaną na komputerze docelowym. |

   > [!NOTE]
   > Jeśli nie można identyfikować punkty przerwania w trybie debugowania gdbserver następuje lokalne, spróbuj trybie gdb. Najpierw należy gdb [zainstalowane](download-install-and-setup-the-linux-development-workload.md) w zdalnym elemencie docelowym.

1. Wybierz docelową zdalnego przy użyciu standardu **debugowania** narzędzi w programie Visual Studio.

   Jeśli zdalny element docelowy jest dostępny, zobaczysz go na liście według nazwy lub adresu IP.

   ![Docelowy zdalnego](media/remote_target.png)

   Jeśli nie masz jeszcze połączenia zdalnego obiektu docelowego, pojawią się instrukcjami, aby użyć [Menedżera połączeń systemu Linux](connect-to-your-remote-linux-computer.md) nawiązać połączenia z docelowym zdalnego.

   ![Architektura zdalnego](media/architecture.png)

1. Ustaw punkt przerwania, klikając na lewym marginesie jakiś kod, który znasz będą wykonywane.

   Czerwona kropka jest wyświetlany na wiersz kodu, gdzie ustawić punkt przerwania.

1. Naciśnij klawisz **F5** (lub **Debuguj > Rozpocznij debugowanie**) można rozpocząć debugowania.

   Podczas uruchamiania debugowania, kompilowania aplikacji w zdalnym elemencie docelowym przed uruchomieniem jej. Błędy kompilacji będą wyświetlane w **lista błędów** okna.

   Jeśli nie ma żadnych błędów, aplikacja zostanie uruchomiona i debuger zostanie wstrzymany w punkcie przerwania.

   ![Trafiony punkt przerwania](media/hit_breakpoint.png)

   Teraz możesz wchodzić w interakcje z aplikacją w jego bieżącym stanie, wyświetlanie zmiennych i Przechodź przez kod, naciskając klawisze poleceń takich jak **F10** lub **F11**.

1. Jeśli chcesz korzystać z konsoli systemu Linux do interakcji z aplikacją, wybierz opcję **Debuguj > Konsola systemu Linux**.

   ![Menu konsoli systemu Linux](media/consolemenu.png)

   Ta konsola będą wyświetlane wszystkie dane wyjściowe konsoli z komputera docelowego, a także pobierać dane wejściowe i wysłać go do komputera docelowego.

   ![Okno konsoli systemu Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options-msbuild-based-projects"></a>Skonfiguruj inne opcje debugowania (projektów opartych na platformie MSBuild)

- Argumenty wiersza polecenia mogą być przekazywane do pliku wykonywalnego przy użyciu **argumenty programu** element w projekcie ma **debugowanie** stronę właściwości.

   ![Argumenty programu](media/settings_programarguments.png)

- Opcje debugera określonej mogą być przekazywane do GDB przy użyciu **dodatkowe polecenia debugera** wpisu.  Na przykład można zignorować SIGILL (niedozwolona instrukcja) sygnałów.  Można użyć **obsługi** polecenie, aby to osiągnąć, dodając następujące polecenie, aby **dodatkowe polecenia debugera** wpisu, jak pokazano powyżej:

   `handle SIGILL nostop noprint`

## <a name="configure-other-debugging-options-cmake-projects"></a>Skonfiguruj inne opcje debugowania (projekty narzędzia CMake)

Dodatkowe argumenty wiersza polecenia dla projektu narzędzia CMake można określić w pliku launch.vs.json. Aby uzyskać więcej informacji, zobacz [debugowania projektu narzędzia CMake](cmake-linux-project.md#debug_cmake_project)

## <a name="debug-with-attach-to-process"></a>Debugowanie z Dołącz do procesu

[Debugowanie](prop-pages/debugging-linux.md) stronę właściwości dla projektów programu Visual Studio i **Launch.vs.json** ustawienia dla projektów CMake ma ustawienia, które umożliwiają dołączanie do uruchomionego procesu. Jeśli potrzebujesz dodatkowej kontroli jest informacje podane w tych ustawień, możesz umieścić plik o nazwie `Microsoft.MIEngine.Options.xml` w katalogu głównym rozwiązania lub obszaru roboczego. Poniżej przedstawiono prosty przykład:

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

**AttachOptionsForConnection** ma większość atrybutów może być konieczne. W powyższym przykładzie pokazuje, jak określić lokalizację do szukania bibliotek SO dodatkowe. Element podrzędny **ServerOptions** umożliwia dołączanie do procesu zdalnego za pomocą serwera gdbserver zamiast tego. Aby to zrobić, należy określić klienta lokalnego gdb (dostarczany w programie Visual Studio 2017 jest pokazany powyżej), jak i lokalną kopię pliku binarnego z symbolami. **SetupCommands** element umożliwia przekazywanie poleceń, bezpośrednio do gdb. Możesz znaleźć wszystkie opcje dostępne w [schematu LaunchOptions.xsd](https://github.com/Microsoft/MIEngine/blob/master/src/MICore/LaunchOptions.xsd) w witrynie GitHub.

::: moniker range="vs-2019"

## <a name="separate_build_debug"></a> Określ różnych maszyn na potrzeby kompilowania i debugowania

W programie Visual Studio 2019 wersji 16.1 można oddzielić zdalnych kompilacji maszyny z komputera zdalnego debugowania dla projektów opartych na platformie MSBuild systemu Linux i projekty narzędzia CMake, przeznaczonych dla zdalnej maszyny z systemem Linux. Na przykład można teraz cross kompilacji na x64 i wdrażać na urządzeniu usługi ARM przy przeznaczeniu scenariuszy IoT.

### <a name="msbuild-based-projects"></a>Projektach MSBuild

Domyślnie komputer do debugowania zdalnego jest taka sama jak zdalny kompilator (**właściwości konfiguracji** > **ogólne** > **maszyny zdalnej kompilacji**). Aby określić nowy komputer do debugowania zdalnego, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i przejdź do **właściwości konfiguracji** > **debugowanie**  >  **Zdalnego debugowania maszyny**.  

![Zdalne debugowanie maszyny z systemem Linux](media/linux-remote-debug-machine.png)

Menu rozwijane dla **komputera zdalnego debugowania** jest wypełniana przy użyciu wszystkich ustanowionych połączeń zdalnych. Aby dodać nowe połączenia zdalnego, przejdź do **narzędzia** > **opcje** > **Międzyplatformowe**  >   **Menedżer połączeń** lub wyszukaj "Menedżera połączeń" w **Szybkie uruchamianie**. Można również określić nowy zdalnego wdrażania katalogu na stronach właściwości projektu (**właściwości konfiguracji** > **ogólne** > **katalogu zdalnego wdrażania** ).

Domyślnie tylko te pliki, które są niezbędne do procesu debugowania będą wdrażane maszyny zdalne debugowanie. Możesz użyć **Eksploratora rozwiązań** skonfigurować źródło, które pliki zostaną wdrożone na maszyny zdalne debugowanie. Po kliknięciu w pliku źródłowym, zostanie wyświetlony podgląd właściwości pliku bezpośrednio poniżej Eksploratora rozwiązań.

![Pliki do wdrożenia systemu Linux](media/linux-deployable-content.png)

**Zawartości** właściwość określa, czy plik zostanie wdrożony komputer do debugowania zdalnego. Możesz wyłączyć wdrożenie całkowicie, przechodząc do **stron właściwości** > **programu Configuration Manager** i usuwając zaznaczenie pola wyboru **Wdróż** dla żądany Konfiguracja.

W niektórych przypadkach mogą wymagać większej kontroli nad wdrażania projektu. Na przykład niektóre pliki, które mają zostać wdrożone może znajdować się poza rozwiązania lub chcesz dostosować zdalnych katalog dla pliku StopFileName wdrożenia. W takich przypadkach Dołącz następujący bloków kodu do pliku .vcxproj i zastąp "example.cpp" nazwą rzeczywistego pliku:

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

W pliku launch.vs.json można określić nowy komputer do debugowania zdalnego dla projektów CMake, przeznaczonych dla zdalnej maszyny z systemem Linux. Domyślnie wartość "NazwaKomputeraZdalnego" są synchronizowane z właściwością "NazwaKomputeraZdalnego" w pliku CMakeSettings.json, który odnosi się do maszyny zdalnej kompilacji. Te właściwości nie są już potrzebne dopasować, a wartość "NazwaKomputeraZdalnego" w pliku launch.vs.json wyznaczają, które maszyny zdalnej jest używany do wdrażania i debugowania.

![Komputer do debugowania zdalnego narzędzia CMake](media/cmake-remote-debug-machine.png)

Funkcja IntelliSense zasugeruje listę wszystkich ustanowionych połączeń zdalnych. Można dodać nowego połączenia zdalnego, przechodząc do **narzędzia** > **opcje** > **Międzyplatformowe**  >   **Menedżer połączeń** lub wyszukiwanie "Connection Manager" w **Szybkie uruchamianie**.

Jeśli ma pełną kontrolę nad wdrożeniem, można dołączyć następujące bloków kodu w pliku launch.vs.json. Pamiętaj, aby zastąpić symbole zastępcze wartości rzeczywistych:

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

- Aby debugować urządzeń ARM w systemie Linux, zobacz ten wpis w blogu: [Debugowanie urządzenia osadzonego ARM w programie Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/).

## <a name="see-also"></a>Zobacz także

[C++, debugowanie — właściwości (Linux C++)](prop-pages/debugging-linux.md)
