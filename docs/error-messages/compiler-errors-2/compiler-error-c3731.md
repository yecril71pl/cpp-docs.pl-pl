---
title: C3731 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3731
dev_langs:
- C++
helpviewer_keywords:
- C3731
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7b87b59fa7a3e3695da88b5ddb30a84837f6e60
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275307"
---
# <a name="compiler-error-c3731"></a>C3731 błąd kompilatora
niezgodne zdarzenie "function1" i obsługi 'function2'; Źródło zdarzenia i program obsługi zdarzeń muszą być tego samego typu  
  
 Źródło zdarzenia i odbiornika zdarzeń musi mieć tego samego typu (na przykład `native` a `com` typy). Aby naprawić ten błąd, należy typów źródło zdarzeń i dopasowania programu obsługi zdarzeń.  
  
 Poniższy przykład generuje C3731:  
  
```  
// C3731.cpp  
// compile with: /clr  
#using <mscorlib.dll>  
[event_source(native)]  
struct A {  
   __event void MyEvent();  
};  
  
[event_receiver(managed)]  
// try the following line instead  
// [event_receiver(native)]  
struct B {  
   void func();  
   B(A a) {  
      __hook(&A::MyEvent, &a, &B::func);   // C3731  
   }  
};  
  
int main() {  
}  
```