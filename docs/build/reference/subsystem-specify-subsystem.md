---
title: /SUBSYSTEM (Określ podsystem)
ms.date: 11/04/2016
f1_keywords:
- /subsystem
- VC.Project.VCLinkerTool.SubSystem
- VC.Project.VCLinkerTool.SubSystemVersion
helpviewer_keywords:
- /SUBSYSTEM linker option
- SUBSYSTEM linker option
- -SUBSYSTEM linker option
- subsystem specifications
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
ms.openlocfilehash: ecda3443d0422af4d5ceec9282d86590c53af2f5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821264"
---
# <a name="subsystem-specify-subsystem"></a>/SUBSYSTEM (Określ podsystem)

```
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|
            POSIX|WINDOWS)
            [,major[.minor]]
```

## <a name="arguments"></a>Argumenty

**BOOT_APPLICATION**<br/>
Aplikacja, która jest uruchamiana w środowisku Windows rozruchowego. Aby uzyskać więcej informacji dotyczących aplikacji rozruchu, zobacz [o BCD](/previous-versions/windows/desktop/bcd/about-bcd).

**KONSOLA**<br/>
Aplikacja trybu znaków Win32. System operacyjny zapewnia konsolę dla aplikacji konsoli. Jeśli `main` lub `wmain` jest zdefiniowany dla kodu natywnego, `int main(array<String ^> ^)` jest zdefiniowany dla kodu zarządzanego, lub całkowicie skompilować aplikację przy użyciu `/clr:safe`, CONSOLE jest wartością domyślną.

**EFI_APPLICATION**<br/>
**EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
Podsystemy rozszerzalnego interfejsu oprogramowania układowego. Zobacz specyfikację interfejsu EFI, aby uzyskać więcej informacji. Przykłady zobacz witrynę sieci Web Intel. Minimalna wersja wersji i domyślne to 1.0.

**NATYWNE**<br/>
Sterowniki trybu jądra Windows NT. Ta opcja jest zazwyczaj zarezerwowana dla składników systemu Windows. Jeśli [WDM](driver-windows-nt-kernel-mode-driver.md) określono NATYWNYCH jest ustawieniem domyślnym.

**POSIX**<br/>
Aplikacja uruchamiana z podsystem POSIX w Windows NT.

**SYSTEMU WINDOWS**<br/>
Aplikacja nie wymaga konsoli, prawdopodobnie ponieważ powoduje to utworzenie własnego systemu windows do interakcji z użytkownikiem. Jeśli `WinMain` lub `wWinMain` jest zdefiniowany dla kodu natywnego lub `WinMain(HISTANCE *, HINSTANCE *, char *, int)` lub `wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)` jest zdefiniowany dla kodu zarządzanego, systemu WINDOWS jest ustawieniem domyślnym.

*główne* i *pomocnicza*<br/>
(Opcjonalnie) Określ minimalną wymaganą wersję podsystemu. Argumenty są liczbami dziesiętnymi z zakresu od 0 do 65 535. Zobacz uwagi, aby uzyskać więcej informacji. Nie ma żadnych granic dla numerów wersji.

## <a name="remarks"></a>Uwagi

**/Subsystem** opcja określa środowisko dla pliku wykonywalnego.

Wybór podsystemu wpływa na symbol punktu wejścia (lub funkcję punktu wejścia), które wybierze konsolidator.

Opcjonalne minimalnych i domyślnych *głównych* i *pomocnicza* numery wersji dla podsystemów są następujące.

|Podsystem|Minimalnie|Domyślny|
|---------------|-------------|-------------|
|BOOT_APPLICATION|1.0|1.0|
|KONSOLA|5.01 (x86) 5.02 (x64) 6.02 (ARM)|6.00 (x86, x64) 6.02 (ARM)|
|SYSTEMU WINDOWS|5.01 (x86) 5.02 (x64) 6.02 (ARM)|6.00 (x86, x64) 6.02 (ARM)|
|NATYWNY (DRIVER: WDM)|1.00 (x86) 1.10 (x64, ARM)|1.00 (x86) 1.10 (x64, ARM)|
|NATYWNE (bez WDM)|4.00 (x86) 5.02 (x64) 6.02 (ARM)|4.00 (x86) 5.02 (x64) 6.02 (ARM)|
|POSIX|1.0|19.90|
|EFI_APPLICATION, EFI_BOOT_SERVICE_DRIVER, EFI_ROM, EFI_RUNTIME_DRIVER|1.0|1.0|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz folder konsolidatora.

1. Wybierz **systemu** stronę właściwości.

1. Modyfikowanie `SubSystem` właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
