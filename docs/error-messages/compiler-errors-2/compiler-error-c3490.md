---
title: "C3490 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3490
dev_langs:
- C++
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6439b48dc752d2bed01371cae59b2d77db16f1f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3490"></a>C3490 błąd kompilatora
Nie można zmodyfikować "var", ponieważ jest uzyskiwany za pośrednictwem obiektu const  
  
 Wyrażenie lambda, które są zadeklarowane w `const` metody nie mogą modyfikować danych niemodyfikowalnym elementu członkowskiego.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń `const` modyfikator z Twojej deklaracji metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3490, ponieważ modyfikuje zmiennej członkowskiej `_i` w `const` metody:  
  
```  
// C3490a.cpp  
// compile with: /c  
  
class C  
{  
   void f() const   
   {  
      auto x = [=]() { _i = 20; }; // C3490  
   }  
  
   int _i;  
};  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład usuwa C3490 przez usunięcie `const` modyfikatora w deklaracji metody:  
  
```  
// C3490b.cpp  
// compile with: /c  
  
class C  
{  
   void f()  
   {  
      auto x = [=]() { _i = 20; };  
   }  
  
   int _i;  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)