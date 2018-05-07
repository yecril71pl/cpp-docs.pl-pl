---
title: C3298 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3298
dev_langs:
- C++
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a67e155fb6cf0eab1ea085839d075d4d835de101
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3298"></a>C3298 błąd kompilatora
"constraint_1": nie można użyć "constraint_2" jako ograniczenia ponieważ "constraint_2" ma ograniczenie ref oraz "constraint_1" ma wartość ograniczenia  
  
 Nie można określić właściwości wykluczają się wzajemnie ograniczenia. Na przykład parametr typu generycznego nie można ograniczyć do typu wartości i typ referencyjny.  
  
 Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu ogólnego (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3298.  
  
```  
// C3298.cpp  
// compile with: /clr /c   
generic<class T, class U>  
where T : ref class  
where U : T, value class   // C3298  
public ref struct R {};  
```