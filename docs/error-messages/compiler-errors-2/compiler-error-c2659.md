---
title: C2659 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2659
dev_langs:
- C++
helpviewer_keywords:
- C2659
ms.assetid: b0883600-4d27-4ca7-a931-8ca6bd48654d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b01afeaaa82ed772f5d812f36b3de0aac24679a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2659"></a>C2659 błąd kompilatora
'operator' : działa jako lewy operand  
  
 Funkcja była po lewej stronie określonego operatora. Najczęstszą przyczyną tego błędu jest to, że kompilator przeanalizował identyfikator po lewej stronie operatora jako funkcję, podczas gdy programista chciał, aby była to zmienna. Aby uzyskać więcej informacji, zobacz Wikipedia artykułu [najbardziej vexing analizy](http://en.wikipedia.org/wiki/Most_vexing_parse). Ten przykład przedstawia deklarację funkcji i definicję zmiennej, które łatwo pomylić:  
  
```  
// C2659a.cpp  
// Compile using: cl /W4 /EHsc C2659a.cpp  
#include <string>  
using namespace std;  
  
int main()   
{  
   string string1(); // string1 is a function returning string  
   string string2{}; // string2 is a string initialized to empty   
  
   string1 = "String 1"; // C2659  
   string2 = "String 2";  
}  
```  
  
 Aby rozwiązać ten problem, zmień deklarację identyfikatora, tak aby nie był analizowany jako deklaracja funkcji.  
  
 Błąd C2659 może również wystąpić, gdy funkcja ma typ, którego nie można używać w wyrażeniu po lewej stronie określonego operatora. Ten przykład generuje C2659, gdy kod przypisuje wskaźnik funkcji do funkcji:  
  
```  
// C2659b.cpp  
// Compile using: cl /W4 /EHsc C2659b.cpp  
int func0(void) { return 42; }  
int (*func1)(void);  
  
int main()  
{  
   func1 = func0;  
   func0 = func1; // C2659  
}  
```