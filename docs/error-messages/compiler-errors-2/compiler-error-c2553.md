---
title: C2553 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2553
dev_langs:
- C++
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8cfb09f2701b418ab5570641a78c465ff72ed943
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2553"></a>C2553 błąd kompilatora
"base_function": przesłanianie wirtualnej funkcji zwracany typ różni się od "override_function"  
  
 Funkcja w klasie pochodnej próbował zastąpić funkcję wirtualną w klasie podstawowej, ale funkcja klasy pochodnej nie miał taki sam typ zwracany funkcji klasy podstawowej.  Sygnatura funkcji zastąpienie musi być zgodna podpis przesłaniana funkcja.  
  
 Poniższy przykład generuje C2553:  
  
```  
// C2553.cpp  
// compile with: /clr /c  
ref struct C {  
   virtual void f();  
};  
  
ref struct D : C {  
   virtual int f() override ;   // C2553   
  
   // try the following line instead  
   // virtual void f() override;  
};  
```