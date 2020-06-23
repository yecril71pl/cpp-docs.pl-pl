---
title: Tworzenie i Konfigurowanie projektu systemu Linux CMake w programie Visual Studio
description: Jak utworzyć, skonfigurować, edytować i kompilować projekt systemu Linux CMake w programie Visual Studio
ms.date: 06/22/2020
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 2149b102c452149070d59c9645ce34a5977a6057
ms.sourcegitcommit: f9344b09a734e8b05a7494415991a22b7aec5ae8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85269731"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>Tworzenie i konfigurowanie projektu CMake systemu Linux

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="before-you-begin"></a>Przed rozpoczęciem

Najpierw upewnij się, że masz zainstalowaną **platformę Linux z** zainstalowanym obciążeniem języka C++, w tym składnik CMAKE. Zobacz [Instalowanie obciążeń C++ Linux w programie Visual Studio](download-install-and-setup-the-linux-development-workload.md).

W systemie Linux upewnij się, że zainstalowano następujące elementy:

- zatoce
- GDB
- rsync
- kodu
- Ninja — kompilacja

::: moniker-end

::: moniker range="vs-2019"

Obsługa systemu Linux dla projektów CMake wymaga, aby komputer docelowy miał najnowszą wersję CMake. Często Wersja oferowana przez domyślny Menedżer pakietów dystrybucji nie jest wystarczająca do obsługi wszystkich funkcji wymaganych przez program Visual Studio. Program Visual Studio 2019 wykrywa, czy w systemie Linux jest zainstalowana najnowsza wersja programu CMake. Jeśli nie zostanie znaleziona, program Visual Studio wyświetli pasek informacji w górnej części okienka edytora. Oferuje ona możliwość instalacji CMake z programu [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) .

Obsługa CMake w programie Visual Studio wymaga obsługi trybu serwera, która została wprowadzona w CMake 3,8. W programie Visual Studio 2019 zaleca się wersję 3,14 lub nowszą.

::: moniker-end

::: moniker range="vs-2017"

Obsługa CMake w programie Visual Studio wymaga obsługi trybu serwera, która została wprowadzona w CMake 3,8. W przypadku CMake z wariantem dostarczonym przez firmę Microsoft Pobierz najnowsze wstępnie skompilowane pliki binarne w [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) .

Pliki binarne są instalowane w programie `~/.vs/cmake` . Po wdrożeniu plików binarnych projekt zostanie automatycznie replikny. Jeśli CMake określony przez `cmakeExecutable` pole w *CMakeSettings.json* jest nieprawidłowy (nie istnieje lub jest nieobsługiwaną wersją), a wstępnie skompilowane pliki binarne są obecne, program Visual Studio ignoruje `cmakeExecutable` i używa wstępnie skompilowanych plików binarnych.

:::moniker-end

::: moniker range="vs-2019"

## <a name="create-a-new-linux-cmake-project"></a>Tworzenie nowego projektu CMake systemu Linux

Aby utworzyć nowy projekt systemu Linux CMake w programie Visual Studio 2019:

1. Wybierz pozycję **plik > nowy projekt** w programie Visual Studio lub naciśnij **klawisze Ctrl + Shift + N**.
1. Ustaw **Język** na **C++** i wyszukaj ciąg "CMAKE". Następnie wybierz przycisk **dalej**. Wprowadź **nazwę** i **lokalizację**, a następnie wybierz pozycję **Utwórz**.

Program Visual Studio tworzy plik o minimalnym *CMakeLists.txt* tylko przy użyciu nazwy pliku wykonywalnego i minimalnej wymaganej wersji CMAKE. Możesz jednak ręcznie edytować ten plik. Program Visual Studio nigdy nie zastąpi zmian. W tym pliku można określić argumenty wiersza polecenia CMake i zmienne środowiskowe. Kliknij prawym przyciskiem myszy plik głównego *CMakeLists.txt* w **Eksplorator rozwiązań** i wybierz pozycję **Ustawienia CMAKE dla projektu**. Aby określić opcje debugowania, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Debuguj i Uruchom ustawienia**.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="open-a-cmake-project-folder"></a>Otwieranie folderu projektu CMake

Po otwarciu folderu zawierającego istniejący projekt CMake program Visual Studio używa zmiennych w pamięci podręcznej CMake, aby automatycznie konfigurować funkcje IntelliSense i kompilacje. Ustawienia konfiguracji lokalnej i debugowania są przechowywane w plikach JSON. Możesz opcjonalnie udostępniać te pliki innym osobom korzystającym z programu Visual Studio.

Program Visual Studio nie modyfikuje plików *CMakeLists.txt* . Jest to samo samo, tak aby inne osoby pracujące nad tym samym projektem mogły nadal korzystać z istniejących narzędzi. Program Visual Studio generuje ponownie pamięć podręczną podczas zapisywania zmian w *CMakeLists.txt* lub w niektórych przypadkach, aby *CMakeSettings.jsna*. Ale jeśli korzystasz z **istniejącej konfiguracji pamięci podręcznej** , program Visual Studio nie modyfikuje pamięci podręcznej.

Aby uzyskać ogólne informacje na temat obsługi CMake w programie Visual Studio, zobacz [CMAKE projects in Visual Studio](../build/cmake-projects-in-visual-studio.md). Najpierw przeczytaj ten element przed kontynuowaniem.

Aby rozpocząć, wybierz pozycję **plik**  >  **Otwórz**  >  **folder** z menu głównego lub inny typ `devenv.exe <foldername>` w oknie [wiersza polecenia dewelopera](../build/building-on-the-command-line.md) . Otwarty folder powinien zawierać plik *CMakeLists.txt* wraz z kodem źródłowym.

W poniższym przykładzie przedstawiono prosty plik *CMakeLists.txt* i plik. cpp:

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

*CMakeLists.txt*:

```txt
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Wybierz element docelowy systemu Linux

Po otwarciu folderu Program Visual Studio analizuje plik *CMakeLists.txt* i określa element docelowy systemu Windows dla **debugowania x86**. Aby wskazać zdalny system Linux, Zmień ustawienia projektu na **Linux-Debug** lub **Linux-Release**. (Zobacz [Konfigurowanie ustawień CMAKE dla systemu Linux](#configure_cmake_linux) poniżej).

::: moniker-end

::: moniker range="vs-2019"

Aby kierować podsystem Windows dla systemu Linux, kliknij pozycję **Zarządzanie konfiguracjami** na liście rozwijanej konfiguracja na głównym pasku narzędzi. Następnie naciśnij przycisk **Dodaj konfigurację** i wybierz **WSL-Debug** lub **WSL-Release** , jeśli korzystasz z programu w zatoce. Użyj wariantów Clang, jeśli używasz zestawu narzędzi Clang/LLVM.

**Visual Studio 2019 w wersji 16,1** W przypadku określania wartości docelowej WSL nie jest wymagane kopiowanie źródeł ani nagłówków. Dzieje się tak, ponieważ kompilator w systemie Linux ma bezpośredni dostęp do plików źródłowych w systemie plików Windows. (W systemie Windows 10 w wersji 1903 lub nowszej aplikacje systemu Windows mogą również bezpośrednio uzyskiwać dostęp do plików nagłówkowych z systemem Linux. Program Visual Studio nie pozwala jeszcze korzystać z tej funkcji.

::: moniker-end

::: moniker range=">=vs-2017"

Program Visual Studio wybiera pierwszy system zdalny z listy w obszarze **Narzędzia**  >  **Opcje**  >  Menedżer połączeń**między platformami**  >  **Connection Manager** domyślnie dla zdalnych obiektów docelowych. Jeśli nie zostaną znalezione żadne połączenia zdalne, zostanie wyświetlony monit o utworzenie jednego z nich. Aby uzyskać więcej informacji, zobacz [nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](connect-to-your-remote-linux-computer.md).

Jeśli określisz docelowy zdalny system Linux, źródło zostanie skopiowane do systemu zdalnego.

Po wybraniu elementu docelowego CMake jest uruchamiany automatycznie w systemie Linux w celu wygenerowania pamięci podręcznej CMake dla projektu.

![Generowanie pamięci podręcznej CMake w systemie Linux](media/cmake-linux-1.png "Generowanie pamięci podręcznej CMake w systemie Linux")

### <a name="intellisense"></a>Technologia

Aby zapewnić obsługę funkcji IntelliSense dla nagłówków w zdalnych systemach Linux, program Visual Studio automatycznie kopiuje je z komputera z systemem Linux do katalogu na lokalnym komputerze z systemem Windows. Aby uzyskać więcej informacji, zobacz [IntelliSense dla zdalnych nagłówków](configure-a-linux-project.md#remote_intellisense).

### <a name="locale"></a>Regionalne

Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne docelowego systemu Linux](configure-a-linux-project.md#locale).

## <a name="debug-the-cmake-project"></a><a name="debug_cmake_project"></a>Debuguj projekt CMake

Aby debugować kod w określonym systemie docelowym, ustaw punkt przerwania. Wybierz obiekt docelowy CMake jako element startowy w menu paska narzędzi obok ustawienia projektu. Następnie wybierz pozycję **&#x23f5; Rozpocznij** na pasku narzędzi lub naciśnij klawisz **F5**.

Aby dostosować argumenty wiersza polecenia programu, naciśnij przycisk **Przełącz cele** w górnej części **Eksplorator rozwiązań** a następnie wybierz pozycję **widok obiektów docelowych**. Następnie kliknij prawym przyciskiem myszy obiekt docelowy i wybierz pozycję **Ustawienia debugowania i uruchamiania**. To polecenie otwiera lub tworzy *launch.vs.jsw* pliku konfiguracji, który zawiera informacje o programie. Aby określić lokalizację plików źródłowych, należy dodać do pliku Właściwość **sourceFileMap** , jak pokazano w poniższym przykładzie:

```json
"MIMode": "gdb",
"externalConsole": true,
"sourceFileMap": {
"c/Users/USER/source/repos/CMAKEPROJECTNAME": "C:\\Users\\USER\\source\\repos\\CMAKEPROJECTNAME"
},
"remoteMachineName": "${debugInfo.remoteMachineName}",
```

Aby określić dodatkowe argumenty, należy dodać je do `args` tablicy JSON. Aby uzyskać więcej informacji, zobacz temat [Otwieranie projektów folderu dla języka C++](../build/open-folder-projects-cpp.md) i [Konfigurowanie sesji debugowania CMAKE](../build/configure-cmake-debugging-sessions.md).

## <a name="configure-cmake-settings-for-linux"></a><a name="configure_cmake_linux"></a>Konfigurowanie ustawień CMake dla systemu Linux

*CMakeSettings.js* w pliku w projekcie CMAKE systemu Linux może określać wszystkie właściwości wymienione w temacie [Dostosowywanie ustawień CMAKE](../build/customize-cmake-settings.md)oraz dodatkowe właściwości kontrolujące ustawienia kompilacji na zdalnym komputerze z systemem Linux.

::: moniker-end

::: moniker range="vs-2019"

Aby zmienić domyślne ustawienia CMake w programie Visual Studio 2019, na głównym pasku narzędzi Otwórz listę rozwijaną **Konfiguracja** i wybierz pozycję **Zarządzaj konfiguracjami**.

![CMake Zarządzanie konfiguracjami](../build/media/vs2019-cmake-manage-configurations.png "Lista rozwijana konfiguracji CMake")

To polecenie powoduje wyświetlenie **edytora ustawień CMAKE**, którego można użyć do edytowania *CMakeSettings.js* pliku w folderze głównym projektu. Możesz również otworzyć plik bezpośrednio, klikając przycisk **Edytuj kod JSON** w edytorze. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień CMAKE](../build/customize-cmake-settings.md).

Domyślna konfiguracja systemu Linux — debugowanie w programie Visual Studio 2019 w wersji 16,1 i nowszej jest następująca:

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "configurationType": "Debug",
      "cmakeExecutable": "/usr/bin/cmake",
      "remoteCopySourcesExclusionList": [ ".vs", ".git", "out" ],
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_x64" ],
      "remoteMachineName": "${defaultRemoteMachineName}",
      "remoteCMakeListsRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/src",
      "remoteBuildRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/build/${name}",
      "remoteInstallRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/install/${name}",
      "remoteCopySources": true,
      "rsyncCommandArgs": "-t --delete --delete-excluded",
      "remoteCopyBuildOutput": false,
      "remoteCopySourcesMethod": "rsync",
      "addressSanitizerRuntimeFlags": "detect_leaks=0",
      "variables": []
    }
  ]
}
```

::: moniker-end

::: moniker range="vs-2017"

Aby zmienić domyślne ustawienia CMAKE w programie Visual Studio 2017, wybierz pozycję **CMAKE**  >  **Zmień ustawienia CMAKE**  >  **CMakeLists.txt** z menu głównego. Lub kliknij prawym przyciskiem myszy *CMakeSettings.txt* w **Eksplorator rozwiązań** i wybierz **Zmień ustawienia CMAKE**. Program Visual Studio tworzy następnie nowy *CMakeSettings.jsw* pliku w folderze głównym projektu. Plik można otworzyć, korzystając z edytora **ustawień CMAKE** lub bezpośrednio modyfikując plik. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień CMAKE](../build/customize-cmake-settings.md).

W poniższym przykładzie przedstawiono konfigurację domyślną dla systemu Linux — debugowanie w programie Visual Studio 2017 (i Visual Studio 2019 w wersji 16,0) na podstawie poprzedniego przykładowego kodu:

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "remoteMachineName": "${defaultRemoteMachineName}",
      "configurationType": "Debug",
      "remoteCMakeListsRoot": "/var/tmp/src/${workspaceHash}/${name}",
      "cmakeExecutable": "/usr/local/bin/cmake",
      "buildRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteInstallRoot": "/var/tmp/build/${workspaceHash}/install/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "remoteCopySourcesMethod": "rsync",
      "remoteCopySourcesExclusionList": [".vs", ".git"],
      "rsyncCommandArgs" : "-t --delete --delete-excluded",
      "remoteCopyBuildOutput" : "false",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```

::: moniker-end

::: moniker range=">=vs-2017"

Aby uzyskać więcej informacji na temat tych ustawień, zobacz [CMakeSettings.json Reference](../build/cmakesettings-reference.md).

## <a name="optional-settings"></a>Ustawienia opcjonalne

Aby uzyskać więcej kontroli, można użyć następujących ustawień opcjonalnych:

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

Te opcje umożliwiają uruchamianie poleceń w systemie Linux przed i po skompilowaniu oraz przed CMake generacji. Wartości mogą być dowolnym poleceniem, które jest prawidłowe w systemie zdalnym. Dane wyjściowe są przekazywane z powrotem do programu Visual Studio.

## <a name="see-also"></a>Zobacz też

[Praca z właściwościami projektu](../build/working-with-project-properties.md)<br/>
[CMake projekty w programie Visual Studio](../build/cmake-projects-in-visual-studio.md)<br/>
[Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](connect-to-your-remote-linux-computer.md)<br/>
[Dostosuj ustawienia CMake](../build/customize-cmake-settings.md)<br/>
[Konfigurowanie sesji debugowania narzędzia CMake](../build/configure-cmake-debugging-sessions.md)<br/>
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](deploy-run-and-debug-your-linux-project.md)<br/>
[CMake wstępnie zdefiniowanej konfiguracji](../build/cmake-predefined-configuration-reference.md)

::: moniker-end
