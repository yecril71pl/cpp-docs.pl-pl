---
title: -MERGE (Połącz sekcje) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /merge
- VC.Project.VCLinkerTool.MergeSections
dev_langs:
- C++
helpviewer_keywords:
- sections, combining
- /MERGE linker option
- sections, naming
- sections
- -MERGE linker option
- MERGE linker option
ms.assetid: 10fb20c2-0b3f-4c8d-98a8-f69aedf03d52
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01768ffcfd647d3e05c0b96647d544e3d68e77d0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722673"
---
# <a name="merge-combine-sections"></a>/MERGE (Połącz sekcje)

```
/MERGE:from=to
```

## <a name="remarks"></a>Uwagi

Opcja/merge Scala pierwszą sekcję (*z*) z drugą sekcją (*do*), nazywając wynikową sekcję *do*. Na przykład `/merge:.rdata=.text`.

Jeśli druga sekcja nie istnieje, LINK zmienia nazwę sekcji *z* jako *do*.

Opcja/merge Scala jest przydatne do tworzenia urządzenia vxd i zastępowanie nazwy sekcji generowanych przez kompilator.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **zaawansowane** stronę właściwości.

1. Modyfikowanie **Scal sekcje** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergeSections%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)