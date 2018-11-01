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
ms.openlocfilehash: 607af17a60612f69bb24708179bb453409098bde
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654756"
---
# <a name="def-specify-module-definition-file"></a>/DEF (Określ plik definicji modułu)

```
/DEF:filename
```

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Nazwa pliku definicji modułu (.def), które zostaną przekazane do konsolidatora.

## <a name="remarks"></a>Uwagi

Opcja/DEF przekazuje plik definicji modułu (.def) do konsolidatora. Można określić tylko jeden plik .def do łącza. Aby uzyskać szczegółowe informacje dotyczące plików o rozszerzeniu def, zobacz [pliki definicji modułu](../../build/reference/module-definition-dot-def-files.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **dane wejściowe** stronę właściwości.

1. Modyfikowanie **plik definicji modułu** właściwości.

Aby określić plik .def z w środowisku deweloperskim, należy dodać go do projektu, wraz z innymi plikami i następnie określ plik aby opcja/DEF.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)