---
title: "Wdrażanie, uruchamiania i debugowania projektu systemu Linux | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 237b6f3dbca8d529362a545f67ee0db4f9770d8d
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Wdrażanie, uruchamiania i debugowania projektu systemu Linux

Po utworzeniu projektu systemu Linux i połączeniu się projekt za pomocą [Menedżera połączeń systemu Linux](../linux/connect-to-your-remote-linux-computer.md), można uruchomić i debugowania projektu. Kompilacja, wykonywanie i debugowania kodu w celu zdalnego.

Istnieje kilka sposobów interakcyjnie i debugowania projektu systemu Linux.

* Debugowanie przy użyciu tradycyjnych funkcje programu Visual Studio, takich jak punkty przerwania, okien wyrażeń kontrolnych i aktywowaniu zmiennej. Za pomocą tych metod, może debugować w zwykły sposób dla innych typów projektów.
* Wyświetl dane wyjściowe z komputera docelowego w specjalnym oknie konsoli systemu Linux. Umożliwia także konsolę do wysyłania wejściowych do komputera docelowego.

## <a name="debug-your-linux-project"></a>Debugowanie projektu systemu Linux

1. Wybierz tryb debugowania w **debugowanie** strony właściwości.

    GDB jest używana do debugowania aplikacji uruchomionych w systemie Linux.  Jednak to można uruchamiać w dwóch różnych trybach, które można wybierać z **tryb debugowania** opcja w projekcie **debugowanie** strony właściwości:

    ![Opcje GDB](media/settings_debugger.png)

    - W **gdbserver** trybie GDB uruchamiane lokalnie która połączy się gdbserver uruchomiona w systemie zdalnym.  Należy pamiętać, że jest to jedyny tryb obsługującej okna konsoli systemu Linux.

    - W **gdb** trybie debuger programu Visual Studio dyski GDB w systemie zdalnym, co jest bardziej zgodne, jeśli lokalna wersja GDB nie jest zgodny z wersją zainstalowaną na komputerze docelowym. |

    > [!NOTE] 
    > Jeśli nie osiągnęła punktów przerwania w trybie debugowania gdbserver, spróbuj gdb tryb. Najpierw należy gdb [zainstalowane](../linux/download-install-and-setup-the-linux-development-workload.md) w celu zdalnego.

2. Wybierz docelową zdalnego przy użyciu standardu **debugowania** paska narzędzi w programie Visual Studio.

    Podczas zdalnego element docelowy jest dostępny, pojawi się liście według nazwy lub adresu IP.

    ![Docelowy zdalnego](media/remote_target.png)

    Jeśli nie ma jeszcze połączenia zdalnego obiektu docelowego, zobaczysz instrukcji, aby użyć [Menedżera połączeń systemu Linux](../linux/connect-to-your-remote-linux-computer.md) można się połączyć z docelowym zdalnego.

    ![Architektura zdalnego](media/architecture.png)

3. Zestaw znać punkt przerwania, klikając w lewym odstępu dla kodu, które będą wykonywane.

    Czerwonej kropki jest wyświetlany w wierszu kodu punktu przerwania.

4. Naciśnij klawisz **F5** (lub **Debuguj > Rozpocznij debugowanie**) można rozpocząć debugowania.

    Po rozpoczęciu debugowania, zanim zostanie ona uruchomiona aplikacja została skompilowana w celu zdalnego. Błędy kompilacji będą widoczne w **listy błędów** okna.

    Jeśli nie ma żadnych błędów, aplikacja zostanie uruchomiona i zatrzyma debugera na punkt przerwania.

    ![Trafiony punkt przerwania](media/hit_breakpoint.png)  

    Teraz możesz pracować z aplikacją w jest bieżący stan, wyświetlanie zmiennych i kroków kodu przez naciskanie klawiszy polecenia, takich jak **F10** lub **F11**.

4. Jeśli chcesz użyć konsoli systemu Linux do interakcji z aplikacji, wybierz **Debuguj > konsoli Linux**.

  ![Menu konsoli systemu Linux](media/consolemenu.png)

  Ta konsola zostanie wyświetlane wszystkie dane wyjściowe konsoli z komputera docelowego, a także pobrać dane wejściowe i wysłać je do komputera docelowego.

  ![Okno konsoli systemu Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options"></a>Skonfigurować inne opcje debugowania

* Argumenty wiersza polecenia mogą być przekazywane do pliku wykonywalnego przy użyciu **argumenty programu** elementu do projektu **debugowanie** strony właściwości.
  
  ![Argumenty programu](media/settings_programarguments.png)

* Opcje debugera określonych mogą zostać przekazane do GDB przy użyciu **dodatkowych poleceń debugera** wpisu.  Na przykład można zignorować sigill — sygnały (niedozwolona instrukcja).  Można użyć **obsługi** polecenie, aby to osiągnąć.  dodając następujące polecenie, aby **dodatkowych poleceń debugera** wpisu, jak pokazano powyżej:

  ```handle SIGILL nostop noprint```

## <a name="see-also"></a>Zobacz także
[C++, debugowanie właściwości (Linux C++)](../linux/prop-pages/debugging-linux.md).
