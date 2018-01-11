---
title: "Stałe całkowite języka C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f851fe628b7ac69fe3d327c290881561219a011
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-integer-constants"></a>Stałe całkowite języka C
"Stała całkowita" jest dziesiętna (o podstawie 10), ósemkowy (podstawa 8) lub liczbą szesnastkową (podstawa 16), która reprezentuje wartością całkowitą. Stałe całkowite umożliwia reprezentują wartości całkowite, których nie można zmienić.  
  
## <a name="syntax"></a>Składnia  
 *stała całkowita*:  
 *decimal — stała liczba całkowita sufiks* opcjonalnych  
  
 *ósemkowe stała liczba całkowita sufiks* opcjonalnych  
  
 *szesnastkowy stała liczba całkowita sufiks* opcjonalnych  
  
 *decimal — stała*:  
 *cyfra różną od zera*  
  
 *cyfra dziesiętna — stała*  
  
 *ósemkowe stała*:  
 **0**  
  
 *ósemkowe stała ósemkowego*  
  
 *Stała liczba szesnastkowa*:  
 **0 x***cyfrę szesnastkową*   
  
 **0 X***cyfrę szesnastkową*   
  
 *Stała liczba szesnastkowa szesnastkowy cyfrowy*  
  
 *niezerowe cyfrowy*: jeden z  
 **1 2 3 4 5 6 7 8 9**  
  
 *ósemkowego*: jeden z  
 **0 1 2 3 4 5 6 7**  
  
 *cyfrę szesnastkową*: jeden z  
 **0 1 2 3 4 5 6 7 8 9**  
  
 **b c d e f**  
  
 **B C D E F**  
  
 *Liczba całkowita sufiks*:  
 *sufiks unsigned long sufiks* opcjonalnych  
  
 *sufiks unsigned long sufiks* opcjonalnych  
  
 *sufiks niepodpisane*: jeden z  
 **u U**  
  
 *sufiks Long*: jeden z  
 **l L**  
  
 *64-bitowa liczba całkowita sufiks*:  
 **komputerach 64**  
  
 Stałe całkowite są dodatnie, chyba że są poprzedzone znakiem minus (**-**). Znak minus jest interpretowany jako Jednoargumentowy operator negacji arytmetyczne. (Zobacz [jednoargumentowe operatory arytmetyczne](../c-language/unary-arithmetic-operators.md) informacji dotyczących tego operatora.)  
  
 Jeśli zaczyna się od stałej całkowitej **0 x** lub **0 X**, jest szesnastkową. Jeśli zaczyna się od cyfry **0**, jest ósemkowe. W przeciwnym razie jest przyjmowana dziesiętną.  
  
 Następujące wiersze są równoważne:  
  
```  
0x1C   /* = Hexadecimal representation for decimal 28 */  
034    /* = Octal representation for decimal 28 */  
```  
  
 Żadne znaki odstępu można oddzielić cyfr całkowitą wartością stałą. Poniższe przykłady pokazują prawidłowych stałych decimal, ósemkowe i szesnastkowe.  
  
```  
/* Decimal Constants */  
10  
132  
32179  
  
/* Octal Constants */  
012  
0204  
076663  
  
/* Hexadecimal Constants */  
0xa or 0xA  
0x84  
0x7dB3 or 0X7DB3  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe języka C](../c-language/c-constants.md)