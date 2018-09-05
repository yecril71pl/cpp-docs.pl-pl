---
title: EVEN i ALIGN — dyrektywy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- align
- EVEN
dev_langs:
- C++
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06a1007c50e3490e5b14e4da886494557be0d37e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688304"
---
# <a name="even-and-align-directives"></a>EVEN i ALIGN — dyrektywy

**Microsoft Specific**

Mimo że wbudowanego asemblera nie obsługuje większość dyrektywy MASM, obsługuje on `EVEN` i **WYRÓWNAJ**. Te dyrektywy umieścić **NOP** (żadna operacja) zgodnie z instrukcjami w kodzie zestawu, zgodnie z potrzebami, aby wyrównać etykiety do określonych granic. To sprawia, że operacje pobierania instrukcji bardziej wydajne dla niektórych procesorów.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>