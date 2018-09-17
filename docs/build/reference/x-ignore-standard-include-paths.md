---
title: -X (Ignoruj standardowe ścieżki dołączanych plików) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
dev_langs:
- C++
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 994568d74c63e612b55d1101ce957e646c555e4a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707437"
---
# <a name="x-ignore-standard-include-paths"></a>/X (Ignoruj standardowe ścieżki dołączanych plików)

Zabezpiecza kompilator przed wyszukiwaniem dołączonych plików w katalogach określonych w zmiennych środowiskowych PATH lub INCLUDE.

## <a name="syntax"></a>Składnia

```
/X
```

## <a name="remarks"></a>Uwagi

Można użyć tej opcji z [/I (dodatkowe katalogi dołączenia)](../../build/reference/i-additional-include-directories.md) (**/I**`directory`) opcji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **preprocesora** stronę właściwości.

1. Modyfikowanie **Ignoruj standardową ścieżkę obejmują** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>.

## <a name="example"></a>Przykład

W poniższym poleceniu `/X` informuje kompilator, aby zignorować lokalizacjach, określonych przez zmienne środowiskowe PATH lub INCLUDE i `/I` Określa katalog, w którym znajdują się pliki dołączane:

```
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)