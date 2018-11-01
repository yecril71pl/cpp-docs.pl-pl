---
title: /RELEASE (Ustaw sumę kontrolną)
ms.date: 11/04/2016
f1_keywords:
- /release
- VC.Project.VCLinkerTool.SetChecksum
helpviewer_keywords:
- -RELEASE linker option
- /RELEASE linker option
- checksum setting
- RELEASE linker option
ms.assetid: 93bcadf4-29ac-4824-914b-6997e3751d22
ms.openlocfilehash: 6a45e6caa94054d4d485476786ecc5149545ed8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478812"
---
# <a name="release-set-the-checksum"></a>/RELEASE (Ustaw sumę kontrolną)

```
/RELEASE
```

## <a name="remarks"></a>Uwagi

Opcja/Release ustawia sumę kontrolną w nagłówku pliku .exe.

System operacyjny wymaga sumę kontrolną dla sterowników urządzeń. Ustaw sumę kontrolną wersji sterowników urządzeń, aby zapewnić zgodność z systemami operacyjnymi przyszłości.

Opcja/Release jest domyślnie ustawiany podczas [Subsystem](../../build/reference/subsystem-specify-subsystem.md) określono opcję.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **zaawansowane** stronę właściwości.

1. Modyfikowanie **Ustaw sumę kontrolną** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SetChecksum%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)