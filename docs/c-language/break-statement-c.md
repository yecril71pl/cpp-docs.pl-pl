---
title: Podziel Statement (C) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: break
dev_langs: C++
helpviewer_keywords: break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a180c88fc71e4786e8512bc26421825132611ed4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="break-statement-c"></a>break — instrukcja (C)
`break` Instrukcji kończy wykonywanie najbliższej otaczającej `do`, `for`, `switch`, lub `while` instrukcji, w której znajduje się. Kontrola przechodzi do instrukcji następującej instrukcji zakończone.  
  
## <a name="syntax"></a>Składnia  
 *Instrukcja skok*:  
 `break;`  
  
 `break` Często używana jest instrukcja o zakończeniu przetwarzania konkretnego przypadku w `switch` instrukcji. Brak otaczającej iteracyjne lub `switch` instrukcji generuje błąd.  
  
 W zagnieżdżonych instrukcjach `break` instrukcji kończy tylko `do`, `for`, `switch`, lub `while` instrukcji ograniczający natychmiast go. Można użyć `return` lub `goto` instrukcji do przekazywania kontroli w innym miejscu struktury zagnieżdżone.  
  
 W tym przykładzie przedstawiono `break` instrukcji:  
  
```  
#include <stdio.h>  
int main() {  
   char c;  
   for(;;) {  
      printf_s( "\nPress any key, Q to quit: " );  
  
      // Convert to character value  
      scanf_s("%c", &c);  
      if (c == 'Q')  
          break;  
   }  
} // Loop exits only when 'Q' is pressed  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcja BREAK](../cpp/break-statement-cpp.md)