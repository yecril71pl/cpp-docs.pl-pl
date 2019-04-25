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
ms.openlocfilehash: 7150d4ff8f35b00d96caa21fd5ea3754fec76030
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317877"
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

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
