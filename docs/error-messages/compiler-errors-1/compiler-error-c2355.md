---
title: "C2355 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2355
dev_langs:
- C++
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3060f97645061e0244091b416dcdfeef343f90b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2355"></a>C2355 błąd kompilatora
"this": może być przywoływany tylko wewnątrz instrukcji lub funkcji niestatycznego elementu członkowskiego danych niestatycznych inicjatorów elementów członkowskich  
  
 `this` Wskaźnik jest prawidłowy tylko w funkcjach niestatycznego elementu członkowskiego lub w danych niestatycznych inicjatorów elementów członkowskich. Ten błąd może spowodować, gdy zakres klasy definicji funkcji członkowskiej, poza deklaracją klasy nie jest poprawnie kwalifikowany. Błąd może również wystąpić, gdy `this` wskaźnika jest używany w funkcji, która nie jest zadeklarowana w klasie.  
  
 Aby rozwiązać ten problem, upewnij się, definicji funkcji członkowskiej dopasowuje deklaracji funkcji Członkowskich w klasie i że jego nie jest zadeklarowany jako statyczny. Dla inicjatorów elementów członkowskich danych upewnij się, że element członkowski danych nie jest zadeklarowany jako statyczny.  
  
 Poniższy przykład generuje C2355 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C2355.cpp  
// compile with: /c  
class MyClass {};  
MyClass *p = this;   // C2355  
  
// OK  
class MyClass2 {  
public:  
   void Test() {  
      MyClass2 *p = this;  
   }  
};  
```