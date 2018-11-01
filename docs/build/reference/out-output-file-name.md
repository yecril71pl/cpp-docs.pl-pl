---
title: /OUT (Nazwa pliku wyjściowego)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
ms.openlocfilehash: f5ba323b830b9d06956d88d957206e3f73c15418
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497190"
---
# <a name="out-output-file-name"></a>/OUT (Nazwa pliku wyjściowego)

```
/OUT:filename
```

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Określone przez użytkownika nazwa pliku wyjściowego. Zastępuje ona nazwę domyślną.

## <a name="remarks"></a>Uwagi

Opcja/out przesłania domyślną nazwę i lokalizację programu tworzonego przez konsolidatora.

Domyślnie konsolidator tworzy nazwę pliku przy użyciu podstawowej nazwy pierwszy plik .obj określony i odpowiednie rozszerzenia (.exe lub .dll).

To opcja domyślna nazwa podstawowej biblioteki .mapfile lub importu. Aby uzyskać więcej informacji, zobacz [Generowanie Mapfile](../../build/reference/map-generate-mapfile.md) (/ MAP) i [/IMPLIB](../../build/reference/implib-name-import-library.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **ogólne** stronę właściwości.

1. Modyfikowanie **plik wyjściowy** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)