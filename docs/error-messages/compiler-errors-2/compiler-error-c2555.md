---
title: "C2555 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2555
dev_langs:
- C++
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c66b464ac38a46716fbed972939feef1273ad03d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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