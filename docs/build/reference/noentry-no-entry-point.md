---
title: /NOENTRY (Brak punktu wejścia)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ResourceOnlyDLL
- /noentry
helpviewer_keywords:
- entry points [C++], linker specifying
- -NOENTRY linker option
- resource-only DLLs [C++], creating
- NOENTRY linker option
- /NOENTRY linker option [C++]
- DLLs [C++], creating
ms.assetid: 0214dd41-35ad-43ab-b892-e636e038621a
ms.openlocfilehash: c750fd94e21eec39a25acf216a452faaa277bf7c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811455"
---
# <a name="noentry-no-entry-point"></a>/NOENTRY (Brak punktu wejścia)

```
/NOENTRY
```

## <a name="remarks"></a>Uwagi

Opcja/noentry jest wymagana do tworzenia biblioteki DLL tylko do zasobów, która nie zawiera kodu wykonywalnego. Aby uzyskać więcej informacji, zobacz [Tworzenie biblioteki DLL Resource-Only](../creating-a-resource-only-dll.md).

Użyj tej opcji, aby zapobiegać łączeniu odwołania do `_main` do biblioteki DLL.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **zaawansowane** stronę właściwości.

1. Modyfikowanie **punkt wejścia nie** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>.

## <a name="see-also"></a>Zobacz także

[Tworzenie biblioteki DLL z samymi zasobami](../creating-a-resource-only-dll.md)<br/>
[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
