---
title: -NOENTRY (Brak punktu wejścia) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ResourceOnlyDLL
- /noentry
dev_langs:
- C++
helpviewer_keywords:
- entry points [C++], linker specifying
- -NOENTRY linker option
- resource-only DLLs [C++], creating
- NOENTRY linker option
- /NOENTRY linker option [C++]
- DLLs [C++], creating
ms.assetid: 0214dd41-35ad-43ab-b892-e636e038621a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd90cb7824050e9bd0110e75f7120c4f004b8b47
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713469"
---
# <a name="noentry-no-entry-point"></a>/NOENTRY (Brak punktu wejścia)

```
/NOENTRY
```

## <a name="remarks"></a>Uwagi

Opcja/noentry jest wymagana do tworzenia biblioteki DLL tylko do zasobów, która nie zawiera kodu wykonywalnego. Aby uzyskać więcej informacji, zobacz [Tworzenie biblioteki DLL Resource-Only](../../build/creating-a-resource-only-dll.md).

Użyj tej opcji, aby zapobiegać łączeniu odwołania do `_main` do biblioteki DLL.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **zaawansowane** stronę właściwości.

1. Modyfikowanie **punkt wejścia nie** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>.

## <a name="see-also"></a>Zobacz też

[Tworzenie biblioteki DLL z samymi zasobami](../../build/creating-a-resource-only-dll.md)<br/>
[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)