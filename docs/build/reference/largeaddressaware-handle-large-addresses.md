---
title: -LARGEADDRESSAWARE (Obsługa dużych adresów) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
dev_langs:
- C++
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a68b18f912d7e6ca0f0f642c85e8439be0e5b67
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726333"
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (Obsługa dużych adresów)

```
/LARGEADDRESSAWARE[:NO]
```

## <a name="remarks"></a>Uwagi

Opcja/largeaddressaware informuje konsolidator, że aplikacja może obsługiwać adresy większe niż 2 gigabajty. W 64-bitowych kompilatorów ta opcja jest domyślnie. W 32-bitowych kompilatorów ustawione jest/largeaddressaware Jeśli/largeaddressaware nie jest określona inaczej w linii konsolidatora.

Jeśli aplikacja została połączona z/largeaddressaware, DUMPBIN [/HEADERS](../../build/reference/headers.md) spowoduje to wyświetlenie informacji w tym celu.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **systemu** stronę właściwości.

1. Modyfikowanie **Włącz duże adresy** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)