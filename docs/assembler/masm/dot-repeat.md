---
title: ". POWTÓRZ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .REPEAT
dev_langs:
- C++
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b5e2bee231ebbf1ec04e56a6cc3a2b2d8b03ecd2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="repeat"></a>.REPEAT
Generuje kod, który powtarza wykonywania blok *instrukcje* do momentu `condition` jest spełniony. [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md), który jest spełniony, gdy CX wynosi zero, może być zastąpiona [. DOPÓKI](../../assembler/masm/dot-until.md). `condition` Jest opcjonalny z **. UNTILCXZ**.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
   .REPEAT  
statements  
.UNTIL condition  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)