---
title: /WINMDKEYCONTAINER (określ kontener klucza)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKEYCONTAINER
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
ms.openlocfilehash: 0b6cb42fc391d94634ae90e5a4cc17e69a14ff09
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813074"
---
# <a name="winmdkeycontainer-specify-key-container"></a>/WINMDKEYCONTAINER (określ kontener klucza)

Określa kontener klucza do podpisania pliku metadanych Windows (winmd).

```
/WINMDKEYCONTAINER:name
```

## <a name="remarks"></a>Uwagi

Przypomina [/KeyContainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md) opcji konsolidatora, która jest stosowana do pliku (.winmd).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **metadanych Windows** stronę właściwości.

1. W **kontener klucza metadanych Windows** wprowadź lokalizację.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
