---
title: "Zapisane rejestrowania wywołującego wywoływanego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ebdcf30ea56587b71015a04b5e514dd9ff21aeba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="callercallee-saved-registers"></a>Zapisane rejestrowania wywołującego/wywoływanego
Rejestruje RAX, RCX, RDX, R8, R9, R10, R11 są traktowane jako nietrwałe i muszą być traktowane jako zniszczona na wywołania funkcji (chyba że w przeciwnym razie bezpieczeństwa-możliwością ich kontrolowania podczas analizy, takie jak optymalizacja całego programu).  
  
 Rejestry RBX, RBP RDI, RSI, źródło, R12, R13, R14 i R15 są uznawane za nieulotnej i musi zostać zapisany i przywrócony przez funkcję używającą je.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencja wywoływania](../build/calling-convention.md)