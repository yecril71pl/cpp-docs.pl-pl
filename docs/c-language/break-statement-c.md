---
title: Przerwij Statement (C) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: aeec33d61f21c34e52d582ebc3c0ef7313bb511f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755037"
---
# <a name="break-statement-c"></a>break — instrukcja (C)
`break` Instrukcja kończy wykonywanie najbliższej otaczającej `do`, `for`, `switch`, lub `while` instrukcji, w której występuje. Kontrola przechodzi do instrukcji następującej instrukcji zakończone.  
  
## <a name="syntax"></a>Składnia

*Instrukcja skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przerwij;**
  
`break` Instrukcji jest często używany do zakończenia przetwarzania konkretnej wielkość liter w obrębie `switch` instrukcji. Brak otaczającego iteracji lub `switch` instrukcja generuje błąd.  
  
W obrębie zagnieżdżonych instrukcji `break` kończy się tylko `do`, `for`, `switch`, lub `while` instrukcji, która bezpośrednio ją obejmuje. Możesz użyć `return` lub `goto` instrukcję, aby przekazać sterowanie w innym miejscu poza struktury zagnieżdżonej.  
  
Ten przykład ilustruje `break` instrukcji:  
  
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