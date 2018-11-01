---
title: Identyfikatory w wyrażeniach podstawowych
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
ms.openlocfilehash: 49b5aa2fd895d96f58e24029b86c8b31c24a7758
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499727"
---
# <a name="identifiers-in-primary-expressions"></a>Identyfikatory w wyrażeniach podstawowych

Identyfikatory mogą mieć całkowitym, **float**, `enum`, `struct`, **Unii**, tablicy, wskaźnika, lub typu funkcji. Identyfikator jest wyrażeniem podstawowym, pod warunkiem, że został zadeklarowany jako wyznaczanie obiektu (w takim przypadku jest to wartość l) lub funkcji (w takim przypadku jest oznaczeniem funkcji). Zobacz [wyrażenia wartości L i r](../c-language/l-value-and-r-value-expressions.md) definicję l wartością.

Wartość wskaźnika, reprezentowane przez identyfikator tablicy nie jest to zmienna, dzięki czemu identyfikatora tablicy nie formularza lewostronny operand operatora przypisania i dlatego nie jest modyfikowalną l wartością.

Identyfikator zadeklarowany jako funkcja reprezentuje wskaźnik, którego wartość jest adres funkcji. Wskaźnik adresów, funkcja zwraca wartość o określonym typie. W związku z tym, funkcja identyfikatorów także nie może być l wartości, w operacji przypisania. Aby uzyskać więcej informacji, zobacz [identyfikatory](../c-language/c-identifiers.md).

## <a name="see-also"></a>Zobacz też

[Wyrażenia podstawowe języka C](../c-language/c-primary-expressions.md)