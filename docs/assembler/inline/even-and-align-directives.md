---
title: EVEN i ALIGN — dyrektywy
ms.date: 08/30/2018
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
ms.openlocfilehash: 63fa73988b9b9433a988035789a923ac73936214
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441579"
---
# <a name="even-and-align-directives"></a>EVEN i ALIGN — dyrektywy

**Specyficzne dla firmy Microsoft**

Chociaż wbudowany asembler nie obsługuje większości dyrektyw MASM, obsługuje `EVEN` i **wyrównywania**. Te dyrektywy wprowadzają **NOP** (bez operacji) instrukcje w kodzie zestawu, jak jest to konieczne do wyrównywania etykiet do określonych granic. Dzięki temu operacje pobierania instrukcji są bardziej wydajne w przypadku niektórych procesorów.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>