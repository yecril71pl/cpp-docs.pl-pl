---
title: Konfigurowanie projektu CMake systemu Linux w programie Visual Studio | Dokumentacja firmy Microsoft
description: Konfigurowanie projektu CMake systemu Linux w programie Visual Studio
ms.custom: ''
ms.date: 07/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: b7c28a8e67ef2731d26071262383e93d32be9583
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064111"
---
# <a name="configure-a-linux-cmake-project"></a>Konfigurowanie projektu CMake systemu Linux

**Visual Studio 2017 w wersji 15.4 lub nowszy**<br/>
Po zainstalowaniu obciążenia języka Linux C++ dla Visual Studio Obsługa CMake dla systemu Linux jest domyślnie zaznaczone. Teraz możesz pracować na istniejącej bazie kodu używającej narzędzia CMake bez konieczności konwertowania go do projektu programu Visual Studio. Jeśli baza kodu jest dla wielu platform, mogą kierować zarówno Windows, jak i Linux z poziomu programu Visual Studio.

W tym temacie założono, że masz podstawowe znajomość Obsługa CMake w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [narzędzia CMake w języku Visual C++](../ide/cmake-tools-for-visual-cpp.md). Aby uzyskać więcej informacji na temat narzędzia CMake, sama zobacz [kompilacji, testów i pakietów usługi oprogramowania za pomocą narzędzia CMake](https://cmake.org/).

> [!NOTE]
> Obsługa CMake w programie Visual Studio wymaga obsługi trybu serwera, która została wprowadzona w CMake 3.8. Dla wariantu dostarczonych przez firmę Microsoft narzędzia CMake pobrać najnowsze wstępnie utworzone pliki binarne w [ https://github.com/Microsoft/CMake/releases ](https://github.com/Microsoft/CMake/releases).

## <a name="open-a-folder"></a>Otwieranie folderu

Aby rozpocząć, wybierz opcję **pliku** > **Otwórz** > **folderu** z menu głównego w przeciwnym razie wpisz `devenv.exe <foldername>` w wierszu polecenia. Folder, który można otworzyć powinny mieć plik CMakeLists.txt, wraz z kodem źródłowym.
Poniższy przykład pokazuje prosty plik CMakeLists.txt i plik .cpp:

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
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Wybierz element docelowy z systemem Linux

Zaraz po otwarciu folderu, programu Visual Studio analizuje plik CMakeLists.txt i określa obiekt docelowy Windows **debugowania x86**. Aby wskazać system Linux, należy zmienić ustawienia projektu do **debugowania dla systemu Linux** lub **wydania Linux**.

Domyślnie program Visual Studio wybiera pierwszy system zdalny na liście w obszarze **narzędzia** > **opcje** > **Międzyplatformowe**  >  **Menedżera połączeń**. Nie zostaną znalezione nie połączeń zdalnych, monit o jego utworzenie.

Po określeniu docelowej systemu Linux, źródło jest kopiowany do maszyną z systemem Linux. Następnie CMake jest uruchamiane na maszynie systemu Linux w celu wygenerowania pamięci podręcznej narzędzia CMake dla Twojego projektu.

![Generuj pamięć podręczną CMake w systemie Linux](media/cmake-linux-1.png "wygenerowania pamięci podręcznej narzędzia CMake w systemie Linux")

**Visual Studio 2017 w wersji 15.7 lub nowszej:**<br/>
Aby zapewnić obsługę funkcji IntelliSense dla zdalnych nagłówków, Visual Studio automatycznie kopiuje je do katalogu na komputerze lokalnym Windows. Aby uzyskać więcej informacji, zobacz [technologii IntelliSense dla zdalnych nagłówków](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-project"></a>Debugowanie projektu

Podczas debugowania kodu w systemie zdalnym, ustaw punkt przerwania, wybierz element docelowy narzędzia CMake jako element startowy w menu narzędzi obok ustawienia projektu i wybierz  **&#x23f5; Start** na pasku narzędzi lub naciśnięciu klawisza F5.

Aby dostosować argumenty wiersza polecenia programu, kliknij prawym przyciskiem myszy plik wykonywalny w **Eksploratora rozwiązań** i wybierz **ustawienia debugowania i uruchamiania**. To spowoduje otwarcie lub tworzy plik konfiguracji pliku launch.vs.json, który zawiera informacje o programie. Aby określić dodatkowe argumenty, dodaj je w `args` tablicę JSON. Aby uzyskać więcej informacji, zobacz [projekty Otwórz Folder w programie Visual C++](../ide/non-msbuild-projects.md).

## <a name="configure-cmake-settings-for-linux"></a>Konfiguruj ustawienia narzędzia CMake dla systemu Linux

Aby zmienić domyślne ustawienia narzędzia CMake, wybierz **CMake | Zmień ustawienia narzędzia CMake | CMakeLists.txt** z menu głównego, lub kliknij prawym przyciskiem myszy CMakeSettings.txt w **Eksploratora rozwiązań** i wybierz polecenie **Zmień ustawienia narzędzia CMake**. Program Visual Studio tworzy nowy plik w folderze o nazwie `CMakeSettings.json` , jest wypełniana przy użyciu domyślnej konfiguracji, które są wymienione w elemencie menu ustawień projektu. Poniższy przykład pokazuje, w domyślnej konfiguracji debugowania dla systemu Linux na podstawie w poprzednim przykładzie kodu:

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

`name` Wartość może być wedle uznania. `remoteMachineName` Wartość określa którego zdalnego systemu docelowego, w przypadku, gdy masz więcej niż jeden. Technologia IntelliSense jest włączona dla tego pola, które ułatwią Ci wybrać odpowiednie system. Pole `remoteCMakeListsRoot` Określa, gdzie źródła projektu zostaną skopiowane do systemu zdalnego. Pole `remoteBuildRoot` jest, gdzie zostaną wygenerowane dane wyjściowe kompilacji w systemie zdalnym. Dane wyjściowe również lokalnie kopiowany do lokalizacji określonej przez `buildRoot`. `remoteInstallRoot` i `installRoot` pola są podobne do `remoteBuildRoot` i `buildRoot`, z wyjątkiem odnoszą się w trakcie instalacji narzędzia cmake. `remoteCopySources` Wpis kontroluje, czy źródłach lokalnych są kopiowane do maszyny zdalnej. Możesz ustawić to wartość false, jeśli masz wiele plików, a już synchronizowania źródeł samodzielnie. `remoteCopyOutputVerbosity` Wartość określa poziom szczegółowości krok kopiowania, w przypadku, gdy musisz zdiagnozować błędy. `remoteCopySourcesConcurrentCopies` Wpis steruje, jak wiele procesów jest zduplikowany kopiowanie. `remoteCopySourcesMethod` Wartość może być jednym z rsync lub sftp. `remoteCopySourcesExclusionList` Pola pozwala na kontrolowanie, co kopiowane do maszyny zdalnej. `rsyncCommandArgs` Wartość umożliwia sterowanie rsync metoda kopiowania. `remoteCopyBuildOutput` Pola określa, czy dane wyjściowe kompilacji zdalnej jest kopiowany do folderu kompilacji lokalnej.

Dostępne są także niektóre ustawienia opcjonalne, których można użyć, aby uzyskać większą kontrolę:

```json
{
      "remotePreBuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostBuildCommand": "",
}
```

Te opcje umożliwiają uruchamianie poleceń w oknie zdalnego, przed i po kompilacji, a przed generowania narzędzia CMake. Mogą to być wszystkie prawidłowe polecenia w oknie zdalnego. Dane wyjściowe w potoku do programu Visual Studio.

## <a name="download-prebuilt-cmake-binaries"></a>Pobierz wstępnie utworzone narzędzia CMake plików binarnych.

Twoje dystrybucja systemu Linux może być starszą wersję narzędzia CMake. Obsługa CMake w programie Visual Studio wymaga obsługi trybu serwera, która została wprowadzona w CMake 3.8. Dla wariantu dostarczonych przez firmę Microsoft narzędzia CMake pobrać najnowsze wstępnie utworzone pliki binarne w [ https://github.com/Microsoft/CMake/releases ](https://github.com/Microsoft/CMake/releases).

## <a name="see-also"></a>Zobacz też

[Praca z właściwościami projektu](../ide/working-with-project-properties.md)<br/>
[Narzędzia CMake w języku Visual C++](../ide/cmake-tools-for-visual-cpp.md)
