---
title: C3068 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3068
dev_langs:
- C++
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f378a60c79defed4fb1738515ca5b65b2851056
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3068"></a>C3068 błąd kompilatora
"Funkcja": funkcja "naked" nie może zawierać obiekty, które wymagałyby rozwinięcia gdy wystąpi wyjątek C++  
  
 Kompilator nie może wykonać odwijanie stosu w [naked](../../cpp/naked-cpp.md) funkcja, która zgłosiła wyjątek, ponieważ tymczasowy obiekt został utworzony w funkcji i C++, obsługa wyjątków ([/ehsc](../../build/reference/eh-exception-handling-model.md)) został określony.  
  
 Aby rozwiązać ten problem, wykonaj co najmniej jedną z następujących czynności:  
  
-   Kompiluje z/ehsc.  
  
-   Nie oznaczaj funkcji jako `naked`.  
  
-   Nie należy tworzyć tymczasowego obiektu w funkcji.  
  
 Jeśli funkcja tworzy tymczasowy obiekt na stosie, funkcja zwraca wyjątek, a obsługa wyjątków C++ jest włączona, kompilator wyczyścić stosu, jeśli jest zgłaszany wyjątek.  
  
 Gdy jest zgłaszany wyjątek, kod wywołuje prologu wygenerowany przez kompilator i epilogu, które nie są obecne w funkcji naked, jest wykonywane dla funkcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3068:  
  
```  
// C3068.cpp  
// compile with: /EHsc  
// processor: x86  
class A {  
public:  
   A(){}  
   ~A(){}  
};  
  
void b(A){}  
  
__declspec(naked) void c() {  
   b(A());   // C3068   
};  
```