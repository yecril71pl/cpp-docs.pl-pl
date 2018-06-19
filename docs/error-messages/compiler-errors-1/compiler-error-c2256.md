---
title: C2256 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2256
dev_langs:
- C++
helpviewer_keywords:
- C2256
ms.assetid: 171fa2bc-8c72-49cd-afe5-d723b7acd3c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b2571d13d08d368bf974b0c283c7d676eab6b56
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169130"
---
# <a name="compiler-error-c2256"></a>C2256 błąd kompilatora
niedozwolone użycie zaprzyjaźnionego specyfikatora na "function"  
  
 Destruktor lub konstruktora nie można określić jako [friend](../../cpp/friend-cpp.md).  
  
 Poniższy przykład generuje C2256:  
  
```  
// C2256.cpp  
// compile with: /c  
class C {  
public:  
   friend ~C();   // C2256  
   ~C();   // OK  
};  
```