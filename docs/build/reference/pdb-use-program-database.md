---
title: /PDB (Korzystaj z bazy danych programu)
ms.date: 11/04/2016
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
ms.openlocfilehash: ddcf83cafd5f499158f3116f04e40397b7f8d0a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320087"
---
# <a name="pdb-use-program-database"></a>/PDB (Korzystaj z bazy danych programu)

```
/PDB:filename
```

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Określone przez użytkownika nazwa bazy danych programu (PDB) tworzonego przez konsolidatora. Zastępuje ona nazwę domyślną.

## <a name="remarks"></a>Uwagi

Domyślnie gdy [/DEBUG](debug-generate-debug-info.md) jest określona, konsolidator tworzy bazę danych programu (PDB) zawierający informacje o debugowaniu. Domyślna nazwa pliku PDB ma podstawowej nazwy programu i rozszerzenia .pdb.

Użyj/PDB:*filename* można określić nazwę pliku PDB. Jeśli nie określono opcji/debug, / PDB — opcja jest ignorowana.

Plik PDB może być maksymalnie 2GB.

Aby uzyskać więcej informacji, zobacz [pliki .pdb — wejście konsolidatora](dot-pdb-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **debugowania** stronę właściwości.

1. Modyfikowanie **Generuj plik bazy danych programu** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
