---
title: C2663 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2663
dev_langs:
- C++
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f39f516b32aaf1159d47726d01623e253ee8b383
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2663"></a>C2663 błąd kompilatora
"Funkcja": przeciążenia numer ma prawne konwersji dla wskaźnika "this"  
  
 Nie można przekonwertować kompilator `this` do dowolnej wersji przeciążonej funkcji członkowskiej.  
  
 Ten błąd może być spowodowany przez wywołanie niż`const` funkcji członkowskiej na `const` obiektu.  Możliwe rozwiązania:  
  
1.  Usuń `const` z deklaracji obiektu.  
  
2.  Dodaj `const` do jednego przeciążenia funkcji Członkowskich.  
  
 Poniższy przykład generuje C2663:  
  
```  
// C2663.cpp  
struct C {  
   void f() volatile {}  
   void f() {}  
};  
  
struct D {  
   void f() volatile;  
   void f() const {}  
};  
  
const C *pcc;  
const D *pcd;  
  
int main() {  
   pcc->f();    // C2663  
   pcd->f();    // OK  
}  
```