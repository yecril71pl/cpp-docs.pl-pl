---
title: "C3540 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3540
dev_langs: C++
helpviewer_keywords: C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b3befc331c4f43f4efd4e5039258e0faddae97db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3540"></a>C3540 błąd kompilatora
'type': nie można zastosować operatora sizeof do typu, który zawiera "auto"  
  
 [Sizeof](../../cpp/sizeof-operator.md) operatora nie można zastosować do wskazanego typu, ponieważ zawiera ona `auto` specyfikator.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca C3540.  
  
```  
// C3540.cpp  
// Compile with /Zc:auto  
int main() {  
    auto x = 123;  
    sizeof(x);    // OK  
    sizeof(auto); // C3540  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Auto — słowo kluczowe](../../cpp/auto-keyword.md)   
 [/ Zc: Auto (dedukuj typ zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof, operator](../../cpp/sizeof-operator.md)