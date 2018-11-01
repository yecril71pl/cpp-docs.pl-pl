---
title: EVEN i ALIGN — dyrektywy
ms.date: 08/30/2018
f1_keywords:
- align
- EVEN
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
ms.openlocfilehash: 522d5689d680d0fc334743d2802abe21570dd6f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604378"
---
# <a name="even-and-align-directives"></a>EVEN i ALIGN — dyrektywy

**Microsoft Specific**

Mimo że wbudowanego asemblera nie obsługuje większość dyrektywy MASM, obsługuje on `EVEN` i **WYRÓWNAJ**. Te dyrektywy umieścić **NOP** (żadna operacja) zgodnie z instrukcjami w kodzie zestawu, zgodnie z potrzebami, aby wyrównać etykiety do określonych granic. To sprawia, że operacje pobierania instrukcji bardziej wydajne dla niektórych procesorów.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>