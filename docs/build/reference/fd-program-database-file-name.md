---
title: /Fd (Nazwa pliku bazy danych programu)
ms.date: 11/04/2016
f1_keywords:
- /FD
- VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName
- VC.Project.VCCLCompilerTool.ProgramDataBaseFileName
helpviewer_keywords:
- /FD compiler option [C++]
- program database file name [C++]
- -FD compiler option [C++]
- PDB files, creating
- program database compiler option [C++]
- .pdb files, creating
- FD compiler option [C++]
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
ms.openlocfilehash: 449b0a2be44f438c35feeb446df6d7c47f270c35
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494320"
---
# <a name="fd-program-database-file-name"></a>/Fd (Nazwa pliku bazy danych programu)

Określa nazwę pliku, plik bazy danych programu (PDB) utworzone przez [/z7, / zi, /ZI (Format informacji debugowania)](../../build/reference/z7-zi-zi-debug-information-format.md).

## <a name="syntax"></a>Składnia

```
/Fdpathname
```

## <a name="remarks"></a>Uwagi

Bez **/Fd**, domyślnie nazwa pliku PDB VC*x*0.pdb, gdzie *x* jest główną wersją Visual C++ w użyciu.

Jeśli określisz nazwę ścieżki, która nie zawiera nazwy pliku (ścieżka kończy się na ukośnik odwrotny), kompilator tworzy plik .pdb o nazwie VC*x*pdb 0 w określonym katalogu.

Jeśli określisz nazwę pliku, który nie zawiera rozszerzenia, kompilator używa .pdb jako rozszerzenie.

Ta opcja również nazwy pliku stanu (.idb) używany do minimalną ponowną kompilację i kompilacji przyrostowej.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **pliki wyjściowe** stronę właściwości.

1. Modyfikowanie **nazwa pliku bazy danych programu** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>.

## <a name="example"></a>Przykład

Ten wiersz polecenia powoduje utworzenie pliku .pdb o nazwie PROG.pdb i .idb pliku o nazwie PROG.idb:

```
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP
```

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/F), opcje](../../build/reference/output-file-f-options.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)