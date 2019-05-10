---
title: Konfigurowanie projektu CMake systemu Linux w programie Visual Studio
description: Jak konfigurować, edytowanie i kompilowanie projektu CMake systemu Linux w programie Visual Studio
ms.date: 05/03/2019
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: a619625bff2cd84db63d58cdceb4d2df98613d2a
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222275"
---
# <a name="configure-a-linux-cmake-project"></a>Konfigurowanie projektu CMake systemu Linux

Po otwarciu folderu zawierającego projektu narzędzia CMake, Visual Studio używa metadanych, które CMake generuje do skonfigurowania funkcji IntelliSense i automatyczne kompilacje. Lokalnej konfiguracji i ustawieniami debugowania są przechowywane w plikach w formacie JSON, które można opcjonalnie można udostępniać innym użytkownikom, którzy korzystają z programu Visual Studio. 

Programu Visual Studio nie zmodyfikować pliki pliku CMakeLists.txt lub oryginalnego pamięć podręczną CMake, tak aby inne nad tym samym projekcie można nadal korzystać z dowolnych narzędzi jest już używany.

Aby uzyskać ogólne informacje o pomocy CMake w programie Visual Studio, zobacz [narzędzia CMake dla programu Visual Studio](../build/cmake-projects-in-visual-studio.md). Przeczytaj, że przed kontynuowaniem tutaj.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Najpierw upewnij się, że masz **programowanie dla systemu Linux przy użyciu języka C++** obciążenia zainstalowany, w tym składnik narzędzia CMake. Zobacz [Zainstaluj obciążenie systemu Linux w języku C++ w programie Visual Studio](download-install-and-setup-the-linux-development-workload.md). 

Na komputerze z systemem Linux upewnij się, że instalowane są następujące elementy: 

- gcc
- gdb
- polecenia rsync
- ZIP 

::: moniker range="vs-2019"

Pomoc techniczna Linux support w przypadku projektów CMake wymaga najnowszej wersji narzędzia CMake w celu zainstalowania na komputerze docelowym. Często wersji oferowanych przez Menedżera pakietów domyślne dystrybucji nie jest wystarczająco długi, do obsługi wszystkich IDE. Visual Studio 2019 r można automatycznie zainstalować lokalną kopię programu CMake użytkownika na komputerach zdalnych systemu Linux, które nie mają najnowszą wersję narzędzia CMake zainstalowane. Jeśli zgodnej wersji CMake nie zostanie wykryte po raz pierwszy Skompiluj projekt, zostanie wyświetlony-paska informacyjnego oferty do zainstalowania narzędzia CMake.

Pliki binarne zostanie zainstalowana tak, aby `~/.vs/cmake`. Po wdrożeniu plików binarnych, projekt zostanie automatycznie ponownie wygenerować. Należy pamiętać, że jeśli narzędzia CMake, określony przez `cmakeExecutable` pole `CMakeSettings.json` jest nieprawidłowy (nie istnieje lub ma nieobsługiwaną wersję) i istnieją wstępnie utworzone pliki binarne programu Visual Studio będzie ignorować `cmakeExecutable` i korzystać ze wstępnie utworzonych plików binarnych.

::: moniker-end

::: moniker range="vs-2017"

Obsługa CMake w programie Visual Studio wymaga obsługi trybu serwera, która została wprowadzona w CMake 3.8. Dla wariantu CMake dostarczonych przez firmę Microsoft, Pobierz najnowszy wstępnie utworzone pliki binarne w [ https://github.com/Microsoft/CMake/releases ](https://github.com/Microsoft/CMake/releases).

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
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Wybierz element docelowy z systemem Linux

Zaraz po otwarciu folderu, programu Visual Studio analizuje plik CMakeLists.txt i określa obiekt docelowy Windows **debugowania x86**. Aby wskazać system Linux, należy zmienić ustawienia projektu do **debugowania dla systemu Linux** lub **wydania Linux**.

Domyślnie program Visual Studio wybiera pierwszy system zdalny na liście w obszarze **narzędzia** > **opcje** > **Międzyplatformowe**  >  **Menedżera połączeń**. Nie zostaną znalezione nie połączeń zdalnych, monit o jego utworzenie. Aby uzyskać więcej informacji, zobacz [nawiązywanie połączenia zdalnego komputer z systemem Linux](connect-to-your-remote-linux-computer.md).

Po określeniu docelowej systemu Linux, źródło jest kopiowany do maszyną z systemem Linux. Następnie CMake jest uruchamiane na maszynie systemu Linux w celu wygenerowania pamięci podręcznej narzędzia CMake dla Twojego projektu.

![Generuj pamięć podręczną CMake w systemie Linux](media/cmake-linux-1.png "wygenerowania pamięci podręcznej narzędzia CMake w systemie Linux")

Aby zapewnić obsługę funkcji IntelliSense dla zdalnych nagłówków, Visual Studio automatycznie kopiuje je z maszyny z systemem Linux do katalogu na komputerze lokalnym Windows. Aby uzyskać więcej informacji, zobacz [technologii IntelliSense dla zdalnych nagłówków](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-project"></a>Debugowanie projektu

Podczas debugowania kodu w systemie zdalnym, ustaw punkt przerwania, wybierz element docelowy narzędzia CMake jako element startowy w menu narzędzi obok ustawienia projektu i wybierz  **&#x23f5; Start** na pasku narzędzi lub naciśnięciu klawisza F5.

Aby dostosować argumenty wiersza polecenia programu, kliknij prawym przyciskiem myszy plik wykonywalny w **Eksploratora rozwiązań** i wybierz **ustawienia debugowania i uruchamiania**. To spowoduje otwarcie lub tworzy plik konfiguracji pliku launch.vs.json, który zawiera informacje o programie. Aby określić dodatkowe argumenty, dodaj je w `args` tablicę JSON. Aby uzyskać więcej informacji, zobacz [Otwórz Folder projektów w języku C++](../build/open-folder-projects-cpp.md) i [konfigurowania CMake sesjami debugowania](../build/configure-cmake-debugging-sessions.md).

## <a name="configure-cmake-settings-for-linux"></a>Konfiguruj ustawienia narzędzia CMake dla systemu Linux

Określić wszystkie właściwości, które są wymienione w pliku CMakeSettings.json w projektu CMake systemu Linux [CMake dostosować ustawienia](../build/customize-cmake-settings.md), oraz dodatkowe właściwości, które kontrolują ustawienia kompilacji na zdalnym komputerze z systemem Linux. 

::: moniker range="vs-2019"

Aby zmienić domyślne ustawienia narzędzia CMake w programie Visual Studio 2019 r, z głównym pasku narzędzi, otwórz **konfiguracji** listy rozwijanej i wybierz polecenie **Zarządzanie konfiguracjami**. 

   ![Konfiguracje zarządzania CMake](../build/media/vs2019-cmake-manage-configurations.png "konfiguracji narzędzia CMake listy rozwijanej")

Spowoduje to przejście **edytora ustawienia narzędzia CMake** używane do edycji `CMakeSettings.json` pliku w folderze głównym projektu. Można również otworzyć plik bezpośrednio, klikając **Edycja JSON** przycisku w edytorze. Aby uzyskać więcej informacji, zobacz [dostosować ustawienia narzędzia CMake](../build/customize-cmake-settings.md).

::: moniker-end

::: moniker range="vs-2017"

Aby zmienić domyślne ustawienia narzędzia CMake w programie Visual Studio 2017, wybierz **CMake | Zmień ustawienia narzędzia CMake | CMakeLists.txt** z menu głównego, lub kliknij prawym przyciskiem myszy CMakeSettings.txt w **Eksploratora rozwiązań** i wybierz polecenie **Zmień ustawienia narzędzia CMake**. Program Visual Studio utworzy nowy `CMakeSettings.json` pliku w folderze głównym projektu. Możesz otworzyć plik, używając **ustawienia narzędzia CMake** edytora lub bezpośrednio zmodyfikować plik. Aby uzyskać więcej informacji, zobacz [CMake dostosować ustawienia](../build/customize-cmake-settings.md).

::: moniker-end

Poniższy przykład pokazuje, w domyślnej konfiguracji debugowania dla systemu Linux na podstawie w poprzednim przykładzie kodu:

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
Poniższa tabela zawiera podsumowanie ustawień:

|Ustawienie|Opis|
|-----------|-----------------|
|`name`|Ta wartość może być wedle uznania.|
|`remoteMachineName`|Określa którego zdalnego systemu docelowego, w przypadku, gdy masz więcej niż jeden. Technologia IntelliSense jest włączona dla tego pola, które ułatwią Ci wybrać odpowiednie system.|
|`remoteCMakeListsRoot`|Określa, gdzie źródła projektu zostaną skopiowane do systemu zdalnego.|
|`remoteBuildRoot`|Określa, gdzie zostaną wygenerowane dane wyjściowe kompilacji w systemie zdalnym. Dane wyjściowe również lokalnie kopiowany do lokalizacji określonej przez `buildRoot`.|
|`remoteInstallRoot` i `installRoot`| Podobnie jak `remoteBuildRoot` i `buildRoot`, z wyjątkiem odnoszą się w trakcie instalacji narzędzia CMake.|
|`remoteCopySources`|Określa, czy źródłach lokalnych są kopiowane do maszyny zdalnej. Możesz ustawić to wartość false, jeśli masz wiele plików, a już synchronizowania źródeł samodzielnie.|
|`remoteCopyOutputVerbosity`| Określa poziom szczegółowości krok kopiowania, w przypadku, gdy musisz zdiagnozować błędy.|
|`remoteCopySourcesConcurrentCopies`| Określa, jak wiele procesów jest zduplikowany kopiowanie.|
|`remoteCopySourcesMethod`| Może być `rsync` lub `sftp`.|
|`remoteCopySourcesExclusionList`| Określa pliki, które mają być kopiowane do maszyny zdalnej.|
|`rsyncCommandArgs`|Określa metodę kopiowania rsync.|
|`remoteCopyBuildOutput`| Określa, czy dane wyjściowe kompilacji zdalnej jest kopiowany do folderu kompilacji lokalnej.|

Aby uzyskać większą kontrolę, można użyć tych opcjonalnych ustawień:

```json
{
      "remotePreBuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostBuildCommand": "",
}
```

Te opcje umożliwiają uruchamianie poleceń w systemie zdalnym, przed i po kompilacji, a przed generowania narzędzia CMake. Te wartości mogą być dowolnego polecenia, który jest prawidłowy w systemie zdalnym. Dane wyjściowe w potoku do programu Visual Studio.

::: moniker range="vs-2019"

W programie Visual Studio 2019 r można edytować tych ustawień w **edytora ustawienia narzędzia CMake**.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Praca z właściwościami projektu](../build/working-with-project-properties.md)<br/>
[Projekty CMake w programie Visual Studio](../build/cmake-projects-in-visual-studio.md)<br/>
[Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](connect-to-your-remote-linux-computer.md)<br/>
[Dostosuj ustawienia narzędzia CMake](../build/customize-cmake-settings.md)<br/>
[Konfigurowanie sesji debugowania narzędzia CMake](../build/configure-cmake-debugging-sessions.md)<br/>
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](deploy-run-and-debug-your-linux-project.md)<br/>
[Informacje o konfiguracji narzędzia CMake wstępnie zdefiniowane](../build/cmake-predefined-configuration-reference.md)<br/>
