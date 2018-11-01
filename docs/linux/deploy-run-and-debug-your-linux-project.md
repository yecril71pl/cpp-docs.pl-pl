---
title: Wdrażanie, uruchamianie i debugowanie projektu systemu Linux w języku C++ w programie Visual Studio
description: Opisuje sposób kompilowania, wykonywania i debugowania kodu zdalnego docelową z wewnątrz projektu języka Linux C++ w programie Visual Studio.
ms.date: 09/12/2018
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: 685299f777f12abbd5534f58b13b3ba16d1cbe70
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501520"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Wdrażanie, uruchamianie i debugowanie projektu systemu Linux

Po utworzeniu projektu języka Linux C++ w programie Visual Studio i łączysz się przy użyciu projektu [Menedżera połączeń systemu Linux](../linux/connect-to-your-remote-linux-computer.md), można uruchamiać i debugować projektu. Skompilować, wykonywanie i możliwe jest debugowanie kodu w zdalnym elemencie docelowym.

Istnieje kilka sposobów interakcji z i debugowanie projektu systemu Linux.

* Debugowanie przy użyciu tradycyjnych funkcje programu Visual Studio, takich jak punkty przerwania, okna czujki i przenosząc kursor myszy nad zmienną. Przy użyciu tych metod, może debugować tak jak zwykle dla innych typów projektów.
* Widok danych wyjściowych z komputera docelowego w specjalnym oknie Konsola systemu Linux. Umożliwia także konsolę do wysyłania danych wejściowych do komputera docelowego.

## <a name="debug-your-linux-project"></a>Debugowanie projektu systemu Linux

1. Wybierz tryb debugowania w **debugowanie** stronę właściwości.

    GDB jest używana do debugowania aplikacji działającej w systemie Linux.  Jednak to można uruchomić w dwóch różnych trybach, które można wybierać z **tryb debugowania** opcja w projekcie **debugowanie** strona właściwości:

    ![Opcje GDB](media/settings_debugger.png)

    - W **serwera gdbserver** trybie GDB jest uruchamiany lokalnie, w którym do serwera gdbserver uruchomiony w systemie zdalnym.  Należy pamiętać, że jest to tylko trybu, który obsługuje okno konsoli systemu Linux.

    - W **gdb** dyski debugera programu Visual Studio trybie GDB w systemie zdalnym, co jest bardziej zgodne, jeśli lokalna wersja GDB nie jest zgodny z wersją zainstalowaną na komputerze docelowym. |

    > [!NOTE]
    > Jeśli nie można identyfikować punkty przerwania w trybie debugowania gdbserver następuje lokalne, spróbuj trybie gdb. Najpierw należy gdb [zainstalowane](../linux/download-install-and-setup-the-linux-development-workload.md) w zdalnym elemencie docelowym.

2. Wybierz docelową zdalnego przy użyciu standardu **debugowania** narzędzi w programie Visual Studio.

    Jeśli zdalny element docelowy jest dostępny, zobaczysz go na liście według nazwy lub adresu IP.

    ![Docelowy zdalnego](media/remote_target.png)

    Jeśli nie masz jeszcze połączenia zdalnego obiektu docelowego, pojawią się instrukcjami, aby użyć [Menedżera połączeń systemu Linux](../linux/connect-to-your-remote-linux-computer.md) nawiązać połączenia z docelowym zdalnego.

    ![Architektura zdalnego](media/architecture.png)

3. Ustaw punkt przerwania, klikając na lewym marginesie jakiś kod, który znasz będą wykonywane.

    Czerwona kropka jest wyświetlany na wiersz kodu, gdzie ustawić punkt przerwania.

4. Naciśnij klawisz **F5** (lub **Debuguj > Rozpocznij debugowanie**) można rozpocząć debugowania.

    Podczas uruchamiania debugowania, kompilowania aplikacji w zdalnym elemencie docelowym przed uruchomieniem jej. Błędy kompilacji będą wyświetlane w **lista błędów** okna.

    Jeśli nie ma żadnych błędów, aplikacja zostanie uruchomiona i debuger zostanie wstrzymany w punkcie przerwania.

    ![Trafiony punkt przerwania](media/hit_breakpoint.png)

    Teraz możesz wchodzić w interakcje z aplikacją w jest bieżący stan, wyświetlanie zmiennych i Przechodź przez kod, naciskając klawisze poleceń takich jak **F10** lub **F11**.

4. Jeśli chcesz korzystać z konsoli systemu Linux do interakcji z aplikacją, wybierz opcję **Debuguj > Konsola systemu Linux**.

  ![Menu konsoli systemu Linux](media/consolemenu.png)

  Ta konsola będą wyświetlane wszystkie dane wyjściowe konsoli z komputera docelowego, a także pobierać dane wejściowe i wysłać go do komputera docelowego.

  ![Okno konsoli systemu Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options"></a>Skonfiguruj inne opcje debugowania

* Argumenty wiersza polecenia mogą być przekazywane do pliku wykonywalnego przy użyciu **argumenty programu** element w projekcie ma **debugowanie** stronę właściwości.

  ![Argumenty programu](media/settings_programarguments.png)

* Opcje debugera określonej mogą być przekazywane do GDB przy użyciu **dodatkowe polecenia debugera** wpisu.  Na przykład można zignorować SIGILL (niedozwolona instrukcja) sygnałów.  Można użyć **obsługi** polecenie, aby to osiągnąć.  dodając następujące polecenie, aby **dodatkowe polecenia debugera** wpisu, jak pokazano powyżej:

  ```handle SIGILL nostop noprint```

## <a name="next-steps"></a>Następne kroki

* Aby debugować urządzeń ARM w systemie Linux, zobacz ten wpis w blogu: [debugowania urządzenia osadzonego ARM w programie Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/).

* Aby debugować za pomocą **dołączyć do procesu** polecenia, zobacz ten wpis w blogu: [ulepszenia obciążeniu C++ dla systemu Linux w systemie projektu, w oknie konsoli systemu Linux, polecenia rsync i Dołącz do procesu](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).

## <a name="see-also"></a>Zobacz także
[C++, debugowanie — właściwości (Linux C++)](../linux/prop-pages/debugging-linux.md).
