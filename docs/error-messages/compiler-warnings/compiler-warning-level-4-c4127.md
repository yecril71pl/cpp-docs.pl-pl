---
title: Kompilatora (poziom 4) ostrzeżenie C4127 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4127
dev_langs:
- C++
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c98b2eb42cfc66c27faf74c3d6e46e981851a0a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293650"
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