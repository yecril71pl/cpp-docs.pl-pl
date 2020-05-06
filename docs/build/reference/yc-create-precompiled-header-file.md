---
title: /Yc (Utwórz prekompilowany plik nagłówka)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
ms.openlocfilehash: 71a05df3adc74edfd814bb6dc15121e4a343dc4d
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825759"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (Utwórz prekompilowany plik nagłówka)

Instruuje kompilator, aby utworzył prekompilowany plik nagłówkowy (. pch), który reprezentuje stan kompilacji w określonym punkcie.

## <a name="syntax"></a>Składnia

> __/YC__\
> __/Yc__*Nazwa pliku* /YC

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Określa plik nagłówka (. h). Gdy ten argument jest używany, kompilator kompiluje cały kod do i łącznie z plikiem. h.

## <a name="remarks"></a>Uwagi

Gdy **/YC** jest określony bez argumentu, kompilator kompiluje cały kod do końca bazowego pliku źródłowego lub do punktu w pliku bazowym, w którym występuje dyrektywa [hdrstop](../../preprocessor/hdrstop.md) . Utworzony plik PCH ma taką samą nazwę bazową jak podstawowy plik źródłowy, chyba że określono inną nazwę pliku przy użyciu **hdrstop** pragma lub opcji **/FP** .

Wstępnie skompilowany kod jest zapisywany w pliku o nazwie utworzonej na podstawie podstawowej nazwy pliku określonego za pomocą opcji **/YC** i rozszerzenia PCH. Można również użyć [/FP (Name. Plik PCH)](fp-name-dot-pch-file.md) , aby określić nazwę prekompilowanego pliku nagłówkowego.

Jeśli używasz*nazwy pliku* __/YC__, kompilator kompiluje cały kod do i łącznie z określonym plikiem do późniejszego użycia z [/Yu (Użyj prekompilowanego pliku nagłówkowego)](yu-use-precompiled-header-file.md) .

Jeśli opcje __/YC__*filename* i __/Yu__*filename* są wykonywane w tym samym wierszu polecenia, a oba odwołania lub implikują, pierwszeństwo ma ta sama nazwa pliku, __/YC__*filename* . Ta funkcja upraszcza pisanie plików reguł programu make.

Aby uzyskać więcej informacji na temat prekompilowanych nagłówków, zobacz:

- [/Y (Prekompilowane nagłówki)](y-precompiled-headers.md)

- [Wstępnie skompilowane pliki nagłówkowe](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Wybierz plik. cpp. Plik. cpp musi #include pliku h, który zawiera wstępnie skompilowane informacje nagłówka. Ustawienie **/YC** projektu można zastąpić na poziomie pliku.

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Otwórz stronę właściwości **Konfiguracja**, **C/C++**, **prekompilowane nagłówki** .

1. Zmodyfikuj właściwość **prekompilowanego nagłówka** .

1. Aby ustawić nazwę pliku, zmodyfikuj Właściwość **prekompilowanego pliku nagłówkowego** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.

## <a name="example"></a>Przykład

Spójrzmy na poniższy kod:

```cpp
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
// ...
```

Gdy ten kod jest kompilowany za pomocą polecenia `CL /YcMYAPP.H PROG.CPP`, kompilator zapisuje wszystkie procesy wstępne dla afxwin. h, Resource. h i MojaApl. h w pliku prekompilowanego nagłówka o nazwie MojaApl. PCH.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Wstępnie skompilowane pliki nagłówkowe](../creating-precompiled-header-files.md)
