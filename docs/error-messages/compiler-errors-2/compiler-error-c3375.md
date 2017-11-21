---
title: "C3375 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3375
dev_langs: C++
helpviewer_keywords: C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8c5fc1af314d5c48149365ab77b4b0b3d9da4915
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3375"></a>C3375 błąd kompilatora
"Funkcja": niejednoznaczna funkcja delegata  
  
 Wystąpienia obiektu delegowanego mogło być do statycznej funkcji członkowskiej lub jako niezwiązanego delegata funkcji wystąpienia, kompilator wystawiony tego błędu.  
  
 Aby uzyskać więcej informacji, zobacz [delegata (C++ Component Extensions)](../../windows/delegate-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3375.  
  
```  
// C3375.cpp  
// compile with: /clr  
ref struct R {  
   static void f(R^) {}  
   void f() {}  
};  
  
delegate void Del(R^);  
  
int main() {  
   Del ^ a = gcnew Del(&R::f);   // C3375  
}  
```