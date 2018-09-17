---
title: -arch (x64) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 236923732a193830fe3fad643570666db56cddac
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707359"
---
# <a name="arch-x64"></a>/arch (x64)

Określa architekturę do generowania kodu na x64. Zobacz też [/arch (x86)](../../build/reference/arch-x86.md) i [/arch (ARM)](../../build/reference/arch-arm.md).

## <a name="syntax"></a>Składnia

```
/arch:[AVX|AVX2]
```

## <a name="arguments"></a>Argumenty

**/ arch:**<br/>
Włącza używanie instrukcji Intel Advanced Vector Extensions.

**/arch:AVX2**<br/>
Włącza używanie instrukcji Intel zaawansowany wektor rozszerzeń 2.

## <a name="remarks"></a>Uwagi

**/ arch** tylko ma wpływ na generowanie kodu dla funkcji natywnych. Kiedy używasz [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) do kompilowania, **/arch** nie ma wpływu na generowanie kodu dla funkcji zarządzanej.

`__AVX__` Symbol preprocesora jest definiowany podczas **/arch:** określono opcję kompilatora. `__AVX2__` Symbol preprocesora jest definiowany podczas **/arch:AVX2** określono opcję kompilatora. Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md). **/Arch:AVX2** opcja została wprowadzona w Visual Studio 2013 Update 2, wersja 12.0.34567.1.

### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora/arch: lub /arch:AVX2 w programie Visual Studio

1. Otwórz **stron właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji**, **C/C++** folderu.

1. Wybierz **generowania kodu** stronę właściwości.

1. W **Włącz rozszerzone rozkazów** listy rozwijanej wybierz **Advanced Vector Extensions (/ arch: AVX)** lub **zaawansowany wektor rozszerzeń 2 (/ arch: AVX2)**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Zobacz też

[/ arch (minimalna architektura Procesora)](../../build/reference/arch-minimum-cpu-architecture.md)
[opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)