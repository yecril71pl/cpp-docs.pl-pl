---
title: /PDBSTRIPPED (Usuń symbole prywatne)
ms.date: 11/04/2016
f1_keywords:
- /pdbstripped
- VC.Project.VCLinkerTool.StripPrivateSymbols
helpviewer_keywords:
- /PDBSTRIPPED linker option
- -PDBSTRIPPED linker option
- .pdb files, stripping private symbols
- PDB files, stripping private symbols
- PDBSTRIPPED linker option
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
ms.openlocfilehash: d03ee9d4f2ad3626dc260d171ef349a3a392fd36
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626034"
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED (Usuń symbole prywatne)

```
/PDBSTRIPPED:pdb_file_name
```

## <a name="arguments"></a>Argumenty

*pdb_file_name*<br/>
Określone przez użytkownika nazwa usuniętych bazy danych programu (PDB) tworzonego przez konsolidatora.

## <a name="remarks"></a>Uwagi

Opcja/pdbstripped tworzy drugi plik bazy danych (PDB) programu podczas tworzenia obrazu programu za pomocą kompilatora lub konsolidatora, opcje, które generują plik PDB ([/DEBUG](../../build/reference/debug-generate-debug-info.md), [/z7](../../build/reference/z7-zi-zi-debug-information-format.md), / zd, lub /Zi). Ten drugi plik PDB pomija symbole, których nie chcesz wysłać do klientów. Drugi plik PDB będzie zawierać tylko:

- Symbole publiczne

- Lista plików obiektów i części pliku wykonywalnego, do którego przyczyniają się

- Ramka wskaźnika optymalizacji (ang.) debugowania rekordów służący do przechodzenia na stosie

Usuniętych plików PDB nie będzie zawierać:

- Informacje o typie

- Informacje o numerze wiersza

- Symbole CodeView pliku dla obiektów, takich jak te funkcje, zmienne lokalne i dane statyczne

Pełny plik PDB będzie nadal generowane, gdy używasz/pdbstripped.

Jeśli nie utworzysz plik PDB, / pdbstripped jest ignorowana.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **debugowania** stronę właściwości.

1. Modyfikowanie **Usuń symbole prywatne** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)