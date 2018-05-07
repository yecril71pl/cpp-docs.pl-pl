---
title: C2555 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2555
dev_langs:
- C++
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d2d1a710177e2c8c72b0afeff662dddf1c22ef5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2555"></a>C2555 błąd kompilatora
"class1::function1": przesłanianie wirtualnej funkcji zwracany typ różni się i nie jest kowariantne z "class2::function2"  
  
 Funkcję wirtualną i pochodne funkcja zastępowanie mają listy parametrów identyczne, ale różne typy zwracane. Zastępowanie funkcji w klasie pochodnej nie może się różnić od w klasie podstawowej tylko przez jej typu zwracanego funkcji wirtualnej.  
  
 Aby rozwiązać ten problem, należy rzutować zwracana wartość po wywołaniu funkcji wirtualnej.  
  
 Ten błąd może również sprawdzić, czy skompiluj z/CLR.   Na przykład Visual C++ odpowiednikiem następujące oświadczenie C#:  
  
```  
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);  
```  
  
 is  
  
```  
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];  
```  
  
 Aby uzyskać więcej informacji o C2555 zobacz artykuł bazy wiedzy Knowledge Base Q240862.  
  
 Poniższy przykład generuje C2555:  
  
```  
// C2555.cpp  
// compile with: /c  
struct X {  
   virtual void func();  
};  
struct Y : X {  
   char func();  // C2555  
   void func2();   // OK  
};  
```