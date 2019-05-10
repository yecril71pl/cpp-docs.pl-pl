---
title: 'Instrukcje: Konfigurowanie programu Visual Studio C++ projekty do docelowego 64-bitowej, x64 platformy'
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: a063c2f333a755ab86a4f91c9d14d0c65a6d1414
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446395"
---
# <a name="how-to-configure-visual-studio-c-projects-to-target-64-bit-x64-platforms"></a>Instrukcje: Konfigurowanie programu Visual Studio C++ projekty do docelowego 64-bitowej, x64 platformy

Konfiguracje projektu w środowisku IDE programu Visual Studio służy do konfigurowania aplikacji w języku C++ pod kątem 64-bitowy, x64 platform. Możesz również migrować ustawień projektu Win32 w konfiguracji projektu 64-bitowych.

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>Aby skonfigurować na platformach 64-bitowej aplikacji w języku C++

1. Otwórz projekt C++, który chcesz skonfigurować.

1. Otwórz strony właściwości dla tego projektu. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](working-with-project-properties.md).

   > [!NOTE]
   > Upewnij się, że w przypadku projektów .NET **właściwości konfiguracji** węzła lub jeden z jego węzłów podrzędnych wybrano  **\<nazwa_projektu > strony właściwości** okno dialogowe; w przeciwnym razie  **Menedżer konfiguracji** przycisk jest niedostępna.

1. Wybierz **programu Configuration Manager** przycisk, aby otworzyć **programu Configuration Manager** okno dialogowe.

1. W **platforma rozwiązania aktywnego** listy rozwijanej wybierz  **\<nowy... >** opcję, aby otworzyć **nowa platforma rozwiązania** okno dialogowe.

1. W **wpisz lub wybierz nową platformę** listy rozwijanej, wybierz 64-bitowych, platformy docelowej.

   > [!NOTE]
   > W **nowa platforma rozwiązania** okno dialogowe, można użyć **Kopiuj ustawienia** opcję, aby skopiować istniejące ustawienia projektu do nowej konfiguracji projektu 64-bitowych.

1. Wybierz **OK** przycisku. Platformy, które wybrano w poprzednim kroku, który pojawia się w obszarze **platforma rozwiązania aktywnego** w **programu Configuration Manager** okno dialogowe.

1. Wybierz **Zamknij** znajdujący się w **programu Configuration Manager** okna dialogowego pole, a następnie wybierz **OK** znajdujący się w  **\<nazwa_projektu > Strony właściwości** okno dialogowe.

### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>Aby skopiować ustawienia projektu Win32 do konfiguracji projektu 64-bitowych

- Gdy **nowa platforma rozwiązania** jest otwarte okno dialogowe podczas konfigurowania projektu do elementu docelowego platformy 64-bitowej w **Kopiuj ustawienia** listy rozwijanej wybierz **Win32**. Te ustawienia projektu są automatycznie aktualizowane na poziomie projektu:

  - [/MACHINE](reference/machine-specify-target-platform.md) ustawiono opcję konsolidatora **/MACHINE:X 64**.

  - **Zarejestruj dane wyjściowe** jest wyłączone. Aby uzyskać więcej informacji, zobacz [strony właściwości konsolidatora](reference/linker-property-pages.md).

  - **Docelowe środowisko** ustawiono **/ENV x64**. Aby uzyskać więcej informacji, zobacz [strony właściwości MIDL: Ogólne](reference/midl-property-pages-general.md).

  - **Sprawdza poprawność parametrów** jest czyszczona i Zresetuj wartość domyślną. Aby uzyskać więcej informacji, zobacz [strony właściwości MIDL: Zaawansowane](reference/midl-property-pages-advanced.md).

  - Jeśli **formatu informacji debugowania** została ustawiona na **/zi** w konfiguracji projektu Win32, następnie ustawiana jest na **/zi** w konfiguracji projektu 64-bitowych. Aby uzyskać więcej informacji, zobacz [/z7, / zi, /ZI (Format informacji debugowania)](reference/z7-zi-zi-debug-information-format.md).

  > [!NOTE]
  > Żadna z tych właściwości projektu są zmieniane, jeśli zostaną one zastąpione na poziomie plików.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie projektów w języku C++ x64 64-bitowy, obiektów docelowych](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Debugowanie aplikacji 64-bitowych](/visualstudio/debugger/debug-64-bit-applications)
