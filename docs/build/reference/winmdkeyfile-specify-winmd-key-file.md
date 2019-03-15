---
title: /WINMDKEYFILE (określ plik klucza winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
ms.openlocfilehash: 4b0c847bc5be6c73b78af4aa15b0074c712cc840
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "57820406"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE (określ plik klucza winmd)

Określa klucz lub parę kluczy do podpisania pliku metadanych środowiska wykonawczego Windows (winmd).

```
/WINMDKEYFILE:filename
```

## <a name="remarks"></a>Uwagi

Przypomina [/KeyFile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) opcji konsolidatora, która jest stosowana do pliku winmd.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **metadanych Windows** stronę właściwości.

1. W **plik klucza metadanych Windows** wpisz lokalizację pliku.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
