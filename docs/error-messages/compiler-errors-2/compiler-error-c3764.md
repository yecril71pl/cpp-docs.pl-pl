---
title: "C3764 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3764
dev_langs: C++
helpviewer_keywords: C3764
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 35ddb204e3444ea270fb2f11bb0897047fe2863f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3764"></a>C3764 błąd kompilatora
"override_function": nie można zastąpić metody klasy podstawowej "base_class_function"  
  
 Kompilator wykryto zastąpienia źle sformułowane. Na przykład funkcja klasa podstawowa nie była `virtual`. Aby uzyskać więcej informacji, zobacz [zastąpienia](../../windows/override-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3764.  
  
```  
// C3764.cpp  
// compile with: /clr /c  
public ref struct A {  
   void g(int);  
   virtual void h(int);  
};  
  
public ref struct B : A {  
   virtual void g(int) override {}   // C3764  
   virtual void h(int) override {}   // OK  
};  
```  
  
## <a name="example"></a>Przykład  
 C3764 może również wystąpić, gdy jest zarówno jawnie metody klasy podstawowej i o nazwie zastąpiona. Poniższy przykład generuje C3764.  
  
```  
// C3764_b.cpp  
// compile with: /clr /c  
ref struct A {  
   virtual void Test() {}  
};  
  
ref struct B : public A {  
   virtual void Test() override {}  
   virtual void Test2() = A::Test {}   // C3764  
};  
```