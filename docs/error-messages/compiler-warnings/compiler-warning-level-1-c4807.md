---
title: "Kompilatora (poziom 1) ostrzeżenie C4807 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4807
dev_langs: C++
helpviewer_keywords: C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5052e82ceb7a426cfa4ec685491285f33886786b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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