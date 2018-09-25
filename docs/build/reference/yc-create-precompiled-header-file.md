---
title: -Yc (Utwórz prekompilowany plik nagłówka) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
dev_langs:
- C++
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37a81eb21065ef67ef6d0b6ee7cdc6724c0a517b
ms.sourcegitcommit: 92c568e9466ffd7346a4120c478c9bdea61c8756
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2018
ms.locfileid: "47029518"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (Utwórz prekompilowany plik nagłówka)

Instruuje kompilator, aby utworzyć plik prekompilowanego pliku nagłówkowego (.pch), który reprezentuje stan kompilacji w pewnym momencie.

## <a name="syntax"></a>Składnia

> __/Yc__<br/>
> __/Yc__*nazwy pliku*

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Określa plik nagłówka (.h). Jeśli ten argument jest używany, kompilator kompiluje całego kodu, w tym plik .h klasy.

## <a name="remarks"></a>Uwagi

Gdy **/Yc** jest określona bez argumentu, kompilator kompiluje cały kod do końca pliku źródłowego podstawowej lub do punktu w pliku podstawowego gdzie [hdrstop](../../preprocessor/hdrstop.md) występuje dyrektywie. Wynikowy plik .pch ma taką samą nazwę podstawowej jako pliku źródłowego podstawowego, chyba że określono nazwę innego pliku za pomocą **hdrstop** pragma lub **/FP** opcji.

Wstępnie skompilowany kod jest zapisywany w pliku o nazwie utworzone na podstawie podstawowej nazwy pliku określonego przez **/Yc** opcja i rozszerzeniem .pch. Można również użyć  [ /FP (nazwa. Plik pch)](../../build/reference/fp-name-dot-pch-file.md) opcję, aby określić nazwę pliku wstępnie skompilowanego nagłówka.

Jeśli używasz __/Yc__*filename*, kompilator kompiluje całego kodu, w tym określony plik do późniejszego użytku z [/Yu (Użyj Prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md) opcji.

Jeśli opcje __/Yc__*filename* i __/Yu__*filename* odbywa się na tym samym wierszu polecenia, a oba odwołania, lub w sposób sugerujący, taką samą nazwę pliku, __/Yc__*filename* ma pierwszeństwo. Ta funkcja ułatwia zapisywanie plików reguł programu make.

Aby uzyskać więcej informacji na temat wstępnie skompilowanych nagłówków zobacz:

- [/Y (Prekompilowane nagłówki)](../../build/reference/y-precompiled-headers.md)

- [Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Wybierz plik .cpp. Plik CPP musi #include plik .h, który zawiera informacje o wstępnie skompilowanego nagłówka. Projekt **/Yc** ustawienie można zastąpić na poziomie plików.

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Otwórz **właściwości konfiguracji**, **C/C++**, **prekompilowanych nagłówków** stronę właściwości.

1. Modyfikowanie **wstępnie skompilowany nagłówek** właściwości.

1. Aby ustawić nazwę pliku, należy zmodyfikować **Prekompilowanego pliku nagłówkowego** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.

## <a name="example"></a>Przykład

Rozważmy poniższy kod:

```cpp
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
// ...
```

Kiedy ten kod jest kompilowany przy użyciu polecenia `CL /YcMYAPP.H PROG.CPP`, kompilator zapisuje wszystkie przetwarzania wstępnego dla AFXWIN.h, RESOURCE.h, i MYAPP.h w pliku wstępnie skompilowanego nagłówka o nazwie MYAPP.pch.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)