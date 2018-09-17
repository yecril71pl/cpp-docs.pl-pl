---
title: -doc (Przetwarzaj komentarze dokumentacji) (C/C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- /doc
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs:
- C++
helpviewer_keywords:
- /doc compiler option [C++]
- comments, C++ code
- XML documentation, comments in source files
- -doc compiler option [C++]
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 488ee353cf245303b5ea73be139a262aea5be49d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706579"
---
# <a name="doc-process-documentation-comments-cc"></a>/doc (Przetwarzaj komentarze dokumentacji) (C/C++)

Powoduje, że kompilator Przetwarzaj komentarze dokumentacji w plikach kodu źródłowego i Utwórz plik .xdc dla każdego pliku kodu źródłowego, który ma komentarze dokumentacji.

## <a name="syntax"></a>Składnia

> **/ doc**[*nazwa*]

## <a name="arguments"></a>Argumenty

*Nazwa*<br/>
Nazwa pliku .xdc, który zostanie utworzony przez kompilator. Prawidłowy tylko w przypadku jeden plik .cpp jest przekazywany w kompilacji.

## <a name="remarks"></a>Uwagi

W plikach xdc są przetwarzane w pliku XML z xdcmake.exe. Aby uzyskać więcej informacji, zobacz [xdcmake — dokumentacja](../../ide/xdcmake-reference.md).

Możesz dodać komentarze dokumentacji do plików kodu źródłowego. Aby uzyskać więcej informacji, zobacz [tagi zalecane dla komentarzy do dokumentacji](../../ide/recommended-tags-for-documentation-comments-visual-cpp.md).

Plik XML wygenerowany za pomocą funkcji IntelliSense, wprowadzić nazwę pliku w pliku XML, który jest taki sam jak zestaw, który chcesz obsługiwać i umieścić ten plik XML w tym samym katalogu co zestaw. W przypadku zestawu odwołuje się do projektu programu Visual Studio, znajduje się także plik XML. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](/visualstudio/ide/using-intellisense) i [podawania komentarzy kodu XML](/visualstudio/ide/supplying-xml-code-comments).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **pliki wyjściowe** stronę właściwości.

1. Modyfikowanie **Generuj pliki dokumentacji XML** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)