---
title: -OUT (nazwa pliku wyjściowego) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
dev_langs:
- C++
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c4bfc79a257424820bed5f784cb0a83daf016d5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725403"
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