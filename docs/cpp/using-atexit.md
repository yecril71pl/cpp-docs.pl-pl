---
title: Używanie funkcji atexit | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- atexit
dev_langs:
- C++
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb0c89c34b5107326a961e874289d20cbd2385c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420970"
---
# <a name="using-atexit"></a>Używanie funkcji atexit
Z [atexit —](../c-runtime-library/reference/atexit.md) funkcji, można określić funkcji przetwarzania zakończenia, która wykonuje przed Kończenie działania programu. Nie statycznych obiektów globalnych zainicjowany przed wywołaniem do `atexit` zostaną zniszczone przed wykonywanie funkcji przetwarzania zakończenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodatkowe zagadnienia dotyczące kończenia](../cpp/additional-termination-considerations.md)