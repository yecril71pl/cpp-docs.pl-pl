---
title: /FI (Nazwa pliku wymuszonego dołączenia)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.ForcedIncludes
- VC.Project.VCCLCompilerTool.ForcedIncludeFiles
- VC.Project.VCCLWCECompilerTool.ForcedIncludeFiles
helpviewer_keywords:
- FI compiler option [C++]
- -FI compiler option [C++]
- /FI compiler option [C++]
- preprocess header file compiler option [C++]
ms.assetid: 07e79577-8152-4df9-a64c-aae08c603397
ms.openlocfilehash: 6460f75e2cad81bc1dcc540e3c687de5d0dc0d32
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439800"
---
# <a name="fi-name-forced-include-file"></a>/FI (Nazwa pliku wymuszonego dołączenia)

Powoduje, że preprocesor przetwarza określony plik nagłówkowy.

## <a name="syntax"></a>Składnia

```
/FI[ ]pathname
```

## <a name="remarks"></a>Uwagi

Ta opcja ma ten sam skutek jak określenie pliku z podwójnym cudzysłowem w dyrektywie `#include` w pierwszym wierszu każdego pliku źródłowego określonego w wierszu polecenia, w zmiennej "CL" lub w pliku poleceń. Jeśli używasz wielu opcji **/Fi** , pliki są uwzględniane w kolejności, w jakiej są przetwarzane przez CL.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **C/C++**  .

1. Kliknij stronę właściwości **Zaawansowane** .

1. Zmodyfikuj właściwość **wymuszonego dołączanego pliku** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedIncludeFiles%2A>.

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)
