---
title: /WINMDKEYCONTAINER (określ kontener klucza)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKEYCONTAINER
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
ms.openlocfilehash: 8d26c49a8cf4a1f71841fabdd4ec30fb437ad349
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532239"
---
# <a name="winmdkeycontainer-specify-key-container"></a>/WINMDKEYCONTAINER (określ kontener klucza)

Określa kontener klucza do podpisania pliku metadanych Windows (winmd).

```
/WINMDKEYCONTAINER:name
```

## <a name="remarks"></a>Uwagi

Przypomina [/KeyContainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md) opcji konsolidatora, która jest stosowana do pliku (.winmd).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **metadanych Windows** stronę właściwości.

1. W **kontener klucza metadanych Windows** wprowadź lokalizację.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)