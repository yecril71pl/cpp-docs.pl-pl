---
title: /FI (Nazwa pliku wymuszonego dołączenia)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.ForcedIncludes
- VC.Project.VCCLCompilerTool.ForcedIncludeFiles
- VC.Project.VCCLWCECompilerTool.ForcedIncludeFiles
- /fi
helpviewer_keywords:
- FI compiler option [C++]
- -FI compiler option [C++]
- /FI compiler option [C++]
- preprocess header file compiler option [C++]
ms.assetid: 07e79577-8152-4df9-a64c-aae08c603397
ms.openlocfilehash: e047ecc5266a898f2c6dc24be3c204f8ddf94386
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293059"
---
# <a name="fi-name-forced-include-file"></a>/FI (Nazwa pliku wymuszonego dołączenia)

Powoduje, że preprocesor można przetworzyć pliku określony nagłówek.

## <a name="syntax"></a>Składnia

```
/FI[ ]pathname
```

## <a name="remarks"></a>Uwagi

Ta opcja ma ten sam skutek co określenie pliku za pomocą podwójnego cudzysłowu w `#include` dyrektywy w pierwszym wierszu każdy plik źródłowy został określony w wierszu polecenia w zmiennej środowiskowej CL lub w pliku poleceń. Jeśli używanych jest wiele **/FI** opcje, pliki znajdują się w kolejności, są przetwarzane przez CL.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **zaawansowane** stronę właściwości.

1. Modyfikowanie **wymuszone Dołącz plik** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedIncludeFiles%2A>.

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)
