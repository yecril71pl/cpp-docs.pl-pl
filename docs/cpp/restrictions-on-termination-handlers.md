---
title: "Ograniczenia dotyczące programu obsługi zakończenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 71486b167f4e9939d4913b3660ed3513dc02b8f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="restrictions-on-termination-handlers"></a>Ograniczenia dotyczące programu obsługi zakończenia
Nie można użyć `goto` instrukcji, aby przejść do `__try` blok instrukcji lub `__finally` blok instrukcji. Zamiast tego należy wprowadzić bloku instrukcji za pomocą przepływu sterowania. (Można jednak przechodzić z `__try` blok instrukcji.) Ponadto nie można zagnieżdżać obsługi wyjątków lub programu obsługi zakończenia wewnątrz `__finally` bloku.  
  
 Ponadto niektóre rodzaje kodu w programu obsługi zakończenia utworzyć wątpliwa wyników, należy ich używać ostrożnie, jeśli w ogóle. Jedna jest `goto` instrukcji, która przechodzi poza `__finally` blok instrukcji. Jeśli blok jest wykonywane w ramach normalnych zakończenia, nic nietypowe się nie dzieje. Ale jeśli system jest odwijanie stosu, który przejmuje odwijaniem przerywa działanie i bieżącej funkcji kontroli tak, jakby nie było żadnych przerwania pracy.  
  
 A `return` instrukcja wewnątrz `__finally` blok instrukcji przedstawia informacje o około samej sytuacji. Zwraca sterowania do bezpośredniego obiektu wywołującego funkcji zawierające programu obsługi zakończenia. Jeśli system został odwijanie stosu, ten proces jest zatrzymywane, a program będzie kontynuowane tak, jakby nie był nie wystąpił wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)   
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)