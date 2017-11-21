---
title: "C3824 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3824
dev_langs: C++
helpviewer_keywords: C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 529e881d8872d3ea1d69da14ac393282c4f3efc1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3824"></a>C3824 błąd kompilatora
"członek": ten typ nie może występować w tym kontekście (parametr funkcji, zwracany typ lub statyczny element członkowski)  
  
 Unieruchamiania wskaźników nie może być działać parametrów i zwracanych typów lub zadeklarowany `static`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3824:  
  
```  
// C3824a.cpp  
// compile with: /clr /c  
void func() {  
   static pin_ptr<int> a; // C3824  
   pin_ptr<int> b; // OK  
}  
```  
