---
title: -WINMDKEYCONTAINER (Określ kontener klucza) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKEYCONTAINER
dev_langs:
- C++
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d48a0966b974b1a264b4d2b539f5861ce0dfd57
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716829"
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