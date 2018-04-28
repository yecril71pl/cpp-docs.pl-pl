---
title: Błąd niekrytyczny ML A2006 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2006
dev_langs:
- C++
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31d2f7df00d1c0658ee8301fbde1efe2522b52fc
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
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