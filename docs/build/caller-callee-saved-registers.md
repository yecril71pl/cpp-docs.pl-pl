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
ms.openlocfilehash: e8e877387dbb5b0be865e11017a3ac71a0c38faa
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707658"
---
# <a name="callercallee-saved-registers"></a>Zapisane rejestrowania wywołującego/wywoływanego

Rejestry RAX RCX, RDX, R8, R9, R10, R11 są traktowane jako nietrwałe oraz muszą być rozważone zniszczona na wywołania funkcji (chyba że inaczej bezpieczeństwa sprawdzalnych podczas analizy, takie jak optymalizacja całego programu).

Rejestrów RBX RBP, RDI, RSI, RSP, R12, R13, R14 i R15 są traktowane jako trwałej i muszą zostać zapisane i przywrócone przez funkcję używającą je.

## <a name="see-also"></a>Zobacz też

[Konwencja wywoływania](../build/calling-convention.md)