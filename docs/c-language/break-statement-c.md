---
title: Podziel Statement (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- break
dev_langs:
- C++
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 194e4c836f0423e20bb747cc6c3b06645c38a5fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381353"
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