---
title: Błąd krytyczny ML A1010 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1010
dev_langs:
- C++
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b622595b6994c4c4eaa74ed8f824f28dffe89b1a
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="ml-fatal-error-a1010"></a>Błąd krytyczny ML A1010
**niedopasowane bloku zagnieżdżenia:**  
  
 Początek bloku nie ma pasującego zakończenia lub zakończenia bloku nie ma pasującego początku. Może zostać objęty jedną z następujących czynności:  
  
-   Dyrektywy wysokiego poziomu, takich jak [. Jeśli](../../assembler/masm/dot-if.md), [. Powtórz](../../assembler/masm/dot-repeat.md), lub [. GDY](../../assembler/masm/dot-while.md).  
  
-   Dyrektywa zestawu warunkowego, takich jak [IF](../../assembler/masm/if-masm.md), [Powtórz](../../assembler/masm/repeat.md), lub **podczas**.  
  
-   Definicja struktury lub związku.  
  
-   Definicja procedury.  
  
-   Definicja segmentu.  
  
-   A [popcontext —](../../assembler/masm/popcontext.md) dyrektywy.  
  
-   W zestawie warunkowego dyrektywy, takich jak [ELSE](../../assembler/masm/else-masm.md), [ELSEIF](../../assembler/masm/elseif-masm.md), lub **ENDIF** bez odpowiadającego mu [IF](../../assembler/masm/if-masm.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)