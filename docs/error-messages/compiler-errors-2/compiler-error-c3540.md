---
title: C3540 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3540
dev_langs:
- C++
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27bae73d387612be41d8462bf0e5e0d82516ba1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 [auto Keyword](../../cpp/auto-keyword.md)   
 [/ Zc: Auto (dedukuj typ zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof, operator](../../cpp/sizeof-operator.md)