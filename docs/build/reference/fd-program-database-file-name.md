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
ms.openlocfilehash: c686de7dc9c9c20c404240db558d2ff66078ceb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292734"
---
# <a name="fd-program-database-file-name"></a>/Fd (Nazwa pliku bazy danych programu)

Określa nazwę pliku, plik bazy danych programu (PDB) utworzone przez [/z7, / zi, /ZI (Format informacji debugowania)](z7-zi-zi-debug-information-format.md).

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

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

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

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)
