---
title: "C2099 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2099
dev_langs: C++
helpviewer_keywords: C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44e5faccc28877793aa42c5fb765e6d21eb19a1b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2099"></a>C2099 błąd kompilatora
Inicjator nie jest stałą  
  
 Ten błąd jest wystawiane tylko przez kompilator C i występuje tylko w przypadku zmiennych nie automatyczne.  Kompilator inicjuje zmienne nieautomatyczne podczas uruchamiania programu i wartości, które są one inicjowane z musi być stałą.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2099.  
  
```  
// C2099.c  
int j;  
int *p;  
j = *p;   // C2099 *p is not a constant  
```  
  
## <a name="example"></a>Przykład  
 C2099 może również wystąpić, gdy kompilator nie będzie mógł wykonywać składania stałej w wyrażeniu w obszarze **/FP: strict** ponieważ zmiennoprzecinkowy ustawienia środowiska precision (zobacz [_controlfp_s —](../../c-runtime-library/reference/controlfp-s.md) dla więcej informacji) może się różnić od kompilacji do czasu wykonywania.  
  
 Gdy jest to stała składania kończy się niepowodzeniem, kompilator wywołuje dynamiczna Inicjalizacja, co jest niedozwolone w C.  
  
 Aby rozwiązać ten problem, skompiluj modułu jako plik .cpp lub Uprość wyrażenie.  
  
 Aby uzyskać więcej informacji, zobacz [/fp (określenie zachowania Floating-Point)](../../build/reference/fp-specify-floating-point-behavior.md).  
  
 Poniższy przykład generuje C2099.  
  
```  
// C2099_2.c  
// compile with: /fp:strict /c  
float X = 2.0 - 1.0;   // C2099  
float X2 = 1.0;   // OK  
```