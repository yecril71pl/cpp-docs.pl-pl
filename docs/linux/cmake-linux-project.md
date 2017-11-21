---
title: Konfigurowanie projektu CMake systemu Linux w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 10/25/2107
ms.reviewer: 
ms.suite: 
ms.technology: cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4e3baa9b6e362f93e7b2cda59d34cabf87324292
ms.sourcegitcommit: 1b480aa74886930b3bd0435d71cfcc3ccda36424
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="configure-a-linux-cmake-project"></a>Konfigurowanie projektu CMake systemu Linux
  
**Visual Studio 2017 wersji 15.4** po zainstalowaniu obciążenia Linux C++ CMake obsługę systemu Linux jest domyślnie zaznaczona. Teraz możesz pracować na istniejący kod podstawowy używającej CMake bez konieczności przekonwertować go do projektu programu Visual Studio. Jeśli kodzie między platformami, można kierować systemów Windows i Linux z poziomu programu Visual Studio. 

W tym temacie założono, że masz podstawowa znajomość CMake pomocy technicznej w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [CMake Tools dla Visual C++](../ide/cmake-tools-for-visual-cpp.md). Aby uzyskać więcej informacji na temat CMake się w temacie [kompilacji testowych i pakietu Your oprogramowania z CMake](https://cmake.org/).

> [!NOTE] 
> Obsługa CMake w programie Visual Studio wymaga obsługi trybu serwera, który został wprowadzony w CMake 3.8. Jeśli Menedżera pakietów udostępnia starszej wersji CMake, możesz można obejść, tworząc 3.8 CMake ze źródła.



## <a name="open-a-folder"></a>Otwórz folder
Aby rozpocząć, wybierz opcję **pliku | Otwórz | Folder** z menu głównego, albo też typu `devenv.exe <foldername>` w wierszu polecenia. Folder, który można otworzyć powinny mieć pliku CMakeLists.txt, wraz z kodu źródłowego.
W poniższym przykładzie przedstawiono prosty plik CMakeLists.txt i plik .cpp:

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

## <a name="choose-a-linux-target"></a>Wybierz element docelowy systemu Linux
Zaraz po otwarciu folderu programu Visual Studio analizuje plik CMakeLists.txt i Określa docelowy Windows x86 debugowania. Pod kątem systemu Linux, Zmień ustawienia projektu debugowania systemu Linux lub wersji systemu Linux.

Domyślnie program Visual Studio wybiera pierwszy system zdalny na liście (w obszarze **narzędzia | Opcje | Różne platformy | Menedżer połączeń**). Nie zostaną znalezione nie połączenia zdalne, monit o jego utworzenie.

Po określeniu docelowego Linux źródła jest kopiowana do maszyny z systemem Linux. Następnie CMake jest uruchamiane na komputerze systemu Linux można wygenerować pamięci podręcznej CMake dla projektu.  

![Generowanie pamięci podręcznej CMake w systemie Linux](media/cmake-linux-1.png "Generowanie CMake pamięci podręcznej w systemie Linux")  

## <a name="debug-the-project"></a>Debugowanie projektu  
Do debugowania kodu w systemie zdalnym, ustaw punkt przerwania, wybierz docelowy CMake jako element startowy z menu paska narzędzi obok ustawienia projektu, i kliknij przycisk Uruchom (lub naciśnij klawisz F5).

## <a name="configure-cmake-settings-for-linux"></a>Skonfiguruj ustawienia CMake dla systemu Linux
Aby zmienić domyślne ustawienia CMake, wybierz **CMake | Zmień ustawienia CMake | CMakeLists.txt** z menu głównego, lub kliknij prawym przyciskiem myszy CMakeSettings.txt w **Eksploratora rozwiązań** i wybierz polecenie **Zmień ustawienia CMake**. Visual Studio utworzy nowy plik w folderze o nazwie `CMakeSettings.json` który jest wypełniana konfiguracje domyślne, które są wyświetlane w elemencie menu ustawień projektu. W poniższym przykładzie przedstawiono konfigurację domyślną dla systemu Linux debugowania oparta na poprzednim przykładzie kodu:

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
`name` Wartość może być dowolne. `remoteMachineName` Wartość określa, które system zdalny do obiektu docelowego w przypadku, gdy masz więcej niż jeden. IntelliSense jest włączona dla tego pola ułatwiające wybranie prawo systemu. Pole `remoteCMakeListsRoot` Określa, gdzie źródła projektu zostaną skopiowane do systemu zdalnego. Pole `remoteBuildRoot` jest, gdzie zostaną wygenerowane dane wyjściowe kompilacji w systemie zdalnym. Dane wyjściowe także lokalnie kopiowany do lokalizacji określonej przez `buildRoot`.

## <a name="building-a-supported-cmake-release-from-source"></a>Tworzenie obsługiwanych wersji CMake ze źródła
Minimalna wersja CMake wymagane w sieci w systemie Linux maszyna jest 3.8 i muszą również obsługiwać tryb serwera. Aby sprawdzić to uruchamiania tego polecenia:

```cmd
cmake --version
```

Aby sprawdzić, czy jest włączony tryb tego serwera, uruchom polecenie:

```cmd
cmake -E capabilities
```

W danych wyjściowych, wyszukaj "serverMode": wartość true. Należy pamiętać, że nawet jeśli kompilacja CMake ze źródła opisanych poniżej możesz należy sprawdzić możliwości po zakończeniu. Linux system może mieć ograniczenia, które uniemożliwiają jest włączony tryb serwera.

Aby rozpocząć korzystanie budynku ze źródła w powłoce programu Linux systemu upewnij się, że Menedżera pakietów jest aktualny, i czy masz git i cmake dostępne. Najpierw sklonuj CMake źródeł:

```cmd
sudo apt-get update
sudo apt-get install -y git cmake
git clone https://github.com/Kitware/CMake.git
cd CMake
```

Następnie upewnij się, że jesteś na obsługiwanych wersji CMake dla programu Visual Studio. Aktywnie Śledzimy programowanie CMake, ale nie możemy zagwarantować, że firma Microsoft obsługuje r. Aby utworzyć CMake 3.9.0 (na przykład), najpierw uruchom:

```cmd
git checkout tags/v3.9.0
```

Następnie uruchom następujące polecenia:

```cmd
mkdir out
cd out
cmake ../
make
sudo make install
```

Powyższych poleceń kompilacji i instalowania bieżącej wersji CMake do /usr/local/bin. Uruchom to polecenie, aby sprawdzić wersji > = 3.8 i że serwer jest włączony tryb:

```cmd
/usr/local/bin/cmake –version
cmake -E capabilities
```

## <a name="see-also"></a>Zobacz też
[Praca z właściwościami projektu](../ide/working-with-project-properties.md)  
[Narzędzia CMake w języku Visual C++](../ide/cmake-tools-for-visual-cpp.md)