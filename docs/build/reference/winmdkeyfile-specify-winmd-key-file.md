---
title: -WINMDKEYFILE (Określ plik klucza winmd) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
dev_langs:
- C++
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d688db3039681fc684e6344e4a27ae7a64544757
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714450"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE (określ plik klucza winmd)

Określa klucz lub parę kluczy do podpisania pliku metadanych środowiska wykonawczego Windows (winmd).

```
/WINMDKEYFILE:filename
```

## <a name="remarks"></a>Uwagi

Przypomina [/KeyFile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) opcji konsolidatora, która jest stosowana do pliku winmd.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **metadanych Windows** stronę właściwości.

1. W **plik klucza metadanych Windows** wpisz lokalizację pliku.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)