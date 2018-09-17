---
title: -TLBOUT (nazwa. Plik TLB) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
dev_langs:
- C++
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c44028f834d2b3200b970fdc613d0bf4d4efd29
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702861"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (Nazywanie pliku .TLB)

```
/TLBOUT:[path\]filename
```

## <a name="arguments"></a>Argumenty

*Ścieżka*<br/>
Specyfikacja bezwzględną lub ścieżką względną tworzona pliku .tlb.

*Nazwa pliku*<br/>
Określa nazwę pliku .tlb utworzony przez kompilator MIDL. Przyjęto, że brak rozszerzenia pliku; Określ *filename*.tlb, jeśli chcesz, aby rozszerzenie .tlb.

## <a name="remarks"></a>Uwagi

Opcja/tlbout Określa nazwę i rozszerzenie pliku .tlb.

Kompilator MIDL jest wywoływana przez konsolidator Visual C++, gdy łączenie projektów, które mają [modułu](../../windows/module-cpp.md) atrybutu.

Jeśli nie określono/tlbout, pliku .tlb otrzymają nazwy z [/idlout](../../build/reference/idlout-name-midl-output-files.md) *filename*. Jeśli nie określono/idlout, pliku .tlb zostanie wywołana metoda vc70.tlb.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **osadzone IDL** stronę właściwości.

1. Modyfikowanie **biblioteki typów** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)<br/>
[/ IGNOREIDL (nie Przetwarzaj atrybutów w MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)
[/MIDL (Określ opcje wiersza polecenia MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)
[kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)