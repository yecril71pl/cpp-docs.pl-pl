---
title: "Błąd niekrytyczny ML A2006 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A2006
dev_langs:
- C++
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d758e612d9e072084498b55e4e8b700748af881f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="ml-nonfatal-error-a2006"></a>Błąd niekrytyczny ML A2006
**Niezdefiniowany symbol: identyfikator**  
  
 Próbowano użyć symbolu, który nie został zdefiniowany.  
  
 Jedną z następujących przyczyn:  
  
-   Symbol nie został zdefiniowany.  
  
-   Pole nie jest członkiem określonej struktury.  
  
-   Symbol został zdefiniowany w pliku dołączenia, które nie zostały uwzględnione.  
  
-   Zewnętrzny symbol został użyty bez [EXTERN](../../assembler/masm/extern-masm.md) lub [externdef —](../../assembler/masm/externdef.md) dyrektywy.  
  
-   Nazwa symbolu została wpisana z błędem.  
  
-   Etykieta kod lokalny odwoływano poza jej zakres.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)