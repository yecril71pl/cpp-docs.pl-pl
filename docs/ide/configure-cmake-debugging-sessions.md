---
title: Konfigurowanie narzędzia CMake debugowania sesji w programie Visual Studio
ms.date: 03/05/2019
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 92aab4a9d8ea33fa2bc1abfb11938cbf7d4236f1
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/07/2019
ms.locfileid: "57566889"
---
# <a name="configure-cmake-debugging-sessions"></a>Konfigurowanie narzędzia CMake sesjami debugowania

Wszystkie elementy docelowe z pliku wykonywalnego narzędzia CMake są wyświetlane w **element startowy** liście rozwijanej **ogólne** paska narzędzi. Aby rozpocząć sesję debugowania, po prostu zaznacz jedną i uruchomić debugera.

![Narzędzie CMake uruchamiania elementu z listy rozwijanej](media/cmake-startup-item-dropdown.png "CMake uruchamiania elementu z listy rozwijanej")

Można również uruchomić sesję debugowania z menu Narzędzia CMake.

## <a name="customize-debugger-settings"></a>Dostosowywanie ustawień debugera

Aby dostosować ustawienia debugera dla dowolnego pliku wykonywalnego docelowych narzędzia CMake w projekcie, kliknij prawym przyciskiem myszy w określonym pliku CMakeLists.txt, a następnie wybierz **ustawienia debugowania i uruchamiania**. Po wybraniu docelowych narzędzia CMake w podmenu plik o nazwie `launch.vs.json` zostanie utworzony. Ten plik jest wstępnie wypełniane przy użyciu informacji o docelowej narzędzia CMake, wybrana przez Ciebie i pozwala określić dodatkowe parametry, takie jak argumenty programu lub typ debugera. Aby odwołać się dowolnym kluczu w `CMakeSettings.json` plików, należy poprzedzić go `cmake.` w `launch.vs.json`. W poniższym przykładzie przedstawiono prosty `launch.vs.json` pliku, który pobiera wartość `remoteCopySources` w `CMakeSettings.json` pliku dla aktualnie wybranej konfiguracji:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

Zaraz po zapisaniu `launch.vs.json` plik, zostanie utworzony wpis w **element startowy** lista rozwijana z nową nazwą. Edytując `launch.vs.json` pliku, można utworzyć dla dowolnej liczby elementów docelowych narzędzia CMake, takich jak wiele konfiguracji debugowania.

## <a name="support-for-cmakesettings-variables"></a>Obsługa zmiennych pliku cmakesettings na pozycji

 `Launch.vs.json` obsługuje zmienne, które są zadeklarowane w `CMakeSettings.json` (patrz poniżej) i które mają zastosowanie do konfiguracji aktualnie wybrany. Także ma klucz o nazwie `currentDir`, który ustawia bieżący katalog uruchamiania aplikacji:

```json
{
  "type": "default",
  "project": "CMakeLists.txt",
  "projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

Po uruchomieniu aplikacji, a wartość `currentDir` jest podobny do

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```
## <a name="see-also"></a>Zobacz także

[Narzędzia CMake w języku Visual C++](../ide/cmake-tools-for-visual-cpp.md)<br/>
[Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)<br/>
[Podłącz do komputera zdalnego systemu Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Dostosowywanie ustawień kompilacji CMake](customize-cmake-settings.md)<br/>
[Konfigurowanie narzędzia CMake sesjami debugowania](configure-cmake-debugging-sessions.md)<br/>
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Informacje o konfiguracji narzędzia CMake wstępnie zdefiniowane](cmake-predefined-configuration-reference.md)<br/>