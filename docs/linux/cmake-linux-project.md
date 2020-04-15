---
title: Tworzenie i konfigurowanie projektu CMake systemu Linux w programie Visual Studio
description: Jak utworzyć, skonfigurować, edytować i skompilować projekt CMake systemu Linux w programie Visual Studio
ms.date: 10/04/2019
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 63c1f7953682e4d491660a18bedfa3d0ca4305ae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364389"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>Tworzenie i konfigurowanie projektu CMake systemu Linux

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range="vs-2019"

Aby utworzyć nowy projekt Linux CMake w programie Visual Studio 2019:

1. Wybierz **opcję Plik > nowy projekt** w programie Visual Studio lub naciśnij **klawisze Ctrl + Shift + N**.
1. Ustaw **język** na **C++** i wyszukaj "CMake". Następnie wybierz pozycję **Dalej**. Wprowadź **nazwę** i **lokalizację**, a następnie wybierz pozycję **Utwórz**.

Visual Studio tworzy minimalny plik CMakeLists.txt tylko nazwę pliku wykonywalnego i minimalna wersja CMake wymagane. Możesz ręcznie edytować ten plik w jak 1998 r.; Visual Studio nigdy nie zastąpi zmian. Argumenty wiersza polecenia CMake i zmienne środowiskowe można określić, klikając prawym przyciskiem myszy główny plik CMakeLists.txt w **Eksploratorze rozwiązań** i wybierając **ustawienia CMake dla projektu**. Aby określić opcje debugowania, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Debugowanie i uruchom ustawienia**.

::: moniker-end

Po otwarciu folderu, który zawiera istniejący projekt CMake, Visual Studio używa zmiennych w pamięci podręcznej CMake skonfigurować IntelliSense i buduje automatycznie. Ustawienia konfiguracji lokalnej i debugowania są przechowywane w plikach JSON, które opcjonalnie mogą być współużytkowane innym osobom korzystającym z programu Visual Studio.

Visual Studio nie modyfikuje plików CMakeLists.txt, dzięki czemu inni pracujący nad tym samym projektem mogą nadal używać narzędzi, których już używają. Visual Studio nie ponownie wygenerować pamięci podręcznej podczas zapisywania zmian do CMakeLists.txt lub w niektórych przypadkach do CMakeSettings.json. Ale jeśli używasz istniejącej konfiguracji **pamięci podręcznej,** program Visual Studio nie modyfikuje pamięci podręcznej.

Aby uzyskać ogólne informacje na temat pomocy technicznej CMake w programie Visual Studio, zobacz [CMake projektów w programie Visual Studio](../build/cmake-projects-in-visual-studio.md). Przeczytaj to najpierw przed kontynuowaniem tutaj.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Najpierw upewnij się, że masz **zainstalowany programowy linuksa z** zainstalowanym obciążeniem C++, w tym składnik CMake. Zobacz [Instalowanie obciążenia systemu Linux w programie Visual Studio.](download-install-and-setup-the-linux-development-workload.md)

W systemie Linux upewnij się, że są zainstalowane następujące elementy:

- Gcc
- Gdb
- Rsync
- Zip
- ninja-build

::: moniker range="vs-2019"

Obsługa systemu Linux dla projektów CMake wymaga najnowszej wersji CMake do zainstalowania na komputerze docelowym. Często wersja oferowana przez domyślny menedżer pakietów dystrybucji nie jest wystarczająco aktualna, aby obsługiwać wszystkie funkcje wymagane przez program Visual Studio. Visual Studio 2019 wykrywa, czy najnowsza wersja CMake jest zainstalowana w systemie Linux. Jeśli nie zostanie znaleziony, program Visual Studio pokazuje pasek informacji w górnej części okienka edytora, który oferuje zainstalowanie go dla Ciebie z [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

Obsługa CMake w programie Visual Studio wymaga obsługi trybu serwera, który został wprowadzony w CMake 3.8. W programie Visual Studio 2019 zaleca się wersję 3.14 lub nowszą.

::: moniker-end

::: moniker range="vs-2017"

Obsługa CMake w programie Visual Studio wymaga obsługi trybu serwera, który został wprowadzony w CMake 3.8. W przypadku wariantu CMake dostarczonego przez firmę [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases)Microsoft pobierz najnowsze wstępnie utworzone pliki binarne w programie .

Pliki binarne zostaną `~/.vs/cmake`zainstalowane w pliku . Po wdrożeniu plików binarnych projekt zostanie automatycznie ponownie wygenerowany. Należy zauważyć, że jeśli CMake określony przez `cmakeExecutable` pole w `CMakeSettings.json` jest nieprawidłowy (nie istnieje lub jest nieobsługiwana `cmakeExecutable` wersja) i wstępnie utworzone pliki binarne są obecne Visual Studio zignoruje i użyje wstępnie utworzonych plików binarnych.

:::moniker-end

## <a name="open-a-folder"></a>Otwieranie folderu

Aby rozpocząć, wybierz polecenie**Folder otwierania** >  **pliku** > z menu głównego lub wpisz**Folder** `devenv.exe <foldername>` w wierszu polecenia. Otwarty folder powinien mieć plik CMakeLists.txt wraz z kodem źródłowym.
W poniższym przykładzie przedstawiono prosty plik CMakeLists.txt i plik cpp:

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

CMakeLists.txt:

```cmd
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Wybierz cel systemu Linux

Po otwarciu folderu program Visual Studio analizuje plik CMakeLists.txt i określa cel systemu Windows **x86-Debug**. Aby kierować reklamy na zdalny system Linux, zmień ustawienia projektu na **Linux-Debug** lub **Linux-Release**. (Zobacz [Konfigurowanie ustawień CMake dla linuksa](#configure_cmake_linux) poniżej).

::: moniker range="vs-2019"

Aby kierować reklamy na podsystem windows dla systemu Linux, kliknij pozycję **Zarządzaj konfiguracjami** w rozwijanej konfiguracji na głównym pasku narzędzi. Następnie naciśnij przycisk **Dodaj konfigurację** i wybierz **WSL-Debug** lub **WSL-Release,** jeśli używasz GCC, lub warianty Clang, jeśli używasz zestawu narzędzi Clang/LLVM.

**Visual Studio 2019 w wersji 16.1** Podczas kierowania na WSL nie jest konieczne kopiowanie źródeł lub nagłówków, ponieważ kompilator w systemie Linux ma bezpośredni dostęp do systemu plików Windows, w którym znajdują się pliki źródłowe. (W systemie Windows w wersji 1903 i nowszej aplikacje systemu Windows również mogą uzyskać bezpośredni dostęp do plików nagłówkowych systemu Linux, ale program Visual Studio nie korzysta jeszcze z tej możliwości).

::: moniker-end

W przypadku obiektów docelowych zdalnych program Visual Studio domyślnie wybiera pierwszy system zdalny na liście > w obszarze Menedżer połączeń**międzyplatformowych** > **Connection Manager****Opcje** **narzędzi** > . Jeśli nie zostaną znalezione żadne połączenia zdalne, zostanie wyświetlony monit o ich utworzenie. Aby uzyskać więcej informacji, zobacz [Łączenie się ze zdalnym komputerem z systemem Linux](connect-to-your-remote-linux-computer.md).

Jeśli określisz zdalny cel systemu Linux, źródło zostanie skopiowane do systemu zdalnego.

Po wybraniu obiektu docelowego CMake uruchamia się automatycznie w systemie Linux, aby wygenerować pamięć podręczną CMake dla projektu.

![Generowanie pamięci podręcznej CMake w systemie Linux](media/cmake-linux-1.png "Generowanie pamięci podręcznej CMake w systemie Linux")

Aby zapewnić obsługę intellisense dla nagłówków w zdalnych systemach Linux, program Visual Studio automatycznie kopiuje je z komputera z systemem Linux do katalogu na lokalnym komputerze z systemem Windows. Aby uzyskać więcej informacji, zobacz [IntelliSense dla nagłówków zdalnych](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-cmake-project"></a><a name="debug_cmake_project"></a>Debugowanie projektu CMake

Aby debugować kod w określonym systemie docelowym debugowania, ustaw punkt przerwania, wybierz cMake target jako element startowy w menu paska narzędzi obok ustawienia projektu i wybierz **&#x23f5; Start** na pasku narzędzi lub naciśnij klawisz F5.

Aby dostosować argumenty wiersza polecenia programu, naciśnij przycisk **Przełącz cele** u góry **Eksploratora rozwiązań,** a następnie wybierz pozycję **Widok obiektów docelowych**. Następnie kliknij prawym przyciskiem myszy na cel i wybierz **debugowanie i uruchom ustawienia**. Spowoduje to otwarcie lub utworzenie pliku konfiguracyjnego launch.vs.json zawierającego informacje o programie. Aby określić lokalizację plików źródłowych, dodaj do pliku właściwość **sourceFileMap,** jak pokazano w tym przykładzie:

```json
"MIMode": "gdb",
"externalConsole": true,
"sourceFileMap": {
"c/Users/USER/source/repos/CMAKEPROJECTNAME": "C:\\Users\\USER\\source\\repos\\CMAKEPROJECTNAME"
},
"remoteMachineName": "${debugInfo.remoteMachineName}",
```

Aby określić dodatkowe argumenty, `args` dodaj je w tablicy JSON. Aby uzyskać więcej informacji, zobacz [Otwieranie projektów folderów dla języka C++](../build/open-folder-projects-cpp.md) i [Konfigurowanie sesji debugowania CMake](../build/configure-cmake-debugging-sessions.md).

## <a name="configure-cmake-settings-for-linux"></a><a name="configure_cmake_linux"></a>Konfigurowanie ustawień CMake dla systemu Linux

Plik CMakeSettings.json w projekcie CMake Linux można określić wszystkie właściwości wymienione w [Dostosuj ustawienia CMake,](../build/customize-cmake-settings.md)plus dodatkowe właściwości, które kontrolują ustawienia kompilacji na zdalnym komputerze z systemem Linux.

::: moniker range="vs-2019"

Aby zmienić domyślne ustawienia CMake w programie Visual Studio 2019, z głównego paska narzędzi otwórz okno **rozwijane Konfiguracja** i wybierz pozycję **Zarządzaj konfiguracjami**.

![CMake Zarządzaj konfiguracjami](../build/media/vs2019-cmake-manage-configurations.png "CKsuj konfiguracje rozwijane")

Spowoduje to wyświetlenie **Edytora ustawień CMake,** którego można użyć do edycji `CMakeSettings.json` pliku w głównym folderze projektu. Plik można również otworzyć bezpośrednio, klikając przycisk **Edytuj JSON** w edytorze. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień CMake](../build/customize-cmake-settings.md).

::: moniker-end

::: moniker range="vs-2017"

Aby zmienić domyślne ustawienia CMake w programie Visual Studio 2017, wybierz **CMake | Zmień ustawienia CMake | CMakeLists.txt** z menu głównego lub kliknij prawym przyciskiem myszy CMakeSettings.txt w **Eksploratorze rozwiązań** i wybierz polecenie **Zmień ustawienia CMake**. Program Visual Studio `CMakeSettings.json` następnie tworzy nowy plik w głównym folderze projektu. Plik można otworzyć za pomocą **edytora CMake Settings** lub bezpośrednio zmodyfikować plik. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień CMake](../build/customize-cmake-settings.md).

W poniższym przykładzie przedstawiono domyślną konfigurację systemu Linux-Debug w programie Visual Studio 2017 (i programie Visual Studio 2019 w wersji 16.0) na podstawie poprzedniego przykładu kodu:

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

::: moniker range="vs-2019"

Domyślna konfiguracja linuksowo-debugowania w programie Visual Studio 2019 w wersji 16.1 i nowszej jest przedstawiona w tym miejscu:

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

Aby uzyskać więcej informacji na temat tych ustawień, zobacz [CMakeSettings.json reference](../build/cmakesettings-reference.md).

## <a name="optional-settings"></a>Ustawienia opcjonalne

Aby uzyskać większą kontrolę, można użyć następujących ustawień opcjonalnych:

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

Te opcje umożliwiają uruchamianie poleceń w systemie Linux przed i po budowie oraz przed generowaniem CMake. Wartości mogą być dowolnym poleceniem, które jest prawidłowe w systemie zdalnym. Dane wyjściowe są potokami z powrotem do programu Visual Studio.

## <a name="see-also"></a>Zobacz też

[Praca z właściwościami projektu](../build/working-with-project-properties.md)<br/>
[CMake projekty w programie Visual Studio](../build/cmake-projects-in-visual-studio.md)<br/>
[Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](connect-to-your-remote-linux-computer.md)<br/>
[Dostosowywanie ustawień CMake](../build/customize-cmake-settings.md)<br/>
[Konfigurowanie sesji debugowania narzędzia CMake](../build/configure-cmake-debugging-sessions.md)<br/>
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](deploy-run-and-debug-your-linux-project.md)<br/>
[CZrobe wstępnie zdefiniowane odwołanie do konfiguracji](../build/cmake-predefined-configuration-reference.md)<br/>
