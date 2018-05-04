---
title: Zapisane rejestrowania wywołującego wywoływanego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f65e88c8609d6a2097e9e54c3f52cbd27dce36d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="callercallee-saved-registers"></a>Zapisane rejestrowania wywołującego/wywoływanego
Rejestruje RAX, RCX, RDX, R8, R9, R10, R11 są traktowane jako nietrwałe i muszą być traktowane jako zniszczona na wywołania funkcji (chyba że w przeciwnym razie bezpieczeństwa-możliwością ich kontrolowania podczas analizy, takie jak optymalizacja całego programu).  
  
 Rejestry RBX, RBP RDI, RSI, źródło, R12, R13, R14 i R15 są uznawane za nieulotnej i musi zostać zapisany i przywrócony przez funkcję używającą je.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencja wywoływania](../build/calling-convention.md)