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
ms.openlocfilehash: 7d9f39f7ce609ea06a2d991ac79c2b1151625bc1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384762"
---
# <a name="identifiers-in-primary-expressions"></a>Identyfikatory w wyrażeniach podstawowych
Identyfikatory mogą mieć typu całkowitego, **float**, `enum`, `struct`, **Unii**, tablica wskaźnika lub typ funkcji. Identyfikator jest podstawowym wyrażenie pod warunkiem, że jej został zadeklarowany jako wyznaczenie obiektu (w takim przypadku jest wartością l-value) lub funkcji (w takim przypadku jest oznaczeniem funkcji). Zobacz [wartości L i r wyrażenia](../c-language/l-value-and-r-value-expressions.md) definicję l wartość.  
  
 Wartość wskaźnika reprezentowany przez identyfikator tablicy nie jest zmienną, więc identyfikator tablicy nie formularza lewostronny operand operatora przypisania i dlatego nie można modyfikować wartości l.  
  
 Identyfikator zadeklarowano jako funkcja reprezentuje wskaźnik, którego wartość jest adresem funkcji. Wskaźnik dotyczy funkcji zwracającej wartość określonego typu. W związku z tym funkcja identyfikatory również nie mogą być l wartości w operacjach przypisania. Aby uzyskać więcej informacji, zobacz [identyfikatory](../c-language/c-identifiers.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia podstawowe języka C](../c-language/c-primary-expressions.md)