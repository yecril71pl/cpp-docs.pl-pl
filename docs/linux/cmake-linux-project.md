---
title: Tworzenie i konfigurowanie projektu CMake systemu Linux w programie Visual Studio
description: Jak tworzyć, konfigurować, edytowanie i kompilowanie projektu CMake systemu Linux w programie Visual Studio
ms.date: 06/12/2019
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: d70ffe593cc014bca40a447a9cdb1c1c96a40e3f
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042676"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>Tworzenie i konfigurowanie projektu CMake systemu Linux

::: moniker range="vs-2015"

Pomoc techniczna Linux support jest dostępne w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

::: moniker range="vs-2019"

Aby utworzyć nowy projekt narzędzia CMake systemu Linux w programie Visual Studio 2019 r.:

1. Wybierz **Plik > Nowy projekt** w programie Visual Studio lub naciśnij klawisz **Ctrl + Shift + N**.
1. Ustaw **języka** do **C++** i poszukaj pozycji "Narzędzia CMake". Następnie wybierz **dalej**. Wprowadź **nazwa** i **lokalizacji**i wybierz polecenie **Utwórz**.

Visual Studio tworzy minimalny plik CMakeLists.txt za pomocą tylko nazwę pliku wykonywalnego i minimalna wymagana wersja narzędzia CMake. Możesz ręcznie edytować ten plik możesz dowolnie; Program Visual Studio nigdy nie zastąpi zmiany. Można określić argumenty wiersza polecenia narzędzia CMake i zmienne środowiskowe, klikając prawym przyciskiem myszy pliku CMakeLists.txt w **Eksploratora rozwiązań** i wybierając pozycję **ustawienia narzędzia CMake dla projektu**. Aby określić opcje dla debugowania, kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz **ustawienia debugowania i uruchamiania**.

::: moniker-end

Po otwarciu folderu zawierającego istniejącego projektu narzędzia CMake, Visual Studio używa metadanych, które CMake generuje do skonfigurowania funkcji IntelliSense i automatyczne kompilacje. Lokalnej konfiguracji i ustawieniami debugowania są przechowywane w plikach w formacie JSON, które można opcjonalnie można udostępniać innym użytkownikom, którzy korzystają z programu Visual Studio. 

Program Visual Studio nie powoduje modyfikacji pliku CMakeLists.txt tak, aby inne nad tym samym projekcie można nadal korzystać z dowolnych narzędzi jest już używany. Program Visual Studio ponownie wygenerować pamięci podręcznej, po wprowadzeniu zmian do pliku CMakeLists.txt lub w niektórych przypadkach do pliku CMakeSettings.json. Ale jeśli używasz **istniejąca pamięć podręczna** konfiguracji, a następnie programu Visual Studio nie powoduje modyfikacji pamięci podręcznej.

Aby uzyskać ogólne informacje o pomocy CMake w programie Visual Studio, zobacz [projektów CMake w programie Visual Studio](../build/cmake-projects-in-visual-studio.md). Przeczytaj, że przed kontynuowaniem tutaj.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Najpierw upewnij się, że masz **programowanie dla systemu Linux przy użyciu języka C++** obciążenia zainstalowany, w tym składnik narzędzia CMake. Zobacz [Zainstaluj obciążenie systemu Linux w języku C++ w programie Visual Studio](download-install-and-setup-the-linux-development-workload.md). 

W systemie Linux upewnij się, że instalowane są następujące elementy: 

- gcc
- gdb
- polecenia rsync
- ZIP 

::: moniker range="vs-2019"

Pomoc techniczna Linux support w przypadku projektów CMake wymaga najnowszej wersji narzędzia CMake w celu zainstalowania na komputerze docelowym. Często wersji oferowanych przez Menedżera pakietów domyślne dystrybucji nie jest wystarczająco obsługują te same funkcje, które są wymagane przez program Visual Studio. Visual Studio 2019 wykrywa, czy zainstalowano najnowszą wersję narzędzia CMake, w systemie Linux. Jeśli nie zostanie znaleziony, Visual Studio Wyświetla pasek informacyjny w górnej części okienka edytora, który umożliwia zainstalowanie aplikacji za Ciebie z [ https://github.com/Microsoft/CMake/releases ](https://github.com/Microsoft/CMake/releases).

Obsługa CMake w programie Visual Studio wymaga obsługi trybu serwera, która została wprowadzona w CMake 3.8. W programie Visual Studio 2019 r zaleca się wersji 3.14 lub nowszej.

::: moniker-end

::: moniker range="vs-2017"

Obsługa CMake w programie Visual Studio wymaga obsługi trybu serwera, która została wprowadzona w CMake 3.8. Dla wariantu CMake dostarczonych przez firmę Microsoft, Pobierz najnowszy wstępnie utworzone pliki binarne w [ https://github.com/Microsoft/CMake/releases ](https://github.com/Microsoft/CMake/releases).

Pliki binarne zostanie zainstalowana tak, aby `~/.vs/cmake`. Po wdrożeniu plików binarnych, projekt zostanie automatycznie ponownie wygenerować. Należy pamiętać, że jeśli narzędzia CMake, określony przez `cmakeExecutable` pole `CMakeSettings.json` jest nieprawidłowy (nie istnieje lub ma nieobsługiwaną wersję) i istnieją wstępnie utworzone pliki binarne programu Visual Studio będzie ignorować `cmakeExecutable` i korzystać ze wstępnie utworzonych plików binarnych.

:::moniker-end

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
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Wybierz element docelowy z systemem Linux

Zaraz po otwarciu folderu, programu Visual Studio analizuje plik CMakeLists.txt i określa obiekt docelowy Windows **debugowania x86**. Aby skierować je do zdalnego systemu Linux, należy zmienić ustawienia projektu do **debugowania dla systemu Linux** lub **wydania Linux**. (Zobacz [Konfiguruj ustawienia narzędzia CMake dla systemu Linux](#configure_cmake_linux) poniżej.)

::: moniker range="vs-2019"

Docelowe podsystemu Windows dla systemu Linux, kliknij **Zarządzanie konfiguracjami** w liście rozwijanej configuration na głównym pasku narzędzi. Następnie naciśnij klawisz **Dodawanie konfiguracji** przycisk, a następnie wybierz **debugowania WSL** lub **WSL wersji** Jeśli używasz kompilatorów GCC dla procesorów lub wariantów Clang, jeśli przy użyciu zestawu narzędzi Clang/LLVM. 

**Visual Studio 2019 wersji 16.1** przy przeznaczeniu WSL, nie kopiowania źródeł lub nagłówki jest konieczne, ponieważ kompilator w systemie Linux ma bezpośredni dostęp do systemu plików Windows, gdzie znajdują się plików źródłowych. (W wersji Windows 1903 lub nowszy, Windows aplikacje podobnie mają dostęp do plików nagłówka systemu Linux bezpośrednio, ale Visual Studio nie jeszcze korzystać z zalet tej funkcji).

::: moniker-end

Dla celów zdalnego programu Visual Studio domyślnie wybiera pierwszy system zdalny na liście w obszarze **narzędzia** > **opcje** > **Międzyplatformowe**  >  **Menedżera połączeń**. Nie zostaną znalezione nie połączeń zdalnych, monit o jego utworzenie. Aby uzyskać więcej informacji, zobacz [nawiązywanie połączenia zdalnego komputer z systemem Linux](connect-to-your-remote-linux-computer.md).

Jeśli określisz zdalnego docelowej systemu Linux, źródło jest kopiowany do systemu zdalnego.

Po zaznaczeniu elementu docelowego CMake uruchamia się automatycznie w systemie Linux do generowania pamięci podręcznej narzędzia CMake dla Twojego projektu. 

![Generuj pamięć podręczną CMake w systemie Linux](media/cmake-linux-1.png "wygenerowania pamięci podręcznej narzędzia CMake w systemie Linux")

Aby zapewnić obsługę funkcji IntelliSense dla nagłówków w zdalnych systemów Linux, Visual Studio automatycznie kopiuje je z maszyny z systemem Linux do katalogu na komputerze lokalnym Windows. Aby uzyskać więcej informacji, zobacz [technologii IntelliSense dla zdalnych nagłówków](configure-a-linux-project.md#remote_intellisense).

## <a name="debug_cmake_project"></a> Debugowanie projektu narzędzia CMake

Podczas debugowania kodu w systemie docelowym określonym debugowania, ustaw punkt przerwania, wybierz element docelowy narzędzia CMake jako element startowy w menu narzędzi obok ustawienia projektu i wybierz  **&#x23f5; Start** na pasku narzędzi lub naciśnięciu klawisza F5.

Aby dostosować argumenty wiersza polecenia programu, naciśnij klawisz **cele przełącznika** znajdujący się u góry **Eksploratora rozwiązań** , a następnie wybierz **widok elementów docelowych**. Kliknij prawym przyciskiem myszy docelowy, a następnie wybierz pozycję **ustawienia debugowania i uruchamiania**. To spowoduje otwarcie lub tworzy plik konfiguracji pliku launch.vs.json, który zawiera informacje o programie. Aby określić dodatkowe argumenty, dodaj je w `args` tablicę JSON. Aby uzyskać więcej informacji, zobacz [Otwórz Folder projektów w języku C++](../build/open-folder-projects-cpp.md) i [konfigurowania CMake sesjami debugowania](../build/configure-cmake-debugging-sessions.md).

## <a name="configure_cmake_linux"></a> Konfiguruj ustawienia narzędzia CMake dla systemu Linux

Określić wszystkie właściwości, które są wymienione w pliku CMakeSettings.json w projektu CMake systemu Linux [CMake dostosować ustawienia](../build/customize-cmake-settings.md), oraz dodatkowe właściwości, które kontrolują ustawienia kompilacji na zdalnym komputerze z systemem Linux. 

::: moniker range="vs-2019"

Aby zmienić domyślne ustawienia narzędzia CMake w programie Visual Studio 2019 r, z głównym pasku narzędzi, otwórz **konfiguracji** listy rozwijanej i wybierz polecenie **Zarządzanie konfiguracjami**. 

![Konfiguracje zarządzania CMake](../build/media/vs2019-cmake-manage-configurations.png "konfiguracji narzędzia CMake listy rozwijanej")

Spowoduje to przejście **edytora ustawienia narzędzia CMake** używane do edycji `CMakeSettings.json` pliku w folderze głównym projektu. Można również otworzyć plik bezpośrednio, klikając **Edycja JSON** przycisku w edytorze. Aby uzyskać więcej informacji, zobacz [dostosować ustawienia narzędzia CMake](../build/customize-cmake-settings.md).

::: moniker-end

::: moniker range="vs-2017"

Aby zmienić domyślne ustawienia narzędzia CMake w programie Visual Studio 2017, wybierz **CMake | Zmień ustawienia narzędzia CMake | CMakeLists.txt** z menu głównego, lub kliknij prawym przyciskiem myszy CMakeSettings.txt w **Eksploratora rozwiązań** i wybierz polecenie **Zmień ustawienia narzędzia CMake**. Program Visual Studio utworzy nowy `CMakeSettings.json` pliku w folderze głównym projektu. Możesz otworzyć plik, używając **ustawienia narzędzia CMake** edytora lub bezpośrednio zmodyfikować plik. Aby uzyskać więcej informacji, zobacz [CMake dostosować ustawienia](../build/customize-cmake-settings.md).

Poniższy przykład przedstawia konfigurację domyślną dla systemu Linux debugowania programu Visual Studio 2017 (i Visual Studio 2019 wersji 16.0) na podstawie poprzedniego przykładu kodu:

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

 Domyślna konfiguracja debugowania dla systemu Linux w Visual Studio 2019 wersji 16.1 i nowszych jest, jak pokazano poniżej:

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

Aby uzyskać więcej informacji o tych ustawieniach, zobacz [odwołania w pliku CMakeSettings.json](../build/cmakesettings-reference.md).


## <a name="optional-settings"></a>Ustawienia opcjonalne

Aby uzyskać większą kontrolę, można użyć następujące opcjonalne ustawienia:

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

Te opcje umożliwiają uruchamianie poleceń w systemie Linux, przed i po kompilacji, a przed generowania narzędzia CMake. Te wartości mogą być dowolnego polecenia, który jest prawidłowy w systemie zdalnym. Dane wyjściowe w potoku do programu Visual Studio.



## <a name="see-also"></a>Zobacz także

[Praca z właściwościami projektu](../build/working-with-project-properties.md)<br/>
[Projekty CMake w programie Visual Studio](../build/cmake-projects-in-visual-studio.md)<br/>
[Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](connect-to-your-remote-linux-computer.md)<br/>
[Dostosuj ustawienia narzędzia CMake](../build/customize-cmake-settings.md)<br/>
[Konfigurowanie sesji debugowania narzędzia CMake](../build/configure-cmake-debugging-sessions.md)<br/>
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](deploy-run-and-debug-your-linux-project.md)<br/>
[Informacje o konfiguracji narzędzia CMake wstępnie zdefiniowane](../build/cmake-predefined-configuration-reference.md)<br/>
