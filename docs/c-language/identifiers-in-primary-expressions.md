---
title: Identyfikatory w wyrażeniach podstawowych
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
ms.openlocfilehash: 053720bcdf635a7e09363712259b558d93a2972c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233089"
---
# <a name="identifiers-in-primary-expressions"></a>Identyfikatory w wyrażeniach podstawowych

Identyfikatory mogą mieć typ całkowity, **zmiennoprzecinkowy**, `enum`, `struct`, **Union**, Array, Pointer lub Function. Identyfikator jest wyrażeniem podstawowym, pod warunkiem że został zadeklarowany jako wyznaczanie obiektu (w tym przypadku jest to wartość l) lub jako funkcja (w tym przypadku jest to oznaczenie funkcji). Patrz [wyrażenia wartości l i R](../c-language/l-value-and-r-value-expressions.md) dla definicji l-wartości.

Wartość wskaźnika reprezentowana przez identyfikator tablicy nie jest zmienną, więc identyfikator tablicy nie może tworzyć operandu po lewej stronie przypisania i w związku z tym nie jest to modyfikowalna wartość l.

Identyfikator zadeklarowany jako funkcja reprezentuje wskaźnik, którego wartość jest adresem funkcji. Wskaźnik odnosi się do funkcji zwracającej wartość określonego typu. W ten sposób identyfikatory funkcji nie mogą również zawierać wartości l w operacjach przypisywania. Aby uzyskać więcej informacji, zobacz temat [Identyfikatory](../c-language/c-identifiers.md).

## <a name="see-also"></a>Zobacz też

[Wyrażenia podstawowe języka C](../c-language/c-primary-expressions.md)
