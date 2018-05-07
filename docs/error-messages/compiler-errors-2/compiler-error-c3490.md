---
title: C3490 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3490
dev_langs:
- C++
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 593e5509ada926f27243a761da3470eb2d846a22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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