---
title: Identyfikatory w wyrażeniach podstawowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53498d5a1402d1953df93ea0f2d7c723218174c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079040"
---
# <a name="identifiers-in-primary-expressions"></a>Identyfikatory w wyrażeniach podstawowych

Identyfikatory mogą mieć całkowitym, **float**, `enum`, `struct`, **Unii**, tablicy, wskaźnika, lub typu funkcji. Identyfikator jest wyrażeniem podstawowym, pod warunkiem, że został zadeklarowany jako wyznaczanie obiektu (w takim przypadku jest to wartość l) lub funkcji (w takim przypadku jest oznaczeniem funkcji). Zobacz [wyrażenia wartości L i r](../c-language/l-value-and-r-value-expressions.md) definicję l wartością.

Wartość wskaźnika, reprezentowane przez identyfikator tablicy nie jest to zmienna, dzięki czemu identyfikatora tablicy nie formularza lewostronny operand operatora przypisania i dlatego nie jest modyfikowalną l wartością.

Identyfikator zadeklarowany jako funkcja reprezentuje wskaźnik, którego wartość jest adres funkcji. Wskaźnik adresów, funkcja zwraca wartość o określonym typie. W związku z tym, funkcja identyfikatorów także nie może być l wartości, w operacji przypisania. Aby uzyskać więcej informacji, zobacz [identyfikatory](../c-language/c-identifiers.md).

## <a name="see-also"></a>Zobacz też

[Wyrażenia podstawowe języka C](../c-language/c-primary-expressions.md)