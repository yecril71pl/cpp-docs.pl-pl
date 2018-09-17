---
title: -RELEASE (Ustaw sumę kontrolną) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /release
- VC.Project.VCLinkerTool.SetChecksum
dev_langs:
- C++
helpviewer_keywords:
- -RELEASE linker option
- /RELEASE linker option
- checksum setting
- RELEASE linker option
ms.assetid: 93bcadf4-29ac-4824-914b-6997e3751d22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69439400ec58e2d41ef0359237b30ea09c5fd170
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710076"
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