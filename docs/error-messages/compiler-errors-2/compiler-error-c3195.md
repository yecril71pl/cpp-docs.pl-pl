---
title: C3195 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3195
dev_langs:
- C++
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce3c51da68b971c34d651826a9c84974957ac46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3195"></a>C3195 błąd kompilatora
"operator": jest zarezerwowany i nie można użyć jako element członkowski typu klasy lub wartość ref. Operatory środowiska CLR lub WinRT musi być zdefiniowana przy użyciu słowa kluczowego "operator"  
  
Kompilator wykryto definicja operatora przy użyciu rozszerzeń zarządzanych dla składni języka C++. Należy użyć składni języka C++ dla operatorów.  
  
Poniższy przykład generuje C3195 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C3195.cpp  
// compile with: /clr /LD  
#using <mscorlib.dll>  
value struct V {  
   static V op_Addition(V v, int i);   // C3195  
   static V operator +(V v, char c);   // OK for new C++ syntax   
};  
```