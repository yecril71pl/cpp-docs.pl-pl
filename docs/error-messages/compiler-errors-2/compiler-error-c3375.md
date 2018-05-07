---
title: C3375 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3375
dev_langs:
- C++
helpviewer_keywords:
- C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11805b7ef714c65ff9816828aeea10baa2217ff6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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