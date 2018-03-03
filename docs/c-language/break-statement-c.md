---
title: Podziel Statement (C) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- break
dev_langs:
- C++
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 648ab54d23e22d6c6aae3022593440cb892c1ea9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
 [break, instrukcja](../cpp/break-statement-cpp.md)