---
title: C2355 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2355
dev_langs:
- C++
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b88bf1619a003faa57d1fe1d4f03219267481d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33195727"
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