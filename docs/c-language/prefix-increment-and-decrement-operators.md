---
title: "Prefiksów inkrementacji i dekrementacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- increment operators, types of
- decrement operators, syntax
- decrement operators
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84d8c3f5a1b43fdec5554003e32db4f23b4f0406
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="prefix-increment-and-decrement-operators"></a>Operatory prefiksów inkrementacji i dekrementacji
Operatory jednoargumentowe (`++` i  **--** ) są nazywane "prefiksu" przyrostu lub operatory dekrementacji, gdy operatory inkrementacji lub dekrementacji pojawią się przed argument. Operatory przyrostka inkrementacji i dekrementacji ma wyższy priorytet niż prefiksów inkrementacji i dekrementacji. Argument musi być typu całkowitego, zmiennoprzecinkową lub wskaźnika typu i musi być wyrażeniem modyfikowalną l wartość (wyrażenia bez **const** atrybutu). Wynik jest wartością l-value.  
  
 Po wyświetleniu przed jej argument operacji operatora operand jest zwiększone lub zmniejszone, a jego nowa wartość jest wynikiem wyrażenia.  
  
 Argument typu całkowitą lub zmiennoprzecinkową jest zwiększone lub zmniejszone przez całkowitą wartość 1. Typ wyniku jest taki sam jak typ argumentu. Argument typu wskaźnika jest zwiększone lub zmniejszone według rozmiaru obiektu, który spełnia. Wskazuje zwiększany wskaźnik do następnego obiektu. zmniejszona wskaźnik wskazuje poprzedniego obiektu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono operator jednoargumentowy dekrementacja prefiksu:  
  
```  
if( line[--i] != '\n' )  
    return;  
```  
  
 W tym przykładzie zmienna `i` jest zmniejszana, zanim zostanie on użyty jako indeks dolny do `line`.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory jednoargumentowe języka C](../c-language/c-unary-operators.md)