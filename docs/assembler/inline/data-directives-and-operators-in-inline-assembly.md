---
title: Dyrektywy danych i operatory w zestawie wbudowanym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0bd3bc686cc8cee1a02e9df936f80f542bec26bd
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Dyrektywy danych i operatory w zestawie wbudowanym
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Mimo że `__asm` bloku może odwoływać się typy danych języka C lub C++ i obiektów, nie można zdefiniować obiekty danych z dyrektywy MASM lub operatorów. W szczególności nie można użyć dyrektywy definicji **DB**, `DW`, **DD**, `DQ`, `DT`, i `DF`, lub operatory `DUP` lub  **TO**. MASM struktury i rejestruje także są niedostępne. Asembler wbudowany nie akceptuje dyrektywy `STRUC`, `RECORD`, **SZEROKOŚĆ**, lub **MASKI**.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)