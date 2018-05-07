---
title: Kompilatora (poziom 2) ostrzeżenie C4307 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4307
dev_langs:
- C++
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52914fc5825bda5647308c006b853538f3d6225e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-2-c4307"></a>Kompilator C4307 ostrzegawcze (poziom 2)
"operator": przepełnienie stałej  
  
 Operator jest używany w wyrażeniu, którego wynikiem stałej całkowitej przepełnienia przestrzeń przydzielona dla niego. Użytkownik może być konieczne użycie typu większych dla stałej. A **podpisany int** ma wartość mniejszą niż `unsigned int` ponieważ **podpisany int** używa jeden bit do reprezentowania logowania.  
  
 Poniższy przykład generuje C4307:  
  
```  
// C4307.cpp  
// compile with: /W2  
int i = 2000000000 + 2000000000;   // C4307  
int j = (unsigned)2000000000 + 2000000000;   // OK  
  
int main()  
{  
}  
```