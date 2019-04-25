---
title: /showIncludes (Wymień pliki dołączane)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ShowIncludes
- VC.Project.VCCLCompilerTool.ShowIncludes
- /showincludes
helpviewer_keywords:
- include files
- /showIncludes compiler option [C++]
- include files, displaying in compilation
- -showIncludes compiler option [C++]
- showIncludes compiler option [C++]
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
ms.openlocfilehash: d454054c132976a899fcc4a56a63be427e79beec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318163"
---
# <a name="showincludes-list-include-files"></a>/showIncludes (Wymień pliki dołączane)

Powoduje, że kompilator danych wyjściowych listy plików dołączanych. Zagnieżdżone obejmują pliki są również wyświetlane (plikami dołączonymi z plików, które należy uwzględnić).

## <a name="syntax"></a>Składnia

```
/showIncludes
```

## <a name="remarks"></a>Uwagi

W przypadku pliku dołączanego podczas kompilacji wiadomość jest na przykład danych wyjściowych:

```
Note: including file: d:\MyDir\include\stdio.h
```

Zagnieżdżone obejmują pliki są wskazywane przez wcięcia jedno miejsce dla poszczególnych poziomów zagnieżdżenia, na przykład:

```
Note: including file: d:\temp\1.h
Note: including file:  d:\temp\2.h
```

W tym przypadku `2.h` został dostarczony z w ramach `1.h`, dlatego wcięcia.

**/Showincludes** opcji emituje do `stderr`, a nie `stdout`.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **zaawansowane** stronę właściwości.

1. Modyfikowanie **Pokaż obejmuje** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
