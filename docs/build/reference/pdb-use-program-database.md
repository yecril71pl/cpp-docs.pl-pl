---
title: -PDB (Użyj bazy danych programu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
dev_langs:
- C++
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8717be9ee8f754f4e61dbed0211360a0b4f4f780
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717246"
---
# <a name="pdb-use-program-database"></a>/PDB (Korzystaj z bazy danych programu)

```
/PDB:filename
```

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Określone przez użytkownika nazwa bazy danych programu (PDB) tworzonego przez konsolidatora. Zastępuje ona nazwę domyślną.

## <a name="remarks"></a>Uwagi

Domyślnie gdy [/DEBUG](../../build/reference/debug-generate-debug-info.md) jest określona, konsolidator tworzy bazę danych programu (PDB) zawierający informacje o debugowaniu. Domyślna nazwa pliku PDB ma podstawowej nazwy programu i rozszerzenia .pdb.

Użyj/PDB:*filename* można określić nazwę pliku PDB. Jeśli nie określono opcji/debug, / PDB — opcja jest ignorowana.

Plik PDB może być maksymalnie 2GB.

Aby uzyskać więcej informacji, zobacz [pliki .pdb — wejście konsolidatora](../../build/reference/dot-pdb-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **debugowania** stronę właściwości.

1. Modyfikowanie **Generuj plik bazy danych programu** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)