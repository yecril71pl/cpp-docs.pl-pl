---
title: -WINMD (Generuj metadane Windows) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
dev_langs:
- C++
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25b8b34e55fc0814653f4c44be50e545633be373
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705734"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (generuj metadane systemu Windows)

Umożliwia generowanie pliku metadanych środowiska wykonawczego Windows (winmd).

```
/WINMD[:{NO|ONLY}]
```

## <a name="remarks"></a>Uwagi

**/ WINMD**<br/>
Ustawieniem domyślnym dla aplikacji Universal Windows Platform. Konsolidator generuje binarny plik wykonywalny i pliku metadanych .winmd.

**/WINMD:NO**<br/>
Konsolidator wygeneruje tylko binarny plik wykonywalny, ale nie w pliku winmd.

**/ WINMD: TYLKO**<br/>
Konsolidator generuje plik .winmd, ale nie binarny plik wykonywalny.

Domyślnie, nazwa pliku wyjściowego ma postać `binaryname`winmd. Aby określić inną nazwę pliku, użyj [/winmdfile](../../build/reference/winmdfile-specify-winmd-file.md) opcji.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **metadanych Windows** stronę właściwości.

1. W **Generowanie metadanych Windows** listy rozwijanej wybierz odpowiednią opcję.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)