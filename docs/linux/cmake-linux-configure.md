---
title: Konfigurowanie projektu systemu Linux CMake w programie Visual Studio
description: Jak skonfigurować ustawienia CMake systemu Linux w programie Visual Studio
ms.date: 08/08/2020
ms.openlocfilehash: d39423b803b66d6bdf55cc67d488e74ccb682323
ms.sourcegitcommit: 2034f8e744a8b36cff8b15e9a5cfe684afebadfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2020
ms.locfileid: "88048192"
---
# <a name="configure-a-linux-cmake-project-in-visual-studio"></a>Konfigurowanie projektu systemu Linux CMake w programie Visual Studio

::: moniker range="vs-2015"
Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych. Aby wyświetlić dokumentację dla tych wersji, Ustaw listę rozwijaną **wersja** znajdującą się powyżej spisu treści w **programie Visual Studio 2017** lub **Visual Studio 2019**.
::: moniker-end

::: moniker range=">=vs-2017"
W tym temacie opisano sposób dodawania konfiguracji systemu Linux do projektu CMake, który jest przeznaczony dla zdalnego systemu Linux lub podsystemu Windows dla systemu Linux (WSL). Kontynuuje serię, która rozpoczęła się przy [tworzeniu projektu systemu Linux CMAKE w programie Visual Studio](cmake-linux-project.md). Jeśli używasz programu MSBuild, zobacz [Konfigurowanie projektu systemu Linux MSBuild w programie Visual Studio](configure-a-linux-project.md)

## <a name="add-a-linux-configuration"></a>Dodawanie konfiguracji systemu Linux

Konfiguracja może służyć jako ukierunkowana na różne platformy (Windows, WSL, system zdalny) z tym samym kodem źródłowym. Konfiguracja służy również do ustawiania kompilatorów, przekazywania zmiennych środowiskowych i dostosowywania sposobu wywoływania CMake. *CMakeSettings.jsw* pliku określa niektóre lub wszystkie właściwości wymienione w temacie [Dostosowywanie ustawień CMAKE](../build/customize-cmake-settings.md)oraz dodatkowe właściwości kontrolujące ustawienia kompilacji na zdalnym komputerze z systemem Linux.
::: moniker-end

::: moniker range="vs-2017"
Aby zmienić domyślne ustawienia CMAKE w programie Visual Studio 2017, wybierz pozycję **CMAKE**  >  **Zmień ustawienia CMAKE**  >  **CMakeLists.txt** z menu głównego. Lub kliknij prawym przyciskiem myszy *CMakeLists.txt* w **Eksplorator rozwiązań** i wybierz **Zmień ustawienia CMAKE**. Program Visual Studio tworzy następnie nowy *CMakeSettings.jsw* pliku w folderze głównym projektu. Aby wprowadzić zmiany, Otwórz plik i zmodyfikuj go bezpośrednio. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień CMAKE](../build/customize-cmake-settings.md).

Domyślna konfiguracja systemu Linux — debugowanie w programie Visual Studio 2017 (i Visual Studio 2019 w wersji 16,0) wygląda następująco:

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
Aby zmienić domyślne ustawienia CMake w programie Visual Studio 2019, na głównym pasku narzędzi Otwórz listę rozwijaną **Konfiguracja** i wybierz pozycję **Zarządzaj konfiguracjami**.

![CMake Zarządzanie konfiguracjami](../build/media/vs2019-cmake-manage-configurations.png "Lista rozwijana konfiguracji CMake")

To polecenie otwiera **Edytor ustawień CMAKE**, którego można użyć do edytowania *CMakeSettings.js* pliku w folderze głównym projektu. Możesz również otworzyć plik za pomocą edytora JSON, klikając przycisk **Edytuj JSON** w edytorze. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień CMAKE](../build/customize-cmake-settings.md).

Domyślna konfiguracja systemu Linux — debugowanie w programie Visual Studio 2019 w wersji 16,1 i nowszej wygląda następująco:

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

W programie Visual Studio 2019 w wersji 16,6 lub nowszej Ninja jest domyślnym generatorem dla konfiguracji przeznaczonych dla zdalnego systemu lub WSL. Aby uzyskać więcej informacji, zobacz ten wpis na [blogu zespołu języka C++](https://devblogs.microsoft.com/cppblog/linux-development-with-visual-studio-first-class-support-for-gdbserver-improved-build-times-with-ninja-and-updates-to-the-connection-manager/).

::: moniker-end
::: moniker range=">=vs-2017"
Aby uzyskać więcej informacji na temat tych ustawień, zobacz [CMakeSettings.json Reference](../build/cmakesettings-reference.md).

Po wykonaniu kompilacji:
- Jeśli obiektem docelowym jest system zdalny, program Visual Studio wybiera pierwszy system zdalny na liście w obszarze **Narzędzia** > **Opcje** > **Cross Platform** > **Menedżer połączeń** wielu platform domyślnie dla zdalnych obiektów docelowych.
- Jeśli nie zostaną znalezione żadne połączenia zdalne, zostanie wyświetlony monit o utworzenie jednego z nich. Aby uzyskać więcej informacji, zobacz [nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](connect-to-your-remote-linux-computer.md).

## <a name="choose-a-linux-target"></a>Wybierz element docelowy systemu Linux

Po otwarciu folderu projektu CMake program Visual Studio analizuje plik *CMakeLists.txt* i określa element docelowy systemu Windows dla **debugowania x86**. Aby wskazać zdalny system Linux, Zmień ustawienia projektu na **Linux-Debug** lub **Linux-Release**.

Jeśli określisz docelowy zdalny system Linux, źródło zostanie skopiowane do systemu zdalnego.

Po wybraniu elementu docelowego CMake jest uruchamiany automatycznie w systemie Linux w celu wygenerowania pamięci podręcznej CMake dla projektu:

![Generowanie pamięci podręcznej CMake w systemie Linux](media/cmake-linux-1.png "Generowanie pamięci podręcznej CMake w systemie Linux")

::: moniker-end
::: moniker range="vs-2019"

### <a name="target-windows-subsystem-for-linux"></a>Docelowy podsystem Windows dla systemu Linux

W przypadku korzystania z podsystemu Windows dla systemu Linux (WSL) nie trzeba dodawać połączenia zdalnego.

Aby docelowa WSL, wybierz pozycję **Zarządzaj konfiguracjami** na liście rozwijanej konfiguracji na głównym pasku narzędzi. Następnie naciśnij przycisk **Dodaj konfigurację** i wybierz **WSL-Debug** lub **WSL-Release** , jeśli korzystasz z programu w zatoce. Użyj wariantów Clang, jeśli używasz zestawu narzędzi Clang/LLVM.

**Visual Studio 2019 w wersji 16,1** Gdy docelowa jest WSL, program Visual Studio nie musi kopiować plików źródłowych i zachować dwóch synchronicznych kopii drzewa kompilacji, ponieważ kompilator w systemie Linux ma bezpośredni dostęp do plików źródłowych w zainstalowanym systemie plików Windows.
::: moniker-end
::: moniker range=">=vs-2017"

### <a name="intellisense"></a>IntelliSense

Dokładne funkcje IntelliSense języka C++ wymagają dostępu do nagłówków języka C++, do których odwołują się pliki źródłowe języka C++. Program Visual Studio automatycznie używa nagłówków, do których odwołuje się projekt CMake z systemu Linux do Windows, aby zapewnić obsługę funkcji IntelliSense o pełnej wierności. Aby uzyskać więcej informacji, zobacz [IntelliSense dla zdalnych nagłówków](configure-a-linux-project.md#remote_intellisense).

### <a name="locale-setting"></a>Ustawienie regionalne

Ustawienia języka programu Visual Studio nie są propagowane do celów systemu Linux, ponieważ program Visual Studio nie zarządza ani nie konfiguruje zainstalowanych pakietów. Komunikaty wyświetlane w oknie danych wyjściowych, takie jak błędy kompilacji, są wyświetlane przy użyciu języka i ustawień regionalnych docelowego systemu Linux. Należy skonfigurować cele systemu Linux dla żądanych ustawień regionalnych.

## <a name="additional-settings"></a>Ustawienia dodatkowe

Użyj następujących ustawień, aby uruchomić polecenia w systemie Linux przed i po skompilowaniu oraz przed CMake generacji. Wartości mogą być dowolnym poleceniem, które jest prawidłowe w systemie zdalnym. Dane wyjściowe są przekazywane z powrotem do programu Visual Studio.

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

## <a name="next-steps"></a>Następne kroki

[Konfigurowanie sesji debugowania narzędzia CMake](../build/configure-cmake-debugging-sessions.md)

## <a name="see-also"></a>Zobacz także

[Praca z właściwościami projektu](../build/working-with-project-properties.md)<br/>
[Dostosuj ustawienia CMake](../build/customize-cmake-settings.md)<br/>
[CMake wstępnie zdefiniowanej konfiguracji](../build/cmake-predefined-configuration-reference.md)

::: moniker-end
