---
title: C2776 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2776
dev_langs:
- C++
helpviewer_keywords:
- C2776
ms.assetid: 9d80addc-62c7-40fc-a2cc-60303abb87df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afbf3c48e5445d101408c2539cc077071b639044
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233771"
---
# <a name="compiler-error-c2776"></a>C2776 błąd kompilatora
tylko jedna metoda "get" może być określona dla właściwości  
  
 Można określić tylko jedno `get` działać w [właściwości](../../cpp/property-cpp.md) rozszerzonych atrybutów. Ten błąd występuje, gdy wiele `get` są określone funkcje.  
  
 Poniższy przykład generuje C2776:  
  
```  
// C2776.cpp  
struct A {  
   __declspec(property(get=GetProp,get=GetPropToo))  
   // try the following line instead  
   // __declspec(property(get=GetProp))  
      int prop;   // C2776  
   int GetProp(void);  
   int GetPropToo(void);  
};  
```