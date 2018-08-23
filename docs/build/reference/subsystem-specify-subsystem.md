---
title: -SUBSYSTEM (Określ podsystem) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /subsystem
- VC.Project.VCLinkerTool.SubSystem
- VC.Project.VCLinkerTool.SubSystemVersion
dev_langs:
- C++
helpviewer_keywords:
- /SUBSYSTEM linker option
- SUBSYSTEM linker option
- -SUBSYSTEM linker option
- subsystem specifications
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a40cf81d0b00123692c9ea8b0e2f3111fb914fbb
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465892"
---
# <a name="subsystem-specify-subsystem"></a>/SUBSYSTEM (Określ podsystem)
```  
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|  
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|  
            POSIX|WINDOWS)  
            [,major[.minor]]  
```  
  
 BOOT_APPLICATION  
 Aplikacja, która jest uruchamiana w środowisku Windows rozruchowego. Aby uzyskać więcej informacji dotyczących aplikacji rozruchu, zobacz [o BCD](http://msdn.microsoft.com/library/windows/desktop/aa362639).  
  
 KONSOLA  
 Aplikacja trybu znaków Win32. System operacyjny zapewnia konsolę dla aplikacji konsoli. Jeśli `main` lub `wmain` jest zdefiniowany dla kodu natywnego, `int main(array<String ^> ^)` jest zdefiniowany dla kodu zarządzanego, lub całkowicie skompilować aplikację przy użyciu `/clr:safe`, CONSOLE jest wartością domyślną.  
  
 Interfejs Extensible Firmware Interface  
 EFI_ * podsystemów. Zobacz specyfikację interfejsu EFI, aby uzyskać więcej informacji. Na przykład zobacz witrynę sieci Web Intel. Minimalna wersja wersji i domyślne to 1.0.  
  
 NATYWNE  
 Sterowniki trybu jądra Windows NT. Ta opcja jest zazwyczaj zarezerwowana dla składników systemu Windows. Jeśli [WDM](../../build/reference/driver-windows-nt-kernel-mode-driver.md) określono NATYWNYCH jest ustawieniem domyślnym.  
  
 POSIX  
 Aplikacja uruchamiana z podsystem POSIX w Windows NT.  
  
 SYSTEMU WINDOWS  
 Aplikacja nie wymaga konsoli, prawdopodobnie ponieważ powoduje to utworzenie własnego systemu windows do interakcji z użytkownikiem. Jeśli `WinMain` lub `wWinMain` jest zdefiniowany dla kodu natywnego lub `WinMain(HISTANCE *, HINSTANCE *, char *, int)` lub `wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)` jest zdefiniowany dla kodu zarządzanego, systemu WINDOWS jest ustawieniem domyślnym.  
  
 `Major` i `minor` (opcjonalnie)  
 Określ minimalną wymaganą wersję podsystemu. Argumenty są liczbami dziesiętnymi z zakresu od 0 do 65 535. Zobacz uwagi, aby uzyskać więcej informacji. Nie ma żadnych granic dla numerów wersji.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/Subsystem określa środowisko dla pliku wykonywalnego.  
  
 Wybór podsystemu wpływa na symbol punktu wejścia (lub funkcję punktu wejścia), które wybierze konsolidator.  
  
 Opcjonalne minimalnych i domyślnych `major` i `minor` numery wersji dla podsystemów są następujące.  
  
|Podsystem|Minimalnie|Domyślny|  
|---------------|-------------|-------------|  
|BOOT_APPLICATION|1.0|1.0|  
|KONSOLA|5.01 (x 86) 5.02 (x 64) 6.02 (ARM)|6.00 (x86, x64) 6.02 (ARM)|  
|SYSTEMU WINDOWS|5.01 (x 86) 5.02 (x 64) 6.02 (ARM)|6.00 (x86, x64) 6.02 (ARM)|  
|NATYWNY (DRIVER: WDM)|1,00 (x 86) — x64 ARM 64 1.10|1,00 (x 86) — x64 ARM 64 1.10|  
|NATYWNE (bez WDM)|4.00 (x 86) 5.02 (x 64) 6.02 (ARM)|4.00 (x 86) 5.02 (x 64) 6.02 (ARM)|  
|POSIX|1.0|19.90|  
|EFI_APPLICATION, EFI_BOOT_SERVICE_DRIVER, EFI_ROM, EFI_RUNTIME_DRIVER|1.0|1.0|  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Wybierz folder konsolidatora.  
  
3.  Wybierz **systemu** stronę właściwości.  
  
4.  Modyfikowanie `SubSystem` właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)