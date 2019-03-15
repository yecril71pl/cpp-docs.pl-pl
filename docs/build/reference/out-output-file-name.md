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
ms.openlocfilehash: be5fe929bdcf52be19955a5bc2d7aa093e194f45
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812424"
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

To opcja domyślna nazwa podstawowej biblioteki .mapfile lub importu. Aby uzyskać więcej informacji, zobacz [Generowanie Mapfile](map-generate-mapfile.md) (/ MAP) i [/IMPLIB](implib-name-import-library.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **ogólne** stronę właściwości.

1. Modyfikowanie **plik wyjściowy** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
