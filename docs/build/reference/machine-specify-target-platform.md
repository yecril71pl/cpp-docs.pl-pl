---
title: -MACHINE (Określ platformę docelową) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.TargetMachine
- /machine
dev_langs:
- C++
helpviewer_keywords:
- mapfiles, creating linker
- target platform
- -MACHINE linker option
- /MACHINE linker option
- MACHINE linker option
ms.assetid: 8d41bf4b-7e53-4ab9-9085-d852b08d31c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e159fe15b0aed441b1a96047a3ffb035077d6266
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708620"
---
# <a name="machine-specify-target-platform"></a>/MACHINE (Określ platformę docelową)

```
/MACHINE:{ARM|EBC|X64|X86}
```

## <a name="remarks"></a>Uwagi

Opcja/Machine Określa docelową platformę dla programu.

Zazwyczaj nie trzeba określić opcję/Machine. LINK wnioskuje typ maszyny z plików .obj. Jednak w niektórych sytuacjach łącze nie można określić typu maszyny i problemów [narzędzi konsolidatora LNK1113 błąd](../../error-messages/tool-errors/linker-tools-error-lnk1113.md). Jeśli wystąpi taki błąd, należy określić/Machine.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **zaawansowane** stronę właściwości.

1. Modyfikowanie **maszyna docelowa** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)