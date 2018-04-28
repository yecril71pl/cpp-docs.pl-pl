---
title: Błąd niekrytyczny ML A2031 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2031
dev_langs:
- C++
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ab35776944604f3133254532d2631460c755983
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="ml-nonfatal-error-a2031"></a>Błąd niekrytyczny ML A2031
**musi być indeksu lub base rejestru**  
  
 Próbowano użyć rejestru, który nie jest podstawowym lub indeks rejestru w wyrażeniu pamięci.  
  
 Na przykład następujących wyrażeń być przyczyną tego błędu:  
  
```  
[ax]  
[bl]  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)