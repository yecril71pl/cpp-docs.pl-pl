---
title: C2258 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2258
dev_langs:
- C++
helpviewer_keywords:
- C2258
ms.assetid: 105eaa87-befb-4ecb-9a3f-e09e14d2f5bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d0e976edda871646a5bfa6c994d303a276b2f4d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167954"
---
# <a name="compiler-error-c2258"></a>C2258 błąd kompilatora
Niedozwolona czysta składnia, musi być "= 0"  
  
 Czystej funkcji wirtualnej jest zadeklarowana z niepoprawną składnię.  
  
 Poniższy przykład generuje C2258:  
  
```  
// C2258.cpp  
// compile with: /c  
class A {  
public:  
   void virtual func1() = 1; // C2258  
   void virtual func2() = 0;   // OK  
};  
```