---
title: "Błąd niekrytyczny ML A2006 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2006
dev_langs: C++
helpviewer_keywords: A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c27f859f7841bb1b64fadd2f7051b9e0647f0b15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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