---
title: /arch (x64)
ms.date: 11/04/2016
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: c515307ee3a49ef746eea939e90d7aecbd661b95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295288"
---
# <a name="arch-x64"></a>/arch (x64)

Określa architekturę do generowania kodu na x64. Zobacz też [/arch (x86)](arch-x86.md) i [/arch (ARM)](arch-arm.md).

## <a name="syntax"></a>Składnia

```
/arch:[AVX|AVX2]
```

## <a name="arguments"></a>Argumenty

**/arch:AVX**<br/>
Włącza używanie instrukcji Intel Advanced Vector Extensions.

**/arch:AVX2**<br/>
Włącza używanie instrukcji Intel zaawansowany wektor rozszerzeń 2.

## <a name="remarks"></a>Uwagi

**/ arch** tylko ma wpływ na generowanie kodu dla funkcji natywnych. Kiedy używasz [/CLR](clr-common-language-runtime-compilation.md) do kompilowania, **/arch** nie ma wpływu na generowanie kodu dla funkcji zarządzanej.

`__AVX__` Symbol preprocesora jest definiowany podczas **/arch:** określono opcję kompilatora. `__AVX2__` Symbol preprocesora jest definiowany podczas **/arch:AVX2** określono opcję kompilatora. Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md). **/Arch:AVX2** opcja została wprowadzona w Visual Studio 2013 Update 2, wersja 12.0.34567.1.

### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora/arch: lub /arch:AVX2 w programie Visual Studio

1. Otwórz **stron właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji**, **C/C++** folderu.

1. Wybierz **generowania kodu** stronę właściwości.

1. W **Włącz rozszerzone rozkazów** listy rozwijanej wybierz **Advanced Vector Extensions (/ arch: AVX)** lub **zaawansowany wektor rozszerzeń 2 (/ arch: AVX2)**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Zobacz także

[/arch (Minimalna architektura procesora CPU)](arch-minimum-cpu-architecture.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
