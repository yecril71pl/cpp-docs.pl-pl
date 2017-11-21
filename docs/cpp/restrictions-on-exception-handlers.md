---
title: "Ograniczenia dotyczące obsługi wyjątków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 42207a9bc1e9a355e6785a609ab0b130be063d55
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="restrictions-on-exception-handlers"></a>Ograniczenia dotyczące obsługi wyjątków
Główna ograniczenie używania programów obsługi wyjątków w kodzie jest, że nie można użyć `goto` instrukcji, aby przejść do `__try` blok instrukcji. Zamiast tego należy wprowadzić bloku instrukcji za pomocą przepływu sterowania. Można przejść z `__try` instrukcji blokować i zagnieździć programy obsługi wyjątków, wybierz polecenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie programu do obsługi wyjątków](../cpp/writing-an-exception-handler.md)   
 [(C/C++) obsługi wyjątków strukturalnych](../cpp/structured-exception-handling-c-cpp.md)