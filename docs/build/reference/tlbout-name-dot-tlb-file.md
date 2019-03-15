---
title: /TLBOUT (Nazywanie pliku .TLB)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
ms.openlocfilehash: 4e04514933a521bbf9d927fa6b47bacb87896353
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822265"
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

Kompilator MIDL jest wywoływana przez konsolidator MSVC podczas łączenia projektów, które mają [modułu](../../windows/module-cpp.md) atrybutu.

Jeśli nie określono/tlbout, pliku .tlb otrzymają nazwy z [/idlout](idlout-name-midl-output-files.md) *filename*. Jeśli nie określono/idlout, pliku .tlb zostanie wywołana metoda vc70.tlb.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **osadzone IDL** stronę właściwości.

1. Modyfikowanie **biblioteki typów** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
[/IGNOREIDL (Nie przetwarzaj atrybutów w MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (Określ opcje wiersza polecenia MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)
