---
title: C2007 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2007
dev_langs:
- C++
helpviewer_keywords:
- C2007
ms.assetid: ecd09d99-5036-408b-9e46-bc15488f049e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 159a4b8f9dffc4f6ee96b0bb1935682f9f6db281
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2007"></a>C2007 błąd kompilatora
\#Zdefiniuj składni  
  
 Identyfikator nie jest umieszczany po `#define`. Aby rozwiązać problem, należy użyć identyfikatora.  
  
 Poniższy przykład generuje C2007:  
  
```  
// C2007.cpp  
#define   // C2007  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2007b.cpp  
// compile with: /c  
#define true 1  
```