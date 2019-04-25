---
title: /DEF (Określ plik definicji modułu)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ModuleDefinitionFile
- /def
helpviewer_keywords:
- module definition files, specifying
- DEF linker option
- -DEF linker option
- module definition files
- /DEF linker option
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
ms.openlocfilehash: c08412fb50835485e7941b2bb1db088943387b71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272311"
---
# <a name="def-specify-module-definition-file"></a>/DEF (Określ plik definicji modułu)

```
/DEF:filename
```

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Nazwa pliku definicji modułu (.def), które zostaną przekazane do konsolidatora.

## <a name="remarks"></a>Uwagi

Opcja/DEF przekazuje plik definicji modułu (.def) do konsolidatora. Można określić tylko jeden plik .def do łącza. Aby uzyskać szczegółowe informacje dotyczące plików o rozszerzeniu def, zobacz [pliki definicji modułu](module-definition-dot-def-files.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **dane wejściowe** stronę właściwości.

1. Modyfikowanie **plik definicji modułu** właściwości.

Aby określić plik .def z w środowisku deweloperskim, należy dodać go do projektu, wraz z innymi plikami i następnie określ plik aby opcja/DEF.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
