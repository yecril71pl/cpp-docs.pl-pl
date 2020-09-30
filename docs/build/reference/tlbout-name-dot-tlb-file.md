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
ms.openlocfilehash: 62913eaadd0f0a88f05ce347a6778062a1e66f17
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509336"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (Nazywanie pliku .TLB)

```
/TLBOUT:[path\]filename
```

## <a name="arguments"></a>Argumenty

*ścieżka*<br/>
Bezwzględna lub względna Specyfikacja ścieżki dla lokalizacji, w której ma zostać utworzony plik. tlb.

*Nazwa pliku*<br/>
Określa nazwę pliku TLB utworzonego przez kompilator MIDL. Nie założono rozszerzenia pliku; Określ *filename*. tlb, jeśli chcesz mieć rozszerzenie. tlb.

## <a name="remarks"></a>Uwagi

Opcja/TLBOUT określa nazwę i rozszerzenie pliku. tlb.

Kompilator MIDL jest wywoływany przez konsolidator MSVC podczas łączenia projektów, które mają atrybut [modułu](../../windows/attributes/module-cpp.md) .

Jeśli/TLBOUT nie zostanie określony, plik. tlb pobierze nazwę z *pliku* [/IDLOUT](idlout-name-midl-output-files.md) . Jeśli/IDLOUT nie zostanie określony, plik. tlb będzie miał nazwę vc70. tlb.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **konsolidator** .

1. Kliknij stronę właściwości **osadzony IDL** .

1. Zmodyfikuj właściwość **biblioteki typów** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[MSVC Opcje konsolidatora](linker-options.md)<br/>
[/IGNOREIDL (nie Przetwarzaj atrybutów w MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (Określ opcje wiersza polecenia MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Kompilowanie programu opartego na atrybutach](../../windows/attributes/cpp-attributes-com-net.md)
