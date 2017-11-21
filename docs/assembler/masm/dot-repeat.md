---
title: ". POWTÓRZ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .REPEAT
dev_langs: C++
helpviewer_keywords: .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e60ae387ec619a0109b322902a4ad40c9ad73f1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Odwołania do dyrektyw](../../assembler/masm/directives-reference.md)