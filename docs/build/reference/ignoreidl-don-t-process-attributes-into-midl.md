---
title: / IGNOREIDL (Don&#39;t procesu atrybutów w MIDL)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
ms.openlocfilehash: f6c5fcbae52ed695f2d0c389607ac4231f069788
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534358"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/ IGNOREIDL (Don&#39;t procesu atrybutów w MIDL)

```
/IGNOREIDL
```

## <a name="remarks"></a>Uwagi

Opcja /IGNOREIDL Określa, że wszelkie [atrybuty IDL](../../windows/idl-attributes.md) w źródle kodu nie powinny być przetwarzane do pliku .idl.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **osadzone IDL** stronę właściwości.

1. Modyfikowanie **Ignoruj osadzone IDL** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)<br/>
[/IDLOUT (Nazwij wyjściowe pliki MIDL)](../../build/reference/idlout-name-midl-output-files.md)<br/>
[/TLBOUT (Nazywanie pliku .TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)<br/>
[/MIDL (Określ opcje wiersza polecenia MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)<br/>
[Kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)