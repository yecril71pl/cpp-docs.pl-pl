---
title: C3002 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3002
dev_langs:
- C++
helpviewer_keywords:
- C3002
ms.assetid: 2d4241a7-c8eb-4d43-a128-dca255d137bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e69b2eede8e186347f7c3812901ef3c1dcc01495
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243277"
---
# <a name="compiler-error-c3002"></a>C3002 błąd kompilatora
"nazwa1 nazwa2": wielokrotne nazwy dyrektyw OpenMP  
  
 Wiele dyrektywy nazwy są niedozwolone.  
  
 Poniższy przykład generuje C3002:  
  
```  
// C3002.c  
// compile with: /openmp  
int main()  
{  
   #pragma omp parallel single   // C3002  
}  
```