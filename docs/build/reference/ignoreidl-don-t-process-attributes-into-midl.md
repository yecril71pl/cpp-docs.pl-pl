---
title: -IGNOREIDL (Don&#39;t procesu atrybutów w MIDL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
dev_langs:
- C++
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7014440c3479016c89b774f9a80cc03fc4b5d4c3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708230"
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
[/ IDLOUT (nazwij wyjściowe pliki MIDL)](../../build/reference/idlout-name-midl-output-files.md)
 [ /tlbout (nazwa. Plik TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)
[/MIDL (Określ opcje wiersza polecenia MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)
[kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)