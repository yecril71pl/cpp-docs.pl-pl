---
title: /STUB (Nazwa pliku klasy zastępczej MS-DOS)
ms.date: 11/04/2016
f1_keywords:
- /stub
- VC.Project.VCLinkerTool.DosStub
helpviewer_keywords:
- Win32 [C++], attaching MS-DOS stub program
- STUB linker option
- MS-DOS stub file name linker option
- /STUB linker option
- Windows API [C++], attaching MS-DOS stub program
- -STUB linker option
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
ms.openlocfilehash: 289812ce8c6167a82204946c0a362ccad6896a39
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642640"
---
# <a name="stub-ms-dos-stub-file-name"></a>/STUB (Nazwa pliku klasy zastępczej MS-DOS)

```
/STUB:filename
```

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Aplikacja systemu MS-DOS.

## <a name="remarks"></a>Uwagi

Opcja/stub dołącza program szczątkowy systemu MS-DOS do programu systemu Win32.

Program szczątkowy jest wywoływana, jeśli plik jest wykonywane w systemie MS-DOS. Zazwyczaj wyświetli odpowiedni komunikat i; Jednak wszystkie prawidłowe aplikacji systemu MS-DOS może być programu klasy zastępczej.

Określ *filename* programu klasy zastępczej po dwukropek (:) w wierszu polecenia. Sprawdzanie konsolidatora *filename* i wysyła komunikat o błędzie, jeśli plik nie jest plikiem wykonywalnym. Program musi być plik .exe; plik .com jest nieprawidłowa dla programu klasy zastępczej.

Jeśli ta opcja nie jest używany, konsolidator dołącza domyślnego programu klasy zastępczej wysyłający następujący komunikat:

```
This program cannot be run in MS-DOS mode.
```

Podczas kompilowania sterownik urządzenia wirtualnego, *filename* umożliwia użytkownikowi określić nazwę pliku, który zawiera strukturę IMAGE_DOS_HEADER (zdefiniowany w Windows NT. H) można używać w VXD, a nie nagłówek domyślny.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)