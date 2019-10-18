---
title: Konfigurowanie sesji debugowania CMake w programie Visual Studio
ms.date: 03/21/2019
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 41f53c0c3ea46a8a1aa11215968aaee6c13c2dea
ms.sourcegitcommit: e33126222c418daf977533ea9e2819d99e0d7b8d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72534102"
---
# <a name="configure-cmake-debugging-sessions"></a>Konfigurowanie sesji debugowania narzędzia CMake

Wszystkie elementy wykonywalne CMake są wyświetlane na liście rozwijanej **elementu startowego** na pasku narzędzi **Ogólne** . Aby rozpocząć sesję debugowania, po prostu wybierz jeden z nich i uruchom debuger.

![Lista rozwijana elementu startowego CMake](media/cmake-startup-item-dropdown.png "Lista rozwijana elementu startowego CMake")

Możesz również uruchomić sesję debugowania z poziomu Eksplorator rozwiązań. Najpierw przejdź do **widoku CMAKE targets** w oknie **Eksplorator rozwiązań** .

![Przycisk Widok elementów docelowych CMake](media/cmake-targets-view.png  "Element menu Widok elementów docelowych CMake")

Następnie kliknij prawym przyciskiem myszy dowolny plik wykonywalny i wybierz polecenie **Debuguj** lub **Debuguj i Uruchom ustawienia**. **Debugowanie** automatycznie rozpocznie debugowanie wybranego elementu docelowego na podstawie aktywnej konfiguracji. **Ustawienia debugowania i uruchamiania** otwierają plik *Launch. vs. JSON* i dodaje nową konfigurację debugowania dla wybranego celu.

## <a name="customize-debugger-settings"></a>Dostosuj ustawienia debugera

Aby dostosować ustawienia debugera dla dowolnego pliku wykonywalnego CMake w projekcie, kliknij prawym przyciskiem myszy określony plik CMakeLists. txt i wybierz polecenie **Ustawienia debugowania i uruchamiania**. (Lub wybierz element docelowy w **widoku targets** w **Eksplorator rozwiązań**). Po wybraniu elementu docelowego CMake w podmenu zostanie utworzony plik o nazwie **Launch. vs. JSON** . Ten plik jest wstępnie wypełniony informacjami o wybranym miejscu docelowym CMake i umożliwia określenie dodatkowych parametrów, takich jak argumenty programu lub typ debugera. Aby odwołać się do dowolnego klucza w pliku **pliku cmakesettings. JSON** , należy poprzedzić go `cmake.` w elemencie **Launch. vs. JSON**. W poniższym przykładzie przedstawiono prosty plik **Launch. vs. JSON** , który ściąga wartość klucza `remoteCopySources` w pliku **pliku cmakesettings. JSON** dla aktualnie wybranej konfiguracji:

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

Po zapisaniu pliku **Launch. vs. JSON** wpis zostanie utworzony na liście rozwijanej **elementu startowego** z nową nazwą. Edytując plik **Launch. vs. JSON** , można utworzyć dowolną liczbę konfiguracji debugowania, tak jak w przypadku dowolnej liczby elementów docelowych CMAKE.

## <a name="support-for-cmakesettings-variables"></a>Obsługa zmiennych pliku cmakesettings

 Plik **Start. vs. JSON** obsługuje zmienne, które są zadeklarowane w **pliku cmakesettings. JSON** (patrz poniżej) i które mają zastosowanie do aktualnie wybranej konfiguracji. Ma również klucz o nazwie `currentDir`, który ustawia bieżący katalog uruchamiania aplikacji dla projektu lokalnego:

```json
{
  "type": "default",
  "project": "CMakeLists.txt",
  "projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

Po uruchomieniu aplikacji wartość `currentDir` jest coś podobnego do

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```

Klucz "cwd" ustawia bieżący katalog uruchamiania aplikacji dla projektu zdalnego. Wartością domyślną jest "$ {debugInfo. defaultWorkingDirectory}", której wynikiem jest 

```cmd
/var/tmp/src/bfc6f7f4-4f0f-8b35-80d7-9198fa973fb9/Linux-Debug
```

## <a name="see-also"></a>Zobacz także

[CMake projekty w programie Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)<br/>
[Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Dostosowywanie ustawień kompilacji narzędzia CMake](customize-cmake-settings.md)<br/>
[Konfigurowanie sesji debugowania narzędzia CMake](configure-cmake-debugging-sessions.md)<br/>
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake wstępnie zdefiniowanej konfiguracji](cmake-predefined-configuration-reference.md)<br/>
