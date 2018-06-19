---
title: Kompilatora (poziom 1) ostrzeżenie C4717 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4717
dev_langs:
- C++
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa953d8d41003ff53e721671845c1ddee26da640
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282431"
---
# <a name="compiler-warning-level-1-c4717"></a>Kompilator C4717 ostrzegawcze (poziom 1)
"Funkcja": cykliczne we wszystkich ścieżkach kontroli, funkcja spowoduje przepełnienie stosu w czasie wykonywania  
  
 Co ścieżka przez funkcję zawiera wywołanie funkcji. Ponieważ nie istnieje żaden sposób, aby zakończyć działanie funkcji bez pierwsze wywołanie, sama rekursywnie, funkcja nigdy nie zostanie zakończona.  
  
 Poniższy przykład generuje C4717:  
  
```  
// C4717.cpp  
// compile with: /W1 /c  
// C4717 expected  
int func(int x) {  
   if (x > 1)  
      return func(x - 1); // recursive call  
   else {  
      int y = func(0) + 1; // recursive call  
      return y;  
   }  
}  
  
int main(){  
   func(1);  
}  
```