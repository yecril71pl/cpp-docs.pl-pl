---
title: "Zapisane rejestrowania wywołującego wywoływanego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 61e8d57c177ded8102f257cf84adedc0de0e312a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="callercallee-saved-registers"></a>Zapisane rejestrowania wywołującego/wywoływanego
Rejestruje RAX, RCX, RDX, R8, R9, R10, R11 są traktowane jako nietrwałe i muszą być traktowane jako zniszczona na wywołania funkcji (chyba że w przeciwnym razie bezpieczeństwa-możliwością ich kontrolowania podczas analizy, takie jak optymalizacja całego programu).  
  
 Rejestry RBX, RBP RDI, RSI, źródło, R12, R13, R14 i R15 są uznawane za nieulotnej i musi zostać zapisany i przywrócony przez funkcję używającą je.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencja wywoływania](../build/calling-convention.md)