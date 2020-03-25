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
ms.openlocfilehash: b191ce0942d7596090bfd7948a37a5c9e6aac15e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169438"
---
# <a name="even-and-align-directives"></a>EVEN i ALIGN — dyrektywy

**Specyficzne dla firmy Microsoft**

Chociaż wbudowany asembler nie obsługuje większości dyrektyw MASM, obsługuje `EVEN` i **wyrównywania**. Te dyrektywy wprowadzają **NOP** (bez operacji) instrukcje w kodzie zestawu, jak jest to konieczne do wyrównywania etykiet do określonych granic. Dzięki temu operacje pobierania instrukcji są bardziej wydajne w przypadku niektórych procesorów.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
