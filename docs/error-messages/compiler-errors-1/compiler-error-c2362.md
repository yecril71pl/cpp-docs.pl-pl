---
title: C2362 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2362
dev_langs:
- C++
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53b0b77930acba6ecf2d0f3c6748ba52e9b28e0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2362"></a>C2362 błąd kompilatora
Inicjalizacja "identyfikatora" jest pomijana przy "etykieta goto"  
  
 Podczas kompilowania za pomocą [/Za](../../build/reference/za-ze-disable-language-extensions.md), przeskakiwanie do etykiet uniemożliwia zainicjowanie identyfikator.  
  
 Nie można przeskoczyć poza deklaracji z inicjatora, chyba że deklaracja jest ujęte w blok nie zostanie wprowadzona lub zmiennej został już zainicjowany.  
  
 Poniższy przykład generuje C2326:  
  
```  
// C2362.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   int i = 1;      // C2362, initialization skipped  
label1:;  
}  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2362b.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   {  
      int j = 1;   // OK, this block is never entered  
   }  
label1:;  
}  
```