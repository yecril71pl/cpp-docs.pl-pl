---
title: 'Porady: Konfigurowanie projektów Visual C++ pod kątem 64-bitowy, x64 platformy | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f1a4c9a27d4fdbbd57348c1fc2ce27301a1a95e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-configure-visual-c-projects-to-target-64-bit-x64-platforms"></a>Porady: Konfigurowanie projektów Visual C++ pod kątem 64-bitowy, x64 platformy

Konfiguracje projektu w programie Visual Studio IDE służy do konfigurowania aplikacji C++ pod kątem 64-bitowy, x64 platform. Można również migrację ustawień projektu Win32 w konfiguracji projektu 64-bitowych.  
  
### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>Aby skonfigurować aplikacje w języku C++ do 64-bitowych platform docelowych  
  
1.  Otwórz projekt C++, który chcesz skonfigurować.  
  
2.  Otwieranie stron właściwości dla tego projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
    > [!NOTE]
    >  Upewnij się, że dla projektów .NET **właściwości konfiguracji** wybrano węzeł lub jednego z jego węzłów podrzędnych w  **\<Projectname > strony właściwości** okno dialogowe; w przeciwnym razie  **Menedżer konfiguracji** przycisku jest niedostępna.  
  
3.  Wybierz **programu Configuration Manager** przycisk, aby otworzyć **programu Configuration Manager** okno dialogowe.  
  
4.  W **aktywnej platformy rozwiązania** listy rozwijanej wybierz  **\<nowy... >** opcję, aby otworzyć **nowa platforma rozwiązania** okno dialogowe.  
  
5.  W **wpisz lub wybierz Nowa platforma** listy rozwijanej, wybierz 64-bitowego platformy docelowej.  
  
    > [!NOTE]
    >  W **nowa platforma rozwiązania** okno dialogowe, można użyć **Kopiuj ustawienia** opcję, aby skopiować istniejące ustawienia projektu do nowej konfiguracji projektu 64-bitowych.  
  
6.  Wybierz **OK** przycisku. Platforma, która w poprzednim kroku wybrano jest wyświetlany w obszarze **aktywnej platformy rozwiązania** w **programu Configuration Manager** okno dialogowe.  
  
7.  Wybierz **Zamknij** przycisk **programu Configuration Manager** okna dialogowego polu, a następnie wybierz pozycję **OK** przycisk  **\<Projectname > Strony właściwości** okno dialogowe.  
  
### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>Aby skopiować ustawienia projektu Win32 w konfiguracji projektu 64-bitowych  
  
-   Gdy **nowa platforma rozwiązania** jest otwarte okno dialogowe podczas konfigurowania projektu do docelowej platformy 64-bitowej w **Kopiuj ustawienia** listy rozwijanej wybierz **Win32**. Te ustawienia projektu są automatycznie aktualizowane na poziomie projektu:  
  
    -   [/Maszyny](../build/reference/machine-specify-target-platform.md) — opcja konsolidatora ma ustawioną wartość **/MACHINE:X 64**.  
  
    -   **Zarejestruj dane wyjściowe** jest wyłączone. Aby uzyskać więcej informacji, zobacz [strony właściwości konsolidatora](../ide/linker-property-pages.md).  
  
    -   **Docelowe środowisko** ustawiono **/ENV x64**. Aby uzyskać więcej informacji, zobacz [strony właściwości MIDL: Ogólne](../ide/midl-property-pages-general.md).  
  
    -   **Sprawdź poprawność parametrów** jest wyczyszczone i Zresetuj wartość domyślną. Aby uzyskać więcej informacji, zobacz [strony właściwości MIDL: zaawansowane](../ide/midl-property-pages-advanced.md).  
  
    -   Jeśli **Format informacji debugowania** ustawiono **/zi** w konfiguracji projektu Win32, następnie ustawiono **/zi** w konfiguracji projektu 64-bitowych. Aby uzyskać więcej informacji, zobacz [/z7, / zi, /ZI (Format informacji debugowania)](../build/reference/z7-zi-zi-debug-information-format.md).  
  
    > [!NOTE]
    >  Żadna z tych właściwości projektu są zmieniane, jeśli zostaną one zastąpione na poziomie plików.  
  
## <a name="see-also"></a>Zobacz też  

[Aplikacje 64-bitowe .NET framework](/dotnet/framework/64-bit-apps)   
[Visual C++ for x64 64-bitowy, konfigurowanie obiektów docelowych](../build/configuring-programs-for-64-bit-visual-cpp.md)   
[Debugowanie aplikacji 64-bitowych](/visualstudio/debugger/debug-64-bit-applications)