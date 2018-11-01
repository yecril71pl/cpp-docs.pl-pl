---
title: Używanie funkcji atexit
ms.date: 11/04/2016
f1_keywords:
- atexit
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
ms.openlocfilehash: 06baba59b5765f853f081b34d73be28a187730ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637453"
---
# <a name="using-atexit"></a>Używanie funkcji atexit

Za pomocą [atexit](../c-runtime-library/reference/atexit.md) funkcji, można określić funkcji zakończenia przetwarzania, który jest wykonywany przed Kończenie działania programu. Nie statycznych obiektów globalnych zainicjowany przed wywołaniem do **atexit** zostaną zniszczone przed wykonywania funkcji zakończenia przetwarzania.

## <a name="see-also"></a>Zobacz także

[Dodatkowe zagadnienia dotyczące kończenia](../cpp/additional-termination-considerations.md)