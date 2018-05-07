---
title: C3227 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3227
dev_langs:
- C++
helpviewer_keywords:
- C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c4d156e70a1ac2c0b05e212ace81b8ccc32d8f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3227"></a>C3227 błąd kompilatora
"parametr": nie można użyć "— słowo kluczowe" przydzielić typu ogólnego  
  
 Do tworzenia wystąpienia typu, wymagana jest odpowiedni konstruktor. Jednak kompilator nie jest w stanie upewnić się, że odpowiedni konstruktor jest dostępny.  
  
 Szablony można użyć zamiast ogólne, aby rozwiązać ten problem, lub można użyć jednej z kilku metod można utworzyć wystąpienia typu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3227.  
  
```  
// C3227.cpp  
// compile with: /clr /c  
generic<class T> interface class ICreate {  
   static T Create();  
};  
  
generic <class T>  
where T : ICreate<T>  
ref class C {  
   void f() {  
      T t = new T;   // C3227  
  
      // OK  
      T t2 = ICreate<T>::Create();  
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );  
   }  
};  
```