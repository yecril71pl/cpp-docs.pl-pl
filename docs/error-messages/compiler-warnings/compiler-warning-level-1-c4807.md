---
title: Kompilatora (poziom 1) ostrzeżenie C4807 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4807
dev_langs:
- C++
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22710ee2b46a270e46aed7c043d4d988fcfaed62
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4807"></a>Kompilator C4807 ostrzegawcze (poziom 1)
"operacji": niebezpieczne połączenie typu "type" i podpisem bitfield typu "type"  
  
 To ostrzeżenie jest generowany, gdy porównanie pola bitowego podpisem jeden bit do `bool` zmiennej. Ponieważ pola bitowego jeden bit, podpisem może zawierać tylko wartości -1 lub 0, jest niebezpieczne porównania jej `bool`. Ostrzeżenia nie są generowane dotyczące `bool` i jeden bit, bez znaku pola bitów ponieważ są one takie same jak `bool` i mogą zawierać tylko 0 lub 1.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4807:  
  
```  
// C4807.cpp  
// compile with: /W1  
typedef struct bitfield {  
   signed mybit : 1;  
} mybitfield;  
  
int main() {  
   mybitfield bf;  
   bool b = true;  
  
   // try..  
   // int b = true;  
  
   bf.mybit = -1;  
   if (b == bf.mybit) {   // C4807  
      b = false;  
   }  
}  
```