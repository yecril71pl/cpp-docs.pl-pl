---
title: "Kompilatora (poziom 4) ostrzeżenie C4127 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4127
dev_langs: C++
helpviewer_keywords: C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d1a5bbd86b6197907f043478df225dceb79679f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4127"></a>Kompilator C4127 ostrzegawcze (poziom 4)
wyrażenie warunkowe jest stałą  
  
 Kontrolowanie wyrażenie `if` instrukcji lub `while` pętli jest stałą. Ze względu na ich typowe obciążenie idiomatyczne trivial stałe, takich jak 1 lub `true` nie wyzwalają ostrzeżenie, chyba że są one wynik operacji w wyrażeniu. Jeśli wyrażenie kontrolowanie `while` pętli jest stałą, ponieważ opuszcza pętlę w środku, rozważ zastąpienie `while` pętli z `for` pętli. Można pominąć inicjowanie, zakończenia testu i pętla przyrost `for` pętli, co powoduje, że pętli nieskończony, podobnie jak `while(1)`, a pętla może wyjść z treści `for` instrukcji.  
  
 Poniższy przykład przedstawia dwa sposoby C4127 jest generowana i przedstawia sposób użycia dla pętli uniknąć tego ostrzeżenia:  
  
```  
// C4127.cpp  
// compile with: /W4  
#include <stdio.h>  
int main() {  
   if (1 == 1) {}   // C4127  
   while (42) { break; }   // C4127  
  
   // OK  
   for ( ; ; ) {  
      printf("test\n");  
      break;  
   }  
}  
```