---
title: C3653 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3653
dev_langs:
- C++
helpviewer_keywords:
- C3653
ms.assetid: 316549d7-f7ef-4578-a2ba-57adc8aac527
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a78dd5a9c52c9dfc845de43c62ae38180d0d079f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266464"
---
# <a name="compiler-error-c3653"></a>C3653 błąd kompilatora
"Funkcja": nie można użyć jako nazwanego przesłaniania: przesłaniana funkcja nie znaleziono; Czy pamiętasz o nazwie funkcji jawnie, przy użyciu:: operator?  
  
 Jawne przesłanianie określić funkcję, która nie została odnaleziona w dowolnym interfejsu. Aby uzyskać więcej informacji, zobacz [jawne zastąpienia](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
 Poniższy przykład generuje C3653:  
  
```  
// C3653.cpp  
// compile with: /clr  
public interface struct I {  
   void h();  
};  
  
public ref struct X : public I {  
   virtual void f() new sealed = J {};   // C3653 no J in scope  
   virtual void g() {}   // OK  
   virtual void h() new sealed = I::h {};   // OK  
};  
```