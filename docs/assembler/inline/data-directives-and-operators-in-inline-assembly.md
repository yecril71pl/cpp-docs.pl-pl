---
title: Dyrektywy danych i operatory w zestawie wbudowanym
ms.date: 08/30/2018
helpviewer_keywords:
- data directives [C++]
- __asm keyword [C++], referencing limitations
- MASM (Microsoft Macro Assembler), directives
- directives [C++], MASM
- MASM (Microsoft Macro Assembler), structures
- operators [MASM]
- inline assembly, operators
- inline assembly, data directives
- MASM (Microsoft Macro Assembler), operators
- structures [C++], MASM
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
ms.openlocfilehash: 52e20c37f3066122a062e3fc9c64ced576b6c302
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577983"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Dyrektywy danych i operatory w zestawie wbudowanym

**Microsoft Specific**

Mimo że `__asm` bloku można odwoływać się do typów danych C lub C++ i obiektów, nie można zdefiniować, obiektów danych za pomocą dyrektywy MASM lub operatorów. Ściślej mówiąc, nie można użyć dyrektywy definicji **DB**, `DW`, **DD**, `DQ`, `DT`, i `DF`, lub operatorów `DUP` lub  **TO**. MASM struktur i rejestruje również są niedostępne. Wbudowany asembler nie zaakceptuje dyrektywy `STRUC`, `RECORD`, **SZEROKOŚĆ**, lub **MASKI**.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>