---
title: "C3227 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3227
dev_langs: C++
helpviewer_keywords: C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 633cd271aec369bfe7503f4dd1c02ca9ce412f2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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