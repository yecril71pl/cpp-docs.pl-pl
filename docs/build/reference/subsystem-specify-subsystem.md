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
ms.openlocfilehash: 70d6f047cf18b8b768d40533e2acc6cb2f649327
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="subsystem-specify-subsystem"></a>/SUBSYSTEM (Określ podsystem)
```  
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|  
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|  
            POSIX|WINDOWS)  
            [,major[.minor]]  
```  
  
 BOOT_APPLICATION  
 Aplikacja jest uruchamiana w środowisku rozruchu systemu Windows. Aby uzyskać więcej informacji na temat aplikacji rozruchu, zobacz [o BCD](http://msdn.microsoft.com/library/windows/desktop/aa362639).  
  
 KONSOLI  
 Aplikacja trybu znaków Win32. System operacyjny udostępnia konsoli dla aplikacji konsoli. Jeśli `main` lub `wmain` jest zdefiniowany dla kodu natywnego `int main(array<String ^> ^)` jest zdefiniowany dla kodu zarządzanego lub całkowicie kompilowania aplikacji za pomocą `/clr:safe`, CONSOLE jest wartością domyślną.  
  
 Interfejs Extensible Firmware Interface  
 EFI_ * podsystemy. Zobacz specyfikację interfejsu EFI, aby uzyskać więcej informacji. Na przykład zobacz witrynę sieci Web Intel. Minimalna wersja wersji i domyślne to 1.0.  
  
 NATYWNY  
 Sterowniki trybu jądra dla systemu Windows NT. Ta opcja jest zarezerwowany dla składników systemu Windows. Jeśli [/Driver: WDM](../../build/reference/driver-windows-nt-kernel-mode-driver.md) określono NATYWNY jest ustawieniem domyślnym.  
  
 POSIX  
 Aplikacja uruchamiana z podsystem POSIX w systemie Windows NT.  
  
 SYSTEMU WINDOWS  
 Aplikacja nie wymaga konsoli, prawdopodobnie ponieważ tworzy własne okna do interakcji z użytkownikiem. Jeśli `WinMain` lub `wWinMain` jest zdefiniowany dla kodu natywnego lub `WinMain(HISTANCE *, HINSTANCE *, char *, int)` lub `wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)` jest zdefiniowany dla zarządzanego kodu systemu WINDOWS jest ustawieniem domyślnym.  
  
 `Major` i `minor` (opcjonalnie)  
 Określ minimalną wymaganą wersję podsystemu. Argumenty są liczbami dziesiętnymi z zakresu od 0 do 65 535. Zobacz uwagi, aby uzyskać więcej informacji. Nie ma żadnych górną granicę numerów wersji.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/Subsystem określa środowisko dla pliku wykonywalnego.  
  
 Wybór podsystemu wpływa na symbol punktu wejścia (lub funkcję punktu wejścia), które wybierze konsolidator.  
  
 Minimalna opcjonalne i domyślne `major` i `minor` numery wersji dla podsystemów są następujące.  
  
|Podsystem|Minimalnie|Domyślny|  
|---------------|-------------|-------------|  
|BOOT_APPLICATION|1.0|1.0|  
|KONSOLI|5.01 (x 86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|6,00 (x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|SYSTEMU WINDOWS|5.01 (x 86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|6,00 (x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|MACIERZYSTY (z użyciem DRIVER: WDM)|1,00 (x 86) 1.10 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ARM)|1,00 (x 86) 1.10 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ARM)|  
|NATYWNE (bez/Driver: WDM)|4.00 (x 86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|4.00 (x 86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|POSIX|1.0|19.90|  
|EFI_APPLICATION, EFI_BOOT_SERVICE_DRIVER, EFI_ROM, EFI_RUNTIME_DRIVER|1.0|1.0|  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Wybierz folder do konsolidatora.  
  
3.  Wybierz **systemu** strony właściwości.  
  
4.  Modyfikowanie `SubSystem` właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)