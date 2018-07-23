---
title: Konfigurowanie projektu CMake systemu Linux w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/28/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 285c1fcd38ef20ea38fe03e2cbd27f77469775cf
ms.sourcegitcommit: 30192458404618039fdadddf37dc269baa559860
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39182541"
---
# <a name="configure-a-linux-cmake-project"></a>Konfigurowanie projektu CMake systemu Linux

**Visual Studio 2017 w wersji 15.4 lub nowszy**  
Po zainstalowaniu obciążenia języka Linux C++, obsługa CMake dla systemu Linux jest domyślnie zaznaczone. Teraz możesz pracować na istniejącej bazie kodu używającej narzędzia CMake bez konieczności konwertowania go do projektu programu Visual Studio. Jeśli baza kodu jest dla wielu platform, mogą kierować zarówno Windows, jak i Linux z poziomu programu Visual Studio.

W tym temacie założono, że masz podstawowe znajomość Obsługa CMake w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [narzędzia CMake w języku Visual C++](../ide/cmake-tools-for-visual-cpp.md). Aby uzyskać więcej informacji na temat narzędzia CMake, sama zobacz [kompilacji, testów i pakietów usługi oprogramowania za pomocą narzędzia CMake](https://cmake.org/).

> [!NOTE]  
> Obsługa CMake w programie Visual Studio wymaga obsługi trybu serwera, która została wprowadzona w CMake 3.8. Jeśli Menedżer pakietów zapewnia starszą wersję CMake, można obejść, jego [tworzenia CMake ze źródła](#build-a-supported-cmake release-from-source) lub pobierania go z oficjalną [strony pobierania narzędzia CMake](https://cmake.org/download/). Dla wariantu CMake dostarczonych przez firmę Microsoft, który obsługuje [widok elementów docelowych narzędzia CMake](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) okienko w programie Visual Studio, pobrać najnowsze wstępnie utworzone pliki binarne w [ https://github.com/Microsoft/CMake/releases ](https://github.com/Microsoft/CMake/releases).

## <a name="open-a-folder"></a>Otwieranie folderu

Aby rozpocząć, wybierz opcję **pliku** > **Otwórz** > **folderu** z menu głównego w przeciwnym razie wpisz `devenv.exe <foldername>` w wierszu polecenia. Folder, który można otworzyć powinny mieć plik CMakeLists.txt, wraz z kodem źródłowym.
Poniższy przykład pokazuje prosty plik CMakeLists.txt i plik .cpp:

```cpp
// Hello.cpp

#include <iostream>;

int main(int argc, char* argv[])
{
    std::cout << "Hello" << std::endl;
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

**Visual Studio 2017 w wersji 15.7 lub nowszej:**  
Aby zapewnić obsługę funkcji IntelliSense dla zdalnych nagłówków, Visual Studio automatycznie kopiuje je do katalogu na komputerze lokalnym Windows. Aby uzyskać więcej informacji, zobacz [technologii IntelliSense dla zdalnych nagłówków](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-project"></a>Debugowanie projektu

Podczas debugowania kodu w systemie zdalnym, ustaw punkt przerwania, wybierz element docelowy narzędzia CMake jako element startowy w menu narzędzi obok ustawienia projektu i wybierz  **&#x23f5; Start** na pasku narzędzi lub naciśnięciu klawisza F5.

Aby dostosować argumenty wiersza polecenia programu, kliknij prawym przyciskiem myszy plik wykonywalny w **Eksploratora rozwiązań** i wybierz **ustawienia debugowania i uruchamiania**. To spowoduje otwarcie lub tworzy plik konfiguracji pliku launch.vs.json, który zawiera informacje o programie. Aby określić dodatkowe argumenty, dodaj je w `args` tablicę JSON. Aby uzyskać więcej informacji, zobacz [projekty Otwórz Folder w programie Visual C++](https://docs.microsoft.com/en-us/cpp/ide/non-msbuild-projects).

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
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```

`name` Wartość może być wedle uznania. `remoteMachineName` Wartość określa którego zdalnego systemu docelowego, w przypadku, gdy masz więcej niż jeden. Technologia IntelliSense jest włączona dla tego pola, które ułatwią Ci wybrać odpowiednie system. Pole `remoteCMakeListsRoot` Określa, gdzie źródła projektu zostaną skopiowane do systemu zdalnego. Pole `remoteBuildRoot` jest, gdzie zostaną wygenerowane dane wyjściowe kompilacji w systemie zdalnym. Dane wyjściowe również lokalnie kopiowany do lokalizacji określonej przez `buildRoot`.

## <a name="build-a-supported-cmake-release-from-source"></a>Tworzenie obsługiwanych wersji CMake ze źródła

Minimalna wersja narzędzia CMake wymagane w sieci w systemie Linux maszyna jest 3.8 i również musi obsługiwać tryb serwera. Aby to sprawdzić, uruchom następujące polecenie:

```cmd
cmake --version
```

Aby sprawdzić, czy jest włączony tryb tego serwera, uruchom polecenie:

```cmd
cmake -E capabilities
```

W danych wyjściowych, poszukaj **"serverMode": true**. Należy pamiętać, że nawet podczas kompilacji CMake ze źródła zgodnie z opisem poniżej ma sprawdzać możliwości po zakończeniu. Systemu Linux mogą mieć ograniczenia, które uniemożliwiają włączane w trybie serwera.

Aby rozpocząć tworzenie CMake ze źródła w powłoce systemu Linux, upewnij się, Menedżera pakietów jest aktualny, i czy masz git i dostępne narzędzia cmake.

Najpierw sklonuj źródeł narzędzia CMake z [repozytorium Microsoft CMake](https://github.com/Microsoft/CMake) której firma Microsoft zachowuje rozwidlenia obsługę narzędzia CMake programu Visual Studio:

```cmd
sudo apt-get update
sudo apt-get install -y git cmake
git clone https://github.com/Microsoft/CMake.git
cd CMake
```

Następnie Aby skompilować i zainstaluj bieżącą wersję cmake do /usr/local/bin, uruchom następujące polecenia:

```cmd
mkdir out
cd out
cmake ../
make
sudo make install
```

Następnie uruchom następujące polecenie, aby sprawdzić, wersja jest > = 3.8 i ten serwer jest włączony tryb:

```cmd
/usr/local/bin/cmake –version
cmake -E capabilities
```

## <a name="see-also"></a>Zobacz też

[Praca z właściwościami projektu](../ide/working-with-project-properties.md)  
[Narzędzia CMake w języku Visual C++](../ide/cmake-tools-for-visual-cpp.md)  
