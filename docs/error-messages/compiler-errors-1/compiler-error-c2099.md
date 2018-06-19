---
title: C2099 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2099
dev_langs:
- C++
helpviewer_keywords:
- C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28f525676f6d9238838f0dbc245d9771f99ebeb5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170820"
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