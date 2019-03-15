---
title: /LARGEADDRESSAWARE (Obsługa dużych adresów)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
ms.openlocfilehash: 81a560ebf083e2f93d9bb514fc401186291d7f41
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808121"
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (Obsługa dużych adresów)

```
/LARGEADDRESSAWARE[:NO]
```

## <a name="remarks"></a>Uwagi

Opcja/largeaddressaware informuje konsolidator, że aplikacja może obsługiwać adresy większe niż 2 gigabajty. W 64-bitowych kompilatorów ta opcja jest domyślnie. W 32-bitowych kompilatorów ustawione jest/largeaddressaware Jeśli/largeaddressaware nie jest określona inaczej w linii konsolidatora.

Jeśli aplikacja została połączona z/largeaddressaware, DUMPBIN [/HEADERS](headers.md) spowoduje to wyświetlenie informacji w tym celu.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **systemu** stronę właściwości.

1. Modyfikowanie **Włącz duże adresy** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
