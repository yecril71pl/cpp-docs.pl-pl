---
title: "Identyfikatory w wyrażeniach podstawowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ce62a6ad0f0cb36678de0756d77155769393f760
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="identifiers-in-primary-expressions"></a>Identyfikatory w wyrażeniach podstawowych
Identyfikatory mogą mieć typu całkowitego, **float**, `enum`, `struct`, **Unii**, tablica wskaźnika lub typ funkcji. Identyfikator jest podstawowym wyrażenie pod warunkiem, że jej został zadeklarowany jako wyznaczenie obiektu (w takim przypadku jest wartością l-value) lub funkcji (w takim przypadku jest oznaczeniem funkcji). Zobacz [wartości L i r wyrażenia](../c-language/l-value-and-r-value-expressions.md) definicję l wartość.  
  
 Wartość wskaźnika reprezentowany przez identyfikator tablicy nie jest zmienną, więc identyfikator tablicy nie formularza lewostronny operand operatora przypisania i dlatego nie można modyfikować wartości l.  
  
 Identyfikator zadeklarowano jako funkcja reprezentuje wskaźnik, którego wartość jest adresem funkcji. Wskaźnik dotyczy funkcji zwracającej wartość określonego typu. W związku z tym funkcja identyfikatory również nie mogą być l wartości w operacjach przypisania. Aby uzyskać więcej informacji, zobacz [identyfikatory](../c-language/c-identifiers.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia podstawowe języka C](../c-language/c-primary-expressions.md)