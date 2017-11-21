---
title: "C2524 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2524
dev_langs: C++
helpviewer_keywords: C2524
ms.assetid: e71d17f5-2fc2-416b-8dbd-e9bed85eb33a
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f0b80ac9029f530b68afdc379d7660bba1ff76cb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2524"></a>C2524 błąd kompilatora
"destruktora": destruktor/finalizatora musi mieć listę parametrów "void"  
  
 Destruktora lub finalizatora ma listę parametrów, który nie jest [void](../../cpp/void-cpp.md). Inne typy parametrów nie są dozwolone.  
  
## <a name="example"></a>Przykład  
 Poniższy kod powoduje wygenerowanie C2524.  
  
```  
// C2524.cpp  
// compile with: /c  
class A {  
   A() {}  
   ~A(int i) {}    // C2524  
   // try the following line instead  
   // ~A() {}  
};  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod powoduje wygenerowanie C2524.  
  
```  
// C2524_b.cpp  
// compile with: /clr /c  
ref struct I1 {  
protected:  
   !I1(int i);   // C2524  
   // try the following line instead  
   // !I1();  
};  
```