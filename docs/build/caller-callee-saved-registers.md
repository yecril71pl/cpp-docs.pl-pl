---
title: Zapisane rejestrowania wywołującego wywoływanego
ms.date: 11/04/2016
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
ms.openlocfilehash: f34fbfff8e6c61b5d568c073f6b7da2a12e34535
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654704"
---
# <a name="callercallee-saved-registers"></a>Zapisane rejestrowania wywołującego/wywoływanego

Rejestry RAX RCX, RDX, R8, R9, R10, R11 są traktowane jako nietrwałe oraz muszą być rozważone zniszczona na wywołania funkcji (chyba że inaczej bezpieczeństwa sprawdzalnych podczas analizy, takie jak optymalizacja całego programu).

Rejestrów RBX RBP, RDI, RSI, RSP, R12, R13, R14 i R15 są traktowane jako trwałej i muszą zostać zapisane i przywrócone przez funkcję używającą je.

## <a name="see-also"></a>Zobacz też

[Konwencja wywoływania](../build/calling-convention.md)