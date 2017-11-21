---
title: "C3541 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3541
dev_langs: C++
helpviewer_keywords: C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 78b4c228999560807aa28dbaecfaa8f0af7b379a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3541"></a>C3541 błąd kompilatora
"type": typeid nie można zastosować do typu, który zawiera "auto"  
  
 [Typeid](../../windows/typeid-cpp-component-extensions.md) operatora nie można zastosować do wskazanego typu, ponieważ zawiera ona `auto` specyfikator.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca C3541.  
  
```  
// C3541.cpp  
// Compile with /Zc:auto  
#include <typeinfo>  
int main() {  
    auto x = 123;  
    typeid(x);    // OK  
    typeid(auto); // C3541  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Auto — słowo kluczowe](../../cpp/auto-keyword.md)   
 [/ Zc: Auto (dedukuj typ zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)   
 [TypeID](../../windows/typeid-cpp-component-extensions.md)