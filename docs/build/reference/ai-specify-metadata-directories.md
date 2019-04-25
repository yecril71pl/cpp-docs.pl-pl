---
title: /AI (Określ katalogi metadanych)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.AdditionalUsingDirectories
- VC.Project.VCNMakeTool.AssemblySearchPath
- /AI
- VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories
helpviewer_keywords:
- /AI compiler option [C++]
- AI compiler option [C++]
- -AI compiler option [C++]
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
ms.openlocfilehash: 3633cfe34a4f9c627f84cf401cb559f02f8c8229
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273225"
---
# <a name="ai-specify-metadata-directories"></a>/AI (Określ katalogi metadanych)

Określa katalog, który kompilator będzie przeszukiwał, aby rozwiązać odwołania do plików przekazywane do `#using` dyrektywy.

## <a name="syntax"></a>Składnia

> **/AI**_katalogu_

## <a name="arguments"></a>Argumenty

*directory*<br/>
Katalog lub ścieżka, w której kompilator będzie wyszukiwał.

## <a name="remarks"></a>Uwagi

Tylko jeden katalog może być przekazywany do **/AI** wywołania. Określ jedną **/AI** opcję dla każdej ścieżki, w której kompilator ma wyszukiwać. Na przykład, aby dodać do ścieżki wyszukiwania kompilatora dla zarówno C:\Project\Meta, jak i C:\Common\Meta `#using` dyrektyw, Dodaj `/AI"C:\Project\Meta" /AI"C:\Common\Meta"` do wiersza polecenia kompilatora lub Dodaj każdy katalog do **dodatkowe # katalogi using** właściwości w programie Visual Studio.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **ogólne** stronę właściwości.

1. Modyfikowanie **dodatkowe # katalogi using** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[#using — dyrektywa](../../preprocessor/hash-using-directive-cpp.md)
