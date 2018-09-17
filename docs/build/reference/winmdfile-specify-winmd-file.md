---
title: -WINMDFILE (Określ plik winmd) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
dev_langs:
- C++
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdea558f1c9a56e68a8e2e61703b92ea569a0629
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709894"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (określ plik winmd)

Określa nazwę pliku dla pliku wyjściowego metadanych środowiska wykonawczego Windows (winmd), który jest generowany przez [/WINMD](../../build/reference/winmd-generate-windows-metadata.md) — opcja konsolidatora.

```
/WINMDFILE:filename
```

## <a name="remarks"></a>Uwagi

Użyj wartości, który jest określony w `filename` do przesłaniania domyślnej nazwy pliku winmd (`binaryname`winmd). Należy zauważyć, że nie dołączaj ".winmd" do `filename`.  Jeśli wiele wartości nie są wyświetlane na **/winmdfile** wiersza polecenia, ostatni z nich ma pierwszeństwo.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **metadanych Windows** stronę właściwości.

1. W **plik metadanych Windows** wpisz lokalizację pliku.

## <a name="see-also"></a>Zobacz też

[/ WINMD (Generuj metadane Windows)](../../build/reference/winmd-generate-windows-metadata.md)
[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)