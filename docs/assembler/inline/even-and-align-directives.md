---
title: "EVEN i ALIGN — dyrektywy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 278794e0105ee054fdd4948967a78982a9d46d8c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="even-and-align-directives"></a>EVEN i ALIGN — dyrektywy
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Asembler wbudowany nie obsługują większość dyrektywy MASM, obsługuje on `EVEN` i **WYRÓWNAJ**. Umieszczanie tych dyrektyw **NOP** (Brak operacji) instrukcjami kodu zestawu zgodnie z potrzebami, aby były wyrównane etykiety do określonych granic. Dzięki temu operacje pobieranie instrukcji efektywniejsze niektórych procesorów.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)