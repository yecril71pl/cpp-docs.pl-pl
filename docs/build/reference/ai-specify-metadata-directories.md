---
title: -AI (Określ katalogi metadanych) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.AdditionalUsingDirectories
- VC.Project.VCNMakeTool.AssemblySearchPath
- /AI
- VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories
dev_langs:
- C++
helpviewer_keywords:
- /AI compiler option [C++]
- AI compiler option [C++]
- -AI compiler option [C++]
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f932e186630d1bc6c846c78af99f98262861068
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110672"
---
# <a name="ai-specify-metadata-directories"></a>/AI (Określ katalogi metadanych)

Określa katalog, który kompilator będzie przeszukiwał, aby rozwiązać odwołania do plików przekazywane do `#using` dyrektywy.

## <a name="syntax"></a>Składnia

> **/AI**_katalogu_

## <a name="arguments"></a>Argumenty

*Katalog*<br/>
Katalog lub ścieżka, w której kompilator będzie wyszukiwał.

## <a name="remarks"></a>Uwagi
Tylko jeden katalog może być przekazywany do **/AI** wywołania. Określ jedną **/AI** opcję dla każdej ścieżki, w której kompilator ma wyszukiwać. Na przykład, aby dodać do ścieżki wyszukiwania kompilatora dla zarówno C:\Project\Meta, jak i C:\Common\Meta `#using` dyrektyw, Dodaj `/AI"C:\Project\Meta" /AI"C:\Common\Meta"` do wiersza polecenia kompilatora lub Dodaj każdy katalog do **dodatkowe # katalogi using** właściwości w programie Visual Studio.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

2. Wybierz **właściwości konfiguracji** > **C/C++** > **ogólne** stronę właściwości.

3. Modyfikowanie **dodatkowe # katalogi using** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)   
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
[#using — dyrektywa](../../preprocessor/hash-using-directive-cpp.md)