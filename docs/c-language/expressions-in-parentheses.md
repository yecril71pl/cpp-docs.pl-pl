---
title: "Wyrażenia w nawiasach | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- parentheses
- expression evaluation, evaluation order
- expressions [C++], evaluating
- parentheses, expressions
ms.assetid: b8636147-6982-408c-9e64-29e40678ee43
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c09209a323a06f883a54e7ecaec17c55a3bc6205
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="expressions-in-parentheses"></a>Wyrażenia w nawiasach
Wszelkie operand można ująć w nawiasach bez zmiany typu lub wartości wyrażenie w nawiasach. Na przykład w wyrażeniu:  
  
```  
( 10 + 5 ) / 5  
```  
  
 nawiasy otaczające `10 + 5` oznaczają, że wartość `10 + 5` jest szacowana jako pierwsza i staje się lewy operand podziału (**/**) operatora. Wynik `( 10 + 5 ) / 5` to 3. Bez nawiasów `10 + 5 / 5` oceni do 11.  
  
 Mimo że nawiasy wpływa na sposób argumenty operacji są pogrupowane w wyrażeniu, nie mogą gwarantować określonej kolejności szacowania we wszystkich przypadkach. Na przykład nawiasy ani grupowania od lewej do prawej z następującym wyrażeniem gwarantuje, jakie wartości `i` będzie w jednym zakresie:  
  
```  
( i++ +1 ) * ( 2 + i )  
```  
  
 Kompilator jest bezpłatna do oceny partnerami mnożenia w dowolnej kolejności. Jeśli wartość początkowa `i` wynosi zero, można obliczyć wyrażenia całego jako tych dwóch instrukcji:  
  
```  
( 0 + 1 + 1 ) * ( 2 + 1 )   
( 0 + 1 + 1 ) * ( 2 + 0 )  
```  
  
 Wyjątki wynikające z efekty uboczne, omówiono w [efekty uboczne](../c-language/side-effects.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia podstawowe języka C](../c-language/c-primary-expressions.md)