---
title: "C3499 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3499
dev_langs: C++
helpviewer_keywords: C3499
ms.assetid: 6717de5c-ae0f-4024-bdf2-b5598009e7b6
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6f9f6ad123e111239cbd2c2d1ff2bd886b587b60
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3499"></a>C3499 błąd kompilatora
lambda, która została określona ma zwrócony typ void nie może zwracać wartości  
  
 Kompilator generuje ten błąd, gdy wyrażenie lambda, która określa `void` jako typ zwracany zwraca wartość lub wyrażenie lambda zawiera więcej niż jedną instrukcję i zwraca wartość, ale nie określa jej typu zwracanego.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zwraca wartość z wyrażenia lambda lub  
  
-   Podaj zwracany typ wyrażenia lambda lub  
  
-   Łączenie instrukcji, które tworzą treści wyrażenia lambda w jednej instrukcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3499, ponieważ treści wyrażenia lambda zawiera wiele instrukcji i zwraca wartość, ale wyrażenie lambda nie określa typ zwracany:  
  
```  
// C3499a.cpp  
  
int main()  
{  
   [](int x) { int n = x * 2; return n; } (5); // C3499  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwa możliwe rozwiązania do C3499. Pierwsze rozwiązanie zapewnia zwracany typ wyrażenia lambda. Drugie rozwiązanie łączy instrukcji, które tworzą treści wyrażenia lambda w jednej instrukcji.  
  
```  
// C3499b.cpp  
  
int main()  
{  
   // Possible resolution 1:   
   // Provide the return type of the lambda expression.  
   [](int x) -> int { int n = x * 2; return n; } (5);  
  
   // Possible resolution 2:   
   // Combine the statements that make up the body of   
   // the lambda expression into a single statement.  
   [](int x) { return x * 2; } (5);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)