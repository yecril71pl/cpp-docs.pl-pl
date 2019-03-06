---
title: /arch (ARM)
ms.date: 11/04/2016
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
ms.openlocfilehash: 7fd396f4ed9c02daff5363342d7c851d022919ac
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424993"
---
# <a name="arch-arm"></a>/arch (ARM)

Określa architekturę do generowania kodu na ARM. Zobacz też [/arch (x86)](../../build/reference/arch-x86.md) i [/arch (x64)](../../build/reference/arch-x64.md).

## <a name="syntax"></a>Składnia

```
/arch:[ARMv7VE|VFPv4]
```

## <a name="arguments"></a>Argumenty

**/arch:ARMv7VE**<br/>
Umożliwia użycie instrukcji ARMv7VE wirtualizacja rozszerzenia.

**/arch:VFPv4**<br/>
Umożliwia użycie instrukcji ARM VFPv4. Jeśli ta opcja nie jest określona, VFPv3 jest ustawieniem domyślnym.

## <a name="remarks"></a>Uwagi

`_M_ARM_FP` — Makro (dla tylko ARM) wskazuje, które, jeśli są dostępne, **/arch** użyto opcji kompilatora. Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).

Kiedy używasz [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) do kompilowania, **/arch** nie ma wpływu na generowanie kodu dla funkcji zarządzanej. **/ arch** tylko ma wpływ na generowanie kodu dla funkcji natywnych.

### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora /arch:ARMv7VE lub /arch:VFPv4 w programie Visual Studio

1. Otwórz **stron właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **C/C++** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. W **dodatkowe opcje** Dodaj `/arch:ARMv7VE` lub `/arch:VFPv4`.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Zobacz także

[/arch (Minimalna architektura procesora CPU)](../../build/reference/arch-minimum-cpu-architecture.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)
