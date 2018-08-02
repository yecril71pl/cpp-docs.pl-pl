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
ms.openlocfilehash: f4acd81a5420f9fe2685e7570f26fea61691b845
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467407"
---
# <a name="using-atexit"></a>Używanie funkcji atexit
Za pomocą [atexit](../c-runtime-library/reference/atexit.md) funkcji, można określić funkcji zakończenia przetwarzania, który jest wykonywany przed Kończenie działania programu. Nie statycznych obiektów globalnych zainicjowany przed wywołaniem do **atexit** zostaną zniszczone przed wykonywania funkcji zakończenia przetwarzania.  
  
## <a name="see-also"></a>Zobacz także  
 [Dodatkowe zagadnienia dotyczące kończenia](../cpp/additional-termination-considerations.md)