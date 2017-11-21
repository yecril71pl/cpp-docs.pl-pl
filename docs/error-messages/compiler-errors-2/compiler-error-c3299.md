---
title: "C3299 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3299
dev_langs: C++
helpviewer_keywords: C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3612762f397914b6058516db7d8f56b840873c1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3299"></a>C3299 błąd kompilatora
"member_function": nie można określić ograniczeń, są one dziedziczone z metody podstawowej  
  
 W przypadku przesłaniania funkcji członkowskiej ogólnego, nie można określić ograniczenia klauzule (powtarzający się ograniczenia oznacza, że ograniczenia nie są dziedziczone).  
  
 Klauzule ograniczenia w funkcji ogólnych, które są zastępowanie będą dziedziczone.  
  
 Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu ogólnego (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3299.  
  
```  
// C3299.cpp  
// compile with: /clr /c  
public ref struct R {  
   generic<class T>   
   where T : R  
   virtual void f();  
};  
  
public ref struct S : R {  
   generic<class T>   
   where T : R   // C3299  
   virtual void f() override;  
};  
```